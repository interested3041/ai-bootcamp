# ai-bootcamp
# 16 周零基础 → 可就业 的 **大模型应用工程师（RAG / LLM 应用）** 详细学习规划（可保存版）

下面是经我优化、面向 **2026 年企业刚需**、同时兼顾你导师要求“学开源 + 学 Cursor/Claude Code 等工业工具”的完整路线。每周都有明确目标、可交付物、关键命令/代码片段与面试/答辩素材。把这份文本复制到笔记或仓库 `README.md` 里即可保存。

> 核心原则：先跑通再理解、项目驱动、每周有交付物、代码优先于视频。
> 必备（立即准备）：Python、Visual Studio Code、Git、GitHub。

---

## 快速目录（点击式心智图）

1. 阶段0（W1–2） 环境与基础工具
2. 阶段1（W3–5） Python + 数据处理
3. 阶段2（W6–8） LLM API、Prompt 与本地模型
4. 阶段3（W9–12） RAG 全链路实战（核心）
5. 阶段4（W13–16） Agent、微调、工程化与面试冲刺
6. 交付物样板、常用命令、面试题、简历要点

---

## 阶段0：环境与基础工具（Week 1–2） — 目标：无障碍开发环境

**目标交付物**：GitHub 仓库 `yourname/ai-bootcamp`（含 README 环境安装说明）

Week 1 — 安装与验证

* 安装/验证：Python、Visual Studio Code、Git、注册 GitHub。
* 创建虚拟环境、测试脚本：

```bash
python -m venv .venv
# Windows:
.venv\Scripts\activate
# mac/linux:
source .venv/bin/activate
pip install -U pip
python -c "print('Hello AI')"
```

* 交付：README + 屏幕录制 30s

Week 2 — 快速 API 与 Docker

* 学会：FastAPI、uvicorn、Docker 基础。
* 快速任务：写 `GET /ping`，用 Docker 打包并运行。

```bash
pip install fastapi uvicorn
# app.py: FastAPI minimal
uvicorn app:app --reload
# Docker
docker build -t fastapi-demo .
docker run -p 8000:8000 fastapi-demo
```

* 交付：GitHub repo + Dockerfile + 运行演示 GIF

---

## 阶段1：Python 与数据处理（Week 3–5） — 目标：能处理数据、调试与脚本化

**关键工具**：`requests`, `numpy`, `pandas`, `matplotlib`

Week 3 — 基础巩固

* 任务：完成 50 个 Python 小练习（函数、列表、字典、文件读写、OOP 基础）。
* 交付：`exercises/` 仓库目录 + 测试脚本

Week 4 — 网络请求与数据清洗

* 任务：调用公开 API（例如 GitHub trending），用 `pandas` 清洗 CSV/Excel，画图。
* 示例：

```python
import requests, pandas as pd
resp = requests.get("https://api.github.com/repos/psf/requests")
```

* 交付：Notebook / script + 输出图表

Week 5 — 调试与自动化

* 任务：学 VS Code 调试、写小型自动化脚本（批量重命名/批量 CSV 清洗）。
* 交付：脚本 + README + 调试配置（`.vscode/launch.json`）

---

## 阶段2：LLM API、Prompt 与本地模型（Week 6–8） — 目标：能做多轮对话与结构化输出

**工具/平台**：本阶段任选免费 API 与本地推理工具（建议后续并行）——Hugging Face、Ollama

Week 6 — LLM API 基础

* 学习：Token、上下文窗口、temperature、streaming。
* 实战：调用一个免费或试用 API（或 Hugging Face inference）写 CLI 聊天机器人（多轮），支持流式。
* 交付：`cli-chatbot/` repo + 交互录屏

Week 7 — Prompt 工程与结构化输出

* 学习：清晰指令、few-shot、CoT、JSON Schema / Function Calling（让模型输出可机器解析的结构化 JSON）。
* 实战：实现 3 个 prompt：代码调试、文案生成、数据分析（写成 `prompts.md`），实现对 JSON 输出的解析与断言。
* 交付：`prompts.md` + 示例交互日志

Week 8 — 本地模型上手（Ollama / vLLM 可选）

* 任务：安装并运行 Ollama（或在资源受限时使用小模型），将聊天机器人切换到本地模型后端，对比延迟/成本。
* 交付：`local-backend/` demo + 简短对比报告（延迟/费用）

---

## 阶段3：RAG（Week 9–12） — **核心**：完成企业级知识库问答 Demo

**核心技术栈**：LangChain 或 LlamaIndex（选一为主），向量库：Chroma / FAISS（入门）

Week 9 — RAG 流程实现（单文档）

* 学习：文档加载 → 拆分 → 嵌入 → 存储 → 检索 → 生成。
* 实战：把一个 PDF 做成可问答的单文档 Demo（LangChain + SentenceTransformer 嵌入 + Chroma）。
* 交付：`rag-single-doc/` repo + demo 视频

Week 10 — 向量 DB 与混合检索

* 任务：对比 Chroma 与 FAISS（召回效果、延迟），实现 BM25 + vector hybrid 重排。
* 交付：对比表 + 代码中实现 hybrid rerank

Week 11 — 前端与多文档支持

* 任务：用 Streamlit 或 Gradio 实现上传多文档并查询，回答显示引用来源（文档 id /页）。
* 交付：可交互 Demo（Streamlit 链接或录屏）

Week 12 — 质量提升与测试

* 任务：chunk 策略优化、召回阈值调参、写 20 条测试问题/参考答案评估（精确率/召回）。
* 交付：测试报告 + 改进记录

---

## 阶段4：Agent、微调、工程化与面试冲刺（Week 13–16）

**目标**：把系统工程化、加上 Agent 能力做复杂任务、做一次轻量微调并准备面试材料

Week 13 — Agent（工具调用）

* 学习：ReAct、工具调用（Function Call）、记忆机制。
* 实战：实现一个 Agent：能检索知识库、执行受限 Python（分析表格）并生成报告（使用 LangChain Agent 或 LangGraph）。
* 交付：Agent 演示视频 + 代码

Week 14 — 轻量微调（就业加分）

* 学习：PEFT / QLoRA 的概念与流程（理解比深究更重要），运行一次 QLoRA 微调 demo（小数据集 100–500 条）并比较输出差异。
* 交付：微调脚本 + 前后对比样例

Week 15 — 工程化打包与部署

* 任务：将 RAG + Agent 打包成一个服务（FastAPI），写 Docker Compose、README、CI（GitHub Actions 简单流水线）。部署到小云主机或 Streamlit Cloud。
* 交付：完整 repo（Dockerfile + deploy 脚本）+ 部署演示链接/录屏

Week 16 — 简历、面试题、答辩准备

* 任务：撰写 1 页架构图、5–10 分钟 Demo 视频、准备 20 个常见面试问答（含 STAR 项目讲述）。模拟面试并录音。
* 交付：简历稿 + PPT（10 slides）+ Demo 视频

---

## 面试/答辩用素材（直接可用）

* 架构图 PNG：前端 → FastAPI → RAG → Vector DB → Model (本地/云)。
* Demo 视频清单：

  1. 上传 PDF → 回答并显示来源（2 min）
  2. Agent 自动执行任务（2 min）
  3. QLoRA 前后效果对比（1 min）
* 必备 README 模板（每个 repo 都要有）：功能、运行步骤、端口、样例请求、截图、成本估算

---

## 推荐学习资源（自助搜）

* Model hub：Hugging Face（找 qlora / embeddings 示例）
* RAG 库：LangChain、LlamaIndex
* 向量 DB：Chroma、FAISS、进阶可学 Milvus
* 本地推理：Ollama、vLLM
* 微调工具：PEFT、QLoRA
* AI 办公/效率：GitHub Copilot、Cursor、Claude Code（把它们当作生产力工具来学，用于加速开发）

---

## 每周检查点（你可以把它贴到 GitHub Issue）

1. 周末提交代码 + README
2. 每月一次把演示视频上传到 Google Drive / GitHub Release
3. 记录 3 个主要问题与解决方法（方便答辩写“遇到的问题与解决办法”）

---

## 简历 / 答辩写法建议（示例 bullet）

* “开发并部署基于 **RAG** 的企业知识库问答系统（FastAPI + LangChain + Chroma），支持 PDF/Word 上传与文档引用回答，部署于 Docker，平均查询延迟 < 300ms。”
* “实现 Agent 自动化流程：模型能自主调用检索、执行 Python 脚本并生成包含数据来源的报告。”
* “完成 QLoRA 轻量微调实验，提升特定话术准确率 18%（对比测试集）。”

---

## 常见面试题（你必须会答）

1. RAG 的核心流程是什么？如何避免模型幻觉？
2. 向量检索里为什么要做 chunking？chunk size 如何取？
3. Chroma / FAISS / Milvus 的适用场景与差异？
4. Function Calling / JSON Schema 实现的好处？
5. QLoRA 的基本原理与适用场景？
   （我可以把每题的答案写成 1–2 页速记稿给你）

---

## 现在就可执行的三件事（立刻行动）

1. 在 GitHub 建 `yourname/ai-bootcamp` 仓库并把本规划贴入 `README.md`。
2. 完成 Week1（安装 Python、VS Code、创建虚拟环境、push 第一个 commit）。
3. 回复 “把 Week1–4 细化命令和样板代码给我” —— 我马上把样板 repo / `fastapi-ping` starter 代码发给你。

---

你要是现在准备好了我就把 **Week1–Week4 的细化命令 + 一个最小 FastAPI + RAG starter repo 模板** 直接给你（包含 `requirements.txt`、`.vscode` 调试配置、Dockerfile、README）。选 “是，给我 Week1–4 模板” 或 直接说 “现在开始 Week1” 都可以 —— 我立刻发你可运行的样板代码和精确命令。
