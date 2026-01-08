---
"date": "2025-03-29"
"description": "Apprenez à optimiser l'enregistrement de vos documents avec Aspose.Words pour Python grâce au format de flux XAML et aux rappels de progression. Améliorez l'efficacité de la gestion de vos documents."
"title": "Optimisation de l'enregistrement de documents dans Python – Flux XAML et rappels de progression Aspose.Words"
"url": "/fr/python-net/performance-optimization/python-aspose-words-xaml-flow-progress-callbacks/"
"weight": 1
---
{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}
# Comment optimiser l'enregistrement de documents en Python avec Aspose.Words : flux XAML et rappels de progression

## Introduction

Vous cherchez à gérer efficacement la conversion de vos documents avec Python ? Vous avez des difficultés à gérer les images et à suivre la progression de l'enregistrement ? Ce tutoriel vous guide pour optimiser l'enregistrement de vos documents avec Aspose.Words pour Python, en se concentrant sur deux fonctionnalités puissantes : `XamlFlowSaveOptions` avec rappel de progression de l'enregistrement du dossier d'images et du document.

Ce guide complet est parfait pour les développeurs qui cherchent à améliorer leurs flux de travail de traitement de documents à l'aide de la bibliothèque Aspose.Words.

**Ce que vous apprendrez :**
- Comment enregistrer un document au format de flux XAML tout en gérant les ressources d'image.
- Implémentation de rappels de progression lors de l'enregistrement du document pour éviter les opérations longues.
- Configuration et configuration d'Aspose.Words pour Python dans votre environnement de développement.
- Applications concrètes de ces fonctionnalités dans les systèmes de gestion de documents.

Plongeons dans les prérequis avant de commencer à coder !

## Prérequis

Avant de commencer, assurez-vous d’avoir les éléments suivants :

### Bibliothèques et versions requises
- **Aspose.Words pour Python**: Assurez-vous d'avoir la version 23.3 ou ultérieure.
- **Python**:La version 3.6 ou supérieure est recommandée.

### Configuration requise pour l'environnement
- Un éditeur de code comme VSCode ou PyCharm.
- Connaissances de base de la programmation Python.

### Prérequis en matière de connaissances
- Connaissance des concepts de traitement de documents.
- Compréhension de la gestion des fichiers et de la gestion des répertoires en Python.

## Configuration d'Aspose.Words pour Python

Pour commencer à utiliser Aspose.Words, vous devez l'installer via PIP. Ouvrez votre terminal ou votre invite de commande et exécutez :

```bash
pip install aspose-words
```

### Étapes d'acquisition de licence
1. **Essai gratuit**: Accéder à une licence temporaire [ici](https://purchase.aspose.com/temporary-license/) à des fins de test.
2. **Achat**: Pour une utilisation à long terme, achetez une licence [ici](https://purchase.aspose.com/buy).
3. **Initialisation et configuration de base**:
   - Chargez votre document en utilisant `aw.Document()`.
   - Configurez les options de sauvegarde selon vos besoins.

## Guide de mise en œuvre

Cette section vous guidera à travers la mise en œuvre des deux principales fonctionnalités de ce didacticiel : XamlFlowSaveOptions avec dossier d'images et rappel de progression de l'enregistrement du document.

### Fonctionnalité 1 : XamlFlowSaveOptions avec dossier d'images

#### Aperçu
Cette fonctionnalité vous permet d'enregistrer un document au format de flux XAML tout en spécifiant un dossier d'images et un alias. Elle est idéale pour gérer efficacement les documents volumineux avec images intégrées.

#### Étapes de mise en œuvre

##### Étape 1 : Importer les bibliothèques nécessaires
```python
import os
from datetime import datetime
import aspose.words as aw
```

##### Étape 2 : définir la classe de rappel ImageUriPrinter
Cette classe compte et redirige les flux d'images vers un dossier d'alias spécifié pendant la conversion.

```python
class ExXamlFlowSaveOptionsImageFolder:
    class ImageUriPrinter(aw.saving.IImageSavingCallback):
        """Counts and prints filenames of images while their parent document is converted to flow-form .xaml."""
        
        def __init__(self, images_folder_alias: str):
            self.images_folder_alias = images_folder_alias
            self.resources = []  # type : Liste[str]

        def image_saving(self, args: aw.saving.ImageSavingArgs):
            self.resources.append(args.image_file_name)
            with open(f"{self.images_folder_alias}/{args.image_file_name}", "wb") as image_stream:
                args.image_stream = image_stream
            args.keep_image_stream_open = False

    def test_image_folder(self):
        YOUR_DOCUMENT_DIRECTORY = 'YOUR_DOCUMENT_DIRECTORY'
        YOUR_OUTPUT_DIRECTORY = 'YOUR_OUTPUT_DIRECTORY'

        doc = aw.Document(f"{YOUR_DOCUMENT_DIRECTORY}/Rendering.docx")
        callback = self.ImageUriPrinter(YOUR_OUTPUT_DIRECTORY + "XamlFlowImageFolderAlias")

        options = aw.saving.XamlFlowSaveOptions()
        options.images_folder = YOUR_OUTPUT_DIRECTORY + "XamlFlowImageFolder"
        options.images_folder_alias = YOUR_OUTPUT_DIRECTORY + "XamlFlowImageFolderAlias"
        options.image_saving_callback = callback

        os.makedirs(options.images_folder_alias, exist_ok=True)
        
        doc.save(f"{YOUR_OUTPUT_DIRECTORY}/XamlFlowSaveOptions.image_folder.xaml", options)

        for resource in callback.resources:
            print(f"{callback.images_folder_alias}/{resource}")
```
**Options de configuration clés :**
- `images_folder`: Spécifie le répertoire dans lequel les images sont enregistrées.
- `images_folder_alias`: Définit un chemin d'alias utilisé lors de la conversion du document.

##### Conseils de dépannage
- Assurez-vous que tous les répertoires existent avant d'exécuter le code pour éviter les erreurs de fichier introuvable.
- Vérifiez les autorisations d’écriture dans votre répertoire de sortie.

### Fonctionnalité 2 : Rappel de progression de l'enregistrement du document

#### Aperçu
Cette fonctionnalité gère le processus de sauvegarde en utilisant un rappel de progression, vous permettant d'annuler les opérations de sauvegarde de longue durée.

#### Étapes de mise en œuvre

##### Étape 1 : définir la classe SavingProgressCallback
La classe surveille la durée d'enregistrement du document et l'annule si elle dépasse une limite de temps spécifiée.

```python
class ExXamlFlowSaveOptionsProgressCallback:
    class SavingProgressCallback(aw.saving.IDocumentSavingCallback):
        """Saving progress callback. Cancel document saving after the 'max_duration' seconds."""
        
        def __init__(self):
            self.saving_started_at = datetime.now()
            self.max_duration = 0.01  # Durée maximale autorisée en sec.

        def notify(self, args: aw.saving.DocumentSavingArgs):
            canceled_at = datetime.now()
            elapsed_seconds = (canceled_at - self.saving_started_at).total_seconds()
            if elapsed_seconds > self.max_duration:
                raise OperationCanceledException(f"estimated_progress = {args.estimated_progress}; canceled_at = {canceled_at}")

    def test_progress_callback(self):
        YOUR_DOCUMENT_DIRECTORY = 'YOUR_DOCUMENT_DIRECTORY'
        YOUR_OUTPUT_DIRECTORY = 'YOUR_OUTPUT_DIRECTORY'

        parameters = [
            (aw.SaveFormat.XAML_FLOW, "xamlflow"),
            (aw.SaveFormat.XAML_FLOW_PACK, "xamlflowpack"),
        ]

        for save_format, ext in parameters:
            doc = aw.Document(f"{YOUR_DOCUMENT_DIRECTORY}/Big document.docx")
            save_options = aw.saving.XamlFlowSaveOptions(save_format)
            save_options.progress_callback = self.SavingProgressCallback()

            try:
                doc.save(f"{YOUR_OUTPUT_DIRECTORY}/XamlFlowSaveOptions.progress_callback.{ext}", save_options)
            except OperationCanceledException as e:
                print(e)
```
**Options de configuration clés :**
- `save_format`: Choisissez entre XAML_FLOW et XAML_FLOW_PACK.
- `progress_callback`: Surveille la progression de l'enregistrement pour gérer les opérations longues.

##### Conseils de dépannage
- Ajuster `max_duration` en fonction de la taille et de la complexité du document.
- Gérez les exceptions avec élégance pour fournir des messages d'erreur informatifs.

## Applications pratiques

Voici quelques cas d’utilisation réels pour ces fonctionnalités :
1. **Systèmes de gestion de documents**: Gérez efficacement les documents volumineux avec des images intégrées en spécifiant des dossiers d'images, améliorant ainsi les performances et l'organisation.
2. **Outils de reporting automatisés**:Utilisez des rappels de progression pour garantir que les rapports sont générés dans des délais acceptables, améliorant ainsi l'expérience utilisateur.
3. **Réseaux de distribution de contenu**:Rationalisez la conversion des documents pour la distribution Web tout en gérant efficacement les ressources.

## Considérations relatives aux performances

Pour optimiser les performances lors de l'utilisation d'Aspose.Words avec Python :
- **Gestion de la mémoire**:Surveillez l’utilisation des ressources et gérez efficacement la mémoire en supprimant les objets après utilisation.
- **Opérations d'E/S de fichiers**:Réduisez les opérations de lecture/écriture de fichiers pour améliorer la vitesse.
- **Traitement par lots**:Traitez les documents par lots lorsque cela est possible pour réduire les frais généraux.

## Conclusion

Dans ce tutoriel, nous avons exploré comment optimiser l'enregistrement de documents avec Aspose.Words pour Python, grâce au flux XAML et aux rappels de progression. En implémentant ces fonctionnalités, vous pouvez améliorer l'efficacité de vos workflows de traitement de documents, gérer efficacement les ressources et garantir la ponctualité des opérations.
{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}