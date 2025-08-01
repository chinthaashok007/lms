pipeline {
    agent any
    stages {
        stage('Code Analysis') {
            steps {
<<<<<<< HEAD
               echo 'Sonar Analysis Started'
               sh 'cd webapp && sudo docker run --rm -e SONAR_HOST_URL="http://3.81.122.225:9000/" -v ".:/usr/src" -e SONAR_TOKEN="sqp_0ecccbc398b22165d361c15a791b2de06166c04d" sonarsource/sonar-scanner-cli -Dsonar.projectKey=lms'
               echo 'Sonar Analysis Completed'
=======
                echo 'CODE QUALITY CHECK'
                // Below command works in jenkins 
                sh 'cd webapp && sudo docker run --rm -e SONAR_HOST_URL="http://3.147.64.186:9000" -v ".:/usr/src" -e SONAR_TOKEN="sqp_64e4ddd0325ea51aa54516d2e8aa0af7c23a48c0" sonarsource/sonar-scanner-cli -Dsonar.projectKey=lms'
                echo 'CODE QUALITY COMPLETED'
>>>>>>> 8c3804402a8412faa2d9cfb9852b268a8ee4151e
            }
        }
        stage('Build Artifacts') {
            steps {
                echo 'Build LMS'
                sh 'cd webapp && npm install && npm run build'
                echo 'Build Completed'
            }
        }
        stage('Release Artifacts') {
            steps {
<<<<<<< HEAD
                script {
                    def packageJson = readJSON file: 'webapp/package.json'
                    def packageJSONVersion = packageJson.version
                    echo "${packageJSONVersion}"
                    sh "zip webapp/lms-${packageJSONVersion}.zip -r webapp/dist"
                    sh "curl -v -u admin:lms12345 --upload-file webapp/lms-${packageJSONVersion}.zip http://3.81.122.225:8081/repository/lms/"
                }
            }
        }
        stage('Deploy LMS - dev') {
            steps {
                script {
                    def packageJson = readJSON file: 'webapp/package.json'
                    def packageJSONVersion = packageJson.version
                    echo "${packageJSONVersion}"
                    sh "curl -u admin:lms12345 -X GET \'http://3.81.122.225:8081/repository/lms/lms-${packageJSONVersion}.zip\' --output lms-'${packageJSONVersion}'.zip"
                    sh 'sudo rm -rf /var/www/html/*'
                    sh "sudo unzip -o lms-'${packageJSONVersion}'.zip"
                    sh "sudo cp -r webapp/dist/* /var/www/html"
                }
            }
        }
        stage('Clean Up Workspace') {
            steps {
                    echo 'Cleaning Work Space'
                    // Install Cleanup Workspace plugin to make below command work
                    cleanWs()
            }
        }
=======
               script {
                   def packageJson = readJSON file: 'webapp/package.json'
                   def packageJSONVersion = packageJson.version
                   echo "${packageJSONVersion}"
                   sh "zip webapp/lms-${packageJSONVersion}.zip -r webapp/dist"
                   sh "curl -v -u admin:lms12345 --upload-file webapp/lms-${packageJSONVersion}.zip http://3.147.64.186:8081/repository/lms/"
               }
           }
>>>>>>> 8c3804402a8412faa2d9cfb9852b268a8ee4151e

        }
        stage('Deploy') {
            steps {
               script {
                   def packageJson = readJSON file: 'webapp/package.json'
                   def packageJSONVersion = packageJson.version
                   echo "${packageJSONVersion}"
                   sh "curl -u admin:lms12345 -X GET \'http://3.147.64.186:8081/repository/lms/lms-${packageJSONVersion}.zip\' --output lms-'${packageJSONVersion}'.zip"
                   sh 'sudo rm -rf /var/www/html/*'
                   sh "sudo unzip -o lms-'${packageJSONVersion}'.zip"
                   sh "sudo cp -r webapp/dist/* /var/www/html"
               }
           }

        }
        stage('Cleanup') {
            steps {
                cleanWs()
            }
        }
    }
}
