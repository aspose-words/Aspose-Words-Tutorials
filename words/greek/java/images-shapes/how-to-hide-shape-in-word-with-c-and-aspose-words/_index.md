---
category: general
date: 2026-09-11
description: Μάθετε πώς να κρύψετε σχήμα στο Word χρησιμοποιώντας C#. Αυτός ο οδηγός
  δείχνει επίσης πώς να εισάγετε σχήμα ορθογωνίου και πώς να εισάγετε σχήμα σε έγγραφο
  Word με το Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape in word
- insert rectangle shape
- insert shape into word document
language: el
lastmod: 2026-09-11
og_description: Πώς να κρύψετε σχήμα στο Word χρησιμοποιώντας C# και Aspose.Words.
  Ακολουθήστε τον βήμα‑βήμα οδηγό για να εισάγετε ορθογώνιο σχήμα και να διαχειριστείτε
  τα σχήματα σε ένα έγγραφο Word.
og_image_alt: Screenshot showing how to hide shape in Word document using C#
og_title: Πώς να κρύψετε σχήμα στο Word – πλήρης οδηγός C#
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  headline: How to hide shape in Word with C# and Aspose.Words
  type: TechArticle
- description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  name: How to hide shape in Word with C# and Aspose.Words
  steps:
  - name: Explanation of each step
    text: 1. **Create a new document** – `Document` represents the Word file in memory.
      `DocumentBuilder` provides a fluent API for inserting content. 2. **Insert rectangle
      shape** – `InsertShape` creates a drawing object of type `Rectangle`. The dimensions
      are expressed in points (1 pt ≈ 1/72 in). This satis
  - name: Expected result
    text: 'Open `output.docx` in Microsoft Word:'
  - name: Manually adding the hidden attribute (fallback)
    text: '```csharp // Fallback for Aspose.Words versions prior to 24.10 Shape shape
      = builder.InsertShape(ShapeType.Rectangle, 100, 50); shape.FillColor = System.Drawing.Color.LightGray;'
  type: HowTo
- questions:
  - answer: No. Hidden shapes are ignored by the layout engine, so they do not consume
      space. This is useful for placeholder content that should not affect page breaks.
    question: Does hiding a shape affect pagination?
  - answer: Yes. The same `Hidden` property works on shapes located anywhere in the
      document tree, including headers, footers, and even inside tables.
    question: Can I hide a shape that is part of a header or footer?
  - answer: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection
      and set `Hidden = true` for each target shape. ```csharp foreach (Shape s in
      doc.GetChildNodes(NodeType.Shape, true)) { if (s.ShapeType == ShapeType.Rectangle)
      s.Hidden = true; } ```
    question: What if I need to hide multiple shapes at once?
  - answer: 'When converting to PDF, hidden shapes are omitted by default, matching
      Word’s rendering behavior. If you need them in the PDF, you must unhide them
      before conversion. ## Tips and pitfalls * **Pro tip:** Set `shape.WrapType =
      WrapType.None` before hiding if you later plan to unhide the shape without '
    question: Is the hidden attribute preserved when converting to PDF?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Word automation
title: Πώς να κρύψετε σχήμα στο Word με C# και Aspose.Words
url: /el/java/images-shapes/how-to-hide-shape-in-word-with-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να κρύψετε σχήμα στο Word με C# και Aspose.Words

Εάν χρειάζεστε να κρύψετε ένα σχήμα στο Word ενώ διατηρείτε το σχήμα στη δομή του εγγράφου, αυτό το tutorial σας δείχνει ακριβώς πώς. Χρησιμοποιώντας το Aspose.Words για .NET μπορείτε να εισάγετε ένα σχήμα ορθογωνίου, να το κρύψετε και να διατηρήσετε τη θέση του για μετέπειτα επεξεργασία.

Η αυτοματοποίηση του Word συχνά απαιτεί λεπτομερή έλεγχο των σχημάτων—είτε δημιουργείτε πρότυπα, ετοιμάζετε εκθέσεις ή χτίζετε μια υπηρεσία επεξεργασίας εγγράφων. Στο τέλος αυτού του οδηγού θα μπορείτε να:

* Εισάγετε ένα σχήμα ορθογωνίου σε ένα έγγραφο Word (`insert rectangle shape`).
* Κρύψετε οποιοδήποτε σχήμα χωρίς να το διαγράψετε (`how to hide shape in word`).
* Αποθηκεύσετε το αποτέλεσμα και να επαληθεύσετε ότι το κρυμμένο σχήμα δεν εμφανίζεται στην αποδοθείσα προβολή (`insert shape into word document`).

Το παράδειγμα λειτουργεί με Aspose.Words 24.10 ή νεότερη έκδοση και στοχεύει .NET 6.0+, αλλά οι έννοιες ισχύουν και για παλαιότερες εκδόσεις.

## Προαπαιτούμενα

* **Aspose.Words for .NET** ≥ 24.10. Μπορείτε να αποκτήσετε δωρεάν προσωρινή άδεια από την ιστοσελίδα της Aspose.
* **.NET SDK** 6.0 ή νεότερο εγκατεστημένο στον υπολογιστή σας.
* Περιβάλλον ανάπτυξης όπως Visual Studio 2022, VS Code ή Rider.
* Βασική εξοικείωση με C# και την έννοια του Word Open XML (προαιρετικό αλλά χρήσιμο).

## Πώς να κρύψετε σχήμα στο Word με Aspose.Words

Παρακάτω υπάρχει ένα πλήρες, εκτελέσιμο πρόγραμμα που δείχνει ολόκληρη τη ροή εργασίας—από τη δημιουργία ενός εγγράφου μέχρι την εισαγωγή ενός σχήματος ορθογωνίου και, τέλος, την απόκρυψή του.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HideShapeDemo
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a rectangle shape (100 × 50 points) at the current cursor position.
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        // Optional: give the shape a visible fill so you can see it before hiding.
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Hide the shape without removing it from the document.
        // The Hidden property is available starting with Aspose.Words 24.10.
        rectangle.Hidden = true;

        // Step 4: Save the document to disk.
        string outputPath = "output.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}. The rectangle shape is hidden.");
    }
}
```

### Επεξήγηση κάθε βήματος

1. **Δημιουργία νέου εγγράφου** – Το `Document` αντιπροσωπεύει το αρχείο Word στη μνήμη. Το `DocumentBuilder` παρέχει ένα ευέλικτο API για την εισαγωγή περιεχομένου.
2. **Εισαγωγή σχήματος ορθογωνίου** – Η `InsertShape` δημιουργεί ένα αντικείμενο σχεδίασης τύπου `Rectangle`. Οι διαστάσεις εκφράζονται σε σημεία (1 pt ≈ 1/72 in). Αυτό ικανοποιεί την απαίτηση `insert rectangle shape`.
3. **Απόκρυψη του σχήματος** – Ορίζοντας `Shape.Hidden = true` σηματοδοτεί το σχήμα ως κρυφό στο markup του Word (`<w:hidden/>`). Το σχήμα παραμένει μέρος του δέντρου του εγγράφου, ώστε να μπορείτε αργότερα να το εμφανίσετε ξανά ή να το αναφερθείτε προγραμματιστικά. Αυτό είναι το κύριο στοιχείο του `how to hide shape in word`.
4. **Αποθήκευση του αρχείου** – Το έγγραφο γράφεται στο `output.docx`. Όταν ανοίξει στο Microsoft Word, το ορθογώνιο δεν θα είναι ορατό, αλλά εξακολουθεί να υπάρχει στο XML και μπορεί να εξεταστεί με έναν προβολέα ZIP ή το Open XML SDK.

### Αναμενόμενο αποτέλεσμα

Ανοίξτε το `output.docx` στο Microsoft Word:

* Το έγγραφο φαίνεται κενό—κανένα ορατό σχήμα.
* Εάν ελέγξετε το υποκείμενο XML (`word/document.xml`) θα βρείτε ένα στοιχείο `<w:pict>` με χαρακτηριστικό `<w:hidden/>`, επιβεβαιώνοντας ότι το σχήμα υπάρχει αλλά είναι κρυφό.

```xml
<w:pict>
  <v:shape id="Shape0" style="position:absolute; ...">
    <v:fillcolor>#ADD8E6</v:fillcolor>
    <w:hidden/>
  </v:shape>
</w:pict>
```

Το κρυμμένο σχήμα μπορεί να γίνει ξανά ορατό ορίζοντας `Hidden = false` και αποθηκεύοντας ξανά το έγγραφο.

## Εισαγωγή σχήματος ορθογωνίου σε έγγραφο Word

Αν και ο κύριος στόχος είναι η απόκρυψη ενός σχήματος, πολλές περιπτώσεις ξεκινούν με την εισαγωγή σχήματος πρώτα. Η μέθοδος `InsertShape` υποστηρίζει πολλές τιμές `ShapeType`, όπως `Rectangle`, `Ellipse`, `Line` και προσαρμοσμένες εικόνες.

```csharp
// Example: Insert an ellipse shape and keep it visible.
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
ellipse.FillColor = System.Drawing.Color.Pink;
```

**Γιατί να χρησιμοποιήσετε ορθογώνιο;**  
Ένα ορθογώνιο παρέχει ένα καθαρό, άξονες‑ευθυγραμμισμένο κοντέινερ που μπορεί να περιέχει κείμενο, εικόνες ή άλλα ενσωματωμένα σχήματα. Συχνά χρησιμοποιείται ως placeholder για δυναμικό περιεχόμενο όπως πίνακες ή διαγράμματα. Εισάγοντας πρώτα το ορθογώνιο, διατηρείτε τη συνοχή της διάταξης ακόμη και μετά την απόκρυψή του.

## Εισαγωγή σχήματος σε έγγραφο Word – βέλτιστες πρακτικές

Όταν `insert shape into word document`, λάβετε υπόψη τα εξής:

* **Ορίστε ρητές διαστάσεις** – Αποφύγετε την εξάρτηση από αυτόματο μέγεθος· καθορίστε πλάτος και ύψος σε σημεία για συνεπή διάταξη σε όλες τις πλατφόρμες.
* **Ορίστε τοποθέτηση** – Από προεπιλογή το σχήμα αγκυροβολείται στην τρέχουσα παράγραφο. Χρησιμοποιήστε `builder.MoveTo` ή `builder.StartBookmark` για ακριβή τοποθέτηση.
* **Εφαρμόστε στυλ νωρίς** – Το χρώμα γεμίσματος, το στυλ γραμμής και η αναδίπλωση κειμένου επηρεάζουν την τελική εμφάνιση. Ακόμη και τα κρυμμένα σχήματα ωφελούνται από σωστό στυλ, επειδή το markup παραμένει αμετάβλητο.
* **Συμβατότητα εκδόσεων** – Η ιδιότητα `Hidden` είναι διαθέσιμη μόνο από το Aspose.Words 24.10 και μετά. Εάν στοχεύετε παλαιότερη έκδοση, μπορείτε να προσθέσετε χειροκίνητα το χαρακτηριστικό `<w:hidden/>` χρησιμοποιώντας το API `Node`.

### Χειροκίνητη προσθήκη του χαρακτηριστικού hidden (εναλλακτική)

```csharp
// Fallback for Aspose.Words versions prior to 24.10
Shape shape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
shape.FillColor = System.Drawing.Color.LightGray;

// Access the underlying OpenXml node.
var shapeNode = shape.GetChildNodes(NodeType.Any, true)[0];
shapeNode.GetAttributes().Add("w:hidden", "true");
```

## Πλήρες παράδειγμα από‑από‑από

Συνδυάζοντας όλα τα παραπάνω, παρακάτω υπάρχει ένα ενιαίο πρόγραμμα που:

1. Εισάγει ένα σχήμα ορθογωνίου.
2. Κρύβει το σχήμα.
3. Εισάγει μια ορατή έλλειψη για αντίθεση.
4. Αποθηκεύει το έγγραφο.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class FullDemo
{
    static void Main()
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert and hide a rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 120, 60);
        rect.FillColor = System.Drawing.Color.LightGreen;
        rect.Hidden = true; // core of how to hide shape in word

        // Insert a visible ellipse to show the difference.
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.FillColor = System.Drawing.Color.Coral;

        // Save the output.
        string filePath = "demo_output.docx";
        doc.Save(filePath);
        Console.WriteLine($"Demo document saved to {filePath}");
    }
}
```

Η εκτέλεση του προγράμματος παράγει το `demo_output.docx`. Όταν ανοίξει, θα δείτε μόνο την κοραλίδα έλλειψη· το πράσινο ορθογώνιο υπάρχει στο XML αλλά είναι κρυφό από την προβολή.

## Συχνές ερωτήσεις και ειδικές περιπτώσεις

**Ε: Επηρεάζει η απόκρυψη ενός σχήματος την σελιδοποίηση;**  
Α: Όχι. Τα κρυμμένα σχήματα αγνοούνται από τη μηχανή διάταξης, επομένως δεν καταναλώνουν χώρο. Αυτό είναι χρήσιμο για placeholders που δεν πρέπει να επηρεάζουν τις αλλαγές σελίδας.

**Ε: Μπορώ να κρύψω σχήμα που βρίσκεται σε κεφαλίδα ή υποσέλιδο;**  
Α: Ναι. Η ίδια ιδιότητα `Hidden` λειτουργεί σε σχήματα οπουδήποτε στο δέντρο του εγγράφου, συμπεριλαμβανομένων κεφαλίδων, υποσέλιδων και ακόμη και μέσα σε πίνακες.

**Ε: Πώς κρύβω πολλαπλά σχήματα ταυτόχρονα;**  
Α: Επανάληψη πάνω στη συλλογή `Document.GetChildNodes(NodeType.Shape, true)` και ορισμός `Hidden = true` για κάθε σχήμα-στόχο.

```csharp
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.ShapeType == ShapeType.Rectangle)
        s.Hidden = true;
}
```

**Ε: Διατηρείται το χαρακτηριστικό hidden κατά τη μετατροπή σε PDF;**  
Α: Κατά τη μετατροπή σε PDF, τα κρυμμένα σχήματα παραλείπονται εξ ορισμού, όπως συμβαίνει και στην απόδοση του Word. Εάν χρειάζεστε τα σχήματα στο PDF, πρέπει να τα εμφανίσετε ξανά πριν από τη μετατροπή.

## Συμβουλές και παγίδες

* **Pro tip:** Ορίστε `shape.WrapType = WrapType.None` πριν την απόκρυψη εάν σκοπεύετε να εμφανίσετε ξανά το σχήμα χωρίς να διαταράξετε το γύρω κείμενο.
* **Προσοχή σε παλαιότερες εκδόσεις Aspose.Words:** Η ιδιότητα `Hidden` προκαλεί `NotSupportedException` πριν από την 24.10. Σε αυτήν την περίπτωση χρησιμοποιήστε την χειροκίνητη προσέγγιση XML.
* **Δοκιμή:** Πάντα ανοίξτε το παραγόμενο `.docx` στο Word και χρησιμοποιήστε την επιλογή “Show XML markup” (καρτέλα Developer) για να επαληθεύσετε ότι υπάρχει το χαρακτηριστικό `<w:hidden/>`.

## Συμπέρασμα

Τώρα γνωρίζετε πώς να κρύψετε σχήμα στο Word χρησιμοποιώντας C# και Aspose.Words, καθώς και πώς να εισάγετε σχήμα ορθογωνίου και να το εισάγετε σε έγγραφο Word με πλήρη έλεγχο της ορατότητας. Εκμεταλλευόμενοι την ιδιότητα `Hidden`, μπορείτε να διατηρήσετε σχήματα στο μοντέλο του εγγράφου για μετέπειτα επεξεργασία, ενώ παρουσιάζετε μια καθαρή προβολή στους τελικούς χρήστες.

Στη συνέχεια, εξερευνήστε σχετικά θέματα όπως **ενημέρωση ιδιοτήτων σχήματος σε χρόνο εκτέλεσης**, **μετατροπή κρυμμένων σχημάτων σε εικόνες**, ή **χρήση του Open XML SDK για άμεση διαχείριση κρυμμένων στοιχείων**. Αυτές οι επεκτάσεις θα εμβαθύνουν

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στην υλοποίηση των δικών σας έργων.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}