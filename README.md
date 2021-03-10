# Contest_RIZHAO
日照-公积金贷款逾期预测的代码文件

具体细节参考我的csdn博客：[日照-公积金贷款逾期预测-比赛总结](https://blog.csdn.net/qq_35167821/article/details/114324476)

## 文件导读

## 代码文件

1. [data_preprocessed.ipynb](data_preprocessed.ipynb)

   数据预处理：1 先处理年龄，2 再去除重复列

2. [data_visualization.ipynb](data_visualization.ipynb)

   数据可视化，查看train与test数据集的各个特征的分布

   1. 导入包
   2. 导入数据
   3. 查看数据描述
   4. 打印现有的列（特征）
   5. 小牛初试：尝试将年龄分组，并且可视化，查看分布
   6. 编写函数
   7. 查看数据取值个数，使用unique, 取值 > 100 为连续，否则为离散。
   8. 离散可视化
   9. 连续可视化
   10. 抽出一个特征检测是否正确

3. [oversampler.ipynb](oversampler.ipynb)

   因为正负样本不平衡，过采样数据，最后两类数据比例差不多

   1. 读取数据
   2. 拆分数据为X, y
   3. 随机采样数据
   4. 合并数据
   5. 导出数据
   6. 检查数据是否导入正确

4. [feature_gene_overampled.ipynb](feature_gene_overampled.ipynb)

   [test-gene.ipynb](test-gene.ipynb)

   特征衍生：对过采样后的数据，进行变量衍生

   这个是train数据的，还有一个test`test-gene.ipynb`，其实这个做的不好，应该在上面`train`的文件一起完成的，TODO.地址

5. [RandomForest.ipynb](RandomForest.ipynb)

   随机森林的粗调参，还被我打断了呜呜，简单记录。

## 数据文件

1. [train.csv](data_file/train.csv) | [test.csv](data_file/test.csv) | [submit.csv](data_file/submit.csv)

   是原始数据文件, `train`、`test`、`submit`分别是训练、测试、提交格式的文件。

2. [train-age-duplicate-processed.csv](data_file/train-age-duplicate-processed) | [test-age-duplicate-processed.csv](data_file/test-age-duplicate-processed.csv)

   是经过[data_preprocessed.ipynb](data_preprocessed.ipynb)处理后输出的已经处理了age和删除重复列的数据文件。以后的EDA数据可视化、特征衍生、特征的相关系数/VIF筛选、随机森林/lightGBM/CatBoost/XGBoost都是在此基础上进行的。

3. [train-age-oversampled.csv](data_file/train-age-oversampled.csv)

   [train-age-duplicate-processed.csv](data_file/train.csv)经过[oversampler.ipynb](oversampler.ipynb)过采样之后得到得到的文件。

4. [date_test_generation.csv](data_file/data_test_generation.csv)

   是[test-age-duplicate-processed.csv](data_file/test-age-duplicate-processed.csv)经过[test-gene.ipynb](test-gene.ipynb)特征衍生之后的`test`数据。（还有train的100多M，传不上来）

5. [data_train_corr.xlsx](data_file/data_train_corr.xlsx)

   是用来查看相关性的文件。经由[feature_gene_overampled.ipynb](feature_gene_overampled.ipynb)计算得到的相关性文件。

6. [submit_randomforest.csv](data_file/submit_randomforest.csv)

   将 [test.csv](data_file/test.csv) 数据放入粗调参之后的`RandomForest`模型中预测，得到的数据。