blog_uiview_and_uiwindow
========================

UIView 和 UIWindow的区别与联系


这两个类是cocoa touch类库中至关重要的两个类，是理解整个UI架构的重中之重，温故而知新，重看这篇文章，获益匪浅！


window和view的关系，window是view的子类但不需要有superView，且可以作为view或viewController的管理者

https://developer.apple.com/library/ios/documentation/windowsviews/conceptual/viewpg_iphoneos/WindowsandViews/WindowsandViews.html


window创建完使用makeKeyAndVisible或设置hidden来显示和隐藏，通过访问UIApplication的windows属性来获得所有的window，window创建完后需要被保留，否则会被ARC自动释放——这是常见的陷阱。

https://developer.apple.com/library/ios/documentation/windowsviews/conceptual/viewpg_iphoneos/CreatingWindows/CreatingWindows.html


view功能强大，绝非三两句话就可以说完，但有一点非常值得重视，view的呈现是由其对应的layer完成的，但layer可以独立于view单独出现，所以某些时候使用layer层次可能比用view层次来呈现更省内存，可能获得关键的性能提升。

https://developer.apple.com/library/ios/documentation/windowsviews/conceptual/viewpg_iphoneos/CreatingViews/CreatingViews.html


UIView的transform矩阵怎么构造，方法多多，使用transform属性之前，很有必要看懂这个文档（其中CTM意为current tranformation matrix）：

顺便说下旋转的理解，(x+yi)*e^(ia)，a表示弧度，就不难理解旋转矩阵了。

https://developer.apple.com/library/ios/documentation/GraphicsImaging/Reference/CGAffineTransform/Reference/reference.html