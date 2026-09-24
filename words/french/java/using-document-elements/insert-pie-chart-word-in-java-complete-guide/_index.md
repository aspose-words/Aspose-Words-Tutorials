---
category: general
date: 2026-09-24
description: Insérez un diagramme circulaire Word dans un DOCX à l'aide d'Aspose.Words
  for Java. Apprenez à définir la taille du trou, à éclater une tranche du diagramme,
  à mettre en surbrillance une tranche du diagramme circulaire et à créer un graphique
  DOCX sans effort.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart word
- set hole size
- explode pie slice
- highlight pie chart slice
- create docx chart
language: fr
lastmod: 2026-09-24
og_description: Insérez un diagramme circulaire Word dans un DOCX avec Aspose.Words
  for Java. Maîtrisez la définition de la taille du trou, l'explosion d'une tranche
  du diagramme, la mise en évidence d'une tranche, et créez un graphique DOCX en quelques
  minutes.
og_image_alt: Screenshot of a Word document displaying a formatted pie chart created
  with Java
og_title: Insérer le mot diagramme circulaire en Java – tutoriel étape par étape
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Insert pie chart word in a DOCX using Aspose.Words for Java. Learn
    to set hole size, explode pie slice, highlight pie chart slice, and create docx
    chart effortlessly.
  headline: Insert pie chart word in Java – complete guide
  type: TechArticle
- description: Insert pie chart word in a DOCX using Aspose.Words for Java. Learn
    to set hole size, explode pie slice, highlight pie chart slice, and create docx
    chart effortlessly.
  name: Insert pie chart word in Java – complete guide
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well) * Aspose.Words
      for Java library (version 23.9 or newer) * An IDE or build tool (Maven/Gradle)
      that can resolve the Aspose.Words dependency'
  - name: Why this matters
    text: '`Document` represents the whole Word file, while `DocumentBuilder` is the
      high‑level API that lets you insert paragraphs, tables, and charts without dealing
      with low‑level XML. Starting with a clean document ensures that the chart you
      add is the only content, which is perfect for learning or for gen'
  - name: Practical tip
    text: If you later decide to switch to a doughnut chart, simply change the `holeSize`
      value to a percentage (e.g., `30`). The same API works for both chart types.
  - name: Why explode?
    text: An exploded slice draws the reader’s eye to the most important data point—perfect
      for dashboards or executive summaries. The value `20` means 20 % of the radius;
      you can adjust it between `0` (no explosion) and `100` (fully detached).
  - name: Expert note
    text: Changing the fill color of a specific slice requires accessing the `DataPoint`
      object. If you have multiple series, iterate through `series.getDataPoints()`
      and apply styles conditionally.
  - name: Pro tip
    text: Always call `setHoleSize(0)` **after** `insertChart`. If you set it before
      insertion, Aspose.Words will revert to the default doughnut size once the chart
      is created.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart formatting
title: Insérer un diagramme circulaire en Java – guide complet
url: /fr/java/using-document-elements/insert-pie-chart-word-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insérer un diagramme circulaire Word en Java – guide complet

Si vous devez **insérer un diagramme circulaire Word** dans un fichier DOCX, ce tutoriel vous montre exactement comment le faire avec Aspose.Words for Java. Vous verrez le flux complet, de la création du document à la personnalisation du graphique afin que la part soit éclatée, la taille du trou soit réglée à zéro et la part soit mise en évidence.

Travailler avec des graphiques dans des documents Word ressemble souvent à une préoccupation distincte du traitement de texte ordinaire, mais Aspose.Words unifie les deux. Dans les étapes ci‑dessous, vous apprendrez également comment **créer un diagramme docx** prêt à être ouvert dans Microsoft Word, Google Docs ou tout autre visualiseur compatible DOCX.

## Ce que vous allez réaliser

* **Insérer un diagramme circulaire Word** dans un document vierge  
* **Définir la taille du trou** pour transformer le graphique en un cercle complet (pas de beignet)  
* **Éclater une part du diagramme** pour attirer l’attention sur une section spécifique  
* **Mettre en évidence une part du diagramme circulaire** avec un formatage personnalisé  
* **Créer un diagramme docx** qui peut être partagé ou édité davantage  

### Prérequis

* Java 17 ou version ultérieure (le code compile également avec Java 8)  
* Bibliothèque Aspose.Words for Java (version 23.9 ou plus récente)  
* Un IDE ou un outil de construction (Maven/Gradle) capable de résoudre la dépendance Aspose.Words  

```xml
<!-- Example Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

---

## Comment insérer un diagramme circulaire Word dans un DOCX avec Aspose.Words

La première étape consiste à créer un nouveau document vierge et à obtenir un `DocumentBuilder`. Le builder vous donne un accès direct au flux de contenu du document, ce qui rend trivial **l’insertion d’un diagramme circulaire Word**.

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

### Pourquoi c’est important
`Document` représente l’ensemble du fichier Word, tandis que `DocumentBuilder` est l’API de haut niveau qui vous permet d’insérer des paragraphes, des tableaux et des graphiques sans manipuler le XML de bas niveau. Commencer avec un document vierge garantit que le graphique que vous ajoutez est le seul contenu, ce qui est parfait pour l’apprentissage ou pour générer des rapports basés sur des modèles.

## Définir la taille du trou pour créer un cercle complet

Par défaut, Aspose.Words crée un graphique en beignet lorsque vous demandez un diagramme circulaire. Pour que le graphique soit un vrai cercle, vous devez **définir la taille du trou** à `0`. Cela supprime le trou intérieur et donne l’apparence classique d’un diagramme circulaire.

```java
        // Step 2: Insert a pie chart with a specific size
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Step 4: Ensure the chart is a full pie (no doughnut hole)
        pieChart.getChart().setHoleSize(0);   // set hole size to zero
```

### Astuce pratique
Si vous décidez plus tard de passer à un graphique en beignet, il suffit de changer la valeur de `holeSize` en pourcentage (par ex., `30`). La même API fonctionne pour les deux types de graphiques.

## Éclater une part du diagramme pour mettre en évidence une section

Éclater une part la fait ressortir visuellement. L’opération **éclater une part du diagramme** déplace la part choisie vers l’extérieur d’un pourcentage du rayon du graphique.

```java
        // Step 3: Explode the first slice to highlight it
        pieChart.getChart().getSeries().get(0).setExplosion(20); // explode pie slice
```

### Pourquoi éclater ?
Une part éclatée attire le regard du lecteur sur le point de données le plus important—idéal pour les tableaux de bord ou les résumés exécutifs. La valeur `20` signifie 20 % du rayon ; vous pouvez l’ajuster entre `0` (pas d’éclatement) et `100` (complètement détachée).

## Mettre en évidence une part du diagramme circulaire avec un formatage personnalisé

Au‑delà de l’éclatement, vous pourriez vouloir **mettre en évidence une part du diagramme circulaire** en changeant sa couleur de remplissage ou sa bordure. Bien que le code de démonstration se concentre sur l’éclatement, vous pouvez l’étendre comme suit :

```java
        // Optional: Change fill color of the exploded slice
        ChartSeries series = pieChart.getChart().getSeries().get(0);
        series.getDataPoints().get(0).getFormat().setFillColor(java.awt.Color.RED);
```

### Note d’expert
Changer la couleur de remplissage d’une part spécifique nécessite d’accéder à l’objet `DataPoint`. Si vous avez plusieurs séries, parcourez `series.getDataPoints()` et appliquez les styles de façon conditionnelle.

## Enregistrer et vérifier le diagramme docx créé

Enfin, vous **créez un diagramme docx** en enregistrant le `Document`. Le fichier résultant peut être ouvert dans Microsoft Word pour voir le diagramme circulaire formaté.

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartFormatted.docx");
    }
}
```

#### Résultat attendu
L’ouverture de `PieChartFormatted.docx` montre un seul diagramme circulaire :

* Le graphique occupe une zone de 400 × 300 pt.  
* La taille du trou est `0`, donc le graphique est un cercle complet.  
* La première part est éclatée de 20 % et colorée en rouge (si vous avez ajouté le formatage optionnel).  

Vous avez maintenant un **diagramme docx** qui peut être distribué, intégré dans des e‑mails ou édité davantage par programme.

---

## Variations courantes et cas limites

| Scénario | Comment adapter le code |
|----------|--------------------------|
| **Séries multiples** | Parcourez `pieChart.getChart().getSeries()` et définissez `Explosion` ou `FillColor` par série. |
| **Données dynamiques** | Remplissez les séries avec des valeurs provenant d’une base de données ou d’un CSV avant d’appeler `setExplosion`. |
| **Taille de graphique différente** | Modifiez les arguments de largeur/hauteur dans `insertChart(ChartType.PIE, width, height)`. |
| **Exportation en PDF** | Après avoir enregistré le DOCX, appelez `doc.save("output.pdf")` pour produire une version PDF du même graphique. |
| **Localisation** | Utilisez `DocumentBuilder.insertChart` avec un format de nombre spécifique à la locale pour les libellés. |

### Astuce pro
Appelez toujours `setHoleSize(0)` **après** `insertChart`. Si vous le définissez avant l’insertion, Aspose.Words reviendra à la taille de beignet par défaut une fois le graphique créé.

---

## Récapitulatif

Vous savez maintenant comment **insérer un diagramme circulaire Word** dans un document Word avec Java, comment **définir la taille du trou** pour obtenir un rendu plein cercle, comment **éclater une part du diagramme** pour attirer l’attention, et comment **mettre en évidence une part du diagramme circulaire** avec des couleurs personnalisées. L’exemple complet montre également comment **créer un diagramme docx** prêt à être distribué.

---

## Prochaines étapes

* Explorez d’autres types de graphiques (`BAR`, `LINE`, `SCATTER`) avec `ChartType`.  
* Combinez la génération de graphiques avec la fusion et publipostage pour produire des rapports personnalisés.  
* Intégrez le DOCX généré dans un service web qui renvoie le fichier à la demande.  

Si vous rencontrez des problèmes, vérifiez que vous utilisez une version compatible d’Aspose.Words et que le répertoire de sortie existe et est accessible en écriture.

Bon codage !

## Que devez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques présentées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser d’autres fonctionnalités de l’API et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Comment créer un diagramme en colonnes avec Aspose.Words pour Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Utilisation de l’API Word Chart](/words/english/net/programming-with-charts/)
- [Insérer un diagramme à bulles dans Word avec Aspose.Words pour .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}