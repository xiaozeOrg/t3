
<style type="text/css"> 
.c-lucky {
	background-image: url(http://demo.sc.chinaz.net/Files/DownLoad/webjs1/201906/jiaoben6857/img/luckyDog/background.png);
	background-size: 650px;
	height: 700px;
	width: 700px;
	background-repeat: no-repeat;
	position: relative;
	margin: auto;
	z-index: 99;
}

.luckyName {
	width: 308px;
	height: 164px;
	margin: 198px 0px 0px 197px;
	position: relative;
	display: inline-block;
	font-size: 50px;
	line-height: 50px;
	overflow: hidden;
	text-align: center;
}

.actionBtn {
	width: 25px;
	height: 85px;
	background-color: transparent;
	border: none;
	background-image: url(http://demo.sc.chinaz.net/Files/DownLoad/webjs1/201906/jiaoben6857/img/luckyDog/action.png);
	background-repeat: no-repeat;
	background-size: 25px;
	outline: none;
	position: absolute;
	z-index: 0;
	top: 290px;
	right: 138px;

}

.stopBtn {
	width: 294px;
	height: 54px;
	position: absolute;
	top: 409px;
	left: 203px;
	border-radius: 20px;
	border: none;
	background-color: transparent;
	outline: none;
	-moz-outline-radius: 20px;
	-moz-outline-radius: 20px;
	font-size: 40px;
	color: white;
}

.c-lucky .name1,
.c-lucky .name2,
.c-lucky .name3 {
	width: 308px;
	height: 164px;
	line-height: 164px;
	position: absolute;

}

.c-lucky .name1 {
	bottom: 164px;
}

.c-lucky .name2 {}

.c-lucky .name3 {

	top: 164px;
}

.isYou {
	width: 400px;
	position: absolute;
	top: -15px;
	left: -165px;
	z-index: 999;
}

.wrapper {
    margin: 0 auto;
    background: #ffffff;
}
footer{
   display:none
}
html {
    background: #ffffff;
}
body {
    padding: 50px 0;
    font: 14px/1.5 Lato, "Helvetica Neue", Helvetica, Arial, sans-serif;
    font-weight: 300;
    width: 800px;
    background-color: #000000;
	background-color: #ffffff;
}
.grant{
	text-align: center;
}
section {
    font-size: 15px;
    border-radius: 0 0 8px 8px;
    padding: 0px;
}
</style> 
<div class="noName" style="display: none;"></div>
<div class="c-lucky">
	<img class="isYou" src="http://demo.sc.chinaz.net/Files/DownLoad/webjs1/201906/jiaoben6857/img/luckyDog/isYou.png" style="display: none;">
	<div class="luckyName">
		<div class="name2">
			祝您好运
		</div>
	</div>
	
	<input class="actionBtn" type="button" id="action">
	<input class="stopBtn" type="button" value="开始" id="stop">
</div>

<script src="https://code.jquery.com/jquery-3.1.1.min.js"></script>
<script>
	alert(window.location.href);
 var tagHeader = document.getElementsByTagName("header");
 var header = $("header");
 header.empty();
 
 var footer = $("footer");
 footer.empty();
 
 $(".c-lucky").parent().append("<p class='grant'>本程序由北京优视科技出版</p>")

var array = ['天啦,95折','恭喜你，喜获店家亲笔签名','天啦,95折','刘德华演唱会一张','天啦,95折','免费逛窑子','天啦,95折','范冰冰谁都可以上','送精美保温瓶一杯(冬天来了，暖手更暖心)','韩信大将军赠予你','天啦,95折','小乔也归你','大乔不能跟我抢','天啦,95折'];

function random(length){
	var temp = Math.floor(Math.random() * length + 1);
	if(temp>length)random(length);
	
	return temp;
}

$("#stop").click(function(){ 
	var used = $("#action").attr("used");
	var stop = $("#stop").attr("stop");
	if(used && stop)return alert("别闹！亲， 您已经抽过奖啦~");
	var stopFlag = $("#stop").val();
	if("停止" === stopFlag){
		$("#stop").attr("stop",true);
		setTimeout(function(){
			var radom = random(array.length);
			var text = array[radom];
			var name2 = $(".name2");
			//name2.css("font-size","30px")
			name2.text(text);
			name2.fadeOut("slow").fadeOut(3000).fadeIn(500);
			fontShowIng(); 
			
		},500); 
		return;
	}
	$("#stop").val("停止");
	$("#action").attr("used",true);
	//显示抽奖的内容
	showing();
});

/**
 * 产生随机整数，包含下限值，包括上限值
 * @param {Number} lower 下限
 * @param {Number} upper 上限
 * @return {Number} 返回在下限到上限之间的一个随机整数
 */
function randomPlus(lower, upper) {
	return Math.floor(Math.random() * (upper - lower+1)) + lower;
} 


function fontShowIng(){
	var radom = randomPlus(20,40);
	$(".name2").css('font-size',radom + "px").fadeOut("slow").fadeIn(500)//	.css("text-align","center");
	setTimeout(fontShowIng,600)
}

$(".stopBtn").click(function(){
	return;
	$("#stop").attr("stop",true);

	setTimeout(function(){
		var radom = random(array.length);
		var text = array[radom];
		var name2 = $(".name2");
		//name2.css("font-size","30px")
		name2.text(text);
		name2.fadeOut("slow").fadeOut(3000).fadeIn(500);
		fontShowIng(); 
		
	},500);  
});
function showing(){
	var stop = $("#stop").attr("stop");
	if(stop){//已经停止了,退出递归
		return;
	}
	var radom = random(array.length);
	var text = array[radom];
	var name2 = $(".name2");
	name2.css({"font-size":"20px"});
	//name2.css({"font-size":"30px","display":"inline-block"});
	name2.text(text);
	
	//name2.fadeOut("slow").fadeOut(3000).fadeIn(500);
	setTimeout(showing,100);
}

function slowStop(stopTime){

	clearInterval(setAction);

	if(stopNowTime<=stopTime){
		setAction = setInterval("action(100+"+stopNowTime+"*1000)",300+stopNowTime*200*3);
		stopNowTime++;
	}else{
		clearInterval(setStop);
		toggle=1;
		$("#palyerAction").attr("src","");
		//$(".isYou").css("display","block");
		setFontSize = setInterval(function(){
			$(".luckyName").animate({"fontSize":"60px"},500).animate({"fontSize":"20px"},500);
		},1100);
	}
}

function runText(el1,el2,el3){
	var data = obj.data;
	var dataLenght =data.length;
	//生成的随机数获取obj中的值
	el1.html(data[luckNum(dataLenght)].name);
	el2.html(data[luckNum(dataLenght)].name);
	el3.html(data[luckNum(dataLenght)].name);
}

function luckNum(max){
	var num =Math.floor(max*Math.random()/1);
	return num;
}

function action(runTime){
	var el1 =$(".name1");
	var el2 =$(".name2");
	var el3 =$(".name3");
	var el4 =$(".noName")
	$(".name1").animate({opacity:0},0).animate({top:name1[0]},runTime).animate({opacity:1},0);
	$(".name2").animate({top:name1[1]},runTime);
	$(".name3").animate({top:name1[2]},runTime,function(){
		runText(el1,el2,el4);
	});
	$(".name1").animate({top:name1[2]},runTime);
	$(".name2").animate({opacity:0},0).animate({top:name1[0]},runTime).animate({opacity:1},0);
	$(".name3").animate({top:name1[1]},runTime,function(){
		runText(el4,el2,el3);
	});
	$(".name1").animate({top:name1[1]},runTime);
	$(".name2").animate({top:name1[2]},runTime);
	$(".name3").animate({opacity:0},0).animate({top:name1[0]},runTime).animate({opacity:1},0,function(){
		runText(el2,el4,el3);
	});
}
 
</script>


