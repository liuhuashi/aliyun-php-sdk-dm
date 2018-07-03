# aliyun-php-sdk-dm

---

阿里云邮件推送服务 DirectMail。

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