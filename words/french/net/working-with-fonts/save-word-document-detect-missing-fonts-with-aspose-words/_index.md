---
category: general
date: 2026-03-22
description: Enregistrez un document Word et détectez les polices manquantes avec
  Aspose.Words. Apprenez comment suivre les polices manquantes et capturer les erreurs
  de police en C#.
draft: false
keywords:
- save word document
- detect missing fonts
- track missing fonts
- capture font errors
language: fr
og_description: Enregistrez un document Word et détectez les polices manquantes en
  C#. Ce guide montre comment suivre les polices manquantes et capturer les erreurs
  de police à l'aide d'un rappel d'avertissement.
og_title: Enregistrer le document Word – Détecter les polices manquantes avec Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: Enregistrer le document Word – Détecter les polices manquantes avec Aspose.Words
url: /fr/net/working-with-fonts/save-word-document-detect-missing-fonts-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Enregistrer un document Word – Détecter les polices manquantes avec Aspose.Words

Vous avez déjà eu besoin d'**enregistrer un document Word** mais vous n'étiez pas sûr que certaines des polices à l'intérieur survivent au aller‑retour ? Cela arrive plus souvent que vous ne le pensez, surtout lorsque les documents circulent entre des machines avec des bibliothèques de polices différentes. La bonne nouvelle ? Aspose.Words vous offre une méthode intégrée pour **détecter les polices manquantes** pendant que vous **enregistrez un document Word**, afin que vous puissiez consigner, avertir, ou même les remplacer avant que le fichier n'apparaisse à l'écran de l'utilisateur.

Dans ce tutoriel, nous parcourrons un exemple complet, prêt à l'exécution, qui non seulement enregistre un document Word mais aussi **suivre les polices manquantes** et **capturer les erreurs de police** à l'aide d'un gestionnaire d'avertissement personnalisé. À la fin, vous saurez exactement pourquoi le rappel d'avertissement est important, comment le brancher, et à quoi ressemble la sortie console lorsqu'une substitution se produit. Pas de fioritures supplémentaires—juste le code que vous pouvez intégrer immédiatement dans un projet .NET.

> **Prérequis**  
> • .NET 6 (ou toute version récente du .NET Framework) installé  
> • Visual Studio 2022 ou votre IDE préféré  
> • Une copie sous licence de **Aspose.Words for .NET** (l'essai gratuit fonctionne pour les tests)  

Si vous avez tout cela, commençons.

---

## Enregistrer un document Word et détecter les polices manquantes

L'idée principale est simple : avant d'appeler `Document.Save`, assignez un objet qui implémente `IWarningCallback` à `Document.WarningCallback`. Aspose.Words invoquera cet objet pour chaque avertissement qu'il rencontre, y compris les avertissements de **substitution de police** qui se produisent lorsque le document source fait référence à une police que votre système ne trouve pas.

```csharp
using Aspose.Words;
using Aspose.Words.Warning;

// Step 1: Create a warning handler that prints font substitution messages
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Only react to font‑substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

// Step 2: Load a document that may contain missing fonts
Document document = new Document("YOUR_DIRECTORY/input.docx");

// Step 3: Register the warning handler with the document
document.WarningCallback = new FontWarningHandler();

// Step 4: Save the document; any font substitution warnings will be output to the console
document.Save("YOUR_DIRECTORY/output.docx");
```

**Ce que vous verrez :**  
Si `input.docx` fait référence à une police qui n'est pas installée, la console affiche quelque chose comme :

```
Font substitution: Font "Comic Sans MS" was substituted with "Arial".
```

Cette ligne vous indique exactement quelle police était manquante et ce qu'Aspose.Words a utilisé à la place—parfait pour **capturer les erreurs de police** avant d'expédier le fichier.

---

## Suivre les polices manquantes avec un rappel d'avertissement (Étape par étape)

### 1️⃣ Installer Aspose.Words

Ouvrez la console NuGet de votre projet et exécutez :

```bash
dotnet add package Aspose.Words
```

Cela récupère la dernière version stable (actuellement 24.10). Garder la bibliothèque à jour vous assure d'obtenir les dernières capacités de **détection des polices manquantes** et les corrections de bugs.

### 2️⃣ Définir le gestionnaire d'avertissement

Pourquoi avons‑nous besoin d'une classe séparée ? Implémenter `IWarningCallback` vous permet de centraliser toute la logique d'avertissement en un seul endroit. Vous pourriez également consigner dans un fichier, envoyer des télémétries, ou lever une exception si une police manquante constitue une erreur critique pour votre flux de travail.

```csharp
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only the warnings we care about
        if (info.Type == WarningType.FontSubstitution)
        {
            // Here we simply write to the console,
            // but you could replace this with any logging framework.
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}
```

> **Astuce :** Si vous devez **suivre les polices manquantes** à travers de nombreux documents, stockez les messages dans une `List<string>` à l'intérieur du gestionnaire et exposez‑les plus tard pour le reporting.

### 3️⃣ Charger votre document source

Le constructeur `Document` peut accepter un chemin de fichier, un flux, ou même des octets bruts. Dans la plupart des cas, vous le pointerez vers un `.docx` que vous avez reçu d'un utilisateur ou d'un autre système.

```csharp
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Si le fichier est volumineux, envisagez d'utiliser `LoadOptions` pour activer le chargement paresseux, ce qui réduit la pression sur la mémoire.

### 4️⃣ Attacher le rappel

Assignez l'instance à `doc.WarningCallback`. À partir de ce moment, chaque avertissement (y compris les substitutions de police) passera par votre gestionnaire.

```csharp
doc.WarningCallback = new FontWarningHandler();
```

### 5️⃣ Enregistrer le document

Vous pouvez maintenant appeler `Save` en toute sécurité. Le gestionnaire d'avertissement s'exécute **synchroniquement** pendant l'opération d'enregistrement, vous verrez donc la sortie immédiatement.

```csharp
doc.Save("YOUR_DIRECTORY/output.docx");
```

Si vous préférez enregistrer dans un format différent (PDF, HTML, etc.), le même mécanisme d'avertissement fonctionne—Aspose.Words signalera toujours les polices manquantes avant la conversion.

---

## Capturer les erreurs de police – Cas limites courants

Bien que le flux de base couvre la plupart des scénarios, les projets du monde réel rencontrent souvent quelques problèmes. Voici quelques variantes que vous pourriez rencontrer et comment les gérer.

### Police manquante dans un en‑tête/pied de page

Les en‑têtes et pieds de page sont des nœuds séparés, mais le système d'avertissement les traite de la même manière que le texte du corps. Aucun code supplémentaire n'est nécessaire ; le rappel se déclenchera également pour ces polices. Assurez‑vous simplement de charger le document complet (le comportement par défaut le fait).

### Substitutions multiples dans un même document

Si un document utilise plusieurs polices inconnues, le gestionnaire sera appelé une fois par substitution. Pour éviter d'inonder la console, vous pourriez dédupliquer les messages :

```csharp
class FontWarningHandler : IWarningCallback
{
    private readonly HashSet<string> _seen = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution && _seen.Add(info.Description))
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}
```

### Transformer les avertissements en exceptions

Parfois, une police manquante est un obstacle majeur. Levez une exception à l'intérieur du gestionnaire pour interrompre l'enregistrement :

```csharp
if (info.Type == WarningType.FontSubstitution)
{
    throw new InvalidOperationException($"Missing font detected: {info.Description}");
}
```

N'oubliez pas d'encadrer `doc.Save` dans un bloc `try/catch` pour gérer l'exception de manière élégante.

---

## Vérifier le résultat – À quoi s'attendre

Après la fin de l'enregistrement, ouvrez `output.docx` dans Microsoft Word (ou tout visualiseur compatible). Vous devriez voir la même mise en page visuelle que l'original, mais les polices substituées apparaîtront comme le secours que vous avez observé dans la console. Pour vérifier, vous pouvez :

1. Ouvrez **Fichier → Options → Avancé → Afficher le contenu du document → Utiliser la qualité brouillon** – cela force Word à révéler les substitutions de police cachées.
2. Utilisez la boîte de dialogue **Remplacer les polices** de Word (`Ctrl+Shift+F`) pour voir quelles polices sont réellement incorporées.

Si tout correspond, vous avez réussi à **enregistrer un document Word** tout en **détectant les polices manquantes** et **capturant les erreurs de police**. 🎉

---

## Exemple complet fonctionnel (prêt à copier‑coller)

Ci-dessous se trouve le programme complet que vous pouvez intégrer dans un nouveau projet d'application console. Remplacez simplement `YOUR_DIRECTORY` par un chemin de dossier réel sur votre machine.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Warning;

namespace FontWarningDemo
{
    // Step 1: Create a warning handler that prints font substitution messages
    class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            // Only handle font‑substitution warnings
            if (info.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Font substitution: {info.Description}");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // Step 2: Load a document that may contain missing fonts
            Document document = new Document("YOUR_DIRECTORY/input.docx");

            // Step 3: Register the warning handler with the document
            document.WarningCallback = new FontWarningHandler();

            // Step 4: Save the document; any font substitution warnings will be output to the console
            document.Save("YOUR_DIRECTORY/output.docx");

            Console.WriteLine("Document saved successfully.");
        }
    }
}
```

**Sortie console attendue** (exemple) :

```
Font substitution: Font "Times New Roman" was substituted with "Arial".
Document saved successfully.
```

C’est toute l’histoire—pas d’étapes cachées, pas de documents externes à poursuivre.

---

## Conclusion

Nous venons de vous montrer comment **enregistrer un document Word** tout en **détectant activement les polices manquantes**, **suivant les polices manquantes**, et **capturant les erreurs de police** à l'aide du rappel d'avertissement d'Aspose.Words. En connectant une petite implémentation de `IWarningCallback`, vous obtenez une visibilité complète sur les substitutions de police au moment de l'enregistrement, vous donnant la possibilité de consigner, remplacer ou interrompre selon les besoins.  

Prêt pour le prochain défi ? Essayez d'étendre le gestionnaire pour écrire les avertissements dans un journal JSON structuré, ou combinez‑le avec Aspose.PDF pour convertir le même document tout en préservant les informations de police. Vous pourriez également explorer l'incorporation des polices manquantes directement dans le fichier de sortie—Aspose.Words prend en charge l'incorporation de polices via `LoadOptions.FontSettings`.  

Testez‑le, ajustez le code pour l'adapter à votre pipeline, et dites‑nous comment cela fonctionne pour vous. Bon codage !

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}