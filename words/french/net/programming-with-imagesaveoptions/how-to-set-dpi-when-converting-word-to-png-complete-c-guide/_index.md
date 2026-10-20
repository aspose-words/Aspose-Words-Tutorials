---
category: general
date: 2025-12-29
description: Apprenez à définir le DPI lors de la conversion de Word en PNG avec Aspose.Words.
  Ce tutoriel étape par étape couvre également l'exportation PNG haute résolution
  et les paramètres de résolution d'image.
draft: false
keywords:
- how to set dpi
- convert word to png
- save word as png
- high resolution png export
- set image resolution png
language: fr
og_description: Comment définir le DPI lors de la conversion de Word en PNG avec Aspose.Words.
  Suivez ce guide pour une exportation PNG haute résolution et le contrôle de la résolution
  d'image.
og_title: Comment définir le DPI lors de la conversion de Word en PNG – Guide complet
  C#
tags:
- Aspose.Words
- C#
- Image Export
title: Comment définir le DPI lors de la conversion de Word en PNG – Guide complet
  C#
url: /fr/net/programming-with-imagesaveoptions/how-to-set-dpi-when-converting-word-to-png-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment définir le DPI lors de la conversion de Word en PNG – Guide complet C#

Vous vous êtes déjà demandé **comment définir le DPI** pendant la conversion d’un document Word en PNG ? Peut‑être avez‑vous besoin de captures d’écran nettes pour une présentation, ou vous générez des éléments imprimables qui doivent être nets à 300 dpi. Dans tous les cas, vous êtes au bon endroit. Dans ce tutoriel, nous allons parcourir la conversion d’un fichier `.docx` multi‑pages en images PNG haute résolution à l’aide d’Aspose.Words, et nous vous montrerons exactement comment définir la résolution d’image afin que le résultat ne soit pas flou.

Nous ajouterons également des astuces sur **convert word to png**, **save word as png**, et comment obtenir une **high resolution png export** sans effort. Aucun document externe, juste un exemple autonome, exécutable, que vous pouvez copier‑coller dans Visual Studio.

---

## Ce dont vous avez besoin

- **Aspose.Words for .NET** (dernière version, par ex. 24.9).  
- .NET 6+ (ou .NET Framework 4.7.2+) – toute version récente du runtime convient.  
- Un fichier Word (`MultiPage.docx`) que vous souhaitez transformer en PNG.  
- Un environnement de développement – Visual Studio, Rider ou VS Code feront l’affaire.

C’est tout. Aucun package NuGet supplémentaire au‑delà d’Aspose.Words.

---

## Étape 1 : Charger le document Word

Première chose à faire : nous avons besoin d’une représentation en mémoire du fichier Word. La classe `Document` s’en charge pour nous.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Load the multi‑page document from disk
Document multiPageDoc = new Document("YOUR_DIRECTORY/MultiPage.docx");
```

> **Pourquoi c’est important :** Charger le document nous donne accès à son `PageCount`, dont nous aurons besoin plus tard pour demander à Aspose d’exporter **toutes les pages** en PNG.

---

## Étape 2 : Configurer ImageSaveOptions avec les paramètres DPI

Nous indiquons maintenant à Aspose que nous voulons une sortie PNG *et* nous spécifions le DPI. Les propriétés `ImageHorizontalResolution` et `ImageVerticalResolution` sont où la magie opère.

```csharp
// Create PNG save options and set the DPI to 300
ImageSaveOptions imageSaveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    // Export every page (0‑based index to PageCount‑1)
    PageSet = new PageSet(0, multiPageDoc.PageCount - 1),

    // Set image resolution – this is the “how to set dpi” part
    ImageHorizontalResolution = 300, // 300 DPI horizontally
    ImageVerticalResolution   = 300, // 300 DPI vertically

    // Give each page a friendly file name
    PageSavingCallback = (sender, args) =>
    {
        args.ImageFileName = $"Page_{args.PageIndex + 1}.png";
    }
};
```

> **Astuce pro :** 300 dpi est la norme de facto pour les graphiques prêts à l’impression. Si vous avez seulement besoin d’une qualité d’affichage à l’écran, 96 dpi réduira considérablement la taille du fichier.

---

## Étape 3 : Enregistrer toutes les pages en un seul PNG mosaïque (ou fichiers séparés)

Aspose vous permet soit de regrouper chaque page dans un PNG mosaïque massif **ou** d’écrire chaque page dans son propre fichier. L’exemple ci‑dessous montre l’approche *mosaïque unique*, mais le `PageSavingCallback` que nous avons ajouté garantit déjà que des fichiers séparés seront créés si vous activez le drapeau `ExportImagesAsSeparateFiles`.

```csharp
// Save the whole document as a tiled PNG file
multiPageDoc.Save("YOUR_DIRECTORY/Pages.png", imageSaveOptions);
```

Si vous préférez un fichier par page, il suffit de définir :

```csharp
imageSaveOptions.ExportImagesAsSeparateFiles = true;
```

et le callback se chargera de nommer chaque `Page_#.png`.

---

## Étape 4 : Vérifier le résultat

Après avoir exécuté le code, ouvrez le `Pages.png` (ou les fichiers `Page_#.png` générés) dans n’importe quel visualiseur d’images. Vous devriez voir des images nettes, haute résolution, qui reproduisent la mise en page des pages Word d’origine.

- **Vérification de la résolution :** Clic droit → Propriétés → Détails → DPI horizontal / DPI vertical → doit indiquer **300**.  
- **Vérification de la taille :** À 300 dpi, une page A4 typique (8,27 po × 11,69 po) devient environ 2481 × 3508 pixels – parfait pour l’impression.

---

## Pièges courants & comment les éviter

| Problème | Pourquoi cela arrive | Solution |
|----------|----------------------|----------|
| **Sortie floue** | DPI laissé à la valeur par défaut (96) | Définir explicitement `ImageHorizontalResolution` **et** `ImageVerticalResolution`. |
| **Pages manquantes** | `PageSet` ne couvre qu’un sous‑ensemble | Utiliser `new PageSet(0, multiPageDoc.PageCount - 1)` pour inclure toutes les pages. |
| **Conflits de noms de fichiers** | Callback non défini | Fournir un `PageSavingCallback` qui génère des noms uniques. |
| **Taille de fichier importante** | 600 dpi ou plus sans besoin | Choisir le DPI le plus bas qui satisfait votre exigence de qualité. |
| **Erreurs de mémoire** pour les documents volumineux | Export d’un PNG mosaïque massif | Passer à `ExportImagesAsSeparateFiles = true` pour écrire chaque page séparément. |

---

## Avancé : Exporter vers différentes variantes PNG

Parfois vous avez besoin d’un **fond transparent** ou d’une **profondeur de couleur différente**. Aspose.Words prend en charge ces ajustements via `PngOptions` dans `ImageSaveOptions`.

```csharp
imageSaveOptions.PngOptions = new PngOptions
{
    // Enable transparency
    Transparency = true,

    // 8‑bit color depth (smaller file) or 24‑bit for full color
    BitDepth = 24
};
```

Vous pouvez également combiner cela avec les réglages DPI ci‑dessus pour obtenir une **high resolution png export** prête à la fois pour le web et l’impression.

---

## Exemple complet fonctionnel

Voici le programme complet, prêt à copier‑coller. Remplacez simplement `YOUR_DIRECTORY` par le chemin réel sur votre machine.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/MultiPage.docx");

        // 2️⃣ Configure PNG export with 300 DPI
        ImageSaveOptions options = new ImageSaveOptions(SaveFormat.Png)
        {
            PageSet = new PageSet(0, doc.PageCount - 1),
            ImageHorizontalResolution = 300,
            ImageVerticalResolution = 300,
            // Optional: separate files per page
            // ExportImagesAsSeparateFiles = true,

            // 3️⃣ Friendly file names for each page
            PageSavingCallback = (sender, args) =>
            {
                args.ImageFileName = $"Page_{args.PageIndex + 1}.png";
            },

            // 4️⃣ High‑resolution PNG tweaks (transparent background, 24‑bit)
            PngOptions = new PngOptions
            {
                Transparency = true,
                BitDepth = 24
            }
        };

        // 5️⃣ Save – either a tiled PNG or separate files
        doc.Save("YOUR_DIRECTORY/Pages.png", options);

        Console.WriteLine("Conversion complete! Check YOUR_DIRECTORY for the PNG files.");
    }
}
```

Exécutez le programme, et vous obtiendrez une **high resolution PNG export** de chaque page, chacune au DPI exact que vous avez défini.

---

## FAQ

**Q : Cela fonctionne‑t‑il avec les anciens fichiers `.doc` ?**  
R : Absolument. Aspose.Words abstrait le format, donc le même code gère `.doc`, `.docx`, `.rtf` et même `.odt`.

**Q : Puis‑je exporter en JPEG au lieu de PNG ?**  
R : Oui – il suffit de remplacer `SaveFormat.Png` par `SaveFormat.Jpeg` et d’ajuster `JpegOptions` si nécessaire.

**Q : Et si j’ai besoin de 600 dpi pour un grand poster ?**  
R : Définissez `ImageHorizontalResolution = 600` et `ImageVerticalResolution = 600`. Surveillez l’utilisation mémoire ; des valeurs DPI élevées augmentent rapidement les dimensions en pixels.

**Q : Existe‑t‑il un moyen de traiter en lot de nombreux fichiers Word ?**  
R : Enveloppez la logique ci‑dessus dans une boucle `foreach (var file in Directory.GetFiles(folder, "*.docx"))`. Pensez à libérer chaque instance `Document` ou à réutiliser un même objet `ImageSaveOptions` pour plus d’efficacité.

---

## Conclusion

Nous avons couvert **comment définir le DPI** lors de la **conversion de Word en PNG** avec Aspose.Words, abordé les subtilités d’une **high resolution PNG export**, et fourni un exemple de code prêt à l’emploi qui **save word as png** avec un contrôle précis de la résolution d’image. En ajustant `ImageHorizontalResolution`, `ImageVerticalResolution` et éventuellement `PngOptions`, vous pouvez générer des graphiques prêts à l’impression ou des actifs légers pour le web en toute confiance.

Prochaines étapes ? Expérimentez avec différentes valeurs DPI, passez à l’exportation de fichiers séparés, ou combinez ce flux de travail avec une chaîne PDF‑to‑PNG pour une gestion de documents encore plus large. Les mêmes principes s’appliquent lorsque vous **set image resolution png** pour d’autres formats, vous êtes donc désormais équipé pour gérer une grande variété de scénarios d’exportation d’images.

Bon codage, et que vos PNG restent toujours ultra‑nets ! 

![Comment définir le DPI lors de la conversion de Word en PNG – exemple de sortie](/images/how-to-set-dpi-word-to-png.png "how to set dpi")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}