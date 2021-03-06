# 像素
---

### CSS像素(逻辑像素（设备独立像素）dip)

  css像素等于逻辑像素

  
### 设备像素（物理像素)

  设备像素（物理像素)，device pixels，单位是px。
  当我们说某个手机的分辨率的时候，其实在描述的就是它的设备像素。
  px可以理解为是一个相对大小，因为受承载设备的影响，同样的PX大小，在不同的设备下人眼所理解的“大”与“小”是不一样的。

### 逻辑像素（设备独立像素）dip

  逻辑像素（logic point 、Device Independent Pixels） 单位是pt(point)，也称为设备独立像素。印刷行业常用单位。大小为1/72英寸，是行业标准的计量单位。是个绝对单位，在此机型下，只存在一套准则。但在实际生活中，机器的大小是多种多样的。
  
### 设备像素比 dpr

  指的是一个设备上的 物理像素和独立像素的比值 
  dpr = 设备像素/设备独立像素(css像素)
  2:1 说明1个css像素等于4个设备像素
  可通过window.devicePixelRadio获取

#### 像素密度 dpi

  dots per inch ， 直接来说就是一英寸多少个像素点。常见取值 120，160，240。我一般称作像素密度，简称密度。
  

  手机型号 | 设备（物理像素）px  | 逻辑（设备独立、CSS）像素pt | dpr
   :-------| :--- | :---| :---|
   iPhone6| 1334 * 750 |  667 * 375 | 2
   iPhoneX | 2436 * 1125 | 812 * 375 | 3
  
***

# viewport
  [参考文档](https://www.cnblogs.com/2050/p/3877280.html)
  viewport 是用户网页的可视区域。

  viewport 翻译为中文可以叫做"视区"。

  手机浏览器是把页面放在一个虚拟的"窗口"（viewport）中，通常这个虚拟的"窗口"（viewport）比屏幕宽，这样就不用把每个网页挤到很小的窗口中（这样会破坏没有针对手机浏览器优化的网页的布局），用户可以通过平移和缩放来看网页的不同部分。

  - layout viewport

    layout viewport是网页布局的区域，是html标签的父级容器。
    **layout viewport用css像素来衡量尺寸，在缩放、调整浏览器窗口的时候不会改变。
    缩放、调整浏览器窗口改变的只是visual viewport。**
    可以通过document.documentElement.clientWidth获取
    
    iphone8 下是 980


  - visual viewport

    visual viewport就是显示在屏幕上的网页区域。通过window.innerWidth获取。 代表浏览器可视区域的大小。
 


  **两者关联**

    layout就相当于是画布，在不同的手机下都不一样，承载了我们的网页。而visual就是我们开发的网页，它相对于layout是动态变化的，可能大于画布、也可能小于画布。这是就需要通过缩放等、滑动滚动条等去展示其他页面的部分。

  - idea viewport (理想尺寸)

    ideal viewport并没有一个固定的尺寸，不同的设备拥有有不同的ideal。
    现在越来越多的网站都会为移动设备进行单独的设计，所以必须还要有一个能完美适配移动设备的viewport。**所谓的完美适配指的是，首先不需要用户缩放和横向滚动条就能正常的查看网站的所有内容；第二，显示的文字的大小是合适，比如一段14px大小的文字，不会因为在一个高密度像素的屏幕里显示得太小而无法看清，理想的情况是这段14px的文字无论是在何种密度屏幕，何种分辨率下，显示出来的大小都是差不多的。当然，不只是文字，其他元素像图片什么的也是这个道理。这个viewport叫做 ideal viewport，也就是第三个viewport——移动设备的理想idea viewport。**

---
  Layout viewport是为了能将电脑上的网页正确的显示到手机上。当浏览器拿到一个网页时，首先会渲染到这个layout viewport里面。可是现在有很多网页会针对手机做专门的设计，比如现在的一些H5活动页，设计的尺寸就是在手机上看的。此时如果还是把网页渲染到这个大的layout viewport上，实在是有点不合适了。**所以，还应该有个ideal viewport，这个ideal viewport应该与手机屏幕大小的相同，确切来说，等于visual viewport的大小。把页面渲染到这个ideal viewport里面，就能在visual viewport中完美显示。**


# meta 
---

  ```html
  <meta name="viewport" content="width=device-width, initial-scale=1.0 maximum-scale=1.0, user-scalable=0">
  ```

width	设置layout viewport  的宽度，为一个正整数，或字符串"width-device"
initial-scale	设置页面的初始缩放值，为一个数字，可以带小数
minimum-scale	允许用户的最小缩放值，为一个数字，可以带小数
maximum-scale	允许用户的最大缩放值，为一个数字，可以带小数
height	设置layout viewport  的高度，这个属性对我们并不重要，很少使用
user-scalable	是否允许用户进行缩放，值为"no"或"yes", no 代表不允许，yes代表允许


  
  属性 | 含义  |
   :-------| :--- |
   width| 设置layout viewport  的宽度，为一个正整数，或字符串"width-device"
   initial-scale	 | 设置页面的初始缩放值，为一个数字，可以带小数|
   minimum-scale	 | 允许用户的最小缩放值，为一个数字，可以带小数
   maximum-scale	 | 允许用户的最大缩放值，为一个数字，可以带小数
   height | 设置layout viewport  的高度，这个属性对我们并不重要，很少使用
   user-scalable | 是否允许用户进行缩放，值为"no"或"yes", no 代表不允许，yes代表允许

# 开发实践

  - 推荐使用rem flexible。以750px基准，分成十份。
  - px2rem安装包,px自动转化rem
