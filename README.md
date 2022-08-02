# A step-by-step setup of NGinx installed on GCP VM and GitHub repo pulled in /var/www/html folder #
## GCP Cloud Storage, Kubernetes, and more ##

### Setting up GCP ###

1. Create GCP account and navigate to the dashboard
2. Go to: Compute Engine > VM Instances
3. Enable API
4. Create new instance with the following settings:
  * Name: {any name}
  * Region: ANY
  * Zone: ANY
  * Series: E2 (recommended)
  * Machine Type: Micro/Small/Medium (recommended)
  * Firewall: Allow both HTTP and HTTPS traffic
  * Management/Automation/Startup script:
      * sudo apt update
      * sudo apt install nano
      * sudo apt install nginx
5. Your VM is ready


### Access your VM from local Terminal ###

1. From the GCP Dashboard navigate to: Compute Engine > VM Instances (you will see your newly created VM)
2. On your VM, under the connect tab, click on the arrow and select 'Open in browser window'
3. Run the following commands:
  * sudo apt-get update
  * sudo apt-get install nginx
4. Run: * sudo systemctl status nginx * to verify the nginx installation
5. Copy the username that is displayed in the console
  ** Note: It will be in the format ###@...:~$ (you need to copy the part before the @ sign) and it will be green
  e.g. if this is displayed in your console: 'example.com@vminstance:$' then copy the 'example.com' part
6. Close the browser console and navigate to your local environment
7. Create a new folder (where you will host the GCP keys) and open a terminal at the folder
8. Run the following commands:
  * pwd (and copy the output)
  * Use the command: ssh-keygen -t rsa -b 4096 -C "the part you copied from STEP 5" -f the/path/that/you/copied/from/above OR puttygen software to generate ssh keys in the folder you created
9. Copy the content of your key.pub (public key)
10. Go to the VM instances in the GCP and click on your VM instance
11. Click on Edit
12. Under Security and Access/SSH Keys click add item and paste your public SSH key
13. Click save
14. From the GCP console copy the external IP address of your VM and go back to your local terminal
15. Run: ssh -i {name of your SSH key} {GCP username from part 5}@{External IP of your VM} 
16. You are now logged in to your VM from your local terminal


### Pull GitHub repository in the /var/www/html/ folder ###

1. Access your VM through terminal
2. Run: cd ../../var/www/html/


### Configure the NGinx server and setup reverse proxy ###

TBC


### Cloud Storage Bucket ###

TBC


