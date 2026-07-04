---
category: general
date: 2026-05-26
description: Δημιουργήστε σχήμα ορθογωνίου σε ένα έγγραφο Word με Java και εφαρμόστε
  εφέ σκιάς. Μάθετε πώς να προσθέσετε σκιά σε σχήμα, να ορίσετε την απόσταση της σκιάς
  και να αποθηκεύσετε το αρχείο.
draft: false
keywords:
- create rectangle shape
- apply shadow effect
- create word document java
- add shape shadow
- set shadow distance
language: el
og_description: Δημιουργήστε σχήμα ορθογωνίου σε ένα έγγραφο Word σε Java, εφαρμόστε
  εφέ σκιάς, προσθέστε σκιά στο σχήμα και ορίστε την απόσταση σκιάς με το Aspose.Words.
og_title: Δημιουργία σχήματος ορθογωνίου σε έγγραφο Word με Java – Πλήρης οδηγός
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Create rectangle shape in a Java Word document and apply shadow effect.
    Learn how to add shape shadow, set shadow distance, and save the file.
  headline: Create Rectangle Shape in Java Word Document – Full Step‑by‑Step Guide
  type: TechArticle
- description: Create rectangle shape in a Java Word document and apply shadow effect.
    Learn how to add shape shadow, set shadow distance, and save the file.
  name: Create Rectangle Shape in Java Word Document – Full Step‑by‑Step Guide
  steps:
  - name: “Can I use a different shape?”
    text: Absolutely. Replace `ShapeType.RECTANGLE` with `ShapeType.OVAL`, `ShapeType.LINE`,
      or any other supported enum. The rest of the shadow code stays the same.
  - name: “What if I need multiple shadows?”
    text: Aspose.Words only supports a single shadow per shape. To simulate multiple
      shadows, duplicate the shape, offset each copy, and adjust the transparency.
  - name: “Is the shadow visible in LibreOffice?”
    text: Yes—Aspose.Words writes standard OOXML, which LibreOffice interprets correctly.
      The shadow may look slightly different due to rendering engines, but the effect
      persists.
  - name: “How do I change the shadow color to match my brand?”
    text: Just swap `java.awt.Color.GRAY` with any `java.awt.Color` you prefer, such
      as `new java.awt.Color(0, 120, 215)` for a corporate blue.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word Automation
title: Δημιουργία σχήματος ορθογωνίου σε έγγραφο Word με Java – Πλήρης οδηγός βήμα‑βήμα
url: /el/java/images-shapes/create-rectangle-shape-in-java-word-document-full-step-by-st/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία Σχήματος Ορθογωνίου σε Έγγραφο Word Java – Πλήρης Οδηγός Βήμα‑βήμα

Έχετε χρειαστεί ποτέ να **create rectangle shape** σε ένα έγγραφο Word Java αλλά δεν ήξερατε από πού να ξεκινήσετε; Δεν είστε μόνοι—πολλοί προγραμματιστές αντιμετωπίζουν αυτό το πρόβλημα όταν δημιουργούν αναφορές ή τιμολόγια προγραμματιστικά. Σε αυτό το tutorial θα δούμε ακριβώς πώς να **create rectangle shape**, να εφαρμόσουμε μια κομψή σκιά και να ρυθμίσουμε τη απόσταση της σκιάς ώστε το αποτέλεσμα να φαίνεται επαγγελματικό.

Θα χρησιμοποιήσουμε το Aspose.Words for Java, μια ισχυρή βιβλιοθήκη που σας επιτρέπει να χειρίζεστε αρχεία Word χωρίς να χρειάζεται εγκατεστημένο Microsoft Office. Στο τέλος αυτού του οδηγού θα μπορείτε να **create word document java** έργα που **add shape shadow**, **apply shadow effect**, και **set shadow distance** με μόνο λίγες γραμμές κώδικα.

---

## What You’ll Build

- Ένα νέο αρχείο `.docx` που περιέχει ένα κυανό ορθογώνιο.
- Μια ρεαλιστική σκιά που είναι θολή, κεκλιμένη και μερικώς διαφανής.
- Πλήρη έλεγχος της απόστασης της σκιάς από το σχήμα.
- Μια έτοιμη προς εκτέλεση κλάση Java που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο Maven ή Gradle.

Χωρίς εξωτερικά εργαλεία, χωρίς χειροκίνητα βήματα UI—απλώς καθαρός κώδικας.

---

## Prerequisites

- Java 8 ή νεότερη (ο κώδικας λειτουργεί σε Java 11, Java 17 κ.λπ.).
- Βιβλιοθήκη Aspose.Words for Java (διαθέσιμη μέσω Maven Central).
- Ένα IDE ή κειμενογράφο που προτιμάτε (IntelliJ IDEA, Eclipse, VS Code…).
- Βασική εξοικείωση με τη σύνταξη της Java.

Αν δεν έχετε προσθέσει ποτέ εξάρτηση Maven, εδώ είναι το γρήγορο απόσπασμα:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

Τώρα, ας βουτήξουμε.

---

## Step 1: Create Rectangle Shape in a Word Document

Το πρώτο που χρειάζεται είναι ένα κενό έγγραφο και ένας `DocumentBuilder`. Σκεφτείτε τον builder ως ένα στυλό που γράφει στο έγγραφο. Μόλις το έχουμε, μπορούμε να **create rectangle shape** με μία μόνο κλήση μεθόδου.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a rectangle shape of 150x80 points.
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
        // Make the shape visible by filling it with cyan.
        rectangleShape.setFillColor(java.awt.Color.CYAN);
```

> **Why this matters:** Η μέθοδος `insertShape` δεν δημιουργεί μόνο τη γεωμετρία αλλά προσθέτει επίσης το σχήμα στη εσωτερική συλλογή του εγγράφου, ώστε να μπορείτε αμέσως να αρχίσετε να το μορφοποιείτε.

---

## Step 2: Apply Shadow Effect to the Shape

Τώρα που το ορθογώνιο βρίσκεται στη σελίδα, θα **apply shadow effect**. Οι σκιές δίνουν βάθος, κάνοντας το σχήμα να φαίνεται σαν να αιωρείται πάνω από τη σελίδα—μια διακριτική βελτίωση UI που μπορεί να ενισχύσει την αναγνωσιμότητα σε αναφορές.

```java
        // Retrieve the shadow format object.
        ShadowFormat shadowFormat = rectangleShape.getShadowFormat();

        // Enable the shadow and configure its appearance.
        shadowFormat.setVisible(true);          // Turn the shadow on.
        shadowFormat.setBlur(5.0);              // Soft blur radius.
        shadowFormat.setAngle(45.0);            // Direction of the shadow.
        shadowFormat.setColor(java.awt.Color.GRAY); // Shadow color.
        shadowFormat.setTransparency(0.3);     // 30% transparent.
```

> **Pro tip:** Ένα blur των `5.0` φαίνεται φυσικό για τα περισσότερα έγγραφα που προβάλλονται σε οθόνη. Αν εκτυπώνετε, ίσως θέλετε μια ελαφρώς χαμηλότερη τιμή ώστε να αποφύγετε την ασαφή εμφάνιση.

---

## Step 3: Set Shadow Distance – Fine‑Tuning Placement

Οι σκιές δεν αφορούν μόνο το blur· χρειάζεται επίσης το σωστό offset. Εδώ **set shadow distance**. Μια απόσταση `7.0` points δημιουργεί ένα μέτριο offset που είναι εμφανές αλλά όχι υπερβολικό.

```java
        // Define how far the shadow sits from the shape.
        shadowFormat.setDistance(7.0); // Distance in points.
```

> **What if you need a bigger offset?** Αυξήστε την τιμή· μειώστε την για πιο στενό αποτέλεσμα. Θυμηθείτε, η απόσταση λειτουργεί μαζί με τη γωνία για να τοποθετήσει σωστά τη σκιά.

---

## Step 4: Save the Document – Persist Your Work

Τέλος, γράφουμε το έγγραφο στο δίσκο. Αλλάξτε τη διαδρομή στο σημείο που θέλετε να αποθηκευτεί το αρχείο.

```java
        // Save the document with the rectangle and its shadow.
        doc.save("YOUR_DIRECTORY/shadow.docx");
    }
}
```

Η εκτέλεση της κλάσης δημιουργεί ένα αρχείο `shadow.docx` που, όταν ανοίξει στο Microsoft Word ή στο LibreOffice, εμφανίζει ένα κυανό ορθογώνιο με μια απαλή γκρι σκιά κεκλιμένη κατά 45° και offset κατά 7 points.

---

## Full Working Example

Παρακάτω είναι ο πλήρης, έτοιμος για αντιγραφή‑και‑επικόλληση κώδικας. Περιλαμβάνει όλες τις εισαγωγές, σχόλια και την τελική κλήση `save`.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a rectangle shape of the desired size.
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
        // Step 3: Apply a fill color to make the shape visible.
        rectangleShape.setFillColor(java.awt.Color.CYAN);

        // Step 4: Configure the shape's shadow effect.
        ShadowFormat shadowFormat = rectangleShape.getShadowFormat();
        shadowFormat.setVisible(true);          // Enable the shadow.
        shadowFormat.setBlur(5.0);              // Set the blur radius.
        shadowFormat.setDistance(7.0);          // Define how far the shadow is from the shape.
        shadowFormat.setAngle(45.0);            // Set the direction of the shadow.
        shadowFormat.setColor(java.awt.Color.GRAY); // Choose the shadow color.
        shadowFormat.setTransparency(0.3);      // Make the shadow partially transparent.

        // Step 5: Save the document with the shaped shadow.
        doc.save("YOUR_DIRECTORY/shadow.docx");
    }
}
```

**Expected output:** Ανοίξτε το `shadow.docx` → θα δείτε ένα κυανό ορθογώνιο κεντραρισμένο στην πρώτη σελίδα, ρίχνοντας μια διακριτική γκρι σκιά ελαφρώς μετατοπισμένη προς τα κάτω‑δεξιά. Το blur και η διαφάνεια της σκιάς το κάνουν να μοιάζει με φυσικό φωτισμό.

---

## Common Questions & Edge Cases

### “Can I use a different shape?”

Απολύτως. Αντικαταστήστε το `ShapeType.RECTANGLE` με `ShapeType.OVAL`, `ShapeType.LINE` ή οποιοδήποτε άλλο υποστηριζόμενο enum. Ο υπόλοιπος κώδικας σκιάς παραμένει ίδιος.

### “What if I need multiple shadows?”

Το Aspose.Words υποστηρίζει μόνο μία σκιά ανά σχήμα. Για να προσομοιώσετε πολλαπλές σκιές, διπλασιάστε το σχήμα, μετατοπίστε κάθε αντίγραφο και ρυθμίστε τη διαφάνεια.

### “Is the shadow visible in LibreOffice?”

Ναι—το Aspose.Words γράφει τυπικό OOXML, το οποίο το LibreOffice ερμηνεύει σωστά. Η σκιά μπορεί να φαίνεται ελαφρώς διαφορετική λόγω των μηχανών απόδοσης, αλλά το εφέ παραμένει.

### “How do I change the shadow color to match my brand?”

Απλώς αντικαταστήστε το `java.awt.Color.GRAY` με οποιοδήποτε `java.awt.Color` προτιμάτε, π.χ. `new java.awt.Color(0, 120, 215)` για ένα εταιρικό μπλε.

---

## Image Illustration

![create rectangle shape in Java Word document](https://example.com/images/rectangle-shadow.png)

*Alt text:* **create rectangle shape** εικονογράφηση που δείχνει ένα κυανό ορθογώνιο με γκρι σκιά σε έγγραφο Word.

---

## Recap & Next Steps

Καλύψαμε πώς να **create rectangle shape**, **apply shadow effect**, **add shape shadow**, και **set shadow distance** χρησιμοποιώντας το Aspose.Words for Java. Ο κώδικας είναι αυτόνομος, τρέχει σε οποιοδήποτε σύγχρονο JDK και παράγει ένα επαγγελματικό αρχείο `.docx` έτοιμο για διανομή.

Θέλετε να προχωρήσετε παραπέρα; Δοκιμάστε:

- Προσθήκη κειμένου μέσα στο ορθογώνιο με `builder.moveTo(rectangleShape.getAbsolutePosition())`.
- Δημιουργία πίνακα σχημάτων για την κατασκευή διαγράμματος.
- Εξαγωγή του εγγράφου σε PDF (`doc.save("output.pdf", SaveFormat.PDF);`).

Κάθε μία από αυτές τις ενέργειες βασίζεται στα ίδια θεμέλια που μόλις εξερευνήσαμε, ώστε να αισθάνεστε άνετα να επεκτείνετε το παράδειγμα.

---

## Final Thoughts

Η εξοικείωση με εργασίες **create word document java** όπως η δημιουργία σχημάτων και η εφαρμογή σκιών σας δίνει τεράστια προβάδισμα όταν αυτοματοποιείτε αναφορές, συμβόλαια ή διαφημιστικό υλικό. Η προσέγγιση που παρουσιάστηκε εδώ είναι καθαρή, συντηρήσιμη και—το πιο σημαντικό—εύκολη στην προσαρμογή για οποιοδήποτε στυλ θέλετε.

Δοκιμάστε τον κώδικα, πειραματιστείτε με το blur, τη γωνία και την απόσταση, και παρακολουθήστε τα έγγραφά σας να μετατρέπονται από απλά σε εντυπωσιακά. Αν αντιμετωπίσετε κάποιο πρόβλημα, αφήστε ένα σχόλιο παρακάτω· θα χαρώ να βοηθήσω.

Happy coding!

## Related Tutorials

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Create PDF from Word with Barcode Generation – Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-barcode-generation/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}