---
category: general
date: 2026-04-28
description: Apprenez à définir un chemin relatif d’image Markdown lors de la conversion
  de Word en Markdown, à extraire les images de Word et à créer un dossier de ressources
  pour les images exportées.
draft: false
keywords:
- markdown image relative path
- convert word to markdown
- extract images from word
- create resources folder
- export images from docx
language: fr
og_description: Définissez un chemin relatif d’image Markdown lors de la conversion
  de Word en Markdown, extrayez les images du document Word et créez un dossier de
  ressources pour les images exportées.
og_title: Chemin relatif d'image markdown – Convertir Word en Markdown
tags:
- Aspose.Words
- C#
- Markdown
- Image Export
title: Chemin relatif d’image markdown – Convertir Word en Markdown
url: /fr/net/programming-with-markdownsaveoptions/markdown-image-relative-path-convert-word-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# chemin d'image markdown relatif – Convertir Word en Markdown

Vous avez déjà eu besoin d'un **chemin d'image markdown relatif** pendant que vous **convertissez Word en markdown** ? Vous n'êtes pas seul. La plupart des développeurs rencontrent un problème lorsque le Markdown généré pointe vers des images dans un dossier plat, rompant la structure de liens relatifs que vous attendez dans un site statique ou un dépôt GitHub.

Dans ce tutoriel, nous allons parcourir une solution complète, de bout en bout, qui **extrait les images de Word**, **crée un dossier resources**, et réécrit les références d'images afin qu'elles utilisent un *chemin d'image markdown relatif* propre. À la fin, vous disposerez d'un fichier `.md` prêt à publier et d'un répertoire `Resources` bien organisé contenant chaque image extraite du `.docx` original.

> **Ce que vous obtiendrez :** un seul programme C# (sans scripts externes), une explication claire du *pourquoi* de chaque étape, et une poignée de conseils pratiques que vous pouvez copier‑coller dans vos propres projets.

---

## Prérequis

Avant de plonger dans le code, assurez‑vous d'avoir :

- **.NET 6.0** ou une version ultérieure installée (vous pouvez également cibler .NET Framework 4.7+, mais .NET 6 est le meilleur choix pour les nouveaux projets).
- **Aspose.Words for .NET** (le dernier package NuGet au moment de la rédaction, version 23.12). Installez‑le avec :
  ```bash
  dotnet add package Aspose.Words
  ```
- Un document Word contenant réellement des images — appelons‑le `WithImages.docx`.
- Un dossier où vous souhaitez que le markdown généré et les images résident, par ex. `C:\Projects\MarkdownExport`.

Aucune bibliothèque supplémentaire n'est requise ; tout le reste est géré par Aspose.Words.

---

## Étape 1 : Charger le document Word source (point de départ pour convertir Word en markdown)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Adjust the path to point at your own .docx file.
        string sourcePath = @"C:\Projects\MarkdownExport\WithImages.docx";

        // Load the document – this is where Aspose.Words parses the Word file.
        Document doc = new Document(sourcePath);
        
        // The rest of the workflow follows…
    }
}
```

*Pourquoi c’est important :* charger le document nous donne accès à l'arbre interne des nœuds, qui inclut les parties image dont nous aurons besoin plus tard pour **exporter les images du docx**. Si le chargement échoue, aucune des étapes suivantes ne s’exécutera, alors vérifiez le chemin et les permissions du fichier.

---

## Étape 2 : Configurer `MarkdownSaveOptions` avec un rappel personnalisé (le cœur de la création du dossier resources)

Le `ResourceSavingCallback` nous permet d'intervenir chaque fois qu'Aspose.Words veut écrire un fichier image. À l'intérieur du rappel, nous allons **créer un sous‑dossier Resources** et ajuster la référence afin que le markdown généré utilise un *chemin d'image markdown relatif*.

```csharp
// Inside Main(), after loading the document:
string outputFolder = @"C:\Projects\MarkdownExport";
string resourcesFolder = Path.Combine(outputFolder, "Resources");

// Make sure the folder exists before we start saving anything.
Directory.CreateDirectory(resourcesFolder);

// Set up the Markdown save options.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // Hook that runs for every image resource.
    ResourceSavingCallback = new MyMarkdownResourceCallback(resourcesFolder)
};

// Save the document as Markdown.
string markdownPath = Path.Combine(outputFolder, "Doc.md");
doc.Save(markdownPath, mdOptions);
```

Remarquez que nous avons passé `resourcesFolder` au constructeur du rappel — cela garde le chemin du dossier flexible et évite de coder en dur des chaînes partout dans le code.

---

## Étape 3 : Implémenter le rappel qui **crée le dossier resources** et réécrit le chemin

```csharp
/// <summary>
/// Handles image extraction and path rewriting for markdown export.
/// </summary>
class MyMarkdownResourceCallback : IResourceSavingCallback
{
    private readonly string _resourcesFolder;

    public MyMarkdownResourceCallback(string resourcesFolder)
    {
        _resourcesFolder = resourcesFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // 1️⃣ Build the full file system path where the image will be stored.
        string targetPath = Path.Combine(_resourcesFolder, args.ResourceFileName);
        
        // 2️⃣ Ensure the directory exists (in case Aspose creates sub‑folders).
        Directory.CreateDirectory(Path.GetDirectoryName(targetPath));

        // 3️⃣ Write the image stream to disk.
        using (FileStream fileStream = File.Create(targetPath))
        {
            args.Stream.CopyTo(fileStream);
        }

        // 4️⃣ Update the markdown reference to use a relative path.
        // This is the crucial line that gives us the markdown image relative path.
        args.ResourceFileName = Path.Combine("Resources", args.ResourceFileName);
    }
}
```

*Pourquoi cela fonctionne :* `args.Stream` contient les octets bruts de l'image. En le copiant dans un fichier à l'intérieur de notre dossier `Resources`, nous **exportons les images du docx** en toute sécurité. Ensuite, nous remplaçons `args.ResourceFileName` par une URL relative (`Resources/image.png`). Lorsque Aspose.Words écrira plus tard le markdown, il injectera exactement cette chaîne, nous donnant le *chemin d'image markdown relatif* souhaité.

---

## Étape 4 : Vérifier le Markdown généré (à quoi ressemble la sortie finale)

Ouvrez `Doc.md` dans n'importe quel éditeur de texte. Vous devriez voir quelque chose de similaire à :

```markdown
# Sample Heading

Here is an inline picture:

![Image 0](Resources/Image_0.png)

And a picture inside a table:

![Image 1](Resources/Image_1.jpg)
```

L'élément important est que chaque référence d'image pointe vers `Resources/...` – c’est le **chemin d'image markdown relatif** que nous recherchions.

![exemple de chemin d'image markdown relatif](example.png "exemple de chemin d'image markdown relatif")

*Astuce :* si vous ouvrez le markdown dans un visualiseur qui respecte les liens relatifs (aperçu VS Code, GitHub, ou un générateur de site statique), les images s'afficheront correctement sans configuration supplémentaire.

---

## Étape 5 : Pièges courants et pro‑conseils

| Problème | Pourquoi cela se produit | Comment le corriger |
|----------|--------------------------|---------------------|
| Les images se retrouvent dans le dossier racine au lieu de `Resources` | Le rappel n’a pas été attaché ou `args.ResourceFileName` n’a pas été écrasé. | Vérifiez que `ResourceSavingCallback` est défini **avant** d’appeler `doc.Save`. |
| Les noms de fichiers contiennent des caractères illégaux | Word nomme parfois les images avec des espaces ou des symboles Unicode. | Utilisez `Path.GetInvalidFileNameChars()` pour nettoyer `args.ResourceFileName` dans le rappel. |
| Les gros documents prennent beaucoup de temps à traiter | Chaque image est écrite de façon synchrone. | Passez à une I/O asynchrone (`await args.Stream.CopyToAsync(fileStream)`) si vous êtes sur .NET 6+ et avez besoin de performance. |
| Les chemins relatifs se cassent quand le markdown est déplacé | Le chemin est relatif à l’emplacement du fichier markdown. | Gardez `Doc.md` et le dossier `Resources` ensemble, ou ajustez le rappel pour utiliser un préfixe relatif différent (ex. `../assets`). |

---

## Étape 6 : Étendre la solution (et si vous avez besoin de plus de contrôle ?)

- **Formats de sortie multiples :** Remplacez `MarkdownSaveOptions` par `HtmlSaveOptions` ou `PdfSaveOptions` tout en conservant le même rappel — Aspose.Words l’invoquera pour chaque image, quel que soit le format.
- **Nommage d'images personnalisé :** Si vous souhaitez renommer les images (ex. `figure-01.png`), modifiez `args.ResourceFileName` dans le rappel avant d’écrire le fichier.
- **Intégration d'images en Base64 :** Définissez `args.ResourceFileName` sur un URI de données (`data:image/png;base64,...`) et ignorez l’écriture du fichier. Cela est pratique pour des exports markdown en un seul fichier.

---

## Conclusion

Vous disposez maintenant d’un programme C# entièrement fonctionnel qui **convertit Word en markdown**, **extrait les images de Word**, **crée un dossier resources**, et garantit un **chemin d'image markdown relatif** propre pour chaque image. Le code est autonome, fonctionne avec la dernière version d’Aspose.Words, et peut être intégré à n’importe quel projet .NET avec un minimum d’effort.

Prochaines étapes ? Essayez d’alimenter le markdown généré dans un générateur de site statique comme Hugo ou Jekyll, ou expérimentez avec le rappel pour intégrer directement les images en chaînes Base64. Si vous rencontrez des cas particuliers—par ex. des images SVG ou des fichiers très volumineux—revenez au tableau « Pièges courants » ; un petit ajustement résout généralement le problème.

Bon codage, et que votre markdown pointe toujours vers le bon dossier !

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}