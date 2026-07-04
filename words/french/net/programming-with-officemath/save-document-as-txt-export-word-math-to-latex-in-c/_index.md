---
category: general
date: 2026-04-24
description: Enregistrez le document au format txt et convertissez Word en LaTeX avec
  Aspose.Words. Apprenez à exporter rapidement les équations mathématiques de Word
  vers LaTeX.
draft: false
keywords:
- save document as txt
- convert word to latex
- convert word equations to latex
- export word math latex
language: fr
og_description: Enregistrez le document au format txt et convertissez les équations
  Word en LaTeX avec C#. Guide complet étape par étape avec le code.
og_title: Enregistrer le document au format TXT – Exporter les formules Word en LaTeX
tags:
- Aspose.Words
- C#
- LaTeX
title: Enregistrer le document au format TXT – Exporter les formules Word en LaTeX
  en C#
url: /fr/net/programming-with-officemath/save-document-as-txt-export-word-math-to-latex-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Enregistrer le document en TXT – Exporter les équations Word en LaTeX en C#

Vous avez déjà eu besoin de **enregistrer le document en txt** tout en conservant vos belles équations intactes ? Vous n'êtes pas le seul. La fonction intégrée de Word « Enregistrer sous texte brut » supprime Office Math, vous laissant avec du charabia illisible. Et si vous pouviez garder ces équations, mais sous forme de LaTeX propre ?

Dans ce tutoriel, nous passerons en revue les étapes exactes pour créer un texte prêt à **convertir Word en LaTeX** à l'aide d'Aspose.Words pour .NET. À la fin, vous disposerez d'un fichier `.txt` où chaque équation est représentée sous forme de balisage LaTeX correct, prêt à être inséré dans un article ou un fichier markdown. Aucun convertisseur externe, aucune copie manuelle—juste quelques lignes de C#.

## Ce que vous allez apprendre

- Comment charger un fichier `.docx` avec Aspose.Words.
- Configurer `TxtSaveOptions` afin que Office Math soit exporté en LaTeX.
- Enregistrer le résultat dans un fichier texte brut que vous pouvez ouvrir avec n'importe quel éditeur.
- Gestion des cas limites pour les équations en ligne vs affichées, et une astuce rapide pour le traitement par lots de plusieurs documents.

### Prérequis

- .NET 6.0 ou supérieur (le code fonctionne également avec .NET Framework 4.6+).
- Package NuGet Aspose.Words pour .NET (`Install-Package Aspose.Words`).
- Un document Word contenant au moins une équation (objet Office Math).

---

## Étape 1 : Installer Aspose.Words et configurer le projet

Tout d'abord, ajoutez la bibliothèque à votre projet. Ouvrez un terminal dans le dossier de votre solution et exécutez :

```bash
dotnet add package Aspose.Words
```

> **Astuce :** Si vous utilisez Visual Studio, l'interface du Gestionnaire de packages NuGet fonctionne tout aussi bien—recherchez « Aspose.Words » et cliquez sur Installer.

Créez maintenant une nouvelle application console (ou insérez le code dans une existante). Les directives `using` dont vous avez besoin sont :

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

Elles importent les classes `Document` et le type `TxtSaveOptions` dans le scope.

## Étape 2 : Charger le document source

Nous devons indiquer à Aspose.Words le fichier Word contenant les équations. Remplacez `YOUR_DIRECTORY/input.docx` par le chemin réel sur votre machine.

```csharp
// Load the source .docx file
Document doc = new Document(@"C:\MyDocs\input.docx");
```

> **Pourquoi c’est important :** Charger le document donne à Aspose.Words un accès complet aux objets Office Math internes, qui sont autrement invisibles pour un simple exportateur de texte.

## Étape 3 : Configurer TxtSaveOptions pour l’exportation LaTeX

La magie se produit dans l'objet `TxtSaveOptions`. En définissant `OfficeMathExportMode` sur `LaTeX`, chaque équation est transformée en son équivalent LaTeX.

```csharp
// Configure save options to export Office Math as LaTeX
TxtSaveOptions txtOptions = new TxtSaveOptions
{
    // Export all Office Math objects as LaTeX code
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,

    // Optional: keep line breaks similar to the original layout
    PreserveTableLayout = true
};
```

> **Et si vous avez besoin de MathML à la place ?** Changez `OfficeMathExportMode` en `MathML`. La même API prend en charge plusieurs formats de sortie.

## Étape 4 : Enregistrer le document en texte brut

Nous écrivons maintenant le fichier. Le `Math.txt` résultant contiendra du texte ordinaire ainsi que des fragments LaTeX pour chaque équation.

```csharp
// Save the document as a .txt file with LaTeX equations
doc.Save(@"C:\MyDocs\Math.txt", txtOptions);
Console.WriteLine("Document saved as txt with LaTeX equations.");
```

Lancer le programme produit un fichier qui ressemble à ceci :

```
This is a simple paragraph.

Here is an inline equation: $E = mc^2$

And a displayed equation:
\[
\int_{0}^{\infty} e^{-x} \, dx = 1
\]
```

Remarquez que l’équation en ligne utilise `$…$` tandis que l’équation affichée est entourée de `\[` et `\]`. C’est la convention LaTeX standard, et Aspose.Words le fait automatiquement.

## Étape 5 : Vérifier la sortie (facultatif)

Si vous souhaitez revérifier que le LaTeX est valide, vous pouvez passer le `.txt` à un compilateur LaTeX comme `pdflatex` ou à un rendu en ligne tel qu'Overleaf. Le texte devrait se compiler sans erreurs, et les équations apparaîtront exactement comme dans Word.

```bash
pdflatex Math.txt
```

Si vous obtenez « Undefined control sequence », assurez‑vous que les packages LaTeX nécessaires (par ex., `amsmath`) sont inclus dans votre préambule lorsque vous intégrez le texte dans un document LaTeX plus grand.

## Gestion des variations courantes

### Conversion de plusieurs fichiers dans un dossier

```csharp
string[] files = Directory.GetFiles(@"C:\MyDocs\", "*.docx");
foreach (var file in files)
{
    Document d = new Document(file);
    d.Save(Path.ChangeExtension(file, ".txt"), txtOptions);
}
Console.WriteLine("Batch conversion complete.");
```

### Gestion des équations en ligne vs affichées

Aspose.Words détecte automatiquement le type d’équation en fonction de sa mise en page dans Word. Si vous devez imposer un style particulier, vous pouvez post‑traiter la sortie :

```csharp
string txt = File.ReadAllText(@"C:\MyDocs\Math.txt");
txt = txt.Replace("$", "\\(").Replace("$", "\\)"); // forces inline math delimiters
File.WriteAllText(@"C:\MyDocs\Math_fixed.txt", txt);
```

### Exportation vers d’autres formats

Si LaTeX n’est pas votre cible, il suffit de changer le mode d’exportation :

```csharp
txtOptions.OfficeMathExportMode = OfficeMathExportMode.MathML; // for MathML
```

Ou utilisez `HtmlSaveOptions` si vous préférez MathML intégré dans du HTML.

---

## Exemple complet fonctionnel

Voici le programme complet, prêt à être exécuté. Copiez‑collez‑le dans `Program.cs` d’un projet console .NET.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

namespace WordToLatexTxt
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the source document
            Document doc = new Document(@"C:\MyDocs\input.docx");

            // 2️⃣ Set up save options to export Office Math as LaTeX
            TxtSaveOptions saveOptions = new TxtSaveOptions
            {
                OfficeMathExportMode = OfficeMathExportMode.LaTeX,
                PreserveTableLayout = true
            };

            // 3️⃣ Save as plain‑text with LaTeX equations
            string outputPath = @"C:\MyDocs\Math.txt";
            doc.Save(outputPath, saveOptions);

            Console.WriteLine($"✅ Saved document as txt at: {outputPath}");
            Console.WriteLine("Open the file to see LaTeX‑formatted equations.");
        }
    }
}
```

Exécutez le programme (`dotnet run`), ouvrez `Math.txt`, et vous verrez votre contenu Word avec les équations LaTeX intactes.

---

## Questions fréquentes

**Q : Cette méthode fonctionne‑t‑elle avec les anciens fichiers .doc ?**  
R : Oui—Aspose.Words peut ouvrir les fichiers `.doc` anciens, mais les équations complexes peuvent être stockées sous forme d’images. Dans ce cas, l’exportateur revient à un commentaire de substitution.

**Q : Que faire si une équation contient des symboles personnalisés ?**  
R : Aspose.Words associe la plupart des symboles Office Math à des commandes LaTeX standard. Pour des symboles vraiment personnalisés, vous devrez peut‑être éditer manuellement le LaTeX généré.

**Q : La sortie est‑elle encodée en UTF‑8 ?**  
R : Par défaut, `TxtSaveOptions` écrit en UTF‑8, ce qui est sûr pour la plupart des langues et des symboles.

---

## Conclusion

Vous savez maintenant comment **enregistrer le document en txt** tout en conservant chaque équation sous forme de balisage LaTeX propre. Cette approche vous permet de **convertir Word en LaTeX** sans outils tiers, et elle s’étend d’un seul fichier à des dossiers entiers. Ensuite, vous pourriez explorer **convertir les équations Word en LaTeX** pour le traitement par lots, ou plonger dans **exporter les mathématiques Word en LaTeX** pour des pipelines HTML ou Markdown.

N’hésitez pas à expérimenter—remplacez `OfficeMathExportMode` par MathML, ajustez la gestion des sauts de ligne, ou intégrez cet extrait dans un flux de génération de documents plus vaste. Bon codage, et que vos équations s’affichent toujours parfaitement !

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}