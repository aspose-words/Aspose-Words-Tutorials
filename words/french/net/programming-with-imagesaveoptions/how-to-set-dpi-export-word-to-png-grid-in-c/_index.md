---
category: general
date: 2026-04-10
description: Comment définir le DPI lors de la conversion de Word en PNG. Apprenez
  à exporter un document Word en PNG avec une mise en page de grille personnalisée
  et une haute résolution.
draft: false
keywords:
- how to set dpi
- convert word to png
- how to export word
- export word to png
- create png grid
language: fr
og_description: Comment définir le DPI lors de l'exportation d'un document Word. Ce
  tutoriel montre comment convertir Word en PNG, exporter Word en PNG et créer une
  grille PNG avec C#.
og_title: comment régler le DPI – Guide complet pour exporter Word en PNG
tags:
- C#
- Aspose.Words
- ImageExport
title: Comment définir le DPI – Exporter Word en grille PNG en C#
url: /fr/net/programming-with-imagesaveoptions/how-to-set-dpi-export-word-to-png-grid-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# comment définir le DPI – Exporter Word en grille PNG en C#

Vous vous êtes déjà demandé **comment définir le DPI** pour une conversion Word‑vers‑PNG sans vous arracher les cheveux ? Vous n'êtes pas le seul. Dans de nombreux projets—pensez aux générateurs de rapports automatisés ou aux pipelines de miniatures—vous avez besoin d'un PNG net qui respecte un DPI spécifique, et souvent vous voulez également plusieurs pages entassées dans une seule image en grille. Dans ce guide, nous parcourrons une solution complète, prête à l’emploi, qui **convertit Word en PNG**, vous permet **d’exporter Word en PNG** avec un réglage de 300 DPI, et même **crée une grille PNG** en une seule fois.

> **Gain rapide :** À la fin de cet article, vous disposerez d’une seule ligne de C# qui prend `input.docx` et génère `output.png` à 300 DPI, disposé en une grille 2 × 2. Aucun outil supplémentaire, aucune retouche d’image manuelle.

## Ce que vous apprendrez

- Comment **définir le DPI** en utilisant Aspose.Words `ImageSaveOptions`.
- Les étapes exactes pour **exporter Word en PNG** avec une mise en page personnalisée.
- Comment **créer une grille PNG** (quatre pages par ligne/colonne) dans un seul fichier.
- Pièges courants lors de la conversion de gros documents et comment les éviter.
- Quelques variantes : exportation de pages individuelles, modification de la taille de la grille, et substitution du PNG par JPEG.

### Prérequis

| Exigence | Pourquoi c’est important |
|----------|---------------------------|
| **Aspose.Words for .NET** (v23.12 or newer) | Fournit les classes `Document` et `ImageSaveOptions` dont nous dépendons. |
| **.NET 6+** (or .NET Framework 4.7.2) | Garantit la compatibilité avec la dernière surface d’API. |
| **Basic C# knowledge** | Vous devrez comprendre les espaces de noms et les chemins de fichiers. |
| **A Word file** (`input.docx`) | Le document source que nous convertirons. |

Si vous n’avez pas encore installé Aspose.Words, exécutez :

```bash
dotnet add package Aspose.Words
```

Maintenant que le décor est planté, plongeons dans le code.

## Étape 1 – Charger le document source (comment exporter le word)

La toute première chose à faire est de charger le fichier Word en mémoire. C’est ici que **comment exporter le word** commence.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Load the source .docx
Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
```

> **Astuce pro :** Utilisez un chemin absolu ou `Path.Combine` pour éviter les surprises sur différents systèmes d’exploitation.

## Étape 2 – Configurer les options d’enregistrement d’image (comment définir le DPI & créer une grille PNG)

Voici le cœur du tutoriel. Nous indiquons à Aspose.Words exactement comment nous voulons que le PNG apparaisse : 300 DPI, format PNG, et une **mise en page en grille** qui regroupe quatre pages en une seule image.

```csharp
// Create PNG save options with a grid layout
ImageSaveOptions imgOptions = new ImageSaveOptions(SaveFormat.Png)
{
    // Arrange pages in a grid (2 columns × 2 rows = 4 pages)
    PageLayout = ImageSaveOptions.PageLayoutType.Grid,
    
    // Number of columns in the grid – 2 columns => 2 rows for 4 pages
    PageCount = 4,
    
    // Set the DPI – this is where we *how to set dpi*
    HorizontalResolution = 300,
    VerticalResolution = 300
};
```

### Pourquoi ces paramètres sont importants

- **`PageLayout = Grid`** – Sans cela, chaque page serait enregistrée comme un PNG séparé. L’option grille les fusionne, vous évitant une étape de post‑traitement.
- **`PageCount = 4`** – Contrôle le nombre de pages que la grille contiendra. Si votre document comporte plus de quatre pages, Aspose créera automatiquement des lignes supplémentaires.
- **Paramètres DPI** – `HorizontalResolution` et `VerticalResolution` sont les réglages qui répondent à la question **comment définir le DPI**. Une image de 300 DPI est prête à l’impression et apparaît nette sur les écrans Retina.

## Étape 3 – Enregistrer le document en un seul PNG (exporter le word en png)

Nous exécutons maintenant l’opération d’enregistrement. Cette ligne unique fait le travail lourd.

```csharp
// Save the document pages as one PNG image
doc.Save(@"YOUR_DIRECTORY\output.png", imgOptions);
```

Après l’exécution de cette ligne, vous trouverez `output.png` dans le dossier spécifié. Ouvrez-le, et vous devriez voir une grille 2 × 2 des quatre premières pages, chacune rendue à 300 DPI.

![exemple de comment définir le DPI](https://example.com/placeholder.png "comment définir le DPI lors de l’exportation de Word en PNG")

*Texte alternatif de l’image : comment définir le DPI lors de l’exportation de Word en PNG – montre une PNG en grille 2×2.*

## Étape 4 – Vérifier le résultat (créer une grille PNG)

Une vérification rapide évite les maux de tête plus tard. Vous pouvez confirmer programmétiquement le DPI et les dimensions :

```csharp
using System.Drawing;

// Load the generated PNG
using (Bitmap bmp = new Bitmap(@"YOUR_DIRECTORY\output.png"))
{
    Console.WriteLine($"Width: {bmp.Width}px, Height: {bmp.Height}px");
    Console.WriteLine($"Horizontal DPI: {bmp.HorizontalResolution}");
    Console.WriteLine($"Vertical DPI: {bmp.VerticalResolution}");
}
```

Si la console affiche `300` pour les deux valeurs DPI, vous avez réussi à **comment définir le DPI**. La largeur et la hauteur refléteront la taille combinée des quatre pages.

## Variations avancées

### Convertir Word en PNG – Un fichier par page

Parfois vous avez besoin de fichiers PNG séparés au lieu d’une grille. Il suffit de changer `PageLayout` en `SinglePage` et de parcourir les pages :

```csharp
for (int i = 0; i < doc.PageCount; i++)
{
    imgOptions.PageIndex = i;               // Export only this page
    imgOptions.PageLayout = ImageSaveOptions.PageLayoutType.SinglePage;
    doc.Save($@"YOUR_DIRECTORY\page_{i + 1}.png", imgOptions);
}
```

Vous avez maintenant `page_1.png`, `page_2.png`, … – parfait pour les galeries de miniatures.

### Exporter Word en PNG avec une taille de grille différente

Si vous avez besoin d’une grille 3 × 3 (neuf pages), ajustez simplement `PageCount` :

```csharp
imgOptions.PageCount = 9;          // 3 columns × 3 rows
imgOptions.PageLayout = ImageSaveOptions.PageLayoutType.Grid;
```

Aspose calculera automatiquement le nombre de lignes nécessaires.

### Remplacer PNG par JPEG (si la taille du fichier compte)

Changer le format est aussi simple que d’échanger `SaveFormat.Png` contre `SaveFormat.Jpeg`. Vous pouvez également contrôler la qualité JPEG :

```csharp
ImageSaveOptions jpegOptions = new ImageSaveOptions(SaveFormat.Jpeg)
{
    PageLayout = ImageSaveOptions.PageLayoutType.Grid,
    PageCount = 4,
    HorizontalResolution = 300,
    VerticalResolution = 300,
    JpegQuality = 90   // 0‑100, higher = better quality
};

doc.Save(@"YOUR_DIRECTORY\output.jpg", jpegOptions);
```

### Gestion des gros documents

Lorsque vous traitez des documents de plus de 100 pages, envisagez de diffuser la sortie pour éviter la pression mémoire :

```csharp
using (FileStream fs = new FileStream(@"YOUR_DIRECTORY\large_output.png", FileMode.Create))
{
    doc.Save(fs, imgOptions);
}
```

Le streaming garantit que le processus reste léger, même sur des serveurs modestes.

## Problèmes courants & comment les éviter

| Symptôme | Cause | Solution |
|----------|-------|----------|
| Le PNG apparaît flou | DPI laissé à la valeur par défaut 96 | **Définir `HorizontalResolution` et `VerticalResolution` à 300** (ou plus). |
| Seule la première page apparaît | `PageLayout` toujours réglé sur `SinglePage` | Passer à `ImageSaveOptions.PageLayoutType.Grid`. |
| Le fichier de sortie est énorme | Le format PNG à 300 DPI peut être volumineux | Utiliser JPEG avec `JpegQuality` < 90, ou réduire le DPI si la qualité d’impression n’est pas requise. |
| La grille coupe les marges de page | Gestion des marges par défaut | Ajuster `ImageSaveOptions.PageMargins` si nécessaire. |

## Récapitulatif – Ce que nous avons couvert

- **comment définir le DPI** – en configurant `HorizontalResolution` et `VerticalResolution`.
- **convertir word en png** – en utilisant `ImageSaveOptions` avec `SaveFormat.Png`.
- **comment exporter le word** – en chargeant le document avec `Document` et en appelant `Save`.
- **exporter le word en png** – une ligne unique qui produit un PNG haute résolution.
- **créer une grille png** – en définissant `PageLayout = Grid` et `PageCount` pour contrôler la mise en page.

Tout cela tient dans un extrait C# compact et autonome que vous pouvez insérer dans n’importe quel projet .NET.

## Et après ?

- Expérimentez avec **différentes valeurs de DPI** (150, 600) pour voir comment la taille du fichier évolue.
- Combinez cette approche avec **Aspose.PDF** pour fusionner la grille PNG dans un rapport PDF.
- Explorez la **conversion d’espace colorimétrique** (RGB → CMYK) si vous envoyez le PNG à une imprimerie professionnelle.
- Examinez la **sauvegarde asynchrone** (`doc.SaveAsync`) pour des applications réactives côté UI.

Des questions sur des cas particuliers—comme l’exportation de fichiers DOCX chiffrés ou la gestion des polices incorporées ? Laissez un commentaire, et je me ferai un plaisir d’approfondir.

*Bon codage ! Si ce tutoriel vous a aidé à **comment définir le DPI** et à exporter vos documents Word en une élégante grille PNG, donnez‑lui une étoile ou partagez‑le avec un collègue qui rencontre le même problème.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}