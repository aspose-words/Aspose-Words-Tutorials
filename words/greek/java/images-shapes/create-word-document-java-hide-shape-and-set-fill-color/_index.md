---
category: general
date: 2026-08-07
description: 'Δημιουργία εγγράφου Word σε Java με Aspose.Words: εισαγωγή έλλειψης,
  ορισμός χρώματος γεμίσματος σχήματος και απόκρυψη σχήματος στο Word με σύντομο παράδειγμα.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document java
- how to hide shape
- how to insert shape
- hide shape in word
- set shape fill color
language: el
lastmod: 2026-08-07
og_description: Δημιουργήστε έγγραφο Word με Java χρησιμοποιώντας το Aspose.Words.
  Μάθετε πώς να εισάγετε ένα σχήμα, να ορίσετε το χρώμα γεμίσματος του και να κρύψετε
  το σχήμα στο Word—όλα σε ένα ενιαίο, εκτελέσιμο παράδειγμα.
og_image_alt: Screenshot showing a hidden ellipse shape in a Word document created
  with Java
og_title: Δημιουργία εγγράφου Word με Java – απόκρυψη σχήματος και ορισμός χρώματος
  γεμίσματος
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: 'Create word document java with Aspose.Words: insert an ellipse, set
    shape fill color, and hide shape in Word using a concise example.'
  headline: Create word document java – hide shape and set fill color
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
- Shape handling
title: Δημιουργία εγγράφου Word σε Java – απόκρυψη σχήματος και ορισμός χρώματος γεμίσματος
url: /el/java/images-shapes/create-word-document-java-hide-shape-and-set-fill-color/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία εγγράφου Word java – απόκρυψη σχήματος και ορισμός χρώματος γεμίσματος

Αν χρειάζεστε **create word document java** με προγραμματισμένη διαχείριση σχήματος, αυτό το tutorial σας δείχνει πώς. Θα μάθετε πώς να εισάγετε ένα σχήμα, να ορίσετε το χρώμα γεμίσματος και να κρύψετε το σχήμα στο Word χρησιμοποιώντας το Aspose.Words for Java.

Ο οδηγός καλύπτει κάθε βήμα, από την αρχικοποίηση ενός αντικειμένου `Document` μέχρι την επαλήθευση ότι το σχήμα είναι αόρατο όταν το αρχείο ανοίξει. Δεν απαιτούνται εξωτερικοί πόροι πέρα από τη βιβλιοθήκη Aspose.Words, και ο πλήρης πηγαίος κώδικας παρέχεται ώστε να μπορείτε να τον εκτελέσετε αμέσως.

**Prerequisites**

- Java 8 ή νεότερη έκδοση
- Maven ή Gradle για διαχείριση εξαρτήσεων (ή το Aspose.Words JAR στο classpath)
- Βασική εξοικείωση με τη σύνταξη της Java
- IDE ή κειμενογράφος για ανάπτυξη Java

Το tutorial εξηγεί επίσης **πώς να κρύψετε σχήμα** σε αρχείο Word, **πώς να εισάγετε σχήμα** με ακριβείς διαστάσεις, και **πώς να ορίσετε χρώμα γεμίσματος σχήματος** για οπτικό στυλ.

---

![Create word document java – hidden shape preview](image-placeholder.png){.align-center width=600 alt="Δημιουργία εγγράφου Word java – προεπισκόπηση κρυφού σχήματος"}

## Δημιουργία εγγράφου Word java – αρχικοποίηση εγγράφου και builder

Το πρώτο βήμα είναι η δημιουργία ενός κεντρικού εγγράφου Word και ενός `DocumentBuilder` που σας επιτρέπει να προσθέτετε περιεχόμενο. Η αρχικοποίηση αυτών των αντικειμένων διανέμει τις εσωτερικές δομές που χρειάζεται το Aspose.Words για την παρακολούθηση σελίδων, παραγράφων και σχημάτων.

```java
import com.aspose.words.*;

public class ShapeVisibilityDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty document
        Document doc = new Document();

        // DocumentBuilder provides methods to insert elements
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Γιατί είναι σημαντικό:* Χωρίς `DocumentBuilder` δεν μπορείτε να εισάγετε σχήματα, κείμενο ή άλλα αντικείμενα. Ο builder λειτουργεί πάνω στο ενσωματωμένο αντικείμενο `Document`, εξασφαλίζοντας ότι όλες οι αλλαγές καταγράφονται πριν αποθηκευτεί το αρχείο.

## Πώς να εισάγετε σχήμα με Aspose.Words

Το Aspose.Words υποστηρίζει πολλά γεωμετρικά σχήματα. Εδώ εισάγουμε μια έλλειψη με πλάτος 150 pt και ύψος 100 pt. Η μέθοδος `insertShape` επιστρέφει ένα αντικείμενο `Shape` που μπορείτε να διαμορφώσετε περαιτέρω.

```java
        // Insert an ellipse shape (width: 150pt, height: 100pt)
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 150, 100);
```

*Γιατί είναι σημαντικό:* Η χρήση του `insertShape` εγγυάται ότι το σχήμα θα αγκυρωθεί σωστά στη ροή του εγγράφου. Το επιστρεφόμενο `Shape` σας επιτρέπει να τροποποιήσετε ιδιότητες όπως το χρώμα γεμίσματος, το στυλ γραμμής και την ορατότητα.

## Ορισμός χρώματος γεμίσματος σχήματος στο Word

Ένα σχήμα χωρίς γέμισμα φαίνεται διαφανές. Ορίζοντας χρώμα γεμίσματος κάνει το σχήμα πιο εμφανές όταν είναι ορατό. Το παράδειγμα χρησιμοποιεί το `java.awt.Color.GREEN` για να δείξει **set shape fill color**.

```java
        // Apply a green fill to the ellipse
        ellipse.setFillColor(java.awt.Color.GREEN);
```

*Γιατί είναι σημαντικό:* Το χρώμα γεμίσματος αποθηκεύεται στον ορισμό XML του σχήματος. Η αλλαγή του κατά το χρόνο εκτέλεσης σας επιτρέπει να δημιουργείτε έγγραφα με χρώματα που ταιριάζουν στην εταιρική σας ταυτότητα ή να επισημαίνετε σημαντικές περιοχές.

## Πώς να κρύψετε σχήμα στο Word

Μερικές φορές χρειάζεστε ένα σχήμα που καθορίζει τη διάταξη ή λειτουργεί ως placeholder, αλλά δεν πρέπει να εμφανίζεται στον τελικό χρήστη. Η κλήση `setHidden(true)` υλοποιεί **how to hide shape** και ικανοποιεί την απαίτηση **hide shape in word**.

```java
        // Hide the shape so it will not be visible when the document is opened
        ellipse.setHidden(true);
```

*Γιατί είναι σημαντικό:* Τα κρυμμένα σχήματα παραμένουν μέρος του μοντέλου αντικειμένων του εγγράφου, πράγμα που σημαίνει ότι μπορούν να αναφερθούν αργότερα (π.χ. για σελιδοδείκτες ή προγραμματιστική διαχείριση) χωρίς να γεμίζουν την οπτική διάταξη.

## Αποθήκευση του εγγράφου και επαλήθευση αποτελεσμάτων

Αφού διαμορφώσετε το σχήμα, αποθηκεύστε το αρχείο στο δίσκο. Το αποθηκευμένο `.docx` μπορεί να ανοιχθεί στο Microsoft Word· η έλλειψη θα είναι αόρατη, αλλά η παρουσία της μπορεί να επιβεβαιωθεί εξετάζοντας το XML του εγγράφου ή χρησιμοποιώντας το Aspose.Words για την απαρίθμηση σχημάτων.

```java
        // Save the document to the desired location
        doc.save("YOUR_DIRECTORY/ShapeVisibilityDemo.docx");
    }
}
```

*Αναμενόμενο αποτέλεσμα:* Το άνοιγμα του `ShapeVisibilityDemo.docx` εμφανίζει μια κανονική σελίδα χωρίς ορατά γραφικά. Αν εξετάσετε το έγγραφο με έναν προβολέα ZIP και ανοίξετε το `word/document.xml`, θα βρείτε ένα στοιχείο `<w:shape>` με `hidden="true"` και ένα `<v:fillcolor>` με τιμή `#00FF00`.

---

## Κοινές παραλλαγές και ειδικές περιπτώσεις

- **Διαφορετικοί τύποι σχημάτων:** Αντικαταστήστε το `ShapeType.ELLIPSE` με `ShapeType.RECTANGLE`, `ShapeType.CLOUD` ή οποιαδήποτε άλλη υποστηριζόμενη τιμή enum για να πετύχετε την επιθυμητή γεωμετρία.
- **Υπό-συνθήκη ορατότητα:** Μπορείτε να εναλλάξετε το `ellipse.setHidden(false)` βάσει λογικής χρόνου εκτέλεσης, επιτρέποντας δυναμική δημιουργία εγγράφων.
- **Σύνθετα γεμίσματα:** Αντί για σταθερό χρώμα, χρησιμοποιήστε `ellipse.getFill().setTextureImage(...)` για μοτίβα. Η ίδια μέθοδος `setHidden` ελέγχει ακόμη την ορατότητα.
- **Πολλαπλά σχήματα:** Δημιουργήστε έναν πίνακα ή λίστα αντικειμένων `Shape`, διαμορφώστε το καθένα ανεξάρτητα και κρύψτε μόνο εκείνα που πληρούν συγκεκριμένα κριτήρια.

*Pro tip:* Όταν δημιουργείτε μεγάλα έγγραφα, επαναχρησιμοποιήστε ένα μόνο αντικείμενο `DocumentBuilder` αντί να δημιουργείτε νέο για κάθε σχήμα. Αυτό μειώνει την κατανάλωση μνήμης και βελτιώνει την απόδοση.

---

## Συμπέρασμα

Τώρα ξέρετε πώς να **create word document java** που εισάγει μια έλλειψη, **set shape fill color**, και **hide shape in word** χρησιμοποιώντας το Aspose.Words. Το πλήρες, εκτελέσιμο παράδειγμα δείχνει κάθε κλήση API, εξηγεί γιατί απαιτείται κάθε βήμα και παρουσιάζει το αναμενόμενο αποτέλεσμα.

Στη συνέχεια, εξερευνήστε σχετικά θέματα όπως **how to insert shape** με περιτύλιξη κειμένου, προσθήκη υπερσυνδέσμων σε σχήματα, και εξαγωγή του εγγράφου σε PDF διατηρώντας τα κρυφά στοιχεία. Πειραματιστείτε με διαφορετικά χρώματα, μεγέθη και σημαίες ορατότητας για να προσαρμόσετε την αυτοματοποίηση του Word στις ανάγκες του έργου σας.

Έτοιμοι να αυτοματοποιήσετε περισσότερες δυνατότητες του Word; Δείτε την τεκμηρίωση του Aspose.Words for Java σχετικά με [working with shapes](https://docs.aspose.com/words/java/working-with-shapes/) και αρχίστε να δημιουργείτε πιο πλούσια, προγραμματιστικά παραγόμενα έγγραφα σήμερα.

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετικές θεματικές που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε επιπλέον δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}