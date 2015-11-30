#windows 环境下配置

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
1.进入php目录 
2.php go-pear.php 一路回车 
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
