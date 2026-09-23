ICT-Support Training Lab - Automatisierung

Dieses Repository enthält die Ansible-Playbooks zur Automatisierung eines Support-Trainingslabors. Über Semaphore können gezielt Fehlerzustände (Sabotage) auf einer Ziel-VM erzeugt und per Knopfdruck wieder behoben (Heilung) werden.

Dies ermöglicht ein realistisches, reproduzierbares Training für den 1st- und 2nd-Level-Support.

🎯 Zielumgebung

Betriebssystem: Linux Mint (Proxmox VM)

IP-Adresse: 10.80.49.125

User: user (mit passwortlosem sudo)

🛠️ Szenarien Übersicht

Das Labor umfasst aktuell 11 voll automatisierte Trainings-Szenarien:

Webserver Ausfall: Stoppt/Startet den Nginx-Dienst.

Login gesperrt: Sperrt den Benutzeraccount (passwd -l).

DNS Sabotage: Manipuliert die /etc/resolv.conf (ungültiger Nameserver).

Fstab Emergency Mode: Trägt einen fehlerhaften Mountpoint in die /etc/fstab ein.

SSH Dienst: Deaktiviert den Remote-Zugang via SSH.

Docker Loop: Stoppt den Docker-Daemon und simuliert Container-Ausfälle.

KI / Ollama Offline: Beendet den lokalen KI-Dienst.

NTP (Zeit verstellt): Deaktiviert die Zeitsynchronisation und setzt ein falsches Datum.

Hosts (Lokale DNS): Leitet localhost in der /etc/hosts falsch um.

Sudo-Rechte entzogen: Entfernt den Benutzer aus der sudo-Gruppe.

Bashrc Sabotage: Erzwingt einen sofortigen Logout bei SSH-Verbindungen (exit in .bashrc).

🚀 Ausführung via Semaphore

Alle Playbooks werden über die Semaphore-Weboberfläche gesteuert.

Sabotage-Tasks: Führen den Fehler herbei und eröffnen (zukünftig) automatisch ein Zammad-Ticket.

Heilungs-Tasks: Setzen das System in den Ausgangszustand zurück und schließen das Zammad-Ticket.

Wichtig: In den Semaphore Task Templates muss unter CLI args zwingend --become gesetzt sein.
