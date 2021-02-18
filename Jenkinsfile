pipeline {
    agent any
    
    environment { 
        FILE_NAME = 'newFile.txt'
    }

    stages {
        stage('Parallel') {
        parallel {
            stage('Stage A') {
                when {
                    environment name: 'FILE_NAME', value: 'filename.txt'
                }
                agent any
                steps {
                    echo "On Stage A"
                    fail()
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
                writeFile file: "$FILE_NAME", text: 'hello write file'
                fail()
            }
        }
        stage('Archive Artifact Write File') {
            steps {
                archiveArtifacts artifacts: "$FILE_NAME", followSymlinks: false
            }
        }
    }
}
