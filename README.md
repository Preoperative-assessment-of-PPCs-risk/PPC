## 项目结构:<br>
1.数据预处理与特征提取：这一部分负责读取和处理原始生理数据，应用平滑技术，提取相关特征，如心率变异性（HRV）、呼吸频率、血氧、睡眠分期等。<br>
2.特征筛选：使用 RFECV（递归特征消除与交叉验证）方法选择最优特征子集。<br>
3.模型训练：使用 XGBoost 等模型等对选定的特征进行训练，以预测目标变量（疾病分类）。<br>
4.模型调优：基于最优特征子集对模型超参微调。<br>
5.PPC预测：使用调优后的模型进行疾病分类任务。<br>
## 环境要求：<br>
确保已安装以下 Python 库：<br>
`pip install pandas xgboost scikit-learn neurokit2 hrvanalysis scipy`<br>
## 工作流程<br>
### 1. 数据预处理与特征提取<br>
从包含生理和临床特征的 Excel 文件中加载数据，提取多种原始生理数据，包括心电图（ECG）、呼吸、血氧（SpO2）和加速度数据，对原始数据应用平滑处理，使用滑动平均滤波。使用 NeuroKit2 提取心电图特征包括 R 波峰值检测，使用 hrvanalysis 库计算心率变异性（HRV）特征，同时还提取了呼吸、血氧饱和度和睡眠相关的特征。<br>
### 2. 特征筛选<br>
使用递归特征消除与交叉验证（RFECV）为每个模型的每个数据表选择最优特征子集。特征选择过程中使用 AUC（曲线下面积）作为评估标准。<br>
### 3. 模型训练<br>
使用 XGBoost 分类器等训练模型，StratifiedKFold（5折）进行交叉验证，将数据划分为训练集和测试集，然后计算多个性能指标，包括 F1 分数、准确率、精确度和 ROC AUC，以评估模型的表现。<br>
### 4. 模型调优<br>
使用 GridSearchCV 进行超参数调优。网格搜索会探索 n_estimators、max_depth 和 learning_rate 等超参数的不同值，以找到最佳的模型配置。<br>
### 5. PPC预测<br>
在完成特征提取、特征筛选和模型调优后，使用优化后的模型进行疾病分类。首先，将数据输入到模型中以生成预测结果。然后，基于分类结果打印性能指标，包括 AUC、准确率、F1 分数和精确度，以评估模型的效果和预测能力。
## 注意事项<br>
1.数据集包含心电图（ECG）、呼吸、SpO2 和加速度计等生理数据和电子病历中的临床数据，这些数据对于分析睡眠和其他健康状况至关重要。<br>
2.运行代码前，请确保文件路径`Physiological and Clinical Characteristics of Sleep 100.xlsx，clinical_data.csv`正确。
