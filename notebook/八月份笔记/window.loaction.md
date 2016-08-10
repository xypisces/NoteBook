<h3>window.loaction</h3>
---------------------------------------
<h4>Q:当在一个页面点击跳转时('<a href="/xxx.html"></a>'),页面跳过去了,但是网络Network还是上个页面的资源.刷新之后就解决了.</h4>

<h4>A:使用href='javascript:window.loaction="xxx.html"'解决了一个问题</h4>

<strong>window.location 对象用于获得当前页面的地址 (URL)，并把浏览器重定向到新的页面</strong>
---------------------------------------

<h4>Q:当页面跨域跳转时,判断导航栏位置,并给添加样式</h4>

<code>
//遍历每个a标签,给点击的标签添加标示,并重定向.
	 $('.neike-ul4 li').each(function(i){
                    $('.neike-ul4 li').eq(i).click(function(){
                        var href = $(this).children().eq(0).attr("href");
                        window.location.href = href+'?index='+i;
                        return false;
                    });
               });

//获取当前页的url,并判断其标示,与之对应的标签添加样式.
$(document).ready(function(){
	var aaa = location.search;
	var back = aaa.substring(7);
	$('.neike-ul li').each(function(i){
		if (i==back) {
			$('.neike-ul li').eq(i).addClass('neike-active');
		}
	});
});               
</code>