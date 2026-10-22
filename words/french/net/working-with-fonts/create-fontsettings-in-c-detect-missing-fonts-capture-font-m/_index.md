---
category: general
date: 2026-03-01
description: Créer FontSettings en C# pour détecter les polices manquantes, capturer
  les messages de police et gérer les polices manquantes avec Aspose.Words. Guide
  étape par étape pour les développeurs.
draft: false
keywords:
- create fontsettings
- detect missing fonts
- capture font messages
- handle missing fonts
- Aspose.Words font handling
- C# document processing
language: fr
og_description: Créer FontSettings en C# pour détecter les polices manquantes, capturer
  les messages de police et gérer les polices manquantes avec Aspose.Words. Tutoriel
  complet avec code.
og_title: Créer FontSettings en C# – Détecter les polices manquantes et capturer les
  messages de police
tags:
- Aspose.Words
- C#
- Font Management
title: Créer FontSettings en C# – Détecter les polices manquantes et capturer les
  messages de police
url: /fr/net/working-with-fonts/create-fontsettings-in-c-detect-missing-fonts-capture-font-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer FontSettings en C# – Détecter les polices manquantes et capturer les messages de police

Vous avez déjà eu besoin de **créer FontSettings** dans un projet .NET mais vous ne saviez pas comment repérer les polices qui ne sont pas installées sur la machine cible ? Vous n'êtes pas seul. Dans de nombreuses applications réelles — pensez aux générateurs de rapports automatisés ou aux convertisseurs de documents — les polices manquantes peuvent casser la mise en page en silence, et vous ne le saurez que lorsque le PDF aura l'air déformé.  

Et si vous pouviez **détecter les polices manquantes**, **capturer les messages de police**, et **gérer les polices manquantes** avant qu'elles ne ruinent votre résultat ? La bonne nouvelle, c’est qu’Aspose.Words rend cela très simple. Dans ce tutoriel, nous parcourrons l’ensemble du processus, depuis la configuration de l’objet `FontSettings` jusqu’à la mise en place d’un rappel d’avertissement qui vous indique exactement quels glyphes ont été substitués.

> **TL;DR :** À la fin, vous disposerez d’une application console C# prête à l’emploi qui consigne chaque substitution de police, vous permettant de décider d’embarquer un remplacement ou d’avertir l’utilisateur.

---

## Prérequis

- SDK .NET 6 (ou toute version .NET récente)  
- Visual Studio 2022 ou VS Code avec les extensions C#  
- Une licence Aspose.Words for .NET (l’essai gratuit suffit pour cette démo)  
- Un fichier DOCX d’exemple qui référence une police que vous n’avez pas installée (par ex., *Comic Sans MS* sur une machine Linux)  

Aucun package NuGet spécial au‑delà de `Aspose.Words` n’est requis.

---

## Étape 1 – Installer Aspose.Words et configurer le projet

Première chose, créez un nouveau projet console et ajoutez la bibliothèque Aspose.Words.

```bash
dotnet new console -n FontSettingsDemo
cd FontSettingsDemo
dotnet add package Aspose.Words
```

> **Astuce :** Si vous avez déjà une solution, ajoutez simplement le package via l’interface du Gestionnaire de packages NuGet — cela facilite le suivi des versions.

---

## Étape 2 – Créer FontSettings (Mot‑clé principal apparaît ici)

L’étape **créer FontSettings** est la pierre angulaire de tout flux de travail lié aux polices. `FontSettings` indique à Aspose.Words où chercher les polices, s’il faut utiliser les dossiers système, et comment réagir lorsqu’une police est absente.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a FontSettings object – this is where we’ll configure search paths.
FontSettings fontSettings = new FontSettings();

// Optional: add a custom folder that contains fallback fonts.
fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);
```

Pourquoi est‑ce important ? Sans un `FontSettings` correctement configuré, le moteur substitue silencieusement les glyphes manquants par la police système par défaut, et vous ne verrez jamais d’avertissement.

---

## Étape 3 – Brancher LoadOptions avec le FontSettings

`LoadOptions` vous permet de transmettre le `FontSettings` au chargeur de documents. C’est le pont qui permet au moteur **détecter les polices manquantes** pendant la phase de construction du `Document`.

```csharp
// 2️⃣ Configure LoadOptions to use the FontSettings we just created.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

Désormais, chaque fois que vous chargez un DOCX avec `loadOptions`, Aspose.Words consultera le `FontSettings` que nous avons configuré précédemment.

---

## Étape 4 – Attacher un rappel d’avertissement pour **capturer les messages de police**

Aspose.Words émet des avertissements pour diverses conditions — la substitution de police étant l’une des plus courantes. En fournissant une implémentation de `IWarningCallback`, vous pouvez **capturer les messages de police** en temps réel.

```csharp
// 3️⃣ Attach a warning handler that will print font‑substitution warnings.
loadOptions.WarningCallback = new FontSubstitutionWarningHandler();
```

### La classe de gestion des avertissements

```csharp
/// <summary>
/// Handles font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Source == WarningSource.FontSubstitution)
        {
            Console.WriteLine($"[FontSubstitution] {info.Description}");
        }
    }
}
```

Le champ `info.Description` contient un message lisible tel que *« Police 'Comic Sans MS' introuvable. Substituée par 'Arial'. »* C’est exactement le type de sortie dont vous avez besoin pour **gérer les polices manquantes** de façon élégante.

---

## Étape 5 – Charger le document et laisser le rappel faire son travail

Avec tout en place, le chargement du document est simple. Si le fichier source référence une police absente du système, notre gestionnaire d’avertissements se déclenchera.

```csharp
// 4️⃣ Load a document that may contain unknown fonts.
Document doc = new Document(@"C:\Docs\UnknownFont.docx", loadOptions);

// Optional: you can now save the document to PDF or any other format.
doc.Save(@"C:\Docs\Result.pdf");
```

Lorsque vous exécutez le programme, vous verrez une sortie console similaire à :

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
[FontSubstitution] Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

Cette sortie correspond à la partie **capturer les messages de police** de notre flux de travail. Vous pouvez étendre le gestionnaire pour enregistrer dans un fichier, envoyer des télémétries, ou même interrompre la conversion si des polices critiques sont manquantes.

---

## Étape 6 – Exemple complet fonctionnel (Tous les éléments réunis)

Voici un programme complet, prêt à copier‑coller. Collez‑le dans `Program.cs`, ajustez les chemins de fichiers, puis lancez `dotnet run`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSettingsDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ----- Step 1: Create FontSettings -----
            FontSettings fontSettings = new FontSettings();
            // Add any custom folder with fallback fonts (optional)
            fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);

            // ----- Step 2: Configure LoadOptions -----
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontSubstitutionWarningHandler()
            };

            // ----- Step 3: Load the document -----
            string inputPath = @"C:\Docs\UnknownFont.docx";
            Document doc = new Document(inputPath, loadOptions);

            // ----- Step 4: Save the result (optional) -----
            string outputPath = @"C:\Docs\Result.pdf";
            doc.Save(outputPath);

            Console.WriteLine("Document processed. Check console for any font substitution warnings.");
        }
    }

    // ----- Warning handler that captures font messages -----
    class FontSubstitutionWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Source == WarningSource.FontSubstitution)
            {
                Console.WriteLine($"[FontSubstitution] {info.Description}");
            }
        }
    }
}
```

### Sortie attendue

Exécuter le programme sur une machine qui ne possède pas *Comic Sans MS* affichera quelque chose comme :

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document processed. Check console for any font substitution warnings.
```

Vous obtiendrez également `Result.pdf` qui utilise les polices substituées, garantissant que la conversion ne plante jamais.

---

## Questions fréquentes & Cas particuliers

| Question | Réponse |
|----------|--------|
| **Et si je veux que la conversion échoue au lieu de substituer ?** | Dans `FontSubstitutionWarningHandler`, lancez une exception lorsque `info.Description` contient le nom d’une police critique. |
| **Puis‑je embarquer automatiquement une police de remplacement ?** | Oui. Après avoir détecté une police manquante, vous pouvez charger un `FontInfo` de secours depuis un chemin connu et l’ajouter à `fontSettings` via `fontSettings.SetFontsFolder`. |
| **Cela fonctionne‑t‑il sous Linux/macOS ?** | Absolument. `FontSettings` fonctionne sur toutes les plateformes ; assurez‑vous simplement que le dossier de secours contient les fichiers `.ttf` ou `.otf` appropriés. |
| **Le rappel d’avertissement est‑il thread‑safe ?** | Le rappel s’exécute sur le même thread que le chargement du document, donc aucune synchronisation supplémentaire n’est nécessaire pour la journalisation console. Pour les scénarios multithreads, protégez les ressources partagées. |
| **Comment enregistrer les avertissements dans un fichier ?** | Remplacez `Console.WriteLine` par `File.AppendAllText("font_warnings.log", ...)` ou utilisez un framework de journalisation (Serilog, NLog). |

---

## Astuces pro pour une gestion des polices prête pour la production

1. **Mettre en cache les recherches de polices** – Réutiliser la même instance de `FontSettings` sur plusieurs chargements de documents évite des analyses répétées du système de fichiers.  
2. **Liste blanche des polices critiques** – Si votre marque nécessite une police spécifique, vérifiez sa présence dès le départ et interrompez avec un message d’erreur clair.  
3. **Utiliser `SetFontFolder` de façon récursive** – Le paramètre `recursive: true` garantit que les sous‑dossiers sont analysés, pratique lorsque vous déployez une collection complète de polices.  
4. **Combiner avec `FontSubstitutionSettings`** – Vous pouvez affiner les règles de substitution (par ex., privilégier les polices du même nom de famille).  

---

## Conclusion

Nous venons de **créer FontSettings**, de configurer `LoadOptions` pour **détecter les polices manquantes**, d’attacher un rappel qui **capture les messages de police**, et nous avons montré comment **gérer les polices manquantes** de manière propre et prête pour la production. L’ensemble du flux tient en quelques dizaines de lignes de C#, tout en vous offrant une visibilité totale sur le paysage des polices de tout DOCX que vous traitez.

Ensuite, vous pourriez explorer :

- **Embarquer des polices de secours** directement dans le PDF de sortie (`PdfSaveOptions.FontEmbeddingMode`).  
- **Substituer les polices programmatiquement** selon les règles de branding de votre entreprise.  
- **Intégrer à une pipeline CI** pour signaler automatiquement les documents qui utilisent des polices non autorisées.

Essayez, ajustez le gestionnaire d’avertissements à vos besoins, et laissez vos pipelines de documents fonctionner en toute confiance — plus de bugs de mise en page mystérieux causés par des substitutions de police invisibles.

Bon codage ! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}