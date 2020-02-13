properties([parameters([string(defaultValue: 'v1', description: 'Please provide a version number', name: 'APP_VERSION', trim: false)])])
node {
    stage("pull repo"){
        git 'https://github.com/azizasalieva95/nodejs_app.git'

    }
    stage("Build Image"){
        sh "docker build -t app1:${APP_VERSION} . "

    }
    stage("Tag Image"){
        sh '''docker tag app1:${APP_VERSION} 763632696774.dkr.ecr.us-east-1.amazonaws.com/app1:${APP_VERSION}'''

    }
    stage("Log in to ECR"){
        sh '''$(aws ecr get-login --no-include-email --region us-east-1)'''

    }
    stage("Push repo"){
        sh "docker push 763632696774.dkr.ecr.us-east-1.amazonaws.com/app1:${APP_VERSION}"
    }
    stage("Notify"){
        sh "echo Hello"

    }
}
