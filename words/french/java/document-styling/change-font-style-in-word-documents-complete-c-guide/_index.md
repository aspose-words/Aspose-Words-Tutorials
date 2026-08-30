---
category: general
date: 2026-06-27
description: Modifiez le style de police dans les documents Word avec C#. Apprenez
  à définir le poids de la police, à appliquer le gras et à ajuster la largeur de
  la police pour une typographie précise.
draft: false
keywords:
- change font style
- set font weight
- set bold weight
- adjust font width
- modify font in word
language: fr
og_description: Modifiez le style de police dans les documents Word avec C#. Découvrez
  comment définir le poids de la police, appliquer le gras et ajuster la largeur de
  la police en quelques étapes simples.
og_title: Modifier le style de police dans les documents Word – Guide complet C#
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Change font style in Word documents with C#. Learn how to set font
    weight, set bold weight, and adjust font width for precise typography.
  headline: Change Font Style in Word Documents – Complete C# Guide
  type: TechArticle
- description: Change font style in Word documents with C#. Learn how to set font
    weight, set bold weight, and adjust font width for precise typography.
  name: Change Font Style in Word Documents – Complete C# Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code compiles on .NET Core as well) - Aspose.Words
      for .NET NuGet package (`Install-Package Aspose.Words`) - A sample `input.docx`
      placed in a folder you can reference (we’ll call it `YOUR_DIRECTORY`)'
  - name: Expected Result
    text: '- All body text that previously used the default font now appears **bold**
      (weight 700). - If you experimented with `SetWidth(80)`, the characters will
      look a bit tighter; `SetWidth(120)` will spread them out. - No other content
      (images, tables, etc.) is altered—only the font characteristics of text'
  - name: Can I change the font family at the same time?
    text: 'Absolutely. After you’ve set the `FontVariation`, you can also assign a
      new `FontInfo` to the `FontSettings`:'
  - name: What if I need to **set bold weight** only for headings?
    text: 'Retrieve the heading style node and apply a separate `FontSettings` instance:'
  - name: Does this work with .NET Core on Linux?
    text: Yes—Aspose.Words is cross‑platform. Just ensure you have the appropriate
      runtime libraries installed (`libgdiplus` on some distributions) if you plan
      to render the document to PDF later.
  type: HowTo
tags:
- C#
- Aspose.Words
- typography
title: Modifier le style de police dans les documents Word – Guide complet C#
url: /fr/java/document-styling/change-font-style-in-word-documents-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Modifier le style de police dans les documents Word – Guide complet C#

Vous avez déjà eu besoin de **modifier le style de police** dans un fichier Word sans savoir quelle appel d’API fait réellement le travail ? Vous n’êtes pas seul — la plupart des développeurs rencontrent ce problème lorsqu’ils essaient pour la première fois d’ajuster la typographie par programme.  

La bonne nouvelle, c’est qu’avec quelques lignes de C# vous pouvez **définir le poids de la police**, même augmenter le poids en gras, et affiner la largeur de chaque glyphe. Dans ce tutoriel, nous parcourrons un exemple complet et exécutable qui modifie un fichier `.docx` du début à la fin.

## Ce que couvre ce guide

Nous commencerons par charger un document existant, puis créerons un objet `FontSettings` contenant un `FontVariation`. À partir de là, nous **définirons le poids de la police**, **définirons le poids en gras**, et **ajusterons la largeur de la police** avant d’appliquer les modifications et d’enregistrer le résultat. Aucun fichier de configuration externe, aucune chaîne magique — juste du C# pur et la bibliothèque Aspose.Words. À la fin, vous serez capable de **modifier la police dans Word** avec assurance, que vous construisiez un moteur de rapports ou un outil de formatage en masse.

### Prérequis

- .NET 6.0 ou version ultérieure (le code compile également sous .NET Core)  
- Package NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)  
- Un fichier d’exemple `input.docx` placé dans un dossier que vous pouvez référencer (nous l’appellerons `YOUR_DIRECTORY`)  

Si vous avez ces bases, plongeons‑y.

---

## Étape 1 : Modifier le style de police – Charger le document Word

La première chose à faire est de charger le fichier cible en mémoire. Considérez cela comme l’ouverture d’une toile vierge où vous peindrez plus tard votre nouvelle typographie.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // Load the document you want to modify
        Document document = new Document(@"YOUR_DIRECTORY\input.docx");
        Console.WriteLine("Document loaded successfully.");
```

> **Astuce :** Si vous exécutez cela sur un serveur sans interface utilisateur, assurez‑vous que la licence Aspose.Words est soit en mode d’évaluation, soit qu’un fichier de licence approprié a été appliqué afin d’éviter les filigranes.

---

## Étape 2 : Définir le poids de la police et le poids en gras

Maintenant que le document est en mémoire, nous créons un conteneur `FontSettings`. Cet objet est la porte d’entrée à chaque réglage de niveau police que vous pouvez effectuer.  

La classe `FontVariation` vous permet de spécifier trois attributs principaux :

| Propriété | Description | Intervalle typique |
|-----------|-------------|--------------------|
| `Weight` | Contrôle la lourdeur visuelle du glyphe. Une valeur de **700** correspond au “gras” standard. | 100‑900 |
| `Width`  | Étire ou condense le glyphe horizontalement. **100** signifie largeur normale. | 50‑200 |
| `Slant`  | Ajoute une inclinaison de type italique. Les nombres positifs inclinent vers la droite. | -90‑90 |

Ci‑dessous, nous **définissons le poids de la police** à 700 (gras) et montrons également comment l’augmenter davantage si votre police supporte un style “extra‑bold”.

```csharp
        // Create a FontSettings object to hold customizations
        FontSettings fontSettings = new FontSettings();

        // Define a FontVariation with the desired style attributes
        FontVariation variation = new FontVariation();
        variation.SetWeight(700);   // Set bold weight (standard)
        // variation.SetWeight(800); // Uncomment for extra‑bold if supported
        variation.SetSlant(0);      // No slant – keep upright

        // Attach the variation to the FontSettings
        fontSettings.SetFontVariation(variation);
```

> **Pourquoi c’est important :** Définir le **poids en gras** directement via `SetWeight` évite d’avoir à créer un objet de style “Bold” séparé, vous offrant un contrôle pixel‑par‑pixel sur l’épaisseur des traits.

---

## Étape 3 : Ajuster la largeur de la police

Si vous avez déjà eu besoin de rendre une police plus serrée pour un titre ou plus espacée pour un paragraphe, vous serez content d’arriver à cette étape. La propriété `Width` fait exactement cela.

```csharp
        // Adjust the width of the font – 100 is normal, 80 is condensed, 120 is expanded
        variation.SetWidth(100); // Normal width
        // variation.SetWidth(80);  // Uncomment for a condensed look
        // variation.SetWidth(120); // Uncomment for an expanded look
```

> **Piège fréquent :** Toutes les polices ne respectent pas les variations de largeur. Si vous ne voyez aucun changement visuel, vérifiez que la famille de polices que vous utilisez prend en charge les glyphes condensés/étendus.

---

## Étape 4 : Appliquer les réglages de police – Modifier la police dans Word

Avec notre `FontSettings` entièrement configuré, le dernier pas consiste à indiquer au document de les utiliser. C’est ici que nous **modifions la police dans Word** au niveau du document, affectant chaque segment de texte qui hérite du style par défaut.

```csharp
        // Apply the FontSettings to the document
        document.FontSettings = fontSettings;
        Console.WriteLine("Font settings applied.");
```

Si vous ne voulez cibler qu’un paragraphe ou un run spécifique, vous pouvez récupérer ce nœud et définir son `FontSettings` individuellement. L’exemple ci‑dessus montre l’approche globale, idéale pour les scénarios de formatage en masse.

---

## Étape 5 : Enregistrer et vérifier les modifications

L’enregistrement est la dernière, mais certainement pas la moindre, partie du flux de travail. Après avoir persistant le fichier, vous pouvez l’ouvrir dans Microsoft Word pour voir le nouveau style en action.

```csharp
        // Save the modified document
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### Résultat attendu

- Tout le texte du corps qui utilisait auparavant la police par défaut apparaît maintenant en **gras** (poids 700).  
- Si vous avez testé `SetWidth(80)`, les caractères seront un peu plus serrés ; `SetWidth(120)` les étirera.  
- Aucun autre contenu (images, tableaux, etc.) n’est modifié — seules les caractéristiques de police des runs textuels le sont.

Ouvrez `output.docx` dans Word, sélectionnez un paragraphe et consultez la boîte de dialogue **Police**. Vous verrez la case **Gras** cochée et l’**Échelle** (largeur) reflétant la valeur que vous avez choisie.

---

## Questions fréquentes & cas particuliers

### Puis‑je changer la famille de police en même temps ?

Absolument. Après avoir défini le `FontVariation`, vous pouvez également assigner un nouveau `FontInfo` au `FontSettings` :

```csharp
fontSettings.SetFontsFolder(@"C:\MyFonts\", true); // Point to a folder with custom fonts
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes("Times New Roman", new[] { "MyCustomFont" });
```

### Et si je veux **définir le poids en gras** uniquement pour les titres ?

Récupérez le nœud de style de titre et appliquez‑lui une instance séparée de `FontSettings` :

```csharp
Style headingStyle = document.Styles["Heading 1"];
headingStyle.Font.Name = "Arial";
headingStyle.Font.Size = 16;
headingStyle.Font.Bold = true; // Quick way for headings only
```

### Cela fonctionne‑t‑il avec .NET Core sous Linux ?

Oui—Aspose.Words est multiplateforme. Assurez‑vous simplement d’avoir les bibliothèques d’exécution appropriées installées (`libgdiplus` sur certaines distributions) si vous prévoyez de rendre le document en PDF plus tard.

---

## Conclusion

Nous venons de **modifier le style de police** dans un document Word du début à la fin, en couvrant comment **définir le poids de la police**, **définir le poids en gras**, et **ajuster la largeur de la police** avec C#. L’exemple complet et exécutable montre chaque importation, création d’objet et appel de méthode requis, afin que vous puissiez le copier‑coller dans votre propre projet et voir la typographie se transformer instantanément.

Maintenant que vous savez comment **modifier la police dans Word**, vous pouvez explorer des sujets connexes comme **l’intégration de polices personnalisées**, **l’application de dégradés de couleur**, ou **la création de tableaux dynamiques**. Chacun de ces sujets repose sur la même base `FontSettings` que nous avons utilisée ici, vous plaçant déjà une longueur d’avance.

Vous avez un scénario qui n’est pas couvert ? Laissez un commentaire, et nous l’examinerons ensemble. Bon codage—et que vos documents aient toujours l’apparence exacte que vous désirez !  

![change font style example](placeholder.png){alt="exemple de modification du style de police"}

## Que devriez‑vous apprendre ensuite ?


Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets et fonctionnels avec des explications pas à pas pour vous aider à maîtriser des fonctionnalités API supplémentaires et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Set Font Emphasis Mark](/words/hindi/net/working-with-fonts/set-font-emphasis-mark/)
- [Set Font Fallback Settings](/words/hindi/net/working-with-fonts/set-font-fallback-settings/)
- [Set Font Formatting](/words/hindi/net/working-with-fonts/set-font-formatting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}