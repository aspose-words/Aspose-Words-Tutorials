---
category: general
date: 2026-10-26
description: Créez un diagramme en anneau et insérez un diagramme circulaire en Java
  avec un code étape par étape. Apprenez le flux de travail complet pour des visualisations
  de graphiques flexibles.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create doughnut chart
- insert pie chart
- Java chart library
- chart customization Java
- data visualization Java
language: fr
lastmod: 2026-10-26
og_description: Créez un diagramme en anneau en Java avec ce guide qui montre également
  comment insérer un diagramme circulaire pour des visualisations flexibles.
og_image_alt: Java code snippet creating a doughnut chart and inserting a pie chart
og_title: Créer un diagramme en anneau et insérer un diagramme circulaire – Guide
  Java
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Create doughnut chart and insert pie chart in Java with step‑by‑step
    code. Learn the full workflow for flexible chart visualizations.
  headline: How to create a doughnut chart and insert a pie chart
  type: TechArticle
tags:
- chart
- Java
- data‑visualization
title: Comment créer un graphique en anneau et insérer un graphique circulaire
url: /fr/java/images-shapes/how-to-create-a-doughnut-chart-and-insert-a-pie-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer un doughnut chart et insérer un pie chart

Si vous avez besoin de **create doughnut chart** en Java, ce tutoriel vous guide à travers les étapes exactes. Nous montrerons également comment **insert pie chart** en utilisant la même API de constructeur, afin que vous puissiez passer d'un style visuel à l'autre sans effort. À la fin du guide, vous disposerez d'un programme complet et exécutable qui génère les deux types de graphiques et démontre les personnalisations courantes.

Le tutoriel couvre :

* L'initialisation du constructeur de graphique fourni par la bibliothèque choisie.  
* La création d'un doughnut chart et la configuration de la taille du trou.  
* L'insertion d'un pie chart et l'explosion d'une tranche pour la mettre en évidence.  
* Des astuces pour gérer les cas limites tels que des séries manquantes ou des types de graphiques non pris en charge.

Vous avez seulement besoin d'un JDK récent (8 ou supérieur) et du JAR de la bibliothèque de graphiques dans votre classpath. Aucun service externe n'est requis.

---

## Prérequis

| Élément | Raison |
|------|--------|
| Java Development Kit (JDK) 8+ | Nécessaire pour compiler et exécuter l'exemple. |
| Chart library (e.g., **Aspose.Cells for Java** or **JFreeChart**) | Fournit `ChartBuilder`, `ChartType` et les méthodes de manipulation de séries utilisées dans le code. |
| An IDE or a text editor | Un IDE ou un éditeur de texte pour écrire et exécuter le fichier source Java. |

Assurez‑vous que le JAR de la bibliothèque est ajouté au chemin de construction de votre projet. Si vous utilisez Maven, ajoutez la dépendance appropriée ; sinon, placez le JAR dans le dossier `libs` et référencez‑le lors de la compilation.

---

## Étape 1 : Configurer le chart builder

La première étape consiste à créer une instance de `ChartBuilder` (ou équivalente) qui générera les objets de graphique. Cet objet agit comme une fabrique et détient la feuille de calcul ou le canevas où le graphique sera placé.

```java
import com.aspose.cells.*;

public class DoughnutAndPieDemo {
    public static void main(String[] args) throws Exception {
        // Create a new workbook to host the charts
        Workbook workbook = new Workbook();
        Worksheet sheet = workbook.getWorksheets().get(0);

        // Initialize the chart builder with the worksheet
        ChartBuilder builder = new ChartBuilder(sheet);
```

**Pourquoi c’est important :**  
Le builder lie le graphique à une feuille de calcul spécifique, garantissant que tous les objets graphiques subséquents partagent la même surface de dessin. Ignorer cette étape vous laisserait sans emplacement cible pour les éléments visuels.

---

## Étape 2 : **Create doughnut chart**

Nous générons maintenant un doughnut chart avec une taille définie. La taille du trou détermine la portion centrale du graphique qui reste vide, transformant un pie chart ordinaire en doughnut chart.

```java
        // Insert a doughnut chart with a width of 500 and height of 350
        Chart doughnutChart = builder.insertChart(ChartType.DOUGHNUT, 500, 350);

        // Set the hole size to 30% of the chart radius
        doughnutChart.getDoughnutChart().setHoleSize(30);

        // Add sample data series
        doughnutChart.getNSeries().add("{10, 20, 30, 40}", true);
```

**Explication :**  

* `insertChart(ChartType.DOUGHNUT, 500, 350)` crée l'objet graphique et réserve l'espace sur la feuille de calcul.  
* `setHoleSize(30)` convertit le pie chart en doughnut chart avec un centre vide de 30 %.  
* `add("{10, 20, 30, 40}", true)` fournit quatre points de données ; le drapeau `true` indique à la bibliothèque de traiter les valeurs comme une série unique.

**Cas limite :** Si le type de graphique sélectionné ne prend pas en charge un trou (par ex., un graphique à barres), l’appel à `getDoughnutChart()` lève une exception. Vérifiez toujours le type de graphique avant d’ajuster la taille du trou.

---

## Étape 3 : **Insert pie chart**

Une fois le doughnut chart prêt, nous montrons comment **insert pie chart** en utilisant le même builder. Cette étape met en évidence la similarité entre les deux types de graphiques et montre comment mettre en avant une tranche.

```java
        // Insert a pie chart next to the doughnut
        Chart pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Add the same data series for consistency
        pieChart.getNSeries().add("{10, 20, 30, 40}", true);

        // Explode the first slice by 10% to draw attention
        pieChart.getSeries().get(0).setExplode(10);
```

**Explication :**  

* `ChartType.PIE` indique au builder de créer un pie chart classique.  
* `setExplode(10)` décale la première tranche de 10 % du rayon, une technique courante pour mettre en avant un point de données clé.  

**Astuce :** La méthode `setExplode` ne fonctionne que sur la première série d’un pie chart. Si vous avez plusieurs séries, vous devez cibler l’index correct.

---

## Étape 4 : Enregistrer le classeur

Enfin, écrivez le classeur dans un fichier afin de pouvoir visualiser les graphiques dans Excel ou tout visualiseur compatible.

```java
        // Save the workbook to a file
        workbook.save("DoughnutAndPieChart.xlsx");
        System.out.println("Workbook created with doughnut and pie charts.");
    }
}
```

**Pourquoi enregistrer maintenant :** La persistance du classeur finalise toutes les opérations de dessin. Tenter de visualiser le fichier avant l’enregistrement entraîne un document vide ou incomplet.

**Résultat :** L’ouverture de *DoughnutAndPieChart.xlsx* montre un doughnut chart avec un trou de 30 % à gauche et un pie chart avec la première tranche éclatée à droite.

---

## Étape 5 : Variations courantes et dépannage

| Situation | Ajustement |
|-----------|------------|
| **Différentes dimensions du graphique** | Modifiez les arguments de largeur et de hauteur dans `insertChart`. |
| **Séries de données multiples** | Appelez `add` plusieurs fois ou passez une chaîne de tableau 2‑D. |
| **Taille du trou dynamique** | Calculez la taille du trou en fonction de la plage de données, puis appelez `setHoleSize`. |
| **Faire exploser plusieurs tranches** | Parcourez `chart.getSeries().get(i).setExplode(percent)` pour chaque tranche que vous souhaitez décaler. |
| **Bibliothèque ne supportant pas le doughnut** | Utilisez un pie chart et dessinez manuellement un cercle blanc en superposition, bien que cela soit moins précis. |

**Pro tip :** Appelez toujours `builder.flush()` (si disponible) après l’insertion des graphiques lorsque vous travaillez avec de gros classeurs. Cela libère les tampons internes et prévient les fuites de mémoire.

---

![Java code creating a doughnut chart and inserting a pie chart](https://example.com/images/doughnut-pie-java.png "exemple de création de doughnut chart en Java")

*L’image illustre la disposition finale du classeur avec les deux graphiques côte à côte.*

---

## Conclusion

Vous savez maintenant comment **create doughnut chart** et **insert pie chart** en Java en utilisant une API de builder fluide. L’exemple complet couvre l’initialisation, la configuration de la taille, le réglage du trou, l’explosion de tranche et la sortie du fichier. À partir de là, vous pouvez explorer des personnalisations supplémentaires telles que les couleurs, les légendes et les étiquettes de données pour répondre à vos exigences de reporting.

**Prochaines étapes**

* Expérimentez les fonctionnalités de **chart customization Java** comme les remplissages en dégradé et les étiquettes de données.  
* Intégrez la génération de graphiques dans un service web qui renvoie le classeur à la demande.  
* Comparez l’approche builder avec d’autres bibliothèques (par ex., JFreeChart) pour choisir la meilleure solution pour votre projet.

Bonne création de graphiques !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets et fonctionnels avec des explications pas à pas pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Comment créer un doughnut chart dans un document Word avec Java](/words/english/java/images-shapes/how-to-create-doughnut-chart-in-a-word-document-with-java/)
- [Enregistrer le document Word après avoir modifié le doughnut chart en Java](/words/english/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/)
- [Insérer un Pie Chart en Java – Explosion, Rotation & Mise en évidence des tranches](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}