   JavaScript数据结构与算法

基本语句

- if-else if 
- switch (){}
- while
- do...while
- for
- for...in

数组

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
  -  array.splice(start[, deleteCount[, item1[, item2[, ...]]]])
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





列表

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



                   

栈

- 栈是一种特殊的列表，栈内的元素只能通过列表的一端访问，这一端称为栈顶 
- 介绍：
  	栈被称为一种后入先出（LIFO，last-in-first-out）的数据结构。 
- 特点：
  	由于栈具有后入先出的特点，所以任何不在栈顶的元素都无法访问。为了得到栈底的元 素，必须先拿掉上面的元素。 
- 操作方法：
  	栈的两种主要操作是将一个元素压入栈和将一个元素弹出栈  



- 用途
  1. 数制间的转换
     -  依次每个位上得到的值压入栈
     - 当没有余数的时候，将栈内元素弹出知道栈为空
     - 将弹出的元素排列成字符串形式
  2. 回文：一个单词、短语或数字，从前往后写和从后往前写都是一样的。 
     - 将字符串的每个字符从左至右压入栈
     - 将栈内元素依次弹出拼成新的字符串
     - 判断两字符串是否相等
  3. 递归演示：
     - 将需要递归的数字n从n到1依次压入栈
     - 将数字挨个弹出连乘





队列

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





链表

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





字典

- 介绍：
  - 字典是一种以键 - 值对形式存储数据的数据结构 
  - Dictionay 类的基础是 Array 类，而不是 Object 类 
  - 字典的主要用途是通过键取值，我们无须太关心数据在字典中的实际存储顺序。然而，很 多人都希望看到一个有序的字典 

散列

- 介绍：
  - 散列是一种常用的数据存储技术，散列后的数据可以快速地插入或取用。
  -  散列使用的数据 结构叫做散列表。 



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





集合

- 介绍：
  - 集合（set）是一种包含不同元素的数据结构 
    - 集合中的成员是无序的 
    - 集合中不允许相同成员存在。 







二叉树和二叉树查找

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
             *  @param  {[type]} node [包含删除数据的节点]
             *  @param  {[type]} data [需要删除的数据]
             *  @return {[type]}      [删除数据后的节点]
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
        
                // 固若该节点有两个子节点，那么用右侧子节点中的最小值或者左侧子节点中的最大值代替该节点
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









图和图算法

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

排序算法

检索算法

高级算法


