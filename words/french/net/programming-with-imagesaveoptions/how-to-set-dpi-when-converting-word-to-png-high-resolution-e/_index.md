---
category: general
date: 2026-03-19
description: Apprenez comment définir le DPI pour une exportation PNG haute résolution
  lors de la conversion de Word en PNG. Le code C# étape par étape utilisant Aspose.Words
  rend cela facile.
draft: false
keywords:
- how to set dpi
- convert word to png
- save word as png
- convert docx to png
- high resolution png export
language: fr
og_description: Comment définir le DPI pour une exportation PNG haute résolution.
  Suivez ce tutoriel pour convertir Word en PNG avec une qualité cristalline.
og_title: Comment définir le DPI lors de la conversion de Word en PNG – Guide complet
tags:
- Aspose.Words
- C#
- Image Export
title: Comment définir le DPI lors de la conversion de Word en PNG – Guide d’exportation
  haute résolution
url: /fr/net/programming-with-imagesaveoptions/how-to-set-dpi-when-converting-word-to-png-high-resolution-e/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment définir le DPI lors de la conversion de Word en PNG – Guide complet

Vous vous êtes déjà demandé **comment définir le DPI** pour que vos PNG soient d’une netteté exceptionnelle après avoir converti un document Word ? Vous n'êtes pas seul. De nombreux développeurs se heurtent à un problème lorsque la sortie par défaut de 96 dpi apparaît floue sur les écrans Retina, et la solution est étonnamment simple.

Dans ce tutoriel, nous parcourrons un **exemple complet et exécutable** qui vous montre exactement comment définir le DPI, **convertir Word en PNG**, et obtenir une **exportation PNG haute résolution** à chaque fois. Pas de références vagues, juste le code que vous pouvez intégrer immédiatement à votre projet.

## Ce que vous apprendrez

- Le pourquoi du DPI et de la qualité d’image lorsque vous **save word as png**.  
- Comment configurer `ImageSaveOptions` pour une **exportation png haute résolution**.  
- Un extrait C# prêt à l’exécution qui **convertit docx en png** avec un DPI personnalisé.  
- Conseils pour gérer les documents multi‑pages, les mises en page en grille et les pièges courants.

### Prérequis

- .NET 6+ (ou .NET Framework 4.7.2+) installé.  
- Une copie sous licence de **Aspose.Words for .NET** (l’essai gratuit suffit pour les tests).  
- Connaissances de base en C# — rien de plus que la création d’une application console.

> **Astuce pro :** Si vous utilisez Visual Studio, créez un nouveau projet « Console App » et ajoutez le package NuGet `Aspose.Words` avant de commencer.

## Comment définir le DPI – Configuration de ImageSaveOptions

Le cœur de la solution réside dans l’objet `ImageSaveOptions`. En ajustant sa propriété `Resolution`, vous indiquez à Aspose exactement combien de points par pouce l’image PNG de sortie doit contenir. DPI plus élevé → dimensions en pixels plus grandes → image plus nette.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Step 1: Load the source Word document
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

        // Step 2: Configure image save options – this is where we set the DPI
        ImageSaveOptions pngOptions = new ImageSaveOptions(SaveFormat.Png)
        {
            // Export every page (0 means all pages)
            PageCount = 0,

            // Layout pages in a grid – handy for multi‑page docs
            PageLayout = PageLayout.Grid,

            // Desired DPI – 300 is a common choice for print quality
            Resolution = 300
        };

        // Step 3: Save the pages as PNG files. 
        // The "{0}" token creates a separate file per page (output_1.png, output_2.png, …)
        doc.Save(@"YOUR_DIRECTORY\output_{0}.png", pngOptions);
    }
}
```

### Pourquoi 300 DPI ?

- **Qualité prête à l’impression :** La plupart des imprimantes attendent 300 dpi ou plus.  
- **Clarté d’écran :** Sur les écrans à haute densité (p. ex., Apple Retina), les images à 300 dpi conservent les détails sans artefacts de mise à l’échelle.  
- **Taille de fichier équilibrée :** C’est un bon compromis — bien plus net que le 96 dpi par défaut, mais pas aussi volumineux que 600 dpi sauf si vous en avez réellement besoin.

Vous pouvez bien sûr expérimenter : définissez `Resolution = 150` pour une génération plus rapide, ou `Resolution = 600` pour des graphiques ultra‑haute définition.

## Étape 1 : Charger le document DOCX

Avant de pouvoir **save word as png**, le document doit être chargé en mémoire. Aspose.Words abstrait le format de fichier, ainsi que vous le fournissiez un `.docx`, `.doc` ou même un `.rtf`, la même API fonctionne.

```csharp
Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
```

- **Et si le fichier est manquant ?** Enveloppez l’appel dans un `try/catch` et affichez un message d’erreur clair.  
- **Fichiers volumineux ?** Aspose diffuse le contenu, donc vous ne dépasserez généralement pas les limites de mémoire, mais vous pouvez activer `LoadOptions` pour plus de contrôle.

## Étape 2 : Choisir le bon DPI pour un PNG haute résolution

Cette étape est le cœur de **how to set dpi**. La propriété `Resolution` accepte un entier représentant les points par pouce.

```csharp
ImageSaveOptions pngOptions = new ImageSaveOptions(SaveFormat.Png)
{
    Resolution = 300,          // <-- Set your desired DPI here
    PageLayout = PageLayout.Grid,
    PageCount = 0
};
```

- **Grille vs. Page unique :** `PageLayout.Grid` assemble toutes les pages en une seule image (utile pour les aperçus). Si vous préférez un PNG par page, remplacez `PageLayout.Grid` par `PageLayout.Single`.  
- **Exportation d’un sous‑ensemble :** Modifiez `PageCount` à un entier positif et définissez `PageIndex` si vous ne avez besoin que de pages spécifiques.

## Étape 3 : Enregistrer le document en images PNG

La ligne finale écrit les fichiers PNG sur le disque. Notez le placeholder `{0}` — Aspose le remplacera par le numéro de page, vous offrant une série de fichiers bien ordonnée.

```csharp
doc.Save(@"YOUR_DIRECTORY\output_{0}.png", pngOptions);
```

**Résultat attendu :**  

- `output_1.png` – première page à 300 dpi.  
- `output_2.png` – deuxième page, même résolution, etc.

Ouvrez l’un des fichiers dans un visualiseur d’images ; vous verrez une réplique nette de la page Word originale, parfaitement adaptée aux miniatures web, aux éléments d’impression ou à un traitement d’image supplémentaire.

## Optionnel : Exporter plusieurs pages en une seule image grille

Si vous préférez un seul PNG contenant chaque page disposée en grille, conservez `PageLayout = PageLayout.Grid` et omettez le token `{0}` :

```csharp
doc.Save(@"YOUR_DIRECTORY\full_document.png", pngOptions);
```

Vous avez maintenant **un PNG haute résolution** qui montre l’ensemble du document — un aperçu pratique pour les systèmes de gestion de documents.

## Problèmes courants & comment les éviter

| Problème | Pourquoi cela se produit | Solution |
|----------|--------------------------|----------|
| La sortie apparaît floue | DPI laissé à la valeur par défaut 96 | Définir `Resolution` à 300 ou plus (voir étape 2). |
| Seule la première page exportée | `PageCount` défini à `1` | Utiliser `PageCount = 0` pour exporter toutes les pages. |
| Les noms de fichiers entrent en conflit | Même nom de sortie pour chaque page | Utiliser le placeholder `{0}` ou une logique de nommage personnalisée. |
| Manque de mémoire sur de gros documents | Chargement du document complet en RAM | Activer `LoadOptions` avec `LoadFormat.Auto` et traiter les pages dans une boucle. |

## Astuces pro pour une exportation PNG prête pour la production

1. **Mettez en cache la valeur du DPI** dans un fichier de configuration afin de pouvoir la modifier sans recompilation.  
2. **Validez le chemin d’entrée** avant d’appeler `new Document(...)` pour éviter les exceptions non gérées.  
3. **Compressez les PNG** après génération si la taille du fichier est importante — des outils comme `ImageSharp` peuvent ré‑encoder avec une profondeur de bits inférieure.  
4. **Parallélisez l’enregistrement des pages** pour les documents volumineux (utilisez `Parallel.For` sur `doc.PageCount`).  

## Exemple complet fonctionnel (prêt à copier‑coller)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class DpiExportDemo
{
    static void Main()
    {
        try
        {
            // Load the source Word file (replace with your actual path)
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(inputPath);

            // Configure export options – set DPI to 300 for high‑quality PNG
            ImageSaveOptions options = new ImageSaveOptions(SaveFormat.Png)
            {
                PageCount = 0,                // Export every page
                PageLayout = PageLayout.Grid, // Change to Single for one file per page
                Resolution = 300              // <-- How to set DPI
            };

            // Save each page as a separate PNG (output_1.png, output_2.png, …)
            string outputPattern = @"YOUR_DIRECTORY\output_{0}.png";
            doc.Save(outputPattern, options);

            Console.WriteLine("✅ PNG export complete! Check YOUR_DIRECTORY for the files.");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"❌ Error: {ex.Message}");
        }
    }
}
```

Exécutez le programme, ouvrez les PNG générés, et vous verrez immédiatement l’**exportation PNG haute résolution** que vous avez demandée.

---

![Diagramme de réglage du DPI](image.png "Comment régler le DPI lors de la conversion de Word en PNG")

*Texte alternatif de l’image :* **comment régler le dpi** lors de la conversion d’un document Word en PNG (illustre l’impact du DPI).

## Conclusion

Vous savez maintenant **comment définir le DPI** pour un flux de travail **convert word to png** impeccable, comment **save word as png** avec Aspose.Words, et comment obtenir une **exportation png haute résolution** qui répond aux exigences d’écran et d’impression. L’extrait ci‑dessus est une **solution complète et autonome** — il suffit de remplacer les chemins placeholders et vous êtes prêt.

Envie d’en savoir plus ? Essayez d’ajuster `Resolution` à 600 dpi pour des impressions ultra‑nettes, ou changez `PageLayout` en `Single` et générez un PNG par page pour une manipulation plus simple. Vous pouvez également explorer d’autres formats de sortie (JPEG, BMP) en modifiant `SaveFormat`.

Si vous avez des questions sur la gestion de documents protégés par mot de passe, l’incorporation de polices, ou le traitement par lots de dizaines de fichiers, laissez un commentaire ci‑dessous. Bon codage, et profitez de ces PNG d’une clarté cristalline !

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}