pipeline {
    agent {
        label 'linux'
    }
    stages {
//        stage('Git') {
//            steps{
//                git branch: 'main', credentialsId: 'f4832340-5da4-45a7-abd6-e57396fa3262', url: 'git@github.com:PanMonsters/roles-vector.git'
//            }
//        }
        stage('Molecule install') {
            steps{
                sh 'pip install molecule==3.4.0'
                sh 'pip install "ansible-lint<6.0.0"'
                sh 'pip install molecule_docker'
            }
        }
        stage('Molecule test'){
            steps{
                sh 'molecule test -s centos7'
                cleanWs()
            }
        }
    }
}
