# awesome-web

##《揭秘css》小练习

## web
 * hsla(色调,饱和度,亮度,透明度) 色调0-360,0、360红色,120绿色,240蓝色,注意饱和度必须写成百分比形式,建议使用hsla而不是rgba,因为它的字符长度更短，重复率更低。
 * currentColor 当前标签继承的文字颜色,适用于自动与文本颜色保持一致的属性
 * background-clip属性,border-box 背景剪裁至边框 padding-box 背景剪裁至内边框 content-box 背景剪裁至内容框
 * column-width 规定列的宽度 column-count规定分成几列 column-gap 规定列间距
 * box-shadow: inset内阴影 水平阴影的位置 垂直阴影的位置 模糊距离 阴影尺寸 颜色,box-shadow text-shadow 都可添加多个阴影
 * background-attachment 属性设置背景图像是否固定或者随着页面的其余部分滚动 scroll默认,fixed,inherit
 * background-origin 属性规定 background-position 属性相对于什么位置来定位 border-box padding-box content-box
 * outline: 轮廓边框宽度 样式 颜色, outline会占据margin
 * box-sizing: border-box; 盒模型的宽度=内容宽度+padding+border

 * linear-gradient = linear-gradient([ [ <angle> | to <side-or-corner> ] ,]? <color-stop>[, <color-stop>]+)
   <side-or-corner> = [left | right] || [top | bottom]
   <color-stop> = <color> [ <length> | <percentage> ]?
   取值：
   下述值用来表示渐变的方向，可以使用角度或者关键字来设置：
   * angle：
   用角度值指定渐变的方向（或角度）。
   to left：
   设置渐变为从右到左。相当于: 270deg
   to right：
   设置渐变从左到右。相当于: 90deg
   to top：
   设置渐变从下到上。相当于: 0deg
   to bottom：
   设置渐变从上到下。相当于: 180deg。这是默认值，等同于留空不写。
   to bottom right 
   渐变到右下 325deg
   to bottom left 
   渐变到左下 45deg 
   * color：指定颜色。
    color-stop 用于指定渐变的起止颜色：
   * length：用长度值指定起止色位置。不允许负值
   * percentage：用百分比指定起止色位置。定义止色位置去掉渐变效果,改为实色块效果
 * repeating-linear-gradient 实现可重复的渐变
 * 径向渐变 radial-gradient ``
 
 ```
 radial-gradient([<bg-position> || <angle>,]? [<shape> || <size>,]? <color-stop>, <color-stop>[, <color-stop>]*);
 径向渐变到目前还不支持Opera的内核浏览器
 ```
 
 * vh and vw
   * 响应式web设计离不开百分比。但是，CSS百分比并不是所有的问题的最佳解决方案。CSS的宽度是相对于包含它的最近的父元素的宽度的。但是如果你就想用视口（viewpoint）的宽度或者高度，而不是父元素的，那该肿么办？ 这就是 vh 和 vw 单位为我们提供的。
   1vh 等于1/100的视口高度。栗子：浏览器高度900px, 1 vh = 900px/100 = 9 px。同理，如果视口宽度未750， 1vw = 750px/100 = 7.5 px。
   * 可以想象到的，他们有很多很多的用途。比如，我们用很简单的方法只用一行CSS代码就实现同屏幕等高的框。
   
   ```
    .slide {
        height: 100vh;
    }
   ```
    
   * 假设你需要一个和屏幕同宽的标题，你只要设置这个标题的font-size的单位为vw，那标题的字体大小就会自动根据浏览器的宽度进行缩放，以达到字体和viewport大小同步的效果，
   
  * requestAnimationFrame html API
    * requestAnimationFrame 是浏览器用于定时循环操作的一个接口，类似于setTimeout，主要用途是按帧对网页进行重绘。
    * 设置这个API的目的是为了让各种网页动画效果（DOM动画、Canvas动画、SVG动画、WebGL动画）能够有一个统一的刷新机制，节省系统资源，提高系统性能，改善视觉效果。
    * 代码中使用这个API，就是告诉浏览器希望执行一个动画，让浏览器在下一个动画帧安排一次网页重绘。
    * requestAnimationFrame的优势，在于充分利用显示器的刷新机制，比较节省系统资源。显示器有固定的刷新频率（60Hz或75Hz），也就是说，每秒最多只能重绘60次或75次，requestAnimationFrame的基本思想就是与这个刷新频率保持同步，利用这个刷新频率进行页面重绘。此外，使用这个API，一旦页面不处于浏览器的当前标签，就会自动停止刷新。这就节省了CPU、GPU和电力。
    * 不过有一点需要注意，requestAnimationFrame是在主线程上完成。这意味着，如果主线程非常繁忙，requestAnimationFrame的动画效果会大打折扣。
    * requestAnimationFrame 使用一个回调函数作为参数。这个回调函数会在浏览器重绘之前调用。
    * 目前，主要浏览器Firefox 23 / IE 10 / Chrome / Safari）都支持这个方法。可以用下面的方法，检查浏览器是否支持这个API。如果不支持，则自行模拟部署该方法。
    
    ```
     window.requestAnimFrame = (function(){
          return  window.requestAnimationFrame       || 
                  window.webkitRequestAnimationFrame || 
                  window.mozRequestAnimationFrame    || 
                  window.oRequestAnimationFrame      || 
                  window.msRequestAnimationFrame     || 
                  function( callback ){
                    window.setTimeout(callback, 1000 / 60);
                  };
        })();
     // 上面的代码按照1秒钟60次（大约每16.7毫秒一次），来模拟requestAnimationFrame。
     ```
    
     * 使用requestAnimationFrame的时候，只需反复调用它即可。
     
     ```
     function repeatOften() {
       // Do whatever
       requestAnimationFrame(repeatOften);
     }
     
     requestAnimationFrame(repeatOften);
     ```
     
 * animation-fill-mode : none | forwards | backwards | 
   * both; none 不改变默认行为。
   * forwards 当动画完成后，保持最后一个属性值（在最后一个关键帧中定义）。
   * backwards 在 animation-delay 所指定的一段时间内，在动画显示之前，应用开始属性值（在第一个关键帧中定义）
   * both 向前和向后填充模式都被应用。
  
 * $('body').on('mousedown', '.h-btn', function(e) {})
   * VS $('.h-btn').on('mousedown', function(e) {}) 第一种方法可以获取到js 动态创建的.h-btn元素,而第二种方法只能获取已有的.h-btn元素
   
 * $(function(){}) 等价于 $(document).ready(function(){}); 表示文档结构已经加载完成（不包含图片等非文字媒体文件)
 * 浏览器对于Javascript的运行有两大特性：
   * 载入后马上执行
   * 执行时会阻塞页面后续的内容（包括页面的渲染、其它资源的下载）。
   * 如果有多个js文件被引入,这些js文件被被串行地载入，并依次执行。
     * 所以，如果你的javascript想操作后面的DOM元素，基本上来说，浏览器都会报错说对象找不到。因为Javascript执行时，后面的HTML被阻塞住了，DOM树时还没有后面的DOM结点。所以程序也就报错了。
     
 * js加载总结
   
   ```
   <html> 
   <head>
      <title>Script Example</title> 
   </head>
   <body>
       <div>
       <script type="text/javascript">
           alert("今天的日期是： " + (new Date()).toDateString());
       </script> 
       </div>
   </body> 
   </html>
   ```
   
   * 当浏览器遇到一个<script>标签时，正如上面的HTML页面那样，没办法知道Javascript是不是在div标签中添加或者删除内容，这样浏览器就停止，运行完当前的脚本，然后再继续执行下面的内容。当然使用外链也是这样的过程，遇到src外链Javascript代码，浏览器也是首先加载这个外部Javascript文件，然后解析运行此Javascript代码，至于什么时候执行，完全要下载此文件需要多久的时间。
   
   ```
   <html> 
   <head>
       <script type="text/javascript" src="file1.js"></script>
       <script type="text/javascript" src="file2.js"></script>
       <script type="text/javascript" src="file3.js"></script>
       <link rel="stylesheet" type="text/css" href="styles.css">
   </head>
   <body>
       <div>
           这是Javascript文件引入的例子。
       </div>
   </body> 
   </html>
   ```
   
   * 脚本位置 这样的写法理论上是没有任何问题的，但是这里就存在了性能和体验的问题。
   * 上面的代码加载了3个外部文件，每个文件在加载的过程中阻塞了页面的解析，浏览器只有等待它们下载并运行了Javascript代码之后，页面才能继续，这我们在上面已经提到过了。最致命的问题就是，把Javascript文件放在顶部，在加载Javascript文件比较慢的时候会出现空白页，以至于用户看不到页面，更不要说交互网页，推荐的办法就是，把所有的Javascript文件，包括外链的文件挡在<body>标签底部位置，减少对整个页面加载的影响。
   
   * 延迟脚本 <script>标签的defer属性 async和defer的相同点是采用并行下载，在下载的过程中都是不会产生阻塞。区别在于执行时机，async是加载完成后自动执行，而defer需要等待页面完成后执行。
   * 动态创建script标签
   * lazyload库
   
   * 将所有的<script>标签放置在页面底部，紧靠body标签的上方，这些方法可以保证页面在脚本运行之前完成解析。讲脚本打包，尽量合并页面的Javascript文件，文件越少，页面的加载速度就会越快，无论是内联的还是外链的Javascript文件。
   
 * <label> 标签为 input 元素定义标注。
   * label 元素不会向用户呈现任何特殊效果。不过，它为鼠标用户改进了可用性。如果您在 label 元素内点击文本，就会触发此控件。就是说，当用户选择该标签时，浏览器就会自动将焦点转到和标签相关的表单控件上。
     <label> 标签的 for 属性可把 label 绑定到另外一个元素, for 属性应当与相关元素的 id 属性相同。
 * user-select：none | text | all | element css3属性 默认text
    none：文本不能被选择
    text：可以选择文本
    all：当所有内容作为一个整体时可以被选择。如果双击或者在上下文上点击子元素，那么被选择的部分将是以该子元素向上回溯的最高祖先元素。
    element：可以选择文本，但选择范围受元素边界的约束
  
 * img属于行内替换元素。height/width/padding/margin均可用。效果等于块元素。
   行内非替换元素，例如, height/width/padding top、bottom/margin top、bottom均无效果。只能用padding left、right改变宽度。
   行内元素设置width无效，height无效(可以设置line-height)，margin上下无效，padding上下无效 padding左右有效
   
 * a标签包裹img产生4px间隙的问题：
   图片文字等inline元素默认是和父级元素的baseline对齐的，而baseline又和父级底边有一定距离（这个距离和 font-size，font-family 相关），所以设置 vertical-align:top/bottom/text-top/text-bottom 都可以避免这种情况出现。其他的block元素中包含img也会有这个现象。
   或设置a标签的父元素line-height: 0;
   或设置img display: block也变成块级元素
 * -webkit-touch-callout 是一个 不规范的属性（unsupported WebKit property），它没有出现在 CSS 规范草案中。
   当你触摸并按住触摸目标时候，禁止或显示系统默认菜单。在iOS上，当你触摸并按住触摸的目标，比如一个链接，Safari浏览器将显示链接有关的系统默认菜单。这个属性可以让你禁用系统默认菜单。
 * -webkit-font-smoothing 属性
   字体平滑,该属性定义文本的平滑属性。
   目前该属性已从W3C标准中移除，慎用！
   none	不平滑，字体具有锯齿锋利边缘，适用于小像素的文本。
   subpixel-antialiased	使用亚像素平滑。
   antialiased	使用灰阶平滑。
 * background 
   * background-clip  规定背景的绘制区域
   background-clip: border-box|padding-box|content-box;
   
   * background-origin 属性规定 background-position 属性相对于什么位置来定位。
   background-origin: padding-box|border-box|content-box;
   
   * background-attachment 属性设置背景图像是否固定或者随着页面的其余部分滚动。
   scroll	默认值。背景图像会随着页面其余部分的滚动而移动。
   fixed	  当页面的其余部分滚动时，背景图像不会移动。
   inherit	规定应该从父元素继承 background-attachment 属性的设置。
 * mvvm
   * model: 模型
   * view: 视图
   * viewmodel: 连接视图和模型
   * e.g.  vue.js
   model: 模型 原生javascript对象
   view: 视图 实际看到的dom结构
   viewmodel:  vue.js提供的vue构建函数 var vm = new Vue({})创造一个实例

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
 
 * 有时代码易维护和代码量少不可兼得
   * e.g. 为元素添加一个10px的边框,但左侧不加边框 border-width: 10px 10px 10px 0;但若以后需要改动边框的宽度，需要同时改3个地方。那么以下这种方式可能更好 border-width: 10px; border-left: 0;
 * 当需要在较大分辨率下得到固定宽度,使用max-width
 * html元素也可分为替换元素和非替换元素。替换元素是浏览器根据标签的元素和属性判断显示的内容,如 `<input type="text"/>` 是文本输入框,type属性是radio时是单选按钮, `<img src="">`由标签元素img和属性决定显示的内容,如img input textarea select object都是替换元素,没有实质内容
 * 不要忘记为替换元素设置一个max-width:100%;
 * 如果需求背景图片铺满整个容器,使用background:cover 优于移动端通过css把大图缩小显示
