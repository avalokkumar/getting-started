## Setting up Jenkins on a local machine

Setting up Jenkins involves a series of steps that include installing the required software, setting up Jenkins, and accessing it through a web interface. 
Below are some detailed guide to help you set up Jenkins on your local machine:

### Step 1: Install Java
Jenkins requires Java to run. You can install OpenJDK 11, which is compatible with Jenkins.

#### For Ubuntu/Debian:
```bash
sudo apt update
sudo apt install openjdk-11-jdk -y
```

#### For Windows:
- Download the JDK installer from the [Oracle JDK](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html) or [OpenJDK](https://jdk.java.net/11/) websites.
- Follow the installer instructions to complete the installation.

#### Verify Java Installation:
```bash
java -version
```

### Step 2: Download and Install Jenkins
You can download Jenkins from the official Jenkins website.

#### For Ubuntu/Debian:
1. Add the Jenkins repository key:
   ```bash
   curl -fsSL https://pkg.jenkins.io/debian/jenkins.io.key | sudo tee \
     /usr/share/keyrings/jenkins-keyring.asc > /dev/null
   ```
2. Add the Jenkins repository:
   ```bash
   echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
     https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
     /etc/apt/sources.list.d/jenkins.list > /dev/null
   ```
3. Install Jenkins:
   ```bash
   sudo apt update
   sudo apt install jenkins -y
   ```
4. Start Jenkins:
   ```bash
   sudo systemctl start jenkins
   sudo systemctl enable jenkins
   ```

#### For Windows:
- Download the Jenkins installer from the [Jenkins Website](https://www.jenkins.io/download/).
- Run the installer and follow the on-screen instructions.

### Step 3: Access Jenkins
1. Open your browser and navigate to `http://localhost:8080`.
2. Unlock Jenkins by entering the initial admin password. You can find the password in the Jenkins log file:
   ```bash
   sudo cat /var/lib/jenkins/secrets/initialAdminPassword
   ```
3. Follow the setup wizard to install suggested plugins and create the first admin user.

### Step 4: Configure Jenkins
1. **Install Plugins**: During the setup, Jenkins will prompt you to install plugins. You can choose to install the recommended plugins or select specific ones you need.
2. **Create Admin User**: Set up an admin user during the configuration step.
3. **Configure Tools and Settings**: You can further configure Jenkins by navigating through `Manage Jenkins` to set up JDK, Git, Maven, etc.

### Step 5: Run Your First Job
1. Click on "New Item" to create your first Jenkins job.
2. Choose "Freestyle Project" and configure the job according to your needs.
3. Save and click "Build Now" to test your setup.

### Step 6: Access Jenkins from Another Machine
If you need to access Jenkins from another machine on your network:
1. Open the Jenkins configuration file (`/etc/default/jenkins` for Debian/Ubuntu) and set the `JENKINS_ARGS` line to use the IP address of your machine or `0.0.0.0` to listen on all interfaces.
   ```bash
   HTTP_HOST=0.0.0.0
   ```
2. Restart Jenkins:
   ```bash
   sudo systemctl restart jenkins
   ```

You should now have Jenkins installed and running on your local machine, accessible via the browser. For further configuration and using Jenkins in various CI/CD scenarios, explore Jenkins plugins and documentation at the [Jenkins official website](https://www.jenkins.io/doc/).
