![image](https://github.com/user-attachments/assets/9828ccc2-e8c5-4215-ae38-301e7dac0d6c)# flask-hello-world
# Flask Jenkins CI/CD on AWS (with IAM Role)

This project sets up an automated CI/CD pipeline on AWS using Jenkins, Flask, and GitHub.

## Architecture
- **EC2 (Ubuntu)** → Jenkins + Flask app
- **GitHub** → Source repository
- **IAM Role** → Secure AWS access (S3)

## Steps
1. Launch EC2 instance (Ubuntu 22.04)
2. Install Python, Git, Jenkins
3. Attach IAM Role (EC2-Jenkins-Flask-Role)
4. Install AWS CLI & test role
5. Setup Jenkins Freestyle project
6. Configure GitHub webhook
7. Deploy Flask app

![image](https://github.com/user-attachments/assets/90335bdf-0191-4a6c-bfb8-0c0c30119317)
<img width="387" alt="result" src="https://github.com/user-attachments/assets/55920917-6493-4a09-8c66-a4d40af0b849" />

http://13.203.222.243:5000/

## IAM Role Permissions
- **AmazonS3FullAccess** → Upload deployment logs
- **CloudWatchAgentServerPolicy** (optional) → Stream logs

## How automation works
1. Developer pushes code to GitHub
2. Webhook triggers Jenkins job
3. Jenkins:
   - Pulls code
   - Installs dependencies
   - Restarts app
   - Uploads logs to S3
4. App runs at http://<EC2-ip>:5000

## Security
- Jenkins secured by restricting port 8080 to IP
- AWS access secured using IAM Role (no hardcoded keys)

⚡ Optional Improvements
- **Dockerize Flask app** → Portability
