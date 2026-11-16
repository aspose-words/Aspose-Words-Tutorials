---
category: general
date: 2026-11-15
description: Μάθετε πώς να δημιουργήσετε διάγραμμα πίτας σε έγγραφο Word και να αποθηκεύσετε
  το docx ως PDF χρησιμοποιώντας Java. Αυτός ο οδηγός καλύπτει επίσης τη μετατροπή
  του Word σε PDF και πώς να προσθέσετε διάγραμμα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save docx as pdf
- convert word to pdf
- how to add chart
- how to create chart
language: el
lastmod: 2026-11-15
og_description: Δημιουργήστε διάγραμμα πίτας σε αρχείο Word και αποθηκεύστε το docx
  ως PDF με Java. Ακολουθήστε αυτόν τον οδηγό βήμα‑βήμα για να μετατρέψετε το Word
  σε PDF και να προσθέσετε διαγράμματα.
og_image_alt: Screenshot showing a pie chart created in a Word document
og_title: Δημιουργήστε ένα διάγραμμα πίτας στο Word και αποθηκεύστε το docx ως PDF
  – Οδηγός Java
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
title: Πώς να δημιουργήσετε διάγραμμα πίτας στο Word και να αποθηκεύσετε το docx ως
  PDF
url: /el/java/document-conversion-and-export/how-to-create-pie-chart-in-word-and-save-docx-as-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε διάγραμμα πίτας στο Word και να αποθηκεύσετε το docx ως PDF

Αν χρειάζεστε να **δημιουργήσετε διάγραμμα πίτας** μέσα σε ένα έγγραφο Word και στη συνέχεια **αποθηκεύσετε το docx ως PDF**, αυτό το tutorial σας δείχνει ακριβώς πώς. Θα δείτε ένα πλήρες, εκτελέσιμο παράδειγμα που μετατρέπει ένα αρχείο .docx σε PDF ενώ ενσωματώνει ένα διάγραμμα πίτας, ώστε να μπορείτε να απαντήσετε στο “πώς να προσθέσετε διάγραμμα” χωρίς να ψάχνετε για διάσπαρτα αποσπάσματα.

Σε αυτόν τον οδηγό θα μάθετε να:

* Φορτώνετε ένα υπάρχον *.docx* (ή ξεκινάτε από το μηδέν)  
* Χρησιμοποιείτε το Aspose.Words for Java για **δημιουργία διαγράμματος πίτας** και συμπλήρωση δεδομένων  
* **Αποθηκεύετε το docx ως PDF** με το διάγραμμα να αποδίδεται σωστά  
* Κατανοείτε τις λεπτομέρειες του **convert word to pdf** όταν εμπλέκονται διαγράμματα  

Τα βήματα λειτουργούν με Aspose.Words 2024‑x.x και Java 17, αλλά οι έννοιες ισχύουν για οποιαδήποτε βιβλιοθήκη που υποστηρίζει τη διαχείριση διαγραμμάτων Word.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

| Απαίτηση | Γιατί είναι σημαντικό |
|-------------|----------------|
| Java 17 (ή νεότερη) | Απαιτείται από το τελευταίο Aspose.Words JAR |
| Maven ή Gradle εργαλείο κατασκευής | Απλοποιεί τη διαχείριση εξαρτήσεων |
| Aspose.Words for Java (τελευταία έκδοση) | Παρέχει τις κλάσεις `Document`, `Chart` και `ChartType` |
| Ένα αρχείο **.docx** εισόδου (ή ένα κενό έγγραφο) | Το διάγραμμα θα εισαχθεί σε αυτό το αρχείο |

Προσθέστε την εξάρτηση Aspose.Words στο `pom.xml` (Maven) ή στο `build.gradle` (Gradle). Παράδειγμα για Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

## Βήμα 1: Φόρτωση του εγγράφου Word (ή δημιουργία νέου)

Η πρώτη ενέργεια είναι η λήψη μιας στιγμής `Document`. Εάν έχετε ήδη ένα πρότυπο, περάστε τη διαδρομή του· διαφορετικά δημιουργήστε ένα κενό έγγραφο.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Load an existing .docx or create a new blank document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // If you prefer a new file, uncomment the next line:
        // Document doc = new Document();
```

*Γιατί αυτό το βήμα;* Το αντικείμενο `Document` είναι ο container για όλο το περιεχόμενο του Word, συμπεριλαμβανομένων των διαγραμμάτων. Η φόρτωση ενός υπάρχοντος αρχείου σας επιτρέπει να διατηρήσετε το περιβάλλον κειμένου και τα στυλ ενώ προσθέτετε ένα νέο οπτικό στοιχείο.

## Βήμα 2: **Δημιουργία διαγράμματος πίτας** – ο πυρήνας του “πώς να δημιουργήσετε διάγραμμα”

Τώρα δημιουργούμε ένα αντικείμενο `Chart` με `ChartType.PIE`. Αυτό δημιουργεί αυτόματα έναν placeholder διαγράμματος πίτας που μπορείτε αργότερα να γεμίσετε με δεδομένα.

```java
        // Step 2: Insert a pie chart into the document
        Chart chart = new Chart(doc, ChartType.PIE);
        // Place the chart at the end of the document body
        doc.getFirstSection().getBody().appendChild(chart);
```

*Εξήγηση*: `ChartType.PIE` λέει στο Aspose.Words να χρησιμοποιήσει ένα πρότυπο διαγράμματος πίτας. Το διάγραμμα προστίθεται στο σώμα του εγγράφου, έτσι εμφανίζεται εκεί που το χρειάζεστε. Αυτό ικανοποιεί την απαίτηση “πώς να προσθέσετε διάγραμμα” με μία μόνο κλήση.

## Βήμα 3: Συμπλήρωση του διαγράμματος – απάντηση στο “πώς να προσθέσετε διάγραμμα” με δεδομένα

Ένα διάγραμμα πίτας δεν έχει νόημα χωρίς δεδομένα σειράς. Χρησιμοποιήστε τη συλλογή `Series` για να προσθέσετε κατηγορίες και τιμές.

```java
        // Step 3: Populate the chart with sample data
        chart.getSeries().add("Category A", 40);
        chart.getSeries().add("Category B", 30);
        chart.getSeries().add("Category C", 30);
```

*Γιατί είναι σημαντικό*: Κάθε κλήση στο `add` δημιουργεί ένα τμήμα της πίτας. Το πρώτο όρισμα είναι η ετικέτα, το δεύτερο η αριθμητική τιμή. Μπορείτε να τα αντικαταστήσετε με δυναμικά δεδομένα από βάση ή αρχείο CSV.

### Προαιρετικό: Προσαρμογή εμφάνισης (δεν είναι απαραίτητο αλλά χρήσιμο)

```java
        // Set a title for the chart
        chart.setTitle("Sales Distribution Q1");
        // Change the legend position
        chart.getLegend().setPosition(LegendPosition.RIGHT);
```

Αυτές οι μικρές αλλαγές δείχνουν πώς μπορείτε **how to create chart** με επαγγελματική εμφάνιση, χωρίς να βγείτε από τον κώδικα Java.

## Βήμα 4: **Αποθήκευση docx ως PDF** – το τελικό μέρος του “convert word to pdf”

Μόλις το διάγραμμα ενσωματωθεί, εξάγετε το έγγραφο σε PDF. Το Aspose.Words αποδίδει το διάγραμμα ως διανυσματικό γραφικό, διατηρώντας την ποιότητα.

```java
        // Step 4: Save the document as PDF – the chart will be rendered with graduations
        doc.save("YOUR_DIRECTORY/output.pdf", SaveFormat.PDF);
    }
}
```

*Κύριο σημείο*: Η μέθοδος `save` μετατρέπει αυτόματα το αρχείο Word σε PDF, διαχειρίζεται τη ραστεροποίηση του διαγράμματος, την ενσωμάτωση γραμματοσειρών και τη διάταξη σελίδας. Αυτό εκπληρώνει το στόχο **save docx as pdf** και δείχνει έναν αξιόπιστο τρόπο **convert word to pdf** όταν υπάρχουν διαγράμματα.

### Αναμενόμενο αποτέλεσμα

Η εκτέλεση του προγράμματος παράγει το `output.pdf` που περιέχει:

* Το αρχικό περιεχόμενο του `input.docx` (αν υπάρχει)  
* Ένα πλήρως αποδομένο διάγραμμα πίτας με τίτλο *Sales Distribution Q1*  
* Ακριβή ποσοστά τμημάτων που ταιριάζουν με τα δεδομένα (40 %, 30 %, 30 %)

Ανοίξτε το PDF σε οποιονδήποτε προβολέα και θα δείτε ένα καθαρό διάγραμμα πίτας, ταυτόσημο με αυτό που βλέπετε στο αρχείο Word.

## Συνηθισμένα προβλήματα και πώς να τα αποφύγετε

| Πρόβλημα | Αιτία | Διόρθωση |
|-------|-------|-----|
| Το διάγραμμα εμφανίζεται κενό στο PDF | Λείπουν ρυθμίσεις γραμματοσειράς ή απόδοσης διαγράμματος | Βεβαιωθείτε ότι χρησιμοποιείτε την τελευταία έκδοση του Aspose.Words· περιλαμβάνει τις απαιτούμενες βιβλιοθήκες απόδοσης. |
| Οι τιμές στρογγυλοποιούνται λανθασμένα | Χρήση ακέραιων τιμών με μεγάλα νούμερα | Παρέχετε τιμές `double` ή κλιμακώστε τους αριθμούς πριν τα προσθέσετε στη σειρά. |
| Το παραγόμενο PDF είναι τεράστιο | Εικόνες ενσωματωμένες σε υψηλή DPI | Ορίστε `PdfSaveOptions.setImageCompressionLevel(CompressionLevel.MAXIMUM)` αν ενσωματώνετε επίσης εικόνες. |
| Το “convert word to pdf” πετάει `UnsupportedOperationException` | Χρήση παλαιότερης έκδοσης Java (< 11) | Αναβαθμίστε σε Java 17 ή νεότερη, η οποία απαιτείται από το Aspose.Words 24.x. |

## Συμβουλή pro: Επαναχρησιμοποίηση της λογικής δημιουργίας διαγράμματος

Αν χρειάζεται να προσθέσετε πολλά διαγράμματα στο ίδιο έγγραφο, εξάγετε τον κώδικα δημιουργίας διαγράμματος σε μια βοηθητική μέθοδο:

```java
private static Chart createPieChart(Document doc, Map<String, Double> data, String title) {
    Chart chart = new Chart(doc, ChartType.PIE);
    data.forEach(chart.getSeries()::add);
    chart.setTitle(title);
    return chart;
}
```

Τώρα μπορείτε να καλέσετε `doc.getFirstSection().getBody().appendChild(createPieChart(...));` για κάθε σύνολο δεδομένων, διατηρώντας τον κώδικά σας DRY (Don’t Repeat Yourself).

## Συμπέρασμα

Τώρα ξέρετε πώς να **δημιουργήσετε διάγραμμα πίτας** μέσα σε ένα έγγραφο Word, να το γεμίσετε με δεδομένα και να **αποθηκεύσετε το docx ως PDF** χρησιμοποιώντας Java. Αυτό το ολοκληρωμένο παράδειγμα καλύπτει όλη τη ροή εργασίας **convert word to pdf**, απαντά στο **how to add chart** και δείχνει πώς να **how to create chart** προγραμματιστικά.  

Από εδώ μπορείτε να εξερευνήσετε:

* Προσθήκη ραβδογράμματος ή γραμμικού διαγράμματος (`ChartType.BAR`, `ChartType.LINE`) – άλλη περίπτωση **how to create chart**.  
* Εξαγωγή σε άλλες μορφές όπως PNG ή HTML (`SaveFormat.PNG`, `SaveFormat.HTML`).  
* Δυναμική δημιουργία του εγγράφου εισόδου με πίνακες ή placeholders πριν την εισαγωγή διαγραμμάτων.

Δοκιμάστε διαφορετικά σύνολα δεδομένων, επιλογές στυλ ή ακόμη και την ενσωμάτωση πολλαπλών διαγραμμάτων ανά σελίδα. Καλή προγραμματιστική!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [How to insert a pie chart into a Word document using Java](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [How to save word as pdf and create accessible PDF in Java](/words/english/java/document-conversion-and-export/create-accessible-pdf-from-docx-in-java-full-guide/)
- [How to create chart in Word with Java and Aspose.Words](/words/english/java/using-document-elements/how-to-create-chart-in-word-with-java-and-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}