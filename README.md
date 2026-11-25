## Hallo 👋

Ich automatisiere die Einrichtung und **Härtung von Ubuntu-Systemen** mit Bash, vom Installer-Stick bis zum laufenden, geprüften System. Ziel sind Clients und Server, die reproduzierbar, offline installierbar und nach **CIS Level 1** und den BSI-Empfehlungen abgesichert sind.

**Plattformen:** Ubuntu 24.04 LTS und 26.04 LTS, amd64 und arm64 (u. a. NVIDIA DGX Spark)

🌐 **Website:** [chicco70.github.io](https://chicco70.github.io)

---

### Projekte

Die Projekte bauen aufeinander auf:

```
ISO-Partitionen  →  SystemSetup  →  Hardening
 Installation       Einrichtung     Härtung + Prüfung
                         ↑
                       Mirror
                interne Paketquellen
```

| Projekt | Worum es geht |
|---|---|
| **ISO-Partitionen** | Ubuntu-Installer (ISO/USB-Stick) mit Autoinstall. Legt ein CIS-konformes Partitionslayout an: LUKS-Verschlüsselung, LVM, getrennte Volumes für `/var`, `/var/log`, `/tmp`, `/home` usw. mit `nodev`, `nosuid` und `noexec`. Secure Boot bleibt erhalten. |
| **SystemSetup** | Richtet ein frisch installiertes System ein: Hostname, Netzwerk, Paketquellen, Benutzer, Pakete, VS Code, Chromium, LM Studio und ClamAV mit geplanten Scans. Läuft auch offline mit Installationsdaten vom USB-Stick. |
| **Mirror** | Interner Mirror-Server für Ubuntu, ClamAV-Signaturen und optional NVIDIA-, Kubernetes- und weitere Repositories. Dazu Skripte, die Clients auf den Mirror umstellen und kopierte Systeme (VM-Export/-Import) anpassen. |
| **Hardening** | Modulares Härtungs-Framework mit 31 Modulen und vier Profilen (desktop, server, secure, kiosk): SSH, PAM, auditd, AIDE, sysctl, Mount-Optionen, fail2ban und mehr. Jede Änderung wird gesichert und kann zurückgenommen werden. Prüfung mit OpenSCAP und Lynis, Ausnahmen sind dokumentiert. |

---

### Arbeitsweise

- **Idempotent:** Ein zweiter Lauf ändert nichts, was schon stimmt.
- **Erst fragen, dann ändern:** Zusammenfassung vor jeder Änderung, `--dry-run` wo möglich.
- **Sicherung und Rollback:** Originaldateien werden vor jeder Änderung gesichert.
- **Offline-fähig:** Installation und Updates ohne Internet über einen eigenen Mirror oder vom USB-Stick.
- **Nachweisbar:** OpenSCAP- und Lynis-Berichte, dokumentierte Ausnahmen für das Audit.

### Werkzeuge

`Bash` · `systemd` · `netplan` · `apt` / `apt-mirror2` · `cloud-init` / Autoinstall · `LUKS` / `LVM` · `OpenSCAP` · `Lynis` · `auditd` · `AIDE` · `ClamAV` · `ufw` · `Apache`

---

<sub>Die Repositories sind privat. Beispiele in der Dokumentation verwenden Platzhalter wie `mirror.example.com` oder `192.0.2.10`. · [Impressum](https://chicco70.github.io/impressum.html) · [Datenschutz](https://chicco70.github.io/datenschutz.html)</sub>
