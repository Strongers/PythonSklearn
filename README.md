### Python sklearn 学习笔记
`By Stronger`
-----
### 学习内容
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

### 参数
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
    用于控制距离的比较方式
    ward ：以最小方差作为判断标准
    average：以cluster内各点到新点距离的平均值为判断标准
    complete：以最大距离作为判断标准
<br>
7. pooling_func : callable, default=np.mean<br> 用于控制将多个变量合并为一个变量<br>
<br>
### 属性
1. labels_ : array [n_samples]<br> 每个样本的标签<br>
<br>
2. n_leaves_ : int <br> 结果树中叶节点的数量<br>
<br>
3. n_components_ : int <br> 结果中cluster的数量<br>
<br>
4. children_ : array-like, shape (n_nodes-1, 2) <br> 每个非叶节点的子节点的数量<br>
### 方法
1. fit(X[, y])	Fit the hierarchical clustering on the data <br> 输入数据，进行分层聚类运算<br>
<br>
2. fit_predict(X[, y])	Performs clustering on X and returns cluster labels. <br> 输入数据X，并输出其标签<br>
<br>
3. get_params([deep])	Get parameters for this estimator. <br> 返回模型的参数<br>
<br>
4. set_params(\*\*params)	Set the parameters of this estimator. <br> 设置模型的参数<br>
