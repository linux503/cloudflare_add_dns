# cloudflare_add_dns

标题:cloudflare批量添加域名及添加dns解析记录php脚本

原理：
程序会循环读取domain.txt的每一行通过cloudflare接口添加，并将record.txt中的记录循环读取添加到每一个域名中。
接口参考：https://api.cloudflare.com/

目前支持A、CNAME记录批量添加。

说明:目前只能支持新添加的域名,脚本不支持添加已有域名添加A记录.

配置方法：

1、首先修改run.php中
$header = array(
    "X-Auth-Email:xxx@gmail.com", #cloudflare账号
    "X-Auth-Key:xxx", #cloudflare的key
);

X-Auth-Email及X-Auth-Key参数从cloudflare后台中查看。其它部分代码不需修改。

2、domain.txt为待加入的域名列表，一行一个，文件编码为utf-8，格式为windows（cr lf）格式（务必）。推荐用notepad++编辑。

3、record.txt为待加入的解析列表。一行一个。文件编码为utf-8，格式为windows（cr lf）格式（务必）。每行分3列，以逗号分隔，第一列为主机记录，如www，第二列为记录类型，如A记录，第三列为值，如114.114.114.114

4、推荐在命令行中执行 php run.php，不要在浏览器中访问。
Macos Monterey 12之前的版本 需要在本地安装
#pip install php

该脚本是基于 git其他脚本优化修改的.忘了之前的地址! 
