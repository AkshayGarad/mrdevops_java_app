@Library('my-shared-library') _

pipeline{
    agent any

    parameters{
        choice(name: 'action', choices: 'create\ndelete', description: 'Choose create/Destroy')
    }

    stages{

        stage('Git Checkout'){
            when { expression {param.action == 'create'}}
            steps{
                script{
                    gitCheckout(
                        branch: "main",
                        url: "https://github.com/AkshayGarad/mrdevops_java_app.git"
                    )
                }
            }
        }

        stage('Unit Test maven'){

            when { expression {param.action == 'create'}}
            steps{
                script{
                    mvnTest()
                }     
            }
        }

        stage('Integration Test maven'){

            when { expression {param.action == 'create'}}
            steps{
                script{
                    mvnintergrationTest()
                }     
            }
        }

        stage('Static Code Analysis: SonarQube'){

            when { expression {param.action == 'create'}}
            steps{
                script{
                    staticCodeAnalysis()
                }     
            }
        }

    }
}