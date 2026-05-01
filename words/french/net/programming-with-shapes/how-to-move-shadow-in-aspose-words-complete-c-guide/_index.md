---
category: general
date: 2026-05-01
description: Comment déplacer l'ombre sur une forme dans Aspose.Words avec C#. Apprenez
  à ajouter une ombre à une forme, modifier le flou, régler la transparence et faire
  pivoter l'ombre en quelques minutes.
draft: false
keywords:
- how to move shadow
- add shadow to shape
- how to change blur
- how to set transparency
- how to rotate shadow
language: fr
og_description: Comment déplacer l’ombre sur une forme dans Aspose.Words en C#. Ce
  tutoriel vous montre comment ajouter une ombre à une forme, modifier le flou, régler
  la transparence et faire pivoter l’ombre.
og_title: Comment déplacer l’ombre dans Aspose.Words – Guide complet C#
tags:
- Aspose.Words
- C#
- Document Automation
title: Comment déplacer l’ombre dans Aspose.Words – Guide complet C#
url: /fr/net/programming-with-shapes/how-to-move-shadow-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment déplacer l'ombre dans Aspose.Words – Guide complet C#

Vous vous êtes déjà demandé **comment déplacer l'ombre** d’une forme dans un document Word sans ouvrir Word manuellement ? Dans mon travail quotidien, j’ai souvent dû ajuster l’ombre d’une forme de façon programmatique—que ce soit pour un rapport soigné ou un modèle dynamique. Bonne nouvelle : avec Aspose.Words, vous pouvez le faire en quelques lignes, et vous apprendrez également **ajouter une ombre à la forme**, **comment modifier le flou**, **comment définir la transparence**, et **comment faire pivoter l'ombre** en une seule passe.

Dans ce tutoriel, nous allons parcourir un scénario réel : charger un DOCX existant contenant déjà une forme, ajuster la position, la douceur, l’opacité et la direction de l’ombre, puis enregistrer le résultat. À la fin, vous disposerez d’un extrait réutilisable à intégrer dans n’importe quel projet .NET, et vous comprendrez l’importance de chaque propriété.

## Prérequis – Ce dont vous avez besoin avant de commencer

- **Aspose.Words for .NET** (version 23.12 ou ultérieure). Vous pouvez l’obtenir via NuGet avec `Install-Package Aspose.Words`.
- Un environnement de développement .NET 6+ (Visual Studio, VS Code, Rider—au choix).
- Un fichier Word d’entrée (`input.docx`) contenant déjà au moins une forme (un rectangle, un cercle ou une image suffit).
- Une connaissance de base de la syntaxe C#—rien de compliqué.

Si l’un de ces éléments vous manque, faites une pause et installez la bibliothèque ; le reste du guide suppose que le package est déjà référencé.

## Étape 1 : Charger le document et récupérer la forme cible – **Comment déplacer l'ombre** commence ici

La première chose à faire est de charger le document source et de localiser la forme que nous voulons modifier. Aspose.Words traite chaque objet (paragraphes, tableaux, formes) comme un nœud d’un arbre, ce qui permet de l’interroger directement.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // 📂 Load the source DOCX that already contains a shape with a shadow.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

        // 🎯 Retrieve the first shape in the document.
        // The GetChild method walks the node tree; the third argument (true) means “search deep”.
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

        // If no shape is found, bail out early.
        if (shape == null)
        {
            System.Console.WriteLine("No shape found in the document.");
            return;
        }

        // -------------------------------------------------
        // The next sections show **how to move shadow**,
        // **add shadow to shape**, **how to change blur**,
        // **how to set transparency**, and **how to rotate shadow**.
        // -------------------------------------------------
```

> **Pourquoi c’est important :** Charger le document une seule fois et réutiliser la même instance `Document` est efficace. L’appel `GetChild` est sûr car il renvoie `null` si l’indice est hors limites, ce qui nous permet de gérer les formes manquantes sans problème.

## Étape 2 : Ajuster le rayon de flou – Maîtriser **Comment modifier le flou**

Une ombre douce paraît professionnelle, tandis qu’un bord dur peut sembler bon marché. La propriété `BlurRadius` contrôle la douceur en points (1 pt ≈ 1/72 pouce). Augmentons-la à 8 pt.

```csharp
        // Increase the blur radius to soften the shadow edges.
        shape.ShadowFormat.BlurRadius = 8.0; // 8 points ≈ 0.11 inches
```

> **Astuce pro :** Le flou par défaut est de 0,5 pt. Tout ce qui dépasse 5 pt devient généralement perceptible, mais attention à ne pas exagérer — une valeur trop élevée peut donner l’impression que la forme est détachée de la page.

## Étape 3 : Définir la transparence – La réponse à **Comment définir la transparence**

La transparence détermine le degré de visibilité de l’ombre. Une valeur de `0` signifie totalement opaque ; `1` signifie complètement invisible. Pour un effet subtil, nous utiliserons `0.3` (30 % transparent).

```csharp
        // Make the shadow semi‑transparent so the shape remains visible through it.
        shape.ShadowFormat.Transparency = 0.3; // 30% transparent
```

> **Pourquoi cela peut vous intéresser :** Si la forme est sombre, une ombre totalement opaque peut masquer le texte sous‑jacent. Ajuster la transparence garde le document lisible tout en apportant de la profondeur.

## Étape 4 : Déplacer l'ombre – Le cœur de **Comment déplacer l'ombre**

La propriété `Distance` définit la distance entre l’ombre et la forme, mesurée en points. Une distance plus grande décale davantage l’ombre, créant un effet plus dramatique.

```csharp
        // Move the shadow farther from the shape for a more pronounced effect.
        shape.ShadowFormat.Distance = 4.0; // 4 points ≈ 0.055 inches
```

> **Et si vous avez besoin d’un léger décalage ?** Fixer `Distance` à `0` placera l’ombre directement derrière la forme, ce qui peut être utile pour des effets d’embossage.

## Étape 5 : Faire pivoter la source de lumière – Résoudre **Comment faire pivoter l'ombre**

Les ombres ne sont pas toujours verticales ; elles suivent l’angle de la source lumineuse. La propriété `Angle` (en degrés) fait pivoter l’ombre autour de la forme. Inclinez‑la de 45°.

```csharp
        // Rotate the light source to change the shadow direction.
        shape.ShadowFormat.Angle = 45; // 45 degrees clockwise from the vertical axis
```

> **Expérience rapide :** Essayez `90` pour une ombre à droite ou `-30` pour une ombre inclinée à gauche. Le changement visuel est immédiat.

## Étape 6 : Enregistrer le document – Voir le résultat de **Ajouter une ombre à la forme**

Maintenant que nous avons ajusté l’ombre, nous écrivons le document sur le disque. Vous pouvez écraser le fichier original ou créer un nouveau ; l’exemple utilise un nouveau fichier de sortie.

```csharp
        // Save the modified document with the adjusted shadow.
        doc.Save(@"YOUR_DIRECTORY\output.docx");

        System.Console.WriteLine("Shadow adjustments applied and saved to output.docx");
    }
}
```

> **Résultat attendu :** Ouvrez `output.docx`. L’ombre de la forme apparaîtra plus douce, légèrement décalée, semi‑transparente et inclinée à 45°. Si vous la comparez côte à côte avec `input.docx`, la différence est flagrante.

### Exemple complet (prêt à copier‑coller)

Voici le programme complet en un seul bloc. Collez‑le dans un nouveau projet console, remplacez `YOUR_DIRECTORY` par un chemin de dossier réel, puis exécutez.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // Load the source document that already contains a shape with a shadow.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

        // Retrieve the first shape in the document (the one we will modify).
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

        if (shape == null)
        {
            System.Console.WriteLine("No shape found in the document.");
            return;
        }

        // 1️⃣ Change blur – soften the edges.
        shape.ShadowFormat.BlurRadius = 8.0;

        // 2️⃣ Set transparency – make it 30% see‑through.
        shape.ShadowFormat.Transparency = 0.3;

        // 3️⃣ Move the shadow – increase distance from the shape.
        shape.ShadowFormat.Distance = 4.0;

        // 4️⃣ Rotate the shadow – change light direction.
        shape.ShadowFormat.Angle = 45;

        // Save the result.
        doc.Save(@"YOUR_DIRECTORY\output.docx");
        System.Console.WriteLine("Shadow adjustments applied and saved to output.docx");
    }
}
```

## Questions fréquentes & cas particuliers

### Et si le document contient plusieurs formes ?

Vous pouvez parcourir toutes les formes :

```csharp
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    // Apply the same shadow settings or customize per shape.
}
```

### Puis‑je ajouter une ombre à une forme qui n’en a pas encore ?

Absolument. L’objet `ShadowFormat` existe toujours ; il suffit de l’activer :

```csharp
shape.ShadowFormat.Enabled = true;
```

### Cela fonctionne‑t‑il avec les images et les SmartArt ?

Oui. Tout nœud dérivé de `Shape`—y compris les images, graphiques et SmartArt—expose `ShadowFormat`. Les mêmes propriétés s’appliquent.

### Comment contrôler la couleur de l’ombre ?

Utilisez la propriété `Color` :

```csharp
shape.ShadowFormat.Color = System.Drawing.Color.Gray;
```

### Problèmes de compatibilité ?

Aspose.Words 23.12+ prend en charge .NET 6, .NET Core 3.1 et .NET Framework 4.6.2+. L’API présentée est stable sur ces versions.

## Conclusion

Nous venons de couvrir **comment déplacer l'ombre** d’une forme avec Aspose.Words, et nous avons également démontré **ajouter une ombre à la forme**, **comment modifier le flou**, **comment définir la transparence**, et **comment faire pivoter l'ombre**. L’exemple complet et exécutable vous permet de modifier l’ombre de n’importe quelle forme en quelques secondes, donnant à vos documents un aspect poli et professionnel sans jamais ouvrir Word.

Prêt pour l’étape suivante ? Essayez de combiner ces ajustements d’ombre avec **la mise en forme conditionnelle**—par exemple, n’appliquer une ombre plus profonde qu’aux titres ou aux graphiques dépassant une certaine taille. Ou explorez les **dégradés de remplissage** pour la forme elle‑même afin de créer un design vraiment accrocheur.

Si vous rencontrez des difficultés, laissez un commentaire ci‑dessous. Bon codage, et que vos ombres tombent toujours exactement où vous le souhaitez ! 

![Diagramme montrant l’effet du déplacement d’une ombre sur une forme – exemple de déplacement d’ombre](https://example.com/images/shadow-demo.png "exemple de déplacement d’ombre")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}