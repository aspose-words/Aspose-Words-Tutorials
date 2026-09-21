---
category: general
date: 2026-09-21
description: Δημιουργήστε έγγραφο Word προγραμματιστικά χρησιμοποιώντας Java. Μάθετε
  πώς να ομαδοποιείτε σχήματα στο Word, να εισάγετε ένα σχήμα ορθογωνίου, να ορίσετε
  το μέγεθος του σχήματος και να προσθέσετε σχήματα σε ένα έγγραφο Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- how to group shapes in word
- how to insert rectangle shape
- add shapes to word document
- set shape size word
language: el
lastmod: 2026-09-21
og_description: 'Δημιουργήστε έγγραφο Word προγραμματιστικά με Java: αυτός ο οδηγός
  δείχνει πώς να ομαδοποιήσετε σχήματα στο Word, να εισάγετε σχήματα ορθογωνίου, να
  ορίσετε το μέγεθος του σχήματος και να προσθέσετε σχήματα σε ένα έγγραφο Word.'
og_image_alt: Screenshot of a Java program creating a Word document with grouped shapes
og_title: Δημιουργία εγγράφου Word προγραμματιστικά, ομαδοποίηση σχημάτων σε Java
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically using Java. Learn how to group
    shapes in Word, insert a rectangle shape, set shape size, and add shapes to a
    Word document.
  headline: Create word document programmatically, group shapes in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Word automation
- Shapes
title: Δημιουργία εγγράφου Word προγραμματιστικά, ομαδοποίηση σχημάτων σε Java
url: /el/java/images-shapes/create-word-document-programmatically-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία εγγράφου Word προγραμματιστικά, ομαδοποίηση σχημάτων σε Java

Αν χρειάζεστε **να δημιουργήσετε έγγραφο Word προγραμματιστικά**, αυτός ο οδηγός σας καθοδηγεί βήμα προς βήμα σε μια πλήρη λύση. Θα δείτε πώς να **ομαδοποιήσετε σχήματα στο Word**, να εισάγετε ένα ορθογώνιο, να ορίσετε το μέγεθός του και να προσθέσετε άλλα σχήματα—όλα χρησιμοποιώντας Java και τη βιβλιοθήκη Aspose.Words for Java.

Ο οδηγός καλύπτει κάθε βήμα από τη ρύθμιση του έργου μέχρι την αποθήκευση του τελικού αρχείου .docx. Στο τέλος θα μπορείτε να δημιουργήσετε ένα έγγραφο Word που περιέχει ένα ορθογώνιο και μια εικόνα τυλιγμένα μέσα σε μια ενιαία ομάδα, καθιστώντας εύκολη τη μετακίνηση ή την αλλαγή μεγέθους τους μαζί. Δεν απαιτείται προηγούμενη εμπειρία με το Aspose.Words API, αλλά θα πρέπει να έχετε ένα βασικό περιβάλλον ανάπτυξης Java.

## Προαπαιτούμενα

* Java Development Kit (JDK) 8 ή νεότερο  
* Maven ή Gradle για διαχείριση εξαρτήσεων  
* Aspose.Words for Java 23.9 (ή την πιο πρόσφατη έκδοση) – η βιβλιοθήκη είναι δωρεάν για αξιολόγηση  
* Αρχείο εικόνας (π.χ., `sample.jpg`) τοποθετημένο σε γνωστό φάκελο  

Η προετοιμασία αυτών των στοιχείων εξασφαλίζει ότι ο κώδικας θα εκτελεστεί χωρίς πρόσθετη διαμόρφωση.

## Βήμα 1: Ρύθμιση του έργου και εισαγωγή του Aspose.Words

Δημιουργήστε ένα έργο Maven (ή προσθέστε την εξάρτηση στο υπάρχον `pom.xml`):

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Αν προτιμάτε Gradle, προσθέστε τα παρακάτω στο `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:23.9'
```

Αφού η εξάρτηση λυθεί, εισάγετε τις απαιτούμενες κλάσεις στο αρχείο πηγαίου κώδικα Java:

```java
import com.aspose.words.*;
import java.io.File;
```

## Βήμα 2: Δημιουργία του εγγράφου Word προγραμματιστικά

Η πρώτη ενέργεια σε οποιοδήποτε σενάριο αυτοματοποίησης είναι η δημιουργία ενός αντικειμένου `Document` και ενός `DocumentBuilder`. Ο builder απλοποιεί την εισαγωγή κειμένου, εικόνων και σχημάτων.

```java
public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Σε αυτό το σημείο το έγγραφο υπάρχει μόνο στη μνήμη. Μπορείτε τώρα να αρχίσετε να προσθέτετε σχήματα.

## Βήμα 3: Εισαγωγή σχήματος ορθογωνίου – πώς να εισάγετε σχήμα ορθογωνίου

Ένα ορθογώνιο είναι ένα βασικό `Shape` με `ShapeType.RECTANGLE`. Ελέγχετε τις διαστάσεις του με `setWidth`, `setHeight` και τη θέση του με `setTop` και `setLeft`.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);
        rectangle.setTop(10.0);
        rectangle.setLeft(10.0);

        // Optional: give the rectangle a visible fill and line color
        rectangle.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);
        rectangle.getStrokeColor().setColor(java.awt.Color.DARK_GRAY);
```

**Γιατί είναι σημαντικό:** Ο καθορισμός του μεγέθους και της θέσης ρητά (`set shape size word`) εγγυάται ότι το ορθογώνιο εμφανίζεται ακριβώς εκεί που το περιμένετε, ανεξάρτητα από την προεπιλεγμένη διάταξη του εγγράφου.

## Βήμα 4: Εισαγωγή εικόνας – προσθήκη σχημάτων στο έγγραφο Word

Το `DocumentBuilder` μπορεί να εισάγει μια εικόνα απευθείας από διαδρομή αρχείου. Μετά την εισαγωγή, μπορείτε να επανατοποθετήσετε την εικόνα όπως οποιοδήποτε άλλο σχήμα.

```java
        // Insert an image; replace the path with your own image location
        String imagePath = "YOUR_DIRECTORY/sample.jpg";
        if (!new File(imagePath).exists()) {
            throw new IllegalArgumentException("Image file not found: " + imagePath);
        }
        Shape picture = builder.insertImage(imagePath);
        picture.setTop(70.0);
        picture.setLeft(10.0);
```

Τόσο το ορθογώνιο όσο και η εικόνα είναι τώρα ανεξάρτητα σχήματα μέσα στο έγγραφο.

## Βήμα 5: Ομαδοποίηση των σχημάτων – πώς να ομαδοποιήσετε σχήματα στο Word

Η ομαδοποίηση σχημάτων είναι χρήσιμη όταν θέλετε να τα μετακινήσετε ή να αλλάξετε το μέγεθός τους ως μία ενιαία μονάδα. Το Aspose.Words παρέχει έναν κοντέινερ `GroupShape` για αυτόν τον σκοπό.

```java
        // Create a GroupShape that will contain the rectangle and the picture
        GroupShape group = builder.insertGroupShape();

        // Append the rectangle and picture to the group
        group.appendChild(rectangle);
        group.appendChild(picture);
```

Όταν η ομάδα αποθηκευτεί, το Word αντιμετωπίζει τα δύο παιδιά ως ένα λογικό αντικείμενο. Μπορείτε αργότερα να επιλέξετε την ομάδα και να τη σύρετε, και τόσο το ορθογώνιο όσο και η εικόνα θα ακολουθήσουν.

## Βήμα 6: Αποθήκευση του εγγράφου

Τέλος, γράψτε το έγγραφο στο δίσκο. Η διαδρομή πρέπει να είναι εγγράψιμη από τη διαδικασία Java.

```java
        // Save the document with the grouped shapes
        String outputPath = "YOUR_DIRECTORY/GroupShapeExample.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Η εκτέλεση της μεθόδου `main` παράγει ένα αρχείο με όνομα **GroupShapeExample.docx**. Ανοίξτε το στο Microsoft Word για να δείτε ένα ορθογώνιο και μια εικόνα κλειδωμένα μαζί μέσα σε μια ομάδα. Η επιλογή της ομάδας σας επιτρέπει να μετακινήσετε και τα δύο αντικείμενα ταυτόχρονα, επιβεβαιώνοντας ότι η ομαδοποίηση πέτυχε.

## Αναμενόμενο αποτέλεσμα

* Ένα αρχείο Word (`GroupShapeExample.docx`) τοποθετημένο στον φάκελο που καθορίσατε.  
* Μέσα στο αρχείο, ένα ορθογώνιο (γεμισμένο με ανοιχτό γκρι) εμφανίζεται στην επάνω‑αριστερή γωνία, και η εικόνα βρίσκεται ακριβώς κάτω από αυτό.  
* Και τα δύο αντικείμενα είναι μέρος μιας ενιαίας ομάδας, έτσι η μετακίνηση του ενός μετακινεί και το άλλο.

## Συνηθισμένες παραλλαγές και ειδικές περιπτώσεις

| Κατάσταση | Σύσταση |
|-----------|----------|
| **Διαφορετικές μορφές εικόνας** | Το Aspose.Words υποστηρίζει PNG, BMP, GIF και TIFF. Χρησιμοποιήστε την κατάλληλη επέκταση αρχείου στη `insertImage`. |
| **Αρνητικές διαστάσεις** | Το API ρίχνει `ArgumentException`. Πάντα να επικυρώνετε το πλάτος και το ύψος πριν καλέσετε `setWidth` / `setHeight`. |
| **Μεγάλα έγγραφα** | Η ομαδοποίηση πολλών σχημάτων μπορεί να αυξήσει το μέγεθος του αρχείου. Σκεφτείτε τη συγχώνευση των σχημάτων σε μία ενιαία εικόνα όταν η απόδοση είναι κρίσιμη. |
| **Συμβατότητα έκδοσης Word** | Το GroupShape λειτουργεί με Word 2007 (`.docx`) και νεότερες εκδόσεις. Για παλαιότερα αρχεία `.doc`, η ομάδα θα ισοπεδωθεί. |
| **Δυναμική τοποθέτηση** | Χρησιμοποιήστε υπολογισμούς βασισμένους στο μέγεθος σελίδας (`doc.getFirstSection().getPageSetup().getPageWidth()`) εάν χρειάζεστε προσαρμοστική τοποθέτηση. |

**Συμβουλή:** Μετά τη δημιουργία της ομάδας, μπορείτε να αλλάξετε

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετικές θεματικές που επεκτείνουν τις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Δημιουργία εγγράφου Word Java – Προσθήκη σχήματος ορθογωνίου με εφέ σκιά](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Δημιουργία σχήματος ορθογωνίου στο Word με Java – Πλήρης Οδηγός](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Δημιουργία Group Shape σε έγγραφο Word χρησιμοποιώντας Aspose.Words για .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}