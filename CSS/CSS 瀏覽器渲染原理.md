## CSS 瀏覽器渲染過程

當與網站的伺服器建立的連接，在瀏覽器發出HTTP GET請求，一般來說是一個HTML文件。伺服器收到請求並且響應返回HTML文件。

瀏覽器收到HTML文件，便會開始解析，並把數據轉為 HTML樹 (DOM)和 CSS樹(CSSOM)，並通過渲染把 DOM 和 CSSOM 合併成渲染樹(Render tree)，並進行佈局(Layout)、繪製(Paint)及合成(Compose)。

### 渲染過程：
1. 根據 HTML 建構 HTML樹 (DOM)
2. 根據 CSS 建構 CSS 樹 (CSSOM)
3. 將兩棵機合併成渲染樹 (Render tree)
4. Layout 佈局
5. Painr 繪製
6. Compose 合成

3種更新方式
1. js>style>layout>paint>composite
例子：div.remove() 觸發當前消失，其他元為relayout
2. js>style>paint>composite
例子：改變 background-color，直接 repaint + composite
3. js>style>composite
例子：transform，只需 composite。

## CSS 製作動畫 

### `transform`
### Synatax
```
/* Keyword values */
transform: none;

/* Function values */
transform: matrix(1.0, 2.0, 3.0, 4.0, 5.0, 6.0);
transform: matrix3d(1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1);
transform: perspective(17px);
transform: rotate(0.5turn);
transform: rotate3d(1, 2.0, 3.0, 10deg);
transform: rotateX(10deg);
transform: rotateY(10deg);
transform: rotateZ(10deg);
transform: translate(12px, 50%);
transform: translate3d(12px, 50%, 3em);
transform: translateX(2em);
transform: translateY(3in);
transform: translateZ(2px);
transform: scale(2, 0.5);
transform: scale3d(2.5, 1.2, 0.3);
transform: scaleX(2);
transform: scaleY(0.5);
transform: scaleZ(0.3);
transform: skew(30deg, 20deg);
transform: skewX(30deg);
transform: skewY(1.07rad);

/* Multiple function values */
transform: translateX(10px) rotate(10deg) translateY(5px);
transform: perspective(500px) translate(10px, 0, 20px) rotateY(3deg);

/* Global values */
transform: inherit;
transform: initial;
transform: revert;
transform: unset;
```

## CSS Animations
### Synatax
-   `@keyframes`
-   `animation-name`
-   `animation-duration`
-   `animation-delay`
-   `animation-iteration-count`
-   `animation-direction`
-   `animation-timing-function`
-   `animation-fill-mode`
-   `animation`