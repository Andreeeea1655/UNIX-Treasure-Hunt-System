# 🗺️ UNIX Treasure Hunt System

A multi-process treasure hunt management system written in C on Linux, using inter-process communication via pipes and UNIX signals.

## Overview

The system is split into three components:

- **`treasure_hub.c`** — the main hub that reads user commands from stdin, manages a background monitor process, and delegates work via signals and pipes.
- **`treasure_manager.c`** — an external executable launched via `execl` to list hunts, list treasures, or view a specific treasure.
- **`calculate_score.c`** — an external executable that computes scores for all hunts and returns results through a pipe.

## Features

- Background monitor process controlled with `start monitor` / `stop monitor`
- Inter-process communication using:
  - **Pipes** — for passing output from child processes back to the hub
  - **SIGUSR1** — triggers command execution in the monitor
  - **SIGUSR2** — acknowledgment signal
  - **SIGTERM** — gracefully stops the monitor
- Commands passed to the monitor via a `cmd.txt` file
- File system operations handled through the `treasure_manager` executable

## Commands

| Command | Description |
|---|---|
| `start monitor` | Starts the background monitor process |
| `stop monitor` | Sends SIGTERM to stop the monitor |
| `exit monitor` | Stops monitor (if running) and exits |
| `list hunts` | Lists all available treasure hunts |
| `list treasures <huntID>` | Lists treasures in a specific hunt |
| `view treasure <huntID> <treasureID>` | Displays details of a specific treasure |
| `calculate score` | Computes and displays scores for all hunts |

## Build & Run

```bash
gcc treasure_hub.c -o treasure_hub
gcc treasure_manager.c -o treasure_manager
gcc calculate_score.c -o calculate_score

./treasure_hub
```

## Technologies

- C (POSIX)
- `fork()`, `execl()`, `waitpid()`
- Pipes (`pipe()`, `dup2()`)
- Signal handling (`sigaction`, SIGUSR1, SIGUSR2, SIGTERM)
- File I/O (`open`, `read`, `write`)
