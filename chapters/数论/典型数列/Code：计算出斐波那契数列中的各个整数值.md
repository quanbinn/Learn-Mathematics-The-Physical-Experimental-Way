# Code：计算出斐波那契数列中的各个整数值

## 开始做实体实验

### 1.在坐标纸上画出相应的坐标点和坐标点之间的连线，结果如下图所示。

![](/images/数论/典型数列/Code：计算出斐波那契数列中的各个整数值/1b1.jpg)

![](/images/数论/典型数列/Code：计算出斐波那契数列中的各个整数值/1b2.jpg)

## 开始做代码实验

单击右方的[在线代码段Url网址](http://www.pythontutor.com/live.html#code=function%20fibonacci%28n%29%7B%0A%20%20%20%20let%20arrOfNums%20%3D%20%5B0,1%5D%3B%0A%20%20%20%20if%28n%20%3C%200%29%20throw%20new%20Error%28'%E4%BD%A0%E9%9C%80%E8%A6%81%E8%BE%93%E5%85%A5%E6%95%B0%E5%AD%97%20%3E%3D%200%E7%9A%84%E6%95%B4%E6%95%B0'%29%3B%0A%20%20%20%20if%28n%20%3D%3D%200%29%20return%200%3B%0A%20%20%20%20if%28n%20%3D%3D%201%29%20return%201%3B%0A%0A%20%20%20%20if%20%28n%20%3E%3D%202%29%20%7B%0A%20%20%20%20%20%20%20%20for%20%28var%20i%20%3D%202%3B%20i%20%3C%3D%20n%3B%20i%2B%2B%29%20%7B%0A%20%20%20%20%20%20%20%20%20%20arrOfNums%5Bi%5D%20%3D%20arrOfNums%5Bi-1%5D%20%2B%20arrOfNums%5Bi-2%5D%0A%20%20%20%20%20%20%20%20%20%20//%20console.log%28arrOfNums%29%3B%20%20%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%7D%0A%0A%20%20%20%20return%20arrOfNums%5Bn%5D%3B%0A%7D%0A%0Aconsole.log%28fibonacci%285%29%29&cumulative=false&curInstr=23&heapPrimitives=nevernest&mode=display&origin=opt-live.js&py=js&rawInputLstJSON=%5B%5D&textReferences=false)，浏览器里会打开一个新的页面，里面有下面的代码段。

```javascript
function fibonacci(n){
    let arrOfNums = [0,1];
    if(n < 0) throw new Error('你需要输入数字 >= 0的整数');
    if(n == 0) return 0;
    if(n == 1) return 1;

    if (n >= 2) {
        for (var i = 2; i <= n; i++) {
          arrOfNums[i] = arrOfNums[i-1] + arrOfNums[i-2]
          // console.log(arrOfNums);          
        }
    }

    return arrOfNums[n];
}

console.log(fibonacci(5))
```

![](/images/数论/典型数列/Code：计算出斐波那契数列中的各个整数值/3b.jpg)

单击右方的[在线代码段Url网址](http://www.pythontutor.com/live.html#code=function%20fibonacci%28n%29%7B%0A%20%20%20%20%20%20%20%20var%20valOfN_2%20%3D%200%3B%0A%20%20%20%20%20%20%20%20var%20valOfN_1%20%3D%201%3B%0A%20%20%20%20%20%20%20%20var%20valOfN%3B%0A%20%0A%20%20%20%20%20%20%20%20if%28n%20%3C%200%29%20throw%20new%20Error%28'%E4%BD%A0%E9%9C%80%E8%A6%81%E8%BE%93%E5%85%A5%E6%95%B0%E5%AD%97%20%3E%3D%200%E7%9A%84%E6%95%B4%E6%95%B0'%29%3B%0A%20%20%20%20%20%20%20%20if%28n%20%3D%3D%200%29%20return%200%3B%0A%20%20%20%20%20%20%20%20if%28n%20%3D%3D%201%29%20return%201%3B%0A%20%20%20%20%20%20%20%20if%28n%20%3E%3D%202%29%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20for%28var%20i%20%3D%202%3Bi%20%3C%3D%20n%3Bi%2B%2B%29%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20valOfN%20%3D%20valOfN_2%20%2B%20valOfN_1%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20valOfN_2%20%3D%20valOfN_1%3B%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20valOfN_1%20%3D%20valOfN%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20return%20valOfN%3B%0A%20%20%20%20%7D%0A%0Aconsole.log%28fibonacci%285%29%29&cumulative=false&curInstr=33&heapPrimitives=nevernest&mode=display&origin=opt-live.js&py=js&rawInputLstJSON=%5B%5D&textReferences=false)，浏览器里会打开一个新的页面，里面有下面的代码段。

```javascript
function fibonacci(n){
        var valOfN_2 = 0;
        var valOfN_1 = 1;
        var valOfN;
 
        if(n < 0) throw new Error('你需要输入数字 >= 0的整数');
        if(n == 0) return 0;
        if(n == 1) return 1;
        if(n >= 2){
            for(var i = 2;i <= n;i++){
                valOfN = valOfN_2 + valOfN_1;
                valOfN_2 = valOfN_1;                
                valOfN_1 = valOfN;
            }
        }
        return valOfN;
    }

console.log(fibonacci(5))
```

![](/images/数论/典型数列/Code：计算出斐波那契数列中的各个整数值/4b1.jpg)
![](/images/数论/典型数列/Code：计算出斐波那契数列中的各个整数值/4b2.jpg)
![](/images/数论/典型数列/Code：计算出斐波那契数列中的各个整数值/4b3.jpg)
![](/images/数论/典型数列/Code：计算出斐波那契数列中的各个整数值/4b4.jpg)
![](/images/数论/典型数列/Code：计算出斐波那契数列中的各个整数值/4b5.jpg)
![](/images/数论/典型数列/Code：计算出斐波那契数列中的各个整数值/4b6.jpg)
![](/images/数论/典型数列/Code：计算出斐波那契数列中的各个整数值/4b7.jpg)
![](/images/数论/典型数列/Code：计算出斐波那契数列中的各个整数值/4b8.jpg)

单击右方的[在线代码段Url网址](http://www.pythontutor.com/live.html#code=function%20fibonacci%28n%29%7B%0A%20%20%20%20if%28n%20%3C%200%29%20throw%20new%20Error%28'%E4%BD%A0%E9%9C%80%E8%A6%81%E8%BE%93%E5%85%A5%E6%95%B0%E5%AD%97%20%3E%3D%200%E7%9A%84%E6%95%B4%E6%95%B0'%29%3B%0A%20%20%20%20if%20%28n%20%3D%3D%200%29%20return%200%3B%20%0A%20%20%20%20if%20%28n%20%3D%3D%201%29%20return%201%3B%20%0A%20%20%20%20if%20%28n%20%3E%3D%202%29%7B%0A%20%20%20%20%20%20%20%20return%20fibonacci%28n-1%29%20%2B%20fibonacci%28n-2%29%3B%20%20%20%20%20%20%0A%20%20%20%20%7D%20%0A%7D%0A%20%20%20%20%0Aconsole.log%28fibonacci%286%29%29&cumulative=false&curInstr=146&heapPrimitives=nevernest&mode=display&origin=opt-live.js&py=js&rawInputLstJSON=%5B%5D&textReferences=false)，浏览器里会打开一个新的页面，里面有下面的代码段。

```javascript
function fibonacci(n){
    if(n < 0) throw new Error('你需要输入数字 >= 0的整数');
    if (n == 0) return 0; 
    if (n == 1) return 1; 
    if (n >= 2){
        return fibonacci(n-1) + fibonacci(n-2);      
    } 
}
    
console.log(fibonacci(6))
```

![](/images/数论/典型数列/Code：计算出斐波那契数列中的各个整数值/2b1.jpg)
![](/images/数论/典型数列/Code：计算出斐波那契数列中的各个整数值/2b2.jpg)
![](/images/数论/典型数列/Code：计算出斐波那契数列中的各个整数值/2b3.jpg)

单击右方的[在线代码段Url网址](http://www.pythontutor.com/live.html#code=function%20fibonacci%28n%29%7B%0A%20%20%20%20if%20%28n%20%3C%200%29%20throw%20new%20Error%28'%E4%BD%A0%E9%9C%80%E8%A6%81%E8%BE%93%E5%85%A5%E6%95%B0%E5%AD%97%20%3E%3D%200%E7%9A%84%E6%95%B4%E6%95%B0'%29%3B%0A%20%20%20%20let%20arrOfNums%20%3D%20%5B0,1%5D%3B%0A%0A%20%20%20%20function%20calc%28n%29%7B%0A%20%20%20%20%20%20%20%20if%28n%20%3C%202%29%7Breturn%20arrOfNums%5Bn%5D%3B%7D%0A%20%20%20%20%20%20%20%20if%28arrOfNums%5Bn%5D%20!%3D%20undefined%29%7Breturn%20arrOfNums%5Bn%5D%3B%7D%0A%0A%20%20%20%20%20%20%20%20let%20valOfN%20%3D%20calc%28n-1%29%20%2B%20calc%28n-2%29%3B%0A%20%20%20%20%20%20%20%20arrOfNums%5Bn%5D%20%3D%20valOfN%3B%0A%20%20%20%20%20%20%20%20console.log%28arrOfNums%29%3B%0A%20%20%20%20%20%20%20%20return%20valOfN%3B%0A%20%20%20%20%7D%0A%0A%20%20%20%20return%20calc%28n%29%3B%0A%7D%0A%0Aconsole.log%28fibonacci%286%29%29&cumulative=false&curInstr=67&heapPrimitives=nevernest&mode=display&origin=opt-live.js&py=js&rawInputLstJSON=%5B%5D&textReferences=false)，浏览器里会打开一个新的页面，里面有下面的代码段。

```javascript
function fibonacci(n){
    if (n < 0) throw new Error('你需要输入数字 >= 0的整数');
    let arrOfNums = [0,1];

    function calc(n){
        if(n < 2){return arrOfNums[n];}
        if(arrOfNums[n] != undefined){return arrOfNums[n];}

        let valOfN = calc(n-1) + calc(n-2);
        arrOfNums[n] = valOfN;
        console.log(arrOfNums);
        return valOfN;
    }

    return calc(n);
}

console.log(fibonacci(6))
```

## 参考文献及资料

1. 维基百科
	- [Fibonacci](https://en.wikipedia.org/wiki/Fibonacci) | [斐波那契](https://zh.wikipedia.org/wiki/%E6%96%90%E6%B3%A2%E9%82%A3%E5%A5%91) 
	- [Fibonacci number](https://en.wikipedia.org/wiki/Fibonacci_number) | [斐波那契数](https://zh.wikipedia.org/wiki/%E6%96%90%E6%B3%A2%E9%82%A3%E5%A5%91%E6%95%B0) 

2. [JavaScript实现斐波那契数列的四种方法介绍（代码）](https://www.php.cn/js-tutorial-416086.html) 

