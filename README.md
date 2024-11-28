# Experiment No. 3: DevOps_Applying-CI-CD-Principles-to-Web-Development-Using-Jenkins-Git-and-Local-HTTP-Server

<h1>Aim</h1>
<p>The aim of this experiment is to set up a CI/CD pipeline for a web development project using Jenkins, Git, and webhooks, without the need for a Jenkinsfile. You will learn how to automatically build and deploy a web application to a local HTTP server whenever changes are pushed to the Git repository, using Jenkins' "Execute Shell" build step.</p>

<h2>Theory</h2>
<p>Continuous Integration and Continuous Deployment (CI/CD) is a critical practice in modern software development, allowing teams to automate the building, testing, and deployment of applications. This process ensures that software updates are consistently and reliably delivered to end-users, leading to improved development efficiency and product quality.</p>
<p>In this context, this introduction sets the stage for an exploration of how to apply CI/CD principles specifically to web development using Jenkins, Git, and a local HTTP server. We will discuss the key components and concepts involved in this process.</p>

<h3>Key Components:</h3>
<ul>
  <li><strong>Jenkins:</strong> Jenkins is a widely used open-source automation server that helps automate various aspects of the software development process. It is known for its flexibility and extensibility and can be employed to create CI/CD pipelines.</li>
  <li><strong>Git:</strong> Git is a distributed version control system used to manage and track changes in source code. It plays a crucial role in CI/CD by allowing developers to collaborate, track changes, and trigger automation processes when code changes are pushed to a repository.</li>
  <li><strong>Local HTTP Server:</strong> A local HTTP server is used to host and serve web applications during development. It is where your web application can be tested before being deployed to production servers.</li>
</ul>

<h3>CI/CD Principles:</h3>
<ul>
  <li><strong>Continuous Integration (CI):</strong> CI focuses on automating the process of integrating code changes into a shared repository frequently. It involves building and testing the application each time code is pushed to the repository to identify and address issues early in the development cycle.</li>
  <li><strong>Continuous Deployment (CD):</strong> CD is the practice of automatically deploying code changes to production or staging environments after successful testing. CD aims to minimize manual intervention and reduce the time between code development and its availability to end-users.</li>
</ul>

<h3>The CI/CD Workflow:</h3>
<ul>
  <li>Code Changes: Developers make changes to the web application's source code locally.</li>
  <li>Git Repository: Developers push their code changes to a Git repository, such as GitHub or Bitbucket.</li>
  <li>Webhook: A webhook is configured in the Git repository to notify Jenkins whenever changes are pushed.</li>
  <li>Jenkins Job: Jenkins is set up to listen for webhook triggers. When a trigger occurs, Jenkins initiates a CI/CD pipeline.</li>
  <li>Build and Test: Jenkins executes a series of predefined steps, which may include building the application, running tests, and generating artifacts.</li>
  <li>Deployment: If all previous steps are successful, Jenkins deploys the application to a local HTTP server for testing.</li>
  <li>Verification: The deployed application is tested locally to ensure it functions as expected.</li>
  <li>Optional Staging: For more complex setups, there might be a staging environment where the application undergoes further testing before reaching production.</li>
  <li>Production Deployment: If the application passes all tests, it can be deployed to the production server.</li>
</ul>

<h3>Benefits of CI/CD in Web Development:</h3>
<ul>
  <li><strong>Rapid Development:</strong> CI/CD streamlines development processes, reducing manual tasks and allowing developers to focus on writing code.</li>
  <li><strong>Improved Quality:</strong> Automated testing helps catch bugs early, ensuring higher code quality.</li>
  <li><strong>Faster Time to Market:</strong> Automated deployments reduce the time it takes to release new features or updates.</li>
  <li><strong>Consistency:</strong> The process ensures that code is built, tested, and deployed consistently, reducing the risk of errors.</li>
</ul>

<h2>Materials</h2>
<ul>
  <li>A computer with administrative privileges</li>
  <li>Jenkins installed and running (<a href="https://www.jenkins.io/download/">Download Jenkins</a>)</li>
  <li>Git installed (<a href="https://git-scm.com/downloads">Download Git</a>)</li>
  <li>A local HTTP server for hosting web content (e.g., Apache, Nginx)</li>
  <li>A Git repository (e.g., on GitHub or Bitbucket)</li>
</ul>

<h2>Experiment Steps</h2>

<h3>Step 1: Set Up the Web Application and Local HTTP Server</h3>
<ul>
  <li>Create a simple web application or use an existing one. Ensure it can be hosted by a local HTTP server.</li>
  <li>Set up a local HTTP server (e.g., Apache or Nginx) to serve the web application. Ensure it's configured correctly and running.</li>
</ul>

<h3>Step 2: Set Up a Git Repository</h3>
<pre><code>git init
git add .
git commit -m "Initial commit"</code></pre>
<ul>
  <li>Create a remote Git repository (e.g., on GitHub or Bitbucket) to push your code to later.</li>
</ul>

<h3>Step 3: Install and Configure Jenkins</h3>
<ul>
  <li>Download and install Jenkins following the instructions for your operating system (<a href="https://www.jenkins.io/download/">Download Jenkins</a>).</li>
  <li>Open Jenkins in your web browser (usually at <code>http://localhost:8080</code>) and complete the initial setup.</li>
  <li>Install the necessary plugins for Git integration, job scheduling, and webhook support.</li>
  <li>Configure Jenkins to work with Git by setting up your Git credentials in the Jenkins Credential Manager.</li>
</ul>

<h3>Step 4: Create a Jenkins Job</h3>
<ul>
  <li>Create a new Jenkins job using the "Freestyle project" type.</li>
  <li>Configure the job to use a webhook trigger by selecting the "GitHub hook trigger for GITScm polling" option in the job's settings.</li>
</ul>

<h3>Step 5: Set Up the Jenkins Job (Using Execute Shell)</h3>
<ul>
  <li>In the job configuration, go to the "Build" section.</li>
  <li>Add a build step of type "Execute shell."</li>
  <li>In the "Command" field, define the build and deployment steps using shell commands:
    <pre><code>
rm -rf /var/www/html/webdirectory/*
cp -r * /var/www/html/webdirectory/
    </code></pre>
  </li>
</ul>

<h3>Step 6: Set Up a Webhook in Git Repository</h3>
<ul>
  <li>In your Git repository (e.g., on GitHub), go to "Settings" and then "Webhooks."</li>
  <li>Create a new webhook and configure it to send a payload to the Jenkins webhook URL (usually <code>http://jenkins-server/github-webhook/</code>).</li>
</ul>

<h3>Step 7: Trigger the CI/CD Pipeline</h3>
<ul>
  <li>Push changes to your Git repository. The webhook should trigger the Jenkins job automatically, executing the build and deployment steps defined in the "Execute Shell" build step.</li>
  <li>Monitor the Jenkins job's progress in the Jenkins web interface.</li>
</ul>

<h3>Step 8: Verify the CI/CD Pipeline</h3>
<ul>
  <li>Visit the URL of your local HTTP server to verify that the web application has been updated with the latest changes.</li>
</ul>

<h2>Conclusion</h2>
<p>This experiment demonstrates how to set up a CI/CD pipeline for web development using Jenkins, Git, a local HTTP server, and webhooks, without the need for a Jenkinsfile. By defining and executing the build and deployment steps using the "Execute Shell" build step, you can automate your development workflow and ensure that your web application is continuously updated with the latest changes.</p>
