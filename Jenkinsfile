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
      echo 'echo set environemnt'
    }
     stage('Build Docker test'){
      echo 'docker build -t react-test -f Dockerfile.test --no-cache .'
     }
     stage('Docker test'){
       echo 'docker run --rm react-test'
     }
     stage('Clean Docker test'){
       echo 'docker rmi react-test'
     }

    stage('Registry'){
      if(env.BRANCH_NAME == 'dev'){
        echo "docker build -t react-app-$BRANCH_NAME-$BUILD_ID --no-cache ."
        echo "docker tag react-app-$BRANCH_NAME-$BUILD_ID localhost:5000/react-app-$BRANCH_NAME-$BUILD_ID"
        echo "docker push localhost:5000/react-app-$BRANCH_NAME-$BUILD_ID"
        echo "docker rmi -f react-app-$BRANCH_NAME-$BUILD_ID localhost:5000/react-app-$BRANCH_NAME-$BUILD_ID"
      }
        if(env.BRANCH_NAME == 'stage'){
          echo "docker build -t react-app-$BRANCH_NAME-$BUILD_ID --no-cache ."
          echo "docker tag react-app-$BRANCH_NAME-$BUILD_ID localhost:5000/react-app-$BRANCH_NAME-$BUILD_ID"
          echo "docker push localhost:5000/react-app-$BRANCH_NAME-$BUILD_ID"
          echo "docker rmi -f react-app-$BRANCH_NAME-$BUILD_ID localhost:5000/react-app-$BRANCH_NAME-$BUILD_ID"
        }
      if(env.BRANCH_NAME == 'main'){
        echo "docker build -t react-app-$BRANCH_NAME-$BUILD_ID --no-cache ."
        echo "docker tag react-app-$BRANCH_NAME-$BUILD_ID localhost:5000/react-app-$BRANCH_NAME-$BUILD_ID"
        echo "docker push localhost:5000/react-app-$BRANCH_NAME-$BUILD_ID"
        echo "docker rmi -f react-app-$BRANCH_NAME-$BUILD_ID localhost:5000/react-app-$BRANCH_NAME-$BUILD_ID"
      }

    }

    stage('Deploy') {
      if(env.BRANCH_NAME == 'main'){
          echo "deploy"
      }
    }
  }
  catch (err) {
    throw err
  }
}
