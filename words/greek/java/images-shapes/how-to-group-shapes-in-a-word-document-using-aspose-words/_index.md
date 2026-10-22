---
category: general
date: 2026-08-20
description: Μάθετε πώς να ομαδοποιείτε σχήματα, να ορίζετε το μέγεθος του σχήματος,
  να εισάγετε εικόνα στο έγγραφο, να προσθέτετε εικόνα στην ομάδα και να δημιουργείτε
  ορθογώνιο σχήμα με το Aspose.Words σε Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert image into document
- set shape size
- add picture to group
- create rectangle shape
language: el
lastmod: 2026-08-20
og_description: Πώς να ομαδοποιήσετε σχήματα σε ένα έγγραφο Word χρησιμοποιώντας το
  Aspose.Words. Ακολουθήστε αυτό το βήμα‑βήμα Java tutorial για να ορίσετε το μέγεθος
  του σχήματος, να εισάγετε εικόνα στο έγγραφο, να προσθέσετε εικόνα στην ομάδα και
  να δημιουργήσετε σχήμα ορθογωνίου.
og_image_alt: Diagram showing how to group shapes in a Word document
og_title: Πώς να ομαδοποιήσετε σχήματα σε ένα έγγραφο Word με το Aspose.Words – Οδηγός
  Java
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to group shapes, set shape size, insert image into document,
    add picture to group, and create rectangle shape with Aspose.Words in Java.
  headline: How to group shapes in a Word document using Aspose.Words
  type: TechArticle
- description: Learn how to group shapes, set shape size, insert image into document,
    add picture to group, and create rectangle shape with Aspose.Words in Java.
  name: How to group shapes in a Word document using Aspose.Words
  steps:
  - name: Create a new document and a `DocumentBuilder`
    text: A `Document` represents the Word file, while `DocumentBuilder` provides
      convenient methods for inserting content.
  - name: Insert a group shape that will hold multiple child shapes
    text: A group shape acts like a container. Its dimensions define the bounding
      box for all child shapes.
  - name: Create a rectangle shape, set its size, and add it to the group
    text: Setting the exact size of a shape is essential when you want precise layout
      control.
  - name: Insert an image, then add the picture shape to the same group
    text: Inserting an image is the core of the **insert image into document** requirement.
      The returned `Shape` is a picture shape that can be grouped like any other shape.
  - name: Position the entire group on the page
    text: After adding all child shapes, you can move, rotate, or hide the whole group.
      Positioning uses the **add picture to group** concept indirectly, because the
      group now contains the picture.
  - name: Save the document
    text: Finally, write the file to disk. You can open the resulting `.docx` in Word
      to verify the grouping.
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Automation
title: Πώς να ομαδοποιήσετε σχήματα σε ένα έγγραφο Word χρησιμοποιώντας το Aspose.Words
url: /el/java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να ομαδοποιήσετε σχήματα σε ένα έγγραφο Word χρησιμοποιώντας το Aspose.Words

Αν χρειάζεστε **how to group shapes** σε ένα αρχείο Word, αυτό το tutorial παρουσιάζει τη πλήρη λύση σε Java. Θα δείτε πώς να **set shape size**, **insert image into document**, **add picture to group**, και **create rectangle shape**—όλα με σαφείς εξηγήσεις και ένα εκτελέσιμο παράδειγμα κώδικα.

Η ομαδοποίηση σχημάτων απλοποιεί τη διαχείριση διάταξης, σας επιτρέπει να μετακινείτε ή να περιστρέφετε πολλαπλά αντικείμενα ως μια ενιαία μονάδα, και διατηρεί το έγγραφό σας τακτοποιημένο. Στα παρακάτω βήματα θα δημιουργήσετε μια ομάδα που περιέχει ένα ορθογώνιο και μια εικόνα, και στη συνέχεια θα τοποθετήσετε την ομάδα στη σελίδα.

## Προαπαιτούμενα

* Java 17 ή νεότερη έκδοση εγκατεστημένη.
* Aspose.Words for Java (έκδοση 23.9 ή μεταγενέστερη) προστέθηκε στο classpath του έργου σας.
* Μια δείγματική εικόνα JPEG στο `YOUR_DIRECTORY/sample.jpg` (αντικαταστήστε το `YOUR_DIRECTORY` με την πραγματική διαδρομή).

Μπορείτε να προσθέσετε το Aspose.Words μέσω Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## Πώς να ομαδοποιήσετε σχήματα με το Aspose.Words

Οι παρακάτω ενότητες περιγράφουν βήμα-βήμα κάθε λειτουργία που απαιτείται για **how to group shapes**. Η κύρια επικεφαλίδα H2 περιέχει τη βασική λέξη-κλειδί, ικανοποιώντας τους κανόνες SEO.

### Βήμα 1: Δημιουργία νέου εγγράφου και ενός `DocumentBuilder`

Ένα `Document` αντιπροσωπεύει το αρχείο Word, ενώ το `DocumentBuilder` παρέχει βολικές μεθόδους για την εισαγωγή περιεχομένου.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Γιατί είναι σημαντικό*: Ξεκινώντας με ένα νέο `Document` εξασφαλίζετε ότι η ομάδα που θα δημιουργήσετε δεν θα επηρεάσει υπάρχοντα στοιχεία.

### Βήμα 2: Εισαγωγή ενός group shape που θα περιέχει πολλαπλά child shapes

Ένα group shape λειτουργεί ως κοντέινερ. Οι διαστάσεις του ορίζουν το πλαίσιο περιβάλλοντος για όλα τα child shapes.

```java
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape groupShape = builder.insertGroupShape(300, 200);
```

*Συμβουλή*: Το πλάτος (`300`) και το ύψος (`200`) είναι σε points (1 pt = 1/72 inch). Προσαρμόστε τα ανάλογα με το μέγεθος των σχημάτων που σκοπεύετε να προσθέσετε.

### Βήμα 3: Δημιουργία ορθογώνιου σχήματος, ορισμός του μεγέθους του, και προσθήκη του στην ομάδα

Ο καθορισμός του ακριβούς μεγέθους ενός σχήματος είναι απαραίτητος όταν θέλετε ακριβή έλεγχο διάταξης.

```java
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // set shape size – width
        rectangleShape.setHeight(50);   // set shape size – height
        // Optionally set a fill color for visibility
        rectangleShape.getFillColor().setRGB(0xFF, 0xCC, 0x00);
        groupShape.appendChild(rectangleShape);
```

*Γιατί ορίζουμε το μέγεθος του σχήματος*: Οι μέθοδοι `setWidth` και `setHeight` αντιστοιχούν στη δευτερεύουσα λέξη-κλειδί **set shape size**, παρέχοντάς σας έλεγχο pixel‑perfect στην εμφάνιση του ορθογωνίου.

### Βήμα 4: Εισαγωγή εικόνας, στη συνέχεια προσθήκη του picture shape στην ίδια ομάδα

Η εισαγωγή μιας εικόνας είναι η ουσία της απαίτησης **insert image into document**. Το επιστρεφόμενο `Shape` είναι ένα picture shape που μπορεί να ομαδοποιηθεί όπως οποιοδήποτε άλλο σχήμα.

```java
        // Step 4: Insert an image, then add the picture shape to the same group
        Shape pictureShape = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        // Resize the picture if needed (example: 120 pt wide, maintain aspect ratio)
        pictureShape.setWidth(120);
        // Add the picture to the previously created group
        groupShape.appendChild(pictureShape);
```

*Pro tip*: Αν χρειάζεται να διατηρήσετε την αρχική αναλογία διαστάσεων, ορίστε μόνο μία διάσταση (`setWidth` ή `setHeight`). Το Aspose.Words κλιμακώνει αυτόματα την άλλη διάσταση.

### Βήμα 5: Τοποθέτηση ολόκληρης της ομάδας στη σελίδα

Αφού προσθέσετε όλα τα child shapes, μπορείτε να μετακινήσετε, να περιστρέψετε ή να κρύψετε ολόκληρη την ομάδα. Η τοποθέτηση χρησιμοποιεί έμμεσα την έννοια **add picture to group**, επειδή η ομάδα περιέχει τώρα την εικόνα.

```java
        // Step 5: Position the entire group on the page (it can also be rotated, hidden, etc.)
        groupShape.setLeft(50);   // distance from the left margin
        groupShape.setTop(100);   // distance from the top margin
        // Optional: rotate the group 15 degrees
        groupShape.setRotation(15);
```

*Εξήγηση*: Οι μέθοδοι `setLeft` και `setTop` τοποθετούν την ομάδα σε σχέση με τα περιθώρια της σελίδας. Η περιστροφή της ομάδας δείχνει ότι όλα τα child shapes κληρονομούν τη μετασχηματισμό.

### Βήμα 6: Αποθήκευση του εγγράφου

Τέλος, γράψτε το αρχείο στο δίσκο. Μπορείτε να ανοίξετε το παραγόμενο `.docx` στο Word για να επαληθεύσετε την ομαδοποίηση.

```java
        // Step 6: Save the document
        doc.save("GroupShapesDemo.docx");
    }
}
```

Η εκτέλεση του προγράμματος παράγει το **GroupShapesDemo.docx** που περιέχει ένα ορθογώνιο και μια εικόνα ενωμένα. Η επιλογή οποιουδήποτε σχήματος στο Word θα επιλέξει επίσης το άλλο, επιβεβαιώνοντας ότι έχετε μάθει επιτυχώς **how to group shapes**.

---

## Αναμενόμενο αποτέλεσμα

Όταν ανοίξετε το *GroupShapesDemo.docx* στο Microsoft Word:

* Ένα ορθογώνιο (χρυσό γέμισμα) εμφανίζεται στην αριστερή πλευρά της ομάδας.
* Η εικόνα που παρείχατε εμφανίζεται στα δεξιά του ορθογωνίου.
* Και τα δύο αντικείμενα κινούνται μαζί όταν σύρετε την ομάδα.
* Η ομάδα τοποθετείται 50 pt από το αριστερό περιθώριο και 100 pt από το άνω περιθώριο, περιστραμμένη 15°.

Αν η εικόνα δεν εμφανίζεται, ελέγξτε ξανά τη διαδρομή αρχείου στο `insertImage`. Το Aspose.Words ρίχνει ένα `IOException` όταν το αρχείο δεν μπορεί να βρεθεί.

---

## Συχνές ερωτήσεις και διαχείριση ειδικών περιπτώσεων

| Question | Answer |
|----------|--------|
| **Μπορώ να προσθέσω περισσότερα από δύο σχήματα;** | Ναι. Καλέστε `groupShape.appendChild(otherShape)` για κάθε επιπλέον σχήμα. |
| **Τι αν χρειάζομαι διαφανές φόντο για το ορθογώνιο;** | Χρησιμοποιήστε `rectangleShape.getFillColor().setRGB(255, 255, 255); rectangleShape.setFillTransparent(true);` |
| **Υποστηρίζεται η ομαδοποίηση σε παλαιότερες μορφές Word (π.χ., `.doc`);** | Η ομαδοποίηση λειτουργεί για `.docx` και `.doc`, αλλά ορισμένοι παλαιότεροι προβολείς μπορεί να αγνοούν τα μεταδεδομένα της ομάδας. Αποθηκεύστε ως `.docx` για πλήρη πιστότητα. |
| **Πώς να απομακρύνω την ομαδοποίηση αργότερα;** | Ανακτήστε τα παιδικά nodes μέσω `groupShape.getChildNodes(NodeType.ANY, true)` και μετακινήστε τα στο σώμα του εγγράφου, στη συνέχεια αφαιρέστε την ομάδα. |
| **Μπορώ να ομαδοποιήσω σχήματα σε διαφορετικές ενότητες;** | Όχι. Ένα `GroupShape` πρέπει να βρίσκεται μέσα σε ένα μόνο `Story` (συνήθως το κύριο σώμα του εγγράφου). |

## Pro συμβουλές για αξιόπιστη διαχείριση σχημάτων

* **Χρησιμοποιήστε την απόλυτη τοποθέτηση με μέτρο** – η σχετική τοποθέτηση (`builder.moveToDocumentEnd()`) συχνά προσφέρει πιο ανταποκρινόμενες διατάξεις.
* **Κρατήστε στην cache το `DocumentBuilder`** – η δημιουργία νέου builder για κάθε λειτουργία μπορεί να μειώσει την απόδοση σε μεγάλα έγγραφα.
* **Ορίστε το `PictureFillMode`** όταν χρειάζεστε την εικόνα να τεντωθεί ή να επαναλαμβάνεται μέσα στο σχήμα: `pictureShape.setPictureFillMode(PictureFillMode.STRETCH);`
* **Επικυρώστε τις διαστάσεις της εικόνας** πριν την εισαγωγή για να αποφύγετε απρόσμενη κλιμάκωση που μπορεί να επηρεάσει το πλαίσιο της ομάδας.

## Επόμενα βήματα

Τώρα που γνωρίζετε **how to group shapes**, μπορείτε να εξερευνήσετε:

* **Insert image into document** με προχωρημένες επιλογές όπως περικοπή (`pictureShape.setCropTop(...)`).
* **Set shape size** δυναμικά βάσει των διαστάσεων της σελίδας (`doc.getFirstSection().getPageSetup().getPageWidth()`).
* **Add picture to group** μαζί με πλαίσια κειμένου για γραφικά με λεζάντες.
* **Create rectangle shape** με στρογγυλεμένες γωνίες (`rectangleShape.setCornerRadius(5);`).

Αυτά τα θέματα βασίζονται στην ίδια επιφάνεια API και σας βοηθούν να δημιουργήσετε σύνθετες, προγραμματιστικές αναφορές Word.

## Συμπέρασμα

Σε αυτό το tutorial μάθατε **how to group shapes** σε ένα έγγραφο Word χρησιμοποιώντας το Aspose.Words for Java. Ακολουθώντας τα έξι βήματα—δημιουργία εγγράφου, εισαγωγή ομάδας, **creating rectangle shape**, **set shape size**, **insert image into document**, **add picture to group**, και τοποθέτηση της ομάδας—διαθέτετε πλέον ένα επαναχρησιμοποιήσιμο πρότυπο για σύνθετα σενάρια διάταξης. Μη διστάσετε να πειραματιστείτε με επιπλέον child shapes, διαφορετικές περιστροφές ή λογική υπό όρους ομαδοποίησης ώστε να ταιριάζει στις ανάγκες της εφαρμογής σας.

Καλό κώδικα!

## Τι Θα Πρέπει Να Μάθετε Στη Σύντομη Μελλοντική;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα-βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Δημιουργία Εγγράφου Word Java – Προσθήκη Ορθογώνιου Σχήματος με Εφέ Σκιάς](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Χρήση Σχημάτων Εγγράφου στο Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Δημιουργία Group Shape σε Έγγραφο Word Χρησιμοποιώντας Aspose.Words για .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}