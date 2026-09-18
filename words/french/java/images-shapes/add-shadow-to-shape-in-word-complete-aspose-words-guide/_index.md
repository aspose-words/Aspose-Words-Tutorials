---
category: general
date: 2026-02-18
description: Ajoutez une ombre à une forme dans Word avec Aspose.Words. Apprenez à
  modifier la couleur de l'ombre dans Word, à définir les décalages, le flou et l'opacité
  en quelques lignes seulement.
draft: false
keywords:
- add shadow to shape
- how to change shadow color in word
language: fr
og_description: Ajoutez une ombre à une forme dans Word avec Aspose.Words. Ce tutoriel
  montre comment changer la couleur de l'ombre dans Word, ajuster le flou, le décalage
  et l'opacité.
og_title: Ajouter une ombre à une forme dans Word – Guide complet d’Aspose.Words
tags:
- Aspose.Words
- C#
- Word Automation
title: Ajouter une ombre à une forme dans Word – Guide complet d’Aspose.Words
url: /fr/java/images-shapes/add-shadow-to-shape-in-word-complete-aspose-words-guide/
---

.

Check for any technical terms: Keep them English. Eg "API", "SDK", "class names". Already fine.

Translate sentences.

Let's craft.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ajouter une ombre à une forme dans Word – Guide complet Aspose.Words

Vous avez déjà eu besoin **d’ajouter une ombre à une forme** dans un document Word sans savoir par où commencer ? Vous n’êtes pas seul — les développeurs demandent souvent *comment changer la couleur de l’ombre dans Word* lorsqu’ils veulent un effet visuel supplémentaire.  

Dans ce tutoriel, nous allons parcourir un exemple concret en utilisant la bibliothèque Aspose.Words for .NET. À la fin, vous disposerez d’un programme prêt à l’emploi qui charge un DOCX, récupère la première forme et applique une ombre bleue semi‑transparente avec un flou et des décalages personnalisés. Pas de raccourcis « voir la documentation » — juste une solution complète à copier‑coller.

## Ce que vous allez apprendre

- Comment charger un document Word et localiser un nœud de forme.  
- Les appels d’API exacts pour **ajouter une ombre à une forme**.  
- Comment **changer la couleur de l’ombre dans Word**, définir le rayon de flou, les décalages X/Y et l’opacité.  
- Astuces pour gérer plusieurs formes, les ombres existantes et les versions de Word.  

### Prérequis

- .NET 6.0 ou supérieur (le code compile avec des versions antérieures, mais .NET 6 est recommandé).  
- Package NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`).  
- Une compréhension de base du C# et du modèle d’objet Word.  

Si vous avez tout cela, plongeons‑y.

---

## Étape 1 – Charger le document Word contenant la forme

Nous créons d’abord une instance `Document` pointant vers notre fichier source. Le chemin peut être absolu ou relatif à l’exécutable.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Load the DOCX that already contains at least one shape.
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Pourquoi c’est important :** La classe `Document` est le point d’entrée de toutes les opérations Aspose.Words. Charger le fichier une seule fois réduit la consommation mémoire et permet d’interroger l’arbre de nœuds efficacement.

## Étape 2 – Récupérer le premier nœud de forme

Les formes vivent dans la hiérarchie des nœuds du document. Nous demandons le premier nœud de type `NodeType.SHAPE`. Le drapeau `true` signifie « recherche en profondeur ».

```csharp
// Grab the first Shape object in the document (depth‑first search).
Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
if (firstShape == null)
{
    System.Console.WriteLine("No shape found in the document.");
    return;
}
```

> **Astuce :** Si vous devez cibler une forme précise, filtrez par `firstShape.Name` ou `firstShape.AlternativeText` au lieu de toujours prendre la première.

## Étape 3 – Obtenir l’objet ombre associé à la forme

Chaque `Shape` possède une propriété `Shadow` qui peut être `null` si aucune ombre n’existe encore. L’accéder nous donne une instance mutable de `Shadow`.

```csharp
// The Shadow object is automatically created if it doesn't exist.
Shadow shapeShadow = firstShape.Shadow;
```

> **Cas particulier :** Les anciens fichiers Word (pré‑2007) stockent parfois les ombres différemment. Aspose.Words normalise cela, de sorte que la même API fonctionne avec DOC, DOCX et même RTF.

## Étape 4 – Définir le rayon de flou (en points)

Un rayon de flou de `5.0` points donne une bordure douce sans paraître floue.

```csharp
shapeShadow.BlurRadius = 5.0;   // points
```

## Étape 5 – Définir les décalages horizontaux et verticaux

Les décalages déplacent l’ombre par rapport à la forme. Des valeurs positives déplacent vers la droite/bas ; des valeurs négatives déplacent vers la gauche/haut.

```csharp
shapeShadow.OffsetX = 3.0;      // move right 3 points
shapeShadow.OffsetY = 3.0;      // move down 3 points
```

## Étape 6 – Choisir une couleur bleue pour l’ombre  

Nous montrons ici **comment changer la couleur de l’ombre dans Word** en utilisant `System.Drawing.Color`.

```csharp
shapeShadow.Color = Color.Blue;   // any System.Drawing.Color works
```

> **Pourquoi la couleur compte :** Une ombre bleue peut donner une impression fraîche et corporative, tandis qu’un gris foncé reste plus neutre. Choisissez ce qui correspond à votre identité visuelle.

## Étape 7 – Ajuster l’opacité de l’ombre

L’opacité varie de `0.0` (invisible) à `1.0` (complètement opaque). Nous utiliserons `0.6` pour un effet subtil.

```csharp
shapeShadow.Opacity = 0.6;   // 60% opacity
```

## Étape 8 – Enregistrer le document modifié

Enfin, écrivez les modifications sur le disque. Vous pouvez écraser le fichier original ou créer un nouveau fichier.

```csharp
doc.Save("YOUR_DIRECTORY/output_with_shadow.docx");
System.Console.WriteLine("Shadow applied and document saved.");
```

### Exemple complet fonctionnel

En rassemblant le tout, voici le programme complet que vous pouvez copier, coller et exécuter :

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class AddShadowToShapeDemo
{
    static void Main()
    {
        // 1️⃣ Load the document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Find the first shape
        Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (firstShape == null)
        {
            System.Console.WriteLine("No shape found in the document.");
            return;
        }

        // 3️⃣ Get (or create) the shadow object
        Shadow shapeShadow = firstShape.Shadow;

        // 4️⃣ Set blur radius
        shapeShadow.BlurRadius = 5.0;

        // 5️⃣ Set offsets
        shapeShadow.OffsetX = 3.0;
        shapeShadow.OffsetY = 3.0;

        // 6️⃣ Change shadow color (how to change shadow color in Word)
        shapeShadow.Color = Color.Blue;

        // 7️⃣ Set opacity
        shapeShadow.Opacity = 0.6;

        // 8️⃣ Save the result
        doc.Save("YOUR_DIRECTORY/output_with_shadow.docx");
        System.Console.WriteLine("Shadow applied and document saved.");
    }
}
```

**Résultat attendu :** Ouvrez `output_with_shadow.docx` dans Microsoft Word. La première forme affiche maintenant une ombre bleue douce, décalée de 3 pt vers la droite et le bas, avec un léger flou et une opacité de 60 %.

---

## Gestion de plusieurs formes

Si votre document contient plusieurs graphiques, parcourez‑les :

```csharp
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
foreach (Shape shp in shapes)
{
    // Apply the same shadow settings to each shape
    shp.Shadow.BlurRadius = 5.0;
    shp.Shadow.OffsetX = 3.0;
    shp.Shadow.OffsetY = 3.0;
    shp.Shadow.Color = Color.Blue;
    shp.Shadow.Opacity = 0.6;
}
```

> **Remarque :** Cette approche écrase toute configuration d’ombre existante. Si vous devez conserver les paramètres d’origine, clonez d’abord l’objet `Shadow`.

## Pièges courants & Astuces

| Piège | Comment l’éviter |
|-------|-------------------|
| **`Shape` nul** – le document ne contient aucune forme. | Vérifiez toujours `null` après `GetChild`. |
| **Ombre déjà existante** – vous pourriez écraser un style personnalisé. | Lisez les propriétés actuelles de `shapeShadow` avant de les modifier. |
| **Espace couleur incorrect** – utiliser `System.Drawing.Color` avec une ancienne version de Word peut produire des teintes inattendues. | Restez sur des couleurs standard ou définissez ARGB manuellement (`Color.FromArgb(255, 0, 0, 255)`). |
| **Impact sur les performances sur de gros documents** – parcourir des milliers de nœuds peut être lent. | Utilisez `doc.GetChildNodes(NodeType.Shape, false)` si vous avez seulement besoin des formes de niveau supérieur. |

---

## Et si je veux un effet d’ombre différent ?

- **Bords durs** : définissez `BlurRadius = 0`.  
- **Décalage plus important** : augmentez `OffsetX`/`OffsetY` à 10 pt ou plus.  
- **Opacité différente** : utilisez des valeurs comme `0.3` pour une lueur légère ou `0.9` pour un rendu prononcé.  
- **Ombres en dégradé** : Aspose.Words ne prend pas en charge les ombres en dégradé directement ; il faut insérer une image avec l’effet pré‑rendu.

---

## Vérifier le résultat par programme

Parfois, vous voulez confirmer les paramètres d’ombre sans ouvrir Word :

```csharp
Shadow s = firstShape.Shadow;
System.Console.WriteLine($"Blur: {s.BlurRadius}, OffsetX: {s.OffsetX}, OffsetY: {s.OffsetY}, " +
                         $"Color: {s.Color}, Opacity: {s.Opacity}");
```

Si la console affiche les valeurs que vous avez définies, vous savez que l’appel d’API a réussi.

---

## Conclusion

Nous avons montré **comment ajouter une ombre à une forme** dans un document Word avec Aspose.Words, et démontré **comment changer la couleur de l’ombre dans Word** ainsi que le flou, le décalage et l’opacité. Le code complet et exécutable ci‑dessus vous permet d’appliquer une ombre à n’importe quelle forme en quelques secondes, tandis que les astuces supplémentaires vous protègent des erreurs courantes.  

Prêt pour le prochain défi ? Essayez d’appliquer des couleurs différentes à chaque forme, ou combinez ombres et reflets pour un effet visuel plus riche. Vous pouvez également explorer la classe `ShapeStyle` d’Aspose.Words pour ajuster l’épaisseur des lignes, les motifs de remplissage ou la rotation 3‑D.  

Si ce guide vous a été utile, partagez‑le avec vos collègues, ajoutez une étoile au dépôt Aspose.Words, ou laissez un commentaire avec vos propres expériences. Bon codage !  

![Forme Word avec ombre bleue – exemple d’ajout d’ombre à une forme](https://example.com/images/shape-shadow.png "exemple d’ajout d’ombre à une forme")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}