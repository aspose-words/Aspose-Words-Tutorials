---
category: general
date: 2026-10-10
description: Traduisez le paragraphe en français et apprenez comment modifier l’étiquette
  de données du graphique, personnaliser l’étiquette de données du graphique, et enregistrer
  le fichier docx modifié en utilisant Aspose.Words AI.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- translate paragraph to french
- how to change chart data label
- how to translate word document with ai
- customize chart data label
- how to save edited docx file
language: fr
lastmod: 2026-10-10
og_description: Traduisez le paragraphe en français et apprenez comment modifier l'étiquette
  de données du graphique, personnaliser l'étiquette de données du graphique et enregistrer
  le fichier docx modifié à l'aide d'Aspose.Words AI.
og_image_alt: Screenshot of a Word document showing a French paragraph and a chart
  with a customized data label
og_title: Traduire le paragraphe en français et modifier l’étiquette du graphique
  dans Word
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Translate paragraph to French and learn how to change chart data label,
    customize chart data label, and save edited docx file using Aspose.Words AI.
  headline: Translate paragraph to French and change chart label in Word
  type: TechArticle
tags:
- Aspose.Words
- C#
- AI translation
- chart customization
title: Traduire le paragraphe en français et modifier l’étiquette du graphique dans
  Word
url: /fr/net/ai-powered-document-processing/translate-paragraph-to-french-and-change-chart-label-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Traduire un paragraphe en français et modifier le libellé du graphique dans Word

Si vous devez **traduire un paragraphe en français** tout en mettant à jour un graphique dans le même document Word, ce guide vous montre exactement comment faire. En utilisant Aspose.Words AI, vous pouvez traduire le texte automatiquement, puis modifier le libellé d’un graphique et enfin enregistrer le fichier `.docx` modifié — le tout en quelques étapes simples.

Le tutoriel couvre tout, depuis le chargement du fichier source jusqu’à la persistance des modifications. À la fin, vous serez capable de traduire n’importe quel paragraphe, de personnaliser le libellé d’un graphique et de produire un nouveau fichier Word prêt à être distribué. Aucun script externe n’est requis ; l’ensemble du flux de travail réside dans un seul programme C#.

## Prérequis

- .NET 6.0 ou version ultérieure (le code fonctionne également avec .NET Framework 4.7+)
- Une licence Aspose.Words for .NET (ou une clé d’évaluation gratuite)
- Un accès Internet pour le traducteur Google AI (la classe `Translator` utilise l’API de Google en interne)
- Un document Word (`input.docx`) contenant au moins un paragraphe et un graphique

## Étape 1 : Configurer le projet et importer les espaces de noms

Créez une nouvelle application console et ajoutez le package NuGet Aspose.Words :

```bash
dotnet new console -n WordAiDemo
cd WordAiDemo
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

Ensuite, incluez les espaces de noms requis en haut de `Program.cs` :

```csharp
using System;
using Aspose.Words;
using Aspose.Words.AI;          // AI translation helpers
using Aspose.Words.Drawing;    // Chart manipulation classes
using Aspose.Words.Tables;     // For accessing chart series and labels
```

Ces importations vous donnent accès aux fonctionnalités de chargement de document, de traduction IA et de modification de graphique.

## Étape 2 : Charger le document Word source

```csharp
// Path to the original file – adjust as needed
string inputPath = @"YOUR_DIRECTORY/input.docx";

// Load the document into memory
Document document = new Document(inputPath);
Console.WriteLine("Document loaded successfully.");
```

Le chargement du fichier crée une représentation en mémoire que vous pouvez interroger et modifier sans toucher au fichier original sur le disque.

## Étape 3 : Traduire le premier paragraphe en français

Le premier paragraphe est souvent un titre ou une phrase d’introduction, ce qui en fait un bon candidat pour la traduction. La classe `Translator` encapsule l’appel au modèle IA de Google.

```csharp
// Retrieve the first paragraph in the first section
Paragraph paragraph = document.FirstSection.Body.FirstParagraph;

// Extract the raw text (including trailing paragraph mark)
string originalText = paragraph.GetText();

// Translate the text to French
string translatedText = Translator.Translate(originalText, Language.French);
Console.WriteLine($"Original: {originalText.Trim()}");
Console.WriteLine($"Translated: {translatedText.Trim()}");

// Replace the paragraph's runs with the translated text
paragraph.Runs.Clear();                     // Remove existing runs
paragraph.AppendChild(new Run(document, translatedText)); // Insert new run
```

**Pourquoi cela fonctionne :**  
`paragraph.Runs.Clear()` supprime toutes les exécutions de texte existantes, garantissant que la nouvelle traduction ne se concatène pas avec l’ancien contenu. `new Run(document, translatedText)` crée une nouvelle exécution qui hérite du formatage du paragraphe.

## Étape 4 : Localiser le premier graphique et personnaliser son libellé de données

Les graphiques sont stockés sous forme de nœuds `Shape` de type `NodeType.Shape`. Le premier graphique peut être récupéré avec `GetChild`.

```csharp
// Find the first chart in the document (deep search)
Chart chart = (Chart)document.GetChild(NodeType.Shape, 0, true);
if (chart == null)
{
    Console.WriteLine("No chart found in the document.");
    return;
}

// Access the first series and its first data label
ChartSeries series = chart.Series[0];
ChartDataLabel dataLabel = series.DataLabels[0];

// Change the label's position and text
dataLabel.Position = ChartDataLabelPosition.OutsideEnd; // Move label outside the bar
dataLabel.Text = "Ventes T1"; // French for "Sales Q1"
Console.WriteLine("Chart data label customized.");
```

**Explication des étapes clés :**

- `GetChild(NodeType.Shape, 0, true)` effectue une recherche en profondeur et renvoie la première forme, qui dans notre cas est un graphique.
- `ChartSeries` représente une collection de points de données ; la première série (`Series[0]`) correspond généralement à l’ensemble de données principal.
- `ChartDataLabelPosition.OutsideEnd` déplace le libellé à l’extérieur de l’extrémité de la barre, améliorant la lisibilité.
- Définir `dataLabel.Text` sur une chaîne en français aligne le libellé avec le paragraphe traduit.

## Étape 5 : Enregistrer le document avec le paragraphe traduit

```csharp
string translatedDocPath = @"YOUR_DIRECTORY/translated.docx";
document.Save(translatedDocPath);
Console.WriteLine($"Translated document saved to {translatedDocPath}");
```

À ce stade, le document contient le paragraphe en français mais conserve toujours la configuration originale du graphique.

## Étape 6 : Enregistrer le document avec le graphique mis à jour

Vous pouvez réutiliser la même instance `Document` — aucune nécessité de le recharger — car les modifications du graphique sont déjà en mémoire.

```csharp
string chartUpdatedPath = @"YOUR_DIRECTORY/chart-updated.docx";
document.Save(chartUpdatedPath);
Console.WriteLine($"Chart‑updated document saved to {chartUpdatedPath}");
```

Les deux fichiers sont maintenant prêts à être distribués :

- **`translated.docx`** – contient le paragraphe en français.  
- **`chart-updated.docx`** – contient le paragraphe en français *et* le libellé du graphique personnalisé.

## Exemple complet, exécutable

Ci‑dessous se trouve le programme complet que vous pouvez copier‑coller dans `Program.cs`. Il se compile et s’exécute tel quel, à condition d’avoir remplacé `YOUR_DIRECTORY` par un chemin de dossier réel.



## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser des fonctionnalités supplémentaires de l’API et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Personnaliser le libellé d’un graphique](/words/english/net/programming-with-charts/chart-data-label/)
- [Formater le nombre de libellés de données dans un graphique](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Libellé de données du graphique](/words/french/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}