🧭 UNIX Treasure Hunt System

A modular UNIX-based system that simulates a treasure hunt game using command-line tools, inter-process communication, file management, and external program integration.
The project demonstrates core concepts of UNIX programming such as processes, signals, pipes, and file handling.

📌 Project Overview

The UNIX Treasure Hunt System is composed of multiple components that work together to simulate a structured treasure hunt workflow.

The system includes:

🗂️ File system-based treasure management
⚙️ Process control using signals
🔁 Inter-process communication (pipes)
🧮 External scoring computation module
📜 Logging and command tracking
🔗 Symbolic link/file-based navigation mechanics
🏗️ Architecture

The project is structured into multiple phases/modules:

1. treasure_manager

Handles:

Creation and storage of treasures
File-based persistence (binary/text depending on implementation)
Basic CRUD operations for treasures
Directory structure management
2. treasure_hub

Core orchestrator of the system:

Starts and manages the main monitor process
Handles signals (SIGUSR1, SIGUSR2, SIGTERM)
Communicates with subprocesses via pipes
Executes commands dynamically using execl
Coordinates the treasure hunt flow
3. calculate_score (external program)
Independent executable
Computes player score based on collected treasures
Used through process execution (fork + exec / pipes)
🔄 Communication Model

The system uses UNIX mechanisms such as:

Signals
Trigger actions like reading command files or terminating processes
Pipes
Send data between parent and child processes
Process execution
External tools executed via execl
⚙️ Technologies Used
C (POSIX UNIX programming)
Signals (signal.h)
Pipes (pipe())
Process control (fork(), exec(), wait())
File I/O (open, read, write)
UNIX filesystem utilities
Symbolic links (if applicable in your implementation)
🚀 How to Build
git clone https://github.com/Andreeeea1655/UNIX-Treasure-Hunt-System.git
cd UNIX-Treasure-Hunt-System
make
▶️ How to Run

Example usage (adjust based on your implementation):

./treasure_manager
./treasure_hub

Or start the hub with monitoring enabled:

./treasure_hub start monitor
📂 Project Structure
.
├── treasure_manager/
├── treasure_hub/
├── calculate_score/
├── include/
├── src/
├── logs/
└── Makefile
🧠 Learning Objectives

This project demonstrates:

UNIX process lifecycle management
Signal handling in C
Inter-process communication
Modular system design
External program integration
Low-level file system operations
📈 Features
Multi-process architecture
Event-driven command execution
Score computation via external module
Logging system for debugging and tracking
Extensible command system
