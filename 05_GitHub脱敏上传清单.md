# GitHub 脱敏上传清单 Draft

这份清单用于我在 WorkBuddy 测试无误后，把核心内容脱敏上传 GitHub 前逐项检查。

## A. 绝对不能上传

- [ ] 真实发票 PDF、OFD、图片、ZIP。
- [ ] 真实行程单、地图截图、付款截图、聊天截图。
- [ ] 真实客户名称。
- [ ] 真实项目名称和项目编号。
- [ ] 真实员工姓名、员工号、手机号、邮箱。
- [ ] 真实金额、发票号码、纳税人识别号、银行账号。
- [ ] 真实历史 output 目录中的 Excel、PDF、Markdown 报告。
- [ ] 我的本机绝对路径，例如 `/Users/HMH028/...`。
- [ ] 公司内部 OA、财务制度、模板原件中不适合公开的字段。

## B. 可以上传的内容

- [ ] 轻量版 WorkBuddy Skill。
- [ ] README 和目录规范。
- [ ] 从零配置清单。
- [ ] 测试话术。
- [ ] 空目录结构说明。
- [ ] 匿名配置模板。
- [ ] 匿名测试样例。
- [ ] 不含真实业务数据的脚本框架。
- [ ] 明确标注 Draft、Human Review Required、禁止自动提交的安全边界。

## C. 路径脱敏规则

我应把：

`/Users/HMH028/Documents/报销管理/hongda_reimbursement_runtime`

替换为：

`~/Documents/报销管理/hongda_reimbursement_runtime`

或：

`<RUNTIME_ROOT>`

文档中可以保留“我的本机测试路径曾用于本地验证”的说明，但 GitHub 公开版不应保留真实用户名和完整路径。

## D. 配置脱敏规则

- [ ] `employee_mapping.json` 改为匿名员工，例如 `E001 / 张三示例`。
- [ ] 项目配置改为 `示例客户/示例项目`。
- [ ] 金额改为小额示例或 0。
- [ ] 发票文件名改为虚构名称。
- [ ] 删除所有真实覆盖规则，例如具体项目确认覆盖 JSON。
- [ ] 保留字段结构，删除真实值。

## E. 测试数据建议

如果需要上传样例，我只上传：

```text
sample_runtime/
  inbox/
    202606_示例项目_HDC_SAMPLE_001/
      发票/
        sample_invoice_placeholder.pdf
      附件/
      行程单/
      说明/
  output/
    .gitkeep
  config/
    employee_mapping.sample.json
    expense_category_mapping.sample.json
    reimbursement_runtime_config.sample.json
  scripts/
```

样例文件可以是空白占位文件或自造测试文件，不使用真实票据。

## F. 上传前最后确认

- [ ] 我已经全文搜索 `HMH028`。
- [ ] 我已经全文搜索 `/Users/`。
- [ ] 我已经全文搜索真实客户名。
- [ ] 我已经全文搜索真实员工姓名。
- [ ] 我已经删除历史 output 真实结果。
- [ ] 我已经确认 GitHub 版本不能直接处理真实票据，必须由使用者本地配置 runtime。

## G. 推荐 GitHub 说明口径

这个仓库只提供本地报销材料预处理的轻量入口和目录规范，不包含真实发票、真实客户、真实员工、真实报销模板或最终财务审核逻辑。所有输出均为 Draft，正式报销仍需人工复核并遵守公司流程。
