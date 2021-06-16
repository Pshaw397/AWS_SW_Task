# AWS_SW_Task

1. After creating and EC2 instance and ssh-ing into it, you need to first download the required dependencies:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install python
sudo apt-get install python-pip
sudo apt-get install awscli
```
2. Next, you need to configure your aws so you can connect to the s3
- Use the command: `aws configure`
- Then input your access key and secret access key into the specific field
- Set "Default region name" to `eu-west-1`
- Set "Default output format" to `json`
- To make sure you're connected, use `aws s3 ls` to display the buckets in the s3

3. Next, create a bucket buy using `aws s3 mb s3://[bucket name]`
4. Create a file in your local directory, then transfer that to the buck by doing: `aws s3 cp [file name] s3://[bucket name]`
5. Change the file permissions by selecting the bucket
- Move to the permission tab
- Move down to the ACL section
- Press the edit button
- Tick the read buttons for `Everyone (public access)`
- Save changes
Additionally, you should change you bucket policy to:
```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::[BUCKET  NAME]/*"
        }
    ]
}
```
Changing [BUCKET NAME] to the name of your bucket

Additional commands:
- `aws s3 sync s3://[bucket name]/ [file name]` - downloads a folder with the stated file inside, from the stated bucket 
- `aws s3 rm s3://[bucket name]/[file name]` - removed the stated file from the stated bucket
- `aws s3 rb s3://[bucket name]` - removes the stated bucket
