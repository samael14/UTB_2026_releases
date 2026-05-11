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
