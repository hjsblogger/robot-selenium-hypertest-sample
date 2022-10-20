# Jenkins vs Codemagic: CI alternative for mobile developers

So the mobile team is all focused on delivering a feature with a tight deadline, but the QA team needs the builds to test what has been implemented already. In cases like this, the need to automate the build and deployment process is needed. This can be done by setting up a Continuous Integration/Delivery (CI/CD) tool. Given that there are varieties of choices out there, it might be difficult to choose a good tool.

Jenkins and [Codemagic](https://codemagic.io/?utm_source=referral&utm_medium=lambdatest_jenkins_article&utm_campaign=lambdatest) are both CI/CD tools. In this article, we will be comparing **Codemagic** with the popular continuous integration service, **Jenkins**, from the perspective of a mobile app developer. You'll also get to see what you should look out for in a CI/CD tool as a mobile developer. 

This article targets mobile developers but will be more focused on Flutter users. While it compares two CI/CD tools, it does not go in-depth on what CI/CD is. The next section discusses our contenders briefly.


### What is Jenkins
[Jenkins](https://www.jenkins.io/) is an open-source continuous integration tool written in Java. It provides good flexibility for choosing tools and has a thriving [plugin library](https://plugins.jenkins.io/).

### What is Codemagic
[Codemagic](https://codemagic.io/?utm_source=referral&utm_medium=lambdatest_jenkins_article&utm_campaign=lambdatest), on the other hand, is a continuous integration and delivery service focused on mobile apps. It has support for most of the popular frameworks, like Android, iOS, Flutter, React Native, Cordova and Ionic.

Comparisons between Jenkins and Codemagic will be made using eight criteria:

* Setup
* Running a build
* Speed
* Code signing
* Deploying artifacts
* Maintaining infrastructure
* Notification integration
* Team collaboration
* Community support


Now that we have defined all our criteria, let’s start exploring each of them in detail and find out if Codemagic is a great alternative to Jenkins, specially for mobile app developers.

## Jenkins vs Codemagic: Setup

Let's start by discussing and comparing the setup process of both of these services.

### Jenkins: Setup

Jenkins is a self-hosted continuous integration tool, so to get started, you will first need to download it to your system.

![](https://blog.codemagic.io/uploads/2021/02/jenkins_cover.png)

In my case, it can be downloaded on macOS using the brew package manager:

```yaml
brew install jenkins-lts
```

Run it as a local server:

```yaml
brew services start jenkins-lts
```

After running it on your system, you can access it by going to `http://localhost:8080`.

If you are running for the first time, you have to provide the **Administrator password**.

![](https://blog.codemagic.io/uploads/2021/02/jenkins_setup_1.png)

Next, you will be presented with options to customize Jenkins.

![](https://blog.codemagic.io/uploads/2021/02/jenkins_setup_2.png)

If you go with the option "**Select plugins to install**", then you will see this page for choosing the plugins:

![](https://blog.codemagic.io/uploads/2021/02/jenkins_setup_3.png)

Wait until the installation of the plugins completes. 

![](https://blog.codemagic.io/uploads/2021/02/jenkins_setup_4.png)

You will then be asked to create an **Admin User**.

![](https://blog.codemagic.io/uploads/2021/02/jenkins_setup_5.png)

You can configure or change your Jenkins URL from this page.

![](https://blog.codemagic.io/uploads/2021/02/jenkins_setup_6.png)

After you complete the initial setup, you will see the Jenkins homepage.

![](https://blog.codemagic.io/uploads/2021/02/jenkins_setup_7.png)

### Codemagic: Setup

Codemagic is a cloud-based CI/CD service, so **you don't have to install any additional tools** on your own system. The setup for Codemagic is pretty straightforward.

[![Jenkins alternative for mobile app developers: you do not need to install additional tools to use Codemagic](https://blog.codemagic.io/uploads/2021/02/codemagic_setup_1.png)](https://codemagic.io/signup/?utm_source=referral&utm_medium=lambdatest_jenkins_article&utm_campaign=lambdatest)

Go to Codemagic's [sign up page](https://codemagic.io/signup/?utm_source=referral&utm_medium=lambdatest_jenkins_article&utm_campaign=lambdatest). You can use any cloud-based Git repository (GitHub, Bitbucket, GitLab) to connect and sign up on Codemagic.

[![Codemagic sign up: choose your preferred Git repository or sign up via email](https://blog.codemagic.io/uploads/2021/02/codemagic_setup_2.png)](https://codemagic.io/signup/?utm_source=referral&utm_medium=lambdatest_jenkins_article&utm_campaign=lambdatest)

Codemagic gives you easy access to your projects stored on your git provider. You will be taken to the dashboard after connecting to the repository.

![Jenkins alternative for mobile app developers: Codemagic has easy and straightforward setup](https://blog.codemagic.io/uploads/2021/02/codemagic_setup_3.png)

You may have noticed that Codemagic's initial setup is pretty **fast and user-friendly**. If you are looking for a Jenkins alternative then Codemagic definitely takes the point when it comes to the ease of signup. 

## Jenkins vs Codemagic: Running build

The prerequisite for running a build on either of the services is that the project should be already committed to a cloud repository (such as GitHub).

### Jenkins: Running a build

To start a build on Jenkins, you have to create a new job. As an example, we will be building and testing a Flutter project, which is present on my GitHub account.

First of all, you have to configure some global environment variables.

Select **Manage Jenkins** from the left menu.

![](https://blog.codemagic.io/uploads/2021/02/jenkins_env_1.png)

Choose **Configure System**.

![](https://blog.codemagic.io/uploads/2021/02/jenkins_env_2.png)

Add some global environment variables with the path of the tools that you will need for building and testing your project on Jenkins. Click on **Save**.

![](https://blog.codemagic.io/uploads/2021/02/jenkins_env_3.png)

Now, you have to configure a new job on Jenkins for your project.

* Click on **Create a job** from the homepage.
  
  ![](https://blog.codemagic.io/uploads/2021/02/jenkins_job_1.png)

* Enter a name and select **Freestyle project**. Click on **OK**.
  
  ![](https://blog.codemagic.io/uploads/2021/02/jenkins_job_2.png)

* Go to the **Source Code Management** tab, select **Git** and add your GitHub account credentials there.
  
  ![](https://blog.codemagic.io/uploads/2021/02/jenkins_job_3.png)

* Scroll down to the **Build** section, click on **Add build step** and select **Execute shell**.
  
  ![](https://blog.codemagic.io/uploads/2021/02/jenkins_job_4.png)

* Now, define a very simple build script for an Android debug build of a Flutter project:
  
  ![](https://blog.codemagic.io/uploads/2021/02/jenkins_job_5.png)

You can navigate to the **Console Output** section from the left menu to see the progress.

![](https://blog.codemagic.io/uploads/2021/02/jenkins_job_6.png)

When the build completes, you will see this on your **Dashboard**:

![](https://blog.codemagic.io/uploads/2021/02/jenkins_job_7.png)

### Codemagic: Running a build

Running builds on Codemagic is much simpler, as it provides a much better UI, and you do not need to connect to your Git repository manually. As you have seen during the setup, Codemagic has already connected to the Git repository.

* To configure a project for building, click on the **Add application** button on the **Applications dashboard**. Click on **Set up build**.
  
  ![](media/codemagic_applications_overview.png)

* Connect your repository by selecting your Git provider — in this case GitHub.
  
  ![](media/codemagic_connect_repository.png)

* Select the repository name from the dropdown, then select project type — in this case, Flutter App, then click on the **Finish: Add application** button.

  ![](media/codemagic_setup_application.png)
* You can configure your build pipeline from this page. Then, just click on **Start your first build**.
  
  ![](media/codemagic_application_home.png)
  > Notice how Codemagic gives you the option to select which Flutter build platforms to build for.

* You can choose to build from a git **branch** or git **tag**. If there are multiple workflows for the project, you can select from the **Select workflow** dropdown. Then click on **Start new build**.
  > Git tags are a specific reference to a point in git history. Unlike branches that get updated, git tags are permanent. These tags are useful for software versioning.

  ![](media/codemagic_specify_build_configuration.png)

This will start the build on Codemagic. Wait for it to complete.

![](media/codemagic_completion.png)


You can also see your previous and currently running builds on the **Builds overview** page:

![](media/codemagic_build_overview.png)
  > Note how you can filter builds based on different parameters. 

Codemagic offers a default workflow for Flutter build pipelines. To set up other project-type workflows (Android, React Native, etc.), you have to use the [codemagic.yaml](https://docs.codemagic.io/getting-started/yaml/?utm_source=referral&utm_medium=lambdatest_jenkins_article&utm_campaign=lambdatest) file.

## Jenkins vs Codemagic: Build speed
The build speed is another essential metric to compare. Although build speed mostly depends on the type of application being built, the computer building the app plays a major role. 

### Jenkins: Build speed
Since Jenkins is locally installed, build speed depends on the host computers.

### Codemagic: Build speed
Codemagic build speed is fast. Codemagic provides the M1 macOS machine instance, by default.
  ![](media/codemagic_default_machine.png)
> By enabling billing, you can access more build machine types. 
## Jenkins vs Codemagic: Code signing and Deployment

Code signing is an important stage of a mobile app development workflow that is required if you want to release your app to the public by publishing it to the Google Play Store or Apple App Store.

Deploying build artifacts to Google Play Store or Apple App Store is a cumbersome process, so using a continuous integration service to manage and handle this process is recommended.


### Jenkins: Code signing and Deployment

There are Jenkins plugins available for code signing your build artifacts for both the Android and iOS platforms.

To code sign your Android builds, you can use the [Android Signing plugin](https://www.jenkins.io/doc/pipeline/steps/android-signing/), and for iOS builds, you can use the [Xcode plugin](https://plugins.jenkins.io/xcode-plugin/).


Jenkins plugins are available for deploying your build artifacts. Android artifacts can be deployed to Google Play Store using the plugin [Google Play Android Publisher](https://plugins.jenkins.io/google-play-android-publisher/). For iOS artifacts, the same [Xcode plugin](https://plugins.jenkins.io/xcode-plugin/) that can be used for code signing can also be used for deploying to Apple App Store.

You can also use third-party services, like App Center, to publish your build artifacts. The [App Center plugin](https://plugins.jenkins.io/appcenter/) is available for Jenkins.

### Codemagic: Code signing and Deployment

Codemagic provides a developer-friendly code-signing process that can be configured from the project settings UI or by using the `codemagic.yaml` file.


Codemagic also provides integration with the **Apple Developer Portal** for even easier iOS code signing.

> For more information, check out the code-signing docs for [Android](https://docs.codemagic.io/code-signing-yaml/signing-android/?utm_source=referral&utm_medium=lambdatest_jenkins_article&utm_campaign=lambdatest) and [iOS](https://docs.codemagic.io/code-signing-yaml/signing-ios/?utm_source=referral&utm_medium=lambdatest_jenkins_article&utm_campaign=lambdatest).


On your project settings page, you can scroll down to the **Distribution** section, where you will find options to sign-up and publish your artifacts using different services. Codemagic has support for directly publishing to Google Play Store and App Store Connect.

![](media/codemagic_code_signin.png)

> For more information on publishing your build artifacts, check out the [documentation](https://docs.codemagic.io/publishing-yaml/distribution/?utm_source=referral&utm_medium=lambdatest_jenkins_article&utm_campaign=lambdatest).


## Jenkins vs Codemagic: Maintaining infrastructure

Infrastructural management cost is an important decision-making factor to consider while you are choosing a continuous integration service.

### Jenkins: Maintaining infrastructure

All Jenkins builds run on **self-hosted** servers, which adds the overhead of having to manage users on your own infrastructure and keeping all the development tools updated. It can be integrated with third-party cloud-based servers where the tools can be maintained, but this requires additional configuration, which might be intimidating for someone who is just getting started with CI for their project and might require a DevOps person to be on the team.

### Codemagic: Maintaining infrastructure

The builds on Codemagic run on their **cloud-based** servers, which are completely managed by the experienced Codemagic team. This helps in keeping all the build tools updated so that users can focus on their app development process without having any infrastructural management overhead. Codemagic build systems are [pre-installed](https://docs.codemagic.io/specs/versions/?utm_source=referral&utm_medium=lambdatest_jenkins_article&utm_campaign=lambdatest#pre-installed-tools) with all the tools required for a common mobile app development workflow.

## Jenkins vs Codemagic: Notification integration

Notifications are necessary to keep your team updated on the build status while they focus on the development of the app.

### Jenkins: Notification integration

Jenkins provides several plugins for enabling build notifications through email, Slack, Telegram, and many other platforms. But all of them require additional configuration to enable them for a project.

### Codemagic: Notification integration

Email notifications on the build status and the generated artifacts are enabled by default on Codemagic. Apart from that, Codemagic provides integration with various third-party services, like Slack, MS Teams, and many others.

> Learn more about the steps for enabling them [here](https://docs.codemagic.io/publishing/email-and-slack-notifications/?utm_source=referral&utm_medium=lambdatest_jenkins_article&utm_campaign=lambdatest).

## Jenkins vs Codemagic: Team collaboration

Any continuous integration and deployment workflow can be made more successful with a proper team collaboration setup, as critical bugs get attention and are fixed faster.

### Jenkins: Team collaboration

Jenkins doesn't provide any tools for building a good team collaboration in a workflow. It has to be organized and managed by the development team.

### Codemagic: Team collaboration

In Codemagic, you can have a [Team](https://docs.codemagic.io/teams/teams/?utm_source=referral&utm_medium=lambdatest_jenkins_article&utm_campaign=lambdatest) account, which makes it easy to maintain a good development workflow when more than one developer is working on a project.

On top of that, Codemagic provides a nice feature called [public dashboards](https://docs.codemagic.io/publishing-yaml/public-dashboards/?utm_source=referral&utm_medium=lambdatest_jenkins_article&utm_campaign=lambdatest) that makes it possible for teams to share the list of builds, release notes and build artifacts with people outside Codemagic using a public link.

## Jenkins vs Codemagic: Community support

Another aspect to take into consideration before choosing a continuous integration service is the community support and the quality of the documentation built around the service.

### Jenkins: Community support

Jenkins, being one of the oldest and most popular continuous integration services, has a huge community base. They help in keeping the [documentation](https://www.jenkins.io/doc/) updated and maintaining its enormous number of plugins to keep them functional.

### Codemagic: Community support

Codemagic provides awesome community support through their **Slack Workspace**, which is accessible to the public. Here, developers can ask about any issue they face while using Codemagic and can even suggest feature improvements directly to the Codemagic team.

Codemagic has very detailed open-source [documentation](https://docs.codemagic.io/?utm_source=referral&utm_medium=lambdatest_jenkins_article&utm_campaign=lambdatest). As it is open source, anyone from the community can suggest any improvement to it or can contribute by sending a pull request to the [GitHub repository](https://github.com/codemagic-ci-cd/codemagic-docs).

Codemagic also maintains a [blog](https://blog.codemagic.io/?utm_source=referral&utm_medium=lambdatest_jenkins_article&utm_campaign=lambdatest), which not only has articles related to its CI service but also about various features and implementations of the frameworks, their testing support and many other topics.

> Join the Codemagic Slack workspace [here](https://slack.codemagic.io/).

## Jenkins vs Codemagic: Conclusion

Choosing and building a proper continuous integration and delivery workflow for the team might be difficult, but this article should have simplified it a bit so that you can choose a CI/CD solution best suited for your workflow. 

**Jenkins** is open-sourced and free of cost as it is a self-hosted service, but this increases the overhead of maintaining the infrastructure and keeping the entire set of tools updated. There is an enormous range of plugins available for integrating various tools and services with the workflow.

**[Codemagic](https://codemagic.io/start/?utm_source=referral&utm_medium=lambdatest_jenkins_article&utm_campaign=lambdatest)** is a cloud-based solution (no overhead of maintaining any infrastructure) with pre-installed tools suited for a mobile app development workflow. In addition, it provides easy code-signing and deployment of apps to major services. It also allows numerous third-party [integrations](https://codemagic.io/integrations/?utm_source=referral&utm_medium=lambdatest_jenkins_article&utm_campaign=lambdatest) that help you to make the workflow more productive with the tools that you love.

In a nutshell, if you are setting up a CI/CD workflow focused on mobile apps, then **Codemagic** (having support for all major app development frameworks and tools) should be a better choice over Jenkins. On the other hand, if you want better flexibility and your workflow consists of testing other backend frameworks as well (in addition to app development), then Jenkins might be a better choice for you.

### References

* [Codemagic docs](https://docs.codemagic.io/?utm_source=referral&utm_medium=lambdatest_jenkins_article&utm_campaign=lambdatest)
* [Jenkins docs](https://www.jenkins.io/doc/)
* [Getting started with Codemagic](https://blog.codemagic.io/getting-started-with-codemagic/?utm_source=referral&utm_medium=lambdatest_jenkins_article&utm_campaign=lambdatest)
* [Codemagic integrations](https://codemagic.io/integrations/?utm_source=referral&utm_medium=lambdatest_jenkins_article&utm_campaign=lambdatest)

