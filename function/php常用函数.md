###跳转对应的邮箱地址
```php
function get_email_url($email) {
  $t = explode('@',$email);
  $t = strtolower($t[1]);
  $http = 'http://';
  if ($t == '163.com') {
      return $http . 'mail.163.com';
  } else if ($t == 'vip.163.com') {
      return $http . 'vip.163.com';
  } else if ($t == '126.com') {
      return $http . 'mail.126.com';
  } else if ($t == 'qq.com' || $t == 'vip.qq.com' || $t == 'foxmail.com') {
      return $http . 'mail.qq.com';
  } else if ($t == 'gmail.com') {
      return $http . 'mail.google.com';
  }else if ($t == 'sohu.com') {
      return $http . 'mail.sohu.com';
  } else if ($t == 'tom.com') {
      return $http . 'mail.tom.com';
  } else if ($t == 'vip.sina.com') {
      return $http . 'vip.sina.com';
  } else if ($t == 'sina.com.cn' || $t == 'sina.com') {
      return $http . 'mail.sina.com.cn';
  } else if ($t == 'tom.com') {
      return $http . 'mail.tom.com';
  } else if ($t == 'yahoo.com.cn' || $t == 'yahoo.cn') {
      return $http . 'mail.cn.yahoo.com';
  } else if ($t == 'tom.com') {
      return $http . 'mail.tom.com';
  } else if ($t == 'yeah.net') {
      return $http . 'www.yeah.net';
  } else if ($t == '21cn.com') {
      return $http . 'mail.21cn.com';
  } else if ($t == 'hotmail.com') {
      return $http . 'www.hotmail.com';
  } else if ($t == 'sogou.com') {
      return $http . 'mail.sogou.com';
  } else if ($t == '188.com') {
      return $http . 'www.188.com';
  } else if ($t == '139.com') {
      return $http . 'mail.10086.cn';
  } else if ($ t== '189.cn') {
      return $http . 'webmail15.189.cn/webmail';
  } else if ($t == 'wo.com.cn') {
      return $http . 'mail.wo.com.cn/smsmail';
  } else if ($t == '139.com') {
      return $http . 'mail.10086.cn';
  } else {
      return '';
  }
}
```

###计算字符长度
```
function mbstrlen($str)
{
    $len = strlen($str);
     
    if ($len <= 0)
    {
        return 0;
    }
     
    $count  = 0;
     
    for ($i = 0; $i < $len; $i++)
    {
        $count++;
        if (ord($str{$i}) >= 0x80)
        {
            $i += 2;
        }
    }
     
    return $count;
}
//GBK会将2个字节当成一个字符来处理，UTF8则需要3个字节
mbstrlen("中国so强大！")       //7
mb_strlen("中国so强大！")      //17
strlen("中国so强大！")         //17
```
