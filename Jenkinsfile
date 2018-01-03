pipeline {
  agent any
  stages {
    stage('test1') {
      parallel {
        stage('test1') {
          steps {
            echo 'begine'
          }
        }
        stage('return1') {
          steps {
            echo 'chooise1'
          }
        }
        stage('return2') {
          steps {
            echo 'chooise2'
          }
        }
      }
    }
    stage('test2') {
      parallel {
        stage('test2') {
          steps {
            sleep 2
          }
        }
        stage('return2') {
          steps {
            tool(name: 'maven3', type: 'tools')
          }
        }
      }
    }
    stage('test3') {
      steps {
        git(url: 'https://github.com/jglick/simple-maven-project-with-tests.git', branch: 'master', changelog: true, poll: true)
      }
    }
    stage('ansible') {
      steps {
        sh '/usr/bin/ansible localhost -m ping'
      }
    }
    stage('end') {
      steps {
        readFile '*.xml'
      }
    }
  }
  environment {
    mvnHome = 'maven3'
  }
}