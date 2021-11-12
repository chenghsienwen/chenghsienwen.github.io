### 一些生物哲學問題

- 歷史與生物學有何關聯？<!-- .element: class="fragment" data-fragment-index="1" -->
- 智人和其他動物的本質差異何在？<!-- .element: class="fragment" data-fragment-index="2" -->
- 歷史上有正義嗎？<!-- .element: class="fragment" data-fragment-index="3" -->
- 歷史有發展方向嗎？<!-- .element: class="fragment" data-fragment-index="4" -->
- 隨著歷史的開展，人們變得更快樂嗎？<!-- .element: class="fragment" data-fragment-index="5" -->
- 在21世紀，科學和技術引發了哪些道德問題？<!-- .element: class="fragment" data-fragment-index="6" -->



### 章節介紹 
- 認知革命
- 農業革命
- 人類的融合統一
- 科學革命
<!-- .slide: style="text-align: center"  -->



### 認知革命



### 農業革命



### 人類的融合統一



### 科學革命



### 個人心得



### END
To install com.vpon.abriefhistoryofhumankind
```scala
libraryDependencies += "com" % "lib" % "0.1.0-SNAPSHOT"
```

```scala
val x = 1
// x: Int = 1
List(x, x)
// res0: List[Int] = List(1, 1)
```



# Markdown Demo
- open with new tab: [scala-with-cats2](https://underscore.io/blog/posts/2020/05/27/scala-with-cats-2.html)<!-- .element: target="_blank" -->


## code highlight

```scala[1-3|4-11|12-14|15-19]
trait Printable[A] {
  def format(a: A): String
}
object PrintableInstance {
  implicit val strPrint: Printable[String] = new Printable[String] {
    def format(a: String): String = a
  }
  implicit val intPrint: Printable[Int] = new Printable[Int] {
    def format(a: Int): String = a.toString
  }
}
object Printable {
  def format[A](a: A)(implicit p: Printable[A]): String = p.format(a)
}
object PrintableSyntax {
  implicit class PrintableOps[A](a: A)(implicit p: Printable[A]) {
    def show: String = p.format(a)
  }
}
```


## make table 

|                |ASCII                          |HTML                         |
|----------------|-------------------------------|-----------------------------|
|Single backticks|`'Isn't this fun?'`            |'Isn't this fun?'            |
|Quotes          |`"Isn't this fun?"`            |"Isn't this fun?"            |
|Dashes          |`-- is en-dash, --- is em-dash`|-- is en-dash, --- is em-dash|



## External 2

Content 2.1



## External 3.1

Content 3.1


## External 3.2

Content 3.2


## External 3.3

![External Image](https://s3.amazonaws.com/static.slid.es/logo/v2/slides-symbol-512x512.png)
