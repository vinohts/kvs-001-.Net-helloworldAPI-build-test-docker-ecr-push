💻 Local Environment
Tool	Version / Details
OS	Windows 11
PowerShell	7.0
.NET SDK	8.0
AWS CLI	Installed & configured (aws configure)
AWS Region	ap-south-1

🪜 STEP 1 — Create Project

In VS-Code
Example D:\
mkdir SimpleDotnet
cd SimpleDotnet
d:\SimpleDotnet
dotnet new webapi -n HelloWorldApi # Creates a folder helloWorldApi and generate the project
cd HelloWorldApi

d:\SimpleDotnet\HelloWorldApi

Test locally:

dotnet run

Visit → http://localhost:5000/swagger  port will differs depends on environment.

🐳 STEP 2 — Create Dockerfile
⚙️ Step 3: Build and Run Docker Image Locally
      docker build -t helloworldapi .
      docker run -p 3535:8585 helloworldapi
      
  Test http://localhost:8585/swagger 

  🪣 Step 4: Create ECR Repository (in AWS)


  aws ecr create-repository --repository-name helloworldapi --region ap-south-1

  123456789012.dkr.ecr.ap-south-1.amazonaws.com/helloworldapi

  🔐 Step 5: Authenticate Docker with ECR


aws ecr get-login-password --region ap-south-1 | docker login --username AWS --password-stdin 123456789012.dkr.ecr.ap-south-1.amazonaws.com



📦 Step 6: Tag and Push Image to ECR

docker tag helloworldapi:latest 123456789012.dkr.ecr.ap-south-1.amazonaws.com/helloworldapi:latest
docker push 123456789012.dkr.ecr.ap-south-1.amazonaws.com/helloworldapi:latest

Check images in ECR:

aws ecr list-images --repository-name helloworldapi --region ap-south-1



Manually Create ECS Cluster and practice 













  




