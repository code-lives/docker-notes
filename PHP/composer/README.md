# 自定义
```
name               在packagist 的 名称 （composer require code-lives/php-compose-demo）
description        简介
type               类型
license            MIT
version            版本 （参数非必选）
authors            作者的一些信息
minimum-stability  stable
autoload           自动加载
psr-4              Demo\\test\\ 命名空间 src 文件路径
```
### composer.json
```
{
    "name": "code-lives/php-compose-demo", 
    "description": "PHP Composer Demo",
    "type": "library",
    "license": "MIT",
    "version":"3.0",
    "authors": [
        {
            "name": "lijie",
            "email": "18734351007@163.com"
        }
    ],
    "minimum-stability": "stable",
    "autoload":{
   	"psr-4":{"Demo\\test\\":"src"}
    }
}
```
### src/Test.php
```
<?php

namespace Demo\test;

class Test
{

	public function __construct()
	{
	}

	public function index()
	{
		echo 1;
	}
}
```
### 目录结构
- src
  - Test.php
- composer.json
