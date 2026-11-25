pipeline {
    agent any

    tools {
        jdk 'JAVA_HOME'
        maven 'M2_HOME'
    }

    stages {
        stage('Récupération du projet') {
            steps {
                git branch: 'main',
                    credentialsId: 'github-credentials',
                    url: 'https://github.com/mahmoudhsin/DevOps-AppGestionDesProjets.git'
            }
        }

        stage('Génération du livrable') {
            steps {
                dir('backend') {
                    sh 'mvn clean package -DskipTests'
                }
            }
        }
    }

    post {
        success {
            echo 'Build réussi : le .jar est dans target/'
        }
        failure {
            echo 'Le build a échoué'
        }
    }
}
