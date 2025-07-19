# 🛡️ Blue Team Labs – Prácticas de Ciberseguridad Defensiva

Bienvenido a mi laboratorio de **ciberseguridad defensiva (Blue Team)**, diseñado sobre un entorno virtualizado con Kali Linux como sistema base. Aquí documento prácticas reales enfocadas en detección, análisis y defensa frente a amenazas en red.

> 🎯 *Objetivo principal: comprender, capturar y mitigar técnicas ofensivas desde el punto de vista del defensor.*

---

## ⚙️ Infraestructura del laboratorio

- 🔸 **Sistema base**: Kali Linux (host)
- 🧪 **Máquinas virtuales**: Ubuntu Server (víctima), Windows (próximamente)
- 🌐 **Red VirtualBox**: `LABNET` (red interna aislada)
- 📡 **Herramientas usadas**:
  - `nmap`, `tcpdump`, `ufw`, `iptables`
  - IDS/IPS: *por integrar (Snort / Suricata)*

---

## 📁 Estructura del repositorio
blue-team-labs/
├── README.md

├── nmap-blue-team-lab.md # Práctica de escaneo detectado con tcpdump

├── captures/ # Capturas .pcap de tráfico real

│ └── scan-full.pcap

├── screenshots/ # Evidencias visuales de terminal

│ └── tcpdump-scan.png

└── notes/ # Apuntes y comandos clave

└── tcpdump-cheatsheet.md

