\# TP 4 — Kubernetes



\*\*Établissement :\*\* Université Abdelmalek Essaadi – GL ENSAH  

\*\*Année universitaire :\*\* 2026/2027  

\*\*Module :\*\* Virtualisation et Cloud Computing  

\*\*TP :\*\* TP 4 – Kubernetes  




\## 1. Objectifs du TP



\- Créer un cluster Kubernetes avec Kind.

\- Comprendre l'architecture Kubernetes.

\- Manipuler les Pods.

\- Déployer une application avec Deployment.

\- Exposer l'application avec un Service.

\- Effectuer un Rolling Update et un Rollback.



\## 2. Partie A — Création du cluster



Création d'un cluster Kind composé d'un nœud Control Plane et de deux Workers.



Commande utilisée :



```powershell

kind create cluster --config kind-config.yaml

```



Résultat : cluster créé et nœuds vérifiés avec `kubectl get nodes -o wide`.



Capture : `captures/01-cluster.png`



\## 3. Partie B — Manipulation des Pods



Création et inspection d'un Pod nginx avec les commandes kubectl.



\- Création du Pod `web`.

\- Consultation des informations avec describe.

\- Consultation des logs.

\- Accès au conteneur avec exec.

\- Accès à nginx avec port-forward.

\- Suppression du Pod et passage au déclaratif.



Capture : `captures/02-pod.png`



\## 4. Partie C — Deployment et Service



Déploiement de l'application whoami avec trois réplicas.



Création d'un Service de type NodePort sur le port 30080.



Vérification de l'application avec :



```powershell

curl.exe http://localhost:30080

```



Test de l'auto-réparation et augmentation du nombre de réplicas à six.



Capture : `captures/03-deployment-service.png`



\## 5. Partie D — Rolling Update et Rollback



Mise à jour de l'image vers `traefik/whoami:v1.11`.



Simulation d'une erreur avec l'image inexistante `traefik/whoami:v9.99`.



Observation de l'état ImagePullBackOff puis retour à la version précédente avec :



```powershell

kubectl rollout undo deployment/whoami

```



Capture : `captures/04-rolling-update.png`



\## 6. Défi DNS



Test de résolution DNS du Service :



`whoami.default.svc.cluster.local`



Capture : `captures/05-dns.png`



\## 7. Conclusion



Ce TP nous a permis de comprendre les principaux mécanismes de Kubernetes : la gestion des Pods, l'utilisation des Deployments et Services, l'auto-réparation, les mises à jour progressives et le retour à une version précédente.



\## 8. Fichiers du projet



\- `kind-config.yaml`

\- `whoami.yaml`

\- `pod.yaml`

\- `rollout-history.txt`

\- `captures/`

\- `README.md`

