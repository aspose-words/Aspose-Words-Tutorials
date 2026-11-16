---
category: general
date: 2026-11-15
description: Μάθετε πώς να προσθέσετε ένα διάγραμμα πίτας σε ένα έγγραφο Word με το
  Aspose.Words for Java. Περιλαμβάνει μετατροπή σε δακτύλιο, εκραγμένο τμήμα και πλήρες
  παράδειγμα κώδικα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart to word document
- Aspose.Words chart example
- Java pie chart tutorial
- create doughnut chart in Word
- explode pie slice Java
language: el
lastmod: 2026-11-15
og_description: Προσθέστε ένα διάγραμμα πίτας σε ένα έγγραφο Word χρησιμοποιώντας
  το Aspose.Words for Java. Αυτό το σεμινάριο δείχνει πώς να απομακρύνετε ένα τμήμα
  και να μετατρέψετε το διάγραμμα σε δακτύλιο.
og_image_alt: Screenshot of a Word document containing an exploded pie chart transformed
  into a doughnut
og_title: Προσθήκη διαγράμματος πίτας σε έγγραφο Word με Java – οδηγός βήμα‑προς‑βήμα
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  headline: How to add a pie chart to a Word document using Java
  type: TechArticle
- description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  name: How to add a pie chart to a Word document using Java
  steps:
  - name: Expected output
    text: 'Open `final-pie-doughnut.docx` in Microsoft Word:'
  - name: Adding multiple series
    text: 'If you need several series (e.g., stacked doughnut), add them sequentially:'
  - name: Custom colors
    text: 'You can assign a color to each slice via `ChartDataPoint.setFillFormat().setSolidFillColor()`:'
  - name: Working with an existing chart
    text: 'If the document already contains a chart and you only want to modify it,
      locate the chart shape:'
  - name: License handling
    text: 'Aspose.Words requires a license for production use. Place your `Aspose.Words.lic`
      file in the classpath and load it at application start:'
  - name: What to explore next
    text: '* **add bar chart to Word document** – similar steps but use `ChartType.BAR`.
      * **customize chart legends and titles** – use `pieChart.getTitle().setText("...")`
      and `pieChart.getLegend().setPosition(LegendPosition.RIGHT)`. * **export the
      Word document as PDF** – change the `SaveFormat` to `PDF` for'
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: Πώς να προσθέσετε ένα διάγραμμα πίτας σε ένα έγγραφο Word χρησιμοποιώντας τη
  Java
url: /el/java/using-document-elements/how-to-add-a-pie-chart-to-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Προσθήκη διαγράμματος πίτας σε έγγραφο Word – πλήρης οδηγός Java

Αν χρειάζεται να **προσθέσετε ένα διάγραμμα πίτας σε έγγραφο Word** προγραμματιστικά, αυτό το tutorial σας δείχνει ακριβώς πώς να το κάνετε με το Aspose.Words for Java. Θα δείτε ολόκληρη τη ροή εργασίας: φόρτωση ενός DOCX, δημιουργία διαγράμματος πίτας, «έκρηξη» του πρώτου κομματιού και μετατροπή του διαγράμματος σε δακτύλιο ορίζοντας το μέγεθος της τρύπας.

Ο οδηγός καλύπτει επίσης κοινές παραλλαγές — όπως η προσθήκη πολλαπλών σειρών, η προσαρμογή χρωμάτων και η διαχείριση εγγράφων που ήδη περιέχουν διαγράμματα — ώστε να μπορείτε να προσαρμόσετε τον κώδικα σε πραγματικά έργα, όπως αυτοματοποιημένες αναφορές ή δυναμικές παρουσιάσεις.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* Java 17 ή νεότερη (ο κώδικας συντάσσεται επίσης με JDK 11+)
* Maven 3.6+ ή Gradle για διαχείριση εξαρτήσεων
* Άδεια Aspose.Words for Java (η δωρεάν δοκιμή λειτουργεί για δοκιμές)
* Βασική κατανόηση της σύνταξης Java και της δομής έργου Maven

## Βήμα 1: Ρύθμιση του έργου Maven και εισαγωγή του Aspose.Words

Δημιουργήστε ένα νέο έργο Maven (ή προσθέστε σε υπάρχον) και συμπεριλάβετε την εξάρτηση Aspose.Words:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-chart-demo</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest stable at time of writing -->
        </dependency>
    </dependencies>
</project>
```

> **Pro tip:** Αν χρησιμοποιείτε Gradle, η αντίστοιχη εγγραφή είναι `implementation 'com.aspose:aspose-words:24.9'`.

Η εξάρτηση φέρνει τις κλάσεις `Document`, `Chart` και `ChartType` που θα χρειαστείτε για τη διαχείριση διαγραμμάτων.

## Βήμα 2: Φόρτωση του στόχου εγγράφου

Μπορείτε να ξεκινήσετε από ένα υπάρχον αρχείο `.docx` ή να δημιουργήσετε ένα νέο κενό έγγραφο. Το παρακάτω παράδειγμα φορτώνει ένα πρότυπο με όνομα `input.docx` που βρίσκεται στο φάκελο `src/main/resources`.

```java
import com.aspose.words.Document;
import com.aspose.words.SaveFormat;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load the Word document that will receive the chart
        Document doc = new Document("src/main/resources/input.docx");
        // Continue with chart creation...
    }
}
```

Αν το αρχείο δεν υπάρχει, το Aspose.Words θα δημιουργήσει αυτόματα ένα νέο κενό έγγραφο όταν καλέσετε `new Document()` χωρίς όνομα αρχείου.

## Βήμα 3: Δημιουργία διαγράμματος πίτας και εισαγωγή του στο έγγραφο

Το Aspose.Words αντιμετωπίζει ένα διάγραμμα ως σχήμα που μπορεί να τοποθετηθεί οπουδήποτε μπορεί να εμφανιστεί μια παράγραφος. Ο παρακάτω κώδικας δημιουργεί μια **διάγραμμα πίτας**, προσθέτει μια μοναδική σειρά δεδομένων και εισάγει το διάγραμμα μετά την πρώτη παράγραφο.

```java
import com.aspose.words.*;
import java.util.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        Document doc = new Document("src/main/resources/input.docx");

        // Create a new chart of type PIE
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // Prepare data for the series: categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // Add a new series to the chart
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // Insert the chart into the document after the first paragraph
        Paragraph firstParagraph = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);
        firstParagraph.appendChild(pieChart);
        
        // Save the document to verify the result
        doc.save("output/add-pie-chart.docx", SaveFormat.DOCX);
    }
}
```

**Γιατί είναι σημαντικό αυτό το βήμα:**  
* `ChartType.PIE` λέει στο Aspose.Words να αποδώσει μια παραδοσιακή διάγραμμα πίτας.  
* Η προσθήκη μιας σειράς με ετικέτες κατηγοριών και αριθμητικές τιμές γεμίζει αυτόματα τα κομμάτια.  
* Η εισαγωγή του διαγράμματος ως παιδί ενός `Paragraph` διατηρεί την ροή του εγγράφου αμετάβλητη.

## Βήμα 4: Έκρηξη του πρώτου κομματιού για να το τονίσετε

Ένα *εκρηγμένο κομμάτι* τραβά την προσοχή σε ένα συγκεκριμένο σημείο δεδομένων. Το API εκθέτει τη μέθοδο `setExplode(boolean)` σε ένα αντικείμενο `ChartSeries`. Ορίζοντάς το στην πρώτη σειρά (δείκτης 0) κάνει το πρώτο κομμάτι να «προβληθεί».

```java
// Explode the first slice (index 0) of the first series
pieChart.getSeries().get(0).setExplode(true);
```

> **Συχνή ερώτηση:** *Τι γίνεται αν έχω πολλαπλές σειρές;*  
> Μπορείτε να στοχεύσετε μια συγκεκριμένη σειρά με το δείκτη της, π.χ. `pieChart.getSeries().get(1).setExplode(true)` για τη δεύτερη σειρά.

## Βήμα 5: Μετατροπή της διαγράμματος πίτας σε δακτύλιο ορίζοντας το μέγεθος της τρύπας

Ένα διάγραμμα δακτυλίου είναι ουσιαστικά μια διάγραμμα πίτας με κεντρική τρύπα. Το Aspose.Words σας επιτρέπει να ορίσετε το μέγεθος της τρύπας ως ποσοστό της ακτίνας του διαγράμματος.

```java
// Turn the pie chart into a doughnut with a 30% hole size
pieChart.setHoleSize(30);
```

Η μέθοδος `setHoleSize` δέχεται τιμές από **0** (κανονική πίτα) έως **100** (εντελώς κενό). Μια τιμή γύρω στο **30‑40** προσφέρει ένα οπτικά ισορροπημένο δακτύλιο.

## Βήμα 6: Αποθήκευση και επαλήθευση του αποτελέσματος

Μετά από όλες τις τροποποιήσεις, αποθηκεύστε το έγγραφο. Η παρακάτω γραμμή γράφει το αρχείο στο φάκελο `output`.

```java
doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);
```

### Αναμενόμενο αποτέλεσμα

Ανοίξτε το `final-pie-doughnut.docx` στο Microsoft Word:

* Ένα διάγραμμα δακτυλίου εμφανίζεται εκεί που ήταν η πρώτη παράγραφος.  
* Το κομμάτι “Apples” είναι εκρηγμένο (ελαφρώς διαχωρισμένο από τα υπόλοιπα).  
* Το διάγραμμα δείχνει τέσσερα κομμάτια με ετικέτες *Apples*, *Bananas*, *Cherries*, *Dates* και τα ποσοστά που δώσατε.

Αν προτιμάτε έξοδο PDF, αλλάξτε το `SaveFormat` σε `SaveFormat.PDF`.

## Διαχείριση ειδικών περιπτώσεων και παραλλαγών

### Προσθήκη πολλαπλών σειρών

Αν χρειάζεστε πολλές σειρές (π.χ. στοίβαξη δακτυλίου), προσθέστε τις διαδοχικά:

```java
double[] values2022 = {20, 30, 25, 25};
double[] values2023 = {25, 20, 30, 25};

ChartSeries s2022 = pieChart.getSeries().add("2022", categories, values2022);
ChartSeries s2023 = pieChart.getSeries().add("2023", categories, values2023);
```

### Προσαρμοσμένα χρώματα

Μπορείτε να αναθέσετε χρώμα σε κάθε κομμάτι μέσω `ChartDataPoint.setFillFormat().setSolidFillColor()`:

```java
ChartDataPoint point = series.getDataPoints().get(0); // first slice
point.getFillFormat().setSolidFillColor(java.awt.Color.RED);
```

### Εργασία με υπάρχον διάγραμμα

Αν το έγγραφο περιέχει ήδη ένα διάγραμμα και θέλετε μόνο να το τροποποιήσετε, εντοπίστε το σχήμα του διαγράμματος:

```java
NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
for (Node shapeNode : (Iterable<Node>) shapes) {
    Shape shape = (Shape) shapeNode;
    if (shape.getShapeType() == ShapeType.CHART) {
        Chart existingChart = shape.getChart();
        // Apply explode/holeSize changes here
    }
}
```

### Διαχείριση άδειας

Το Aspose.Words απαιτεί άδεια για παραγωγική χρήση. Τοποθετήστε το αρχείο `Aspose.Words.lic` στην κλάση‑διαδρομή (classpath) και φορτώστε το κατά την εκκίνηση της εφαρμογής:

```java
License license = new License();
license.setLicense("Aspose.Words.lic");
```

Η μη ρύθμιση άδειας θα προσθέσει υδατογράφημα στο παραγόμενο έγγραφο.

## Πλήρες, εκτελέσιμο παράδειγμα

Ακολουθεί η πλήρης κλάση Java που ενσωματώνει όλα τα βήματα που συζητήθηκαν. Αντιγράψτε την στο `src/main/java/com/example/AddPieChart.java` και εκτελέστε `mvn compile exec:java`.

```java
package com.example;

import com.aspose.words.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load license (optional for trial)
        // new License().setLicense("Aspose.Words.lic");

        // 1️⃣ Load the base document
        Document doc = new Document("src/main/resources/input.docx");

        // 2️⃣ Create a pie chart
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // 3️⃣ Define categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // 4️⃣ Add a series with the data
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // 5️⃣ Explode the first slice
        pieChart.getSeries().get(0).setExplode(true);

        // 6️⃣ Convert to doughnut (30% hole)
        pieChart.setHoleSize(30);

        // 7️⃣ Insert the chart after the first paragraph
        Paragraph firstPara = (Paragraph) doc.getFirstSection()
                .getBody()
                .getChild(NodeType.PARAGRAPH, 0, true);
        firstPara.appendChild(pieChart);

        // 8️⃣ Save the final document
        doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);

        System.out.println("Chart added successfully. Check output/final-pie-doughnut.docx");
    }
}
```

Η εκτέλεση του προγράμματος παράγει το διάγραμμα δακτυλίου που περιγράφηκε παραπάνω. Προσαρμόστε τις `categories`, `values` ή `holeSize` ώστε να ταιριάζουν στα δεδομένα σας.

## Συμπέρασμα

Τώρα γνωρίζετε πώς να **προσθέσετε ένα διάγραμμα πίτας σε έγγραφο Word** χρησιμοποιώντας Java και Aspose.Words. Το tutorial κάλυψε τη φόρτωση εγγράφου, τη δημιουργία διαγράμματος πίτας, την έκρηξη ενός κομματιού, τη μετατροπή του σε δακτύλιο και τη διαχείριση κοινών παραλλαγών όπως πολλαπλές σειρές, προσαρμοσμένα χρώματα και υπάρχοντα διαγράμματα. Με αυτή τη βάση μπορείτε να δημιουργήσετε εργαλεία αυτοματοποιημένων αναφορών, να παράγετε δυναμικές παρουσιάσεις ή να ενσωματώσετε πλούσιες οπτικοποιήσεις απευθείας σε αρχεία Word.

### Τι να εξερευνήσετε στη συνέχεια

* **προσθήκη διαγράμματος ράβδων σε έγγραφο Word** – παρόμοια βήματα αλλά χρησιμοποιήστε `ChartType.BAR`.  
* **προσαρμογή υπομνήματος και τίτλων διαγράμματος** – χρησιμοποιήστε `pieChart.getTitle().setText("...")` και `pieChart.getLegend().setPosition(LegendPosition.RIGHT)`.  
* **εξαγωγή του εγγράφου Word ως PDF** – αλλάξτε το `SaveFormat` σε `PDF` για αρχεία έτοιμα για διανομή.  
* **συμπλήρωση δεδομένων διαγράμματος από βάση δεδομένων** – αντικαταστήστε τους στατικούς πίνακες με αποτελέσματα ερωτημάτων JDBC.

Μη διστάσετε να πειραματιστείτε με διαφορετικούς τύπους διαγραμμάτων, πηγές δεδομένων και επιλογές στυλ. Καλή προγραμματιστική διασκέδαση!

## Τι πρέπει να μάθετε επόμενα;

Τα παρακάτω tutorials καλύπτουν στενά σχετικούς τομείς που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [Πώς να εκρηγνύετε κομμάτι πίτας σε Java – tutorial διαγράμματος Aspose.Words](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [Δημιουργία διαγράμματος πίτας με Aspose.Words Java – πλήρης οδηγός βήμα‑βήμα](/words/english/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}