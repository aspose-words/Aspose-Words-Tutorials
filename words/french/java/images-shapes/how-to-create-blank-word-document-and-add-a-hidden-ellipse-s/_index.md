---
category: general
date: 2026-09-21
description: Créer un document Word vierge avec une ellipse cachée en C#. Apprenez
  à masquer une forme dans Word et à générer une forme cachée par programmation.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to create ellipse
- hide shape in word
- create hidden shape
language: fr
lastmod: 2026-09-21
og_description: Créer un document Word vierge avec une ellipse cachée en C#. Ce guide
  montre comment masquer une forme dans Word et créer des formes cachées programmatiquement.
og_image_alt: Screenshot of a blank Word document that contains a hidden ellipse shape
  created with C#
og_title: Créer un document Word vierge avec une forme d'ellipse cachée en C#
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create blank Word document with a hidden ellipse using C#. Learn how
    to hide shape in Word and generate a hidden shape programmatically.
  headline: How to create blank Word document and add a hidden ellipse shape in C#
  type: TechArticle
- questions:
  - answer: The shape’s XML adds a few hundred bytes, which is negligible for most
      use cases. The file remains essentially the same size as a truly empty document.
    question: Does hiding a shape affect document size?
  - answer: Yes. Load the document, locate the shape (`doc.GetChildNodes(NodeType.Shape,
      true)`), and set `shape.Hidden = false`.
    question: Can I unhide the shape later programmatically?
  - answer: No. Hidden objects are excluded from the print layout, so the printed
      page stays blank.
    question: Will the hidden shape appear when printing?
  - answer: 'The `Hidden` property is part of the OOXML spec, so any Word processor
      that fully implements OOXML (Word, LibreOffice, Google Docs) will respect the
      hidden flag. --- ## Conclusion You now know how to **create blank Word document**,
      **how to create ellipse**, **hide shape in Word**, and **create hidd'
    question: Is this approach compatible with Office Open XML (OOXML) only?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Word automation
title: Comment créer un document Word vierge et ajouter une forme d’ellipse cachée
  en C#
url: /fr/java/images-shapes/how-to-create-blank-word-document-and-add-a-hidden-ellipse-s/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer un document Word vierge et ajouter une forme d’ellipse cachée en C#

Si vous devez **créer un document Word vierge** contenant un graphique invisible, ce guide vous montre exactement comment procéder. À la fin du tutoriel, vous disposerez d’un fichier .docx qui semble vide mais qui stocke en réalité une forme d’ellipse cachée du rendu.

Nous utiliserons Aspose.Words for .NET pour créer le document, insérer une ellipse, la masquer et enregistrer le fichier. Les étapes couvrent également **comment créer une ellipse**, la façon appropriée de **masquer la forme dans Word**, et comment **créer une forme cachée** qui fonctionne avec n’importe quel projet .NET.

## Prérequis

* .NET 6.0 SDK ou version ultérieure installé  
* Visual Studio 2022 (ou tout éditeur C#)  
* Une licence Aspose.Words for .NET ou une copie d’évaluation gratuite  
* Familiarité de base avec la syntaxe C#  

 Aucun package NuGet supplémentaire n’est requis au-delà de `Aspose.Words`.

## Créer un document Word vierge avec Aspose.Words

La première étape consiste à générer un fichier Word vide. Cela nous fournit une toile propre où nous pourrons ensuite insérer des graphiques cachés.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document doc = new Document();

        // The document is currently empty – it contains no paragraphs or shapes.
        // This is the foundation for all further operations.
```

**Pourquoi nous commençons avec un document vierge** – Partir d’un fichier vide garantit qu’aucun contenu indésirable n’interfère avec la forme cachée. Cela maintient également la taille du fichier au minimum, ce qui est utile lorsque le document est ultérieurement utilisé comme modèle.

## Comment créer une ellipse dans le document vierge

Ensuite, nous avons besoin d’un `DocumentBuilder` pour ajouter du contenu. Le builder nous permet de placer les formes précisément où nous le souhaitons.

```csharp
        // Step 2: Initialize a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert an ellipse shape (width: 100 points, height: 50 points)
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

        // The ellipse now exists on the page, but it is visible by default.
```

**Explication** – `ShapeType.Ellipse` indique à Aspose.Words de dessiner une figure de forme circulaire. La largeur et la hauteur sont mesurées en points (1 pt ≈ 1/72 pouce). Vous pouvez ajuster ces valeurs pour répondre à vos besoins de conception.

## Masquer la forme dans Word afin qu’elle n’apparaisse pas dans la mise en page

Une forme qui est masquée reste présente dans le XML du document, ce qui peut être utile pour les métadonnées, le formatage conditionnel ou des modifications programmatiques ultérieures. Pour la masquer, nous définissons la propriété `Hidden` sur `true`.

```csharp
        // Step 4: Hide the shape so it does not appear in the layout
        ellipse.Hidden = true;

        // When Hidden = true, Word treats the shape as if it were not there.
        // The shape remains in the document’s DOM, allowing you to retrieve or modify it later.
```

**Pourquoi masquer la forme** – Les formes masquées sont ignorées par le moteur de mise en page, de sorte que la page apparaît complètement vide. Cependant, les données de la forme persistent, ce qui peut être utile pour stocker des marqueurs, des signets ou du XML personnalisé que les processus en aval peuvent lire.

## Enregistrer le document avec la forme cachée

Enfin, nous écrivons le fichier sur le disque. Le `.docx` enregistré s’ouvrira dans Microsoft Word sans contenu visible, mais l’ellipse cachée sera toujours présente.

```csharp
        // Step 5: Save the document with the hidden shape
        doc.Save(@"C:\Temp\HiddenEllipse.docx");

        // The file now contains a hidden ellipse and appears empty when opened.
    }
}
```

**Vérification** – Ouvrez le fichier généré dans Word, puis appuyez sur `Alt+F9` pour basculer les codes de champ et `Ctrl+A` → `Ctrl+Shift+F9` pour afficher les objets cachés. Vous verrez l’ellipse dans le XML du document (`word/document.xml`) mais rien sur la page.

---

## Exemple complet et exécutable

Ci-dessous se trouve le programme complet que vous pouvez copier‑coller dans un nouveau projet console. Il inclut toutes les directives `using` et la méthode `Main` afin que vous puissiez l’exécuter sans configuration supplémentaire.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace HiddenShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank Word document
            Document doc = new Document();

            // 2️⃣ Prepare a builder to insert content
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert an ellipse (100 pt × 50 pt)
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

            // 4️⃣ Hide the ellipse so the page stays empty
            ellipse.Hidden = true;

            // 5️⃣ Save the file
            string outPath = @"C:\Temp\HiddenEllipse.docx";
            doc.Save(outPath);

            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

**Sortie attendue** – Lorsque vous exécutez le programme, la console affiche le chemin du fichier, et le fichier Word résultant ne contient aucun objet visible. Si vous inspectez le document avec un outil zip (`.docx` est une archive zip), vous trouverez l’élément `<w:pict>` décrivant l’ellipse dans `word/document.xml`.

---

## Variantes courantes et cas limites

| Scénario | Ce qu’il faut changer | Pourquoi c’est important |
|----------|-----------------------|--------------------------|
| **Forme différente** | Remplacez `ShapeType.Ellipse` par `ShapeType.Rectangle`, `ShapeType.Line`, etc. | Vous permet de masquer d’autres graphiques tout en conservant le même flux de travail. |
| **Formes cachées multiples** | Appelez `InsertShape` plusieurs fois et définissez `Hidden = true` pour chacune. | Utile pour intégrer une collection de marqueurs ou d’espaces réservés. |
| **Visibilité conditionnelle** | Utilisez `shape.Visible = false` conjointement avec `shape.Hidden = true` pour plus de sécurité. | Certaines versions plus anciennes de Word traitent `Visible` différemment ; définir les deux couvre tous les cas. |
| **Enregistrement dans un flux** | Remplacez `doc.Save(path)` par `doc.Save(stream, SaveFormat.Docx)`. | Permet d’envoyer le document directement via HTTP ou de le stocker dans une base de données. |
| **Application d’un style** | Après l’insertion, modifiez `ellipse.FillColor`, `ellipse.LineWeight`, etc. avant de masquer. | Le style de la forme est conservé dans le XML, ce qui peut être utile pour la démasquer ultérieurement. |

**Astuce pro :** Testez toujours la forme cachée sur la version cible de Word (par ex., Word 2019, Word 365) car des particularités de rendu peuvent apparaître lorsque des objets cachés interagissent avec des mises en page complexes.

---

## Questions fréquemment posées

**Q : Masquer une forme affecte-t-elle la taille du document ?**  
R : Le XML de la forme ajoute quelques centaines d’octets, ce qui est négligeable pour la plupart des cas d’utilisation. Le fichier reste essentiellement de la même taille qu’un document réellement vide.

**Q : Puis-je démasquer la forme plus tard par programme ?**  
R : Oui. Chargez le document, localisez la forme (`doc.GetChildNodes(NodeType.Shape, true)`) et définissez `shape.Hidden = false`.

**Q : La forme cachée apparaîtra-t-elle à l’impression ?**  
R : Non. Les objets cachés sont exclus du rendu d’impression, de sorte que la page imprimée reste vide.

**Q : Cette approche est‑elle compatible uniquement avec Office Open XML (OOXML) ?**  
R : La propriété `Hidden` fait partie de la spécification OOXML, ainsi tout processeur de texte implémentant pleinement OOXML (Word, LibreOffice, Google Docs) respectera le drapeau caché.

---

## Conclusion

Vous savez maintenant comment **créer un document Word vierge**, **créer une ellipse**, **masquer une forme dans Word**, et **créer une forme cachée** en utilisant Aspose.Words for .NET. Le tutoriel a couvert le cycle complet — de l’initialisation d’un fichier vide à l’insertion, au masquage et à l’enregistrement de la forme — ainsi que les étapes de vérification et les variantes courantes.

Ensuite, vous pourriez explorer :

* Ajouter des zones de texte cachées pour les métadonnées (technique `hide shape in word` appliquée au texte)  
* Utiliser des parties XML personnalisées pour stocker des données structurées à côté des formes cachées  
* Convertir le document contenant la forme cachée en PDF tout en préservant les éléments cachés  

Expérimentez avec différentes formes et paramètres de visibilité pour voir comment le contenu caché peut servir de stockage de données léger à l’intérieur des fichiers Word.

Bonne programmation !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités d’API supplémentaires et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Créer une forme rectangulaire dans Word avec C# – Guide étape par étape](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Créer une forme groupée dans un document Word avec Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Créer un document Word avec un rectangle ombré – Guide étape par étape](/words/english/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}