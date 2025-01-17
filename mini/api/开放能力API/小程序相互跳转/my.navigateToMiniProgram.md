
# 简介
**my.navigateToMiniProgram** 是用于跳转到其他小程序的 API。

目标小程序可通过 [联调设置](https://opendocs.alipay.com/mini/ide/integration-testing) 来唤起指定的开发版本。

相关问题请参见 [小程序相互跳转 FAQ](https://opendocs.alipay.com/mini/api/xqvxl4)。

## 使用限制
此 API 支持个人支付宝小程序、企业支付宝小程序使用。

# 接口调用

## 示例代码

### .js 示例代码
```javascript
// .js
my.navigateToMiniProgram({
      appId: 'xxxx',
      path: 'pages/index/index',
      extraData:{
        "data1":"test"
      },
      success: (res) => {
        console.log(JSON.stringify(res))
      },
      fail: (res) => {
        console.log(JSON.stringify(res))
      }
    });
```

## 入参
Object 类型，属性如下：

| **属性** | **类型** | **必填** | **描述** |
| --- | --- | --- | --- |
| appId | String | 是 | 要跳转的目标小程序 appId。 |
| path | String | 否 | 打开的页面路径，如果为空则打开首页。 |
| extraData | Object | 否 | 需要传递给目标小程序的数据库，为键值对的格式，数值的类型为字符串。<br />目标小程序可在 `App.onLaunch()`、`App.onShow()` 中获取到这份数据。 |
| success | Function | 否 | 调用成功的回调函数。 |
| fail | Function | 否 | 调用失败的回调函数。 |
| complete | Function | 否 | 调用结束的回调函数（）调用成功、失败都会执行。 |


### 错误码
| **错误码** | **描述** | **解决方案** |
| --- | --- | --- |
| 31 | 跳转失败。 | 可能是目标应用信息查询失败导致，建议检查跳转的目标应用是否已经上架。<br />APPID 长度为 8 位的小程序暂不支持跳转。 |


## 常见问题 FAQ

### Q：my.navigateToMiniProgram 的 extraData 的参数在哪里获取？ extraData 是否可以添加多个参数？自定义参数中间使用的什么符号进行拼接？
A：目标小程序可在 App.onLaunch( )、App.onShow( ) 中获取到这份数据。

extraData 可以添加多个参数，自定义参数都是从这里传入的。

自定义参数中间使用 & 符号进行拼接。

### Q：小程序如何跳转收藏有礼页面？
A：可参考如下代码。更多详情请参见 [小程序有礼](https://opendocs.alipay.com/mini/operation/app-with-benefit)。
```javascript
// .js
my.navigateToMiniProgram({
     appId: '2018122562686742',//收藏有礼小程序的appid，固定值请勿修改
     path: 'pages/index/index?originAppId=2017082508366123&newUserTemplate=20190130000000119123',//收藏有礼跳转地址和参数
     success: (res) => {
       // 跳转成功
       my.alert({ content: 'success' });
     },
     fail: (error) => {
       // 跳转失败
       my.alert({ content: 'fail' });
     }
   });
```
