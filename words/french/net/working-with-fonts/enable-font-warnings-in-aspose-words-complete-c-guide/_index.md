---
category: general
date: 2026-04-01
description: Activez les avertissements de police lors du chargement de documents
  Word avec Aspose.Words. Apprenez à intercepter les événements de substitution de
  police à l’aide de LoadOptions et des paramètres de police en C#.
draft: false
keywords:
- enable font warnings
- font substitution
- Aspose.Words
- LoadOptions
- C# document processing
- font settings
language: fr
og_description: Activez les avertissements de police lors du chargement de documents
  Word avec Aspose.Words. Ce tutoriel vous montre comment capturer les événements
  de substitution de police en C#.
og_title: Activer les avertissements de polices dans Aspose.Words – Guide complet
  C#
tags:
- Aspose.Words
- C#
- Font Management
title: Activer les avertissements de polices dans Aspose.Words – Guide complet C#
url: /fr/net/working-with-fonts/enable-font-warnings-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Activer les avertissements de police dans Aspose.Words – Guide complet C# 

Vous vous êtes déjà demandé pourquoi un document Word apparaît soudainement différent après l'avoir chargé de façon programmatique ? **Activer les avertissements de police** et vous saurez immédiatement quand Aspose.Words remplace une police manquante par une police de secours. Dans ce tutoriel, nous parcourrons un exemple pratique qui non seulement capture ces substitutions mais explique également *pourquoi* elles se produisent.

Nous couvrirons tout ce dont vous avez besoin pour démarrer : le package NuGet requis, la configuration exacte de `LoadOptions`, et une sortie console claire indiquant quelles polices ont été remplacées. À la fin, vous disposerez d'un modèle solide et réutilisable pour le **traitement de documents C#** qui fonctionne avec n'importe quelle version d'Aspose.Words.

## Ce que vous apprendrez

- Comment créer une instance de `LoadOptions` qui suit les changements de police.  
- Le but de l'événement `SubstitutionWarning` et comment l'abonner.  
- Un exemple complet et exécutable qui affiche des avertissements clairs dans la console.  
- Conseils pour gérer les cas limites, comme les documents ne contenant que des polices standard.  

Aucune expérience préalable avec Aspose.Words n'est requise — il suffit d'une connaissance de base de C# et .NET.

---

![Diagramme d'activation des avertissements de police](placeholder-image.png "Diagramme d'activation des avertissements de police")

*Texte alternatif : diagramme d'activation des avertissements de police montrant le flux d'événements lorsqu'une police manquante est substituée.*

## Étape 1 : Configurer LoadOptions et activer les avertissements de police

La première chose dont vous avez besoin est un objet `LoadOptions`. Ce conteneur indique à Aspose.Words comment traiter le fichier que vous allez charger. En assignant une nouvelle instance de `FontSettings`, vous ouvrez la porte aux événements liés aux polices.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Prepare load options and enable font substitution warnings
LoadOptions loadOptions = new LoadOptions
{
    // Attach a new FontSettings object – this is where warnings are emitted.
    FontSettings = new FontSettings()
};
```

**Pourquoi c'est important :**  
Si vous omettez l'assignation de `FontSettings`, Aspose.Words remplacera toujours les polices manquantes, mais vous ne recevrez aucune notification. Le mécanisme d'avertissement réside dans `FontSettings`, donc l'initialiser est *crucial* pour notre objectif.

> **Astuce :** Vous pouvez également pointer `FontSettings` vers un dossier de polices personnalisé en utilisant `SetFontsFolder`. Cela réduit le nombre d'avertissements que vous verrez, car Aspose.Words peut réellement trouver les polices manquantes.

## Étape 2 : S'abonner à l'événement SubstitutionWarning (substitution de police)

Maintenant que l'objet `FontSettings` existe, nous nous accrochons à son événement `SubstitutionWarning`. Cet événement se déclenche **à chaque fois** qu'Aspose.Words remplace une police demandée par une autre.

```csharp
// Step 2: Subscribe to the SubstitutionWarning event to be notified when a font is replaced
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // e.FontName – the name that the document asked for
    // e.SubstitutedFontName – the font that Aspose.Words actually used
    Console.WriteLine($"[Warning] Font \"{e.FontName}\" was substituted with \"{e.SubstitutedFontName}\".");
};
```

**Pourquoi c'est important :**  
Sans cet écouteur, vous n'auriez aucune visibilité sur le processus de substitution. La ligne console vous fournit une trace d'audit rapide, ce qui est particulièrement pratique lors de builds automatisés ou lors de la génération de PDF pour des industries fortement réglementées.

> **Question fréquente :** *Et si je veux supprimer les avertissements ?*  
> Vous pouvez simplement détacher le gestionnaire ou définir `FontSettings.SubstitutionWarning += null;`. Cependant, conserver les avertissements est généralement la voie la plus sûre car les substitutions silencieuses peuvent entraîner des problèmes de mise en page.

## Étape 3 : Charger votre document avec les options configurées (traitement de documents C#)

Avec le système d'avertissement prêt, le chargement du document est simple. Passez l'instance `LoadOptions` au constructeur `Document`, et Aspose.Words s'occupera du reste.

```csharp
// Step 3: Load the document using the configured options
string filePath = @"C:\Docs\DocumentWithMissingFont.docx";

Document doc = new Document(filePath, loadOptions);

// Optional: Save to PDF to see the visual impact of the substitution
doc.Save(@"C:\Docs\Output.pdf");
```

**Pourquoi c'est important :**  
L'objet `LoadOptions` est le pont entre le fichier brut et l'infrastructure d'avertissement. Si vous l'omettez, le document se charge silencieusement et toutes les polices manquantes sont remplacées sans laisser de trace.

> **Cas limite :** Certains documents intègrent les fichiers de police exacts dont ils ont besoin. Dans ce scénario, aucun avertissement n'apparaîtra car Aspose.Words trouve la police incorporée. Le code ci‑dessus fonctionne toujours ; vous verrez simplement une sortie console vide.

## Étape 4 : Vérifier la sortie et les pièges courants

Exécutez le programme depuis une invite de commande ou le débogueur de votre IDE. Si le document source contient une police qui n'est pas installée sur la machine (ou n'est pas disponible dans le dossier de polices personnalisé), vous verrez des lignes telles que :

```
[Warning] Font "Comic Sans MS" was substituted with "Arial".
[Warning] Font "MyCustomFont" was substituted with "Times New Roman".
```

Si rien n'est affiché, soit :

1. Toutes les polices ont été trouvées, **ou**  
2. Le gestionnaire `SubstitutionWarning` n'a pas été correctement attaché (vérifiez à nouveau l'étape 2).

### Pourquoi les substitutions de police se produisent‑elles ?

- **Police système manquante :** Le système d'exploitation ne possède pas la police demandée.  
- **Format de police non pris en charge :** Aspose.Words peut lire les formats TrueType et OpenType, mais pas tous les formats propriétaires.  
- **Restrictions de licence :** Certaines polices commerciales bloquent l'intégration, obligeant à un remplacement.  

Comprendre le *pourquoi* vous aide à décider s'il faut fournir les polices manquantes avec votre application ou ajuster le style du document.

## Bonus : Contrôler la police de secours

Si vous souhaitez que chaque police manquante revienne à une famille spécifique (par exemple, “Calibri”), vous pouvez définir une règle de substitution globale :

```csharp
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
    "AnyMissingFont", // wildcard – applies to any font not found
    new[] { "Calibri" } // the preferred substitute
);
```

La console vous avertira toujours, mais le résultat visuel sera cohérent pour toutes les polices manquantes.

---

## Récapitulatif

- **Activer les avertissements de police** en créant un `LoadOptions` avec un nouveau `FontSettings`.  
- Accrocher l'événement `SubstitutionWarning` pour recevoir des alertes en temps réel chaque fois qu'une police est remplacée.  
- Charger votre document en utilisant les options configurées, et éventuellement enregistrer en PDF pour voir l'effet visuel.  
- Diagnostiquer la raison d'une substitution et, si nécessaire, forcer une police de secours spécifique.  

Vous venez d'ajouter un filet de sécurité à votre flux de travail **Aspose.Words** qui empêche les changements de mise en page silencieux. Ensuite, vous pourriez explorer les **paramètres de police** comme `DefaultFontName` ou plonger dans les options de **rendu de document** pour affiner la sortie PDF.

### Que faire ensuite ?

- **Explorer d'autres fonctionnalités de FontSettings** : `SetFontsFolder`, `LoadFontSources` et `DefaultFontName`.  
- **Combiner les avertissements avec des frameworks de journalisation** (Serilog, NLog) pour des diagnostics de niveau production.  
- **Expérimenter différents formats de document** (`.doc`, `.rtf`, `.html`) pour voir comment chacun gère les polices manquantes.  

Des questions ou un scénario particulier ? Laissez un commentaire ci‑dessous, et bon codage !

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}