---
category: general
date: 2026-02-21
description: Apprenez comment activer les avertissements, détecter les polices manquantes
  et charger un fichier docx en toute sécurité avec Aspose.Words en C#. Suivez le
  guide étape par étape.
draft: false
keywords:
- how to enable warnings
- detect missing fonts
- how to load docx
- font substitution handling
- Aspose.Words warnings
language: fr
og_description: Comment activer les avertissements, détecter les polices manquantes
  et charger correctement les fichiers docx avec Aspose.Words. Exemple de code complet
  inclus.
og_title: Comment activer les avertissements et détecter les polices manquantes lors
  du chargement d’un DOCX
tags:
- C#
- Aspose.Words
- Document processing
title: Comment activer les avertissements et détecter les polices manquantes lors
  du chargement de fichiers DOCX
url: /fr/net/working-with-fonts/how-to-enable-warnings-and-detect-missing-fonts-when-loading/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment activer les avertissements et détecter les polices manquantes lors du chargement de fichiers DOCX

Vous vous êtes déjà demandé **comment activer les avertissements** pour les polices manquantes avant qu’elles ne perturbent silencieusement le rendu de votre document ? Vous n’êtes pas seul — la plupart des développeurs supposent que la bibliothèque « fera la bonne chose », pour découvrir plus tard qu’une police a été remplacée sans le moindre indice.  

Dans ce tutoriel, nous vous montrons exactement **comment activer les avertissements**, comment **détecter les polices manquantes**, et la bonne façon **de charger un docx** avec Aspose.Words pour .NET. À la fin, vous disposerez d’un exemple prêt à l’emploi qui affiche chaque avertissement de substitution de police dans la console, afin que vous n'ayez plus jamais à deviner ce qui s’est passé à l’intérieur du fichier.

## Prérequis

- .NET 6.0 ou version ultérieure (le code fonctionne également avec .NET Framework 4.7+)  
- Visual Studio 2022 ou tout IDE C# de votre choix  
- Le package NuGet **Aspose.Words** (`Install-Package Aspose.Words`)  
- Un fichier DOCX pouvant contenir des polices non installées sur votre machine (nous l’appellerons `input.docx`)

> **Astuce :** Si vous n’avez pas de fichier de test, ouvrez simplement un document Word qui utilise une police d’entreprise personnalisée et enregistrez‑le sous le nom `input.docx`. Cela déclenchera l’avertissement que nous voulons capturer.

## Vue d’ensemble de la solution

1. **Créer** un objet `LoadOptions` avec `FontSubstitutionWarnings` activé.  
2. **Charger** le fichier DOCX en utilisant ces options.  
3. **Inspecter** la collection `WarningCallback` pour toute entrée `FontSubstitution`.  
4. **Réagir** – vous pouvez journaliser, afficher ou même remplacer la police manquante par programme.

Ci‑dessous, nous détaillons chaque étape, expliquons *pourquoi* elle est importante, et vous fournissons un extrait de code complet et exécutable.

---

## Étape 1 : Installer Aspose.Words et configurer le projet

Avant de pouvoir **activer les avertissements**, nous avons besoin de la bibliothèque qui les prend réellement en charge.

```bash
# Using the .NET CLI
dotnet add package Aspose.Words
```

Ou, dans la console du Gestionnaire de packages Visual Studio :

```powershell
Install-Package Aspose.Words
```

> **Pourquoi cette étape ?**  
> Sans le package, les classes `LoadOptions`, `Document` et l’infrastructure d’avertissement n’existent tout simplement pas. Ajouter la référence NuGet garantit que vous utilisez la dernière version stable (au moment de la rédaction, 24.5).

---

## Étape 2 : Créer des options de chargement qui activent les avertissements de substitution de police

Le cœur de **comment activer les avertissements** se trouve dans la classe `LoadOptions`. Mettre `FontSubstitutionWarnings` à `true` indique au moteur d’enregistrer chaque fois qu’il doit remplacer une police manquante.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Step 2: Build the options object
LoadOptions loadOptions = new LoadOptions
{
    // This flag makes the library emit warnings for any font it cannot find.
    FontSubstitutionWarnings = true
};
```

> **Pourquoi activer ce drapeau ?**  
> Par défaut, Aspose.Words remplace silencieusement les polices manquantes par une police de secours (généralement Arial). Cela peut entraîner des décalages de mise en page, des caractères invisibles ou des violations de la charte graphique. Activer le drapeau vous donne une visibilité totale.

---

## Étape 3 : Charger le fichier DOCX avec les options configurées

Maintenant que nous savons **comment charger un docx** avec les avertissements activés, nous procédons réellement au chargement.

```csharp
// Step 3: Load the document – replace the path with your own file location.
string docPath = @"YOUR_DIRECTORY\input.docx";
Document document = new Document(docPath, loadOptions);
```

> **Que se passe-t-il en coulisses ?**  
> Lors de l’analyse du DOCX, Aspose.Words examine chaque élément `<w:rFonts>`. Si la police spécifiée n’est pas installée, il enregistre un avertissement `FontSubstitution` et revient à une police par défaut. Parce que nous avons activé les avertissements, ces entrées se retrouvent dans `document.WarningCallback.Warnings`.

---

## Étape 4 : Récupérer et afficher les avertissements de substitution de police

La propriété `WarningCallback` contient une `WarningInfoCollection`. Parcourez‑la, filtrez les éléments de type `WarningType.FontSubstitution`, et affichez les messages.

```csharp
// Step 4: Iterate over warnings and print font‑substitution details.
foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substituted: {warning.Message}");
    }
}
```

**Sortie attendue** (exemple) :

```
⚠️ Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
⚠️ Font substituted: Font 'CorporateLogo' was not found. Substituted with 'Times New Roman'.
```

> **Que faire de ces messages ?**  
> Vous pouvez les journaliser dans un fichier, les afficher dans une interface utilisateur, ou même déclencher une routine de secours de police personnalisée. L’essentiel est que vous *détectiez maintenant les polices manquantes* au lieu de deviner plus tard.

---

## Étape 5 : (Facultatif) Remplacer les polices manquantes par une police de secours spécifique

Si vous disposez d’une police d’entreprise que vous souhaitez imposer, vous pouvez gérer les avertissements et les remplacer à la volée.

```csharp
// Optional: Custom fallback font
string fallbackFont = "Calibri";

foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        // Extract the missing font name from the warning message
        string missingFont = warning.Message.Split('\'')[1];
        Console.WriteLine($"Replacing missing font '{missingFont}' with '{fallbackFont}'");
        document.FontInfos[missingFont].SubstitutedFont = fallbackFont;
    }
}
```

> **Pourquoi envisager cela ?**  
> Cela garantit une cohérence visuelle sur tous les documents générés, ce qui est crucial pour le respect de la marque.

---

## Exemple complet, exécutable

Voici un fichier C# unique que vous pouvez copier‑coller dans une application console. Il couvre tout — de l’installation du package à l’impression des avertissements.

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create LoadOptions with warnings enabled
            LoadOptions loadOptions = new LoadOptions
            {
                FontSubstitutionWarnings = true
            };

            // 2️⃣ Load the DOCX (adjust the path as needed)
            string docPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Show all font‑substitution warnings
            Console.WriteLine("=== Font Substitution Warnings ===");
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Message}");
                }
            }

            // 4️⃣ (Optional) Replace missing fonts with Calibri
            string fallback = "Calibri";
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    string missingFont = warning.Message.Split('\'')[1];
                    Console.WriteLine($"Replacing '{missingFont}' with '{fallback}'");
                    doc.FontInfos[missingFont].SubstitutedFont = fallback;
                }
            }

            // 5️⃣ Save the corrected document (optional)
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

**Exécutez‑le** : `dotnet run` depuis le dossier du projet. Si des polices sont manquantes, vous verrez les avertissements affichés, et le remplacement optionnel sera appliqué avant l’enregistrement du fichier.

---

## Foire aux questions

### Cela fonctionne‑t‑il également avec la conversion PDF ?

Oui. Après avoir géré les avertissements, vous pouvez appeler `doc.Save("output.pdf")` et les polices substituées apparaîtront dans le PDF comme dans le DOCX.

### Et si je veux supprimer les avertissements pour une police spécifique ?

Vous pouvez les filtrer dans la boucle — il suffit d’ignorer le `WarningInfo` dont le `Message` contient le nom de la police que vous souhaitez ignorer.

### `FontSubstitutionWarnings` est‑il disponible dans les anciennes versions d’Aspose.Words ?

Il a été introduit dans la version 20.5. Si vous êtes bloqué sur une version antérieure, mettez à jour via NuGet ; le changement d’API est rétrocompatible.

---

## Conclusion

Nous avons parcouru **comment activer les avertissements**, vous avons montré **comment détecter les polices manquantes**, et démontré la bonne façon **de charger un docx** avec Aspose.Words tout en conservant une visibilité totale sur les substitutions de police. En inspectant `document.WarningCallback.Warnings`, vous obtenez une piste d’audit fiable — plus aucun remplacement silencieux.

Prochaines étapes ? Essayez d’intégrer la logique d’avertissement à un framework de journalisation comme Serilog, ou créez une interface qui met en évidence les polices manquantes avant de livrer le document aux utilisateurs. Vous pouvez également explorer la classe `FontSettings` pour un contrôle plus granulaire des politiques de substitution de police.

Bon codage, et que vos documents s’affichent toujours exactement comme vous le souhaitez ! 

![Diagram illustrating the flow from loading a DOCX file to capturing font substitution warnings – how to enable warnings in Aspose.Words](/images/font-warning-flow.png)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}