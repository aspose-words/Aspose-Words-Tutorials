---
category: general
date: 2026-03-28
description: Comment capturer les avertissements lors du chargement d’un DOCX avec
  Aspose.Words et obtenir les messages d’avertissement pour les polices manquantes.
  Apprenez à gérer efficacement les polices manquantes.
draft: false
keywords:
- how to capture warnings
- get warning messages
- handle missing fonts
- Aspose.Words warning callback
- font substitution warning
language: fr
og_description: Comment capturer les avertissements lors du chargement d’un DOCX avec
  Aspose.Words, obtenir les messages d’avertissement et gérer les polices manquantes
  avec des exemples de code pratiques.
og_title: Comment capturer les avertissements dans Aspose.Words – Guide complet C#
tags:
- Aspose.Words
- C#
- Document Processing
title: Comment capturer les avertissements dans Aspose.Words – Guide complet C#
url: /fr/net/working-with-fonts/how-to-capture-warnings-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment capturer les avertissements dans Aspose.Words – Guide complet C#

Vous vous êtes déjà demandé **comment capturer les avertissements** qui apparaissent lorsque vous chargez un document Word avec Aspose.Words ? Peut‑être voyez‑vous des changements de police étranges et vous avez besoin de savoir exactement pourquoi. En bref, vous pouvez vous brancher sur le système d’avertissement de la bibliothèque, **obtenir les messages d’avertissement**, et même **gérer les polices manquantes** avant qu’elles ne gâchent votre mise en page.  

Dans ce tutoriel, nous parcourrons un scénario réel : charger un DOCX, collecter chaque avertissement émis par le moteur, et afficher les détails de toute substitution de police qui se produit. À la fin, vous disposerez d’un exemple de code prêt à l’emploi, comprendrez le « pourquoi » de chaque étape, et saurez comment étendre l’approche à vos propres projets.

## Ce que vous allez apprendre

- Comment configurer `LoadOptions` afin que les avertissements soient capturés automatiquement.  
- La façon exacte d’**obtenir les messages d’avertissement** depuis la `WarningInfoCollection`.  
- Comment identifier et réagir aux **polices manquantes** via le drapeau `WarningType.FontSubstitution`.  
- Astuces pour dépanner les cas limites, comme les documents contenant des polices intégrées ou des dossiers de polices personnalisés.  

Aucune référence externe n’est nécessaire – tout ce dont vous avez besoin se trouve ici.

---

## Prérequis

- .NET 6.0 ou version ultérieure (le code fonctionne également sur .NET Framework 4.7+).  
- Package NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`).  
- Un fichier DOCX d’exemple (`input.docx`) qui manque certaines polices ou utilise des polices non installées sur votre machine.  

C’est tout. Si vous êtes déjà à l’aise avec C# et Visual Studio, vous pouvez copier‑coller le code et l’exécuter immédiatement.

---

## Étape 1 : Préparer les options de chargement et un rappel d’avertissement

La première chose qu’Aspose.Words fait lorsque vous appelez `new Document(path, loadOptions)` est d’analyser le fichier. Pendant l’analyse, il peut rencontrer des polices manquantes, des fonctionnalités non prises en charge ou du balisage obsolète. Pour intercepter ces événements, vous avez besoin d’un objet **rappel d’avertissement**.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Step 1: Create a collection that will hold all warnings.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Step 2: Wire the collection into LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    // The library will push every warning into this collection.
    WarningCallback = warningCollector
};
```

**Pourquoi c’est important :** Sans rappel, Aspose.Words consigne silencieusement les avertissements dans la console (ou les ignore), vous laissant dans l’ignorance des substitutions de police qui pourraient affecter la mise en page. En fournissant une `WarningInfoCollection` dédiée, vous obtenez une visibilité totale.

> **Astuce :** Si vous ne vous souciez que des avertissements liés aux polices, vous pouvez filtrer plus tard – mais collecter *tous* les avertissements vous donne une marge de sécurité pour les problèmes futurs.

---

## Étape 2 : Charger le document avec les options configurées

Maintenant que le rappel est prêt, chargez le fichier. Le constructeur `Document` invoquera automatiquement le rappel pour chaque problème détecté.

```csharp
// Step 3: Load the DOCX while capturing warnings.
string filePath = @"YOUR_DIRECTORY/input.docx";
Document doc = new Document(filePath, loadOptions);
```

**Que se passe‑t‑il en coulisses ?** Aspose.Words analyse l’Open XML, résout les styles, et tente d’associer chaque référence de police à une police installée sur le système. Si aucune correspondance n’est trouvée, il crée une entrée `WarningInfo` de type `FontSubstitution`.

---

## Étape 3 : Récupérer et inspecter les avertissements collectés

Une fois le chargement terminé, votre `warningCollector` contient maintenant chaque avertissement survenu. Extrayons‑les et concentrons‑nous sur les messages de substitution de police.

```csharp
// Step 4: Iterate through the collected warnings.
foreach (WarningInfo warning in warningCollector)
{
    // Only interested in font‑substitution warnings?
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {warning.Description}");
    }
}
```

**Exemple de sortie** (votre console peut afficher quelque chose comme :

```
Font substituted: Font "Comic Sans MS" was not found. Substituted with "Arial".
Font substituted: Font "Times New Roman" was not found. Substituted with "Liberation Serif".
```

Si vous voulez *tous* les avertissements, supprimez simplement la condition `if` ou consignez `warning.Type` pour chaque entrée.

---

## Étape 4 : Gérer les polices manquantes – Au‑delà du simple journal

Capturer les avertissements est utile, mais souvent vous devez **gérer les polices manquantes** de façon programmatique. Voici deux stratégies courantes :

### 4.1 Remplacer les polices manquantes par une police de secours spécifique

```csharp
// Define a fallback font that you know is available.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";

// Apply the settings before loading (or after, if you reload).
loadOptions.FontSettings = fontSettings;
```

Désormais, toute police manquante sera remplacée par *Calibri* au lieu de la police de secours par défaut de la bibliothèque.

### 4.2 Intégrer dynamiquement une police de substitution

Si vous disposez d’un fichier de police personnalisé (par ex. `MyFallback.ttf`), vous pouvez l’enregistrer à l’exécution :

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", true); // true = recursive search
loadOptions.FontSettings = fontSettings;
```

Cette approche est pratique lorsque vous distribuez une police d’entreprise spécifique avec votre application.

> **Cas limite :** Les documents qui intègrent déjà la police requise ignoreront les règles de substitution système. Dans ce scénario, la collection d’avertissements sera vide pour cette police, ce qui est exactement ce que vous voulez.

---

## Étape 5 : Exemple complet fonctionnel (prêt à copier‑coller)

Voici un programme autonome qui montre tout, du début à la fin. Remplacez simplement `YOUR_DIRECTORY/input.docx` par le chemin de votre fichier de test.

```csharp
// ------------------------------------------------------------
// Complete example: Capture warnings and handle missing fonts
// ------------------------------------------------------------
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();

        // 2️⃣ Configure LoadOptions with the collector.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = warningCollector
        };

        // OPTIONAL: Set a global fallback font (e.g., Calibri).
        FontSettings fontSettings = new FontSettings();
        fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";
        loadOptions.FontSettings = fontSettings;

        // 3️⃣ Load the document.
        string filePath = @"YOUR_DIRECTORY/input.docx";
        Document doc = new Document(filePath, loadOptions);

        // 4️⃣ Process warnings – focus on font substitution.
        Console.WriteLine("=== Font Substitution Warnings ===");
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine($"⚠️ {warning.Description}");
            }
        }

        // 5️⃣ (Optional) Save the document to verify that the fallback was applied.
        string outPath = @"YOUR_DIRECTORY/output.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**Ce à quoi vous devez vous attendre**

- La console affiche chaque avertissement de substitution de police, préfixé d’un emoji d’avertissement pour plus de visibilité.  
- Le DOCX de sortie (`output.docx`) utilise *Calibri* chaque fois qu’une police manquante a été détectée.  
- Aucun exception non gérée – le système d’avertissement gère gracieusement toute police inconnue.

---

## Questions fréquentes

**Q : Cela fonctionnera‑t‑il avec des PDF générés depuis Word ?**  
R : Oui. Aspose.Words traite les PDF comme un autre format de sortie. La capture des avertissements se produit pendant la phase de *chargement*, donc elle est indépendante de l’export final.

**Q : Et si je dois capturer les avertissements pour **toutes** les opérations sur le document (enregistrement, conversion, etc.) ?**  
R : Vous pouvez réutiliser la même `WarningInfoCollection` en l’affectant à `Document.WarningCallback` après l’instanciation du document. Chaque opération subséquente ajoutera de nouvelles entrées dans la même collection.

**Q : Le rappel d’avertissement impacte‑t‑il les performances ?**  
R : De façon négligeable. La collection se contente de stocker des objets ; à moins de traiter des milliers d’avertissements dans une boucle serrée, vous ne remarquerez aucun ralentissement.

**Q : Comment supprimer les avertissements qui ne m’intéressent pas ?**  
R : Implémentez une classe personnalisée qui hérite de `IWarningCallback` et filtre à l’intérieur de la méthode `Warning`. Le `WarningInfoCollection` intégré ne fait que stocker, il ne filtre pas.

---

## Astuces pro & pièges courants

- **Astuce :** Inspectez toujours `Warning.Description` – il contient le nom exact de la police manquante. Cela peut vous aider à décider si vous devez livrer la police avec votre application.  
- **Attention aux polices intégrées :** Si le DOCX source intègre déjà la police requise, Aspose.Words n’émettra pas d’avertissement de substitution, même si la police n’est pas installée localement.  
- **Sécurité des threads :** `WarningInfoCollection` n’est pas thread‑safe. Si vous chargez plusieurs documents en parallèle, attribuez à chaque thread sa propre collection.  
- **Vérification de version :** L’API d’avertissement est stable depuis Aspose.Words 20.8. Assurez‑vous d’utiliser une version récente pour ne pas manquer les nouveaux types d’avertissements.

---

## Conclusion

Nous avons couvert **comment capturer les avertissements** d’Aspose.Words, démontré comment **obtenir les messages d’avertissement**, et présenté des moyens pratiques de **gérer les polices manquantes** via des polices de secours ou des dossiers de polices personnalisés. L’exemple complet est prêt à être intégré dans n’importe quel projet .NET, et les concepts s’étendent aux pipelines d’automatisation plus importants.

Ensuite, vous pourriez explorer :

- Utiliser `Document.WarningCallback` pour capturer les avertissements lors des opérations de **sauvegarde**.  
- Consigner les avertissements dans un fichier ou un système de télémétrie pour la surveillance en production.  
- Étendre le rappel afin de remplacer automatiquement les polices manquantes par des caractères de marque spécifiques à votre entreprise.

N’hésitez pas à expérimenter : changez la police de secours, ajoutez d’autres documents au lot, ou intégrez le collecteur d’avertissements dans une chaîne CI qui signale les régressions liées aux polices. Bon codage, et que vos documents s’affichent toujours exactement comme vous l’attendez !

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}