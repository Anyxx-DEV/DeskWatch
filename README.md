<h1 align="center">🖥️ DeskWatch 🖥️</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Language-Python-blue?style=for-the-badge&logo=python" />
  <img src="https://img.shields.io/badge/Platform-Windows-0078D6?style=for-the-badge&logo=windows" />
  <img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge" />
</p>

<p align="center">
  <em>See who is connecting to your machine over AnyDesk.</em>
</p>

---

## 🚩 Overview

**DeskWatch** is a Python tool that monitors active **AnyDesk connections** on your own system and prints the **remote IP address and port** in a **gradient CLI**. A **persistent blacklist** keeps each address from being reported twice, and the console can be made transparent.

It is meant for the case where someone opens a remote session to your machine and you want to know where that session originates.

> [!CAUTION]
> DeskWatch monitors **your own machine**. Do not deploy it on systems you do not own, and do not use the addresses it reports for access attempts, retaliation, or any other unauthorized action.

---

## ✨ Features

* 👀 **Monitor AnyDesk connections** — detects running AnyDesk processes and reads their active connections.
* 🧠 **Persistent blacklist** — every IP is reported once, no repeats.
* 🌈 **Gradient CLI** — color gradients and scrolling output via `rgbprint`.
* 🖥️ **Transparent console** — adjustable transparency for a cleaner look.
* ⚡ **Real time** — polls continuously and reports new peers immediately.

---

## 🧭 How it works

1. Start the tool (`python main.py`).
2. DeskWatch looks for **AnyDesk processes** on the system.
3. Once AnyDesk is running, its **active remote connections** are read and displayed:
   * Remote IP
   * Port
4. **Link-local addresses** (`169.254.x.x`), `127.0.0.1`, and ports 80 and 443 are ignored.
5. Addresses that were already reported go on the **blacklist** automatically.
6. Output is rendered with **color gradients** and scrolling effects.

---

## 🧰 Requirements

* 🐍 Python **3.9+**
* 📦 Dependencies:

    ```bash
    pip install rgbprint psutil colorama
    ```

* 🖥️ Windows (for console transparency and connection lookup)

---

## ▶️ Usage

```bash
python main.py
```

---

## 📝 Project structure

```/
├─ main.py ➔ Main logic and CLI
├─ LICENSE ➔ License file
└─ README.md ➔ This file
```

---

## ⚙️ Technical details

* `psutil` detects running AnyDesk processes and reads their TCP connections.
* Sockets in **LISTEN** state and link-local addresses are filtered out.
* Console transparency is set through `ctypes` and the Windows API.
* Gradients and scrolling effects come from `rgbprint`.
* The persistent blacklist ensures each IP is printed only once.

---

## ⚖️ License

Released under the **MIT License**. See `LICENSE` for details.

DeskWatch is based on an existing MIT-licensed project; the original copyright notice is retained as the license requires.

---

## 🚨 Disclaimer

DeskWatch is for **monitoring your own system**. Do not use it to intrude on other systems or to carry out unauthorized actions.
This project is **not affiliated with, endorsed by, or sponsored by AnyDesk**.
