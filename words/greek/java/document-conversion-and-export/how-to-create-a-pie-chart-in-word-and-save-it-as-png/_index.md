---
category: general
date: 2026-10-07
description: Μάθετε πώς να δημιουργήσετε ένα διάγραμμα πίτας στο Word, να προσθέσετε
  σειρά δεδομένων και να αποθηκεύσετε το διάγραμμα ως PNG χρησιμοποιώντας Java. Ακολουθήστε
  τον οδηγό βήμα‑βήμα για γρήγορα αποτελέσματα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add data series
- save chart as png
- generate pie chart in word
- save word chart as image
language: el
lastmod: 2026-10-07
og_description: 'Δημιουργήστε γρήγορα διάγραμμα πίτας στο Word: αυτό το σεμινάριο
  δείχνει πώς να προσθέσετε σειρά δεδομένων, να δημιουργήσετε το διάγραμμα και να
  αποθηκεύσετε το διάγραμμα του Word ως εικόνα (PNG). Ακολουθήστε το πλήρες παράδειγμα
  κώδικα.'
og_image_alt: Screenshot of a create pie chart result in a Word document
og_title: Δημιουργία διαγράμματος πίτας στο Word και εξαγωγή ως PNG – οδηγός
schemas:
- author: GroupDocs
  dateModified: '2026-10-07'
  description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  headline: How to create a pie chart in Word and save it as PNG
  type: TechArticle
- description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  name: How to create a pie chart in Word and save it as PNG
  steps:
  - name: Load the source document
    text: You must open the Word file that will host the chart. The `Document` class
      reads the `.docx` content into memory.
  - name: Add data series to the chart
    text: Creating a **pie chart** starts with a `Chart` instance. The constructor
      receives the parent `Document` and the chart type (`ChartType.PIE`). After the
      chart object exists, you populate it with numeric values and optional labels.
  - name: Save chart as PNG
    text: Once the chart is part of the document, you can export the visual representation.
      The `save` method on the underlying chart object writes a PNG file to the file
      system.
  type: HowTo
tags:
- Java
- Word automation
- Chart generation
title: Πώς να δημιουργήσετε ένα διάγραμμα πίτας στο Word και να το αποθηκεύσετε ως
  PNG
url: /el/java/document-conversion-and-export/how-to-create-a-pie-chart-in-word-and-save-it-as-png/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε ένα διάγραμμα πίτας στο Word και να το αποθηκεύσετε ως PNG

Αν χρειάζεστε να **δημιουργήσετε διαγράμματα πίτας** μέσα σε ένα αρχείο Microsoft Word, αυτός ο οδηγός σας δείχνει ακριβώς πώς να το κάνετε με Java. Θα μάθετε επίσης πώς να **προσθέσετε σειρές δεδομένων** στο διάγραμμα και να **αποθηκεύσετε το διάγραμμα ως PNG** ώστε η εικόνα να μπορεί να χρησιμοποιηθεί εκτός του Word.

Η δημιουργία διαγράμματος απευθείας σε ένα έγγραφο σας εξοικονομεί την εξαγωγή δεδομένων σε ξεχωριστό εργαλείο γραφικών. Στο τέλος αυτού του οδηγού θα έχετε ένα πλήρως λειτουργικό αρχείο Word που περιέχει ένα διάγραμμα πίτας και μια αντίστοιχη εικόνα PNG στο δίσκο.

## Προαπαιτούμενα

* Java 17 ή νεότερη εγκατεστημένη.
* Το **GroupDocs.Viewer for Java** (ή μια συμβατή βιβλιοθήκη που παρέχει τις κλάσεις `Document`, `Chart`, `ChartType` και `ImageSaveOptions`).
* Ένα έργο Maven ή Gradle όπου μπορείτε να προσθέσετε την εξάρτηση της βιβλιοθήκης.
* Ένα αρχείο Word εισόδου (`input.docx`) τοποθετημένο σε φάκελο που μπορείτε να αναφερθείτε από τον κώδικα.

Αν χρησιμοποιείτε Maven, προσθέστε την εξάρτηση (αντικαταστήστε το `VERSION` με την τελευταία έκδοση):

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-viewer</artifactId>
    <version>VERSION</version>
</dependency>
```

## Πώς να δημιουργήσετε διάγραμμα πίτας στο Word

Ο πυρήνας της λύσης περιστρέφεται γύρω από τρεις ενέργειες:

1. Φορτώστε το πηγαίο αρχείο `.docx`.
2. **Προσθέστε σειρές δεδομένων** σε ένα νέο αντικείμενο `Chart` τύπου `PIE`.
3. **Αποθηκεύστε το διάγραμμα ως PNG** ώστε να λάβετε ένα αρχείο εικόνας δίπλα στο έγγραφο Word.

Κάθε βήμα εξηγείται λεπτομερώς παρακάτω, ακολουθούμενο από τον ακριβή κώδικα Java που χρειάζεστε.

### Βήμα 1: Φόρτωση του πηγαίου εγγράφου

Πρέπει να ανοίξετε το αρχείο Word που θα φιλοξενήσει το διάγραμμα. Η κλάση `Document` διαβάζει το περιεχόμενο του `.docx` στη μνήμη.

```java
// Step 1: Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Γιατί είναι σημαντικό*: Η φόρτωση του εγγράφου δημιουργεί ένα μεταβλητό μοντέλο. Όλες οι επόμενες λειτουργίες διαγράμματος τροποποιούν αυτήν την αναπαράσταση στη μνήμη, την οποία στη συνέχεια αποθηκεύετε ξανά στο δίσκο.

### Βήμα 2: Προσθήκη σειρών δεδομένων στο διάγραμμα

Η δημιουργία ενός **διαγράμματος πίτας** ξεκινά με μια παρουσία `Chart`. Ο κατασκευαστής λαμβάνει το γονικό `Document` και τον τύπο διαγράμματος (`ChartType.PIE`). Αφού το αντικείμενο διαγράμματος υπάρχει, το γεμίζετε με αριθμητικές τιμές και προαιρετικές ετικέτες.

```java
// Step 2: Create a pie chart and configure its data series
Chart chart = new Chart(doc, ChartType.PIE);

// Example: add a data series (replace with your actual data)
double[] values = { 30, 20, 50 };
String[] categories = { "A", "B", "C" };
chart.getSeries().add(values, categories);
```

*Γιατί είναι σημαντικό*: Η μέθοδος `add` **προσθέτει σειρές δεδομένων** στο διάγραμμα. Κάθε καταχώρηση στο `values` γίνεται ένα τμήμα της πίτας, ενώ τα `categories` παρέχουν τις ετικέτες του υπομνήματος. Μπορείτε να δώσετε οποιονδήποτε αριθμό σημείων· η βιβλιοθήκη θα υπολογίσει αυτόματα τις γωνίες των τμημάτων.

### Βήμα 3: Αποθήκευση διαγράμματος ως PNG

Μόλις το διάγραμμα είναι μέρος του εγγράφου, μπορείτε να εξάγετε την οπτική αναπαράσταση. Η μέθοδος `save` στο υποκείμενο αντικείμενο διαγράμματος γράφει ένα αρχείο PNG στο σύστημα αρχείων.

```java
// Step 3: Save the chart as a PNG image (graduations are added automatically)
chart.getChartShape()
     .getChart()
     .save("YOUR_DIRECTORY/radial.png",
           ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

*Γιατί είναι σημαντικό*: Η αποθήκευση του διαγράμματος ως PNG σας παρέχει μια ραστερ εικόνα που μπορεί να ενσωματωθεί σε ιστοσελίδες, email ή αναφορές χωρίς να απαιτείται το αρχικό αρχείο Word. Το αντικείμενο `ImageSaveOptions` σας επιτρέπει να ελέγχετε τη μορφή, την ανάλυση και άλλες ρυθμίσεις εξαγωγής.

## Δημιουργία διαγράμματος πίτας στο Word – προσαρμογή της εμφάνισης

Πέρα από τα βασικά βήματα, ίσως θέλετε να προσαρμόσετε χρώματα, τίτλους ή ετικέτες δεδομένων. Οι περισσότερες βιβλιοθήκες εκθέτουν ένα αντικείμενο `ChartOptions` ή παρόμοιο. Εδώ είναι ένα γρήγορο παράδειγμα που προσθέτει έναν τίτλο και αλλάζει τα χρώματα των τμημάτων:

```java
chart.getChart().setTitle("Sales Distribution Q1");

// Set custom colors (RGB format)
chart.getSeries().get(0).setColors(new int[] {
    0xFF5733, // slice A – orange
    0x33FF57, // slice B – green
    0x3357FF  // slice C – blue
});
```

Αυτές οι προσαρμογές είναι προαιρετικές αλλά δείχνουν πώς μπορείτε να **δημιουργήσετε διάγραμμα πίτας στο Word** που ταιριάζει με την επωνυμία σας.

## Αποθήκευση διαγράμματος Word ως εικόνα – εναλλακτικές προσεγγίσεις

Αν χρειάζεστε μόνο την εικόνα και όχι το διάγραμμα μέσα στο έγγραφο, μπορείτε να παραλείψετε την εισαγωγή του σχήματος διαγράμματος στο αρχείο Word και να καλέσετε απευθείας τη μέθοδο `save` μετά τη δημιουργία του διαγράμματος. Ο κώδικας παραμένει ίδιος· απλώς παραλείπετε τυχόν βήματα που προσθέτουν το διάγραμμα στο σώμα του εγγράφου.

```java
// Directly save the chart without embedding it in the document
chart.getChart().save("YOUR_DIRECTORY/pie_only.png",
                      ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

Αυτή η τεχνική είναι χρήσιμη όταν δημιουργείτε πολλά διαγράμματα σε μια παρτίδα και σας ενδιαφέρει μόνο η έξοδος PNG.

## Πλήρες εκτελέσιμο παράδειγμα

Αντιγράψτε την παρακάτω κλάση στο έργο σας, προσαρμόστε τις διαδρομές αρχείων και εκτελέστε την. Το πρόγραμμα θα:

1. Φορτώσει το `input.docx`.
2. **Δημιουργήσει ένα διάγραμμα πίτας**, **προσθέσει σειρές δεδομένων**, και το ενσωματώσει στο έγγραφο.
3. **Αποθηκεύσει το διάγραμμα ως PNG** (`radial.png`).
4. Αποθηκεύσει το τροποποιημένο αρχείο Word ως `output.docx`.



## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να δημιουργήσετε διάγραμμα στήλης χρησιμοποιώντας το Aspose.Words για Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Δημιουργία Scatter Chart σε Word χρησιμοποιώντας το Aspose.Words για .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Εισαγωγή διαγράμματος στήλης σε Word χρησιμοποιώντας το Aspose.Words για .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}