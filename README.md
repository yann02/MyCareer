# MyCareer
My learning record of Android development.

## UI 
### 动画
#### Property Animation
* ValueAnimator
> 在监听动画的方法里修改对象属性，来达到动画的效果。  
* ObjectAnimator
> 继承自ValueAnimator，对对象的可set/get属性动画，用法更简单，不需要在监听器中更新对象属性。但是可以设置动画的监听器，监听动画完成等事件。监听动画完成，可以在动画完成后执行一些我们想要的操作。  

#### View Animation
> 有两大约束
* 只是修改视图的绘制，并不会修改视图的位置。尤其是只有点击初始位置才能接收到点击事件  
* 只能对View使用
---
### 图片选择器
#### 推荐使用的库
1. [__PictureSelector__](https://github.com/LuckSiege/PictureSelector)
---
### 字符串资源引用
* 省略号
> …
