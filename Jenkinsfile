pipeline
{
agent any
stages
{
   stage('scm checkout')
   { steps {  git branch: 'master', url: 'https://github.com/prakashk0301/maven-project'  }  }


   stage('build the code')
   { steps {withMaven(jdk: 'JAVA_HOME', maven: 'MAVEN_HOME')
            { sh 'mvn package' }
 
           }}
   
  stages('copy plybook from workspace to ansible master && run playbook to deploy artifact from ansible master to dev remote server')
   {{
   
}
}
}
