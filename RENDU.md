# Rendu — Atelier Kubernetes

> Complétez ce fichier au fil de l'atelier, puis faites un commit et un push (voir la section « Rendu » du README).

**Nom / Prénom :sarsoura camelia**
**Groupe :**

---

## Exercice 1 — Cluster

1. Combien de nœuds affiche `kubectl get nodes` ? Quel est le rôle de chacun ?
   > La commande affiche 3 nœuds :
- k3d-lab-server-0 : nœud manager, il gère le cluster.
- k3d-lab-agent-0 : nœud worker, il exécute les applications.
- k3d-lab-agent-1 : nœud worker, il exécute également les applications.
 
2. Que montre `docker ps` ? Qu'est-ce qu'un « nœud » dans k3d, concrètement ?
   > docker ps affiche les conteneurs Docker en cours d'exécution dans le cluster.
   > Dans k3d, un nœud est concrètement un conteneur Docker qui représente une machine du cluster Kubernetes. Il peut gérer le cluster ou exécuter des applications.

## Exercice 2 — Premier déploiement

3. Quels objets Kubernetes ont été créés par `kubectl create deployment` ? (indice : `kubectl get all`)
   >Deployment : gère le déploiement de l'application.
ReplicaSet : veille à maintenir le nombre de pods souhaité.
Pod : contient le conteneur Nginx qui exécute l'application.
4. Vous avez supprimé le pod `web-...` : que s'est-il passé, et pourquoi ?
   >un pod a été recrée automatiquement

## Exercice 3 — Modifier un conteneur en direct

5. Après suppression du pod, votre message « Bienvenue... » a-t-il survécu ? Pourquoi ?
   > Non, le message n'a pas survécu, car il était enregistrer uniquement dans le conteneur supprimé.
6. Pourquoi le `port-forward` a-t-il cessé de fonctionner après la suppression du pod ?
   > Le port-forward a cessé de fonctionner car il était connecté à l'ancien pod, qui a été supprimé.

## Exercice 4 — Déclaratif

7. Quelle différence entre `kubectl create` et `kubectl apply` ?
   >."kubectl create" crée un objet Kubernetes alors que "kubectl apply" crée ou met à jour un objet à partir d'un fichier YAML.
8. À quoi sert le `selector` d'un Service ? Que se passe-t-il s'il ne correspond à aucun pod ?
   >.Le selector permet au Service de trouver les pods auxquels il doit envoyer le trafic. S'il ne correspond à aucun pod, le Service ne peut envoyer le trafic à aucune application

## Exercice 5 — Scaling & mises à jour

9. Sur quels nœuds se trouvent vos 3 réplicas ? Collez la sortie de `kubectl get pods -l app=site -o wide`.
   ```Les 3 réplicas sont répartis sur les trois nœuds :
                k3d-lab-agent-0
                k3d-lab-agent-1
                k3d-lab-server-0
       NAME                    READY   STATUS    RESTARTS   AGE   IP          NODE
       site-5cc664db9c-ptqmg   1/1     Running   0          99s   10.42.0.6   k3d-lab-agent-0
       site-5cc664db9c-t5k4x   1/1     Running   0          93s   10.42.2.7   k3d-lab-agent-1
       site-5cc664db9c-tcttf   1/1     Running   0          85s   10.42.1.8   k3d-lab-server-0```
10. Avec l'image `nginx:9.99`, quel statut avait le pod ? Quelle commande vous a donné la cause ?
    >
11. Pendant la panne, le site restait-il accessible ? Pourquoi ?
    >

## Exercice 6 — Portainer & Mario

12. URL publique de votre Mario :
    >
13. Retrouvez le Deployment `mario` en ligne de commande. Portainer et `kubectl` parlent-ils au même composant ? Lequel ?
    >

## Bonus (facultatif)

14. Bonus réalisés et remarques :
    >

---

**Score obtenu avec `./scripts/check.sh` :** ... / ...
