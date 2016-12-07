# Python sklearn 学习笔记
`By Stronger`
-----
## 学习内容
```
  package sklearn
  sklearn.cluster.AgglomerativeClustering
  sklearn.cluster.FeatureAgglomeration
  sklearn.model_selection.GridSearchCV
  sklearn.model_selection.RandomizedSearchCV
  sklearn.model_selection.ParameterGrid
  sklearn.model_selection.ParameterSampler
  sklearn.model_selection.fit_grid_point
```
## AgglomerativeClustering
<br>
### 层次聚类
<br>
**层次聚类**：一层一层地进行聚类，可以**从下而上地把小的cluster合并聚集**，也可以从上而下地将大的cluster进行分割。一般用得比较多的是从下而上地聚集。具体而言，就是每次找到距离最短的两个cluster，然后进行合并成一个大的cluster，直到全部合并为一个cluster。整个过程就是建立一个**树结构**。<br>
![树结构图](http://attach.dataguru.cn/attachments/portal/201308/30/101335h3te1bxmbk86zeqe.jpg)<br>
一开始每个数据点独自作为一个类，它们的距离就是这两个点之间的距离。而对于包含不止一个数据点的 cluster，就可以选择多种方法了。最常用的，就是average-linkage，即计算两个cluster各自数据点的两两距离的平均值。类似的 还有single-linkage/complete-linkage，选择两个cluster中距离最短/最长的一对数据点的距离作为类的距离。<br>
**层次聚类最大的优点**:它一次性地得到了整个聚类的过程，只要得到了上面那样的聚类树，想要分多少个cluster都可以直接根据树结构来得到结果，改变 cluster数目不需要再次计算数据点的归属。层次聚类的缺点是计算量比较大，因为要每次都要计算多个cluster内所有数据点的两两距离。另外，由于层次聚类使用的是贪心算法，得到的显然只是局域最优，不一定就是全局最优。<br>
**确定最优cluster数的方法**:可以根据聚类过程中，每次合并的两个cluster的距离来作大概判断，如下图。因为总共有2000个数据点，每次合并两个cluster，所以总共要做2000次合并,从图中可以看到在后期合并的两个cluster的距离会有一个陡增。**现实情况下可能没有这么明显**<br>
![距离图](http://attach.dataguru.cn/attachments/portal/201308/30/101415pm8uumher2lpu0mr.jpg)
### 参数
<br>
AgglomerativeClustering(n_clusters=2, affinity='euclidean', memory=Memory(cachedir=None), connectivity=None, compute_full_tree='auto', linkage='ward', pooling_func=<function mean>) <br>
<br>
Recursively merges the pair of clusters that minimally increases a given linkage distance. <br>
通过最小距离,递归的将新的元素加入到现有的聚类结果中 <br>**属于分层聚类的一种算法** <br>
<br>
1. n_clusters : int, default=2 <br>
The number of clusters to find. <br>
聚类的数量 <br>
<br>
2. connectivity : array-like or callable, optional <br>
Connectivity matrix. Defines for each sample the neighboring samples following a given structure of the data. This can be a connectivity matrix itself or a callable that transforms the data into a connectivity matrix, such as derived from kneighbors_graph. Default is None, i.e, the hierarchical clustering algorithm is unstructured. <br>
连接矩阵 <br>
<br>
3. affinity : string or callable, default: “euclidean” <br>
距离计算方式，如欧式距离、L2、L1 <br>
<br>
4. memory : Instance of joblib.Memory or string (optional) <br>用于缓存树的结果输出，输入为路径字符串，当设定为空值时，结果树将不被储存<br>
<br>
5. compute_full_tree : bool or ‘auto’ (optional)<br> 用于控制是否计算整棵树，可有效减少计算时间。<br>
<br>
6. linkage : {“ward”, “complete”, “average”}, optional, default: “ward”<br> 
    用于控制距离的比较方式<br>
    ward ：以最小方差作为判断标准<br>
    average：以cluster内各点到新点距离的平均值为判断标准<br>
    complete：以最大距离作为判断标准<br>
<br>
7. pooling_func : callable, default=np.mean<br> 用于控制将多个变量合并为一个变量<br>
<br>
### 属性
<br>
1. labels_ : array [n_samples]<br> 每个样本的标签<br>
<br>
2. n_leaves_ : int <br> 结果树中叶节点的数量<br>
<br>
3. n_components_ : int <br> 结果中cluster的数量<br>
<br>
4. children_ : array-like, shape (n_nodes-1, 2) <br> 每个非叶节点的子节点的数量<br>
### 方法
<br>
1. fit(X[, y])	Fit the hierarchical clustering on the data <br> 输入数据，进行分层聚类运算<br>
<br>
2. fit_predict(X[, y])	Performs clustering on X and returns cluster labels. <br> 输入数据X，并输出其标签<br>
<br>
3. get_params([deep])	Get parameters for this estimator. <br> 返回模型的参数<br>
<br>
4. set_params(\*\*params)	Set the parameters of this estimator. <br> 设置模型的参数<br>
