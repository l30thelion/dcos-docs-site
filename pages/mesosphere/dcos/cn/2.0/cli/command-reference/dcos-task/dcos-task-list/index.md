---
layout: layout.pug
navigationTitle:  dcos task list
title: dcos task list
menuWeight: 2
excerpt: 列出群集内的任务
render: mustache
model: /mesosphere/dcos/2.0/data.yml
enterprise: false
---

# 说明

`dcos task list` 命令可列出群集中的 DC/OS 任务。

# 使用

```bash
dcos task list [OPTIONS]
```

# 选项

| 名称 | 说明 |
|---------|-------------|
| `-h`, `--help`  | 打印使用情况。|
| `--agent-id`  |    仅列出指定代理的任务。 |
| `--info` | 打印该子命令的简短描述。|
| `--version` | 打印版本信息。|

# 父命令

| 命令 | 说明 |
|---------|-------------|
| [dcos task](/mesosphere/dcos/cn/2.0/cli/command-reference/dcos-task/) | 管理 DC/OS 任务。|
