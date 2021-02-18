pipeline {
    agent any
    
   parameters {
        string(name: 'FILE_NAME', defaultValue: 'myfile.txt', description: 'File name to archive?')
    }

    stages {
        stage('Parallel') {
        parallel {
            stage('Stage A') {
                agent any
                steps {
                    echo "On Stage A"
                }
            }
            stage('Stage B') {
                agent any
                steps {
                    echo "On Stage B"
                }
            }
        }
        }
        stage('Echo Hello World') {
            steps {
                echo 'Hello World'
            }
        }
        stage('Create Write File') {
            steps {
                writeFile file: "${params.FILE_NAME}", text: 'hello write file'
            }
        }
        stage('Archive Artifact Write File') {
            steps {
                archiveArtifacts artifacts: "${params.FILE_NAME}", followSymlinks: false
            }
        }
    }
}
