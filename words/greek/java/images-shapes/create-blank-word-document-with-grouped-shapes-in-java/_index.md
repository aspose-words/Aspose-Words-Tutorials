---
category: general
date: 2026-08-07
description: Δημιουργήστε κενό έγγραφο Word με ομαδοποιημένα σχήματα σε Java χρησιμοποιώντας
  το Aspose.Words. Μάθετε πώς να ομαδοποιείτε σχήματα, να ορίζετε το μέγεθος του σχήματος
  και να προσθέτετε σχήματα στο Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shape
- group shapes word
- set shape size
- add shapes to word
language: el
lastmod: 2026-08-07
og_description: Δημιουργήστε κενό έγγραφο Word με ομαδοποιημένα σχήματα σε Java. Ακολουθήστε
  αυτόν τον οδηγό για να ορίσετε το μέγεθος των σχημάτων, να προσθέσετε σχήματα στο
  Word και να μάθετε πώς να ομαδοποιείτε σχήματα.
og_image_alt: Create blank Word document with grouped shapes using Aspose.Words for
  Java
og_title: Δημιουργήστε κενό έγγραφο Word με ομαδοποιημένα σχήματα – οδηγός Java
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create blank Word document with grouped shapes in Java using Aspose.Words.
    Learn how to group shape, set shape size, and add shapes to Word.
  headline: Create blank Word document with grouped shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word Automation
- Shapes
title: Δημιουργία κενού εγγράφου Word με ομαδοποιημένα σχήματα σε Java
url: /el/java/images-shapes/create-blank-word-document-with-grouped-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία κενής εγγράφου Word με ομαδοποιημένα σχήματα σε Java

Αν χρειάζεστε **να δημιουργήσετε κενό έγγραφο Word** που περιέχει αρκετά σχήματα διατεταγμένα ως μία ενότητα, αυτό το tutorial σας δείχνει ακριβώς πώς. Θα δείτε ένα πλήρες, εκτελέσιμο παράδειγμα που επιδεικνύει **πώς να ομαδοποιήσετε σχήματα**, να προσαρμόσετε τις διαστάσεις τους και **να προσθέσετε σχήματα στο Word** χρησιμοποιώντας το Aspose.Words for Java.

Ο οδηγός περνάει από κάθε βήμα — από τη ρύθμιση του έργου μέχρι την αποθήκευση του τελικού αρχείου .docx — ώστε να μπορείτε να αντιγράψετε τον κώδικα απευθείας στην εφαρμογή σας. Δεν απαιτούνται εξωτερικές αναφορές και η λύση λειτουργεί με Aspose.Words 23.9 ή νεότερη έκδοση.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* Java 17 (ή οποιοδήποτε υποστηριζόμενο JDK)
* Maven ή Gradle για διαχείριση εξαρτήσεων
* Άδεια Aspose.Words for Java (ή προσωρινό κλειδί αξιολόγησης)
* Ένα δείγμα αρχείου εικόνας (π.χ. `sample.jpg`) τοποθετημένο σε γνωστό φάκελο

Αν λείπει κάποιο από αυτά, εγκαταστήστε το πρώτα· το υπόλοιπο tutorial υποθέτει ότι το περιβάλλον είναι έτοιμο.

## Βήμα 1: Προσθήκη Aspose.Words στο έργο σας

Προσθέστε την εξάρτηση Aspose.Words στο `pom.xml` (Maven) ή στο `build.gradle` (Gradle). Αυτή η βιβλιοθήκη παρέχει τις κλάσεις `Document`, `DocumentBuilder`, `GroupShape` και `Shape` που χρησιμοποιούνται αργότερα.

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:23.9'
```

**Γιατί είναι σημαντικό:** Χωρίς τη βιβλιοθήκη, καμία από τις API επεξεργασίας Word δεν είναι διαθέσιμη και δεν μπορείτε **να δημιουργήσετε κενό έγγραφο Word** προγραμματιστικά.

## Βήμα 2: Δημιουργία κενής εγγράφου Word

Η πρώτη συγκεκριμένη ενέργεια είναι η δημιουργία ενός αντικειμένου `Document`, το οποίο αντιπροσωπεύει ένα **κενό έγγραφο Word** στη μνήμη.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new, empty document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*`Document()`* δημιουργεί ένα **κενό έγγραφο Word** με προεπιλεγμένες ρυθμίσεις (σελίδα A4, προεπιλεγμένα περιθώρια). Ο συνοδευτικός `DocumentBuilder` σας επιτρέπει να εισάγετε περιεχόμενο στη τρέχουσα θέση του δρομέα.

## Βήμα 3: Εισαγωγή ομαδοποιημένου σχήματος (πώς να ομαδοποιήσετε σχήματα)

Ένα *ομαδοποιημένο σχήμα* λειτουργεί ως δοχείο για άλλα σχήματα. Σε αυτό το βήμα μαθαίνετε **πώς να ομαδοποιήσετε σχήματα** ώστε να μετακινούνται μαζί.

```java
        // Insert a group shape with a width of 300 points and height of 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

Η μέθοδος `insertGroupShape` τοποθετεί το δοχείο στη θέση του δρομέα του builder. Η ομαδοποίηση είναι ουσιώδης όταν θέλετε να αντιμετωπίζετε πολλά σχέδια ως μία ενότητα — αυτό είναι το βασικό στοιχείο της λειτουργικότητας **group shapes word**.

## Βήμα 4: Δημιουργία ορθογωνίου και ορισμός μεγέθους

Τώρα προσθέστε ένα ορθογώνιο στην ομάδα. Αυτό δείχνει **ορισμό μεγέθους σχήματος**, που είναι απαραίτητο για ακριβή διάταξη.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // set shape width
        rectangle.setHeight(50.0);   // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Append rectangle to the group
        group.appendChild(rectangle);
```

*Γιατί ορίζουμε διαστάσεις;* Η ρητή κλήση `setWidth` και `setHeight` εγγυάται ότι το ορθογώνιο εμφανίζεται ακριβώς όπως προορίζεται, ανεξάρτητα από τα προεπιλεγμένα στυλ σχήματος του εγγράφου.

## Βήμα 5: Εισαγωγή εικόνας και προσθήκη στην ομάδα

Η προσθήκη μιας εικόνας δείχνει μια άλλη κοινή περίπτωση χρήσης για **προσθήκη σχημάτων στο word**. Η εικόνα γίνεται μέρος της ίδιας ομάδας, μετακινείται μαζί με το ορθογώνιο.

```java
        // Insert an image at the current cursor position
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        picture.setLeft(150.0);   // position inside the group
        picture.setTop(30.0);     // position inside the group

        // Append picture to the group
        group.appendChild(picture);
```

Αν το αρχείο εικόνας λείπει, το Aspose.Words ρίχνει εξαίρεση. Ένα πρακτικό tip είναι να ελέγχετε τη διαδρομή εκ των προτέρων:

```java
        File imgFile = new File("YOUR_DIRECTORY/sample.jpg");
        if (!imgFile.exists()) {
            throw new IllegalArgumentException("Image file not found: " + imgFile.getAbsolutePath());
        }
```

## Βήμα 6: Αποθήκευση του εγγράφου που περιέχει τα ομαδοποιημένα σχήματα

Τέλος, αποθηκεύστε το **κενό έγγραφο Word** (τώρα γεμάτο με ομαδοποιημένο σχήμα) στο δίσκο.

```java
        // Save the document as a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

Όταν ανοίξετε το `GroupShapeDemo.docx` στο Microsoft Word, θα δείτε ένα ενιαίο ομαδοποιημένο αντικείμενο που περιέχει ένα ορθογώνιο και μια εικόνα. Επιλέγοντας οποιοδήποτε τμήμα της ομάδας μετακινεί ολόκληρο το δοχείο, επιβεβαιώνοντας ότι τα σχήματα ομαδοποιήθηκαν σωστά.

### Αναμενόμενο αποτέλεσμα

* Ένα αρχείο με όνομα `GroupShapeDemo.docx` στον καθορισμένο φάκελο.
* Το άνοιγμα του αρχείου εμφανίζει ένα δοχείο 300 × 200 σημείων με:
  * Ένα ορθογώνιο 100 × 50 σημείων τοποθετημένο στο (20, 20).
  * Μια εικόνα τοποθετημένη στο (150, 30) μέσα στο ίδιο δοχείο.

## Περιπτώσεις άκρων και παραλλαγές

| Κατάσταση | Πώς να το αντιμετωπίσετε |
|-----------|--------------------------|
| **Διαφορετικό μέγεθος σελίδας** | Κλήση `doc.getFirstSection().getPageSetup().setPaperSize(PaperSize.A5);` πριν την εισαγωγή της ομάδας. |
| **Πολλαπλές ομάδες** | Επανάληψη των βημάτων 3‑5 με νέο αντικείμενο `GroupShape`; κάθε ομάδα μπορεί να τοποθετηθεί ανεξάρτητα. |
| **Περιστροφή σχημάτων** | Χρήση `shape.setRotationAngle(45.0);` για περιστροφή ενός ορθογωνίου ή εικόνας πριν την προσθήκη στην ομάδα. |
| **Μη‑εικόνα σχήματα** | Δημιουργία αντικειμένων `Shape` τύπου `ShapeType.ELLIPSE`, `ShapeType.LINE`, κ.λπ., και προσθήκη όπως το ορθογώνιο. |
| **Μεγάλες εικόνες** | Κλιμάκωση της εικόνας με `picture.setWidth(80.0); picture.setHeight(60.0);` ώστε η ομάδα να παραμένει εντός των αρχικών ορίων της. |

Αυτές οι παραλλαγές σας επιτρέπουν να προσαρμόσετε το βασικό μοτίβο σε ένα ευρύ φάσμα σεναρίων δημιουργίας εγγράφων.

## Πρακτικές συμβουλές από εμπειρία

* **Pro tip:** Ορίστε το `RelativeHorizontalPosition` και `RelativeVerticalPosition` της ομάδας σε `RelativeHorizontalPosition.PAGE` και `RelativeVerticalPosition.PAGE` αν θέλετε η ομάδα να παραμένει αγκυροβολημένη στη σελίδα αντί για τον δρομέα.
* **Προσοχή:** Προσθήκη σχήματος που υπερβαίνει τις διαστάσεις της ομάδας· το σχήμα θα περικοπεί στο Word. Προσαρμόστε το μέγεθος της ομάδας με `group.setWidth()` και `group.setHeight()` ανάλογα.
* **Σημείωση απόδοσης:** Αν δημιουργείτε πολλά έγγραφα σε βρόχο, επαναχρησιμοποιήστε ένα ενιαίο αντικείμενο `DocumentBuilder` και καλέστε `doc.clone()` για μείωση του κόστους δημιουργίας αντικειμένων.

## Συμπέρασμα

Τώρα ξέρετε πώς να **δημιουργήσετε κενό έγγραφο Word** που περιέχει μια ομαδοποιημένη συλλογή σχημάτων χρησιμοποιώντας το Aspose.Words for Java. Το tutorial κάλυψε τη πλήρη ροή εργασίας: ρύθμιση της βιβλιοθήκης, δημιουργία του εγγράφου, εισαγωγή ομάδας, **ορισμό μεγέθους σχήματος**, **προσθήκη σχημάτων στο word**, και αποθήκευση του αποτελέσματος.

Από εδώ μπορείτε να εξερευνήσετε πιο προχωρημένα χαρακτηριστικά όπως ομαδοποίηση διαγραμμάτων, εφαρμογή στυλ σε μεμονωμένα σχήματα ή εξαγωγή του εγγράφου σε PDF. Κάθε ένα από αυτά τα θέματα βασίζεται στις ίδιες αρχές που παρουσιάστηκαν σε αυτόν τον οδηγό.

---


## Τι πρέπει να μάθετε στη συνέχεια;


Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στην υλοποίηση των δικών σας έργων.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}