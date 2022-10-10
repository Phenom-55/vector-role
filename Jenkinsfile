pipeline {
    agent {
        label 'centos'
    }
    stages {
        stage('Git') {
            steps{
                git branch: 'master', credentialsId: '60011bee-bc4e-4ca6-a33a-910882e63afc', url: 'git@github.com:Phenom-55/vector-role.git'
            }
        }
        stage('Molecule install') {
            steps{
                sh 'pip install molecule==3.4.0'
                sh 'pip install "ansible-lint<6.0.0"'
                sh 'pip install molecule_docker'
                sh 'pip install molecule_podman'
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
