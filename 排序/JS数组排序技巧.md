## 1.冒泡排序:

1. 思想：

    冒泡排序思想：每一次对比相邻两个数据的大小，小的排在前面，如果前面的数据比后面的大就交换这两个数的位置
    
    要实现上述规则需要用到两层for循环，外层从第一个数到倒数第二个数，内层从外层的后面一个数到最后一个数

2. 特点：排序算法的基础。简单实用易于理解，缺点是比较次数多，效率较低。

3. 实现：
    
 
       var examplearr=[8,94,15,88,55,76,21,39];
        function sortarr(arr){
            for(i=0;i<arr.length-1;i++){
                for(j=0;j<arr.length-1-i;j++){
                    if(arr[j]>arr[j+1]){
                        var temp=arr[j];  //交换位置
                        arr[j]=arr[j+1];
                        arr[j+1]=temp;
                    }
                }
            }
            return arr;
        }
        sortarr(examplearr);
        console.log(examplearr);

两个循环

当i=0的时候，里面的循环完整执行，从j=0执行到j=6,这也就是第一遍排序，结果是将最大的数排到了最后，这一遍循环结束后的结果应该是[8,15,88,55,76,21,39,94]

当i=1的时候，里面的循环再次完整执行，由于最大的数已经在最后了，没有必要去比较数组的最后两项，这也是j<arr.length-1-i的巧妙之处，结果是[8,15,55,76,21,39,88,94]

说到这里，规律就清楚了，每次将剩下数组里面最大的一个数排到最后面，当第一个循环执行到最后的时候，也就是i=6,此时，j=0,只需要比较数组的第一和第二项，比较完毕，返回。



## 2. 快速排序
(http://www.ruanyifeng.com/blog/2011/04/quicksort_in_javascript.html)

快速排序（Quicksort）是对冒泡排序的一种改进，是一种分而治之算法归并排序的风格

核心的思想就是通过一趟排序将要排序的数据分割成独立的两部分，其中一部分的所有数据都比另外一部分的所有数据都要小，然后再按此方法对这两部分数据分别进行快速排序，整个排序过程可以递归进行，以此达到整个数据变成有序序列

理论上的步骤：

1. 找到一个“支点”项目在数组中，可以是中心点,基准
1. 在阵列中的第一项开始指针（左指针）。
1. 在数组中的最后一个项目开始一个指针（右指针）。
1. 而在左指针数组中的值小于枢轴值，将左指针向右（加1）。 继续，直到在左指针的值大于或等于所述枢轴值。
1. 而在合适的指针数组中的值大于枢轴值，将右指针向左（减去1）。 继续下去，直到在正确的指针的值小于或等于所述枢轴值。
1. 如果左指针是小于或等于右指针，然后交换的值在数组中的这些位置。
1. 移动左指针向右由1和右指针向左之一。
1. 如果左指针和右指针不符合，请转到步骤1。

简而言之:
- 在数据集之中，选择一个元素作为"基准"（pivot）。
- 所有小于"基准"的元素，都移到"基准"的左边；所有大于"基准"的元素，都移到"基准"的右边。
- 对"基准"左边和右边的两个子集，不断重复第一步和第二步，直到所有子集只剩下一个元素为止。

        - 第一步，选择中间的元素45作为"基准"。（基准值可以任意选择，但是选择中间的值比较容易理解。）
        var arr=[85, 24, 63, 45, 17, 31, 96, 50];
        ![image](http://www.ruanyifeng.com/blogimg/asset/201104/bg2011040403.png)
        - 第二步，按照顺序，将每个元素与"基准"进行比较，形成两个子集，一个"小于45"，另一个"大于等于45"。
        ![image](http://www.ruanyifeng.com/blogimg/asset/201104/bg2011040403.png)
        - 第三步，对两个子集不断重复第一步和第二步，直到所有子集只剩下一个元素为止。
        ![image](http://www.ruanyifeng.com/blogimg/asset/201104/bg2011040405.png)
        ![image](http://www.ruanyifeng.com/blogimg/asset/201104/bg2011040406.png)
        ![image](http://www.ruanyifeng.com/blogimg/asset/201104/bg2011040407.png)
        ![image](http://www.ruanyifeng.com/blogimg/asset/201104/bg2011040408.png)
        
        
    #####     下面参照网上的资料（这里和这里），用Javascript语言实现上面的算法。

- 首先，定义一个quickSort函数，它的参数是一个数组。

         var quickSort = function(arr) {
    
         };
- 然后，检查数组的元素个数，如果小于等于1，就返回。

        var quickSort = function(arr) {
        　　if (arr.length <= 1) { return arr; }
      };
      
- 接着，选择"基准"（pivot），并将其与原数组分离，再定义两个空数组，用来存放一左一右的两个子集。

        var quickSort = function(arr) {
        
        　　if (arr.length <= 1) { return arr; }
        
        　　var pivotIndex = Math.floor(arr.length / 2) ;
        
        　　var pivot = arr.splice(pivotIndex, 1)[0];
        
        　　var left = [];
        
        　　var right = [];
        
        };
            
- 然后，开始遍历数组，小于"基准"的元素放入左边的子集，大于基准的元素放入右边的子集。 
        
         var quickSort = function(arr) {
        　　if (arr.length <= 1) { return arr; }
        　　var pivotIndex = Math.floor(arr.length / 2) ;
        　　var pivot = arr.splice(pivotIndex, 1)[0];
        　　var left = [];
        　　var right = [];
        　　for (var i = 0; i < arr.length; i++){
        　　　　if (arr[i] < pivot) {
        　　　　    　　left.push(arr[i]);
        　　　　} else {
        　　　　    　　right.push(arr[i]);
        　　　　}
        　　}
        };
        
- 最后，使用递归不断重复这个过程，就可以得到排序后的数组。

        var quickSort = function(arr) {
        　　if (arr.length <= 1) { return arr; }
        　　var pivotIndex = Math.floor(arr.length / 2);
        　　var pivot = arr.splice(pivotIndex, 1)[0];
        　　var left = [];
        　　var right = [];
        　　for (var i = 0; i < arr.length; i++){
        　　　　if (arr[i] < pivot) {
        　　　　　　left.push(arr[i]);
        　　　　} else {
        　　　　　　right.push(arr[i]);
        　　　　}
        　　}
        　　return quickSort(left).concat([pivot], quickSort(right));
        };

- 使用的时候，直接调用quickSort()就行了。



## 3. 插入排序


    <script>
			var arr = [2,88,6,8,3,0,34,72];
			function insertSort(arr){
				//i从1开始向右遍历每个元素
				for(var i=1;i<arr.length;i++){
					//将i位置的值临时保存到变量t中
					var t=arr[i];
					//定义p=i-1;
					var p=i-1;
					//反复(p>=0&&p位置的值>=t)
					while(p>=0&&arr[p]>=t){
						//将p位置的值赋值给p+1位置
						arr[p+1]=arr[p];
						//p--
						p--;
					}
					//(循环结束)
					//将t保存在p+1位置
					arr[p+1]=t;
				}
			}
			insertSort(arr);
			console.log(arr);
		</script>


## 4. 选择排序
#####    原理：
   每一次从待排序的数据元素中选出最小（或最大）的一个元素，存放在序列的起始位置，直到全部待排序的数据元素排完。 选择排序是不稳定的排序方法
   
   假定数组每次比较范围内第一个元素最小min，和剩下的比较，如果比假定的这个元素小，则令min为这个元素，直到找到最小的，然后交换位置,每比较一次，
   就把最小的一位数找出来放数组最前面。
   
       <script>
    		var arr = [2,88,6,8,3,0,34,72];
    		function selectSort(arr){
    			for(var i=0;i<arr.length;i++){
    				var min=arr[i]; //假定比较范围内的第一个值为最小值
    				var index=i; //记录最小值的下标
    				for(var j=i+1;j<arr.length;j++){
    					//找到比较范围内第一个值为最小值的记录下来
    					if(arr[j]<min){
    						min=arr[j];
    						index=j;
    					}
    					//吧范围内最小的值交换到范围内的第一个
    					if(index!=i){
    						var temp=arr[i];
    						arr[i]=arr[index];
    						arr[index]=temp;
    					}
    				}
    			}
    		}
    		selectSort(arr);
    		console.log(arr);
    	</script>
    	
## 5.希尔排序
#####   原理：
先将整个待排元素序列分割成若干个子序列（由相隔某个“增量”的元素组成的）分别进行直接插入排序，然后依次缩减增量再进行排序，待整个序列中的元素基本有序

   （增量足够小）时，再对全体元素进行一次直接插入排序。
   
![image](https://images2015.cnblogs.com/blog/1093977/201707/1093977-20170718211012786-181929403.jpg)
    	
  像这个算法看图理解起来并不是很难，就像比赛一样，1-6一组，2-7一组，每差5为一组进行比较，之后再每差2为一组进行比较，最后就是两两比较，有点类似冒泡算法，但又比冒泡多了一层增量的概念。起初小编看到这个导图的时候感觉编程挺简单的，无非就是改变一下增量，这有何难？人呐，都是眼高手低，废话不多说直接看代码：  	
  
      <script>
    		var arr=[3,44,38,5,47,15,36,26,27,2,46,4,19,50,48];
    		function shellSort(arr){
    			var len=arr.length;
    			for(var fraction = Math.floor(len / 2);fraction > 0; fraction = Math.floor(fraction / 2)){
    				 for (var i = fraction; i < len; i++) {
    						for (var j = i - fraction; j >= 0 && arr[j] > arr[fraction + j]; j -= fraction) {
    							var temp = arr[j];
    							arr[j] = arr[fraction + j];
    							arr[fraction + j] = temp;
    						}
    				 }
    			}
    		}
    		 shellSort(arr);
    		 console.log(arr);
    	</script>
        	
    	
    	
    	
    	
    	
    	
    	
    	
    	
    	
参考:
http://www.qdfuns.com/notes/17693/19282a53e49c02b2c057d2a037ef3362.html
    	