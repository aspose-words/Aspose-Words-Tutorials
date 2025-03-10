---
title: Convertir les métafichiers en Emf ou Wmf
linktitle: Convertir les métafichiers en Emf ou Wmf
second_title: API de traitement de documents Aspose.Words
description: Guide étape par étape pour convertir des métafichiers aux formats EMF ou WMF lors de la conversion d'un document en HTML avec Aspose.Words pour .NET.
weight: 10
url: /fr/net/programming-with-htmlsaveoptions/convert-metafiles-to-emf-or-wmf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Convertir les métafichiers en Emf ou Wmf

## Introduction

Bienvenue dans une nouvelle plongée dans le monde d'Aspose.Words pour .NET. Aujourd'hui, nous abordons une astuce intéressante : convertir des images SVG aux formats EMF ou WMF dans vos documents Word. Cela peut sembler un peu technique, mais ne vous inquiétez pas. À la fin de ce tutoriel, vous serez un pro. Que vous soyez un développeur chevronné ou que vous débutiez avec Aspose.Words pour .NET, ce guide vous expliquera tout ce que vous devez savoir, étape par étape.

## Prérequis

Avant de nous plonger dans le code, assurons-nous que tout est configuré. Voici ce dont vous avez besoin :

1.  Bibliothèque Aspose.Words pour .NET : assurez-vous d'avoir la dernière version. Si vous ne l'avez pas, vous pouvez la télécharger à partir de[ici](https://releases.aspose.com/words/net/).
2. .NET Framework : assurez-vous que .NET Framework est installé sur votre ordinateur.
3. Environnement de développement : un IDE comme Visual Studio vous facilitera la vie.
4. Connaissances de base de C# : vous n’avez pas besoin d’être un expert, mais une compréhension de base sera utile.

Vous avez tout reçu ? Super ! Commençons.

## Importer des espaces de noms

Tout d'abord, nous devons importer les espaces de noms nécessaires. Cela est crucial car cela indique à notre programme où trouver les classes et les méthodes que nous utiliserons.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Ces espaces de noms couvrent tout, des fonctions système de base aux fonctionnalités spécifiques d'Aspose.Words dont nous avons besoin pour ce didacticiel.

## Étape 1 : Configurez votre répertoire de documents

Commençons par définir le chemin d'accès à votre répertoire de documents. C'est là que votre document Word sera enregistré après la conversion des métafichiers.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Remplacer`"YOUR DOCUMENT DIRECTORY"` avec le chemin réel où vous souhaitez enregistrer votre document.

## Étape 2 : créer la chaîne HTML avec SVG

Ensuite, nous avons besoin d'une chaîne HTML contenant l'image SVG que nous voulons convertir. Voici un exemple simple :

```csharp
string html = 
    @"<html>
        <svg xmlns='http://www.w3.org/2000/svg' width='500' height='40' viewBox='0 0 500 40'>
            <text x='0' y='35' font-family='Verdana' font-size='35'>Hello world!</text>
        </svg>
    </html>";
```

Cet extrait HTML inclut un SVG de base qui dit « Bonjour le monde ! ».

## Étape 3 : Charger du code HTML avec l'option ConvertSvgToEmf

 Maintenant, nous utilisons le`HtmlLoadOptions` pour spécifier comment nous voulons gérer les images SVG dans le HTML.`ConvertSvgToEmf` à`true` garantit que les images SVG sont converties au format EMF.

```csharp
HtmlLoadOptions loadOptions = new HtmlLoadOptions { ConvertSvgToEmf = true };
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(html)), loadOptions);
```

 Cet extrait de code crée un nouveau`Document` objet en chargeant la chaîne HTML avec les options de chargement spécifiées.

## Étape 4 : définir HtmlSaveOptions pour le format de métafichier

 Pour enregistrer le document avec le format de métafichier correct, nous utilisons`HtmlSaveOptions` . Ici, nous avons mis`MetafileFormat` à`HtmlMetafileFormat.Png` , mais vous pouvez changer cela en`Emf` ou`Wmf` selon vos besoins.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions { MetafileFormat = HtmlMetafileFormat.Png };
```

## Étape 5 : Enregistrer le document

Enfin, nous enregistrons le document en utilisant les options d’enregistrement spécifiées.

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToPng.html", saveOptions);
```

Cela enregistre le document dans le répertoire spécifié avec le format de métafichier converti comme défini.

## Conclusion

Et voilà ! En suivant ces étapes, vous avez réussi à convertir des images SVG aux formats EMF ou WMF dans vos documents Word à l'aide d'Aspose.Words pour .NET. Cette méthode est pratique pour garantir la compatibilité et maintenir l'intégrité visuelle de vos documents sur différentes plateformes. Bon codage !

## FAQ

### Puis-je convertir d’autres formats d’image en utilisant cette méthode ?
Oui, vous pouvez convertir différents formats d'image en ajustant les options de chargement et d'enregistrement en conséquence.

### Est-il nécessaire d'utiliser une version spécifique de .NET Framework ?
Aspose.Words pour .NET prend en charge plusieurs versions de .NET Framework, mais c'est toujours une bonne idée d'utiliser la dernière version pour une meilleure compatibilité et des fonctionnalités optimales.

### Quel est l’avantage de convertir SVG en EMF ou WMF ?
La conversion de SVG en EMF ou WMF garantit que les graphiques vectoriels sont préservés et rendus correctement dans des environnements qui peuvent ne pas prendre entièrement en charge SVG.

### Puis-je automatiser ce processus pour plusieurs documents ?
Absolument ! Vous pouvez parcourir plusieurs fichiers HTML en appliquant le même processus pour automatiser la conversion pour le traitement par lots.

### Où puis-je trouver plus de ressources et d'assistance pour Aspose.Words pour .NET ?
 Vous trouverez une documentation complète[ici](https://reference.aspose.com/words/net/) et obtenez le soutien de la communauté Aspose[ici](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
