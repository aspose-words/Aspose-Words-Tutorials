---
category: general
date: 2026-11-15
description: Apprenez à créer un graphique en secteurs dans un document Word et à
  enregistrer le fichier .docx au format PDF en utilisant Java. Ce guide couvre également
  la conversion de Word en PDF et la façon d’ajouter un graphique.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save docx as pdf
- convert word to pdf
- how to add chart
- how to create chart
language: fr
lastmod: 2026-11-15
og_description: Créer un diagramme circulaire dans un fichier Word et enregistrer
  le docx en PDF avec Java. Suivez ce tutoriel étape par étape pour convertir Word
  en PDF et ajouter des graphiques.
og_image_alt: Screenshot showing a pie chart created in a Word document
og_title: Créer un diagramme circulaire dans Word et enregistrer le docx en PDF –
  Guide Java
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to create pie chart in a Word document and save docx as PDF
    using Java. This guide also covers convert word to pdf and how to add chart.
  headline: How to create pie chart in Word and save docx as PDF
  type: TechArticle
tags:
- Java
- Aspose.Words
- Chart
- PDF
title: Comment créer un graphique circulaire dans Word et enregistrer le docx en PDF
url: /fr/java/document-conversion-and-export/how-to-create-pie-chart-in-word-and-save-docx-as-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer un diagramme circulaire dans Word et enregistrer le docx en PDF

Si vous devez **créer un diagramme circulaire** dans un document Word puis **enregistrer le docx en PDF**, ce tutoriel vous montre exactement comment faire. Vous verrez un exemple complet et exécutable qui convertit un fichier .docx en PDF tout en intégrant un diagramme circulaire, afin que vous puissiez répondre à « comment ajouter un graphique » sans chercher des extraits dispersés.

Dans ce guide, vous apprendrez à :

* Charger un *.docx* existant (ou démarrer de zéro)  
* Utiliser Aspose.Words for Java pour **créer un diagramme circulaire** et le remplir de données  
* **Enregistrer le docx en PDF** avec le graphique correctement rendu  
* Comprendre les subtilités de la **conversion de Word en PDF** lorsqu’il y a des graphiques  

Les étapes fonctionnent avec Aspose.Words 2024‑x.x et Java 17, mais les concepts s’appliquent à toute bibliothèque qui supporte la manipulation de graphiques Word.

## Prérequis

Avant de commencer, assurez-vous d’avoir :

| Prérequis | Pourquoi c’est important |
|-----------|---------------------------|
| Java 17 (ou version ultérieure) | Requis par le dernier JAR Aspose.Words |
| Outil de construction Maven ou Gradle | Simplifie la gestion des dépendances |
| Aspose.Words for Java (dernière version) | Fournit les classes `Document`, `Chart` et `ChartType` |
| Un fichier **.docx** d’entrée (ou un document vierge) | Le graphique sera inséré dans ce fichier |

Ajoutez la dépendance Aspose.Words à votre `pom.xml` (Maven) ou `build.gradle` (Gradle). Exemple pour Maven :

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

## Étape 1 : Charger le document Word (ou en créer un nouveau)

La première action consiste à obtenir une instance de `Document`. Si vous avez déjà un modèle, indiquez son chemin ; sinon créez un document vide.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Load an existing .docx or create a new blank document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // If you prefer a new file, uncomment the next line:
        // Document doc = new Document();
```

*Pourquoi cette étape ?* L’objet `Document` est le conteneur de tout le contenu Word, y compris les graphiques. Charger un fichier existant vous permet de conserver le texte et les styles environnants tout en ajoutant un nouvel élément visuel.

## Étape 2 : **Créer un diagramme circulaire** – le cœur du « comment créer un graphique »

Nous instancions maintenant un objet `Chart` avec `ChartType.PIE`. Cela crée automatiquement un espace réservé pour un diagramme circulaire que vous remplirez ensuite avec des données.

```java
        // Step 2: Insert a pie chart into the document
        Chart chart = new Chart(doc, ChartType.PIE);
        // Place the chart at the end of the document body
        doc.getFirstSection().getBody().appendChild(chart);
```

*Explication* : `ChartType.PIE` indique à Aspose.Words d’utiliser un modèle de diagramme circulaire. Le graphique est ajouté au corps du document, de sorte qu’il apparaisse à l’endroit souhaité. Cela répond à la demande « comment ajouter un graphique » en un seul appel.

## Étape 3 : Remplir le graphique – répondre à « comment ajouter un graphique » avec des données

Un diagramme circulaire n’a aucun sens sans données de séries. Utilisez la collection `Series` pour ajouter des catégories et des valeurs.

```java
        // Step 3: Populate the chart with sample data
        chart.getSeries().add("Category A", 40);
        chart.getSeries().add("Category B", 30);
        chart.getSeries().add("Category C", 30);
```

*Pourquoi c’est important* : Chaque appel à `add` crée une tranche du diagramme. Le premier argument est le libellé, le deuxième est la valeur numérique. Vous pouvez remplacer ces valeurs par des données dynamiques provenant d’une base de données ou d’un fichier CSV.

### Optionnel : Personnaliser l’apparence (non obligatoire mais utile)

```java
        // Set a title for the chart
        chart.setTitle("Sales Distribution Q1");
        // Change the legend position
        chart.getLegend().setPosition(LegendPosition.RIGHT);
```

Ces ajustements illustrent comment vous pouvez **créer un graphique** avec un rendu professionnel, sans quitter le code Java.

## Étape 4 : **Enregistrer le docx en PDF** – la partie finale de « convertir Word en PDF »

Une fois le graphique intégré, exportez le document au format PDF. Aspose.Words rend le graphique sous forme de vecteur, préservant ainsi la qualité.

```java
        // Step 4: Save the document as PDF – the chart will be rendered with graduations
        doc.save("YOUR_DIRECTORY/output.pdf", SaveFormat.PDF);
    }
}
```

*Point clé* : La méthode `save` convertit automatiquement le fichier Word en PDF, gérant la rasterisation du graphique, l’inclusion des polices et la mise en page. Cela réalise l’objectif **enregistrer le docx en PDF** et montre une façon fiable de **convertir Word en PDF** lorsque des graphiques sont présents.

### Résultat attendu

L’exécution du programme produit `output.pdf` contenant :

* Le contenu original de `input.docx` (le cas échéant)  
* Un diagramme circulaire entièrement rendu intitulé *Sales Distribution Q1*  
* Des pourcentages de tranches précis correspondant aux données (40 %, 30 %, 30 %)

Ouvrez le PDF avec n’importe quel lecteur et vous devriez voir un diagramme circulaire net, identique à celui du fichier Word.

## Problèmes courants et comment les éviter

| Problème | Cause | Solution |
|----------|-------|----------|
| Le graphique apparaît vide dans le PDF | Paramètres de police ou de rendu du graphique manquants | Assurez‑vous d’utiliser la dernière version d’Aspose.Words ; elle inclut les bibliothèques de rendu nécessaires. |
| Les valeurs sont arrondies de façon incorrecte | Utilisation de valeurs entières avec de grands nombres | Fournissez des valeurs `double` ou mettez à l’échelle les nombres avant de les ajouter aux séries. |
| Le PDF de sortie est volumineux | Images intégrées à haute résolution DPI | Définissez `PdfSaveOptions.setImageCompressionLevel(CompressionLevel.MAXIMUM)` si vous intégrez également des images. |
| « convertir Word en PDF » lève `UnsupportedOperationException` | Utilisation d’une version Java ancienne (< 11) | Passez à Java 17 ou supérieur, requis par Aspose.Words 24.x. |

## Astuce pro : Réutiliser la logique de création du graphique

Si vous devez ajouter plusieurs graphiques au même document, extrayez le code de création du graphique dans une méthode d’aide :

```java
private static Chart createPieChart(Document doc, Map<String, Double> data, String title) {
    Chart chart = new Chart(doc, ChartType.PIE);
    data.forEach(chart.getSeries()::add);
    chart.setTitle(title);
    return chart;
}
```

Vous pouvez alors appeler `doc.getFirstSection().getBody().appendChild(createPieChart(...));` pour chaque jeu de données, en gardant votre code DRY (Don’t Repeat Yourself).

## Conclusion

Vous savez maintenant comment **créer un diagramme circulaire** dans un document Word, le remplir de données, et **enregistrer le docx en PDF** avec Java. Cet exemple de bout en bout couvre l’ensemble du flux de travail **convertir Word en PDF**, répond à **comment ajouter un graphique** et montre **comment créer un graphique** de façon programmatique.  

À partir d’ici, vous pouvez explorer :

* Ajouter des graphiques à barres ou en lignes (`ChartType.BAR`, `ChartType.LINE`) – un autre scénario **comment créer un graphique**.  
* Exporter vers d’autres formats comme PNG ou HTML (`SaveFormat.PNG`, `SaveFormat.HTML`).  
* Générer dynamiquement le document d’entrée avec des tableaux ou des espaces réservés avant d’insérer les graphiques.

N’hésitez pas à expérimenter avec différents jeux de données, options de style, ou même à intégrer plusieurs graphiques par page. Bon codage !

## Que devez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications pas à pas pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d’implémentation alternatives dans vos propres projets.

- [How to insert a pie chart into a Word document using Java](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [How to save word as pdf and create accessible PDF in Java](/words/english/java/document-conversion-and-export/create-accessible-pdf-from-docx-in-java-full-guide/)
- [How to create chart in Word with Java and Aspose.Words](/words/english/java/using-document-elements/how-to-create-chart-in-word-with-java-and-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}