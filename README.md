# AWS Syndicate for NodeJS - Serverless
## 1. Installation
```bash
pip install aws-syndicate
``` 
## 2. Create Project
```bash
syndicate generate project --name $project_name
```
## 3. Create config files
```bash
syndicate generate config
    --name                      $configuration_name   [required]
    --region                    $region_name          [required]
    --bundle_bucket_name        $s3_bucket_name       [required]
    --access_key                $access_key  
    --secret_key                $secret_key   
    --config_path               $path_to_store_config
    --project_path              $relative_path_to_project
    --prefix                    $prefix
    --suffix                    $suffix
    --extended_prefix           $extended_prefix_mode
    --use_temp_creds            $use_temp_creds #Specify,if use mfa or access_role
    --access_role               $role_name
    --serial_number             $serial_number
    --tags                      $KEY:VALUE
    --iam_permissions_boundary  $ARN
```
## 4. Export Config
```bash
# Unix
export SDCT_CONF=$path_to_store_config 
```
## 5. Create Lambda Function
```bash
syndicate generate lambda --name $lambda_function --runtime nodejs
```
### NodeJS lambda Structure 
```bash
    .
    ├── $project_path
    │   └── app
    │       └── lambdas
    │           ├── $lambda_name_1
    │           │   ├── deployment_resources.json
    │           │   ├── lambda_config.json
    │           │   ├── index.js
    │           │   ├── package.json
    │           │   └── package-lock.json
    │           └── $lambda_name_2
    │               ├── deployment_resources.json
    │               ├── lambda_config.json
    │               ├── index.js
    │               ├── package.json
    │               └── package-lock.json
    └── ...
```
## 6. Deployment
### Create S3 bucket for AWS Syndicate Artifacts
```bash
syndicate create_deploy_target_bucket
```
### Bulid Project Artifacts
```bash
syndicate build
```
### Deploy Project
```bash
syndicate deploy
```
### Clean Project from AWS
```bash
syndicate clean
```
