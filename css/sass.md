# sass

* **变量**
        $color: red;
        div {
            color: $color;
        }
        $side: left;
        div {
            border-#{$side}-color: $color;
        }

* **计算功能**
        body {
            margin: (100px/2);
            width: 100px + 1px;
            height: $var * 2;
        }

* **嵌套**
        div {
            span {
                color: $color;
            }
        }
        div {
            border: { /*border后面必须加上冒号*/
                color: $color;
            }
        }
        a {
            &:hover { /*可以使用&引用父元素*/
                color: $color;
            }
        }

* **继承**
        .parent {
            width: 100px;
        }
        .child {
            @extend .parent;
            color: $color;
        }

* **Mixin（可重用的代码块）**
        @mixin left {
            float: left;
        }
        /*使用@include命令，调用mixin*/
        div {
            @include left;
        }
        /*更强大之处，可以指定参数和缺省值*/
        @mixin left($value: 10px) {
            float: left;
            margin-left: $value;
        }
        div {
            @include left(20px);
        }

* **颜色函数**
        lighten(#cc3, 10%)
        darken(#cc3, 10%)

* **插入文件**
        @import "../xxx.scss";

* **条件语句**
        p {
            @if 2 > 1 {
                color: $color;
            } @else {
                background-color: #fff;
            }
        }        

* **循环语句**
        @for $i from 1 to 5 {
            #id-#{$i} {
                width: #{$i * 10}px;
            }
        }

        $i: 10;
        @while $i > 0 {
            width: #{$i}px;
            $i: $i - 1;
        }

        @each $member in a, b, c {
            .#{$member} {
                color: $color;
            }
        }

* **自定义函数**
        @function double($n) {
            $return $n * 2;
        }
        div {
            width: double(10px);
        }

**相关文章**
* [SASS用法指南](http://www.ruanyifeng.com/blog/2012/06/sass.html)