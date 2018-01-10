## js数组操作大全

#### 1. shift
shift: 删除原数组第一项，并返回删除元素的值；如果数组为空则返回undefined 

    var a = [1,2,3,4,5];   
    var b = a.shift(); //a:[2,3,4,5] b:1  
    
#### 2.unshift
unshift: 将参数添加到原数组开头，并返回数组的长度 

    var a = [1,2,3,4,5];   
    var b = a.unshift(-2,-1); //a:[-2,-1,1,2,3,4,5] b:7   
    
注:在IE6.0下测试返回值总为undefined，FF2.0下测试返回值为7，所以这个方法的返回值不可靠，需要用返回值时可用splice代替本方法来使用

#### 3.pop
pop:删除原数组最后一项，并返回删除元素的值；如果数组为空则返回undefined 

    var a = [1,2,3,4,5];   
    var b = a.pop(); //a:[1,2,3,4] b:5      
    
#### 4.push
push:将参数添加到原数组末尾，并返回数组的长度 

    var a = [1,2,3,4,5];   
    var b = a.push(6,7); //a:[1,2,3,4,5,6,7] b:7  
    
#### 5.concat
concat:返回一个新数组，是将参数添加到原数组中构成的 

    var a = [1,2,3,4,5];   
    var b = a.concat(6,7); //a:[1,2,3,4,5] b:[1,2,3,4,5,6,7]  
    
#### 6.splice
splice(start,deleteCount,val1,val2,...):从start位置开始删除deleteCount项，并从该位置起插入val1,val2,... 

    var a = [1,2,3,4,5];   
    var b = a.splice(2,2,7,8,9); //a:[1,2,7,8,9,5] b:[3,4]   
    var b = a.splice(0,1); //同shift   
    a.splice(0,0,-2,-1); var b = a.length; //同unshift   
    var b = a.splice(a.length-1,1); //同pop   
    a.splice(a.length,0,6,7); var b = a.length; //同push 

#### 7.reverse
reverse:将数组反序

    var a = [1,2,3,4,5];   
    var b = a.reverse(); //a:[5,4,3,2,1] b:[5,4,3,2,1]  
#### 8.sort
sort(orderfunction):按指定的参数对数组进行排序

默认情况下，==按照元素的Unicode码大小按升序排列==

    var a = [1,2,3,4,5];   
    var b = a.sort(); //a:[1,2,3,4,5] b:[1,2,3,4,5]  

#### 9. slice
slice(start,end):返回从原数组中指定开始下标到结束下标之间的项组成的新数组

==取头不取尾==
-  start:从哪个下标处开始截取，取值为正，从前向后取，取值为负，从后向前算位置。
 
 	     下标       0      1      2      3
    	var arr=["中国","美国","日本","英国"];
    	          -4     -3     -2     -1

- end : 指定结束处的下标(不包含)，该参数可以省略，如果省略的话，就是从start一直截取到结束
	注意：
		1、该函数不会影响现有数组，会返回全新的数组


    var a = [1,2,3,4,5];   
    var b = a.slice(2,5); //a:[1,2,3,4,5] b:[3,4,5]  
    
#### 10.join
join(separator):将数组的元素组起一个字符串，以separator为分隔符，省略的话则用默认用逗号为分隔符

    var a = [1,2,3,4,5];   
    var b = a.join("|"); //a:[1,2,3,4,5] b:"1|2|3|4|5"  
    
#### 11.toString
toString()将一个数组转换为字符串
	
	语法：var str = 数组对象.toString();
