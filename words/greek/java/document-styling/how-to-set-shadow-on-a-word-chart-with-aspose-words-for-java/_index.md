---
category: general
date: 2026-09-11
description: Πώς να ορίσετε σκιά σε γράφημα Word με το Aspose.Words for Java – μάθετε
  πώς να φορτώνετε ένα έγγραφο Word, να αλλάζετε τα περιγράμματα και να προσαρμόζετε
  την εμφάνιση του γραφήματος.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to set shadow
- how to change border
- modify word chart
- load word document
- set chart border
language: el
lastmod: 2026-09-11
og_description: Πώς να ορίσετε σκιά σε διάγραμμα Word με το Aspose.Words for Java.
  Ακολουθήστε αυτόν τον οδηγό βήμα‑βήμα για να φορτώσετε ένα έγγραφο Word, να αλλάξετε
  το περίγραμμα και να εφαρμόσετε ένα εφέ σκιάς.
og_image_alt: Screenshot of a Word chart with a gray border and a soft shadow applied
og_title: Πώς να ορίσετε σκιά σε γράφημα του Word – πλήρης οδηγός Java
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: How to set shadow on a Word chart with Aspose.Words for Java – learn
    to load a Word document, change borders, and customize chart appearance.
  headline: How to set shadow on a Word chart with Aspose.Words for Java
  type: TechArticle
- description: How to set shadow on a Word chart with Aspose.Words for Java – learn
    to load a Word document, change borders, and customize chart appearance.
  name: How to set shadow on a Word chart with Aspose.Words for Java
  steps:
  - name: Expected result
    text: 'Open `output.docx` in Microsoft Word:'
  - name: What if the document contains multiple charts?
    text: 'The example retrieves the **first** chart. To modify all charts, iterate
      over the filtered list:'
  - name: Does the shadow work for all chart types?
    text: Yes. Aspose.Words applies the shadow at the chart container level, so bar,
      line, and pie charts all receive the effect. However, 3‑D charts may render
      the shadow slightly differently because of their built‑in lighting model.
  - name: How to set a custom shadow color?
    text: The API currently supports a simple on/off toggle (`setShadow(true)`). For
      more advanced shadow styling (color, blur, offset), you would need to convert
      the chart to an image and use a graphics library, which is beyond the scope
      of this tutorial.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: Πώς να ορίσετε σκιά σε γράφημα Word με το Aspose.Words για Java
url: /el/java/document-styling/how-to-set-shadow-on-a-word-chart-with-aspose-words-for-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να ορίσετε σκιά σε ένα γράφημα Word με Aspose.Words για Java

Αν χρειάζεστε **πώς να ορίσετε σκιά σε ένα γράφημα Word** γρήγορα, αυτός ο οδηγός σας δείχνει τα ακριβή βήματα χρησιμοποιώντας το Aspose.Words για Java. Θα μάθετε πώς να **φορτώνετε ένα έγγραφο Word**, να ανακτήσετε το πρώτο γράφημα και στη συνέχεια να εφαρμόσετε τόσο το εφέ σκιάς όσο και ένα προσαρμοσμένο περίγραμμα.

Η βελτίωση του οπτικού στυλ ενός γραφήματος είναι χρήσιμη για αναφορές, παρουσιάσεις ή αυτοματοποιημένες διαδικασίες δημιουργίας εγγράφων. Στο τέλος αυτού του σεμιναρίου θα μπορείτε να **τροποποιήσετε αντικείμενα Word chart**, να αλλάξετε το χρώμα του περιγράμματός τους και να απαντήσετε στην κοινή ερώτηση **πώς να αλλάξετε το περίγραμμα** χωρίς να αφήσετε τον κώδικα Java.

## Προαπαιτούμενα και τι θα δημιουργήσετε

* Java 17 (ή οποιοδήποτε πρόσφατο JDK) εγκατεστημένο.
* Maven ή Gradle για διαχείριση εξαρτήσεων.
* Άδεια Aspose.Words για Java (η δωρεάν δοκιμή λειτουργεί για ανάπτυξη).
* Ένα δείγμα αρχείου Word (`input.docx`) που περιέχει τουλάχιστον ένα γράφημα.

Το τελικό πρόγραμμα θα:

1. **Φορτώσει έγγραφο Word** (`load word document`).
2. Ανακτήσει το πρώτο σχήμα γραφήματος (`modify word chart`).
3. **Ορίσει το περίγραμμα του γραφήματος** σε γκρι (`set chart border`).
4. Εφαρμόσει ένα **εφέ σκιάς** (`how to set shadow`).
5. Αποθηκεύσει το τροποποιημένο έγγραφο ως `output.docx`.

## Βήμα 1: Ρύθμιση του έργου και προσθήκη του Aspose.Words

Δημιουργήστε ένα νέο έργο Maven (ή ισοδύναμο Gradle) και προσθέστε την εξάρτηση Aspose.Words:

```xml
<!-- pom.xml -->
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>24.9</version> <!-- use the latest version -->
    </dependency>
</dependencies>
```

> **Συμβουλή:** Αν χρησιμοποιείτε Gradle, το ισοδύναμο είναι `implementation 'com.aspose:aspose-words:24.9'`.

## Βήμα 2: Πώς να φορτώσετε ένα έγγραφο Word και να ανακτήσετε το γράφημα

Η φόρτωση ενός εγγράφου είναι μια μόνο γραμμή κώδικα, αλλά η κατανόηση της ιεραρχίας κόμβων βοηθά όταν χρειάζεται να **τροποποιήσετε word chart** αντικείμενα αργότερα.

```java
import com.aspose.words.*;

public class ChartShadowDemo {
    public static void main(String[] args) throws Exception {
        // Load the Word document that contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        
        // Retrieve the first Shape that is a chart
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true)
                                    .stream()
                                    .filter(node -> ((Shape) node).getShapeType() == ShapeType.CHART)
                                    .findFirst()
                                    .orElseThrow(() -> new IllegalArgumentException("No chart found"));
        
        // Cast the Shape to a Chart object
        Chart chart = chartShape.getChart();
```

*Γιατί είναι σημαντικό*: Η συλλογή `NodeType.SHAPE` μπορεί να περιέχει εικόνες, πλαίσια κειμένου ή γραφήματα. Η φιλτράρισμα με `ShapeType.CHART` εγγυάται ότι εργάζεστε με γράφημα, κάτι που είναι ουσιώδες για **πώς να ορίσετε σκιά** σωστά.

## Βήμα 3: Πώς να ορίσετε σκιά σε ένα γράφημα Word

Το Aspose.Words εκθέτει μια μέθοδο `setShadow(boolean)` στην κλάση `Chart`. Η ενεργοποίηση της σκιάς δίνει στο γράφημα ένα διακριτικό εφέ βάθους.

```java
        // Enable a shadow effect for the chart
        chart.setShadow(true);
```

Όταν το έγγραφο ανοίξει στο Microsoft Word, το γράφημα εμφανίζει τώρα μια ήπια γκρι σκιά γύρω από το περιθώριό του. Αυτή είναι η κύρια απάντηση στο **πώς να ορίσετε σκιά** σε ένα γράφημα.

## Βήμα 4: Πώς να αλλάξετε το περίγραμμα ενός γραφήματος Word

Η αλλαγή του περιγράμματος περιλαμβάνει δύο ιδιότητες:

* `setBorderColor(Color)` – ορίζει το χρώμα.
* `setBorderWidth(double)` – προαιρετικό, ορίζει το πάχος (η προεπιλογή είναι 0,5 pt).

```java
        // Apply a gray border color to the chart
        chart.setBorderColor(java.awt.Color.GRAY);
        // Optionally increase the border width for better visibility
        chart.setBorderWidth(1.0);
```

Αυτές οι γραμμές απαντούν στο **πώς να αλλάξετε το περίγραμμα** και επίσης ικανοποιούν την απαίτηση της λέξης-κλειδί **set chart border**. Το περίγραμμα θα εμφανιστεί γύρω από κάθε φέτα ενός διαγράμματος πίτας ή γύρω από ολόκληρη την περιοχή του γραφήματος για διαγράμματα στήλης.

## Βήμα 5: Πώς να «εξερράγητε» φέτες γραφήματος (προαιρετική οπτική βελτίωση)

Αν και δεν αποτελεί μέρος του κύριου συνόλου λέξεων-κλειδιών, η εξερράγηση φετών είναι μια κοινή οπτική βελτίωση που ταιριάζει καλά με τις σκιές.

```java
        // Explode the chart slices by 10 %
        chart.setExplode(10);
```

## Βήμα 6: Αποθήκευση του τροποποιημένου εγγράφου

Μετά από όλες τις προσαρμογές, γράψτε το έγγραφο πίσω στο δίσκο.

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

Η εκτέλεση του προγράμματος παράγει το `output.docx` όπου το πρώτο γράφημα έχει τώρα ένα γκρι περίγραμμα, μια έκρηξη 10 % και ένα εφέ σκιάς.

### Αναμενόμενο αποτέλεσμα

Ανοίξτε το `output.docx` στο Microsoft Word:

* Το γράφημα εμφανίζει μια ήπια σκιά στη δεξιά πλευρά.
* Ένα λεπτό γκρι περίγραμμα περιβάλλει το γράφημα.
* Εάν προσθέσατε το βήμα εξερράγησης, οι φέτες χωρίζονται ελαφρώς.

![Γράφημα Word με σκιά και γκρι περίγραμμα](https://example.com/placeholder-image.png){alt="Γράφημα Word με σκιά και γκρι περίγραμμα"}

## Συχνές ερωτήσεις και αντιμετώπιση ειδικών περιπτώσεων

### Τι γίνεται αν το έγγραφο περιέχει πολλαπλά γραφήματα;

Το παράδειγμα ανακτά το **πρώτο** γράφημα. Για να τροποποιήσετε όλα τα γραφήματα, επαναλάβετε τη φιλτραρισμένη λίστα:

```java
List<Shape> charts = doc.getChildNodes(NodeType.SHAPE, true).stream()
    .filter(node -> ((Shape) node).getShapeType() == ShapeType.CHART)
    .map(node -> (Shape) node)
    .collect(Collectors.toList());

for (Shape shape : charts) {
    Chart c = shape.getChart();
    c.setShadow(true);
    c.setBorderColor(java.awt.Color.GRAY);
}
```

### Λειτουργεί η σκιά για όλους τους τύπους γραφημάτων;

Ναι. Το Aspose.Words εφαρμόζει τη σκιά στο επίπεδο του περιέκτη του γραφήματος, έτσι ώστε γραφήματα ράβδων, γραμμής και πίτας να λαμβάνουν το εφέ. Ωστόσο, τα 3‑D γραφήματα μπορεί να εμφανίζουν τη σκιά ελαφρώς διαφορετικά λόγω του ενσωματωμένου μοντέλου φωτισμού.

### Πώς να ορίσετε προσαρμοσμένο χρώμα σκιάς;

Το API αυτή τη στιγμή υποστηρίζει μια απλή εναλλαγή on/off (`setShadow(true)`). Για πιο προχωρημένο στυλ σκιάς (χρώμα, θόλωση, μετατόπιση), θα χρειαστεί να μετατρέψετε το γράφημα σε εικόνα και να χρησιμοποιήσετε μια βιβλιοθήκη γραφικών, κάτι που υπερβαίνει το πεδίο αυτού του σεμιναρίου.

## Συμβουλές για κώδικα παραγωγής

* **License early** – καλέστε `License license = new License(); license.setLicense("Aspose.Words.lic");` πριν φορτώσετε το έγγραφο για να αποφύγετε υδατογραφήματα αξιολόγησης.
* **Reuse Document objects** – εάν επεξεργάζεστε πολλά αρχεία σε batch, επαναχρησιμοποιήστε ένα μόνο αντικείμενο `Document` για να μειώσετε την πίεση στο GC.
* **Validate chart existence** – πάντα ελέγχετε για `NoSuchElementException` όταν ένα έγγραφο δεν περιέχει γράφημα· αποτρέπει σφάλματα χρόνου εκτέλεσης.
* **Thread safety** – τα αντικείμενα Aspose.Words δεν είναι thread‑safe. Δημιουργήστε ένα ξεχωριστό `Document` ανά νήμα όταν επεξεργάζεστε παράλληλα.

## Συμπέρασμα

Τώρα γνωρίζετε **πώς να ορίσετε σκιά σε ένα γράφημα Word** χρησιμοποιώντας το Aspose.Words για Java, καθώς και πώς να **αλλάξετε το περίγραμμα**, **φορτώσετε έγγραφο Word**, και **ορίσετε το περίγραμμα του γραφήματος**. Ακολουθώντας τα παραπάνω βήματα, μπορείτε προγραμματιστικά να βελτιώσετε τα οπτικά στοιχεία των γραφημάτων, κάνοντας τις αυτοματοποιημένες αναφορές να φαίνονται επαγγελματικές και καλοσχεδιασμένες.

Έτοιμοι για την επόμενη πρόκληση; Εξερευνήστε **πώς να προσθέσετε ετικέτες δεδομένων**, **να προσαρμόσετε τα χρώματα των γραφημάτων**, ή **να εξάγετε γραφήματα σε εικόνες** – όλα εφικτά με το ίδιο API του Aspose.Words. Καλή προγραμματιστική!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω σεμινάρια καλύπτουν στενά σχετικές θεματικές που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε σε πρόσθετες λειτουργίες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να δημιουργήσετε γράφημα στήλης χρησιμοποιώντας Aspose.Words για Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Δημιουργία εγγράφου Word Java – Προσθήκη σχήματος ορθογωνίου με εφέ σκιάς](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Πώς να ορίσετε LoadOptions στο Aspose.Words για Java](/words/english/java/document-loading-and-saving/using-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}