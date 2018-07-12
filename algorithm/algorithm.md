JavaScript数据结构与算法

目录 JavaScript数据结构与算法
1.基本语句
2.数组
3.列表
4.栈
5.队列
6.链表
7.字典
8.散列
9.集合
10.二叉树和二叉树查找
11.图和图算法
12.排序算法
13.检索算法
14.高级算法


1.基本语句

- if-else if 
- switch (){}
- while
- do...while
- for
- for...in

2.数组

- 读写数组
  - str.split('分隔符'[,限制数组的个数])
    - 作用：由字符串生成数组
    - 返回值：返回分隔后的每部分（字符串）组合在一起的数组
    - 注意：字符串和分隔符都是空字符串，则返回一个空数组 
    
  - 浅复制
    - 简单的数组元素赋值操作------数组相应元素的引用不变





---

- 存取数组
  - arr.indexOf(searchElement[, fromIndex = 0])   或lastindexOf()
    - 作用：查找元素
    - 返回值：首个被找到的元素在数组中的索引位置; 若没有找到则返回 -1
    - 注意：fromIndex为负则为倒数第几个开始查找
    
  - join('分隔号')   
    - 作用：数组转字符串  ，另外还有toString方法
    - 返回值：字符串
    - 注意：当join不传参的时候逗号还是以逗号的方式输出
    
  - new_array = old_array.concat(value1[, value2[, ...[, valueN]]])  
    - 作用：创建新数组
    - 返回值：新的数组，‘不影响旧的数组’
    - 注意：返回的是其它数组的浅拷贝，对于新数组的任何操作（仅当元素不是对象引用时）都不会对原始数组产生影响，反之亦然
    
  ---
  - array.splice(start[, deleteCount[, item1[, item2[, ...]]]])
    - 作用：对原数组进行操作：删除数组元素，增加数组元素。返回新的（删除的元素组成的）数组
    - 返回值：
      - 由被    ——删除——   的元素组成的一个数组 ====> 如果是增添元素，则返回一个空的数组
    - 注意：splice() 方法会直接对数组进行修改。 





---

- 可变函数：
  - 追加元素 ====> 返回数组长度
    - arr.push(element1, ..., elementN)	
      - Array.prototype.push.apply(arr1, arr2);     //将arr2融入到arr1中
      
    - arr.unshift(element1, ..., elementN)
          arr.unshift(-2, -1); // = 5
          //arr is [-2, -1, 0, 1, 2]   //注意-2和-1的顺序
  
  - 删除元素 ====> 返回删除的元素
    - arr.pop()
      - pop 方法从一个数组中删除并返回最后一个元素。 
      - 从数组中删除的元素(当数组为空时返回undefined) 
      
    - arr.shift()
      - shift 方法从一个数组中删除并返回第一个元素。
        
  - 为数组排序：
    - reverse() 
      - reverse 方法颠倒数组中元素的位置，并返回该数组的引用。 
      - 原数组元素被颠倒，且返回一个该数组的引用
      
    - sort(compareFunction)
      - 返回排序后的数组。原数组已经被排序后的数组代替。 
  
  
  ---
- 迭代器方法
  - 不生成新数组的迭代器方法
    - forEach()
      - array.forEach(callback(currentValue, index, array){
            //do something
        }, this)
      - 没有返回一个新数组! &&&& 没有返回值! 
      
    - every()
      - arr.every(callback[, thisArg])====callback用来测试每个元素的函数。
      - callback 被调用时传入三个参数：元素值，元素的索引，原数组。 
      - 回调函数都有返回的布尔值，只有当都为true时，最终整个操作结果才会返回true
    - some()
      - 回调函数都有返回的布尔值，当有一个返回值为true时，最终整个操作结果返回true
      
    - arr.reduce(callback[, initialValue])
          [0, 1, 2, 3, 4].reduce(function(accumulator, currentValue, currentIndex, array){
            return accumulator + currentValue;
          });
      - 返回函数累计处理的结果 
      
      
      ---
- 生成新数组的迭代器
  - map()
        let new_array = arr.map(function callback(currentValue, index, array) { 
            // Return element for new_array 
        }[, thisArg])
    - 一个新数组，每个元素都是回调函数的结果。 
  - filter()
    - 为数组中的每个元素调用一次 callback 函数，并利用所有使得 callback 返回 true 或 等价于 true 的值 的元素创建一个新数组 





- 创建二维数组
      Array.matrix = function(numrows, numcols, initial) {
      var arr = [];
      for (var i = 0; i < numrows; ++i) {
      var columns = [];
      for (var j = 0; j < numcols; ++j) {
      columns[j] = initial;
      }
      arr[i] = columns;
      }
      return arr;
      }





3.列表

- 列表的抽象数据类型并未指明列表的存储结构 

  属性/方法         	作用               
  listSize（属性）  	列表的元素个数          
  pos（属性）       	列表的当前位置          
  length（属性）    	返回列表中元素的个数       
  clear（方法）     	清空列表中的所有元素       
  toString（方法）  	返回列表的字符串形式       
  getElement（方法）	返回当前位置的元素        
  insert（方法）    	在现有元素后插入新元素      
  append（方法）    	在列表的末尾添加新元素      
  remove（方法）    	从列表中删除元素         
  front（方法）     	将列表的当前位置设移动到第一个元素
  end（方法）       	将列表的当前位置移动到最后一个元素
  prev（方法）      	将当前位置后移一位        
  next（方法）      	将当前位置前移一位        
  currPos（方法）   	返回列表的当前位置        
  moveTo（方法）    	将当前位置移动到指定位置     



                   

4.栈

- 栈是一种特殊的列表，栈内的元素只能通过列表的一端访问，这一端称为栈顶 
- 介绍：
  	栈被称为一种后入先出（LIFO，last-in-first-out）的数据结构。 
- 特点：
  	由于栈具有后入先出的特点，所以任何不在栈顶的元素都无法访问。为了得到栈底的元 素，必须先拿掉上面的元素。 
- 操作方法：
  	栈的两种主要操作是将一个元素压入栈和将一个元素弹出栈  



- 用途
  1. 数制间的转换
     - 依次每个位上得到的值压入栈
     - 当没有余数的时候，将栈内元素弹出知道栈为空
     - 将弹出的元素排列成字符串形式
  2. 回文：一个单词、短语或数字，从前往后写和从后往前写都是一样的。 
     - 将字符串的每个字符从左至右压入栈
     - 将栈内元素依次弹出拼成新的字符串
     - 判断两字符串是否相等
  3. 递归演示：
     - 将需要递归的数字n从n到1依次压入栈
     - 将数字挨个弹出连乘





5.队列

- 队列是一种列表，不同的是队列只能在队尾插入元素，在队首删除元素 
- 介绍：
  	队列是一种先进先出（First-In-First-Out，FIFO）的数据结构 。 
- 操作方法：
  	向队列中插入新元素和删除队列中的元素。插入操作也叫做入 队，删除操作也叫做出队。 



- 用途：使用队列对数据进行排序**
  1.基数排序：非最快的排序算法，但是比较有趣
  - 如对0-99的随机数字排序
    1. 建立10个队列(下标为0-9)
    2. 遍历数组，将个位数为n的数放入到下标为n的队列中-----入队
    3. 从0-9遍历队列，将每个队列中的元素取出来，拼成一个新的数组--------出对并且生成新的数组
    4. 遍历数组，将十位数为n的数放入到下标为n的队列中-----入队
    5. 从0-9遍历队列，将每个队列中的元素取出来，拼成一个新的数组--------出对并且生成新的数组
    6. 最终得到的数组即为排过序的数组
    
  2.优先队列
  - 比较优先码的大小，将优先级高的元素用splice方法移除并返回。
  - 依次执行上面的操作，将返回的值放入到一个新的队列当中





6.链表

- 数组缺陷：在很多编程语言中，数组的长度是固定 的，所以当数组已被数据填满时，再要加入新的元素就会非常困难。 
- JavaScript 的数组并不存在上述问题 ，但是JavaScript 中数组，它们被实现成了对象，与其他语言（比如 C++ 和 Java） 的数组相比，效率很低 



- 链表：
  - 是由一组节点组成的集合。每个节点都使用一个对象的引用指向它的后继。指向另一 个节点的引用叫做链 
  - 与数组的区别：数组元素靠它们的位置进行引用，链表元素则是靠相互之间的关系进行引用 



- 结构：
  - 许多链表的实现都在链表最前面有一个特殊节 点，叫做头节点 
  - 链表的尾元素指向一个 null 节点 
  
  - 插入节点：向链表中插入一个节点，需要修改它前面的节点（前 驱），使其指向新加入的节点，而新加入的节点则指向原来前驱指向的节点 ====》效率高
  - 删除节点：将待删除元素的前驱节点指向待删除元素的后继节点，同时 将待删除元素指向 null，元素就删除成功了 



- 方法：
  - 查找节点find()
            function find(item) {
              var currNode = this.head;
              while (currNode.element != item) {
                currNode = currNode.next;
              }
              return currNode;
            }
  - 插入节点insert()
            function insert(newElement, item) {
              var newNode = new Node(newElement);
              var current = this.find(item);
              newNode.next = current.next;
              current.next = newNode;
            }
  - 删除节点remove()
            function remove(item) {
              var prevNode = this.findPrevious(item);
              if (!(prevNode.next == null)) {
                prevNode.next = prevNode.next.next;
              }
            }
  ---
- 双向链表
  - 通过 给 Node 对象增加一个属性，该属性存储指向前驱节点的链接 (previous属性，最终指向null)
  - 插入删除节点的时候需要重新设置这个属性（previous）
  - 从某种程度来讲，双向链表从前往后或者从后往前，只有next和previous属性的差异而已



---

- 循环链表
  - 循环链表和单向链表相似，节点类型都是一样的。唯一的区别是，在创建循环链表时，让 其头节点的 next 属性指向它本身 
  - head.next = head 

```javascript
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>链表</title>
</head>

<body>
  <script>
  //问题：一共41人形成一个圈，从第一人开始数，每数到第三个人，该人就出局，
  //最后留下来的两人是哪两个
    var arr = []

    //创建包含对象的数组
    for (var i = 1; i < 42; i++) {
      arr.push(new node(i))
    }

    //关联数组中的对象
    for (var j = 0; j < 41; j++) {
      if (j < 40) {
        arr[j].next = arr[j + 1]
      } else {
        arr[j].next = arr[0]
      }
    }

    //调用删除数据的函数
    remove(arr)

    //对象构造函数
    function node(data) {
      this.data = data
      this.next = null
    }

    //找到相关的数据并在数组中删除它
    function find(item) {
      for (var i = 0; i < 41; i++) {
        if (item == arr[i]) {
          var newnode = arr.splice(i, 1)
        }
      }
      return newnode[0]
    }

    //循环查找并删除，最终打印剩余的数组
    function remove(arr) {
      var current = arr[0]
      while (arr.length > 2) {
        var remove = find(current.next.next)
        current.next.next = remove.next
        current = current.next.next
      }
      console.log(arr);
    }
  </script>
</body>

</html>

```



7.字典

- 介绍：
  - 字典是一种以键 - 值对形式存储数据的数据结构 
  - Dictionay 类的基础是 Array 类，而不是 Object 类 
  - 字典的主要用途是通过键取值，我们无须太关心数据在字典中的实际存储顺序。然而，很 多人都希望看到一个有序的字典 







8.散列

- 介绍：
  - 散列是一种常用的数据存储技术，
  - 散列后的数据可以快速地插入或取用。
  - 散列使用的数据 结构叫做散列表。 



- HashTable类
  - 选择一个散列函数
    - 将键值的ASCII码相加然后除以数组长度，然后将得到的余数作为该键值的键，从而来存储数据。
      - 数组的长度最好是质数，这样键就分布得比较均匀
      - 问题：得到的键可能发生重复（称为 --碰撞），从而覆盖之前的键值
  - 使用更好的散列函数
    - 键值 = 键值 * 一个质数 + 键值.charCodeAt(i)



- 碰撞处理：当散列函数对于多个输入产生同样的输出时，就产生了碰撞 
  - 开链法：
    - 将存储数据的数组转化成二维数组
    - 得到散列后的键的时候，查询这个里面的索引，找到没有存数据的位置。
    - 然后将键存进去，在下一个位置存数据
    - 最后通过散列后的键和散列前的键加1 即能找到该数据
  - 线性探测法：当发生碰撞时，线性探测法检查散列表中的下一个位置是否为空。如果为空， 就将数据存入该位置；如果不为空，则继续检查下一个位置，直到找到一个空的位置为 止 。
    - 如果数组的大小是待存储数据个数的 1.5 倍， 那么使用开链法；如果数组的大小是待存储数据的两倍及两倍以上时，那么使用线性探 测法。 
    - 方法：
      - 准备两个数组：一个放键，一个放数据
      - 得到散列后的键
      - 如果在放键的数组中，该键存在，那么向下一个位置寻找，看是否有空位。
      - 如果有空位，则将键放在该空位上。并且记录下这个空位的位置n
      - 在放数据的n的位置存入数据
      - 最后通过遍历放键的数组，找到该键的存放位置。再到放数据的数组中，找到该数据





9.集合

- 介绍：
  - 集合（set）是一种包含不同元素的数据结构 
    - 集合中的成员是无序的 
    - 集合中不允许相同成员存在。 







10.二叉树和二叉树查找

- 介绍：
  - 树是一种非线性的数据结构，以分层的方式 存储数据。 
  - 树由一组以边连接的节点组成 
    - 一棵树最上面的节点称为 根节点 
    - 如果一个节点下面连接多个节点，那么该节点称为父节点，它下面的节点称为子 节点。 
    - 没有任何子节点的节点称为叶子节点。 
    - 从一个节点到另一个节点的这一组边称为路径 
    - 以某种特定顺序 访问树中所有的节点称为树的遍历。 
    - 义树的层数就是树的深度。 



- 二叉树：是一棵空树或者由一个根节点和两棵子树构成，而每棵子树也是二叉树
  - 树是一种特殊的树，它的子节点个数不超过两个 
  - 一个父 节点的两个子节点分别称为左节点和右节点 



- 实现二叉查找树 ---------------BST
  - 查找正确插入点的算法： 
    1. 设当前节点为根节点（判断当前节点是否有根节点，无则设新节点为根节点）
    2. 如果插入节点的数据小于当前节点，则设当前节点为原节点的左节点；反之执行第四步
    3. 如果当前节点为null，就将新的节点插入这个位置，退出循环；反之，继续执行下一次循环
    4. 设当前节点为原节点的右节点
    5. 如果当前节点为null，就将新的节点插入这个位置，退出循环；反之，继续执行下一次循环
            //节点构造函数
            function Node(data = 0, left = null, right = null) {
              this.data = data
              this.left = left
              this.right = right
            }
        
            //二叉树构造函数
            function Bst() {
              this.root = null
              this.line = 0
            }
        
            //初始化方法
            //插入节点方法
            Bst.prototype.insert = function(data) {
              let newNode = new Node(data, null, null)
              if (!this.root) {
                this.root = newNode
              } else {
                let currentNode = this.root
                while (true) {
                  //使用变量parent保存当前对象的指针
                  let parent = currentNode
                  if (newNode.data < currentNode.data) {
                    currentNode = currentNode.left
                    if (currentNode === null) {
                      //这个位置是parent的left指向这个新的对象。而不是currentNode 指向这个对象，               //那样就会切断currentNode 指向currentNode.left 这个对象的引用
                      parent.left = newNode
                      break
                    }
                  } else {
                    currentNode = currentNode.right
                    if (currentNode === null) {
                      parent.right = newNode
                      break
                    }
                  }
                }
              }
            }
        
            //遍历方法
            Bst.prototype.inOrder = function(node) {
              //递归思想！！！
              //==========中序查找===========
              //当元素不为空的时候，
              //首先打印该元素的左边
              //其次打印该元素本身
              //最后打印该元素的右边
        
              //初始值是叶子节点：
              //左边不执行，本身自己打印，右边不执行
        
              if (!(node === null)) {
                this.inOrder(node.left)
                console.log(node.data)
                this.inOrder(node.right)
              }
        
              //==========先序查找===========
              // if (!(node === null)) {
              //   console.log(node.data)
              //   this.inOrder(node.left)
              //   this.inOrder(node.right)
              // }
        
              //==========后序查找===========
              // if (!(node === null)) {
              //   this.inOrder(node.left)
              //   this.inOrder(node.right)
              //   console.log(node.data)
              // }
        
            }
        
            //查找最小值方法
            Bst.prototype.getMin = function(node) {
              let currentNode = node
              while (!(currentNode.left === null)) {
                currentNode = currentNode.left
              }
              return currentNode
            }
        
            //查找最大值方法
            Bst.prototype.getMax = function(node) {
              let currentNode = node
              while (!(currentNode.right === null)) {
                currentNode = currentNode.right
              }
              return currentNode
            }
        
            //查找给定值方法
            Bst.prototype.find = function(data) {
              let currentNode = this.root
        
              while (!(currentNode === null)) {
                if (currentNode.data === data) {
                  return currentNode
                } else if (currentNode.data > data) {
                  currentNode = currentNode.left
                } else {
                  currentNode = currentNode.right
                }
              }
        
              return null
            }
        
            //删除节点方法
            Bst.prototype.remove = function(data) {
              //由于子节点可能是同样的值，所以在删除之后需要判断一下是否删除完了
              while (this.find(data)) {
                //调用删除节点的方法，接收删除数据后的根节点
                this.root = this.removeNode(this.root, data);
              }
            }
        
            /**
             *  [删除二叉树中的某个节点]
             *  @method
             *  @param  {[Object]} node [包含删除数据的节点]
             *  @param  {[Number]} data [需要删除的数据]
             *  @return {[Object]}      [删除数据后的节点]
             */
            Bst.prototype.removeNode = function(node, data) {
              //如果当前节点不存在，说明该二叉树中没有该数据，返回null相当于没有删除数据
              if (node == null) {
                return null;
              }
        
              //当找到了该数据的时候
              if (data == node.data) {
        
                // 如果该节点没有子节点，那么直接删除这个节点就行了
                if (node.left == null && node.right == null) {
                  return null;
                }
        
                // 如果节点没有左子节点，那么将父节点的子节点直接指向该节点的右节点
                if (node.left == null) {
                  return node.right;
                }
        
                // 如果节点没有右子节点，那么将父节点的子节点直接指向该节点的左节点
                if (node.right == null) {
                  return node.left;
                }
        
                // 如果该节点有两个子节点，那么用右侧子节点中的最小值或者左侧子节点中的最大值代替该节点=========>最好是选择右边，因为如果有重复的元素，以上的insert方法会将其插入到重复元素的右边。如果这时选择删除的是右边的元素的话，可能导致右边里面重复的元素被删除。所以这个时候选择用右边的最小值来替代而不是左边的最大值
                var tempNode = this.getMin(node.right);
                node.data = tempNode.data;
                // 然后删除那个替代的子节点（这个子节点是叶子节点）
                node.right = this.removeNode(node.right, tempNode.data);
                return node;
              }
        
              //如果要删除的数据小于当前节点的数据，
              //那么在在节点的左边删除数据。返回删除数据后的节点
              else if (data < node.data) {
                node.left = this.removeNode(node.left, data);
                return node;
              }
              //如果要删除的数据大于当前节点的数据，
              //那么在在节点的右边删除数据。返回删除数据后的节点
              else {
                node.right = this.removeNode(node.right, data);
                return node;
              }
            }
        
            //数连接节点的线的数量
            Bst.prototype.countLine = function(currentNode) {
                if (currentNode.left) {
                  this.line++
                  this.countLine(currentNode.left)
                }
                if (currentNode.right) {
                  this.line++
                  this.countLine(currentNode.right)
                }
                return this.line
            }
        
            //实例化二叉树对象
            let nums = new Bst()
            nums.insert(23)
            nums.insert(45)
            nums.insert(16)
            nums.insert(37)
            nums.insert(3)
            nums.insert(99)
            nums.insert(37)
            nums.insert(37)
            nums.insert(37)
            nums.insert(37)
            nums.insert(22)
            nums.insert(37)
            nums.remove(37)
            nums.inOrder(nums.root)
            console.log(nums.countLine(nums.root))
            // console.log(nums.getMin(nums.root))
            // console.log(nums.getMax(nums.root))
            // console.log(nums.find(45))
            // console.log(nums.find(33))









11.图和图算法

- 图由边的集合及顶点的集合组成 
  - 顶点也有权重，也称为成本。 
  - 如果一个 图的顶点对是有序的，则可以称之为有向图 
  - 如果图是无序的，则称之为无序图，或无向图 
  - 图中的一系列顶点构成路径，路径中所有的顶点都由边连接。
  - 路径的长度用路径中第一个 顶点到最后一个顶点之间边的数量表示 
  - 由指向自身的顶点组成的路径称为环，环的长度 为 0。 
  - 圈是至少有一条边的路径，且路径的第一个顶点和最后一个顶点相同 
  - 无论是有向图还是 无向图，只要是没有重复边或重复顶点的圈，就是一个简单圈。 
  - 除了第一个和最后一个顶 点以外，路径的其他顶点有重复的圈称为平凡圈 
  - 如果两个顶点之间有路径，那么这两个顶点就是强连通的 
  - 如果有向图的所有 的顶点都是强连通的，那么这个有向图也是强连通的。 



- 表示边 
  - 表示图的边的方法称为邻接表或者邻接表数组 
    - 将边存储为由顶点的相邻顶点列表构成的数组，并以此顶点作为索引 
  - 另一种表示图边的方法被称为邻接矩阵。它是一个二维数组，其中的元素表示两个顶 点之间是否有一条边。 



- 构建图
          let Graph = function(v) {
            this.vertices = v
            this.edges = 0
            this.arr = []
          }
      
          //初始化图，生成二维数组
          Graph.prototype.init = function() {
            for (let i = 0; i < this.vertices; i++) {
              this.arr[i] = []
              this.arr[i].push('')
            }
          }
      
          //添加边
          Graph.prototype.addEdges = function(v, w) {
            this.arr[v].push(w)
            this.arr[w].push(v)
            this.edges++
          }
      
          //显示图
          Graph.prototype.showGraph = function() {
            for (let i = 0; i < this.vertices; i++) {
              console.log(i + '====>')
              for (let j = 0; j < this.vertices; j++) {
                if (this.arr[i][j] != undefined) {
                  console.log(this.arr[i][j] + ' ')
                }
              }
            }
          }
      
      
          //实例化图
          let graph = new Graph(8)
          graph.init()
          graph.addEdges(1, 0)
          graph.addEdges(0, 2)
          graph.addEdges(1, 5)
          graph.addEdges(4, 3)
          graph.addEdges(4, 5)
          graph.showGraph()



- 搜索图
  - 深度优先搜索
    - 深度优先搜索包括从一条路径的起始顶点开始追溯，直到到达最后一个顶点，然后回溯， 继续追溯下一条路径，直到到达最后的顶点，如此往复，直到没有路径为止。这不是在搜 索特定的路径，而是通过搜索来查看在图中有哪些路径可以选择。 
            //深度优先搜索
            Graph.prototype.dfs = function(v) {
              this.marked[v] = true
              if (this.marked[v] != undefined) {
                console.log(v);
              }
              for (let i = 0; i < this.arr[v].length; i++) {
                if (!this.marked[this.arr[v][i]]) {
                  this.dfs(this.arr[v][i])
                }
              }
            }
    
  - 广度优先搜索
    - 广度优先搜索从第一个顶点开始，尝试访问尽可能靠近它的顶点。本质上，这种搜索在图 上是逐层移动的，首先检查最靠近第一个顶点的层，再逐渐向下移动到离起始顶点最远的 层 
            //构建图
            let Graph = function(v) {
              //顶点个数
              this.vertices = v
              //边的条数
              this.edges = 0
              //存储点与点之间的关系
              this.arr = []
              //用于判断哪个点已经被访问过了
              this.marked = []
              //用于存储点到点的指向
              this.edgeTo = []
              //
              this.vertexList = []
            }
        
            //初始化图，生成二维数组
            Graph.prototype.init = function() {
              for (let i = 0; i < this.vertices; i++) {
                this.arr[i] = []
                // this.arr[i].push('')
                this.marked[i] = false
              }
            }
        
            //添加边
            Graph.prototype.addEdge = function(v, w) {
              this.arr[v].push(w)
              this.arr[w].push(v)
              this.edges++
            }
        
            //显示图
            Graph.prototype.showGraph = function() {
              for (let i = 0; i < this.vertices; i++) {
                let str = i + '====>'
                for (let j = 0; j < this.vertices; j++) {
                  if (this.arr[i][j] != undefined) {
                    str += this.arr[i][j] + ' '
                  }
                }
                console.log(str)
              }
            }
        
            //深度优先搜索
            Graph.prototype.dfs = function(v) {
              this.marked[v] = true
        
              if (this.arr[v] != undefined) {
                console.log(v);
              }
        
              for (let i = 0; i < this.arr[v].length; i++) {
                if (!this.marked[this.arr[v][i]]) {
                  this.dfs(this.arr[v][i])
                }
              }
            }
        
            //广度优先搜索
            Graph.prototype.bfs = function(s) {
              //生成一个数列，专门用来存放遍历后的结果
              //将每一层的数据追加到该队列的后面
              let queue = []
              this.marked[s] = true
              queue.push(s)
        
              //遍历数列中的元素
              while (queue.length > 0) {
                let v = queue.shift()
        
                if (v !== undefined) {
                  console.log(v)
                }
        
                //循环遍历里面当前访问元素的所有子元素，并追加到队列之后
                for (let i = 0; i < this.arr[v].length; i++) {
        
                  //因为每一个this.arr[v]都是一个数组，所以length属性都是存在的
                  //为了知道队列在哪个位置终止===>使用条件判断，
                  //即如果所有的数据都已经被访问过了，那么队列后面就不会再追加数据了
                  if (!this.marked[this.arr[v][i]]) {
        
                    //存储子节点到父节点的指向===>当寻找路径的时候，利用这个指向来查找
                    this.edgeTo[this.arr[v][i]] = v
        
                    //将数据追加到数列中，并且把该数据标示为已经访问
                    //===>因为追加到数列当中的所有元素都 将会 被访问
                    this.marked[this.arr[v][i]] = true
                    queue.push(this.arr[v][i])
                  }
                }
              }
            }
        
            /**
             *  [寻找某个顶点到另一个顶点的最短路径]
             *  @method
             *  @param  {[Number]} source [出发的点]
             *  @param  {[Number]} target [最终到达的点]
             *  @return {[type]}        [description]
             */
            Graph.prototype.pathTo = function(source, target) {
              //因为在广度优先搜索中，已经将全部的点都搜索过了
              //那么如果这个目标点没有被搜索过的话，说明它不存在
              if (!this.marked[target]) {
                return console.log('can not find ' + target);
              }
        
              //因为target在bfs中都是唯一的，且有与上一个点的联系
              //因此，从target开始向上查找，直到找到source（bfs是以source来查找的）
              let path = []
        
              //起始值目标，终点值source，过程this.edgeTo
              for (let i = target; i != source; i = this.edgeTo[i]) {
                path.push(i)
              }
              path.push(source)
        
              this.showPath(path)
            }
        
            //显示路径
            Graph.prototype.showPath = function(path) {
              let str = ''
              while (path.length > 0) {
                if (path.length > 1) {
                  str += path.pop() + ' ===> '
                } else {
                  str += path.pop()
                }
              }
              console.log(str)
            }
        
            //拓扑结构
            Graph.prototype.topSort = function() {
              //栈用于存储访问过的数据
              let stack = []
        
              //用于存储数据是否被访问过，并全部初始化为false
              let visited = []
              for (let i = 0; i < this.vertices; i++) {
                visited[i] = false
              }
        
              // 从第0个顶点开始访问，如同深度优先搜索。但是最终会记录下搜索的数据的顺序
              for (let i = 0; i < this.vertices; i++) {
                if (visited[i] === false) {
                  this.topSortHelper(i, visited, stack)
                }
              }
        
              //根据记录的数据的顺序来访问真实数据
              for (let i = 0; i < stack.length; i++) {
                if (stack[i] !== undefined && stack[i] !== false) {
                  console.log(this.vertexList[stack[i]])
                }
              }
            }
        
            //拓扑结构辅助函数
            Graph.prototype.topSortHelper = function(v, visited, stack) {
              visited[v] = true
              stack.push(v)
              for (let i = 0; i < this.arr[v].length; i++) {
                if (!visited[this.arr[v][i]]) {
                  this.topSortHelper(this.arr[v][i], visited, stack)
                }
              }
            }
        
            //实例化图
            let graph = new Graph(8)
            graph.init()
            graph.addEdge(0, 1)
            graph.addEdge(1, 2)
            graph.addEdge(1, 3)
            graph.addEdge(2, 4)
            graph.addEdge(2, 5)
        
            console.log('显示图结构')
            graph.showGraph()
        
            console.log('深度优先搜索')
            graph.dfs(0)
            //注意在搜索的时候要先把之前的搜索给去掉，不然就全标记为搜索过了
        
            // console.log('广度优先搜索')
            // graph.bfs(0)
        
            // console.log('显示路径')
            // graph.pathTo(0, 1)
            // graph.pathTo(0, 2)
            // graph.pathTo(0, 3)
            // graph.pathTo(0, 4)
            // graph.pathTo(0, 5)
        
            graph.vertexList = ["CS1", "CS2", "Data Structures", "Assembly Language", "Operating Systems", "Algorithms", "promise", "silence"]
            console.log('拓扑排序')
            graph.topSort()
    

12.排序算法

- 基本排序算法
  - 冒泡排序
    - 它是最慢的排序算法之一，但也是一种最容易实现的排 序算法。 
    - 数据值会像气泡一样从数组的一端漂 浮到另一端。 
  - 选择排序
  - 插入排序
  - 速度：插入排序最快> 选择排序> 冒泡排序最慢
            //冒泡排序--升序
            function bubbleSortUp(arr) {
        
              for (let i = 0; i < arr.length; i++) {
                for (let j = 0; j < arr.length - i; j++) {
                  if (arr[j] > arr[j + 1]) {
                    let temp = arr[j]
                    arr[j] = arr[j + 1]
                    arr[j + 1] = temp
                  }
                }
              }
              return arr
            }
        
            //选择排序
            function selectSortUp(arr) {
        
              for (let i = 0; i < arr.length; i++) {
                for (let j = i + 1; j < arr.length; j++) {
                  if (arr[i] > arr[j]) {
                    let temp = arr[i]
                    arr[i] = arr[j]
                    arr[j] = temp
                  }
                }
              }
              return arr
            }
        
            //插入排序
            function insertionSortUp(arr) {
        
              //遍历数组，选择需要插入的元素
              for (let i = 0; i < arr.length - 1; i++) {
        
                //记录下这个时候这个待插入的数据
                let temp = arr[i]
                j = i
        
                //在这个数组的j前面的最后一个元素跟这个临时数据比较
                //如果临时数据比较小的话，那么这个数组的元素就要往后挪一下
                //当循环条件不满足的时候，说明这个数据已经找到了合适的位置
                //此时将临时数据插入即可
                while (j > 0 && arr[j - 1] >= temp) {
                  arr[j] = arr[j - 1]
                  j--
                }
                arr[j] = temp
              }
              return arr
            }
        
        
            let arr = []
            for (let i = 0; i < 20000; i++) {
              arr.push(parseInt(Math.random() * 5000))
            }
        
            // //计时开始
            // let start1 = Date.now()
            // console.log(bubbleSortUp(arr))
            // //计时结束
            // let end1 = Date.now()
            // console.log(end1 - start1)//1667ms
        
            // //计时开始
            // let start2 = Date.now()
            // console.log(selectSortUp(arr))
            // //计时结束
            // let end2 = Date.now()
            // console.log(end2 - start2)//970ms
        
            //计时开始
            let start3 = Date.now()
            console.log(insertionSortUp(arr))
            //计时结束
            let end3 = Date.now()
            console.log(end3 - start3) //418ms



- 高级排序算法
  - 希尔排序
            let arr = []
            for (let i = 0; i < 1000000; i++) {
              arr.push(parseInt(Math.random() * 50000))
            }
        
            //希尔排序，在插入排序的基础之上改进了排序的间隔===>由大间隔到小间隔
            function shellsort(arr) {
              let gaps = [701, 301, 132, 57, 23, 10, 4, 1]
              for (let g = 0; g < gaps.length; g++) {
                for (let i = arr[g]; i < arr.length; i++) {
                  let temp = arr[i]
                  let j = i
                  for (j; j >= gaps[g] && arr[j - gaps[g]] > temp; j -= gaps[g]) {
                    arr[j] = arr[j - gaps[g]]
                  }
                  arr[j] = temp
                }
              }
              return arr
            }
        
            let start = Date.now()
            console.log(shellsort(arr))
            let end = Date.now()
            console.log(end - start)
            //100万的数据花了3344ms
            //10万的数据花了80ms
            //通过改变gaps可以很有效的缩短时间





- 归并排序
  - 自顶向下的归并排序 ：。。。。。。。。。。（深奥？）
  - 自底向上的归并排序 
            function mergeSort(arr) {
              //如果数组成都小于2，那么就不需要合并了
              if (arr.length < 2) {
                return arr
              }
        
              //step用于将数组分成一小份一小份的
              let step = 1
              let left, right
        
              //只有当step大于等于数组长度的时候，才能说明数组已经完全合并了
              while (step < arr.length) {
                //设定初始值left从0到step，right从step到2*step
                left = 0
                right = step
        
                //只有当最右边的数据所在位置小于数组长度时才能循环
                while (right + step <= arr.length) {
        
                  //合并小数组
                  mergeArrays(arr, left, left + step, right, right + step)
                  //改变数组初始值，即合并同行其他的数组
                  left = right + step
                  right = left + step
                }
        
                //最后循环跳出的时候,right+step>arr.length,此时右边的终止点应该是arr.length
                if (right < arr.length) {
                  mergeArrays(arr, left, left + step, right, arr.length)
                }
        
                //完成了一次合并之后，非最后一个数组的数组的长度都翻倍了，因此step需要翻倍
                step *= 2
              }
        
              return arr
            }
        
            function mergeArrays(arr, startLeft, stopLeft, startRight, stopRight) {
              //生成两个空数组，数组长度最后需要加1，用来存哨兵值
              let leftArr = new Array(stopLeft - startLeft + 1)
              let rightArr = new Array(stopRight - startRight + 1)
        
              //将原数组的对应值复制给新生成的数组
              let j = startLeft
              for (let i = 0; i < leftArr.length - 1; i++) {
                leftArr[i] = arr[j]
                j++
              }
        
              let k = startRight
              for (let i = 0; i < rightArr.length - 1; i++) {
                rightArr[i] = arr[k]
                j
                k++
              }
        
              //将最后一个值设为哨兵值，方便后面值的比较（无穷大）
              leftArr[leftArr.length - 1] = Infinity //哨兵值
              rightArr[rightArr.length - 1] = Infinity //哨兵值
        
              //合并数组，将两个数组中的值比较后放入到原数组中
              let m = 0
              let n = 0
              for (let v = startLeft; v < stopRight; v++) {
                if (leftArr[m] <= rightArr[n]) {
                  arr[v] = leftArr[m]
                  m++
                } else {
                  arr[v] = rightArr[n]
                  n++
                }
              }
            }
        
        
            let arr = []
            for (let i = 0; i < 2000000; i++) {
              arr.push(parseInt(Math.random() * 50000))
            }
        
            let start = Date.now()
            console.log(mergeSort(arr));
            let end = Date.now()
            console.log(end - start)
            //100万  480ms
            //200万  1000ms





- 快速排序
          //快速排序是处理大数据集最快的排序算法之一
          function fastSorting(arr) {
            if (arr.length === 0) {
              return []
            }
            let lesser = []
            let greater = []
            //基准值
            let pivot = arr[0]
      
            for (let i = 1; i < arr.length; i++) {
              if (arr[i] < pivot) {
                lesser.push(arr[i])
              } else {
                greater.push(arr[i])
              }
            }
      
            return fastSorting(lesser).concat(pivot, fastSorting(greater))
          }
      
          let arr = []
          for (let i = 0; i < 5000000; i++) {
            arr.push(parseInt(Math.random() * 50000))
          }
      
          let start = Date.now()
          console.log(fastSorting(arr));
          let end = Date.now()
          console.log(end - start)
          //100万  1468ms
          //500万  13146ms
          //1000万 34746ms









13.检索算法

- 顺序查找---暴力查找
  - 查找最大值最小值---将第一个数设为基准，比较（换值）
  - 使用自组织数据 
    - 于对数据的查找遵循“80-20 原则” 
    - “80-20 原则”是指对某一数据集执行的 80% 的查找操作都是对其中 20% 的数据元素 进行查找 
    - 自组织的方式最终会把这 20% 的数据置于数据集的起始位置 
    - 类似这种“80-20 原则”的概率分布被称为帕累托（Pareto）分布 
    - 思想：
      1. 当查找一个数据的时候，让该数据跟它之前的第n(由自己设置)个数进行交换位置
      2. 当要查找的这个数据在前20%的时候，就不交换位置了。



- 二分查找：
  - 思想
    1. 将中点设置为（上边界加上下边界）除以 2 
    2. 如果中点的元素小于查询的值，则将下边界设置为中点元素所在下标加 1 
    3. . 如果中点的元素大于查询的值，则将上边界设置为中点元素所在下标减 1。 
    4. 否则中点元素即为要查找的数据，可以进行返回 
  - 计算重复次数
    - 先找到该数的位置，然后用两个循环分别向上向下查找，找到count++
    - 或者直接顺序查找







14.高级算法

- 动态规则
  - 动态规划有时被认为是一种与递归相反 的技术。 
  - 动态规划解决方案从底部开始解决问题，将所有小问题解决掉，然后合并成一个 整体解决方案，从而解决掉整个大问题。 
    使用递归去解决问题虽然简洁，但效率不高。包括 JavaScript 在内的众多语言，不能高效 地将递归代码解释为机器代码，尽管写出来的程序简洁，但是执行效率低下。但这并不是 说使用递归是件坏事，本质上说，只是那些指令式编程语言和面向对象的编程语言对递归 的实现不够完善，因为它们没有将递归作为高级编程的特性。 
     
  - 动态规划实例：计算斐波那契数列 
    - 递归函数中，有许多值都会被重复计算，因此效率较低
    - 动态规则中，将之前计算的数据保存了下来，所以效率较高
  - 
  - 计算斐波那契数列
            //计算斐波那契数列
            function fib(n) {
              let num = 1
              let nextnum = 1
              let sum = 0
              for (let i = 2; i < n; i++) {
                sum = num + nextnum
                num = nextnum
                nextnum = sum
              }
              return sum
            }
            console.log(fib(10)); //55
     
  - 求最长公共字符串
            //最长公共字符串
            function commonStr(str1, str2) {
              let max = 0
              let index = 0
              //生成的数组成都要加1
              let strArr = new Array(str1.length + 1)
              //生成二维数，行和列的长度都加1
              //因为不管后面在计算的时候需要第一组数据中的0（第一行和第一列）
              for (let i = 0; i <= str1.length; i++) {
                strArr[i] = new Array(str2.length + 1)
                for (let j = 0; j <= str2.length; j++) {
                  strArr[i][j] = 0
                }
              }
        
        
              //将整个二位数组看作是一个有行有列的表格
              //当字符相同的时候，交集位置加1（根据斜对角来定）
              for (let i = 0; i <= str1.length; i++) {
                for (let j = 0; j <= str2.length; j++) {
                  //将每一列每一行的第一个数设置为0
                  if (i === 0 || j === 0) {
                    strArr[i][j] = 0
                  }
                  //当字符相等的时候，它的长度等于前面的两个字符相等的长度加1
                  else if (str1[i - 1] == str2[j - 1]) {
                    strArr[i][j] = strArr[i - 1][j - 1] + 1
                  }
                  //如果不想等，那么就要重置这个计数了
                  else {
                    strArr[i][j] = 0
                  }
                  //将最大额字符串长度保存到max中，并且记录此时的索引
                  if (max < strArr[i][j]) {
                    max = strArr[i][j]
                    index = i
                  }
                }
              }
        
              let str = ''
              if (max === 0) {
                return ''
              } else {
                //根据记录的索引，以及max值，推导出公共字符串的第一个位置，遍历至最后一个位置
                for (let i = index - max; i < index; i++) {
                  str += str1[i]
                }
        
                return str
              }
            }
        
            console.log(commonStr('123456789', '467654321')) 
    
  - 背包问题
    - 递归思想
              //背包问题：递归解决方案
              function knapsack(capacity, size, value, n) {
                if (n === 0 || capacity === 0) {
                  return 0
                }
                if (size[n - 1] > capacity) {
                  return knapsack(capacity, size, value, n - 1)
                } else {
                  return Math.max(value[n - 1] + knapsack(capacity - size[n - 1], size, value, n - 1), knapsack(capacity, size, value, n - 1))
                }
              }
              let value = [4, 5, 10, 11, 13]
              let size = [3, 4, 7, 8, 9]
              let capacity = 16
              let n = 5
              console.log(knapsack(capacity, size, value, n));
       
    - 动态规则
              //背包问题：动态规划方案
              /**
               *  @param  {[type]}  capacity [背包的容积]
               *  @param  {[type]}  size     [每件物品的体积组成的数组]
               *  @param  {[type]}  value    [每件物品相应的价格组成的数组]
               *  @param  {[type]}  n        [物品的数量]
               *  @return {[type]}           [背包中装下物品的最高价格]
               */
              function dKnapsack(capacity, size, value, n) {
                //初始化一个二维数组
                let k = []
                for (let i = 0; i <= n; i++) {
                  k[i] = []
                }
          
                //当物品数量和背包容积增加时，相对应的能容下的最高价格的物品
                //物品数量递增
                for (let i = 0; i <= n; i++) {
          
                  //当物品数量一定时，背包的容积依次递增
                  for (let j = 0; j <= capacity; j++) {
          
                    //将行和列的开始位置 初始化为0
                    if (i === 0 || j === 0) {
                      k[i][j] = 0
                    }
          
                    //如果此时的背包数为i,背包容积为j
                    //第i个物品的体积小于背包的容积
                    //第一种情况为：含有第i个物品时的最高价格 =====> 但是其他值有可能取不到最佳值
                    //  即为 第i个物品的价格 + 物品数减1容积减区这个物品体积时的背包所能装下的最高价格
                    //第二种情况：不包含这个物品时 =====> 有可能第i个物品非常合适而不能达到最佳值
                    //  即为 有i-1个物品且在此背包容积下 能容下的最高价格
                    //根据两者的缺点 ====> 最后将两者比较，取结果自高者
                    else if (size[i - 1] <= j) {
                      k[i][j] = Math.max(value[i - 1] + k[i - 1][j - size[i - 1]], k[i - 1][j])
                    }
          
                    //由于物品体积大于背包的体积，所以该物品不能放入到背包，背包的最高价格与物品数-1的时候相同
                    else {
                      k[i][j] = k[i - 1][j]
                    }
                  }
          
                }
                return k[n][capacity]
              }
          
              let value = [13, 5, 10, 11, 4]
              let size = [9, 4, 7, 8, 3]
              let capacity = 16
              let n = 5
              console.log(dKnapsack(capacity, size, value, n)); //23
              //  ================= k的取值（为了方便观察将其放入对象中了） ===============
              // {
              //   0: [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
              //   1: [0, 0, 0, 0, 0, 0, 0, 0, 0, 13, 13, 13, 13, 13, 13, 13, 13],
              //   2: [0, 0, 0, 0, 5, 5, 5, 5, 5, 13, 13, 13, 13, 18, 18, 18, 18],
              //   3: [0, 0, 0, 0, 5, 5, 5, 10, 10, 13, 13, 15, 15, 18, 18, 18, 23],
              //   4: [0, 0, 0, 0, 5, 5, 5, 10, 11, 13, 13, 15, 16, 18, 18, 21, 23],
              //   5: [0, 0, 0, 4, 5, 5, 5, 10, 11, 13, 14, 15, 17, 18, 19, 21, 23]
              // }
      
- 贪心算法
  - 一种以寻找“优质解”为手段从而达成整体解决方案的算法 
  - 这些优质的解决 方案称为局部最优解
  - 将有希望得到正确的最终解决方案，也称为全局最优解 
     
  - 背包问题：
    - 选择性价比最高的物品 ====> 求出单价
    - 将所有性价比最高的物品放入背包
    - 如果背包还有剩余空间，将所有性价比其次的物品放入背包
    - ……循环……
    - 直到背包容积不够的时候，将该性价比的物品的一部分放入背包
