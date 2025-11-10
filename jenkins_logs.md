Started by GitHub push by vsanthoshraj
Obtained Jenkinsfile from git https://github.com/vsanthoshraj/g3sha-news-website-node-js.git
[Pipeline] Start of Pipeline
[Pipeline] withCredentials
Masking supported pattern matches of $NEWS_API_KEY
[Pipeline] {
[Pipeline] withEnv
[Pipeline] {
[Pipeline] stage
[Pipeline] { ( Checkout)
[Pipeline] node
Running on docker in /home/ubuntu/docker-slave/workspace/news-website-pipeline
[Pipeline] {
[Pipeline] checkout
Selected Git installation does not exist. Using Default
The recommended git tool is: NONE
using credential github-ssh-key
Cloning the remote Git repository
Avoid second fetch
Checking out Revision 05db076516432d0c04f0c0df190b169679971363 (refs/remotes/origin/main)
Commit message: "Update Jenkinsfile"
Cloning repository https://github.com/vsanthoshraj/g3sha-news-website-node-js.git
 > git init /home/ubuntu/docker-slave/workspace/news-website-pipeline # timeout=10
Fetching upstream changes from https://github.com/vsanthoshraj/g3sha-news-website-node-js.git
 > git --version # timeout=10
 > git --version # 'git version 2.25.1'
using GIT_SSH to set credentials 
Verifying host key using known hosts file
You're using 'Known hosts file' strategy to verify ssh host keys, but your known_hosts file does not exist, please go to 'Manage Jenkins' -> 'Security' -> 'Git Host Key Verification Configuration' and configure host key verification.
 > git fetch --tags --force --progress -- https://github.com/vsanthoshraj/g3sha-news-website-node-js.git +refs/heads/*:refs/remotes/origin/* # timeout=10
 > git config remote.origin.url https://github.com/vsanthoshraj/g3sha-news-website-node-js.git # timeout=10
 > git config --add remote.origin.fetch +refs/heads/*:refs/remotes/origin/* # timeout=10
 > git rev-parse refs/remotes/origin/main^{commit} # timeout=10
 > git config core.sparsecheckout # timeout=10
 > git checkout -f 05db076516432d0c04f0c0df190b169679971363 # timeout=10
 > git rev-list --no-walk f2b4b7e364e9eecbde34811f5a3da5446f80ad9b # timeout=10
[Pipeline] withEnv
[Pipeline] {
[Pipeline] echo
========== Checking out code ==========
[Pipeline] checkout
Selected Git installation does not exist. Using Default
The recommended git tool is: NONE
using credential github-ssh-key
Fetching changes from the remote Git repository
Checking out Revision 05db076516432d0c04f0c0df190b169679971363 (refs/remotes/origin/main)
Commit message: "Update Jenkinsfile"
[Pipeline] sh
 > git rev-parse --resolve-git-dir /home/ubuntu/docker-slave/workspace/news-website-pipeline/.git # timeout=10
 > git config remote.origin.url https://github.com/vsanthoshraj/g3sha-news-website-node-js.git # timeout=10
Fetching upstream changes from https://github.com/vsanthoshraj/g3sha-news-website-node-js.git
 > git --version # timeout=10
 > git --version # 'git version 2.25.1'
using GIT_SSH to set credentials 
Verifying host key using known hosts file
You're using 'Known hosts file' strategy to verify ssh host keys, but your known_hosts file does not exist, please go to 'Manage Jenkins' -> 'Security' -> 'Git Host Key Verification Configuration' and configure host key verification.
 > git fetch --tags --force --progress -- https://github.com/vsanthoshraj/g3sha-news-website-node-js.git +refs/heads/*:refs/remotes/origin/* # timeout=10
 > git rev-parse refs/remotes/origin/main^{commit} # timeout=10
 > git config core.sparsecheckout # timeout=10
 > git checkout -f 05db076516432d0c04f0c0df190b169679971363 # timeout=10
+ git log --oneline -1
05db076 Update Jenkinsfile
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] }
[Pipeline] // node
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { ( SonarQube Analysis)
[Pipeline] node
Running on docker in /home/ubuntu/docker-slave/workspace/news-website-pipeline
[Pipeline] {
[Pipeline] checkout
Selected Git installation does not exist. Using Default
The recommended git tool is: NONE
using credential github-ssh-key
Fetching changes from the remote Git repository
Checking out Revision 05db076516432d0c04f0c0df190b169679971363 (refs/remotes/origin/main)
Commit message: "Update Jenkinsfile"
[Pipeline] withEnv
[Pipeline] {
[Pipeline] script
[Pipeline] {
[Pipeline] tool
[Pipeline] echo
========== Running SonarQube Analysis ==========
[Pipeline] withSonarQubeEnv
Injecting SonarQube environment variables using the configuration: SonarQube
[Pipeline] {
[Pipeline] sh
+ /home/ubuntu/docker-slave/tools/hudson.plugins.sonar.SonarRunnerInstallation/SonarQube_Scanner/bin/sonar-scanner -Dsonar.projectKey=news-website -Dsonar.sources=. -Dsonar.javascript.lcov.reportPaths=coverage/lcov.info
 > git rev-parse --resolve-git-dir /home/ubuntu/docker-slave/workspace/news-website-pipeline/.git # timeout=10
 > git config remote.origin.url https://github.com/vsanthoshraj/g3sha-news-website-node-js.git # timeout=10
Fetching upstream changes from https://github.com/vsanthoshraj/g3sha-news-website-node-js.git
 > git --version # timeout=10
 > git --version # 'git version 2.25.1'
using GIT_SSH to set credentials 
Verifying host key using known hosts file
You're using 'Known hosts file' strategy to verify ssh host keys, but your known_hosts file does not exist, please go to 'Manage Jenkins' -> 'Security' -> 'Git Host Key Verification Configuration' and configure host key verification.
 > git fetch --tags --force --progress -- https://github.com/vsanthoshraj/g3sha-news-website-node-js.git +refs/heads/*:refs/remotes/origin/* # timeout=10
 > git rev-parse refs/remotes/origin/main^{commit} # timeout=10
 > git config core.sparsecheckout # timeout=10
 > git checkout -f 05db076516432d0c04f0c0df190b169679971363 # timeout=10
07:50:39.312 INFO  Scanner configuration file: /home/ubuntu/docker-slave/tools/hudson.plugins.sonar.SonarRunnerInstallation/SonarQube_Scanner/conf/sonar-scanner.properties
07:50:39.318 INFO  Project root configuration file: NONE
07:50:39.339 INFO  SonarScanner CLI 7.3.0.5189
07:50:39.342 INFO  Linux 5.15.0-1084-aws amd64
07:50:40.909 INFO  Communicating with SonarQube Community Build 25.11.0.114957
07:50:40.911 INFO  JRE provisioning: os[linux], arch[x86_64]
07:50:41.553 INFO  Starting SonarScanner Engine...
07:50:41.557 INFO  Java 17.0.13 Eclipse Adoptium (64-bit)
07:50:43.728 INFO  Load global settings
07:50:43.860 INFO  Load global settings (done) | time=131ms
07:50:43.866 INFO  Server id: 48A8E9DF-AZpsOikMA03ISpfIk6Cy
07:50:43.907 INFO  Loading required plugins
07:50:43.908 INFO  Load plugins index
07:50:43.932 INFO  Load plugins index (done) | time=24ms
07:50:43.933 INFO  Load/download plugins
07:50:43.991 INFO  Load/download plugins (done) | time=59ms
07:50:44.526 INFO  Process project properties
07:50:44.557 INFO  Process project properties (done) | time=31ms
07:50:44.582 INFO  Project key: news-website
07:50:44.583 INFO  Base dir: /home/ubuntu/docker-slave/workspace/news-website-pipeline
07:50:44.583 INFO  Working dir: /home/ubuntu/docker-slave/workspace/news-website-pipeline/.scannerwork
07:50:44.607 INFO  Load project settings for component key: 'news-website'
07:50:44.623 INFO  Load project settings for component key: 'news-website' (done) | time=18ms
07:50:44.682 INFO  Load quality profiles
07:50:44.741 INFO  Load quality profiles (done) | time=58ms
07:50:44.775 INFO  Auto-configuring with CI 'Jenkins'
07:50:44.821 INFO  Load active rules
07:50:45.256 INFO  Load active rules (done) | time=436ms
07:50:45.266 INFO  Load analysis cache
07:50:45.290 INFO  Load analysis cache (5.8 kB) | time=25ms
07:50:45.434 INFO  Preprocessing files...
07:50:45.664 INFO  5 languages detected in 9 preprocessed files (done) | time=229ms
07:50:45.665 INFO  23 files ignored because of scm ignore settings
07:50:45.667 INFO  Loading plugins for detected languages
07:50:45.667 INFO  Load/download plugins
07:50:45.675 INFO  Load/download plugins (done) | time=7ms
07:50:45.947 INFO  Load project repositories
07:50:46.117 INFO  Load project repositories (done) | time=171ms
07:50:46.160 INFO  Indexing files...
07:50:46.161 INFO  Project configuration:
07:50:46.176 INFO  9 files indexed (done) | time=16ms
07:50:46.181 INFO  Quality profile for css: Sonar way
07:50:46.183 INFO  Quality profile for docker: Sonar way
07:50:46.185 INFO  Quality profile for js: Sonar way
07:50:46.186 INFO  Quality profile for json: Sonar way
07:50:46.194 INFO  Quality profile for web: Sonar way
07:50:46.195 INFO  ------------- Run sensors on module news-website
07:50:46.281 INFO  Load metrics repository
07:50:46.316 INFO  Load metrics repository (done) | time=34ms
07:50:46.932 INFO  Reflections took 154 ms to scan 1 urls, producing 24 keys and 257 values
07:50:47.234 INFO  Sensor JaCoCo XML Report Importer [jacoco]
07:50:47.236 INFO  'sonar.coverage.jacoco.xmlReportPaths' is not defined. Using default locations: target/site/jacoco/jacoco.xml,target/site/jacoco-it/jacoco.xml,build/reports/jacoco/test/jacocoTestReport.xml
07:50:47.237 INFO  No report imported, no coverage information will be imported by JaCoCo XML Report Importer
07:50:47.237 INFO  Sensor JaCoCo XML Report Importer [jacoco] (done) | time=3ms
07:50:47.237 INFO  Sensor IaC CloudFormation Sensor [iac]
07:50:47.306 INFO  There are no files to be analyzed for the CloudFormation language
07:50:47.307 INFO  Sensor IaC CloudFormation Sensor [iac] (done) | time=70ms
07:50:47.308 INFO  Sensor IaC cfn-lint report Sensor [iac]
07:50:47.309 INFO  Sensor IaC cfn-lint report Sensor [iac] (done) | time=2ms
07:50:47.310 INFO  Sensor IaC Docker Sensor [iac]
07:50:47.470 INFO  1 source file to be analyzed
07:50:47.644 INFO  1/1 source file has been analyzed
07:50:47.649 INFO  Sensor IaC Docker Sensor [iac] (done) | time=337ms
07:50:47.650 INFO  Sensor IaC hadolint report Sensor [iac]
07:50:47.650 INFO  Sensor IaC hadolint report Sensor [iac] (done) | time=1ms
07:50:47.650 INFO  Sensor IaC Azure Resource Manager Sensor [iac]
07:50:47.654 INFO  There are no files to be analyzed for the Azure Resource Manager language
07:50:47.657 INFO  Sensor IaC Azure Resource Manager Sensor [iac] (done) | time=8ms
07:50:47.658 INFO  Sensor Java Config Sensor [iac]
07:50:47.663 INFO  There are no files to be analyzed for the Java language
07:50:47.665 INFO  Sensor Java Config Sensor [iac] (done) | time=7ms
07:50:47.666 INFO  Sensor HTML [web]
07:50:47.790 INFO  Sensor HTML [web] (done) | time=124ms
07:50:47.791 INFO  Sensor JavaScript/TypeScript analysis [javascript]
07:50:48.263 INFO  Detected os: Linux arch: amd64 alpine: false. Platform: LINUX_X64
07:50:48.265 INFO  Deploy location /home/ubuntu/.sonar/js/node-runtime, tagetRuntime: /home/ubuntu/.sonar/js/node-runtime/node,  version: /home/ubuntu/.sonar/js/node-runtime/version.txt
07:50:48.279 INFO  Using embedded Node.js runtime.
07:50:48.280 INFO  Using Node.js executable: '/home/ubuntu/.sonar/js/node-runtime/node'.
07:50:51.347 INFO  Memory configuration: OS (1925 MB), Node.js (987 MB).
07:50:51.487 INFO  WebSocket client connected on /ws
07:50:51.494 INFO  Plugin version: [11.5.0.35357]
07:50:54.152 INFO  Using generated tsconfig.json file using wildcards /tmp/tsconfig-YIWgv3.json
07:50:56.438 INFO  Found 1 tsconfig.json file(s): [/tmp/tsconfig-YIWgv3.json]
07:50:56.438 INFO  2 source files to be analyzed
07:50:56.438 INFO  Creating TypeScript program
07:50:56.439 INFO  TypeScript(5.9.3) configuration file /tmp/tsconfig-YIWgv3.json
07:50:56.439 INFO  2/2 source files have been analyzed
07:50:56.463 INFO  Hit the cache for 0 out of 2
07:50:56.465 INFO  Miss the cache for 2 out of 2: ANALYSIS_MODE_INELIGIBLE [2/2]
07:50:56.465 INFO  Sensor JavaScript/TypeScript analysis [javascript] (done) | time=8673ms
07:50:56.465 INFO  Sensor JavaScript inside HTML analysis [javascript]
07:50:56.475 INFO  1 source file to be analyzed
07:50:56.544 INFO  1/1 source file has been analyzed
07:50:56.544 INFO  Hit the cache for 0 out of 1
07:50:56.544 INFO  Miss the cache for 1 out of 1: ANALYSIS_MODE_INELIGIBLE [1/1]
07:50:56.545 INFO  Sensor JavaScript inside HTML analysis [javascript] (done) | time=80ms
07:50:56.545 INFO  Sensor CSS Rules [javascript]
07:50:56.565 INFO  2 source files to be analyzed
07:50:56.785 INFO  2/2 source files have been analyzed
07:50:56.786 INFO  Hit the cache for 0 out of 0
07:50:56.786 INFO  Miss the cache for 0 out of 0
07:50:56.786 INFO  Sensor CSS Rules [javascript] (done) | time=237ms
07:50:56.786 INFO  Sensor JavaScript/TypeScript Coverage [javascript]
07:50:56.825 INFO  No LCOV files were found using coverage/lcov.info
07:50:56.826 WARN  No coverage information will be saved because all LCOV files cannot be found.
07:50:56.826 INFO  Sensor JavaScript/TypeScript Coverage [javascript] (done) | time=44ms
07:50:56.826 INFO  Sensor CSS Metrics [javascript]
07:50:56.878 INFO  Sensor CSS Metrics [javascript] (done) | time=53ms
07:50:56.879 INFO  Sensor TextAndSecretsSensor [text]
07:50:56.907 INFO  Available processors: 2
07:50:56.907 INFO  Using 2 threads for analysis.
07:50:57.628 INFO  The property "sonar.tests" is not set. To improve the analysis accuracy, we categorize a file as a test file if any of the following is true:
  * The filename starts with "test"
  * The filename contains "test." or "tests."
  * Any directory in the file path is named: "doc", "docs", "test" or "tests"
  * Any directory in the file path has a name ending in "test" or "tests"

07:50:57.672 INFO  Start fetching files for the text and secrets analysis
07:50:57.687 INFO  Using Git CLI to retrieve untracked files
07:50:57.723 INFO  Retrieving language associated files and files included via "sonar.text.inclusions" that are tracked by git
07:50:57.724 INFO  Starting the text and secrets analysis
07:50:57.727 INFO  8 source files to be analyzed for the text and secrets analysis
07:50:57.814 INFO  8/8 source files have been analyzed for the text and secrets analysis
07:50:57.819 INFO  Sensor TextAndSecretsSensor [text] (done) | time=941ms
07:50:57.824 INFO  ------------- Run sensors on project
07:50:58.050 INFO  Sensor Zero Coverage Sensor
07:50:58.059 INFO  Sensor Zero Coverage Sensor (done) | time=9ms
07:50:58.059 INFO  ------------- Gather SCA dependencies on project
07:50:58.063 INFO  Dependency analysis skipped
07:50:58.077 INFO  CPD Executor Calculating CPD for 3 files
07:50:58.092 INFO  CPD Executor CPD calculation finished (done) | time=13ms
07:50:58.098 INFO  SCM revision ID '05db076516432d0c04f0c0df190b169679971363'
07:50:58.303 INFO  Analysis report generated in 203ms, dir size=298.6 kB
07:50:58.366 INFO  Analysis report compressed in 58ms, zip size=49.1 kB
07:50:58.397 INFO  Analysis report uploaded in 27ms
07:50:58.402 INFO  ANALYSIS SUCCESSFUL, you can find the results at: http://35.170.213.164:9000/dashboard?id=news-website
07:50:58.404 INFO  Note that you will be able to access the updated dashboard once the server has processed the submitted analysis report
07:50:58.408 INFO  More about the report processing at http://35.170.213.164:9000/api/ce/task?id=9aa82824-f1cf-425f-b02c-496e555c6323
07:50:58.533 INFO  Analysis total time: 14.481 s
07:50:58.536 INFO  SonarScanner Engine completed successfully
07:50:58.893 INFO  EXECUTION SUCCESS
07:50:58.900 INFO  Total time: 19.647s
[Pipeline] }
[Pipeline] // withSonarQubeEnv
[Pipeline] }
[Pipeline] // script
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] }
[Pipeline] // node
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Build Docker Image)
[Pipeline] node
Running on docker in /home/ubuntu/docker-slave/workspace/news-website-pipeline
[Pipeline] {
[Pipeline] checkout
Selected Git installation does not exist. Using Default
The recommended git tool is: NONE
using credential github-ssh-key
Fetching changes from the remote Git repository
Checking out Revision 05db076516432d0c04f0c0df190b169679971363 (refs/remotes/origin/main)
Commit message: "Update Jenkinsfile"
[Pipeline] withEnv
[Pipeline] {
[Pipeline] echo
========== Building Docker Image ==========
[Pipeline] sh
Warning: A secret was passed to "sh" using Groovy String interpolation, which is insecure.
		 Affected argument(s) used the following variable(s): [NEWS_API_KEY]
		 See https://jenkins.io/redirect/groovy-string-interpolation for details.
+ echo NEWS_API_KEY=****
+ docker build -t news-website:39 .
#0 building with "default" instance using docker driver

#1 [internal] load build definition from Dockerfile
#1 transferring dockerfile: 402B done
#1 DONE 0.0s

#2 [internal] load metadata for docker.io/library/node:18-alpine
#2 DONE 0.1s

#3 [internal] load .dockerignore
#3 transferring context: 2B done
#3 DONE 0.0s
 > git rev-parse --resolve-git-dir /home/ubuntu/docker-slave/workspace/news-website-pipeline/.git # timeout=10
 > git config remote.origin.url https://github.com/vsanthoshraj/g3sha-news-website-node-js.git # timeout=10
Fetching upstream changes from https://github.com/vsanthoshraj/g3sha-news-website-node-js.git
 > git --version # timeout=10
 > git --version # 'git version 2.25.1'
using GIT_SSH to set credentials 
Verifying host key using known hosts file
You're using 'Known hosts file' strategy to verify ssh host keys, but your known_hosts file does not exist, please go to 'Manage Jenkins' -> 'Security' -> 'Git Host Key Verification Configuration' and configure host key verification.
 > git fetch --tags --force --progress -- https://github.com/vsanthoshraj/g3sha-news-website-node-js.git +refs/heads/*:refs/remotes/origin/* # timeout=10
 > git rev-parse refs/remotes/origin/main^{commit} # timeout=10
 > git config core.sparsecheckout # timeout=10
 > git checkout -f 05db076516432d0c04f0c0df190b169679971363 # timeout=10

#4 [1/5] FROM docker.io/library/node:18-alpine@sha256:8d6421d663b4c28fd3ebc498332f249011d118945588d0a35cb9bc4b8ca09d9e
#4 DONE 0.0s

#5 [internal] load build context
#5 transferring context: 130.90kB 0.0s done
#5 DONE 0.0s

#6 [2/5] WORKDIR /app
#6 CACHED

#7 [3/5] COPY package*.json ./
#7 CACHED

#8 [4/5] RUN npm install --only=production
#8 CACHED

#9 [5/5] COPY . .
#9 DONE 0.1s

#10 exporting to image
#10 exporting layers 0.0s done
#10 writing image sha256:8986c7cebf7167c0ce005e56d32304348d23488cc38376db6a56a79bf939a0af done
#10 naming to docker.io/library/news-website:39 done
#10 DONE 0.1s
+ docker tag news-website:39 news-website:latest
+ echo Image built: news-website:39
Image built: news-website:39
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] }
[Pipeline] // node
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { ( Deploy)
[Pipeline] node
Running on docker in /home/ubuntu/docker-slave/workspace/news-website-pipeline
[Pipeline] {
[Pipeline] checkout
Selected Git installation does not exist. Using Default
The recommended git tool is: NONE
using credential github-ssh-key
Fetching changes from the remote Git repository
Checking out Revision 05db076516432d0c04f0c0df190b169679971363 (refs/remotes/origin/main)
Commit message: "Update Jenkinsfile"
[Pipeline] withEnv
[Pipeline] {
[Pipeline] echo
========== Deploying Application ==========
[Pipeline] sh
Warning: A secret was passed to "sh" using Groovy String interpolation, which is insecure.
		 Affected argument(s) used the following variable(s): [NEWS_API_KEY]
		 See https://jenkins.io/redirect/groovy-string-interpolation for details.
+ docker stop news-website
 > git rev-parse --resolve-git-dir /home/ubuntu/docker-slave/workspace/news-website-pipeline/.git # timeout=10
 > git config remote.origin.url https://github.com/vsanthoshraj/g3sha-news-website-node-js.git # timeout=10
Fetching upstream changes from https://github.com/vsanthoshraj/g3sha-news-website-node-js.git
 > git --version # timeout=10
 > git --version # 'git version 2.25.1'
using GIT_SSH to set credentials 
Verifying host key using known hosts file
You're using 'Known hosts file' strategy to verify ssh host keys, but your known_hosts file does not exist, please go to 'Manage Jenkins' -> 'Security' -> 'Git Host Key Verification Configuration' and configure host key verification.
 > git fetch --tags --force --progress -- https://github.com/vsanthoshraj/g3sha-news-website-node-js.git +refs/heads/*:refs/remotes/origin/* # timeout=10
 > git rev-parse refs/remotes/origin/main^{commit} # timeout=10
 > git config core.sparsecheckout # timeout=10
 > git checkout -f 05db076516432d0c04f0c0df190b169679971363 # timeout=10
news-website
+ docker rm news-website
news-website
+ docker run -d --name news-website -p 3000:3000 -e NEWS_API_KEY=**** -e PORT=3000 --restart always news-website:latest
509ff1c12f34449c48f43a47a74cce3b6806bbb515008543fa36b7ac03cb1a20
+ sleep 3
+ docker ps
+ grep news-website
509ff1c12f34   news-website:latest   "docker-entrypoint.s…"   3 seconds ago   Up 3 seconds (health: starting)   0.0.0.0:3000->3000/tcp, [::]:3000->3000/tcp   news-website
+ echo Application deployed on port 3000
Application deployed on port 3000
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] }
[Pipeline] // node
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Declarative: Post Actions)
[Pipeline] node
Running on docker in /home/ubuntu/docker-slave/workspace/news-website-pipeline
[Pipeline] {
[Pipeline] cleanWs
[WS-CLEANUP] Deleting project workspace...
[WS-CLEANUP] Deferred wipeout is used...
[WS-CLEANUP] done
[Pipeline] }
[Pipeline] // node
[Pipeline] echo
 BUILD SUCCESS!
[Pipeline] echo
App running at: http://52.71.5.19:3000/api/news
[Pipeline] }
[Pipeline] // stage
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] }
[Pipeline] // withCredentials
[Pipeline] End of Pipeline
Finished: SUCCESS
