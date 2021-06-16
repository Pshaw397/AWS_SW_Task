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
5. Change the file permissions by selecting the file you wish to share
- Move to the permission tab
- Press the edit button
- Tick the read buttons for `Everyone (public access)`
- Save changes
