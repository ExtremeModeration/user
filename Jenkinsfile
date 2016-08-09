node {
    // Mark the code checkout 'stage'....
    stage 'Stage Checkout'

    // Checkout code from repository and update any submodules
    checkout scm
    sh 'git submodule update --init'

    stage 'Stage Build'

    //branch name from Jenkins environment variables
    echo "My branch is: ${env.BRANCH_NAME}"

    // make gradlew executable
    sh "chmod +x gradlew"

    // build the binary
    sh "./gradlew clean build"

    stage 'Stage Archive'
    //tell Jenkins to archive the apks
    step([$class: 'ArtifactArchiver', artifacts: 'build/libs/*.jar', fingerprint: true])
}
