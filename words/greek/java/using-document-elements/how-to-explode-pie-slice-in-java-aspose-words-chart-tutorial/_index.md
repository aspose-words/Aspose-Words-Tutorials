---
category: general
date: 2026-08-07
description: Πώς να αποσπάσετε τμήμα πίτας σε Java χρησιμοποιώντας το Aspose.Words.
  Μάθετε να προσθέτετε γραμμές οδηγούς στην πίτα, να δημιουργείτε διάγραμμα Word και
  να προσαρμόζετε τα τμήματα του διαγράμματος πίτας.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode pie slice
- add leader lines to pie
- java create word chart
- customize pie chart slices
language: el
lastmod: 2026-08-07
og_description: Πώς να «εξαπολύσετε» ένα τμήμα πίτας σε Java με το Aspose.Words. Αυτός
  ο οδηγός σας δείχνει πώς να προσθέσετε γραμμές οδηγούς στην πίτα, να δημιουργήσετε
  διαγράμματα Word και να προσαρμόσετε τα τμήματα του διαγράμματος πίτας για σαφή
  οπτική επίδραση.
og_image_alt: Screenshot of a Word document with an exploded pie chart created using
  Java Aspose.Words
og_title: Πώς να αποσπάσετε ένα τμήμα πίτας σε Java – Οδηγός Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to explode pie slice in Java using Aspose.Words. Learn to add leader
    lines to pie, create Word chart, and customize pie chart slices.
  headline: How to explode pie slice in Java – Aspose.Words chart tutorial
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart
- Pie Chart
title: Πώς να αποσπάσετε φέτα πίτας σε Java – Εκπαιδευτικό σετ Aspose.Words για γραφήματα
url: /el/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να «εξαπολύσετε» ένα τμήμα πίτας σε Java – Εγχειρίδιο διαγραμμάτων Aspose.Words

Αν χρειάζεστε να μάθετε **πώς να εξαπολύσετε ένα τμήμα πίτας** σε ένα έγγραφο Word χρησιμοποιώντας Java, αυτό το tutorial σας καλύπτει. Θα σας δείξουμε επίσης **πώς να προσθέσετε γραμμές οδηγού σε διαγράμματα πίτας**, **java create word chart** αντικείμενα, και **προσαρμογή τμημάτων διαγράμματος πίτας** για ένα επαγγελματικό αποτέλεσμα. Στο τέλος αυτού του οδηγού θα έχετε ένα πλήρες, εκτελέσιμο παράδειγμα που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο Java.

![How to explode pie slice in Java – Aspose.Words chart](/images/pie-chart-exploded.png)

## Προαπαιτήσεις

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* Java Development Kit (JDK) 8 ή νεότερο.
* Maven ή Gradle για διαχείριση εξαρτήσεων.
* Άδεια Aspose.Words for Java (η δωρεάν αξιολόγηση λειτουργεί για εκπαιδευτικούς σκοπούς).
* Βασική εξοικείωση με τη σύνταξη της Java και τις αντικειμενοστραφείς έννοιες.

> **Pro tip:** Παρόλο που το Aspose.Words προσφέρει δωρεάν δοκιμή, η αγορά άδειας αφαιρεί το υδατογράφημα αξιολόγησης από τα παραγόμενα έγγραφα.

## Τι καλύπτει αυτό το tutorial

* Δημιουργία νέου εγγράφου Word από το μηδέν.  
* Εισαγωγή **διαγράμματος πίτας** χρησιμοποιώντας το `DocumentBuilder`.  
* **Εξαπόλυση τμήματος πίτας** για ανάδειξη ενός σημείου δεδομένων.  
* **Προσθήκη γραμμών οδηγού σε πίτα** για πιο καθαρή ετικετοποίηση.  
* Προσαρμογή εμφάνισης τμημάτων, όπως χρώματα και περιθώρια.  
* Αποθήκευση του εγγράφου στο δίσκο και επαλήθευση του αποτελέσματος.

---

## Πώς να εξαπολύσετε τμήμα πίτας με Aspose.Words σε Java

Το πρώτο βήμα είναι να ρυθμίσετε το αντικείμενο διαγράμματος και να εξαπολύσετε το επιθυμητό τμήμα. Το Aspose.Words εκθέτει το διάγραμμα μέσω της κλάσης `Shape`, και κάθε τμήμα είναι ένα `ChartPoint`. Ορίζοντας την ιδιότητα `Explosion` ελέγχετε πόσο μακριά θα μετακινηθεί το τμήμα προς τα έξω.

```java
// Step 1: Create a blank document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Step 2: Insert a pie chart (400x300 points)
Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);
Chart chart = pieChart.getChart();

// Step 3: Explode the first slice (index 0) by 20 points
chart.getSeries().get(0).getPoints().get(0).setExplosion(20);
```

**Γιατί λειτουργεί:**  
`setExplosion(20)` λέει στη μηχανή διαγράμματος να μετατοπίσει το τμήμα κατά 20 μονάδες από το κέντρο του διαγράμματος. Η τιμή είναι σχετική· μεγαλύτεροι αριθμοί δημιουργούν πιο δραματικό αποτέλεσμα. Μπορείτε να εξαπολύσετε οποιοδήποτε τμήμα αλλάζοντας το δείκτη (`get(1)`, `get(2)`, …).

## Προσθήκη γραμμών οδηγού σε πίτα για πιο καθαρές ετικέτες

Οι γραμμές οδηγού συνδέουν την ετικέτα ενός τμήματος με την άκρη του, κάτι που είναι ιδιαίτερα χρήσιμο όταν τα τμήματα είναι εξαπολυμένα ή όταν το διάγραμμα περιέχει πολλά μικρά τμήματα. Η κλήση `setLeaderLines(true)` ενεργοποιεί αυτή τη λειτουργία για ολόκληρη τη σειρά.

```java
// Step 4: Enable leader lines for the series
chart.getSeries().get(0).setLeaderLines(true);
```

**Γιατί χρειάζεστε γραμμές οδηγού:**  
Όταν ένα τμήμα είναι εξαπολυμένο, η προεπιλεγμένη ετικέτα μπορεί να επικαλύπτεται με άλλα στοιχεία. Οι γραμμές οδηγού διατηρούν την ετικέτα αναγνώσιμη, σχεδιάζοντας μια μικρή γραμμή από το τμήμα προς το πλαίσιο κειμένου.

## Java create Word chart – εισαγωγή σειράς δεδομένων

Ένα διάγραμμα χωρίς δεδομένα δεν είναι πολύ χρήσιμο. Πρέπει να γεμίσετε τη σειρά με κατηγορίες και τιμές. Παρακάτω προσθέτουμε τρεις κατηγορίες που αντιπροσωπεύουν το μερίδιο αγοράς.

```java
// Step 5: Populate the chart with data
ChartSeries series = chart.getSeries().get(0);
series.getDataLabel().setShowCategoryName(true); // show labels
series.getDataLabel().setShowPercentage(true);   // show percentages

// Add categories and values
series.getCategories().add("Product A");
series.getCategories().add("Product B");
series.getCategories().add("Product C");

series.getValues().add(45); // Product A = 45%
series.getValues().add(30); // Product B = 30%
series.getValues().add(25); // Product C = 25%
```

**Επεξήγηση:**  
`ChartSeries` περιέχει τόσο τις κατηγορίες (τα ονόματα των τμημάτων) όσο και τις αριθμητικές τιμές. Η ενεργοποίηση των `ShowCategoryName` και `ShowPercentage` κάνει το διάγραμμα αυτοεξηγηματικό, κάτι που ταιριάζει τέλεια με τις γραμμές οδηγού που προσθέσαμε νωρίτερα.

## Προσαρμογή τμημάτων διαγράμματος πίτας πέρα από την εξαπόλυση

Πέρα από την εξαπόλυση ενός τμήματος, συχνά θέλετε να ρυθμίσετε χρώματα, περιθώρια ή ακόμη και να κρύψετε ένα τμήμα εντελώς. Το παρακάτω απόσπασμα δείχνει τρεις κοινές προσαρμογές:

```java
// Step 6: Change slice colors and borders
ChartPoint pointA = series.getPoints().get(0); // Product A
ChartPoint pointB = series.getPoints().get(1); // Product B
ChartPoint pointC = series.getPoints().get(2); // Product C

// Set custom fill colors
pointA.getFormat().getFill().setForeColor(java.awt.Color.decode("#4CAF50")); // green
pointB.getFormat().getFill().setForeColor(java.awt.Color.decode("#2196F3")); // blue
pointC.getFormat().getFill().setForeColor(java.awt.Color.decode("#FF9800")); // orange

// Add a thin border to each slice
for (ChartPoint pt : series.getPoints()) {
    pt.getFormat().getLine().setWeight(0.5);
    pt.getFormat().getLine().setForeColor(java.awt.Color.BLACK);
}

// Optional: hide a slice (e.g., Product C) without removing data
pointC.setIsHidden(true);
```

**Γιατί να προσαρμόσετε τα τμήματα:**  
Τα προσαρμοσμένα χρώματα κάνουν το διάγραμμα να ταιριάζει με την εταιρική ταυτότητα, ενώ τα περιθώρια βελτιώνουν την αναγνωσιμότητα σε εκτυπωμένες σελίδες. Η απόκρυψη ενός τμήματος είναι χρήσιμη όταν θέλετε να διατηρήσετε το μοντέλο δεδομένων αμετάβλητο αλλά να παραλείψετε προσωρινά μια κατηγορία από την οπτική παρουσίαση.

## Αποθήκευση του εγγράφου και επαλήθευση του αποτελέσματος

Τέλος, γράψτε το έγγραφο στο δίσκο. Μπορείτε να ανοίξετε το παραγόμενο `.docx` στο Microsoft Word, LibreOffice ή οποιονδήποτε προβολέα που υποστηρίζει τη μορφή.

```java
// Step 7: Save the document
String outputPath = "output/PieChartDemo.docx";
document.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

**Αναμενόμενο αποτέλεσμα:**  
Όταν ανοίξετε το `PieChartDemo.docx`, θα δείτε ένα διάγραμμα πίτας όπου το πρώτο τμήμα (Product A) είναι εξαπολυμένο προς τα έξω, οι γραμμές οδηγού δείχνουν από κάθε τμήμα στην ετικέτα του, και τα τμήματα εμφανίζονται στα προσαρμοσμένα χρώματα πράσινο, μπλε και πορτοκαλί. Το κρυφό τμήμα (Product C) δεν θα είναι ορατό, αλλά τα ποσοστά θα αθροίζουν ακόμα στο 100 % επειδή τα δεδομένα παραμένουν στη σειρά του διαγράμματος.

---

## Πλήρες, εκτελέσιμο παράδειγμα

Παρακάτω βρίσκεται το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε, επικολλήσετε και εκτελέσετε μετά την προσθήκη της εξάρτησης Aspose.Words στο έργο σας.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a pie chart (400x300 points)
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = pieChart.getChart();

        // Explode the first slice to highlight it
        chart.getSeries().get(0).getPoints().get(0).setExplosion(20);

        // Enable leader lines for clearer labeling
        chart.getSeries().get(0).setLeaderLines(true);

        // Populate the chart with data
        ChartSeries series = chart.getSeries().get(0);
        series.getDataLabel().setShowCategoryName(true);
        series.getDataLabel().setShowPercentage(true);

        series.getCategories().add("Product A");
        series.getCategories().add("Product B");
        series.getCategories().add("Product C");

        series.getValues().add(45);
        series.getValues().add(30);
        series.getValues().add(25);

        // Customize slice colors and borders
        ChartPoint pointA = series.getPoints().get(0);
        ChartPoint pointB = series.getPoints().get(1);
        ChartPoint pointC = series.getPoints().get(2);

        pointA.getFormat().getFill().setForeColor(java.awt.Color.decode("#4CAF50"));
        pointB.getFormat().getFill().setForeColor(java.awt.Color.decode("#2196F3"));
        pointC.getFormat().getFill().setForeColor(java.awt.Color.decode("#FF9800"));

        for (ChartPoint pt : series.getPoints()) {
            pt.getFormat().getLine().setWeight(0.5);
            pt.getFormat().getLine().setForeColor(java.awt.Color.BLACK);
        }

        // Hide the third slice (optional)
        pointC.setIsHidden(true);

        // Save the document
        document.save("output/PieChartDemo.docx");
        System.out.println("Pie chart Word document created successfully.");
    }
}
```

**Dependency (Maven)**  

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- Use the latest stable version -->
</dependency>
```


## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να δημιουργήσετε διάγραμμα στήλης χρησιμοποιώντας Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Πώς να φορτώσετε έγγραφα Word με Aspose.Words Java: Ολοκληρωμένος Οδηγός](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [Πώς να δημιουργήσετε πεδία φόρμας και να προσθέσετε περιεχόμενο χρησιμοποιώντας DocumentBuilder στο Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}