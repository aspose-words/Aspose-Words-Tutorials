---
category: general
date: 2026-06-24
description: Comment utiliser IWarningCallback pour détecter les polices manquantes
  dans les documents Aspose.Words. Découvrez un exemple complet, exécutable et les
  meilleures pratiques.
draft: false
keywords:
- how to use iwarningcallback
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
- missing font detection in .docx
language: fr
og_description: Comment utiliser IWarningCallback pour détecter les polices manquantes
  dans Aspose.Words. Suivez le guide étape par étape pour une solution complète, prête
  pour la production.
og_title: Comment utiliser IWarningCallback – détecter les polices manquantes
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: How to use IWarningCallback to detect missing fonts in Aspose.Words
    documents. Learn a full, runnable example and best practices.
  headline: How to Use IWarningCallback – Detect Missing Fonts with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document Processing
title: Comment utiliser IWarningCallback – Détecter les polices manquantes avec Aspose.Words
url: /fr/net/working-with-fonts/how-to-use-iwarningcallback-detect-missing-fonts-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment utiliser IWarningCallback – Détecter les polices manquantes avec Aspose.Words

Utiliser **IWarningCallback** est essentiel lorsque vous travaillez avec Aspose.Words et devez **détecter les polices manquantes** dans un fichier DOCX. Dans ce guide, nous parcourrons un exemple complet, copiable‑collable, qui vous montre exactement comment utiliser IWarningCallback pour intercepter les avertissements de substitution de police, pourquoi c’est important, et quoi faire une fois que vous les avez capturés.

Si vous avez déjà ouvert un document et vu du texte illisible parce qu’une police personnalisée n’était pas installée, vous connaissez la frustration. À la fin de ce tutoriel, vous disposerez d’une méthode fiable pour exposer ces problèmes de façon programmatique, les consigner, ou même appliquer automatiquement une police de secours.

## Ce que vous apprendrez

- Le but de **IWarningCallback** et quand l’utiliser.  
- Comment implémenter un collecteur d’avertissements personnalisé qui isole les événements de **détection de polices manquantes**.  
- Brancher le collecteur dans **LoadOptions** afin que chaque chargement de document soit surveillé.  
- Vérifier la sortie et gérer les cas limites (plusieurs polices manquantes, avertissements silencieux, etc.).  

### Prérequis

- .NET 6.0 ou supérieur (le code fonctionne également sur .NET Framework 4.6+).  
- Aspose.Words pour .NET installé via NuGet (`Install-Package Aspose.Words`).  
- Un fichier DOCX qui référence une police absente sur la machine (par ex., `DocumentWithMissingFont.docx`).  

Aucune bibliothèque supplémentaire n’est requise — tout réside dans Aspose.Words.

---

## Comment utiliser IWarningCallback pour détecter les polices manquantes dans Aspose.Words

Voici le **programme complet et exécutable**. Copiez‑le dans un nouveau projet console, ajustez le chemin du fichier, puis exécutez‑le. Vous verrez la sortie console pour chaque avertissement de police manquante.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 1: Create a warning collector that implements IWarningCallback.
    // This collector will be invoked each time Aspose.Words raises a warning.
    class FontWarningCollector : IWarningCallback
    {
        // The Warning method receives a WarningInfo object.
        // We filter for FontSubstitution warnings because those indicate missing fonts.
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                // Print the warning to the console – you could also log to a file or database.
                Console.WriteLine($"[Missing Font] {info.Description}");
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2: Configure LoadOptions to use our custom collector.
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // Step 3: Load the document with the specified options.
            // Any font that cannot be resolved triggers the warning collector above.
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFont.docx";

            try
            {
                Document doc = new Document(docPath, loadOptions);
                Console.WriteLine("Document loaded successfully.");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Error loading document: {ex.Message}");
            }

            // Keep the console window open when debugging.
            Console.WriteLine("Press any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### Résultat attendu

Si `DocumentWithMissingFont.docx` référence une police appelée *« MyFancyFont »* qui n’est pas installée, vous verrez quelque chose comme :

```
[Missing Font] Font substitution: The font 'MyFancyFont' was not found. Substituted with 'Arial'.
Document loaded successfully.
Press any key to exit...
```

Chaque ligne préfixée par **[Missing Font]** est générée par notre implémentation de **IWarningCallback**, prouvant que nous avons bien **détecté les polices manquantes**.

---

## Étape 1 : Implémenter l’interface IWarningCallback

Pourquoi avons‑nous besoin d’une classe personnalisée ? Aspose.Words génère des **avertissements** pour diverses raisons — problèmes de format de fichier, fonctionnalités obsolètes, et, surtout pour nous, la substitution de police. En implémentant `IWarningCallback`, nous obtenons un point d’ancrage qui reçoit chaque avertissement au moment où il se produit. Filtrer sur `WarningType.FontSubstitution` isole le scénario spécifique où une police est absente.

**Astuce :** Si vous devez capturer *tous* les avertissements à des fins de diagnostic, supprimez simplement la condition `if` et consignez chaque `info.Type`.

## Étape 2 : Brancher le rappel dans LoadOptions

`LoadOptions` est la porte d’entrée qui indique à Aspose.Words comment traiter le document entrant. Définir `WarningCallback` sur une instance de notre collecteur garantit que le rappel est actif pendant toute l’opération de chargement. Vous pouvez réutiliser le même objet `LoadOptions` pour plusieurs documents, ce qui est pratique dans les pipelines de traitement par lots.

**Question fréquente :** *Que se passe‑t‑il si je charge un document sans spécifier LoadOptions ?*  
Réponse : Aspose.Words générera toujours des avertissements en interne, mais sans rappel ils sont simplement ignorés, et vous perdez la possibilité de **détecter les polices manquantes**.

## Étape 3 : Charger un document et capturer les avertissements de police manquante

Le constructeur `Document` qui accepte un chemin de fichier et des `LoadOptions` effectue le travail lourd. Au fur et à mesure que le fichier est analysé, toute police manquante déclenche notre méthode `FontWarningCollector.Warning`. La sortie console prouve que le mécanisme fonctionne.

**Cas limite :** Un seul document peut référencer plusieurs polices absentes. Le rappel se déclenche une fois par police manquante, vous verrez donc plusieurs lignes — idéal pour créer un rapport complet.

## Pourquoi utiliser IWarningCallback plutôt que des vérifications manuelles de polices ?

Vous pourriez parcourir manuellement les propriétés `Run.Font` du document après le chargement, mais cela nécessiterait que le document se charge correctement d’abord — ce qui échoue si la police est totalement indisponible. Le système d’avertissement fonctionne **avant** toute substitution, vous donnant une image précise de ce qui manque.

De plus, le rappel s’exécute **dans le cadre du pipeline de chargement**, ce qui vous permet d’interrompre le processus tôt, de remplacer les polices à la volée, ou de consigner des diagnostics détaillés sans passages supplémentaires sur l’arbre du document.

## Gérer plusieurs polices manquantes de façon élégante

Si vous prévoyez de nombreuses polices manquantes, envisagez de les agréger dans une collection :

```csharp
class AggregatingFontCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}
```

Après le chargement, vous pouvez parcourir `MissingFonts` et, par exemple, les écrire dans un fichier CSV pour l’équipe de conception.

## Bonus : Consigner les avertissements dans un fichier

La sortie console convient aux démonstrations, mais le code de production consigne généralement dans un stockage persistant. Remplacez l’appel `Console.WriteLine` par quelque chose comme :

```csharp
File.AppendAllText("font-warnings.log", $"{DateTime.Now}: {info.Description}{Environment.NewLine}");
```

Vous disposez ainsi d’une trace d’audit qui pourra être consultée ultérieurement, répondant aux exigences de conformité.

## Conclusion

Nous avons couvert **comment utiliser IWarningCallback** pour **détecter les polices manquantes** dans Aspose.Words, depuis l’implémentation du rappel jusqu’à son branchement dans `LoadOptions` et la gestion des avertissements résultants. Cette approche vous donne une visibilité en temps réel sur les problèmes liés aux polices, vous permettant de consigner, remplacer ou alerter les utilisateurs avant que le document ne soit rendu.

Prochaines étapes que vous pourriez explorer :

- **Polices de secours :** attribuer programmatique une police par défaut lorsqu’une substitution se produit.  
- **Traitement par lots :** parcourir un dossier de documents en réutilisant le même `AggregatingFontCollector`.  
- **Retour utilisateur :** afficher les avertissements de police manquante dans une interface plutôt que dans la console.

Essayez-le dans votre propre projet — plus de texte illisible mystérieux, seulement des diagnostics clairs et exploitables. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Comment charger un DOCX et détecter les polices manquantes – Guide complet C#](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)
- [Comment détecter les polices dans Aspose.Words – Gérer les avertissements et les paramètres](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Comment utiliser LoadOptions dans Aspose.Words – Guide complet](/words/english/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}