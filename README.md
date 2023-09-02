# php-compilation

# PHP compile from source

Download PHP: https://www.php.net/downloads.php

Ex: wget https://www.php.net/distributions/php-7.2.34.tar.gz

Required Packages: openssl-devel, curl-devel, 

# For Amazon Linux 2023: 

yum groupinstall "Development Tools"

yum install libxml2-devel libjpeg-devel libpng-devel freetype-devel libmcrypt-devel

# Note

In Amazon Linux 2023, openssl version is more updated like 3.0.8 so php-7.2.34 isn't compatible with it's RSA algorithm. So need to remove default openssl latest version then have to compile openssl version 1.1.1k or 1.1.1t using source file. 

# To compile openssl from source in Amazon Linux 2023

Remove default openssl: dnf remove openssl

Download openssl: wget https://www.openssl.org/source/openssl-1.1.1k.tar.gz

$ tar -xzf openssl-1.1.1k.tar.gz

$ cd openssl-1.1.1k/

$ ./config

$ make 

$ make installl 

$ $ ldd /usr/local/bin/openssl

$ ls /usr/local/lib64

$ cd /etc/ld.so.conf.d

$ vi dyninst-x86_64.conf

Add /usr/local/lib64 in this file.

$ ldconfig

$ openssl version

$ cd /root/php-7.2.34

$ ./configure --prefix=/opt/php7.2.23 --with-config-file-path=/etc/php-7.2.34 --enable-mbstring --enable-zip --enable-bcmath --enable-pcntl --enable-fpm --enable-exif --enable-calendar --enable-sysvmsg --enable-sysvsem --enable-sysvshm --enable-wddx --with-curl --with-mysqli --with-gd --with-jpeg-dir --with-png-dir --with-zlib --with-freetype-dir --with-openssl --with-xmlrpc --with-libdir=lib64 --enable-soap --with-pear --enable-intl

