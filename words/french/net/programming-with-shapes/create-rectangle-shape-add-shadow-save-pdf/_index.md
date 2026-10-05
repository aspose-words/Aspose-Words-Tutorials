---
category: general
date: 2026-02-24
description: Créer une forme rectangulaire en C# avec Aspose.Words, ajouter une ombre
  à la forme et enregistrer le document au format PDF. Apprenez comment ajouter une
  ombre et comment enregistrer un PDF en quelques minutes.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- how to save pdf
language: fr
og_description: Créer une forme rectangulaire en C# avec Aspose.Words, puis ajouter
  une ombre à la forme et enregistrer le document au format PDF – un guide complet,
  étape par étape.
og_title: Créer une forme rectangulaire, ajouter une ombre et enregistrer le PDF
tags:
- Aspose.Words
- C#
- PDF generation
title: Créer une forme rectangulaire, ajouter une ombre et enregistrer le PDF
url: /fr/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer une forme rectangulaire, ajouter une ombre et enregistrer en PDF

Vous avez déjà eu besoin de **créer une forme rectangulaire** dans un document Word tout en souhaitant une belle ombre portée et une sortie PDF ? Vous n'êtes pas le seul. Dans de nombreux projets de reporting ou de génération de factures, la finition visuelle — comme une ombre subtile — fait la différence entre « un simple fichier » et « un document de qualité professionnelle ».

Dans ce tutoriel, nous allons passer en revue exactement cela : utiliser **Aspose.Words for .NET** pour créer une forme rectangulaire, ajouter une ombre à la forme, et enfin **enregistrer le document en PDF**. À la fin, vous disposerez d’une application console C# prête à l’emploi qui génère un PDF avec un rectangle ombré, et vous comprendrez comment ajuster l’ombre ou modifier les options d’exportation.

## Ce dont vous avez besoin

- .NET 6 SDK (ou toute version récente de .NET) – l’API fonctionne de la même façon sur .NET Framework 4.x également.  
- Package NuGet Aspose.Words for .NET (`Aspose.Words`) – installez‑le avec `dotnet add package Aspose.Words`.  
- Un éditeur de code – Visual Studio, VS Code ou Rider convient.  

Aucune étape de licence supplémentaire pour cet exemple ; le mode d’évaluation gratuit suffit pour voir la sortie PDF.

## Étape 1 : Configurer le projet et importer les espaces de noms

Tout d’abord, créons un projet console et importons les classes dont nous aurons besoin.

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The rest of the code lives here – see the following steps.
        }
    }
}
```

*Pourquoi c’est important :* `Document` et `DocumentBuilder` nous fournissent la toile, tandis que `Shape` et `ShadowFormat` nous permettent de dessiner et de styliser le rectangle. Les importer dès le départ garde le code ultérieur propre.

## Étape 2 : **Créer une forme rectangulaire** avec les dimensions souhaitées

Nous créons maintenant réellement un document vierge et y insérons un rectangle. Notez comment la méthode `InsertShape` renvoie un objet `Shape` que nous pouvons styliser immédiatement.

```csharp
// Inside Main()
Document document = new Document();               // blank Word document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle of 200x100 points (≈2.78" × 1.39")
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
rectangle.FillColor = System.Drawing.Color.LightBlue;
```

*Explication* : La taille est exprimée en points (1 pt = 1/72 in). Ajustez les nombres pour correspondre à votre mise en page. Nous donnons également à la forme un remplissage bleu clair pour faire ressortir l’ombre.

## Étape 3 : **Ajouter une ombre à la forme** – affiner l’effet

Une ombre n’est pas simplement « activée/désactivée ». Vous pouvez contrôler sa couleur, son flou, sa distance, sa direction, et même sa transparence. Voici une configuration pratique qui fonctionne bien pour la plupart des rapports.

```csharp
// Access the shape's shadow format
ShadowFormat shadow = rectangle.ShadowFormat;
shadow.Visible = true;                     // turn the shadow on
shadow.Color = System.Drawing.Color.Gray;  // shadow colour
shadow.BlurRadius = 5.0;                    // soft edges (higher = blurrier)
shadow.Distance = 4.0;                      // how far the shadow is from the shape
shadow.Direction = 45;                     // angle in degrees (45° = down‑right)
shadow.Transparency = 0.3;                  // 30 % transparent for a subtle look
```

*Pourquoi vous pourriez modifier ces valeurs :*
- **BlurRadius** – augmentez pour un effet flou, diminuez pour un bord net.  
- **Direction** – 0° pointe vers la droite, 90° vers le bas, 180° vers la gauche, etc. Faites pivoter pour correspondre à la mise en page de votre page.  
- **Transparency** – définissez à `0` pour une ombre solide, `0.5` pour semi‑transparent, etc.

### Comment ajouter une ombre – approches alternatives

Si vous avez besoin d’une **ombre à plusieurs couches** (par ex., une ombre extérieure plus sombre plus une intérieure plus claire), vous pouvez créer une seconde forme, la décaler, et définir un `ShadowFormat` différent. Ou, pour un rendu rapide « sans flou », définissez `BlurRadius = 0`.

## Étape 4 : **Enregistrer le document en PDF** – l’exportation finale

Avec le rectangle et son ombre prêts, la dernière étape consiste à enregistrer le fichier au format PDF. Aspose.Words gère la conversion en interne ; il suffit d’appeler `Save` avec le format souhaité.

```csharp
// Define the output path – adjust to your environment
string outputPath = @"C:\Temp\ShadowRectangle.pdf";

// Save as PDF (the format is inferred from the extension)
document.Save(outputPath);
Console.WriteLine($"PDF saved to {outputPath}");
```

*Astuce* : Si vous devez contrôler la conformité du PDF (PDF/A, PDF/X) ou incorporer des polices, utilisez une surcharge :

```csharp
PdfSaveOptions options = new PdfSaveOptions
{
    Compliance = PdfCompliance.PdfA1b,
    EmbedFullFonts = true
};
document.Save(outputPath, options);
```

C’est la partie **comment enregistrer le pdf** en bref.

## Exemple complet, exécutable

Ci-dessous le programme complet que vous pouvez copier‑coller dans `Program.cs`. Il compile et s’exécute tel quel (assurez‑vous simplement que le dossier de sortie existe).

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank document and a builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert a rectangle shape
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // 3️⃣ Add a shadow to the shape
            ShadowFormat shadow = rectangle.ShadowFormat;
            shadow.Visible = true;
            shadow.Color = System.Drawing.Color.Gray;
            shadow.BlurRadius = 5.0;
            shadow.Distance = 4.0;
            shadow.Direction = 45;
            shadow.Transparency = 0.3;

            // 4️⃣ Save the document as PDF
            string outputPath = @"C:\Temp\ShadowRectangle.pdf";
            document.Save(outputPath);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

### Résultat attendu

Ouvrez le fichier `ShadowRectangle.pdf` généré. Vous verrez une page unique avec un rectangle bleu clair, une ombre gris doux décalée de 45° vers le bas‑droite, et des bords nets. Le PDF doit être lisible dans n’importe quel lecteur moderne (Adobe Acrobat, Edge, Chrome).

![Créer une forme rectangulaire avec ombre dans le PDF](/images/shadow-rectangle.png "Créer une forme rectangulaire avec ombre dans le PDF")

*(Le texte alternatif de l’image inclut le mot‑clé principal pour le SEO.)*

## Questions fréquentes & gestion des cas limites

**Que faire si l’ombre disparaît dans le PDF ?**  
Assurez‑vous d’utiliser une version récente d’Aspose.Words (≥23.3). Les versions antérieures comportaient un bug où certaines propriétés d’ombre étaient ignorées lors de la conversion en PDF.

**Puis‑je changer la couleur de l’ombre pour correspondre à ma marque ?**  
Absolument — il suffit de remplacer `System.Drawing.Color.Gray` par n’importe quelle `Color` de votre choix, par ex., `Color.FromArgb(128, 0, 0, 255)` pour un bleu semi‑transparent.

**Comment ajouter une ombre à d’autres formes (ellipse, étoile, etc.) ?**  
Le même `ShadowFormat` fonctionne pour tout objet `Shape`. Après avoir créé la forme, récupérez son `ShadowFormat` et définissez les propriétés.

**Qu’en est‑il des problèmes de DPI ou de mise à l’échelle ?**  
Le rendu PDF respecte la taille en points de la forme. Si vous avez besoin d’une sortie à plus haute résolution (pour l’impression), ajustez les dimensions de la forme en conséquence ou définissez `PdfSaveOptions.ImageResolution`.

**Puis‑je exporter vers d’autres formats, comme PNG ?**  
Oui—il suffit d’appeler `document.Save("output.png", SaveFormat.Png)`. L’ombre sera rendue de la même façon.

## Astuces pro & bonnes pratiques

- **Réutilisez le builder** : Si vous ajoutez plusieurs formes, conservez une seule instance de `DocumentBuilder` ; c’est moins coûteux que d’en créer plusieurs.  
- **Enregistrement par lots** : Lors de la génération de nombreux PDF dans une boucle, réutilisez l’objet `PdfSaveOptions` pour éviter des allocations répétées.  
- **Tests** : Ouvrez toujours le PDF après l’enregistrement pour vérifier que l’ombre apparaît comme prévu. Certains lecteurs PDF rendent les ombres légèrement différemment ; Adobe Acrobat est la référence la plus fiable.  
- **Performance** : Pour les gros documents, désactivez les sauts de page automatiques de `DocumentBuilder.InsertShape` en définissant `builder.PageSetup.DifferentFirstPageHeaderFooter = false` si vous n’en avez pas besoin.

## Conclusion

Nous avons couvert tout ce dont vous avez besoin pour **créer une forme rectangulaire**, **ajouter une ombre à la forme**, et **enregistrer le document en PDF** en utilisant Aspose.Words for .NET. Le code est compact, les concepts sont expliqués, et vous disposez maintenant d’une base solide pour expérimenter d’autres formes, styles d’ombre et options d’exportation.  

Prochaines étapes ? Essayez de remplacer le rectangle par un arrondi‑

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}