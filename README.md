# 🏗️ Architecture Microservices — Spring Boot, Eureka, Gateway & REST

## 📌 Introduction
Ce projet met en place une architecture microservices basée sur Spring Boot.  
Chaque service est indépendant et communique via un Service Discovery Eureka et une API Gateway.

### 🧩 Services inclus
- 🔎 Eureka Server — registre des services  
- 👤 Service Client — gestion des clients  
- 🚘 Service Voiture — gestion des voitures  
- 🌐 API Gateway — point d’entrée unique pour les requêtes externes  

Cette architecture facilite :
✔️ la découverte des services  
✔️ la scalabilité  
✔️ la résilience  
✔️ la maintenance  

---

## A️⃣ — Service Discovery : Eureka Server

### 🎯 Rôle
Eureka permet aux microservices de se découvrir dynamiquement, sans coder les IP/Ports en dur.

### ⚙️ Création du projet
Projet généré via Spring Initializr avec la dépendance :

Eureka Server


https://github.com/YASSMINEOUQUELLI12/tp20/blob/main/eurekaserver/tp20-1.PNG
https://github.com/YASSMINEOUQUELLI12/tp20/blob/main/clientserver/tp20-2.PNG
https://github.com/YASSMINEOUQUELLI12/tp20/blob/main/servicegateway/tp20-3.PNG
https://github.com/YASSMINEOUQUELLI12/tp20/blob/main/clientserver/tp20-2.PNG


### 🏁 Classe principale
```java
@EnableEurekaServer
@SpringBootApplication
public class EurekaServerApplication {
    public static void main(String[] args) {
        SpringApplication.run(EurekaServerApplication.class, args);
    }
}
B️⃣ — Microservice Client
🎯 Rôle

Le service Client gère les informations sur les clients et utilise MySQL.

Fonctionnalités REST

Ajouter un client

Consulter la liste des clients

Rechercher un client par identifiant

Le service est enregistré automatiquement dans Eureka.

C️⃣ — API Gateway
🎯 Rôle

Spring Cloud Gateway sert de point d'entrée unique.
Il redirige les requêtes vers les différents microservices enregistrés dans Eureka.

D️⃣ — Microservice Voiture
🎯 Rôle

Le service Voiture gère les informations relatives aux voitures.

Fonctionnalités REST

Récupérer toutes les voitures

Rechercher une voiture par ID

Afficher aussi les informations du client associé

Communique avec le service Client via Eureka + Gateway.

▶️ Démarrer les services (ordre recommandé)

Démarrer Eureka Server

Démarrer Service Client

Démarrer Service Voiture

Démarrer API Gateway

Vérifier dans :
http://localhost:8761

🧪 Tests via Gateway

Liste des clients :
GET http://localhost:8888/SERVICE-CLIENT/api/client

Liste des voitures :
GET http://localhost:8888/SERVICE-VOITURE/api/cars


📚 Concepts clés

Service Discovery

API Gateway

RESTful APIs

Base de données indépendante par service

🙌 Conclusion

Cette architecture illustre une approche moderne, évolutive et maintenable pour une application microservices.
Elle peut être enrichie avec la sécurité, Docker, Kubernetes, monitoring, etc.


