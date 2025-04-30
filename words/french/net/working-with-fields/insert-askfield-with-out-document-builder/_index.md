---
"description": "Découvrez comment insérer un champ ASK sans utiliser Document Builder dans Aspose.Words pour .NET. Suivez ce guide pour enrichir vos documents Word de manière dynamique."
"linktitle": "Insérer ASKField sans Document Builder"
"second_title": "API de traitement de documents Aspose.Words"
"title": "Insérer ASKField sans Document Builder"
"url": "/fr/net/working-with-fields/insert-askfield-with-out-document-builder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Insérer ASKField sans Document Builder

## Introduction

Vous souhaitez maîtriser l'automatisation de vos documents avec Aspose.Words pour .NET ? Vous êtes au bon endroit ! Aujourd'hui, nous vous expliquons comment insérer un champ ASK sans utiliser de générateur de documents. Cette fonctionnalité est très pratique pour inviter les utilisateurs à saisir des informations spécifiques, rendant ainsi vos documents Word plus interactifs et dynamiques. Alors, plongeons-nous dans le vif du sujet et rendons vos documents plus intelligents !

## Prérequis

Avant de nous salir les mains avec du code, assurons-nous que tout est configuré :

1. Aspose.Words pour .NET : Assurez-vous d'avoir installé cette bibliothèque. Sinon, vous pouvez la télécharger depuis [ici](https://releases.aspose.com/words/net/).
2. Environnement de développement : un IDE adapté comme Visual Studio.
3. .NET Framework : assurez-vous que .NET Framework est installé.

Super ! Maintenant que tout est prêt, commençons par importer les espaces de noms nécessaires.

## Importer des espaces de noms

Tout d'abord, nous devons importer l'espace de noms Aspose.Words pour accéder à toutes les fonctionnalités d'Aspose.Words pour .NET. Voici comment procéder :

```csharp
using Aspose.Words;
using Aspose.Words.Fields;
```

## Étape 1 : Créer un nouveau document

Avant d'insérer un champ ASK, nous avons besoin d'un document. Voici comment créer un nouveau document :

```csharp
// Le chemin vers le répertoire des documents.
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Création de documents.
Document doc = new Document();
```

Cet extrait de code configure un nouveau document Word dans lequel nous ajouterons notre champ ASK.

## Étape 2 : Accéder au nœud Paragraphe

Dans un document Word, le contenu est organisé en nœuds. Nous devons accéder au premier nœud de paragraphe où nous allons insérer notre champ « ASK » :

```csharp
Paragraph para = (Paragraph)doc.GetChild(NodeType.Paragraph, 0, true);
```

Cette ligne de code récupère le premier paragraphe du document, prêt pour notre insertion de champ ASK.

## Étape 3 : Insérer le champ ASK

Passons maintenant à l'étape principale : l'insertion du champ « Demander ». Ce champ invitera l'utilisateur à saisir une information à l'ouverture du document.

```csharp
// Insérez le champ ASK.
FieldAsk field = (FieldAsk)para.AppendField(FieldType.FieldAsk, false);
```

Ici, nous ajoutons un champ « ASK » au paragraphe. Simple, non ?

## Étape 4 : Configurer le champ ASK

Nous devons définir certaines propriétés pour définir le comportement du champ « ASK ». Configurons le nom du signet, le texte de l'invite, la réponse par défaut et le comportement du publipostage :

```csharp
field.BookmarkName = "Test1";
field.PromptText = "Please enter your response:";
field.DefaultResponse = "Default response";
field.PromptOnceOnMailMerge = true;
```

- BookmarkName : un identifiant unique pour le champ ASK.
- PromptText : le texte qui invite l'utilisateur à effectuer une saisie.
- DefaultResponse : la réponse pré-remplie que l'utilisateur peut modifier.
- PromptOnceOnMailMerge : détermine si l’invite n’apparaît qu’une seule fois lors d’un publipostage.

## Étape 5 : Mettre à jour le champ

Après avoir configuré le champ ASK, nous devons le mettre à jour pour garantir que tous les paramètres sont appliqués correctement :

```csharp
field.Update();
```

Cette commande garantit que notre champ ASK est prêt et correctement configuré dans le document.

## Étape 6 : Enregistrer le document

Enfin, enregistrons le document dans notre répertoire spécifié :

```csharp
doc.Save(dataDir + "InsertionChampASKSansDocumentBuilder.docx");
```

Cette ligne enregistre le document avec le champ « Demander ». Et voilà ! Votre document est désormais doté d'un champ « Demander » dynamique !

## Conclusion

Félicitations ! Vous venez d'ajouter un champ ASK à un document Word avec Aspose.Words pour .NET sans le Générateur de documents. Cette fonctionnalité peut considérablement améliorer l'interaction utilisateur avec vos documents, les rendant plus flexibles et conviviaux. Continuez à expérimenter avec différents champs et propriétés pour exploiter tout le potentiel d'Aspose.Words. Bon codage !

## FAQ

### Qu'est-ce qu'un champ ASK dans Aspose.Words ?
Un champ ASK dans Aspose.Words est un champ qui invite l'utilisateur à effectuer une saisie spécifique lorsque le document est ouvert, permettant une saisie de données dynamique.

### Puis-je utiliser plusieurs champs ASK dans un seul document ?
Oui, vous pouvez insérer plusieurs champs ASK dans un document, chacun avec des invites et des réponses uniques.

### Quel est le but de la `PromptOnceOnMailMerge` propriété?
Le `PromptOnceOnMailMerge` la propriété détermine si l'invite ASK apparaît une seule fois lors d'une opération de publipostage ou à chaque fois.

### Dois-je mettre à jour le champ ASK après avoir défini ses propriétés ?
Oui, la mise à jour du champ ASK garantit que toutes les propriétés sont correctement appliquées et que le champ fonctionne comme prévu.

### Puis-je personnaliser le texte de l’invite et la réponse par défaut ?
Absolument ! Vous pouvez personnaliser le texte de l'invite et les réponses par défaut pour adapter le champ « Demander » à vos besoins spécifiques.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}