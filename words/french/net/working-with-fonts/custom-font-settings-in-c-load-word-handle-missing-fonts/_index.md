---
category: general
date: 2026-03-08
description: Les paramètres de police personnalisés vous permettent de définir les
  paramètres de police, de charger un document Word en toute sécurité et de gérer
  les polices manquantes avec Aspose.Words.
draft: false
keywords:
- custom font settings
- set font settings
- load word document
- handle missing fonts
language: fr
og_description: Les paramètres de police personnalisés vous permettent de définir
  les paramètres de police, de charger un document Word en toute sécurité et de gérer
  les polices manquantes avec Aspose.Words.
og_title: Paramètres de police personnalisés en C# – Charger Word et gérer les polices
  manquantes
tags:
- Aspose.Words
- C#
- Font Management
title: Paramètres de police personnalisés en C# – Charger Word et gérer les polices
  manquantes
url: /fr/net/working-with-fonts/custom-font-settings-in-c-load-word-handle-missing-fonts/
---

.

Make sure to keep all shortcodes exactly.

Let's craft final output.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Paramètres de police personnalisés en C# – Charger Word et gérer les polices manquantes

Vous êtes‑vous déjà demandé comment fonctionnent les **paramètres de police personnalisés** lorsqu’un fichier Word fait référence à des polices que vous n’avez pas installées ? C’est un problème fréquent — votre document s’affiche correctement sur une machine, puis soudainement chaque paragraphe passe à une police de secours sur une autre.

Bonne nouvelle ? Avec Aspose.Words vous pouvez **définir les paramètres de police**, **charger le contenu d’un document Word** et **gérer les polices manquantes** en un seul flux bien organisé. Vous trouverez ci‑dessous un exemple complet, prêt à être exécuté, qui montre exactement comment procéder, ainsi que le « pourquoi » de chaque étape.

## Ce que vous apprendrez

Dans ce guide nous aborderons :

* La création d’un objet `LoadOptions` et l’attachement d’une instance `FontSettings`.  
* L’enregistrement d’un rappel d’avertissement afin de voir quelles polices sont substituées.  
* Le chargement d’un fichier DOCX pouvant contenir des polices manquantes, et l’affichage des détails de substitution dans la console.  

À la fin, vous pourrez déployer votre application C# en toute confiance, sachant que chaque scénario de police manquante est enregistré et pourra être traité ultérieurement.

> **Prérequis :** Aspose.Words for .NET (v23.12 ou plus récent) installé via NuGet, et une connaissance de base des applications console C#.

---

## Paramètres de police personnalisés – Configurer LoadOptions

La première chose dont vous avez besoin est un objet `LoadOptions`. Il indique à Aspose.Words comment traiter le fichier entrant. En assignant une nouvelle instance `FontSettings`, nous offrons à la bibliothèque un endroit où rechercher des polices personnalisées.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Step 1: Create LoadOptions and enable custom font settings.
LoadOptions loadOptions = new LoadOptions
{
    // Attach a new FontSettings object – it starts empty.
    FontSettings = new FontSettings()
};
```

**Pourquoi c’est important :**  
Si vous omettez `FontSettings`, Aspose.Words revient à la collection de polices par défaut du système. Cela signifie que toute police manquante sera substituée silencieusement, et vous ne saurez pas quelles polices ont été remplacées. En créant un conteneur `FontSettings` explicite, vous obtenez un contrôle total sur le processus de recherche.

---

## Définir les paramètres de police sur LoadOptions

Maintenant que nous disposons d’un objet `FontSettings`, vous vous demandez peut‑être où le pointer. En général, vous ajoutez un dossier contenant les polices que vous livrez avec votre application :

```csharp
// Optional: add a custom folder that holds your private fonts.
string customFontFolder = @"C:\MyApp\Fonts";
loadOptions.FontSettings.SetFontsFolder(customFontFolder, recursive: true);
```

*Si vous n’avez pas de dossier privé, vous pouvez omettre ce bloc—Aspose.Words signalera toujours les polices manquantes via le rappel d’avertissement.*

**Astuce :** Utilisez le drapeau `recursive: true` si vos polices sont réparties dans des sous‑dossiers. Cela vous évite d’ajouter manuellement chaque chemin.

---

## Charger un document Word avec des paramètres de police personnalisés

Avec les options prêtes, le chargement du document devient un jeu d’enfant. Le constructeur `Document` accepte le chemin du fichier et le `LoadOptions` que nous venons de créer.

```csharp
// Step 2: Attach a warning callback to capture font substitution details.
loadOptions.WarningCallback = new FontWarningHandler();

// Step 3: Load the document that may contain missing fonts using the configured options.
Document doc = new Document(@"C:\MyApp\Docs\input.docx", loadOptions);
```

**Que se passe‑t‑il en coulisses ?**  
Aspose.Words analyse le DOCX, vérifie chaque référence `<w:font>`, et consulte les `FontSettings` que vous avez fournis. Si une police n’est pas trouvée, il déclenche un avertissement de type `FontSubstitution`. Notre gestionnaire personnalisé (voir ci‑après) interceptera ces avertissements.

---

## Gérer les polices manquantes avec le rappel d’avertissement

L’interface `IWarningCallback` vous permet de réagir à tout problème survenant pendant le chargement. La mettre en œuvre est simple :

```csharp
public class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Step 4: When a font substitution occurs, output the substituted font name.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

Lorsque le document est chargé, chaque police manquante générera une ligne comme :

```
Font substituted: Arial -> Liberation Sans
```

**Pourquoi vous devriez consigner cela :**  
En production, vous pouvez rediriger ces messages vers un fichier ou un système de télémétrie, ce qui facilite l’identification des polices à regrouper ou à licencier.

---

## Exemple complet fonctionnel

Voici un programme console autonome qui réunit tous les éléments. Copiez‑collez‑le dans un nouveau projet console .NET Core et lancez‑le avec **Run**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

namespace FontDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create LoadOptions with a fresh FontSettings instance.
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };

            // OPTIONAL: Point to a folder that contains your private fonts.
            // Uncomment and adjust the path if you have custom fonts.
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyApp\Fonts", true);

            // 2️⃣ Register a warning callback to capture missing‑font events.
            loadOptions.WarningCallback = new FontWarningHandler();

            // 3️⃣ Load the Word document using the custom options.
            string docPath = @"C:\MyApp\Docs\input.docx";
            Document doc = new Document(docPath, loadOptions);

            // 4️⃣ (Optional) Save the document to another format to verify it loaded correctly.
            doc.Save(@"C:\MyApp\Docs\output.pdf");
            Console.WriteLine("Document loaded and saved as PDF successfully.");
        }
    }

    // 5️⃣ Warning handler that prints font substitution details.
    public class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Font substituted: {info.Description}");
            }
        }
    }
}
```

**Sortie attendue** (en supposant que `input.docx` utilise une police que vous n’avez pas) :

```
Font substituted: Times New Roman -> Liberation Serif
Font substituted: Calibri -> Arial
Document loaded and saved as PDF successfully.
```

Si toutes les polices sont présentes, vous ne verrez que la ligne de confirmation finale.

---

## Questions fréquentes et cas limites

| Question | Réponse |
|----------|--------|
| **Que faire si je dois incorporer les polices manquantes dans le PDF ?** | Après le chargement, appelez `doc.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "YourFallback";` puis activez l’incorporation avec `doc.FontSettings.EmbeddingMode = FontEmbeddingMode.Embedding;`. |
| **Puis‑je supprimer les avertissements au lieu de les consigner ?** | Oui—définissez `loadOptions.WarningCallback = null;` ou implémentez le rappel pour ignorer les avertissements qui ne concernent pas les polices. |
| **Cela fonctionne‑t‑il avec les fichiers `.doc` et `.rtf` ?** | Absolument. Le même objet `LoadOptions` s’applique à tout format pris en charge par Aspose.Words. |
| **Le rappel est‑il thread‑safe ?** | Le rappel s’exécute sur le même thread qui charge le document, vous pouvez donc écrire en toute sécurité dans la console. Pour les scénarios multi‑threads, utilisez une collection concurrente ou un framework de journalisation. |

---

## Astuces & pièges

* *Astuce :* Si vous distribuez une police qui n’est pas installée sur la machine cible, ajoutez‑la au dossier que vous passez à `SetFontsFolder`. Cela garantit un rendu déterministe.  
* *Attention aux licences :* Certaines polices nécessitent des licences commerciales pour l’incorporation. Vérifiez toujours le CLUF de la police avant de la regrouper.  
* *Note de performance :* Charger de grandes bibliothèques de polices peut ralentir l’analyse du document. Gardez le dossier léger—n’incluez que les polices réellement nécessaires.  
* *Cas limite :* Lorsqu’un document fait référence à une police par son *nom PostScript* plutôt que par le nom de famille, Aspose.Words la résout toujours tant que le fichier de police est présent dans le chemin de recherche.

---

## Conclusion

Vous disposez maintenant d’un modèle complet, prêt pour la production, pour utiliser les **paramètres de police personnalisés** en C#. En configurant `LoadOptions`, en enregistrant un rappel d’avertissement et, éventuellement, en pointant vers un dossier de polices privé, vous pouvez **définir les paramètres de police**, **charger le contenu d’un document Word** de manière fiable.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}