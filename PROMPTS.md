# 四条智能体提示词：从总结经验到 SkillPay 收费

> 配套《Skill 发布完全指南：从创建标准 Skill 到 SkillPay 收费》一文（公众号 smiler488）。
> 尖括号处换成你的内容，按顺序发给智能体即可走完整条链路。

## 提示词一：把经验总结成标准 Skill

````
把我的重复工作总结成一个标准 Skill。
我的工作是：<一句话描述>
要求：
1. 先向我提 3-5 个问题：做什么、什么时候触发、步骤、边界、出错怎么办；
2. 生成 SKILL.md：frontmatter 含 name 和 description（description 写触发场景，不写形容词），
   正文含「何时使用 / 工作流程 / 边界与注意」，脚本放 scripts/，资料放 references/；
3. 生成后本地装上自测：模拟相关和无关请求各一次，确认该触发时触发、流程跑得通。
````

## 提示词二：发布到 GitHub

````
把这个 Skill 发布到 GitHub：
1. 先检查包内无密钥（API Key、Token、.env），配好 .gitignore；
2. 写 README（是什么、怎么装、怎么用）和 LICENSE（MIT），git init 并提交；
3. 创建公开仓库 <用户名/仓库名>，推送 main 分支，打标签 v1.0.0；
4. 推送后把 README 里的每个链接都打开验证一遍。
````

## 提示词三：上架 SkillHub

````
根据 https://skillhub.cn/ai/release.md 把 <你的 Skill 文件夹> 发布到 SkillHub。
````

首次发布前先在 skillhub.cn 注册、实名、备好 API Token。发布规范原文见
https://skillhub.cn/ai/release.md ，CLI 手动流程见 https://skillhub.cn/tutorials 。

## 提示词四（个人版）：配置 SkillPay（支付宝 AI 按量付费）

前置：`npx -y @alipay/alipay-aipay@latest install`（支付宝官方集成 Skill）。

````
请加载 alipay-aipay，为本项目的业务 API 接入支付宝 AI 按量付费，并在沙箱环境中完成测试。
业务信息：
- 接口用途：<例如：生成图片、查询数据或调用模型>
- 请求方式及路径：<例如：POST /api/resource>
- 请求参数、请求体和必要请求头：<按实际接口填写>
- 单次价格：<0.01～50 元，最多两位小数>
要求：
1. 保留接口原有业务逻辑和成功响应。
2. 验证 402 账单、Payment-Proof 验证、资源交付、履约回执和同一订单重试。
3. 输出测试结果、代码变更、启动方式、环境变量模板，以及上线前需要替换的生产配置；不要求我提供生产私钥。
4. 本轮不发起真实付款；缺少信息时先向我确认。
````

（本提示词改编自支付宝官方集成流程：https://aipay.alipay.com/docs/ai-receive/MACHINE_PAY.html ）

## 提示词四（企业版）：把现有 Skill 改造成 Pay Skill（微信支付 Agent Pay）

前置：完成企业认证、绑定微信商户号，服务端已接入微信支付下单（详见 https://skillhub.cn/tutorials#agent-pay-onboard ）。

````
请检查当前项目是否已有业务 Skill。若已有，保留原有业务能力、触发条件和输出，为它接入
已经部署的收费接口；若没有，按下面的业务信息创建完整的 Pay Skill。
业务信息：
- Skill 名称：<小写英文名称>
- 能力与触发词：<填写>
- 请求方式及完整资源 URL：<填写>
- 请求参数、请求体和必要请求头：<按实际接口填写>
- 单次价格：<与支付平台登记一致>
- 成功响应及展示字段：<填写>
要求：
1. 按官方支付能力文档调用支付，不自行实现付款或签名；支付后复用同一订单，状态不明先查单。
2. 用模拟响应测试 402、支付处理中、成功、失败和同订单重试；再加载本地 Skill 验证触发与
   参数传递，停在付款确认前。
3. 提供安装、运行与打包说明；排除密钥、.env、状态文件和 node_modules。
4. 未经我确认不发起真实付款；缺少信息先向我确认。
````

（本提示词改编自 SkillHub 官方 Pay Skill 改造提示词模板：https://skillhub.cn/tutorials#agent-pay-onboard ）
