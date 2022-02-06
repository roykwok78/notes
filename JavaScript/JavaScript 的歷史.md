# JavaScript
JavaScript 由 BRENDAN EICH 使用了10天時間把原型設計了出來。

## JavaScript 緣起
1994年 網景公司（Netscape）發佈了一款瀏覽器，需要一種網頁的腳本語言，使得瀏覽器與網頁可以互動。

1995年 Sun公司將 Oak 語言改名為 Java。當時Sun公司宣稱，Java可以「一次編寫，到處運行」(Write Once, Run Anywhere)。在當時看來很可能成為主流的編程語言。

網景公司作為第一款比較成熟的瀏覽器，因此與Sun公司結成聯盟。它不僅允許Java程序以applet（小程序）的形式，直接在瀏覽器中運行；甚至還考慮直接將Java作為腳本語言嵌入網頁，只是因為這樣會使HTML網頁過於複雜，後來才不得不放棄。

當時網景公司的整個管理層，都是 Java 語言的信徒，Sun公司完全介入網頁腳本語言的決策。因此，Javascript後來就是網景和Sun兩家公司一起攜手推向市場的，這種語言被命名為"Java+script"並不是偶然的。

1995年4月，BRENDAN EICH 受網景公司錄用。

1995年5月，網景公司決定，未來網頁腳本的語言必須看上去與 Java 相似，但又要比 Java 簡單，使業餘網頁製作者都很快上手。於是指派 BRENDAN EICH 設計這種簡化版的 Java 語言。

BRENDAN EICH 對Java一點興趣也沒有。為了應付公司安排的任務，他只用10天時間就把Javascript設計出來了。

這也導致了由於設計時間太短，語言的一些細節考慮得不夠嚴謹，導致後來很長一段時間，Javascript寫出來的程序混亂不堪。

總的來說，他的設計思路是這樣的：
- 借鑒C語言的基本語法；
- 借鑒Java語言的數據類型和內存管理；
- 借鑒Scheme語言，將函數提升到"第一等公民"（first class）的地位；
- 借鑒Self語言，使用基於原型（prototype）的繼承機制。

所以，Javascript語言實際上是兩種語言風格的混合產物
- 簡化的函數式編程
- 簡化的面向對象編程

## JavaScript 的10個設計缺陷
      

**1.不適合開發大型程序**

Javascript沒有名稱空間（namespace），很難模塊化；沒有如何將代碼分布在多個文件的規範；允許同名函數的重復定義，後面的定義可以覆蓋前面的定義，很不利於模塊化加載。

**2.非常小的標準庫**

Javascript提供的標準函數庫非常小，只能完成一些基本操作，很多功能都不具備。

**3.null和undefined**

null屬於對象（object）的一種，意思是該對象為空；undefined則是一種數據類型，表示未定義。

```
typeof null; // object
typeof undefined; // undefined
```

兩者非常容易混淆，但是含義完全不同。

```
　var foo;
　　alert(foo == null); // true
　　alert(foo == undefined); // true
　　alert(foo === null); // false
　　alert(foo === undefined); // true
```

在編程實踐中，null幾乎沒用，根本不應該設計它。

**4.全局變量難以控制**

Javascript的全局變量，在所有模塊中都是可見的；任何一個函數內部都可以生成全局變量，這大大加劇了程序的複雜性。

```
　　a = 1;
　　(function(){
　　　　b=2;
　　　　alert(a);
　　})(); // 1
　　alert(b); //2
```

**5.自動插入行尾分號**

Javascript的所有語句，都必須以分號結尾。但是，如果你忘記加分號，解釋器並不報錯，而是為你自動加上分號。有時候，這會導致一些難以發現的錯誤。

比如，下面這個函數根本無法達到預期的結果，返回值不是一個對象，而是undefined。

```
function(){
　　　　return
　　　　　　{
　　　　　　　　i=1
　　　　　　};
　　}
```

**6.加號運算符**

+號作為運算符，有兩個含義，可以表示數字與數字的和，也可以表示字符與字符的連接。

```
alert(1+10); // 11
alert("1"+"10"); // 110
```

如果一個操作項是字符，另一個操作項是數字，則數字自動轉化為字符。
```
alert(1+"10"); // 110
alert("10"+1); // 101
```

這樣的設計，不必要地加劇了運算的複雜性，完全可以另行設置一個字符連接的運算符。

**7.NaN**

NaN是一種數字，表示超出瞭解釋器的極限。它有一些很奇怪的特性：

```
NaN === NaN; //false
NaN !== NaN; //true
alert( 1 + NaN ); // NaN
```

與其設計NaN，不如解釋器直接報錯，反而有利於簡化程序。

**8.數組和對象的區分**

由於Javascript的數組也屬於對象（object），所以要區分一個對象到底是不是數組，相當麻煩。Douglas Crockford的代碼是這樣的：

```
if ( arr &&
typeof arr === 'object' &&
typeof arr.length === 'number' &&
!arr.propertyIsEnumerable('length')){
alert("arr is an array");
}
```

**9.== 和 === 

== 用來判斷兩個值是否相等。當兩個值類型不同時，會發生自動轉換，得到的結果非常不符合直覺。

```
　"" == "0" // false

　　0 == "" // true  

　　0 == "0" // true

　　false == "false" // false 

　　false == "0" // true

　　false == undefined // false
  
　　false == null // false

　　null == undefined // true

　　" \t\r\n" == 0 // true
```

因此，推薦任何時候都使用 === （精確判斷）比較符。

**10.基本類型的包裝對象**

Javascript有三種基本數據類型：字符串、數字和布爾值。它們都有相應的建構函數，可以生成字符串對象、數字對象和布爾值對象。

```
new Boolean(false);
new String("Hello World");
```

與基本數據類型對應的對象類型，作用很小，造成的混淆卻很大。

```
alert( typeof 1234); // number

alert( typeof new Number(1234)); // object
```