# Build and push Docker image automatically to ECR from GitHub

To push GitHub code to Amazon ECR (Elastic Container Registry) automatically whenever new code is added to GitHub, you can set up a GitHub Actions workflow. Below is a basic workflow example to achieve this:

**1. Set Up Amazon ECR:**
First, ensure you have an Amazon ECR repository set up where you want to push your Docker images.

**2. Set Up GitHub Secrets:**
You'll need to store your AWS credentials securely in GitHub Secrets to access your Amazon ECR repository. Go to your GitHub repository > Settings > Secrets and add the following secrets:

- **AWS_ACCESS_KEY_ID:** Your AWS Access Key ID.
- **AWS_SECRET_ACCESS_KEY:** Your AWS Secret Access Key.
- **AWS_REGION:** The AWS region where your ECR repository is located.
- **ECR_REPOSITORY:** The name of your ECR repository.

**3. Create GitHub Actions Workflow:**
In your GitHub repository, create a directory **`.github/workflows`** if it doesn't exist already. Inside this directory, create a YAML file (e.g., **`ecr_push.yml`**) for your workflow

Make sure to replace placeholders like **`${{ secrets.AWS_REGION }}`**, **`${{ secrets.ECR_REPOSITORY }}`**, etc., with your actual values.

**4. Commit and Push:**
Commit the changes to your GitHub repository. The GitHub Actions workflow will be triggered automatically whenever new code is pushed to the specified branch (in this case, the main branch).

This workflow will build a Docker image from your repository's Dockerfile, tag it with the ECR repository URI, and then push it to your Amazon ECR repository whenever there's a new push to your specified branch.
