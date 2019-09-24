Pipeline configuration:

The default interaction with Jenkins required manual jobs. It keeps configuration of a job in Jenkins separately from source code. With Pipeline plugin users can implement al pipeline procedure in Jenkinsfile and store it in repository with other code. This approach is used in Mr Checker framework
More info: https://jenkins.io/solutions/pipeline/

Our CI & CD process is divided into a few separate files:
Jenkins_node.groovy – it is file to manage all process. It defines all operations executes on Jenkins node, so all code in this file is closed in node closure. 
Workflow in Jenkinsfile:
* Read all parameters from Jenkins job
* Execute stage to preparing environment
* Execute git pull command
* Set Jenkins job description
* Execute compilation of the project in special prepared docker container
* Execute unit tests
* Execute integration tests
* Deploy artifacts to local repository
* Deploy artifacts to outside repository (nexus/arifactory)

Not all steps must be in the Jenkins files. It should be configure specially for job requirements.

## Description of stages:

### Stage “Prepare environment”

First thing to do in this stage is overwriting of properties loaded from Jenkins job. It is defined in “overrideProperties” function. Next function “setJenkinsJobVariables” defines environment variables such as : 
* JOB_NAME_UPSTREAM
* BUILD_DISPLAY_NAME_UPSTREAM
* BUILD_URL_UPSTREAM
* GIT_CREDENTIALS
* JENKINS_CREDENTIALS

Last function in stage – “setWorkspace” Creates an environment variable with path to local workspace. This is required because when using pipeline plugin. Jenkins does not create the WORKSPACE env variables.

### Stage “Git pull”

It pulls sources from the repository and loads “git pull” file which contains additional methods: 

* setGitAuthor – setting properties about git author to the file “build.properties” and loading created file
* tryMergeWithBranch – checking if actual branch can be merged with default main branch

### Stage “Build compile”

Verify by maven that code can builds without errors

### Stage “Unit test”

Execute unit tests with mvn surefire test and publish reports as junit and allure format

### Stage “Integration test”

Execute integration tests with mvn surefire test and publish reports as junit and allure format

### Stage “Deploy – local repo”

Archive artifacts as jar in local repository

### Stage ”Deploy – nexu repo”

Deploy to the outside repository by maven release deploy command with credentials stored in Jenkins machine
 Additional files:
* mailSender.groovy – contains methods to send mail with generated content
* stashNotification.groovy – send job status for bitbucket by curl command
* utils.groovy -   contains additional functions to load properties, files and generating additional data



