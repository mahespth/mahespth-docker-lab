In this lesson, we begin working with Terraform commands. We will start by creating a very simple Terraform file that will pull down the an image from Docker Hub.

List the Terraform commands:

terraform

Common commands:
apply: Builds or changes infrastructure
console: Interactive console for Terraform interpolations
destroy: Destroys Terraform-managed infrastructure
fmt: Rewrites configuration files to canonical format
get: Downloads and installs modules for the configuration
graph: Creates a visual graph of Terraform resources
import: Imports existing infrastructure into Terraform
init: Initializes a new or existing Terraform configuration
output: Reads an output from a state file
plan: Generates and shows an execution plan
providers: Prints a tree of the providers used in the configuration
push: Uploads this Terraform module to Terraform Enterprise to run
refresh: Updates local state file against real resources
show: Inspects Terraform state or plan
taint: Manually marks a resource for recreation
untaint: Manually unmarks a resource as tainted
validate: Validates the Terraform files
version: Prints the Terraform version
workspace: Workspace management

Set up the environment:

mkdir -p terraform/basics
cd terraform/basics

Create a Terraform script:

vi main.tf

main.tf contents:

# Download the latest Ghost image
resource "docker_image" "image_id" {
  name = "ghost:latest"
}

Initialize Terraform:

terraform init

Validate the Terraform file:

terraform validate

List providers in the folder:

ls .terraform/plugins/linux_amd64/

List providers used in the configuration:

terraform providers

Terraform Plan:

terraform plan

Useful flags for plan:
-out=path: Writes a plan file to the given path. This can be used as input to the "apply" command.
-var 'foo=bar': Set a variable in the Terraform configuration. This flag can be set multiple times.

Terraform Apply:

terraform apply

Useful flags for apply:
-auto-approve: This skips interactive approval of plan before applying.
-var 'foo=bar': This sets a variable in the Terraform configuration. It can be set multiple times.

Confirm your apply by typing yes. The apply will take a bit to complete.

List the Docker images:

docker image ls

Terraform Show:

terraform show

Terraform Destroy:

terraform destroy

Confirm your destroy by typing yes.

Useful flags for destroys:
-auto-approve: Skip interactive approval of plan before applying.

Re-list the Docker images:

docker image ls

Using a plan:

terraform plan -out=tfplan

Applying a plan:

terraform apply tfplan

Show the Docker Image resource:

terraform show

Destroy the resource once again:

terraform destroy
