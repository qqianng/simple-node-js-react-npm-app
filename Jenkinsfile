// pipeline {
//     agent any
//     environment {
//         CI = 'true'
//     }
//     stages {
//         stage('master') {
//             steps {
//                 sh 'echo master'
//             }
//         }


//         stage('dev') {
//             steps {
//                 sh 'echo dev'
//             }
//         }

//         stage('release') {
//             steps {
//                 sh 'echo release'
//             }
//         }
//     }
// }



pipeline {
    agent any
    stages {
        stage('Check Commit Message') {
            when {
                expression {
                    // 检查提交信息中是否包含 "release:"
                    return sh(script: "git log -1 --pretty=%B | grep -q '^release:'", returnStatus: true) == 0
                }
            }
            steps {
                echo "Commit message contains 'release:', proceeding with build..."
                // 在这里添加构建或部署步骤
                sh 'echo master '
            }
        }

        stage('Skip Build') {
            when {
                expression {
                    // 如果提交信息不包含 "release:"，则跳过构建
                    return sh(script: "git log -1 --pretty=%B | grep -q '^release:'", returnStatus: true) != 0
                }
            }
            steps {
                echo "Commit message does not contain 'release:', skipping build. "
                // 如果需要，添加任何需要执行的步骤
            }
        }
    }
}