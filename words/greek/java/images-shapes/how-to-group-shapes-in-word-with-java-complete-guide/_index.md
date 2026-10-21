---
category: general
date: 2026-10-16
description: Μάθετε πώς να ομαδοποιείτε σχήματα στο Word χρησιμοποιώντας Java. Αυτό
  το σεμινάριο δείχνει πώς να προσθέσετε σχήμα ορθογωνίου, να ορίσετε το μέγεθος και
  τις διαστάσεις του σχήματος και να αποθηκεύσετε το έγγραφο.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- set shape size
- set shape dimensions
- rectangle shape code
language: el
lastmod: 2026-10-16
og_description: Ομαδοποίηση σχημάτων στο Word με χρήση Java. Προσθήκη σχήματος ορθογωνίου,
  ορισμός μεγέθους και διαστάσεων του σχήματος και δημιουργία επαγγελματικών εγγράφων
  προγραμματιστικά.
og_image_alt: Screenshot of a Word document showing grouped rectangle and ellipse
  shapes created with Java
og_title: Ομαδοποίηση σχημάτων στο Word με Java – βήμα‑βήμα οδηγός
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Learn how to group shapes in Word using Java. This tutorial shows how
    to add rectangle shape, set shape size and dimensions, and save the document.
  headline: How to group shapes in Word with Java – complete guide
  type: TechArticle
- description: Learn how to group shapes in Word using Java. This tutorial shows how
    to add rectangle shape, set shape size and dimensions, and save the document.
  name: How to group shapes in Word with Java – complete guide
  steps:
  - name: Expected output
    text: '- A file named **GroupShapeDemo.docx** appears in the project folder. -
      Opening the file in Word shows two shapes (a rectangle and an ellipse) that
      are grouped together. - Dragging either shape moves the whole group, confirming
      that **group shapes in word** works as intended.'
  - name: Pro tip
    text: 'When you need to **set shape dimensions** based on dynamic data (e.g.,
      a barcode length), calculate the width/height in points first:'
  - name: What’s next?
    text: '- Explore **add rectangle shape** variations such as rounded corners (`ShapeType.RECTANGLE`
      with `setCornerRadius`). - Combine **group shapes in word** with tables or charts
      for richer documents. - Look into the Aspose.Words API for **text wrapping**
      (`shape.setWrapType(WrapType.SQUARE)`) to control'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Πώς να ομαδοποιήσετε σχήματα στο Word με Java – πλήρης οδηγός
url: /el/java/images-shapes/how-to-group-shapes-in-word-with-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να ομαδοποιήσετε σχήματα στο Word με Java – πλήρης οδηγός

Αν χρειάζεστε να **ομαδοποιήσετε σχήματα στο Word** προγραμματιστικά, αυτό το σεμινάριο σας παρέχει μια έτοιμη προς εκτέλεση λύση. Θα δείτε πώς να **προσθέσετε σχήμα ορθογωνίου**, να προσαρμόσετε το μέγεθός του, να ορίσετε τις διαστάσεις του σχήματος και, τέλος, να αποθηκεύσετε ένα αρχείο DOCX που περιέχει ένα ομαδοποιημένο ορθογώνιο και μια έλλειψη.

Η ομαδοποίηση σχημάτων στο Word είναι χρήσιμη για τη δημιουργία σύνθετων διαγραμμάτων, την κατασκευή επαναχρησιμοποιήσιμων γραφικών στοιχείων ή απλώς για τη διατήρηση σχετικών αντικειμένων μαζί όταν το έγγραφο επεξεργάζεται αργότερα. Ο κώδικας χρησιμοποιεί τη βιβλιοθήκη Aspose.Words for Java, η οποία λειτουργεί με οποιοδήποτε πρόσφατο JDK και δεν απαιτεί την εγκατάσταση του Microsoft Word.

## Prerequisites

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

| Απαίτηση | Αιτία |
|-------------|--------|
| Java 17 (ή νεότερη) | Η βιβλιοθήκη στοχεύει σε σύγχρονες εκδόσεις Java. |
| Aspose.Words for Java (latest version) | Παρέχει τις κλάσεις `Document`, `DocumentBuilder`, `GroupShape` και `Shape` που χρησιμοποιούνται στο παράδειγμα. |
| Ένα IDE ή εργαλείο κατασκευής (Maven/Gradle) | Για τη μεταγλώττιση και εκτέλεση του δείγματος. |
| Βασικές γνώσεις της σύνταξης Java | Απαιτείται για την κατανόηση της ροής του κώδικα. |

Add the Aspose.Words dependency to your project. For Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version> <!-- Use the latest version -->
</dependency>
```

Or for Gradle:

```gradle
implementation 'com.aspose:aspose-words:23.10'
```

## Overview of the solution

The tutorial follows a clear **problem → solution → explanation** pattern:

1. **Δημιουργήστε ένα νέο έγγραφο Word** και αποκτήστε ένα `DocumentBuilder`.  
2. **Εισάγετε ένα δοχείο `GroupShape`** που θα περιέχει πολλαπλά σχήματα.  
3. **Προσθέστε ένα ορθογώνιο**, ορίστε το πλάτος/ύψος του (το βήμα **set shape size**), και συνδέστε το με την ομάδα.  
4. **Προσθέστε μια έλλειψη**, τοποθετήστε την μέσα στην ίδια ομάδα, και επίσης ορίστε τις διαστάσεις της.  
5. **Αποθηκεύστε** το έγγραφο στον δίσκο.

Each step includes the **why** behind the code, so you understand what the API does and how you can adapt it to other scenarios.

## Step 1: Create the document and a DocumentBuilder

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to work with it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Why this matters:** `Document` represents the entire DOCX file, while `DocumentBuilder` is a helper that lets you insert content without dealing with low‑level node management. Creating them first gives you a clean canvas for all subsequent shape operations.

## Step 2: Insert a GroupShape container

```java
        // Step 2: Insert a GroupShape container that will hold multiple shapes
        GroupShape groupShape = builder.insertGroupShape();
```

A `GroupShape` works like a **folder** for drawing objects. When you move, rotate, or delete the group, all child shapes follow automatically. This is the core of **group shapes in word**.

## Step 3: Add a rectangle shape – the rectangle shape code

```java
        // Step 3: Create a rectangle, set its size, and add it to the group
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // set shape width in points
        rectangleShape.setHeight(50);   // set shape height in points
        groupShape.appendChild(rectangleShape);
```

- **add rectangle shape** – Ο κατασκευαστής `Shape` λαμβάνει `ShapeType.RECTANGLE`, το οποίο λέει στην Aspose.Words να αποδώσει ένα ορθογώνιο περίγραμμα.  
- **set shape size** – `setWidth` και `setHeight` ορίζουν τις **διαστάσεις του σχήματος** σε πόντους (1 pt = 1/72 in). Αυτός είναι ο πιο συνηθισμένος τρόπος ελέγχου του οπτικού μεγέθους.  
- **Why we use `appendChild`** – Συνδέει το ορθογώνιο με το `GroupShape` ώστε να κινείται μαζί με την ομάδα.

## Step 4: Add an ellipse and position it inside the group

```java
        // Step 4: Create an ellipse, set its size and position inside the group, then add it
        Shape ellipseShape = new Shape(document, ShapeType.ELLIPSE);
        ellipseShape.setWidth(80);      // set shape width
        ellipseShape.setHeight(80);     // set shape height (making it a circle)
        ellipseShape.setLeft(120);      // position relative to the group container
        groupShape.appendChild(ellipseShape);
```

The ellipse demonstrates **set shape dimensions** beyond a simple rectangle. By calling `setLeft`, we control the horizontal offset inside the group, which is useful when arranging multiple objects.

## Step 5: Save the document

```java
        // Step 5: Save the document with the grouped shapes
        document.save("GroupShapeDemo.docx");
    }
}
```

When you open *GroupShapeDemo.docx* in Microsoft Word, you’ll see a rectangle and an ellipse locked together inside a single group. Selecting either shape will select the entire group—exactly what you expect when **group shapes in word**.

## Full, runnable example

Putting all pieces together, here is the complete source file you can copy into your IDE:

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a GroupShape that will hold the rectangle and ellipse
        GroupShape groupShape = builder.insertGroupShape();

        // Add a rectangle (add rectangle shape) and define its size (set shape size)
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // width in points
        rectangleShape.setHeight(50);   // height in points
        groupShape.appendChild(rectangleShape);

        // Add an ellipse, set its dimensions, and position it inside the group
        Shape ellipseShape = new Shape(document, ShapeType.ELLIPSE);
        ellipseShape.setWidth(80);
        ellipseShape.setHeight(80);
        ellipseShape.setLeft(120);      // horizontal offset relative to the group
        groupShape.appendChild(ellipseShape);

        // Save the document to the local file system
        document.save("GroupShapeDemo.docx");
    }
}
```

### Expected output

- Ένα αρχείο με όνομα **GroupShapeDemo.docx** εμφανίζεται στο φάκελο του έργου.  
- Ανοίγοντας το αρχείο στο Word εμφανίζει δύο σχήματα (ένα ορθογώνιο και μια έλλειψη) που είναι ομαδοποιημένα μαζί.  
- Σέρνοντας οποιοδήποτε σχήμα μετακινεί ολόκληρη την ομάδα, επιβεβαιώνοντας ότι η **group shapes in word** λειτουργεί όπως αναμένεται.

## Common variations and edge cases

| Σενάριο | Τι να αλλάξετε | Αιτία |
|----------|----------------|-----|
| **Διαφορετικοί τύποι σχήματος** (π.χ., τρίγωνο) | Χρησιμοποιήστε `ShapeType.TRIANGLE` ή οποιαδήποτε άλλη τιμή enum κατά την κατασκευή του `Shape`. | Σας επιτρέπει να δημιουργήσετε πιο σύνθετα διαγράμματα. |
| **Ορισμός χρώματος γεμίσματος** | Καλέστε `shape.getFillColor().setColor(Color.BLUE);` μετά τη δημιουργία του σχήματος. | Βελτιώνει την οπτική εμφάνιση χωρίς να επηρεάζει την ομαδοποίηση. |
| **Περιστροφή της ομάδας** | `groupShape.setRotationAngle(45);` | Περιστρέφει όλα τα παιδικά σχήματα μαζί, χρήσιμο για εικονίδια. |
| **Προσθήκη κειμένου μέσα σε σχήμα** | `shape.appendChild(new Paragraph(document));` then add a `Run` with text. | Κάνει το σχήμα να λειτουργεί ως ετικέτα ή κλήση. |
| **Αποθήκευση σε ροή** | `ByteArrayOutputStream out = new ByteArrayOutputStream(); document.save(out, SaveFormat.DOCX);` | Χρήσιμο για υπηρεσίες web που επιστρέφουν το έγγραφο άμεσα. |

### Pro tip

When you need to **set shape dimensions** based on dynamic data (e.g., a barcode length), calculate the width/height in points first:

```java
double inches = 2.5;
int points = (int)(inches * 72); // 1 inch = 72 points
shape.setWidth(points);
```

## Conclusion

You now know how to **group shapes in Word** using Java, how to **add rectangle shape**, and how to **set shape size** and **set shape dimensions** with concise, production‑ready code. By following the steps above, you can create reusable graphic groups, embed them in automated reports, or build custom diagramming tools without ever opening Word manually.

### What’s next?

- Εξερευνήστε παραλλαγές του **add rectangle shape** όπως στρογγυλεμένες γωνίες (`ShapeType.RECTANGLE` με `setCornerRadius`).  
- Συνδυάστε **group shapes in word** με πίνακες ή γραφήματα για πιο πλούσια έγγραφα.  
- Δείτε το API της Aspose.Words για **text wrapping** (`shape.setWrapType(WrapType.SQUARE)`) ώστε να ελέγχετε πώς το κείμενο γύρω αλληλεπιδρά με τα ομαδοποιημένα γραφικά σας.

Feel free to experiment, adapt the **rectangle shape code**, and share your results

## What Should You Learn Next?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Δημιουργία Εγγράφου Word Java – Προσθήκη Σχήματος Ορθογωνίου με Εφέ Σκιάς](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Δημιουργία σχήματος ορθογωνίου στο Word με Java – Πλήρης Οδηγός](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Δημιουργία Ομαδικού Σχήματος σε Έγγραφο Word Χρησιμοποιώντας Aspose.Words για .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}