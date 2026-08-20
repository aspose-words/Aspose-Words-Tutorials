---
category: general
date: 2026-08-20
description: Ajoutez rapidement des lignes de repère à un diagramme circulaire en
  Java. Apprenez à insérer, éclater, recolorer et étiqueter les parts à l'aide de
  l'API Chart.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add leader lines to pie chart
- pie chart explosion Java
- set sector color Chart API
- builder.insertChart usage
- ChartType.PIE example
language: fr
lastmod: 2026-08-20
og_description: Ajoutez des lignes de repère à un camembert en Java avec un exemple
  concis. Suivez ce guide pour insérer, éclater, recolorer et étiqueter les parts
  à l'aide de l'API Chart.
og_image_alt: Screenshot showing a pie chart with an exploded slice and leader lines
  – add leader lines to pie chart
og_title: Ajouter des lignes de repère au diagramme circulaire en Java – guide pas
  à pas de l'API Chart
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Add leader lines to pie chart in Java quickly. Learn to insert, explode,
    recolor, and label slices using the Chart API.
  headline: How to add leader lines to pie chart in Java with the Chart API
  type: TechArticle
tags:
- pie chart
- Java
- Chart API
- data visualization
title: Comment ajouter des lignes de repère à un diagramme circulaire en Java avec
  l'API Chart
url: /fr/java/using-document-elements/how-to-add-leader-lines-to-pie-chart-in-java-with-the-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment ajouter des lignes de repère à un diagramme circulaire en Java avec l'API Chart

Si vous devez **ajouter des lignes de repère à un diagramme circulaire** en Java, ce guide vous accompagne à travers le processus complet. Vous verrez comment insérer un diagramme circulaire, exploser une tranche pour la mettre en évidence, changer sa couleur, et enfin activer les lignes de repère qui étiquettent le segment explosé.

L'exemple utilise l'API Chart standard que l'on trouve dans de nombreuses bibliothèques de reporting Java. Aucun outil externe n'est requis, et le code s'exécute sur n'importe quel environnement JDK 8+.

## Ce que vous allez accomplir

* Créer un `Chart` de type `ChartType.PIE` avec une taille personnalisée.  
* Exploser la première tranche pour attirer l'attention.  
* Définir la couleur du secteur de la tranche explosée en bleu.  
* **Ajouter des lignes de repère à un diagramme circulaire** afin que l'étiquette de la tranche soit clairement reliée.

Vous devez déjà disposer d'un projet Java avec la bibliothèque Chart dans le classpath. Si vous utilisez Maven, ajoutez la dépendance indiquée dans la section prérequis.

## Prérequis

* JDK 8 ou version supérieure installé.  
* La bibliothèque Chart (par ex., `com.example.chart:chart-api:2.5.0`).  
* Familiarité de base avec les classes Java et les appels de méthodes.

---

## Comment ajouter des lignes de repère à un diagramme circulaire

Ci-dessous se trouve un programme complet et exécutable qui démontre chaque étape. Le code est délibérément autonome afin que vous puissiez le copier, le coller et l'exécuter sans modifications.

```java
// File: AddLeaderLinesDemo.java
import com.example.chart.Chart;
import com.example.chart.ChartBuilder;
import com.example.chart.ChartType;
import com.example.chart.Color;

/**
 * Demonstrates adding leader lines to a pie chart in Java.
 */
public class AddLeaderLinesDemo {

    public static void main(String[] args) {
        // 1️⃣ Insert a pie chart with the desired size
        ChartBuilder builder = new ChartBuilder();
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // 2️⃣ Pull out the first slice for emphasis (explosion)
        chart.getSeries().get(0).setExplosion(20);

        // 3️⃣ Change the color of the first slice to blue
        chart.getSeries().get(0).setSectorColor(Color.BLUE);

        // 4️⃣ Show leader lines for the exploded slice
        chart.setLeaderLines(true);

        // Optional: Save the chart as an image file
        chart.saveAsPng("pie-with-leader-lines.png");
        System.out.println("Chart saved to pie-with-leader-lines.png");
    }
}
```

### Explication de chaque étape

| Étape | Ce que fait le code | Pourquoi c’est important |
|------|-------------------|----------------|
| **1️⃣ Insérer un diagramme circulaire** | `builder.insertChart(ChartType.PIE, 400, 300)` crée un diagramme circulaire de 400 × 300 pixels. | Établit le conteneur du diagramme et définit ses dimensions, ce qui influence le placement des étiquettes et la longueur des lignes de repère. |
| **2️⃣ Exploser la première tranche** | `setExplosion(20)` décale la tranche de 20 % du rayon. | Une tranche explosée attire l'attention du lecteur et rend la ligne de repère visible. |
| **3️⃣ Définir la couleur du secteur** | `setSectorColor(Color.BLUE)` change le remplissage de la tranche en bleu. | Le contraste de couleur améliore la lisibilité, surtout lorsque la tranche est mise en évidence. |
| **4️⃣ Activer les lignes de repère** | `setLeaderLines(true)` active les lignes de connexion qui relient la tranche à son étiquette. | Les lignes de repère garantissent que l'étiquette reste lisible même lorsque la tranche est déplacée vers l'extérieur. |

L'appel `saveAsPng` est optionnel mais utile pour vérifier le résultat visuel. Après l'exécution du programme, vous devriez voir une image similaire à celle ci-dessous.

![Ajouter des lignes de repère à un diagramme circulaire](https://example.com/assets/pie-leader-lines.png "Ajouter des lignes de repère à un diagramme circulaire – tranche explosée avec couleur bleue et lignes de repère")

*Figure : Un diagramme circulaire où la première tranche est explosée, colorée en bleu, et reliée à son étiquette par une ligne de repère.*

## Personnalisation des lignes de repère (avancé)

L'appel de base `setLeaderLines(true)` utilise le style par défaut de la bibliothèque. Vous pouvez contrôler davantage l'apparence :

```java
// Change leader line color to dark gray
chart.setLeaderLineColor(Color.DARK_GRAY);

// Increase line thickness for better visibility
chart.setLeaderLineWidth(2);

// Position labels outside the chart area
chart.setLabelPlacement(Chart.LabelPlacement.OUTSIDE);
```

Ces options sont pratiques lorsque vous devez correspondre à l'identité visuelle de l'entreprise ou améliorer l'accessibilité.

### Gestion de plusieurs séries

Si votre diagramme circulaire contient plus d'une série, vous pouvez ne vouloir des lignes de repère que pour une tranche spécifique. Utilisez l'index de la série pour cibler le bon élément :

```java
// Enable leader lines only for the second series, third slice
chart.getSeries().get(1).get(2).setExplosion(15);
chart.getSeries().get(1).get(2).setLeaderLineEnabled(true);
```

Lorsqu'une tranche n'est pas explosée, la ligne de repère est généralement masquée automatiquement, mais vous pouvez la forcer avec `setLeaderLineEnabled(true)`.

## Pièges courants et comment les éviter

| Piège | Symptom | Solution |
|--------|---------|-----|
| **Lignes de repère non visibles** | Le diagramme s'affiche sans connecteurs. | Assurez-vous que la tranche est explosée (`setExplosion` > 0) ou activez explicitement les lignes de repère sur la tranche. |
| **Chevauchement des étiquettes** | Les étiquettes se chevauchent. | Augmentez la taille du diagramme ou définissez `setLabelPlacement(Chart.LabelPlacement.OUTSIDE)`. |
| **Couleur non appliquée** | La tranche conserve la couleur par défaut. | Vérifiez que vous ciblez le bon index de série (`getSeries().get(0)`). |
| **Image non enregistrée** | `saveAsPng` lève une exception. | Vérifiez les permissions d'écriture du répertoire de sortie et que la bibliothèque prend en charge l'export PNG. |

Résoudre ces problèmes dès le départ évite les surprises à l'exécution et produit un diagramme soigné.

## Listing complet du code source

Pour plus de commodité, voici à nouveau le fichier source complet, incluant les imports et les commentaires :

```java
// AddLeaderLinesDemo.java
import com.example.chart.Chart;
import com.example.chart.ChartBuilder;
import com.example.chart.ChartType;
import com.example.chart.Color;

/**
 * Complete example that adds leader lines to a pie chart.
 */
public class AddLeaderLinesDemo {

    public static void main(String[] args) {
        // Create a builder and insert a 400×300 pie chart
        ChartBuilder builder = new ChartBuilder();
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // Explode the first slice (20% offset) and color it blue
        chart.getSeries().get(0).setExplosion(20);
        chart.getSeries().get(0).setSectorColor(Color.BLUE);

        // Turn on leader lines for the exploded slice
        chart.setLeaderLines(true);

        // Optional styling
        chart.setLeaderLineColor(Color.DARK_GRAY);
        chart.setLeaderLineWidth(2);
        chart.setLabelPlacement(Chart.LabelPlacement.OUTSIDE);

        // Export the chart as a PNG image
        chart.saveAsPng("pie-with-leader-lines.png");
        System.out.println("Chart generated successfully.");
    }
}
```

L'exécution de ce programme génère `pie-with-leader-lines.png`, qui affiche un diagramme circulaire avec une tranche bleue explosée et des lignes de repère claires pointant vers l'étiquette de la tranche.

## Conclusion

Vous savez maintenant comment **ajouter des lignes de repère à un diagramme circulaire** en Java en utilisant l'API Chart. Le processus consiste à insérer un `ChartType.PIE`, exploser la tranche souhaitée, personnaliser sa couleur, et activer les lignes de repère. Avec les options de style optionnelles, vous pouvez affiner la couleur, l'épaisseur des lignes et le placement des étiquettes pour répondre à n'importe quel besoin visuel.

Ensuite, envisagez d'explorer des sujets connexes tels que **pie chart explosion Java**, **set sector color Chart API**, et **builder.insertChart usage** pour créer des visualisations plus sophistiquées comme des diagrammes en anneau, des diagrammes circulaires empilés, ou des tableaux de bord interactifs.

N'hésitez pas à expérimenter avec différents indices de tranche, couleurs et styles de lignes de repère — vos diagrammes deviendront plus informatifs et visuellement attrayants à chaque ajustement. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l'API et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Comment créer un diagramme en colonnes avec Aspose.Words pour Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Ajouter des valeurs de date et d'heure à l'axe d'un diagramme](/words/english/net/programming-with-charts/date-time-values-to-axis/)
- [Insérer un diagramme en colonnes dans Word avec Aspose.Words pour .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}