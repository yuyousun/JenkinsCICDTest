pipeline {
    agent any
  options {
        ansiColor('xterm')
        timestamps()
    }
    triggers {
        GenericTrigger (
            causeString: 'Triggered by develop', 
            genericVariables: [[key: 'ref', value: '$.ref']], 
            printContributedVariables: true, 
            printPostContent: true, 
            regexpFilterExpression: 'refs/heads/' + BRANCH_NAME, 
            regexpFilterText: 'refs/heads/develop', 
            token: 'VXnNT5X/GH8Rs'
        )
    } 
    stages {
      stage("测试部署") {
            when {
                branch 'develop'
            }
          steps {
                echo 'develop branch'
          }
      }
      stage("生产部署") {
            when {
                branch 'master'
            }
          steps {
                echo 'master branch'
          }
      }
    }
    post {
        unstable {
            echo "post unstable=============================="
            // emailext (
            //     body: """项目名称：${JOB_NAME}\n构建编号：${BUILD_NUMBER}\n构建日志：${BUILD_URL}console""",
            //     subject: '【Jenkins构建通知】:$JOB_NAME - Build # $BUILD_NUMBER - Unstable!',
            //     to: 'admin@test.cn',
            //     from: 'test@test.cn'
            // )   
        }   
        success {
            echo "post success=============================="
            // emailext (
            //     body: """项目名称：${JOB_NAME}\n构建编号：${BUILD_NUMBER}\n构建日志：${BUILD_URL}console""",
            //     subject: '【Jenkins构建通知】:$JOB_NAME - Build # $BUILD_NUMBER - Successful!',
            //     to: 'admin@test.cn',
            //     from: 'test@test.cn'
            // )   
        }   
        failure {
            echo "post failure=============================="
            // emailext (
            //     body: """项目名称：${JOB_NAME}\n构建编号：${BUILD_NUMBER}\n构建日志：${BUILD_URL}console""",
            //     subject: '【Jenkins构建通知】:$JOB_NAME - Build # $BUILD_NUMBER - Failure!',
            //     to: 'admin@test.cn',
            //     from: 'test@test.cn'
            // )   
        }   
    } 
}
