//Declarative Pipeline
// pipeline {
//     agent any

//     stages {
//         stage('Build') {
//             agent {
//                 docker {
//                     image 'node:18-alpine' 
//                     reuseNode true
//                 }
//             }
//             steps {
//                 sh '''
//                     ls -la
//                     node --version
//                     npm --version
//                     npm ci
//                     npm run build
//                     ls -la
//                 '''
//             }
//         }

//         stage('Test') {
//             agent {
//                 docker {
//                     image 'node:18-alpine' 
//                     reuseNode true
//                 }
//             }
//             steps {
//                 sh '''
//                     test -f build/index.html
//                     npm test
//                 '''
//             }
//         }

//         stage('Experiment') {
//             agent {
//                 docker {
//                     image 'node:18-alpine'
//                     reuseNode true
//                 }
//             }
//             steps {
//                 sh '''
//                     echo "Running experiment stage"
//                     echo "Build content:"
//                     ls -la build
//                 '''
//             }
//         }
//     }
// }


//Scripted Pipeline
node {
    // Stage for Build
    stage('Build') {
        // Use Docker container for this stage
        docker.image('node:18-alpine').inside {
            sh '''
                ls -la
                node --version
                npm --version
                npm ci
                npm run build
                ls -la
            '''
        }
    }

    // Stage for Test
    stage('Test') {
        // Use Docker container for this stage
        docker.image('node:18-alpine').inside {
            sh '''
                test -f build/index.html
                npm test
            '''
        }
    }

    // Stage for Experiment
    stage('Experiment') {
        // Use Docker container for this stage
        docker.image('node:18-alpine').inside {
            sh '''
                echo "Running experiment stage"
                echo "Build content:"
                ls -la build
            '''
        }
    }
}
