---
category: general
date: 2026-08-14
description: Απόκρυψη εικόνας στο Word χρησιμοποιώντας Java. Μάθετε πώς να αποκρύψετε
  εικόνα, να κρύψετε εικόνα, να ορίσετε την ιδιότητα hidden και να αποκρύψετε σχήμα
  στο Word με το Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- hide picture in word
- how to hide picture
- how to hide image
- set hidden property
- hide shape in word
language: el
lastmod: 2026-08-14
og_description: Απόκρυψη εικόνας στο Word χρησιμοποιώντας Java και Aspose.Words. Αυτό
  το σεμινάριο δείχνει πώς να ορίσετε την ιδιότητα κρυφής σε μια εικόνα, να αποκρύψετε
  σχήμα στο Word και να αποθηκεύσετε το έγγραφο σε δευτερόλεπτα.
og_image_alt: Screenshot of Java code hiding a picture in a Word document
og_title: Απόκρυψη εικόνας στο Word – οδηγός Java βήμα‑βήμα με το Aspose
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Hide picture in Word using Java. Learn how to hide picture, hide image,
    set hidden property, and hide shape in Word with Aspose.Words.
  headline: Hide picture in Word – step‑by‑step Java guide with Aspose
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Απόκρυψη εικόνας στο Word – βήμα‑βήμα οδηγός Java με το Aspose
url: /el/java/images-shapes/hide-picture-in-word-step-by-step-java-guide-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Απόκρυψη εικόνας στο Word – βήμα‑βήμα οδηγός Java με Aspose

Αν χρειάζεστε **απόκρυψη εικόνας στο Word** προγραμματιστικά, αυτός ο οδηγός παρουσιάζει τη πλήρη λύση. Θα δείτε πώς να εντοπίσετε μια εικόνα, να εφαρμόσετε τη σημαία hidden και να γράψετε το ενημερωμένο αρχείο πίσω στο δίσκο.

Η απόκρυψη ενός γραφικού είναι συχνή απαίτηση όταν δημιουργείτε αναφορές, πρότυπα ή προετοιμάζετε έγγραφα για έλεγχο συμμόρφωσης. Το παρακάτω παράδειγμα δείχνει **πώς να αποκρύψετε εικόνα** χρησιμοποιώντας το Aspose.Words for Java, αλλά οι ίδιες έννοιες ισχύουν για οποιαδήποτε βιβλιοθήκη επεξεργασίας Word που εκθέτει τη μέθοδο `setHidden` ενός σχήματος.

## Τι θα πετύχετε

Στο τέλος αυτού του tutorial θα μπορείτε:

* Να φορτώσετε ένα αρχείο `.docx` με το Aspose.Words.
* Να βρείτε το πρώτο σχήμα εικόνας στο έγγραφο.
* **Να ορίσετε την ιδιότητα hidden** σε αυτό το σχήμα ώστε να μην εμφανίζεται όταν το αρχείο ανοίξει στο Microsoft Word.
* Να αποθηκεύσετε το τροποποιημένο έγγραφο χωρίς να αλλάξετε άλλο περιεχόμενο.

Η μόνη προϋπόθεση είναι ένα περιβάλλον ανάπτυξης Java (JDK 8 ή νεότερο) και μια έγκυρη άδεια Aspose.Words for Java. Δεν απαιτούνται πρόσθετα Maven plugins εκτός από τη βασική βιβλιοθήκη.

## Απόκρυψη εικόνας στο Word με Aspose.Words

Το πρώτο βήμα είναι η δημιουργία ενός αντικειμένου `Document` που αντιπροσωπεύει το αρχείο προέλευσης. Το Aspose.Words διαβάζει ολόκληρο το πακέτο Word στη μνήμη, καθιστώντας εύκολο το πέρασμα από κόμβους όπως σχήματα, παραγράφους και πίνακες.

```java
// Step 1: Load the Word document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Η δημιουργία της παρουσίας `Document` επικυρώνει τη μορφή του αρχείου και δημιουργεί ένα εσωτερικό δέντρο κόμβων. Αυτό το δέντρο αποτελεί τη βάση για όλες τις επόμενες λειτουργίες, συμπεριλαμβανομένου του **πώς να αποκρύψετε αντικείμενα εικόνας**.

## Πώς να αποκρύψετε εικόνα χρησιμοποιώντας την ιδιότητα set hidden

Μια εικόνα σε αρχείο Word αποθηκεύεται ως κόμβος `Shape` με `ShapeType.IMAGE`. Η βιβλιοθήκη παρέχει τη μέθοδο `setHidden(boolean)` για τον έλεγχο της ορατότητας του σχήματος. Το παρακάτω τμήμα φιλτράρει τη συλλογή κόμβων ώστε να εντοπίσει το πρώτο σχήμα εικόνας.

```java
// Step 2: Locate the first picture shape in the document
Shape picture = (Shape) doc.getChildNodes(NodeType.SHAPE, true)
        .stream()
        .filter(node -> ((Shape) node).getShapeType() == ShapeType.IMAGE)
        .findFirst()
        .orElse(null);
```

Η κλήση `getChildNodes` διασχίζει ολόκληρο το δέντρο του εγγράφου (`true` ενεργοποιεί την βαθιά αναζήτηση). Η έκφραση lambda ελέγχει το `ShapeType` κάθε κόμβου. Αυτό το μοτίβο είναι η συνιστώμενη μέθοδος για **πώς να αποκρύψετε εικόνα** όταν χρειάζεστε ακριβή έλεγχο της επιλογής κόμβων.

## Πώς να αποκρύψετε εικόνα σε έγγραφο Word

Μόλις εντοπιστεί το επιθυμητό σχήμα, εφαρμόστε τη σημαία hidden. Η ρύθμιση αυτής της ιδιότητας δεν αφαιρεί την εικόνα· απλώς υποδεικνύει στο Word να θεωρήσει το σχήμα κρυφό κατά την απόδοση.

```java
// Step 3: Hide the picture if it was found
if (picture != null) {
    picture.setHidden(true);
}
```

Η κλήση `setHidden(true)` αντιστοιχεί άμεσα στο υποκείμενο χαρακτηριστικό XML `w:hidden="true"`. Το Word σέβεται αυτό το χαρακτηριστικό τόσο στον επιτραπέζιο όσο και στον διαδικτυακό επεξεργαστή, εξασφαλίζοντας ότι η εικόνα παραμένει αόρατη για όλους τους αναγνώστες.

## Απόκρυψη σχήματος στο Word – επιπλέον παρατηρήσεις

Αν και το παράδειγμα αποκρύπτει μόνο την πρώτη εικόνα, μπορείτε να επεκτείνετε τη λογική ώστε να επεξεργάζεται πολλαπλά σχήματα:

```java
// Hide all picture shapes
for (Node node : doc.getChildNodes(NodeType.SHAPE, true)) {
    Shape shape = (Shape) node;
    if (shape.getShapeType() == ShapeType.IMAGE) {
        shape.setHidden(true);
    }
}
```

* **Απόδοση** – Η διέλευση του δέντρου κόμβων είναι O(n); για πολύ μεγάλα έγγραφα, σκεφτείτε να περιορίσετε την αναζήτηση σε συγκεκριμένα τμήματα.
* **Συμβατότητα** – Η σημαία hidden λειτουργεί με Word 2007+ (`.docx`) και Word 97‑2003 (`.doc`) αρχεία.
* **Εναλλαγή ορατότητας** – Για να κάνετε ξανά ορατή μια κρυφή εικόνα, καλέστε `shape.setHidden(false)`.

Αυτές οι συμβουλές σας βοηθούν να κυριαρχήσετε σε σενάρια **απόκρυψης σχήματος στο Word** πέρα από την βασική περίπτωση χρήσης.

## Αποθήκευση του τροποποιημένου εγγράφου

Αφού ενημερώσετε τη σημαία hidden, γράψτε το έγγραφο πίσω στην αποθήκευση. Το Aspose.Words διατηρεί αυτόματα όλα τα άλλα μέρη του εγγράφου, όπως στυλ, κεφαλίδες και υποσέλιδα.

```java
// Step 4: Save the modified document
doc.save("YOUR_DIRECTORY/output.docx");
```

Η μέθοδος `save` υποστηρίζει μια ευρεία γκάμα μορφών (PDF, HTML, ODT). Σε αυτό το tutorial κρατάμε την έξοδο ως αρχείο Word για να δείξουμε άμεσα το αποτέλεσμα της απόκρυψης εικόνας.

## Πλήρες εκτελέσιμο παράδειγμα

Συνδυάζοντας όλα τα βήματα προκύπτει ένα αυτόνομο πρόγραμμα που μπορείτε να μεταγλωττίσετε και να εκτελέσετε αμέσως.

```java
import com.aspose.words.*;

public class HidePictureExample {
    public static void main(String[] args) throws Exception {
        // Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Locate the first picture shape in the document
        Shape picture = (Shape) doc.getChildNodes(NodeType.SHAPE, true)
                .stream()
                .filter(node -> ((Shape) node).getShapeType() == ShapeType.IMAGE)
                .findFirst()
                .orElse(null);

        // Hide the picture if it was found
        if (picture != null) {
            picture.setHidden(true);
        }

        // Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**Αναμενόμενο αποτέλεσμα:** Ανοίξτε το `output.docx` στο Microsoft Word. Η αρχική εικόνα δεν θα εμφανίζεται, αλλά το υπόλοιπο του εγγράφου (κείμενο, πίνακες, άλλα γραφικά) παραμένει αμετάβλητο. Αν εξετάσετε το XML (`document.xml`) θα δείτε το χαρακτηριστικό `w:hidden="true"` στο στοιχείο `<w:pict>` που αντιστοιχεί στην κρυφή εικόνα.

## Συμπέρασμα

Τώρα ξέρετε πώς να **αποκρύψετε εικόνα στο Word** χρησιμοποιώντας Java, Aspose.Words και την ιδιότητα `setHidden`. Ο οδηγός κάλυψε τον εντοπισμό σχήματος εικόνας, την εφαρμογή της σημαίας hidden και την αποθήκευση των αλλαγών. Με αυτά τα θεμέλια μπορείτε επίσης να **αποκρύψετε σχήμα στο Word**, να επεξεργαστείτε πολλαπλές εικόνες ή να εναλλάξετε την ορατότητα βάσει επιχειρηματικών κανόνων.

**Επόμενα βήματα**

* Εξερευνήστε **πώς να αποκρύψετε εικόνα** υπό όρους με βάση μεταδεδομένα (π.χ., ρόλο χρήστη).
* Συνδυάστε αυτήν την τεχνική με mail‑merge για τη δημιουργία εξατομικευμένων, ιδιωτικότητας‑συνεπών εγγράφων.
* Ανασκοπήστε την αναφορά API του Aspose.Words για προχωρημένη διαχείριση σχημάτων, όπως αλλαγή περιστροφής ή εφαρμογή υδατογραφήματος.

Μη διστάσετε να πειραματιστείτε με παραλλαγές, όπως απόκρυψη γραφημάτων ή αντικειμένων SmartArt, και να μοιραστείτε τα ευρήματά σας με την κοινότητα προγραμματιστών. Καλή κωδικοποίηση!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε πρόσθετες δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Show Hide Bookmarked Content In Word Document](/words/english/net/programming-with-bookmarks/show-hide-bookmarked-content/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}