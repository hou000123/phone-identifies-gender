# 根据手机号识性别
目前基本功能已经实现，采用 `chan` + `goroutine`, 支持多个手机并行搜索，更细化的需要根据实际需求实现, e.g: 读文件、输出到文件

## 实现思路
目前大多数手机号都注册了微信，所以思路就是控制手机上的微信搜索来获取性别
- usb 连接手机，打开 usb 调试，开模拟点击的授权
- 手机打开搜索页, 通讯录>新的朋友->点下搜索框
- `adb uiautomator` 获取到当前页面的 xml, 分析出搜索框的坐标
- `adb` 输入手机号，并点击搜索
- `adb uiautomator` 获取到搜索结果页的 xml, 分析出性别

## 实现思路(2022優化內容)
微信UI布局有改動
- 修改在文字認別, 作元素定位
- 使用顏色認別, 作男女識別

## 如何使用
```bash
go run *.go
```

```bash
2020/07/19 22:46:59 启动中...
2020/07/19 22:46:59 共有1台设备连接
2020/07/19 22:47:00 手机号输入框坐标: &{521 161}
2020/07/19 22:47:02 清除手机号输入框坐标: &{881 161}
2020/07/19 22:47:02 搜索按钮坐标: &{648 312}
18339258680 男
133456789 该用户不存在
18339258680 男
```


## 实现思路(2022優化內容)

