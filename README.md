#### 优化
- 优化完善Swagger导入，支持实体和数组，实现多级显示

#### Docker 开发调试

- docker build -t eolinkerphp:test .;
- docker run -d --name eolinkerweb -p 8001:80 -v /xxxxxx/：/var/www/html/ eolinkerphp:test;


#### Docker 部署1

- docker build -t eolinkerphp:prod .;
- docker run -d --restart=always --name eolinkerweb -p 8001:80 -v /xxxxxx/：/var/www/html/server/RTP/config/ eolinkerphp:prod;

这样每次启动，设置不会被重置

#### Docker 部署1

- cd server/RTP/config
- touch eo_config.php
- modify db config
```
<?php
//主机地址
defined('DB_URL') or define('DB_URL', '192.168.1.2');

//主机端口,默认mysql为3306
defined('DB_PORT') or define('DB_PORT', '3306');

//连接数据库的用户名
defined('DB_USER') or define('DB_USER', 'dbuser');

//连接数据库的密码，推荐使用随机生成的字符串
defined('DB_PASSWORD') or define('DB_PASSWORD', 'dbpassword');

//数据库名
defined('DB_NAME') or define('DB_NAME', 'eolinker_os');

//是否允许新用户注册
defined('ALLOW_REGISTER') or define('ALLOW_REGISTER', TRUE);

//是否允许更新项目，如果设置为FALSE，那么自动更新和手动更新都将失效
defined('ALLOW_UPDATE') or define('ALLOW_UPDATE', TRUE);

//网站名称
defined('WEBSITE_NAME') or define('WEBSITE_NAME', 'eoLinker开源版本');

//数据表前缀
defined('DB_TABLE_PREFIXION') or define('DB_TABLE_PREFIXION', 'eo');

//语言
defined('LANGUAGE') or define ('LANGUAGE', 'zh-cn');
?>
```
- cd server\RTP\db
- import eolinker_os_mysql.sql
- docker build -t eolinkerphp:prod .;
- docker run -d --restart=always --name eolinkerweb -p 8001:80 eolinkerphp:prod;


## eolinker开源版本
 * @name eolinker ams open source，eolinker开源版本
 * @link https://www.eolinker.com/
 * @package eolinker
 * @author www.eolinker.com 广州银云信息科技有限公司 2015-2017
 * eoLinker是目前全球领先、国内最大的在线API接口管理平台，提供自动生成API文档、API自动化测试、Mock测试、团队协作等功能，旨在解决由于前后端分离导致的开发效率低下问题。
 * 如在使用的过程中有任何问题，欢迎加入用户讨论群进行反馈，我们将会以最快的速度，最好的服务态度为您解决问题。
 *
 * eoLinker AMS开源版的开源协议遵循Apache License 2.0，如需获取最新的eolinker开源版以及相关资讯，请访问:https://www.eolinker.com/#/os/download
 *
 * 官方网站：https://www.eolinker.com/
 * 官方博客以及社区：http://blog.eolinker.com/
 * 使用教程以及帮助：http://help.eolinker.com/
 * 商务合作邮箱：market@eolinker.com
 * 用户讨论QQ群：284421832