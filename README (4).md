# Lab 3 — Interception de trafic avec Burp Suite

Ce fichier `README.md` documente les étapes réalisées dans le cadre du **Lab 3**, portant sur l'interception et l'analyse du trafic réseau à l'aide de **Burp Suite** et d'un émulateur Android.

---

# Étape 1 — Préparation de Burp Suite

Lancer **Burp Suite** et s'assurer que le mode **"Intercept is off"** est activé par défaut, afin de laisser le trafic transiter librement dans un premier temps :

![Préparation de Burp Suite](./images/1.png)

---

# Étape 2 — Configuration du proxy

Configurer les paramètres réseau du proxy pour permettre la communication entre l'émulateur Android et **Burp Suite**. Cette étape est indispensable pour que les requêtes soient bien acheminées vers l'outil :

![Vérification des paramètres du proxy](./images/2.png)

---

# Étape 3 — Paramétrage de l'émulateur Android

Dans l'émulateur, renseigner l'adresse IP de la machine hôte ainsi que le port d'écoute configuré dans **Burp Suite**, afin d'établir la liaison via le proxy :

![Configuration du proxy sur l'émulateur](./images/3.png)

---

# Étape 4 — Vérification de l'interception HTTP

Confirmer que **Burp Suite** intercepte correctement les requêtes HTTP émises depuis l'émulateur. Le trafic doit apparaître dans l'onglet **Proxy > HTTP History** :

![Capture du trafic HTTP](./images/4.png)

---

# Étape 5 — Analyse de la requête brute

Ouvrir la requête interceptée et consulter son contenu dans l'onglet **RAW** afin d'examiner en détail les en-têtes, paramètres et corps de la requête :

![Lecture de la requête brute](./images/5.png)

---

# Étape 6 — Activation de l'interception active

Passer en mode **"Intercept is on"** pour bloquer et inspecter chaque requête avant qu'elle ne soit transmise au serveur. Cela permet de modifier les requêtes à la volée :

![Activation de l'interception](./images/6-2.png)

---

# Étape 7 — Installation du certificat CA

Afin d'intercepter également le trafic **HTTPS**, il est nécessaire d'installer le certificat **CA** de Burp Suite sur l'émulateur. Sans ce certificat, le navigateur signale une connexion non sécurisée.

## Étape 7.1 — Accès à la gestion des certificats

Accéder aux paramètres de sécurité de l'émulateur et naviguer jusqu'à la section de gestion des certificats pour lancer l'installation du certificat CA :

![Gestion des certificats CA](./images/7-1.png)

## Étape 7.2 — Validation de la connexion sécurisée

Une fois le certificat installé, la connexion est reconnue comme sécurisée. **Burp Suite** est désormais en mesure d'intercepter et de déchiffrer le trafic **HTTP et HTTPS** :

![Connexion sécurisée confirmée](./images/7-3.png)
