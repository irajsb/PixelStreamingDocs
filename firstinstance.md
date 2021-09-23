### First step to make a pixel streaming solution is to make a base image that we can launch instances from.  

## Start an instance 
- Login to your aws account.

- Open EC2 Menu.
  
- Make sure you have desired region selected.  

- Click launch instances.
  
- Select your desired base image (there are images with drivers pre installed make sure to watch software cost before launching , official NVIDIA and AMD images usually have 0.0$ software cost I'm using NVIDIA Gaming PC - Windows Server 2019 for this example ). 

- Choose instance type (I'm chosing g4dn for this example).

- We can skip `3. Configure Instance` step but you can change it as desired.

- Add storage : storage cannot be less than base AMI size which in this case is 30GB , storage type has a major impact on instance startup time. some storage types have fees as high as 2000$/month so be sure to calculate your price estimate by using aws calculator (googleit) . I'm just changing gp2 to gp3 here for this example.

- You can choose to add tags now or do it later (I recommend using key `Name` and value `ProjectBaseImage` for clarification .

- You need to open some ports in pixel streaming security group. this is the config that we currently have:  
![](https://docs.pixelsteam.net/Images/Ports.jpg)

- Next you need to review and provide a key pair . key pairs are needed for logging in instances if you don't have one open a new tab and create one (key pairs are given to you only once so be sure to store it somewhere or it will be lost forever).

## Setup Instance
- Login to instance using your keypair (may be a little tricky for NVIDIA image I've to try many times to login). Be sure to store your password since it will be password for your images too !

- Paste folder proivded to you to C:\  .  

- Open `C:\PixelStreamer\Downloads` .

- Download project folder as zip and place it in this folder . Make sure there is only one zip file in this directory . Make sure that root of your zip file is WindowsNoEditor(or Windows Folder in recent UE versions) and there is an executable file inside that folder . (you can also use Downloader script to download your file from a direct link).

- Run `UE4-Pixel-Streamer-Bootstrap` as admin it will install node,extract project, add firewall rules ,and add Startup script to the system startup .

-Install prerequisites (usually located in extra folder inside project folder) you may see that dotnet 3.5 install has failed you may ignore this since its optional for most projects.

- [Optional] You can uncomment lines in startup.ps1 script that runs multiple instances of pixel streaming if you need (and your project is efficient enough to do so) , instances can be accessed in this order `https://your-instance-ip-address.server.pixelsteam.net:443 https://your-instance-ip-address.server.pixelsteam.net:444 https://your-instance-ip-address.server.pixelsteam.net:446 https://your-instance-ip-address.server.pixelsteam.net:447 ` note that 445 port is used by another service by default so we skip that .

- Run startup script verify that app runs as expected 

- Go to aws console reboot instance after 20-30 secs you should access your instance without logging in  (using url example that we provided in the step before ) if everything is done correctly!

## Make an Image template 

- Right click your instance in aws console and click create image. 

-  options are good enough so we finalize creating image.

- Click on AMI option located in the menu on the left and wait until your image is created.

- Terminate your base instance since we will not be needing it anymore.


 
