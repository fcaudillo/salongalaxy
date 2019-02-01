 node {
 
   stage('Git checkout') {
       git 'https://github.com/fcaudillo/salongalaxy.git'
   }
   
   stage('Construyendo imagen') {
       sh ('ls')
       sh ('docker build -t fcaudillo/salon-galaxy -f Dockerfile-dev-galaxy . ') 
   }
  
   stage('Subiendo la imagen.') {
        withDockerRegistry([ credentialsId: "my_crends_docker", url: '' ]) {   
           sh "docker push fcaudillo/salon-galaxy  "    
           
       }    
   }
   
   stage('Deploy a produccion') {
       sh "cd main && docker-compose up -d --no-deps --build salon-galaxy"
   }

}