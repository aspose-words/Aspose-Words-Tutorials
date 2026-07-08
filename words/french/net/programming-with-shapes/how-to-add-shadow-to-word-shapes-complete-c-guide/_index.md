---
category: general
date: 2026-06-30
description: Comment ajouter une ombre en C# avec Aspose.Words. Apprenez à changer
  la couleur de l'ombre, ajuster la transparence de l'ombre, ajouter une ombre à une
  forme et enregistrer le document modifié.
draft: false
keywords:
- how to add shadow
- change shadow color
- save modified document
- add shadow to shape
- adjust shadow transparency
language: fr
og_description: Comment ajouter une ombre en C# avec Aspose.Words. Ce tutoriel montre
  comment ajouter une ombre à une forme, changer la couleur de l’ombre, ajuster la
  transparence de l’ombre et enregistrer le document modifié.
og_title: Comment ajouter une ombre aux formes Word – Guide complet C#
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: How to add shadow in C# using Aspose.Words. Learn to change shadow
    color, adjust shadow transparency, add shadow to shape, and save modified document.
  headline: How to Add Shadow to Word Shapes – Complete C# Guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: Comment ajouter une ombre aux formes Word – Guide complet C#
url: /fr/net/programming-with-shapes/how-to-add-shadow-to-word-shapes-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment ajouter une ombre aux formes Word – Guide complet en C#

Vous vous êtes déjà demandé **comment ajouter une ombre** à une forme Word avec C# ? Vous n'êtes pas le seul. Les développeurs ont souvent besoin de cet effet de profondeur subtil pour des rapports, des brochures ou tout document qui doit paraître un peu plus soigné. Bonne nouvelle : avec quelques lignes de code, vous pouvez activer une ombre, ajuster sa couleur et même modifier sa transparence — le tout en conservant un flux de travail entièrement automatisé.

Dans ce tutoriel, nous verrons **comment ajouter une ombre** à une forme, **modifier la couleur de l'ombre**, **ajuster la transparence de l'ombre**, puis **enregistrer le document modifié** afin que les changements persistent. À la fin, vous disposerez d’un extrait réutilisable que vous pourrez intégrer à n’importe quel projet Aspose.Words.

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

* **Aspose.Words for .NET** (version 23.11 ou plus récente). Vous pouvez l’obtenir via NuGet avec `Install-Package Aspose.Words`.
* Un environnement de développement **.NET 6+** (Visual Studio, Rider ou VS Code).
* Un fichier Word d’entrée (`input.docx`) contenant déjà au moins une forme (par ex. un rectangle, une étoile ou une image).

C’est tout — aucune bibliothèque supplémentaire, aucune étape manuelle d’interface utilisateur. Prêt ? C’est parti.

## Étape 1 – Charger le document Word (Comment ajouter une ombre)

La première chose à savoir **comment ajouter une ombre**, c’est que vous devez charger le document dans un objet `Aspose.Words.Document`. Cela vous donne un accès programmatique à chaque nœud, y compris les formes.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // Load the source document that contains the shape.
        Document doc = new Document(@"C:\Docs\input.docx");
```

> **Pourquoi c’est important :** Le chargement du fichier est la porte d’entrée de toute manipulation. Sans instance `Document`, vous ne pouvez pas atteindre l’arbre des formes et donc appliquer d’une ombre.

## Étape 2 – Récupérer la forme cible (Ajouter une ombre à la forme)

Maintenant que le document est en mémoire, localisons la forme que nous voulons styliser. Cette étape montre **ajouter une ombre à la forme** pour la première forme trouvée, mais vous pouvez facilement l’étendre pour sélectionner par nom ou par indice.

```csharp
        // Retrieve the first shape in the document (searches recursively).
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

        if (shape == null)
        {
            Console.WriteLine("No shape found in the document.");
            return;
        }
```

> **Astuce :** Si votre document contient plusieurs formes, remplacez le `0` par l’indice approprié ou parcourez `doc.GetChildNodes(NodeType.Shape, true)`.

## Étape 3 – Activer l’ombre et configurer son apparence (Modifier la couleur de l’ombre & Ajuster la transparence de l’ombre)

Voici le cœur de **comment ajouter une ombre** : nous activons l’ombre, définissons son décalage, son flou, sa couleur et sa transparence. N’hésitez pas à expérimenter avec les valeurs numériques pour obtenir exactement le rendu souhaité.

```csharp
        // Turn the shadow on.
        shape.ShadowFormat.Visible = true;

        // Position the shadow 4 points to the right and 4 points down.
        shape.ShadowFormat.OffsetX = 4; // Horizontal offset in points.
        shape.ShadowFormat.OffsetY = 4; // Vertical offset in points.

        // Adjust shadow transparency – this demonstrates **adjust shadow transparency**.
        shape.ShadowFormat.Transparency = 0.3; // 30 % transparent.

        // Change the shadow color – this is the **change shadow color** part.
        shape.ShadowFormat.Color = Color.Gray; // You can use any System.Drawing.Color.

        // Add a subtle blur to soften the edges.
        shape.ShadowFormat.BlurRadius = 5; // Blur radius in points.
```

> **Pourquoi ces paramètres ?**  
> *`Visible`* active l’effet.  
> *`OffsetX`/`OffsetY`* simulent une source de lumière, donnant de la profondeur.  
> *`Transparency`* vous permet d’éclaircir ou d’assombrir l’ombre sans changer la couleur — une façon classique **d’ajuster la transparence de l’ombre**.  
> *`Color`* vous permet **de changer la couleur de l’ombre** ; le gris convient à la plupart des documents professionnels, mais vous pouvez utiliser `Color.Black` ou toute couleur personnalisée via `Color.FromArgb(...)`.  
> *`BlurRadius`* ajoute du réalisme — des ombres nettes paraissent artificielles.

## Étape 4 – Enregistrer le document modifié (Enregistrer le document modifié)

Enfin, nous persistons les changements. Cette étape répond à **enregistrer le document modifié** sans aucune intervention manuelle.

```csharp
        // Save the updated document to a new file.
        doc.Save(@"C:\Docs\output.docx");

        Console.WriteLine("Shadow applied and document saved successfully.");
    }
}
```

> **Que se passe‑t‑il en coulisses ?** Aspose.Words écrit les parties XML mises à jour, y compris l’élément `<w:shadow>` avec tous les attributs que vous venez de définir. Le fichier `output.docx` résultant s’ouvrira dans Word avec l’ombre déjà appliquée.

## Exemple complet fonctionnel

En réunissant tous les morceaux, voici le programme complet, prêt à copier‑coller :

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the shape.
        Document doc = new Document(@"C:\Docs\input.docx");

        // 2️⃣ Retrieve the first shape (add shadow to shape).
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found in the document.");
            return;
        }

        // 3️⃣ Enable the shadow and configure its appearance.
        shape.ShadowFormat.Visible = true;
        shape.ShadowFormat.OffsetX = 4;
        shape.ShadowFormat.OffsetY = 4;
        shape.ShadowFormat.Transparency = 0.3;      // Adjust shadow transparency.
        shape.ShadowFormat.Color = Color.Gray;      // Change shadow color.
        shape.ShadowFormat.BlurRadius = 5;

        // 4️⃣ Save the modified document (save modified document).
        doc.Save(@"C:\Docs\output.docx");

        Console.WriteLine("Shadow applied and document saved successfully.");
    }
}
```

### Résultat attendu

Ouvrez `output.docx` dans Microsoft Word. La première forme présente dans `input.docx` affichera désormais une ombre grise douce, décalée de 4 pt, avec 30 % de transparence et un léger flou. Le reste du document reste inchangé.

## Variantes courantes & cas limites

| Situation | Ce qu’il faut ajuster | Pourquoi |
|-----------|-----------------------|----------|
| **Formes multiples** | Parcourir `doc.GetChildNodes(NodeType.Shape, true)` et appliquer les mêmes paramètres à chaque forme. | Garantit que chaque graphique obtient la même profondeur visuelle. |
| **Couleurs d’ombre différentes** | Utiliser `shape.ShadowFormat.Color = Color.FromArgb(255, 100, 100);` pour une teinte rougeâtre. | Permet d’harmoniser avec la charte graphique ou le thème. |
| **Pas d’ombre pour une forme particulière** | Ignorer la forme en fonction de `shape.Name` ou `shape.ShapeType`. | Évite les effets indésirables sur les logos ou icônes. |
| **Transparence plus élevée** | Définir `Transparency = 0.7` pour une ombre très légère. | Utile pour des arrière‑plans subtils. |
| **Performance sur de gros documents** | Charger le document avec `LoadOptions` qui ignorent les polices inutiles. | Réduit l’empreinte mémoire lors du traitement de nombreux fichiers. |

## Astuces & conseils (Pro Tips)

* **Pro tip :** Si vous avez besoin d’une *ombre portée* qui imite Photoshop, augmentez `BlurRadius` à 10‑12 et réglez `Transparency` à 0.2 pour un rendu plus net.  
* **Attention à :** Les formes *en ligne* vs *flottantes*. Les formes en ligne héritent du format du paragraphe et leur ombre peut ne pas s’afficher de la même façon. Utilisez `shape.IsInline` pour décider si vous devez d’abord les convertir en forme flottante.  
* **Méthode réutilisable :** Encapsulez la logique d’ombre dans une méthode d’assistance :

```csharp
static void ApplyShadow(Shape s, int offset = 4, double transparency = 0.3,
                        Color? color = null, int blur = 5)
{
    s.ShadowFormat.Visible = true;
    s.ShadowFormat.OffsetX = offset;
    s.ShadowFormat.OffsetY = offset;
    s.ShadowFormat.Transparency = transparency;
    s.ShadowFormat.Color = color ?? Color.Gray;
    s.ShadowFormat.BlurRadius = blur;
}
```

Vous pouvez alors appeler `ApplyShadow(shape);` partout où cela est nécessaire.

## Conclusion

Nous venons de couvrir **comment ajouter une ombre** à une forme Word avec C#. Les étapes vous ont montré comment **ajouter une ombre à la forme**, **modifier la couleur de l’ombre**, **ajuster la transparence de l’ombre**, puis **enregistrer le document modifié**. Avec ces connaissances, vous pouvez enrichir n’importe quel rapport automatisé, brochure marketing ou mémo interne d’une touche visuelle professionnelle.

Et après ? Essayez de combiner cela avec d’autres fonctionnalités de mise en forme — comme les remplissages en dégradé ou les effets 3‑D — pour créer des documents vraiment accrocheurs. Ou explorez l’API Aspose.Words pour les tableaux, graphiques et la fusion‑mail afin de bâtir des pipelines de documents de bout en bout.

Vous avez une question sur un type de forme spécifique ou besoin d’appliquer des ombres de façon conditionnelle ? Laissez un commentaire ci‑dessous, et poursuivons la discussion. Bon codage !

## Que devez‑vous apprendre ensuite ?

Les tutoriels suivants abordent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Add Text Watermark in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-watermark/add-text-watermark/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}