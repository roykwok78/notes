# 語句 Statment
JavaScript 程式執行單位是行 line，一行一行執行。每一行就是一個語句。

語句 Statment 例子：

```
var a = 1
```

例子使用了`var`的命令，聲明了變量a，並把 1 賦值到 a。

# 表達式 expression

```
var a = 1 + 3
```

表達式 expression 例子：

`1 + 3` 是表達式，即是會得到返回值的算，值是3。

`add(1,2)` 的表達式的值為函數有返回值。

`console.log` 表達式的值為函數本身

`console.log(3)`  表達式的值是 `undefined`

語句與表達式的分別是前者只是執行操作，一般不需要返回值；後者則為了得到返回值，且一定會返回一個值。

return 後不能加回車

# 標識符 identifier 
標識符是指用來識別各種值的合法命名。最常見是變量可或函數名。JavaScript 標籤符對大小寫敏感。例如 `a` 和 `A` 是兩個不同標識符。

JavaScript 有一套命名規則，不合符規則的 JavaScript 引擎遇到時會報錯。

## JavaScript 命名規則
- 第一個字符是可以任意 Unicode 字母。包括英文字母和其語言言字母。以及美元符號 `$` 和下劃線 `_` 。
- 第二個字符及後面的字符，除了 Unicode 字母、美元符號 `$` 和下劃線 `_`，還可以用數字 `0-9`

以下都是合符命名規則的例子：
```
arg0
$1
_me
```

不合符命名規則的例子：
```
1$
()
a+b
-d
99
```

此外有以下英文字符也不合符命名規則：
```
arguments、break、case、catch、class、const、continue、debugger、default、delete、do、else、enum、eval、export、extends、false、finally、for、function、if、implements、import、in、instanceof、interface、let、new、null、package、private、protected、public、return、static、super、switch、this、throw、true、try、typeof、var、void、while、with、yield。
```

# 條件語句
JavaScript 提供 `if` 及 `switch` 的條件語句。只有滿足條件才執行。

## if 
`if` 會根據判斷一個表達式的布爾值 `true` 或 `false` 去執行不同語句。

例子：
```
if(布爾值) 
語句；

//或

if(布爾值){
語句;
}
```

布爾值往往由一個表達式產生，必須放在 `()` 裡。如果表達式返回 `true` 就會執行後面的語句。如返回 `false` 則會跳過語句。如果想執行多個語句，在 `()` 之後必須加上 `{}` 代表代碼塊。建議一律使用`{}`，方便插入語句。

## if else
在 `if` 代碼塊後，還可以跟一個 `else` 的代碼塊。表示不滿足條件時，所要執行的代碼。

例子
```
if (m === 3){
滿足條件時，執行語句
} else {
不滿足條件時，執行的語句
}
```

例子中判斷變量 `m` 是否等於3，等於就執行 `if` 的代碼塊，否則執行 `else` 的代碼塊。

如果對一個變量需要進行多次判斷時，多個 `if...else` 語句可以連寫在一起。
```
if(m === 0){
//...
} else if (m === 1){
//...
} else if (m === 2){
//...
} else {
//...
}
```

## while
`while` 語句包括一個循環條件和一段代碼塊，只要條件為真，就不斷循環執行代碼塊。

```
while (條件)
語句;

// 或者

while (條件) ｛
語句;
}
```
  
`while` 語句的循環條件一個表達式，必須放在 `()` 裡。如果想執行多個語句，在 `()` 之後必須加上 `{}` 代表代碼塊。建議一律使用`{}`，方便插入語句。

## for
`for` 語句是循環命令的另一種形式，可以指定循環的起點、終點和終止條件。它的格式如下。

```
for (初始化表達式; 條件; 遞增表達式)
 語句
  
// 或者

for (初始化表達式; 條件; 遞增表達式) {
 語句
}
```

for語句後面的括號裡面，有三個表達式。
-   初始化表達式（initialize）：確定循環變量的初始值，只在循環開始時執行一次。
-   條件表達式（test）：每輪循環開始時，都要執行這個條件表達式，只有值為真，才繼續進行循環。
-   遞增表達式（increment）：每輪循環的最後一個操作，通常用來遞增循環變量。

```
var x = 3

for(i = 0;i < x; i++){
console.log(i)
}
// 0
// 1
// 2
```

上面代碼中，初始化表達式是`var i = 0`，即初始化一個變量`i`；測試表達式是`i < x`，即只要`i小於x`，就會執行循環；遞增表達式是`i++`，即每次循環結束後，`i` 增大1。

## contiune / break
`break` 語句和 `continue` 語句都具有跳轉作用，可以讓代碼不按既有的順序執行。

`break` 用於跳出語句，例子：
```
var x = 5
for(i = 0; i < x; i++ ){
console.log(i)
if (i === 2){
break;
}
}

// 0
// 1
// 2
```

上面代碼 `i` 等於2，就會跳出循環。

`continue` 是立即跳出本輪循環，跳到循環頭部，立即執行下一輪循環。

```
var x = 3
for(i = 0; i < x; i++ ){
if (i === 1){
continue;
}console.log(i)
}

// 0
// 2
```

上面代碼 `i` 等於1時，就會跳出立即跳出循環，跳到循環頭部，立即執行下一輪循環。因此第二次循環時沒有執行 `console.log(i)` ，沒有打印出1。

## label
JavaScript 語言允許，語句的前面有標籤（label），相當於定位符，用於跳轉到程序的任意位置，標籤的格式如下。

```
label:
語句
```

label 的值可以是任何的非保留字的 JavaScript 標識符， statement 可以是任意你想要標識的語句（塊）。

label 通常與 `break` 或 `continue` 語句配合使用，跳出特定循環

label 與 `break` 配合使用例子：
```
var num = 0;
label1:
for (var i = 0 ; i < 10 ; i++){
 for (var j = 0 ; j < 10 ; j++){
 if( i == 5 && j == 5 ){
 break label1; // 在 i = 5，j = 5 時，跳出所有循環，
 // 返回到整個 label1 下方，繼續執行
 }
 num++;
 }
}

alert(num); // 輸出 55
```

label 與 `continue` 配合使用例子：
```
var num = 0;
label2:
for(var i = 0; i < 10; i++) {
  for(var j = 0; j < 10; j++) {
    if(i == 5 && j == 5) {
      continue label2;
    }
    num++;
  }
}
alert(num);  // 95
```

