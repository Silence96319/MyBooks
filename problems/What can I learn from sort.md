# 一次爬坑历程——数组的sort()方法

​	今天偶然看到一个关于sort排序的问题，本以为比较简单，但最后弄了一上午，终于给弄明白了。问题代码如下：

```javascript
    function compare(pro) {return function(obj1, obj2) {
        var val1 = obj1[pro]
        var val2 = obj2[pro]
        if (val1 < val2) {
          return -1;
        } else {
          return 1;
        }
      }
    }
    var arr = [{
      name: "whwh",
      age: 18
    }, {
      name: "haha",
      age: 27
    }, {
      name: "atat",
      age: 9
    }]
    var arr1 = arr.sort(compare('age'))
    console.log(arr1)
    console.log(arr1[1].name,arr1[1].age)
    var arr2 = arr.sort(compare('name'))
    console.log(arr2)
```

看上去结果很明显吧，下面就是正确结果~

```javascript
    console.log(arr1)
    //[{
    //   name: "atat",
    //   age: 9
    // },
    // {
    //   name: "haha",
    //   age: 27
    // },
    // name: "whwh",
    // age: 18
    // }]
    console.log(arr1[1].name, arr1[1].age)
    //whwh 18
    console.log(arr2)
    //[{
    //   name: "atat",
    //   age: 9
    // },
    // {
    //   name: "haha",
    //   age: 27
    // },
    // name: "whwh",
    // age: 18
    // }]
```

……

​	我看到结果之后瞬间懵了，这个arr1是怎么了。。。

​	''幸好''这时群里有人提醒，说这是浅拷贝的原因，arr1、arr2都是对arr的引用，而那个值则是primitive value。这一句话对我来讲真是太关键了，彻底让我沦陷到懵里去了。。。既然是引用，那么arr1打印出来的结果为什么会跟arr2一样？难道是我对浅拷贝的理解或者说是对console.log的打印有误解？

​	想到这，我就是一顿查找` 浅拷贝 ` `深拷贝` `栈` `内存` `堆`。。。

​	最终的结果是众说纷纭，但是总体来说实现浅拷贝和深拷贝的方法是一致的。如下代码所示：

```javascript
    //浅拷贝
    function clone(theObj) {
      var obj = {}
      for (var key in theObj) {
        obj[key] = theObj[key]
      }
      return obj
    }
    var obj = {
      a:1,
      b:{c:2,
         d:3},
      e:function () {
        alert(4)
      }
    }
    var obj1 = obj
    var obj2 = clone(obj)
    console.log(obj1.a,obj1.b,obj1.e)  //1 func...
    console.log(obj2.a,obj2.b,obj2.e)  //1 func...
    console.log(obj2.b.c) //2
    obj1.a = 5
    console.log(obj.a,obj1.a,obj2.a) //5,5,1
    obj2.a = 6
    console.log(obj.a,obj1.a,obj2.a) //5,5,6
    obj1.b.d = 7
    console.log(obj.b.d,obj1.b.d,obj2.b.d) //7,7,7
    obj2.b.d = 8
    console.log(obj.b.d,obj1.b.d,obj2.b.d)  //8,8,8
```

​	由上面的结果可以推论出，浅拷贝和赋值是不同的。赋值是通过只是将obj1的指针指向了obj对象，而浅拷贝是通过创建一个新的对象，将obj属性的值赋值给这个对象，将obj属性的的引用给obj2的属性，因此我大胆推论它们的内存图如下

| 变量名              | 栈     | 堆               |
| ------------------- | ------ | ---------------- |
| obj                 | 0x110  | [a,b,e]地址0x110 |
| obj1                | 0x110  | [a,b,e]地址0x110 |
| 0bj2                | 0x120  | [a.b,e]地址0x102 |
|                     |        |                  |
| obj.b/obj1.b/obj2.b | 0x1101 | obj.b地址0x1101  |
| obj.a/obj1.a        | 2      |                  |
| obj2.a              | 2      |                  |

​	再来看看深拷贝

```javascript
    //深拷贝
    function deepclone(initalObj, finalObj) {
      var obj = finalObj || {}
      for (var key in initalObj) {
        var prop = initalObj[key] //便面相互引用导致死循环
        if (prop === obj) {
          continue;
        }
        if (typeof prop === 'object') {
          obj[key] = (prop.constructor === Array) ? [] : {}
          arguments.callee(prop, obj[key])
        } else {
          obj[i] = prop
        }
        return obj
      }
```

​	深拷贝是创建一个对象，将另一个对象的所有属性包括其子项统统拷贝过来，因此是完全不同的两个对象，且子项也没有公共的引用。

​	通过上面对赋值、浅拷贝和深拷贝的认识，下面我们就可以进行对上述问题进行分析了。

​	首先，arr经过sort进行排序，其指针不变，对象内容发生变化。然后arr1引用了这个对象，其指针指向该对象，所以打印出来的是经过第一次排序的数组（与上面看到的结果不同，稍后解释）。第二次排序的时候，将第一次排序后的对象进行了又一次的排序。此时arr2也指向这个对象，打印的是第二次排序的结果。所以总体来说，这只是简单的指针指向问题。。。

​	但是，我的分析却与实际结果不同。。。

​	然后我又开始了分析之旅——之断点调试。

​	最后调试的结果竟然是与我的分析一致，也就是说我的思路都是正确的而console.log()它打印错了！为了验证我这一想法，我用console.time（）测试了代码运行的时间发现console.log()用的时间比较长，难道是console.log()还没打印出来的时候下面的代码就已经执行完了？？？

```javascript
    function compare(pro) {
      return function(obj1, obj2) {
        var val1 = obj1[pro]
        var val2 = obj2[pro]
        if (val1 < val2) {
          return -1;
        } else {
          return 1;
        }
      }
    }
    var arr = [{
      name: "whwh",
      age: 18
    }, {
      name: "haha",
      age: 27
    }, {
      name: "atat",
      age: 9
    }]
    var arr1 = arr.sort(compare('age'))
    console.log(arr1)
    // [{
    //   name: "atat",
    //   age: 9
    // },
    // {
    //   name: "whwh",
    //   age: 18
    // },
    // name: "haha",
    // age: 27
    // }]
    console.log(arr1[1].name, arr1[1].age)//whwh 18
    setTimeout(function() {
      var arr2 = arr.sort(compare('name'))
      console.log(arr2)
      // [{
      //   name: "atat",
      //   age: 9
      // },
      // {
      //   name: "haha",
      //   age: 27
      // },
      // name: "whwh",
      // age: 18
      // }]
    }, 10000)
```

​	结果就是这样的！弄了一上午最后发现是console.log（）对象时用时比较长最后导致输出结果不符合，但是这个并不是结局。。。

​	当点开打印的数组时，打印出来的数据没问题。。。而当不打开数组的时候，最终打印出来的还是最开始的结果=  =！ 无力了。。。

​        最最最后的结果是。。。

`console.log机制：console.log 知识输出一个对象的引用，当鼠标点击的时候，会去内存里取这个引用，取到的是最后的值！！！这才是正解！！！！`





