#  Docker 
## Alpine
### apt-get install 依赖搜索    https://pkgs.alpinelinux.org
### pecl 安装
```
RUN echo '' | pecl install -o -f redis msgpack grpc protobuf grpc protobuf \
    && rm -rf /tmp/pear \
    && docker-php-ext-enable redis msgpack grpc protobuf grpc protobuf 
```

# PHP Packagist
### 网址 https://packagist.org

# Go Packagist
### 网址 https://pkg.go.dev

# GitHub 头像显示
### 网址 https://en.gravatar.com
