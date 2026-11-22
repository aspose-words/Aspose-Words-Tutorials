---
category: general
date: 2026-11-22
description: Προσθέστε σχήμα ορθογωνίου σε έγγραφο Word με Java, ορίστε το μέγεθος
  του σχήματος, ομαδοποιήστε πολλαπλά σχήματα και προσθέστε το σχήμα στην ομάδα αποδοτικά.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add rectangle shape
- set shape size
- group multiple shapes
- set shape dimensions
- append shape to group
language: el
lastmod: 2026-11-22
og_description: Προσθέστε σχήμα ορθογωνίου σε έγγραφο Word χρησιμοποιώντας Java, στη
  συνέχεια ορίστε το μέγεθος του σχήματος, ομαδοποιήστε πολλαπλά σχήματα και προσθέστε
  σχήμα στην ομάδα σε μια ενιαία ροή εργασίας.
og_image_alt: Screenshot showing a rectangle shape added and grouped in a Word document
  using Java
og_title: Προσθήκη σχήματος ορθογωνίου και ομαδοποίηση σχημάτων σε Java – πλήρης οδηγός
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  headline: Add rectangle shape and group shapes in Java
  type: TechArticle
- description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  name: Add rectangle shape and group shapes in Java
  steps:
  - name: Insert the rectangle shape
    text: The rectangle is the first visual element we want to place inside the document.
      By using the `Shape` constructor with `ShapeType.RECTANGLE`, you get a fully
      editable object.
  - name: Set shape size and dimensions
    text: Set shape size and dimensions
  - name: Create a group shape container
    text: '```java // Step 6: Create a group shape that will hold the rectangle and
      other shapes GroupShape groupShape = builder.insertGroupShape(); ```'
  - name: Append shape to group
    text: Append shape to group
  - name: Save the document
    text: '```java // Save the result to a new file doc.save("output.docx"); } } ```'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shape manipulation
title: Προσθήκη σχήματος ορθογωνίου και ομαδοποίηση σχημάτων σε Java
url: /el/java/images-shapes/add-rectangle-shape-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Προσθήκη σχήματος ορθογωνίου και ομαδοποίηση σχημάτων σε Java

Αν χρειάζεται να **προσθέσετε σχήμα ορθογωνίου** σε ένα έγγραφο Word με Java, αυτός ο οδηγός σας καθοδηγεί βήμα‑βήμα. Θα μάθετε επίσης πώς να **ορίσετε το μέγεθος του σχήματος**, **ομαδοποιήσετε πολλαπλά σχήματα** και **προσθέσετε σχήμα σε ομάδα** χωρίς να αφήσετε το IDE.

Η εργασία με διανυσματικά γραφικά μέσα σε αρχείο DOCX συχνά μοιάζει με χειρισμό ξεχωριστών API. Στο τέλος αυτού του tutorial θα έχετε ένα ενιαίο, αυτόνομο πρόγραμμα που δημιουργεί ένα ορθογώνιο, μια έλλειψη και τυχόν επιπλέον σχήματα που χρειάζεστε, τα ομαδοποιεί ώστε να κινούνται ως ένα αντικείμενο. Δεν απαιτούνται εξωτερικά εργαλεία πέρα από το Aspose.Words for Java.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* Java 17 ή νεότερη εγκατεστημένη.
* Maven 3.8+ (ή Gradle) για διαχείριση εξαρτήσεων.
* Ένα έγκυρο license του Aspose.Words for Java (η αξιολόγηση λειτουργεί για δοκιμές).
* Ένα IDE όπως IntelliJ IDEA ή VS Code, αν και οποιοσδήποτε επεξεργαστής κειμένου αρκεί.

Αυτές οι απαιτήσεις επιτρέπουν στον κώδικα να μεταγλωττιστεί και να εκτελεστεί σε οποιοδήποτε σύγχρονο περιβάλλον ανάπτυξης.

## Βήμα 1: Ρύθμιση του έργου Maven

Δημιουργήστε ένα νέο έργο Maven ή προσθέστε την εξάρτηση Aspose.Words σε ένα υπάρχον `pom.xml`:

```xml
<project>
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.example</groupId>
  <artifactId>shape‑demo</artifactId>
  <version>1.0.0</version>

  <dependencies>
    <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.12</version>
    </dependency>
  </dependencies>
</project>
```

Η εξάρτηση φέρνει όλες τις κλάσεις που χρειάζονται για τη διαχείριση εγγράφων, συμπεριλαμβανομένων των `Document`, `DocumentBuilder`, `Shape` και `GroupShape`. Το Maven θα κατεβάσει αυτόματα τα JAR όταν εκτελέσετε `mvn compile`.

## Βήμα 2: Φόρτωση του εγγράφου και δημιουργία DocumentBuilder

Ένας `DocumentBuilder` παρέχει το fluent API για την εισαγωγή περιεχομένου. Φορτώστε ένα υπάρχον DOCX ή ξεκινήστε από ένα κενό έγγραφο:

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document or create a new one
        Document doc = new Document("input.docx");          // replace with your path
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Η δημιουργία του builder νωρίς σας δίνει έναν κέρσορα τοποθετημένο στην αρχή του εγγράφου, έτοιμο για εισαγωγή σχήματος.

## Προσθήκη σχήματος ορθογωνίου σε έγγραφο Word

### Βήμα 3: Εισαγωγή του σχήματος ορθογωνίου

Το ορθογώνιο είναι το πρώτο οπτικό στοιχείο που θέλουμε να τοποθετήσουμε μέσα στο έγγραφο. Χρησιμοποιώντας τον κατασκευαστή `Shape` με `ShapeType.RECTANGLE`, λαμβάνετε ένα πλήρως επεξεργάσιμο αντικείμενο.

```java
        // Step 3: Insert a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        // The shape is not yet sized; we will set its dimensions next.
```

Η προσθήκη του ορθογωνίου σε αυτό το σημείο δεν επηρεάζει τη διάταξη μέχρι να οριστεί το μέγεθός του και να προστεθεί σε έναν container.

### Ορισμός μεγέθους και διαστάσεων σχήματος

#### Βήμα 4: Καθορισμός πλάτους και ύψους

Ο καθορισμός των διαστάσεων του σχήματος καθορίζει πώς θα εμφανίζεται στη σελίδα. Οι τιμές πλάτους και ύψους μετρώνται σε points (1 pt = 1/72 in).

```java
        // Step 4: Set shape size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

Μπορείτε να προσαρμόσετε αυτούς τους αριθμούς ώστε να ταιριάζουν με τις απαιτήσεις του σχεδίου σας. Οι ίδιες μέθοδοι ισχύουν για οποιοδήποτε αντικείμενο `Shape`, ώστε να τα επαναχρησιμοποιήσετε για κύκλους, βέλη ή προσαρμοσμένα σχέδια.

#### Βήμα 5: Εισαγωγή του ορθογωνίου στο έγγραφο

Τώρα που το ορθογώνιο έχει μέγεθος, τοποθετήστε το στη σελίδα. Η μέθοδος `insertShape` του `DocumentBuilder` προσθέτει το σχήμα στην τρέχουσα θέση του κέρσορα.

```java
        // Insert the rectangle at the builder’s current position
        builder.insertShape(rectangle);
```

Σε αυτό το στάδιο το ορθογώνιο εμφανίζεται μόνο του στη σελίδα. Τα επόμενα βήματα δείχνουν πώς να το συνδυάσετε με άλλα σχήματα.

## Ομαδοποίηση πολλαπλών σχημάτων μαζί

Η ομαδοποίηση σχημάτων σας επιτρέπει να τα μετακινείτε, περιστρέφετε ή αλλάζετε το μέγεθός τους ως μία ενιαία μονάδα. Αυτό είναι ιδιαίτερα χρήσιμο για τη δημιουργία σύνθετων διαγραμμάτων.

### Βήμα 6: Δημιουργία container ομάδας σχήματος

```java
        // Step 6: Create a group shape that will hold the rectangle and other shapes
        GroupShape groupShape = builder.insertGroupShape();
```

Η κλήση `insertGroupShape` προσθέτει έναν κενό container στο έγγραφο. Οποιαδήποτε σχήματα προστεθούν σε αυτόν τον container γίνονται μέρος της ομάδας.

### Προσθήκη σχήματος στην ομάδα

#### Βήμα 7: Προσθήκη του ορθογωνίου στην ομάδα

```java
        // Append the previously created rectangle to the group
        groupShape.appendChild(rectangle);
```

Η προσθήκη μετακινεί το ορθογώνιο από το σώμα του εγγράφου στη εσωτερική συλλογή της ομάδας. Το ορθογώνιο τώρα σέβεται τις μετασχηματισμούς της ομάδας.

#### Βήμα 8: Προσθήκη έλλειψης για επίδειξη

```java
        // Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(80);
        ellipse.setHeight(80);
        groupShape.appendChild(ellipse);
```

Η έλλειψη μοιράζεται τον ίδιο χώρο συντεταγμένων με το ορθογώνιο, ώστε να μπορείτε να τα ευθυγραμμίσετε οπτικά ρυθμίζοντας τις ιδιότητες `setLeft` και `setTop` αν χρειαστεί.

### Βήμα 9: Αποθήκευση του εγγράφου

```java
        // Save the result to a new file
        doc.save("output.docx");
    }
}
```

Η εκτέλεση του προγράμματος δημιουργεί το `output.docx`. Ανοίξτε το αρχείο στο Microsoft Word ή στο LibreOffice· θα δείτε ένα ορθογώνιο και μια έλλειψη ομαδοποιημένα μαζί. Η επιλογή οποιουδήποτε σχήματος επισημαίνει ολόκληρη την ομάδα, επιβεβαιώνοντας ότι η **προσθήκη σχήματος στην ομάδα** ολοκληρώθηκε με επιτυχία.

![Add rectangle shape example in Java](image.png){alt="Παράδειγμα προσθήκης σχήματος ορθογωνίου σε Java"}

*Το στιγμιότυπο δείχνει το ορθογώνιο και την έλλειψη μέσα σε μία ομάδα, έτοιμα για κοινή επεξεργασία.*

## Γιατί αυτή η προσέγγιση είναι σημαντική

* **Μία πηγή αλήθειας** – Όλες οι ιδιότητες του σχήματος ορίζονται πριν δημιουργηθεί η ομάδα, αποτρέποντας σφάλματα διάταξης.
* **Επαναχρησιμοποίηση** – Οι ίδιες μέθοδοι `setWidth`/`setHeight` λειτουργούν για οποιοδήποτε σχήμα, ώστε να επεκτείνετε το παράδειγμα σε βέλη, αστέρια ή προσαρμοσμένα SVG.
* **Απόδοση** – Η ομαδοποίηση μειώνει τον αριθμό των αντικειμένων σχεδίασης που πρέπει να διαχειριστεί ο renderer του Word, βελτιώνοντας τον χρόνο ανοίγματος μεγάλων εγγράφων.
* **Διατηρησιμότητα** – Κρατώντας τη λογική δημιουργίας σχήματος και ομαδοποίησης μαζί, οι μελλοντικοί προγραμματιστές μπορούν να τροποποιήσουν διαστάσεις ή να προσθέσουν νέα σχήματα χωρίς να ψάχνουν σε άσχετο κώδικα.

## Συνηθισμένες παραλλαγές και ειδικές περιπτώσεις

| Σενάριο | Προσαρμογή |
|----------|------------|
| **Διαφορετικές μονάδες** | Χρησιμοποιήστε τη μετατροπή `PointsToPixels` ή ορίστε `Shape.setWrapType(WrapType.INLINE)` για ενσωματωμένη τοποθέτηση. |
| **Περιστροφή της ομάδας** | Καλέστε `groupShape.setRotation(45);` για να περιστρέψετε όλα τα παιδικά σχήματα κατά 45°. |
| **Προσθήκη κειμένου σε σχήμα** | Χρησιμοποιήστε `Shape.setText("Label");` μετά τον ορισμό του μεγέθους. |
| **Δυναμικό μέγεθος** | Ανακτήστε τις διαστάσεις της σελίδας μέσω `doc.getFirstSection().getPageSetup().getPageWidth()` και υπολογίστε τα μεγέθη των σχημάτων αναλογικά. |

Αυτές οι παραλλαγές δείχνουν πώς το βασικό μοτίβο — **προσθήκη σχήματος ορθογωνίου**, **ορισμός μεγέθους σχήματος**, **ομαδοποίηση πολλαπλών σχημάτων**, **προσθήκη σχήματος στην ομάδα** — προσαρμόζεται σε πολλές πραγματικές απαιτήσεις.

## Συμπέρασμα

Τώρα ξέρετε πώς να **προσθέσετε σχήμα ορθογωνίου** σε έγγραφο Word χρησιμοποιώντας Java, **ορίσετε το μέγεθος του σχήματος**, **ομαδοποιήσετε πολλαπλά σχήματα** και **προσθέσετε σχήμα στην ομάδα** με καθαρό, συντηρήσιμο τρόπο. Το πλήρες παράδειγμα μεταγλωττίζεται σε μία εκτελέσιμη κλάση, και το παραγόμενο αρχείο DOCX δείχνει το αναμενόμενο αποτέλεσμα.

Από εδώ μπορείτε να εξερευνήσετε:

* Προσθήκη ετικετών κειμένου ή υπερσυνδέσμων σε κάθε σχήμα.
* Ενσωμάτωση ομάδων για δημιουργία ιεραρχικών διαγραμμάτων.
* Εξαγωγή του εγγράφου σε PDF διατηρώντας τις ομάδες σχημάτων.

Νιώστε ελεύθεροι να πειραματιστείτε με διαφορετικές διαστάσεις, χρώματα και επιπλέον τύπους σχημάτων. Η εξοικείωση με τη διαχείριση σχημάτων ανοίγει το δρόμο για αυτοματοποιημένη δημιουργία αναφορών, δυναμικά διαγράμματα και πλούσιες εμπειρίες εγγράφων—όλα απευθείας από κώδικα Java.

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [Insert Rectangle Shape in Java – Group and Position Shapes](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [How to create and insert ellipse and rectangle shapes inside a group shape in a Word document using Aspose.Words](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [Create rectangle shape in a Word document using Java](/words/english/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}