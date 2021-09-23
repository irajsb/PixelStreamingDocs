First step to make a pixel streaming solution is to make a base image that we can launch instances from.  

## Start an instance 
- Login to your aws account.

- Open EC2 Menu.
  
- Make sure you have desired region selected.  
- Click launch instances.  
- Select your desired base image (there are images with drivers pre installed make sure to watch software cost before launching , official NVIDIA and AMD images usually have 0.0$ software cost I'm using NVIDIA Gaming PC - Windows Server 2019 for this example ). 
- Choose instance type (I'm chosing g4dn for this example).
- We can skip `3. Configure Instance` step but you can change it as desired 
- Add storage : storage cannot be less than base AMI size which in this case is 30GB , storage type has a major impact on instance startup time. some storage types have fees as high as 2000$/month so be sure to calculate your price estimate by using aws calculator (googleit) . I'm just changing gp2 to gp3 here for this example.
- You can choose to add tags now or do it later (I recommend using key `Name` and value `ProjectBaseImage` for clarification 
- You need to open some port in pixel streaming security group this is the config that we currently have
- Next you need to review and provide a key pair . key pairs are needed for logging in instances if you don't have one open a new tab and create one (key pairs are given to you only once so be sure to store it somewhere or it will be lost forever)
