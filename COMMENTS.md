# Step 1 - Requirements
- Nginx accepts requests on 80 & 443
- HTTP redirects successfully to HTTPS
- Used provided certificate files and set correct permissions
- Nginx proxies requests through the upstream directive

### Configuring nginx:
```
- Create upstream group (ran into issues here specifically because I'm accustomed to using localhost rather than 127.0.0.1 which is what the python script is expecting)
- Setup 301 permanent redirect to https
- Setup 443 listener, configure suggested SSL settings per cipherli.st -- Noticed that the version of nginx that the centos image uses does not support TLS1.3 so removed that from the protocol list
- Configured all necessary proxy_set_headers and eventually pass to upstream
```

# Step 2 - Requirements:
- Nginx is installed successfully
- Ansible copies all files to the expecting directories
- Appropriate file permissions are set for all files (to my preferences)
- Unzips contents to /opt/application/
- sample-app.service is configured to run as systemd
- Starts nginx and sample-app services
- Prints "Pass" on all four tests

### Configure playbook.yml
```
- Install nginx and other dependencies (python, openssl and unzip)
- Move nginx.conf file created in step 1 to expecting directory
- Created and moved the systemd .service file for the node application into the expecting directory
- Moved keys to expecting directory
- Invoke unzip and place application files in /opt/
- Start both app and nginx services

I don't use Ansible in production, so I would appreciate some guidance on the preferred format for these playbook files with regards to includes.
```
