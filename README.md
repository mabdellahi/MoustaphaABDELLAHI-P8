**PROJET 8: Déployer un modèle dans le cloud**

Moustapha Abdellahi

Enoncé Openclassrooms

**Mission**

Vous êtes donc chargé de développer dans un environnement Big Data une première chaîne de traitement des données qui comprendra le preprocessing et une étape de réduction de dimension.

Il n’est pas nécessaire d’entraîner un modèle pour le moment.

L’important est de mettre en place les premières briques de traitement qui serviront lorsqu’il faudra passer à l’échelle en termes de volume de données !

**Contraintes**

Vous devrez tenir compte dans vos développements du fait que le volume de données va augmenter très rapidement après la livraison de ce projet.

Vous développerez donc des scripts en Pyspark et utiliserez par exemple le cloud AWS pour profiter d’une architecture Big Data (EC2, S3, IAM), basée sur un serveur EC2 Linux.

La mise en œuvre d’une architecture Big Data sous (par exemple) AWS peut nécessiter une configuration serveur plus puissante que celle proposée gratuitement (EC2 = t2.micro, 1 Go RAM, 8 Go disque serveur).


**Livrables attendus**

Un notebook sur le cloud contenant les scripts en Pyspark exécutables (le preprocessing et une étape de réduction de dimension).

Les images du jeu de données initial ainsi que la sortie de la réduction de dimension (une matrice écrite sur un fichier CSV ou autre) disponible dans un espace de stockage sur le cloud.

Un support de présentation pour la soutenance, présentant :

les différentes briques d'architecture choisies sur le cloud

leur rôle dans l’architecture Big Data

les étapes de la chaîne de traitement.

**Mon approche**

A cause des ressources limitées et pour la preuve-de-concept, j'ai dû sélectionner 5 catégories de fruits dans le jeux de données et choisir à chaque fois deux images random, total = 10 images. Ensuite, je les ai uploadé sur mon serveur S3. Dans l'étape de set-up, j'ai hébergé ce code dans un serveur EC2 payant (t2.medium, 4 Go RAM, 30 Go disque serveur, OS = Linux 18.x, 64-bit). L'étape d'installation de l'environement PySpark était vraiment compliquée.

**Récapitulation des différents étapes d'installation :**

Sélectionner la bonne instance EC2, avec la bonne mémoire et suffisamment de stockage
Créer un groupe de sécurité (configurer ssh particulièrement)
Setup la connextion ssh, attention au username = "ec2-user" ou "ubuntu"
Créer un bucket S3 (et setup les autorisations/droits en .json, grâce au générateur de stratégie)
Créer un AMI user et bien garder les clés access et private
Dans le serveur EC2, tout en ligne de commande
- Télécharger puis bash anaconda, https://repo.anaconda.com/archive/Anaconda3-2021.05-Linux-x86_64.sh, faire très attention aux versions,
- Installer Java sudo apt-get install default-jre, faire très attention aux versions
- Installer Scala sudo apt-get install scala
- Télécharger puis décompresser spark-3.2.1-hadoop-3.3.2, faire attention aux versions
- Gérer les credentials jupyter
- Installer awscli : sudo apt install awscli
- Gérer les crédentials du S3 via les clés données par le AMI user
Ajouter tous les packages nécessaires (tensorflow, py4j, boto3, ...)
