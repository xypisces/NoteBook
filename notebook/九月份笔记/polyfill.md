# polyfill解决兼容性

### picturefill 解决响应式图片兼容
- 使用picture
<code>
    <picture>
        <source srcset='img/ad00.png' media="(min-width:50em)">
        <source srcset='img/ad00-m.png' media="(min-width:30em)">
        <img src="img/add001" alt="图片">
    </picture>
</code>
<script src='引入polyfill脚本'></script>
### 压缩图片
- www.tinypng.com