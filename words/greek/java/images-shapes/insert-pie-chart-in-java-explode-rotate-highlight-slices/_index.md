---
category: general
date: 2026-07-20
description: Εισαγάγετε διάγραμμα πίτας σε Java με οδηγό βήμα‑βήμα. Μάθετε πώς να
  απομονώσετε ένα τμήμα, πώς να περιστρέψετε το διάγραμμα πίτας, να επισημάνετε ένα
  τμήμα του διαγράμματος πίτας και να προσαρμόσετε το τμήμα του διαγράμματος πίτας.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to explode slice
- how to rotate pie chart
- highlight pie chart slice
- customize pie chart slice
language: el
lastmod: 2026-07-20
og_description: Εισάγετε διάγραμμα πίτας σε Java και μάθετε πώς να ξεχωρίζετε τμήμα,
  πώς να περιστρέφετε το διάγραμμα πίτας, να τονίζετε τμήμα διαγράμματος πίτας και
  να προσαρμόζετε τμήμα διαγράμματος πίτας για κομψές οπτικές αναφορές.
og_image_alt: Screenshot showing an inserted pie chart with an exploded and rotated
  slice
og_title: Εισαγωγή διαγράμματος πίτας σε Java – Αποσπασμός, Περιστροφή & Επισήμανση
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Insert pie chart in Java with a step‑by‑step guide. Learn how to explode
    slice, how to rotate pie chart, highlight pie chart slice and customize pie chart
    slice.
  headline: Insert Pie Chart in Java – Explode, Rotate & Highlight Slices
  type: TechArticle
tags:
- Java
- charting
- visualization
title: Εισαγωγή διαγράμματος πίτας σε Java – Αποσπάστε, Περιστρέψτε & Επισημάνετε
  τις φέτες
url: /el/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Εισαγωγή Πίτας Γραφήματος σε Java – Έκρηξη, Περιστροφή & Επισήμανση Τμημάτων

Κάποτε χρειάστηκε να **εισάγετε πίτα γράφημα** σε μια αναφορά Java αλλά δεν ήξερες πώς να κάνεις ένα τμήμα να «ξεπροβάλλει»; Δεν είσαι μόνος/η. Είτε δημιουργείς έναν πίνακα ελέγχου, παράγεις ένα τιμολόγιο, είτε απλώς οπτικοποιείς αποτελέσματα έρευνας, ένα καλά σχεδιασμένο πίτα γράφημα μπορεί να μετατρέψει ακατέργαστους αριθμούς σε άμεσα κατανοητές πληροφορίες.

Σε αυτό το tutorial θα δεις ένα πλήρες, έτοιμο‑για‑εκτέλεση παράδειγμα που δείχνει πώς να εισάγεις ένα πίτα γράφημα, **πώς να εκτοξεύσεις τμήμα**, **πώς να περιστρέψεις το γράφημα**, και ακόμη **πώς να επισημάνεις τμήμα πίτας** με προσαρμοσμένα χρώματα. Στο τέλος θα έχεις ένα επαναχρησιμοποιήσιμο snippet που μπορείς να ενσωματώσεις σε οποιοδήποτε έργο Java που χρησιμοποιεί τη δημοφιλή βιβλιοθήκη *JFreeChart* (ή οποιοδήποτε παρόμοιο API).

## Προαπαιτούμενα

- Java 17 ή νεότερη (ο κώδικας συντάσσεται και με παλαιότερες εκδόσεις, αλλά θα χρησιμοποιήσουμε τη σύγχρονη σύνταξη `var` για συντομία).  
- Maven ή Gradle για την προσθήκη της εξάρτησης `org.jfree:jfreechart`.  
- Βασική κατανόηση των κλάσεων Java και της έννοιας ενός chart builder.  

Αν ποτέ δεν πρόσθεσες βιβλιοθήκη σε έργο Maven, απλώς πρόσθεσε αυτό στο `pom.xml` σου:

```xml
<dependency>
    <groupId>org.jfree</groupId>
    <artifactId>jfreechart</artifactId>
    <version>1.5.4</version>
</dependency>
```

Τόσο! Δεν απαιτείται επιπλέον ρύθμιση.

## Βήμα 1: Εισαγωγή Πίτας Γραφήματος – Δημιουργία Builder και Chart Object

Πρώτα απ' όλα: χρειαζόμαστε έναν *builder* (σκεφτείτε το ως εργοστάσιο) που ξέρει πώς να παράγει γραφήματα. Στο JFreeChart, η `ChartFactory` κάνει το βαριά δουλειά.

```java
import org.jfree.chart.ChartFactory;
import org.jfree.chart.JFreeChart;
import org.jfree.data.general.DefaultPieDataset;

public class PieChartDemo {

    public static JFreeChart createPieChart() {
        // Prepare the data set
        var dataset = new DefaultPieDataset();
        dataset.setValue("Apples", 40);
        dataset.setValue("Bananas", 30);
        dataset.setValue("Cherries", 20);
        dataset.setValue("Dates", 10);

        // Insert pie chart with a width of 400 and height of 300
        JFreeChart chart = ChartFactory.createPieChart(
                "Fruit Distribution", // chart title
                dataset,              // data
                true,                 // include legend
                true,                 // tooltips
                false                 // URLs
        );
        return chart;
    }
}
```

Γιατί ξεκινάμε με το dataset; Επειδή το γράφημα είναι απλώς ένα οπτικό περίβλημα γύρω από τους αριθμούς. Με την **εισαγωγή πίτας γραφήματος** εδώ έχουμε ήδη έναν καμβά 400 × 300 (το μέγεθος θα εφαρμοστεί αργότερα όταν το αποδώσουμε σε εικόνα).

## Βήμα 2: Πώς να Εκτοξεύσετε Τμήμα – Έμφαση στο Πρώτο Τμήμα

Τώρα που υπάρχει το γράφημα, ας κάνουμε το πρώτο τμήμα να ξεχωρίσει. Η εκτόξευση ενός τμήματος το απομακρύνει ελαφρώς από τον κύκλο, τραβώντας το βλέμμα του αναγνώστη.

```java
import org.jfree.chart.plot.PiePlot;
import org.jfree.chart.plot.PiePlotState;

public static void explodeFirstSlice(JFreeChart chart) {
    // Grab the plot from the chart – this is where we tweak appearance
    PiePlot plot = (PiePlot) chart.getPlot();

    // Explode the first slice (index 0) to highlight it
    // The key "Apples" corresponds to the first entry we added
    plot.setExplodePercent("Apples", 0.15); // 15% outward
}
```

Παρατηρήστε ότι χρησιμοποιούμε τη φράση **πώς να εκτοξεύσετε τμήμα** στο όνομα της μεθόδου· αυτό κάνει την πρόθεση κρυστάλλινη. Η μέθοδος `setExplodePercent` δέχεται ένα κλειδί (την ετικέτα του τμήματος) και ένα ποσοστό, ώστε να μπορείς να ρυθμίσεις την απόσταση «ξεπροβολής» όπως χρειάζεται.

## Βήμα 3: Πώς να Περιστρέψετε το Πίτα Γράφημα – Αλλαγή της Αρχικής Γωνίας

Ένα προεπιλεγμένο πίτα γράφημα ξεκινά στη θέση 12 ωρών. Μερικές φορές θέλεις το πρώτο τμήμα να αρχίζει αλλού—ίσως για να ταιριάζει με ένα mock‑up σχεδίου ή με άλλο γράφημα.

```java
public static void rotateChart(JFreeChart chart, double startAngle) {
    PiePlot plot = (PiePlot) chart.getPlot();

    // Rotate the chart so the first slice starts at the given angle (degrees)
    plot.setStartAngle(startAngle);
}
```

Καλώντας `rotateChart(chart, 45)` περιστρέφει ολόκληρη την πίτα ώστε το τμήμα “Apples” να αρχίζει σε γωνία 45 μοιρών, ακριβώς όπως απαιτεί η **πώς να περιστρέψετε το πίτα γράφημα** απαίτηση.

## Βήμα 4: Επισήμανση Τμήματος Πίτας – Προσαρμοσμένα Χρώματα και Ετικέτες

Πέρα από την εκτόξευση, μπορεί να θέλεις να δώσεις σε ένα τμήμα μοναδικό χρώμα ή έντονη ετικέτα για να **επισημάνετε τμήμα πίτας**.

```java
import java.awt.Color;
import org.jfree.chart.labels.StandardPieSectionLabelGenerator;

public static void customizeSlice(JFreeChart chart) {
    PiePlot plot = (PiePlot) chart.getPlot();

    // Set a vivid color for the "Apples" slice
    plot.setSectionPaint("Apples", new Color(0xFF5722)); // deep orange

    // Make the label display both key and value in bold
    plot.setLabelGenerator(new StandardPieSectionLabelGenerator(
            "{0}: {1} ({2})")); // key: value (percent)
    plot.setLabelFont(plot.getLabelFont().deriveFont(java.awt.Font.BOLD));
}
```

Εδώ **προσαρμόζουμε τμήμα πίτας** αλλάζοντας το χρώμα και το στυλ της ετικέτας. Μπορείς ελεύθερα να αλλάξεις το χρώμα ή τη γραμματοσειρά ώστε να ταιριάζει με την παλέτα της μάρκας σου.

## Βήμα 5: Απόδοση του Γραφήματος σε Εικόνα (Προαιρετικό αλλά Χρήσιμο)

Οι περισσότερες πραγματικές εφαρμογές χρειάζονται το γράφημα ως PNG, JPEG ή ακόμη PDF. Παρακάτω υπάρχει ένας γρήγορος τρόπος για να γράψεις το γράφημα σε αρχείο.

```java
import java.io.File;
import org.jfree.chart.ChartUtils;

public static void saveChart(JFreeChart chart, String filename) throws Exception {
    int width = 400;
    int height = 300;
    File outFile = new File(filename);
    ChartUtils.saveChartAsPNG(outFile, chart, width, height);
}
```

Η εκτέλεση της πλήρους ροής θα παραγάγει ένα PNG 400 × 300 που μοιάζει με το παρακάτω:

![Insert pie chart example](image.png){: alt="Παράδειγμα εισαγωγής πίτας γραφήματος που δείχνει ένα εκτοξευμένο και περιστραμμένο τμήμα"}

## Πλήρες Παράδειγμα Λειτουργίας

Συνδυάζοντας όλα τα παραπάνω, εδώ είναι μια μέθοδος `main` που μπορείς να αντιγράψεις‑επικολλήσεις σε μια νέα κλάση Java και να εκτελέσεις:

```java
public class PieChartDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Insert the pie chart
        JFreeChart chart = createPieChart();

        // 2️⃣ Explode the first slice
        explodeFirstSlice(chart);

        // 3️⃣ Rotate the chart 45° so the first slice starts at 45 degrees
        rotateChart(chart, 45);

        // 4️⃣ Highlight and customize the exploded slice
        customizeSlice(chart);

        // 5️⃣ Save to disk (optional)
        saveChart(chart, "fruit-pie.png");

        System.out.println("Pie chart generated: fruit-pie.png");
    }

    // ... (include the helper methods from steps 1‑4 here) ...
}
```

### Αναμενόμενο Αποτέλεσμα

Η εκτέλεση του προγράμματος δημιουργεί ένα αρχείο με όνομα **fruit-pie.png**. Άνοιξέ το και θα δεις:

- Ένα πίτα γράφημα 400 × 300 με τίτλο “Fruit Distribution”.  
- Το τμήμα “Apples” εκτοξευμένο προς τα έξω κατά 15 %.  
- Ολόκληρο το γράφημα περιστραμμένο ώστε το “Apples” να αρχίζει στη θέση των 45 μοιρών.  
- Το εκτοξευμένο

## Τι Πρέπει να Μάθεις Στη Σύντομη Επόμενη

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σε βοηθήσουν να κυριαρχήσεις πρόσθετες δυνατότητες του API και να εξερευνήσεις εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σου έργα.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Insert Scatter Chart](/words/hindi/net/programming-with-charts/insert-scatter-chart/)
- [Insert Area Chart](/words/hindi/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}