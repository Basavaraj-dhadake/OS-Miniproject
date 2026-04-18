# 🚀 OS Jackfruit - Lightweight Container Runtime

## 📌 Project Overview

This project implements a **lightweight container runtime system** in Linux using **namespaces** and a **kernel module** for memory monitoring and enforcement.

It simulates core concepts behind container technologies like Docker.

---

## ⚙️ Features

* Create isolated containers using Linux namespaces
* Run CPU, Memory, and I/O workloads
* Monitor memory usage using kernel module
* Enforce memory limits:

  * Soft Limit (warning)
  * Hard Limit (process termination)
* Container management commands:

  * start
  * stop
  * ps
  * logs

---

## 🧠 Technologies Used

* C Programming
* Linux System Calls
* Kernel Module Programming
* UNIX Domain Sockets (IPC)

---

## 📂 Project Structure

```
engine.c           → Container runtime engine
monitor.c          → Kernel module for memory monitoring
monitor_ioctl.h    → Interface between user space & kernel
cpu_hog.c          → CPU intensive workload
memory_hog.c       → Memory stress test
io_pulse.c         → I/O workload
Makefile           → Build instructions
```

---

## 🚀 How to Run

### 1. Build project

```
make
```

### 2. Load kernel module

```
sudo insmod monitor.ko
```

### 3. Start supervisor

```
sudo ./engine supervisor ./rootfs
```

### 4. Run container

```
sudo ./engine start alpha ./rootfs /bin/sh
```

---

## 🧪 Experiments

### CPU Test

```
sudo ./engine start cpu1 ./rootfs /cpu_hog
```

### Memory Test

```
sudo ./engine start mem1 ./rootfs /memory_hog
dmesg | tail
```

✔ Soft limit → Warning
✔ Hard limit → Process killed

---

## 📊 Sample Output

```
SOFT LIMIT container=mem1 ...
HARD LIMIT container=mem1 ...
```

---

## 🎯 Key Concepts

* **Namespaces** → Process isolation
* **RSS (Resident Set Size)** → Memory used in RAM
* **Kernel Module** → Enforces memory limits

---

## 🏁 Conclusion

This project demonstrates how container runtimes work internally and how kernel-level resource control can be implemented.

---

## 👨‍💻 Author

Basavaraj Dhadake
SRN:PES2UG24CS110

---
