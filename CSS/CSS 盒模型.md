# CSS box model 盒模型

在CSS裡，對於HTML每個元素都視為一個盒子，然後針對這個盒子作出調整。

Box Model 主要由四個部分組成，由內而外分別是 Content (內容)、Padding（內邊距）、Broder(邊框)、Margin（外邊距）。
![](https://drafts.csswg.org/css2/images/boxdim.png)

padding 及 border 相當於在 content 外層加上去，都會影響整個box 的高度及寬度。

## content box
瀏覽器一般默認的是： `box-sizing: content-box` 即
- 內容就是盒子的邊界
- 寬度計算只包含 `content`

![](https://www.roy.coffee/content/images/2022/02/content-box.png)

假設今天想要一個 box 是 200x100，想要加個padding 及 border 等等，又不想要這個 box 因此而變大，就可以使用`box-sizing: border-box` 屬性去調整。

## border box
- 用`box-sizing: border-box`的話，就會把 padding 等地考慮進來，而自動做內縮調整
- 邊框是盒子的邊界
- 寬度計算則包含了 `border padding content`

![](https://www.roy.coffee/content/images/2022/02/border-box.gif)

## margin 合併
### 哪些情況會合併？
- 父元素及子元素上下之間重疊會合併
- 兄弟元素上下之間重疊會合併

*marign 左右重疊位置不會合併*

### 不合併的方法： 
1. 父子
- `padding/broder`
- `overflow: hidden`
- `display:flex`

2. 兄弟合併是符合預期的，但也可以用：
- `display: inline-block`

