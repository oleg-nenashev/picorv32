pipeline {
    agent { docker 'librecores/librecores-ci-riscv' }
    environment { 
        testReports = "target/test_reports"
    }
    stages {
      // Run the existing Test suite
      stage("Test") {
        steps {
          sh "ls"
          sh "mkdir -p $testReports"
          sh "make test | tee $testReports/report_noopt.txt"
          sh "make test_sp | tee $testReports/report_sp.txt"
          sh "make test_axi | tee $testReports/report_axi.txt"
        }
      }
    }
    post {
      always {
        archive "$testReports/*"
      }
    }
}