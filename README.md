# 淘宝任务 Mobile Runner Starter

这是一个用于制作手机端本地任务入口的项目。快捷指令内直接固化任务深链，只使用本地配置生成，不拉取远程 JSON 或外部脚本。

## 目录

- `data/task-config.json`: 芭芭农场任务配置来源。
- `data/farm-bargain-task-config.json`: 农场砍价任务配置来源。
- `data/hhle-task-config.json`: 红包花花乐任务配置来源。
- `data/jump-618-task-config.json`: 淘宝618跳一跳任务配置来源。
- `data/kkl-task-config.json`: 红包砍砍乐任务配置来源。
- `data/tjb-task-config.json`: 淘金币任务配置来源。
- `scripts/build_shortcut.js`: 根据本地配置将任务深链直接嵌入快捷指令 XML。
- `shortcuts/`: 生成的快捷指令 XML 和后续签名产物目录。

## 目标

生成手机端快捷指令，用于从内置列表中按顺序打开任务深链。当前快捷指令：

- 从第一个深链开始，按列表顺序逐个打开。
- 每打开一个深链后按配置等待，再继续下一个。
- 所有深链都会被依次打开一遍。
- 不包含“获取 URL 内容”动作，不请求远程 JSON。
- 远程配置即使变更或不可用，也不会改变已经导入手机的快捷指令行为。

## 使用

重新生成芭芭农场本地固化 XML：

```bash
node scripts/build_shortcut.js
```

重新生成农场砍价本地固化 XML：

```bash
node scripts/build_shortcut.js farm-bargain
```

重新生成红包砍砍乐本地固化 XML：

```bash
node scripts/build_shortcut.js kkl
```

重新生成红包花花乐本地固化 XML：

```bash
node scripts/build_shortcut.js hhle
```

重新生成淘宝618跳一跳本地固化 XML：

```bash
node scripts/build_shortcut.js jump-618
```

重新生成淘金币任务本地固化 XML：

```bash
node scripts/build_shortcut.js tjb
```

全部重新生成：

```bash
node scripts/build_shortcut.js all
```

生成后文件位于：

```text
shortcuts/baba-farm-mobile-runner.xml
shortcuts/farm-bargain-mobile-runner.xml
shortcuts/hhle-mobile-runner.xml
shortcuts/jump-618-mobile-runner.xml
shortcuts/kkl-mobile-runner.xml
shortcuts/tjb-mobile-runner.xml
```

校验并签名后即可导入手机。每次希望更新任务列表时，需要重新生成并重新导入新版快捷指令；手机运行时不会在线更新配置。

## 隐私

不要在配置、脚本、README 或提交记录中写入个人账号、Cookie、Bark key、手机号、邮箱或其他凭据。
