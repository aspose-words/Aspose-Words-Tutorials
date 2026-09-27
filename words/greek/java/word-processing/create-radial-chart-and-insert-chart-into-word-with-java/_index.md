---
category: general
date: 2026-09-27
description: Δημιουργήστε ένα ακτινικό γράφημα σε Java και ενσωματώστε το γράφημα
  στο Word. Μάθετε πώς να ορίσετε το μέγεθος του γραφήματος, να προσθέσετε σειρά δεδομένων
  και να δημιουργήσετε ένα κενό έγγραφο Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- insert chart into word
- create blank word document
- how to set chart size
- add data series chart
language: el
lastmod: 2026-09-27
og_description: Δημιουργήστε ακτινικό γράφημα σε Java, στη συνέχεια εισάγετε το γράφημα
  στο Word. Αυτός ο οδηγός δείχνει πώς να ορίσετε το μέγεθος του γραφήματος, να προσθέσετε
  σειρά δεδομένων και να δημιουργήσετε ένα κενό έγγραφο Word.
og_image_alt: Screenshot showing a radial chart inserted into a Word document created
  with Java
og_title: Δημιουργήστε ακτινικό γράφημα και εισάγετε το γράφημα στο Word με Java
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create radial chart in Java and insert chart into Word. Learn how to
    set chart size, add data series, and generate a blank Word document.
  headline: Create radial chart and insert chart into Word with Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart generation
title: Δημιουργία ακτινικού διαγράμματος και εισαγωγή του στο Word με Java
url: /el/java/word-processing/create-radial-chart-and-insert-chart-into-word-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία ακτινικού διαγράμματος και εισαγωγή διαγράμματος σε Word με Java

Αν χρειάζεστε **create radial chart** σε αρχείο Word χρησιμοποιώντας Java, αυτό το tutorial σας δείχνει ακριβώς πώς. Θα δείτε πώς να **insert chart into Word**, να ορίσετε τις διαστάσεις του διαγράμματος και να δημιουργήσετε ένα **blank Word document** από την αρχή.

Θα περάσουμε από κάθε απαιτούμενο βήμα, από την αρχικοποίηση του εγγράφου μέχρι την προσθήκη μιας σειράς δεδομένων και την αποθήκευση του τελικού `.docx`. Στο τέλος θα έχετε ένα πλήρως λειτουργικό αρχείο Word που περιέχει ένα radial chart, και θα κατανοήσετε **how to set chart size** και **add data series chart** για μελλοντικές προσαρμογές.

## Προαπαιτούμενα

* Java 17 ή νεότερο (ο κώδικας μεταγλωττίζεται με οποιοδήποτε σύγχρονο JDK)
* Aspose.Words for Java 24.9 ή νεότερο – η μέθοδος `setShowGraduations` είναι διαθέσιμη μόνο από αυτήν την έκδοση
* Ένα IDE ή εργαλείο κατασκευής (Maven/Gradle) που μπορεί να συμπεριλάβει το Aspose.Words JAR
* Βασική εξοικείωση με τη σύνταξη Java και τη διαχείριση εξαρτήσεων Maven/Gradle

> **Pro tip:** Αν χρησιμοποιείτε Maven, προσθέστε τα παρακάτω στο `pom.xml` σας:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## Βήμα 1: Δημιουργία κενής εγγράφου Word

Ένα κενό έγγραφο είναι ο καμβάς πάνω στον οποίο θα τοποθετηθεί το διάγραμμα. Η κλάση `Document` αντιπροσωπεύει ολόκληρο το αρχείο `.docx`.

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank Word document
```

Η δημιουργία ενός κενό εγγράφου εξασφαλίζει ότι κανένα προϋπάρχον περιεχόμενο δεν θα επηρεάσει τη διάταξη του διαγράμματος.

## Βήμα 2: Αρχικοποίηση DocumentBuilder

`DocumentBuilder` παρέχει βολικές μεθόδους για την εισαγωγή αντικειμένων, κειμένου και άλλων στοιχείων στο έγγραφο.

```java
        // Step 2: Initialise a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Ο builder θα χρησιμοποιηθεί αργότερα για **insert chart into Word**.

## Βήμα 3: Δημιουργία του radial chart

Το Aspose.Words υποστηρίζει πολλούς τύπους διαγραμμάτων· η `ChartType.RADIAL` δημιουργεί ένα radial (πολικό) διάγραμμα.

```java
        // Step 3: Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);
```

Σε αυτό το σημείο το διάγραμμα υπάρχει αλλά δεν έχει δεδομένα, μέγεθος ή οπτικές επιλογές.

## Βήμα 4: Προσθήκη σειράς δεδομένων στο διάγραμμα

Ένα διάγραμμα χωρίς σειρά δεδομένων είναι κενό. Η μέθοδος `add` δέχεται ένα όνομα σειράς και έναν πίνακα τιμών.

```java
        // Step 4: Add a data series to the chart
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});
```

Μπορείτε να προσθέσετε πολλαπλές σειρές καλώντας την `add` επανειλημμένα. Αυτό ικανοποιεί την απαίτηση **add data series chart**.

## Βήμα 5: Ενεργοποίηση graduations (προαιρετικό)

Οι graduations είναι οι ακτινικές γραμμές πλέγματος που βελτιώνουν την αναγνωσιμότητα. Είναι διαθέσιμες μόνο από την έκδοση 24.9.

```java
        // Step 5: Enable graduations on the chart (available from version 24.9)
        chart.getChartObject().setShowGraduations(true);
```

Αν χρησιμοποιείτε παλαιότερη έκδοση του Aspose.Words, αυτή η γραμμή θα προκαλέσει εξαίρεση—γιαυτό ελέγξτε πρώτα την έκδοση της βιβλιοθήκης.

## Βήμα 6: Ορισμός διαστάσεων του διαγράμματος

Ο έλεγχος του μεγέθους του διαγράμματος σας επιτρέπει να το προσαρμόσετε όμορφα στα περιθώρια της σελίδας. Αυτό καλύπτει το **how to set chart size**.

```java
        // Step 6: Define the chart's dimensions
        chart.setWidth(400);   // width in points (≈5.5 inches)
        chart.setHeight(300);  // height in points (≈4.2 inches)
```

Μπορείτε να προσαρμόσετε τις τιμές πλάτους και ύψους ώστε να ταιριάζουν στις ανάγκες της διάταξής σας. Θυμηθείτε ότι 1 point ≈ 1/72 inch.

## Βήμα 7: Εισαγωγή του διαγράμματος στο έγγραφο Word

Τώρα το διάγραμμα είναι έτοιμο για τοποθέτηση. Η μέθοδος `insertChart` του `DocumentBuilder` διαχειρίζεται την εισαγωγή.

```java
        // Step 7: Insert the chart into the document
        builder.insertChart(chart);
```

Αυτό είναι ο πυρήνας της λειτουργίας **insert chart into word**.

## Βήμα 8: Αποθήκευση του εγγράφου

Τέλος, γράψτε το έγγραφο στο δίσκο. Το αρχείο θα περιέχει το radial chart που μόλις δημιουργήσατε.

```java
        // Step 8: Save the document with the chart
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Η εκτέλεση του προγράμματος παράγει το `RadialChart.docx` στον κατάλογο εργασίας του έργου. Το άνοιγμα του αρχείου στο Microsoft Word εμφανίζει ένα radial chart με τρία σημεία δεδομένων και ορατές graduations.

### Αναμενόμενο αποτέλεσμα

* Ένα αρχείο Word με όνομα `RadialChart.docx`
* Μέσα στο αρχείο, μια μοναδική σελίδα που περιέχει ένα radial chart διαστάσεων 400 × 300 points
* Το διάγραμμα εμφανίζει μία σειρά με τίτλο **Series 1** και τιμές **10, 20, 30**
* Οι graduations (ακτινικές γραμμές πλέγματος) είναι ορατές γύρω από το διάγραμμα

## Συνηθισμένες παραλλαγές και ειδικές περιπτώσεις

| Situation | What to change | Reason |
|-----------|----------------|--------|
| **Πολλαπλές σειρές** | Κλήση `chart.getSeries().add(...)` για κάθε σειρά | Επιτρέπει συγκριτική απεικόνιση δεδομένων |
| **Διαφορετικός τύπος διαγράμματος** | Αντικαταστήστε `ChartType.RADIAL` με `ChartType.COLUMN` (ή οποιονδήποτε άλλο) | Χρησιμοποιήστε τον τύπο διαγράμματος που αντιπροσωπεύει καλύτερα τα δεδομένα σας |
| **Προσαρμοσμένα χρώματα** | Πρόσβαση `chart.getSeries().get(i).getFormat().getFill().setForeColor(Color)` | Βελτιώνει την οπτική ταυτότητα |
| **Παλαιότερη έκδοση Aspose.Words** | Αφαιρέστε τη γραμμή `setShowGraduations` ή αναβαθμίστε τη βιβλιοθήκη | Αποτρέπει το `NoSuchMethodError` |
| **Αποθήκευση σε διαφορετική μορφή** | Χρησιμοποιήστε `doc.save("RadialChart.pdf", SaveFormat.PDF)` | Δημιουργεί PDF αντί για DOCX |

## Πλήρες εκτελέσιμο παράδειγμα

Παρακάτω βρίσκεται το πλήρες, αυτόνομο πρόγραμμα Java. Αντιγράψτε το σε ένα αρχείο με όνομα `RadialChartExample.java`, προσθέστε την εξάρτηση Aspose.Words και εκτελέστε το.

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank Word document
        Document doc = new Document();

        // 2. Initialise a DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);

        // 4. Add a data series (add data series chart)
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});

        // 5. Enable graduations (requires Aspose.Words 24.9+)
        chart.getChartObject().setShowGraduations(true);

        // 6. Set chart size (how to set chart size)
        chart.setWidth(400);
        chart.setHeight(300);

        // 7. Insert the chart into the document (insert chart into word)
        builder.insertChart(chart);

        // 8. Save the document (create blank word document with chart)
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

## Συμπέρασμα

Τώρα ξέρετε πώς να **create radial chart** προγραμματιστικά, **add data series chart**, να ελέγχετε **how to set chart size**, και **insert chart into Word** ξεκινώντας από ένα **blank Word document**. Το παράδειγμα χρησιμοποιεί Aspose.Words for Java 24.9, αλλά οι ίδιες έννοιες ισχύουν για άλλες βιβλιοθήκες διαγραμμάτων που εκθέτουν παρόμοιο API.

### Επόμενα βήματα

* Εξερευνήστε άλλους τύπους διαγραμμάτων (`ChartType.PIE`, `ChartType.LINE`, κλπ.) – αυτό συνδέεται με τη δευτερεύουσα λέξη-κλειδί **insert chart into word**.
* Προσαρμόστε τις ετικέτες αξόνων, τις υπομνήματα και τα χρώματα ώστε να ταιριάζουν με τις οδηγίες της μάρκας σας.
* Δημιουργήστε διαγράμματα δυναμικά από ερωτήματα βάσεων δεδομένων ή αρχεία CSV.
* Μετατρέψτε το παραγόμενο `.docx` σε PDF για διανομή (`doc.save("output.pdf", SaveFormat.PDF)`).

Μη διστάσετε να πειραματιστείτε με τις διαστάσεις, τα δεδομένα των σειρών και τις επιλογές στυλ για να δημιουργήσετε το ακριβές οπτικό αποτέλεσμα που χρειάζεστε. Καλή προγραμματιστική!

## Τι Θα Πρέπει Να Μάθετε Στη Σύντομη Μελλοντική;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να δημιουργήσετε διάγραμμα στήλης χρησιμοποιώντας Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Δημιουργία εγγράφου Word Java – Προσθήκη σχήματος ορθογωνίου με εφέ σκιάς](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Εισαγωγή διαγράμματος περιοχής σε έγγραφο Word](/words/english/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}