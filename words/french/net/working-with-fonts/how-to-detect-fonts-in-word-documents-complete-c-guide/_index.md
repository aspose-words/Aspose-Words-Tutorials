---
category: general
date: 2026-02-24
description: Comment détecter les polices dans un document Word à l'aide d'Aspose.Words.
  Apprenez à définir le rappel et à charger le document Word avec un exemple complet
  de code.
draft: false
keywords:
- how to detect fonts
- how to set callback
- load word document
- font substitution warning
- Aspose.Words warning callback
language: fr
og_description: Comment détecter les polices dans un document Word en utilisant un
  rappel d’avertissement. Ce guide montre comment définir le rappel et charger un
  document Word avec Aspose.Words.
og_title: Comment détecter les polices dans les documents Word – Tutoriel C# étape
  par étape
tags:
- C#
- Aspose.Words
- Document Processing
title: Comment détecter les polices dans les documents Word – Guide complet C#
url: /fr/net/working-with-fonts/how-to-detect-fonts-in-word-documents-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment détecter les polices dans les documents Word – Guide complet C#

Vous vous êtes déjà demandé **comment détecter les polices** manquantes lorsque vous chargez un fichier Word ? Peut‑être avez‑vous rencontré un document qui semble correct dans l’éditeur, mais le PDF que vous générez remplace quelques polices en coulisses. C’est un symptôme classique de substitution de police, et le détecter tôt peut vous éviter de mauvaises surprises de mise en page.

Dans ce tutoriel, nous allons parcourir une solution pratique : utiliser **Aspose.Words** pour charger un `.docx`, attacher un rappel d’avertissement, et **comment définir le rappel** qui signale chaque substitution de police. À la fin, vous ne saurez pas seulement **comment détecter les polices** programmétiquement, vous comprendrez également **comment définir le rappel** correctement et **charger le document Word** en toute sécurité—le tout dans un seul exemple C# exécutable.

> **Ce que vous obtiendrez**
> * Un exemple de code complet, prêt à copier‑coller  
> * Une explication pas à pas de chaque ligne  
> * Des astuces pour gérer les cas limites comme plusieurs polices manquantes ou des dossiers de polices personnalisés  
> * La sortie console attendue afin que vous puissiez vérifier que tout fonctionne

---

## Prérequis

- .NET 6.0 ou ultérieur (le code fonctionne également avec .NET Core)  
- Package NuGet Aspose.Words pour .NET (`Install-Package Aspose.Words`)  
- Un fichier Word qui référence intentionnellement une police que vous n’avez pas installée (par ex., `MissingFont.docx`)  
- Visual Studio, Rider, ou tout éditeur de votre choix

Aucune autre bibliothèque n’est nécessaire ; tout le reste fait partie du runtime .NET standard.

---

## Comment détecter les polices dans un document Word

### Étape 1 : Créer les options de chargement et attacher un rappel d’avertissement

La première chose que nous faisons est d’indiquer à Aspose.Words que nous souhaitons être notifiés de tout problème survenant lors du chargement du fichier. C’est ici que **comment définir le rappel** entre en jeu.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

/// <summary>
/// Collects font‑related warnings during document loading.
/// </summary>
public class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            var substitution = (FontSubstitutionWarning)info;
            Console.WriteLine(
                $"Font '{substitution.MissingFontName}' was substituted with " +
                $"'{substitution.SubstitutedFontName}' at {substitution.Location}");
        }
    }
}
```

**Pourquoi c’est important :**  
`LoadOptions` est la porte d’entrée pour personnaliser le processus de chargement. En assignant une instance de `FontWarningCollector` à `WarningCallback`, Aspose.Words invoquera notre méthode `Warning` chaque fois qu’elle remplace une police manquante par une police de secours. C’est le cœur de **comment détecter les polices** qui ne sont pas présentes sur la machine.

### Étape 2 : Préparer l’instance LoadOptions

Nous créons maintenant une instance de `LoadOptions` et y attachons notre rappel.

```csharp
// Step 2: Initialize LoadOptions and attach the warning collector.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCollector()
};
```

**Astuce :** Si vous devez contrôler *où* Aspose recherche les polices de remplacement, vous pouvez également définir `loadOptions.FontSettings` ici. Cela est utile lorsque vous avez un dossier de polices privé sur le serveur.

### Étape 3 : Charger le document Word

Avec les options prêtes, nous **chargeons enfin le document Word**. C’est le moment où Aspose analyse le DOCX et, si des polices sont manquantes, notre rappel se déclenche.

```csharp
// Step 3: Load the document that may contain missing fonts.
string filePath = @"YOUR_DIRECTORY\MissingFont.docx";
Document doc = new Document(filePath, loadOptions);
```

**Que se passe-t-il en coulisses ?**  
Aspose.Words lit les parties XML du DOCX, résout chaque référence `<w:font>` et vérifie la collection de polices du système. Chaque fois qu’une référence ne peut être satisfaite, il substitue la première police de secours correspondante et génère un avertissement `FontSubstitution`.

### Étape 4 : Vérifier la sortie

Exécutez le programme et observez la console. Pour chaque police manquante, vous verrez une ligne du type :

```
Font 'Comic Sans MS' was substituted with 'Arial' at Paragraph 3, Run 2
```

Si le document ne contient aucune police manquante, la console reste silencieuse—ce qui signifie que **comment détecter les polices** n’a renvoyé aucun résultat.

### Étape 5 : Exemple complet fonctionnel (application console)

Ci‑dessous se trouve un `Program.cs` autonome que vous pouvez placer dans un nouveau projet console. Il inclut toutes les pièces que nous avons abordées ainsi qu’un petit utilitaire pour garder la fenêtre console ouverte lors du débogage.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontDetectionDemo
{
    // ----- Step 1: Warning callback implementation -----
    public class FontWarningCollector : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                var substitution = (FontSubstitutionWarning)info;
                Console.WriteLine(
                    $"Font '{substitution.MissingFontName}' was substituted with " +
                    $"'{substitution.SubstitutedFontName}' at {substitution.Location}");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // ----- Step 2: Configure LoadOptions -----
            var loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // ----- Step 3: Load the Word file -----
            string filePath = @"YOUR_DIRECTORY\MissingFont.docx";
            Document doc = new Document(filePath, loadOptions);

            // Optional: Do something with the document (e.g., save as PDF)
            // doc.Save("output.pdf");

            // Keep console open for debugging
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

**Sortie console attendue** (exemple) :

```
Font 'Papyrus' was substituted with 'Times New Roman' at Paragraph 1, Run 5
Font 'Brush Script MT' was substituted with 'Calibri' at Paragraph 4, Run 1

Press any key to exit...
```

Si vous remplacez `MissingFont.docx` par un fichier qui n’utilise que des polices installées, vous ne verrez que la ligne « Press any key… »—confirmant que la logique de détection fonctionne comme prévu.

---

## Questions fréquentes & cas limites

### Et si je dois capturer *tous* les avertissements, pas seulement les substitutions de police ?

Il suffit de supprimer la condition `if (info.Type == WarningType.FontSubstitution)`. L’objet `WarningInfo` contient une énumération `Type` sur laquelle vous pouvez basculer pour d’autres scénarios (par ex., `DocumentStructure`, `ImageLoading`).

### Puis‑je enregistrer les avertissements dans un fichier au lieu de la console ?

Absolument. Remplacez `Console.WriteLine` par n’importe quel appel à un framework de journalisation (`Serilog`, `NLog`, etc.). Le rappel s’exécute sur le même thread qui charge le document, assurez‑vous donc que votre logger soit thread‑safe.

### Comment cela se comporte‑t‑il dans une application web ?

Dans ASP.NET Core, vous injecterez généralement une implémentation singleton de `IWarningCallback` et la passerez via `LoadOptions`. N’oubliez pas d’éviter d’écrire directement dans le flux de réponse — journalisez dans une base de données ou une collection en mémoire que vous pourrez ensuite exposer via un point d’accès API.

### Et les polices personnalisées stockées dans un dossier non‑système ?

```csharp
var fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
loadOptions.FontSettings = fontSettings;
```

Aspose.Words recherchera désormais `C:\MyCustomFonts` avant de revenir aux polices du système d’exploitation, réduisant ainsi le nombre d’avertissements de substitution que vous voyez.

---

## Résumé visuel

![Detect fonts warning callback in Aspose.Words](/images/font-warning-callback.png "How to detect fonts using a warning callback")

*La capture d’écran montre la sortie console lorsqu’une police manquante est substituée. Le texte alternatif contient le mot‑clé principal pour le SEO.*

---

## Conclusion

Vous disposez désormais d’un modèle solide et prêt pour la production pour **comment détecter les polices** dans n’importe quel fichier Word que vous chargez avec Aspose.Words. En **définissant le rappel**, vous obtenez une visibilité en temps réel sur les polices manquantes ou substituées, et vous avez appris la bonne façon de **charger le document Word** tout en gardant votre code propre et maintenable.

Prochaines étapes ? Essayez d’étendre le rappel pour collecter les avertissements dans une liste, puis les exposer dans une interface ou un rapport automatisé. Vous pouvez également explorer `FontSettings.SubstitutionSettings` pour contrôler *quelles* polices sont choisies comme secours.

N’hésitez pas à expérimenter—remplacez le document, ajoutez plus de polices manquantes, ou intégrez la logique dans un pipeline de traitement de documents plus vaste. Si vous rencontrez des problèmes, laissez un commentaire ci‑dessous ou contactez‑moi sur GitHub.

Bon codage, et que vos documents s’affichent toujours avec les polices attendues !

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}