## 欢迎来到贝莱优品弹子石旗舰店，下面是您今天的福利，注意查收哦、
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
</style> 
<input class="actionBtn" type="button" id="action">
<input class="stopBtn" type="button" value="停止" id="stop">
<script src="https://code.jquery.com/jquery-3.1.1.min.js"></script>
<script>
 var tagHeader = document.getElementsByTagName("header");
 var header = $("header");
 header.empty();
 
 var footer = $("footer");
 footer.empty();
 
 console.log(tagHeader);
 var constant  = ['天啦,95折', '送精美保温瓶一杯(冬天来了，暖手更暖心)', '恭喜你，喜获店家亲笔签名','刘德华演唱会一张'];
 var temp = Math.floor(Math.random()*10+1);
 var result = constant[temp]
 if(result){
  document.write(result);
 }else{
  document.write('很遗憾，下次努力，幸运一定会掉落在您的头顶哈');
 }
 
 var obj={
	"data":[
		{"name":"李白"},
		{"name":"露娜"},
		{"name":"诸葛亮"},
		{"name":"王昭君"},
		{"name":"钟无艳"},
		{"name":"曹操"},
		{"name":"刘禅"},
		{"name":"刘备"},
		{"name":"吕布"},
		{"name":"黄忠"},
		{"name":"周瑜"},
		{"name":"小乔"},
		{"name":"孙策"},
		{"name":"大乔"},
		{"name":"狂铁"},
		{"name":"白起"},
		{"name":"韩信"},
		{"name":"孙悟空"},
		{"name":"阿珂"},
		{"name":"甄姬"},
	],
	"code":1,
	"mag":"请求成功！"
}
var name1 =[164,-164,0];
var time1 = [0,500,500];
var toggle = 1;
var setAction=null;
var setStop=null;
var setFontSize=null;
var stopNowTime=1;


$("#action").click(function(){
	$("#palyerAction").attr("src","img/luckyDog/action.mp3");
	if(toggle==1){
		setAction = setInterval("action(100)",300);
		toggle=0;
		stopNowTime=1;
		$(".isYou").css("display","none");
		clearInterval(setFontSize);
	}
});


$(".stopBtn").click(function(){
	if(toggle==0){
		$("#palyerAction").attr("src","img/luckyDog/jump.mp3");
		setTimeout(function(){
			setStop= setInterval("slowStop(5)",1000);
		},2000);
	}else{
		alert("请先拉动拉杆！");
	}
});

function slowStop(stopTime){

	clearInterval(setAction);

	if(stopNowTime<=stopTime){
		setAction = setInterval("action(100+"+stopNowTime+"*1000)",300+stopNowTime*200*3);
		stopNowTime++;
	}else{
		clearInterval(setStop);
		toggle=1;
		$("#palyerAction").attr("src","");
		$(".isYou").css("display","block");
		setFontSize = setInterval(function(){
			$(".luckyName").animate({"fontSize":"100px"},500).animate({"fontSize":"40px"},500);
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


