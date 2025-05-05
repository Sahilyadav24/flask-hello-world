
# flask-hello-world
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

<img width="950" alt="Screenshot 2025-05-06 014006" src="https://github.com/user-attachments/assets/51233c23-17c4-4452-a167-759ea7023115" />
<img width="941" alt="Screenshot 2025-05-06 015103" src="https://github.com/user-attachments/assets/fe74e851-becf-4178-989f-366036445254" />
<img width="929" alt="Screenshot 2025-05-06 014039" src="https://github.com/user-attachments/assets/e07ad8db-f49e-4258-8ee6-cd01bd00e181" />
<img width="948" alt="Screenshot 2025-05-06 013824" src="https://github.com/user-attachments/assets/acead5a1-477b-4c00-8b96-4efab7cf1347" />
<img width="274" alt="Screenshot 2025-05-06 013751" src="https://github.com/user-attachments/assets/7624a227-9ef2-4825-9cf8-24e41c11249b" />


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
