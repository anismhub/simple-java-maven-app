node {
    docker.image('maven:3.9.3-eclipse-temurin-11').inside('-v /root/.m2:/root/.m2'){
        stage('Build') {
		    sh 'mvn -B -DskipTests clean package'
        }
        stage('Test') {
            try {
                sh 'mvn test'
            } catch (Exception e) {
                echo "Test failed: ${e.message}"
            } finally {
                junit 'target/surefire-reports/*.xml'
            }
        }
    }
}