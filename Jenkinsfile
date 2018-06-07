node ('rocm_sshaik1') {
  
    stage('checkouts') {

        env.WORKSPACE = pwd()
        sh "rm ${env.WORKSPACE}/* -fr"
        sh 'id'
        deleteDir()
        stage('Jenkinsfile utility')
        git credentialsId: '8c1bf1d6-da10-49c0-89ed-0165f97d10d4', url: 'https://github.com/rahulmula/Gladiator_Hip.git'
       
      }


    stage('Build') {
      
               sh  """#!/usr/bin/env bash
               cd ${WORKSPACE}
               mkdir build
               cd build
               cmake -DCMAKE_INSTALL_PREFIX=$PWD/ ..
               make -j16
               make install
               """
    }


        
    stage('Unit Test') {

    	try {

                sh 'make check'
                sh 'make package'                
                
    	        }

    	          

catch (Exception ex) {
    
    println("Error in the test");

}

}

    }

