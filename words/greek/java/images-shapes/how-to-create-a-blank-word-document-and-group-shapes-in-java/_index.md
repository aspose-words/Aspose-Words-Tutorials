---
category: general
date: 2026-09-24
description: Μάθετε πώς να δημιουργήσετε ένα κενό έγγραφο Word σε Java και να ομαδοποιήσετε
  σχήματα όπως ορθογώνια και γραμμές χρησιμοποιώντας το Aspose.Words. Περιλαμβάνει
  κώδικα βήμα‑βήμα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shapes
- add rectangle shape
- group shapes in word
- set shape size
language: el
lastmod: 2026-09-24
og_description: Δημιουργήστε ένα κενό έγγραφο Word σε Java και μάθετε πώς να ομαδοποιείτε
  σχήματα, να προσθέτετε σχήμα ορθογωνίου και να ορίζετε το μέγεθος του σχήματος με
  το Aspose.Words.
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: Δημιουργήστε ένα κενό έγγραφο Word και ομαδοποιήστε σχήματα σε Java – οδηγός
  βήμα‑βήμα
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Learn how to create a blank Word document in Java and group shapes
    like rectangles and lines using Aspose.Words. Includes step‑by‑step code.
  headline: How to create a blank Word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Πώς να δημιουργήσετε ένα κενό έγγραφο Word και να ομαδοποιήσετε σχήματα σε
  Java
url: /el/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε ένα κενό έγγραφο Word και να ομαδοποιήσετε σχήματα σε Java

Αν χρειάζεστε **να δημιουργήσετε ένα κενό έγγραφο Word** και στη συνέχεια να οργανώσετε πολλαπλά αντικείμενα σχεδίασης, αυτός ο οδηγός σας δείχνει ακριβώς πώς. Με τη χρήση του Aspose.Words for Java μπορείτε να εισάγετε ένα group shape, να προσθέσετε ένα rectangle shape, να σχεδιάσετε μια γραμμή και να ελέγξετε το μέγεθος και τη θέση κάθε σχήματος — όλα σε ένα εκτελέσιμο πρόγραμμα.

Θα περάσετε από κάθε βήμα, από την αρχικοποίηση του εγγράφου μέχρι την αποθήκευση του τελικού `.docx`. Στο τέλος θα καταλάβετε **πώς να ομαδοποιήσετε σχήματα**, **πώς να προσθέσετε rectangle shape** και **πώς να ορίσετε το μέγεθος του σχήματος** ώστε τα αρχεία Word σας να φαίνονται ακριβώς όπως θέλετε.

## Προαπαιτούμενα

- Java 17 ή νεότερη (ο κώδικας μεταγλωττίζεται με οποιοδήποτε πρόσφατο JDK)
- Βιβλιοθήκη Aspose.Words for Java (λήψη από την [Aspose website](https://products.aspose.com/words/java))
- IDE ή εργαλείο κατασκευής (Maven/Gradle) που μπορεί να προσθέσει το JAR του Aspose.Words στο classpath
- Βασικές γνώσεις σύνταξης Java

> **Συμβουλή:** Χρησιμοποιήστε Maven για διαχείριση εξαρτήσεων· προσθέστε `com.aspose:aspose-words:23.12` (ή την πιο πρόσφατη έκδοση) στο `pom.xml` σας.

## Βήμα 1: Δημιουργία κενό εγγράφου Word

Το πρώτο καθήκον είναι **να δημιουργήσετε ένα κενό έγγραφο Word**. Αυτό σας παρέχει έναν καθαρό καμβά στον οποίο μπορείτε αργότερα να εισάγετε σχήματα.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document
        Document document = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Γιατί είναι σημαντικό:* Ένα αντικείμενο `Document` αντιπροσωπεύει ολόκληρο το αρχείο `.docx`. Ξεκινώντας με ένα κενό έγγραφο εξασφαλίζετε ότι δεν υπάρχει κρυφή μορφοποίηση που θα επηρεάσει τα σχήματα που θα προσθέσετε.

## Βήμα 2: Εισαγωγή group shape – το δοχείο για πολλαπλά αντικείμενα

Ένα **group shape** λειτουργεί σαν δοχείο που σας επιτρέπει να μετακινείτε, να αλλάζετε μέγεθος ή να περιστρέφετε πολλά σχήματα μαζί. Αυτό αποτελεί τον πυρήνα του **πώς να ομαδοποιήσετε σχήματα** στο Word.

```java
        // Insert a group shape of width 300 points and height 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

*Εξήγηση:* Η μέθοδος `insertGroupShape` δημιουργεί ένα αντικείμενο `GroupShape` και το τοποθετεί στην τρέχουσα θέση του δρομέα. Όλα τα επόμενα σχήματα που θα `appendChild` σε αυτήν την ομάδα θα αντιμετωπίζονται ως μία ενιαία μονάδα.

## Βήμα 3: Προσθήκη rectangle shape και ορισμός του μεγέθους

Τώρα **προσθέτουμε rectangle shape** στην ομάδα και **ορίζουμε το μέγεθος του σχήματος** με ακρίβεια.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);   // set shape width
        rectangle.setHeight(100.0);  // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Add the rectangle to the group
        group.appendChild(rectangle);
```

*Γιατί πρέπει να ορίσετε το μέγεθος του σχήματος:* Το πλάτος και το ύψος ελέγχουν πώς εμφανίζεται το ορθογώνιο στη σελίδα. Οι μέθοδοι `setLeft` και `setTop` τοποθετούν το ορθογώνιο σε σχέση με το σημείο προέλευσης της ομάδας, δίνοντάς σας έλεγχο pixel‑perfect στη διάταξη.

## Βήμα 4: Προσθήκη line shape και ρύθμιση διαστάσεων

Μια γραμμή είναι ένα ακόμη συνηθισμένο αντικείμενο σχεδίασης. Θα **προσθέσουμε λογική παρόμοια με rectangle shape** σε μια γραμμή, δείχνοντας ότι οι ίδιες αρχές μεγέθους ισχύουν.

```java
        // Create a line shape
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);   // line length
        line.setHeight(0.0);    // height is zero for a horizontal line
        line.setLeft(20.0);
        line.setTop(130.0);

        // Add the line to the same group
        group.appendChild(line);
```

*Κύριο σημείο:* Παρόλο που μια γραμμή δεν έχει ύψος, εξακολουθείτε να χρησιμοποιείτε `setWidth` για να ορίσετε το μήκος της. Η τοποθέτηση (`setLeft`, `setTop`) ακολουθεί το ίδιο σύστημα συντεταγμένων με τα άλλα σχήματα.

## Βήμα 5: Αποθήκευση του εγγράφου με τα ομαδοποιημένα σχήματα

Τέλος, διατηρήστε τις αλλαγές αποθηκεύοντας το έγγραφο. Αυτό παράγει ένα αρχείο `.docx` που μπορείτε να ανοίξετε στο Microsoft Word για να επαληθεύσετε το αποτέλεσμα.

```java
        // Save the document to disk
        document.save("GroupShapeDemo.docx");
    }
}
```

**Αναμενόμενο αποτέλεσμα:** Το άνοιγμα του `GroupShapeDemo.docx` εμφανίζει μια κενή σελίδα που περιέχει ένα ομαδοποιημένο ορθογώνιο και μια γραμμή. Επιλέγοντας οποιοδήποτε σχήμα επιλέγεται ολόκληρη η ομάδα, επιτρέποντάς σας να τα μετακινήσετε μαζί.

## Συχνές ερωτήσεις και διαχείριση ειδικών περιπτώσεων

| Ερώτηση | Απάντηση |
|----------|--------|
| *Μπορώ να προσθέσω περισσότερα από δύο σχήματα στην ομάδα;* | Ναι. Καλέστε `group.appendChild(yourShape)` για κάθε επιπλέον σχήμα. |
| *Τι αν χρειαστώ διαφορετική μονάδα (π.χ. εκατοστά) για το μέγεθος;* | Το Aspose.Words χρησιμοποιεί points (1 point = 1/72 ίντσα). Μετατρέψτε με `Points = centimeters * 28.3465`. |
| *Θα διατηρήσει η ομάδα τη διάταξή της όταν το έγγραφο ανοιχτεί σε άλλο υπολογιστή;* | Απόλυτα. Όλα τα δεδομένα μεγέθους και θέσης αποθηκεύονται στο αρχείο `.docx`, καθιστώντας τη διάταξη φορητή. |
| *Πώς μπορώ να αποομαδοποιήσω τα σχήματα αργότερα;* | Ανακτήστε το αντικείμενο `GroupShape`, στη συνέχεια επαναλάβετε πάνω στο `group.getChildNodes(NodeType.SHAPE, true)` και μετακινήστε κάθε παιδί έξω από την ομάδα. |
| *Τι αν χρειαστεί να περιστρέψω ολόκληρη την ομάδα;* | Χρησιμοποιήστε `group.setRotationAngle(double angleInDegrees)` πριν αποθηκεύσετε. |

## Πλήρες, εκτελέσιμο παράδειγμα

Παρακάτω βρίσκεται το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε‑και‑επικολλήσετε στο IDE σας. Περιλαμβάνει όλες τις απαραίτητες εισαγωγές και σχόλια.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape (container)
        GroupShape group = builder.insertGroupShape(300.0, 200.0);

        // Step 3: Add a rectangle shape and set its size
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);
        rectangle.setHeight(100.0);
        rectangle.setLeft(20.0);
        rectangle.setTop(20.0);
        group.appendChild(rectangle);

        // Step 4: Add a line shape and configure its dimensions
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);
        line.setHeight(0.0);
        line.setLeft(20.0);
        line.setTop(130.0);
        group.appendChild(line);

        // Step 5: Save the document with the grouped shapes
        document.save("GroupShapeDemo.docx");
    }
}
```

Εκτελέστε το πρόγραμμα, ανοίξτε το `GroupShapeDemo.docx` στο Microsoft Word και θα δείτε τα ομαδοποιημένα σχήματα ακριβώς όπως περιγράφηκε.

## Συμπέρασμα

Τώρα ξέρετε πώς να **δημιουργήσετε ένα κενό έγγραφο Word**, **να ομαδοποιήσετε σχήματα στο Word**, **να προσθέσετε rectangle shape** και **να ορίσετε το μέγεθος του σχήματος** χρησιμοποιώντας το Aspose.Words for Java. Τοποθετώντας σχήματα μέσα σε ένα `GroupShape`, αποκτάτε πλήρη έλεγχο πάνω στη συλλογική θέση, κλίμακα και περιστροφή — ιδανικό για διαγράμματα, ροές εργασίας ή προσαρμοσμένα γραφικά ενσωματωμένα σε αυτοματοποιημένες αναφορές.

**Επόμενα βήματα:**  
- Εξερευνήστε **πώς να ομαδοποιήσετε σχήματα** με πιο σύνθετα αντικείμενα όπως εικόνες ή πλαίσια κειμένου.  
- Πειραματιστείτε με το `setRotationAngle` για να περιστρέψετε ολόκληρη την ομάδα.  
- Συνδυάστε αυτήν την τεχνική με mail‑merge για να δημιουργήσετε εξατομικευμένα έγγραφα που περιλαμβάνουν εμπορικά σήματα.

Αισθανθείτε ελεύθεροι να προσαρμόσετε τον κώδικα στα δικά σας έργα και να μοιραστείτε τα αποτελέσματά σας στα σχόλια!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετικές θεματικές που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στην υλοποίηση των δικών σας έργων.

- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}