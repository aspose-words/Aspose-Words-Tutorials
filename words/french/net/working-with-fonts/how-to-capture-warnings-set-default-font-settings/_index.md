---
category: general
date: 2026-03-19
description: Apprenez à capturer les avertissements dans Aspose.Words, à définir les
  paramètres de police par défaut et à détecter les polices manquantes lors du chargement
  d’un document Word.
draft: false
keywords:
- how to capture warnings
- set default font settings
- load word document
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
language: fr
og_description: Comment capturer les avertissements dans Aspose.Words, définir les
  paramètres de police par défaut et détecter les polices manquantes lors du chargement
  d’un document Word.
og_title: Comment capturer les avertissements – Définir les paramètres de police par
  défaut
tags:
- Aspose.Words
- C#
- Document Processing
title: Comment capturer les avertissements – Définir les paramètres de police par
  défaut
url: /fr/net/working-with-fonts/how-to-capture-warnings-set-default-font-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment capturer les avertissements – Définir les paramètres de police par défaut

**Comment capturer les avertissements** est un besoin courant lorsque vous travaillez avec Aspose.Words, surtout si vos documents dépendent de polices spécifiques qui pourraient ne pas être présentes sur la machine cible. Vous êtes déjà ouvert un DOCX et vous vous êtes demandé pourquoi la mise en page était décalée ? La réponse se cache souvent dans un avertissement concernant une police manquante.  

Dans ce guide, nous allons parcourir **comment capturer les avertissements** pendant que vous **chargez le document Word**, configurez **définissez les paramètres de police par défaut**, et enfin **détectez les polices manquantes** afin de pouvoir réagir de manière programmatique. Pas de fioritures—juste un exemple complet et exécutable ainsi que le raisonnement derrière chaque ligne.

> *Astuce :* Capturer les avertissements tôt vous évite de déboguer des problèmes de mise en page mystérieux plus tard.

---

## Ce dont vous aurez besoin

- **Aspose.Words for .NET** (dernière version à partir de 2026).  
- Un environnement de développement .NET (Visual Studio, Rider ou VS Code).  
- Un fichier DOCX d'exemple qui référence une police que vous *n’avez pas* installée (par ex., *Comic Sans MS* sur une machine Linux).  

C’est tout. Aucun paquet NuGet supplémentaire n’est requis au-delà d’Aspose.Words.

---

## Étape 1 – Comprendre pourquoi vous devez capturer les avertissements

Lorsque Aspose.Words analyse un document, il peut rencontrer des polices qui ne sont pas disponibles sur l’hôte. Par défaut, la bibliothèque substitue silencieusement une police de secours, ce qui peut modifier les sauts de ligne, l’espacement et même faire disparaître du texte.  

Utiliser le **WarningCallback** avec un objet **FontSettings** vous offre deux avantages :

1. **Visibilité** – vous obtenez une entrée `WarningInfo` pour chaque substitution.  
2. **Contrôle** – vous pouvez pré‑configurer une police par défaut pour minimiser les surprises visuelles.

Pensez-y comme à l’installation d’un « chien de garde » qui crie chaque fois que le moteur échange une pièce sous le capot.

---

## Étape 2 – Définir les paramètres de police par défaut

Le premier mot‑clé secondaire, **set default font settings**, apparaît ici même. Vous créez une instance `FontSettings` et, éventuellement, la pointez vers un dossier contenant vos polices de secours.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

// Create a FontSettings object and point it to a folder with fallback fonts (optional)
var fontSettings = new FontSettings();
// Example: fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);
```

**Pourquoi ?**  
Si vous ne spécifiez pas de police de secours, Aspose.Words choisit la première police système correspondant au style, ce qui peut être très différent. En définissant une police par défaut connue, vous garantissez un rendu cohérent sur toutes les machines.

---

## Étape 3 – Préparer un rappel d’avertissement pour capturer les avertissements

Nous allons maintenant **comment capturer les avertissements** en attachant un `WarningInfoCollection` aux options de chargement. Cette collection stockera chaque avertissement émis pendant le processus de chargement.

```csharp
// Step 3: Prepare a list that will collect warning information
var warningInfos = new List<WarningInfo>();

// Create a WarningInfoCollection that forwards warnings to our list
var warningCallback = new WarningInfoCollection(warningInfos);
```

Le `WarningInfoCollection` implémente `IWarningCallback`, ainsi Aspose.Words pousse automatiquement chaque avertissement dans `warningInfos`. Aucun sondage n’est nécessaire.

---

## Étape 4 – Charger le document Word avec les options configurées

C’est ici que le deuxième mot‑clé secondaire, **load word document**, brille. Nous transmettons à la fois le `FontSettings` et le `WarningCallback` via une instance `LoadOptions`.

```csharp
// Step 4: Build LoadOptions with our font settings and warning callback
var loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = warningCallback
};

// Load the DOCX – this is the moment we actually **load word document**
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

Si le document référence une police qui n’est pas installée, le rappel d’avertissement capturera une entrée `WarningType.FontSubstitution`.

---

## Étape 5 – Détecter les polices manquantes à partir des avertissements collectés

Enfin, nous répondons au troisième mot‑clé secondaire, **detect missing fonts**, en parcourant les avertissements collectés.

```csharp
// Step 5: Examine the collected warnings for any font substitution events
foreach (var warning in warningInfos)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substitution detected: {warning.Description}");
    }
}
```

Un exemple de sortie ressemble à :

```
⚠️ Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Cette ligne indique exactement quelle police est manquante et quelle police de secours a été utilisée — des informations que vous pouvez consigner, afficher à l’utilisateur, ou même déclencher une routine d’installation de police personnalisée.

---

## Exemple complet exécutable

Ci-dessous le programme complet que vous pouvez copier‑coller dans une application console. Il démontre **comment capturer les avertissements**, **définir les paramètres de police par défaut**, **charger le document Word**, et **détecter les polices manquantes** en un seul flux.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace CaptureWarningsDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Prepare a list to collect warning information during loading
            var warningInfos = new List<WarningInfo>();

            // 2️⃣ Configure load options – this is where we **set default font settings**
            var fontSettings = new FontSettings();
            // Uncomment and adjust the line below if you have a fallback folder:
            // fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);

            var loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new WarningInfoCollection(warningInfos)
            };

            // 3️⃣ **Load word document** with the configured options
            string docPath = @"YOUR_DIRECTORY/MissingFont.docx";
            Document document = new Document(docPath, loadOptions);

            // 4️⃣ **Detect missing fonts** by scanning the collected warnings
            Console.WriteLine("Scanning for font substitution warnings...");
            foreach (var warning in warningInfos)
            {
                if (warning.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Description}");
                }
            }

            // Optional: keep console window open
            Console.WriteLine("Done. Press any key to exit.");
            Console.ReadKey();
        }
    }
}
```

**Résultat attendu :** Lorsque le DOCX spécifié référence une police qui n’est pas installée, la console affiche un avertissement pour chaque substitution. Si toutes les polices sont présentes, la boucle ne produit aucune sortie.

---

## Pièges courants et cas limites

| Situation | Pourquoi cela se produit | Comment le gérer |
|-----------|--------------------------|------------------|
| **Aucun avertissement n’apparaît** même si la mise en page semble incorrecte | Le document peut utiliser des polices *intégrées*, que Aspose.Words rend sans substitution. | Vérifiez `Document.HasEmbeddedFonts` et envisagez d’extraire les polices intégrées si vous en avez besoin sur une autre machine. |
| **Multiple avertissements pour le |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}