现实判断：明天完成一个真正的"企业级 E2E demo"不现实。 这类项目正常需要3-5天。但你可以在今天/明天24小时内做出一个可演示的MVP(数据层简化+核心链路打通)。下面是精简方案。
时间预算（关键）
┌─────────────────┬──────────┬─────────────────────────┐
│ 阶段             │ 耗时      │ 产出                     │
├─────────────────┼──────────┼─────────────────────────┤
│ 数据层搭建        │ 2-3h     │ Salesforce Dev Org + 假数据│
│ Agent层搭建       │ 3-4h     │ 开源Agent + MCP连接       │
│ Skills/Prompt设计 │ 2-3h     │ 3个场景的预设prompt       │
│ 表现层(Dashboard) │ 3-4h     │ Streamlit/简单前端        │
│ 联调+录demo       │ 2h       │ 可演示视频/live demo      │
└─────────────────┴──────────┴─────────────────────────┘
总计：12-16小时（建议熬一个通宵+次日上午冲刺）
架构设计
┌──────────────────────────────────────────────────┐
│  表现层 (Streamlit / Next.js)                      │
│  - Sales Dashboard / Marketing Dashboard           │
└─────────────────────┬──────────────────────────────┘
                       │
┌──────────────────────▼──────────────────────────────┐
│  Agent层 (开源Agent Framework)                       │
│  - 预设Prompts + Skills库                            │
│  - 场景路由 (销售/市场/报表)                          │
└─────────────────────┬──────────────────────────────┘
                       │ MCP Protocol
┌──────────────────────▼──────────────────────────────┐
│  数据/知识层                                         │
│  - Salesforce Dev Org (DX MCP Server)                │
│  - HubSpot Free CRM (REST API)                       │
│  - 简易RAG (Chroma + 几份PDF当"企业知识库")            │
└────────────────────────────────────────────────────┘
工具选型（直接结论）
层级选择理由数据-CRMSalesforce Developer Edition（永久免费）自带MCP支持(salesforcecli/mcp，本地stdio运行)，预置示例数据数据-MarketingHubSpot Free CRM公开REST API简单，无需MCP也能快速接知识库/RAGChroma (本地向量库) + 3-5份PDF1小时内可搭好，足够撑场景Agent框架不推荐OpenManus（不够稳定）→ 推荐 LangGraph + MCP adapters最可控，文档全，官方支持MCP client备选(更快但less控制)Dify (开源, 自带可视化Agent编排+MCP插件)如果你想省编码时间，用Dify拖拽更快表现层Streamlit1人一天内能出像样dashboard，Python生态打通容易
今晚执行顺序（按优先级）

先打通一条完整链路（Salesforce → Agent → Dashboard），不要并行做多个数据源
Salesforce Dev Org 注册 → 装 salesforcecli/mcp → 本地跑通 describe_sobject/查询
LangGraph 接 MCP client，写1个销售场景的预设prompt（如"生成本周Pipeline健康报表"）
Streamlit 渲染Agent输出成图表
HubSpot和RAG作为"加分项"，时间不够就砍掉，先保证一条线能跑通demo

关键风险提示

Salesforce Hosted MCP（GA版）需要Enterprise Edition以上，免费Dev Edition只能用本地DX MCP Server（够用，但需要本地装CLI，不是托管服务）
OpenManus 目前生态不够成熟，企业demo慎用，容易现场翻车
不要同时折腾3个数据源+自建RAG+开源Agent——砍范围比赶进度更重要

需要我直接帮你写 Salesforce DX MCP Server 安装命令 + LangGraph 接入代码骨架吗？






För att enkelt logga in senare, spara denna URL:
https://vltaaitechonologyab.my.salesforce.com
  
Användarnamn:
cppemu_yj0sif@gmail.com
Lösenord:
[Stockholm11!]  




2026-07-01 00:02:58.497 Uvicorn server started on 0.0.0.0:8501

  You can now view your Streamlit app in your browser.

  Local URL: http://localhost:8501
  Network URL: http://192.168.86.149:8501



Hubspot
login through google: cppemu@gmail.com 






