Pre-Requisites
Terraform client installation: https://www.terraform.io/downloads
Cloud Provider account: https://console.cloud.google.com/


Initial Setup
For this course, we'll use a free version (upto EUR 300 credits).

1.Create an account with your Google email ID

2.Setup your first project if you haven't already
eg. "DTC DE Course", and note down the "Project ID" (we'll use this later when deploying infra with TF)

3.Setup service account & authentication for this project
    Grant Viewer role to begin with.
    Download service-account-keys (.json) for auth.


4.Download the Google Cloud SDK installer script:
https://cloud.google.com/sdk/docs/quickstart


Set environment variable to point to your downloaded GCP keys:
export GOOGLE_APPLICATION_CREDENTIALS="<path/to/your/service-account-authkeys>.json"

# Refresh token/session, and verify authentication
gcloud auth application-default login


Setup for Access
IAM Roles for Service account:

Go to the IAM section of IAM & Admin https://console.cloud.google.com/iam-admin/iam
Click the Edit principal icon for your service account.
Add these roles in addition to Viewer : Storage Admin + Storage Object Admin + BigQuery Admin
Enable these APIs for your project:

https://console.cloud.google.com/apis/library/iam.googleapis.com
https://console.cloud.google.com/apis/library/iamcredentials.googleapis.com
Please ensure GOOGLE_APPLICATION_CREDENTIALS env-var is set.

export GOOGLE_APPLICATION_CREDENTIALS="<path/to/your/service-account-authkeys>.json"


Starting the Terraform

# Refresh service-account's auth-token for this session
gcloud auth application-default login

# Initialize state file (.tfstate)
terraform init


terraform plan -var="project=<your-gcp-project-id>"


terraform plan -var="project=de-project-388007"



# Create new infra
terraform apply -var="project=<your-gcp-project-id>"

# Delete infra after your work, to avoid costs on any running services
terraform destroy

