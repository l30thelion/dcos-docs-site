---
layout: layout.pug
navigationTitle:  dcos security org groups delete
title: dcos security org groups delete
menuWeight: 140
excerpt: 删除组
render: mustache
model: /mesosphere/dcos/1.13/data.yml
enterprise: true
---
# 说明

`dcos security org groups delete` 命令允许您删除组。

# 使用

```
dcos security org groups delete [OPTIONS] GID
```

# 选项

| 名称 | 说明 |
|---------|-------------|
| `-h`, `--help`| 显示此消息并退出。|

## 位置自变量

| 名称 | 说明 |
|---------|-------------|
| `GID` | 组 ID。（必填）|

# 父命令

| 命令 | 说明 |
|---------|-------------|
| [dcos security org groups](/mesosphere/dcos/cn/1.13/cli/command-reference/dcos-security/dcos-security-org/dcos-security-org-groups/) | 管理用户组和组成员。 |
