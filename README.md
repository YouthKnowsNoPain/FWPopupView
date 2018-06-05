# IOS之弹窗 -- Swift4.x/[OC版本](https://github.com/choiceyou/FWPopupViewOC)（注意：OC版本目前只实现了弹窗基类）

[![Platform](http://img.shields.io/badge/platform-iOS-blue.svg?style=flat)](http://cocoapods.org/?q=FWPopupView)&nbsp;
![Language](https://img.shields.io/badge/language-swift-orange.svg?style=flat)&nbsp;
[![License](http://img.shields.io/badge/license-MIT-green.svg?style=flat)](https://github.com/choiceyou/FWPopupView/blob/master/FWPopupView/LICENSE)



## 支持pod导入：

```cocoaPods
pod 'FWPopupView'
注意：如出现 [!] Unable to find a specification for 'FWPopupView' 错误，可执行 pod repo update 命令。
```



## 更新记录：

```更新记录
• v2.0.4 ：
  1.灰色背景默认值由原来的 alpha=0.6 改为 alpha=0.5；
  2.在原类初始化方法中添加输入框键盘类型参数：UIKeyboardType（鉴于方法可能跟着版本改动，所以建议封装使用）；
  
• v2.0.5 :
  1.修复弹窗隐藏时未设置原window为keywindow的问题；
  
• v2.0.6 :
  1.原FWPopupItemHandler改为FWPopupItemClickedBlock，增加反馈当前弹窗参数；
  2.FWItemType加入参数canAutoHide：点击该按钮后会自动隐藏弹窗。这样子做能够适应更多的弹窗场景；
  
• v2.0.7 :
  1.支持单独设置某个按钮的文字、背景颜色；
  
• v3.0.0（大版本） :
  1.弹窗基类重构：设置视图展示位置+偏移量来设置弹窗真正需要展示的位置；有多重可选动画类型。
  2.由于OC类不能继承Swift类，所以弹窗基类实现了两种语言。swift版本：FWPopupView；OC版本：FWPopupBaseView；
  3.FWAlertView/FWSheetView/FWDateView使用基类提供动画类型；
  4.新增FWMenuView，可实现类似QQ/微信首页右上角菜单；
  5.其他细节修改；
```



## 简单使用：（注：可下载demo具体查看，分别有OC、Swift的demo） 
```swift
/// 类初始化方法
///
/// - Parameters:
///   - title: 标题
///   - detail: 描述
///   - confirmBlock: 确定按钮回调
/// - Returns: self
open class func alert(title: String,
                     detail: String,
               confirmBlock: @escaping FWPopupItemHandler) -> FWAlertView
                          
```

```swift
/// 类初始化方法
///
/// - Parameters:
///   - title: 标题
///   - itemTitles: 点击项标题
///   - itemBlock: 点击回调
///   - cancenlBlock: 取消按钮回调
///   - property: FWSheetView的相关属性
/// - Returns: self
open class func sheet(title: String?,
                 itemTitles: [String],
                  itemBlock: @escaping FWPopupItemHandler,
               cancenlBlock: @escaping FWPopupVoidBlock,
                   property: FWSheetViewProperty?) -> FWSheetView
```

### Swift:
```swift
let alertView = FWAlertView.alert(title: "标题", detail: "描述描述描述描述") { (index) in
    print("点击了确定")
}
alertView.show()
```
```python
let sheetView = FWSheetView.sheet(title: "测试", 
                             itemTitles: ["Sheet0", "Sheet1", "Sheet2", "Sheet3"], 
                              itemBlock: { (index) in
    print("Sheet：点击了第\(index)个按钮")
}, cancenlBlock: {
    print("点击了取消")
})
sheetView.show()
```


### OC：<br>
```oc
FWAlertView *alertView = [FWAlertView alertWithTitle: @"标题" 
                                              detail: @"描述描述描述描述" 
                                        confirmBlock:^(NSInteger index) {
    NSLog(@"点击了确定");
}];
[alertView show];
```
```oc
FWSheetView *sheetView = [FWSheetView sheetWithTitle: @"标题" 
                                          itemTitles: @[@"Sheet0", @"Sheet1", @"Sheet2", @"Sheet3"] 
                                           itemBlock:^(NSInteger index) {
    NSLog(@"Sheet：点击了第 %ld 个按钮", (long)index);
} cancenlBlock:^{
    NSLog(@"点击了取消");
}];
[sheetView show];
```



## 效果：
![](https://github.com/choiceyou/FWPopupView/blob/master/%E6%95%88%E6%9E%9C/IMG_0714.PNG)
![](https://github.com/choiceyou/FWPopupView/blob/master/%E6%95%88%E6%9E%9C/IMG_0715.PNG)

![](https://github.com/choiceyou/FWPopupView/blob/master/%E6%95%88%E6%9E%9C/IMG_0716.PNG)
![](https://github.com/choiceyou/FWPopupView/blob/master/%E6%95%88%E6%9E%9C/IMG_0717.PNG)

![](https://github.com/choiceyou/FWPopupView/blob/master/%E6%95%88%E6%9E%9C/IMG_0718.PNG)
![](https://github.com/choiceyou/FWPopupView/blob/master/%E6%95%88%E6%9E%9C/IMG_0719.PNG)

![](https://github.com/choiceyou/FWPopupView/blob/master/%E6%95%88%E6%9E%9C/IMG_0720.PNG)
![](https://github.com/choiceyou/FWPopupView/blob/master/%E6%95%88%E6%9E%9C/IMG_0721.PNG)

![](https://github.com/choiceyou/FWPopupView/blob/master/%E6%95%88%E6%9E%9C/Custom.gif)
![](https://github.com/choiceyou/FWPopupView/blob/master/%E6%95%88%E6%9E%9C/Menu.gif)



## 结尾语：

- 使用过程中发现bug请issues或（QQ群：670698309）；
- 有新的需求欢迎提出；
