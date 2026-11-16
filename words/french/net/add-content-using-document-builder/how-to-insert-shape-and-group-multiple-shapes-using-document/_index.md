---
category: general
date: 2026-11-15
description: Apprenez à insérer une forme dans un document Word et à regrouper plusieurs
  formes avec Aspose.Words DocumentBuilder. Inclut des exemples d’insertion d’une
  forme rectangle et d’insertion de plusieurs formes.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert shape
- group multiple shapes
- insert multiple shapes
- insert rectangle shape
language: fr
lastmod: 2026-11-15
og_description: Comment insérer une forme dans un fichier Word à l’aide d’Aspose.Words.
  Ce guide couvre le regroupement de plusieurs formes, l’insertion d’une forme rectangle
  et l’ajout de plusieurs formes de manière efficace.
og_image_alt: Screenshot showing how to insert shape and group multiple shapes in
  a Word document using DocumentBuilder
og_title: Comment insérer une forme et regrouper plusieurs formes avec DocumentBuilder
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  headline: How to insert shape and group multiple shapes using DocumentBuilder in
    C#
  type: TechArticle
- description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  name: How to insert shape and group multiple shapes using DocumentBuilder in C#
  steps:
  - name: Why use a group?
    text: '* **Single‑point transformation** – rotate or resize the whole group with
      one call. * **Logical organization** – the Word document tree reflects the grouping,
      making later edits easier. * **Consistent layout** – moving the group keeps
      the relative positions of its children intact.'
  - name: Adding more shapes – extending **insert multiple shapes** inside the group
    text: 'You can keep calling `InsertShape` while the cursor remains inside the
      `GroupShape`. For example, to add a triangle:'
  - name: Expected output
    text: '* **First two shapes** – a rectangle and an ellipse placed independently
      on the page. * **Grouped block** – a rectangle, an ellipse, and a triangle that
      move together when you click any of them in Word.'
  type: HowTo
tags:
- Aspose.Words
- C#
- DocumentBuilder
- Shape handling
title: Comment insérer une forme et regrouper plusieurs formes avec DocumentBuilder
  en C#
url: /fr/net/add-content-using-document-builder/how-to-insert-shape-and-group-multiple-shapes-using-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment insérer une forme et regrouper plusieurs formes à l'aide de DocumentBuilder en C#

Si vous devez savoir **comment insérer une forme** dans un document Word avec Aspose.Words, ce guide vous montre les étapes exactes. Vous apprendrez également comment **regrouper plusieurs formes** afin qu’elles se comportent comme un seul objet, et comment **insérer une forme rectangle** aux côtés d’autres graphiques.

L’automatisation de documents nécessite souvent l’ajout de plusieurs graphiques — diagrammes, logos, encadrés — tout en les gardant organisés. À la fin de ce tutoriel, vous serez capable **d’insérer plusieurs formes**, de les placer dans un groupe, et d’enregistrer une mise en page propre et réutilisable.

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

* .NET 6.0 ou version ultérieure installé  
* Visual Studio 2022 (ou tout IDE C#)  
* Une licence Aspose.Words for .NET ou une clé d’évaluation gratuite  
* Une connaissance de base du C# et de la classe Aspose.Words `DocumentBuilder`  

Vous **n’avez pas** besoin d’autres bibliothèques tierces ; tout le nécessaire fait partie d’Aspose.Words.

## Étape 1 : Installer Aspose.Words via NuGet

Ouvrez votre projet dans Visual Studio et exécutez la commande suivante dans la console du Gestionnaire de packages :

```powershell
Install-Package Aspose.Words
```

Le package comprend les classes `DocumentBuilder`, `Shape` et `GroupShape` utilisées tout au long de ce tutoriel.

## Étape 2 : Créer une instance de DocumentBuilder – la base pour **comment insérer une forme**

La première ligne de code actionnable consiste à créer un `DocumentBuilder`. Cet objet vous donne un accès direct à l’arbre du document, vous permettant de placer les formes exactement où vous le souhaitez.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Initialise a new blank document
        Document doc = new Document();
        // Create a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // The rest of the tutorial inserts and groups shapes here …
    }
}
```

*Pourquoi c’est important* : `DocumentBuilder` maintient un curseur (le « point d’insertion »). Chaque appel suivant à `Insert…` utilise ce curseur, c’est pourquoi nous le déplaçons plus tard dans un `GroupShape` pour garder toutes les formes ensemble.

## Étape 3 : **Insérer une forme rectangle** – le premier graphique que vous ajouterez

Un rectangle est un espace réservé courant pour les tableaux, images ou encadrés. Utilisez `InsertShape` avec `ShapeType.Rectangle` et spécifiez la largeur et la hauteur en points (1 pt ≈ 1/72 in).

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

Le rectangle apparaît à l’emplacement actuel du curseur. Vous pourrez personnaliser son remplissage, son style de ligne ou son texte ultérieurement si besoin.

## Étape 4 : Insérer une autre forme – une ellipse pour varier le visuel

Ajouter plus d’une forme démontre **l’insertion de plusieurs formes**. L’ellipse sera placée après le rectangle dans le flux du document.

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

À ce stade, le document contient deux formes indépendantes. Si vous déplacez le curseur ou ajoutez du texte, les formes restent à l’endroit où elles ont été insérées.

## Étape 5 : **Regrouper plusieurs formes** afin qu’elles agissent comme une seule unité

Le regroupement est essentiel lorsque vous devez déplacer, faire pivoter ou formater plusieurs graphiques ensemble. Le code suivant crée un `GroupShape`, déplace le curseur du builder à l’intérieur, puis insère à nouveau les mêmes formes — cette fois elles deviennent des enfants du groupe.

```csharp
// 1️⃣ Create a GroupShape and add it to the document tree
GroupShape group = new GroupShape(builder.Document);
builder.InsertNode(group);

// 2️⃣ Position the cursor inside the group so new inserts go into it
builder.MoveTo(group);

// 3️⃣ Insert a rectangle shape inside the group
builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Insert an ellipse shape inside the same group
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

### Pourquoi utiliser un groupe ?

* **Transformation à point unique** – faites pivoter ou redimensionnez tout le groupe en un seul appel.  
* **Organisation logique** – l’arbre du document Word reflète le regroupement, ce qui facilite les modifications ultérieures.  
* **Mise en page cohérente** – déplacer le groupe conserve les positions relatives de ses enfants.

### Ajouter d’autres formes – étendre **l’insertion de plusieurs formes** à l’intérieur du groupe

Vous pouvez continuer à appeler `InsertShape` tant que le curseur reste à l’intérieur du `GroupShape`. Par exemple, pour ajouter un triangle :

```csharp
builder.InsertShape(ShapeType.Triangle, 60, 60);
```

Chaque appel respecte le contexte du groupe, de sorte que le triangle devient automatiquement partie du même ensemble groupé.

## Étape 6 : Enregistrer le document et vérifier le résultat

Après avoir placé toutes les formes, persistez le document dans un fichier `.docx`. L’ouverture du fichier dans Microsoft Word (ou tout visualiseur compatible) doit afficher deux formes séparées suivies d’un ensemble groupé contenant le même rectangle, ellipse et triangle.

```csharp
// Save the document
doc.Save("GroupedShapesDemo.docx");
```

### Résultat attendu

* **Premières deux formes** – un rectangle et une ellipse placés indépendamment sur la page.  
* **Bloc groupé** – un rectangle, une ellipse et un triangle qui se déplacent ensemble lorsque vous cliquez sur l’une d’elles dans Word.

Vous pouvez tester le regroupement en sélectionnant n’importe quelle forme du groupe ; Word mettra en surbrillance l’ensemble complet, confirmant que l’opération **regrouper plusieurs formes** a réussi.

## Problèmes courants et astuces professionnelles

| Problème | Pourquoi cela se produit | Solution |
|----------|--------------------------|----------|
| Les formes apparaissent en dehors de la page prévue | Le curseur du builder n’a pas été déplacé dans le `GroupShape` avant l’insertion. | Appelez toujours `builder.MoveTo(group)` **avant** tout appel `InsertShape` appartenant au groupe. |
| Le groupe disparaît après l’enregistrement | Le groupe a été inséré sans être ajouté à la collection de nœuds du document. | Utilisez `builder.InsertNode(group)` immédiatement après la création du `GroupShape`. |
| Taille inattendue à cause du DPI du document | Aspose.Words utilise des points ; si vous pensez en pixels, les dimensions peuvent ne pas correspondre. | Convertissez les pixels en points (`points = pixels * 72 / 96`) ou travaillez directement en points. |
| Les formes se chevauchent involontairement | Aucun positionnement explicite n’a été défini ; Word les place séquentiellement. | Définissez `Shape.Left` et `Shape.Top` après l’insertion pour contrôler le placement exact. |

**Astuce pro** : après le regroupement, vous pouvez récupérer la collection `Shapes` du groupe (`group.Shapes`) pour itérer, renommer ou appliquer un formatage en masse.

## Étape 7 : Étendre l’exemple – quelles suites ?

Maintenant que vous savez **comment insérer une forme**, **insérer une forme rectangle**, et **regrouper plusieurs formes**, vous pouvez explorer :

* **Animer les formes groupées** – définissez des propriétés de rotation ou de retournement sur le groupe.  
* **Appliquer des styles** – utilisez `Shape.FillColor`, `Shape.LineFormat` ou `Shape.TextBox` pour ajouter des libellés.  
* **Exporter en PDF** – la même mise en page groupée s’affiche correctement lorsque vous appelez `doc.Save("output.pdf")`.  

Toutes ces extensions réutilisent le même flux de travail `DocumentBuilder`, gardant votre code propre et maintenable.

## Conclusion

Ce tutoriel a démontré **comment insérer une forme** dans un document Word avec Aspose.Words, comment **insérer une forme rectangle**, et comment **regrouper plusieurs formes** afin qu’elles se comportent comme un seul objet. En suivant le code pas à pas, vous pouvez insérer de façon fiable **plusieurs formes**, les organiser en groupes, et produire des documents de qualité professionnelle de façon programmatique.

N’hésitez pas à expérimenter avec différents types de formes, couleurs et transformations de groupe. Lorsque vous serez prêt, intégrez ce modèle dans des solutions de reporting ou de templating plus larges pour automatiser des mises en page de documents complexes. Bon codage !

## Que devez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [How to create and insert ellipse and rectangle shapes inside a group shape in a Word document using Aspose.Words](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [How to group shapes in a Word document using Aspose.Words](/words/english/java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}