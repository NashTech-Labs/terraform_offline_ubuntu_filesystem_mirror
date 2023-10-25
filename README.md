# terraform_offline_ubuntu_filesystem_mirror

## Initialize Terraform offline with Filesystem mirror

Run Terraform init without an internet connection for Ubuntu users, we can run the command through the cache from .terraformrc file. 

## Step 1: 
Create a directory in your system. 
```
mkdir "$HOME/tf_cache"
```
Now simply copy the registry.terraform.io folder here. This configuration helps you to run terraform init without internet connection

## Step 2: 
Create this file inside above directory. Create ".terraformrc".

```
provider_installation {
  filesystem_mirror {
    path = "/home/knoldus/tf_cache"
    include = ["registry.terraform.io/hashicorp/*"]
  }
  direct {
    exclude = ["registry.terraform.io/hashicorp/*"]
  }
}
plugin_cache_dir = "home/knoldus/tf_cache"
disable_checkpoint=true
```

## Step 3: 
Setup env variables as follows
  
  ```
for Ubuntu
export TF_PLUGIN_CACHE_DIR="c:/tf_cache"
export TF_CLI_CONFIG_FILE="c:/tf_cache/terraform.rc"
  ```

## Step 4: 
Now just run 
```
terraform init
  ```
It will take the cache from the registry.terraform.io in tf_cache directory


