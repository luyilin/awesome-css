# awesome-css
🍭css

《揭秘css》小练习

## css 属性
 * hsla(色调,饱和度,亮度,透明度) 色调0-360,0、360红色,120绿色,240蓝色,建议使用hsla而不是rgba,因为它的字符长度更短，重复率更低。

## css编码技巧
 * 提高代码可维护性要尽量减少改动时要编辑的地方
  
  e.g.
 ```
 font-size:20px;
 padding:6px 12px;
 background: #58a linear-gradient(#77a0bb, #58a);
 border-radius: 4px;
 box-shadow: 0 1px 5px gray;
 color: white;
 text-shadow:0 -1px 1px #335166;
 line-height:30px;
 ```
 * 代码改善点:
   * 如果改变字号,则需同时调整行高。(某些值相互依赖时,应该用代码表示相互关系)
   * padding border-radius box-shadow text-shadow line-height等参数应随父元素的字号改变
   * em相对父元素的字体大小,rem相对html根元素的字体大小,px相对显示器屏幕分辨率
 修改后的代码:
 
 ```
 font-size: 125% /* e.g.父元素的font-size:16px 相对父元素的字体大小*/
 padding: .3em .8em;
 background: #58a linear-gradient(hsla(0,0%,100%,.2),transparent); 
 /* 产生主色调的亮色或暗色变体,可用半透明的黑色或白色叠加在主色调上*/
 border-radius: .2em;
 box-shadow: 0 .05em .25em rgba(0,0,0,.5);
 line-height: 1.5; /* line-height: 150% 根据父元素继承来的font-size计算 line-height: 1.5 根据自身元素的font-size计算*/
 ```
   
