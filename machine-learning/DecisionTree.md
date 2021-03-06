# 决策树

## 目录

- <a href="#liucheng"> 基本流程</a>
- <a href="#choice">划分选择</a>

##  <a id="liucheng">基本流程</a>

决策树是机器学习中一个常见的机器学习算法，即使是在小量数据上也能够有很好的拟合效果，顾名思义，此算法是基于树结构进行决策过程，同时这与人类做决策时的机制很类似，也易于理解。我相信大多数人看到这个名字，就已经出现了**N-if-else**的树形结构图了~~~

> 数据量大了，这个算法就显得有些鸡肋，需要使用更有学习能力的工具

需要知道的知识点：

- 决策过程中每个判定问题都是对某个属性的**“测试”**，每个测试的结果或是导出最终结论，或是导出进一步的判定问题，其考虑范围都是在上次决策结果的前行范围之内。每进行一次决策，都是对属性域进行进一步分割，然后在各自分割后的域内做进一步决策过程。

- 叶子节点对应着判定结果，内部节点（非叶子节点）代表着属性测试。

- 处理过程遵循**分而治之**的思想。

**流程如下：**

```python
def TreeGenerate(D,A):
    """
    D = {(x_1,y_1),(x_2,y_2),...,(x_m,y_m)}
    A = {a_1,a_2,...,a_d}
    """
    node = TreeNode()
    if D 中样本全部属于一个类别C:
        将node标记为C类叶节点
        return
    if A = None or D 中样本在A上取值相同:
        将node标记为叶节点，其类别标记为D中样本数最多的类
        return
    a = A 中最优划分属性
    for a_i in set(D.a):
        child_node = TreeNode()
        D_a_i = D[D.a == a_i] # 在数据集中筛选该属性值对应的数据
        if D_a_i == None or len(D_a_i) ==0:
            child_node = LeafNode()
            child_node.type = max(D) # 选择D中样本最多的类
            return
        else:
            TreeGenerate(D_a_i,a_i)
```

> 将西瓜书上面的算法描述，用`python伪代码`描述了一遍，比较适合程序员阅读 😁 

以上代码为伪代码，如果想要查看具体示例，可看[scikit-learn官方代码用例]( https://scikit-learn.org/stable/modules/tree.html )。

根据以上代码可知：决策树的生成过程是一个**递归过程**。

##  <a id="choice">划分选择</a>

- **纯度**：分支节点所包含的数据尽可能只分为同一类别

- 信息熵越小，纯度越高（信息熵越小，数据混乱程度越小）

  > 整个世界都是始终处于一个熵增的过程：世界在不停的运动，混乱程度也在不停的在增大

- 信息增益越大，使用该属性来划分所得到的**纯度提升**也就越大。

- 



## 问题测试

- [30 Questions to test a data scientist on Tree Based Models]( https://www.analyticsvidhya.com/blog/2017/09/30-questions-test-tree-based-models/ )
- [226 questions with answers in Decision Trees](https://www.researchgate.net/topic/Decision-Trees)