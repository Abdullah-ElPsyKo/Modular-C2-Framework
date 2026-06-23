# Modular C2 Framework & Post-Exploitation Agent

## Operational Security & Ethics Notice
This framework was developed exclusively for research, defensive engineering, and educational purposes within an isolated lab environment. All testing and validation were executed against authorized, self-hosted infrastructure to analyze command-and-control (C2) transport mechanics and endpoint artifact generation.

## Project Overview
This project features a modular post-exploitation agent written in Python that leverages a dynamic runtime architecture. The framework is designed to decouple the core execution engine from individual functional tasks, allowing components to be loaded, updated, or toggled via centralized configurations without altering the primary codebase.

---

## Technical Architecture

### Core Engine (`main.py`)
* **Dynamic Module Loading:** Implements runtime importing of functional modules based on orchestration rules.
* **Asynchronous Execution:** Handles scheduling, module polling loops, and state persistence.
* **C2 Transport Layer:** Integrates natively with the GitHub API, utilizing a secure private repository as an out-of-band communication channel for receiving configurations and exfiltrating telemetry data.

### Configuration Specification (`config.json`)
The infrastructure configuration dictates agent behavior dynamically through the following parameters:
* `poll_interval`: Controls the operational beaconing frequency (default: 60 seconds).
* `modules`: Dictates which tactical modules are actively compiled and executed at runtime.

---

## Subsystem Capabilities

### 1. Network Enumeration & Intelligence (Portscanner)
Engineered around Python's `threading` primitives to ensure high-throughput network analysis while minimizing race conditions.
* **Target Scanning:** Scans arbitrary IP address ranges or user-defined port lists.
* **Service Mapping:** Targeted validation of common service ports (`22`, `80`, `443`).
* **Subnet Discovery:** Discovers active hosts within a specified network block.
* **Passive OS Fingerprinting:** Infers remote operating system types using ICMP Time-to-Live (TTL) boundary analysis.
* **DNS Resolution:** Performs reverse lookups to extract hostnames and domain details.

### 2. Endpoint Reconnaissance (System Enumeration)
Provides deep inspection of host state and active configuration boundaries.
* **Process Auditing:** Enumerates all active execution processes running on the host.
* **Network State:** Maps current network configurations (IP, gateway, subnet mask) and live socket connections.
* **Identity Management:** Identifies the current execution context and lists local system users.
* **Hardware & Storage:** Extracts physical volume partitioning, disk utilization metrics, and system hardware specifications.
* **Wireless Reconnaissance:** Lists available local IEEE 802.11 wireless networks.

### 3. Remote Access (Backdoor)
* **Reverse Shell Transport:** Establishes TCP socket connections back to a designated listening listener.
* **Command Interactivity:** Receives, parses, and executes arbitrary shell instructions from the management infrastructure, returning raw stdout/stderr output.

---

## Lab Validation & Engineering Reflections

### Performance Verification
Testing was conducted within an isolated virtual infrastructure to monitor execution stability and artifact footprint:
* **Transport Reliability:** The GitHub API beaconing loop functioned with zero dropped telemetry sets.
* **Concurrency Optimization:** Early development revealed minor synchronization anomalies and race conditions during high-volume port scanning. These were mitigated by implementing global thread locks (`Threading.Lock`) and optimizing socket timeout handling.

### Key Takeaways
* **Extensible Software Design:** Developing a plug-and-play module loader provided deep insight into robust architectural patterns applicable to scalable enterprise software.
* **Multithreaded Performance:** Handling concurrent socket connections highlighted the critical need for deterministic resource management and thread synchronization in systems-level tools.

---

## Deliverables & Artifacts

* **Source Code Architecture:** Complete core engine (`main.py`), modular configuration mapping (`config.json`), and the tactical module suite.
* **Version Control Management:** Maintained within a restricted GitHub repository structure to isolate testing telemetry and code assets.
* **Operational Video Demonstration:** A comprehensive execution walkthrough showing the C2 infrastructure interacting with the deployment agent.
  * **Link:** [https://youtu.be/RH3AChMOpz4](https://youtu.be/RH3AChMOpz4)
