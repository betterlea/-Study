function animate(obj,json,fn){//obj动  需要改变obj什么才会动都装在json里 fn是回调函数在动画完后需要什么效果
		clearInterval(obj.timer);//启动计时器先清除一遍计时器
		obj.timer = setInterval(function(){//语句病
	// 		1.获取步长
	// 		2.步长取整
	// 		3.改变计时器
	// 		4.停止计时器
		var flag = true;//必须放在for循环外面
		for(var attr in json){//遍历json里每个属性
			var current =0;
			if(attr == "opacity"){
				current = parseInt(getStyle(obj,attr)*100);//标准浏览器的透明度 0-1
			}else{
				current = parseInt(getStyle(obj,attr));//当前属性值
			}
			var step = (json[attr]-current)/10;//获取步长
			step = step > 0?Math.ceil(step):Math.floor(step);//步长取整
			if(attr == "opacity"){//先判断json里是否有透明度
				if("opacity" in obj.style){//再判断样式里是否有透明度
					obj.style.opacity = (current+step)/100;//得到标准浏览器的透明度
				}else{
					obj.style.opacity = "apha(opacity="+json[attr]*100+")";//得到 ie 浏览器中的透明度
				}
			}else if(attr == "zIndex"){//判断json里是否有zIndex属性 不带px
				obj.style[attr]=json[attr];//得到层级
			}else{
				obj.style[attr] = current+step+"px";
			}
			if(current != json[attr]){//只要一个没达到目标值就不应该停止计时器 一定要放在for循环里
				flag = false;
			}		
		}
		if(flag){//用于判断清楚计时器的条件
			clearInterval(obj.timer);//清除计时器
			if(fn){
				fn();//如果实参有传 就回调函数
			}
		}
		},30);
	}
function getStyle(obj,attr){//获取元素的样式
	if(obj.currentStyle){//ie 
		return obj.currentStyle[attr];
	}else{
		return window.getComputedStyle(obj,null)[attr];
	}
}
