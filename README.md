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

aluminum-strategy-agent/
├── README.md
├── LICENSE
├── strategy_suggestions.csv # 推理输出
│
├── notebooks/
│ ├── 1_data_preprocessing.ipynb
│ ├── 2_state_generation.ipynb
│ ├── 3_agent_inference.ipynb
│ ├── 4_model_training.ipynb
│ └── 5_strategy_evaluation.ipynb
│
├── data/
│ ├── aluminum_prices_sample.csv
│ ├── energy_index_sample.csv
│ ├── usd_index_sample.csv
│ ├── inventory_sample.csv
│ └── warehouse_daily_sample.xlsx
│
├── models/
│ └── logistic_model.pkl
│
└── docs/
└── project_report.md

---

## 🚀 快速开始

1. 克隆项目：

```bash
git clone https://github.com/your-username/aluminum-strategy-agent.git
cd aluminum-strategy-agent
```

2. 打开 notebooks/ 中的文件依次执行：

状态生成 ➝ GPT推理 ➝ 模型训练与策略评估

3. 生成策略建议文件：

`strategy_suggestions.csv`

🧠 技术栈
Python / Pandas / Scikit-learn

Azure OpenAI GPT API

Azure Blob Storage / Notebook

CSV 数据建模与策略追踪

📄 License
MIT License
