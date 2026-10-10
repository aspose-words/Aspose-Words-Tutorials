---
category: general
date: 2026-10-10
description: Créez un document Word vierge, insérez une image dans Word, ajoutez un
  groupe d’images et masquez la forme dans le fichier enregistré. Suivez ce guide
  étape par étape.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert image into word
- add image group
- hide shape word document
language: fr
lastmod: 2026-10-10
og_description: Créer un document Word vierge, insérer une image dans Word, ajouter
  un groupe d'images et masquer la forme. Ce guide montre le code C# complet.
og_image_alt: Screenshot of a blank Word document with a hidden image group
og_title: Créer un document Word vierge, ajouter un groupe d’images, masquer la forme
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Create a blank Word document, insert image into Word, add an image
    group, and hide shape in the saved file. Follow this step‑by‑step guide.
  headline: Create a blank Word document, add an image group, hide shape
  type: TechArticle
tags:
- Word automation
- Aspose.Words
- C#
- Document processing
title: Créer un document Word vierge, ajouter un groupe d’images, masquer la forme
url: /fr/java/images-shapes/create-a-blank-word-document-add-an-image-group-hide-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un document Word vierge, ajouter un groupe d'images, masquer la forme

Si vous devez **créer un document Word vierge** et masquer plus tard des éléments visuels, ce tutoriel vous montre exactement comment faire. Vous apprendrez à insérer une image dans Word, ajouter un groupe d'images et masquer la forme dans le document Word dans une routine C# réutilisable.

Nous utiliserons la bibliothèque Aspose.Words for .NET, qui vous permet de manipuler des fichiers .docx sans Microsoft Word installé. À la fin de ce guide, vous disposerez d’un programme exécutable qui génère un fichier Word contenant un groupe d’images masqué, prêt pour un traitement en aval ou un affichage conditionnel.

## Prérequis

- .NET 6.0 ou version ultérieure (le code fonctionne également avec .NET Framework 4.6+)
- Package NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)
- Un dossier sur le disque où vous pouvez lire un fichier image et écrire le document de sortie
- Une connaissance de base du C# et de Visual Studio (ou tout autre IDE de votre choix)

## Créer un document Word vierge avec Aspose.Words

La première étape consiste à **créer un document Word vierge**. Aspose.Words fournit la classe `Document` qui représente un fichier Word en mémoire. L’instancier sans arguments vous donne un document vide prêt à recevoir du contenu.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();                 // blank .docx container
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Pourquoi c’est important :* Commencer avec un document vierge garantit qu’aucun formatage caché ou section résiduelle n’interfère avec la forme que vous ajouterez plus tard.

## Insérer une image dans Word à l’aide de DocumentBuilder

Ensuite, nous **insérons une image dans Word** en créant d’abord une forme de groupe qui contiendra l’image. Les formes de groupe vous permettent de traiter plusieurs objets de dessin comme une seule unité, ce qui est pratique lorsque vous souhaitez les masquer ou les déplacer ensemble ultérieurement.

```csharp
        // Step 2: Insert a group shape with the desired size (width: 300, height: 200)
        GroupShape group = builder.InsertGroupShape(300, 200);
```

La méthode `InsertGroupShape` crée un conteneur vide. Les dimensions sont exprimées en points (1 point = 1/72 pouce). Ajustez la taille pour qu’elle corresponde à la résolution de l’image que vous prévoyez d’intégrer.

## Ajouter le groupe d’images au document

Nous **ajoutons le groupe d’images** en déplaçant le curseur du builder à l’intérieur du groupe nouvellement créé et en insérant l’image. Toutes les insertions suivantes feront partie du groupe.

```csharp
        // Step 3: Position the builder inside the group so subsequent inserts go into it
        builder.MoveTo(group);

        // Step 4: Add an image to the group shape
        // Replace the path with the actual location of your PNG/JPEG file
        builder.InsertImage(@"YOUR_DIRECTORY\photo1.png");
```

*Astuce :* Utilisez un chemin absolu ou un chemin relatif correctement échappé ; sinon `InsertImage` lèvera une `FileNotFoundException`.

## Masquer la forme dans un document Word

Enfin, nous **masquons la forme dans le document Word** en définissant la propriété `Hidden` du groupe à `true`. Les formes masquées ne sont pas affichées lorsque le document est ouvert dans Word, mais elles restent dans le fichier et peuvent être révélées programmatiquement plus tard.

```csharp
        // Step 5: Hide the entire group (the image will not be visible in the saved document)
        group.Hidden = true;

        // Step 6: Save the document with the hidden group
        doc.Save(@"YOUR_DIRECTORY\GroupHidden.docx");
    }
}
```

Lorsque vous ouvrez *GroupHidden.docx* dans Microsoft Word, vous verrez une page complètement blanche parce que le groupe d’images est masqué. Le fichier contient toujours les données de l’image, que vous pouvez démasquer plus tard avec `group.Hidden = false` si besoin.

## Exemple complet et exécutable

Voici le programme complet que vous pouvez copier‑coller dans un nouveau projet console :

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a blank Word document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a group shape (300 pt × 200 pt)
            GroupShape group = builder.InsertGroupShape(300, 200);

            // 3️⃣ Move inside the group so inserts become part of it
            builder.MoveTo(group);

            // 4️⃣ Insert the image (replace with your own file)
            builder.InsertImage(@"YOUR_DIRECTORY\photo1.png");

            // 5️⃣ Hide the group so the image is not shown
            group.Hidden = true;

            // 6️⃣ Save the result
            doc.Save(@"YOUR_DIRECTORY\GroupHidden.docx");

            Console.WriteLine("Document created successfully.");
        }
    }
}
```

**Résultat attendu**

- Un fichier nommé `GroupHidden.docx` apparaît dans `YOUR_DIRECTORY`.
- L’ouverture du fichier dans Word affiche une page vide.
- L’image masquée peut être révélée en modifiant `group.Hidden = false` puis en réenregistrant.

## Variations courantes et cas limites

| Situation | Comment adapter le code |
|-----------|--------------------------|
| **Images multiples** | Insérez des appels supplémentaires à `InsertImage` après `builder.MoveTo(group)`. Toutes les images restent à l’intérieur du même groupe et partagent le drapeau masqué. |
| **Différents formats d’image** | Aspose.Words prend en charge PNG, JPEG, BMP, GIF, TIFF. Changez simplement l’extension du fichier ; aucune modification du code n’est nécessaire. |
| **Visibilité conditionnelle** | Stockez une variable de document personnalisée (`doc.Variables.Add("ShowImages", "true")`) et basculez `group.Hidden` en fonction de sa valeur à l’exécution. |
| **Documents volumineux** | Créez le groupe sur une page spécifique (`builder.InsertBreak(BreakType.PageBreak)`) avant d’insérer le groupe afin d’éviter les déplacements de mise en page. |
| **Compatibilité avec les versions plus anciennes de Word** | Enregistrez sous `doc.Save("output.doc", SaveFormat.Doc)` si vous avez besoin du format legacy `.doc` ; les formes masquées se comportent de la même façon. |

**Conseil pro :** Toujours définir `group.Hidden = true` *après* avoir inséré tous les éléments enfants. Modifier le drapeau avant d’ajouter le contenu peut entraîner le rendu inattendu de certains éléments dans les versions plus anciennes de Word.

## Conclusion

Vous savez maintenant comment **créer un document Word vierge**, **insérer une image dans Word**, **ajouter un groupe d’images** et **masquer la forme dans le document Word** en utilisant Aspose.Words for .NET. L’exemple complet montre chaque étape, de l’initialisation du document à l’enregistrement d’un fichier contenant un groupe d’images masqué.

Ensuite, vous pourriez explorer :

- Ajouter des zones de texte ou des graphiques au même groupe
- Utiliser `DocumentBuilder.StartBookmark` / `EndBookmark` pour marquer des sections masquées
- Basculez la visibilité de façon programmatique selon les entrées utilisateur ou les variables du document

N’hésitez pas à expérimenter avec différentes formes, tailles et règles de visibilité pour répondre à votre scénario d’automatisation. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document with Floating Image in .NET](/words/english/net/add-content-using-documentbuilder/insert-floating-image/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}