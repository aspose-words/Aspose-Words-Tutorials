---
category: general
date: 2026-06-08
description: Αποθηκεύστε το έγγραφο ως DOCX χρησιμοποιώντας το Aspose.Words σε Java.
  Μάθετε πώς να προσθέτετε σκιά σε σχήμα, να ορίζετε το χρώμα γεμίσματος του σχήματος
  και να ελέγχετε τη διαφάνεια του σχήματος βήμα‑βήμα.
draft: false
keywords:
- save document as docx
- add shadow to shape
- how to set shape transparency
- how to insert rectangle shape
- set shape fill color
language: el
og_description: Αποθηκεύστε το έγγραφο ως DOCX χρησιμοποιώντας το Aspose.Words σε
  Java. Αυτός ο οδηγός δείχνει πώς να προσθέσετε σκιά σε σχήμα, να ορίσετε το χρώμα
  γεμίσματος του σχήματος και να ρυθμίσετε τη διαφάνεια του σχήματος.
og_title: Αποθήκευση εγγράφου ως DOCX με το Aspose.Words – Εγχειρίδιο Java
schemas:
- author: Aspose
  dateModified: '2026-06-08'
  description: Save document as DOCX using Aspose.Words in Java. Learn to add shadow
    to shape, set shape fill color, and control shape transparency step‑by‑step.
  headline: Save Document as DOCX with Aspose.Words – Complete Java Guide
  type: TechArticle
- description: Save document as DOCX using Aspose.Words in Java. Learn to add shadow
    to shape, set shape fill color, and control shape transparency step‑by‑step.
  name: Save Document as DOCX with Aspose.Words – Complete Java Guide
  steps:
  - name: Expected Result
    text: 'Open `ShadowShape.docx` in Microsoft Word or LibreOffice:'
  - name: What if the shadow isn’t visible?
    text: Shadows are rendered only if the shape isn’t clipped by page margins. Ensure
      there’s enough white space around the shape, or increase the page size via `document.getFirstSection().getPageSetup().setPaperSize(PaperSize.A4)`
      before inserting the shape.
  - name: Can I add multiple shapes?
    text: Absolutely. Just call `builder.insertShape` again after the first shape,
      or move the cursor with `builder.moveTo` to position subsequent shapes. Each
      shape gets its own `ShadowFormat` and fill settings.
  - name: How to make the rectangle transparent instead of the shadow?
    text: Use `rectangleShape.setTransparency(0.5)` (or `setFillColor` with an alpha
      channel). The `setTransparency` method on the shape itself controls the fill’s
      opacity, whereas the one on `ShadowFormat` affects the shadow.
  - name: Does this work with older Word versions?
    text: Yes. Aspose.Words writes `.docx` files that are compatible with Word 2007
      and later. If you need legacy `.doc` support, change the file extension to `.doc`
      and Aspose will automatically downgrade the format.
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Generation
title: Αποθήκευση εγγράφου ως DOCX με το Aspose.Words – Πλήρης οδηγός Java
url: /el/java/document-conversion-and-export/save-document-as-docx-with-aspose-words-complete-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Αποθήκευση Εγγράφου ως DOCX με Aspose.Words – Πλήρης Οδηγός Java

Έχετε ποτέ αναρωτηθεί πώς να **save document as docx** ενώ προσθέτετε μια μικρή οπτική πινελιά στα σχήματά σας; Δεν είστε μόνοι. Πολλοί προγραμματιστές συναντούν δυσκολίες όταν χρειάζονται έναν γρήγορο τρόπο για να δημιουργήσουν ένα αρχείο Word με ένα ορθογώνιο που έχει προσαρμοσμένο χρώμα γεμίσματος και μια διακριτική σκιά. Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα ακριβώς από αυτό—πώς να εισάγουμε ένα σχήμα ορθογωνίου, να ορίσουμε το χρώμα γεμίσματος, να ρυθμίσουμε τη διαφάνεια και, τέλος, να **save document as docx** με μία μόνο γραμμή κώδικα.

Θα απαντήσουμε επίσης στις επίμονες ερωτήσεις «πώς να προσθέσετε σκιά σε σχήμα», «πώς να ορίσετε τη διαφάνεια του σχήματος» και «πώς να εισάγετε σχήμα ορθογωνίου» χωρίς να τσακώσετε τα μαλλιά σας. Στο τέλος θα έχετε ένα έτοιμο‑για‑εκτέλεση πρόγραμμα Java που παράγει ένα επεξεργασμένο αρχείο `.docx`, ιδανικό για αναφορές, τιμολόγια ή οποιοδήποτε έγγραφο που χρειάζεται μια δόση σχεδίασης.

## Τι Θα Μάθετε

- Τα ακριβή βήματα για **save document as docx** χρησιμοποιώντας το Aspose.Words for Java.  
- Πώς να **add shadow to shape** και να ελέγξετε την απόσταση, το θόλωμα και το χρώμα.  
- Τη σύνταξη για **how to set shape transparency** ώστε η σκιά να φαίνεται ακριβώς σωστή.  
- Τη μέθοδο για **how to insert rectangle shape** και να του δώσετε φόντο με **set shape fill color**.  
- Συμβουλές, παγίδες και προτάσεις βέλτιστων πρακτικών για εργασία με σχήματα σε έγγραφα Word.

> **Prerequisites:** Java 8+ εγκατεστημένο, Maven ή Gradle για λήψη του Aspose.Words, και βασική κατανόηση της σύνταξης Java. Δεν απαιτείται προγενέστερη εμπειρία με το Aspose—απλώς ακολουθήστε τα βήματα.

---

## Βήμα 1: Ρύθμιση Aspose.Words στο Έργο Java

Πριν μπορέσουμε να **save document as docx**, χρειάζεται η βιβλιοθήκη Aspose.Words στο classpath. Αν χρησιμοποιείτε Maven, προσθέστε την παρακάτω εξάρτηση στο `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- Use the latest stable version -->
</dependency>
```

Για Gradle, τοποθετήστε αυτό στο `build.gradle`:

```groovy
implementation 'com.aspose:aspose-words:23.12'
```

Μόλις η βιβλιοθήκη λυθεί, είστε έτοιμοι να γράψετε κώδικα που θα **save document as docx**.

## Βήμα 2: Δημιουργία Νέου Κενού Εγγράφου και DocumentBuilder

Η κλάση `Document` αντιπροσωπεύει ολόκληρο το αρχείο Word, ενώ το `DocumentBuilder` είναι το πινέλο σας. Σκεφτείτε το builder ως έναν κέρσορα που σας επιτρέπει να εισάγετε κείμενο, πίνακες ή σχήματα όπου χρειάζεται.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Create a fresh, empty document
        Document document = new Document();

        // DocumentBuilder lets us add content to the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

Σε αυτό το σημείο το έγγραφο είναι κενό, αλλά έχουμε ήδη τα εργαλεία για να **save document as docx** αργότερα.

## Βήμα 3: Πώς να Εισάγετε Σχήμα Ορθογωνίου

Τώρα έρχεται το διασκεδαστικό μέρος—η προσθήκη ενός ορθογωνίου. Η μέθοδος `insertShape` δέχεται ένα enum `ShapeType`, πλάτος και ύψος (σε points). Αν δεν ξέρετε τις μονάδες, 72 points ισοδυναμούν με ένα ίντσα, οπότε 200 × 100 points δίνουν περίπου ένα ορθογώνιο 2.78 × 1.39 ίντσες.

```java
        // Insert a rectangle shape of 200x100 points
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 200, 100);
```

Αυτή η εντολή κάνει τρία πράγματα:

1. Δημιουργεί ένα αντικείμενο σχήματος.  
2. Το τοποθετεί στην τρέχουσα θέση του κέρσορα.  
3. Επιστρέφει μια αναφορά (`rectangleShape`) ώστε να μπορούμε να ρυθμίσουμε την εμφάνισή του.

## Βήμα 4: Ορισμός Χρώματος Γεμίσματος Σχήματος

Ένα απλό γκρι κουτί δεν είναι πολύ εντυπωσιακό, σωστά; Ας του δώσουμε ένα **set shape fill color** που ταιριάζει στην παλέτα της μάρκας μας. Το Aspose χρησιμοποιεί `java.awt.Color` για τις τιμές χρώματος, οπότε διαλέξτε οποιαδήποτε σταθερά ή δημιουργήστε μια προσαρμοσμένη τιμή RGB.

```java
        // Apply a light gray fill color to the rectangle
        rectangleShape.setFillColor(java.awt.Color.LIGHT_GRAY);
```

Μπορείτε να αντικαταστήσετε το `LIGHT_GRAY` με `Color.BLUE`, `new Color(255, 215, 0)` (χρυσό) ή οποιοδήποτε χρώμα προτιμάτε. Το σημαντικό είναι ότι το σχήμα τώρα έχει φόντο, το οποίο θα είναι ορατό όταν **save document as docx**.

## Βήμα 5: Προσθήκη Σκιάς στο Σχήμα

Οι σκιές δίνουν βάθος. Το Aspose εκθέτει ένα αντικείμενο `ShadowFormat` όπου μπορείτε να ελέγξετε την απόσταση, την ακτίνα θολώματος, τη διαφάνεια και το χρώμα. Ας δούμε κάθε ιδιότητα.

```java
        // Configure shadow offset (horizontal & vertical) in points
        rectangleShape.getShadowFormat().setOffsetX(5);
        rectangleShape.getShadowFormat().setOffsetY(5);

        // Set the blur radius – higher values make the shadow softer
        rectangleShape.getShadowFormat().setBlurRadius(4);

        // **How to set shape transparency** – 0.0 = fully opaque, 1.0 = fully transparent
        rectangleShape.getShadowFormat().setTransparency(0.3); // 30% transparent

        // Choose a dark gray color for the shadow itself
        rectangleShape.getShadowFormat().setColor(java.awt.Color.DARK_GRAY);
```

Παρατηρήστε το σχόλιο που λειτουργεί και ως γρήγορη απάντηση στο *how to set shape transparency*. Η μέθοδος `setTransparency` δέχεται ένα double μεταξύ 0 και 1, καθιστώντας εύκολο το λεπτομερές fine‑tuning.

> **Pro tip:** Αν θέλετε πιο δραματικό αποτέλεσμα, αυξήστε το `OffsetX/Y` σε 10 και το `BlurRadius` σε 8. Θυμηθείτε ότι μεγάλες αποστάσεις μπορεί να ωθήσουν τη σκιά εκτός των περιθωρίων της σελίδας, κάτι που μπορεί να περικοπεί κατά την εκτύπωση.

## Βήμα 6: Αποθήκευση Εγγράφου ως DOCX

Όλη η οπτική δουλειά ολοκληρώθηκε· τώρα απλώς **save document as docx**. Το Aspose σας επιτρέπει να καθορίσετε τη μορφή μέσω της επέκτασης του αρχείου, οπότε η παράδοση του `"ShadowShape.docx"` αρκεί.

```java
        // Persist the document to a .docx file
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

Αντικαταστήστε το `YOUR_DIRECTORY` με μια απόλυτη ή σχετική διαδρομή στην οποία η διαδικασία Java μπορεί να γράψει. Όταν εκτελέσετε το πρόγραμμα, ένα αρχείο Word θα εμφανιστεί στην τοποθεσία αυτή, περιέχοντας ένα ορθογώνιο με γκρι γέμισμα και μια διακριτική σκούρα σκιά.

### Αναμενόμενο Αποτέλεσμα

Ανοίξτε το `ShadowShape.docx` στο Microsoft Word ή στο LibreOffice:

- Μία σελίδα με κεντραρισμένο ορθογώνιο.  
- Το εσωτερικό του ορθογωνίου είναι ανοιχτό γκρι.  
- Μια ήπια, ελαφρώς διαφανής σκούρα σκιά εμφανίζεται 5 pts δεξιά και κάτω, δίνοντας στο σχήμα μια «ανυψωμένη» εμφάνιση.

Αν δείτε αυτά τα στοιχεία, συγχαρητήρια—έχετε ολοκληρώσει επιτυχώς το **save document as docx** με στυλιζαρισμένο σχήμα!

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

### Τι γίνεται αν η σκιά δεν είναι ορατή;

Οι σκιές αποδίδονται μόνο αν το σχήμα δεν είναι κομμένο από τα περιθώρια της σελίδας. Βεβαιωθείτε ότι υπάρχει αρκετός λευκός χώρος γύρω από το σχήμα ή αυξήστε το μέγεθος της σελίδας μέσω `document.getFirstSection().getPageSetup().setPaperSize(PaperSize.A4)` πριν την εισαγωγή του σχήματος.

### Μπορώ να προσθέσω πολλαπλά σχήματα;

Απόλυτα. Απλώς καλέστε ξανά το `builder.insertShape` μετά το πρώτο σχήμα, ή μετακινήστε τον κέρσορα με `builder.moveTo` για να τοποθετήσετε επόμενα σχήματα. Κάθε σχήμα λαμβάνει το δικό του `ShadowFormat` και τις ρυθμίσεις γεμίσματος.

### Πώς να κάνω το ορθογώνιο διαφανές αντί της σκιάς;

Χρησιμοποιήστε `rectangleShape.setTransparency(0.5)` (ή `setFillColor` με κανάλι άλφα). Η μέθοδος `setTransparency` στο ίδιο το σχήμα ελέγχει τη διαφάνεια του γεμίσματος, ενώ αυτή στο `ShadowFormat` επηρεάζει τη σκιά.

### Λειτουργεί αυτό με παλαιότερες εκδόσεις του Word;

Ναι. Το Aspose.Words γράφει αρχεία `.docx` που είναι συμβατά με Word 2007 και νεότερα. Αν χρειάζεστε υποστήριξη για παλαιότερο `.doc`, αλλάξτε την επέκταση σε `.doc` και το Aspose θα κάνει αυτόματα την υποβάθμιση.

## Πλήρες Παράδειγμα Εργασίας

Παρακάτω βρίσκεται το ολοκληρωμένο, έτοιμο‑για‑εκτέλεση πρόγραμμα Java. Αντιγράψτε‑και‑επικολλήστε το στο IDE σας, προσαρμόστε τη διαδρομή εξόδου και πατήστε **Run**.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a rectangle shape of desired size and set its fill color
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 200, 100);
        rectangleShape.setFillColor(java.awt.Color.LIGHT_GRAY); // set shape fill color

        // Step 3: Configure the shadow effect – offset, blur, transparency, and color
        rectangleShape.getShadowFormat().setOffsetX(5);
        rectangleShape.getShadowFormat().setOffsetY(5);
        rectangleShape.getShadowFormat().setBlurRadius(4);
        rectangleShape.getShadowFormat().setTransparency(0.3); // how to set shape transparency
        rectangleShape.getShadowFormat().setColor(java.awt.Color.DARK_GRAY); // add shadow to shape

        // Step 4: Save the document with the shaped shadow to a file
        document.save("YOUR_DIRECTORY/ShadowShape.docx"); // save document as docx
    }
}
```

Τρέξτε το πρόγραμμα, ανοίξτε το παραγόμενο αρχείο και θαυμάστε το αποτέλεσμα. 🎉

## Ανακεφαλαίωση: Γιατί Αυτή η Προσέγγιση Είναι Καταπληκτική

- **Απλότητα:** Μόνο τέσσερα λογικά βήματα για **save document as docx** με στυλιζαρισμένο ορθογώνιο.  
- **Ευελιξία:** Κάθε οπτική ιδιότητα (`fill color`, `shadow offset`, `blur radius`, `transparency`) εκτίθεται μέσω ενός σαφούς API.  
- **Φορητότητα:** Ο ίδιος κώδικας λειτουργεί σε Windows, macOS και Linux, εφόσον είναι εγκατεστημένα το Java και το Aspose.Words.  
- **Διατηρησιμότητα:** Διαχωρίζοντας τη δημιουργία σχήματος, το στυλ και την αποθήκευση, μπορείτε εύκολα να επεκτείνετε το demo—προσθέστε κείμενο, εικόνες ή ακόμη και βρόχους που δημιουργούν πολλαπλά σχήματα.

## Επόμενα Βήματα & Σχετικά Θέματα

- **Προσθήκη κειμένου μέσα στο ορθογώνιο** χρησιμοποιώντας `builder.insertParagraph` μετά τη θέση του κέρσορα.  
- **Δημιουργία διαβαθμισμένων γεμισμάτων** με `rectangleShape.getFill().setFillType(FillType.GRADIENT)`.  
- **Εξαγωγή σε PDF** καλώντας `document.save("output.pdf")`—ιδανικό για διανομή.  
- Εξερευνήστε το **how to insert rectangle shape** μέσα σε πίνακες ή κεφαλίδες για πιο σύνθετες διατάξεις.  
- Βυθιστείτε στο **set shape fill color** με προσαρμοσμένες τιμές RGB ή μοτίβα γεμίσματος για branding.

Μην διστάσετε να πειραματιστείτε—αλλάξτε χρώματα, τροποποιήστε τη διαφάνεια της σκιάς ή στοιβάξτε πολλαπλά σχήματα. Το API του Aspose.Words είναι γενναιόδωρο, και τώρα γνωρίζετε το βασικό μοτίβο για **save document as docx** με οπτικές βελτιώσεις.

---

![save document as docx example](alt="παράδειγμα αποθήκευσης εγγράφου ως docx με ορθογώνιο και σκιά")


## Τι Θα Μάθετε Στη Σειρά Επόμενη;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to Load HTML and Save as DOCX using Aspose.Words for Java](/words/english/java/document-loading-and-saving/loading-and-saving-html-documents/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}