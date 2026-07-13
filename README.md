# bedrock-map-tagging
Bedrock model agnostic MAP tagging is available. The official guidance is per [link](https://docs.aws.amazon.com/MAP/latest/userguide/bedrock-map-tagging.html#bedrock-map-tagging-iam-principal)

# operation process
1. check with customer what specific ways are they using in terms of calling Bedrock models
   - Bedrock API Key
   - IAM User with attached IAM policies
   - IAM Role with attached IAM policies

2. Choose the corresponding ways of tagging according to customer's specific ways of calling bedrock models
   - Bedrock API Key
     Find corresponding **IAM user of the Bedrock API Key in IAM console**, and tag this IAM user by
     ```sh
     aws iam tag-user --user-name MyBedrockUser --tags "Key=map-migrated,Value=migYOUR_MPE_ID"
     ```
     and run the below cmd to check that the IAM user has been correctly tagged
     ```sh
     aws iam list-user-tags --user-name MyBedrockUser
     ```
     if correctly tagged, the output should include:
      ```txt
      {
        "Tags": [
          {
            "Key": "map-migrated",
            "Value": "mig123456789"
          }
        ]
      }
      ```
   - IAM User with attached IAM policies
     Find corresponding IAM user in IAM console, and tag this IAM user by
     ```sh
     aws iam tag-user --user-name MyBedrockUser --tags "Key=map-migrated,Value=migYOUR_MPE_ID"
     ```
     and run the below cmd to check that the IAM user has been correctly tagged
     ```sh
     aws iam list-user-tags --user-name MyBedrockUser
     ```
     if correctly tagged, the output should include:
      ```txt
      {
        "Tags": [
          {
            "Key": "map-migrated",
            "Value": "mig123456789"
          }
        ]
      }
      ```     
   - IAM Role with attached IAM policies
     Find corresponding IAM role in IAM console, and tag this IAM role by
     ```sh
     aws iam tag-role --role-name MyBedrockRole --tags "Key=map-migrated,Value=migYOUR_MPE_ID"
     ```
     and run the below cmd to check that the IAM role has been correctly tagged
     ```sh
     aws iam list-role-tags --role-name MyBedrockRole
     ```
     if correctly tagged, the output should include:
      ```txt
      {
        "Tags": [
          {
            "Key": "map-migrated",
            "Value": "mig123456789"
          }
        ]
      }
      ```

3. Activate the tag in Billing and Cost Management console referring this [link](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/activating-tags.html)

