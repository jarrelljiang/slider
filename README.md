# slider
查看demo:
<!DOCTYPE html>
<html>
<head>
	<title></title>
	<script type="text/javascript" src="jquery-1.9.1.js"></script>
	<style type="text/css">
	*{margin: 0;padding: 0;}
	li{list-style: none; float: left;height: 200px;width: 200px;background: gray;color: red}
	.box{height: 200px;width: 600px;overflow: hidden; margin: 100px auto;position: relative;}
	#left,#right{position: absolute;height: 30px; width: 30px;background: #eee;color: red}
	#left{top: 40%; left: 0;}
	#right{top: 40%;right: 0;}
	ul{position: absolute;width: 1000px}
	</style>
</head>
<body>
<div class="box">
	<ul>
		<li>1</li>
		<li>2</li>
		<li>3</li>
		<li>4</li>
		<li>5</li>
	</ul>
	<div id="left">上</div>
	<div id="right">下</div>
</div>

<script type="text/javascript">
function move(){
	$('ul').animate({
		left: '-200px'},
		1000, function() {
		$('ul').css('left',0);
		$('ul').find('li').eq(0).appendTo('ul');
	});
}
$('#right').click(function(){
	if($('ul')[0].offsetLeft==0){
		move();
	}
})
$('#left').click(function(){
	if($('ul')[0].offsetLeft==0){
		$('ul').find('li:last-child').prependTo('ul');
		$('ul').css('left','-200px');
		$('ul').animate({
			left: 0
		},1000);
	}
})
var t=setInterval(move,2000);
$('.box').hover(function() {
	clearInterval(t);
}, function() {
	t=setInterval(move,2000);
});
</script>
</body>
</html>
