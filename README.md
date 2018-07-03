# aliyun-php-sdk-dm

---

阿里云邮件推送服务 DirectMail。

## 安装

```php
composer require rjyxz/aliyun-php-sdk-dm
```

## 例子

```php
use Dm\Request\V20151123\SingleSendMailRequest;

function sendMail(){
    $iClientProfile = \DefaultProfile::getProfile("cn-hangzhou", "<your accessKey>", "<your accessSecret>");
    
    $client = new \DefaultAcsClient($iClientProfile);
    $request = new SingleSendMailRequest();
    
    $request->setAccountName("控制台创建的发信地址");
    $request->setFromAlias("发信人昵称");
    $request->setAddressType(1);
    $request->setTagName("控制台创建的标签");
    $request->setReplyToAddress("true");
    $request->setToAddress("目标地址");        
    $request->setSubject("邮件主题");
    $request->setHtmlBody("邮件正文");        
    
    try {
        $response = $client->getAcsResponse($request);
        print_r($response);
    }
    catch (\ClientException  $e) {
        print_r($e->getErrorCode());   
        print_r($e->getErrorMessage());   
    }
}
```

## 阿里云邮件推送

服务地址 [https://dm.console.aliyun.com](https://dm.console.aliyun.com)

邮件推送 > API 参考 

[https://help.aliyun.com/document_detail/29434.html](https://help.aliyun.com/document_detail/29434.html)

邮件推送 > SDK 参考

[https://help.aliyun.com/document_detail/29460.html](https://help.aliyun.com/document_detail/29460.html)

## 手动添加第三方库

```php
// 添加SDK包,将两个包放到自定义目录Services
app/Services/aliyun-php-sdk-core
app/Services/aliyun-php-sdk-dm
// 添加Composer自动加载
"classmap": [
    "database/seeds",
    "database/factories",
    "app/Services/aliyun-php-sdk-core",
    "app/Services/aliyun-php-sdk-dm"
],
// 更新Composer自动加载类
composer dump-autoload
```