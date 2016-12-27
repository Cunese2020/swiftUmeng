# swift 集成友盟统计
> 前言

友盟统计分析平台是国内最大的移动应用统计分析平台。用于帮助移动应用开发商统计和分析流量来源、内容使用、用户属性和行为数据，以便开发商利用数据进行产品、运营、推广策略的决策。**由于官网提供的代码样例是Objective-C的，下面我将演示如何使用Swift来调用友盟的SDK。**

### 什么是友盟

- 友盟致力于为移动开发者提供专业的数据统计分析、开发和运营组件及推广服务。服务包含移动应用统计分析以及细分行业的移动游戏统计分析、社会化分享组件、消息推送、自动更新、用户反馈、错误分析等产品。
- 友盟提供iOS、Android和Windows Phone等多平台服务。

### 集成步骤
（1）获得Appkey
在集成友盟SDK之前，首先需要到 [友盟官网](http://mobile.umeng.com/apps) 注册并且添加新应用，获得Appkey

- 特别提醒：我们建议开发者在注册账号时使用企业邮箱，避免使用个人邮箱注册，防止由于个人离职带来的问题，建议使用的账号形式 ：umeng@企业域名、apps@企业域名、dev@企业域名。
![](http://7xuul2.com1.z0.glb.clouddn.com/QQ20161227-0@2x.png)

(2)下载统计sdk

- [下载sdk](http://dev.umeng.com/analytics/ios-doc/sdk-download)并解压缩。

(3)把sdk添加到项目中去

- 将sdk中的  **UMMobClick.framework** 文件拖入XCode工程目录**Frameworks**结构中。

![](http://7xuul2.com1.z0.glb.clouddn.com/QQ20161227-1@2x.png)

**同时还要记得添加桥接文件，在其中增加对友盟分析的引用。**
> `#import <UMMobClick/MobClick.h>`

如果不知道怎么添加，请自行 Google


(4)在 AppDelegate.swift 中增加配置，代码如下：

```
import UIKit
 
@UIApplicationMain
class AppDelegate: UIResponder, UIApplicationDelegate {
 
    var window: UIWindow?
 
    func application(application: UIApplication,
        didFinishLaunchingWithOptions launchOptions: [NSObject: AnyObject]?) -> Bool {
         
        //友盟统计
        let cofingUmeng = UMAnalyticsConfig();
        cofingUmeng.appKey = "585895f7f5ade4037f002237"
        cofingUmeng.channelId = "App Store"
        MobClick.startWithConfigure(cofingUmeng);
         
        return true
    }
     func applicationWillResignActive(application: UIApplication) {
    }
 
    func applicationDidEnterBackground(application: UIApplication) {
    }
 
    func applicationWillEnterForeground(application: UIApplication) {
    }
 
    func applicationDidBecomeActive(application: UIApplication) {
    }
 
    func applicationWillTerminate(application: UIApplication) {
    }
}

```
(5)测试效果

- 上面配置完以后直接启动测试下（真机模拟器均可），进入友盟后台，可以看到新增用户信息了。
![](http://7xuul2.com1.z0.glb.clouddn.com/QQ20161227-0.png)

如果在后台成功的看见有数据变化证明已经集成 ok 啦🙄，如果想扩展统计更多功能请参考[友盟官网文档](http://dev.umeng.com/analytics/ios-doc/integration)

有什么问题欢迎留言或者私信，作者看到后都会一一回复

么么哒~






