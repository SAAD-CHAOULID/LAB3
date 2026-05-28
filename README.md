# Lab 3 : Interception du trafic réseau Android avec Burp Suite

Ce document détaille les étapes de configuration nécessaires pour intercepter et analyser le trafic HTTP/HTTPS provenant d'un émulateur Android à l'aide de Burp Suite.

## 1. Préparation de Burp Suite
Lancez **Burp Suite** et accédez à l'onglet **Proxy > Intercept**. Assurez-vous que le mode d'interception est défini sur **"Intercept is off"** afin que le trafic circule sans interruption tout en étant enregistré.

<img width="1261" height="712" alt="image" src="https://github.com/user-attachments/assets/ff9aa9ae-4cdc-44a9-9ea8-454330ccd67c" />

## 2. Configuration du "Proxy Listener"
Accédez aux **paramètres du Proxy (Proxy settings)** et ajoutez ou modifiez un écouteur de proxy ("listener") sur un port spécifique (par exemple, `8080`). Assurez-vous qu'il est lié à une interface réseau que l'émulateur Android peut atteindre (comme `All interfaces` ou votre adresse IP locale spécifique).

<img width="1249" height="664" alt="image" src="https://github.com/user-attachments/assets/76b38e88-f3ea-49f0-926a-0fb897f68349" />

## 3. Configuration de l'émulateur Android
Sur votre émulateur Android, modifiez les paramètres de connexion Wi-Fi pour utiliser un **Proxy manuel**. Définissez le nom d'hôte (hostname) du proxy sur l'adresse IP de votre machine hôte exécutant Burp Suite, et le port sur le port configuré précédemment (par exemple, `8080`).

<img width="469" height="707" alt="image" src="https://github.com/user-attachments/assets/73de483a-01d1-41f5-8800-5ae4ed7ceb49" />

## 4. Capture du trafic HTTP
Ouvrez un navigateur web sur l'émulateur Android et naviguez vers un site (par exemple, `example.com`). Vérifiez l'onglet **HTTP history** dans Burp Suite pour vous assurer que le trafic est bien capturé.

<img width="1273" height="419" alt="image" src="https://github.com/user-attachments/assets/9f809a36-6fdf-457a-ad50-9257ab73540c" />

## 5. Analyse des détails de la requête
Sélectionnez n'importe quelle requête capturée dans l'historique **HTTP history**. Dans le panneau inférieur sous l'onglet **Raw**, vous pouvez examiner la structure exacte de la requête HTTP, y compris les en-têtes (headers) tels que le `User-Agent`.

<img width="1014" height="603" alt="image" src="https://github.com/user-attachments/assets/b87d91ef-dba1-4f4d-a323-31762d6a95a8" />

## 6. Interception active des requêtes
Pour manipuler le trafic en temps réel, retournez à l'onglet **Intercept** et activez l'option **"Intercept is on"**. Les requêtes suivantes seront mises en pause, ce qui vous permettra de les visualiser et de les modifier avant de les transmettre.

<img width="1273" height="339" alt="image" src="https://github.com/user-attachments/assets/2e346d3d-ebc1-4bb4-9497-cd4786f6761d" />

## 7. Installation du certificat CA (HTTPS)
Par défaut, l'interception du trafic HTTPS provoquera des avertissements de sécurité dans le navigateur. Pour résoudre ce problème, vous devez installer le certificat CA de Burp Suite sur l'appareil Android.

### 7.1. Installation du certificat
Accédez aux paramètres de gestion des certificats CA dans Android pour installer le certificat CA de Burp.

<img width="466" height="446" alt="image" src="https://github.com/user-attachments/assets/ad5dc625-0650-44a3-8013-1c0fa59b3330" />

### 7.2. Validation des connexions sécurisées
Une fois le certificat installé avec succès, les connexions HTTPS ne généreront plus d'erreurs, ce qui vous permettra d'intercepter et d'analyser facilement les échanges sécurisés.

<img width="483" height="511" alt="image" src="https://github.com/user-attachments/assets/8ccf7d2f-08be-4e9a-b603-160e7cb6c648" />

