# 芭芭农场 Mobile Runner Starter

这是一个用于制作手机端本地任务入口的项目。快捷指令内直接固化任务深链，只使用本地配置生成，不拉取远程 JSON 或外部脚本。

## 目录

- `data/task-config.json`: 唯一任务配置来源，更新任务时只修改这里。
- `scripts/build_shortcut.js`: 根据本地配置将任务深链直接嵌入快捷指令 XML。
- `shortcuts/`: 生成的快捷指令 XML 和后续签名产物目录。

## 目标

生成一个手机端快捷指令，用于从内置列表中随机打开任务深链。当前快捷指令：

- 随机打开一个已经固化在快捷指令里的任务深链。
- 不包含“获取 URL 内容”动作，不请求 `bbnc.json`。
- 远程配置即使变更或不可用，也不会改变已经导入手机的快捷指令行为。

## 使用

修改 `data/task-config.json` 后，重新生成本地固化 XML：

```bash
node scripts/build_shortcut.js
```

生成后文件位于：

```text
shortcuts/baba-farm-mobile-runner.xml
```

校验并签名后即可导入手机。每次希望更新任务列表时，需要重新生成并重新导入新版快捷指令；手机运行时不会在线更新配置。

## 隐私

不要在配置、脚本、README 或提交记录中写入个人账号、Cookie、Bark key、手机号、邮箱或其他凭据。
