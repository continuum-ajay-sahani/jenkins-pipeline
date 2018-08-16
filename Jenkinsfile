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
        buildDiscarder(logRotator(numToKeepStr: '20'))
    }

    /*
    https://jenkins.io/doc/book/pipeline/syntax/#environment
    */
    environment{
        CHECKOUTPATH = 'mycustompath/path'
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
                dir(CHECKOUTPATH){
                    git(                    
                        url: 'https://github.com/dhavlev/simple-java-maven-app.git',
                        branch: 'master'
                    )
                }
                script{
                    if (isUnix()){
                        sh(
                            script: 'echo This is Pre Step'
                        )
                    } else{
                        bat(
                            script: 'echo This is Pre Step'
                        )
                    }
                }              
            }
        }

        stage('Build'){
            steps{
                script{
                    if (isUnix()){
                        sh(
                            script: 'echo This is Build Step'
                        )
                    } else{
                        bat(
                            script: 'echo This is Build Step'
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