背景：<video>标签在移动端的不同平台存在不少兼容性问题，因此在这列出各个问题以及问题的解决方案。



1. 如果将一个<video>直接显示在页面中，那么就会看到各种五花八门的播放器初始效果；并且poster（封面图）属性在各个平台的兼容性不一致，iOS 支持，Android 不一定支持，而且各产商表现差异大

解决方案：制作一个模拟的视频播放视图，比如一个封面加一个播放按钮。而真实的<video>视频元素要隐藏起来，通过点击图片来控制视频播放。最好不要用{display: none}或者{width:0;height:0;}的方式，因为这样视频元素会处于未激活的状态，给后续的处理带来麻烦。将视频设置成1x1像素大小，放在视觉边缘的位置是个比较合适的方案。



2. 在视频加载完成后，若首先点击全屏按钮而未点击播放按钮，在某些安卓微信浏览器中会出现白屏现象及会在头部提示“网页由XXX提供，QQ浏览器X5内核提供技术支持”

问题原因：QQ浏览器会强制劫持video标签，微信里也是直接替换成腾讯的播放器插件。

解决方案：经测试在播放的情况下再去点击全屏不会出现怪异行为，因此方案可同问题1，强制视频播放后才可执行全屏操作。



3. 在某些安卓浏览器中<video>标签总是在最前（可以理解为video标签的z-index属性是Max）

问题原因：QQ浏览器会劫持所有video标签，生成一个与其等大的native播放框，所以设置z-index是不起作用的，微信的处理方式和QQ浏览器一致。

解决方案：尚无较完整的解决方案，可参考https://zhuanlan.zhihu.com/p/27559167



