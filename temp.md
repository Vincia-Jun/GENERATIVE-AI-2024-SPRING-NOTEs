
以下是面试中常见的损失函数与激活函数相关题型及答案整理：


### **题型1：逻辑回归的损失函数是什么？**
**准确回答**：  
逻辑回归使用**交叉熵损失（Cross-Entropy Loss）**，也称为对数损失（Log Loss）。其数学表达式为：  

$$
L = -\frac{1}{N}\sum_{i=1}^N \left[y_i \log \hat{y}_i + (1-y_i) \log (1-\hat{y}_i)\right]
$$  

其中，$y_i$是真实标签（0或1），$\hat{y}_i$是模型预测的概率值。


### **题型2：二分类任务使用的loss和最后一层的激活函数是什么？**
**准确回答**：  
- **激活函数**：最后一层使用**Sigmoid**，将输出压缩到[0,1]区间，表示概率。  
- **损失函数**：使用**二元交叉熵损失（Binary Cross-Entropy Loss）**，与Sigmoid结合优化分类效果。


### **题型3：回归问题一般选择什么损失？**
**准确回答**：  
回归问题常用**均方误差（Mean Squared Error, MSE）**或**平均绝对误差（Mean Absolute Error, MAE）**。  
- **MSE**：对异常值敏感，梯度稳定，计算方便。  
- **MAE**：对异常值鲁棒，但梯度可能稀疏。


### **题型4：多分类任务的loss和激活函数如何设置？**
**准确回答**：  
- **激活函数**：最后一层使用**Softmax**，将输出转换为概率分布。  
- **损失函数**：使用**交叉熵损失（Categorical Cross-Entropy Loss）**，直接优化类别概率。


### **题型5：多标签分类任务如何选择loss？**
**准确回答**：  
- **激活函数**：每个标签独立使用**Sigmoid**（输出0/1概率）。  
- **损失函数**：使用**二元交叉熵损失（Binary Cross-Entropy Loss）**，每个标签单独计算损失后求和。

```python
import numpy as np
def sigmoid(z):
    return 1 / (1 + np.exp(-z))

def compute_loss_v1(y_true, y_pred):
    t_loss = y_true * np.log(sigmoid(y_pred)) + \
             (1 - y_true) * np.log(1 - sigmoid(y_pred))  # [batch_size,num_class]
    loss = t_loss.mean(axis=-1)  # 得到每个样本的损失值, 这里可以是
    return -loss.mean()  # 返回整体样本的损失均值（或其他）

if __name__ == '__main__':
    y_true = np.array([[1, 1, 0, 0], [0, 1, 0, 1]])
    y_pred = np.array([[0.2, 0.5, 0, 0], [0.1, 0.5, 0, 0.8]])
    print(compute_loss_v1(y_true, y_pred)) # 0.5926
```

```python
import torch
import torch.nn.functional as F

def sigmoid(z):
    return 1 / (1 + torch.exp(-z))

def compute_loss_v1(y_true, y_pred):
    t_loss = y_true * torch.log(sigmoid(y_pred)) + \
             (1 - y_true) * torch.log(1 - sigmoid(y_pred))
    loss = t_loss.mean(dim=-1)
    return -loss.mean()

if __name__ == '__main__':
    y_true = torch.tensor([[1, 1, 0, 0], [0, 1, 0, 1]], dtype=torch.float32)
    y_pred = torch.tensor([[0.2, 0.5, 0, 0], [0.1, 0.5, 0, 0.8]], dtype=torch.float32)
    print(compute_loss_v1(y_true, y_pred))
```
    

### **题型6：为什么回归问题不使用激活函数？**
**准确回答**：  
回归问题的输出是连续值，不需要激活函数。激活函数会引入非线性变换，可能限制模型拟合能力。例如，若强制输出在[0,1]区间，会导致模型无法预测超出该范围的真实值。


### **题型7：为什么分类问题需要激活函数？**
**准确回答**：  
分类任务需要将输出转换为概率或类别分布：  
- **Sigmoid**：用于二分类，输出概率值。  
- **Softmax**：用于多分类，输出归一化概率分布。  
激活函数使模型输出符合概率解释，便于交叉熵损失优化。


### **题型8：为什么交叉熵损失常用于分类问题？**
**准确回答**：  
交叉熵损失直接衡量预测分布与真实分布的差异，对概率输出敏感。其梯度与预测误差成正比，训练效率高，避免均方误差在分类任务中梯度消失的问题。


### **总结表格**
| 任务类型       | 激活函数       | 损失函数                     |
|----------------|----------------|------------------------------|
| 二分类         | Sigmoid        | 二元交叉熵                   |
| 多分类         | Softmax        | 交叉熵                       |
| 多标签分类     | Sigmoid（每个标签） | 二元交叉熵（逐标签求和）     |
| 回归           | 无             | MSE、MAE等                   |

**注意**：面试中需结合具体场景（如是否平衡数据、异常值处理）说明选择理由。
