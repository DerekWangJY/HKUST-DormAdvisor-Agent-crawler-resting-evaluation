# HKUST DormAdvisor Agent - Crawler - Resting - Evaluation

## 📖 项目简介

本项目是香港科技大学（HKUST）宿舍推荐智能体（Chatbot）的完整开发、测评与评估系统。项目涵盖了从数据爬取、知识库构建、智能体提示词设计、多模型测评到结果分析的全流程。

## 📁 目录结构说明

```
Agent - crawler - resting - evaluation/
├── Hall data/                      # 📚 HKUST宿舍知识库数据
├── 爬虫包crawler/                   # 🕷️ 数据爬虫工具
├── 智能体提示词Agent prompts/       # 🤖 Chatbot提示词配置
├── DeepseekV4Pro测评结果/          # 📊 DeepseekV4Pro模型测评数据
├── Kimi_k2.6测评结果/              # 📊 Kimi K2.6模型测评数据
├── qwen3.6plus测评结果/            # 📊 Qwen 3.6 Plus模型测评数据
├── bot_histories_full&batches/     # 📝 完整对话历史记录
├── 测评结果汇总/                    # 📈 多模型测评结果汇总
├── 测评结果可视化Report_figures_eng/ # 📊 测评结果可视化图表
└── HKUST宿舍推荐Chatbot 测评标准.md  # 📋 测评标准文档
```

## 📚 各模块详细说明

### 1. Hall data/ - 宿舍知识库数据

包含HKUST宿舍相关的14个核心知识库文件，作为Chatbot的事实依据：

| 文件名 | 内容说明 |
|--------|----------|
| `facility.md` | 宿舍设施配置信息 |
| `hall_admission_policy.md` | 宿舍入住政策与分配规则 |
| `hall_charges.md` | 宿舍费用标准 |
| `hall_charges_availability_matrix.md` | 费用与可用性矩阵 |
| `hall_key_dates.md` | 重要日期（申请、入住、退宿等） |
| `hall_life_checkin_checkout.md` | 入住与退宿流程 |
| `hall_life_guest_pass.md` | 访客通行证管理 |
| `hall_life_guide.md` | 宿舍生活指南 |
| `hall_life_services.md` | 日常生活服务 |
| `hall_members.md` | 宿舍成员信息 |
| `hall_reviews_chinese.md` | 宿舍评测（中文版） |
| `hall_room_types.md` | 宿舍房型信息 |
| `HKUST_Hall_Reviews_EN.md` | 宿舍评测（英文版） |
| `shrlo_about_and_contact.md` | SHRLO联系方式与办公信息 |

### 2. 爬虫包crawler/ - 数据采集工具

包含用于从HKUST官方网站爬取宿舍相关数据的Jupyter Notebook：

- `Crawler 1.1.ipynb` - 第一版爬虫脚本
- `Crawler 1.2.ipynb` - 优化版爬虫脚本

### 3. 智能体提示词Agent prompts/ - Chatbot配置

包含智能体的核心提示词配置：

- `hall chatbot prompt.md` - 宿舍推荐Chatbot的系统提示词
- `hall recommendation prompt.md` - 宿舍推荐专用提示词

### 4. 多模型测评结果

#### DeepseekV4Pro测评结果/
- 包含DeepseekV4Pro模型在不同测试集上的对话历史记录（CSV/XLSX格式）
- 测评报告：`HKUST_Chatbot测评报告_DeepseekV4Pro测评.md`
- 测试集：ada1, ada2, chen1, chen2, final_test_8, final_test_9, iedA-D

#### Kimi_k2.6测评结果/
- 包含Kimi K2.6模型在不同测试集上的对话历史记录
- 测评报告：`HKUST_Chatbot测评报告_Kimi_k2.6测评.md`

#### qwen3.6plus测评结果/
- 包含Qwen 3.6 Plus模型在不同测试集上的对话历史记录
- 测评报告：`HKUST_Chatbot测评报告_qwen3.6plus测评.md`

### 5. bot_histories_full&batches/ - 完整对话历史

包含所有批次的完整对话记录，用于深度分析和仲裁：
- `bot_histories__full100rows.csv` - 完整100行对话数据
- 各测试批次的详细对话记录（按用户账号分类）

### 6. 测评结果汇总/

多模型测评结果的汇总分析：

- `3models testing result.csv` - 三模型测试结果
- `3models_testing_result_final.csv` - 最终测试结果
- `final_arbitration_result.csv` - 最终仲裁结果
- `测评统计报告_多模型仲裁.md` - 多模型仲裁统计报告

### 7. 测评结果可视化Report_figures_eng/

测评结果的可视化图表（英文版）：

| 图表 | 说明 |
|------|------|
| `fig1_boxplot_scores.png` | 分数箱线图 |
| `fig2_radar_dimensions.png` | 多维度雷达图 |
| `fig3_consistency_pie_error_types.png` | 一致性与错误类型饼图 |
| `fig4_model_deviation_bar.png` | 模型偏差柱状图 |
| `fig5_score_distribution_hist.png` | 分数分布直方图 |
| `fig6_batch_comparison.png` | 批次对比图 |
| `fig7_pairwise_scatter.png` | 配对散点图 |

### 8. HKUST宿舍推荐Chatbot 测评标准.md

详细的测评标准文档，包含：
- 评分核心前提与原则
- 固定评分框架（总分100分，5个维度）
- 各维度详细打分与扣分规则
- 特殊场景评分规则
- 标准化测评执行流程
- 强制输出格式要求

## 🎯 测评维度

测评采用五维度评分体系（总分100分）：

| 维度 | 权重 | 说明 |
|------|------|------|
| 事实准确性 | 40分 | 对标知识库校验回答真实性 |
| 个性化适配能力 | 20分 | 用户身份、预算、偏好适配 |
| 问题解决与任务完成度 | 20分 | 提问点覆盖与诉求解决 |
| 合规性与边界控制 | 10分 | 服务边界与内容管控 |
| 回答规范性与可用性 | 10分 | Markdown格式与可读性 |

## 🚀 使用方法

### 1. 查看测评标准
```bash
cat "HKUST宿舍推荐Chatbot 测评标准.md"
```

### 2. 查看知识库数据
```bash
cd "Hall data"
ls -la
```

### 3. 运行爬虫（如需更新数据）
```bash
cd "爬虫包crawler"
# 使用Jupyter Notebook打开并运行
```

### 4. 查看测评结果
```bash
cd "测评结果汇总"
cat "测评统计报告_多模型仲裁.md"
```

## 📊 测评模型对比

本项目对比了三个主流大语言模型在HKUST宿舍推荐场景下的表现：

1. **DeepseekV4Pro** - 深度求索最新版本
2. **Kimi K2.6** - 月之暗面Kimi模型
3. **Qwen 3.6 Plus** - 阿里云通义千问模型

各模型的详细测评报告可在对应文件夹中查看。

## 🔧 技术栈

- **数据采集**: Python, Jupyter Notebook, Web Crawler
- **知识库**: Markdown格式结构化数据
- **智能体**: LLM-based Chatbot with Prompt Engineering
- **测评**: 多维度量化评分体系
- **可视化**: Python绘图库（Matplotlib/Seaborn等）
- **数据分析**: CSV/Excel数据处理

## 📝 项目说明

本项目是HKUST宿舍推荐系统的完整评估框架，包含：
- ✅ 完整的知识库构建流程
- ✅ 标准化的测评体系
- ✅ 多模型对比分析
- ✅ 可视化结果展示
- ✅ 仲裁与质量控制机制

## 👨‍💻 作者

Derek Wang JY

## 📄 许可证

本项目仅供学术研究使用。

## 📮 联系方式

GitHub: https://github.com/DerekWangJY

---

*最后更新: 2026年5月*