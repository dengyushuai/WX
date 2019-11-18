# WX
调用微信案例
1、首先配置公众号的JS接口安全域名 业务域名 网页授权域名(3个域名要一致)
2、配置IP白名单 也就是把本地电脑IP添加到公众号IP白名单中
 3、调用后台接口获取微信config配置项(appId(公众号的唯一标识): 公众号中可以取到 直接写死，timestamp(生产签名的时间戳): 后台返回，nonceStr(生成签名的随机串): 后台返回，signature(签名): 后台返回，jsApiList(需要使用JS接口列表，这里调用的扫一扫): ['scanQRCode'](公众号开发文档(https://developers.weixin.qq.com/doc/offiaccount/OA_Web_Apps/JS-SDK.html#%E9%99%84%E5%BD%951-JS-SDK%E4%BD%BF%E7%94%A8%E6%9D%83%E9%99%90%E7%AD%BE%E5%90%8D%E7%AE%97%E6%B3%95)附录2-所有JS接口列表里))
 引入微信js<script src="https://res.wx.qq.com/open/js/jweixin-1.2.0.js"></script>
 5、这里以扫一扫为例 wx.scanQRCode()方法要写到wx.reday()
6，公众号扫一扫到这配置完成
传给后台的参数URl问题如下
1、url为传给后台参数 后台用来请求签名
2、url必须为页面的完整路径不能带#号 也就是域名 + 参数 例：www.baidu.com?name=1&age=2
3，url的域名必须是真实域名，然后此url的域名要和公众号配置的JS接口安全域名网页授权域名业务域名四个域名要一致；如果此url与公众号配置的域名不同就会报无效的URL如果此URL与公众号配置的域名相同（则此URL写死了，想在本地测试）与地址栏上不同（本地使用github测试）就会报签名错误（签名签名）
具体请看代码
