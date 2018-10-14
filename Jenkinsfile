pipeline {
agent any
    
stages{
    stage("Demo"){
        steps{

            echo 'Hello World'
        }
    }
    stage("Checkout"){
        steps{
        //     echo 'Checking out CalibrationResults'
        //     checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'CloneOption', depth: 0, noTags: true, reference: '', shallow: false, timeout: 60], [$class: 'SubmoduleOption', disableSubmodules: false, parentCredentials: false, recursiveSubmodules: true, reference: '', timeout: 60, trackingSubmodules: true], [$class: 'RelativeTargetDirectory', relativeTargetDir: 'server-core'],[$class: 'CheckoutOption', timeout: 60]], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/subrat82/Maven-jenkins.git']]])
        //
        
            git branch: 'master',
            credentialsId: 'subrat82',
             url: 'https://github.com/subrat82/Maven-jenkins.git'
        }
    }
    
    stage("MVN build"){
        steps{
            sh '/opt/apache-maven-3.5.4/bin/mvn clean package -f "/var/lib/jenkins/workspace/TestBuildPipeline/java-maven-app/pom.xml" '
            //-DskipTests "/var/lib/jenkins/workspace/TestBuildPipeline/java-maven-app/"'
        }
    }

    stage("Deploy"){
        steps{
            echo "Deploy"
            sh'/opt/apache-maven-3.5.4/bin/mvn deploy'
        }
    }
}
}
