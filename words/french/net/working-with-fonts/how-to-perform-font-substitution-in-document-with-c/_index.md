---
category: general
date: 2026-10-13
description: Apprenez la substitution de polices dans un document en utilisant C#.
  Ce guide montre comment définir l’encodage big5, charger un DOCX et remplacer les
  polices héritées par des polices modernes.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- font substitution in document
- big5 encoding
- C# LoadOptions
- legacy font replacement
- document encoding for Chinese
- Docx loading C#
language: fr
lastmod: 2026-10-13
og_description: La substitution de polices dans un document est essentielle lorsqu’on
  travaille avec des fichiers chinois anciens. Suivez ce tutoriel étape par étape
  pour charger un DOCX avec l’encodage big5 et remplacer les anciennes polices.
og_image_alt: Screenshot of C# code that performs font substitution in document
og_title: Substitution de police dans un document avec C# – guide complet
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn font substitution in document using C#. This guide shows how
    to set big5 encoding, load a DOCX, and replace legacy fonts with modern ones.
  headline: How to perform font substitution in document with C#
  type: TechArticle
tags:
- C#
- Aspose.Words
- Unicode
- Chinese text
title: Comment effectuer la substitution de police dans un document avec C#
url: /fr/net/working-with-fonts/how-to-perform-font-substitution-in-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Substitution de police dans le document – tutoriel complet C#

Si vous avez besoin de **font substitution in document** pour rendre correctement les fichiers chinois anciens, ce guide vous montre exactement comment procéder. En configurant le bon encodage de texte et en remplaçant une police obsolète par une police moderne, vous garantissez que le DOCX final s’affiche comme prévu.

Le traitement de documents échoue souvent lorsque la source utilise un ancien encodage comme **big5** ou fait référence à une police qui n’existe plus sur le système. Ce tutoriel vous guide pour charger un DOCX avec le bon **big5 encoding**, appliquer **legacy font replacement**, et produire une sortie propre qui fonctionne sur n’importe quelle machine Windows.

Vous apprendrez :

* Comment créer un objet `LoadOptions` avec **big5 encoding**.  
* Comment ouvrir un fichier DOCX en utilisant **C# LoadOptions**.  
* Comment effectuer **font substitution in document** en mappant une ancienne police à une équivalente moderne.  
* Gestion des cas limites pour les polices manquantes et les familles de polices multiples.

Aucun outil externe n’est requis au-delà de la bibliothèque Aspose.Words for .NET, et le code complet peut être copié dans un projet console et exécuté immédiatement.

## Prérequis

* .NET 6.0 ou version ultérieure (l’exemple utilise la syntaxe console .NET 6).  
* Aspose.Words for .NET – installer via `dotnet add package Aspose.Words`.  
* Un fichier DOCX enregistré avec **big5 encoding** qui fait référence à la police legacy `MingLiU-ExtB`.  
* Une connaissance de base de C# et de Visual Studio ou de tout IDE de votre choix.

## Étape 1 : Configurer le projet et importer les espaces de noms

Créez une nouvelle application console et ajoutez les directives `using` requises. Cela garantit que le code se compile sans modifications supplémentaires.

```csharp
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSubstitutionDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The tutorial steps are called from here.
            PerformFontSubstitution();
        }

        static void PerformFontSubstitution()
        {
            // Steps 2‑4 are implemented inside this method.
        }
    }
}
```

> **Astuce :** Gardez la méthode `Main` minimale ; cela améliore la lisibilité et rend le tutoriel plus facile à suivre.

## Étape 2 : Définir les options de chargement avec le bon encodage de texte (big5 pour le chinois traditionnel)

La classe `LoadOptions` indique à Aspose.Words comment interpréter les octets bruts du fichier source. Utiliser **big5 encoding** est essentiel pour les caractères chinois traditionnels qui ont été enregistrés avec cette page de code legacy.

```csharp
// Step 2: Define load options with big5 encoding.
LoadOptions loadOptions = new LoadOptions
{
    // Explicitly set the encoding to the traditional Chinese code page.
    Encoding = Encoding.GetEncoding("big5")
};
```

**Pourquoi c’est important :** Si vous omettez l’encodage ou utilisez l’UTF‑8 par défaut, les caractères peuvent apparaître comme des symboles illisibles (mojibake). Spécifier `big5` préserve les glyphes originaux avant toute substitution de police.

## Étape 3 : Charger le fichier DOCX en utilisant l’encodage spécifié

Passez l’instance `loadOptions` au constructeur `Document`. Cela charge le fichier tout en respectant le **document encoding for Chinese** que vous avez défini précédemment.

```csharp
// Step 3: Load the DOCX file with the big5 encoding.
string inputPath = @"C:\Docs\big5_doc.docx"; // Update this path to your file location.
Document doc = new Document(inputPath, loadOptions);
```

Si le fichier est introuvable, le programme lève une `FileNotFoundException`. Assurez‑vous que le chemin est correct et que l’application possède les permissions de lecture.

## Étape 4 : Substituer une police legacy par une équivalente moderne

De nombreux documents chinois anciens font référence à `MingLiU-ExtB`, qui peut ne pas être présent sur les installations Windows récentes. Le mapper à `Microsoft JhengHei` (une police Unicode largement disponible) assure un rendu correct.

```csharp
// Step 4: Perform font substitution in document.
doc.FontInfos.Substitution.Add("MingLiU-ExtB", "Microsoft JhengHei");

// Optional: Verify that the substitution succeeded.
foreach (FontInfo fontInfo in doc.FontInfos)
{
    Console.WriteLine($"Original: {fontInfo.FontFamilyName}, Substituted: {fontInfo.SubstitutedFontFamilyName}");
}
```

**Explication  :**  
- `FontInfos.Substitution.Add(oldFont, newFont)` enregistre une règle de remplacement globale. Chaque fois qu’Aspose.Words rencontre `MingLiU-ExtB`, il le remplace par `Microsoft JhengHei`.  
- La boucle optionnelle affiche le mappage, ce qui est utile pour le débogage dans les gros documents contenant plusieurs familles de polices.

## Étape 5 : Enregistrer le document traité

Après la substitution, écrivez le document dans un nouveau fichier. La sortie affichera le texte chinois en utilisant la police moderne, éliminant les avertissements de glyphes manquants.

```csharp
// Step 5: Save the updated document.
string outputPath = @"C:\Docs\big5_doc_fixed.docx";
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved to {outputPath}");
```

Ouvrez le fichier résultant dans Microsoft Word ou tout visualiseur DOCX ; vous devriez voir les caractères chinois traditionnels rendus proprement avec `Microsoft JhengHei`.

## Gestion des cas limites et des pièges courants

| Situation | Approche recommandée |
|-----------|----------------------|
| **La police source n’est pas répertoriée dans le document** | Utilisez `doc.FontInfos.Substitution.Add` avec un motif générique, par ex., `doc.FontInfos.Substitution.Add("*MingLiU*", "Microsoft JhengHei")`. |
| **Plusieurs polices legacy nécessitent un remplacement** | Appelez `Add` pour chaque paire, ou chargez un dictionnaire de substitution depuis un fichier de configuration. |
| **La police cible n’est pas disponible sur la machine cible** | Choisissez une police fournie avec Windows (par ex., `Arial Unicode MS`) ou intégrez la police en utilisant `doc.FontInfos.EmbeddingMode = FontEmbeddingMode.EmbedAll`. |
| **Des erreurs d’encodage apparaissent toujours** | Vérifiez que le fichier source utilise réellement **big5** ; vous pouvez inspecter le fichier avec un éditeur hexadécimal ou utiliser `File.ReadAllBytes` et comparer les motifs d’octets. |

## Exemple complet fonctionnel

Ci‑dessus se trouve le programme complet et autonome. Copiez‑le dans `Program.cs`, ajustez les chemins de fichiers, et exécutez‑le.

```csharp
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSubstitutionDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            PerformFontSubstitution();
        }

        static void PerformFontSubstitution()
        {
            // 1️⃣ Define big5 encoding for Traditional Chinese.
            LoadOptions loadOptions = new LoadOptions
            {
                Encoding = Encoding.GetEncoding("big5")
            };

            // 2️⃣ Load the DOCX that uses the legacy font.
            string inputPath = @"C:\Docs\big5_doc.docx";
            Document doc = new Document(inputPath, loadOptions);

            // 3️⃣ Substitute MingLiU-ExtB with Microsoft JhengHei.
            doc.FontInfos.Substitution.Add("MingLiU-ExtB", "Microsoft JhengHei");

            // 4️⃣ (Optional) Log substitution details for verification.
            foreach (FontInfo fontInfo in doc.FontInfos)
            {
                Console.WriteLine($"Original: {fontInfo.FontFamilyName}, Substituted: {fontInfo.SubstitutedFontFamilyName}");
            }

            // 5️⃣ Save the corrected document.
            string outputPath = @"C:\Docs\big5_doc_fixed.docx";
            doc.Save(outputPath, SaveFormat.Docx);

            Console.WriteLine($"✅ Font substitution in document completed. Output saved to {outputPath}");
        }
    }
}
```

**Résultat attendu :** L’ouverture de `big5_doc_fixed.docx` montre tous les caractères chinois traditionnels correctement rendus, sans avertissements de glyphes manquants, car `MingLiU-ExtB` a été remplacé par `Microsoft JhengHei`.

## Conclusion

Vous disposez maintenant d’une méthode fiable pour les tâches de **font substitution in document** en C#. En configurant **big5 encoding**, en chargeant le DOCX avec `LoadOptions`, et en mappant les polices legacy vers des équivalents modernes, vous éliminez les problèmes de rendu qui affectent les anciens fichiers chinois.

À partir d’ici, vous pouvez :

* Étendre la carte de substitution pour couvrir d’autres polices legacy.  
* Automatiser le processus pour des lots de documents (boucler sur un répertoire).  
* Combiner la substitution de police avec d’autres transformations de documents telles que le filigrane ou la conversion PDF.

N’hésitez pas à expérimenter avec différentes polices cibles ou à intégrer des polices personnalisées pour une portabilité totale. Si vous rencontrez des problèmes, consultez à nouveau le tableau des cas limites ci‑dessus ou la documentation Aspose.Words pour la gestion avancée des polices.

Bonne programmation !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Activer les avertissements de substitution de police dans Aspose.Words – Guide complet](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Journaliser les avertissements de substitution de police – Guide complet Aspose.Words](/words/english/net/working-with-fonts/log-font-substitution-warnings-complete-aspose-words-guide/)
- [Charger avec encodage dans un document Word](/words/english/net/programming-with-loadoptions/load-with-encoding/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}