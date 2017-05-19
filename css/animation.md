# 动画

* **animation有八个子属性**
<table>
    <tbody>
        <tr>
            <td colspan="2">animation: name duration timing-function delay iteration-count direction play-state fill-mode;</td>
        </tr>
        <tr>
            <td>animation-name</td>
            <td>规定需要绑定到选择器的 keyframe 名称。。</td>
        </tr>
        <tr>
            <td>animation-duration</td>
            <td>规定完成动画所花费的时间，以秒或毫秒计。</td>
        </tr>
        <tr>
            <td>animation-timing-function</td>
            <td>规定动画的速度曲线。</td>
        </tr>
        <tr>
            <td>animation-delay</td>
            <td>规定在动画开始之前的延迟。</td>
        </tr>
        <tr>
            <td>animation-iteration-count</td>
            <td>规定动画应该播放的次数。</td>
        </tr>
        <tr>
            <td>animation-direction</td>
            <td>规定是否应该轮流反向播放动画。</td>
        </tr>
        <tr>
            <td>animation-play-state</td>
            <td>规定动画是否正在运行或暂停。默认是 "running"。</td>
        </tr>
        <tr>
            <td>animation-fill-mode</td>
            <td>规定对象动画时间之外的状态。</td>
        </tr>
    </tbody>
</table>

* **例子**
        @keyframes myanimate {
            0%   {background: red; left:0px; top:0px;}
            25%  {background: yellow; left:200px; top:0px;}
            50%  {background: blue; left:200px; top:200px;}
            75%  {background: green; left:0px; top:200px;}
            100% {background: red; left:0px; top:0px;}
        }
        div {
            animation-name: myanimate;
            animation-duration: 5s;
            animation-timing-function: linear;
            animation-delay: 2s;
            animation-iteration-count: infinite;
            animation-direction: alternate;
            animation-play-state: running;
        }