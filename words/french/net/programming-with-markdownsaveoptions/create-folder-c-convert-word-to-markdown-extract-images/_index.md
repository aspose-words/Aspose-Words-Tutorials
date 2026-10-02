---
category: general
date: 2026-02-26
description: Créer un dossier tutoriel C# montrant comment convertir Word en markdown,
  extraire les images d’un docx et copier le flux vers un fichier — le tout en une
  seule étape.
draft: false
keywords:
- create folder c#
- convert word to markdown
- extract images from docx
- copy stream to file
language: fr
og_description: Le tutoriel C# « Create folder » vous guide à travers la conversion
  de Word en markdown, l’extraction d’images d’un docx et la copie d’un flux vers
  un fichier avec des exemples de code clairs.
og_title: Créer un dossier C# – Convertir Word en Markdown et extraire les images
tags:
- C#
- Aspose.Words
- Markdown
- Image Extraction
title: Créer un dossier C# – Convertir Word en Markdown et extraire les images
url: /fr/net/programming-with-markdownsaveoptions/create-folder-c-convert-word-to-markdown-extract-images/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un dossier C# – Convertir Word en Markdown & Extraire les images

Vous avez déjà eu besoin de **create folder C#** tout en transformant un document Word en markdown et en extrayant chaque image ? Vous n'êtes pas le seul à vous gratter la tête à ce sujet. Dans de nombreux pipelines d'automatisation, vous vous retrouvez à jongler avec des tâches de système de fichiers, la conversion de formats et la gestion de données binaires—le tout en une seule fois.  

Dans ce guide, nous parcourrons une solution complète et exécutable qui fait exactement cela : elle crée un répertoire cible, convertit un `.docx` en markdown, extrait chaque image intégrée, et utilise la logique **copy stream to file** afin que les images atterrissent où vous le souhaitez. Aucun script externe, aucune étape manuelle. Juste du pur C# et la bibliothèque Aspose.Words.

> **Ce que vous obtiendrez**  
> * Une structure de dossiers claire prête pour le markdown et les ressources  
> * Un fichier markdown qui référence correctement les images extraites  
> * Le code source complet que vous pouvez intégrer dans n'importe quel projet .NET  

Avant de commencer, assurez‑vous d'avoir :

* .NET 6.0 (ou version ultérieure) SDK installé – le code utilise des fonctionnalités modernes du langage.  
* Une licence pour **Aspose.Words for .NET** (l'essai gratuit suffit pour les tests).  
* Visual Studio 2022 ou votre éditeur préféré.  

Si vous vous demandez *pourquoi* extraire les images plutôt que de les intégrer, pensez aux générateurs de sites statiques : ils adorent le markdown avec des chemins d'image relatifs, et garder les ressources dans un dossier dédié rend les choses plus propres et plus compatibles avec le cache.

---

## Créer un dossier C# et préparer la structure de sortie

La première chose dont nous avons besoin est un emplacement sur le disque où tout vivra. Cette étape est celle où l'action **create folder C#** se produit, et c'est étonnamment simple grâce à `Directory.CreateDirectory`. La méthode est idempotente — elle ne lève pas d'exception si le dossier existe déjà, ce qui nous évite des vérifications supplémentaires.

```csharp
using System;
using System.IO;

// Define the base output directory (adjust as needed)
string baseOutput = Path.Combine(Environment.CurrentDirectory, "output");

// Subfolders for markdown and images
string markdownFolder = Path.Combine(baseOutput, "markdown");
string imagesFolder   = Path.Combine(baseOutput, "MyImages");

// Ensure the folders exist
Directory.CreateDirectory(markdownFolder);
Directory.CreateDirectory(imagesFolder);

Console.WriteLine($"Created folders:\n • {markdownFolder}\n • {imagesFolder}");
```

**Pourquoi c'est important :**  
Créer les dossiers à l'avance garantit que les étapes d'enregistrement ultérieures ne échoueront pas avec `DirectoryNotFoundException`. Cela vous donne également une disposition prévisible : `output/markdown` pour le fichier `.md` et `output/MyImages` pour chaque image que nous extrayons.

> **Astuce :** Si vous exécutez le programme à plusieurs reprises, vous voudrez peut‑être nettoyer le dossier d'images d'abord (`Directory.GetFiles(imagesFolder).ToList().ForEach(File.Delete);`) pour éviter les fichiers obsolètes.

---

## Convertir Word en Markdown avec Aspose.Words

Maintenant que l'arborescence de répertoires est prête, convertissons le document Word en markdown. Aspose.Words fait le gros du travail—pas besoin de manipuler OpenXML ou des convertisseurs tiers.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Load the source DOCX (replace with your actual path)
string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
var doc = new Document(inputPath);

// Configure markdown options and attach the image callback (we’ll define it later)
var mdOptions = new MarkdownSaveOptions
{
    // The callback will redirect each extracted image to our custom folder
    ResourceSavingCallback = new ImageSavingCallback(imagesFolder)
};

// Save the markdown file into the previously created folder
string markdownPath = Path.Combine(markdownFolder, "output.md");
doc.Save(markdownPath, mdOptions);

Console.WriteLine($"Word document converted to markdown at: {markdownPath}");
```

**Ce qui se passe sous le capot :**  
`MarkdownSaveOptions` indique à Aspose d'émettre la syntaxe markdown. Par défaut, la bibliothèque placerait les images dans le même dossier que le fichier markdown avec des noms générés automatiquement. En fournissant un `ResourceSavingCallback`, nous interceptons ce comportement et **copy stream to file** dans l'emplacement de notre choix.

---

## Extraire les images du DOCX et les enregistrer

La classe de rappel implémente `IResourceSavingCallback`. À l'intérieur, nous recevons un objet `ResourceSavingArgs` qui contient le flux d'image original et le nom de fichier suggéré. Nous écrivons alors ce flux sur le disque, renommons le fichier si nous le souhaitons, et informons Aspose que nous avons géré l'opération.

```csharp
using Aspose.Words.Saving;
using System.IO;

/// <summary>
/// Handles image extraction during markdown conversion.
/// </summary>
public class ImageSavingCallback : IResourceSavingCallback
{
    private readonly string _targetFolder;

    public ImageSavingCallback(string targetFolder)
    {
        _targetFolder = targetFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Ensure the target folder exists (defensive, though we created it earlier)
        Directory.CreateDirectory(_targetFolder);

        // Build a new, friendly file name – you can customize the pattern
        string newFileName = $"img_{Path.GetFileName(args.ResourceFileName)}";
        string fullPath = Path.Combine(_targetFolder, newFileName);

        // **Copy stream to file** – the core of the image extraction
        using (FileStream fs = new FileStream(fullPath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }

        // Tell Aspose to use our new path in the markdown reference
        args.ResourceFileName = Path.Combine("MyImages", newFileName);
        args.Handled = true; // Prevent default saving logic
    }
}
```

### À quoi ressemblera le markdown

Après la conversion, le fichier `output.md` généré contiendra des lignes telles que :

```markdown
![Image 1](MyImages/img_picture1.png)
```

Comme nous avons modifié `args.ResourceFileName` en un chemin relatif, le markdown pointe directement vers le dossier que nous avons créé. C’est exactement ce que les générateurs de sites statiques attendent.

**Gestion des cas limites :**  
*Si le document contient des noms d'image dupliqués*, le préfixe `img_` ajouté au nom original évite généralement les collisions, mais vous pouvez aussi ajouter un GUID (`Guid.NewGuid()`) pour une unicité absolue.

---

## Copier le flux vers un fichier – gestion des données d'image

Vous vous demandez peut‑être pourquoi nous n'appelons pas simplement `File.WriteAllBytes`. La réponse réside dans la **flexibilité du stream**. `args.Stream` peut être un memory stream, un network stream ou toute autre implémentation. En utilisant `CopyTo`, nous restons agnostiques et laissons .NET gérer efficacement la taille du tampon.

Voici une méthode utilitaire compacte si vous avez besoin de copier un flux générique ailleurs :

```csharp
/// <summary>
/// Copies any readable stream to a file on disk.
/// </summary>
public static void CopyStreamToFile(Stream source, string destinationPath)
{
    using (var file = new FileStream(destinationPath, FileMode.Create, FileAccess.Write))
    {
        source.CopyTo(file);
    }
}
```

Vous pouvez remplacer la copie en ligne dans `ImageSavingCallback` par un appel à `CopyStreamToFile` si vous préférez une approche à responsabilité unique.

---

## Exemple complet exécutable

Assembler toutes les pièces vous donne un programme autonome que vous pouvez lancer depuis la ligne de commande :

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create the folder structure
        string baseOutput = Path.Combine(Environment.CurrentDirectory, "output");
        string markdownFolder = Path.Combine(baseOutput, "markdown");
        string imagesFolder   = Path.Combine(baseOutput, "MyImages");
        Directory.CreateDirectory(markdownFolder);
        Directory.CreateDirectory(imagesFolder);

        // 2️⃣ Load the DOCX
        string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        var doc = new Document(inputPath);

        // 3️⃣ Set up markdown options with our image callback
        var mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new ImageSavingCallback(imagesFolder)
        };

        // 4️⃣ Save as markdown
        string markdownPath = Path.Combine(markdownFolder, "output.md");
        doc.Save(markdownPath, mdOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown: {markdownPath}");
        Console.WriteLine($"Images folder: {imagesFolder}");
    }
}

// ---------- ImageSavingCallback (same as earlier) ----------
public class ImageSavingCallback : IResourceSavingCallback
{
    private readonly string _targetFolder;
    public ImageSavingCallback(string targetFolder) => _targetFolder = targetFolder;

    public void ResourceSaving(ResourceSavingArgs args)
    {
        Directory.CreateDirectory(_targetFolder);
        string newFileName = $"img_{Path.GetFileName(args.ResourceFileName)}";
        string fullPath = Path.Combine(_targetFolder, newFileName);
        using (FileStream fs = new FileStream(fullPath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }
        args.ResourceFileName = Path.Combine("MyImages", newFileName);
        args.Handled = true;
    }
}
```

**Résultat attendu**

* `output/markdown/output.md` – un fichier markdown dont les références d'image ressemblent à `![Alt text](MyImages/img_picture1.png)`.  
* `output/MyImages/` – un fichier PNG/JPEG par image qui se trouvait à l'origine dans `input.docx`.  

Ouvrez le markdown dans n'importe quel visualiseur (VS Code, GitHub ou un générateur de site statique) et vous verrez les images rendues exactement à l'endroit où elles se trouvaient dans le fichier Word original.

---

## Questions fréquentes & dépannage

| Question | Réponse |
|----------|--------|
| **Et si le dossier cible contient déjà des fichiers ?** | `Directory.CreateDirectory` ne remplacera pas les fichiers. Si vous avez besoin d'une exécution propre, supprimez |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}