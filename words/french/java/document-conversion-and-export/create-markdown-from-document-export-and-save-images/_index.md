---
category: general
date: 2026-02-18
description: Créer du markdown à partir d’un document avec des étapes simples pour
  exporter le document en markdown et enregistrer les images dans un sous‑dossier.
  Apprenez comment enregistrer le document en markdown en C#.
draft: false
keywords:
- create markdown from document
- export document to markdown
- save document as markdown
- save images to subfolder
language: fr
og_description: Créez du markdown à partir d’un document en C# et apprenez comment
  exporter le document en markdown tout en enregistrant les images dans un sous‑dossier.
  Suivez le guide étape par étape.
og_title: Créer du markdown à partir du document – Exporter et enregistrer les images
tags:
- C#
- Aspose.Words
- Markdown export
title: Créer du markdown à partir du document – Exporter et enregistrer les images
url: /fr/java/document-conversion-and-export/create-markdown-from-document-export-and-save-images/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer du markdown à partir d'un document – Exporter et enregistrer les images

Vous avez déjà eu besoin de **créer du markdown à partir d'un document** sans savoir comment garder les images intégrées bien rangées ? Vous n'êtes pas seul. Dans de nombreux projets, nous générons des rapports, des manuels ou des brouillons de blog de façon programmatique, et la dernière chose que l’on veut est un fouillis de fichiers image éparpillés dans le dossier de sortie.  

Dans ce tutoriel, nous allons parcourir une solution complète, prête à l’emploi, qui **exporte le document en markdown**, stocke chaque image dans un sous‑dossier dédié *md‑resources*, puis **enregistre le document au format markdown** à l’aide de l’API Aspose.Words for .NET. À la fin, vous disposerez d’une méthode unique que vous pourrez intégrer dans n’importe quel projet C#, ainsi que de quelques astuces pour gérer les cas particuliers.

> **Aperçu rapide :**  
> • Configurer `MarkdownSaveOptions`  
> • Fournir un `IResourceSavingCallback` qui redirige les images vers un sous‑dossier  
> • Appeler `Document.Save` avec les options configurées  

Si vous vous demandez pourquoi nous utilisons un callback plutôt qu’un post‑processing, continuez la lecture – le raisonnement est expliqué étape par étape.

---

## Prérequis

- .NET 6.0 ou version ultérieure (le code fonctionne également avec .NET Framework 4.7+)
- Aspose.Words for .NET (package NuGet `Aspose.Words`)
- Un objet `Document` source (peut être un .docx, .pdf, .rtf, etc.)

Aucune bibliothèque supplémentaire n’est requise ; l’API de callback est intégrée à Aspose.Words.

---

## Étape 1 : Créer du markdown à partir d'un document – configurer les options d’enregistrement

La première chose que nous faisons est d’instancier `MarkdownSaveOptions`. Cet objet indique à Aspose.Words comment la conversion doit se comporter, par exemple quel flavour de Markdown utiliser, s’il faut intégrer les images en Base64, et où placer les fichiers générés.

```csharp
// Step 1: Initialize Markdown save options
var markdownSaveOptions = new Aspose.Words.Saving.MarkdownSaveOptions();
```

> **Pourquoi c’est important :**  
> Sans créer explicitement `MarkdownSaveOptions`, la bibliothèque revient aux paramètres par défaut qui intègrent les images directement dans le fichier Markdown sous forme de chaînes Base64. Cela rend le fichier énorme et va à l’encontre de l’objectif d’avoir un dossier *images* propre.

---

## Étape 2 : Exporter le document en markdown et définir la gestion des ressources

Nous indiquons maintenant au sauvegardeur **où** placer chaque image. L’interface `IResourceSavingCallback` nous fournit un point d’ancrage qui se déclenche pour chaque ressource (image, SVG, etc.) découverte pendant l’export. Dans le callback, nous :

1. Vérifions que le dossier cible existe (`md-resources/`).  
2. Affectons `OutputFileName` au dossier plus le nom de la ressource d’origine.  

```csharp
// Step 2: Hook into the resource‑saving pipeline
markdownSaveOptions.ResourceSavingCallback = new Aspose.Words.Saving.IResourceSavingCallback(
    (args) =>
    {
        // All images will be placed in "md-resources" relative to the output .md file
        const string folder = "md-resources/";
        Directory.CreateDirectory(folder);          // Create folder if it doesn’t exist

        // Preserve the original file name (e.g., image001.png) but prepend the folder path
        args.OutputFileName = Path.Combine(folder, args.ResourceFileName);

        // Optional: you could also change the format here (e.g., convert BMP to PNG)
        // args.ResourceFileName = Path.ChangeExtension(args.ResourceFileName, ".png");
    });
```

> **Question fréquente :** *Et si je veux intégrer les images plutôt que les enregistrer ?*  
> Il suffit d’ignorer le callback ou de définir `args.OutputFileName = null;` – le sauvegardeur intégrera alors l’image sous forme de chaîne Base64 automatiquement.

> **Cas particulier :** Certains documents plus anciens contiennent des noms d’image en double. Le callback ci‑dessus écrasera le fichier précédent. Pour éviter cela, vous pouvez ajouter un GUID :

```csharp
args.OutputFileName = Path.Combine(folder,
    $"{Path.GetFileNameWithoutExtension(args.ResourceFileName)}_{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}");
```

---

## Étape 3 : Enregistrer le document en markdown et vérifier les images enregistrées

Une fois les options entièrement configurées, l’appel final se résume à une seule ligne qui écrit le fichier Markdown et les images associées sur le disque.

```csharp
// Step 3: Perform the actual export
string outputPath = @"C:\Exports\MyReport.md";
doc.Save(outputPath, markdownSaveOptions);
```

Si tout se passe bien, vous verrez :

- `MyReport.md` – la représentation Markdown de votre document source.  
- `md-resources/` – un dossier à côté du fichier .md contenant chaque image extraite (par ex., `image001.png`, `image002.jpg`).  

**Extrait de Markdown** (généré automatiquement par Aspose.Words) :

```markdown
# Sample Report

Here is an introductory paragraph.

![Sample image](md-resources/image001.png)

More text follows...
```

> **Astuce pro :** Ouvrez le fichier `.md` généré dans VS Code ou tout autre visualiseur Markdown ; les images devraient s’afficher immédiatement car les chemins relatifs correspondent à la structure du dossier.

---

## Exemple complet, exécutable

Voici un programme console autonome que vous pouvez coller dans un nouveau projet .NET et exécuter. Il crée un document Word simple, ajoute une image, puis **crée du markdown à partir du document** tout en stockant l’image dans un sous‑dossier.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a sample Word document with an image
        var doc = new Document();
        var builder = new DocumentBuilder(doc);
        builder.Writeln("Hello, this is a test document.");
        builder.InsertImage("sample-image.png"); // Ensure this file exists next to exe

        // 2️⃣ Configure markdown export options (see Step 1 & 2 above)
        var markdownOptions = new MarkdownSaveOptions();
        markdownOptions.ResourceSavingCallback = new IResourceSavingCallback(
            (args) =>
            {
                const string folder = "md-resources/";
                Directory.CreateDirectory(folder);
                args.OutputFileName = Path.Combine(folder, args.ResourceFileName);
            });

        // 3️⃣ Save as markdown (Step 3)
        string outputFolder = Path.Combine(Environment.CurrentDirectory, "output");
        Directory.CreateDirectory(outputFolder);
        string markdownPath = Path.Combine(outputFolder, "ExportedDoc.md");
        doc.Save(markdownPath, markdownOptions);

        Console.WriteLine($"✅ Markdown saved to: {markdownPath}");
        Console.WriteLine("📂 Images saved in: md-resources/");
    }
}
```

**Ce que vous devriez voir** après l’exécution :

```
✅ Markdown saved to: C:\MyProject\output\ExportedDoc.md
📂 Images saved in: md-resources/
```

Ouvrez `ExportedDoc.md` – la référence d’image pointera vers `md-resources/sample-image.png`, et l’image s’affichera correctement dans n’importe quel visualiseur Markdown.

---

## Variantes fréquemment demandées

| Scénario | Comment adapter le code |
|----------|--------------------------|
| **Ignorer l'exportation d'image** (intégrer en Base64) | Omettre complètement `ResourceSavingCallback`, ou définir `args.OutputFileName = null;` dans le callback. |
| **Changer le format d'image** (par ex., tout en PNG) | Dans le callback, modifier `args.ResourceFileName` et éventuellement convertir le flux avant l’écriture. |
| **Nom de dossier personnalisé** | Remplacer `"md-resources/"` par tout chemin relatif ou absolu que vous préférez. |
| **Plusieurs documents en lot** | Parcourir une collection d’objets `Document`, en réutilisant la même instance de `MarkdownSaveOptions` (veiller simplement à ce que le dossier soit vidé ou nommé de façon unique à chaque exécution). |

---

## Conclusion

Nous venons de vous montrer **comment créer du markdown à partir d'un document**, **exporter le document en markdown**, et **enregistrer les images dans un sous‑dossier** grâce à une approche propre basée sur les callbacks. Les points clés sont :

- Utiliser `MarkdownSaveOptions` pour un contrôle fin de l’export.  
- Implémenter `IResourceSavingCallback` afin de diriger les images vers un dossier dédié, gardant votre Markdown ordonné.  
- Le même schéma fonctionne pour d’autres types de ressources (SVG, audio) – il suffit d’inspecter `args.ResourceType`.  

Ensuite, vous pourriez explorer **l’enregistrement du document en markdown** avec des styles de titres personnalisés, ou intégrer cette routine dans une API Web ASP.NET qui renvoie un ZIP contenant le fichier `.md` et ses ressources. Quoi qu’il en soit, les blocs de construction sont maintenant dans votre boîte à outils.

Des questions, ou un cas particulier que nous n’avons pas couvert ? Laissez un commentaire ci‑dessous, et bon codage !

---

![créer du markdown à partir d'un document exemple](placeholder.png "créer du markdown à partir d'un document exemple")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}