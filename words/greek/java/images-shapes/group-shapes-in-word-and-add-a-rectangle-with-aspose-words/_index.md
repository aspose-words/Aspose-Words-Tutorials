---
category: general
date: 2026-09-11
description: Ομαδοποιήστε σχήματα στο Word και προσθέστε ένα σχήμα ορθογωνίου χρησιμοποιώντας
  το Aspose.Words for Java. Μάθετε πώς να ορίζετε το μέγεθος του σχήματος, να ομαδοποιείτε
  αντικείμενα και να αποθηκεύετε το έγγραφο.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- set shape size
- how to group shapes
- how to add rectangle
language: el
lastmod: 2026-09-11
og_description: Ομαδοποιήστε σχήματα στο Word και προσθέστε ένα σχήμα ορθογωνίου χρησιμοποιώντας
  το Aspose.Words for Java. Αυτό το σεμινάριο δείχνει πώς να ορίσετε το μέγεθος του
  σχήματος, να ομαδοποιήσετε σχήματα και να εξάγετε το έγγραφο.
og_image_alt: Screenshot showing grouped shapes in a Word document
og_title: Ομαδοποίηση σχημάτων στο Word – προσθήκη ορθογωνίου με το Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  headline: Group shapes in Word and add a rectangle with Aspose.Words
  type: TechArticle
- description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  name: Group shapes in Word and add a rectangle with Aspose.Words
  steps:
  - name: Prerequisites
    text: '* Java 17 or later installed. * Maven or Gradle to manage dependencies.
      * A valid Aspose.Words for Java license (or a free evaluation key). * An image
      file (`sample.png`) placed in a known directory (replace `YOUR_DIRECTORY` with
      your actual path).'
  - name: Add a group shape
    text: A group shape is a container that can hold other shapes. Think of it as
      a folder for drawing objects.
  - name: How to add rectangle
    text: The code above demonstrates **how to add rectangle** by creating a `Shape`
      instance with `ShapeType.RECTANGLE` and then appending it to the `GroupShape`.
      This pattern works for any other shape type (e.g., `ELLIPSE`, `POLYLINE`).
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Ομαδοποίηση σχημάτων στο Word και προσθήκη ορθογωνίου με το Aspose.Words
url: /el/java/images-shapes/group-shapes-in-word-and-add-a-rectangle-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ομαδοποίηση σχημάτων στο Word και προσθήκη ορθογωνίου με Aspose.Words

Αν χρειάζεστε **ομαδοποίηση σχημάτων στο Word** ενώ προσθέτετε προγραμματιστικά ένα ορθογώνιο, αυτός ο οδηγός σας παρέχει μια πλήρη, έτοιμη‑για‑εκτέλεση λύση. Θα δείτε ακριβώς πώς να εισάγετε ένα group shape, να προσθέσετε ένα rectangle shape, να ορίσετε το μέγεθος του σχήματος και, τέλος, να αποθηκεύσετε το έγγραφο ώστε να μπορείτε να δείτε το αποτέλεσμα αμέσως.

Η εργασία με έγγραφα Word συχνά σημαίνει την οργάνωση πολλαπλών αντικειμένων—εικόνων, διαγραμμάτων ή απλών γεωμετρικών σχημάτων—σε μια ενιαία λογική μονάδα. Η ομαδοποίηση αυτών των αντικειμένων καθιστά ευκολότερη τη μετακίνηση, περιστροφή ή μορφοποίηση τους μαζί. Σε αυτό το tutorial θα καλύψουμε επίσης **πώς να προσθέσετε ορθογώνιο** σχήμα και **πώς να ορίσετε το μέγεθος του σχήματος** για τέλεια έλεγχο διάταξης.

## Τι θα μάθετε

* Πώς να δημιουργήσετε ένα νέο έγγραφο Word με Aspose.Words for Java.  
* **Πώς να ομαδοποιήσετε σχήματα** ώστε να συμπεριφέρονται ως ένα ενιαίο αντικείμενο.  
* **Προσθήκη ορθογωνίου σχήματος** σε μια ομάδα και εισαγωγή εικόνας στην ίδια ομάδα.  
* **Ορισμός μεγέθους σχήματος** τόσο για το ορθογώνιο όσο και για την εικόνα.  
* Αποθήκευση του εγγράφου και άνοιγμα του σε Microsoft Word για επαλήθευση του αποτελέσματος.

### Προαπαιτούμενα

* Java 17 ή νεότερη εγκατεστημένη.  
* Maven ή Gradle για διαχείριση εξαρτήσεων.  
* Έγκυρη άδεια Aspose.Words for Java (ή κλειδί δωρεάν αξιολόγησης).  
* Ένα αρχείο εικόνας (`sample.png`) τοποθετημένο σε γνωστό φάκελο (αντικαταστήστε το `YOUR_DIRECTORY` με την πραγματική διαδρομή σας).

---

## Πώς να ομαδοποιήσετε σχήματα στο Word χρησιμοποιώντας Aspose.Words

Το πρώτο βήμα είναι η δημιουργία ενός `Document` και ενός `DocumentBuilder`. Ο builder παρέχει ένα βολικό API για την εισαγωγή σχημάτων, κειμένου και άλλων στοιχείων.

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Initialize the document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Γιατί είναι σημαντικό:** Το `DocumentBuilder` λειτουργεί άμεσα με το υποκείμενο αντικείμενο `Document`, επιτρέποντάς σας να εισάγετε σχήματα χωρίς να χειρίζεστε χειροκίνητα συλλογές κόμβων χαμηλού επιπέδου.

### Προσθήκη group shape

Ένα group shape είναι ένας container που μπορεί να περιέχει άλλα σχήματα. Σκεφτείτε το ως φάκελο για αντικείμενα σχεδίασης.

```java
        // Insert an empty group shape – this will hold the rectangle and the picture
        GroupShape group = builder.insertGroupShape();
```

Η μέθοδος `insertGroupShape()` δημιουργεί έναν κόμβο `GroupShape` και τον επιστρέφει ώστε να μπορείτε να προσθέσετε παιδικά σχήματα αργότερα.  

---

## Προσθήκη ορθογωνίου σχήματος στην ομάδα

Τώρα θα **προσθέσουμε ορθογώνιο σχήμα** στην προηγουμένως δημιουργημένη ομάδα. Το ορθογώνιο θα λειτουργήσει ως φόντο ή περιθώριο για την εικόνα.

```java
        // Create a rectangle shape with a specific size
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points
        rectangle.setHeight(50.0);   // height in points
        rectangle.setFillColor(java.awt.Color.LIGHT_GRAY);
        rectangle.setStrokeColor(java.awt.Color.DARK_GRAY);
        rectangle.setStrokeWeight(1.0);
        // Append the rectangle to the group
        group.appendChild(rectangle);
```

> **Συμβουλή:** Ο ορισμός των `FillColor` και `StrokeColor` κάνει το ορθογώνιο ορατό στο τελικό έγγραφο. Αν παραλείψετε αυτές τις ιδιότητες, το σχήμα μπορεί να εμφανιστεί διαφανές.

### Πώς να προσθέσετε ορθογώνιο

Ο παραπάνω κώδικας δείχνει **πώς να προσθέσετε ορθογώνιο** δημιουργώντας μια παρουσία `Shape` με `ShapeType.RECTANGLE` και στη συνέχεια προσαρτώντας την στο `GroupShape`. Αυτό το μοτίβο λειτουργεί για οποιοδήποτε άλλο τύπο σχήματος (π.χ., `ELLIPSE`, `POLYLINE`).

---

## Ορισμός μεγέθους σχήματος για το ορθογώνιο και την εικόνα

Η σωστή διάσταση εξασφαλίζει ότι το ορθογώνιο και η εικόνα ευθυγραμμίζονται σωστά. Εδώ επίσης **ορίζουμε το μέγεθος σχήματος** για την εικόνα που θα εισάγουμε στη συνέχεια.

```java
        // Insert an image and set its size
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.png");
        picture.setWidth(100.0);   // match rectangle width
        picture.setHeight(50.0);   // match rectangle height
        // Append the picture to the same group
        group.appendChild(picture);
```

Τώρα το ορθογώνιο και η εικόνα μοιράζονται τις ίδιες διαστάσεις (100 × 50 points). Επειδή ανήκουν στην ίδια ομάδα, η μετακίνηση ή η περιστροφή της ομάδας θα επηρεάσει και τα δύο σχήματα ταυτόχρονα.

> **Γιατί να ταιριάζουν τα μεγέθη;** Η ευθυγράμμιση των διαστάσεων εγγυάται ότι η εικόνα τοποθετείται κομψά μέσα στο ορθογώνιο, δημιουργώντας ένα καθαρό «πλαισιωμένο» εφέ.

---

## Αποθήκευση του εγγράφου και προβολή του αποτελέσματος

Τέλος, γράφουμε το έγγραφο στο δίσκο. Το άνοιγμα του αρχείου σε Microsoft Word εμφανίζει τα ομαδοποιημένα σχήματα ως ένα ενιαίο επιλέξιμο αντικείμενο.

```java
        // Save the document – the group will appear as one object in Word
        doc.save("YOUR_DIRECTORY/output.docx");
        System.out.println("Document saved successfully.");
    }
}
```

Όταν ανοίξετε το `output.docx`, θα δείτε ένα ορθογώνιο με την εικόνα μέσα του. Κάνοντας κλικ στο σχήμα επιλέγονται τόσο το ορθογώνιο όσο και η εικόνα επειδή είναι **ομαδοποιημένα**.

![group shapes in word example](https://example.com/images/group-shapes-word.png "group shapes in word example")

*Κείμενο alt εικόνας:* *παράδειγμα ομαδοποίησης σχημάτων στο word* – ένα έγγραφο Word που δείχνει ένα ομαδοποιημένο ορθογώνιο και εικόνα.

---

## Συχνές ερωτήσεις και διαχείριση ειδικών περιπτώσεων

| Ερώτηση | Απάντηση |
|----------|--------|
| **Τι κάνω αν χρειάζομαι διαφορετικό μέγεθος για την εικόνα;** | Ρυθμίστε `picture.setWidth()` και `picture.setHeight()` μετά την εισαγωγή. Το ορθογώνιο μπορεί να διατηρήσει το αρχικό του μέγεθος ή μπορείτε επίσης να το προσαρμόσετε ώστε να ταιριάζει. |
| **Μπορώ να προσθέσω περισσότερα σχήματα στην ίδια ομάδα;** | Ναι. Καλέστε `group.appendChild(newShape)` για οποιοδήποτε επιπλέον αντικείμενο `Shape`. |
| **Πώς περιστρέφω ολόκληρη την ομάδα;** | Χρησιμοποιήστε `group.setRotationAngle(double angleInRadians)`. Η περιστροφή εφαρμόζεται σε κάθε παιδικό σχήμα. |
| **Τι γίνεται αν λείπει το αρχείο εικόνας;** | Η `insertImage` ρίχνει `FileNotFoundException`. Περιβάλλετε την κλήση σε try‑catch και παρέχετε εναλλακτικό σχήμα placeholder. |
| **Μπορεί να γίνει αποομαδοποίηση αργότερα;** | Καλέστε `group.removeAllChildren()` για να αποσυνδέσετε τα παιδιά, έπειτα εισάγετε τα ξανά στο έγγραφο ξεχωριστά. |

---

## Συμπέρασμα

Τώρα έχετε ένα πλήρες, εκτελέσιμο παράδειγμα που δείχνει **πώς να ομαδοποιήσετε σχήματα στο Word**, **πώς να προσθέσετε ορθογώνιο σχήμα**, **πώς να ορίσετε το μέγεθος σχήματος**, και **πώς να αποθηκεύσετε** το έγγραφο χρησιμοποιώντας Aspose.Words for Java. Ομαδοποιώντας το ορθογώνιο και την εικόνα, μπορείτε να τα μετακινήσετε, να τα αλλάξετε σε μέγεθος ή να τα περιστρέψετε ως μια ενιαία μονάδα—ακριβώς αυτό που απαιτούν πολλές περιπτώσεις αυτοματοποίησης εγγράφων.

Από εδώ μπορείτε να εξερευνήσετε:

* Προσθήκη πλαισίων κειμένου στην ίδια ομάδα (`how to add rectangle`‑style text).  
* Εφαρμογή διαφορετικών μοτίβων γεμίσματος ή διαβαθμίσεων (`set shape size` σε συνδυασμό με στυλ).  
* Χρήση της ίδιας τεχνικής για ομαδοποίηση διαγραμμάτων, πινάκων ή SmartArt (`how to group shapes` σε άλλους τύπους αντικειμένων).  

Μη διστάσετε να πειραματιστείτε με άλλους τύπους σχημάτων, χρώματα και επιλογές διάταξης. Καλή προγραμματιστική!

## Τι πρέπει να μάθετε στη συνέχεια;

Οι παρακάτω οδηγίες καλύπτουν στενά σχετικά θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στην υλοποίηση των δικών σας έργων.

- [Δημιουργία Εγγράφου Word Java – Προσθήκη Σχήματος Ορθογωνίου με Εφέ Σκιάς](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Πώς να δημιουργήσετε πεδία φόρμας και να προσθέσετε περιεχόμενο χρησιμοποιώντας DocumentBuilder στο Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Πώς να Μετατρέψετε Word σε PDF Χρησιμοποιώντας Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}