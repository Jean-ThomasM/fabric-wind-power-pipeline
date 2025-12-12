# Wind Power Analytics - Microsoft Fabric Pipeline

Pipeline end-to-end sur Microsoft Fabric pour ingérer, transformer et analyser la production d'énergie éolienne en architecture Medallion (Bronze/Silver/Gold).

## Sommaire
- Aperçu rapide
- Architecture
- Flux de données
- Contenu du dépôt
- Mise en route
- Statut & jalons

## Aperçu rapide
- Collecte automatisée de fichiers CSV depuis GitHub vers le Lakehouse (zone Bronze).
- Nettoyage et enrichissement via notebooks PySpark/SQL pour constituer Silver puis Gold.
- Modèle dimensionnel de type étoile exposé au modèle sémantique Power BI.
- Orchestration via Data Pipeline pour automatiser ingestion et transformations.
- Visualisation des indicateurs éoliens dans Power BI avec mesures DAX.

## Architecture
```
GitHub (CSV) -> Bronze (Delta) -> Silver (Delta) -> Gold (Delta) -> Semantic Model -> Power BI
```
Technologies : Microsoft Fabric, Delta Lake, PySpark, SQL, Power BI, DAX.

## Flux de données
1. Ingestion : récupération des jeux de données CSV hébergés sur GitHub.
2. Bronze : stockage brut dans le Lakehouse en tables Delta.
3. Silver : normalisation, typage et nettoyage via PySpark/SQL.
4. Gold : agrégations et modèles métiers (schéma en étoile) prêts pour l'analyse.
5. Sémantique & BI : modèle Power BI, mesures DAX et rapports.
6. Orchestration : pipeline Fabric qui enchaîne ingestion, transformations et rafraîchissements.

## Contenu du dépôt
- `notebooks/bronze/NB_Get_Daily_Data_Python (1)(2).ipynb` : ingestion quotidienne vers Bronze.
- `notebooks/silver/NB_Bronze_To_Silver_Transformations_Python.ipynb` : transformations PySpark Bronze -> Silver.
- `notebooks/silver/NB_Bronze_To_Silver_Transformations_SQL.ipynb` : transformations équivalentes en SQL.
- `notebooks/gold/NB_Silver_To_Gold_Transformations_Python.ipynb` : agrégations métier vers Gold.
- `documentation/` : documentation complémentaire (à compléter).
- `screenshots/` : captures d'écran Fabric / Power BI (à compléter).
- `grab_temp/` : artefacts temporaires.

## Mise en route (Fabric)
1. Cloner le dépôt puis ouvrir un Workspace Microsoft Fabric.
2. Créer un Lakehouse et configurer la connexion au dépôt GitHub source (CSV).
3. Importer les notebooks Bronze/Silver/Gold ci-dessus dans le workspace.
4. Configurer un Data Pipeline qui exécute les notebooks dans l'ordre Bronze -> Silver -> Gold, puis rafraîchit le modèle Power BI.
5. Publier ou rafraîchir le rapport Power BI connecté au modèle sémantique Gold.

## Statut & jalons
- Statut actuel : 🔨 en cours de développement.
- Prochaines étapes possibles : automatiser le déclenchement quotidien, améliorer les rapports.

---

Projet réalisé dans le cadre d'une formation sur Microsoft Fabric  
Date de début : 16 novembre 2025
