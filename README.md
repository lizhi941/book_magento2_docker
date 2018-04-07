# My Awesome Book

This file file serves as your book's preface, a great place to describe your book's content and ideas.

测试一下，能不能上传,再次测试，再次测试，再次测试

**该官方镜像缺少magento需要的一些插件：**

通过 运行magento223的安装程序：

可以看出 缺少的插件为 ：PHP Extension mcrypt，PHP Extension xsl，PHP Extension intl，PHP Extension pdo\_mysql，PHP Extension soap， PHP Extension zip , PHP Extension gd.经过查看对应的官网php-7.1.16 源码，以上缺少均是官方插件

现在需要在官方镜像 **php:7.1.15-apache的基础上安装相关插件 :**

其Dockerfile文件如下 ：

```
FROM php:7.1.15-apache
RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng-dev \
        libxslt-dev \
        libicu-dev  \


    && docker-php-ext-install -j$(nproc) iconv mcrypt xsl intl pdo_mysql soap zip \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd
```

构建过程报错： configure: error: xslt-config not found. Please reinstall the libxslt &gt;= 1.1.0 distributionconfigure: error: xslt-config not found. Please reinstall the libxslt &gt;= 1.1.0 distribution

configure: error: Unable to detect ICU prefix or no failed. Please verify ICU install prefix and make sure icu-config works.

另附参考 ：[How to install php-redis extension using the official PHP Docker image approach?](https://stackoverflow.com/questions/31369867/how-to-install-php-redis-extension-using-the-official-php-docker-image-approach)

以Docker的官方镜像php:7.1.15-apache为基础建立magento2.2.3镜像

Dockerfile**该官方镜像缺少magento需要的一些插件：**

通过 运行magento223的安装程序：

可以看出 缺少的插件为 ：PHP Extension mcrypt，PHP Extension xsl，PHP Extension intl，PHP Extension pdo\_mysql，PHP Extension soap， PHP Extension zip , PHP Extension gd.经过查看对应的官网php-7.1.16 源码，以上缺少均是官方插件

现在需要在官方镜像 **php:7.1.15-apache的基础上安装相关插件 :**

其Dockerfile文件如下 ：

```
FROM php:7.1.15-apache
RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng-dev \
        libxslt-dev \
        libicu-dev  \


    && docker-php-ext-install -j$(nproc) iconv mcrypt xsl intl pdo_mysql soap zip \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd
```

构建过程报错： configure: error: xslt-config not found. Please reinstall the libxslt &gt;= 1.1.0 distributionconfigure: error: xslt-config not found. Please reinstall the libxslt &gt;= 1.1.0 distribution

configure: error: Unable to detect ICU prefix or no failed. Please verify ICU install prefix and make sure icu-config works.

另附参考 ：[How to install php-redis extension using the official PHP Docker image approach?](https://stackoverflow.com/questions/31369867/how-to-install-php-redis-extension-using-the-official-php-docker-image-approach)

以Docker的官方镜像php:7.1.15-apache为基础建立magento2.2.3镜像

Dockerfile

