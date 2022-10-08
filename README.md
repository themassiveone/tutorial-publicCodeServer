# tutorial-publicCodeServer

### Status

##### Complete

- VM Hosting
- Ssh Configuration on Macos
- VsCode over SSH

##### Incomplete

- Http vsCode using [code-server](https://github.com/coder/code-server)
- Ssh Configuration on Windows

## About

In here i will show you how to create a (vs)code server accessible over ssh or http hosted on Oracle Cloud Always Free Resources.

### Requirements

- Credit Card (will not be charged)
- free OCI Account registration (takes 5 min)
- Depending on how familiar you are with these steps, it will take about 30min to 5hours of time to recreate those steps

## Step 1: Create Compute Instance

1. Go to https://cloud.oracle.com/.
2. Log into Oracle Cloud using its Identity Managing System ![login image](/media/login.png)
3. Access OCI Sidebar and go to Instances ![sidebar](/media/ociSidebar.png)
4. If you have less than 2 Instances running, your are eligible to create a free instance, if you choose the correct settings. Click on Create
5. Call it appropriately
6. Make sure the selected Availability Domain is Always Free eligible within the Placement section ![availability domain](/media/availabilityDomain.png)
7. Locate the _Image and shape_ section. Change the OS Image to the OS most familiar to you. We are going to go with Ubuntu 22.04. Be aware that any other changes might not work with Always Free-eligible status. ![platformImage](/media/platformImage.png)
8. Download the then generated private key in the _Add SSH keys_ section
   ![download key](/media/downloadKey.png)
9. Leave everything else as is and click on the **Create** button at the bottom of the page

## Step 2: Setup ssh connection to your instance

<details>
  <summary>For MacOS users</summary>
  
  1. Deposit the private key file in 
  ```~/.ssh/```
  2. Change Permissions in order to use your private key when connecting via ssh
  ```chmod 400 ~/.ssh/yourKeyFileName.key```
  2. Edit your ssh config file located at 
  ```code ~/.ssh/config```
  3. Fetch your instances public IP from Oracle Cloud Infrastructure ![fetchPublicIP](/media/fetchPublicIP.png)
  4. Add the follwing lines to your config
  ```
  Host *callMeWhatever*
    HostName *insert ip here*
    User ubuntu
    IdentityFile /Users/*username*/.ssh/*keyFileName*.key
  ```

5. Connect to your host like this:
   ![selfSignedCertificate](/media/selfSignedCertificate.png)
   You will need to type _yes_ in order to accept, that your VM is currently using a self signed certificate to identify itself. At this point you should be connected to your instance.

</details>

<details>
  <summary>For Windows users</summary>
</details>

## Step 3: Setup VSCode over SSH

1. Download VsCode
2. Install the VsCode Extension **Remote - SSH**
   ![extension](/media/extension.png)
3. Click on the remote Button at the bottom left of VsCode
   ![remoteSshButton](/media/RemoteSshButton.png)
4. Choose your configuration Name, that you choose when editing your ssh config
5. (optionally) choose linux as the operating system type. This dialog happens occasionally.
6. Now you should be connected to your Oracle instance using VsCode. Open the terminal in vscode and type in some command to test if your vm is responsive
   ![testLs](/media/testLs.png)
