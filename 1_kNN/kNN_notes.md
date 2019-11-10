# kNN

## 一、模型原理
### 1.1 模型定义
**kNN** (k-NearestNeighbor) 意为 k最近邻算法。即给出一个新样本，通过距离其最近的k个元素来判断该样本的类型的算法。
eg：判断X是什么颜色的，只需找到离他最近的5个点，如果都是红色，则他也是红色的。（找邻居+投票）

### 1.2 算法过程
模型三要素：距离度量、k值、分类决策规则。

**算法流程**
1. 计算到每个点距离，排序
2. 选出最近k个邻居，统计频率
3. 选取最高频类别为对象类别

### 1.3 模型作用
既可以用来做分类，也可以用来做回归。对数据没有假设，准确度高，对异常点不敏感。

## 二、代码实现
### 2.1 基本实现
构造样本
计算距离
距离排序：np.argsort(array)—>输入一个数组，返回的是排序后的索引（从小到大排序），如第一个元素是数组中最小的元素的索引
取前k个元素
统计类别：      
from collections import Counter
votes = Counter(y_label) —>输入为一个list，统计这个list中各元素出现的次数，返回一个字典
predict_y = votes.most_common(1)[0][0]—>返回字典中出现次数最多的元素

### 2.2 面向对象
assert impression, "warning" —>当assert后面为真时执行，否则则输出warning

### 2.3 sklearn的kNN
from sklearn.neighbors import KNeighborsClassifier
kNN_classifier = KNeighborsClassifier(n_neighbors=6)
kNN_classifier.fit(X_train, y_train)
y_predict = kNN_classifier.predict(x.reshape(1,-1))
