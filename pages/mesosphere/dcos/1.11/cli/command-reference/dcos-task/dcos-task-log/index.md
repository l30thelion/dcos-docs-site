---
layout: layout.pug
navigationTitle:  dcos task log
title: dcos task log
menuWeight: 1
excerpt: Displaying the task log

enterprise: false
---


# Description
The `dcos task log` command displays the task log.

# Usage

```bash
dcos task log <task> <file> [OPTION]
```

# Options

| Name, shorthand | Default | Description |
|---------|-------------|-------------|
| `--completed`   |             | Displays completed and in-progress tasks. |
| `--follow`   |             |  Dynamically update the log. |
| `--lines=N`   |     10      |  Displays the last N lines. |

# Positional arguments

| Name, shorthand | Default | Description |
|---------|-------------|-------------|
| `<task>`   |             |  A full task ID, a partial task ID, or a regular expression. |
| `<file>`   |  `stdout`  |  Specify the sandbox file to Displays. |

The log file parameters should be paths relative to the Mesos sandbox. For example:
```
dcos task log [mesosID] /mnt/mesos/sandbox/exporter.log
```
will return an error message. Instead, use this format:

```
dcos task log [mesosID] exporter.log
```

# Parent command

| Command | Description |
|---------|-------------|
| [dcos task](/mesosphere/dcos/1.11/cli/command-reference/dcos-task/)   | Manage DC/OS tasks. |

# Examples

For an example, see the [documentation](/mesosphere/dcos/1.11/monitoring/logging/).
