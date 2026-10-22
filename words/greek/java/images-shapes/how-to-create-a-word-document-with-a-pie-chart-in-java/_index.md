---
category: general
date: 2026-09-18
description: Μάθετε πώς να δημιουργήσετε ένα έγγραφο Word και να εισάγετε διάγραμμα
  πίτας χρησιμοποιώντας το Aspose.Words for Java. Περιλαμβάνει βήματα για περιστροφή
  του διαγράμματος πίτας και δημιουργία αρχείου Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- rotate pie chart
- generate word file
- how to create pie chart
language: el
lastmod: 2026-09-18
og_description: Δημιουργήστε ένα έγγραφο Word και εισάγετε ένα διάγραμμα πίτας χρησιμοποιώντας
  Java. Ακολουθήστε αυτόν τον οδηγό για να περιστρέψετε το διάγραμμα πίτας, να εκτοξεύσετε
  τα τμήματα και να δημιουργήσετε ένα αρχείο Word.
og_image_alt: Screenshot showing a Word document containing a pie chart created with
  Java
og_title: Δημιουργήστε ένα έγγραφο Word με διάγραμμα πίτας – οδηγός Java βήμα‑προς‑βήμα
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  headline: How to create a Word document with a pie chart in Java
  type: TechArticle
- description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  name: How to create a Word document with a pie chart in Java
  steps:
  - name: Expected output
    text: 'After running the program, open `output/PieChart.docx`. You should see:'
  - name: Inserting multiple charts
    text: 'If you need more than one chart, call `builder.insertChart` again after
      moving the cursor:'
  - name: Changing chart colors
    text: 'You can customize slice colors via the series'' `getPoints()` collection:'
  - name: Handling large datasets
    text: For datasets with more than 10 slices, consider using a doughnut chart (`ChartType.DOUGHNUT`)
      to keep the visual clear.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: Πώς να δημιουργήσετε ένα έγγραφο Word με διάγραμμα πίτας σε Java
url: /el/java/images-shapes/how-to-create-a-word-document-with-a-pie-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε ένα έγγραφο Word με διάγραμμα πίτας σε Java

Αν χρειάζεστε **να δημιουργήσετε ένα έγγραφο Word** που οπτικοποιεί δεδομένα, αυτός ο οδηγός σας δείχνει πώς να το κάνετε με το Aspose.Words for Java. Θα μάθετε να εισάγετε ένα διάγραμμα πίτας, να «εκτοξεύετε» ένα τμήμα, να περιστρέφετε το διάγραμμα και τελικά **να δημιουργήσετε ένα αρχείο Word** που μπορείτε να ανοίξετε στο Microsoft Word.

Η δημιουργία αναφορών που συνδυάζουν κείμενο και διαγράμματα δεν απαιτεί ξεχωριστό εργαλείο γραφικών. Στο τέλος αυτού του tutorial θα έχετε ένα πλήρες, εκτελέσιμο πρόγραμμα που δημιουργεί ένα αρχείο .docx με ένα πλήρως διαμορφωμένο διάγραμμα πίτας.

## Προαπαιτούμενα

- Java 17 ή νεότερη (ο κώδικας μεταγλωττίζεται επίσης με Java 8+)
- Maven ή Gradle για διαχείριση εξαρτήσεων
- Άδεια Aspose.Words for Java (η δωρεάν δοκιμαστική έκδοση λειτουργεί για αυτό το παράδειγμα)
- Βασική εξοικείωση με τη σύνταξη της Java

## Βήμα 1: Ρύθμιση του έργου Maven

Δημιουργήστε ένα νέο έργο Maven και προσθέστε την εξάρτηση Aspose.Words στο `pom.xml`:

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>word-pie-chart</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>23.12</version>
        </dependency>
    </dependencies>
</project>
```

> **Συμβουλή:** Διατηρήστε τον αριθμό έκδοσης ενημερωμένο· οι νεότερες εκδόσεις προσθέτουν βελτιώσεις τύπων διαγραμμάτων και διορθώσεις σφαλμάτων.

## Βήμα 2: Δημιουργία νέου εγγράφου Word

Η πρώτη ενέργεια όταν **δημιουργείτε ένα έγγραφο Word** προγραμματιστικά είναι η δημιουργία ενός αντικειμένου `Document`. Αυτό το αντικείμενο αντιπροσωπεύει ολόκληρο το αρχείο .docx στη μνήμη.

```java
import com.aspose.words.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a blank document
        Document doc = new Document();

        // Continue with chart insertion...
```

Η κλάση `Document` είναι το σημείο εισόδου για όλες τις λειτουργίες επεξεργασίας Word. Δεν γράφεται κανένα αρχείο στο δίσκο σε αυτό το σημείο· όλα συμβαίνουν στη μνήμη RAM μέχρι να καλέσετε τη μέθοδο `save`.

## Βήμα 3: Πώς να εισάγετε ένα διάγραμμα πίτας

Ένας `DocumentBuilder` σας επιτρέπει να προσθέτετε περιεχόμενο στο έγγραφο. Με τη μέθοδο `insertChart` μπορείτε να **εισάγετε αντικείμενα διαγράμματος πίτας** απευθείας.

```java
        // Step 3: Initialize DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with width=400pt, height=300pt
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

`ChartType.PIE` λέει στο Aspose.Words να δημιουργήσει ένα διάγραμμα πίτας. Οι διαστάσεις εκφράζονται σε points (1 pt ≈ 1/72 in). Μετά από αυτήν την κλήση το διάγραμμα εμφανίζεται σε μια νέα παράγραφο.

## Βήμα 4: Συμπλήρωση του διαγράμματος με δεδομένα

Ένα διάγραμμα πίτας χρειάζεται μια σειρά τιμών. Εδώ προσθέτουμε τρεις κατηγορίες: “Apples”, “Bananas” και “Cherries”.

```java
        // Create a data series
        chart.getSeries().add("Fruits", new String[]{"Apples", "Bananas", "Cherries"},
                new double[]{30, 45, 25});
```

Η μέθοδος `add` δημιουργεί τη σειρά και αυτόματα δημιουργεί καταχωρήσεις υπομνήματος. Μπορείτε να επαναχρησιμοποιήσετε αυτό το μοτίβο για οποιοδήποτε αριθμητικό σύνολο δεδομένων.

## Βήμα 5: Τονισμός του πρώτου τμήματος

Η «εκτόξευση» ενός τμήματος τραβά την προσοχή σε μια συγκεκριμένη τιμή. Το πρώτο τμήμα (δείκτης 0) εκτοξεύεται κατά 20 points.

```java
        // Step 5: Explode the first slice
        chart.getSeries().get(0).setExplode(20);
```

Ο ορισμός του `explode` στη σειρά επηρεάζει ολόκληρο το διάγραμμα, έτσι μόνο το πρώτο σημείο δεδομένων μετατοπίζεται.

## Βήμα 6: Πώς να περιστρέψετε ένα διάγραμμα πίτας

Η περιστροφή του διαγράμματος βελτιώνει την οπτική ισορροπία, ειδικά όταν το μεγαλύτερο τμήμα δεν βρίσκεται στην κορυφή. Η μέθοδος `setRotationAngle` δέχεται μοίρες.

```java
        // Step 6: Rotate the chart 45 degrees
        chart.setRotationAngle(45);
```

Μια περιστροφή 45° μετακινεί τη γωνία εκκίνησης δεξιόστροφα, καθιστώντας το διάγραμμα πιο εύκολο στην ανάγνωση σε πολλές διατάξεις.

## Βήμα 7: Αποθήκευση του εγγράφου και δημιουργία αρχείου Word

Τέλος, γράψτε το έγγραφο στο δίσκο. Αυτό το βήμα **δημιουργεί αρχείο Word** που μπορεί να ανοιχθεί με το Microsoft Word, το LibreOffice ή οποιονδήποτε συμβατό προβολέα.

```java
        // Step 7: Save the document
        String outputPath = "output/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

Η μέθοδος `save` ανιχνεύει αυτόματα την επέκταση .docx και γράφει ένα πακέτο συμβατό με το Word. Ο φάκελος `output` πρέπει να υπάρχει ή μπορείτε να τον δημιουργήσετε προγραμματιστικά.

### Αναμενόμενο αποτέλεσμα

Μετά την εκτέλεση του προγράμματος, ανοίξτε το `output/PieChart.docx`. Θα πρέπει να δείτε:

- Μία μόνο σελίδα που περιέχει ένα διάγραμμα πίτας 400 × 300 pt.
- Το τμήμα “Apples” εκτοξεύεται προς τα έξω κατά 20 pt.
- Ολόκληρο το διάγραμμα περιστρέφεται 45° δεξιόστροφα.
- Ένα υπόμνημα που ταιριάζει με τις τρεις κατηγορίες φρούτων.

## Συνηθισμένες παραλλαγές και ειδικές περιπτώσεις

### Εισαγωγή πολλαπλών διαγραμμάτων

Αν χρειάζεστε περισσότερα από ένα διάγραμμα, καλέστε ξανά το `builder.insertChart` μετά τη μετακίνηση του δρομέα:

```java
builder.writeln();               // Add a line break
Chart secondChart = builder.insertChart(ChartType.PIE, 300, 200);
```

### Αλλαγή χρωμάτων διαγράμματος

Μπορείτε να προσαρμόσετε τα χρώματα των τμημάτων μέσω της συλλογής `getPoints()` της σειράς:

```java
chart.getSeries().get(0).getPoints().get(0).getFormat().getFill().setForeColor(Color.RED);
```

### Διαχείριση μεγάλων συνόλων δεδομένων

Για σύνολα δεδομένων με περισσότερα από 10 τμήματα, εξετάστε το ενδεχόμενο χρήσης διαγράμματος δακτυλίου (`ChartType.DOUGHNUT`) για να διατηρήσετε την οπτική σαφήνεια.

## Συμπέρασμα

Τώρα γνωρίζετε πώς να **δημιουργήσετε ένα έγγραφο Word**, **εισάγετε διάγραμμα πίτας**, **περιστρέψετε διάγραμμα πίτας** και **να δημιουργήσετε ένα αρχείο Word** χρησιμοποιώντας το Aspose.Words for Java. Η πλήρης λύση δείχνει τη συνολική ροή εργασίας από την αρχικοποίηση του εγγράφου μέχρι την τελική έξοδο του αρχείου, καλύπτοντας τόσο το “πώς” όσο και το “γιατί” κάθε βήματος.

Στη συνέχεια, εξερευνήστε συναφή θέματα όπως **πώς να δημιουργήσετε δεδομένα διαγράμματος πίτας** από βάση δεδομένων, προσθήκη ετικετών δεδομένων ή εξαγωγή του διαγράμματος ως εικόνα. Πειραματιστείτε με διαφορετικούς τύπους διαγραμμάτων (στήλη, γραμμή, δακτύλιος) για να επεκτείνετε το σύνολο εργαλείων αυτοματοποίησης του Word.

## Τι Θα Πρέπει Να Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά σχετικές θεματικές που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να δημιουργήσετε διάγραμμα στήλης χρησιμοποιώντας το Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Δημιουργία Εγγράφου Word Java – Προσθήκη Σχήματος Ορθογωνίου με Εφέ Σκιάς](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Καταγραφή Αλλαγών σε Έγγραφα Word Χρησιμοποιώντας Aspose.Words Java: Πλήρης Οδηγός για Αναθεωρήσεις Εγγράφου](/words/english/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}