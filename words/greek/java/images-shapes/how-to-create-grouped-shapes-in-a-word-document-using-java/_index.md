---
category: general
date: 2026-10-13
description: Μάθετε πώς να δημιουργείτε ομαδοποιημένα σχήματα στο Word με Java. Αυτός
  ο οδηγός σας δείχνει πώς να εισάγετε ένα ομαδικό σχήμα, να προσθέσετε γραμμή στην
  ομάδα και να ομαδοποιήσετε πολλαπλά σχήματα σε όλο το έγγραφο.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create grouped shapes
- add line to group
- group multiple shapes word
- insert group shape
language: el
lastmod: 2026-10-13
og_description: Δημιουργήστε ομαδοποιημένα σχήματα στο Word με Java. Ακολουθήστε αυτό
  το πλήρες σεμινάριο για να εισάγετε ομαδικό σχήμα, να προσθέσετε γραμμή στην ομάδα
  και να ομαδοποιήσετε πολλαπλά σχήματα σε έγγραφα Word.
og_image_alt: Screenshot of a Word document showing created grouped shapes
og_title: Δημιουργία ομαδοποιημένων σχημάτων στο Word με Java – βήμα‑βήμα οδηγός
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to create grouped shapes in Word with Java. This guide shows
    you how to insert group shape, add line to group, and group multiple shapes word‑wide.
  headline: How to create grouped shapes in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Πώς να δημιουργήσετε ομαδοποιημένα σχήματα σε ένα έγγραφο Word χρησιμοποιώντας
  Java
url: /el/java/images-shapes/how-to-create-grouped-shapes-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε ομαδοποιημένα σχήματα σε έγγραφο Word χρησιμοποιώντας Java

Εάν χρειάζεται να **δημιουργήσετε ομαδοποιημένα σχήματα** σε αρχείο Microsoft Word από Java, αυτό το tutorial σας καθοδηγεί βήμα‑βήμα σε όλη τη διαδικασία. Θα δείτε πώς να **εισάγετε group shape**, να τοποθετήσετε ένα ορθογώνιο και μια γραμμή μέσα στον ίδιο container και, τέλος, να αποθηκεύσετε το έγγραφο με τα ομαδοποιημένα γραφικά.

Η ομαδοποίηση σχημάτων διευκολύνει τη μετακίνηση, την αλλαγή μεγέθους ή το στυλ πολλαπλών αντικειμένων σχεδίασης ως μια ενιαία μονάδα — ιδανική για διαγράμματα, flowcharts ή προσαρμοσμένες διακοσμήσεις σελίδας. Στο τέλος αυτού του οδηγού θα μπορείτε να **προσθέσετε line to group**, **group multiple shapes word** έγγραφα, και να επαναχρησιμοποιήσετε την ίδια τεχνική για οποιονδήποτε αριθμό σχημάτων.

## Προαπαιτούμενα

- Java 17 ή νεότερη εγκατεστημένη στο περιβάλλον ανάπτυξής σας.  
- Άδεια Aspose.Words for Java (ή δωρεάν evaluation).  
- Έργο Maven ή Gradle όπου μπορείτε να προσθέσετε την εξάρτηση Aspose.Words:

```xml
<!-- Maven example -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

Δεν απαιτούνται πρόσθετες βιβλιοθήκες.

## Βήμα 1: Εισαγωγή του container group shape

Το πρώτο βήμα είναι να **εισάγετε group shape** στο έγγραφο. Αυτό το container θα περιέχει κάθε επόμενο σχήμα.

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // The rest of the code will add shapes to this group
```

Η μέθοδος `builder.insertGroupShape()` δημιουργεί ένα κενό αντικείμενο `Shape` τύπου `GROUPSHAPE`. Σκεφτείτε το ως έναν διαφανή καμβά που μπορεί να περιέχει άλλα αντικείμενα σχεδίασης.

## Βήμα 2: Προσθήκη ορθογωνίου στην ομάδα

Ένα ορθογώνιο συχνά λειτουργεί ως οπτικό φόντο για μια ομάδα σχημάτων.

```java
        // Create a rectangle shape
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // width in points
        rectangleShape.setHeight(50);   // height in points
        rectangleShape.setLeft(0);      // X‑coordinate inside the group
        rectangleShape.setTop(0);       // Y‑coordinate inside the group

        // Append the rectangle to the group container
        groupShape.appendChild(rectangleShape);
```

Ορίζοντας `Left` και `Top` στο `0` τοποθετεί το ορθογώνιο στην πάνω‑αριστερή γωνία της ομάδας. Μπορείτε να αλλάξετε αυτές τις τιμές για να μετατοπίσετε το σχήμα εντός της ομάδας.

## Βήμα 3: **Προσθήκη line to group** – δημιουργία σχήματος γραμμής

Τώρα **προσθέτουμε line to group**. Η γραμμή θα εμφανιστεί κάτω από το ορθογώνιο.

```java
        // Create a line shape
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);   // length of the line
        lineShape.setTop(60);      // vertical position (60 points down)

        // Append the line to the same group
        groupShape.appendChild(lineShape);
```

Η ιδιότητα `Top` μετακινεί τη γραμμή 60 points κάτω από το ορθογώνιο, δημιουργώντας μια απλή στοίβα. Μπορείτε επίσης να ορίσετε `Left` αν χρειάζεστε οριζόντια μετατόπιση.

## Βήμα 4: Αποθήκευση του εγγράφου με τα ομαδοποιημένα σχήματα

```java
        // Save the document to a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

Όταν ανοίξετε το `GroupShapeDemo.docx` στο Microsoft Word, θα δείτε μια ενιαία ομάδα που περιέχει τόσο το ορθογώνιο όσο και τη γραμμή. Επιλέγοντας την ομάδα μπορείτε να μετακινήσετε και τα δύο σχήματα μαζί, αποδεικνύοντας ότι έχετε επιτυχώς **group multiple shapes word**.

## Πλήρες, εκτελέσιμο παράδειγμα

Παρακάτω βρίσκεται το πλήρες πρόγραμμα με όλες τις εισαγωγές και τη διαχείριση σφαλμάτων. Αντιγράψτε το στο IDE σας, αντικαταστήστε το `YOUR_DIRECTORY` με μια υπάρχουσα διαδρομή φακέλου και τρέξτε το.

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // Step 3: Add a rectangle to the group
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);
        rectangleShape.setHeight(50);
        rectangleShape.setLeft(0);
        rectangleShape.setTop(0);
        groupShape.appendChild(rectangleShape);

        // Step 4: Add a line to the group
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);
        lineShape.setTop(60);
        groupShape.appendChild(lineShape);

        // Step 5: Save the document
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

### Αναμενόμενο αποτέλεσμα

- Ένα αρχείο με όνομα `GroupShapeDemo.docx` εμφανίζεται στον προορισμό.  
- Το άνοιγμα του αρχείου στο Word δείχνει ένα ενιαίο ομαδοποιημένο αντικείμενο που περιέχει ένα ορθογώνιο στην κορυφή και μια γραμμή από κάτω.  
- Η σύρσιμο της ομάδας μετακινεί και τα δύο σχήματα μαζί, επιβεβαιώνοντας ότι **δημιουργήσατε ομαδοποιημένα σχήματα** επιτυχώς.

## Συμβουλές και κοινά προβλήματα

- **Pro tip:** Αν χρειάζεται να περιστρέψετε ή να στυλιζάτε μεμονωμένα σχήματα μέσα στην ομάδα, καλέστε τα αντίστοιχα setters (`setRotation`, `getFill().setForeColor`, κ.λπ.) πριν τα προσθέσετε στην ομάδα. Η ομάδα θα διατηρήσει αυτές τις οπτικές ιδιότητες.  
- **Watch out for:** Η παράλειψη του ορισμού της ιδιότητας `Top` για τη γραμμή μπορεί να προκαλέσει επικάλυψη με το ορθογώνιο, κάνοντας την ομάδα να φαίνεται ακατάστατη.  
- **Edge case:** Όταν προσθέτετε περισσότερα από δύο σχήματα, θυμηθείτε ότι οι συντεταγμένες κάθε παιδιού είναι σχετικές με την αρχή της ομάδας (0,0). Σχεδιάστε τη διάταξη αναλόγως.  
- **Performance note:** Η ομαδοποίηση μεγάλου αριθμού σχημάτων (εκατοντάδες) μπορεί να αυξήσει ελαφρώς το μέγεθος του αρχείου, αλλά απλοποιεί την επεξεργασία αργότερα στο Word.

## Πώς να **group multiple shapes word** έγγραφα προγραμματιστικά

Το μοτίβο που παρουσιάστηκε παραπάνω — δημιουργία container ομάδας, ρύθμιση ιδιοτήτων κάθε παιδιού και προσθήκη — λειτουργεί για οποιονδήποτε αριθμό σχημάτων: κύκλους, εικόνες, πλαίσια κειμένου κ.λπ. Απλώς επαναλάβετε τα βήματα «δημιουργία σχήματος → ορισμός ιδιοτήτων → προσθήκη» πριν καλέσετε `doc.save()`.

Αν χρειάζεται να **add line to group** αφού η ομάδα περιέχει ήδη άλλα σχήματα, μπορείτε να ανακτήσετε την υπάρχουσα ομάδα με:

```java
Shape existingGroup = (Shape) doc.getChildNodes(NodeType.SHAPE, true)
                                 .stream()
                                 .filter(s -> ((Shape) s).getShapeType() == ShapeType.GROUPSHAPE)
                                 .findFirst()
                                 .orElseThrow(() -> new IllegalStateException("No group found"));
existingGroup.appendChild(lineShape);
```

Αυτό δείχνει ότι μπορείτε να τροποποιήσετε μια ομάδα οποιαδήποτε στιγμή στον κύκλο ζωής του εγγράφου.

## Συμπέρασμα

Τώρα γνωρίζετε πώς να **δημιουργήσετε ομαδοποιημένα σχήματα** σε έγγραφο Word χρησιμοποιώντας Java και Aspose.Words. Με **inserting group shape**, **adding line to group**, και **group multiple shapes word**, μπορείτε να κατασκευάσετε σύνθετες σχεδίες που συμπεριφέρονται ως ένα ενιαίο αντικείμενο — ιδανικό για διαγράμματα, πρότυπα και αυτόματη δημιουργία αναφορών.

Επόμενα, εξερευνήστε τα σχετικά θέματα:

- **Applying styles to grouped shapes** – μάθετε πώς να ορίσετε χρώματα γεμίσματος, περιγράμματα και εφέ για όλα τα παιδιά ταυτόχρονα.  
- **Exporting grouped shapes to PDF** – δείτε πώς η ίδια ομάδα διατηρείται όταν μετατρέπετε το έγγραφο.  
- **Animating shapes with VBA** – συνδυάστε τις ομάδες που παράγει η Java με μακροεντολές Word για διαδραστικά έγγραφα.

Μη διστάσετε να πειραματιστείτε με διαφορετικούς τύπους σχημάτων, μεγέθη και θέσεις. Η ομαδοποίηση σας δίνει την ευελιξία να αντιμετωπίζετε πολλά αντικείμενα ως ένα, απλοποιώντας τόσο τον κώδικα όσο και την αλληλεπίδραση του χρήστη. Καλή προγραμματιστική!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στην υλοποίηση των δικών σας έργων.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}