# Jenkins CI Pipeline with Docker-based Build Agent

## Overview

This project demonstrates a Jenkins CI pipeline where application builds are executed inside Docker containers. The pipeline is designed to keep the Jenkins server lightweight while ensuring consistent and reproducible build environments.

The setup reflects modern CI practices used in enterprise environments, where Jenkins acts as an orchestrator and delegates build execution to containerized agents.

---

## Architecture
<img width="1024" height="1024" alt="maven conatiner" src="https://github.com/user-attachments/assets/85e928ff-c408-4cd1-905c-78fb6c7f6160" />


---

## Key Design Decisions

### 1. Docker-based Build Isolation

Build tools such as Maven and Java are not installed directly on the Jenkins server. Instead, a Docker image containing all required dependencies is used to execute the build.

**Benefits:**

* Eliminates dependency conflicts
* Ensures consistent builds across environments
* Keeps Jenkins server lightweight

---

### 2. Pipeline as Code

The entire CI workflow is defined using a Jenkinsfile stored in the repository.

**Benefits:**

* Version-controlled CI configuration
* Easier reviews and updates
* Consistent pipeline across environments

---

### 3. On-Demand Resource Usage

Docker containers are created only for the duration of the build and destroyed afterward. This approach aligns with cost-efficient CI practices, especially in constrained environments.

---

## Jenkinsfile Summary

* Uses a Docker agent with a Maven + Java image
* Executes `mvn clean package` inside the container
* Provides clear success and failure status handling

---

## Use Case

This approach is suitable for:

* Java-based CI pipelines
* Teams adopting containerized build agents
* Environments where Jenkins server resources must be conserved

---

## Notes on Resource-Constrained Environments

In low-resource environments (e.g., free-tier cloud instances), Docker-based builds may require dedicated agents or higher memory allocation. In production setups, Jenkins agents are typically provisioned separately to handle build workloads efficiently.

---

## Conclusion

This project reflects a modern CI pattern where Jenkins focuses on orchestration while Docker ensures clean, repeatable build environments. The same pattern is widely adopted in scalable and production-grade CI/CD systems.
