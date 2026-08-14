---
category: general
date: 2026-08-14
description: Créez un graphique circulaire dans Word avec Java en utilisant Aspose.Words.
  Apprenez à ajouter des données de série au graphique et à faire pivoter une tranche
  du graphique circulaire en quelques lignes seulement.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart in word
- how to add series data to chart
- rotate pie chart slice
- Aspose.Words chart API
- Java document automation
language: fr
lastmod: 2026-08-14
og_description: Créer un diagramme circulaire dans Word avec Java en utilisant Aspose.Words.
  Ce tutoriel montre comment ajouter des données de série au diagramme et faire pivoter
  rapidement une tranche du diagramme circulaire.
og_image_alt: Screenshot of a Word document containing a colorful pie chart generated
  by Java code
og_title: Créer un diagramme circulaire dans Word avec Java – guide complet de codage
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  headline: Create pie chart in Word with Java – step-by-step guide
  type: TechArticle
- description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  name: Create pie chart in Word with Java – step-by-step guide
  steps:
  - name: Why use Aspose.Words?
    text: '* **No Microsoft Office required** – the library works on any server or
      CI environment. * **Full .docx fidelity** – the generated chart looks identical
      to one created manually in Word. * **Single‑file dependency** – just add the
      JAR and you’re ready to go.'
  - name: Expected output
    text: '* A file named **PieChart.docx** appears in the `output` folder. * Opening
      the file in Microsoft Word shows a colorful pie chart with three slices (40
      %, 30 %, 30 %). * The chart is rotated 45° clockwise, so the first slice starts
      slightly to the right of the vertical axis.'
  - name: Tips for production use
    text: '* **Reuse the `DocumentBuilder`** – you can insert multiple charts in the
      same document by calling `insertChart` repeatedly. * **Styling** – use `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);`
      to display percentages directly on the chart. * **Performance** – generate the
      chart on'
  - name: What’s next?
    text: '* Explore other chart types (`ChartType.BAR`, `ChartType.LINE`) to broaden
      your automation toolkit. * Combine chart generation with **mail merge** to produce
      personalized reports for each recipient. * Dive into the **Styling API** (`ChartFormat`,
      `DataLabel`, `ChartTitle`) to match your corporate br'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Créer un diagramme circulaire dans Word avec Java – guide étape par étape
url: /fr/java/using-document-elements/create-pie-chart-in-word-with-java-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un diagramme circulaire dans Word avec Java – guide étape par étape

Si vous devez **créer un diagramme circulaire dans Word** de façon programmatique, ce guide vous montre exactement comment le faire avec Java et Aspose.Words. Vous apprendrez le flux de travail complet, de l’insertion du diagramme à l’ajout de points de données et à la rotation de la première tranche.

Générer un diagramme directement dans un fichier `.docx` supprime l’étape manuelle de copier‑coller et vous permet d’automatiser des rapports, factures ou tableaux de bord. En cours de route, nous aborderons également **comment ajouter des données de série au diagramme** et comment **faire pivoter une tranche du diagramme circulaire** pour une meilleure mise en valeur visuelle.

## Créer un diagramme circulaire dans Word – aperçu

Aspose.Words for Java fournit une API fluide `DocumentBuilder` qui peut insérer un objet diagramme dans un document Word. Le type de diagramme que vous choisissez détermine la mise en page par défaut, et vous pouvez personnaliser les séries, les couleurs, les angles, et même passer à une forme de beignet avec un seul appel de méthode.

### Pourquoi utiliser Aspose.Words ?

* **Pas besoin de Microsoft Office** – la bibliothèque fonctionne sur n’importe quel serveur ou environnement CI.  
* **Fidélité totale du .docx** – le diagramme généré ressemble exactement à celui créé manuellement dans Word.  
* **Dépendance à un seul fichier** – ajoutez simplement le JAR et vous êtes prêt à démarrer.

## Comment ajouter des données de série au diagramme

Un diagramme sans données n’est qu’un espace réservé. L’objet `Chart` expose une collection `Series` ; chaque série contient une liste de valeurs numériques qui correspondent aux tranches (pour un diagramme circulaire) ou aux points (pour une ligne). Ajouter des données est simple :

```java
// Add three values to the first (and only) series of the pie chart
chart.getSeries().get(0).add(40); // 40 % of the whole
chart.getSeries().get(0).add(30); // 30 %
chart.getSeries().get(0).add(30); // remaining 30 %
```

**Ce que fait le code :**  
* `chart.getSeries()` renvoie une `List<ChartSeries>`.  
* `get(0)` sélectionne la première série car un diagramme circulaire ne contient, par définition, qu’une seule série.  
* `add(double)` ajoute un point de donnée. Les valeurs sont automatiquement converties en pourcentages qui totalisent 100 % lors du rendu du diagramme.

> **Astuce :** Si votre source de données contient plus de trois catégories, continuez à ajouter des valeurs de la même façon. Aspose.Words créera automatiquement des tranches supplémentaires.

## Faire pivoter une tranche du diagramme circulaire

Parfois, vous voulez qu’une tranche particulière commence à un angle spécifique afin que le segment le plus important fasse face au lecteur. La méthode `setFirstSliceAngle(double)` fait pivoter l’ensemble du diagramme, déplaçant ainsi le départ de la première tranche :

```java
// Rotate the chart so that the first slice starts at 45 degrees
chart.setFirstSliceAngle(45);
```

L’angle est mesuré en degrés dans le sens des aiguilles d’une montre à partir de l’axe vertical. Le régler à `0` (valeur par défaut) place la première tranche en haut. Ajustez la valeur pour mettre en avant une tranche ou pour respecter une directive de conception.

> **Question fréquente :** *La rotation affecte‑t‑elle l’ordre des données ?*  
> Non. L’ordre des données reste le même ; seule la position de départ visuelle change.

## Exemple complet en Java

Voici un programme complet, prêt à être exécuté, qui crée un document Word avec un diagramme circulaire, ajoute des données de série, fait pivoter la tranche, puis enregistre le fichier. Toutes les importations nécessaires sont listées, vous pouvez donc copier le code dans n’importe quel IDE.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartInWord {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a PIE chart with a width of 400 points and a height of 300 points
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Add data points to the first (and only) series
        chart.getSeries().get(0).add(40); // Slice 1
        chart.getSeries().get(0).add(30); // Slice 2
        chart.getSeries().get(0).add(30); // Slice 3

        // 4️⃣ Rotate the start angle so the first slice begins at 45°
        chart.setFirstSliceAngle(45);

        // 5️⃣ (Optional) If you prefer a doughnut chart, uncomment the next line
        // chart.setHoleSize(0.5); // hole size between 0.0 (pie) and 1.0 (empty)

        // 6️⃣ Save the document – adjust the path as needed
        String outPath = "output/PieChart.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### Résultat attendu

* Un fichier nommé **PieChart.docx** apparaît dans le dossier `output`.  
* L’ouverture du fichier dans Microsoft Word montre un diagramme circulaire coloré avec trois tranches (40 %, 30 %, 30 %).  
* Le diagramme est pivoté de 45° dans le sens des aiguilles d’une montre, de sorte que la première tranche débute légèrement à droite de l’axe vertical.

## Pièges courants et bonnes pratiques

| Problème | Pourquoi cela se produit | Solution |
|----------|--------------------------|----------|
| **Le diagramme apparaît vide** | Le document a été enregistré avant que le diagramme ne soit complètement rendu. | Appelez `doc.save()` **après** toutes les modifications du diagramme. |
| **Les valeurs des tranches ne totalisent pas 100 %** | Ajouter des nombres bruts qui ne représentent pas des pourcentages peut entraîner un redimensionnement inattendu. | Fournissez des valeurs qui représentent logiquement des parties d’un tout, ou laissez Aspose.Words calculer automatiquement les pourcentages. |
| **La rotation n’a aucun effet** | Utiliser `ChartType.DOUGHNUT` sans définir `holeSize` peut masquer l’effet de rotation. | Conservez le diagramme en `PIE` ou ajustez `holeSize` après avoir défini l’angle. |
| **Erreurs de chemin de fichier** | Les chemins relatifs peuvent être résolus différemment sous Windows vs. Linux. | Utilisez `Paths.get("output", "PieChart.docx").toString()` ou un chemin absolu pour le code de production. |

### Conseils pour la production

* **Réutilisez le `DocumentBuilder`** – vous pouvez insérer plusieurs diagrammes dans le même document en appelant `insertChart` de façon répétée.  
* **Style** – utilisez `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);` pour afficher les pourcentages directement sur le diagramme.  
* **Performance** – générez le diagramme une fois et clonez‑le (`chart.deepClone()`) si vous avez besoin de diagrammes identiques à plusieurs endroits.

## Faire pivoter une tranche du diagramme circulaire – scénarios avancés

* **Angle dynamique** – calculez l’angle en fonction des données (par ex., faites commencer la plus grande tranche en haut).  
  ```java
  double maxValue = Collections.max(chart.getSeries().get(0).getDataPoints());
  double total = chart.getSeries().get(0).getDataPoints().stream().mapToDouble(Double::doubleValue).sum();
  double startAngle = 360 * (maxValue / total) / 2; // Center the largest slice
  chart.setFirstSliceAngle(startAngle);
  ```
* **Séries multiples** – bien qu’un diagramme circulaire possède normalement une seule série, Aspose.Words vous permet d’en ajouter d’autres pour des diagrammes circulaires empilés. La rotation s’applique toujours uniquement à la première série.

## Conclusion

Vous savez maintenant comment **créer un diagramme circulaire dans Word** avec Java, comment **ajouter des données de série au diagramme**, et comment **faire pivoter une tranche du diagramme circulaire** pour une mise en avant visuelle. L’exemple complet montre l’ensemble du flux de travail – de l’initialisation du document à l’enregistrement du fichier `.docx` final – afin que vous puissiez intégrer la génération de diagrammes dans n’importe quel pipeline de reporting automatisé.

### Et après ?

* Explorez d’autres types de diagrammes (`ChartType.BAR`, `ChartType.LINE`) pour élargir votre boîte à outils d’automatisation.  
* Combinez la génération de diagrammes avec **mail merge** pour produire des rapports personnalisés pour chaque destinataire.  
* Plongez dans l’**API de style** (`ChartFormat`, `DataLabel`, `ChartTitle`) pour harmoniser vos graphiques avec l’identité visuelle de votre entreprise.

N’hésitez pas à expérimenter avec différents jeux de données, angles et styles de diagrammes. Bon codage !

## Que devez‑vous apprendre ensuite ?


Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Convert Word to PDF Using Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}