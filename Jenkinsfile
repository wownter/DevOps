
pipeline {
    agent any

    options {
        skipDefaultCheckout(true)
        disableConcurrentBuilds()
    }

    stages {

        stage('Подготовка окружения') {
            steps {
                // Получаем проект из GitHub
                checkout scm

                // Передаём пароль sudo через Credentials
                withCredentials([
                    string(
                        credentialsId: 'ubuntu-lr4-sudo',
                        variable: 'ANSIBLE_BECOME_PASS'
                    )
                ]) {
                    ansiblePlaybook(
                        installation: 'Ansible-LR4',
                        playbook: 'ansible/run-playbook.yml',
                        inventory: 'ansible/inventory/jenkins/hosts',
                        credentialsId: 'ubuntu-jenkins-ssh',
                        hostKeyChecking: true,
                        become: true,
                        tags: 'prepare'
                    )
                }
            }
        }

        stage('Запуск приложений') {
            steps {
                withCredentials([
                    string(
                        credentialsId: 'ubuntu-lr4-sudo',
                        variable: 'ANSIBLE_BECOME_PASS'
                    )
                ]) {
                    ansiblePlaybook(
                        installation: 'Ansible-LR4',
                        playbook: 'ansible/run-playbook.yml',
                        inventory: 'ansible/inventory/jenkins/hosts',
                        credentialsId: 'ubuntu-jenkins-ssh',
                        hostKeyChecking: true,
                        become: true,
                        tags: 'launch'
                    )
                }
            }
        }
    }
}
