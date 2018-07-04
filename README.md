环境配置：
    Anaconda 4.4.10, python 3.6.4

依赖库：
    pandas 0.22.0, numpy 1.14.2, scikit-learn 0.19.1, lightgbm 2.2.1

步骤说明：
    按文件名顺序依次运行代码，先后完成预处理、特征工程、模型训练与测试集预测

特征的使用与生成情况：
    除原始特征稀疏矩阵与组合ID稀疏矩阵外，还采用了分块转化率、点击量、点击比例偏好、兴趣类特征长度、兴趣类特征组合转化率共五组统计特征，构造过程分别用cvr、click、ratio、length、CV_cvr表示。其中cvr统计方法为将训练集分成五份，其中一份作为验证集不加入统计计算，其余四份交叉统计。而CV_cvr则是利用ct\marriageStatus\interest字段编码生成稀疏矩阵，通过lightgbm模型的特征重要性排序提取前二十维转化为onehot编码，与其余字段进行组合转化率统计，统计方法同cvr。
    
体会：
    模型方面
    
致谢：
    本次参赛特别感谢byran的baseline，让我学会了使用稀疏矩阵。另外，也特别感谢郭大开源的nffm，没有nffm，单靠lgb我们最后只能达到0.763+的成绩。
