pipeline{
    agent{
        node{
            label 'master'
        }
    }

    /*
    https://jenkins.io/doc/book/pipeline/syntax/#tools
    */
    tools{
        git 'Default'
    }

    /*
    https://jenkins.io/doc/book/pipeline/syntax/#parameters
    */
    parameters{
        string(
            name: 'deploy_env',
            defaultValue: 'int',
            description: 'this will make build parameterised'
        )
    }

    /*
    https://jenkins.io/doc/book/pipeline/syntax/#options
    https://jenkins.io/doc/book/pipeline/syntax/#stage-options
    */
    options{
        buildDiscarder(logRotator(numToKeepStr: '1'))
    }

    /*
    https://jenkins.io/doc/book/pipeline/syntax/#environment
    */
    environment{
        CC = 'clang'
    }

    /*
    https://jenkins.io/doc/book/pipeline/syntax/#triggers
    */
    triggers{
        cron('H */4 * * 1-5')
    }

    /*
    https://jenkins.io/doc/book/pipeline/syntax/#stages
    */
    stages{
        stage('pre'){
            steps{
                git(                    
                    url: 'https://github.com/dhavlev/simple-java-maven-app.git',
                    branch: 'master'
                )
                script{
                    if (isUnix()){
                        sh(
                            script: 'echo Hello World'
                        )
                    } else{
                        bat(
                            script: 'echo Hello World'
                        )
                    }
                }              
            }
        }
    }

    /*
    https://jenkins.io/doc/book/pipeline/syntax/#post
    */
    post{
        always{
            echo 'I will always say Hello again!'
        }
    }
}