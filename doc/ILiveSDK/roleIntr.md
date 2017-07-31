## 角色

## 什么是角色
互动直播引入角色的概率，用于实现在单一平台上也可以配置不同的参数。可以将角色理解为终端进入房间的配置集。

### 如何配置角色
用户可以在腾讯云后台，配置角色
![](https://zhaoyang21cn.github.io/iLiveSDK_Help/readme_img/role_config.png 

)

### 如何定制角色
用户可以根据自己的需求定制自己的角色
![](https://zhaoyang21cn.github.io/iLiveSDK_Help/readme_img/role_detail.png 

)

### 如何使用角色
用户可以在进房间的option中配置要使用的角色

Android:
```
ILVLiveRoomOption hostOption = new ILVLiveRoomOption(hostId)
                .controlRole("LiveMaster");     // 使用 LiveMaster 角色
```

IOS
```
//TILLiveSDK（直播SDK）
TILLiveRoomOption *hostOption = [TILLiveRoomOption defaultHostLiveOption];
hostOption.controlRole = @"LiveMaster";   // 使用 LiveMaster 角色
```
```
//TILCallSDK（通话SDK）
TILCallSponsorConfig *sponsorConfig = [[TILCallSponsorConfig alloc] init];
sponsorConfig.controlRole = @"LiveMaster";   // 使用 LiveMaster 角色
```

### 如何切换角色
用户在进进入房间后，仍然可以根据需求调整角色

Android:
```
// 切换角色为 LiveGuest
ILiveRoomManager.getInstance().changeRole("LiveGuest", new ILiveCallBack() {
            @Override
            public void onSuccess(Object data) {
                //...
            }

            @Override
            public void onError(String module, int errCode, String errMsg) {
                //...
            }
        });
```


IOS:
```
// 切换角色为 LiveGuest
ILiveRoomManager *manager = [ILiveRoomManager getInstance];
[manager changeRole:@"LiveGuest" succ:^ {
        NSLog(@"角色改变成功");
    } failed:^(NSString *module, int errId, NSString *errMsg) {
        NSLog(@"角色改变失败");
    }];
```


### 角色的高阶应用
根据网络状态调整动态当前的视频质量：
用户可以在腾讯云针对主播，观众分别配置多个角色(高清，标清，流畅)，用户可以检测当前的网络状态，动态调整当前使用的角色，以达到动态修改视频质量的效果
可以参照随心播。
