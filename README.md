# securite-mobile-lab7x
## LAB 7 : Analyse Dynamique Mobile avec MobSF
### Objectifs du lab

Comprendre en profondeur l’analyse dynamique (runtime) d’une application Android avec MobSF (Mobile Security Framework).  

Configurer un émulateur propre sans Play Store.  

Installer/lancer MobSF via Docker.  

Tester l’APK vulnérable DIVA (Damn Insecure and Vulnerable Android App) en dynamique : logs runtime, trafic réseau, instrumentation Frida, proxy HTTPS, etc.  

Apprendre à détecter des vulnérabilités en temps réel (stockage insecure, intents, hard-coded secrets, etc.).      

## L’émulateur (AVD sans Play Store)  
## l’AVD : MobSF_DIVA_API_29  
L’image ne contient aucun Play Store  

<img width="601" height="958" alt="image" src="https://github.com/user-attachments/assets/d2bf2b5d-a8ec-4ebe-a4fe-e8fb732cf305" />

  ## Cloner MobSF pour utiliser les scripts AVD officiels   
  
<img width="1282" height="265" alt="image" src="https://github.com/user-attachments/assets/4fdd13ff-c9b6-497b-9313-00b5cd286a55" />

   ## Lancement de MobSF via Docker


<img width="1430" height="532" alt="image" src="https://github.com/user-attachments/assets/9fe275d3-9b95-432c-ad46-b0c9920940e6" />  

  ## LOGIN:mobsf:mobsf

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/bf7ba626-5fce-4fef-8fb2-6907ee72c221" />  
## Apres login   


  <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/ec726696-b66a-40c8-a91e-447a7ece5378" />  
  ## Télécharger l'APK DIVA  
  ### Lien de DIVA   
  <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/57b42ca0-c670-4600-8b3c-25981824d043" />

  
  <img width="1920" height="362" alt="image" src="https://github.com/user-attachments/assets/b3ab0588-a98c-4fc9-b41f-55e8680950fb" />  
  ##  Upload de DIVA dans MobSF  
  <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/a2acca4b-4801-4448-aa4e-539de4fc6797" />
  ## Lanalyse de lapk

  <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/5307b369-2463-4da3-91e9-27ab45c09974" />    
  
  <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/fda5bb3f-517c-458d-8727-55a96f1b3884" />    
  
  🔴 Security Score : 36/100 → application très vulnérable  
    
⚠️ 2/17 Exported Activities → activités accessibles sans permission  

🔴 1/1 Exported Providers → Content Provider exposé  

🎯 Target SDK 23, Min SDK 15 → très vieux, plein de vulnérabilités      

## Larchitecture     

<img width="785" height="581" alt="image" src="https://github.com/user-attachments/assets/6f644bb5-0176-43cc-9644-9c827fb671ff" />  

  Le bouton vert "Start Dynamic Analysis" !  
  
Après le clic, MobSF va automatiquement :  


⏳ Installer DIVA sur l'émulateur  

⏳ Lancer Frida Server  

⏳ Configurer le proxy HTTPS global  

⏳ Ouvrir l'interface Dynamic Analyzer    

<img width="736" height="156" alt="image" src="https://github.com/user-attachments/assets/fb06b063-da1a-4d9d-aff4-4e93547c5e1f" />    

<img width="736" height="180" alt="image" src="https://github.com/user-attachments/assets/43ddd1fa-81e7-4c11-94e0-2f36909e3816" />

  
  <img width="1101" height="146" alt="image" src="https://github.com/user-attachments/assets/855fc6bd-b4c9-4ffd-958c-6fa6f7a501ee" />

  # jai relancer lemulateure 

 <img width="1350" height="560" alt="image" src="https://github.com/user-attachments/assets/aa589ca4-2bc7-400d-96a0-13b5410165dc" />  
 ## le prob <img width="972" height="148" alt="image" src="https://github.com/user-attachments/assets/6751fa32-981e-4f9a-8fff-966ade531b7a" />    
 ## Lancement de l'Analyse Dynamique  
 
 <img width="1556" height="421" alt="image" src="https://github.com/user-attachments/assets/7e389afb-5d52-4729-9557-2b51b82144b5" />

  ## Interface Dynamic Analyzer  
  <img width="1550" height="693" alt="image" src="https://github.com/user-attachments/assets/2af3243d-891b-469d-85f1-ec182b1763b9" />  
  ## Logcat Stream en temps réel  
  Le flux Logcat filtré pour le package jakhar.aseem.diva affiche en temps réel les logs système lors de l'installation de l'application. On peut voir les événements PACKAGE_ADDED et les vérifications de type MediaProvider.

Utilité : Le Logcat Stream permet de détecter en live les fuites d'informations dans les logs (Challenge #1 — Insecure Logging). Des mots de passe, tokens ou données sensibles peuvent apparaître ici si l'application ne filtre pas ses logs en production.  
##  TLS/SSL Security Tester  
<img width="1104" height="820" alt="image" src="https://github.com/user-attachments/assets/e68def1f-51e4-41ab-9430-6e00a16e054c" />  
## MobSF exécute une batterie de tests TLS/SSL sur DIVA  
<img width="1109" height="438" alt="image" src="https://github.com/user-attachments/assets/193650f5-fefa-4e58-8b6f-6fecca74f183" />  

  ## Challenge "Input Validation" — Missile Launch App
<img width="1528" height="608" alt="image" src="https://github.com/user-attachments/assets/17e3ac84-817f-40db-b86c-d2b4090ff514" />  
## Instrumentation Frida
<img width="1501" height="669" alt="image" src="https://github.com/user-attachments/assets/66a615b7-8e27-4870-9744-4be734156e54" />    
 
bypass_build_properties()  

bypass_phonenumber()  

bypass_deviceid()  

bypass_imsi()  

bypass_operator_name()  
## Frida + crypto-aes-key + Shell Access root
<img width="1501" height="669" alt="image" src="https://github.com/user-attachments/assets/eabe8b02-4041-4920-9d77-af64ebf21761" />  
Le script Frida crypto-aes-key est sélectionné. Ce script intercepte les appels à SecretKeySpec et capture les clés AES utilisées par l'application en clair, en affichant leur contenu hexadécimal. En bas de page, le Shell Access donne un accès root direct à l'émulateur ([root@android] #)  

<img width="910" height="666" alt="image" src="https://github.com/user-attachments/assets/cb39b738-7642-4c3a-910f-c48f672f6600" />
# Rapport Dynamique Final
<img width="1518" height="704" alt="image" src="https://github.com/user-attachments/assets/7e52010e-b249-4e16-95ce-4ecbb27b4360" />    

Le rapport dynamique final présente :

Information : Accès aux HTTPTools pour consulter le trafic brut.  

Raw Logs : HTTP(S) Traffic | Logcat Logs | Dumpsys Logs | Application Data. 

    
TLS/SSL Security Tester : 4 tests passés (Cleartext Traffic, TLS Misconfiguration, TLS Pinning Bypass, TLS Pinning/Certificate Transparency). 

  
Exported Activity Tester : Tests des activités exportées accessibles sans permission.  

Le menu latéral liste toutes les sections : Information, TLS/SSL Security Tester, Exported Activity Tester, Activity Tester, Screenshots, Runtime Dependencies, Malware Analysis, Reconnaissance, File Analysis, Download/Print Report.  
# 🔐 Rapport d’Audit de Sécurité - [Nom de l'Application]

Ce document résume les vulnérabilités critiques et les faiblesses de sécurité identifiées lors de l’analyse statique de l’application. L’objectif est de fournir une vision claire des risques et de prioriser les corrections.

## 📊 Résumé des Vulnérabilités

| Catégorie | Sévérité | Détail |
| :--- | :--- | :--- |
| **Security Score** | 🔴 Critique | **36/100** — Application extrêmement vulnérable |
| **Exported Activities** | 🟠 Haut | 2/17 activités exportées sans restriction |
| **Exported Providers** | 🔴 Critique | 1/1 Content Provider accessible sans permission |
| **Insecure Data Storage** | 🔴 Critique | Données en clair (SharedPrefs, SQLite, Fichiers) |
| **Insecure Logging** | 🟠 Haut | Données sensibles visibles dans Logcat |
| **Hardcoded Credentials** | 🔴 Critique | Clés / mots de passe codés en dur dans l'APK |
| **Input Validation** | 🔴 Critique | SQLi, XSS WebView, Buffer Overflow natif |
| **Access Control** | 🟠 Haut | Activités et Providers accessibles sans authentification |
| **TLS/SSL** | 🔵 Info | SSL Pinning contourné avec succès par MobSF |

---

## 🧾 Légende des Sévérités

*   🔴 **Critique** : À corriger immédiatement. Risque élevé de compromission totale.
*   🟠 **Haut** : Priorité haute. Exposition significative des données ou des fonctionnalités.
*   🟡 **Moyen** : À planifier. Faiblesses nécessitant une attention.
*   🔵 **Info** : Information ou faible risque. Bonnes pratiques à améliorer.

---


**Note** : Ce rapport est basé sur une analyse dynamique et statique. Une revue manuelle du code source est recommandée pour confirmer certains points.








    








