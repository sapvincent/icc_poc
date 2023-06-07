@Library('Library_Jenkins') _
try {
node ('master') {
   def uniqueId = UUID.randomUUID().toString()
   initialisation(uniqueId)
   {node (uniqueId) {

      // Folder or Path in which are placed the notebooks within Databricks workspace.
      def ADBNOTEBOOKPATH = "MY_NOTEBOOK_FOLDER"        
      def GITHUBPATH = "path_in_the_repo"
      def POCBRANCH = "" //LEGACY
      def TESTBRANCH = "name_of_your_test_branch"
      def PRODBRANCH = "name_of_your_main_branch"
      deployJenkins(ADBNOTEBOOKPATH, GITHUBPATH, POCBRANCH, TESTBRANCH, PRODBRANCH)
      }
   }
}
} catch(Exception err){
   currentBuild.result = "FAILED"
   // You should provide the URL of the alert reaction procedure
   url = "url of the reaction procedure in case of failure"
   // You have provide the email address of the person or the DL which will receive the alert
   email_address = "mail_1@example.com, mail_2@example.com, mail_3@example.com"
   custom_alert_message = "This message will be in the body of the alert email."
   notifyFailed(env.JOB_NAME, env.BUILD_NUMBER, env.BUILD_URL, err.getMessage(), url, email_address, custom_alert_message)
   // need to throw again the error for the pipeline to correctly fail
    throw(err)
}