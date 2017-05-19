# 变形

* **transform属性应用于元素的2D或3D转换。这个属性允许将元素旋转、缩放、移动、倾斜等**
<table>
    <tbody>
        <tr>
            <td colspan="2">transform: none | transform-functions;</td>
        </tr>
        <tr>
            <td>none</td>
            <td>定义不进行转换。</td>
        </tr>
        <tr>
            <td>matrix(<i>n</i>,<i>n</i>,<i>n</i>,<i>n</i>,<i>n</i>,<i>n</i>)</td>
            <td>定义 2D 转换，使用六个值的矩阵。</td>
        </tr>
        <tr>
            <td>matrix3d(<i>n</i>,<i>n</i>,<i>n</i>,<i>n</i>,<i>n</i>,<i>n</i>,<i>n</i>,<i>n</i>,<i>n</i>,<i>n</i>,<i>n</i>,<i>n</i>,<i>n</i>,<i>n</i>,<i>n</i>,<i>n</i>)</td>
            <td>定义 3D 转换，使用 16 个值的 4x4 矩阵。</td>
        </tr>
        <tr>
            <td>translate(<i>x</i>,<i>y</i>)</td>
            <td>定义 2D 转换。</td>
        </tr>
        <tr>
            <td>translate3d(<i>x</i>,<i>y</i>,<i>z</i>)</td>
            <td>定义 3D 转换。</td>
        </tr>
        <tr>
            <td>translateX(<i>x</i>)</td>
            <td>定义转换，只是用 X 轴的值。</td>
        </tr>
        <tr>
            <td>translateY(<i>y</i>)</td>
            <td>定义转换，只是用 Y 轴的值。</td>
        </tr>
        <tr>
            <td>translateZ(<i>z</i>)</td>
            <td>定义 3D 转换，只是用 Z 轴的值。</td>
        </tr>
        <tr>
            <td>scale(<i>x</i>[,<i>y</i>]?) </td>
            <td>定义 2D 缩放转换。</td>
        </tr>
        <tr>
            <td>scale3d(<i>x</i>,<i>y</i>,<i>z</i>)</td>
            <td>定义 3D 缩放转换。</td>
        </tr>
        <tr>
            <td>scaleX(<i>x</i>)</td>
            <td>通过设置 X 轴的值来定义缩放转换。</td>
        </tr>
        <tr>
            <td>scaleY(<i>y</i>)</td>
            <td>通过设置 Y 轴的值来定义缩放转换。</td>
        </tr>
        <tr>
            <td>scaleZ(<i>z</i>)</td>
            <td>通过设置 Z 轴的值来定义 3D 缩放转换。</td>
        </tr>
        <tr>
            <td>rotate(<i>angle</i>)</td>
            <td>定义 2D 旋转，在参数中规定角度。</td>
        </tr>
        <tr>
            <td>rotate3d(<i>x</i>,<i>y</i>,<i>z</i>,<i>angle</i>)</td>
            <td>定义 3D 旋转。</td>
        </tr>
        <tr>
            <td>rotateX(<i>angle</i>)</td>
            <td>定义沿着 X 轴的 3D 旋转。</td>
        </tr>
        <tr>
            <td>rotateY(<i>angle</i>)</td>
            <td>定义沿着 Y 轴的 3D 旋转。</td>
        </tr>
        <tr>
            <td>rotateZ(<i>angle</i>)</td>
            <td>定义沿着 Z 轴的 3D 旋转。</td>
        </tr>
        <tr>
            <td>skew(<i>x-angle</i>,<i>y-angle</i>)</td>
            <td>定义沿着 X 和 Y 轴的 2D 倾斜转换。</td>
        </tr>
        <tr>
            <td>skewX(<i>angle</i>)</td>
            <td>定义沿着 X 轴的 2D 倾斜转换。</td>
        </tr>
        <tr>
            <td>skewY(<i>angle</i>)</td>
            <td>定义沿着 Y 轴的 2D 倾斜转换。</td>
        </tr>
        <tr>
            <td>perspective(<i>n</i>)</td>
            <td>为 3D 转换元素定义透视视图。</td>
        </tr>
    </tbody>
</table>

* **例子**
        .container {
            perspective: 1000px;
            transform-style: preserve-3d;
            transition: transform 1s;
        }
        .item {
            transform: rotateY(10deg) translateZ(50px);
        }