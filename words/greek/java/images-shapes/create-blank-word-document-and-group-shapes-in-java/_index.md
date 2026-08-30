---
category: general
date: 2026-08-23
description: Δημιουργήστε ένα κενό έγγραφο Word με το Aspose.Words for Java, μάθετε
  πώς να ομαδοποιείτε σχήματα, να χρωματίζετε σχήμα ορθογωνίου και να αποθηκεύετε
  το έγγραφο ως docx σε λίγα λεπτά.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- save document as docx
- how to group shapes
- color rectangle shape
language: el
lastmod: 2026-08-23
og_description: Δημιουργήστε κενό έγγραφο Word με το Aspose.Words for Java, στη συνέχεια
  δείτε πώς να ομαδοποιήσετε σχήματα, να χρωματίσετε το ορθογώνιο σχήμα και να αποθηκεύσετε
  το έγγραφο ως docx αποδοτικά.
og_image_alt: Screenshot of a blank Word document containing grouped colored rectangle
  shapes
og_title: Δημιουργήστε κενό έγγραφο Word και ομαδοποιήστε σχήματα σε Java – βήμα‑βήμα
  οδηγός
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Create blank Word document with Aspose.Words for Java, learn how to
    group shapes, color rectangle shape, and save document as docx in minutes.
  headline: Create blank Word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Δημιουργία κενού εγγράφου Word και ομαδοποίηση σχημάτων σε Java
url: /el/java/images-shapes/create-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία κενής εγγράφου Word και ομαδοποίηση σχημάτων σε Java

Αν χρειάζεστε να **create blank Word document** προγραμματιστικά, το Aspose.Words for Java το καθιστά απλό. Αυτό το tutorial σας δείχνει ακριβώς πώς να **create blank Word document**, να εισάγετε ένα **group shapes in Word**, να εφαρμόσετε **color rectangle shape**, και τέλος να **save document as docx**. Στο τέλος θα έχετε ένα επαναχρησιμοποιήσιμο κομμάτι κώδικα που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο Java.

Θα μάθετε:

* Η απαιτούμενη εξάρτηση Maven/Gradle για το Aspose.Words.
* Πώς να δημιουργήσετε ένα κενό έγγραφο και ένα `DocumentBuilder`.
* Τα ακριβή βήματα για **how to group shapes** μέσα σε ένα `GroupShape`.
* Πώς να ορίσετε χρώματα γεμίσματος σε σχήματα ορθογωνίου.
* Η βέλτιστη πρακτική για **save document as docx** και πού να βρείτε το αρχείο εξόδου.

Δεν απαιτείται προγενέστερη εμπειρία με το Aspose.Words, αλλά θα πρέπει να είστε άνετοι με την βασική ανάπτυξη Java και να έχετε εγκατεστημένο JDK 8 ή νεότερο.

---

## Προαπαιτούμενα

| Απαίτηση | Έκδοση / Λεπτομέρεια |
|-------------|-------------------|
| Java Development Kit | 8 or higher |
| Build tool | Maven 3+ or Gradle 6+ |
| Aspose.Words for Java | 23.12 or later (the latest version at the time of writing) |
| IDE (optional) | IntelliJ IDEA, Eclipse, VS Code, or any Java‑compatible editor |

---

## Βήμα 1: Προσθήκη Aspose.Words στο έργο σας

### Maven

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

### Gradle

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **Συμβουλή:** Αν χρησιμοποιείτε εταιρικό proxy, ρυθμίστε το Maven/Gradle ώστε να κατεβάζει το πακέτο από το αποθετήριο Aspose όπως περιγράφεται στα επίσημα έγγραφα.

---

## Βήμα 2: **Create blank Word document** με έναν builder

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new blank document
        Document doc = new Document();               // <-- create blank Word document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Ο κατασκευαστής `Document` δημιουργεί ένα κενό κοντέινερ `.docx` στη μνήμη. Ο `DocumentBuilder` σας παρέχει ένα ευέλικτο API για την προσθήκη περιεχομένου, συμπεριλαμβανομένων σχημάτων.

---

## Βήμα 3: Εισαγωγή ενός **group shapes in Word** container

```java
        // Step 3.1: Insert a GroupShape that will hold individual shapes
        // Width = 300 points, Height = 200 points
        GroupShape groupShape = builder.insertGroupShape(300, 200);
```

Ένα `GroupShape` λειτουργεί όπως ένα μικρό καμβά. Όλα τα σχήματα που προστίθενται σε αυτό κινούνται μαζί, κάτι που είναι ακριβώς **how to group shapes** για συνέπεια διάταξης.

---

## Βήμα 4: Προσθήκη του πρώτου **color rectangle shape** (κόκκινο)

```java
        // Step 4.1: Create the first rectangle and set its fill color to red
        Shape redRectangle = new Shape(doc, ShapeType.RECTANGLE);
        redRectangle.setWidth(120);
        redRectangle.setHeight(80);
        redRectangle.getFill().setForeColor(java.awt.Color.RED);
        // Append the rectangle to the group
        groupShape.appendChild(redRectangle);
```

Η σταθερά `ShapeType.RECTANGLE` δημιουργεί ένα απλό ορθογώνιο. Καλώντας `getFill().setForeColor(...)` ελέγχετε το **color rectangle shape**. Μπορείτε να αντικαταστήσετε το `java.awt.Color.RED` με οποιαδήποτε σταθερά `java.awt.Color` ή προσαρμοσμένη τιμή RGB.

---

## Βήμα 5: Προσθήκη του δεύτερου **color rectangle shape** (πράσινο) και τοποθέτηση

```java
        // Step 5.1: Create a second rectangle, color it green, and offset it inside the group
        Shape greenRectangle = new Shape(doc, ShapeType.RECTANGLE);
        greenRectangle.setWidth(120);
        greenRectangle.setHeight(80);
        greenRectangle.setLeft(130); // Horizontal offset inside the group
        greenRectangle.getFill().setForeColor(java.awt.Color.GREEN);
        groupShape.appendChild(greenRectangle);
```

Η ρύθμιση `setLeft` (ή `setTop`) μετακινεί το σχήμα σε σχέση με την πάνω‑αριστερή γωνία του **group shapes in Word** container. Αυτό δείχνει **how to group shapes** με ακριβή τοποθέτηση.

---

## Βήμα 6: **Save document as docx** και επαλήθευση του αποτελέσματος

```java
        // Step 6.1: Persist the document to the file system
        String outputPath = "output/GroupShapeDemo.docx";
        doc.save(outputPath);          // <-- save document as docx
        System.out.println("Document saved to: " + outputPath);
    }
}
```

Η μέθοδος `save` γράφει αυτόματα ένα αρχείο `.docx` επειδή η επέκταση του αρχείου είναι `.docx`. Αν χρειάζεστε διαφορετική μορφή (π.χ., PDF), περάστε το αντίστοιχο enum `SaveFormat`.

> **Συμβουλή:** Βεβαιωθείτε ότι ο φάκελος προορισμού (`output/` σε αυτό το παράδειγμα) υπάρχει ή δημιουργήστε τον προγραμματιστικά με `new File("output").mkdirs();`.

---

## Πλήρης πηγαίος κώδικας για γρήγορη αντιγραφή‑επικόλληση

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document
        Document doc = new Document();               // create blank Word document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a GroupShape (the container for grouped shapes)
        GroupShape groupShape = builder.insertGroupShape(300, 200);

        // 3️⃣ First rectangle – red
        Shape redRectangle = new Shape(doc, ShapeType.RECTANGLE);
        redRectangle.setWidth(120);
        redRectangle.setHeight(80);
        redRectangle.getFill().setForeColor(java.awt.Color.RED);
        groupShape.appendChild(redRectangle);

        // 4️⃣ Second rectangle – green, positioned next to the red one
        Shape greenRectangle = new Shape(doc, ShapeType.RECTANGLE);
        greenRectangle.setWidth(120);
        greenRectangle.setHeight(80);
        greenRectangle.setLeft(130); // offset inside the group
        greenRectangle.getFill().setForeColor(java.awt.Color.GREEN);
        groupShape.appendChild(greenRectangle);

        // 5️⃣ Save the file as DOCX
        String outPath = "output/GroupShapeDemo.docx";
        doc.save(outPath);          // save document as docx
        System.out.println("Document saved to: " + outPath);
    }
}
```

**Αναμενόμενο αποτέλεσμα:** Το άνοιγμα του `GroupShapeDemo.docx` στο Microsoft Word εμφανίζει μια σελίδα με δύο χρωματιστά ορθογώνια (κόκκινο στα αριστερά, πράσινο στα δεξιά) που κινούνται μαζί όταν επιλέγετε την ομάδα.

---

## Συχνές ερωτήσεις και διαχείριση ειδικών περιπτώσεων

| Ερώτηση | Απάντηση |
|----------|--------|
| *Μπορώ να προσθέσω περισσότερα από δύο σχήματα στην ίδια ομάδα;* | Ναι. Καλέστε `groupShape.appendChild(yourShape)` για κάθε επιπλέον σχήμα. Η ομάδα θα αλλάξει αυτόματα μέγεθος ώστε να ταιριάζει στα πιο απομακρυσμένα άκρα, ή μπορείτε να προσαρμόσετε χειροκίνητα το πλάτος/ύψος. |
| *Τι κάνω αν χρειάζομαι διαφορετικό τύπο σχήματος (π.χ., ellipse);* | Αντικαταστήστε το `ShapeType.RECTANGLE` με `ShapeType.ELLIPSE`. Η ίδια λογική γεμίσματος χρώματος ισχύει. |
| *Χρειάζεται να απελευθερώσω το αντικείμενο `Document`;* | Το Aspose.Words διαχειρίζεται εσωτερικά τους εγγενείς πόρους. Όταν η JVM τερματίσει, οι πόροι απελευθερώνονται. Για εφαρμογές μεγάλης διάρκειας, καλέστε `doc.dispose();` αν χρησιμοποιείτε την έκδοση **Aspose.Words for Java (Native)**. |
| *Πώς αλλάζω τη σειρά Z ώστε ένα ορθογώνιο να εμφανίζεται πάνω;* | Χρησιμοποιήστε `groupShape.insertAfter(shape, referenceShape);` ή `groupShape.insertBefore(shape, referenceShape);` για να αλλάξετε τη σειρά των παιδιών μέσα στην ομάδα. |
| *Μπορώ να ομαδοποιήσω σχήματα σε διαφορετικές ενότητες;* | Όχι. Ένα `GroupShape` πρέπει να βρίσκεται μέσα σε μια ενιαία παράγραφο ή κοντέινερ σχήματος. Για ομαδοποίηση σε διαφορετικές ενότητες, δημιουργήστε ξεχωριστές ομάδες σε κάθε ενότητα. |

---

## Συμπέρασμα

Τώρα γνωρίζετε πώς να **create blank Word document** με το Aspose.Words for Java, **group shapes in Word**, να εφαρμόσετε στυλ **color rectangle shape**, και να **save document as docx**. Αυτό το πρότυπο επεκτείνεται σε πιο σύνθετες διατάξεις—απλώς προσθέστε επιπλέον σχήματα, προσαρμόστε τις μετατοπίσεις, και προαιρετικά ορίστε κείμενο, εικόνες ή υπερσυνδέσμους μέσα στην ομάδα.

**Επόμενα βήματα** που μπορείτε να εξερευνήσετε:

* Χρησιμοποιήστε **group shapes in Word** για να δημιουργήσετε διαγράμματα ροής ή προεπισκοπήσεις UI.
* Πειραματιστείτε με **save document as docx** σε συνδυασμό με μετατροπή σε PDF (`doc.save("out.pdf")`).
* Εφαρμόστε διαβαθμίσεις ή μοτίβα στο **color rectangle shape** για πιο πλούσιο οπτικό σχεδιασμό.
* Συνδυάστε ομαδοποιημένα σχήματα με πίνακες ή γραφήματα για προχωρημένα έγγραφα αναφοράς.

Νιώστε ελεύθεροι να τροποποιήσετε τις διαστάσεις, τα χρώματα ή τους τύπους σχημάτων ώστε να ταιριάζουν με την επωνυμία του έργου σας. Καλό προγραμματισμό!

## Τι Θα Πρέπει Να Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Using Document Shapes in Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}