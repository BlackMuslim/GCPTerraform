# GCP Terraform Authentication


**Step 1: Create a Service Account***

- Log in to your Google Cloud Platform (GCP) account.
- In the search bar, type "Service Accounts" and select it.

![service accounts](https://github.com/BlackMuslim/GCPTerraform/assets/144186877/02c25b5a-3cea-4473-a2e8-25684a3af9ee)


**Step 2 Service Account**
- Click on "Create Service Account" and fill in the required details (name and description).

<img src="https://github.com/mindmotivate/GCP_Terraform/assets/130941970/4094e37f-f1a5-4ca5-84b6-07e14fe4073e" alt="Image20240421175752" width="50%">

- Click "Create" and continue. Grant the service account permissions by selecting a role (e.g., Owner or Editor). Then Select Done

![roles](https://github.com/BlackMuslim/GCPTerraform/assets/144186877/62ad8b9d-c6c7-4192-85ab-f48b2c4534d8)


**Step 3 Creating the key**
- You will see there is no key, in order for terraform to connect with your GCP account you will first need a Key.

![no keys](https://github.com/BlackMuslim/GCPTerraform/assets/144186877/6d4446ce-b8bf-423f-ac06-a826fa4eaeef)


- You must create a key click on the new Editor account you just made. 
- Under Keys you will see add key select this. 
- Use the JSOn file type.

![keys](https://github.com/BlackMuslim/GCPTerraform/assets/144186877/9587d27d-6759-40f8-838b-8d514bf4408d)


- GCP will create a key and auto download for you.

![key downloaded](https://github.com/BlackMuslim/GCPTerraform/assets/144186877/47d4c3aa-2965-42e8-ae55-baa999e931cb)



**Step 4: Connect Terraform**

- Go to the Terraform Providers page on the Terraform website.
- Select Google Cloud Platform (GCP)
- Click "Use Provider" to copy the provider configuration code. 

![providercode](https://github.com/BlackMuslim/GCPTerraform/assets/144186877/3c655f65-eb21-4711-b96a-491f151230f3)


**Step 5: Set Up Terraform Project**

1. Open Visual Studio Code and create a new Terraform project.
2. Create a directory structure (e.g., `terraform/GCP/Humzamaroc`) and open it in Visual Studio Code.
3. Create a new file named `main.tf` and paste the copied provider configuration code into it.

![Screenshot 2024-04-21 120856](https://github.com/BlackMuslim/GCPTerraform/assets/144186877/dbd54912-4759-4ec8-afc6-a9c4c75fb250)


4. Move the downloaded JSON key file to the workspace directory in Visual Studio Code.

**Step 6: Configure Terraform**

1. In the `main.tf` file, specify the following parameters:
   - `project`: The GCP project ID (found in the JSON key file).
   - `region`: The GCP region where resources will be deployed (e.g., `us-central1`).
   - `credentials`: The file name of the JSON key file.

![Screenshot 2024-04-21 122201](https://github.com/BlackMuslim/GCPTerraform/assets/144186877/5077f57f-d676-4943-985f-0f74fc0551b9)


**Step 7: Terraform Commands**

1. Use the terminal in Visual Studio Code to run Terraform commands:
   - `terraform validate`: Authenticate with GCP and validate the Terraform configuration.
   - `terraform plan`: Check the plan for deploying resources.
   - `terraform apply`: Apply the `main.tf` configuration to GCP and create a Terraform state file.
  
![Screenshot 2024-04-21 124954](https://github.com/BlackMuslim/GCPTerraform/assets/144186877/100022bd-2ca4-4961-a3f2-3c39d3802849)



![terra apply](https://github.com/BlackMuslim/GCPTerraform/assets/144186877/8bb172ff-6f54-41e4-989e-494ee5dc8481)




**Step 8: Create a GCS Bucket**

1. Go to the Terraform Registry documentation and search for "Cloud Storage."
2. Copy the code for creating a GCS bucket and paste it into the `main.tf` file below the credentials configuration.

![Screenshot 2024-04-21 130553](https://github.com/BlackMuslim/GCPTerraform/assets/144186877/0db9ec42-3728-4a77-84a4-f51a3cf9161b)



**Step 9: Save and Apply Changes**

1. Save the `main.tf` file.
2. Run `terraform validate`, `terraform plan`, and `terraform apply` to authenticate with GCP, check the plan, and apply the configuration, respectively.

By following these steps, you can authenticate Terraform with GCP, configure a Terraform project, and deploy resources such as a Google Cloud Storage bucket using Terraform.

***This is your bucket Code:***


```hcl
resource "google_storage_bucket" "static-site" {
  name          = "image-store.com"
  location      = "EU"
  force_destroy = true

  uniform_bucket_level_access = true

}
```




