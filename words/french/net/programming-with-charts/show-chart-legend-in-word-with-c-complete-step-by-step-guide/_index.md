---
category: general
date: 2026-06-02
description: Afficher la légende du graphique dans un document Word avec C#. Apprenez
  à ajouter une légende, appliquer un style de graphique prédéfini et personnaliser
  les visuels du graphique Word en quelques minutes.
draft: false
keywords:
- show chart legend
- how to add legend
- add legend word chart
- apply preset chart style
- apply chart style word
language: fr
og_description: Affichez la légende du graphique dans un document Word instantanément.
  Ce guide vous explique comment ajouter une légende, appliquer un style de graphique
  prédéfini et gérer les cas particuliers.
og_title: Afficher la légende du graphique dans Word – Tutoriel complet C#
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  headline: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  name: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  steps:
  - name: How to add legend to a specific chart (not the first one)?
    text: 'Replace the `0` index in `GetChild(NodeType.Chart, 0, true)` with the zero‑based
      position of your target chart, or loop through all chart nodes:'
  - name: Can I place the legend at the bottom instead of the right?
    text: 'Absolutely. Just change the `LegendPosition` enum:'
  - name: What if the chart already has a legend but I want to hide it?
    text: 'Set `HasLegend` to `false`:'
  - name: Does this work with Word 2010, 2016, and later?
    text: Yes. Aspose.Words abstracts the underlying Word version, so the same code
      works across all modern .docx files.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word chart
- Legend customization
title: Afficher la légende du graphique dans Word avec C# – Guide complet étape par
  étape
url: /fr/net/programming-with-charts/show-chart-legend-in-word-with-c-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Afficher la légende du graphique dans Word avec C# – Guide complet étape par étape

Vous vous êtes déjà demandé **comment ajouter une légende** à un graphique intégré dans un document Word ? Vous n'êtes pas le seul. Dans de nombreux rapports, l'absence de légende rend les données cryptiques, et la corriger ne devrait pas être un casse‑tête.  

Dans ce tutoriel, nous allons **afficher la légende du graphique** dans un fichier Word en utilisant Aspose.Words pour .NET, appliquer un style de graphique prédéfini, et nous assurer que la légende apparaît exactement où vous le souhaitez. À la fin, vous disposerez d’un exemple prêt à l’exécution que vous pourrez intégrer à n’importe quel projet C#.

## Ce que couvre ce guide

Nous allons parcourir l’ensemble du flux de travail :

1. Charger un *.docx* existant qui contient déjà un graphique.  
2. Récupérer le premier graphique (ou tout autre graphique ciblé).  
3. **Appliquer un style de graphique prédéfini** pour donner à la visualisation un aspect professionnel.  
4. **Afficher la légende du graphique**, la positionner à droite, et gérer les cas particuliers comme les graphiques en cascade.  
5. Enregistrer le document modifié.

Pas d’outils externes, pas de manipulation manuelle de l’interface—juste du code pur. La seule condition préalable est une référence au package NuGet Aspose.Words (version 23.10 ou ultérieure) et une compréhension de base du C#.

---

## Prérequis

- .NET 6.0 ou version ultérieure (l’exemple fonctionne également avec .NET Framework 4.7.2).  
- Bibliothèque Aspose.Words pour .NET installée (`Install-Package Aspose.Words`).  
- Un fichier Word (`input.docx`) contenant déjà au moins un graphique.  
- Visual Studio, Rider, ou tout IDE de votre choix.

---

## Étape 1 : Configurer le projet et charger le document

Tout d’abord, créez une application console (ou intégrez le code dans un projet existant). Ajoutez les directives `using` et chargez le fichier `.docx`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        
        // Continue with the next steps...
```

> **Pourquoi c’est important :** Charger le document est la base. Sans instance de `Document`, vous ne pouvez pas accéder aux objets de graphique exposés par Aspose.Words.

---

## Étape 2 : Récupérer le graphique ciblé

Les graphiques sont stockés comme nœuds dans l’arbre du document. La méthode `GetChild` effectue une recherche en profondeur, nous permettant de récupérer le premier graphique quel que soit son emplacement (en‑tête, corps, pied de page, etc.).

```csharp
        // Retrieve the first chart in the document (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }
```

> **Astuce :** Si vous avez plusieurs graphiques, changez l’indice `0` en `1`, `2`, … ou parcourez `doc.GetChildNodes(NodeType.Chart, true)`.

---

## Étape 3 : Appliquer un style visuel prédéfini

Un graphique esthétique commence souvent par un style. Aspose.Words propose des dizaines de styles intégrés ; `ChartStyle.Style12` est une option épurée et moderne.

```csharp
        // Apply a preset visual style to the chart
        chart.Style = ChartStyle.Style12;
```

> **Comment ça fonctionne :** La propriété `Style` correspond aux styles de graphique Word intégrés que vous voyez dans l’interface. Choisir un style prédéfini vous évite de définir manuellement les couleurs, polices et marqueurs.

---

## Étape 4 : Activer la légende et la positionner

Passons maintenant à la vedette du spectacle—**afficher la légende du graphique**. Nous activons la légende, puis l’ancrons du côté droit du graphique.

```csharp
        // Enable the legend and place it on the right side
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;
```

> **Pourquoi à droite ?** Placer la légende à droite laisse la zone de données plus large, ce qui est particulièrement utile pour les graphiques à barres ou en colonnes.

---

## Étape 5 : Gérer les graphiques en cascade (cas spécial)

Les graphiques en cascade se comportent légèrement différemment ; la légende peut être masquée par défaut. La clause de garde suivante garantit que la légende est visible lorsque le type de graphique est Waterfall.

```csharp
        // For Waterfall charts, ensure the legend is visible
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }
```

> **Note de cas limite :** Certaines versions anciennes de Word ignorent `HasLegend` pour les graphiques en cascade, donc définir explicitement `Legend.Show` assure la visibilité.

---

## Étape 6 : Enregistrer le document modifié

Enfin, écrivez les modifications sur le disque. Vous pouvez écraser le fichier original ou en créer un nouveau.

```csharp
        // Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

L’exécution du programme générera `output.docx` avec une légende visible à droite, stylisée avec `Style12`. Ouvrez le fichier dans Word pour vérifier le résultat.

---

## Exemple complet fonctionnel (toutes les étapes combinées)

Voici le code complet, prêt à l’exécution. Copiez‑collez‑le dans `Program.cs` (ou tout fichier C#) et ajustez les chemins de fichiers.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Retrieve the first chart (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // 3️⃣ Apply a preset visual style (show chart legend with a nice look)
        chart.Style = ChartStyle.Style12;

        // 4️⃣ Enable the legend and dock it to the right
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;

        // 5️⃣ Special handling for Waterfall charts
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }

        // 6️⃣ Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

**Sortie attendue :** L’ouverture de `output.docx` montre le graphique original avec une légende alignée à droite, stylisée avec le moderne `Style12`. Toutes les séries de données sont clairement étiquetées, rendant le graphique immédiatement compréhensible.

---

## Questions fréquentes (FAQ)

### Comment ajouter une légende à un graphique spécifique (pas le premier) ?

Remplacez l’indice `0` dans `GetChild(NodeType.Chart, 0, true)` par la position (index zéro) de votre graphique ciblé, ou parcourez tous les nœuds de graphiques :

```csharp
NodeCollection charts = doc.GetChildNodes(NodeType.Chart, true);
foreach (Chart c in charts)
{
    // Apply the same steps to each chart
}
```

### Puis‑je placer la légende en bas plutôt qu’à droite ?

Absolument. Il suffit de modifier l’énumération `LegendPosition` :

```csharp
chart.Legend.Position = LegendPosition.Bottom;
```

### Que faire si le graphique possède déjà une légende mais que je veux la masquer ?

Définissez `HasLegend` à `false` :

```csharp
chart.HasLegend = false;
```

### Cette méthode fonctionne‑t‑elle avec Word 2010, 2016 et les versions ultérieures ?

Oui. Aspose.Words abstrait la version sous‑jacente de Word, de sorte que le même code fonctionne avec tous les fichiers .docx modernes.

---

## Astuces pro & pièges courants

- **Astuce pro :** Après avoir appliqué un style, vous pouvez toujours ajuster les éléments individuels (couleurs, étiquettes de données) via la collection `Chart.Series`. Le style vous fournit une base solide.
- **À surveiller :** Si le graphique se trouve dans une cellule de tableau, la légende peut être à l’étroit. Envisagez d’augmenter la taille du graphique (`chart.Width`, `chart.Height`) avant de positionner la légende.
- **Note de performance :** Charger de gros documents (des centaines de Mo) peut être gourmand en mémoire. Utilisez `LoadOptions` avec `LoadFormat.Docx` pour réduire la charge si vous ne manipulez que des graphiques.

---

## Prochaines étapes

Maintenant que vous savez **comment ajouter une légende** et **appliquer un style de graphique prédéfini** dans Word, vous pouvez explorer :

- **Couleurs de graphique personnalisées** (`chart.Series[i].Format.Fill.ForeColor`).  
- **Mise en forme des étiquettes de données** (`chart.Series[i].HasDataLabel = true`).  
- **Exportation du graphique en image** (`chart.ToImage()`), utile pour l’intégrer ailleurs.  

Chacun de ces sujets s’appuie sur le même modèle d’objet, de sorte que la courbe d’apprentissage restera douce.

---

## Conclusion

Nous venons de démontrer une solution propre, de bout en bout, pour **afficher la légende du graphique** dans un document Word en utilisant C#. En chargeant le document, en récupérant le graphique, en appliquant un style prédéfini, en activant la légende et en gérant les particularités des graphiques en cascade, vous obtenez un graphique soigné, prêt pour tout rapport d’entreprise.  

N’hésitez pas à expérimenter d’autres valeurs `ChartStyle` ou positions de légende — vos visualisations de données méritent la meilleure présentation. Si vous rencontrez des problèmes, laissez un commentaire ci‑dessous ; bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Using Word Chart API](/words/english/net/programming-with-charts/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}