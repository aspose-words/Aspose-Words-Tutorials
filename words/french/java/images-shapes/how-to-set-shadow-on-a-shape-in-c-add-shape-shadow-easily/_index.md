---
category: general
date: 2026-04-28
description: Comment appliquer rapidement une ombre à une forme. Apprenez comment
  ajouter une ombre à une forme, définir la couleur de l'ombre et personnaliser l'ombre
  de la forme avec Aspose.Words pour .NET.
draft: false
keywords:
- how to set shadow
- add shape shadow
- set shadow color
- how to add shadow
- customize shape shadow
language: fr
og_description: Comment définir une ombre sur une forme en C# avec Aspose.Words. Guide
  étape par étape couvrant l’ajout d’ombre à une forme, la définition de la couleur
  de l’ombre et la personnalisation de l’ombre de la forme.
og_title: Comment appliquer une ombre à une forme en C# – Guide complet
tags:
- Aspose.Words
- C#
- Document Automation
title: Comment appliquer une ombre à une forme en C# – Ajoutez facilement une ombre
  à une forme
url: /fr/java/images-shapes/how-to-set-shadow-on-a-shape-in-c-add-shape-shadow-easily/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment appliquer une ombre à une forme en C# – Ajouter facilement une ombre de forme

Vous vous êtes déjà demandé **comment appliquer une ombre** à une forme sans fouiller dans d'innombrables documents API ? Vous n'êtes pas seul. De nombreux développeurs se heurtent à un mur lorsqu'ils ont besoin d'une ombre portée subtile pour faire ressortir un diagramme, mais ils ne trouvent pas d'exemple clair montrant *à la fois* le “quoi” et le “pourquoi”.

Dans ce tutoriel, nous allons parcourir l'ajout d'une ombre à une forme, la modification de la couleur de l'ombre, et le réglage fin de son flou, de son décalage et de sa transparence—le tout avec Aspose.Words pour .NET. À la fin, vous disposerez d'un extrait prêt à l'emploi que vous pourrez insérer dans n'importe quel projet C#, ainsi que de quelques astuces pour personnaliser les ombres de forme dans des scénarios plus complexes.

> **Note :** Le code fonctionne avec Aspose.Words 22.9 ou ultérieur et nécessite .NET 6+ (ou .NET Framework 4.7.2+).  

![Forme avec ombre personnalisée](shape-shadow.png "Forme avec ombre personnalisée")

## Ce que vous apprendrez

- **Ajouter une ombre à la forme** de façon programmatique à la première forme d'un document Word.  
- **Définir la couleur de l'ombre** à n'importe quel `System.Drawing.Color`.  
- **Personnaliser l'ombre de la forme** en ajustant le rayon de flou, les décalages et la transparence.  
- Comment gérer plusieurs formes et réinitialiser les paramètres d'ombre si nécessaire.  

Aucun outil externe, aucune macro Visual Basic—juste du pur C#.

---

## Prérequis

| Exigence | Pourquoi c'est important |
|----------|---------------------------|
| **Aspose.Words for .NET** (package NuGet `Aspose.Words`) | Fournit les classes `Document`, `Shape` et `ShadowFormat` utilisées dans l'exemple. |
| **.NET 6 SDK** (ou .NET Framework 4.7.2) | Garantit la compatibilité avec la dernière surface d'API. |
| **Un fichier .docx** contenant au moins une forme (par ex., un rectangle ou une image) | Le tutoriel manipule la *première* forme ; vous pouvez en créer une dans Word si vous n'en avez pas. |

Installez la bibliothèque avec :

```bash
dotnet add package Aspose.Words
```

---

## Étape par étape : comment appliquer une ombre à une forme

### 1. Charger le document Word

Nous commençons par ouvrir le fichier `.docx`. Le constructeur `Document` lit le fichier en mémoire, nous donnant un accès complet à ses nœuds.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Pourquoi ?** Charger le document est la base—sans cela, vous ne pouvez pas parcourir l'arbre des formes.

### 2. Récupérer la première forme (ou toute forme dont vous avez besoin)

Aspose.Words stocke les formes comme des nœuds de type `NodeType.SHAPE`. La méthode `GetChild` nous permet de récupérer la *n‑ème* forme ; ici nous prenons l'index 0, c’est‑à‑dire la première forme.

```csharp
// Grab the first shape in the document (depth‑first search)
Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
if (firstShape == null)
{
    throw new InvalidOperationException("No shape found in the document.");
}
```

> **Astuce pro :** Si vous devez **ajouter une ombre à la forme** à une forme spécifique, remplacez l'index par la valeur appropriée ou itérez sur `doc.GetChildNodes(NodeType.Shape, true)`.

### 3. Accéder à l'objet de formatage d'ombre

Chaque `Shape` possède une propriété `ShadowFormat` exposant tous les paramètres liés à l'ombre.

```csharp
ShadowFormat shadow = firstShape.ShadowFormat;
```

Nous pouvons maintenant commencer à ajuster l'ombre.

### 4. Définir le rayon de flou – adoucir les bords

Un rayon de flou plus grand rend l'ombre plus diffusée. La valeur est exprimée en points (1 pt ≈ 1/72 pouce).

```csharp
shadow.BlurRadius = 5.0; // 5 pt blur – looks nicely soft
```

> **Quand ajuster ?** Si votre forme est petite, un flou de 2–3 pt peut suffire ; pour de grandes bannières, augmentez à 8–10 pt.

### 5. Définir les décalages horizontaux et verticaux

Les décalages contrôlent la distance à laquelle l'ombre est déplacée par rapport à la forme. Des valeurs positives déplacent l'ombre vers la droite/bas ; des valeurs négatives la déplacent vers la gauche/haut.

```csharp
shadow.DistanceX = 3.0; // 3 pt to the right
shadow.DistanceY = 3.0; // 3 pt downwards
```

### 6. Ajuster la transparence (opacité)

`Transparency` varie de `0.0` (complètement opaque) à `1.0` (complètement invisible). Une valeur autour de `0.3` donne un rendu subtil et semi‑transparent.

```csharp
shadow.Transparency = 0.3; // 30 % transparent
```

### 7. Choisir une couleur d'ombre – **définir la couleur de l'ombre** à n'importe quel `System.Drawing.Color`

Vous pouvez choisir n'importe quelle couleur prédéfinie ou créer une couleur personnalisée avec des valeurs RVB.

```csharp
shadow.Color = Color.FromArgb(0, 120, 215); // A calm blue shade
```

Si vous préférez une ombre noire classique, utilisez simplement `Color.Black`.

### 8. Enregistrer le document modifié

Enfin, persistez les modifications. Vous pouvez écraser le fichier original ou écrire vers un nouvel emplacement.

```csharp
doc.Save("YOUR_DIRECTORY/output_with_shadow.docx");
```

---

## Exemple complet fonctionnel (Toutes les étapes en un seul bloc)

Copiez‑collez ce qui suit dans la méthode `Main` d'une application console. Il compile tel quel, à condition que le package NuGet soit installé.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1. Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first shape (add shape shadow)
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            System.Console.WriteLine("No shape found – aborting.");
            return;
        }

        // 3. Get the shadow formatting object
        ShadowFormat shadow = shape.ShadowFormat;

        // 4. Set blur radius
        shadow.BlurRadius = 5.0;

        // 5. Define offsets
        shadow.DistanceX = 3.0;
        shadow.DistanceY = 3.0;

        // 6. Adjust transparency (0 = opaque, 1 = fully transparent)
        shadow.Transparency = 0.3;

        // 7. Set shadow color (set shadow color)
        shadow.Color = Color.GetBlue(); // or any custom color

        // 8. Save the result
        doc.Save("YOUR_DIRECTORY/output_with_shadow.docx");

        System.Console.WriteLine("Shadow applied successfully!");
    }
}
```

**Résultat attendu :** Ouvrez `output_with_shadow.docx` dans Word ; la première forme affiche maintenant une ombre bleue douce, décalée de 3 pt, avec un léger flou et 30 % de transparence.

---

## Variations courantes & cas particuliers

### Ajouter des ombres à *toutes* les formes

Si votre document contient plusieurs diagrammes, vous voudrez peut‑être parcourir chaque forme :

```csharp
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
foreach (Shape s in shapes)
{
    ShadowFormat sf = s.ShadowFormat;
    sf.BlurRadius = 4.0;
    sf.DistanceX = 2.0;
    sf.DistanceY = 2.0;
    sf.Transparency = 0.25;
    sf.Color = Color.Gray;
}
```

### Réinitialiser une ombre

Parfois une forme possède déjà une ombre que vous devez supprimer. Réglez `ShadowFormat.Visible` sur `false` :

```csharp
shape.ShadowFormat.Visible = false;
```

### Utiliser une couleur personnalisée avec alpha (semi‑transparent)

```csharp
shadow.Color = Color.FromArgb(128, 255, 0, 0); // 50 % transparent red
```

### Note de compatibilité

L'API `ShadowFormat` est stable entre les versions d'Aspose.Words, mais les versions antérieures (< 19.1) utilisaient des champs `ShadowFormat` avec des conventions de nommage légèrement différentes. Visez toujours le dernier package NuGet pour de meilleurs résultats.

---

## Astuces pro pour une ombre soignée

- **Équilibrer flou et décalage :** Un flou important avec un petit décalage peut donner un effet “glowy” plutôt qu'une vraie ombre portée. Expérimentez avec `BlurRadius` × `DistanceX/Y`.
- **Faire correspondre le thème du document :** Si le fichier Word utilise un thème sombre, une ombre claire (`Color.White`) peut créer un effet de levée subtil.
- **Performance :** Modifier les ombres de centaines de formes peut ajouter quelques millisecondes par forme. Regroupez l'opération si vous traitez de gros rapports.
- **Tests :** Ouvrez le `.docx` résultant à la fois dans Word Desktop et Word Online pour vous assurer que l'ombre s'affiche de manière cohérente.

---

## Conclusion

Nous venons de couvrir **comment appliquer une ombre** à une forme avec C#. En suivant les huit étapes ci‑dessus, vous pouvez **ajouter une ombre à la forme**, **définir la couleur de l'ombre**, et **personnaliser entièrement l'ombre de la forme** pour correspondre à n'importe quel langage de design. L'exemple est autonome, fonctionne immédiatement, et vous offre une base solide pour étendre la logique à plusieurs formes, des couleurs dynamiques, ou même des paramètres définis par l'utilisateur.

Prêt pour le prochain défi ? Essayez de combiner cette technique avec **la rotation de forme**, ou générez un rapport complet où chaque graphique reçoit sa propre ombre de marque. Les possibilités sont infinies, et le code que vous venez d’apprendre constitue un excellent tremplin.

Si ce guide vous a été utile, n’hésitez pas à mettre une étoile au dépôt, laisser un commentaire, ou partager vos propres astuces de réglage d’ombre ci‑dessous. Bon codage !

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}