This code will install matrix-mxisd on your server & get an certificates from `letsencrypt.org` for your domain, and set a cron job to renew the certificates.

**Tested:**  
 - Ubuntu Xenial (16.04)

**Minimum Requirements:**
 - Ubuntu >= 16.04
 - Vagrant >= 1.7.0 (If your staging server is vagrant, if not, this is not applicable)
 - ansible >=2.0

**Be mindful you need to set the variables before running the script; the variables are to be set in the ansible-jitsi/main.yaml file**

  - Path to install mxisd (Change if you don't have root password or want to install elsewhere); NOTE: You still need to be a sudoer to use this script.
    - path: path/for/mxisd/file
  - URL from where mxisd will be download. (Please check for the latest version)
    - urlToDownloadDebFile: url://to.download.mxisd
  - Nginx File for configuration (Most probably you want to edit present in `files/nginx.conf` not the path to it.)
    - matrixConfFileToSend: location/to/nginx/file
  - Port you want to hit (You might want to change this if multiple services are running un the same domain Sample www.YOUR_AWESOME_DOMAIN.com:PORTNUMBER)
    - portForRiot: NUMBER
  - This is a sample value, enter your domain; sample: www.YOUR_AWESOME_DOMAIN.com
    - hostname: www.YOUR_AWESOME_DOMAIN.com
  - Email is required if you plan to use letsencrypt for https (secure) connection.
    - letsencrypt_email: YOUR@AWESOME_EMAIL.COM

**How to run:**
  1. Install Ansible
  2. Add your server group in the inventory.
  3. Change the `hosts` from `all` to the server group in which you want to install jitsi. (In file ansible-Jitsi/main.yaml)
  4. Make sure you have set the variables you desire for installation. (In file ansible-Jitsi/defaults/main.yaml)
  5. Run the following command (from inside the ansible-Jitsi folder): `ansible-playbook main.yaml --ask-become`

- mxisd: https://github.com/kamax-io/mxisd/
- letsencrypt: https://letsencrypt.org/
- Ansible: https://www.ansible.com

**Feel free to contribute in this Repository or open an issue.**
