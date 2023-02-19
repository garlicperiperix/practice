pipeline {
            agent any;
            
            tools {
                maven "MVN_HOME"
            }
            
            stages{
                stage("checkout"){
                        steps{
                            echo "fetch the code from GitHib"
                            git 'https://github.com/garlicperiperix/practice.git'
                        }
                    }
                stage("build"){
                        steps{
                            echo "mvn clean package"
                            sh 'mvn clean package -f google/pom.xml'
                        }
                    }
                stage("Artifactory"){
                        steps{
                            echo "Uploading to nexus"
                            nexusArtifactUploader artifacts: [[artifactId: 'google', classifier: '', file: '/root/.jenkins/workspace/declarative-pipeline/google/target/google.war', type: 'war']], credentialsId: 'Nexus', groupId: 'google.photos', nexusUrl: '192.168.0.15:8081/nexus', nexusVersion: 'nexus2', protocol: 'http', repository: 'snapshots', version: '2.0-SNAPSHOT'
                        }
                    }
                stage("Security Scan"){
                        steps{
                            echo "Scanning the security"
                        }
                    }
                stage("Deploy"){
                        steps{
                            echo "Deploy to productive webserver"
                        }
                    } 
            }                    

                        
        
}
