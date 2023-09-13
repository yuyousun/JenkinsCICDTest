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
            emailext (
                body: """项目名称：${JOB_NAME}\n构建编号：${BUILD_NUMBER}\n构建日志：${BUILD_URL}console""",
                subject: '【Jenkins构建通知】:$JOB_NAME - Build # $BUILD_NUMBER - Unstable!',
                to: 'admin@test.cn',
                from: 'test@test.cn'
            )   
        }   
        success {
            emailext (
                body: """项目名称：${JOB_NAME}\n构建编号：${BUILD_NUMBER}\n构建日志：${BUILD_URL}console""",
                subject: '【Jenkins构建通知】:$JOB_NAME - Build # $BUILD_NUMBER - Successful!',
                to: 'admin@test.cn',
                from: 'test@test.cn'
            )   
        }   
        failure {
            emailext (
                body: """项目名称：${JOB_NAME}\n构建编号：${BUILD_NUMBER}\n构建日志：${BUILD_URL}console""",
                subject: '【Jenkins构建通知】:$JOB_NAME - Build # $BUILD_NUMBER - Failure!',
                to: 'admin@test.cn',
                from: 'test@test.cn'
            )   
        }   
    } 
}

作者：木讷大叔爱运维
链接：https://juejin.cn/post/7002588434728484871
来源：稀土掘金
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
