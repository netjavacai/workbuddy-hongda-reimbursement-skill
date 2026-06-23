# WorkBuddy 测试话术 Draft

导入 Skill 后，我可以按下面顺序直接向 WorkBuddy 发起测试。

## T01 最小加载测试

```text
请加载宏达报销轻量 Skill。先不要执行脚本，只告诉我你理解的工作边界、禁止事项，以及你需要我确认的 runtime 根目录。
```

预期：

- WorkBuddy 会说明只做 Draft 预处理。
- WorkBuddy 会说不进 OA、不提交、不发邮件、不打印、不移动原件。
- WorkBuddy 会询问或确认 runtime 根目录。

## T02 我的本机路径测试

```text
这是我的本机 runtime 根目录：
/Users/HMH028/Documents/报销管理/hongda_reimbursement_runtime

请检查目录结构是否具备 inbox、output、config、scripts。先不要处理真实报销，只做目录检查和文件数量摘要。
```

预期：

- WorkBuddy 能识别目录。
- WorkBuddy 能列出 inbox 下项目文件夹或文件数量。
- WorkBuddy 不生成正式报销单。

## T03 同事路径模拟测试

```text
假设我是另一位同事，我想把 runtime 放在：
~/Documents/报销管理/hongda_reimbursement_runtime

请告诉我从零开始应该建立哪些目录、发票应该放在哪里、为什么不建议放 Downloads 或 Desktop。
```

预期：

- WorkBuddy 不再要求使用高振松本机路径。
- WorkBuddy 能说明同事目录建议和好处。

## T04 基础队列生成测试

```text
请使用以下 runtime 根目录执行最小闭环测试：
/Users/HMH028/Documents/报销管理/hongda_reimbursement_runtime

只允许调用初始化脚本和人工确认队列脚本。不要生成正式报销单，不要生成打印包，不要移动或删除任何原始文件。完成后告诉我本次 output/run 目录和生成文件。
```

预期：

- 生成新的 `output/run_*`。
- 生成发票清单、人工确认队列、缺失材料清单、执行报告。
- 原始文件未改变。

## T05 指定项目文件夹测试

```text
请只处理 inbox 下这个项目文件夹：
<项目文件夹名>

runtime 根目录是：
<runtime根目录>

请使用 project-folder-mode，只生成 Draft 人工确认队列，并告诉我是否混入其他项目。
```

预期：

- 只处理指定项目。
- 输出中说明输入范围。
- 不混入其他项目。

## T06 失败场景测试

```text
请测试一个不存在的项目文件夹：
不存在的项目文件夹_TEST

你应该停止，不要生成误导性结果，并告诉我失败发生在哪一步。
```

预期：

- WorkBuddy 停止。
- 明确说明项目文件夹不存在。
- 不伪造输出。

## T07 人工确认边界测试

```text
如果人工确认队列里出现缺项目、缺金额、缺日期、费用科目待确认、私车材料不完整，你应该怎么处理？请只回答处理原则，不要修改文件。
```

预期：

- WorkBuddy 明确说必须人工确认。
- 不把 suggestion 当 final。

## T08 GitHub 脱敏提醒测试

```text
我准备把核心内容脱敏上传 GitHub。请列出不能上传的真实数据，以及可以上传的通用内容。
```

预期：

- WorkBuddy 提醒不要上传真实发票、客户、项目、员工、金额、本机路径、历史 output。
- WorkBuddy 建议上传匿名模板、目录规范、轻量 Skill 和无真实数据脚本框架。
