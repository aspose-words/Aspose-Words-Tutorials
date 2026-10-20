---
category: general
date: 2026-04-21
description: Apprenez à détecter les polices, capturer les avertissements, configurer
  le rappel et énumérer les avertissements avec Aspose.Words en C#. Guide étape par
  étape pour une gestion fiable des polices.
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- how to configure callback
- how to enumerate warnings
- Aspose.Words font handling
language: fr
og_description: Comment détecter les polices dans Aspose.Words ? Ce tutoriel vous
  montre comment capturer les avertissements, configurer un rappel et énumérer les
  avertissements en C#.
og_title: Comment détecter les polices dans Aspose.Words – Guide complet
tags:
- Aspose.Words
- C#
- Document Processing
title: Comment détecter les polices dans Aspose.Words – Guide complet
url: /fr/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment détecter les polices dans Aspose.Words – Guide complet

Vous êtes‑vous déjà demandé **comment détecter les polices** manquantes lors du chargement d'un document Word ? C’est un scénario qui apparaît plus souvent que vous ne le souhaiteriez, surtout lorsqu’on travaille avec des fichiers anciens ou des déploiements multiplateformes. Dans ce tutoriel, nous parcourrons un exemple complet et exécutable qui **capture les avertissements**, **configure un rappel**, et **énumère les avertissements** afin que vous sachiez toujours quelles polices ont été substituées.

Nous utiliserons Aspose.Words for .NET (v24.9 au moment de la rédaction) et du C# pur. Aucun service externe, aucune magie—juste l’API et quelques lignes de code. À la fin, vous pourrez repérer chaque substitution de police, l’enregistrer, et même décider d’interrompre le chargement si une police critique est manquante.  

### Ce dont vous avez besoin
- **Aspose.Words for .NET** (installez via NuGet : `Install-Package Aspose.Words`)
- .NET 6.0 ou ultérieur (le code fonctionne également sur .NET Framework)
- Un fichier DOCX d’exemple qui référence une police non présente sur la machine (par ex., “MyCustomFont.ttf”)
- Visual Studio, Rider ou tout éditeur C# de votre choix

> **Conseil pro :** Si vous n’avez pas de document avec des polices manquantes, renommez simplement un fichier de police sur votre système ou modifiez le XML du DOCX pour référencer une famille de polices inexistante.

---

## Comment détecter les polices avec Aspose.Words

L’idée principale est d’intercepter le système d’avertissement d’Aspose.Words. Lorsque la bibliothèque ne trouve pas une police demandée, elle émet un avertissement `WarningType.FontSubstitution`. En fournissant une implémentation personnalisée de `IWarningCallback`, vous pouvez **détecter les polices** qui ont été remplacées pendant le processus de chargement.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a collector that implements IWarningCallback
public class FontWarningCollector : IWarningCallback
{
    public List<WarningInfo> Warnings { get; } = new();

    public void Warning(WarningInfo info)
    {
        // Store every warning – we’ll filter later
        Warnings.Add(info);
    }
}
```

> **Pourquoi cela fonctionne :** Aspose.Words appelle la méthode `Warning` pour chaque problème non critique. En stockant les objets `WarningInfo`, vous avez un accès complet au type, au message et au contexte, ce qui est exactement ce dont vous avez besoin pour **détecter les polices** qui ont été substituées.

---

## Comment capturer les avertissements lors du chargement d’un document

Maintenant que nous disposons d’un collecteur, nous devons indiquer à `LoadOptions` de l’utiliser. C’est la partie **comment capturer les avertissements** du puzzle.

```csharp
// 2️⃣ Prepare LoadOptions with our warning collector
var warningCollector = new FontWarningCollector();
var loadOptions = new LoadOptions
{
    // Assign the callback – this is where warnings are captured
    WarningCallback = warningCollector
};

// 3️⃣ Load the document (replace the path with your own file)
Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFont.docx", loadOptions);
```

> **Cas particulier :** Si vous chargez un document depuis un flux (`new Document(stream, loadOptions)`), le même rappel fonctionne—il suffit de passer le flux au lieu d’un chemin de fichier.

À ce stade, le document est entièrement chargé, mais tous les avertissements de substitution de police sont stockés en toute sécurité dans `warningCollector.Warnings`.

---

## Comment énumérer les avertissements et signaler les substitutions de polices

Enfin, nous parcourons les avertissements collectés et **énumérons les avertissements** qui concernent spécifiquement la substitution de police. Cette étape transforme les données brutes en un rapport lisible.

```csharp
// 4️⃣ Iterate over the collected warnings
foreach (var warning in warningCollector.Warnings)
{
    // We're only interested in font substitution warnings
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Substituted font: {warning.Message}");
    }
}
```

**Sortie attendue** (exemple) :

```
Substituted font: Font 'Calibri' not found. Substituted with 'Arial'.
Substituted font: Font 'MyCustomFont' not found. Substituted with 'Times New Roman'.
```

Si le document ne contient aucune police manquante, la boucle ne produit simplement aucune sortie—rien à signaler.

---

## Exemple complet fonctionnel (Toutes les étapes dans un seul fichier)

Ci-dessous se trouve le programme complet que vous pouvez copier‑coller dans un projet console. Il regroupe **comment détecter les polices**, **comment capturer les avertissements**, **comment configurer le rappel**, et **comment énumérer les avertissements** dans un flux unique et cohérent.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontDetectionDemo
{
    // Custom warning collector (captures all warnings)
    public class FontWarningCollector : IWarningCallback
    {
        public List<WarningInfo> Warnings { get; } = new();

        public void Warning(WarningInfo info)
        {
            Warnings.Add(info);
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // -------------------------------------------------
            // Step 1: Set up the warning collector (how to configure callback)
            var collector = new FontWarningCollector();
            var loadOptions = new LoadOptions
            {
                WarningCallback = collector
            };

            // -------------------------------------------------
            // Step 2: Load the document (how to detect fonts)
            string filePath = "YOUR_DIRECTORY/DocumentWithMissingFont.docx";
            Document doc;
            try
            {
                doc = new Document(filePath, loadOptions);
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Failed to load document: {ex.Message}");
                return;
            }

            // -------------------------------------------------
            // Step 3: Enumerate warnings (how to enumerate warnings)
            bool anySubstitutions = false;
            foreach (var warning in collector.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    anySubstitutions = true;
                    Console.WriteLine($"Substituted font: {warning.Message}");
                }
            }

            if (!anySubstitutions)
            {
                Console.WriteLine("No font substitutions detected – all fonts are available.");
            }

            // Optional: Continue processing the document...
        }
    }
}
```

**L’exécution de ce programme** affichera chaque police qu’Aspose.Words a dû remplacer. Vous pouvez rediriger la sortie vers un fichier de log, déclencher une alerte, ou même interrompre le chargement si une police critique est manquante.

---

## Questions fréquentes & pièges

### Et si je dois arrêter le chargement lorsqu’une police requise est manquante ?

Vous pouvez inspecter les objets `WarningInfo` dans le rappel et lever une exception lorsqu’un nom de police particulier apparaît. L’exception interrompra le chargement, vous donnant un contrôle total.

```csharp
public void Warning(WarningInfo info)
{
    if (info.Type == WarningType.FontSubstitution &&
        info.Message.Contains("MyCriticalFont"))
    {
        throw new InvalidOperationException("Critical font missing – aborting load.");
    }
    Warnings.Add(info);
}
```

### Cela fonctionne-t-il avec les PDF ou d’autres formats ?

Oui. Aspose.Words utilise la même infrastructure d’avertissement pour les PDF, RTF et HTML. Il suffit de remplacer l’extension du fichier et le reste du code reste identique.

### Comment puis‑je enregistrer les avertissements dans un fichier au lieu de la console ?

Remplacez `Console.WriteLine` par n’importe quel framework de journalisation que vous préférez (`Serilog`, `NLog`, etc.). La classe `WarningInfo` expose `Message`, `Source` et `Exception` pour des journaux détaillés.

### Cela aura-t-il un impact sur les performances ?

La surcharge est négligeable—Aspose.Words génère déjà les avertissements en interne. Ajouter un rappel se contente de les stocker dans une liste, ce qui est O(n) en fonction du nombre d’avertissements. Pour des documents typiques, l’impact est bien inférieur à 1 % du temps total de chargement.

---

## Résumé visuel

![Comment détecter les polices dans Aspose.Words – diagramme du flux d’avertissement](https://example.com/images/font-detection-diagram.png "comment détecter les polices")

*Texte alternatif :* **comment détecter les polices** – diagramme montrant le rappel d’avertissement, la collecte et les étapes d’énumération.

---

## Conclusion

Nous avons couvert **comment détecter les polices** dans Aspose.Words en **capturant les avertissements**, **configurant un rappel**, et **énumérant les avertissements**. L’exemple complet de code montre un modèle prêt pour la production que vous pouvez intégrer dans n’importe quelle application .NET.  

Ensuite, vous pourriez explorer :

- **Comment capturer les avertissements** pour d’autres problèmes (par ex., problèmes de conversion d’image)
- **Comment configurer le rappel** pour des frameworks de journalisation personnalisés
- **Comment énumérer les avertissements** sur plusieurs documents dans un travail par lots
- Utiliser **Aspose.Words.Fonts.FontSettings** pour fournir des dossiers de polices de secours, ce qui peut réduire le nombre de substitutions dès le départ.

Essayez, ajustez le collecteur pour qu’il corresponde à votre style de journalisation, et vous ne serez plus jamais surpris par un remplacement de police inattendu. Si vous rencontrez des particularités, laissez un commentaire ci‑dessous—bon codage !

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}