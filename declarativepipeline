pipeline{
agent any
{
stages
{
stage ('checkout') {
steps{
 git 'https://github.com/smustaba/maven.git'
}
}

stage('build') {
steps{
sh 'mvn package'
}
}

stage ('deploy'){
steps{
sh 'scp /var/lib/jenkins/workspace/declarative-pipeline/webapp/target/webapp.war syed@192.168.52.135:/var/lib/tomcat10/webapps/testapp.war'
}
}
stage ('testing'){
steps{
git 'https://github.com/smustaba/FunctionalTesting.git'
sh 'java -jar /var/lib/jenkins/workspace/declarative-pipeline/testing.jar'
}
}

stage ('deploy to production'){
steps{
sh 'scp /var/lib/jenkins/workspace/declarative-pipeline/webapp/target/webapp.war syed@192.168.52.132:/var/lib/tomcat10/webapps/prodapp.war'
}
}

}
}
}



