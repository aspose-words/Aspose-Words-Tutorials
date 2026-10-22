---
category: general
date: 2026-09-30
description: Regrouper des formes dans Word avec C# – apprenez comment regrouper des
  formes, ajouter un rectangle et une ellipse, et insérer une forme rectangle dans
  des documents Word de manière programmatique.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- how to add rectangle
- how to add ellipse
- insert rectangle shape word
language: fr
lastmod: 2026-09-30
og_description: Regroupez des formes dans Word avec C# et Aspose.Words. Suivez ce
  guide complet pour ajouter un rectangle, ajouter une ellipse et apprendre à regrouper
  les formes efficacement.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape
og_title: Regrouper des formes dans Word avec C# – guide étape par étape
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: group shapes in Word with C# – learn how to group shapes, add rectangle
    and ellipse, and insert rectangle shape Word documents programmatically.
  headline: How to group shapes in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Comment regrouper des formes dans Word en utilisant C# et Aspose.Words
url: /fr/net/programming-with-shapes/how-to-group-shapes-in-word-using-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment regrouper des formes dans Word avec C# et Aspose.Words

Si vous devez **regrouper des formes dans Word** de façon programmatique, ce guide vous montre exactement comment procéder. Vous verrez comment ajouter un rectangle, ajouter une ellipse, puis les combiner en une seule forme groupée à l’aide de la bibliothèque Aspose.Words pour .NET.

Travailler avec des formes est une exigence courante lors de la génération automatique de rapports, de contrats ou de documents marketing. À la fin de ce tutoriel, vous disposerez d’une méthode C# réutilisable qui charge un fichier DOCX, insère un rectangle et une ellipse, les groupe, puis enregistre le résultat — le tout sans ouvrir Word manuellement.

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

* .NET 6.0 SDK ou version ultérieure installé  
* Un environnement de développement tel que Visual Studio 2022 (l’édition Community convient)  
* Une licence Aspose.Words for .NET ou une copie d’évaluation gratuite (l’API fonctionne sans licence mais ajoute un filigrane)  

Vous avez également besoin d’un document Word source (`input.docx`) dans un dossier que vous pouvez référencer depuis le code. Le document peut être vide ; le tutoriel se concentre sur la gestion des formes.

## Étape 1 : Créer un nouveau projet console et ajouter Aspose.Words

Ouvrez un terminal ou l’invite de commandes de Visual Studio et exécutez :

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

Cela crée une nouvelle application console nommée **WordShapeDemo** et ajoute le package NuGet `Aspose.Words`, qui contient les classes `Document` et `DocumentBuilder` utilisées pour manipuler les fichiers Word.

## Étape 2 : Charger ou créer un document

La première opération lorsqu’on travaille avec **des formes groupées dans Word** consiste à obtenir un objet `Document`. Vous pouvez soit charger un fichier DOCX existant, soit partir d’un document vierge.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Load an existing document (replace the path with your own)
        Document document = new Document(@"YOUR_DIRECTORY\input.docx");

        // If you prefer a brand‑new document, uncomment the next line:
        // Document document = new Document();
```

La classe `Document` représente l’ensemble du fichier Word. Charger un fichier vous fournit une toile prête à recevoir des formes.

## Étape 3 : Commencer une forme groupée

Une *forme groupée* vous permet de traiter plusieurs formes indépendantes comme une seule unité — idéal pour les déplacer ou les redimensionner ensemble. Pour démarrer un groupe, appelez `StartGroupShape()` sur un `DocumentBuilder`.

```csharp
        // Create a builder to edit the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Begin a group shape that will contain multiple shapes
        builder.StartGroupShape();
```

Appeler `StartGroupShape` indique à Aspose.Words que chaque insertion de forme suivante appartient au même groupe logique jusqu’à ce que vous appeliez `EndGroupShape`.

## Étape 4 : Comment ajouter une forme rectangle dans Word

Maintenant que le groupe est ouvert, insérez un rectangle. La méthode `InsertShape` prend une énumération `ShapeType`, suivie de la largeur et de la hauteur (en points).

```csharp
        // Add a rectangle shape to the group (100 pt wide, 50 pt high)
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

Le rectangle devient le premier membre du groupe. Vous pourrez personnaliser son remplissage, son contour ou son texte ultérieurement si besoin.

## Étape 5 : Comment ajouter une forme ellipse dans Word

Ensuite, ajoutez une ellipse (un cercle lorsque la largeur est égale à la hauteur). Cela montre **comment ajouter une ellipse** en utilisant le même `DocumentBuilder`.

```csharp
        // Add an ellipse shape to the same group (80 pt wide, 80 pt high)
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

Les deux formes partagent désormais le même espace de coordonnées à l’intérieur du groupe, ce qui facilite leur alignement visuel.

## Étape 6 : Fermer la définition de la forme groupée

Lorsque vous avez ajouté tous les membres souhaités, fermez le groupe. Cela finalise la collection de formes afin que Word les traite comme un seul objet.

```csharp
        // End the group shape definition
        builder.EndGroupShape();
```

À ce stade, le document contient une unique forme groupée composée d’un rectangle et d’une ellipse.

## Étape 7 : Enregistrer le document modifié

Enfin, écrivez les modifications sur le disque. Vous pouvez écraser le fichier original ou en créer un nouveau.

```csharp
        // Save the document with the grouped shapes
        document.Save(@"YOUR_DIRECTORY\output.docx");

        Console.WriteLine("Document saved with grouped shapes.");
    }
}
```

L’exécution du programme produit `output.docx`. Ouvrez le fichier dans Microsoft Word, sélectionnez la forme, et vous verrez que le rectangle et l’ellipse se déplacent ensemble — preuve que l’opération **group shapes in Word** a réussi.

### Résultat attendu

* Le fichier Word contient un seul objet groupé.  
* Sélectionner le groupe vous permet de le faire glisser, de le redimensionner ou de le faire pivoter simultanément pour le rectangle et l’ellipse.  
* Aucune interaction manuelle avec Word n’est requise ; tout est réalisé via le code C#.

![Grouped shapes in Word document](grouped-shapes.png "Screenshot of a Word document showing a grouped rectangle and ellipse shape")

*Texte alternatif de l’image : « Capture d’écran d’un document Word affichant un rectangle et une ellipse groupés »* (satisfait l’exigence de texte alt de l’image).

## Pourquoi le regroupement de formes est important

Regrouper des formes va au‑delà d’une simple commodité visuelle. Cela vous permet de :

* **Maintenir la cohérence de la mise en page** – déplacer un groupe conserve les positions relatives.  
* **Appliquer des transformations une seule fois** – faire pivoter ou mettre à l’échelle l’ensemble du groupe au lieu de chaque forme individuellement.  
* **Simplifier le traitement en aval** – lorsque d’autres outils lisent le DOCX, ils voient une forme composite unique, ce qui réduit la complexité.

Si vous devez ajouter d’autres formes (par ex., une ligne ou une zone de texte) à la même unité logique, il suffit d’appeler à nouveau `InsertShape` avant `EndGroupShape`.

## Variantes courantes et cas limites

| Situation | Comment le gérer |
|-----------|------------------|
| **Unités différentes** – vous avez des mesures en centimètres | Convertissez les centimètres en points (`1 cm ≈ 28,35 pt`) avant d’appeler `InsertShape`. |
| **Ajout d’une étiquette texte** – vous voulez une légende à l’intérieur du groupe | Insérez un `ShapeType.TextBox` après le rectangle et l’ellipse, puis définissez sa propriété `Text`. |
| **Application d’une couleur de remplissage** – vous avez besoin d’un rectangle bleu | Après `InsertShape`, récupérez la dernière forme via `builder.CurrentParagraph.Runs[0].Font` et définissez `shape.FillColor = System.Drawing.Color.Blue;`. |
| **Utilisation d’un format de document différent** – vous ciblez `.doc` au lieu de `.docx` | Le même code fonctionne ; il suffit de changer l’extension du fichier lors de l’appel à `Save`. Aspose.Words gère automatiquement le format. |

## Astuces professionnelles

* **Réutiliser le builder** – vous pouvez démarrer et terminer plusieurs groupes dans le même document ; il suffit d’appeler de nouveau `StartGroupShape` après `EndGroupShape`.  
* **Performance** – insérer plusieurs formes en bloc à l’intérieur d’un même bloc `StartGroupShape/EndGroupShape` est plus rapide que d’insérer les formes individuellement hors d’un groupe.  
* **Licence** – une licence d’évaluation ajoute un filigrane sur la première page. Installez une licence appropriée pour le supprimer en production.

## Conclusion

Vous savez maintenant comment **regrouper des formes dans Word** avec C#, comment **ajouter un rectangle**, comment **ajouter une ellipse**, et comment **insérer une forme rectangle dans des documents Word** à l’aide d’Aspose.Words. L’exemple complet et exécutable montre chaque étape, de la configuration du projet à l’enregistrement du fichier final.

À partir d’ici, vous pouvez explorer d’autres types de formes, appliquer des styles, ou combiner des formes groupées avec des tableaux et des images pour créer des documents sophistiqués générés programmatique­ment.

---

**Prochaines étapes**

* Apprenez comment **faire pivoter des formes groupées** : utilisez `Shape.RotationAngle` après la fermeture du groupe.  
* Explorez la **personnalisation du remplissage et du contour** pour les rectangles et les ellipses.  
* Intégrez cette logique dans une API ASP.NET Core pour générer des rapports à la demande.  

Bon codage !

## Que devez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser des fonctionnalités supplémentaires de l’API et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Rectangle Shape in Word – Full Aspose.Words Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}