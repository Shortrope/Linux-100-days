# Install Nginx
http://nginx.org/en/linux_packages.html

Centos 7

Cretae repo file for nginx

    vim /etc/yum.repos.d/nginx.repo

    [nginx]
    name=nginx repo
    baseurl=http://nginx.org/packages/centos/7/$basearch/
    gpgcheck=0
    enabled=1

Update and install

    yum update
    yum install nginx
    systemctl start nginx
    systemctl enable nginx