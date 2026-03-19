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








