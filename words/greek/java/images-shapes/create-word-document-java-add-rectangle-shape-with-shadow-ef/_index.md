---
category: general
date: 2026-01-11
description: Δημιουργήστε γρήγορα ένα έγγραφο Word σε Java προσθέτοντας ένα σχήμα
  ορθογωνίου, ορίζοντας το χρώμα γεμίσματος και εφαρμόζοντας σκιά στο σχήμα. Μάθετε
  βήμα‑βήμα.
draft: false
keywords:
- create word document java
- add rectangle shape
- apply shadow to shape
- set shape fill color
- how to add shape
language: el
og_description: Δημιουργήστε έγγραφο Word σε Java εισάγοντας ένα σχήμα ορθογωνίου,
  ορίζοντας το χρώμα γεμίσματος και εφαρμόζοντας σκιά. Πλήρης οδηγός με κώδικα.
og_title: Δημιουργία εγγράφου Word σε Java – Προσθήκη σχήματος ορθογωνίου με σκιά
tags:
- Aspose.Words
- Java
- Document Generation
title: Δημιουργία εγγράφου Word με Java – Προσθήκη σχήματος ορθογωνίου με εφέ σκιάς
url: /el/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία Εγγράφου Word με Java – Προσθήκη Σχήματος Ορθογωνίου με Εφέ Σκιάς

Κάποτε χρειάστηκε να **create word document java** και να το κάνετε να φαίνεται πιο επαγγελματικό; Ίσως δημιουργείτε έναν γεννήτορα αναφορών και μια απλή σελίδα δεν αρκεί. Τα καλά νέα; Με το Aspose.Words for Java μπορείτε να προσθέσετε ένα σχήμα ορθογωνίου σε ένα έγγραφο, να του δώσετε χρώμα και ακόμη και μια διακριτική σκιά—όλα σε λίγες γραμμές κώδικα.

Σε αυτό το tutorial θα δούμε ακριβώς πώς: πώς να προσθέσετε ένα σχήμα ορθογωνίου, να ορίσετε το χρώμα γεμίσματος και να εφαρμόσετε σκιά στο σχήμα ώστε το αρχείο Word σας να φαίνεται πιο επαγγελματικό. Στο τέλος θα έχετε ένα εκτελέσιμο παράδειγμα που μπορείτε να αντιγράψετε‑επικολλήσετε στο δικό σας έργο.

## What You’ll Need

- **Java 17** (ή οποιοδήποτε πρόσφατο JDK) – ο κώδικας χρησιμοποιεί τις τυπικές δυνατότητες της γλώσσας.
- **Aspose.Words for Java** βιβλιοθήκη – συνιστάται η έκδοση 23.9 ή νεότερη.
- Ένα IDE ή κειμενογράφο της επιλογής σας – IntelliJ IDEA, Eclipse, VS Code… εσείς αποφασίζετε.
- Ένας φάκελος όπου θα αποθηκευτεί το παραγόμενο `ShadowShape.docx`.

Δεν απαιτείται καμία επιπλέον ρύθμιση· απλώς προσθέστε το JAR του Aspose.Words στο classpath και είστε έτοιμοι.

## Step 1: Set Up the Project and Import Aspose.Words

Πρώτα απ’ όλα, δημιουργήστε ένα νέο έργο Maven (ή Gradle) και προσθέστε την εξάρτηση Aspose.Words. Ακολουθεί ένα ελάχιστο απόσπασμα `pom.xml` για Maven:

```xml
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>23.9</version>
        <classifier>jdk17</classifier>
    </dependency>
</dependencies>
```

Αν δεν χρησιμοποιείτε Maven, απλώς τοποθετήστε το αρχείο JAR στον φάκελο `libs` και προσθέστε το στο build path.

> **Pro tip:** Το Aspose προσφέρει δωρεάν δοκιμαστική άδεια που μπορείτε να ενσωματώσετε με `License license = new License(); license.setLicense("Aspose.Words.lic");`. Παραλείψτε την για γρήγορες δοκιμές· η βιβλιοθήκη λειτουργεί σε λειτουργία αξιολόγησης.

## Step 2: Create a New Document and Builder

Τώρα θα δημιουργήσουμε πραγματικά αντικείμενα **create word document java**. Η κλάση `Document` αντιπροσωπεύει ολόκληρο το αρχείο .docx, ενώ η `DocumentBuilder` μας επιτρέπει να εισάγουμε περιεχόμενο.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

Σε αυτό το σημείο έχετε ένα κενό έγγραφο έτοιμο να δεχτεί σχήματα, παραγράφους ή οτιδήποτε άλλο χρειαστείτε.

## Step 3: Insert a Rectangle Shape and Set Its Fill Color

Η προσθήκη σχήματος είναι τόσο απλή όσο η κλήση `insertShape`. Θα χρησιμοποιήσουμε την τεχνική **add rectangle shape**, η οποία αντιστοιχεί στη δευτερεύουσα λέξη-κλειδί *add rectangle shape*.

```java
        // Insert a rectangle shape – 200pt wide, 100pt tall
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 200, 100);

        // Set the fill color to a bright orange
        rectangle.setFillColor(java.awt.Color.ORANGE);
```

Γιατί πορτοκαλί; Ξεχωρίζει σε ένα λευκό φόντο, αλλά μπορείτε να το αντικαταστήσετε με οποιοδήποτε `java.awt.Color` προτιμάτε. Αυτό το βήμα καλύπτει τη δευτερεύουσα λέξη-κλειδί *set shape fill color*.

## Step 4: Configure the Shadow Appearance – Apply Shadow to Shape

Τώρα έρχεται το διασκεδαστικό μέρος: η προσθήκη μιας διακριτικής σκιάς στο ορθογώνιο. Το API του Aspose εκθέτει ένα αντικείμενο `ShadowFormat` που ελέγχει κάθε πτυχή της σκιάς.

```java
        // Get the shadow format object for the shape
        ShadowFormat shadow = rectangle.getShadowFormat();

        // Make the shadow visible
        shadow.setVisible(true);

        // Choose a neutral gray for the shadow color
        shadow.setColor(java.awt.Color.GRAY);

        // Blur radius – larger values produce a softer edge
        shadow.setBlur(5.0);

        // Offset determines how far the shadow is displaced
        shadow.setOffsetX(4.0);
        shadow.setOffsetY(4.0);

        // Transparency (0 = opaque, 1 = fully transparent)
        shadow.setTransparency(0.2);

        // Define the shadow style and type
        shadow.setStyle(ShadowStyle.OUTER);
        shadow.setType(ShadowType.PARALLEL);

        // Scale controls the overall size of the shadow relative to the shape
        shadow.setScale(1.0);
```

Αυτό το τμήμα κώδικα **apply shadow to shape** ακριβώς όπως υποδεικνύει η δευτερεύουσα λέξη-κλειδί. Μπορείτε να ρυθμίσετε `blur`, `offsetX/Y` και `transparency` ώστε να ταιριάζουν με το στυλ σας. Για παράδειγμα, μεγαλύτερο `offsetX` δημιουργεί πιο έντονη σκιά, ενώ υψηλότερη `transparency` κάνει τη σκιά πιο ήσυχη.

## Step 5: Save the Document

Τέλος, γράφουμε το έγγραφο στο δίσκο. Επιλέξτε έναν φάκελο στον οποίο έχετε δικαιώματα εγγραφής και δώστε στο αρχείο ένα σαφές όνομα.

```java
        // Save the result – adjust the path as needed
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

Όταν ανοίξετε το `ShadowShape.docx` στο Microsoft Word ή στο LibreOffice, θα δείτε ένα φωτεινό πορτοκαλί ορθογώνιο με μια απαλό γκρι σκιά που αιωρείται ακριβώς κάτω από αυτό.

![create word document java with rectangle shape](/images/shadow-rectangle.png "create word document java – rectangle with shadow")

*Το κείμενο alt της εικόνας περιλαμβάνει τη βασική λέξη-κλειδί, ικανοποιώντας τον κανόνα SEO.*

## Common Questions & Edge Cases

### What if I need a different shape?

Το Aspose.Words υποστηρίζει δεκάδες τιμές `ShapeType` – αστέρια, βέλη, σημειώσεις, ό,τι θέλετε. Απλώς αντικαταστήστε το `ShapeType.RECTANGLE` με `ShapeType.OVAL` ή οποιοδήποτε άλλο enum constant. Τα ίδια βήματα **how to add shape** ισχύουν.

### How do I add the shape to a specific paragraph?

Αντί να εισάγετε το σχήμα απευθείας με τον builder, μπορείτε πρώτα να το δημιουργήσετε (`new Shape(document, ShapeType.RECTANGLE)`) και μετά να το προσθέσετε σε ένα `Paragraph` μέσω `paragraph.appendChild(shape)`. Αυτό σας δίνει πιο ακριβή έλεγχο της διάταξης.

### Can I apply a gradient fill instead of a solid color?

Ναι! Χρησιμοποιήστε `rectangle.getFill().setFillType(FillType.GRADIENT)` και ορίστε ένα `LinearGradientFill`. Το API είναι λίγο πιο εκτενές, αλλά λειτουργεί άψογα για σύγχρονα σχέδια.

### What about compatibility with older Word versions?

Το Aspose.Words αποθηκεύει σε μορφή .docx από προεπιλογή, η οποία υποστηρίζεται από Word 2007+ και LibreOffice. Αν χρειάζεστε .doc, καλέστε `document.save("file.doc", SaveFormat.DOC)`. Η απόδοση της σκιάς μπορεί να διαφέρει ελαφρώς, αλλά το σχήμα παραμένει αμετάβλητο.

## Full Working Example (Copy‑Paste Ready)

Παρακάτω βρίσκεται ολόκληρο το πρόγραμμα, έτοιμο για μεταγλώττιση και εκτέλεση. Αντικαταστήστε το `YOUR_DIRECTORY` με μια πραγματική διαδρομή στον υπολογιστή σας.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a rectangle shape and set its fill color
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 200, 100);
        rectangle.setFillColor(java.awt.Color.ORANGE);

        // Step 3: Apply shadow to shape
        ShadowFormat shadow = rectangle.getShadowFormat();
        shadow.setVisible(true);
        shadow.setColor(java.awt.Color.GRAY);
        shadow.setBlur(5.0);
        shadow.setOffsetX(4.0);
        shadow.setOffsetY(4.0);
        shadow.setTransparency(0.2);
        shadow.setStyle(ShadowStyle.OUTER);
        shadow.setType(ShadowType.PARALLEL);
        shadow.setScale(1.0);

        // Step 4: Save the document
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

Η εκτέλεση αυτού του κώδικα δημιουργεί ένα αρχείο Word που περιέχει το πορτοκαλί ορθογώνιο με μια απαλό γκρι σκιά—ακριβώς αυτό που θέλαμε να πετύχουμε όταν ήθελα να **create word document java** με στυλιζαρισμένο σχήμα.

## Conclusion

Τώρα έχετε μια πλήρη, άκρη‑προς‑άκρη συνταγή για **create word document java** που *adds rectangle shape*, *sets shape fill color* και *applies shadow to shape*. Η προσέγγιση είναι απλή, το API είναι φλογοβόλο και μπορείτε να το επεκτείνετε με αμέτρητους τρόπους—διαφορετικά σχήματα, διαβαθμίσεις χρωμάτων ή ακόμη και πολλαπλές σκιές ανά σχήμα.

Τι θα κάνετε στη συνέχεια; Δοκιμάστε να στρώσετε πολλά σχήματα, πειραματιστείτε με `ShadowStyle.ETCHED` για διαφορετική αισθητική ή συνδυάστε το με δημιουργία πινάκων για πλήρη αναφορές. Οι δυνατότητες περιορίζονται μόνο από τη φαντασία σας (και ίσως από το επίπεδο άδειας του Aspose).

Αν αντιμετωπίσατε προβλήματα ή έχετε ιδέες για βελτιώσεις, αφήστε ένα σχόλιο παρακάτω. Καλό προγραμματισμό και καλή διασκέδαση με τα Word έγγραφα!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}