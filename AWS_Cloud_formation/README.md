## What is AWS CloudFormation

AWS CloudFormation is an Infrastructure as Code(Iac) Service that allows you to define and Provision AWS infastructure using templates written in YAML or JSON. It helps automate the deployment and management of AWS resources in a repeatable and Scalable way.

## How is CloudFormation Different from other IaC Tools?

- **Native to AWS** - Deep integeration with AWS Services, unlike **Terraform**, which supports cloud providers.
- **State Management** - Unlike Terraform, which mantains a seperate state files, CloudFormation automatically tracks resources using AWS itself.
- **Free to use** - You only pay for the AWS resources provisioned; there is no seperate cost for using CLoudFormation.
- **Less Flexibility** - CloudFormation is AWS-specific, whereas tools like Terraform support hybrid cloud environments.

## Deploy your First EC2 Instance with CloudFormation

Follow these steps to set up an EC2 instance using AWS CloudFormation.

**Step 1:** Create a CloudFormation template.

Save the following YAML template as ec2-instance.yaml : 

```bash
AWSTemplateFormatVersion: '2010-09-09'
Description: 'CloudFormation Template to launch an EC2 instance'

Resources:
  MyEC2Instance:
    Type: AWS::EC2::Instance
    Properties:
      InstanceType: t2.micro
      ImageId: ami-0c55b159cbfafe1f0  # Replace with your region-specific AMI ID
      KeyName: my-key-pair  # Replace with your key pair name
      SecurityGroups:
        - default
      Tags:
        - Key: Name
          Value: MyFirstEC2

```
**Step 2:** Deploy the CloudFormation Stack

1) Go to AWS Console -> CloudFormation
2) Click Create stack -> With new resorces.

![Screenshot 2025-03-30 125646](https://github.com/user-attachments/assets/2b696b9d-794a-4e8d-a95e-4cf8957b9fe5)


3) Upload the ec2-instance.yaml template.

![Screenshot 2025-03-30 125741](https://github.com/user-attachments/assets/3c999216-0776-440b-a30c-e7ad5a5a6d4e)


You can View your Infra just click on View Infrastructure Composer.

![Screenshot 2025-03-30 124623](https://github.com/user-attachments/assets/80cab84a-028a-4beb-babe-05626d596b31)


4) Provide a stack name (eg, MyEC2Stack).

![Screenshot 2025-03-30 130054](https://github.com/user-attachments/assets/bc44f8f8-9817-4be9-b64e-e63c44171d5a)


5) Click Next and review the settings.
6) Click Create Stack.

**Step 3:** Verify the EC2 instance.

- Go to the EC2 Dashboard in AWS.
- Check if an instance with the tag MyFirstEC2 is running.

![Screenshot 2025-03-30 124728](https://github.com/user-attachments/assets/a14d3a7b-7202-4daf-b873-344e0fc23e41)

## You can update your Stack 

![Screenshot 2025-03-30 124846](https://github.com/user-attachments/assets/4d3543ac-eaf1-4357-841f-d697420da4bf)


## Deleting an AWS CloudFormation Stack

- Steps to Delete the CloudFormation Stack

    - **Go to the AWS Console** → Open **CloudFormation**.
    - **Find your stack** (e.g., `MyEC2Stack`).
    - Click on the **stack name** to open details.
    - Click **Delete** and confirm the action.

## What Happens?
- CloudFormation will **automatically** delete all resources it created, including the EC2 instance.
- If you created any resources manually (outside of CloudFormation), they **will not** be deleted.

![Screenshot 2025-03-30 124908](https://github.com/user-attachments/assets/d36d555b-36e7-4f9c-af50-7c0d48e66b19)

## Troubleshooting

💡 **If deletion fails:**
- Check if the instance has a manually attached volume or security group.
- Ensure you didn’t modify CloudFormation-managed resources manually.

---

Following these steps ensures a clean deletion of your AWS CloudFormation stack without leaving behind unused resources.
