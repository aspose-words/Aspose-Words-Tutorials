---
category: general
date: 2026-10-26
description: Μάθετε πώς να δημιουργείτε έγγραφο Word προγραμματιστικά, να προσθέτετε
  σχήμα και να κρύβετε αντικείμενο στο Word χρησιμοποιώντας το Aspose.Words for Java
  – οδηγός βήμα‑προς‑βήμα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- how to hide shape
- how to add shape
- hide object in word
language: el
lastmod: 2026-10-26
og_description: Δημιουργήστε έγγραφο Word προγραμματιστικά, μάθετε πώς να προσθέσετε
  σχήμα και να κρύψετε αντικείμενο στο Word με το Aspose.Words for Java. Πλήρες, εκτελέσιμο
  παράδειγμα.
og_image_alt: Screenshot of a Word document created programmatically with a hidden
  ellipse shape
og_title: Δημιουργία εγγράφου Word προγραμματιστικά – προσθήκη και απόκρυψη σχημάτων
  σε Java
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to create Word document programmatically, add a shape, and
    hide object in Word using Aspose.Words for Java – step‑by‑step guide.
  headline: Create Word document programmatically and add a shape in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Δημιουργία εγγράφου Word προγραμματιστικά και προσθήκη σχήματος σε Java
url: /el/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία εγγράφου Word προγραμματιστικά και προσθήκη σχήματος σε Java

Αν χρειάζεστε να **create Word document programmatically**, αυτό το tutorial σας δείχνει ακριβώς πώς να το κάνετε, να προσθέσετε ένα σχήμα και στη συνέχεια να κρύψετε το αντικείμενο στο Word. Είτε δημιουργείτε έναν γεννήτρια αναφορών είτε ένα αυτοματοποιημένο σύστημα συμβάσεων, θα λάβετε μια πλήρη, έτοιμη‑για‑εκτέλεση λύση σε λίγα μόνο λεπτά.

Θα μάθετε πώς να:

* Αρχικοποιήσετε ένα έγγραφο Word με το Aspose.Words for Java.  
* Εισάγετε μια έλλειψη (ή οποιοδήποτε άλλο σχήμα) χρησιμοποιώντας την τεχνική **how to add shape**.  
* Κρύψετε αυτό το σχήμα ώστε να μην εμφανίζεται ποτέ όταν ανοίγεται το αρχείο, απαντώντας στην ερώτηση **how to hide shape**.  

Δεν απαιτούνται εξωτερικά εργαλεία πέρα από τη βιβλιοθήκη Aspose.Words, και ο κώδικας λειτουργεί με Java 17 και νεότερες εκδόσεις.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* Java Development Kit (JDK) 17 ή νεότερο εγκατεστημένο.  
* Maven ή Gradle για διαχείριση εξαρτήσεων (το παράδειγμα χρησιμοποιεί Maven).  
* Έγκυρη άδεια Aspose.Words for Java (η δωρεάν αξιολόγηση λειτουργεί για δοκιμές).  

Αν είστε νέοι στο Aspose.Words, ανατρέξτε στον επίσημο οδηγό Getting Started, αλλά δεν χρειάζεται να τον διαβάσετε για να ακολουθήσετε αυτό το tutorial.

## Εξάρτηση Maven

Προσθέστε την ακόλουθη εξάρτηση στο `pom.xml` σας:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

> **Pro tip:** Διατηρήστε τον αριθμό έκδοσης ενημερωμένο· οι νεότερες εκδόσεις περιέχουν διορθώσεις σφαλμάτων για τη διαχείριση σχημάτων.

## Βήμα 1: Δημιουργία εγγράφου Word προγραμματιστικά – αρχικοποίηση του εγγράφου

Το πρώτο πράγμα που κάνετε όταν **create Word document programmatically** είναι να δημιουργήσετε ένα αντικείμενο `Document`. Αυτό το αντικείμενο αντιπροσωπεύει ολόκληρο το αρχείο .docx στη μνήμη.

```java
import com.aspose.words.*;

public class WordShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document
        Document doc = new Document();

        // Create a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Γιατί αυτό το βήμα είναι σημαντικό*: Η κλάση `Document` είναι το σημείο εισόδου για όλες τις λειτουργίες επεξεργασίας Word. Χωρίς αυτή δεν μπορείτε να προσθέσετε σελίδες, παραγράφους ή σχήματα.

## Βήμα 2: How to add shape – εισαγωγή έλλειψης

Τώρα αντιμετωπίζουμε το τμήμα **how to add shape** του tutorial. Το Aspose.Words υποστηρίζει πολλούς τύπους σχημάτων (Ellipse, Rectangle, TextBox, κ.λπ.). Παρακάτω εισάγουμε μια έλλειψη με πλάτος και ύψος 50 points.

```java
        // Insert an ellipse shape of size 50x50 points
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 50.0, 50.0);

        // Position the shape (optional)
        ellipse.setLeft(100);
        ellipse.setTop(100);
```

Η μέθοδος `insertShape` επιστρέφει ένα αντικείμενο `Shape` που μπορείτε να προσαρμόσετε περαιτέρω — χρώμα, στυλ γραμμής, περιστροφή και άλλα. Οι συντεταγμένες μετρώνται σε points (1/72 ίντσα).

*Γιατί μπορεί να θέλετε να προσθέσετε ένα σχήμα*: Τα σχήματα είναι χρήσιμα για υδατογραφήματα, διακοσμητικά στοιχεία ή placeholders που αργότερα κρύβετε ή αντικαθιστάτε.

## Βήμα 3: How to hide shape – καθιστώντας το αντικείμενο αόρατο στο Word

Για να απαντήσετε στην ερώτηση **how to hide shape**, απλώς ορίστε την ιδιότητα `Hidden` του σχήματος σε `true`. Αυτό λέει στο Word να θεωρήσει το σχήμα ως κρυφό αντικείμενο, ώστε να μην εμφανίζεται ποτέ στην προβολή ή την εκτύπωση του εγγράφου.

```java
        // Hide the shape so it does not appear in the rendered document
        ellipse.setHidden(true);
```

Αν χρειάζεται να **hide object in Word** για συγκεκριμένο χρήστη ή κατάσταση, μπορείτε να εναλλάξετε αυτή την ιδιότητα κατά την εκτέλεση βάσει της επιχειρηματικής λογικής σας.

> **Note:** Τα κρυφά σχήματα εξακολουθούν να αποτελούν μέρος της δομής XML του εγγράφου. Μπορούν να αποκαλυφθούν αργότερα ορίζοντας `setHidden(false)`.

## Βήμα 4: Αποθήκευση του εγγράφου

Αφού προσθέσετε και κρύψετε το σχήμα, γράψτε το έγγραφο στο δίσκο.

```java
        // Save the document as a .docx file
        doc.save("HiddenShapeDemo.docx");
        System.out.println("Document created successfully.");
    }
}
```

Όταν ανοίξετε το `HiddenShapeDemo.docx` στο Microsoft Word, θα δείτε μια κενή σελίδα επειδή η έλλειψη είναι κρυφή. Το έγγραφο συμπεριφέρεται διαφορετικά όπως οποιοδήποτε κανονικό αρχείο Word.

## Πλήρες λειτουργικό παράδειγμα

Συνδυάζοντας όλα τα κομμάτια, εδώ είναι το πλήρες, εκτελέσιμο πρόγραμμα:

```java
import com.aspose.words.*;

public class WordShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a document programmatically
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: How to add shape – insert an ellipse (50x50 points)
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 50.0, 50.0);
        ellipse.setLeft(100);
        ellipse.setTop(100);

        // Step 3: How to hide shape – hide the ellipse so it never appears
        ellipse.setHidden(true);

        // Step 4: Save the file
        doc.save("HiddenShapeDemo.docx");
        System.out.println("Document created successfully.");
    }
}
```

**Αναμενόμενο αποτέλεσμα**

```
Document created successfully.
```

Ανοίγοντας το `HiddenShapeDemo.docx` εμφανίζεται μια κενή σελίδα· η κρυφή έλλειψη δεν αποδίδεται, επιβεβαιώνοντας ότι η λειτουργία **hide object in Word** πέτυχε.

## Περιπτώσεις άκρων και παραλλαγές

| Κατάσταση | Τι να αλλάξετε | Γιατί |
|-----------|----------------|-------|
| Απόκρυψη ενός ορθογωνίου αντί για έλλειψη | Χρησιμοποιήστε `ShapeType.RECTANGLE` στο `insertShape` | Διαφορετικό οπτικό placeholder |
| Απόκρυψη πολλαπλών σχημάτων ταυτόχρονα | Κάντε βρόχο μέσω `doc.getChildNodes(NodeType.SHAPE, true)` και ορίστε `setHidden(true)` | Χρήσιμο για μαζική επεξεργασία |
| Εμφάνιση του σχήματος μόνο στην προβολή εκτύπωσης | Ορίστε `shape.setVisible(false)` και `shape.setPrint(true)` | Το Word διακρίνει μεταξύ ορατότητας στην οθόνη και στην εκτύπωση |
| Χρήση διαφορετικής μονάδας μέτρησης | Καλέστε `builder.getDocument().getCompatibilityOptions().setMeasureUnit(MeasureUnit.INCHES)` | Συμφωνεί με τις απαιτήσεις διάταξης σας |

## Συνηθισμένα προβλήματα

* **Ξεχάνοντας να καλέσετε `setHidden(true)`** – το σχήμα θα εμφανιστεί κανονικά.  
* **Αποθήκευση του εγγράφου πριν κρύψετε το σχήμα** – η σειρά είναι σημαντική· κρύψτε πρώτα, μετά αποθηκεύστε.  
* **Χρήση παλιάς έκδοσης Aspose.Words** – οι παλαιότερες εκδόσεις μπορεί να μην έχουν το API `setHidden`.  

Πάντα δοκιμάζετε το παραγόμενο αρχείο στην έκδοση του Microsoft Word-στόχο για να βεβαιωθείτε ότι η κρυφή κατάσταση λειτουργεί όπως αναμένεται.

## Συμπέρασμα

Σε αυτόν τον οδηγό μάθατε πώς να **create Word document programmatically**, **add shape**, και **hide object in Word** χρησιμοποιώντας το Aspose.Words for Java. Το πλήρες παράδειγμα δείχνει τα ακριβή βήματα, από την αρχικοποίηση του εγγράφου μέχρι την αποθήκευση ενός αρχείου όπου το σχήμα δεν εμφανίζεται ποτέ.

Από εδώ μπορείτε να:

* Πειραματιστείτε με άλλους τύπους σχημάτων (`ShapeType.LINE`, `ShapeType.TEXT_BOX`).  
* Συνδυάστε κρυφά σχήματα με σελιδοδείκτες για δημιουργία δυναμικών προτύπων.  
* Εξερευνήστε τις ιδιότητες `setVisible` και `setPrint` για πιο λεπτομερή έλεγχο της ορατότητας του αντικειμένου.

Καλή προγραμματιστική δουλειά και απολαύστε την αυτοματοποίηση των εγγράφων Word σας!

## Τι Πρέπει Να Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να δημιουργήσετε κενό έγγραφο Word με Aspose.Words for Java](/words/english/java/document-manipulation/how-to-create-blank-word-document-with-aspose-words-for-java/)
- [Πώς να κρύψετε σχήμα σε έγγραφο Word χρησιμοποιώντας Java](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Δημιουργία Εγγράφου Word Java – Προσθήκη Σχήματος Ορθογωνίου με Εφέ Σκιάς](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}