# lib-flexible
## 此项目为自身理解手淘的移动端自适应方案[lib-flexible][1]建立

### 概念
#### 1. 物理像素(physical pixel)(设备像素、硬件像素)

#### 2. 设备独立像素(density-independent pixel)

#### 3. 设备像素比(device pixel ratio)


### lib-flexible做的事情,以iPhone6, 375 * 667 为例
#### 1.检测dpr,根据dpr设置initial-scale,initial-scale = 1 / dpr，解决1px的横线问题
未缩放：dpr = 2，1 * 1px的css像素占据的物理像素为 2 * 2px, 整体显示 375 * 667 的css像素内容
缩放后：initial-scale = 0.5, 1*1px css像素缩小了一倍，占用 1 * 1px 物理像素（解决1px问题），整体可显示 750 * 1334 的css像素内容
#### 2.根据缩放，设置html.fontSize,使 10 html.fontSize = html.width
document.documentElement.getBoundingClientRect().width / 10 = html.fontSize;
initial-scale = 1.0: width = 375
initial-scale = 0.5: width = 750
### lib-flexible 使用不便的地方
#### 1.缩放导致固定px的单位变小
如：initial-scale = 1 下的 font-size = 12px 和 initial-scale = 0.5 下的 font-size = 24px是一样大的
这么做导致第三方库(如weui、vux)若是使用了固定单位，在不同dpr下同一个尺寸的元素差异很大，根本无法使用（很致命，公司小，没法自己些所有的库，这个问题会导致引入lib-flexible的成本很大（个人理解））
#### 2.


### 参考资料
1. [使用Flexible实现手淘H5页面的终端适配][2]
2. []

[1]: https://github.com/amfe/lib-flexible        "lib-flexible" 
[2]: https://github.com/amfe/article/issues/17   "使用Flexible实现手淘H5页面的终端适配"
[3]: http://www.html-js.com/article/Mobile-terminal-H5-mobile-terminal-HD-multi-screen-adaptation-scheme%203041 "移动端高清、多屏适配方案"