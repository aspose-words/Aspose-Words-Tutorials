---
"description": "Découvrez comment exporter des champs de formulaire de saisie de texte sous forme de texte brut à l'aide d'Aspose.Words pour .NET avec ce guide complet étape par étape."
"linktitle": "Exporter le champ de saisie de texte sous forme de texte"
"second_title": "API de traitement de documents Aspose.Words"
"title": "Exporter le champ de saisie de texte sous forme de texte"
"url": "/fr/net/programming-with-htmlsaveoptions/export-text-input-form-field-as-text/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Exporter le champ de saisie de texte sous forme de texte

## Introduction

Alors, vous vous lancez dans l'univers d'Aspose.Words pour .NET ? Excellent choix ! Si vous souhaitez apprendre à exporter un champ de saisie de texte au format texte, vous êtes au bon endroit. Que vous débutiez ou que vous perfectionniez vos compétences, ce guide vous expliquera tout ce que vous devez savoir. Commençons !

## Prérequis

Avant de plonger dans le vif du sujet, assurons-nous que vous disposez de tout ce dont vous avez besoin pour suivre en douceur :

- Aspose.Words pour .NET : téléchargez et installez la dernière version à partir de [ici](https://releases.aspose.com/words/net/).
- IDE : Visual Studio ou tout autre environnement de développement C#.
- Connaissances de base en C# : Compréhension de la syntaxe de base du C# et des concepts de programmation orientée objet.
- Document : Un exemple de document Word (`Rendering.docx`) avec des champs de formulaire de saisie de texte.

## Importer des espaces de noms

Tout d'abord, vous devez importer les espaces de noms nécessaires. Ce sont les éléments de base qui assurent le bon fonctionnement de l'ensemble.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;
```

Très bien, maintenant que nos espaces de noms sont prêts, passons à l’action !

## Étape 1 : Configurer le projet

Avant d’entrer dans le code, assurons-nous que notre projet est correctement configuré.

## Création du projet

1. Ouvrez Visual Studio : commencez par ouvrir Visual Studio ou votre environnement de développement C# préféré.
2. Créer un nouveau projet : accédez à `File > New > Project`Sélectionner `Console App (.NET Core)` ou tout autre type de projet pertinent.
3. Nommez votre projet : donnez à votre projet un nom significatif, quelque chose comme `AsposeWordsExportExample`.

## Ajout d'Aspose.Words

1. Gérer les packages NuGet : faites un clic droit sur votre projet dans l’Explorateur de solutions et sélectionnez `Manage NuGet Packages`.
2. Rechercher Aspose.Words : Dans le gestionnaire de packages NuGet, recherchez `Aspose.Words`.
3. Installez Aspose.Words : Cliquez sur `Install` pour ajouter la bibliothèque Aspose.Words à votre projet.

## Étape 2 : Charger le document Word

Maintenant que notre projet est configuré, chargeons le document Word qui contient les champs de saisie de texte.

1. Spécifiez le répertoire du document : définissez le chemin d’accès au répertoire dans lequel votre document est stocké.
2. Charger le document : utilisez le `Document` classe pour charger votre document Word.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

## Étape 3 : préparer le répertoire d’exportation

Avant d'exporter, vérifions que notre répertoire d'exportation est prêt. C'est là que seront enregistrés notre fichier HTML et nos images.

1. Définir le répertoire d'exportation : spécifiez le chemin où les fichiers exportés seront enregistrés.
2. Vérifiez et nettoyez le répertoire : assurez-vous que le répertoire existe et est vide.

```csharp
string imagesDir = Path.Combine(dataDir, "Images");

if (Directory.Exists(imagesDir))
    Directory.Delete(imagesDir, true);

Directory.CreateDirectory(imagesDir);
```

## Étape 4 : Configurer les options d’enregistrement

C'est ici que la magie opère : nous devons configurer nos options d'enregistrement pour exporter le champ de saisie de texte au format texte brut.

1. Créer des options d'enregistrement : initialiser une nouvelle `HtmlSaveOptions` objet.
2. Définir l'option d'exportation de texte : configurer le `ExportTextInputFormFieldAsText` propriété à `true`.
3. Définir le dossier d'images : définissez le dossier dans lequel les images seront enregistrées.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.Html)
{
    ExportTextInputFormFieldAsText = true,
    ImagesFolder = imagesDir
};
```

## Étape 5 : Enregistrer le document au format HTML

Enfin, enregistrons le document Word en tant que fichier HTML en utilisant nos options d’enregistrement configurées.

1. Définir le chemin de sortie : spécifiez le chemin où le fichier HTML sera enregistré.
2. Enregistrer le document : utilisez le `Save` méthode de la `Document` classe pour exporter le document.

```csharp
doc.Save(dataDir + "ExportedDocument.html", saveOptions);
```

## Conclusion

Et voilà ! Vous avez réussi à exporter un champ de saisie de texte au format texte brut avec Aspose.Words pour .NET. Ce guide devrait vous avoir fourni une approche claire et étape par étape pour y parvenir. N'oubliez pas : c'est en forgeant qu'on devient forgeron ! Continuez donc à tester différentes options et paramètres pour découvrir les possibilités d'Aspose.Words.

## FAQ

### Puis-je exporter d’autres types de champs de formulaire en utilisant la même méthode ?

Oui, vous pouvez exporter d’autres types de champs de formulaire en configurant différentes propriétés du `HtmlSaveOptions` classe.

### Que faire si mon document contient des images ?

Les images seront enregistrées dans le dossier d'images spécifié. Assurez-vous de définir le `ImagesFolder` propriété dans le `HtmlSaveOptions`.

### Ai-je besoin d'une licence pour Aspose.Words ?

Oui, vous pouvez obtenir un essai gratuit [ici](https://releases.aspose.com/) ou acheter une licence [ici](https://purchase.aspose.com/buy).

### Puis-je personnaliser le HTML exporté ?

Absolument ! Aspose.Words propose diverses options pour personnaliser la sortie HTML. Consultez le [documentation](https://reference.aspose.com/words/net/) pour plus de détails.

### Aspose.Words est-il compatible avec .NET Core ?

Oui, Aspose.Words est compatible avec .NET Core, .NET Framework et d’autres plates-formes .NET.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}