---
category: general
date: 2026-11-15
description: Δημιουργήστε σχήμα ορθογωνίου στο Word με Java και μάθετε πώς να προσθέτετε
  σχήματα στο Word, να ορίζετε τις διαστάσεις του σχήματος και να αποθηκεύετε το έγγραφο
  Word αποδοτικά.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add shapes to word
- save word document
- set shape dimensions
- define shape size
language: el
lastmod: 2026-11-15
og_description: Δημιουργήστε σχήμα ορθογωνίου σε έγγραφο Word χρησιμοποιώντας Java.
  Μάθετε πώς να προσθέτετε σχήματα στο Word, να ορίζετε τις διαστάσεις του σχήματος
  και να αποθηκεύετε το έγγραφο Word σε λίγα λεπτά.
og_image_alt: Screenshot showing a rectangle shape inside a group shape in a Word
  document
og_title: Δημιουργία σχήματος ορθογωνίου στο Word με Java – οδηγός βήμα‑προς‑βήμα
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  headline: Create rectangle shape in a Word document using Java
  type: TechArticle
- description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  name: Create rectangle shape in a Word document using Java
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well). * Aspose.Words
      for Java 23.10 or newer – you can obtain it from Maven Central. * A basic understanding
      of Java syntax and object‑oriented concepts.'
  - name: Expected output
    text: '* A Word file named `RectangleShapeDemo.docx`. * Inside the first paragraph,
      a group shape containing a 100 pt × 50 pt rectangle. * No text is added, so
      the rectangle appears on a blank page.'
  - name: What’s next?
    text: '* Explore **add shapes to Word** by inserting circles, arrows, or text
      boxes. * Combine multiple shapes into a single `GroupShape` and apply transformations
      (rotate, flip). * Generate reports that embed charts as shapes, then **save
      Word document** as PDF for sharing.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Δημιουργία σχήματος ορθογωνίου σε έγγραφο Word με Java
url: /el/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία σχήματος ορθογωνίου σε έγγραφο Word χρησιμοποιώντας Java

Αν χρειάζεστε **create rectangle shape** μέσα σε αρχείο Word, αυτός ο οδηγός σας δείχνει ακριβώς πώς να το κάνετε με Java. Θα δείτε πώς να **add shapes to Word**, να ελέγξετε το **set shape dimensions**, και τελικά να **save Word document** χωρίς να φύγετε από το IDE σας.

Στις επόμενες ενότητες θα λάβετε ένα πλήρες, εκτελέσιμο παράδειγμα, εξήγηση κάθε γραμμής και συμβουλές για κοινά προβλήματα όπως ζητήματα μεγέθους και συμβατότητας εγγράφου. Δεν απαιτούνται εξωτερικές αναφορές—μόνο η βιβλιοθήκη Aspose.Words for Java.

## Τι θα μάθετε

* Πώς να αρχικοποιήσετε ένα `Document` και ένα `DocumentBuilder`.
* Πώς να εισάγετε ένα **group shape** και να τοποθετήσετε ένα ορθογώνιο μέσα του.
* Πώς να **define shape size** χρησιμοποιώντας `setWidth` και `setHeight`.
* Πώς να **save Word document** σε μορφή `.docx`.
* Διαχείριση edge‑case για διαφορετικά μεγέθη σελίδας και ρυθμίσεις DPI.

### Προαπαιτούμενα

* Java 17 ή νεότερη (ο κώδικας συντάσσεται επίσης με Java 8).
* Aspose.Words for Java 23.10 ή νεότερη – μπορείτε να την αποκτήσετε από το Maven Central.
* Βασική κατανόηση της σύνταξης Java και των αντικειμενοστραφών εννοιών.

> **Pro tip:** Εάν σκοπεύετε να προσθέσετε περισσότερα σχήματα αργότερα (π.χ., κύκλους ή πλαίσια κειμένου), κρατήστε τα μέσα στο ίδιο `GroupShape`. Αυτό καθιστά την μετακίνηση, περιστροφή ή μορφοποίηση ολόκληρης της συλλογής πολύ πιο εύκολη.

## Βήμα 1: Αρχικοποίηση του εγγράφου και του builder

Το πρώτο βήμα είναι να δημιουργήσετε ένα κενό αρχείο Word και ένα `DocumentBuilder` που σας επιτρέπει να γράψετε περιεχόμενο.  

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Why this matters:* Ένα `Document` αντιπροσωπεύει ολόκληρο το αρχείο, ενώ το `DocumentBuilder` παρέχει μεθόδους υψηλού επιπέδου για εισαγωγή κειμένου, πινάκων και **shapes**. Χωρίς τον builder θα έπρεπε να χειριστείτε χειροκίνητα κόμβους χαμηλού επιπέδου.

## Βήμα 2: Εισαγωγή group shape για να κρατήσει πολλαπλά σχήματα

Ένα **group shape** λειτουργεί ως κοντέινερ· μπορείτε να προσθέσετε πολλά σχήματα και να τα αντιμετωπίζετε ως ένα ενιαίο αντικείμενο αργότερα (π.χ., να τα μετακινήσετε ή να τα περιστρέψετε μαζί).

```java
        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();
```

*Why use a group shape?* Εάν αργότερα αποφασίσετε να προσθέσετε βέλη, κύκλους ή ετικέτες γύρω από το ορθογώνιο, το group διατηρεί όλα ευθυγραμμισμένα. Επίσης απλοποιεί τη ροή εργασίας **add shapes to Word** επειδή χρειάζεται μόνο μία κλήση στο `appendChild` για κάθε νέο σχήμα.

## Βήμα 3: Δημιουργία του σχήματος ορθογωνίου

Τώρα δημιουργούμε το πραγματικό ορθογώνιο που θα ζει μέσα στο group. Ο κατασκευαστής `Shape` χρειάζεται το ιδιοκτησιακό `Document` και τον τύπο σχήματος που θέλετε.

```java
        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
```

*Why a rectangle?* `ShapeType.RECTANGLE` είναι το πιο κοινό πρωτότυπο για επισήμανση τμημάτων, δημιουργία placeholders ή σχεδίαση απλών UI mock‑ups απευθείας μέσα στο Word.

## Βήμα 4: Ορισμός του μεγέθους του ορθογωνίου

Η ρύθμιση των διαστάσεων είναι το σημείο όπου το **set shape dimensions** γίνεται σημαντικό. Μπορείτε να χρησιμοποιήσετε οποιαδήποτε μονάδα μέτρησης υποστηρίζεται από το Aspose.Words· η προεπιλογή είναι τα points (1 pt = 1/72 inch).

```java
        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

> **Note:** Εάν προτιμάτε χιλιοστά, καλέστε `rectangle.setWidth(ConversionUtil.inchesToPoints(1.39));` όπου `1.39 in ≈ 35 mm`. Αυτό δείχνει την ευελιξία του **define shape size**.

## Βήμα 5: Προσθήκη του ορθογωνίου στο group shape

Η προσθήκη του ορθογωνίου στο προηγουμένως δημιουργημένο group το κάνει ορατό στο έγγραφο.

```java
        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);
```

Σε αυτό το σημείο το ορθογώνιο βρίσκεται στην πάνω‑αριστερή γωνία του group. Μπορείτε να το μετακινήσετε αργότερα με `rectangle.setLeft(...)` και `rectangle.setTop(...)` εάν χρειάζεστε ακριβή τοποθέτηση.

## Βήμα 6: (Προαιρετικό) Αποθήκευση του εγγράφου για να δείτε το αποτέλεσμα

Τέλος, γράψτε το έγγραφο στο δίσκο. Αυτό είναι το βήμα **save Word document** που παράγει ένα αρχείο `.docx` που μπορείτε να ανοίξετε στο Microsoft Word, LibreOffice ή Google Docs.

```java
        // Step 6: Save the document (optional but recommended for verification)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

Η εκτέλεση του προγράμματος δημιουργεί το `RectangleShapeDemo.docx` που περιέχει ένα μόνο ορθογώνιο μέσα σε ένα group shape. Το άνοιγμα του αρχείου δείχνει ένα λευκό ορθογώνιο—ακριβώς το μέγεθος που ορίσατε.

### Αναμενόμενο αποτέλεσμα

* Ένα αρχείο Word με όνομα `RectangleShapeDemo.docx`.
* Στην πρώτη παράγραφο, ένα group shape που περιέχει ένα ορθογώνιο 100 pt × 50 pt.
* Δεν προστέθηκε κείμενο, έτσι το ορθογώνιο εμφανίζεται σε κενή σελίδα.

## Συνηθισμένες παραλλαγές και edge cases

| **Διαφορετικό μέγεθος σελίδας** (π.χ., A4) | Call `document.getFirstSection().getPageSetup().setPaperSize(PaperSize.A4);` before inserting the shape. |
| **Υψηλότερο DPI για εκτύπωση** | Multiply width/height by the desired DPI factor, e.g., `rectangle.setWidth(200 * 2);` for double resolution. |
| **Προσθήκη ετικέτας κειμένου μέσα στο ορθογώνιο** | Create a `Shape` of type `TEXT_BOX`, set its `setWidth`/`setHeight` to match the rectangle, then add it to the same `GroupShape`. |
| **Περιστροφή του ορθογωνίου** | Use `rectangle.setRotationAngle(45);` to rotate 45 degrees clockwise. |
| **Αποθήκευση ως PDF αντί για DOCX** | Replace `document.save("output.docx");` with `document.save("output.pdf");` – the same API works for PDF, preserving the rectangle. |

## Pro tips για μια αξιόπιστη υλοποίηση

1. **Reuse the builder** – after inserting the group shape, you can continue adding paragraphs or tables without creating a new builder instance.
2. **Dispose resources** – although Java’s garbage collector handles most objects, explicitly calling `document.close();` (if using streams) prevents file‑handle leaks.
3. **Validate dimensions** – before calling `setWidth`/`setHeight`, ensure the values are positive; negative values throw `IllegalArgumentException`.
4. **Version compatibility** – the code works with Aspose.Words 23.x and later. Earlier versions may require `Shape.setSize(width, height)` instead of separate setters.

## Πλήρες, εκτελέσιμο παράδειγμα

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();

        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);

        // Optional: set a light gray fill to make it visible in Word
        rectangle.getFillColor() .setRGB(200, 200, 200);

        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);

        // Step 6: Save the document (you can also save as PDF)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

> **Result verification:** Open `output/RectangleShapeDemo.docx` in Microsoft Word. You should see a rectangle of the specified size centered at the top of the first page. If the rectangle appears too small, adjust the values passed to `setWidth` and `setHeight`.

## Συμπέρασμα

Τώρα γνωρίζετε πώς να **create rectangle shape** σε αρχείο Word χρησιμοποιώντας Java, πώς να **add shapes to Word** μέσω ενός `GroupShape`, πώς να **set shape dimensions** και **define shape size**, και τέλος πώς να **save Word document** για περαιτέρω διανομή. Το ίδιο μοτίβο λειτουργεί για άλλους τύπους σχημάτων, επιτρέποντάς σας να δημιουργήσετε σύνθετα διαγράμματα προγραμματιστικά.

### Τι ακολουθεί;

* Εξερευνήστε **add shapes to Word** εισάγοντας κύκλους, βέλη ή πλαίσια κειμένου.
* Συνδυάστε πολλαπλά σχήματα σε ένα `GroupShape` και εφαρμόστε μετασχηματισμούς (περιστροφή, αναστροφή).
* Δημιουργήστε αναφορές που ενσωματώνουν διαγράμματα ως σχήματα, και στη συνέχεια **save Word document** ως PDF για κοινή χρήση.

Αισθανθείτε ελεύθεροι να πειραματιστείτε με τις διαστάσεις, τα χρώματα και την τοποθέτηση ώστε να ταιριάζουν στο συγκεκριμένο σενάριό σας. Καλή κωδικοποίηση!

## Τι πρέπει να μάθετε στη συνέχεια;

Οι παρακάτω εκπαιδευτικές ενότητες καλύπτουν στενά σχετικές θεματικές που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Δημιουργία εγγράφου Word Java – Προσθήκη σχήματος ορθογωνίου με εφέ σκιά](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Δημιουργία σχήματος ορθογωνίου σε έγγραφο Word Java – Πλήρης οδηγός βήμα‑βήμα](/words/english/java/images-shapes/create-rectangle-shape-in-java-word-document-full-step-by-st/)
- [Δημιουργία εγγράφου Word java – απόκρυψη σχήματος και ορισμός χρώματος γεμίσματος](/words/english/java/images-shapes/create-word-document-java-hide-shape-and-set-fill-color/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}