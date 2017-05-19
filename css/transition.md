# 过渡

* **transition四个子属性**
<table>
    <tbody>
        <tr>
            <td colspan="2">transition: property duration timing-function delay;</td>
        </tr>
        <tr>
            <td>transition-property</td>
            <td>规定设置过渡效果的 CSS 属性的名称。</td>
        </tr>
        <tr>
            <td>transition-duration</td>
            <td>规定完成过渡效果需要多少秒或毫秒。</td>
        </tr>
        <tr>
            <td>transition-timing-function</td>
            <td>规定速度效果的速度曲线。</td>
        </tr>
        <tr>
            <td>transition-delay</td>
            <td>定义过渡效果何时开始。</td>
        </tr>
    </tbody>
</table>
* **transitionend事件**
        document.getElementById('xxx').addEventListener('transitionend', function(event){
            console.log(event)
        }, false)
* **永久过渡：即将delay值设置很大**
        .forever {
            transition: all 1s ease-in-out 99999s;
        }
        .forever:hover {
            transform: scale(2);
            transition: all 1s ease-in-out;
        }