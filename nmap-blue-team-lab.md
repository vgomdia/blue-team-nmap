# 🛡️ Blue Team – Detección de escaneo Nmap (Laboratorio VirtualBox)

## 🔧 Escenario
- 🖥️ **Host base**: Kali Linux (VirtualBox)
- 🧪 **VM víctima**: Ubuntu Server
- 🌐 **Red**: Interna (VirtualBox) – `LABNET`
- 📦 **Modo de red**: Promiscuo desactivado

## 🎯 Objetivo
Detectar y analizar un escaneo Nmap SYN (`-sS -A -T4 -Pn`) desde la perspectiva del **equipo defensor (Blue Team)**.

---

## 🧱 Infraestructura

| Rol         | SO             | IP             | Interfaz  |
|-------------|----------------|----------------|-----------|
| Kali Linux  | Kali Rolling   | 10.73.2.X      | `enp0s3`  |
| Ubuntu VM   | Ubuntu Server  | 10.73.2.141    | `enp0s3`  |

---

## 🔍 Escaneo ofensivo (Kali – Red Team)

```bash
sudo nmap -sS -T4 -A -Pn 10.73.2.141
```

**Resultado:**
- Puerto SSH (22/tcp) abierto
- Detección de versión: `OpenSSH 8.2p1 Ubuntu`
- Sistema operativo estimado: Linux 4.X/5.X
- MAC address visible (VirtualBox NIC)
- Saltos: 1 (host directo)

---

## 🛡️ Detección defensiva (Ubuntu – Blue Team)

### 1. Instalar `tcpdump`:
```bash
sudo apt update && sudo apt install tcpdump -y
```

### 2. Capturar tráfico:
```bash
sudo tcpdump -i enp0s3
```

### 3. Opcional – Solo SYN:
```bash
sudo tcpdump -i enp0s3 'tcp[tcpflags] & tcp-syn != 0'
```

### 4. Resultado esperado:
```
IP 10.73.2.X.#### > 10.73.2.141.22: Flags [S], ...
IP 10.73.2.X.#### > 10.73.2.141.443: Flags [S], ...
...
```

Cada línea representa un intento de conexión TCP (SYN) a distintos puertos → actividad típica de escaneo.

---

## 🔐 Conclusión

Este ejercicio muestra cómo un escaneo activo con Nmap deja rastros claros en el sistema objetivo. Como defensor puedes:
- Identificar patrones de escaneo
- Registrar IPs atacantes
- Activar medidas como:
  - Reglas `iptables`/`ufw`
  - Bloqueo dinámico con `fail2ban`
  - IDS como `Suricata` o `Snort`

---

## 📁 Archivos sugeridos para GitHub

```
/blue-team-lab/
├── nmap-blue-team-lab.md   ← Este documento
├── captures/
│   └── scan-full.pcap      ← (exportado con Wireshark o tcpdump -w)
└── screenshots/
    └── tcpdump-scan.png
```

---

## 📌 Recomendación
Sube también capturas de pantalla del terminal con `tcpdump` y del escaneo de Nmap para documentar evidencias visuales. Añade etiquetas en tu repositorio como `blue-team`, `nmap`, `tcpdump`, `virtualbox-lab`.

```
Invest in yourself everyday – CyberLab | Blue Team | Barcelona 🇪🇸
```
