---
category: general
date: 2026-06-17
description: Gérez la substitution de polices dans Aspose.Words et détectez rapidement
  les polices manquantes grâce à ce tutoriel étape par étape destiné aux développeurs
  .NET.
draft: false
keywords:
- handle font substitution
- detect missing fonts
- how to detect missing fonts
language: fr
og_description: Gérez la substitution de polices dans Aspose.Words et apprenez à détecter
  les polices manquantes dans vos documents avec des exemples de code clairs.
og_title: Gérer la substitution de polices dans Aspose.Words – Guide complet
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Handle font substitution in Aspose.Words and detect missing fonts quickly
    with this step‑by‑step tutorial for .NET developers.
  headline: Handle Font Substitution in Aspose.Words – Complete Programming Guide
  type: TechArticle
- description: Handle font substitution in Aspose.Words and detect missing fonts quickly
    with this step‑by‑step tutorial for .NET developers.
  name: Handle Font Substitution in Aspose.Words – Complete Programming Guide
  steps:
  - name: '**Create a test DOCX** that references a font you know isn’t on the machine
      (e.g., “Comic Sans MS” on a minimal Docker image).'
    text: '**Create a test DOCX** that references a font you know isn’t on the machine
      (e.g., “Comic Sans MS” on a minimal Docker image).'
  - name: Run the console app or API endpoint.
    text: Run the console app or API endpoint.
  - name: Verify that the console (or HTTP response) lists the substitution warning.
    text: Verify that the console (or HTTP response) lists the substitution warning.
  - name: Optionally, open the resulting PDF and check the font properties—Aspose.Words
      should show the fallback font you configured.
    text: Optionally, open the resulting PDF and check the font properties—Aspose.Words
      should show the fallback font you configured.
  type: HowTo
tags:
- Aspose.Words
- .NET
- Font Management
title: Gérer la substitution de polices dans Aspose.Words – Guide complet de programmation
url: /fr/net/working-with-fonts/handle-font-substitution-in-aspose-words-complete-programmin/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Gérer la substitution de polices dans Aspose.Words – Guide complet de programmation

Vous êtes‑vous déjà demandé comment **gérer la substitution de polices** lorsqu’un document Word fait référence à une police qui n’est pas installée sur le serveur ? Vous n’êtes pas seul. Dans de nombreuses applications réelles—pensez aux générateurs de factures ou aux services de rapports automatisés—les polices manquantes entraînent des substitutions silencieuses qui ruinent la mise en page.  

La bonne nouvelle, c’est qu’Aspose.Words vous propose un système d’avertissement intégré qui vous permet de **détecter les polices manquantes** et de réagir comme vous le souhaitez. Dans ce tutoriel, nous allons parcourir l’enregistrement d’un gestionnaire d’avertissement, le chargement d’un document, et l’extraction des événements de substitution de police dont vous avez besoin. À la fin, vous verrez également comment répondre à la question classique « **comment détecter les polices manquantes** ? » avec du code propre, prêt pour la production.

## Ce que couvre ce tutoriel

* Configurer Aspose.Words pour émettre des avertissements à chaque substitution de police.  
* Capturer ces avertissements dans un gestionnaire personnalisé afin de les journaliser, les remplacer ou les interrompre.  
* Utiliser les données capturées pour **détecter les polices manquantes** avant que le document ne soit enregistré ou rendu.  
* Astuces pour dépanner les cas limites—par exemple lorsqu’une police de secours est choisie silencieusement.  
* Un exemple complet et exécutable que vous pouvez intégrer dans n’importe quelle application console .NET.

> **Prérequis** – Vous aurez besoin d’un SDK .NET récent (6.0+ fonctionne très bien), d’une licence valide Aspose.Words for .NET (ou d’une clé d’évaluation temporaire), et d’un fichier DOCX d’exemple qui référence intentionnellement une police que vous n’avez pas installée. Aucune autre bibliothèque tierce n’est requise.

---

## ## Gérer la substitution de polices avec un gestionnaire d’avertissement personnalisé

Aspose.Words génère un objet `WarningInfo` chaque fois qu’il ne trouve pas la police demandée. Par défaut, ces avertissements sont ignorés, ce qui explique pourquoi vous ne remarquez souvent jamais une substitution. Pour **gérer la substitution de polices**, vous remplacez le gestionnaire d’avertissement par défaut par un gestionnaire qui fait réellement quelque chose.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // Register a custom warning handler that prints font‑substitution events.
        FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
            (sender, args) =>
            {
                // We're only interested in font‑substitution warnings.
                if (args.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ Font substituted: {args.Description}");
                }
            });

        // Load a document that deliberately references an unavailable font.
        Document doc = new Document("Samples/MissingFont.docx");

        // Force a save to trigger any pending warnings (e.g., PDF conversion).
        doc.Save("Output/Result.pdf");
    }
}
```

### Pourquoi cela fonctionne

* `FontSettings.DefaultWarningHandler` est une propriété statique globale — une fois définie, **toutes** les opérations Aspose.Words dans le domaine d’application actuel utilisent votre délégué.  
* Le `WarningInfoCollectionHandler` reçoit un objet `WarningInfo` contenant `WarningType` et une `Description` lisible par l’homme. Filtrer sur `WarningType.FontSubstitution` garantit que vous ne voyez que les événements qui vous intéressent.  
* L’appel à `doc.Save` force la bibliothèque à résoudre toutes les polices, moment où les avertissements sont déclenchés. Si vous avez seulement besoin d’inspecter le document sans l’enregistrer, vous pouvez appeler `doc.UpdatePageLayout()` à la place.

**Sortie console attendue** (en supposant que la police manquante soit « Papyrus ») :

```
⚠️ Font substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
```

Cette ligne est la preuve que la bibliothèque **a détecté les polices manquantes** et a choisi une police de secours.

---

## ## Détecter les polices manquantes avant le rendu

Parfois, vous voulez arrêter le processus entièrement si une police requise est manquante—peut‑être parce que les directives de marque exigent une typographie exacte. Le gestionnaire d’avertissement peut être étendu pour collecter tous les messages de police manquante dans une liste, puis vous pouvez prendre une décision.

```csharp
using System.Collections.Generic;

// ...

static List<string> missingFonts = new List<string>();

static void Main()
{
    FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
        (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
            {
                // Store the description for later analysis.
                missingFonts.Add(args.Description);
                Console.WriteLine($"⚠️ Font substituted: {args.Description}");
            }
        });

    Document doc = new Document("Samples/MissingFont.docx");
    doc.UpdatePageLayout();   // Triggers warnings without saving.

    if (missingFonts.Count > 0)
    {
        Console.WriteLine("\n❗ Detected missing fonts:");
        foreach (var msg in missingFonts)
            Console.WriteLine($" - {msg}");

        // Optionally abort the operation.
        // throw new InvalidOperationException("Missing required fonts.");
    }
    else
    {
        Console.WriteLine("\n✅ No font substitution detected.");
    }

    // Continue with saving or further processing if you wish.
    doc.Save("Output/Result.pdf");
}
```

### Comment cela répond à « comment détecter les polices manquantes »

* La liste `missingFonts` agit comme un registre de chaque événement de substitution.  
* Après `UpdatePageLayout`, vous pouvez inspecter la liste et décider de continuer, de journaliser ou de lever une exception.  
* Ce modèle fonctionne pour n’importe quel format de sortie (PDF, HTML, images) car le système d’avertissement est indépendant du format.

---

## ## Astuce avancée : remplacer les polices manquantes par un substitut spécifique

Si vous disposez d’une police d’entreprise qui doit être utilisée, vous pouvez indiquer à Aspose.Words de remplacer automatiquement toute police manquante par votre police de secours. Cela est pratique lorsque vous voulez que le document *reste* présentable sans post‑traitement manuel.

```csharp
// Configure a fallback font collection.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
    "AnyMissingFont", new string[] { "Calibri", "Arial" });

FontSettings.DefaultFontSettings = fontSettings;
```

Placez le fragment ci‑dessus **avant** le chargement du document. Désormais, toute police manquante—quel que soit son nom d’origine—sera remplacée par « Calibri » (ou « Arial » si Calibri n’est pas présent). Vous recevrez toujours l’avertissement, mais le document sera rendu avec la police que vous contrôlez.

---

## ## Pièges courants et comment les éviter

| Piège | Pourquoi cela se produit | Solution |
|---------|----------------|-----|
| **Les avertissements disparaissent après le premier appel** | La propriété statique `DefaultWarningHandler` est écrasée plus tard dans l’application. | Définissez le gestionnaire **une seule fois** au démarrage de l’application, ou conservez une référence et ré‑attribuez‑le si vous devez le changer. |
| **Seule la première police manquante est signalée** | Certaines API regroupent les avertissements ; vous devez appeler `UpdatePageLayout` ou `Save` pour vider la file. | Forcez une mise à jour de la mise en page ou enregistrez dans le format que vous avez l’intention de générer. |
| **La substitution se produit toujours même après l’abandon** | Le gestionnaire d’avertissement s’exécute *après* que la substitution a déjà eu lieu. | Utilisez le gestionnaire pour **journaliser** puis lever une exception afin d’arrêter le traitement ultérieur. |
| **Polices manquantes dans les conteneurs Linux** | Linux ne possède souvent pas le catalogue de polices Windows, entraînant de nombreuses substitutions. | Montez les polices requises dans le conteneur ou utilisez `FontSettings.SetFontsFolder` pour pointer vers un répertoire de polices personnalisé. |

---

## ## Détecter la substitution de polices dans un scénario Web API

Si vous servez des documents via ASP.NET Core, vous ne voulez probablement pas écrire dans la console. À la place, collectez les avertissements et renvoyez‑les dans la réponse HTTP.

```csharp
[ApiController]
[Route("api/[controller]")]
public class DocumentController : ControllerBase
{
    [HttpPost("convert")]
    public IActionResult Convert(IFormFile file)
    {
        var missingFonts = new List<string>();

        FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
            (s, e) =>
            {
                if (e.WarningType == WarningType.FontSubstitution)
                    missingFonts.Add(e.Description);
            });

        using var stream = file.OpenReadStream();
        var doc = new Document(stream);
        doc.UpdatePageLayout();

        if (missingFonts.Any())
        {
            return BadRequest(new { message = "Missing fonts detected", details = missingFonts });
        }

        // Convert to PDF and stream back.
        var pdfStream = new MemoryStream();
        doc.Save(pdfStream, SaveFormat.Pdf);
        pdfStream.Position = 0;
        return File(pdfStream, "application/pdf", "result.pdf");
    }
}
```

L’API **détecte maintenant les polices manquantes** et renvoie une charge JSON claire avant que tout PDF ne soit généré. C’est une illustration pratique de « comment détecter les polices manquantes » dans un service de niveau production.

---

## ## Tester votre implémentation

1. **Créer un DOCX de test** qui référence une police que vous savez absente de la machine (par ex., « Comic Sans MS » sur une image Docker minimale).  
2. Exécutez l’application console ou le point de terminaison API.  
3. Vérifiez que la console (ou la réponse HTTP) répertorie l’avertissement de substitution.  
4. Optionnellement, ouvrez le PDF résultant et contrôlez les propriétés de police — Aspose.Words devrait afficher la police de secours que vous avez configurée.

Si vous voyez l’avertissement mais que le PDF utilise encore une police inattendue, revérifiez l’ordre des `SubstitutionSettings` ; la première correspondance l’emporte.

---

## ## Conclusion

Nous avons couvert tout ce dont vous avez besoin pour **gérer la substitution de polices** dans Aspose.Words, depuis l’enregistrement d’un gestionnaire d’avertissement jusqu’à la détection programmatique des **polices manquantes** et même leur remplacement par une police d’entreprise. En exploitant le système d’avertissement intégré, vous obtenez une visibilité complète sur chaque événement « police non trouvée », ce qui répond directement à la question « **comment détecter les polices manquantes** ? » que chaque développeur se pose lorsqu’il automatise la génération de documents.

Et après ? Essayez de combiner cette logique avec le **chargement dynamique de polices** (`FontSettings.SetFontsFolder`) pour prendre en charge les polices téléchargées par les utilisateurs à la volée, ou étendez le gestionnaire d’avertissement pour écrire les entrées dans un service de journalisation central comme Serilog. Plus vous instrumentez la gestion des polices, plus votre pipeline de documents devient fiable.

Vous avez un scénario de substitution de polices difficile ? Laissez un commentaire ci‑dessous, et résolvons‑le ensemble. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets et fonctionnels avec des explications pas à pas pour vous aider à maîtriser des fonctionnalités supplémentaires de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Comment détecter les polices dans Aspose.Words – Gérer les avertissements & les paramètres](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Activer les avertissements de substitution de polices dans Aspose.Words – Guide complet](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Comment charger un DOCX et détecter les polices manquantes – Guide complet C#](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}