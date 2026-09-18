---
category: general
date: 2026-09-18
description: Μάθετε πώς να δημιουργήσετε ένα ακτινικό γράφημα σε ένα έγγραφο Word
  χρησιμοποιώντας Java, να προσθέσετε ετικέτες δεδομένων στο γράφημα και να εισάγετε
  δεδομένα σειράς με ένα πλήρες παράδειγμα κώδικα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- add chart data labels
- add series data
- create blank word
- how to insert chart
language: el
lastmod: 2026-09-18
og_description: Δημιουργήστε ακτινικό γράφημα σε ένα έγγραφο Word χρησιμοποιώντας
  Java, προσθέστε ετικέτες δεδομένων του γραφήματος και εισάγετε δεδομένα σειράς σε
  έναν ενιαίο οδηγό.
og_image_alt: Radial chart displayed inside a generated Word document
og_title: Δημιουργία ακτινικού διαγράμματος στο Word με Java – βήμα‑βήμα οδηγός
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn how to create radial chart in a Word document using Java, add
    chart data labels, and insert series data with a complete code example.
  headline: How to create radial chart in a Word document with Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Chart
- Word automation
title: Πώς να δημιουργήσετε ακτινικό γράφημα σε έγγραφο Word με Java
url: /el/java/using-document-elements/how-to-create-radial-chart-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε ακτινικό γράφημα σε έγγραφο Word με Java

Αν χρειάζεστε να δημιουργήσετε ακτινικό γράφημα σε έγγραφο Word, αυτός ο οδηγός σας δείχνει τα ακριβή βήματα. Θα μάθετε επίσης πώς να προσθέσετε ετικέτες δεδομένων στο γράφημα και να εισάγετε δεδομένα σειράς ώστε το γράφημα να είναι έτοιμο για παρουσίαση.

Η δημιουργία γραφήματος προγραμματιστικά αφαιρεί την ανάγκη για χειροκίνητη μορφοποίηση και εγγυάται συνέπεια μεταξύ των αναφορών. Το tutorial υποθέτει ότι έχετε βασικές γνώσεις Java και μια πρόσφατη έκδοση της βιβλιοθήκης Aspose.Words for Java εγκατεστημένη.

## Τι θα χρειαστείτε

* Java 17 ή νεότερη  
* Aspose.Words for Java (έκδοση 23.12 ή νεότερη)  
* Ένα IDE ή εργαλείο κατασκευής που μπορεί να επιλύσει εξαρτήσεις Maven/Gradle  

Η εγκατάσταση αυτών των προαπαιτούμενων σας επιτρέπει να εκτελέσετε το παράδειγμα χωρίς πρόσθετη διαμόρφωση.

## Πώς να δημιουργήσετε ακτινικό γράφημα σε έγγραφο Word

Το πρώτο βήμα είναι να δημιουργήσετε ένα κενό αρχείο Word που θα φιλοξενήσει το γράφημα. Ένα κενό έγγραφο παρέχει καθαρό καμβά και αποφεύγει ανεπιθύμητες μορφές.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;

/* Step 1: Create a new blank Word document */
Document doc = new Document();

/* Step 2: Open a builder to add content */
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` αντιπροσωπεύει ολόκληρο το αρχείο .docx, ενώ το `DocumentBuilder` παρέχει μεθόδους για την εισαγωγή στοιχείων όπως παραγράφους, πίνακες και γραφήματα.

## Πώς να εισαγάγετε γράφημα

Στη συνέχεια εισάγετε το ίδιο το γράφημα. Η μέθοδος `insertChart` δημιουργεί ένα αντικείμενο γραφήματος και το τοποθετεί στη τρέχουσα θέση του δρομέα του builder.

```java
import com.aspose.words.Chart;
import com.aspose.words.ChartType;

/* Step 3: Insert a polar (radial) chart with a width of 400 pt and height of 300 pt */
Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);
```

Ένα πολικό γράφημα αποτυπώνει τα σημεία δεδομένων γύρω από έναν κεντρικό άξονα, κάτι ιδανικό για την εμφάνιση κυκλικών πληροφοριών. Οι διαστάσεις εκφράζονται σε σημεία (1 pt ≈ 1/72 inch).

## Προσθήκη δεδομένων σειράς στο γράφημα

Ένα γράφημα χωρίς δεδομένα σειράς είναι κενό. Μπορείτε να προσθέσετε μια σειρά χειροκίνητα ή να τη συνδέσετε με πηγή δεδομένων. Το παρακάτω παράδειγμα προσθέτει μία σειρά με τρία σημεία δεδομένων.

```java
import com.aspose.words.ChartSeries;
import java.util.Arrays;

/* Step 4: Add a series and populate it with values */
ChartSeries series = chart.getSeries().add("Sample Series",
        Arrays.asList("Jan", "Feb", "Mar"),
        Arrays.asList(30.0, 45.0, 25.0));
```

`add` λαμβάνει το όνομα της σειράς, μια λίστα ετικετών κατηγοριών και μια λίστα αντίστοιχων αριθμητικών τιμών. Μπορείτε να επαναλάβετε αυτό το μπλοκ για να προσθέσετε επιπλέον σειρές (`addSeriesData`).

## Προσθήκη ετικετών δεδομένων στο γράφημα για την πρώτη σειρά

Οι ετικέτες δεδομένων κάνουν το γράφημα αναγνώσιμο χωρίς να χρειάζεται να περάσετε το ποντίκι πάνω στα σημεία. Η παρακάτω γραμμή ενεργοποιεί τις ετικέτες τιμών για την πρώτη σειρά.

```java
/* Step 5: Show the numeric values as data labels */
chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);
```

Ορίζοντας `showValue` σε `true` εμφανίζει την τιμή κάθε σημείου απευθείας στο γράφημα. Μπορείτε επίσης να ενεργοποιήσετε ονόματα κατηγοριών, ποσοστά ή γραμμές οδηγού μέσω του ίδιου αντικειμένου `DataLabelFormat`.

## Αποθήκευση του αρχείου Word

Αφού το γράφημα διαμορφωθεί, γράψτε το έγγραφο στο δίσκο. Επιλέξτε μια θέση που η εφαρμογή σας μπορεί να προσπελάσει.

```java
/* Step 6: Save the document containing the radial chart */
doc.save("output/RadialChart.docx");
```

Το αρχείο `RadialChart.docx` τώρα περιέχει ένα πλήρως λειτουργικό ακτινικό γράφημα με ετικέτες δεδομένων.

## Πλήρες λειτουργικό παράδειγμα

Παρακάτω υπάρχει ένα αυτόνομο πρόγραμμα που μπορείτε να αντιγράψετε, να μεταγλωττίσετε και να εκτελέσετε. Δείχνει τη συνολική ροή εργασίας από τη δημιουργία ενός κεντρικού εγγράφου Word μέχρι την αποθήκευση ενός ακτινικού γραφήματος με ετικέτες δεδομένων.

```java
import com.aspose.words.*;

import java.util.Arrays;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Create a new blank Word document
        Document doc = new Document();

        // Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a polar (radial) chart with the desired dimensions
        Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);

        // Add a series and populate it with sample data
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                Arrays.asList("Q1", "Q2", "Q3", "Q4"),
                Arrays.asList(15000.0, 23000.0, 18000.0, 21000.0));

        // Show the numeric values as data labels for the first series
        chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);

        // Save the document containing the chart
        doc.save("output/RadialChart.docx");
    }
}
```

**Αναμενόμενο αποτέλεσμα**

Όταν ανοίξετε το `output/RadialChart.docx` στο Microsoft Word, θα δείτε ένα ακτινικό γράφημα με τίτλο *Quarterly Sales*. Κάθε σημείο εμφανίζει την αριθμητική του τιμή (π.χ., “15000”) δίπλα στο δείκτη.

## Κοινές παραλλαγές και ειδικές περιπτώσεις

| Κατάσταση | Συνιστώμενη αλλαγή |
|-----------|--------------------|
| Χρειάζεστε διαφορετικό τύπο γραφήματος | Αντικαταστήστε το `ChartType.POLAR` με οποιαδήποτε άλλη τιμή του enum `ChartType` (π.χ., `ChartType.COLUMN`). |
| Το γράφημα πρέπει να χρησιμοποιεί εξωτερικό εύρος Excel | Χρησιμοποιήστε `chart.setDataRange("Sheet1!A1:B5")` μετά τη δημιουργία του γραφήματος και τη φόρτωση του φύλλου εργασίας. |
| Θέλετε να κρύψετε το υπόμνημα | `chart.getLegend().setVisible(false);` |
| Το έγγραφο πρέπει να αποθηκευτεί ως PDF | Καλέστε `doc.save("RadialChart.pdf");` – το Aspose.Words μετατρέπει αυτόματα το γράφημα. |

Αυτές οι προσαρμογές διατηρούν τη βασική λογική αμετάβλητη ενώ προσαρμόζουν το αποτέλεσμα σε συγκεκριμένες απαιτήσεις.

## Συμβουλές επαγγελματιών

* **Επαναχρησιμοποίηση του builder** – Μπορείτε να εισάγετε πολλαπλά γραφήματα στο ίδιο έγγραφο καλώντας επανειλημμένα το `builder.insertChart`.  
* **Απόδοση** – Όταν δημιουργείτε πολλά γραφήματα, δημιουργήστε μία μόνο παρουσία του `DocumentBuilder` και επαναχρησιμοποιήστε την για να μειώσετε το κόστος κατανομής αντικειμένων.  
* **Στυλ** – Η εμφάνιση του γραφήματος (χρώματα, πάχος γραμμής) ελέγχεται μέσω των μεθόδων του αντικειμένου `Chart` όπως `getSeries().get(i).getFormat()`. Πειραματιστείτε με αυτές τις ρυθμίσεις για να ταιριάξετε την εταιρική σας ταυτότητα.

## Συμπέρασμα

Τώρα γνωρίζετε πώς να δημιουργήσετε ακτινικό γράφημα σε έγγραφο Word με Java, να προσθέσετε δεδομένα σειράς και ετικέτες δεδομένων πριν αποθηκεύσετε το αρχείο. Το πλήρες παράδειγμα μπορεί να επεκταθεί για να διαχειριστεί επιπλέον σειρές, προσαρμοσμένα στυλ ή εναλλακτικές μορφές εξόδου.

Εξερευνήστε σχετικά θέματα όπως **πώς να εισαγάγετε γράφημα** από εξωτερικές πηγές δεδομένων, **δημιουργία κενών εγγράφων Word** με προκαθορισμένα πρότυπα, και **προσθήκη δεδομένων σειράς** δυναμικά από βάσεις δεδομένων. Πειραματιστείτε με διαφορετικούς τύπους γραφημάτων για να ανακαλύψετε ποια οπτική παρουσίαση επικοινωνεί καλύτερα τα δεδομένα σας.

## Τι πρέπει να μάθετε στη συνέχεια;

Οι παρακάτω οδηγίες καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να δημιουργήσετε γράφημα στήλης χρησιμοποιώντας το Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Δημιουργία εγγράφου Word Java – Προσθήκη σχήματος ορθογωνίου με εφέ σκιάς](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Ορισμός προεπιλεγμένων επιλογών για ετικέτες δεδομένων σε γράφημα](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}