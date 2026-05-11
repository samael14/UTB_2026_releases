# Boîte à outils complète pour techniciens et administrateurs système Windows. Application Electron + React + Python.

# Installation & Lancement — Version Standalone (EXE)

Guide pour les utilisateurs finaux souhaitant installer ou utiliser UTB sans passer par le code source.

---

## Télécharger

Rendez-vous sur la page des releases GitHub :

**https://github.com/samael14/UTB_2026_releases/releases/latest**

Deux fichiers disponibles :

| Fichier | Type | Usage |
|---------|------|-------|
| `Ultimate ToolBox Setup X.X.X.exe` | Installeur | Installation classique, raccourci Bureau/Menu Démarrer |
| `Ultimate ToolBox X.X.X.exe` | Portable | Lancement direct sans installation, depuis une clé USB |

---
![Cover](https://github.com/samael14/UTB_2026_releases/blob/main/utb.png)
![Cover](https://github.com/samael14/UTB_2026_releases/blob/main/utb1.png)

## Prérequis

- **Windows 10 ou 11 — 64 bits**
- **Python 3.10+** (requis pour les fonctionnalités avancées du backend)
  - Télécharger : https://www.python.org/downloads/
  - ⚠️ Cocher **"Add Python to PATH"** lors de l'installation
- **~500 Mo d'espace disque libre**
- **Droits Administrateur** (obligatoire pour les modules système : AD, services, registre, pare-feu…)

---

## Option 1 — Installeur (recommandé)

1. Télécharger `Ultimate ToolBox Setup X.X.X.exe`
2. **Clic droit → Exécuter en tant qu'administrateur**
3. Accepter l'UAC
4. Suivre l'assistant (dossier par défaut : `C:\Program Files\Ultimate ToolBox`)
5. Cocher "Lancer Ultimate ToolBox" à la fin

Au **premier lancement**, l'application installe automatiquement les dépendances Python backend :
```
flask, flask-cors, psutil, requests, pywin32, wmi, ...
```
Cette opération prend 1 à 3 minutes selon la connexion Internet.

---

## Option 2 — Portable (aucune installation)

1. Télécharger `Ultimate ToolBox X.X.X.exe`
2. Placer le fichier dans le dossier souhaité (ex : `D:\Outils\UTB\`)
3. **Clic droit → Exécuter en tant qu'administrateur**

> Le mode portable stocke ses données dans `%APPDATA%\Ultimate ToolBox\`.

---

## Premier lancement

L'application démarre avec un **splash screen** puis accède au dashboard.

Si le backend Python ne démarre pas automatiquement :
1. Ouvrir PowerShell en administrateur
2. Naviguer vers le dossier d'installation
3. Lancer manuellement :
```powershell
python python\server.py
```

---
## Modules disponibles

### 🖥️ Système
- Informations système (CPU, RAM, BIOS, matériel)
- Gestion des services Windows
- Éditeur de registre
- Variables d'environnement
- Gestionnaire de tâches avancé
- Journaux d'événements
- Maintenance & Technicien (SFC, DISM, chkdsk, BCD)
- Nettoyage du PC (corbeille, temp, prefetch, WinSxS)
- Dossiers partagés (NTFS/SMB)
- Éditeur Hosts
- Gestionnaire démarrage (Autorun)
- Planificateur de tâches
- Profils locaux Windows (analyse, nettoyage cache, backup, suppression)
- **🚀 Tweaks Windows** *(v1.3.0)* — 18 tweaks : performances, vie privée, réseau, jeux, MAJ, explorateur
- **🏢 Active Directory & GPO** — 7 onglets + filtre OU *(v1.3.0)*

### 💾 Disques
- Liste et informations disques
- Formatage sécurisé
- Gestion des partitions
- Nettoyage de disque
- Initialisation de disques

### 🌐 Réseau
- Configuration IP / WiFi / DNS
- Tables de routage
- Wake-on-LAN
- Scanner de ports
- Diagnostics réseau
- Gestionnaire Proxy
- Gestionnaire VPN

### 🔒 Sécurité
- Windows Defender
- Pare-feu
- Gestion des certificats
- Audit sécurité Windows
- Scanner de vulnérabilités (CVE local + Nmap)
- Outils Pentest
- OSINT Framework
- **Alertes ANSSI / NVD CVE** *(NVD API v2)*

### 🛠️ Outils
- Chocolatey / Winget
- Checksum (MD5, SHA1, SHA256, SHA512)
- Speedtest
- Gestionnaire de fichiers avancé
- Imprimantes et scanners
- Encodeur/Décodeur (Base64, URL, HTML, JWT)
- Générateur de mots de passe
- Formateur JSON
- Comparateur de texte (diff)
- Lanceur ScriptManager

### 📊 Monitoring
- CPU, RAM, Disque en temps réel
- Trafic réseau / Bande passante
- Activité disques
- Logs système

### 🌍 Accès distant
- Client SSH (avec gestion clés)
- FTP/SFTP
- Bureau à distance
- Gestionnaire serveurs PMAD
- PsTools (PsExec, PsList, PsKill)

### 💻 Développement
- Docker management
- Git tools
- Clients BDD (MySQL, PostgreSQL, MongoDB, SQLite)
- REST API client

### 🔬 Diagnostic
- Rapport système complet
- Tests connectivité
- Analyse démarrage

## Fonctionnalités nécessitant des droits élevés

Certains modules ne fonctionnent qu'avec des droits Administrateur :

| Module | Raison |
|--------|--------|
| Active Directory | Requêtes LDAP/PowerShell AD |
| Services Windows | Start/Stop services système |
| Registre | Lecture/écriture HKLM |
| Pare-feu | Modification règles netsh |
| Windows Tweaks | Modification registre système |
| Pentest / Scanner | Accès réseau bas niveau |
| Maintenance (SFC/DISM) | Commandes système protégées |

---

## Désinstallation

**Version installeur** : Panneau de configuration → Programmes → Ultimate ToolBox → Désinstaller

**Version portable** : Supprimer le fichier `.exe`. Les données utilisateur restent dans `%APPDATA%\Ultimate ToolBox\` (suppression manuelle si souhaité).

---

## Problèmes courants

| Problème | Solution |
|----------|----------|
| "Windows a protégé votre PC" | Clic sur "Informations complémentaires" → "Exécuter quand même" |
| Backend Python ne démarre pas | Vérifier que Python est dans le PATH : `python --version` |
| Module AD inactif | Installer RSAT sur le PC : `Get-WindowsCapability -Online -Name RSAT*` |
| Erreur "accès refusé" | Relancer en tant qu'administrateur |
