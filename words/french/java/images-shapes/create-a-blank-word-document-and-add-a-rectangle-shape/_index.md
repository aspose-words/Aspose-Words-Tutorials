---
category: general
date: 2026-10-23
description: Créez un document Word vierge, ajoutez une forme rectangle et masquez
  la forme dans Word à l’aide d’Aspose.Words. Code étape par étape pour les développeurs
  .NET.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- how to insert shape
- hide shape word
language: fr
lastmod: 2026-10-23
og_description: Créez un document Word vierge, ajoutez une forme rectangulaire et
  masquez la forme dans Word avec Aspose.Words. Suivez l'exemple complet en C#.
og_image_alt: Screenshot of a Word document containing a hidden rectangle shape
og_title: Créer un document Word vierge et ajouter une forme rectangle cachée
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Create a blank Word document, add a rectangle shape, and hide the shape
    in Word using Aspose.Words. Step‑by‑step code for .NET developers.
  headline: Create a blank Word document and add a rectangle shape
  type: TechArticle
tags:
- Aspose.Words
- .NET
- Word automation
title: Créer un document Word vierge et ajouter une forme rectangulaire
url: /fr/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un document Word vierge et ajouter une forme rectangle

Si vous devez **créer un document Word vierge**, ce guide vous montre comment le faire avec Aspose.Words for .NET. Vous apprendrez également **comment insérer une forme** — plus précisément un rectangle — et **masquer la forme dans Word** afin qu’elle n’affecte pas la mise en page.

Le tutoriel passe en revue chaque ligne de code, explique pourquoi chaque étape est importante et couvre les pièges courants tels que la visibilité des formes masquées dans différents modes d’affichage de Word. À la fin, vous disposerez d’un fichier `.docx` pleinement fonctionnel contenant une forme rectangle masquée que vous pourrez révéler ou manipuler ultérieurement par programme.

## Prérequis

- .NET 6.0 ou version ultérieure (le code fonctionne également avec .NET Framework 4.6+)
- Package NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)
- Un environnement de développement tel que Visual Studio 2022 ou VS Code avec les extensions C#
- Une connaissance de base de la syntaxe C# et des concepts de documents Word

Aucune installation supplémentaire d’Office n’est requise car Aspose.Words fonctionne entièrement en mémoire.

## Créer un document Word vierge

La première étape consiste à instancier un objet `Document` vide. Cet objet représente un fichier Word qui ne contient pour l’instant aucune section, aucun paragraphe et aucun contenu.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document
Document document = new Document();
```

**Pourquoi c’est important :**  
Un `Document` vierge vous offre une toile propre. Si vous partez d’un modèle existant, les formes masquées pourraient hériter de styles indésirables. Commencer à zéro garantit que la forme rectangle que vous ajouterez plus tard sera le seul contenu que vous contrôlez.

## Ajouter une forme rectangle au document

Ensuite, nous avons besoin d’un `DocumentBuilder` pour placer du contenu dans le document. La méthode `InsertShape` du builder est la façon standard **d’insérer une forme**, comme des rectangles, des cercles ou des dessins personnalisés.

```csharp
// Step 2: Initialize a DocumentBuilder to add content
DocumentBuilder builder = new DocumentBuilder(document);

// Step 3: Insert a rectangle shape of size 200x100 points
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

**Pourquoi c’est important :**  
`InsertShape` renvoie un objet `Shape` que vous pouvez configurer davantage (couleur, style de ligne, etc.). Les dimensions sont exprimées en points (1 point = 1/72 pouce), ce qui correspond au système de mesure interne de Word.

### Optionnel : styliser le rectangle (facultatif)

Si vous souhaitez que le rectangle possède une bordure visible lorsque vous le réafficherez plus tard, vous pouvez définir son épaisseur de ligne et sa couleur :

```csharp
rectangleShape.LineWeight = 0.5;               // Thin border
rectangleShape.LineColor = System.Drawing.Color.Blue;
```

Ces lignes sont optionnelles car la forme sera masquée à l’étape suivante.

## Masquer la forme dans Word

Word permet de masquer les formes du rendu tout en les maintenant dans le modèle d’objet du document. Définir la propriété `Hidden` à `true` rend la forme invisible en mode affichage normal mais reste sélectionnable via l’API.

```csharp
// Step 4: Hide the shape so it does not appear in the layout
rectangleShape.Hidden = true;
```

**Pourquoi c’est important :**  
Une forme masquée est utile pour stocker des métadonnées, des espaces réservés pour un traitement ultérieur ou du contenu conditionnel que vous ne révélez que dans certaines circonstances (par ex., lors de la génération d’un rapport final). La forme reste dans le fichier, vous pouvez donc la démasquer programmatiquement plus tard avec `rectangleShape.Hidden = false;`.

## Enregistrer le document

Enfin, écrivez le document sur le disque. L’extension du fichier détermine le format Word ; `.docx` est le format Open XML moderne.

```csharp
// Step 5: Save the document with the hidden shape
string outputPath = @"C:\Temp\HiddenShape.docx";
document.Save(outputPath);
```

**Résultat :**  
L’ouverture de `HiddenShape.docx` dans Microsoft Word affiche une page autrement vide. Le rectangle n’est pas visible, mais si vous allez dans **Accueil → Sélectionner → Volet de sélection**, vous verrez la forme listée et pourrez basculer sa visibilité.

## Exemple complet fonctionnel

Ci‑dessous se trouve le programme complet que vous pouvez copier, coller et exécuter. Il comprend toutes les instructions `using` nécessaires ainsi que des commentaires.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document
        Document document = new Document();

        // Initialize a DocumentBuilder for content insertion
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a rectangle shape (200x100 points)
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // Optional styling (comment out if not needed)
        rectangleShape.LineWeight = 0.5;
        rectangleShape.LineColor = System.Drawing.Color.Blue;

        // Hide the shape so it does not appear in the layout
        rectangleShape.Hidden = true;

        // Save the document
        string outputPath = @"C:\Temp\HiddenShape.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Sortie attendue :**  

- La console affiche le chemin de sauvegarde.  
- `HiddenShape.docx` s’ouvre comme une page blanche dans Word.  
- La forme rectangle existe mais est masquée ; vous pouvez la vérifier via le *Volet de sélection* ou en définissant programmatiquement `Hidden = false` puis en rouvrant le fichier.

## Questions fréquentes et cas particuliers

| Question | Réponse |
|----------|--------|
| **Puis‑je masquer d’autres types de forme ?** | Oui. Toute `Shape` (par ex., `ShapeType.Ellipse`, `ShapeType.Picture`) prend en charge la propriété `Hidden`. |
| **La forme masquée augmentera‑t‑elle la taille du fichier ?** | L’augmentation est négligeable (quelques kilo‑octets) car les données de la forme sont stockées en XML dans le package `.docx`. |
| **Et si je veux que la forme n’apparaisse que dans la vue impression ?** | Utilisez la propriété `Shape.IsPrint` à la place de `Hidden`. Définir `IsPrint = false` masque la forme de la sortie imprimée tout en la gardant visible à l’écran. |
| **Comment démasquer la forme plus tard ?** | Chargez le document, localisez la forme (par ex., via `Shape.Name`), puis définissez `shape.Hidden = false;` et enregistrez. |
| **Cela fonctionne‑t‑il avec le format .doc (binaire) ?** | Oui, Aspose.Words peut enregistrer en `.doc` avec `document.Save("file.doc");`. Le drapeau masqué est conservé. |

## Astuces professionnelles

- **Nommez vos formes** : `rectangleShape.Name = "PlaceholderRectangle";` facilite la recherche ultérieure via `document.GetChildNodes(NodeType.Shape, true).Cast<Shape>().FirstOrDefault(s => s.Name == "PlaceholderRectangle")`.
- **Traitement par lots** : Si vous devez ajouter des formes masquées à de nombreux documents, encapsulez le code dans une méthode et réutilisez l’instance `DocumentBuilder`.
- **Performance** : Créer une forme est peu coûteux, mais enregistrer fréquemment de gros documents peut être limité par les I/O. Envisagez d’utiliser `MemoryStream` pour le traitement intermédiaire.

## Conclusion

Vous savez maintenant comment **créer un document Word vierge**, **ajouter une forme rectangle** et **masquer la forme dans Word** à l’aide d’Aspose.Words for .NET. Cette technique vous permet d’intégrer des espaces réservés invisibles que vous pourrez révéler ou manipuler plus tard, un schéma utile pour la génération dynamique de rapports, le contenu conditionnel et la création de modèles de documents.

Prochaines étapes que vous pourriez explorer :

- Remplacer le rectangle par une image ou un graphique en utilisant `ShapeType.Picture`.
- Utiliser **comment insérer une forme** dans les sections d’en‑tête/pied de page pour des espaces réservés de type filigrane.
- Combiner des formes masquées avec la validation de données basée sur **ajouter une forme rectangle** (par ex., stocker du JSON dans la propriété `AlternativeText` d’une forme).

Bon codage, et n’hésitez pas à expérimenter avec d’autres types de formes et options de visibilité pour répondre à vos besoins d’automatisation de documents !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser des fonctionnalités supplémentaires de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Create Word Document – How to Add Rectangle Shape and Shadow](/words/english/net/programming-with-shapes/create-word-document-how-to-add-rectangle-shape-and-shadow/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide](/words/english/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}