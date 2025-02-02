# DynaPD: The 1st dynamic phishing kit dataset 

We crawled over 6k phishing kits, which cover over 2059 phishing kit families. The kits have been "de-weaponized": (i) we have replaced Telegram-based credential-sending code with email-based credential-sending code, and (ii) we have replaced the attacker’s email with an email address configurable by the dataset user.

## Installation Guide

---

### For Windows Users

1. Download the DynaPD phishing kit dataset from this [link](https://drive.google.com/file/d/1o2Hgr3SvtcsVsMiB4gnSafMezc_4FSLa/view?usp=sharing)
2. Download [XAMPP](https://www.apachefriends.org/), run installation
3. Move the downloaded DynaPD dataset to **xampp/htdocs**
   
   <img width="713" alt="1" src="https://github.com/user-attachments/assets/a43f6d14-b7e4-45c7-9663-6ae08a4ad36f" />

5. Edit the **Windows/System32/drivers/etc/hosts** file:

   For each subdomain, add the IP address **_127.0.0.1<space><subdomain>.localhost_** each on a new line.

   Note: This can be automated with a script. One script is included in the folder

   <img width="494" alt="2" src="https://github.com/user-attachments/assets/763f045e-4eb1-4366-8c8b-0044549a67bb" />


7. Edit the **C:/xampp/apache/conf/extra/httpd-vhosts.conf** file:

   For each phishing kit, add a tag
   ```
   <VirtualHost *:80>
     DocumentRoot <path_to_kit>
     Servername <subdomain_name>
   </VirtualHost *:80>
   ```

   The <subdomain_name> has to be consistent with what was created in the hosts file.

   Note: This can be automated with a script. One script is included in the folder

   <img width="430" alt="3" src="https://github.com/user-attachments/assets/231ced74-9a42-4f09-9579-e87bbc4cebe0" />


6. Start the server:
   
   Once the two files are correctly edited, you can start the localhost server by starting the Xampp application and clicking on Apache start button.

   <img width="386" alt="4" src="https://github.com/user-attachments/assets/57214cb3-abcc-44cc-b131-26054e514305" />

7. Visit the hosted kits at http://phishing.localhost

### For Linux Users

1. Download the DynaPD phishing kit dataset from this [link](https://drive.google.com/file/d/1o2Hgr3SvtcsVsMiB4gnSafMezc_4FSLa/view?usp=sharing)
2. Download [XAMPP](https://www.apachefriends.org/), run **xampp-linux-x64-8.0.28-0-installer.run**, the xampp will be installed in /opt/lampp
3. Edit **/opt/lampp/etc/httpd.conf**, uncomment this line
   ```
	# Virtual hosts
   Include etc/extra/httpd-vhosts.conf
   ```
4. Edit **/opt/lampp/etc/extra/httpd-vhosts.conf**, Add the following

   ```
   <VirtualHost *:80>
    DocumentRoot "phishing-kit"
    ServerName phishing.localhost
    <Directory "phishing-kit">
       Require all granted
    </Directory>
   </VirtualHost *:80>
   ```

5. Edit **/etc/hosts**, Add this line to host the phishing kits on localhost
```
127.0.0.1       phishing.localhost
```

6. Start lampp
```
sudo /opt/lampp/lampp start
```

7. Visit the hosted kits at http://phishing.localhost

## Notes

In the case where there are failures with starting the Apache server. 
You may want to look through the following areas

1. Ensure that port 80 and 443 are not in use. If these ports must be used elsewhere, there have to be additional configurations to change the ports for xampp
2. Ensure that in your automated script, spaces in paths are appropriately handled

In the case where you would want to change the location of the folder that stores the kit, 
some configuration is required to allow access to those folders from localhost.


## Citation
If you find our work useful, please consider citing our paper :)
```bibtex
@inproceedings {291106,
    author = {Ruofan Liu and Yun Lin and Yifan Zhang and Penn Han Lee and Jin Song Dong},
    title = {Knowledge Expansion and Counterfactual Interaction for {Reference-Based} Phishing Detection},
    booktitle = {32nd USENIX Security Symposium (USENIX Security 23)},
    year = {2023},
    isbn = {978-1-939133-37-3},
    address = {Anaheim, CA},
    pages = {4139--4156},
    url = {https://www.usenix.org/conference/usenixsecurity23/presentation/liu-ruofan},
    publisher = {USENIX Association},
    month = aug,
}
```
```

