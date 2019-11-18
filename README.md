# WX
# 前端调用微信扫一扫
#### 一、扫一扫配置
1、首先配置公众号的JS接口安全域名 业务域名 网页授权域名(3个域名要一致) <br/>
2、配置IP白名单 也就是把本地电脑IP添加到公众号IP白名单中 <br/>
3、调用后台接口获取微信config配置项如下: <br/>
* appId(公众号的唯一标识): 公众号中可以取到 直接写死 <br/>
* timestamp(生产签名的时间戳): 后台返回 <br/>
* nonceStr(生成签名的随机串): 后台返回 <br/>
* signature(签名): 后台返回 <br/>
* jsApiList(需要使用JS接口列表，这里调用的扫一扫): ['scanQRCode'](公众号开发文档(<a  href="https://developers.weixin.qq.com/doc/offiaccount/OA_Web_Apps/JS-SDK.html#%E9%99%84%E5%BD%951-JS-SDK%E4%BD%BF%E7%94%A8%E6%9D%83%E9%99%90%E7%AD%BE%E5%90%8D%E7%AE%97%E6%B3%95">接口列表地址<a/>)附录2-所有JS接口列表里) <br/>

4、引入微信js<script src="https://res.wx.qq.com/open/js/jweixin-1.2.0.js"></script> <br/>
5、这里以扫一扫为例 wx.scanQRCode()方法要写到wx.reday() <br/>
6，公众号扫一扫到这配置完成
#### 二、扫一扫传给后台的参数URl问题如下
1、url为传给后台参数 后台用来请求签名 <br/>
2、url必须为页面的完整路径不能带#号 也就是域名 + 参数 例：www.baidu.com?name=1&age=2 <br/>
3，url的域名必须是真实域名，此url的域名要和公众号配置的JS接口安全域名网页授权域名业务域名四个域名要一致；<br/>
* 如果此url与公众号配置的域名不同就会报无效的URL<br/>
* 如果此URL与公众号配置的域名相同（此URL为公众号配置的域名）与地址栏上URL不同（使用本地启动的服务器测试时）就会报签名错误(也就是说此URL与地址栏上的URL不同时就会报签名错误，没有使用location.href.split('#')[0]获取URL) <br/>

4、具体请看代码 <br/>


`如有大牛不经意间看见此代码，看见问题一定留下您的宝贵意见，感激不尽。`
