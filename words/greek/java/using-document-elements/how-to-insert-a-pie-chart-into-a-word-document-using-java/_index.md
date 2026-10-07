---
category: general
date: 2026-09-27
description: Μάθετε πώς να εισάγετε διάγραμμα πίτας σε ένα έγγραφο Word με Java, να
  δημιουργήσετε διάγραμμα πίτας στο Word και να εμφανίσετε τα ποσοστά στο διάγραμμα
  πίτας για σαφή κατανόηση των δεδομένων.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- create pie chart in word
- show percentages on pie chart
- add chart to word document
- how to add leader lines
language: el
lastmod: 2026-09-27
og_description: Πώς να εισάγετε διάγραμμα πίτας σε έγγραφο Word με Java. Αυτός ο οδηγός
  σας δείχνει πώς να δημιουργήσετε διάγραμμα πίτας στο Word, να εμφανίσετε τα ποσοστά
  στο διάγραμμα πίτας και να προσθέσετε γραμμές οδηγίας.
og_image_alt: Screenshot of a formatted pie chart inserted into a Word document
og_title: Πώς να εισάγετε ένα διάγραμμα πίτας σε ένα έγγραφο Word χρησιμοποιώντας
  Java
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  headline: How to insert a pie chart into a Word document using Java
  type: TechArticle
- description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  name: How to insert a pie chart into a Word document using Java
  steps:
  - name: Expected output
    text: '![Formatted pie chart in Word](/images/pie-formatted.png){: .center-image
      alt="Formatted pie chart inserted into a Word document"}'
  - name: Changing slice values
    text: 'If you need custom data, replace the default series values:'
  - name: Multiple series (donut chart)
    text: While a simple pie chart has one series, Aspose.Words also supports donut
      charts with multiple series. Switch `ChartType.PIE` to `ChartType.DONUT` and
      repeat the series‑configuration steps.
  - name: Exporting to PDF
    text: If your downstream workflow requires PDF, call `doc.save("output/PieFormatted.pdf");`
      after the chart is built. The visual layout remains identical.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word automation
- Chart
title: Πώς να εισάγετε ένα διάγραμμα πίτας σε ένα έγγραφο Word χρησιμοποιώντας Java
url: /el/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να εισαγάγετε ένα διάγραμμα πίτας σε ένα έγγραφο Word χρησιμοποιώντας Java

Αν χρειάζεστε **how to insert pie chart** σε ένα αρχείο Word, αυτός ο οδηγός σας καθοδηγεί μέσα από τη διαδικασία από την αρχή μέχρι το τέλος. Θα δείτε πώς να **create pie chart in Word**, να εμφανίσετε τα ποσοστά σε κάθε φέτα και να προσθέσετε γραμμές οδηγούς για ένα επαγγελματικό αποτέλεσμα.

Η αυτοματοποίηση του Word συχνά φαίνεται βαριά, αλλά με το Aspose.Words for Java μπορείτε να δημιουργήσετε πλήρως μορφοποιημένα έγγραφα προγραμματιστικά. Στο τέλος αυτού του σεμιναρίου θα έχετε ένα εκτελέσιμο απόσπασμα Java που παράγει ένα έγγραφο Word που περιέχει ένα στυλιζαρισμένο διάγραμμα πίτας.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

- Εγκατεστημένη Java 17 ή νεότερη
- Maven ή Gradle για τη διαχείριση εξαρτήσεων
- Aspose.Words for Java (έκδοση 23.11 ή νεότερη) προστιθέμενο στο έργο σας
- Βασική εξοικείωση με τη σύνταξη της Java

Δεν απαιτείται προηγούμενη εμπειρία με APIs διαγραμμάτων· τα παρακάτω βήματα καλύπτουν τα πάντα, από τη ρύθμιση του έργου μέχρι το τελικό αποτέλεσμα.

## Βήμα 1: Ρύθμιση της εξάρτησης Maven

Προσθέστε τη βιβλιοθήκη Aspose.Words στο `pom.xml`. Αυτή η μοναδική εξάρτηση σας δίνει πρόσβαση στα `Document`, `DocumentBuilder` και τις κλάσεις διαγραμμάτων.

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.11</version>
</dependency>
```

Αν χρησιμοποιείτε Gradle, το ισοδύναμο είναι:

```groovy
implementation 'com.aspose:aspose-words:23.11'
```

> **Συμβουλή:** Χρησιμοποιήστε την πιο πρόσφατη σταθερή έκδοση για να επωφεληθείτε από διορθώσεις σφαλμάτων και νέες δυνατότητες διαγραμμάτων.

## Βήμα 2: Δημιουργία νέου εγγράφου και builder

Το αντικείμενο `Document` αντιπροσωπεύει το αρχείο Word, ενώ το `DocumentBuilder` σας επιτρέπει να εισάγετε περιεχόμενο. Αυτό αποτελεί τη βάση για **add chart to word document**.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Ο builder είναι τώρα έτοιμος να τοποθετήσει αντικείμενα οπουδήποτε στο έγγραφο.

## Βήμα 3: Εισαγωγή διαγράμματος πίτας

Το Aspose.Words υποστηρίζει πολλούς τύπους διαγραμμάτων· επιλέγουμε το `ChartType.PIE`. Το μέγεθος εκφράζεται σε points (1 point = 1/72 ίντσα).

```java
        // Step 3: Insert a pie chart with a size of 400x300 points
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

Σε αυτό το στάδιο το διάγραμμα περιέχει μια προεπιλεγμένη σειρά δεδομένων με τιμές placeholder. Μπορείτε να αντικαταστήσετε αυτές τις τιμές αργότερα, αν χρειαστεί.

## Βήμα 4: Πρόσβαση στη σειρά του διαγράμματος

Ένα διάγραμμα πίτας έχει μία σειρά που κρατά τις τιμές των φετών. Ανακτήστε την για να εφαρμόσετε μορφοποίηση.

```java
        // Step 4: Get the first (and only) series
        ChartSeries series = chart.getSeries().get(0);
```

## Βήμα 5: Εκτόξευση της πρώτης φέτας

Η εκτόξευση μιας φέτας τραβά την προσοχή σε ένα συγκεκριμένο σημείο δεδομένων. Αυτό είναι ένα κοινό οπτικό σήμα όταν θέλετε να τονίσετε ένα βασικό μέτρο.

```java
        // Step 5: Explode the first slice
        series.setExploded(true);
```

## Βήμα 6: Εμφάνιση ποσοστών σε κάθε φέτα

Η εμφάνιση ποσοστών απευθείας στο διάγραμμα βελτιώνει την κατανόηση των δεδομένων. Αυτό ικανοποιεί την απαίτηση **show percentages on pie chart**.

```java
        // Step 6: Show percentages on each slice
        series.setShowPercentage(true);
```

## Βήμα 7: Προσθήκη γραμμών οδηγών για πιο καθαρές ετικέτες

Οι γραμμές οδηγούς συνδέουν τις ετικέτες των φετών με τα αντίστοιχα τμήματά τους, εξαλείφοντας την ασάφεια. Αυτό εκπληρώνει το **how to add leader lines**.

```java
        // Step 7: Add leader lines so labels are clearly connected
        series.setShowLeaderLines(true);
```

## Βήμα 8: Αποθήκευση του εγγράφου

Τέλος, γράψτε το έγγραφο στον δίσκο. Μπορείτε να επιλέξετε οποιονδήποτε φάκελο έχετε δικαίωμα εγγραφής.

```java
        // Step 8: Save the document with the formatted pie chart
        doc.save("output/PieFormatted.docx");
    }
}
```

Η εκτέλεση του προγράμματος δημιουργεί το `output/PieFormatted.docx`. Ανοίξτε το αρχείο στο Microsoft Word και θα δείτε ένα διάγραμμα πίτας όπου:

- Η πρώτη φέτα είναι εκτοξευμένη.
- Κάθε φέτα εμφανίζει την τιμή του ποσοστού.
- Οι γραμμές οδηγούς δείχνουν από τα ποσοστά στις αντίστοιχες φέτες.

### Αναμενόμενο αποτέλεσμα

![Διαμορφωμένο διάγραμμα πίτας σε Word](/images/pie-formatted.png){: .center-image alt="Διαμορφωμένο διάγραμμα πίτας που εισήχθη σε ένα έγγραφο Word"}

Το στιγμιότυπο (το κείμενο alt χρησιμοποιεί τη βασική λέξη-κλειδί) απεικονίζει την τελική εμφάνιση: ένα καθαρό, δεδομένα‑οδηγούμενο διάγραμμα πίτας έτοιμο για αναφορές, προτάσεις ή πίνακες ελέγχου.

## Συνηθισμένες παραλλαγές και ειδικές περιπτώσεις

### Αλλαγή τιμών φετών

Αν χρειάζεστε προσαρμοσμένα δεδομένα, αντικαταστήστε τις προεπιλεγμένες τιμές της σειράς:

```java
double[] values = {30, 45, 25};
String[] categories = {"Apples", "Bananas", "Cherries"};
series.getDataLabelCollection().clear(); // remove placeholder labels

for (int i = 0; i < values.length; i++) {
    series.getData().add(values[i]);
    series.getCategory().add(categories[i]);
}
```

### Πολλαπλές σειρές (διάγραμμα ντόνατ)

Ενώ ένα απλό διάγραμμα πίτας έχει μία σειρά, το Aspose.Words υποστηρίζει επίσης διαγράμματα ντόνατ με πολλαπλές σειρές. Αλλάξτε το `ChartType.PIE` σε `ChartType.DONUT` και επαναλάβετε τα βήματα διαμόρφωσης της σειράς.

### Εξαγωγή σε PDF

Αν η επόμενη διαδικασία σας απαιτεί PDF, καλέστε `doc.save("output/PieFormatted.pdf");` μετά την κατασκευή του διαγράμματος. Η οπτική διάταξη παραμένει αμετάβλητη.

## Πλήρης λίστα πηγαίου κώδικα

Παρακάτω βρίσκεται το πλήρες, αυτόνομο αρχείο Java που μπορείτε να αντιγράψετε‑και‑επικολλήσετε στο IDE σας.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300‑point pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Access the single series in the pie chart
        ChartSeries series = chart.getSeries().get(0);

        // Explode the first slice for emphasis
        series.setExploded(true);

        // Show percentages on each slice
        series.setShowPercentage(true);

        // Add leader lines for clear label connections
        series.setShowLeaderLines(true);

        // Save the document
        doc.save("output/PieFormatted.docx");
    }
}
```

Συγκεντρώστε και εκτελέστε το πρόγραμμα με `mvn compile exec:java -Dexec.mainClass=PieChartExample` (ή την ισοδύναμη εντολή Gradle). Το παραγόμενο αρχείο Word θα περιέχει το πλήρως μορφοποιημένο διάγραμμα πίτας.

## Συμπέρασμα

Τώρα ξέρετε **how to insert pie chart** σε ένα έγγραφο Word χρησιμοποιώντας Java, πώς να **create pie chart in Word**, πώς να **show percentages on pie chart**, και πώς να **add chart to word document** με γραμμές οδηγούς. Το πλήρες παράδειγμα δείχνει κάθε βήμα, εξηγεί γιατί ο κώδικας είναι γραμμένος έτσι και παρέχει συμβουλές για προσαρμογή.

Στη συνέχεια, μπορείτε να εξερευνήσετε:

- Προσθήκη ετικετών δεδομένων με προσαρμοσμένες γραμματοσειρές (**show percentages on pie chart** παραλλαγές)
- Συνδυασμό πολλαπλών διαγραμμάτων σε ένα μόνο έγγραφο (**add chart to word document** χρήση)
- Αυτοματοποίηση δημιουργίας αναφορών με πίνακες και διαγράμματα μαζί

Μη διστάσετε να πειραματιστείτε με χρώματα, σειρά φετών ή εξαγωγή σε PDF. Καλή προγραμματιστική διασκέδαση!

## Τι πρέπει να μάθετε στη συνέχεια;

Οι παρακάτω οδηγοί καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε επιπλέον δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να δημιουργήσετε διάγραμμα στήλης χρησιμοποιώντας το Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Απόκρυψη άξονα διαγράμματος σε έγγραφο Word](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Δημιουργία γραμμικού διαγράμματος σε Word χρησιμοποιώντας το Aspose.Words for .NET](/words/english/net/working-with-charts/create-chart-using-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}