---
category: general
date: 2026-11-25
description: Απόκρυψη σχήματος στο Word με το Aspose.Words και μάθετε πώς να δημιουργείτε
  έγγραφο Word με το Aspose ενώ εισάγετε σχήμα ορθογωνίου στο Word με λίγες μόνο γραμμές
  κώδικα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- hide shape in word
- create word document aspose
- insert rectangle shape word
- Aspose.Words shape handling
- hide Word objects programmatically
language: el
lastmod: 2026-11-25
og_description: Απόκρυψη σχήματος στο Word χρησιμοποιώντας το Aspose.Words. Αυτό το
  σεμινάριο δείχνει πώς να δημιουργήσετε έγγραφο Word με το Aspose, να εισάγετε σχήμα
  ορθογωνίου στο Word και να το αποκρύψετε προγραμματιστικά.
og_image_alt: Screenshot of a hidden rectangle shape inside a Word document created
  with Aspose.Words
og_title: Απόκρυψη σχήματος στο Word με το Aspose.Words – γρήγορος οδηγός βήμα‑βήμα
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Hide shape in Word with Aspise.Words and learn to create Word document
    aspose while you insert rectangle shape word in just a few lines of code.
  headline: How to hide shape in Word using Aspose.Words
  type: TechArticle
- description: Hide shape in Word with Aspise.Words and learn to create Word document
    aspose while you insert rectangle shape word in just a few lines of code.
  name: How to hide shape in Word using Aspose.Words
  steps:
  - name: Prerequisites
    text: '* Java 17+ (or .NET 6+ if you prefer C#—the API calls are analogous). *
      Aspose.Words for Java 24.x (the latest version at the time of writing). * An
      IDE such as IntelliJ IDEA, Eclipse, or VS Code.'
  - name: Create a Word document aspose
    text: First, instantiate a blank `Document` and a `DocumentBuilder`. The builder
      provides a fluent API for adding content, including shapes.
  - name: Insert rectangle shape word
    text: Now we add a rectangle shape. The `insertShape` method requires the shape
      type and its dimensions in points (1 point = 1/72 inch).
  - name: Hide the shape so it does not appear in the layout
    text: Aspose.Words mirrors the Microsoft Word *Hidden* attribute. Setting it to
      `true` tells Word to omit the shape from rendering, while keeping the object
      in the document structure.
  - name: Save and verify the result
    text: Finally, write the document to disk. Open the file in Microsoft Word to
      confirm that the rectangle is not visible. You can also inspect the underlying
      XML to see the hidden flag.
  - name: (Optional) Unhide the shape later
    text: If you need to make the shape visible again, load the document, locate the
      shape, and set `hidden` to `false`.
  - name: What the output files contain
    text: '* **HideShapeResult.docx** – the rectangle is hidden; the page looks empty.
      * **UnhiddenShape.docx** – the same rectangle is visible, showing a red box
      with a black outline.'
  - name: Next steps
    text: '* Explore **conditional content** by combining hidden shapes with mail‑merge
      fields. * Learn how to **hide text runs** (`Run.setHidden(true)`) for more granular
      control. * Check the Aspose.Words documentation on **document protection** to
      prevent users from accidentally unhiding shapes.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Shape manipulation
title: Πώς να κρύψετε σχήμα στο Word χρησιμοποιώντας το Aspose.Words
url: /el/java/images-shapes/how-to-hide-shape-in-word-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να κρύψετε σχήμα στο Word χρησιμοποιώντας Aspose.Words

Αν χρειάζεστε **να κρύψετε σχήμα στο Word** κατά τη δημιουργία εγγράφων προγραμματιστικά, το Aspose.Words το κάνει εύκολο. Σε αυτόν τον οδηγό θα δείτε ακριβώς πώς να δημιουργήσετε ένα έγγραφο Word aspose, να εισάγετε σχήμα ορθογωνίου word, και στη συνέχεια να κρύψετε αυτό το σχήμα ώστε να μην εμφανίζεται στη διάταξη. Παρέχεται το πλήρες, εκτελέσιμο παράδειγμα ώστε να το αντιγράψετε‑επικολλήσετε στο IDE σας και να δείτε το αποτέλεσμα αμέσως.

Θα ολοκληρώσετε αυτό το tutorial με ένα αρχείο Word που περιέχει ένα κρυφό ορθογώνιο—χρήσιμο για placeholders, υπό όρους περιεχόμενο, ή μεταδεδομένα που πρέπει να παραμείνουν αόρατα στον αναγνώστη. Δεν απαιτούνται εξωτερικά εργαλεία πέρα από τη βιβλιοθήκη Aspose.Words for Java (ή .NET).

## Τι θα μάθετε

* Πώς να **δημιουργήσετε ένα έγγραφο Word aspose** από το μηδέν.  
* Πώς να **εισάγετε σχήμα ορθογωνίου word** χρησιμοποιώντας το `DocumentBuilder`.  
* Πώς να ορίσετε την ιδιότητα `hidden` του σχήματος ώστε να μην αποδίδεται στην τελική διάταξη.  
* Πώς να επαληθεύσετε ότι το σχήμα είναι κρυφό και πώς να το εμφανίσετε ξανά αν χρειαστεί.  

### Προαπαιτούμενα

* Java 17+ (ή .NET 6+ αν προτιμάτε C#—οι κλήσεις API είναι ανάλογες).  
* Aspose.Words for Java 24.x (η πιο πρόσφατη έκδοση τη στιγμή της συγγραφής).  
* Ένα IDE όπως IntelliJ IDEA, Eclipse, ή VS Code.  

> **Pro tip:** Χρησιμοποιήστε την δωρεάν προσωρινή άδεια από την Aspose αν δεν έχετε ακόμα εμπορική. Η βιβλιοθήκη λειτουργεί χωρίς άδεια για αξιολόγηση, αλλά μια άδεια αφαιρεί τα υδατογραφήματα αξιολόγησης.

## Κρύψτε σχήμα στο Word με Aspose.Words

Τα βασικά βήματα είναι:

1. **Δημιουργήστε ένα νέο `Document`.**  
2. **Εισάγετε ένα σχήμα ορθογωνίου** χρησιμοποιώντας το `DocumentBuilder`.  
3. **Σημειώστε το σχήμα ως κρυφό** ώστε να μην εμφανίζεται όταν ανοίξει το αρχείο.  

Κάθε βήμα εξηγείται παρακάτω με κώδικα και λογική.

### Βήμα 1: Δημιουργήστε ένα έγγραφο Word aspose

Πρώτα, δημιουργήστε ένα κενό `Document` και ένα `DocumentBuilder`. Ο builder παρέχει μια fluent API για την προσθήκη περιεχομένου, συμπεριλαμβανομένων των σχημάτων.

```java
// Step 1: Create a new document and a DocumentBuilder to work with it
import com.aspose.words.*;

public class HideShapeExample {
    public static void main(String[] args) throws Exception {
        // Load a free evaluation license (optional for production)
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // Create an empty Word document
        Document doc = new Document();

        // DocumentBuilder lets us add text, tables, shapes, etc.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Γιατί είναι σημαντικό:**  
Η δημιουργία ενός φρέσκου `Document` σας δίνει έναν καθαρό καμβά. Ο `DocumentBuilder` είναι η συνιστώμενη μέθοδος για την τροποποίηση του εγγράφου επειδή παρακολουθεί αυτόματα το τρέχον σημείο εισαγωγής και διαχειρίζεται τις ενότητες/σελίδες για εσάς.

### Βήμα 2: Εισάγετε σχήμα ορθογωνίου word

Τώρα προσθέτουμε ένα σχήμα ορθογωνίου. Η μέθοδος `insertShape` απαιτεί τον τύπο του σχήματος και τις διαστάσεις του σε points (1 point = 1/72 ίντσα).

```java
        // Step 2: Insert a rectangle shape of size 100x50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);

        // Optional: give the shape a visible fill and outline so you can see it before hiding
        rectangle.getFillColor().setRGB(255, 0, 0); // red fill
        rectangle.getStroke().setColor(java.awt.Color.BLACK);
        rectangle.getStroke().setWeight(1.0);
```

**Γιατί είναι σημαντικό:**  
Η `insertShape` δημιουργεί ένα αντικείμενο σχεδίασης που ζει στο *drawing* τμήμα του εγγράφου. Καθορίζοντας το μέγεθος, ελέγχετε πόσο χώρο θα κατείχε το σχήμα αν ήταν ορατό. Η προαιρετική μορφοποίηση σας βοηθά να επαληθεύσετε το σχήμα πριν το κρύψετε.

### Βήμα 3: Κρύψτε το σχήμα ώστε να μην εμφανίζεται στη διάταξη

Το Aspose.Words αντικατοπτρίζει το χαρακτηριστικό *Hidden* του Microsoft Word. Ορίζοντάς το σε `true` λέτε στο Word να παραλείψει το σχήμα από την απόδοση, διατηρώντας το αντικείμενο στη δομή του εγγράφου.

```java
        // Step 3: Hide the shape so it does not appear in the layout
        rectangle.setHidden(true);
```

**Γιατί είναι σημαντικό:**  
Ένα κρυφό σχήμα μπορεί ακόμη να προσπελαστεί προγραμματιστικά (π.χ., για υπό‑όρους επεξεργασία) και μπορεί να εμφανιστεί ξανά αργότερα αλλάζοντας την ιδιότητα. Αυτό είναι ιδανικό για σενάρια όπως **υπό‑όρους placeholders** που πρέπει να εμφανίζονται μόνο για συγκεκριμένα ακροατήρια.

### Βήμα 4: Αποθηκεύστε και επαληθεύστε το αποτέλεσμα

Τέλος, γράψτε το έγγραφο στο δίσκο. Ανοίξτε το αρχείο στο Microsoft Word για να επιβεβαιώσετε ότι το ορθογώνιο δεν είναι ορατό. Μπορείτε επίσης να εξετάσετε το υποκείμενο XML για να δείτε τη σημαία hidden.

```java
        // Save the document
        String outPath = "HideShapeResult.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

**Αναμενόμενη έξοδος:**  
Η εκτέλεση του προγράμματος εκτυπώνει:

```
Document saved to HideShapeResult.docx
```

Όταν ανοίξετε το *HideShapeResult.docx* στο Word, η σελίδα φαίνεται κενή (ή περιέχει οποιοδήποτε άλλο περιεχόμενο προσθέσατε πριν το σχήμα). Το ορθογώνιο υπάρχει στο XML του αρχείου (`<w:hidden>` attribute) αλλά δεν αποδίδεται.

### Βήμα 5: (Προαιρετικό) Εμφανίστε ξανά το σχήμα αργότερα

Αν χρειαστεί να κάνετε το σχήμα ορατό ξανά, φορτώστε το έγγραφο, εντοπίστε το σχήμα, και ορίστε `hidden` σε `false`.

```java
        // Load the document again
        Document loadedDoc = new Document(outPath);
        Shape hiddenRect = (Shape) loadedDoc.getChild(NodeType.SHAPE, 0, true);
        hiddenRect.setHidden(false);
        loadedDoc.save("UnhiddenShape.docx");
```

**Γιατί είναι σημαντικό:**  
Η δυνατότητα εναλλαγής της σημαίας hidden σας δίνει πλήρη έλεγχο πάνω στη δυναμική δημιουργία εγγράφων—π.χ., μπορείτε να δημιουργήσετε ένα κύριο έγγραφο με όλα τα προαιρετικά στοιχεία κρυμμένα, και στη συνέχεια να τα εμφανίσετε επιλεκτικά βάσει προτιμήσεων χρήστη.

## Πλήρες, εκτελέσιμο παράδειγμα (δημιουργία word document aspose, εισαγωγή σχήματος ορθογωνίου word, κρύψιμο σχήματος)

Παρακάτω βρίσκεται το πλήρες πρόγραμμα που μπορείτε να μεταγλωττίσετε και να εκτελέσετε άμεσα.

```java
// HideShapeExample.java
import com.aspose.words.*;

public class HideShapeExample {
    public static void main(String[] args) throws Exception {
        // ---- License (optional for evaluation) ----
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // ---- Step 1: Create a new document ----
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // ---- Step 2: Insert rectangle shape ----
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rectangle.getFillColor().setRGB(255, 0, 0); // red fill for visual check
        rectangle.getStroke().setColor(java.awt.Color.BLACK);
        rectangle.getStroke().setWeight(1.0);

        // ---- Step 3: Hide the shape ----
        rectangle.setHidden(true);

        // ---- Step 4: Save the document ----
        String outPath = "HideShapeResult.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);

        // ---- Optional Step 5: Unhide and save a second file ----
        Document loadedDoc = new Document(outPath);
        Shape hiddenRect = (Shape) loadedDoc.getChild(NodeType.SHAPE, 0, true);
        hiddenRect.setHidden(false);
        loadedDoc.save("UnhiddenShape.docx");
        System.out.println("Unhidden document saved to UnhiddenShape.docx");
    }
}
```

**Εκτέλεση του κώδικα**

```bash
javac -cp "aspose-words-24.10.jar" HideShapeExample.java
java -cp ".:aspose-words-24.10.jar" HideShapeExample
```

Αντικαταστήστε το `aspose-words-24.10.jar` με την πραγματική έκδοση που κατεβάσατε.

### Τι περιέχουν τα αρχεία εξόδου

* **HideShapeResult.docx** – το ορθογώνιο είναι κρυφό· η σελίδα φαίνεται κενή.  
* **UnhiddenShape.docx** – το ίδιο ορθογώνιο είναι ορατό, εμφανίζοντας ένα κόκκινο κουτί με μαύρο περίγραμμα.

## Συχνές ερωτήσεις & διαχείριση edge‑case

| Ερώτηση | Απάντηση |
|----------|--------|
| *Θα επηρεάσει το κρυφό σχήμα την σελιδοποίηση;* | Όχι. Τα κρυφά αντικείμενα αγνοούνται από τη μηχανή διάταξης, οπότε δεν ωθούν το κείμενο σε νέα σελίδα. |
| *Μπορώ να κρύψω άλλα αντικείμενα Word (π.χ., εικόνες, πίνακες);* | Ναι. Οι περισσότερες υποκλάσεις του `Node` (συμπεριλαμβανομένων των `Shape`, `Paragraph`, `Run`) διαθέτουν μέθοδο `setHidden(boolean)`. |
| *Τι γίνεται αν το έγγραφο περιέχει ήδη σχήματα;* | Χρησιμοποιήστε `doc.getChildNodes(NodeType.SHAPE, true)` για να επαναλάβετε και να κρύψετε μόνο τα σχήματα που στοχεύετε. |
| *Αυξάνει το κρυφό σχήμα το μέγεθος του αρχείου;* | Ελαφρώς, επειδή το XML του σχήματος παραμένει. Η επίπτωση είναι αμελητέα για τυπικά έγγραφα. |
| *Θα παραμείνει η σημαία hidden όταν το έγγραφο αποθηκευτεί ως PDF;* | Κατά τη μετατροπή σε PDF, τα κρυφά σχήματα παραλείπονται εξ ορισμού. Μπορείτε να το ελέγξετε με `PdfSaveOptions` αν χρειάζεται. |

## Καλές πρακτικές κατά τη δουλειά με κρυφά αντικείμενα

* **Ονομάστε τα σχήματά σας** χρησιμοποιώντας `setName("MyPlaceholder")`. Αυτό διευκολύνει την μελλοντική τους εντόπιση.  
* **Ομαδοποιήστε σχετικούς κρυφούς αντικειμένους** μέσα σε ένα `GroupShape` αν χρειάζεται να εναλλάξετε την ορατότητα πολλών στοιχείων ταυτόχρονα.  
* **Καταγράψτε τον σκοπό** των κρυφών στοιχείων σε σχόλια ή σε ξεχωριστό αρχείο προδιαγραφών—οι μελλοντικοί συντηρητές θα το εκτιμήσουν.  
* **Αποφύγετε την υπερβολική χρήση** κρυφών αντικειμένων· αυξάνουν την πολυπλοκότητα του εγγράφου και μπορούν να μπερδέψουν τους τελικούς χρήστες που εξετάζουν το XML χειροκίνητα.

## Συμπέρασμα

Τώρα ξέρετε πώς να **κρύψετε σχήμα στο Word** χρησιμοποιώντας Aspose.Words, πώς να **δημιουργήσετε ένα έγγραφο Word aspose**, και πώς να **εισάγετε σχήμα ορθογωνίου word** πριν το κρύψετε. Το παράδειγμα δείχνει ολόκληρο τον κύκλο ζωής: δημιουργία, εισαγωγή, κρύψιμο, αποθήκευση, και προαιρετικά εμφάνιση ξανά. Εφαρμόστε αυτές τις τεχνικές για να δημιουργήσετε δυναμικές αναφορές, υπό‑όρους πρότυπα, ή οποιαδήποτε αυτοματοποιημένη ροή εργασίας Word όπου χρειάζονται αόρατα placeholders.

### Επόμενα βήματα

* Εξερευνήστε **υπό‑όρους περιεχόμενο** συνδυάζοντας κρυφά σχήματα με πεδία mail‑merge.  
* Μάθετε πώς να **κρύψετε τμήματα κειμένου** (`Run.setHidden(true)`) για πιο λεπτομερή έλεγχο.  
* Δείτε την τεκμηρίωση Aspose.Words για **προστασία εγγράφου** ώστε να αποτρέψετε τους χρήστες από το να εμφανίσουν κατά λάθος κρυφά σχήματα.

Καλή προγραμματιστική δουλειά, και αφήστε τα παραγόμενα αρχεία Word σας καθαρά ενώ μεταφέρουν τα κρυφά δεδομένα που χρειάζεστε!

### Τι θα πρέπει να μάθετε στη συνέχεια;

Οι παρακάτω οδηγίες καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [Create a Word document programmatically, add and hide a shape in Java using Aspose.Words](/words/english/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/)
- [How to hide shape in a Word document using Java](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Create a blank .docx Word document and add a hidden rectangle shape with Aspose.Words](/words/english/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}