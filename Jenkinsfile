pipeline{
agent any stages {
stage('Maven Compile'){
steps{
echo 'Project compile stage'
bat label: 'Compilation running', script: '''mvn compile'''
}
}

stage('Unit Test') {
steps {
echo 'Project Testing stage'
bat label: 'Test running', script: '''mvn test'''

}
}

stage('Jacoco Coverage Report') {
steps{
jacoco()
}
}

stage('SonarQube'){
steps{
bat label: '', script: '''mvn sonar:sonar \
-Dsonar.host.url=http://localhost:9000 \
-Dsonar.login=03b6738e54a71924b82a0cd3811d515b9f51c292'''
}
}



stage('Maven Package'){
steps{
echo 'Project packaging stage'
bat label: 'Project packaging', script: '''mvn package'''
}
}
}
}