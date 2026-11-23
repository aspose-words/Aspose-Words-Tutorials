---
category: general
date: 2026-11-22
description: Μάθετε πώς να προσθέτετε σχήμα στο Word χρησιμοποιώντας το Aspose.Words
  for Java – εισάγετε ένα ορθογώνιο και κρύψτε το προγραμματιστικά.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shape to word
- how to insert shape
- how to hide shape
- hide shape in word
language: el
lastmod: 2026-11-22
og_description: Προσθέστε σχήμα στο Word χρησιμοποιώντας το Aspose.Words for Java.
  Αυτό το σεμινάριο δείχνει πώς να εισάγετε ένα ορθογώνιο, να κρύψετε το σχήμα και
  να αποθηκεύσετε το έγγραφο.
og_image_alt: Screenshot of Java code that adds and hides a shape in a Word document
og_title: Προσθήκη σχήματος στο Word με το Aspose.Words – Οδηγός Java
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  headline: How to add shape to Word documents with Aspose.Words for Java
  type: TechArticle
- description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  name: How to add shape to Word documents with Aspose.Words for Java
  steps:
  - name: Expected output
    text: '* The file `output.docx` opens without any visible shapes. * If you inspect
      the document with Aspose.Words (e.g., `doc.getChildNodes(NodeType.SHAPE, true).size()`),
      the shape count will be **1**, confirming that the shape exists but is hidden.'
  - name: 1. Creating a shape in a fresh document
    text: 'If you start from scratch, replace the load line with:'
  - name: 2. Positioning the shape precisely
    text: 'By default, `insertShape` places the shape at the current cursor location.
      To position it absolutely:'
  - name: 3. Controlling visibility per output format
    text: 'If you need the shape visible in the Word UI but hidden when exporting
      to PDF, use `Shape.setWrapType(WrapType.NONE)` together with `Hidden`:'
  - name: 4. Adding text inside the shape
    text: 'A rectangle can contain a text frame:'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Shape handling
title: Πώς να προσθέσετε σχήμα σε έγγραφα Word με το Aspose.Words για Java
url: /el/java/images-shapes/how-to-add-shape-to-word-documents-with-aspose-words-for-jav/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να προσθέσετε σχήμα σε έγγραφα Word με το Aspose.Words for Java

Αν χρειάζεστε **προσθήκη σχήματος σε Word** έγγραφα προγραμματιστικά, το Aspose.Words for Java το καθιστά απλό. Σε αυτόν τον οδηγό θα μάθετε **πώς να εισάγετε σχήμα**, να ελέγξετε την ορατότητά του, και **πώς να κρύψετε σχήμα** ώστε το τελικό αρχείο να φαίνεται ακριβώς όπως το περιμένετε.

Θα περάσετε από ένα πλήρες, εκτελέσιμο παράδειγμα που φορτώνει ένα υπάρχον `.docx`, εισάγει ένα ορθογώνιο, το κρύβει και αποθηκεύει το αποτέλεσμα. Δεν απαιτούνται εξωτερικά scripts ή χειροκίνητα βήματα, και το tutorial καλύπτει κοινές παραλλαγές όπως η δημιουργία νέου εγγράφου από το μηδέν ή η απόκρυψη ενός σχήματος μόνο κατά την εκτύπωση.

## Προαπαιτούμενα

* Java 17 (ή νεότερη) εγκατεστημένη – οι παλαιότερες εκδόσεις λειτουργούν αλλά η πιο πρόσφατη LTS προσφέρει καλύτερη απόδοση.  
* Maven 3.8+ για διαχείριση εξαρτήσεων.  
* Έγκυρη άδεια Aspose.Words for Java (η δωρεάν αξιολόγηση λειτουργεί για μάθηση).  
* Ένα IDE ή κειμενογράφο της επιλογής σας (π.χ., IntelliJ IDEA, VS Code).

## Βήμα 1: Προσθέστε το Aspose.Words στο Maven project σας

Προσθέστε την ακόλουθη εξάρτηση στο `pom.xml`. Αυτό θα φέρει την πιο πρόσφατη σταθερή έκδοση (από τον Νοέμβριο 2026).

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

> **Συμβουλή:** Χρησιμοποιήστε μια δήλωση `<scope>provided</scope>` εάν σκοπεύετε να διανείμετε το JAR με τη δική σας λογική αδειοδότησης.

## Προσθήκη σχήματος σε Word – αρχικοποίηση του εγγράφου

Το πρώτο λειτουργικό βήμα είναι η λήψη ενός αντικειμένου `Document`. Μπορείτε είτε να φορτώσετε ένα υπάρχον αρχείο είτε να δημιουργήσετε ένα καινούργιο.

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document (or create a new one)
        Document doc = new Document("input.docx");   // <-- replace with your path
        // If you prefer a blank document, use:
        // Document doc = new Document();
```

*Γιατί είναι σημαντικό*: Η κλάση `Document` είναι το σημείο εισόδου για όλες τις επεμβάσεις σε Word. Η φόρτωση ενός υπάρχοντος αρχείου διατηρεί τα στυλ, τις κεφαλίδες και τα υποσέλιδα, ενώ ένα νέο έγγραφο σας δίνει καθαρό καμβά.

## Πώς να εισάγετε σχήμα σε έγγραφο Word

Στη συνέχεια, δημιουργήστε ένα `DocumentBuilder` για να τροποποιήσετε το περιεχόμενο του εγγράφου. Ο builder παρέχει μεθόδους για εισαγωγή κειμένου, πινάκων και **σχημάτων**.

```java
        // Create a builder attached to the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a rectangle shape with a width of 100 points and height of 50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
```

Η κλήση `insertShape` επιστρέφει ένα αντικείμενο `Shape` που μπορείτε να διαμορφώσετε περαιτέρω (χρώμα, περίγραμμα, κείμενο κ.λπ.). Οι διαστάσεις εκφράζονται σε points (1 pt = 1/72 in).

*Γιατί μπορεί να χρησιμοποιήσετε ένα ορθογώνιο*: Τα ορθογώνια είναι το πιο κοινό δοχείο για σημειώσεις, υδατογραφήματα ή placeholders. Μπορείτε να αντικαταστήσετε το `ShapeType.RECTANGLE` με `ShapeType.ELLIPSE`, `ShapeType.LINE` κ.λπ., για να καλύψετε διαφορετικές οπτικές ανάγκες.

## Πώς να κρύψετε σχήμα σε Word

Μερικές φορές χρειάζεται ένα σχήμα να υπάρχει για υπολογισμούς διάταξης αλλά να μην εμφανίζεται στην τελική απόδοση. Το Aspose.Words παρέχει τη μέθοδο `setHidden(true)` για να το πετύχετε.

```java
        // Hide the shape so it does not appear when the document is opened
        rectangle.setHidden(true);
```

Η σημαία hidden λειτουργεί όπως η επιλογή μορφοποίησης **Hidden** στο Microsoft Word: το σχήμα παραλείπεται από την οπτική διάταξη αλλά εξακολουθεί να συμμετέχει στο μοντέλο αντικειμένων του εγγράφου. Αυτό είναι χρήσιμο για:

* Αποθήκευση μεταδεδομένων ή δεικτών που η εφαρμογή σας διαβάζει αργότερα.  
* Δημιουργία placeholders που αφαιρούνται λίγο πριν τη δημοσίευση.  
* Έλεγχο ορατότητας για διαφορετικές μορφές εξόδου (π.χ., κρύψιμο σε HTML αλλά διατήρηση σε PDF).

> **Σημείωση:** Τα κρυμμένα σχήματα εξακολουθούν να εξάγονται σε PDF εξ ορισμού. Εάν χρειάζεται να παραλειφθούν και από το PDF, ορίστε `rectangle.getWrapType( ) = WrapType.NONE` και προσαρμόστε την ιδιότητα `Hidden` αναλόγως.

## Βήμα 4: Αποθήκευση του τροποποιημένου εγγράφου

Τέλος, αποθηκεύστε τις αλλαγές σε ένα νέο αρχείο.

```java
        // Save the document with the hidden rectangle
        doc.save("output.docx");   // <-- replace with your desired output path
    }
}
```

Όταν ανοίξετε το `output.docx` στο Microsoft Word, το ορθογώνιο δεν θα είναι ορατό, αλλά παραμένει μέρος του δέντρου του εγγράφου. Μπορείτε να επαληθεύσετε την παρουσία του προγραμματιστικά ξαναφορτώνοντας το αρχείο και ελέγχοντας το `Shape.isHidden()`.

### Αναμενόμενο αποτέλεσμα

* Το αρχείο `output.docx` ανοίγει χωρίς κανένα ορατό σχήμα.  
* Εάν ελέγξετε το έγγραφο με το Aspose.Words (π.χ., `doc.getChildNodes(NodeType.SHAPE, true).size()`), ο αριθμός των σχημάτων θα είναι **1**, επιβεβαιώνοντας ότι το σχήμα υπάρχει αλλά είναι κρυφό.

## Προχωρημένες παραλλαγές και ειδικές περιπτώσεις

### 1. Δημιουργία σχήματος σε νέο έγγραφο

Αν ξεκινάτε από το μηδέν, αντικαταστήστε τη γραμμή φόρτωσης με:

```java
Document doc = new Document();          // creates an empty Word file
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Report Title");        // add a title before the shape
```

### 2. Ακριβής τοποθέτηση του σχήματος

Από προεπιλογή, το `insertShape` τοποθετεί το σχήμα στην τρέχουσα θέση του κέρσορα. Για απόλυτη τοποθέτηση:

```java
rectangle.setLeft(72);   // 1 inch from the left margin
rectangle.setTop(144);   // 2 inches from the top of the page
rectangle.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangle.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
```

### 3. Έλεγχος ορατότητας ανά μορφή εξόδου

Εάν χρειάζεστε το σχήμα ορατό στη διεπαφή του Word αλλά κρυφό κατά την εξαγωγή σε PDF, χρησιμοποιήστε το `Shape.setWrapType(WrapType.NONE)` μαζί με το `Hidden`:

```java
rectangle.setHidden(false);                 // visible in Word
rectangle.getParagraph().getParagraphFormat()
        .setPageBreakBefore(true);          // ensure it stays on its own line
// When converting to PDF, hide it programmatically:
if (exportingToPdf) {
    rectangle.setHidden(true);
}
```

### 4. Προσθήκη κειμένου μέσα στο σχήμα

Ένα ορθογώνιο μπορεί να περιέχει ένα πλαίσιο κειμένου:

```java
Shape textBox = builder.insertShape(ShapeType.TEXT_BOX, 200, 50);
textBox.getTextBox().setInternalMarginLeft(5);
textBox.getTextBox().setInternalMarginTop(5);
builder.moveTo(textBox.getFirstParagraph());
builder.write("Confidential");
```

Μπορείτε στη συνέχεια να κρύψετε το πλαίσιο κειμένου με την ίδια κλήση `setHidden(true)`.

## Συνηθισμένα προβλήματα και πώς να τα αποφύγετε

| Συμπτωμα | Αιτία | Διόρθωση |
|----------|-------|----------|
| Το σχήμα εμφανίζεται ακόμη και μετά το `setHidden(true)` | Το έγγραφο αποθηκεύτηκε πριν οριστεί η σημαία hidden. | Βεβαιωθείτε ότι καλείτε το `setHidden(true)` **πριν** το `doc.save()`. |
| Το μέγεθος του σχήματος φαίνεται παραμορφωμένο | Συγχυση μεταξύ points και pixels σε οθόνες υψηλής ανάλυσης. | Χρησιμοποιήστε points (72 pt = 1 in) για συνεπή μέγεθος σε όλες τις πλατφόρμες. |
| Το κρυμμένο σχήμα εξακολουθεί να εκτυπώνεται | Ορισμένοι εκτυπωτές αγνοούν τη σημαία hidden. | Ορίστε `Shape.setWrapType(WrapType.NONE)` και επίσης καθαρίστε το `Shape.getParagraph().getParagraphFormat().setPageBreakBefore(false)`. |

## Συμπέρασμα

Τώρα ξέρετε πώς να **προσθέσετε σχήμα σε Word** έγγραφα χρησιμοποιώντας το Aspose.Words for Java, **πώς να εισάγετε σχήμα**, και **πώς να κρύψετε σχήμα** ώστε να παραμένει αόρατο για τους τελικούς χρήστες ενώ εξακολουθεί να αποτελεί μέρος της δομής του εγγράφου. Το πλήρες παράδειγμα παραπάνω φορτώνει ένα αρχείο, εισάγει ένα ορθογώνιο, το κρύβει και αποθηκεύει το αποτέλεσμα, καλύπτοντας τόσο τυπικές περιπτώσεις χρήσης όσο και αρκετές ειδικές περιπτώσεις.

Από εδώ μπορείτε να εξερευνήσετε σχετικά θέματα όπως **πώς να εισάγετε σχήμα** με προσαρμοσμένα χρώματα γεμίσματος, **πώς να κρύψετε σχήμα σε Word** για υπό όρους εκτύπωση, ή αυτοματοποίηση μαζικής επεξεργασίας εγγράφων με το Aspose.Words. Πειραματιστείτε με διαφορετικές τιμές `ShapeType`, επιλογές τοποθέτησης και σημαίες ορατότητας για να ταιριάζουν στη δική σας ροή εργασίας.

Καλό προγραμματισμό, και απολαύστε την ευελιξία που προσφέρει η προγραμματιστική διαχείριση Word στις Java εφαρμογές σας!

## Τι Θα Πρέπει Να Μάθετε Στη Σύντομη Μελλοντική Περίοδο;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Δημιουργήστε ένα έγγραφο Word προγραμματιστικά, προσθέστε και κρύψτε ένα σχήμα σε Java χρησιμοποιώντας το Aspose.Words](/words/english/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/)
- [Πώς να κρύψετε σχήμα σε έγγραφο Word χρησιμοποιώντας Java](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Δημιουργήστε ένα κενό έγγραφο .docx Word και προσθέστε ένα κρυφό ορθογώνιο σχήμα με το Aspose.Words](/words/english/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}