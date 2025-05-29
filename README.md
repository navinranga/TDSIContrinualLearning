# Apprentissage Continu pour la Segmentation des IRM des Muscles de la Jambe

Ce projet explore l'utilisation du deep learning et de l'apprentissage continu pour la segmentation automatique des muscles de la jambe à partir d’images IRM. Deux approches sont comparées : **Replay** et **Elastic Weight Consolidation (EwC)**.

## Cloner le dépôt

Pour récupérer le projet en local :

    git clone https://github.com/navinranga/TDSIContrinualLearning.git
    cd TDSIContrinualLearning


## Structure du projet

### `unet_continual_learning_replay/`

Contient le pipeline de prétraitement, l'entraînement du modèle U-Net de base, ainsi que la méthode de **continual learning par replay**.

- `notebook_unet_replay.ipynb` : Notebook Jupyter du prétraitement jusqu’au modèle avec replay.
- `best_model/` : (non présent) Devrait contenir le meilleur modèle U-Net sans apprentissage continu.
- `data/` : (non présent) Dossier attendu pour les données brutes (DICOM).
- `processed_data/` : (vide) Données traitées au format NumPy.
- `exported_data/` : (vide) Format intermédiaire pour éviter le prétraitement répété.
- `best_model.pth` : (non présent) Modèle U-Net de base entraîné.
- `best_model_replay.pth` : (non présent) Modèle final entraîné avec la méthode de replay.

### `continual_learning_incremental_ewc/`

Contient l'approche basée sur la **méthode EWC (Elastic Weight Consolidation)**, utilisant des images en sous-résolution pour des entraînements rapides.

- `Notebook_continual_learning_ewc.ipynb` : Notebook Jupyter décrivant l'apprentissage incrémental avec EWC.
- `processed_data/` : (vide) Données en sous-résolution après prétraitement.
- `best_model_continual_learning.pth` : (non présent) Modèle final après EWC.

## Méthodologie

Le projet repose sur :

- **Prétraitement des IRM** : Normalisation, redimensionnement, et augmentation des données.
- **U-Net** : Architecture utilisée pour la segmentation pixel-par-pixel des muscles.
- **Replay** : Méthode où les anciennes données sont mélangées aux nouvelles pour limiter l'oubli catastrophique.
- **EWC** : Méthode qui pénalise les changements sur les paramètres critiques à la performance passée.

## Résultats obtenus

- Dice score > 0.89 pour le modèle U-Net de base.
- Amélioration significative avec EWC (jusqu’à 0.94), démontrant une meilleure adaptation avec conservation des acquis.

## Remarques

> Les fichiers `.pth` et les dossiers de données ne sont pas inclus dans ce dépôt. Seuls les notebooks Jupyter sont disponibles pour la démonstration et l’expérimentation du code.

## Auteurs

- Evan Gossard
- Louis Lafontaine
- Navin Ranga  
- Encadrant : Pr Thomas GRENIER
*(INSA Lyon – PTI TDSI 2024)*

## Références

- Ronneberger et al., "U-Net: Convolutional Networks for Biomedical Image Segmentation", MICCAI 2015.
- Kirkpatrick et al., "Overcoming Catastrophic Forgetting", arXiv 2017.
- MONAI Project: [Active Learning](https://github.com/Project-MONAI/MONAILabel/wiki/Active-Learning)

