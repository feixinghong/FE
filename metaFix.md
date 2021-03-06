#	metaFix.js的使用方法

### metaFix.js用于动态设定viewport的值，以使得我们可以按照设计图的尺寸进行设置。

> 在require引用中此模块的引用代号为 `MetaFix` ,需要注意的是，此模块只需要引用并不用做任何设置，
代码内部默认执行了 `MetaFix.viewport(640);`。

#	API

### MetaFix.viewport(designWidth)
 此方法为默认执行方法,且传入的参数为640.
 此方法是通过动态改变viewport的值进行操作的
* designWidth : 设计图的宽度尺寸，单位为px

### MetaFix.zoom(designWidth)
 此方法是通过改变body的zoom属性来达到缩放页面的效果的
* designWidth : 设计图的宽度尺寸，单位为px

由于该模块内部自动执行了 `MetaFix.viewport(640);`，所以此方法作为备选方法使用，
如果需要调用此方法，则需要手动调用 `MetaFix.zoom(640)`方法。
此方法内部占用了`id='M_zoom'` 和 `class='.M_zoom'`,使用时请注意。
> 此方法内部默认会将viewport设置成为如下形式:
 `<meta id="meta_viewport" name="viewport" content="width=device-width, initial-scale=1.0, minimum-scale=1.0, maximum-scale=1.0, user-scalable=no">`，此方法可能会影响到高度的获取，例如:$(window).height(),此时如果想要获取window的高度就需要$(window).height()/_zoom

另外，此方法中提供了两个全局变量，_zoom表示页面的缩放比例，_os是一个对象，包含了系统类型、系统版本等相关信息，
Android系统下的形式如下：
```html
{android: true, version: "4.4.4"}
```
ios系统下的形式如下：
```html
{iphone: true, ios: true, version: "7.0"}
```
