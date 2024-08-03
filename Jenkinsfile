pipeline{
  agent {
      label 'slave1'
  }
  stages{
    stage('version-control'){
      steps{
       checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'id_jenkin', url: 'https://github.com/ikos24/jenkins-master-jobs-1.git']])
    }
    stage('parallel-job'){
      parallel{
        stage('sub-job1'){
          steps{
            echo 'action1'
          }
        }
        stage('sub-job2'){
          steps{
            echo 'action2'
          }
        }
        stage('sub-job3'){
            steps{
                echo 'action3'
            }
        }
      }
    }
    stage('codebuild'){
      agent {
          label 'slave2'
      }
      steps{
        sh 'cat /etc/passwd'
      }
    }
  }
}
}
