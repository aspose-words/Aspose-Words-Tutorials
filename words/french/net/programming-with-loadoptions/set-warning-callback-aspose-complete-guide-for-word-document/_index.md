---
category: general
date: 2026-05-23
description: Définir le rappel d’avertissement Aspose pour capturer les avertissements
  de substitution de police dans Aspose.Words. Découvrez LoadOptions, FontSettings
  et l’implémentation de IWarningCallback.
draft: false
keywords:
- set warning callback aspose
- aspose words loadoptions
- aspose fonts substitution
- iwarningcallback implementation
- aspose document loading
language: fr
og_description: Définissez le rappel d’avertissement Aspose pour surveiller la substitution
  de polices dans Aspose.Words. Ce tutoriel montre LoadOptions, FontSettings et l’implémentation
  du gestionnaire d’avertissements.
og_title: Définir le rappel d’avertissement Aspose – Guide étape par étape
schemas:
- author: Aspose
  dateModified: '2026-05-23'
  description: set warning callback aspose to capture font substitution warnings in
    Aspose.Words. Learn LoadOptions, FontSettings, and IWarningCallback implementation.
  headline: set warning callback aspose – Complete Guide for Word Document Loading
  type: TechArticle
- description: set warning callback aspose to capture font substitution warnings in
    Aspose.Words. Learn LoadOptions, FontSettings, and IWarningCallback implementation.
  name: set warning callback aspose – Complete Guide for Word Document Loading
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code works on .NET Framework 4.5+ as well). -
      A valid Aspose.Words for .NET license or a trial key. - Visual Studio, Rider,
      or any C# editor you prefer. - A sample DOCX (`fontTest.docx`) that references
      a missing font (optional but helpful).'
  - name: Expected console output
    text: 'If `fontTest.docx` references a font that isn’t installed, you’ll see something
      like:'
  - name: When to use a custom LoadOptions
    text: '- **Batch processing** of many files where you want a uniform logging strategy.
      - **Cloud services** that need to report missing fonts back to the caller. -
      **Testing pipelines** that verify documents adhere to a corporate font policy.'
  type: HowTo
tags:
- Aspose.Words
- C#
- FontSettings
title: Définir le rappel d’avertissement Aspose – Guide complet du chargement de documents
  Word
url: /fr/net/programming-with-loadoptions/set-warning-callback-aspose-complete-guide-for-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# définir le rappel d'avertissement aspose – Guide complet pour le chargement de documents Word

Vous vous êtes déjà demandé comment **set warning callback aspose** afin de ne jamais manquer une alerte de substitution de police à nouveau ? Vous n'êtes pas seul. Lorsqu'un DOCX fait référence à une police qui n'est pas installée, Aspose.Words la remplace silencieusement, et sans un rappel approprié vous pourriez ne jamais savoir qu'un changement a eu lieu.

Dans ce tutoriel, nous parcourrons un exemple complet et exécutable qui montre exactement comment capturer ces avertissements. À la fin, vous comprendrez **Aspose.Words LoadOptions**, comment configurer **FontSettings**, et pourquoi implémenter **IWarningCallback** est la façon la plus propre de rester informé. Pas de superflu—juste le code que vous pouvez intégrer dans un projet .NET dès aujourd'hui.

## Ce que vous apprendrez

- Comment **set warning callback aspose** sur une instance `LoadOptions`.  
- Le rôle de **Aspose.Words LoadOptions** lors de l'ouverture d'un document.  
- Configurer la gestion de **Aspose fonts substitution** avec `FontSettings`.  
- Écrire une implémentation personnalisée de **IWarningCallback** pour consigner les problèmes de police.  
- Charger un document en toute sécurité avec les meilleures pratiques de **Aspose document loading**.

### Prérequis

- .NET 6.0 ou ultérieur (le code fonctionne également sur .NET Framework 4.5+).  
- Une licence valide d'Aspose.Words pour .NET ou une clé d'essai.  
- Visual Studio, Rider ou tout éditeur C# de votre choix.  
- Un fichier DOCX d'exemple (`fontTest.docx`) qui fait référence à une police manquante (optionnel mais utile).

> **Astuce :** Si vous n'avez pas de DOCX avec police manquante, renommez simplement une police dans le style du document et observez l'avertissement se déclencher.

---

## Comment définir le rappel d'avertissement aspose pour le chargement de documents

Voici le programme complet et autonome. Enregistrez-le sous `Program.cs`, restaurez les packages NuGet, puis exécutez-le. La console affichera chaque avertissement de substitution de police généré par Aspose.Words lors du chargement du fichier.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// ------------------------------------------------------------
// Step 1: Create a warning handler that implements IWarningCallback
// ------------------------------------------------------------
class FontSubstitutionWarningHandler : IWarningCallback
{
    // This method is called by Aspose.Words for each warning.
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // The Description property tells you which font was substituted.
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

// ------------------------------------------------------------
// Step 2: Prepare FontSettings (default works for most cases)
// ------------------------------------------------------------
FontSettings fontSettings = new FontSettings();
// You could add custom font folders here if you want to avoid substitution:
// fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

// ------------------------------------------------------------
// Step 3: Build LoadOptions and attach our warning callback
// ------------------------------------------------------------
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = new FontSubstitutionWarningHandler()
};

// ------------------------------------------------------------
// Step 4: Load the document using the configured LoadOptions
// ------------------------------------------------------------
try
{
    // Replace the path with the location of your test document.
    Document doc = new Document("YOUR_DIRECTORY/fontTest.docx", loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

### Sortie console attendue

Si `fontTest.docx` fait référence à une police qui n'est pas installée, vous verrez quelque chose comme :

```
Font substitution: Font 'Comic Sans MS' was substituted with 'Arial'.
Document loaded successfully.
```

Si toutes les polices sont présentes, la seule ligne affichée sera *Document loaded successfully*—aucun avertissement, aucun bruit.

![set warning callback aspose example](image.png "set warning callback aspose example")

---

## Comprendre LoadOptions dans Aspose.Words

`LoadOptions` est la porte d'entrée de chaque réglage que vous pouvez apporter à **aspose document loading**. Il vous permet de :

1. **Spécifier un `FontSettings` personnalisé** – utile lorsque votre application fournit ses propres polices.  
2. **Attacher un rappel d'avertissement** – exactement ce que nous avons fait pour intercepter les substitutions de police.  
3. Contrôler la détection du format du document, la gestion des mots de passe, et plus encore.

Comme `LoadOptions` est passé au constructeur `Document`, les paramètres sont appliqués **une seule fois**, dès le moment où le fichier est analysé. C’est pourquoi nous pouvons garantir que notre gestionnaire d’avertissement verra chaque substitution avant que le document ne soit même construit en mémoire.

### Quand utiliser un LoadOptions personnalisé

- **Traitement par lots** de nombreux fichiers où vous souhaitez une stratégie de journalisation uniforme.  
- **Services cloud** qui doivent signaler les polices manquantes à l'appelant.  
- **Pipelines de test** qui vérifient que les documents respectent une politique de police d'entreprise.

## Configurer FontSettings pour la substitution de polices Aspose

L'objet `FontSettings` contrôle la façon dont Aspose.Words résout les polices. Par défaut, il recherche dans les dossiers de polices du système, puis utilise les substituts intégrés. Vous pouvez affiner ce comportement :

```csharp
FontSettings fontSettings = new FontSettings();

// Add a folder that contains your corporate fonts.
fontSettings.SetFontsFolder(@"C:\Corporate\Fonts", recursive: true);

// Optionally, map a missing font to a specific substitute.
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
    "MissingFont", new[] { "Arial", "Times New Roman" });
```

Ces lignes sont optionnelles pour le scénario de base « set warning callback aspose », mais elles illustrent comment vous pouvez **réduire** le nombre d’avertissements de substitution en fournissant les bonnes polices à l'avance.

## Implémenter IWarningCallback pour les avertissements de substitution de police

L'interface `IWarningCallback` est minuscule—un seul méthode `Warning`. Pourtant, elle vous donne **un contrôle total** sur la façon dont les avertissements sont gérés :

- **Consigner dans un fichier** au lieu de la console.  
- **Collecter les avertissements** dans une liste pour une analyse ultérieure.  
- **Lancer des exceptions** pour les avertissements critiques (par ex., lorsqu'une police requise est manquante).

Voici un exemple rapide qui stocke les avertissements dans une `List<string>` :

```csharp
class CollectingWarningHandler : IWarningCallback
{
    public List<string> Messages { get; } = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Messages.Add(info.Description);
    }
}
```

Vous pourriez ensuite inspecter `handler.Messages` après le chargement du document pour décider d'abandonner le traitement.

## Charger un document avec une gestion personnalisée des avertissements (flux complet)

En combinant le tout, le modèle final que vous réutiliserez probablement ressemble à ceci :

```csharp
// 1️⃣ Create the warning handler.
CollectingWarningHandler handler = new CollectingWarningHandler();

// 2️⃣ Set up FontSettings (add custom fonts if needed).
FontSettings fs = new FontSettings();
fs.SetFontsFolder(@"C:\MyApp\Fonts", true);

// 3️⃣ Build LoadOptions with both FontSettings and the handler.
LoadOptions opts = new LoadOptions
{
    FontSettings = fs,
    WarningCallback = handler
};

// 4️⃣ Load the document.
Document doc = new Document("input.docx", opts);

// 5️⃣ React to any font‑substitution warnings.
if (handler.Messages.Any())
{
    Console.WriteLine("The following fonts were substituted:");
    foreach (var msg in handler.Messages)
        Console.WriteLine("- " + msg);
}
else
{
    Console.WriteLine("No font issues detected.");
}
```

Cet extrait démontre le flux **aspose document loading** que vous utiliserez en production : configurer, charger, puis réagir. Le modèle s'adapte bien que vous traitiez un seul fichier ou que vous parcouriez des milliers.

## Questions fréquentes & cas limites

**Que faire si le document est protégé par mot de passe ?**  
Ajoutez `Password = "secret"` à l'initialiseur `LoadOptions`. Le rappel d'avertissement fonctionne toujours une fois le fichier déchiffré.

**Le rappel se déclenchera-t-il pour d'autres types d'avertissements ?**  
Oui—`WarningInfo.Type` peut être `DocumentStructure`, `UnsupportedFileFormat`, etc. Dans notre exemple nous filtrons sur `FontSubstitution`, mais vous pouvez tout consigner en supprimant la condition `if`.

**Cela affecte-t-il les performances ?**  
Négligeablement. Le rappel n'est invoqué que lorsqu'un avertissement se produit, ce qui est bien moins fréquent que les étapes normales d'analyse.

**Puis-je désactiver complètement la substitution de police ?**  
Vous pouvez définir `fontSettings.SubstitutionSettings.DefaultFontSubstitution = false;` mais alors Aspose.Words lèvera une exception pour les polices manquantes au lieu de les remplacer.

## Conclusion

Vous savez maintenant exactement comment **set warning callback aspose** pour surveiller les événements de substitution de police pendant le traitement des **Aspose.Words LoadOptions**. En configurant `FontSettings`, en implémentant un `IWarningCallback` léger, et en chargeant le document avec ces options, vous obtenez une visibilité complète sur toutes les modifications de police qu'Aspose effectue en coulisses.

À partir d'ici, vous pourriez :

- Étendre le gestionnaire d'avertissement pour écrire dans un service de journalisation central.  
- Combiner le rappel avec une stratégie de secours de police personnalisée.  
- Utiliser le modèle lors de la création d'une API cloud qui valide les documents téléchargés par les clients.

Essayez-le avec vos propres fichiers DOCX, ajustez les `FontSettings`, et observez la console vous indiquer exactement quelles polices ont été remplacées. Bon codage, et que vos documents s'affichent toujours comme prévu !

## Tutoriels associés

- [Capturer les avertissements de substitution de police en Java avec Aspose.Words – Guide complet](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Activer les avertissements de substitution de police dans Aspose.Words – Guide complet](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Comment définir LoadOptions dans Aspose.Words pour Java](/words/english/java/document-loading-and-saving/using-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}