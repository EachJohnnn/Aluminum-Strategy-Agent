# 🧠 Aluminum Strategy Agent  
**基于 Azure OpenAI 的铝期货智能采购决策系统**

---

## 📌 项目简介

本项目旨在构建一个具备“状态感知 + 策略推理 + 行为验证”能力的智能铝期货策略系统，采用 Azure 平台提供的 OpenAI GPT 服务作为推理核心，并结合规则引擎与监督学习模型，形成一个可评估、可解释的多通道智能采购顾问原型系统。

该系统支持自动读取铝价、美元指数、能源价格与库存等多源数据，识别每日市场状态，并输出自然语言采购建议，结合仓单库存行为进行策略有效性验证。

---

## ⚙️ 系统模块

- **📊 状态感知**：每日提取铝价、美元、能源、库存等因素构建状态特征
- **🤖 AI Agent**：使用 Azure OpenAI GPT-4.1-mini 模型生成自然语言建议
- **📏 规则引擎**：基于专家经验构建条件判断建议
- **🧠 行为标签**：使用仓单日报生成实际采购行为标签 `actual_action`
- **📈 模型训练**：训练监督模型（逻辑回归）评估策略与行为的契合程度
- **✅ 策略评估**：对比 GPT、规则与模型策略的命中率与鲁棒性

---

## 📂 项目结构

```
aluminum-strategy-agent/
├── README.md
├── LICENSE
├── notebooks/                       # Jupyter Notebook分析流程
│   ├── 1_Perception_Agent.ipynb
│   ├── 2_AI_Reasoning_Agent.ipynb
│   └── 3_Model_Traning&Evaluation_Agent.ipynb
│
├── data/                            # 数据与输出
│   ├── state output/
│   │   ├── state_output.csv
│   │   ├── state_output2.csv
│   │   └── state_output3.csv
│   ├── strategy suggestions/
│   │   ├── strategy_suggestions.csv
│   │   ├── strategy_suggestions2.csv
│   │   ├── strategy_suggestions3.csv
│   ├── aluminum_prices_sample.csv
│   ├── energy_index_sample.csv
│   ├── usd_index_sample.csv
│   ├── inventory_sample.csv
│   └── warehouse_daily_sample.xlsx
│
├── models/                          # 训练模型
│   ├── logistic_model1.pkl
│   ├── logistic_model2.pkl
│   └── logistic_model3.pkl
│
└── docs/                            # 项目文档
    ├── Project Proposal.docx
    ├── Project Report.md
    └── 系统架构图.png
```
---

### 📁 data 文件说明

- `state output/`  
  - `state_output.csv`, `state_output2.csv`, `state_output3.csv`  
    存储不同版本或阶段的市场状态特征提取结果，用于后续推理与建模。

- `strategy suggestions/`  
  - `strategy_suggestions.csv`, `strategy_suggestions2.csv`, `strategy_suggestions3.csv`  
    存储系统输出的采购策略建议（不同轮次或模型版本）。
    
- `aluminum_prices_5years.csv`  
  铝价历史数据（五年），字段包括日期与价格。
- `energy_index_5years.csv`  
  能源价格指数（五年），用于评估能源成本影响。
- `futures_inventory.csv`  
  期货库存数据，辅助市场供需分析。
- `inventory_5years.xlsx`  
  五年期社会库存数据，含每日明细与实际采购行为标签。
- `usd_index_5years.csv`  
  美元指数（五年），用于捕捉汇率波动对市场的影响。

---

## 🚀 快速开始

1. 克隆项目：

```bash
git clone https://github.com/your-username/aluminum-strategy-agent.git
cd aluminum-strategy-agent
```

2. 打开 notebooks/ 中的文件依次执行：

状态生成 ➝ GPT推理 ➝ 模型训练与策略评估

3. 相关数据文件位于 `data/state output/` 与 `data/strategy suggestions/` 文件夹内。自动生成的策略建议文件为：

   - `data/strategy suggestions/strategy_suggestions.csv` 等

---

## 🧠 技术栈

- Python / Pandas / Scikit-learn
- Azure OpenAI GPT API
- Azure Blob Storage / Jupyter Notebook
- CSV/XLSX 数据建模与策略追踪

---

## 📄 License

MIT License
