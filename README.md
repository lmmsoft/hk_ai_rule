# Shadowrocket 香港 AI 白名单规则

## 背景
- 场景：在香港日常访问 Google 等海外网站无需代理，唯独海外大模型（OpenAI/ChatGPT、Claude、Gemini、Copilot等）限制香港用户，需要代理才能正常使用。
- 问题：网上常见规则多为**内地场景**，默认将大量海外站点走代理，**浪费流量**且**影响速度**，不适合香港用户。
- 目标：做一个“AI 代理白名单 + 其余直连”的规则文件，专门为香港环境优化。

## 文件说明
- 规则文件：`ai_proxy.conf`
- 策略：
  - 仅 AI 相关域名/IP 走 `PROXY`，按服务分组，提高可读性。
  - 其他域名直连；`FINAL,DIRECT`，避免非 AI 流量走代理。
- 参考项目列表：
  - ACL4SSR：
    - https://github.com/ACL4SSR/ACL4SSR/blob/master/Clash/Ruleset/OpenAi.list  
    - https://github.com/ACL4SSR/ACL4SSR/blob/master/Clash/Ruleset/AI.list
  - blackmatrix7：Shadowrocket/OpenAI 等规则  
    - https://github.com/blackmatrix7/ios_rule_script/tree/master/rule/Shadowrocket
    - https://github.com/blackmatrix7/ios_rule_script/tree/master/rule/Shadowrocket/OpenAI
    - https://github.com/blackmatrix7/ios_rule_script/blob/master/rule/Shadowrocket/Gemini/Gemini.list

## 使用方式（简）
1) 将 `ai_proxy.conf` 导入 Shadowrocket。
2) 测试规则是否符合预期
3) 启用后，AI 域名自动走代理，其余流量直连；如有遗漏可在对应分组追加条目。
