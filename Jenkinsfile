pipeline {
    agent any

    tools {
        // 지정된 이름으로 Gradle을 사용하도록 설정
        gradle 'Gradle 8.2.1'
    }

    stages {
        stage('Checkout') {
            steps {
                script {
                    // Git checkout step with Git tool named "Default"
                    checkout([
                        $class: 'GitSCM',  // GitSCM 클래스를 사용하여 Git 관련 설정을 정의합니다.
                        branches: [[name: '*/master']],  // 가져올 브랜치를 '*/master'로 지정합니다.
                        doGenerateSubmoduleConfigurations: false,  // 서브모듈 구성을 자동으로 생성하지 않도록 설정합니다.
                        extensions: [],  // Git 확장 옵션을 지정하지 않습니다.
                        submoduleCfg: [],  // 서브모듈 구성도 지정하지 않습니다.
                        userRemoteConfigs: [  // Git 원격 저장소 설정을 정의합니다.
                            [url: 'https://github.com/00eunyoung/spring_project.git']  // 원격 저장소 URL을 지정합니다.
                        ]
                    ])
                }
            }
        }

        stage('Prepare Gradle Wrapper') {
            steps {
                // Give execute permission to Gradle Wrapper script
                sh 'chmod +x ./gradlew'
            }
        }

        stage('Build') {
            steps {
                // Gradle clean and build
                sh './gradlew clean build'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                // Copy the WAR file to Tomcat server using scp
                sh "scp -o StrictHostKeyChecking=no build/libs/*.war root@10.0.3.10:/path/to/tomcat/webapps/"

                // 배포가 완료되면 로그에 메시지 출력
                echo 'WAR 파일을 원격 Tomcat 서버로 배포했습니다.'
            }
        }
    }
}
