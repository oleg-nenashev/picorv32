docker.image('librecores/librecores-ci-riscv').inside {
  // Checkout SCM
  stage("Checkout") {
    checkout scm
  }
  
  // Run the existing Test suite
  stage("Test") {
    def testReports = "target/test_reports"
    sh "mkdir -p $testReports"
    sh "make test | tee $testReports/report_noopt.txt"
    sh "make test_sp | tee $testReports/report_sp.txt"
    sh "make test_axi | tee $testReports/report_axi.txt"
    archive "$testReports/*"
  }
}