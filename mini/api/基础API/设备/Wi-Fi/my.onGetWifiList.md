
# 简介
监听在获取到 Wi-Fi 列表数据时的事件，在回调中将返回 wifiList。

# 使用限制

- **基础库** [1.11.0](https://opendocs.alipay.com/mini/framework/compatibility) 开始支持。若版本较低，建议采取 [兼容处理](https://opendocs.alipay.com/mini/framework/compatibility)。
- 此 API 暂仅支持企业支付宝小程序使用。

# 接口调用

## 示例代码

### .js 示例代码
```javascript
my.onGetWifiList(function(res) {
  console.log(res)
})
```

## 入参
**function callback**<br />获取到 Wi-Fi 列表数据事件的回调函。

## callback 参数
| **属性** | **类型** | **描述** |
| --- | --- | --- |
| wifiList | Array<WifiList> | Wi-Fi 列表数据。 |


### WifiList
| **属性** | **类型** | **秒速** |
| --- | --- | --- |
| SSID | String | Wi-Fi 的 SSID。 |
| BSSID | String | Wi-Fi 的 BSSID。 |
| secure | Boolean | Wi-Fi 是否安全。 |
| signalStrength | Number | Wi-Fi 信号强度。取值 0 ～ 100，值越大强度越大。 |

