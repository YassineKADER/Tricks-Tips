# Jenkins
### Setup Jenkins on your machine
Install an OpemJdk:
```
sudo apt install openjdk-11-jdk
```
Add Jenkins repository && Install Jenkins:
```
wget https://pkg.jenkins.io/debian-stable/jenkins.io.key
sudo apt-key add jenkins.io.key
sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
sudo apt update
sudo apt install jenkins
```
Start Jenkins:
```
sudo systemctl start jenkins
```
Enable Jenkins:
```
sudo systemctl enable jenkins
```
Jenkins runs on port 8080 by default. Open a web browser and enter the IP address or hostname of your VM followed by port 8080 (e.g., http://your-vm-ip-address:8080). You should see the Jenkins setup wizard.Unlock Jenkins: Retrieve the initial administrator password to unlock Jenkins. You can find it in the following file:
```
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```
### Some Errors that i face and how i fix them:
#### Jenkins: 403 No valid crumb was included in the request
We came along this issue when we changed Jenkins to be accessible via a reverse proxy.
There is an option in the "Configure Global Security" that "Enable proxy compatibility"
This helped with my issue.
![image](https://github.com/YassineKADER/Tricks-Tips/assets/80207770/5bd35374-b570-40af-82b9-1bdfe65899e4)
#### Github or git not working
-try to install git in your vm <br>
-verify if you install the git plugin <br>
-add github credientials to jenkins user is your giithub username and password is your github acces token <br>
-if you use Bluue ocean try to replace the repo link with this link: `https://<PAT>@github.com/PATH_TO_YOUR_REPO` replace <PAT> with your access token
#### Permessions
  this problem you may faced when you try to use a command with root permessions inside a **stage** so to fix that:
  **Grant passwordless sudo access to the Jenkins user:** Run the command `sudo visudo` on your machine, Locate the line that grants sudo access to the Jenkins user, Add the following line below it to allow passwordless sudo access:
  ```
  jenkins ALL=(ALL) NOPASSWD: ALL
  ```
