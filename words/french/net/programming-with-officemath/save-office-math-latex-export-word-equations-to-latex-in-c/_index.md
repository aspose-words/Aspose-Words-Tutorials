---
category: general
date: 2026-04-21
description: Enregistrez rapidement le LaTeX des formules Office avec Aspose.Words
  – apprenez également à enregistrer le texte brut de Word et à exporter les équations
  Word en LaTeX en une seule opération.
draft: false
keywords:
- save office math latex
- save word plain text
- export word equations latex
- convert word math latex
- convert word equations mathml
language: fr
og_description: enregistrez le LaTeX des mathématiques Office instantanément ; apprenez
  à exporter les équations Word en LaTeX et à convertir le LaTeX des mathématiques
  Word avec Aspose.Words en C#.
og_title: sauvegarder Office Math LaTeX – Exporter les équations Word vers LaTeX
tags:
- Aspose.Words
- C#
- LaTeX
title: sauvegarder office math latex – Exporter les équations Word vers LaTeX en C#
url: /fr/net/programming-with-officemath/save-office-math-latex-export-word-equations-to-latex-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# save office math latex – Export Word equations to LaTeX with Aspose.Words

Vous avez déjà eu besoin de **save office math latex** à partir d’un fichier `.docx` sans savoir par où commencer ? Vous n’êtes pas seul, et la bonne nouvelle, c’est que la solution est assez simple. Dans ce guide, nous parcourrons les étapes exactes pour exporter les équations Word en LaTeX (et même en MathML) avec Aspose.Words for .NET, tout en vous montrant comment **save word plain text** en même temps que les formules.

Nous couvrirons tout ce qui peut vous venir à l’esprit : pourquoi choisir LaTeX plutôt que d’autres formats, comment configurer le `TxtSaveOptions`, et quoi faire si vous devez **convert word math latex** vers une autre représentation. À la fin, vous disposerez d’un extrait fonctionnel qui prend un document Word contenant des objets Office Math et génère un fichier `.txt` propre contenant les équations LaTeX (ou MathML). Aucun outil externe, aucune copie‑collage manuelle — juste du code C# propre que vous pouvez intégrer à n’importe quel projet.

## Prérequis

- **Aspose.Words for .NET** (v23.10 ou ultérieure). Le package NuGet est `Aspose.Words`.
- Un environnement de développement .NET (Visual Studio, Rider, ou VS Code avec l’extension C#).
- Un fichier Word (`.docx`) contenant au moins une équation créée avec l’éditeur Office Math.
- Une connaissance de base de la syntaxe C# — rien de spécial, juste les habituelles instructions `using`.

Si ces points sont déjà cochés, super — plongeons‑y.

## Étape 1 – Configurer les options **save office math latex**

La première chose à faire est d’indiquer à Aspose.Words comment vous souhaitez que le contenu mathématique soit rendu. La classe `TxtSaveOptions` possède une propriété `OfficeMathExportMode` qui accepte trois valeurs : `LaTeX`, `MathML` ou `Text`. Pour notre objectif principal, nous choisirons `LaTeX`.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Configure TXT save options to export equations as LaTeX
TxtSaveOptions txtOptions = new TxtSaveOptions
{
    // This line makes the library output LaTeX for every Office Math object
    OfficeMathExportMode = OfficeMathExportMode.LaTeX
    // You could also use OfficeMathExportMode.MathML or .Text here
};
```

**Pourquoi c’est important :** Lorsque vous définissez `OfficeMathExportMode` sur `LaTeX`, chaque équation est transformée en son code source LaTeX brut. Ce code peut ensuite être compilé avec n’importe quel moteur LaTeX, vous offrant une mise en page parfaite sans avoir à retaper les formules.

> **Astuce :** Si vous devez un jour **convert word equations mathml**, il suffit de remplacer la valeur de l’énumération par `OfficeMathExportMode.MathML`. Le reste du code reste identique.

## Étape 2 – Charger le document Word (scénario **save word plain text**)

Ensuite, nous chargeons le fichier source `.docx`. Cette étape est identique que vous soyez uniquement intéressé par l’extraction du texte brut ou que vous vouliez aussi les équations en LaTeX.

```csharp
// Load the document that contains Office Math objects
Document doc = new Document(@"C:\MyDocs\input.docx");

// Optional: verify that the document actually has equations
bool hasMath = doc.GetChildNodes(NodeType.OfficeMath, true).Count > 0;
if (!hasMath)
{
    Console.WriteLine("Warning: No Office Math objects found in the document.");
}
```

**Que se passe‑t‑il ici ?** Le constructeur `Document` lit le fichier en mémoire. Le contrôle rapide avec `GetChildNodes` vous permet de détecter un cas fréquent — tenter d’exporter du LaTeX depuis un fichier qui ne contient aucune équation. C’est une petite précaution qui évite d’obtenir un résultat vide et déroutant plus tard.

## Étape 3 – **save office math latex** dans un fichier texte

Nous écrivons enfin le fichier. La méthode `Save` respecte les `TxtSaveOptions` que nous avons configurées précédemment, de sorte que le `.txt` résultant contiendra à la fois le texte ordinaire et les extraits LaTeX de chaque équation.

```csharp
// Define the output path
string outputPath = @"C:\MyDocs\Equations.txt";

// Save the document as plain text, with LaTeX equations embedded
doc.Save(outputPath, txtOptions);

Console.WriteLine($"Document saved successfully to {outputPath}");
```

Lorsque vous ouvrez `Equations.txt`, vous verrez quelque chose comme :

```
This is a sample paragraph.

\begin{equation}
E = mc^2
\end{equation}

Another paragraph follows.
```

Les blocs LaTeX sont automatiquement entourés de `\begin{equation}` … `\end{equation}`, ce qui les rend prêts à être inclus dans n’importe quel document LaTeX.

## Étape 4 – Alternative : **convert word equations mathml** au lieu de LaTeX

Si votre chaîne d’outils en aval préfère le MathML (par exemple, une page web qui rend les équations avec MathJax), il suffit de changer le mode d’exportation :

```csharp
txtOptions.OfficeMathExportMode = OfficeMathExportMode.MathML;
doc.Save(@"C:\MyDocs\EquationsMathML.txt", txtOptions);
```

Le résultat contiendra maintenant des balises MathML de type XML, telles que :

```xml
<math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi>E</mi>
  <mo>=</mo>
  <mi>m</mi>
  <msup><mi>c</mi><mn>2</mn></msup>
</math>
```

C’est la façon rapide de **convert word equations mathml** sans écrire de parseur personnalisé.

## Étape 5 – Bonus : **save word plain text** tout en gardant les équations séparées

Parfois, vous avez besoin d’une version texte propre du document *sans* LaTeX ni MathML intégrés. Vous pouvez y parvenir en passant le mode d’exportation à `Text` et en exécutant une seconde passe de sauvegarde :

```csharp
// Export pure plain text (no math markup)
txtOptions.OfficeMathExportMode = OfficeMathExportMode.Text;
doc.Save(@"C:\MyDocs\PlainDocument.txt", txtOptions);
```

Vous obtenez alors trois fichiers côte à côte :

| Fichier                       | Contenu                                 |
|------------------------------|------------------------------------------|
| `Equations.txt`              | Texte brut **+** équations LaTeX         |
| `EquationsMathML.txt`        | Texte brut **+** équations MathML        |
| `PlainDocument.txt`          | Texte pur, équations supprimées          |

Ce schéma est pratique lorsque vous devez alimenter un index de recherche avec le texte brut tout en conservant les formules originales pour la publication académique.

## Exemple complet (prêt à copier‑coller)

Voici le programme complet que vous pouvez compiler et exécuter tel quel. Il montre **save office math latex**, **export word equations latex**, **convert word math latex**, et **save word plain text** — le tout dans un seul script bien organisé.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Configure TXT save options for LaTeX export
        TxtSaveOptions txtOptions = new TxtSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };

        // 2️⃣ Load the source Word document
        string inputPath = @"C:\MyDocs\input.docx";
        Document doc = new Document(inputPath);

        // Quick sanity check for equations
        if (doc.GetChildNodes(NodeType.OfficeMath, true).Count == 0)
        {
            Console.WriteLine("No equations found – proceeding with plain‑text export only.");
        }

        // 3️⃣ Save with LaTeX equations embedded
        string latexPath = @"C:\MyDocs\Equations.txt";
        doc.Save(latexPath, txtOptions);
        Console.WriteLine($"LaTeX export saved to {latexPath}");

        // 4️⃣ Switch to MathML and save (optional)
        txtOptions.OfficeMathExportMode = OfficeMathExportMode.MathML;
        string mathmlPath = @"C:\MyDocs\EquationsMathML.txt";
        doc.Save(mathmlPath, txtOptions);
        Console.WriteLine($"MathML export saved to {mathmlPath}");

        // 5️⃣ Finally, pure plain‑text export (no math markup)
        txtOptions.OfficeMathExportMode = OfficeMathExportMode.Text;
        string plainPath = @"C:\MyDocs\PlainDocument.txt";
        doc.Save(plainPath, txtOptions);
        Console.WriteLine($"Plain‑text export saved to {plainPath}");
    }
}
```

**Résultat attendu :** Après exécution, vous trouverez trois fichiers texte dans `C:\MyDocs`. Ouvrez `Equations.txt` et vous verrez les blocs LaTeX ; `EquationsMathML.txt` contiendra du MathML ; `PlainDocument.txt` sera dépourvu de toute balise d’équation.

## Questions fréquentes & cas particuliers

- **Et si je ne veux le LaTeX que pour un sous‑ensemble d’équations ?**  
  Utilisez l’API des nœuds `OfficeMath` pour parcourir chaque équation, l’exporter manuellement avec `MathConverter`, et remplacer le texte de substitution où vous le désirez. Cette approche offre un contrôle fin mais ajoute quelques lignes de code supplémentaires.

- **Cela fonctionne‑t‑il avec .NET Core / .NET 5+ ?**  
  Absolument. Aspose.Words est multiplateforme, donc le même code s’exécute sous Windows, Linux et macOS tant que la version du runtime correspond aux exigences de la bibliothèque.

- **Puis‑je changer le wrapper LaTeX (`\begin{equation}`) pour autre chose ?**  
  Oui. Définissez `txtOptions.OfficeMathExportMode = OfficeMathExportMode.LaTeX` puis modifiez `txtOptions.MathExportSettings` (disponible dans les versions récentes) pour personnaliser les délimiteurs.

- **Des problèmes de performance pour de très gros documents ?**  
  La bibliothèque diffuse la sortie, de sorte que l’utilisation mémoire reste modeste. Cependant

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}