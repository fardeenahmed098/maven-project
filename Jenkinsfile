pipeline
{
agent any
stages
{
   stage('scm checkout')
   { steps {  git branch: 'master', url: 'https://github.com/fardeenahmed098/maven-project'  }  }


   stage('build the code')
   { steps {withMaven(jdk: 'JDK_HOME', maven: 'Maven_Home')
            { sh 'mvn package' }
 
           }}
   
  stages('copy plybook from workspace to ansible master && run playbook to deploy artifact from ansible master to dev remote server')
   { steps { sshPublisher(publishers: [sshPublisherDesc(configName: 'ansible_master', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: '', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '//etc//ansible//playbooks', remoteDirectorySDF: false, removePrefix: '', sourceFiles: 'webapp/target/webapp.war'), sshTransfer(cleanRemote: false, excludes: '', execCommand: 'ansible-playbook /etc/ansible/playbooks/dev-deploy.yaml', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '//etc//ansible//playbooks', remoteDirectorySDF: false, removePrefix: '', sourceFiles: 'dev-deploy.yaml')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])}
   
}
}
}
