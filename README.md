# DynaPD: The 1st dynamic phishing kit dataset 

We crawled over 6k phishing kits, which cover over 2059 phishing kit families. The kits have been "de-weaponized": (i) we have replaced Telegram-based credential-sending code with email-based credential-sending code, and (ii) we have replaced the attacker’s email with an email address configurable by the dataset user.

## Installation Guide

---

### For Windows Users

1. Download the DynaPD phishing kit dataset from this [link](https://drive.google.com/file/d/1o2Hgr3SvtcsVsMiB4gnSafMezc_4FSLa/view?usp=sharing)
2. Download [XAMPP](https://www.apachefriends.org/)
3. Move the downloaded DynaPD dataset to **xampp/htdocs**
4. Edit the **Windows/System32/drivers/etc/hosts** file:

   For each subdomain, add the IP address **_127.0.0.1<space><subdomain>.localhost_** each on a new line.

   Note: This can be automated with a script. One script is included in the folder

5. Edit the **xampp/apache/conf/extra/httpd-vhosts.conf** file:

   For each phishing kit, add a tag

```
<VirtualHost *:80>
  DocumentRoot <path_to_kit>
  Servername <subdomain_name>
</VirtualHost *:80>
```

The <subdomain_name> has to be consistent with what was created in the hosts file.

Note: This can be automated with a script. One script is included in the folder

6. Start the server:
   Once the two files are correctly edited, you can start the localhost server by starting the Xampp application and clicking on Apache start button. 


### For Linux Users
