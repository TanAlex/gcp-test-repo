# gcbapp-dockerfile-example
Example used in the Cloud Build GitHub app tutorial
https://cloud.google.com/cloud-build/docs/run-builds-on-github

The env in github action run

LEIN_HOME=/usr/local/lib/lein
M2_HOME=/usr/share/apache-maven-3.6.3
GOROOT_1_11_X64=/opt/hostedtoolcache/go/1.11.13/x64
ANDROID_HOME=/usr/local/lib/android/sdk
JAVA_HOME_11_X64=/usr/lib/jvm/adoptopenjdk-11-hotspot-amd64
ImageVersion=20200920.1
AGENT_TOOLSDIRECTORY=/opt/hostedtoolcache
LANG=C.UTF-8
AZURE_EXTENSION_DIR=/opt/az/azcliextensions
POWERSHELL_DISTRIBUTION_CHANNEL=GitHub-Actions-ubuntu18
GITHUB_API_URL=https://api.github.com
INVOCATION_ID=76f00828fec54b4eb84ea36749cb452c
BOOST_ROOT_1_72_0=/opt/hostedtoolcache/boost/1.72.0/x64
JAVA_HOME_12_X64=/usr/lib/jvm/adoptopenjdk-12-hotspot-amd64
ANDROID_SDK_ROOT=/usr/local/lib/android/sdk
RUNNER_TOOL_CACHE=/opt/hostedtoolcache
SWIFT_PATH=/usr/share/swift/usr/bin
JAVA_HOME=/usr/lib/jvm/adoptopenjdk-8-hotspot-amd64
RUNNER_TRACKING_ID=github_527933d6-528b-4e7f-8d83-a101529bfba6
DOTNET_MULTILEVEL_LOOKUP="0"
GITHUB_REPOSITORY_OWNER=TanAlex
GITHUB_ACTIONS=true
DOTNET_SKIP_FIRST_TIME_EXPERIENCE="1"
CI=true
DOTNET_NOLOGO="1"
USER=runner
GITHUB_HEAD_REF=
GITHUB_ACTOR=TanAlex
GITHUB_ACTION=run2
GRADLE_HOME=/usr/share/gradle
PWD=/home/runner/work/gcp-test-repo/gcp-test-repo
ImageOS=ubuntu18
HOME=/home/runner
GOROOT=/opt/hostedtoolcache/go/1.14.9/x64
CLOUDSDK_METRICS_ENVIRONMENT=github-actions-setup-gcloud
JOURNAL_STREAM=9:22534
GOROOT_1_14_X64=/opt/hostedtoolcache/go/1.14.9/x64
JAVA_HOME_8_X64=/usr/lib/jvm/adoptopenjdk-8-hotspot-amd64
RUNNER_TEMP=/home/runner/work/_temp
GITHUB_RETENTION_DAYS=90
GOROOT_1_15_X64=/opt/hostedtoolcache/go/1.15.2/x64
CONDA=/usr/share/miniconda
GOROOT_1_13_X64=/opt/hostedtoolcache/go/1.13.15/x64
BOOST_ROOT_1_69_0=/opt/hostedtoolcache/boost/1.69.0/x64
GITHUB_ENV=/home/runner/work/_temp/_runner_file_commands/set_env_422f5776-0ba1-444f-9a41-c23b063842d3
DEBIAN_FRONTEND=noninteractive
RUNNER_WORKSPACE=/home/runner/work/gcp-test-repo
GITHUB_REF=refs/heads/master
GITHUB_SHA=ed4364976870e00f5ecba2485dc8d86af7f0dae8
GITHUB_RUN_ID=290716281
GITHUB_SERVER_URL=https://github.com
SERVICE_NAME=my-test-service
GOROOT_1_12_X64=/opt/hostedtoolcache/go/1.12.17/x64
GECKOWEBDRIVER=/usr/local/share/gecko_driver
DEPLOYMENT_BASEPATH=/opt/runner
GITHUB_EVENT_PATH=/home/runner/work/_temp/_github_workflow/event.json
CHROMEWEBDRIVER=/usr/local/share/chrome_driver
HOMEBREW_REPOSITORY="/home/linuxbrew/.linuxbrew/Homebrew"
GITHUB_GRAPHQL_URL=https://api.github.com/graphql
RUN_ACTION=rollback
RUNNER_OS=Linux
GITHUB_BASE_REF=
VCPKG_INSTALLATION_ROOT=/usr/local/share/vcpkg
GITHUB_PATH=/home/runner/work/_temp/_runner_file_commands/add_path_422f5776-0ba1-444f-9a41-c23b063842d3
GITHUB_JOB=setup-build-deploy
PERFLOG_LOCATION_SETTING=RUNNER_PERFLOG
JAVA_HOME_7_X64=/usr/lib/jvm/zulu-7-azure-amd64
RUNNER_USER=runner
SHLVL=1
HOMEBREW_PREFIX="/home/linuxbrew/.linuxbrew"
GITHUB_REPOSITORY=TanAlex/gcp-test-repo
GITHUB_EVENT_NAME=workflow_dispatch
LEIN_JAR=/usr/local/lib/lein/self-installs/leiningen-2.9.4-standalone.jar
RUN_REGION=us-central1
GITHUB_RUN_NUMBER=5
RUNNER_PERFLOG=/home/runner/perflog
GITHUB_WORKFLOW=Deploy to Dev
ANT_HOME=/usr/share/ant
PATH=/opt/hostedtoolcache/gcloud/290.0.1/x64/bin:/home/linuxbrew/.linuxbrew/bin:/home/linuxbrew/.linuxbrew/sbin:/usr/share/rust/.cargo/bin:/home/runner/.config/composer/vendor/bin:/home/runner/.dotnet/tools:/snap/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
SELENIUM_JAR_PATH=/usr/share/java/selenium-server-standalone.jar
GITHUB_WORKSPACE=/home/runner/work/gcp-test-repo/gcp-test-repo
CHROME_BIN=/usr/bin/google-chrome
HOMEBREW_CELLAR="/home/linuxbrew/.linuxbrew/Cellar"

Only when it runs as GITHUB_EVENT_NAME=workflow_dispatch
we will get the parameters for workflow
We can use
```
if [ "$GITHUB_EVENT_NAME" = "workflow_dispatch" ];then
   if [ "$GITHUB_REF" != "refs/heads/dev" ];then
      echo "GITHUB_REF: $GITHUB_REF is not refs/heads/dev, quit"
      exit(1)
   fi
else
   RUN_ACTION=deploy
fi
```