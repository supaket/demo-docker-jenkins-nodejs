node {
  try {
    stage('Checkout') {
      checkout scm
    }
    stage('Environment') {
      sh 'git --version'
      echo "Branch: ${env.BRANCH_NAME}"
      echo "Build ID: ${env.BUILD_ID}"
      echo "Build Tag: ${env.BUILD_TAG}"
      sh 'docker -v'
      sh 'printenv'
    }
//     stage('Build Docker test'){
//      sh 'docker build -t react-test -f Dockerfile.test --no-cache .'
//     }
//     stage('Docker test'){
//       sh 'docker run --rm react-test'
//     }
//     stage('Clean Docker test'){
//       sh 'docker rmi react-test'
//     }
    stage('Registry'){
      if(env.BRANCH_NAME == 'dev'){
        sh "docker build -t react-app-$BRANCH_NAME --no-cache ."
        sh "docker tag react-app-$BRANCH_NAME localhost:5000/react-app-${env.BRANCH_NAME}"
        sh "docker push localhost:5000/react-app-$BRANCH_NAME"
        sh "docker rmi -f react-app-$BRANCH_NAME localhost:5000/react-app-$BRANCH_NAME"
      }
//       if(env.BRANCH_NAME == 'stage'){
//         sh 'docker build -t react-app-${env.BRANCH_NAME} --no-cache .'
//         sh 'docker tag react-app-${env.BRANCH_NAME} localhost:5000/react-app-${env.BRANCH_NAME}'
//         sh 'docker push localhost:5000/react-app-${env.BRANCH_NAME}'
//         sh 'docker rmi -f react-app-${env.BRANCH_NAME} localhost:5000/react-app-${env.BRANCH_NAME}'
//       }
//       if(env.BRANCH_NAME == 'main'){
//         sh 'docker build -t react-app-${env.BRANCH_NAME} --no-cache .'
//         sh 'docker tag react-app-${env.BRANCH_NAME} localhost:5000/react-app-${env.BRANCH_NAME}'
//         sh 'docker push localhost:5000/react-app-${env.BRANCH_NAME}'
//         sh 'docker rmi -f react-app-${env.BRANCH_NAME} localhost:5000/react-app-${env.BRANCH_NAME}'
//       }
    }
  }
  catch (err) {
    throw err
  }
}