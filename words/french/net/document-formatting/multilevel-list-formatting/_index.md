---
title: Formatage de liste à plusieurs niveaux dans un document Word
linktitle: Formatage de liste à plusieurs niveaux dans un document Word
second_title: API de traitement de documents Aspose.Words
description: Apprenez à maîtriser la mise en forme de listes à plusieurs niveaux dans des documents Word à l'aide d'Aspose.Words pour .NET grâce à notre guide étape par étape. Améliorez la structure de vos documents sans effort.
weight: 10
url: /fr/net/document-formatting/multilevel-list-formatting/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Formatage de liste à plusieurs niveaux dans un document Word

## Introduction

Si vous êtes un développeur cherchant à automatiser la création et la mise en forme de documents Word, Aspose.Words pour .NET est une solution révolutionnaire. Aujourd'hui, nous allons découvrir comment vous pouvez maîtriser la mise en forme de listes à plusieurs niveaux à l'aide de cette puissante bibliothèque. Que vous créiez des documents structurés, que vous rédigiez des rapports ou que vous génériez de la documentation technique, les listes à plusieurs niveaux peuvent améliorer la lisibilité et l'organisation de votre contenu.

## Prérequis

Avant de passer aux détails, assurons-nous que vous disposez de tout ce dont vous avez besoin pour suivre ce tutoriel.

1. Environnement de développement : assurez-vous de disposer d’un environnement de développement. Visual Studio est un excellent choix.
2.  Aspose.Words pour .NET : Téléchargez et installez la bibliothèque Aspose.Words pour .NET. Vous pouvez l'obtenir[ici](https://releases.aspose.com/words/net/).
3.  Permis : obtenez un permis temporaire si vous n'en avez pas un complet. Obtenez-le[ici](https://purchase.aspose.com/temporary-license/).
4. Connaissances de base en C# : une connaissance de C# et du framework .NET sera bénéfique.

## Importer des espaces de noms

Pour utiliser Aspose.Words pour .NET dans votre projet, vous devez importer les espaces de noms nécessaires. Voici comment procéder :

```csharp
using Aspose.Words;
using Aspose.Words.Lists;
```

## Étape 1 : Initialisez votre document et votre générateur

Tout d'abord, créons un nouveau document Word et initialisons DocumentBuilder. La classe DocumentBuilder fournit des méthodes pour insérer du contenu dans le document.

```csharp
// Le chemin vers le répertoire des documents.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Étape 2 : Appliquer la numérotation par défaut

 Pour commencer avec une liste numérotée, vous utilisez le`ApplyNumberDefault` méthode. Cela définit le formatage par défaut de la liste numérotée.

```csharp
builder.ListFormat.ApplyNumberDefault();
builder.Writeln("Item 1");
builder.Writeln("Item 2");
```

 Dans ces lignes,`ApplyNumberDefault` commence la liste numérotée, et`Writeln` ajoute des éléments à la liste.

## Étape 3 : Indentation pour les sous-niveaux

 Ensuite, pour créer des sous-niveaux dans votre liste, vous utilisez le`ListIndent` méthode. Cette méthode indente l'élément de la liste, le transformant en sous-niveau de l'élément précédent.

```csharp
builder.ListFormat.ListIndent();
builder.Writeln("Item 2.1");
builder.Writeln("Item 2.2");
```

Cet extrait de code met en retrait les éléments, créant ainsi une liste de deuxième niveau.

## Étape 4 : Indentation supplémentaire pour des niveaux plus profonds

Vous pouvez continuer à créer des indentations pour créer des niveaux plus profonds dans votre liste. Ici, nous allons créer un troisième niveau.

```csharp
builder.ListFormat.ListIndent();
builder.Writeln("Item 2.2.1");
builder.Writeln("Item 2.2.2");
```

Vous disposez désormais d'une liste de troisième niveau sous « Élément 2.2 ».

## Étape 5 : Augmenter le retrait pour revenir à des niveaux plus élevés

 Pour revenir à un niveau supérieur, utilisez le`ListOutdent` méthode. Cela ramène l'élément au niveau de liste précédent.

```csharp
builder.ListFormat.ListOutdent();
builder.Writeln("Item 2.3");
```

Cela ramène « Article 2.3 » au deuxième niveau.

## Étape 6 : Supprimer la numérotation

Une fois que vous avez terminé votre liste, vous pouvez supprimer la numérotation pour continuer avec du texte normal ou un autre type de formatage.

```csharp
builder.ListFormat.ListOutdent();
builder.Writeln("Item 3");
builder.ListFormat.RemoveNumbers();
```

Cet extrait de code complète la liste et arrête la numérotation.

## Étape 7 : Enregistrez votre document

Enfin, enregistrez le document dans le répertoire souhaité.

```csharp
doc.Save(dataDir + "DocumentFormatting.MultilevelListFormatting.docx");
```

Cela enregistre votre document magnifiquement formaté avec des listes à plusieurs niveaux.

## Conclusion

Et voilà ! Vous avez réussi à créer une liste à plusieurs niveaux dans un document Word à l'aide d'Aspose.Words pour .NET. Cette puissante bibliothèque vous permet d'automatiser facilement des tâches complexes de mise en forme de documents. N'oubliez pas que la maîtrise de ces outils permet non seulement de gagner du temps, mais également de garantir la cohérence et le professionnalisme de votre processus de génération de documents.

## FAQ

### Puis-je personnaliser le style de numérotation de la liste ?
 Oui, Aspose.Words pour .NET vous permet de personnaliser le style de numérotation de la liste à l'aide de`ListTemplate` classe.

### Comment ajouter des puces au lieu de numéros ?
 Vous pouvez appliquer des puces en utilisant le`ApplyBulletDefault` méthode au lieu de`ApplyNumberDefault`.

### Est-il possible de continuer la numérotation à partir d'une liste précédente ?
 Oui, vous pouvez continuer la numérotation en utilisant le`ListFormat.List` propriété permettant de créer un lien vers une liste existante.

### Comment modifier le niveau d’indentation de manière dynamique ?
 Vous pouvez modifier dynamiquement le niveau d'indentation en utilisant`ListIndent` et`ListOutdent` méthodes selon les besoins.

### Puis-je créer des listes à plusieurs niveaux dans d’autres formats de documents comme PDF ?
Oui, Aspose.Words prend en charge l'enregistrement de documents dans divers formats, y compris PDF, en conservant la mise en forme.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
