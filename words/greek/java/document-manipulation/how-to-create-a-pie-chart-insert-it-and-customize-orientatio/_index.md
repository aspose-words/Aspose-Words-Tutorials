---
category: general
date: 2026-11-25
description: Μάθετε πώς να δημιουργήσετε ένα διάγραμμα πίτας σε Java, να ενσωματώσετε
  το διάγραμμα πίτας σε έγγραφο Word, να «εκραγίσετε» ένα τμήμα της πίτας και να αλλάξετε
  τον προσανατολισμό του διαγράμματος με σαφή παραδείγματα κώδικα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- change chart orientation
- explode pie slice
- insert pie chart
- rotate pie chart
language: el
lastmod: 2026-11-25
og_description: Δημιουργήστε ένα διάγραμμα πίτας σε Java, εισάγετε το διάγραμμα πίτας
  σε ένα έγγραφο, εκτοπίστε ένα τμήμα της πίτας και αλλάξτε τον προσανατολισμό του
  διαγράμματος με βήμα‑βήμα κώδικα.
og_image_alt: Screenshot of a created pie chart with an exploded slice and rotated
  orientation
og_title: Δημιουργία διαγράμματος πίτας σε Java – εισαγωγή, εξάπλωση φέτας και περιστροφή
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to create a pie chart in Java, insert pie chart into a Word
    document, explode pie slice and change chart orientation with clear code examples.
  headline: How to create a pie chart, insert it, and customize orientation in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Charting
title: Πώς να δημιουργήσετε ένα διάγραμμα πίτας, να το εισάγετε και να προσαρμόσετε
  τον προσανατολισμό στο Java
url: /el/java/document-manipulation/how-to-create-a-pie-chart-insert-it-and-customize-orientatio/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε ένα διάγραμμα πίτας, να το εισάγετε και να προσαρμόσετε τον προσανατολισμό σε Java

Αν χρειάζεστε **δημιουργία διαγράμματος πίτας** μέσα σε ένα έγγραφο Word, αυτός ο οδηγός σας δείχνει ακριβώς πώς να το κάνετε. Θα δείτε πώς να **εισάγετε διάγραμμα πίτας**, να «ξεσπάσετε» ένα τμήμα για έμφαση και να **αλλάξετε τον προσανατολισμό του διαγράμματος** με μια απλή περιστροφή.

Το tutorial καλύπτει όλα όσα χρειάζεστε — από τη ρύθμιση της βιβλιοθήκης Aspose.Words for Java μέχρι την παραγωγή ενός τελικού αρχείου `.docx` που εμφανίζει ένα περιστραμμένο, «ξεσπασμένο» διάγραμμα πίτας. Δεν απαιτείται εξωτερική τεκμηρίωση· ακολουθήστε τα βήματα και εκτελέστε τον κώδικα.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* Java 17 ή νεότερη εγκατεστημένη.
* Maven ή Gradle για διαχείριση εξαρτήσεων.
* Ένα έγκυρο license του Aspose.Words for Java (ή χρησιμοποιήστε τη δωρεάν λειτουργία αξιολόγησης).

Προσθέστε την εξάρτηση Aspose.Words στο `pom.xml` (Maven) ή στο `build.gradle` (Gradle). Παράδειγμα για Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version>
</dependency>
```

> **Pro tip:** Κρατήστε την έκδοση της βιβλιοθήκης ενημερωμένη· η πιο πρόσφατη έκδοση (24.10 τη στιγμή της συγγραφής) περιλαμβάνει διορθώσεις σφαλμάτων για την απόδοση διαγραμμάτων.

## Βήμα 1: Δημιουργία διαγράμματος πίτας και εισαγωγή του στο έγγραφο

Το πρώτο βήμα είναι η **δημιουργία διαγράμματος πίτας** και η ενσωμάτωσή του σε ένα αρχείο Word. Ο παρακάτω κώδικας δημιουργεί ένα απλό έγγραφο, προσθέτει έναν placeholder διαγράμματος και εισάγει ένα διάγραμμα πίτας μεγέθους 400 × 300 pixel.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new Document and DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a pie chart of size 400x300
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Populate the chart with sample data
        chart.getSeries().clear(); // remove default series
        ChartSeries series = chart.getSeries().add("Sales", new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Save the document so far (optional)
        doc.save("Step1_InsertPieChart.docx");
    }
}
```

**Γιατί είναι σημαντικό:** Η μέθοδος `builder.insertChart` δημιουργεί έναν placeholder διαγράμματος που το Aspose.Words μετατρέπει αυτόματα σε OOXML διάγραμμα όταν αποθηκεύεται το έγγραφο. Το όρισμα `ChartType.PIE` λέει στη βιβλιοθήκη να αποδώσει ένα διάγραμμα πίτας, ικανοποιώντας την απαίτηση **insert pie chart**.

## Βήμα 2: Ξεσπάστε ένα τμήμα πίτας για να τονίσετε ένα τμήμα

Το «ξεσπάσιμο» ενός τμήματος τραβάει την προσοχή σε ένα συγκεκριμένο σημείο δεδομένων. Η παρακάτω γραμμή ξεσπά το πρώτο τμήμα (δείκτης 0) κατά 10 μονάδες:

```java
// 4️⃣ Explode the first slice (index 0) by 10 points
chart.getSeries().get(0).setExplode(0, 10);
```

Μπορείτε να αλλάξετε το δείκτη για να στοχεύσετε διαφορετικό τμήμα ή να προσαρμόσετε την απόσταση ξεσπάσματος για πιο ήπιο αποτέλεσμα. Το ξεσπάσιμο τμήματος είναι ο τυπικός τρόπος για **explode pie slice** στο Aspose.Words.

## Βήμα 3: Αλλαγή προσανατολισμού διαγράμματος με περιστροφή

Η περιστροφή του διαγράμματος προσφέρει μια φρέσκια οπτική προοπτική. Χρησιμοποιήστε `setRotationAngle` για να περιστρέψετε ολόκληρο το διάγραμμα δεξιόστροφα (η γωνία μετράται σε μοίρες).

```java
// 5️⃣ Rotate the entire chart by 45 degrees
chart.setRotationAngle(45);
```

Η κλήση παραπάνω ικανοποιεί τις απαιτήσεις **rotate pie chart** και **change chart orientation**. Δέχεται οποιαδήποτε γωνία μεταξύ 0 και 360 μοίρες.

## Πλήρες εκτελέσιμο παράδειγμα

Συνδυάζοντας όλα τα παραπάνω, εδώ είναι ένα πλήρες, αυτόνομο πρόγραμμα που δημιουργεί διάγραμμα πίτας, ξεσπά ένα τμήμα και περιστρέφει το διάγραμμα. Εκτελέστε το από το IDE ή από τη γραμμή εντολών με `java -cp <classpath> PieChartDemo`.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300 pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Prepare data series (Sales per quarter)
        chart.getSeries().clear(); // remove default placeholder
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Explode the first slice (Q1) by 10 points
        chart.getSeries().get(0).setExplode(0, 10);

        // Rotate the chart 45 degrees clockwise
        chart.setRotationAngle(45);

        // Save the final document
        doc.save("CreatePieChartDemo.docx");
        System.out.println("Document created successfully: CreatePieChartDemo.docx");
    }
}
```

### Αναμενόμενο αποτέλεσμα

* Ένα αρχείο με όνομα **CreatePieChartDemo.docx** εμφανίζεται στον τρέχοντα φάκελο.
* Το άνοιγμα του αρχείου στο Microsoft Word δείχνει ένα διάγραμμα πίτας 400 × 300 pixel.
* Το πρώτο τμήμα (Q1) είναι μετατοπισμένο προς τα έξω κατά 10 μονάδες, δημιουργώντας το εφέ **explode pie slice**.
* Ολόκληρο το διάγραμμα είναι κλινόμενο 45 μοίρες, επιδεικνύοντας **change chart orientation** και **rotate pie chart**.

## Συνηθισμένες παραλλαγές και ειδικές περιπτώσεις

| Κατάσταση | Πώς να προσαρμόσετε τον κώδικα |
|-----------|-------------------------------|
| **Διαφορετικό μέγεθος διαγράμματος** | Αλλάξτε τα ορίσματα `400, 300` στην `insertChart`. |
| **Πολλαπλές σειρές** | Προσθέστε περισσότερα αντικείμενα `ChartSeries` στο `chart.getSeries()`. |
| **Ξεσπάστε διαφορετικό τμήμα** | Χρησιμοποιήστε `setExplode(sliceIndex, distance)` με το επιθυμητό `sliceIndex`. |
| **Δεν απαιτείται περιστροφή** | Παραλείψτε την κλήση `setRotationAngle` ή ορίστε τη γωνία σε `0`. |
| **Εξαγωγή σε PDF αντί για DOCX** | Μετά τη δημιουργία του εγγράφου, καλέστε `doc.save("output.pdf")` με τη μορφή PDF. |

> **Προσοχή:** Η χρήση αρνητικής απόστασης ξεσπάσματος προκαλεί `IllegalArgumentException`. Πάντα δίνετε μη‑αρνητική τιμή.

## Συμβουλή απόδοσης

Αν παράγετε πολλά διαγράμματα σε βρόχο, επαναχρησιμοποιήστε ένα μόνο `DocumentBuilder` και καλέστε `insertChart` μόνο για κάθε επανάληψη. Αυτό μειώνει το φορτίο μνήμης και επιταχύνει την επεξεργασία.

## Συμπέρασμα

Τώρα ξέρετε πώς να **create pie chart**, **insert pie chart**, **explode pie slice** και **rotate pie chart** χρησιμοποιώντας το Aspose.Words for Java. Το πλήρες παράδειγμα δείχνει τη συνολική ροή εργασίας — από την αρχικοποίηση του εγγράφου μέχρι την αποθήκευση ενός αρχείου που οπτικοποιεί ένα περιστραμμένο, «ξεσπασμένο» διάγραμμα πίτας.

Στη συνέχεια, μπορείτε να εξερευνήσετε περαιτέρω το **changing chart orientation** εφαρμόζοντας εφέ 3‑D, ή να πειραματιστείτε με άλλους τύπους διαγραμμάτων όπως **Bar** ή **Line**. Τα ίδια πρότυπα API ισχύουν, οπότε η επέκταση αυτού του tutorial είναι απλή.

Αλλάξτε ελεύθερα τα δεδομένα, το δείκτη τμήματος ή τη γωνία περιστροφής ώστε να ταιριάζουν στις δικές σας ανάγκες αναφοράς, και μοιραστείτε τα αποτελέσματά σας με την κοινότητα!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε επιπλέον δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στην υλοποίηση των δικών σας έργων.

- [How to insert a pie chart into a Word document using Java](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [How to explode pie slice in Java – Aspose.Words chart tutorial](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}