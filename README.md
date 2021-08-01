# Construire un modèle de scoring pour "Prêt à dépenser"

Données financières + Classification par apprentissage automatique = Remboursement prédit du prêt

## Informations générales

"Prêt à dépenser" est une société financière qui propose des crédits à la consommation pour des personnes ayant peu ou pas d'historique de prêt.

## Objectifs

Pour accorder un crédit à la consommation, l’entreprise calcule la probabilité qu’un client le rembourse, ou non. Elle souhaite donc développer un algorithme de scoring pour aider à décider si un prêt peut être accordé à un client.

Les chargés de relation client seront les utilisateurs du modèle de scoring. Puisqu’ils s’adressent aux clients, ils ont besoin que notre modèle soit facilement interprétable. Les chargés de relation souhaitent, en plus, disposer d’une mesure de l’importance des variables qui ont poussé le modèle à donner cette probabilité à un client.

### Activité

Construire un modèle du scoring pour savoir si un prêt sera remboursé ou non.

### Données

1) Établir un lien entre les ensembles de données.
2) Avec cette compréhension, utilisez les ensembles de données pour prédire le remboursement des prêts.

## Ensembles de données

### application_{train|test}.csv

Il s'agit de la table principale, divisé en deux fichiers pour Train (avec TARGET) et Test (sans TARGET). Données statiques pour toutes les applications. Une ligne représente un prêt dans notre échantillon de données.

### bureau.csv

Tous les crédits précédents du client fournis par d'autres institutions financières qui ont été rapportés au Credit Bureau (pour les clients qui ont un prêt dans notre échantillon). Pour chaque prêt dans notre échantillon, il y a autant de lignes que le nombre de crédits que le client avait dans le Credit Bureau avant la date de la demande.

### bureau_balance.csv

Soldes mensuels des crédits précédents dans Credit Bureau. Cette table comporte une ligne pour chaque mois de l'historique de chaque crédit précédent déclaré au Credit Bureau - c'est-à-dire que la table comporte ( nombre de prêts dans l'échantillon x nombre de crédits précédents relatifs x nombre de mois où nous avons un historique observable pour les crédits précédents) lignes.

### POS_CASH_balance.csv

Instantanés des soldes mensuels des prêts POS (Point Of Sales, Point De Vente en français) et cash précédents que le demandeur a eu avec Prêt à dépenser. Cette table comporte une ligne pour chaque mois de l'historique de chaque crédit précédent au Prêt à dépenser (crédit à la consommation et prêts en espèces) lié aux prêts de notre échantillon - c'est-à-dire que la table comporte (nombre de prêts dans l'échantillon x nombre de crédits précédents relatifs x nombre de mois dans lesquels nous avons un historique observable pour les crédits précédents) lignes.

### credit_card_balance.csv

Instantanés des soldes mensuels des cartes de crédit précédentes que le demandeur possède auprès de Prêt à dépenser. Cette table comporte une ligne pour chaque mois de l'historique de chaque crédit précédent chez Prêt à dépenser (crédit à la consommation et prêts de trésorerie) lié aux prêts de notre échantillon - c'est-à-dire que la table comporte (#prêts dans l'échantillon x nombre de cartes de crédit précédentes relatives x nombre de mois où nous avons un historique observable pour la carte de crédit précédente) lignes.

### previous_application.csv

Toutes les demandes précédentes de crédit immobilier des clients qui ont des prêts dans notre échantillon. Il y a une ligne pour chaque demande précédente liée aux prêts dans notre échantillon de données.

### installments_payments.csv

Historique des remboursements pour les crédits déboursés précédemment dans Prêt à dépenser liés aux prêts de notre échantillon. Il y a :
a) une ligne pour chaque paiement effectué et
b) une ligne pour chaque paiement manqué.
Une ligne est équivalente à un paiement d'un versement OU à un versement correspondant à un paiement d'un crédit Prêt à dépenser précédent lié aux prêts de notre échantillon.

### HomeCredit_columns_description.csv

Ce fichier contient les descriptions des colonnes dans les différents fichiers de données.
