
pipeline {
    agent any

    stages {
     
        stage('checkout conf') {
            steps {
                   dir('code') {
                        sh 'pwd'
                        checkout([
                        $class: 'GitSCM',
                        branches: [[name: '*/main']],
                        extensions: [],
                        userRemoteConfigs: [[url: 'https://github.com/yakirch/myApp_code.git']]
                        ])
                    }
                

                dir('conf') {
                    checkout([
                        $class: 'GitSCM',
                        branches: [[name: '*/main']],
                        extensions: [],
                        userRemoteConfigs: [[url: 'https://github.com/yakirch/myApp_conf1.git']]
                        ])
                }

            }
        }
        stage('run') {
            steps {
                
                //sh 'ls -lRt'
                sh './code/my_code/code.sh'
                sh './conf/my_conf1/config.sh'
               
            }
        }
    }
}