# 树的结构

```
- Binary Trees:AA Tree, AVL Tree, Binary Search Tree, Binary Tree, Cartesian Tree,left child/right sibling tree, order statistic tree, Pagoda
 *       ,
 *       , ...
 *
 *     B Trees:
 *       B Tree, B+ Tree, B* Tree, B Sharp Tree, Dancing Tree, 2-3 Tree, ...
 *
 *     Heaps:
 *       Heap, Binary Heap, Weak Heap, Binomial Heap, Fibonacci Heap, Leonardo
 *       Heap, 2-3 Heap, Soft Heap, Pairing Heap, Leftist Heap, Treap, ...
 *
 *     Trees:
 *       Trie, Radix Tree, Suffix Tree, Suffix Array, FM-index, B-trie, ...
 *
 *     Multi-way Trees:
 *       Ternary Tree, K-ary tree, And-or tree, (a,b)-tree, Link/Cut Tree, ...
 *
 *     Space Partitioning Trees:
 *       Segment Tree, Interval Tree, Range Tree, Bin, Kd Tree, Quadtree,
 *       Octree, Z-Order, UB-Tree, R-Tree, X-Tree, Metric Tree, Cover Tree, ...
 *
 *     Application-Specific Trees:
 *       Abstract Syntax Tree, Parse Tree, Decision Tree, Minimax Tree, ...
/**
 * The remaining two data structures we are going to cover are both in the
 * "tree" family.
 *
 * Much like real life, there are many different types of tree data structures.
 *

 *
 * Little did you know you'd be studying dendrology today... and thats not even
 * all of them. But don't let any of this scare you, most of those don't matter
 * at all. There were just a lot of Computer Science PhDs who had something to
 * prove.
 *
 * Trees are much like graphs or linked lists except they are "unidirectional".
 * All this means is that they can't have loops of references.
 *
 *        Tree:                Not a Tree:
 *
 *          A                        A
 *        ↙   ↘                    ↗   ↘
 *      B       C                B ←–––– C
 *
 * If you can draw a loop between connected nodes in a tree... well, you don't
 * have a tree.
 *
 * Trees have many different uses, they can used to optimize searching or
 * sorting. They can organize programs better. They can give you a
 * representation that is easier to work with.
 */
```

一个节点数>5 的树，至少删去 1 个结点才可以使该树不连通。

# 二叉树

二叉树是有限个结点的集合，这个集合或者是空集，或者由一个根结点和两颗不相交的二叉树组成，其中一棵叫做根的左子树，另一棵叫做根的右子树。其中满二叉树被定义为高为`k`，并且有$2^k - 1$个结点的二叉树，如下图所示: ![](https://coding.net/u/hoteam/p/Cache/git/raw/master/2016/7/4/63495205-70BE-4584-B20E-27FFC97B01F6.png) 而完全二叉树是具有下述性质的二叉树：

- 所有叶节点都出现在$k$或者$k-1$层。
- $k-1$层的所有叶节点都在非终结结点的右边。
- 除了$k-1$层的最右非终结结点可能有一个(只能是左分支)或者两个分支之外，其余非终结结点都有两个分支。某个完全二叉树的示范如下: ![](https://coding.net/u/hoteam/p/Cache/git/raw/master/2016/7/4/854B0455-06CA-4E71-B6EA-B108AF55569E.png)

## Traversal:遍历

二叉树的遍历指的是按照一定的顺序访问二叉树的每个结点，使得每个结点被访问一次，并且仅访问一次。这样对二叉树进行一次完整而有规则的扫描，将得到二叉树结点的一个线性序列，这对于与二叉树结构相关的算法非常重要。遍历二叉树的主要方法有先根遍历、中根遍历与后根遍历。

### 先根遍历:PreOrder

先根遍历算法流程为:

- 若二叉树为空，则退出；否则
- 访问根结点；
- 先根顺序遍历左子树；
- 先根顺序遍历右子树；
- 退出。对于上图先根遍历的结果为：A B D H I E J C F G
  ### 中根遍历:InOrder
- 若二叉树为空，则退出；否则
- 中根顺序遍历左子树；
- 访问根结点；
- 中根顺序遍历右子树；
- 退出。对于上图中根遍历的结果为：H D I B J E A F C G
  ### 后根遍历:PostOrder
- 若二叉树为空，则退出；否则
- 后根顺序遍历左子树；
- 后根顺序遍历右子树；
- 访问根结点；
- 退出。对于上图后根遍历的结果为：H I D J E B F G C A 前序遍历:1 2 4 8 9 10 11 5 3 6 7 (规律：根在前；子树在根后且左子树比右子树靠前)； 中序遍历:8 4 10 9 11 2 5 1 6 3 7 (规律：根在中；左子树在跟左边，右子树在根右边)； 后序遍历:8 10 11 9 4 5 2 6 7 3 1 (规律：根在后；子树在根前且左子树比右子树靠前)； 其它例子: 前序遍历:ABDECFG 中序遍历:DBEAFCG 后序遍历:DEBFGCA 前序遍历:1 2 4 3 5 7 6 中序遍历:2 4 1 5 7 3 6 后序遍历:4 2 7 5 6 3 1 做类似的题目，你可以先由两个遍历画出二叉树。通过形象的二叉树来写出另一个遍历，写的方法如上(递归)。画出二叉树的方法如下: 已知一棵二叉树的前序序列和中序序列，构造该二叉树的过程如下: 1. 根据前序序列的第一个元素建立根结点； 2. 在中序序列中找到该元素，确定根结点的左右子树的中序序列； 3. 在前序序列中确定左右子树的前序序列； 4. 由左子树的前序序列和中序序列建立左子树； 5. 由右子树的前序序列和中序序列建立右子树。已知一棵二叉树的后序序列和中序序列，构造该二叉树的过程如下: 1. 根据后序序列的最后一个元素建立根结点； 2. 在中序序列中找到该元素，确定根结点的左右子树的中序序列； 3. 在后序序列中确定左右子树的后序序列； 4. 由左子树的后序序列和中序序列建立左子树； 5. 由右子树的后序序列和中序序列建立右子树。另外,站长团上有产品团购,便宜有保证

# 多叉树

四叉树或四元树也被称为 Q 树(Q-Tree)。四叉树广泛应用于图像处理、空间数据索引、2D 中的快速碰撞检测、存储稀疏数据等，而八叉树(Octree)主要应用于 3D 图形处理。对游戏编程，这会很有用。

## 四叉树

四叉树(Q-Tree)是一种树形数据结构。四叉树的定义是：它的每个节点下至多可以有四个子节点，通常把一部分二维空间细分为四个象限或区域并把该区域 里的相关信息存入到四叉树节点中。这个区域可以是正方形、矩形或是任意形状。以下为四叉树的二维空间结构(左)和存储结构(右)示意图(注意节点颜色与网 格边框颜色): ![](http://hi.csdn.net/attachment/201108/20/0_1313865588OPCK.gif) 四叉树的每一个节点代表一个矩形区域(如上图黑色的根节点代表最外围黑色边框的矩形区域)，每一个矩形区域又可划分为四个小矩形区域，这四个小矩形区域作为四个子节点所代表的矩形区域。四叉树存储结构的 c 语言描述：

```
/* 一个矩形区域的象限划分：:

       UL(1)   |    UR(0)
     ----------|-----------
       LL(2)   |    LR(3)
以下对该象限类型的枚举
*/
typedef enum
{
    UR = 0,
    UL = 1,
    LL = 2,
    LR = 3
}QuadrantEnum;

/* 矩形结构 */
typedef struct quadrect_t
{
    double  left,
            top,
            right,
            bottom;
}quadrect_t;

/* 四叉树节点类型结构 */
typedef struct quadnode_t
{
    quadrect_t    rect;          //节点所代表的矩形区域
    list_t        *lst_object;   //节点数据, 节点类型一般为链表，可存储多个对象
    struct  quadnode_t  *sub[4]; //指向节点的四个孩子
}quadnode_t;

/* 四叉树类型结构 */
typedef struct quadtree_t
{
    quadnode_t  *root;
    int         depth;           // 四叉树的深度
}quadtree_t;
```

### 建立四叉树

(1)利用四叉树分网格，如本文的第一张图<四层完全四叉树结构示意图>，根据左图的网格图形建立如右图所示的完全四叉树。伪码: Funtion QuadTreeBuild ( depth, rect ) { QuadTree->depth = depth;

/_创建分支，root 树的根，depth 深度，rect 根节点代表的矩形区域_/ QuadCreateBranch ( root, depth, rect ); }

Funtion QuadCreateBranch ( n, depth,rect ) { if ( depth!=0 ) { n = new node; //开辟新节点 n ->rect = rect; //将该节点所代表的矩形区域存储到该节点中将 rect 划成四份 rect[UR], rect[UL], rect[LL], rect[LR];

/_创建各孩子分支_/ QuadCreateBranch ( n->sub[UR], depth-1, rect [UR] ); QuadCreateBranch ( n->sub[UL], depth-1, rect [UL] ); QuadCreateBranch ( n->sub[LL], depth-1, rect [LL] ); QuadCreateBranch ( n->sub[LR], depth-1, rect [LR] ); } } (2)假设在一个矩形区域里有 N 个对象，如下左图一个黑点代表一个对象，每个对象的坐标位置都是已知的，用四叉树的一个节点存储一个对象，构建成如下右图所示的四叉树。![](http://hi.csdn.net/attachment/201108/20/0_1313865592s6Yc.gif) 方法也是采用递归的方法对该矩形进行划分分区块，分完后再往里分，直到每一个子矩形区域里只包含一个对象为止。伪码: Funtion QuadtreeBuild() { Quadtree = {empty}； For (i = 1;i<n;i++) //遍历所有对象 { QuadInsert(i, root)；//将 i 对象插入四叉树 }  
 剔除多余的节点； //执行完上面循环后，四叉树中可能有数据为空的叶子节点需要剔除 }

Funtion QuadInsert(i,n) //该函数插入后四叉树中的每个节点所存储的对象数量不是 1 就是 0 {  
 if(节点 n 有孩子) {  
 通过划分区域判断 i 应该放置于 n 节点的哪一个孩子节点 c；  
 QuadInsert(i,c)； } else if(节点 n 存储了一个对象) { 为 n 节点创建四个孩子； 将 n 节点中的对象移到它应该放置的孩子节点中； 通过划分区域判断 i 应该放置于 n 节点的哪一个孩子节点 c； QuadInsert(i,c)； } else if(n 节点数据为空)  
 { 将 i 存储到节点 n 中； } }

### 四叉树查找

1、采用盲目搜索，与二叉树的递归遍历类似，可采用后序遍历或前序遍历或中序遍历对其进行搜索某一对象，时间复杂度为 O(n)。

2、根据对象在区域里的位置来搜索，采用分而治之思想，时间复杂度只与四叉树的深度有关。比起盲目搜索，这种搜索在区域里的对象越多时效果越明显 ![](http://hi.csdn.net/attachment/201108/20/0_1313865576IER6.gif) 伪码：

```
Funtion find ( n, pos, )
  {
      If (n节点所存的对象位置为 pos所指的位置 )
          Return n;
      If ( pos位于第一象限 )
          temp = find ( n->sub[UR], pos );
      else if ( pos位于第二象限)
          temp = find ( n->sub[UL], pos );
      else if ( pos位于第三象限 )
          temp = find ( n->sub[LL], pos );
      else  //pos 位于第四象限
          temp = find ( n->sub[LR], pos );
      return temp;
  }
```

## 八叉树

较之四叉树，八叉树将场景从二维空间延伸到了三维空间。八叉树(Octree)的定义是：若不为空树的话，树中任一节点的子节点恰好只会有八个，或零个，也就是子节点不会有 0 与 8 以外的数目。那么，这要用来做什么？想象一个立方体，我们最少可以切成多少个相同等分的小立方体？答案就是 8 个。如下八叉树的结构示意图所示: ![](http://hi.csdn.net/attachment/201108/20/0_1313865581gEU3.gif)

# 哈夫曼

当树中的节点被赋予一个表示某种意义的数值，我们称之为该节点的权。从树的根节点到任意节点的路径长度(经过的边数)与该节点上权值的乘积称为该节点的带权路径长度。树中所有叶节点的带权路径长度之和称为该树的带权路径长度(WPL)。当带权路径长度最小的二叉树被称为哈夫曼树，也成为最优二叉树。

哈夫曼树在构造时每次从备选节点中挑出两个权值最小的节点进行构造，每次构造完成后会生成新的节点，将构造的节点从备选节点中删除并将新产生的节点加入到备选节点中。新产生的节点权值为参与构造的两个节点权值之和。举例如下：

- [](https://images2015.cnblogs.com/blog/872539/201611/872539-20161104194812346-1641453195.png)

- 备选节点为 a,b,c,d，权值分别为 7,5,2,4

- 选出 c 和 d 进行构造(权值最小),生成新节点为 e(权值为 6)，备选节点变为 7,5,6

- 选出 b 和 e 进行构造，生成新节点 f(权值为 11),备选节点为 7,11

- 将最后的 7 和 11 节点进行构造，最后生成如图所示的哈夫曼树

## 哈夫曼树的应用

在处理字符串序列时，如果对每个字符串采用相同的二进制位来表示，则称这种编码方式为定长编码。若允许对不同的字符采用不等长的二进制位进行表示，那么这种方式称为可变长编码。可变长编码其特点是对使用频率高的字符采用短编码，而对使用频率低的字符则采用长编码的方式。这样我们就可以减少数据的存储空间，从而起到压缩数据的效果。而通过哈夫曼树形成的哈夫曼编码是一种的有效的数据压缩编码。

# 多级分类

## 预排序遍历树算法

预排序遍历树算法(modified preorder tree traversal algorithm)是一种为查询而生的遍历树算法，如果业务需求要求查询的场景高于、多于增删改，可以考虑此算法，该算法会牺牲掉一些插入、删除的性能。算法简单概括：类二叉树先序遍历，将树上的每个节点标示 left、right、level、parent 属性（parent 可以更方便画出树结构），查询通过 left 和 right 取值，一般情况可以通过一条 sql 查询和排序出整个需要的树节点。

![image](https://user-images.githubusercontent.com/5803001/45407303-96bdb000-b69b-11e8-8791-b25e69425a74.png)

为了能够像上面的递归函数那样显示整个树状结构，我们还需要对这样的查询进行排序。用节点的左值进行排序：

```sql
SELECT * FROM tree WHERE lft BETWEEN 2 AND 11 ORDER BY lft ASC;
```

添加同一层次的节点的方法如下：

```sql
LOCK TABLE nested_category WRITE;

SELECT @myRight := rgt FROM nested_category WHERE name = 'Cherry';

UPDATE nested_category SET rgt = rgt + 2 WHERE rgt > @myRight;
UPDATE nested_category SET lft = lft + 2 WHERE lft > @myRight;

INSERT INTO nested_category(name, lft, rgt) VALUES('Strawberry', @myRight + 1, @myRight + 2);

UNLOCK TABLES;
```

添加树的子节点的方法如下：

```sql
LOCK TABLE nested_category WRITE;

SELECT @myLeft := lft FROM nested_category WHERE name = 'Beef';

UPDATE nested_category SET rgt = rgt + 2 WHERE rgt > @myLeft;
UPDATE nested_category SET lft = lft + 2 WHERE lft > @myLeft;

INSERT INTO nested_category(name, lft, rgt) VALUES('charqui', @myLeft + 1, @myLeft + 2);

UNLOCK TABLES;
```

每次插入节点之后都可以用以下 SQL 进行查看验证：

```sql
SELECT CONCAT( REPEAT( ' ', (COUNT(parent.name) - 1) ), node.name) AS name
FROM nested_category AS node,
nested_category AS parent
WHERE node.lft BETWEEN parent.lft AND parent.rgt
GROUP BY node.name
ORDER BY node.lft;
```
