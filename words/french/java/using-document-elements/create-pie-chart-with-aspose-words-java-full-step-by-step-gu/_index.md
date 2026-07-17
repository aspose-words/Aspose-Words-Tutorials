---
category: general
date: 2026-07-16
description: Créer un diagramme circulaire en Java avec Aspose.Words. Apprenez comment
  ajouter des lignes de repère, afficher la légende du graphique et détacher une tranche
  dans un seul tutoriel.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add leader lines
- show chart legend
- how to explode slice
- how to add legend
language: fr
lastmod: 2026-07-16
og_description: Créez un diagramme circulaire en Java avec Aspose.Words. Ce guide
  montre comment ajouter des lignes de repère, afficher la légende du graphique et
  détacher une tranche, vous offrant un visuel soigné en quelques minutes.
og_image_alt: Screenshot of a Java‑generated pie chart with an exploded slice and
  visible legend
og_title: Créer un diagramme circulaire avec Aspose.Words Java – Tutoriel complet
  de mise en forme
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  headline: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  type: TechArticle
- description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  name: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  steps:
  - name: Java 17 (or later) installed.
    text: Java 17 (or later) installed.
  - name: Aspose.Words for Java JAR on your classpath.
    text: Aspose.Words for Java JAR on your classpath.
  - name: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
    text: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart Formatting
- Data Visualization
title: Créer un diagramme circulaire avec Aspose.Words Java – Guide complet étape
  par étape
url: /fr/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un diagramme circulaire avec Aspose.Words Java – Guide complet étape par étape

Vous vous êtes déjà demandé comment **créer un diagramme circulaire** programmatique en Java sans vous battre avec des API de dessin bas‑niveau ? Vous n'êtes pas le seul. De nombreux développeurs ont besoin d'un visuel rapide pour des rapports, tableaux de bord ou documents automatisés, et ils se tournent vers Aspose.Words car il gère le gros du travail.  

Dans ce tutoriel, nous parcourrons un exemple complet, prêt à l'exécution, qui non seulement **crée un diagramme circulaire**, mais vous montre également comment **ajouter des lignes de repère**, **afficher la légende du graphique**, et même **exploser une tranche** pour la mettre en évidence. À la fin, vous disposerez d'un fichier `.docx` qui a l'air suffisamment soigné pour impressionner un client.

> **Gain rapide :** Le fragment de code ci‑dessous fonctionne immédiatement avec Aspose.Words for Java 23.9 (ou toute version plus récente). Aucune dépendance supplémentaire, juste le JAR.

## Ce que vous apprendrez

- Configurer un document Word vierge avec `DocumentBuilder`.
- Insérer un **diagramme circulaire** de taille personnalisée.
- Utiliser la fonctionnalité **exploser une tranche** pour mettre en évidence un point de données.
- Activer les **lignes de repère** afin que la tranche explosée reste connectée à l'étiquette.
- Activer la **légende du graphique** pour que les lecteurs puissent identifier instantanément chaque tranche.
- Enregistrer le résultat dans un fichier `.docx` que vous pouvez ouvrir avec Microsoft Word ou LibreOffice.

**Prérequis** – Vous aurez besoin de :

1. Java 17 (ou ultérieur) installé.
2. JAR Aspose.Words for Java dans votre classpath.
3. Un IDE ou éditeur de texte basique — IntelliJ IDEA, Eclipse, VS Code, ou tout autre que vous préférez.

Maintenant, plongeons‑dans le vif du sujet.

## Étape 1 : Initialiser le Document et le Builder – Préparer la **création du diagramme circulaire**

Tout d'abord, nous avons besoin d'une toile de document vierge. `Document` représente l'ensemble du fichier Word, tandis que `DocumentBuilder` est l'assistant qui nous permet d'ajouter du contenu.

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();               // the container for our Word file
        DocumentBuilder builder = new DocumentBuilder(doc); // convenient API for adding elements
```

> **Pourquoi c'est important :** Commencer avec un `Document` vierge garantit l'absence de styles cachés ou d'objets résiduels qui pourraient interférer avec le rendu du graphique.

## Étape 2 : Insérer le **diagramme circulaire** – La taille compte

Aspose.Words rend l'insertion d'un graphique en une seule ligne. Ici, nous demandons un diagramme circulaire de 400 × 300 points — soit environ 5,5 × 4,2 pouces sur un écran typique.

```java
        // Step 2: Insert a pie chart of size 400x300 points
        Shape chartShape = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = chartShape.getChart(); // the underlying chart object we will format
```

> **Astuce pro :** Si vous avez besoin d'une taille différente, modifiez simplement les deux arguments numériques. L'API fonctionne en points, où 72 points = 1 pouce.

## Étape 3 : **Comment exploser une tranche** – Mettre en évidence un point de données clé

Explooser une tranche la fait sortir du reste du diagramme, attirant l'œil du lecteur. La méthode `setExplosion` prend un entier représentant la distance en points.

```java
        // Step 3: Explode the first slice to emphasize it
        chart.getSeries().get(0).setExplosion(10); // 10 points outward
```

> **Et si vous avez plusieurs séries ?** Vous pouvez appeler `setExplosion` sur n'importe quel indice de série (`get(1)`, `get(2)`, …) pour exploser différentes tranches.

## Étape 4 : **Ajouter des lignes de repère** et **afficher la légende du graphique** – Relier les points

Lorsqu'une tranche est explosée, l'étiquette peut s'éloigner. Les lignes de repère maintiennent l'étiquette attachée, préservant la lisibilité. En même temps, une légende offre une clé rapide pour toutes les tranches.

```java
        // Step 4: Enable leader lines for the exploded slice and show the legend
        chart.getSeries().get(0).setLeaderLines(true); // draws a line from slice to its label
        chart.setShowLegend(true);                     // makes the legend visible below the chart
```

> **Pourquoi activer les lignes de repère ?** Sans elles, l'étiquette peut sembler flotter, ce qui confond les utilisateurs quant à la tranche à laquelle elle appartient.  
> **Besoin d'une position personnalisée pour la légende ?** Utilisez `chart.getLegend().setPosition(LegendPosition.TOP)` ou toute autre valeur d'énumération.

## Étape 5 : Enregistrer le Document – L'étape finale de **création du diagramme circulaire**

Enfin, nous persistons le document sur le disque. Ajustez le chemin vers un dossier où vous avez les droits d'écriture.

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartDemo.docx");
    }
}
```

Exécutez le programme, ouvrez le `PieChartDemo.docx` généré, et vous devriez voir un diagramme circulaire bien formaté avec la première tranche explosée, des lignes de repère et une légende visible.

![Exemple de diagramme circulaire montrant une tranche explosée et la légende](pie-chart-example.png){: .center-image alt="Exemple de création de diagramme circulaire avec tranche explosée, lignes de repère et légende"}

### Résultat attendu

Lorsque vous ouvrez le fichier Word, le graphique ressemble approximativement à ceci :

- Un diagramme circulaire de 400 × 300 pt.
- La première tranche est décalée de 10 pt.
- Une fine ligne de repère relie la tranche explosée à son étiquette.
- Une légende sous le graphique répertorie le nom de chaque série.

Si vous ne voyez pas la ligne de repère, vérifiez que `setLeaderLines(true)` est appelé *après* le réglage d'explosion — l'ordre compte.

## Pièges courants et comment les éviter

| Problème | Pourquoi cela se produit | Solution |
|----------|--------------------------|----------|
| **Aucune légende n'apparaît** | `setShowLegend(true)` a été omis ou appelé sur le mauvais objet graphique. | Assurez‑vous d'appeler `chart.setShowLegend(true)` **après** avoir récupéré le `Chart` depuis la forme. |
| **Ligne de repère manquante** | La tranche n'a pas été explosée, ou le type de graphique ne prend pas en charge les lignes de repère. | Seuls `ChartType.PIE` (ou `PIE_3D`) prennent en charge les lignes de repère. Appelez d'abord `setExplosion`, puis `setLeaderLines(true)`. |
| **La tranche ne bouge pas** | Valeur d'explosion trop faible (0‑2 pt). | Augmentez l'entier, par ex., `setExplosion(10)` ou plus pour un effet plus spectaculaire. |
| **Le graphique apparaît déformé** | Utiliser une taille non carrée (largeur ≠ hauteur) peut écraser le diagramme. | Gardez la largeur et la hauteur égales ou proches ; 400 × 300 fonctionne mais 400 × 400 donne un cercle parfait. |

## Ajustements avancés (optionnel)

Si vous souhaitez aller au-delà des bases, envisagez :

- **Couleurs personnalisées** : `chart.getSeries().get(0).getDataPoints().get(i).getFormat().getFill().setForeColor(Color.RED);`
- **Étiquettes de données** : `chart.getSeries().get(0).setDataLabelType(ChartDataLabelType.CATEGORY);`
- **Effet 3‑D** : Remplacez `ChartType.PIE` par `ChartType.PIE_3D`.

Ces options vous permettent d'ajuster finement le visuel pour correspondre aux directives de marque de l'entreprise.

## Récapitulatif – Ce que nous avons accompli

Nous avons commencé avec un document Word vierge, **créé un diagramme circulaire**, **explosé la première tranche**, **ajouté des lignes de repère**, et **affiché la légende du graphique**. L'ensemble du flux tient dans une méthode `main` concise, ce qui facilite son intégration dans des pipelines de reporting plus larges.

## Prochaines étapes

- **Ajouter plus de séries** : Remplir le graphique avec des données réelles provenant d'une base de données ou d'un CSV.
- **Exporter en PDF** : Utilisez `doc.save("output.pdf", SaveFormat.PDF);` pour générer une version PDF.
- **Combiner avec d'autres formes** : Insérez des tableaux, images ou graphiques supplémentaires pour un rapport complet.

Si vous êtes curieux des autres types de graphiques — colonne, barre, ligne — remplacez simplement `ChartType.PIE` par l'énumération appropriée et suivez les mêmes étapes de formatage.

---

*Bon graphique !* N'hésitez pas à laisser un commentaire si quelque chose n'a pas fonctionné comme prévu, ou à partager comment vous avez personnalisé la position de la légende. Vos retours nous aident tous à créer de meilleurs documents automatisés.

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Comment créer un graphique en colonnes avec Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Comment créer des documents PDF avec Aspose.Words for Java | Document Processing API](/words/english/java/)
- [Comment ajouter un filigrane aux documents avec Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}