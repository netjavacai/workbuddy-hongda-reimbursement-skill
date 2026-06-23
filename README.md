# 宏达报销 WorkBuddy 轻量技能包 v0.2 Draft

这是我准备导入 WorkBuddy 测试的轻量技能包。它不是完整 Codex Skill 的复制版，而是一个“同事轻量入口”：让 WorkBuddy 负责识别目录、调用本地脚本、输出结果摘要；复杂规则继续放在 runtime 的 `config/` 和 `scripts/` 中。

## 这个包解决什么问题

上一版把我的本地测试目录：

`/Users/HMH028/Documents/报销管理/hongda_reimbursement_runtime`

写得过于固定。这个路径只适合我本机测试，不适合同事直接照抄。v0.2 已改为：

- 我的电脑：保留该路径作为测试示例。
- 同事电脑：先确认他们自己的 runtime 根目录。
- README 明确建议同事把发票放在哪里，以及这样做的好处。

## 包内文件

- `SKILL.md`
  可直接导入 WorkBuddy 的主 Skill（含 YAML frontmatter，符合导入规范）。

- `02_从零开始配置清单.md`  
  从一台新电脑开始配置 runtime、放票、测试、验收的检查清单。

- `03_同事发票目录建议.md`  
  给同事看的放票目录规范和好处说明。

- `04_WorkBuddy测试话术.md`  
  导入技能后可直接复制给 WorkBuddy 的测试指令。

- `05_GitHub脱敏上传清单.md`  
  测试无误后，整理开源/共享版本前使用的脱敏检查清单。

- `README.md`  
  本说明文件。

## 同事发票建议放在哪里

推荐每位同事使用独立 runtime 目录：

`~/Documents/报销管理/hongda_reimbursement_runtime`

发票和材料放在：

`~/Documents/报销管理/hongda_reimbursement_runtime/inbox/`

推荐项目结构：

```text
hongda_reimbursement_runtime/
  inbox/
    202606_项目名称_项目编号/
      发票/
      附件/
      行程单/
      说明/
  output/
  config/
  scripts/
```

## 这样放的好处

- 路径稳定：Documents 比 Downloads、Desktop、聊天缓存更不容易被清理。
- 权限清晰：WorkBuddy 更容易获得读取和写入权限。
- 项目隔离：每个项目单独文件夹，减少混票和错归项目。
- 便于复核：人工打开 output/run 目录即可看到本次生成结果。
- 便于备份：整个 `报销管理` 文件夹可以同步或备份。
- 便于推广：每位同事一个独立 runtime，互不影响。
- 便于脱敏：后续上传 GitHub 时，只保留目录规范、脚本框架和匿名示例，不上传真实发票、真实项目、真实员工数据。

## 不建议放在哪里

- 不建议放在 `Downloads/`：容易被清理，文件来源混乱。
- 不建议放在 `Desktop/`：容易误拖、误删、被临时文件污染。
- 不建议放在微信、企业微信、邮箱附件缓存目录：路径复杂，权限和文件生命周期不稳定。
- 不建议多人共用同一个 `inbox/`：容易混淆责任和项目归属。
- 不建议把真实发票放进将来准备上传 GitHub 的目录。

## WorkBuddy 的边界

WorkBuddy 只做：

- 检查目录。
- 调用 runtime 脚本。
- 生成 Draft 清单。
- 汇总输出结果。
- 提醒人工确认。

WorkBuddy 不做：

- 不给最终报销结论。
- 不进入 OA。
- 不提交报销。
- 不发送邮件。
- 不自动打印。
- 不移动、删除、改名原始票据。
- 不覆盖报销模板。

## 我的测试顺序

1. 导入 `SKILL.md`（拖入 WorkBuddy「导入技能」对话框或上传 zip）。
2. 按 `02_从零开始配置清单.md` 检查 runtime。
3. 放入少量测试发票。
4. 使用 `04_WorkBuddy测试话术.md` 做 T01-T06 最小闭环。
5. 确认 WorkBuddy 能输出新 `output/run_*` 目录。
6. 再测试真实项目文件夹。
7. 无误后，准备脱敏版上传 GitHub。

## GitHub 脱敏提醒

后续上传 GitHub 前，我需要删除或替换：

- 真实发票、行程单、截图、ZIP、PDF、OFD。
- 真实员工姓名、员工号、客户名、项目编号、项目金额。
- 本机绝对路径。
- 历史 output 中含真实业务信息的 Excel、PDF、Markdown。

建议上传：

- 轻量 Skill。
- README。
- 空目录结构说明。
- 匿名配置模板。
- 匿名测试样例。
- 不含真实数据的脚本框架。

## 当前建议结论

我不再把完整 Codex Skill 直接交给 WorkBuddy。WorkBuddy 先定位为“同事轻量入口”，用于节省 Codex 流量；Codex 保留为高级调试、规则维护、复杂异常处理和 GitHub 脱敏整理环境。
