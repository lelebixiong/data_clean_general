📂 Data Cleaning for COVID-19 Research Datasets

🔍 项目简介
本项目致力于对与 COVID-19 疫苗和蛋白质研究相关的多个数据集进行自动化清洗和标准化处理。通过统一的 Python 脚本 input_sars.py，实现了如下功能：

缺失值处理（数值型用中位数填充，类别型用众数填充）

异常值检测与裁剪（使用 IQR 方法）

类型转换与分类变量编码（One-Hot Encoding）

数据标准化（Z-score 归一化）

无用列处理（删除常量列与重复行）

自动保存清洗后的结果到 cleaned/ 文件夹

该清洗流程可用于后续的机器学习建模、特征提取与生物信息学分析任务。

📁 项目结构
bash
复制
编辑
data_clean_general/
├── input_sars.py              # 主清洗脚本

├── surf dataset/              # 原始数据目录

│   ├── covid.csv

│   ├── windows_ag.csv

│   └── ...

├── cleaned/                   # 清洗后的数据将保存在此目录

├── .gitattributes             # Git LFS 配置

├── .gitignore

└── README.md                  # 项目说明文件

⚙️ 使用方法
1. 安装依赖（建议使用虚拟环境）
bash
复制
编辑
pip install -r requirements.txt
# 或手动安装
pip install pandas numpy
2. 运行清洗脚本
bash
复制
编辑
python input_sars.py
脚本默认读取文件路径为：

python
复制
编辑
file_path = r"D:\surf dataset\ED.csv"
你可以自行修改为其他数据集路径。

✅ 清洗流程说明
步骤	描述
1	读取 CSV 文件（支持自动类型推断与错误处理）
2	数值列缺失值填充（中位数）
3	类别列缺失值填充（众数）
4	删除重复行
5	裁剪异常值（IQR）并保证非负
6	将分类变量统一为小写并尝试转为数值
7	对低基数分类变量进行 One-Hot 编码
8	对数值列进行 Z-score 标准化
9	删除常量列（无信息）
10	保存到 cleaned/ 子文件夹中

⚠ 注意事项
部分大文件（如超过 100MB 的 CSV）使用 Git LFS 管理，请确保已安装 Git LFS。

清洗后的文件可能会被自动重命名为 *_cleaned.csv 保存在 cleaned/ 子目录中。

清洗逻辑中的变量处理规则可根据具体数据情况自定义修改。

📦 Git LFS 支持（如适用）
若你是项目协作者，请确保运行以下命令以启用大文件支持：

bash
复制
编辑
git lfs install

👤 作者信息
作者：陈熙元（Xiyuan Chen）

项目方向：AI for COVID-19 vaccine（疫苗与蛋白质数据处理）

联系方式：[你的邮箱或 GitHub 地址]

📜 许可证
本项目代码采用 MIT License，数据文件请遵循原始来源的版权声明。
