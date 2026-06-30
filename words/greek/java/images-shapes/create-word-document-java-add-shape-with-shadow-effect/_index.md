---
category: general
date: 2026-06-30
description: Δημιουργήστε παράδειγμα Java για έγγραφο Word που δείχνει πώς να προσθέσετε
  σχήμα σε έγγραφο Word, να ορίσετε το χρώμα γεμίσματος του σχήματος και να εφαρμόσετε
  σκιά στο σχήμα σε λίγες μόνο γραμμές.
draft: false
keywords:
- create word document java
- how to add shadow to shape
- add shape to word document
- set shape fill color
- apply shadow effect shape
language: el
og_description: Δημιουργήστε ένα σεμινάριο Java για έγγραφο Word που δείχνει πώς να
  προσθέσετε σχήμα σε έγγραφο Word, να ορίσετε το χρώμα γεμίσματος του σχήματος και
  να εφαρμόσετε σκιά στο σχήμα.
og_title: Δημιουργία εγγράφου Word με Java – Προσθήκη σχήματος με εφέ σκιάς
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Create word document java example that shows how to add shape to word
    document, set shape fill color, and apply shadow effect shape in just a few lines.
  headline: Create Word Document Java – Add Shape with Shadow Effect
  type: TechArticle
- description: Create word document java example that shows how to add shape to word
    document, set shape fill color, and apply shadow effect shape in just a few lines.
  name: Create Word Document Java – Add Shape with Shadow Effect
  steps:
  - name: Creates the shape object.
    text: Creates the shape object.
  - name: Positions it at the current cursor location (top‑left of the page by default).
    text: Positions it at the current cursor location (top‑left of the page by default).
  - name: Adds it to the document’s internal node collection.
    text: Adds it to the document’s internal node collection.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word Automation
- Shapes
title: Δημιουργία εγγράφου Word με Java – Προσθήκη σχήματος με εφέ σκιάς
url: /el/java/images-shapes/create-word-document-java-add-shape-with-shadow-effect/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία Εγγράφου Word Java – Προσθήκη Σχήματος με Εφέ Σκιάς

Έχετε ποτέ χρειαστεί κώδικα **create word document java** που σχεδιάζει ένα ορθογώνιο και του προσθέτει μια ήπια σκιά; Δεν είστε μόνοι. Είτε δημιουργείτε αναφορές, τιμολόγια ή ένα απλό φυλλάδιο, η δυνατότητα **add shape to word document** προγραμματιστικά εξοικονομεί ώρες χειροκίνητης προσαρμογής.  

Σε αυτόν τον οδηγό θα περάσουμε βήμα προς βήμα ένα πλήρες, έτοιμο‑για‑εκτέλεση παράδειγμα που όχι μόνο δημιουργεί ένα νέο αρχείο Word, αλλά επίσης **set shape fill color**, **how to add shadow to shape**, και τέλος **apply shadow effect shape** με το Aspose.Words for Java. Χωρίς περιττά—μόνο τα ακριβή βήματα που μπορείτε να αντιγράψετε‑και‑επικολλήσετε στο IDE σας.

> **Pro tip:** Αν είστε νέοι στο Aspose.Words, βεβαιωθείτε ότι έχετε το τελευταίο JAR στο classpath σας. Το API που χρησιμοποιούμε λειτουργεί με την έκδοση 23.10 και νεότερες.

## Τι Θα Δημιουργήσετε

Στο τέλος αυτού του tutorial θα έχετε ένα αρχείο `.docx` που περιέχει:

* Ένα κενό έγγραφο Word που δημιουργείται από το μηδέν.
* Ένα κίτρινο ορθογώνιο (150 × 80 pts) που εισάγεται στην πρώτη σελίδα.
* Μια ήπια γκρι σκιά μετατοπισμένη με μερικά σημεία, δίνοντας στο σχήμα μια ανυψωμένη εμφάνιση.
* Όλα τα παραπάνω επιτυγχάνονται με μόνο λίγες δηλώσεις Java.

Χωρίς εξωτερικά πρότυπα, χωρίς πολύπλοκο XML—καθαρός κώδικας Java που μπορεί να τρέξει οποιοσδήποτε.

## Δημιουργία Εγγράφου Word Java – Εισαγωγή Σχήματος

Το πρώτο που χρειαζόμαστε είναι ένα νέο αντικείμενο `Document` και ένα `DocumentBuilder`. Σκεφτείτε το builder ως ένα στυλό που μας επιτρέπει να σχεδιάζουμε μέσα στο έγγραφο.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to add content.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Γιατί είναι σημαντικό:* Το `Document` αντιπροσωπεύει ολόκληρο το αρχείο, ενώ το `DocumentBuilder` μας παρέχει βολικές μεθόδους όπως `insertShape`. Χωρίς το builder θα έπρεπε να χειριζόμαστε κόμβους χαμηλού επιπέδου απευθείας—πολύ περισσότερη δουλειά.

## Προσθήκη Σχήματος σε Έγγραφο Word – Προσθήκη του Ορθογωνίου

Τώρα στην πραγματικότητα **add shape to word document**. Στην περίπτωσή μας είναι ένα ορθογώνιο, αλλά μπορείτε να επιλέξετε οποιοδήποτε `ShapeType` υποστηρίζει το Aspose (έλλειψη, βέλος κ.λπ.).

```java
        // Step 2: Insert a rectangle shape of size 150x80 points.
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
```

Αυτή η μοναδική γραμμή κάνει τρία πράγματα:

1. Δημιουργεί το αντικείμενο σχήματος.
2. Το τοποθετεί στην τρέχουσα θέση του κέρσορα (πάνω‑αριστερά της σελίδας εξ ορισμού).
3. Το προσθέτει στη συλλογή εσωτερικών κόμβων του εγγράφου.

Αν ποτέ αναρωτηθήκατε *how to add shadow to shape* μετά από αυτό, συνεχίστε την ανάγνωση—επειδή θα το καλύψουμε στο επόμενο βήμα.

## Ορισμός Χρώματος Γέμισης Σχήματος – Προσαρμογή Εμφάνισης

Ένα απλό λευκό ορθογώνιο δεν είναι πολύ εντυπωσιακό, οπότε ας **set shape fill color** σε κάτι φωτεινό. Θα χρησιμοποιήσουμε την κλάση `java.awt.Color` της Java, την οποία το Aspose δέχεται άμεσα.

```java
        // Step 3: Set the shape's fill color to yellow.
        rectangle.setFillColor(java.awt.Color.YELLOW);
```

Μπορείτε ελεύθερα να αντικαταστήσετε το `YELLOW` με `RED`, `GREEN`, ή οποιαδήποτε προσαρμοσμένη τιμή RGB (`new Color(123, 45, 67)`). Το χρώμα γέμισης είναι η επιφάνεια που θα δείτε πριν η σκιά αρχίσει να εμφανίζεται.

## Πώς να Προσθέσετε Σκιά σε Σχήμα – Διαμόρφωση της Σκιάς

Εδώ συμβαίνει η μαγεία. Το Aspose.Words εκθέτει ένα αντικείμενο `ShadowEffect` που μας επιτρέπει να ρυθμίσουμε λεπτομερώς την εμφάνιση της σκιάς.

```java
        // Step 4: Configure a custom shadow effect for the shape.
        ShadowEffect shadow = rectangle.getShadowEffect();
        shadow.setColor(java.awt.Color.GRAY);      // Shadow color
        shadow.setBlurRadius(5.0);                 // Softness of the shadow
        shadow.setOffsetX(4.0);                    // Horizontal offset
        shadow.setOffsetY(4.0);                    // Vertical offset
        shadow.setTransparency(0.3);               // Shadow opacity (0 = opaque, 1 = fully transparent)
```

**Γιατί κάθε ιδιότητα είναι σημαντική:**

| Ιδιότητα | Τι κάνει | Τυπικές τιμές |
|----------|----------|----------------|
| `setColor` | Καθορίζει την απόχρωση της σκιάς. Το γκρι λειτουργεί στις περισσότερες περιπτώσεις, αλλά μπορείτε να το κάνετε έντονο με `Color.BLUE`. | Any `java.awt.Color` |
| `setBlurRadius` | Ελέγχει πόσο μαλακές εμφανίζονται οι άκρες. Μεγαλύτεροι αριθμοί δίνουν πιο διάχυτη εμφάνιση. | 0 – 10 (float) |
| `setOffsetX` / `setOffsetY` | Μετακινεί τη σκιά δεξιά/αριστερά και πάνω/κάτω. Θετικές τιμές ωθούν τη σκιά προς τα κάτω‑και‑δεξιά. | -10 – 10 |
| `setTransparency` | Ορίζει την αδιαφάνεια· 0 είναι αδιαπέραστη, 1 είναι αόρατη. | 0.0 – 1.0 |

Αν αναρωτιέστε **how to add shadow to shape** χωρίς να χαλάσετε τη διάταξη, το κλειδί είναι να κρατήσετε τις μετατοπίσεις μέτριες. Πολύ μεγάλες και η σκιά μπορεί να εκχυλίσει στην επόμενη σελίδα.

## Εφαρμογή Σκιάς στο Σχήμα – Αποθήκευση του Εγγράφου

Με το σχήμα μορφοποιημένο και τη σκιά ρυθμισμένη, χρειάζεται μόνο να αποθηκεύσουμε το αρχείο.

```java
        // Step 5: Save the document with the shaped shadow.
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

Αντικαταστήστε το `YOUR_DIRECTORY` με μια απόλυτη ή σχετική διαδρομή που υπάρχει στον υπολογιστή σας. Μετά την εκτέλεση του προγράμματος, ανοίξτε το `ShadowShape.docx` στο Microsoft Word ή στο LibreOffice—θα πρέπει να δείτε ένα κίτρινο ορθογώνιο να αιωρείται πάνω από τη σελίδα, χάρη στη γκρι σκιά που εφαρμόσαμε.

## Επαλήθευση του Αποτελέσματος – Τι να Παρατηρήσετε

Όταν ανοίξετε το παραγόμενο αρχείο:

* Το ορθογώνιο πρέπει να είναι κεντραρισμένο στο σημείο όπου ξεκίνησε ο κέρσορας (πάνω‑αριστερά της σελίδας εξ ορισμού).
* Η γέμιση του είναι φωτεινό κίτρινο.
* Μια ήπια γκρι θολή εμφανίζεται 4 pts δεξιά και κάτω, με περίπου 30 % διαφάνεια.

Αν η σκιά φαίνεται πολύ έντονη, μειώστε το `BlurRadius` ή αυξήστε το `Transparency`. Αν το σχήμα δεν είναι ορατό, ελέγξτε ξανά την κλήση `setFillColor`—ίσως το χρώμα που επιλέξατε να ενσωματώνεται με το φόντο της σελίδας.

## Συνηθισμένα Προβλήματα & Ακραίες Περιπτώσεις

| Πρόβλημα | Αιτία | Διόρθωση |
|----------|-------|----------|
| **Η σκιά εξαφανίζεται** | `Transparency` ορίστηκε σε `1.0` (πλήρως διαφανές). | Χρησιμοποιήστε χαμηλότερη τιμή, π.χ., `0.3`. |
| **Το σχήμα δεν είναι ορατό** | Το χρώμα γέμισης ταιριάζει με το φόντο της σελίδας (συχνά λευκό). | Επιλέξτε ένα αντίθετο χρώμα με `setFillColor`. |
| **Η σκιά κόβεται στο περιθώριο της σελίδας** | Οι μετατοπίσεις ωθούν τη σκιά εκτός της εκτυπώσιμης περιοχής. | Μειώστε τα `OffsetX`/`OffsetY` ή αυξήστε τα περιθώρια της σελίδας μέσω `PageSetup`. |
| **Σφάλμα μεταγλώττισης: `cannot find symbol ShadowEffect`** | Χρήση παλαιότερης έκδοσης Aspose.Words που δεν υποστηρίζει σκιά. | Αναβαθμίστε σε Aspose.Words 23.10+ (το API εισήγαγε το `ShadowEffect` στην έκδοση 22.12). |

## Επόμενα Βήματα – Πέρα από τα Βασικά

Τώρα που ξέρετε πώς να **create word document java**, **add shape to word document**, **set shape fill color**, **how to add shadow to shape**, και **apply shadow effect shape**, μπορεί να αναρωτιέστε τι άλλο μπορείτε να κάνετε. Εδώ είναι μερικές ιδέες:

* **Δυναμικά χρώματα** – Ανάκτηση τιμών RGB από βάση δεδομένων για χρωματική κωδικοποίηση σχημάτων βάσει κατάστασης.
* **Πολλαπλές σκιές** – Στοίβαξη δύο ρυθμίσεων `ShadowEffect` κλωνοποιώντας το σχήμα και μετατοπίζοντας κάθε αντίγραφο.
* **Κείμενο μέσα σε σχήματα** – Χρησιμοποιήστε το `Shape.getTextFrame()` για να ενσωματώσετε μια λεζάντα ή ετικέτα.
* **Εξαγωγή σε PDF** – Κλήση του `document.save("output.pdf", SaveFormat.PDF)` για να λάβετε μια εκτυπώσιμη έκδοση με την ίδια οπτική πιστότητα.

Κάθε ένα από αυτά βασίζεται στο ίδιο βασικό μοτίβο που δείξαμε: δημιουργήστε ένα έγγραφο, εισάγετε ένα σχήμα, μορφοποιήστε το και αποθηκεύστε το.

## Πλήρες Παράδειγμα Εργασίας (Έτοιμο για Αντιγραφή‑Επικόλληση)

```java
import com.aspose.words.*;
import java.awt.Color;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document and a builder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape (150 × 80 pts).
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 150, 80);

        // 3️⃣ Set the shape's fill color to yellow.
        rectangle.setFillColor(Color.YELLOW);

        // 4️⃣ Configure the shadow effect.
        ShadowEffect shadow = rectangle.getShadowEffect();
        shadow.setColor(Color.GRAY);        // Shadow color
        shadow.setBlurRadius(5.0);          // Softness
        shadow.setOffsetX(4.0);             // Horizontal offset
        shadow.setOffsetY(4.0);             // Vertical offset
        shadow.setTransparency(0.3);        // 30 % transparent

        // 5️⃣ Save the document.
        document.save("ShadowShape.docx");
    }
}
```

Η εκτέλεση της κλάσης παράγει το `ShadowShape.docx` στον τρέχοντα φάκελο εργασίας. Ανοίξτε το και θα δείτε το ακριβές αποτέλεσμα που περιγράφηκε νωρίτερα.

## Συμπέρασμα

Σας δείξαμε πώς να **create word document java** από το μηδέν, **add shape to word document**, **set shape fill color**, **how to add shadow to shape**, και τέλος **apply shadow effect shape**—όλα με ένα σύντομο, εύκολο‑κατανοητό παράδειγμα κώδικα.

Η προσέγγιση είναι σκόπιμα απλή ώστε να την προσαρμόσετε σε πιο σύνθετα σενάρια—είτε χρειάζεστε πολλαπλά σχήματα, διαφορετικά χρώματα ή σκιές στυλ animation. Θυμηθείτε να παρακολουθείτε τη συμβατότητα της έκδοσης του API, και μην διστάζετε να ρυθμίσετε τις παραμέτρους της σκιάς ώστε να ταιριάζουν στη γλώσσα σχεδίασής σας.

Δοκιμάσατε κάποια παραλλαγή; Ίσως τοποθετήσατε μια εικόνα πίσω από το ορθογώνιο ή προσθέσατε έναν πίνακα μέσα στο σχήμα. Αφήστε ένα σχόλιο παρακάτω· μου αρέσει να ακούω πώς οι προγραμματιστές προωθούν αυτά τα παραδείγματα. Καλή προγραμματιστική!

## Τι Θα Μάθετε Στη Σύντομη Μελλοντική Περίοδο;

Τα παρακάτω tutorials καλύπτουν στενά σχετικούς θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Δημιουργία Εγγράφου Word Java – Προσθήκη Σχήματος Ορθογωνίου με Εφέ Σκιάς](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Πώς να Δημιουργήσετε PDF Έγγραφα με Aspose.Words for Java | Document Processing API](/words/english/java/)
- [Aspose.Words Java: Πλήρης Οδηγός για Επεξεργασία Εγγράφων Word](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}