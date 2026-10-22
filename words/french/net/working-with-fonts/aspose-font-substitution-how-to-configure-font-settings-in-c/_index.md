---
category: general
date: 2026-03-27
description: 'Substitution de polices Aspose simplifiée : apprenez à configurer les
  paramètres de police, à capturer les avertissements et à gérer les polices manquantes
  dans vos applications .NET.'
draft: false
keywords:
- aspose font substitution
- configure font settings
- Aspose.Words warning callback
- FontSubstitutionWarningHandler
- LoadOptions example
language: fr
og_description: Maîtrisez la substitution de polices Aspose en configurant les paramètres
  de police et en gérant les polices manquantes avec un rappel d’avertissement. Guide
  complet C#.
og_title: Substitution de polices Aspose – Configurer les paramètres de police en
  C#
tags:
- Aspose.Words
- C#
- Font Management
title: Substitution de polices Aspose – Comment configurer les paramètres de police
  en C#
url: /fr/net/working-with-fonts/aspose-font-substitution-how-to-configure-font-settings-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution – Guide complet pour configurer les paramètres de police

Vous êtes déjà tombé sur un document qui remplace soudainement votre police personnalisée par quelque chose de générique ? C’est **aspose font substitution** qui fait son travail — en remplaçant les polices manquantes par la correspondance la plus proche qu’il peut trouver. C’est pratique, mais si vous devez savoir *exactement* quelle police a été remplacée, vous devez exploiter le système d’avertissement de la bibliothèque et configurer vous‑même les paramètres de police.

Dans ce tutoriel, nous parcourrons un scénario réel : charger un DOCX qui référence une police que vous n’avez pas, capturer l’événement de substitution et afficher un message convivial dans la console. À la fin, vous serez à l’aise avec **configure font settings**, la mise en place d’un **Aspose.Words warning callback**, et l’extension de l’exemple pour s’adapter à n’importe quel flux de travail.

> **Ce dont vous aurez besoin**  
> • .NET 6+ (or .NET Framework 4.7.2+)  
> • Aspose.Words for .NET (latest NuGet)  
> • Un DOCX qui référence une police manquante (nous l’appellerons `MissingFont.docx`)  

Plongeons‑y.

---

## Étape 1 : Installer Aspose.Words et préparer le projet

Avant d’écrire du code, assurez‑vous que le package Aspose.Words est référencé :

```bash
dotnet add package Aspose.Words
```

> **Conseil pro :** utilisez la dernière version stable ; en mars 2026, il s’agit de la 23.11.0. Les versions plus récentes améliorent les algorithmes de correspondance des polices et ajoutent des types d’avertissement supplémentaires.

Créez une nouvelle application console (ou ajoutez le code dans un projet existant) et ajoutez les directives `using` habituelles :

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Ces espaces de noms nous donnent accès aux classes `Document`, `LoadOptions` et aux classes liées aux polices dont nous aurons besoin.

## Étape 2 : Configurer les paramètres de police avec LoadOptions

Le cœur du contrôle de **aspose font substitution** se trouve dans `LoadOptions.FontSettings`. En fournissant un objet `FontSettings` vide, nous indiquons à Aspose d’utiliser ses chemins de recherche par défaut *et* de signaler toute substitution via un rappel d’avertissement.

```csharp
// Step 2: Prepare LoadOptions with a fresh FontSettings instance
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};
```

Pourquoi ne pas simplement se fier aux valeurs par défaut ? Parce que l’attachement d’un rappel d’avertissement (étape suivante) ne fonctionne que lorsque la propriété `FontSettings` n’est pas nulle. Cette petite ligne nous fournit un point d’ancrage dans le processus de substitution sans modifier le comportement réel de recherche des polices.

## Étape 3 : Attacher un rappel d’avertissement pour capturer les substitutions

Aspose.Words implémente l’interface `IWarningCallback`. Chaque fois qu’un événement notable se produit — comme une police manquante — il appelle notre méthode `Warning`. Nous implémenterons un petit gestionnaire qui filtre les `WarningType.FontSubstitution` et affiche la description.

```csharp
// Step 3: Register the warning handler
loadOptions.WarningCallback = new FontSubstitutionWarningHandler();
```

Et voici le gestionnaire lui‑même :

```csharp
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Step 4: Output information about the substituted font
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

> **Pourquoi c’est important** – Sans le rappel, Aspose remplace silencieusement les polices, et vous ne savez jamais laquelle a été utilisée. Le rappel rend le processus transparent, ce qui est essentiel pour les rapports de conformité ou le débogage des problèmes de mise en page.

## Étape 4 : Charger le document en utilisant les options configurées

Nous chargeons enfin le document, en passant le `loadOptions` que nous venons de préparer. Si le fichier source référence une police qui n’est pas installée, notre gestionnaire sera déclenché.

```csharp
// Step 4: Load the document with the custom LoadOptions
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

Remplacez `YOUR_DIRECTORY` par le chemin réel où se trouve `MissingFont.docx`. Lorsque vous exécutez le programme, vous devriez voir une sortie similaire à :

```
Font substitution detected: Font "MyCustomFont" was not found. Substituted with "Arial".
```

Cette ligne indique exactement quelle police était manquante et quel substitut Aspose a choisi.

## Étape 5 : (Optionnel) Affiner les chemins de recherche des polices

Si vous avez un dossier privé contenant des polices d’entreprise, vous pouvez indiquer à Aspose où chercher avant qu’il ne se rabattre sur les polices système. C’est une utilisation avancée de **configure font settings** :

```csharp
// Optional: Add a custom folder to the font search collection
loadOptions.FontSettings.SetFontsFolder(@"C:\Company\Fonts", recursive: true);
```

Définir `recursive: true` fait qu’Aspose parcourt également les sous‑dossiers. La bibliothèque essaiera d’abord vos polices privées, réduisant ainsi le risque de substitution indésirable.

## Exemple complet fonctionnel

En rassemblant tous les éléments, voici le programme complet, prêt à être exécuté :

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare FontSettings inside LoadOptions
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // 2️⃣ Hook our warning handler
        loadOptions.WarningCallback = new FontSubstitutionWarningHandler();

        // 3️⃣ (Optional) Add a custom font folder
        // loadOptions.FontSettings.SetFontsFolder(@"C:\Company\Fonts", true);

        // 4️⃣ Load the document – triggers warnings if needed
        Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // 5️⃣ Do something with the document – e.g., save as PDF
        doc.Save("Output.pdf");
        Console.WriteLine("Document processed and saved as Output.pdf");
    }
}

// Warning handler that prints substitution details
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**Sortie attendue** (lorsqu’une police manquante est rencontrée) :

```
Font substitution detected: Font "MyCustomFont" was not found. Substituted with "Arial".
Document processed and saved as Output.pdf
```

Si toutes les polices sont présentes, le programme s’exécute silencieusement (aucun avertissement) et produit toujours le PDF.

## Questions fréquentes & cas particuliers

### Que faire si je dois *empêcher* toute substitution ?

Définissez `FontSettings.SubstitutionSettings` à `null` ou utilisez `FontSettings.FontSubstitutionSettings` pour contrôler le comportement. Par exemple :

```csharp
loadOptions.FontSettings.SubstitutionSettings.DefaultFontSubstitution = false;
```

Aspose lèvera maintenant une exception au lieu de substituer silencieusement, ce qui peut être intercepté et géré.

### Cela fonctionne‑t‑il avec d’autres formats de fichier (par ex., .doc, .rtf) ?

Absolument. Le même objet `LoadOptions` peut être passé à n’importe quel constructeur `Document` qui accepte un chemin de fichier. Le rappel d’avertissement sera déclenché pour tous les formats qui utilisent des polices.

### Puis‑je capturer le nom exact de la police de substitution ?

Oui. La chaîne `info.Description` contient à la fois la police manquante et le substitut. Si vous avez besoin du nom programmatiquement, vous pouvez l’analyser ou utiliser l’objet `FontInfo` (disponible dans les versions récentes).

### Comment cela se comporte‑t‑il dans un environnement multithread ?

`FontSettings` n’est **pas** thread‑safe. Créez un `LoadOptions` distinct (avec son propre `FontSettings`) par thread, ou protégez l’accès avec un verrou.

## Conclusion

Nous avons couvert tout ce dont vous avez besoin pour maîtriser **aspose font substitution** et **configure font settings** dans une application C# :

1. Installez Aspose.Words et ajoutez les directives `using` nécessaires.  
2. Créez un objet `LoadOptions` avec un nouveau `FontSettings`.  
3. Attachez un `IWarningCallback` personnalisé pour exposer les événements de substitution.  
4. Chargez le document, en laissant le rappel signaler toute police manquante.  
5. (Optionnel) Étendez le chemin de recherche ou désactivez complètement la substitution.

Grâce à ce modèle, vous pouvez consigner les polices manquantes pour la conformité, alerter les utilisateurs dans une interface, ou intégrer automatiquement des polices de secours avant la publication. Ensuite, vous pourriez explorer les **politiques de substitution de police Aspose.Words** ou intégrer le flux de travail dans une chaîne de traitement de documents plus vaste.

Bon codage, et que vos documents s’affichent toujours avec la bonne police !  

---  

![Diagramme montrant Aspose.Words chargeant un document, invoquant FontSettings, déclenchant un rappel d’avertissement et affichant les informations de substitution](image-placeholder.png "flux de travail de substitution de police aspose")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}