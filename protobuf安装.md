#windows 环境下配置

###注意：pb4php这个解析是绿色安装，可惜不支持protobuf 3
https://code.google.com/p/pb4php/downloads/list

###php 5.3以上

###protoc安装
1.下载protoc-3.0.0-beta-1-win32.zip(https://github.com/google/protobuf/releases) 
2.解压在D盘根目录下 d:/ 
3.建立一个文件tutorial.proto 
4.填入内容
```C++
package tutorial;

message Person {
  required string name = 1;
  required int32 id = 2;
  optional string email = 3;

  enum PhoneType {
    MOBILE = 0;
    HOME = 1;
    WORK = 2;
  }

  message PhoneNumber {
    required string number = 1;
    optional PhoneType type = 2 [default = HOME];
  }

  repeated PhoneNumber phone = 4;
}

message AddressBook {
  repeated Person person = 1;
}
```

###pear安装
```
1.下载go-pear.phar  http://pear.php.net/go-pear.phar
2.coky至php目录 
3.php go-pear.php 一路回车 
```

###drslump/Protobuf-PHP安装（https://github.com/drslump/Protobuf-PHP）
```
1.pear channel-discover pear.pollinimini.net 
2.pear install drslump/Protobuf-beta 
3.安装完成后，在php根目录下出现pear/DrSlump目录，protoc-gen-php，protoc-gen-php.bat文件 
```

###生成tutorial类
```
1.打开cmd,进入D盘protoc目录下 
2.protoc-gen-php.bat -i . tutorial.proto 
注意：如果不进入protoc.exe所在的根目录，编译运行所错找不到文件 
```

###安装composer
###下载Protobuf-PHP（https://github.com/drslump/Protobuf-PHP）
1.下载包放在程序里面
2.composer install 安装

###参考调用
```
<?php
require_once 'DrSlump/Protobuf.php';
\DrSlump\Protobuf::autoload();

$person = new Tutorial\Person();
$person->setId(12);
$data = $person->serialize();
```

###其他错误(https://github.com/drslump/Protobuf-PHP/issues/28)
```
A simple fix for this is to change drslump code: DrSlump/Protobuf/Codec/Binary.php, line 249, change
$wire = $this->getWireType($type);
to
$wire = $this->getWireType($type, null);
That is because the function getWireType, defined above in the same file, really takes 2 arguments:
protected function getWireType($type, $default)
Some other uses of getWireType pass $default equal to null, so it seems correct. It seems 2nd argument is used only by assertWireType.

Disclaimer: I just changed it blindly and it seems to work for me. No guarantees :)
```
