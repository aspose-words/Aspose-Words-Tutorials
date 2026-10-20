---
category: general
date: 2026-02-18
description: Créez une forme rectangulaire avec Aspose.Words et apprenez à ajouter
  une ombre, à définir la taille de la forme et à enregistrer le document Word en
  quelques minutes.
draft: false
keywords:
- create rectangle shape
- how to add shadow
- save word document
- set shape size
- how to create document
language: fr
og_description: Créer une forme rectangulaire dans un fichier Word, apprendre à ajouter
  une ombre, définir la taille de la forme et enregistrer le document avec Aspose.Words
  en C#.
og_title: Créer une forme rectangulaire dans Word – Tutoriel complet Aspose.Words
tags:
- Aspose.Words
- C#
- Word automation
title: Créer une forme rectangulaire dans Word avec Aspose.Words – Guide étape par
  étape
url: /fr/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer une forme rectangulaire dans Word avec Aspose.Words – Guide étape par étape

Vous avez déjà eu besoin de **créer une forme rectangulaire** dans un fichier Word sans savoir par où commencer ? Vous n'êtes pas seul — les développeurs demandent souvent « comment ajouter une ombre à une forme tout en gardant le document modifiable ? ». Dans ce tutoriel, nous répondrons à cela et vous montrerons également **comment ajouter une ombre**, **définir la taille de la forme**, et **enregistrer le document Word** en un seul flux fluide.

Nous passerons en revue tout ce dont vous avez besoin, depuis l'initialisation d'un nouveau document (oui, c’est la première étape pour **comment créer un document**) jusqu'à la persistance du *.docx* final sur le disque. Aucun référentiel externe, juste un exemple autonome que vous pouvez copier‑coller dans Visual Studio et exécuter dès aujourd'hui.

---

## Prérequis

- .NET 6+ (ou .NET Framework 4.7+). Aspose.Words fonctionne avec n'importe quel runtime .NET récent.  
- Une licence valide Aspose.Words (ou la clé d'évaluation gratuite) – sinon vous verrez un filigrane.  
- Visual Studio, Rider, ou tout éditeur C# de votre choix.  
- Connaissances de base en C# — rien de compliqué, juste la capacité d'exécuter une application console.

> **Astuce pro :** Si vous êtes sur Mac, le même code s'exécute sous .NET 6 avec VS Code—assurez‑vous simplement de référencer le package NuGet `Aspose.Words`.

---

## Étape 1 : Initialiser le document – la base de **comment créer un document**

Avant de pouvoir dessiner quoi que ce soit, il nous faut une toile vierge. Aspose.Words appelle cela un `Document`.  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Create a new blank document
Document document = new Document();
```

> **Pourquoi c’est important :** L'objet `Document` représente l'intégralité du fichier *.docx*. Toutes les formes, paragraphes et sections que vous ajoutez deviennent des enfants de cet objet. Commencer avec un document vierge garantit qu'aucun style caché n'interfère avec votre rectangle.

---

## Étape 2 : Définir le rectangle et **définir la taille de la forme**

Un rectangle n'est qu'un `Shape` avec `ShapeType.Rectangle`. Nous lui attribuerons des dimensions explicites afin qu'il apparaisse exactement comme prévu.

```csharp
// Step 2: Create a rectangular shape and define its size
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 200; // width in points (≈2.78 inches)
rectangleShape.Height = 100; // height in points (≈1.39 inches)
```

> **Ce que signifient les nombres :** Aspose.Words utilise les points (1 pt = 1/72 in). Ajustez les valeurs pour correspondre à votre mise en page ; pour une page A4 typique, 200 pt constitue une largeur confortable.

---

## Étape 3 : **Comment ajouter une ombre** – faire ressortir la forme

Les ombres donnent un indice visuel que la forme est « levée » de la page. La propriété `Shadow` vous permet de régler la couleur, la distance, la transparence et le flou.

```csharp
// Step 3: Apply a shadow to the shape
rectangleShape.Shadow.Color        = Color.Black; // Shadow color
rectangleShape.Shadow.Distance    = 5;           // Offset distance in points
rectangleShape.Shadow.Transparency = 0.4;        // 40 % transparent
rectangleShape.Shadow.BlurRadius  = 8;           // Soft edge radius
```

> **Pourquoi utiliser la transparence ?** Une ombre totalement opaque peut paraître dure. La régler à 0,4 rend l'effet subtil et professionnel.

---

## Étape 4 : Positionner le rectangle – flux en ligne avec le texte environnant

Si vous voulez que la forme se comporte comme un caractère dans un paragraphe, définissez son `WrapType` sur `Inline`. Cela maintient la mise en page prévisible, surtout lorsque le document est modifié ultérieurement.

```csharp
// Step 4: Set the shape to flow inline with the surrounding text
rectangleShape.WrapType = WrapType.Inline;
```

> **Cas particulier :** Si vous avez besoin que le rectangle flotte au-dessus du texte (par ex. un filigrane), changez `WrapType` en `Square` ou `BehindText`.

---

## Étape 5 : Insérer la forme dans le corps du document

Nous plaçons maintenant le rectangle dans le premier paragraphe. Si le document n'a pas encore de contenu, `FirstParagraph` est créé automatiquement.

```csharp
// Step 5: Insert the shape into the first paragraph of the document
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

> **Conseil :** Vous pouvez également créer un nouveau paragraphe d'abord, puis y ajouter la forme—utile lorsque vous avez besoin de texte autour.

---

## Étape 6 : **Enregistrer le document Word** – l'étape finale

Avec tout en place, la persistance du fichier se résume à une seule ligne. Choisissez n'importe quel chemin ; l'exemple utilise un espace réservé que vous devez remplacer par votre propre répertoire.

```csharp
// Step 6: Save the document with the shadowed shape
document.Save(@"C:\Temp\ShadowShape.docx");
```

> **Résultat :** Ouvrez le *.docx* généré dans Microsoft Word. Vous verrez un rectangle avec une ombre noire, 200 pt de large et 100 pt de haut, placé en ligne avec le premier paragraphe.

---

## Résultat attendu

Lorsque vous ouvrez **ShadowShape.docx**, le document affiche :

- Un seul paragraphe contenant une forme rectangulaire.  
- Le rectangle possède une ombre noire subtile décalée de 5 pt.  
- La taille de la forme correspond aux dimensions définies à l'Étape 2.  
- Aucun texte supplémentaire n'apparaît, sauf si vous l'ajoutez manuellement.

Si la forme n'apparaît pas, vérifiez que vous avez bien référencé la bonne version d'Aspose.Words et que votre licence (ou version d'essai) est active.

---

## Questions fréquentes & Variantes

| Question | Réponse |
|----------|---------|
| *Puis‑je changer la couleur de l'ombre pour autre chose que le noir ?* | Absolument—définissez `rectangleShape.Shadow.Color = Color.Blue;` ou toute autre `System.Drawing.Color`. |
| *Et si j’ai besoin d’un rectangle plus grand ?* | Ajustez les valeurs `Width` et `Height`. Rappelez‑vous qu’elles sont en points ; 72 pt = 1 in. |
| *Est‑il possible de placer la forme à une position absolue ?* | Oui—utilisez `WrapType = WrapType.Absolute` et définissez les propriétés `Top`/`Left`. |
| *Cela fonctionne‑t‑il avec .NET Core ?* | Oui. Aspose.Words est multiplateforme ; il suffit d'installer le package NuGet pour .NET Standard. |
| *Puis‑je ajouter du texte à l'intérieur du rectangle ?* | Pas directement ; il vous faudrait insérer une forme `TextBox` à la place d'un simple rectangle. |

---

## Exemple complet fonctionnel (prêt à copier‑coller)

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize a new document
        Document document = new Document();

        // 2️⃣ Create rectangle and set its size
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width  = 200;
        rectangleShape.Height = 100;

        // 3️⃣ Add a subtle black shadow
        rectangleShape.Shadow.Color         = Color.Black;
        rectangleShape.Shadow.Distance     = 5;
        rectangleShape.Shadow.Transparency = 0.4;
        rectangleShape.Shadow.BlurRadius   = 8;

        // 4️⃣ Make the shape flow inline with text
        rectangleShape.WrapType = WrapType.Inline;

        // 5️⃣ Insert the shape into the first paragraph
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // 6️⃣ Persist the file
        document.Save(@"C:\Temp\ShadowShape.docx");

        System.Console.WriteLine("Document saved successfully!");
    }
}
```

Exécutez le programme, accédez à `C:\Temp\ShadowShape.docx`, et vous verrez le rectangle avec une ombre exactement comme décrit.

---

## Conclusion

Vous savez maintenant comment **créer une forme rectangulaire** dans un fichier Word avec Aspose.Words, comment **définir la taille de la forme**, **ajouter une ombre**, et enfin **enregistrer le document Word** avec les modifications. Le processus complet—de **comment créer un document** à la persistance du résultat—se résume à quelques lignes de C# et peut être étendu à des mises en page plus complexes.

Prêt pour le prochain défi ? Essayez de remplacer le rectangle par une forme à coins arrondis, expérimentez avec différentes couleurs d'ombre, ou intégrez la forme dans une cellule de tableau. Chaque ajustement renforce les concepts de base que nous avons couverts ici.

Si ce guide vous a été utile, partagez‑le, laissez un commentaire avec vos propres variantes, ou explorez nos autres tutoriels sur l'automatisation Word, comme l'insertion d'images ou la génération de tableaux avec Aspose.Words. Bon codage !

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}