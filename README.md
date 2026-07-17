# Modular C2 Framework

> A modular command-and-control framework built in Python for security research, defensive engineering, and software architecture exploration.

## Disclaimer

This project was developed exclusively for educational purposes and authorized security research within an isolated laboratory environment. It demonstrates command-and-control architecture, modular software design, and remote task orchestration. It is **not intended for unauthorized use**.

---

## Overview

Modular C2 Framework is a Python-based command-and-control framework designed around a plugin-oriented architecture. Rather than embedding all functionality into a single executable, the agent dynamically loads and executes independent modules based on a central configuration.

The primary goal of this project is to explore scalable software architecture, runtime extensibility, asynchronous execution, and secure communication patterns commonly found in modern distributed systems.

---

## Features

- Dynamic runtime module loading
- Configuration-driven task execution
- GitHub API based communication channel
- Modular plugin architecture
- Multi-threaded network operations
- Process and system enumeration
- Network reconnaissance utilities
- Remote command execution (lab environment)

---

## Architecture

```
                Operator
                    │
                    ▼
        Private GitHub Repository
                    │
     Configuration & Tasking
                    │
                    ▼
          Python Agent (main.py)
                    │
        ┌───────────┼───────────┐
        │           │           │
        ▼           ▼           ▼
   Port Scanner  System Info  Remote Shell
```

The core engine remains independent from operational modules. New functionality can be added simply by implementing a module and updating the configuration, without modifying the agent itself.

---

## Components

### Core Engine

Responsible for:

- Agent lifecycle management
- Configuration parsing
- Dynamic module loading
- Task scheduling
- Communication with the C2 infrastructure

---

### Configuration

The framework behavior is controlled through `config.json`.

Example options include:

- Poll interval
- Enabled modules
- Runtime configuration
- Communication settings

---

### Network Enumeration

Provides network reconnaissance capabilities including:

- Port scanning
- Host discovery
- Service identification
- Reverse DNS lookups
- Basic operating system fingerprinting using TTL analysis

---

### System Enumeration

Collects host information such as:

- Running processes
- Local users
- Network configuration
- Active connections
- Disk information
- Hardware details
- Wireless networks

---

### Remote Command Execution

Implements a controlled remote command interface for laboratory testing, allowing commands to be executed and results returned through the communication channel.

---

## Technologies

- Python
- GitHub REST API
- JSON
- Threading
- Socket Programming
- Modular Software Architecture

---

## What I Learned

Building this project provided practical experience with:

- Designing extensible software architectures
- Dynamic module loading
- Multithreaded programming
- Network programming
- Concurrent resource management
- Remote communication patterns
- Configuration-driven applications

---

## Repository Structure

```
Modular-C2-Framework/
│
├── main.py
├── config.json
├── modules/
│   ├── portscanner.py
│   ├── system_enum.py
│   └── ...
├── README.md
└── ...
```

---

## Future Improvements

- Encrypted transport layer
- Authenticated tasking
- Cross-platform agent support
- Improved plugin API
- Event-driven architecture
- Unit and integration tests

---

## License

This project is intended for educational use, defensive security research, and software engineering study within authorized environments.
