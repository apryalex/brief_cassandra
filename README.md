Projet Docker avec Cassandra, FastAPI, Streamlit et Docker Compose :

```markdown
# Projet Docker Cassandra, FastAPI, Streamlit

Ce projet consiste en une application qui utilise Cassandra pour stocker des données sur les restaurants et leurs inspections, et expose ces données via une API FastAPI et une interface utilisateur Streamlit.

## Prérequis

Assurez-vous d'avoir les éléments suivants installés sur votre système :

- Docker (version 24.0.6 ou supérieure)
- Docker Compose (version 1.29.2 ou supérieure)
- Git (pour cloner le dépôt du projet)

## Instructions d'installation

1. Clonez ce dépôt GitHub sur votre machine :

   ```bash
   git clone https://github.com/votre-utilisateur/votre-projet.git
   ```

2. Accédez au répertoire du projet :

   ```bash
   cd votre-projet
   ```

3. Construisez et lancez les conteneurs Docker à l'aide de Docker Compose :

   ```bash
   docker compose up -d
   ```

   Cela va créer et exécuter des conteneurs Docker pour Cassandra, FastAPI et Streamlit.

   
IMPORTANT   IMPORTANT  IMPORTANT IMPORTANT



   ```markdown
Après avoir exécuté `docker-compose up`, vous devrez obtenir l'adresse IP du conteneur Cassandra `cassandra-node1` en utilisant la commande suivante :

```bash
docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' cassandra-node1
```



Assurez-vous de copier cette adresse IP dans le fichier `app.py` de votre serveur pour initialiser la connexion à Cassandra. Voici un extrait du fichier `app.py` côté serveur avec l'adresse IP mise à jour :

```python
# Initialisez la connexion à Cassandra
cluster = Cluster(['172.24.0.3'])  # Remplacez '172.24.0.3' par l'adresse IP obtenue
session = cluster.connect('resto')  # Remplacez 'resto' par le nom de votre keyspace Cassandra
```

Veillez à utiliser l'adresse IP correcte que vous avez obtenue avec la commande `docker inspect` pour que votre serveur puisse se connecter au conteneur Cassandra correctement.
```

5. Une fois que les conteneurs sont en cours d'exécution, vous pouvez accéder à l'interface utilisateur Streamlit à l'adresse [http://localhost:8501](http://localhost:8501) dans votre navigateur.

## Utilisation de l'API FastAPI

L'API FastAPI est exposée à l'adresse [http://localhost:8000](http://localhost:8000). Vous pouvez interagir avec l'API en utilisant des requêtes HTTP. Voici un exemple de requête pour obtenir des données sur un restaurant par son ID :

```http
GET http://localhost:8000/api/restaurants/{restaurant_id}
```

## Maintenance et nettoyage

Pour arrêter et supprimer les conteneurs Docker, exécutez la commande suivante dans le répertoire du projet :

```bash
docker compose down
```







## Remarques

- Le fichier `docker-compose.yml` définit la configuration des conteneurs Docker, y compris les volumes et les ports exposés.
- Les fichiers `dockerfile` dans les répertoires `client` et `server` contiennent les instructions pour la création des images Docker pour Streamlit et FastAPI.
- Les fichiers `requirements.txt` dans les répertoires `client` et `server` spécifient les dépendances Python pour chaque composant.

Ce projet est fourni à titre d'exemple et peut être adapté à vos besoins spécifiques. Amusez-vous bien !
```


