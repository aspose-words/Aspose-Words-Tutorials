---
title: Travailler avec un modèle d'IA ouvert
linktitle: Travailler avec un modèle d'IA ouvert
second_title: API de traitement de documents Aspose.Words
description: Bénéficiez d'une synthèse efficace des documents à l'aide d'Aspose.Words pour .NET avec les puissants modèles d'OpenAI. Plongez dès maintenant dans ce guide complet.
weight: 10
url: /fr/net/ai-powered-document-processing/working-with-open-ai-model/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Travailler avec un modèle d'IA ouvert

## Introduction

Dans le monde numérique d'aujourd'hui, le contenu est roi. Que vous soyez étudiant, professionnel ou écrivain passionné, la capacité à manipuler, résumer et générer des documents de manière efficace est inestimable. C'est là qu'entre en jeu la bibliothèque Aspose.Words pour .NET, vous permettant de gérer des documents comme un pro. Dans ce didacticiel complet, nous verrons comment exploiter Aspose.Words en conjonction avec les modèles OpenAI pour résumer efficacement des documents. Prêt à libérer votre potentiel de gestion de documents ? Commençons !

## Prérequis

Avant de retrousser nos manches et de plonger dans le code, vous devez mettre en place quelques éléments essentiels :

### Cadre .NET
Assurez-vous que vous utilisez une version du framework .NET compatible avec Aspose.Words. En règle générale, .NET 5.0 et versions ultérieures devraient fonctionner parfaitement.

### Bibliothèque Aspose.Words pour .NET
 Vous devrez télécharger et installer la bibliothèque Aspose.Words. Vous pouvez la récupérer à partir de[ce lien](https://releases.aspose.com/words/net/).

### Clé API OpenAI
Pour intégrer les modèles de langage d'OpenAI pour la synthèse de documents, vous aurez besoin d'une clé API. Vous pouvez l'obtenir en vous inscrivant sur la plateforme OpenAI et en récupérant votre clé dans les paramètres de votre compte.

### IDE pour le développement
Disposer d’un environnement de développement intégré (IDE) tel que Visual Studio est idéal pour développer des applications .NET.

### Connaissances de base en programmation
Une compréhension fondamentale de C# et de la programmation orientée objet vous aidera à saisir les concepts plus facilement.

## Paquets d'importation

Maintenant que tout est en place, nous allons importer nos packages. Ouvrez votre projet Visual Studio et ajoutez les bibliothèques nécessaires. Voici comment procéder :

### Ajouter le package Aspose.Words

Vous pouvez ajouter le package Aspose.Words via le gestionnaire de packages NuGet. Voici comment procéder :
- Accédez à Outils -> Gestionnaire de packages NuGet -> Gérer les packages NuGet pour la solution.
- Recherchez « Aspose.Words » et cliquez sur Installer.

### Ajouter un environnement système

 Assurez-vous d'inclure le`System`espace de noms pour gérer les variables d’environnement :
```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```

### Ajouter Aspose.Words

Ensuite, incluez l’espace de noms Aspose.Words dans votre fichier C# :
```csharp
using Aspose.Words;
```

### Ajouter la bibliothèque OpenAI

Si vous utilisez une bibliothèque pour interagir avec OpenAI (comme un client REST), assurez-vous de l'inclure également. Vous devrez peut-être l'ajouter via NuGet de la même manière que nous avons ajouté Aspose.Words.

Maintenant que nous avons préparé notre environnement et importé les packages nécessaires, décomposons le processus de résumé du document étape par étape.

## Étape 1 : définissez vos répertoires de documents

Avant de pouvoir commencer à jouer avec vos documents, vous devez configurer les répertoires dans lesquels résideront vos documents et artefacts :

```csharp
// Votre répertoire de documents
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
// Votre répertoire d'objets
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```
 Cela rend votre code plus gérable, car vous pouvez facilement modifier les chemins si nécessaire.`MyDir` est l'endroit où vos documents d'entrée sont stockés, tandis que`ArtifactsDir` c'est là que vous enregistrerez les résumés générés.

## Étape 2 : Chargez vos documents

Ensuite, vous chargerez les documents que vous souhaitez résumer. C'est très simple avec Aspose.Words :

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```
Assurez-vous que les noms de vos documents correspondent à ceux que vous avez l'intention d'utiliser, sinon vous rencontrerez des erreurs !

## Étape 3 : obtenez votre clé API

Maintenant que vos documents sont chargés, il est temps de récupérer votre clé API OpenAI. Vous la récupérerez à partir des variables d'environnement pour la protéger :
```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
```
Il est essentiel de gérer votre clé API en toute sécurité pour tenir les utilisateurs non autorisés à distance.

## Étape 4 : Créer une instance de modèle OpenAI

Avec votre clé API prête, vous pouvez maintenant créer une instance du modèle OpenAI. Pour la synthèse du document, nous utiliserons le modèle Gpt4OMini :

```csharp
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```
Cette étape définit essentiellement la puissance cérébrale nécessaire pour résumer vos documents, vous donnant accès à un résumé piloté par l’IA.

## Étape 5 : Résumer un document unique

Commençons par résumer le premier document. C'est là que la magie opère :

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```
 Ici, nous utilisons le`Summarize` méthode du modèle. Le`SummaryLength.Short`le paramètre spécifie que nous voulons un bref résumé — parfait pour un aperçu rapide !

## Étape 6 : Résumer plusieurs documents

Vous vous sentez ambitieux ? Vous pouvez résumer plusieurs documents à la fois. Regardez comme c'est simple :

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```
Cette fonctionnalité est particulièrement pratique pour comparer plusieurs fichiers. Vous préparez peut-être une réunion et avez besoin de notes concises issues de plusieurs longs rapports. C'est votre nouveau meilleur ami !

## Conclusion

Résumer des documents avec Aspose.Words pour .NET et OpenAI n'est pas seulement une compétence utile, c'est aussi une véritable aide. En suivant ce guide, vous avez transformé un texte long et compliqué en résumés concis, ce qui vous a fait gagner du temps et des efforts. Que vous souhaitiez assurer la clarté pour vos clients ou préparer une présentation importante, vous disposez désormais des outils nécessaires pour le faire efficacement.

Alors, qu'attendez-vous ? Plongez dans vos documents en toute confiance et laissez la technologie faire le gros du travail !

## FAQ

### Qu'est-ce que Aspose.Words pour .NET ?  
Aspose.Words pour .NET est une bibliothèque puissante qui permet aux développeurs de créer, manipuler et convertir des documents par programmation.

### Ai-je besoin d'une clé API pour OpenAI ?  
Oui, vous devez disposer d'une clé API OpenAI valide pour accéder aux capacités de résumé à l'aide de leurs modèles.

### Puis-je résumer plusieurs documents à la fois ?  
Absolument ! Vous pouvez résumer plusieurs documents en un seul appel, ce qui est idéal pour les rapports détaillés.

### Comment installer Aspose.Words ?  
Vous pouvez l'installer via NuGet Package Manager dans Visual Studio en recherchant « Aspose.Words ».

### Existe-t-il un essai gratuit pour Aspose.Words ?  
 Oui, vous pouvez accéder à un essai gratuit d'Aspose.Words via leur[site web](https://releases.aspose.com/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
