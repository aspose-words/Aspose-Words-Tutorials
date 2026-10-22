---
category: general
date: 2026-08-17
description: Comment ajouter des contrôles ActiveX et insérer un graphique circulaire
  dans un document Word avec Aspose.Words. Exploser une tranche et enregistrer au
  format DOCX en quelques étapes.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert pie chart
- save as docx
- how to insert chart
- explode pie slice
language: fr
lastmod: 2026-08-17
og_description: Comment ajouter des contrôles ActiveX, insérer un diagramme circulaire,
  éclater une tranche et enregistrer au format DOCX avec Aspose.Words – guide complet
  étape par étape.
og_image_alt: Screenshot of a Word document showing an ActiveX button and a pie chart
  with an exploded slice
og_title: Comment ajouter ActiveX et insérer un graphique circulaire dans un document
  Word
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: How to add ActiveX controls and insert a pie chart in a Word doc using
    Aspose.Words. Explode a slice and save as DOCX in a few steps.
  headline: How to add ActiveX and insert a pie chart in a Word doc
  type: TechArticle
tags:
- Aspose.Words
- ActiveX
- Chart
- DOCX
title: Comment ajouter un ActiveX et insérer un diagramme circulaire dans un document
  Word
url: /fr/java/using-document-elements/how-to-add-activex-and-insert-a-pie-chart-in-a-word-doc/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment ajouter ActiveX et insérer un diagramme circulaire dans un document Word

Si vous avez besoin de **comment ajouter ActiveX** contrôles et d'intégrer un graphique dans un document Word, ce tutoriel vous montre une solution complète et exécutable. En utilisant Aspose.Words, vous pouvez placer un ActiveX CommandButton, créer un diagramme circulaire, éclater une tranche pour la mettre en évidence, et enfin **enregistrer au format DOCX** en quelques lignes de C#.

Dans les sections ci‑dessous, vous verrez chaque import requis, une liste complète de code, et des explications sur l’importance de chaque étape. À la fin, vous serez capable d’intégrer des contrôles interactifs et des données visuelles dans n’importe quel fichier .docx que vous générez programmaticalement.

## Prérequis

* .NET 6.0 ou version ultérieure (le code fonctionne également avec .NET Framework 4.7+)
* Le package Aspose.Words for .NET (disponible via NuGet)
* Un environnement de développement tel que Visual Studio 2022 ou VS Code
* Une connaissance de base du C# et du modèle d’objet Word

Aucune bibliothèque de graphiques tierce supplémentaire n’est requise — Aspose.Words fournit une création de graphiques intégrée.

## Comment ajouter des contrôles ActiveX avec Aspose.Words

Les contrôles ActiveX vous permettent d’intégrer des éléments d’interface utilisateur interactifs directement dans un fichier Word. Dans ce guide, nous ajoutons un **CommandButton** qui pourra ensuite être relié à du code VBA.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Step 1: Create a new document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Step 2: Insert a group shape to hold the ActiveX control
GroupShape groupShape = builder.InsertGroupShape();

// Step 3: Insert a rectangle shape, hide it, and attach it to the group
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
groupShape.AppendChild(rectangleShape);
rectangleShape.SetHidden(true);

// Step 4: Insert a plain‑text StructuredDocumentTag (optional placeholder)
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "MyTag");

// Step 5: Insert the CommandButton ActiveX control
Forms2OleControl commandButton = builder.InsertForms2OleControl();
commandButton.SetActiveXControlType(Forms2OleControlType.CommandButton);
commandButton.SetCaption("Click Me");

// The CommandButton now appears in the document and can be used in VBA macros.
```

**Pourquoi cela fonctionne :**  
`InsertForms2OleControl` crée un conteneur OLE que l’interface Word reconnaît comme un contrôle ActiveX. Définir le type de contrôle sur `CommandButton` et lui attribuer une légende le fait se comporter comme un bouton standard lorsque l’utilisateur ouvre le fichier dans Word.

## Insérer un diagramme circulaire et éclater une tranche

Les graphiques sont utiles pour visualiser des données sans quitter le document. Les étapes suivantes démontrent **comment insérer un graphique** et spécifiquement un **diagramme circulaire** dont la première tranche est éclatée.

```csharp
// Step 6: Insert a pie chart (400 × 300 points)
Chart pieChart = (Chart)builder.InsertChart(ChartType.Pie, 400, 300);

// Populate the chart with sample data
pieChart.Series.Clear();
ChartSeries series = pieChart.Series.Add("Sales", new[] { "Q1", "Q2", "Q3", "Q4" },
                                          new[] { 12000, 15000, 9000, 13000 });

// Step 7: Explode the first slice for emphasis
series.SetExplode(0, true);

// Optional: Customize colors or labels here if needed
```

**Pourquoi éclater la tranche :**  
Appeler `SetExplode(0, true)` indique à Aspose.Words de décaler le premier point de données, attirant ainsi l’œil du lecteur vers ce segment. C’est une technique courante dans les présentations pour mettre en avant une valeur clé.

## Enregistrer au format DOCX

Après avoir ajouté le bouton ActiveX et le graphique, enregistrez le document sur le disque. Cette étape montre **enregistrer au format DOCX** en utilisant la méthode standard.

```csharp
// Step 8: Save the document in DOCX format
document.Save("Output.docx", SaveFormat.Docx);
```

Le fichier `Output.docx` contient désormais un bouton interactif, un diagramme circulaire avec une tranche éclatée, et peut être ouvert dans Microsoft Word sans plugins supplémentaires.

## Exemple complet exécutable

En rassemblant tous les éléments, voici un programme autonome que vous pouvez copier dans une application console et exécuter immédiatement.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Create document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert group shape and hidden rectangle (required for ActiveX positioning)
        GroupShape group = builder.InsertGroupShape();
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        group.AppendChild(rect);
        rect.SetHidden(true);

        // Optional placeholder tag
        builder.InsertStructuredDocumentTag(StructuredDocumentTagType.PlainText, "MyTag");

        // Insert CommandButton ActiveX control
        Forms2OleControl button = builder.InsertForms2OleControl();
        button.SetActiveXControlType(Forms2OleControlType.CommandButton);
        button.SetCaption("Click Me");

        // Insert pie chart and explode first slice
        Chart chart = (Chart)builder.InsertChart(ChartType.Pie, 400, 300);
        chart.Series.Clear();
        ChartSeries series = chart.Series.Add("Revenue", new[] { "Jan", "Feb", "Mar" },
                                               new[] { 5000, 7000, 3000 });
        series.SetExplode(0, true); // explode pie slice

        // Save the document
        doc.Save("Output.docx", SaveFormat.Docx);

        Console.WriteLine("Document created successfully: Output.docx");
    }
}
```

**Résultat attendu :**  
L’ouverture de `Output.docx` dans Word affiche un bouton intitulé *Click Me* et un diagramme circulaire où la première tranche (January) est décalée du reste. Le bouton est prêt pour la gestion d’événements VBA, et le graphique peut être modifié à l’aide des outils de graphiques intégrés de Word.

## Questions fréquentes et cas particuliers

- **Puis‑je ajouter d’autres types d’ActiveX ?**  
  Oui. Remplacez `Forms2OleControlType.CommandButton` par n’importe quelle valeur de l’énumération `Forms2OleControlType` (par ex., `CheckBox`, `OptionButton`). Le même modèle d’insertion s’applique.

- **Et si j’ai besoin d’un type de graphique différent ?**  
  Utilisez `ChartType.Bar`, `ChartType.Line`, etc., dans l’appel `InsertChart`. L’étape **comment insérer un graphique** reste identique ; seule la valeur de l’énumération change.

- **Comment contrôler la taille de la tranche éclatée ?**  
  Aspose.Words prend actuellement en charge un indicateur binaire d’éclatement (true/false). Pour un contrôle plus fin (par ex., distance de décalage), vous devrez modifier le OOXML sous‑jacent après l’enregistrement.

- **Le document est‑il compatible avec les anciennes versions de Word ?**  
  Enregistrer au format DOCX assure la compatibilité avec Word 2007 et versions ultérieures. Pour Word 2003, vous pourriez changer `SaveFormat.Doc`, mais la prise en charge d’ActiveX est limitée dans ce format.

- **Dois‑je référencer `System.Drawing` ?**  
  Non. Tous les objets de dessin sont fournis par Aspose.Words, ainsi le seul package NuGet requis est `Aspose.Words`.

## Conclusion

Vous savez maintenant **comment ajouter ActiveX**, **insérer un diagramme circulaire**, **éclater une tranche de diagramme**, et **enregistrer au format DOCX** en utilisant Aspose.Words pour .NET. L’exemple complet couvre chaque étape, de la création du document à la persistance finale, et explique la logique derrière chaque appel d’API.

Ensuite, vous pourriez explorer :

* Ajouter des macros VBA qui répondent au clic du CommandButton (**comment insérer un graphique** et automatiser les mises à jour de données)
* Personnaliser l’apparence du graphique (couleurs, étiquettes de données) pour correspondre à l’image de marque de l’entreprise
* Intégrer des contrôles ActiveX supplémentaires tels que **ComboBox** ou **ListBox** pour des formulaires plus riches

N’hésitez pas à expérimenter avec le code, à remplacer les données d’exemple, et à intégrer la solution dans vos propres pipelines de génération de documents. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités d’API supplémentaires et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert a Simple Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Insert a Bubble Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}