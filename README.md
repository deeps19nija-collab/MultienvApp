# MultienvApp

## MULTI-ENVIRONMENT TICKET MANAGEMENT SYSTEM – DEPLOYMENT DOCUMENTATION


## This document explains everything needed to deploy the Dev backend, Prod backend, Frontend, and MongoDB locally using Docker & Docker Compose.

It includes:
1.  PreRequisites
2.  EnvironmentVariables
3.	Full deployment steps
4.	Access information (ports + URLs)
5.	How to Add Data
6.	Running Application Screenshots
7.	Assumtions
8.	Limitations.

*************************************************************************************************************************************************

## 1.	PREREQUISITES
Before deployment, install:
•	Docker Desktop
•	Docker Compose (already included in Docker Desktop)
•	VS Code


## 2.	 ENVIRONMENT VARIABLES
Dev Backend → backend/dev/.env
FLASK_ENV=development
MONGO_URI=mongodb://dev-mongo:27017/devdb
Prod Backend → backend/prod/.env
FLASK_ENV=production
MONGO_URI=mongodb://prod-mongo:27017/proddb

## 3. DEPLOYMENT STEPS
Follow these steps:
________________________________________
Step 1 — Open VS Code as Administrator
If you had permission issues before, running as admin helps.
________________________________________
Step 2 — Navigate to Your Project
cd path/to/multiEnv
________________________________________
Step 3 — Build & Start All Services
docker compose up --build
________________________________________
Step 4 — Verify Containers
docker ps
You should see:
•	dev-mongo
•	prod-mongo
•	dev-backend
•	prod-backend
•	frontend

 ## 4. ACCESS INFORMATION (URLs + PORTS)
Below are the access URLs information: 

 **Frontend (React)**
Environment	URL	Port  
Frontend App	http://localhost:3001	3001  

**Backend Services (Flask)** 

**Dev Backend**  
Type	URL	Port  
API (GET tickets)	http://localhost:3000/api/tickets	3000  
Web UI	http://localhost:3000/	3000  

**Prod Backend**  
Type	URL	Port  
API (GET tickets)	http://localhost:3002/api/tickets	3002  
Web UI	http://localhost:3002/  


 **MongoDB Databases**  
Purpose	Container	Local Port	Internal Port  

Dev Database	dev-mongo	27018	27017  
Prod Database	prod-mongo	27019	27017  
 connect to Mongo using Compass:  
mongodb://localhost:27018  
mongodb://localhost:27019  

## 5. HOW TO ADD DATA  

**Method 1 — Use Backend UI  **
Dev:  
http://localhost:3000/  
Prod:  
http://localhost:3002/  

**These pages include:**
•	Add ticket form  
•	Mark complete  
•	Delete  

**Method 2 — Use MongoDB Compass**  
Insert documents manually.  

## 6.  Running Application Screenshots

**Running Application Logs**  
https://github.com/deeps19nija-collab/MultienvApp/blob/main/logs.txt

### docker compose build --no-cache
<img width="1060" height="542" alt="image" src="https://github.com/user-attachments/assets/b44e93e4-bbcb-4135-8e0d-248a59f59a53" />

### docker compose up
<img width="1076" height="557" alt="image" src="https://github.com/user-attachments/assets/ac6ee19c-e5c9-4eae-9f48-369d7e862d9c" />


<img width="1918" height="661" alt="image" src="https://github.com/user-attachments/assets/cffd03f1-9207-4b4e-8ea8-127d2739cc5f" />

DEV Environment
<img width="1918" height="397" alt="image" src="https://github.com/user-attachments/assets/3c2016f5-c69b-4171-9d26-dd73b0dd93ea" />

Prod Environment  

<img width="1918" height="506" alt="image" src="https://github.com/user-attachments/assets/8d8e69f3-3a1d-472c-8084-fcdc1d7750fc" />

Add a prod Ticket 
<img width="1918" height="573" alt="image" src="https://github.com/user-attachments/assets/c35f3969-9fbd-4ae4-b581-fbd342294174" />
<img width="1918" height="787" alt="image" src="https://github.com/user-attachments/assets/b1480eef-2028-4eb7-ad1c-040bb82cf47c" />
Pending Ticket list
<img width="1918" height="467" alt="image" src="https://github.com/user-attachments/assets/2b338d82-5ee1-4126-a988-80f7a2d13300" />

Marked the ticket as completed
<img width="1918" height="672" alt="image" src="https://github.com/user-attachments/assets/c888cc6d-d9f8-4499-8b53-e346359ea14f" />
<img width="1918" height="443" alt="image" src="https://github.com/user-attachments/assets/fb80725e-57ca-4d5f-8668-1ffbaf7cb210" />

### Add a new Dev Ticket

<img width="1918" height="823" alt="image" src="https://github.com/user-attachments/assets/0872e45a-5317-4bd9-9496-a098da7a2160" />
<img width="1912" height="678" alt="image" src="https://github.com/user-attachments/assets/e003cd52-7c2e-4a3b-9c36-bae52890469a" />
<img width="1907" height="833" alt="image" src="https://github.com/user-attachments/assets/04496cb9-c718-4948-b4c8-59391f4884e4" />
<img width="1912" height="472" alt="image" src="https://github.com/user-attachments/assets/d28460c6-0e37-4195-9162-b98930d90be2" />

### Delete a Prod Ticket
<img width="1913" height="837" alt="image" src="https://github.com/user-attachments/assets/92820b4d-d258-4a30-ac26-76a32f798f11" />

<img width="1902" height="458" alt="image" src="https://github.com/user-attachments/assets/e5a413c3-adeb-4425-a1f1-160fee04b64f" />

### Delete a DEV Ticket


<img width="1738" height="820" alt="image" src="https://github.com/user-attachments/assets/989f4e78-273c-4224-aaf7-4be05d00476a" />

<img width="1918" height="532" alt="image" src="https://github.com/user-attachments/assets/5194c599-9497-4078-962c-e333c5f4e5c7" />

##  7. ASSUMPTIONS
1. MongoDB is required for both environments
2. Frontend expects these env variables:
•	REACT_APP_DEV_API
•	REACT_APP_PROD_API
  No authentication is implemented

## 8. LIMITATIONS
•	No create/update/delete API for tickets (only web UI supports write actions)
•	No role-based access or login system
•	No reverse proxy (NGINX)
•	Both dev and prod MongoDB run locally (not secure for real use)


















