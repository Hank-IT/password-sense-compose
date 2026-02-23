# Password Sense – Docker Compose Basis

Dieses Repository enthält die **Basis-Docker-Compose-Konfiguration** für **Password Sense**.

Die bereitgestellte `compose.yml` ist **nicht für den direkten Einsatz gedacht**, sondern dient als **Grundlage**, die **zwingend über eine `compose.override.yml`** an die jeweilige Zielumgebung angepasst werden muss.

## Override-Konzept

Die Trennung ist bewusst gewählt:

- `compose.yml`  
  Enthält die **generische, wiederverwendbare Basiskonfiguration**.
- `compose.override.yml`  
  Wird **pro Umgebung** bereitgestellt und ergänzt oder überschreibt z. B.:
  - Labels (z. B. für Traefik)
  - Ressourcen-Limits
  - Volumes
  - Umgebungsabhängige Anpassungen

Docker Compose merged beide Dateien automatisch oder explizit via `-f`.

## Netzwerk-Voraussetzung

Die Konfiguration geht davon aus, dass ein **externes Docker-Netzwerk** mit dem Namen **frontend** bereits existiert.

Dieses Netzwerk wird typischerweise von **Traefik** verwendet und **nicht** von dieser Compose-Datei erstellt.

Beispiel:
```bash
docker network create frontend