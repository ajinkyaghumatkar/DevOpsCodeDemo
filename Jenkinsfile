pipeline{

    agent any
    tools{
      maven 'mymaven'
    }
//parameters are used to store data, these parameters can be used in step
//parameters have values which can be of type string,inetegr,boolean,secrret,password
    //synatx of parameter
    //dataType(name:'give name',defaultValue:'value',description:'describe the parameter')
    
    parameters{

        choice(name:'ENV',choices:["","Dev","QA"],description:'Select The environment')

    }

    stages{


            stage('Build on Dev'){

                when{

                    expression{

                        params.ENV == "Dev"
                    }
                }
                steps{

                    git 'https://github.com/ajinkyaghumatkar/DevOpsCodeDemo.git'
                    sh 'mvn pmd:pmd'
                    sh 'mvn compile'
                    echo "Build completed AJinkya !"
                }

            stage('Build on Test'){

                when{

                    expression{

                        params.ENV == "QA"
                    }
                }
                steps{

                    git 'https://github.com/ajinkyaghumatkar/DevOpsCodeDemo.git'
                    sh 'mvn test'
                    echo "Testing completed Ajinkya!"
                }

            }
    }
}
}
