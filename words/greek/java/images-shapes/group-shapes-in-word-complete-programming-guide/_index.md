---
category: general
date: 2026-08-14
description: Ομαδοποίηση σχημάτων στο Word με Java χρησιμοποιώντας το Aspose.Words.
  Μάθετε πώς να δημιουργήσετε σχήμα ορθογωνίου, να ορίσετε τις διαστάσεις του σχήματος
  και να ομαδοποιήσετε πολλαπλά σχήματα σε ένα κενό έγγραφο Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create rectangle shape
- set shape dimensions
- group multiple shapes
- build blank word document
language: el
lastmod: 2026-08-14
og_description: Ομαδοποιήστε σχήματα στο Word χρησιμοποιώντας το Aspose.Words for
  Java. Δημιουργήστε ένα κενό έγγραφο Word, δημιουργήστε σχήμα ορθογωνίου, ορίστε
  τις διαστάσεις του σχήματος και ομαδοποιήστε πολλαπλά σχήματα σε λίγα λεπτά.
og_image_alt: Screenshot showing grouped rectangle shapes in a Word document created
  with Java
og_title: Ομαδοποίηση σχημάτων στο Word – Παράδειγμα Java για προγραμματιστές
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Group shapes in Word with Java using Aspose.Words. Learn how to create
    rectangle shape, set shape dimensions, and group multiple shapes in a blank Word
    document.
  headline: Group shapes in Word – complete programming guide
  type: TechArticle
- questions:
  - answer: Overlap is allowed; Word will render them in the order they were added.
      Use `setZOrder` if you need explicit stacking.
    question: What if the shapes overlap?
  - answer: No. A `GroupShape` is confined to a single page because its coordinate
      system is page‑relative.
    question: Can I group shapes across different pages?
  - answer: Each child keeps its own formatting (fill color, line style). To apply
      a uniform style, iterate over `groupShape.getChildNodes()` and set properties
      programmatically.
    question: Do grouped shapes inherit formatting?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Word automation
- Shapes
title: Ομαδοποίηση σχημάτων στο Word – πλήρης οδηγός προγραμματισμού
url: /el/java/images-shapes/group-shapes-in-word-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ομαδοποίηση σχημάτων στο Word – πλήρης προγραμματιστικός οδηγός

Αν χρειάζεται να **ομαδοποιήσετε σχήματα στο Word**, αυτό το tutorial σας καθοδηγεί βήμα‑βήμα στη διαδικασία με Java και Aspose.Words. Θα μάθετε πώς να **δημιουργήσετε ένα κενό έγγραφο Word**, **δημιουργήσετε ορθογώνιο σχήμα**, **ορίσετε διαστάσεις σχήματος**, και τελικά **ομαδοποιήσετε πολλαπλά σχήματα** ώστε να συμπεριφέρονται ως ένα ενιαίο αντικείμενο.

Η εργασία με σχήματα σε ένα αρχείο Word συχνά μοιάζει με σχεδίαση σε καμβά χωρίς πινέλο. Στο τέλος αυτού του οδηγού θα έχετε ένα επαναχρησιμοποιήσιμο κομμάτι κώδικα που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο Java, είτε δημιουργείτε αναφορές, τιμολόγια ή προσαρμοσμένα πρότυπα.

## Τι θα χρειαστείτε

- Java 8 ή νεότερη
- Aspose.Words for Java (η πιο πρόσφατη έκδοση, π.χ. 24.9)
- Ένα IDE όπως IntelliJ IDEA ή Eclipse
- Βασική εξοικείωση με αντικειμενο‑προσανατολισμένο προγραμματισμό

Όλες αυτές οι προαπαιτούμενες είναι δωρεάν για εγκατάσταση, και ο παρακάτω κώδικας μεταγλωττίζεται με μία μόνο εξάρτηση Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

## Βήμα 1: Δημιουργία κενής εγγράφου Word και αρχικοποίηση του builder

Το πρώτο που πρέπει να κάνετε είναι **να δημιουργήσετε ένα κενό έγγραφο Word**. Αυτό σας παρέχει έναν καθαρό καμβά στον οποίο μπορείτε αργότερα να εισάγετε σχήματα.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder lets you add content programmatically
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` αντιπροσωπεύει ολόκληρο το αρχείο *.docx*, ενώ `DocumentBuilder` είναι ο βοηθός που εισάγει παραγράφους, πίνακες και σχήματα. Η αρχικοποίηση και των δύο αντικειμένων αποτελεί τη βάση για κάθε εργασία αυτοματοποίησης του Word.

## Βήμα 2: Εισαγωγή ενός κοντέινερ ομαδικού σχήματος

Ένα **ομαδικό σχήμα** λειτουργεί όπως ένας φάκελος που μπορεί να περιέχει άλλα σχήματα. Πρώτα δημιουργούμε το κοντέινερ με σταθερό μέγεθος 400 pt × 200 pt.

```java
        // Insert a group shape that will hold other shapes (400 pt × 200 pt)
        GroupShape groupShape = builder.insertGroupShape(400, 200);
```

Η μέθοδος `insertGroupShape` επιστρέφει ένα αντικείμενο `GroupShape`. Όλα τα επόμενα σχήματα που θέλετε να αντιμετωπίζετε ως ενιαία μονάδα πρέπει να προσαρτηθούν σε αυτό το αντικείμενο.

## Βήμα 3: Δημιουργία ορθογώνιων σχημάτων και ορισμός διαστάσεων σχήματος

Τώρα **δημιουργούμε αντικείμενα ορθογώνιου σχήματος**, ρυθμίζουμε το μέγεθός τους και τα τοποθετούμε μέσα στην ομάδα. Αυτό το βήμα δείχνει επίσης πώς να **ορίσετε ακριβείς διαστάσεις σχήματος**.

```java
        // ---- First rectangle -------------------------------------------------
        Shape rectangle1 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle1.setWidth(150);   // set shape dimensions: width = 150 pt
        rectangle1.setHeight(100);  // set shape dimensions: height = 100 pt
        rectangle1.setTop(20);      // vertical offset inside the group
        rectangle1.setLeft(20);     // horizontal offset inside the group
        groupShape.appendChild(rectangle1); // add to the group

        // ---- Second rectangle ------------------------------------------------
        Shape rectangle2 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle2.setWidth(150);
        rectangle2.setHeight(100);
        rectangle2.setTop(20);
        rectangle2.setLeft(200);    // place it beside the first rectangle
        groupShape.appendChild(rectangle2);
```

Και τα δύο ορθογώνια έχουν τις ίδιες διαστάσεις, αλλά οι ιδιότητες `left` διαφέρουν, έτσι εμφανίζονται πλάι‑πλάι. Μπορείτε να αλλάξετε `setTop` και `setLeft` για να διαμορφώσετε οποιαδήποτε διάταξη χρειάζεστε.

## Βήμα 4: Αποθήκευση του εγγράφου που περιέχει τα ομαδοποιημένα ορθογώνια

Αφού τα σχήματα βρίσκονται μέσα στην ομάδα, απλώς αποθηκεύετε το `Document`. Το παραγόμενο αρχείο θα εμφανίζει δύο ορθογώνια που κινούνται μαζί όταν επιλεγούν.

```java
        // Save the document to disk
        String outputPath = "GroupShape.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Η εκτέλεση του προγράμματος δημιουργεί το `GroupShape.docx` στον τρέχοντα φάκελο εργασίας. Ανοίξτε το στο Microsoft Word, επιλέξτε ένα ορθογώνιο και θα παρατηρήσετε ότι ολόκληρη η ομάδα κινείται ως μονάδα — ακριβώς αυτό που σημαίνει **ομαδοποίηση σχημάτων στο Word**.

![Group shapes in Word example](group-shapes.png){alt="Παράδειγμα ομαδοποίησης σχημάτων στο Word"}

*Σχήμα: Δύο ορθογώνια σχήματα ομαδοποιημένα μαζί σε ένα έγγραφο Word.*

## Συμβουλή: Επαναχρησιμοποίηση του ίδιου ομαδικού σχήματος

Αν χρειαστεί να προσθέσετε περισσότερα σχήματα αργότερα (π.χ. κύκλους, πλαίσια κειμένου), διατηρήστε μια αναφορά στο `groupShape` και συνεχίστε να καλείτε `appendChild`. Αυτό αποφεύγει τη δημιουργία νέου κοντέινερ και εξασφαλίζει ότι όλα τα μέλη παραμένουν συγχρονισμένα.

```java
        // Example: add a third shape later
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(120);
        ellipse.setHeight(80);
        ellipse.setTop(130);
        ellipse.setLeft(140);
        groupShape.appendChild(ellipse);
```

## Περιπτώσεις άκρων και συχνές ερωτήσεις

- **Τι γίνεται αν τα σχήματα επικαλύπτονται;** Η επικάλυψη επιτρέπεται· το Word θα τα αποδώσει με τη σειρά που προστέθηκαν. Χρησιμοποιήστε `setZOrder` αν χρειάζεστε ρητή στοίβαξη.
- **Μπορώ να ομαδοποιήσω σχήματα σε διαφορετικές σελίδες;** Όχι. Ένα `GroupShape` περιορίζεται σε μία σελίδα επειδή το σύστημα συντεταγμένων του είναι σχετικό με τη σελίδα.
- **Κληρονομούν τα ομαδοποιημένα σχήματα τη μορφοποίηση;** Κάθε παιδί διατηρεί τη δική του μορφοποίηση (χρώμα γεμίσματος, στυλ γραμμής). Για ομοιόμορφη εμφάνιση, επαναλάβετε πάνω από `groupShape.getChildNodes()` και ορίστε τις ιδιότητες προγραμματικά.

## Πλήρης κώδικας πηγής για αναφορά

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // 1. Build blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert group shape container (400 pt × 200 pt)
        GroupShape groupShape = builder.insertGroupShape(400, 200);

        // 3. Create first rectangle and set shape dimensions
        Shape rectangle1 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle1.setWidth(150);
        rectangle1.setHeight(100);
        rectangle1.setTop(20);
        rectangle1.setLeft(20);
        groupShape.appendChild(rectangle1);

        // 4. Create second rectangle and set shape dimensions
        Shape rectangle2 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle2.setWidth(150);
        rectangle2.setHeight(100);
        rectangle2.setTop(20);
        rectangle2.setLeft(200);
        groupShape.appendChild(rectangle2);

        // 5. Save the document containing the grouped rectangles
        String outputPath = "GroupShape.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Η εκτέλεση του προγράμματος παράγει ένα αρχείο DOCX όπου τα δύο ορθογώνια είναι **ομαδοποιημένα**. Η επιλογή οποιουδήποτε ορθογωνίου μετακινεί και τα δύο, επιβεβαιώνοντας ότι έχετε επιτύχει την **ομαδοποίηση πολλαπλών σχημάτων**.

## Συμπέρασμα

Τώρα γνωρίζετε πώς να **ομαδοποιήσετε σχήματα στο Word** χρησιμοποιώντας Java, από το **δημιουργία ενός κενού εγγράφου Word** μέχρι το **δημιουργία ορθογώνιου σχήματος**, **ορισμό διαστάσεων σχήματος**, και τελικά την **ομαδοποίηση πολλαπλών σχημάτων** σε ένα ενιαίο, κινητό αντικείμενο. Αυτό το πρότυπο κλιμακώνεται σε οποιονδήποτε αριθμό σχημάτων και μπορεί να συνδυαστεί με κείμενο, εικόνες ή διαγράμματα για τη δημιουργία πλούσιων, προγραμματιστικών εγγράφων.

### Τι θα ακολουθήσει;

- Εξερευνήστε **ομαδοποίηση πολλαπλών σχημάτων** με διαφορετικούς τύπους (έλλειψη, βέλη, πλαίσια κειμένου).
- Εφαρμόστε χρώματα γεμίσματος ή περιγράμματα καλώντας `shape.getFillColor()` και `shape.getLine().setColor()`.
- Εισάγετε το ομαδοποιημένο σχήμα σε κελί πίνακα για δομημένες αναφορές.
- Συνδυάστε αυτήν την προσέγγιση με mail‑merge για τη δημιουργία εξατομικευμένων συμβάσεων που περιλαμβάνουν εμπορικά σήματα.

Νιώστε ελεύθεροι να πειραματιστείτε, να προσαρμόσετε τις διαστάσεις ή να ενσωματώσετε πρόσθετο περιεχόμενο. Όταν κυριαρχήσετε στην ομαδοποίηση, τα σενάρια αυτοματοποίησης του Word γίνονται πολύ πιο ευέλικτα και συντηρήσιμα. Καλή κωδικοποίηση!

## Τι πρέπει να μάθετε στη συνέχεια;

Οι παρακάτω οδηγίες καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [Χρήση Σχημάτων Εγγράφου στο Aspose.Words για Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Δημιουργία Εγγράφου Word με Java – Προσθήκη Ορθογώνιου Σχήματος με Εφέ Σκιάς](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Δημιουργία Ομαδικού Σχήματος σε Έγγραφο Word Χρησιμοποιώντας Aspose.Words για .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}