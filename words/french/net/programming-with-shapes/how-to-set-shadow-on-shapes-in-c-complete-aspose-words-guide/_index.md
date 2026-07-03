---
category: general
date: 2026-07-03
description: Comment définir une ombre sur une forme en C# avec Aspose.Words. Apprenez
  à ajouter une ombre à une forme, modifier le flou, ajuster la transparence et enregistrer
  le document au format PDF.
draft: false
keywords:
- how to set shadow
- add shadow to shape
- save document as pdf
- how to change blur
- how to adjust transparency
language: fr
og_description: Comment définir une ombre sur une forme en C# avec Aspose.Words. Ce
  guide montre comment ajouter une ombre à une forme, modifier le flou, ajuster la
  transparence et enregistrer le document au format PDF.
og_title: Comment appliquer une ombre aux formes en C# – Tutoriel complet Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: How to set shadow on a shape in C# using Aspose.Words. Learn to add
    shadow to shape, change blur, adjust transparency, and save document as PDF.
  headline: How to Set Shadow on Shapes in C# – Complete Aspose.Words Guide
  type: TechArticle
- description: How to set shadow on a shape in C# using Aspose.Words. Learn to add
    shadow to shape, change blur, adjust transparency, and save document as PDF.
  name: How to Set Shadow on Shapes in C# – Complete Aspose.Words Guide
  steps:
  - name: – Load the Word Document
    text: '```csharp using System; using System.Drawing; // For Color using Aspose.Words;
      using Aspose.Words.Drawing; // Shape and shadow types'
  - name: – Retrieve the Target Shape
    text: '```csharp // Grab the first shape in the document (index 0). Shape shape
      = (Shape)doc.GetChild(NodeType.Shape, 0, true); if (shape == null) { Console.WriteLine("No
      shape found – make sure your .docx contains a drawing."); return; } ```'
  - name: – Add Shadow to Shape (Core of “how to set shadow”)
    text: '```csharp // Enable shadow and set its basic properties. shape.ShadowFormat.Visible
      = true; // Turn the shadow on. shape.ShadowFormat.Distance = 4.0; // Distance
      from the shape (in points). shape.ShadowFormat.BlurRadius = 6.0; // Softness
      of the shadow. shape.ShadowFormat.Transparency = 0.3; // 30 %'
  - name: – How to Change Blur on the Shadow
    text: '```csharp // Increase blur for a softer look, or decrease for a crisp edge.
      shape.ShadowFormat.BlurRadius = 12.0; // Example of a heavier blur. ```'
  - name: – How to Adjust Transparency of the Shadow
    text: '```csharp // Make the shadow more subtle. shape.ShadowFormat.Transparency
      = 0.6; // 60 % transparent (more see‑through). ```'
  - name: – Save Document as PDF to View the Shadow Effect
    text: '```csharp // Export the modified document to PDF so you can see the shadow.
      doc.Save("YOUR_DIRECTORY/ShadowAdjusted.pdf", SaveFormat.Pdf); Console.WriteLine("PDF
      saved – open ShadowAdjusted.pdf to see the shadow."); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- PDF generation
title: Comment appliquer une ombre aux formes en C# – Guide complet d’Aspose.Words
url: /fr/net/programming-with-shapes/how-to-set-shadow-on-shapes-in-c-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment définir une ombre sur les formes en C# – Guide complet Aspose.Words

Vous êtes-vous déjà demandé **comment définir une ombre** sur une forme lors de la génération de documents de façon programmatique ? D’après mon expérience, la touche visuelle d’une ombre subtile peut transformer un diagramme fade en quelque chose qui *saute* réellement à la page. La bonne nouvelle ? Avec Aspose.Words, vous pouvez **ajouter une ombre à une forme** en quelques lignes de code C#, ajuster le flou, contrôler la transparence, puis **enregistrer le document au format PDF** pour voir l’effet immédiatement.

Dans ce tutoriel, nous passerons en revue chaque étape nécessaire pour maîtriser le style d’ombre : charger un fichier Word, localiser une forme, configurer son `ShadowFormat`, et enfin exporter le résultat en PDF. À la fin, vous saurez **comment modifier le flou**, comprendrez **comment ajuster la transparence**, et disposerez d’un extrait prêt à l’emploi que vous pourrez intégrer dans n’importe quel projet .NET.

## Comment définir une ombre sur une forme dans Aspose.Words

La première chose dont vous avez besoin est une référence à la bibliothèque Aspose.Words. Si vous ne l’avez pas encore installée, exécutez :

```bash
dotnet add package Aspose.Words
```

Passons maintenant au code. Nous décomposerons le processus en étapes faciles à suivre afin que vous puissiez voir exactement pourquoi chaque ligne est importante.

### Étape 1 – Charger le document Word

```csharp
using System;
using System.Drawing;               // For Color
using Aspose.Words;
using Aspose.Words.Drawing;        // Shape and shadow types

// Load a document that already contains at least one shape.
Document doc = new Document("YOUR_DIRECTORY/Shapes.docx");
```

*Pourquoi c’est important :*  
`Document` est le point d’entrée pour chaque opération dans Aspose.Words. En chargeant un fichier qui possède déjà une forme, nous évitons le code supplémentaire nécessaire pour créer une forme à partir de zéro — idéal pour une démonstration ciblée « comment définir une ombre ».

### Étape 2 – Récupérer la forme cible

```csharp
// Grab the first shape in the document (index 0). 
Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
if (shape == null)
{
    Console.WriteLine("No shape found – make sure your .docx contains a drawing.");
    return;
}
```

*Que se passe-t-il ici ?*  
`GetChild` parcourt l’arbre DOM et renvoie le premier nœud de type `Shape`. Le drapeau `true` indique à l’API de rechercher de façon récursive, ce qui est pratique lorsque la forme se trouve dans un en‑tête, un pied de page ou une zone de texte.

### Étape 3 – Ajouter une ombre à la forme (cœur du « comment définir une ombre »)

```csharp
// Enable shadow and set its basic properties.
shape.ShadowFormat.Visible = true;          // Turn the shadow on.
shape.ShadowFormat.Distance = 4.0;          // Distance from the shape (in points).
shape.ShadowFormat.BlurRadius = 6.0;        // Softness of the shadow.
shape.ShadowFormat.Transparency = 0.3;      // 30 % transparent.
shape.ShadowFormat.Color = Color.Black;    // Shadow color.
```

**Comment ajouter une ombre à une forme** – c’est la ligne que vous cherchiez. Mettre `Visible` à `true` active l’effet ; le reste affine son apparence. N’hésitez pas à expérimenter avec d’autres couleurs ou distances pour correspondre à votre charte graphique.

#### Astuce pro
Si vous avez besoin d’une ombre portée qui imite une source de lumière provenant du haut‑gauche, définissez également `shape.ShadowFormat.Angle = 45;` et `shape.ShadowFormat.Distance = 2.0;`. Cette petite modification ajoute du réalisme sans code supplémentaire.

### Étape 4 – Comment modifier le flou de l’ombre

```csharp
// Increase blur for a softer look, or decrease for a crisp edge.
shape.ShadowFormat.BlurRadius = 12.0;   // Example of a heavier blur.
```

Modifier directement le `BlurRadius` répond à **comment modifier le flou**. La valeur est exprimée en points ; des nombres plus élevés produisent une ombre plus diffusée. Gardez à l’esprit que des valeurs de flou très élevées peuvent légèrement augmenter la taille du fichier PDF, car le rendu doit stocker plus d’informations graphiques.

### Étape 5 – Comment ajuster la transparence de l’ombre

```csharp
// Make the shadow more subtle.
shape.ShadowFormat.Transparency = 0.6;   // 60 % transparent (more see‑through).
```

La propriété `Transparency` accepte un double compris entre `0.0` (complètement opaque) et `1.0` (totalement invisible). C’est la réponse exacte à **comment ajuster la transparence** d’une ombre de forme. Utilisez une valeur basse pour des éléments UI audacieux, une valeur plus élevée pour des décorations en arrière‑plan.

### Étape 6 – Enregistrer le document au format PDF pour visualiser l’effet d’ombre

```csharp
// Export the modified document to PDF so you can see the shadow.
doc.Save("YOUR_DIRECTORY/ShadowAdjusted.pdf", SaveFormat.Pdf);
Console.WriteLine("PDF saved – open ShadowAdjusted.pdf to see the shadow.");
```

Ici nous **enregistrons le document au format PDF**, ce qui est la méthode la plus fiable pour vérifier les changements visuels sur toutes les plateformes. Le PDF préserve le rendu exact d’Aspose.Words, contrairement à l’aperçu natif de Word qui peut masquer les effets subtils.

## Ajouter une ombre à une forme avec des paramètres personnalisés (avancé)

Parfois, vous souhaitez une ombre qui corresponde à la palette de couleurs de votre marque. Vous pouvez combiner les étapes précédentes dans une méthode réutilisable :

```csharp
/// <summary>
/// Applies a customized shadow to the provided shape.
/// </summary>
static void ApplyCustomShadow(Shape shape, double distance, double blur, double transparency, Color color)
{
    shape.ShadowFormat.Visible = true;
    shape.ShadowFormat.Distance = distance;
    shape.ShadowFormat.BlurRadius = blur;
    shape.ShadowFormat.Transparency = transparency;
    shape.ShadowFormat.Color = color;
}

// Usage example:
ApplyCustomShadow(shape, 5.0, 8.0, 0.25, Color.FromArgb(80, 0, 0, 0));
```

*Pourquoi l’encapsuler ?*  
L’encapsulation garde votre flux principal propre et vous permet **d’ajouter une ombre à une forme** avec un seul appel où que vous en ayez besoin — idéal pour le traitement par lots de dizaines de documents.

## Enregistrer le document au format PDF – Pièges courants

- **Problèmes de chemin de fichier :** Utilisez toujours des chemins absolus ou `Path.Combine` pour éviter les erreurs « file not found ».
- **Restrictions de licence :** Si vous utilisez la version d’évaluation gratuite d’Aspose.Words, le PDF généré contiendra un filigrane. Achetez une licence pour obtenir une sortie propre.
- **Inclusion des polices :** Assurez‑vous que les polices utilisées dans le `.docx` d’origine sont disponibles sur le serveur ; sinon le PDF pourra les substituer, affectant l’apparence de l’ombre.

## Modifier dynamiquement le rayon du flou (scénario réel)

Imaginez que vous génériez un catalogue où les images produit nécessitent une ombre plus marquée pour mettre en valeur. Vous pourriez calculer `BlurRadius` en fonction de la taille de l’image :

```csharp
double ComputeBlur(double imageWidth)
{
    // Larger images get a softer shadow.
    return Math.Max(4.0, imageWidth / 50.0);
}

// Later in the pipeline:
double blur = ComputeBlur(shape.Width);
shape.ShadowFormat.BlurRadius = blur;
```

Cet extrait montre **comment modifier le flou** de façon programmatique, en s’adaptant à un contenu variable sans ajustements manuels.

## Ajuster la transparence en fonction de l’arrière‑plan (conseil pratique)

Si l’arrière‑plan du document est sombre, une ombre de couleur claire sera plus visible. Voici une méthode rapide pour déterminer la transparence :

```csharp
double DetermineTransparency(Color background)
{
    // Dark backgrounds → lighter (more transparent) shadows.
    return background.GetBrightness() < 0.5 ? 0.5 : 0.2;
}

// Apply:
shape.ShadowFormat.Transparency = DetermineTransparency(Color.White);
```

Vous avez maintenant maîtrisé **comment ajuster la transparence** selon le contexte, une nuance souvent négligée dans les démonstrations rapides.

## Exemple complet fonctionnel

Ci‑dessous se trouve le programme complet, prêt à être exécuté. Copiez‑collez‑le dans une application console, remplacez `YOUR_DIRECTORY` par un vrai répertoire, et observez le PDF apparaître.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the source document.
        Document doc = new Document("YOUR_DIRECTORY/Shapes.docx");

        // 2️⃣ Find the first shape.
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found in the document.");
            return;
        }

        // 3️⃣ Apply a custom shadow (how to set shadow).
        ApplyCustomShadow(shape, distance: 4.0, blur: 10.0, transparency: 0.35, color: Color.Black);

        // 4️⃣ Save as PDF (save document as pdf) to view the result.
        doc.Save("YOUR_DIRECTORY/ShadowAdjusted.pdf", SaveFormat.Pdf);
        Console.WriteLine("Shadow applied and PDF saved successfully.");
    }

    /// <summary>
    /// Configures shadow properties for a shape.
    /// </summary>
    static void ApplyCustomShadow(Shape shape, double distance, double blur, double transparency, Color color)
    {
        shape.ShadowFormat.Visible = true;
        shape.ShadowFormat.Distance = distance;          // distance from shape
        shape.ShadowFormat.BlurRadius = blur;            // how to change blur
        shape.ShadowFormat.Transparency = transparency; // how to adjust transparency
        shape.ShadowFormat.Color = color;                // shadow color
    }
}
```

**Résultat attendu :** Ouvrez `ShadowAdjusted.pdf`. Vous verrez la forme d’origine (souvent un rectangle ou une image) rendue avec une ombre noire douce, semi‑transparente, décalée de 4 pt. Le flou doit paraître lisse, et le PDF affichera exactement ce que vous verriez dans l’aperçu d’impression de Word.

## Conclusion

Nous avons couvert **comment définir une ombre** sur une forme avec Aspose.Words, démontré **l’ajout d’ombre à une forme**, expliqué **comment modifier le flou**, montré **comment ajuster la transparence**, et enfin **enregistré le document au format PDF** pour vérifier l’effet. L’approche est modulaire, vous pouvez donc réutiliser le helper `ApplyCustomShadow` dans plusieurs projets, ajuster les paramètres à la volée, et même l’étendre pour prendre en charge plusieurs formes par document.

Prochaines étapes ? Essayez de superposer plusieurs ombres, expérimentez avec différentes couleurs, ou combinez cette technique avec le style des tableaux pour un rapport soigné. Si vous souhaitez aller plus loin dans la manipulation graphique, explorez les propriétés `ShapeBase` d’Aspose.Words comme `OutlineFormat` ou les options de rendu PDF pour un contrôle encore plus fin.

Bon codage, et que vos documents possèdent toujours la profondeur idéale !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [How to Add Shadow in C# – Complete Programming Guide](/words/english/python-net/images-shapes/how-to-add-shadow-in-c-complete-programming-guide/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}