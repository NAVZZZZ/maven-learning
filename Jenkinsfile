pipeline {
agent any

tools {
    jdk 'jdk-21'
    maven 'maven-ci-server'
}

stages {

    stage('Check Tools') {
        steps {
            sh 'echo $JAVA_HOME'
            sh 'java -version'
            sh 'mvn -version'
        }
    }

    stage('Compile') {
        steps {
            sh 'mvn compile'
        }
    }

    stage('Test') {
        steps {
            sh 'mvn test'
        }
    }

    stage('Package') {
        steps {
            sh 'mvn package -DskipTests'
        }
    }
}

post {
    always {
        junit 'target/surefire-reports/*.xml'
    }
}

}
