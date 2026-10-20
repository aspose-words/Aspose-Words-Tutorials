---
category: general
date: 2026-06-17
description: Δημιουργήστε ένα σεμινάριο Java για το Word που δείχνει πώς να εισάγετε
  σχήμα ορθογωνίου στο Word, να εφαρμόσετε σκιά στο σχήμα και να αποθηκεύσετε το έγγραφο
  ως docx με το Aspose.Words.
draft: false
keywords:
- create word document java
- apply shadow to shape
- save document as docx
- how to add shadow effect
- insert rectangle shape word
language: el
og_description: 'Δημιουργία εγγράφου Word με Java βήμα‑βήμα: εισαγωγή σχήματος ορθογωνίου
  στο Word, εφαρμογή σκιάς στο σχήμα και αποθήκευση του εγγράφου ως docx χρησιμοποιώντας
  το Aspose.Words.'
og_title: Δημιουργία εγγράφου Word Java – Προσθήκη σκιάς σε σχήμα
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Create word document java tutorial that shows how to insert rectangle
    shape word, apply shadow to shape, and save document as docx with Aspose.Words.
  headline: Create Word Document Java – Add Shadow to Shape Guide
  type: TechArticle
tags:
- Java
- Aspose.Words
- Word Automation
- Shapes
title: Δημιουργία εγγράφου Word με Java – Οδηγός προσθήκης σκιάς σε σχήμα
url: /el/java/images-shapes/create-word-document-java-add-shadow-to-shape-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία Εγγράφου Word Java – Οδηγός Προσθήκης Σκιάς σε Σχήμα

Έχετε ποτέ χρειαστεί κώδικα **create word document java** που παράγει ένα επαγγελματικό αρχείο DOCX χωρίς να ανοίξετε το Microsoft Word; Δεν είστε μόνοι. Σε πολλές επιχειρηματικές εφαρμογές πρέπει να δημιουργούμε αναφορές, τιμολόγια ή πιστοποιητικά άμεσα, και η άμεση δημιουργία από τη Java εξοικονομεί χρόνο και άδειες.  

Σε αυτό το tutorial θα περάσουμε βήμα-βήμα τις ακριβείς ενέργειες για **create word document java** χρησιμοποιώντας το Aspose.Words, **insert rectangle shape word**, **apply shadow to shape**, και τελικά **save document as docx**. Στο τέλος θα έχετε ένα εκτελέσιμο πρόγραμμα που δημιουργεί ένα ορθογώνιο με απαλή γκρι σκιά στο παραγόμενο αρχείο — χωρίς χειροκίνητη επεξεργασία.

## Τι Θα Μάθετε

- Πώς να ρυθμίσετε ένα έργο Java με τη βιβλιοθήκη Aspose.Words for Java.  
- Ο ακριβής κώδικας που απαιτείται για **create word document java** και την προσθήκη ενός ορθογωνίου σχήματος.  
- Λεπτομερής διαμόρφωση του **shadow format** ώστε να κατανοήσετε σωστά το **how to add shadow effect**.  
- Η μίας‑γραμμής εντολή που **save document as docx** και πού αποθηκεύεται το αρχείο.  
- Μερικά κοινά προβλήματα και συμβουλές βέλτιστων πρακτικών που θα θέλετε να θυμάστε την επόμενη φορά που θα δημιουργείτε αρχεία Word.

> **Απαιτούμενα** – Χρειάζεστε Java 8 ή νεότερη, Maven (ή Gradle) για τη διαχείριση εξαρτήσεων, και μια έγκυρη άδεια Aspose.Words for Java (η δωρεάν δοκιμή λειτουργεί για demos). Δεν απαιτούνται άλλα εξωτερικά εργαλεία.

---

## Δημιουργία Εγγράφου Word Java – Ρύθμιση του Έργου

Πρώτα απ' όλα: πρέπει να δημιουργήσετε το σκελετό του έργου **create word document java**. Αν χρησιμοποιείτε Maven, προσθέστε την εξάρτηση Aspose.Words στο `pom.xml` σας:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- check for the latest version -->
</dependency>
```

> **Συμβουλή**: Κρατήστε τον αριθμό έκδοσης ενημερωμένο· οι νεότερες εκδόσεις διορθώνουν σφάλματα σχετικά με την απόδοση σχήματος και τη διαχείριση σκιάς.

Μόλις επιλυθεί η εξάρτηση, μπορείτε να αρχίσετε να γράφετε κώδικα Java. Η πρώτη γραμμή οποιασδήποτε ροής εργασίας Aspose.Words είναι η δημιουργία ενός αντικειμένου `Document` — αυτή είναι η καρδιά του **create word document java**.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Παρατηρήστε πώς το `DocumentBuilder` μας παρέχει έναν βολικό κέρσορα για την εισαγωγή περιεχομένου. Σε αυτό το σημείο έχουμε έναν καθαρό καμβά, έτοιμο για σχήματα.

## Εισαγωγή Ορθογώνιου Σχήματος Word με Aspose.Words

Τώρα που το έγγραφο υπάρχει, ας **insert rectangle shape word**. Το ορθογώνιο θα λειτουργήσει ως θέση κράτησης για οποιοδήποτε γραφικό μπορεί να χρειαστείτε αργότερα — σκεφτείτε το ως σήμα, φόντο λογότυπου ή απλό πλαίσιο επισήμανσης.

```java
        // Step 2: Insert a rectangle shape (150x80 points) and give it a light gray fill.
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
        rectangle.setFillColor(java.awt.Color.LIGHT_GRAY);
```

Γιατί ένα ορθογώνιο; Επειδή είναι το πιο απλό σχήμα που εξακολουθεί να δείχνει πώς λειτουργούν οι σκιές σε αντικείμενα που δεν είναι κείμενο. Οι διαστάσεις είναι σε points (1/72 ίντσας), που ταιριάζει με το εσωτερικό σύστημα μέτρησης του Word.

## Εφαρμογή Σκιάς σε Σχήμα – Διαμόρφωση ShadowFormat

Εδώ συμβαίνει η μαγεία — **apply shadow to shape**. Το αντικείμενο `ShadowFormat` σας επιτρέπει να ρυθμίσετε το θόλωμα, την απόσταση, τη διαφάνεια και το χρώμα. Η κατανόηση κάθε ιδιότητας θα σας βοηθήσει να **how to add shadow effect** πέρα από τις προεπιλεγμένες ρυθμίσεις.

```java
        // Step 3: Enable the shadow and configure its visual properties.
        rectangle.getShadowFormat().setVisible(true);          // turn the shadow on
        rectangle.getShadowFormat().setBlurRadius(5.0);        // soft blur
        rectangle.getShadowFormat().setOffsetX(6.0);           // horizontal shift
        rectangle.getShadowFormat().setOffsetY(6.0);           // vertical shift
        rectangle.getShadowFormat().setTransparency(0.3);     // 30 % transparent
        rectangle.getShadowFormat().setColor(java.awt.Color.DARK_GRAY);
```

- **BlurRadius** ελέγχει πόσο θολές φαίνονται οι άκρες· μια τιμή γύρω στο 5 δίνει ένα διακριτικό φτερό.  
- **OffsetX/Y** μετακινεί τη σκιά σε σχέση με το σχήμα· θετικές τιμές τη μεταφέρουν κάτω‑δεξιά.  
- **Transparency** σας επιτρέπει να εξασθενίσετε τη σκιά ώστε να μην κυριαρχεί στη σελίδα.  
- **Color** είναι συνήθως μια πιο σκούρα απόχρωση του γεμίσματος, αλλά μπορείτε να πειραματιστείτε με μπλε ή κόκκινα για στυλιζαρισμένη εμφάνιση.

> **Συχνή ερώτηση**: *Τι γίνεται αν δεν βλέπω σκιά;* Βεβαιωθείτε ότι το `setVisible(true)` καλείται **μετά** την ρύθμιση των άλλων ιδιοτήτων· διαφορετικά το Word μπορεί να αγνοήσει τη διαμόρφωση.

## Αποθήκευση Εγγράφου ως DOCX – Διατήρηση της Εργασίας

Τέλος, πρέπει να **save document as docx** ώστε το αρχείο να μπορεί να ανοίξει από οποιαδήποτε πρόσφατη έκδοση του Microsoft Word, LibreOffice ή Google Docs. Η μέθοδος `save` δέχεται διαδρομή και μορφή· θα χρησιμοποιήσουμε την προεπιλεγμένη μορφή DOCX.

```java
        // Step 4: Save the document with the shaped shadow applied.
        doc.save("output/ShadowShape.docx"); // adjust the folder as needed
    }
}
```

Αυτή η μοναδική γραμμή γράφει ολόκληρο το έγγραφο — συμπεριλαμβανομένου του ορθογωνίου και της σκιάς του — στο δίσκο. Όταν ανοίξετε το `ShadowShape.docx`, θα δείτε ένα ανοιχτό‑γκρι ορθογώνιο με σκοτεινή, ημιδιαφανή σκιά μετατοπισμένη προς τα κάτω‑δεξιά.

> **Συμβουλή**: Χρησιμοποιήστε απόλυτη διαδρομή κατά το debugging (`C:/temp/ShadowShape.docx`) για να αποφύγετε εκπλήξεις «αρχείο δεν βρέθηκε», και μετά επιστρέψτε σε σχετική διαδρομή για παραγωγή.

## Πώς να Προσθέσετε Σκιά – Προχωρημένες Παραλλαγές

Αν αναρωτιέστε **how to add shadow effect** σε άλλα αντικείμενα, το ίδιο `ShadowFormat` εφαρμόζεται σε εικόνες, διαγράμματα και ακόμη και σε πλαίσια κειμένου. Εδώ είναι ένα γρήγορο απόσπασμα που προσθέτει σκιά σε μια εικόνα:

```java
Shape picture = builder.insertImage("logo.png");
picture.getShadowFormat().setVisible(true);
picture.getShadowFormat().setBlurRadius(8.0);
picture.getShadowFormat().setOffsetX(4.0);
picture.getShadowFormat().setOffsetY(4.0);
picture.getShadowFormat().setColor(java.awt.Color.BLACK);
```

Θυμηθείτε, η εμφάνιση της σκιάς μπορεί να διαφέρει μεταξύ εκδόσεων του Word. Αν στοχεύετε σε παλαιότερα αρχεία Word 2007 (`.doc`), ορισμένες ιδιότητες σκιάς μπορεί να αγνοηθούν — πάντα δοκιμάζετε με την ακριβή έκδοση που θα ανοίξουν οι χρήστες.

## Πλήρες Παράδειγμα Εργασίας

Παρακάτω βρίσκεται το πλήρες, αυτόνομο πρόγραμμα Java που **create word document java**, εισάγει ένα ορθογώνιο, εφαρμόζει σκιά, και **save document as docx**. Αντιγράψτε‑και‑επικολλήστε το στο IDE σας, προσαρμόστε τη διαδρομή εξόδου και τρέξτε το.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a rectangle shape and give it a light gray fill.
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
        rectangle.setFillColor(java.awt.Color.LIGHT_GRAY);

        // Step 3: Enable and configure the shadow.
        rectangle.getShadowFormat().setVisible(true);
        rectangle.getShadowFormat().setBlurRadius(5.0);
        rectangle.getShadowFormat().setOffsetX(6.0);
        rectangle.getShadowFormat().setOffsetY(6.0);
        rectangle.getShadowFormat().setTransparency(0.3);
        rectangle.getShadowFormat().setColor(java.awt.Color.DARK_GRAY);

        // Step 4: Save the document.
        doc.save("output/ShadowShape.docx");
    }
}
```

**Αναμενόμενο αποτέλεσμα:** Το άνοιγμα του `ShadowShape.docx` εμφανίζει ένα ορθογώνιο 150 × 80 pt ανοιχτό‑γκρι με μια απαλή σκούρα γκρι σκιά μετατοπισμένη κατά 6 pt οριζόντια και κάθετα. Δεν απαιτείται επιπλέον χειροκίνητη μορφοποίηση.

## Συμπέρασμα

Μόλις δείξαμε πώς να **create word document java** από το μηδέν, **insert rectangle shape word**, **apply shadow to shape**, και **save document as docx** χρησιμοποιώντας το Aspose.Words. Η προσέγγιση είναι απλή, πλήρως προγραμματιστική και λειτουργεί σε όλες τις σύγχρονες εκδόσεις του Word.  

Στη συνέχεια, σκεφτείτε να πειραματιστείτε με άλλους τύπους σχημάτων — έλλειψη, βέλη ή προσαρμοσμένα SVG — και να παίξετε με τα χρώματα της σκιάς ώστε να ταιριάζουν με την παλέτα της μάρκας σας. Μπορείτε επίσης να εξερευνήσετε την προσθήκη κειμένου μέσα στο ορθογώνιο ή τη στρωμάτωση πολλαπλών σχημάτων για πιο πλούσιες σχεδιάσεις.  

Αν έχετε ερωτήσεις σχετικά με την άδεια, συμβουλές απόδοσης για μεγάλα έγγραφα, ή θέλετε να δείτε πώς να επεξεργάζεστε δεκάδες αρχεία μαζικά, ενημερώστε με στα σχόλια. Καλή προγραμματιστική εργασία, και απολαύστε τη νέα δυνατότητα δημιουργίας όμορφων αρχείων Word απευθείας από τη Java!  

![Δημιουργία εγγράφου word java με σχήμα σκιάς](/images/create-word-document-java-shadow.png "παράδειγμα create word document java")

## Τι Θα Πρέπει Να Μάθετε Στη Σειρά;

- [Δημιουργία Εγγράφου Word Java – Προσθήκη Ορθογώνιου Σχήματος με Εφέ Σκιάς](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words Java: Πλήρης Οδηγός Επεξεργασίας Εγγράφων Word](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [Παρακολούθηση Αλλαγών σε Έγγραφα Word Χρησιμοποιώντας Aspose.Words Java: Πλήρης Οδηγός Αναθεώρησης Εγγράφων](/words/english/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}