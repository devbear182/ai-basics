# Local AI Setup

## Ziel

Lokale KI-Umgebung auf einem privaten Linux-PC für:

- Lernen und Experimentieren mit lokalen LLMs
- DevOps-Unterstützung
- PowerShell- und Azure-Unterstützung
- Coding Assistant
- spätere Erweiterung um RAG, Agenten und Automatisierung

---

## Hardware

CPU:

```
AMD Ryzen 7 5700X 8-Core Processor
```

GPU:

```
NVIDIA GeForce RTX 5060
VRAM: 8 GB
Driver: 580.159.03
CUDA: 13.0
```

RAM:

```
16 GB
```

Storage:

```
NVMe SSD 1 TB
Freier Speicher ausreichend
```

---

## Betriebssystem

Distribution:

```
Linux Mint 22.3 (Zena)
```

Basis:

```
Ubuntu 24.04 / Noble
```

Kernel:

```
6.17.0-35-generic
```

---

## Aktuelle Architektur

```
Linux Mint Host
│
├── Ollama
│     ├── systemd Service
│     ├── localhost:11434
│     └── lokale Modelle
│
└── Docker
      └── Open WebUI
            ├── host networking
            ├── localhost:8080
            └── persistentes Volume
```

---

## 1. Ollama Installation

### Installation

Ollama wurde als nativer Linux-Service installiert.

Bewusste Entscheidung:

- kein Ollama Docker Container
- direkter Zugriff auf NVIDIA GPU
- weniger Komplexität für Einstieg

---

## Prüfung

Version:

```bash
ollama --version
```

Service:

```bash
systemctl status ollama
```

Erwartung:

```
ollama.service
Active: active (running)
```

---

### Netzwerk

Aktueller Zustand:

```
127.0.0.1:11434
```

Prüfung:

```bash
sudo ss -tulpn | grep 11434
```

Bedeutung:

- Ollama ist nur lokal erreichbar.
- Kein direkter Zugriff aus dem Netzwerk.
- Open WebUI greift über Host Networking darauf zu.

---

## 2. Modell Installation

Installiertes Modell:

```
qwen2.5:7b
```

Installation:

```bash
ollama pull qwen2.5:7b
```

Prüfung:

```bash
ollama list
```

API-Prüfung:

```bash
curl http://127.0.0.1:11434/api/tags
```

Aktuelle Eigenschaften:

```
Model:
qwen2.5:7b

Parameter:
7.6B

Format:
GGUF

Quantisierung:
Q4_K_M

Größe:
ca. 4.7 GB

Context:
32768 Tokens
```

---

## 3. Docker Installation

### Installation

Docker Engine wurde installiert.

Kein Docker Desktop verwendet.

Grund:

- Linux-System
- geringere Komplexität
- nativer Docker Engine Betrieb

---

### Prüfung

```bash
sudo docker run hello-world
```

Erwartung:

```
Hello from Docker!
This message shows that your installation appears to be working correctly.
```

---

## 4. Open WebUI Installation

### Container Start

Aktueller Container:

```bash
sudo docker run -d \
  --network=host \
  -v open-webui:/app/backend/data \
  -e OLLAMA_BASE_URL=http://127.0.0.1:11434 \
  --name open-webui \
  --restart unless-stopped \
  ghcr.io/open-webui/open-webui:main
```

---

## Begründung der nicht standardmäßigen Einstellungen

### Docker Netzwerk

Verwendet:

```
--network=host
```

Grund:

- Ollama läuft direkt auf Linux Host.
- Ollama lauscht nur auf 127.0.0.1.
- Open WebUI kann dadurch direkt localhost:11434 verwenden.

Alternative:

```
--add-host=host.docker.internal:host-gateway
```

wäre für normales Docker Bridge Networking möglich.

Diese Variante wurde bewusst nicht verwendet.

---

### Ollama Verbindung

Verwendet:

```
OLLAMA_BASE_URL=http://127.0.0.1:11434
```

Nicht verwendet:

```
http://host.docker.internal:11434
```

Grund:

Bei:

```
--network=host
```

gilt:

```
Container localhost == Linux Host localhost
```

Bei normalem Docker Networking wäre dagegen:

```
host.docker.internal
```

korrekt.

---

### Open WebUI Port

Kein Port Mapping:

```
-p 3000:8080
```

verwendet.

Grund:

Bei:

```
--network=host
```

nutzt der Container direkt den Host-Port.

Aktuelle URL:

```
http://localhost:8080
```

---

### Restart Policy

Verwendet:

```
--restart unless-stopped
```

Bedeutung:

- Container startet automatisch nach Neustart des PCs.
- Container startet nach Fehler automatisch neu.
- Ein bewusst gestoppter Container bleibt gestoppt.

---

### Persistente Daten

Verwendet:

```
-v open-webui:/app/backend/data
```

Das Docker Volume enthält:

- Benutzer
- Chats
- Einstellungen
- Knowledge Bases
- zukünftige RAG-Daten

Das Löschen des Containers entfernt diese Daten nicht.

---

## Open WebUI Benutzerverwaltung

Aktueller Modus:

```
Multi User Mode
```

Nicht verwendet:

```
Single User Mode
```

Grund:

Spätere Nutzung durch mehrere Linux-Benutzer möglich.

Vorteile:

- getrennte Chats
- getrennte Dokumente
- getrennte Einstellungen

---

## Aktuelle URLs

Open WebUI:

```
http://localhost:8080
```

Ollama API:

```
http://127.0.0.1:11434
```

---

## Verifikation

### Ollama

```bash
ollama list
```

Erwartung:

```
qwen2.5:7b
```

---

### Ollama API

```bash
curl http://127.0.0.1:11434/api/tags
```

Erwartung:

JSON mit installiertem Modell.

---

### Docker

```bash
sudo docker ps
```

Erwartung:

```
open-webui   Up
```

---

### Open WebUI

Browser:

```
http://localhost:8080
```

Erwartung:

- Login funktioniert
- Modell qwen2.5:7b sichtbar
- Prompts werden beantwortet

---

# Bekannte Entscheidungen / spätere Erweiterungen

## Noch nicht umgesetzt

- Docker Compose
- Git Repository für Infrastruktur
- Backup Strategie
- RAG
- Embedding Datenbank
- Agenten
- Monitoring

---

## Geplante nächste Ausbaustufen

### Stufe 1
Produktive Nutzung:

- VS Code Integration
- Continue.dev
- Aider
- DevOps-Unterstützung

### Stufe 2
Lokale Wissensbasis:

- Dokumente
- PDFs
- Markdown
- Projektdokumentation

### Stufe 3
Agenten:

- kontrollierte Aktionen
- Git Integration
- Human Approval

### Stufe 4
Homelab Ausbau:

- Docker Compose
- mehrere Modelle
- Monitoring
- Automatisierung




https://github.com/open-webui/open-webui#troubleshooting