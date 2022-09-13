pipeline{
    agent any
    tools{ nodejs 'nodejs'}
    stages{
        stage('Test stage'){
            steps{
                echo 'This is the test stage'

            }

        }
        stage('Build Stage'){
            steps{
                echo "This is the building stage"
                '''
                ssh -i /home/ubuntu/server.pem -t -o StrictHostKeyChecking=no ubuntu@ec2-3-89-19-90.compute-1.amazonaws.com
                cd /var/www
                rm -rf html
                sudo mkdir html
                cd html
                sudo pm2 kill
                sudo git init 
                sudo git remote add origin http://github.com/Fearreece/website
                sudo git pull origin main
                npm install
                sudo PORT=3000 pm2 start ./bin/www


                '''

            }

        }
    }
}