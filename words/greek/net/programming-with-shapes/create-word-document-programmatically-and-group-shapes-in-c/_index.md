---
category: general
date: 2026-08-10
description: Δημιουργήστε έγγραφο Word προγραμματιστικά χρησιμοποιώντας το Aspose.Words,
  μάθετε πώς να ομαδοποιείτε πολλαπλά σχήματα στο Word, προσθέστε ορθογώνιο στο Word
  και δημιουργήστε μια ομαδοποιημένη μορφή σε C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- group multiple shapes word
- add rectangle to word
- how to create group shape
language: el
lastmod: 2026-08-10
og_description: Δημιουργήστε έγγραφο Word προγραμματιστικά με το Aspose.Words. Αυτός
  ο οδηγός σας δείχνει πώς να ομαδοποιήσετε πολλαπλά σχήματα στο Word, να προσθέσετε
  ορθογώνιο στο Word και να ενσωματώσετε έναν έλεγχο περιεχομένου απλού κειμένου,
  όλα σε C#.
og_image_alt: Screenshot of a Word file showing a grouped rectangle and ellipse with
  a plain‑text content control
og_title: Δημιουργία εγγράφου Word προγραμματιστικά – ομαδοποίηση σχημάτων σε C#
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  headline: Create word document programmatically and group shapes in C#
  type: TechArticle
- description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  name: Create word document programmatically and group shapes in C#
  steps:
  - name: – Initialize the document and builder
    text: The `Document` object represents the entire DOCX file, while `DocumentBuilder`
      provides a convenient API to add content. Initializing them is the first requirement
      whenever you **create word document programmatically**.
  - name: – Create a group shape container
    text: A `Shape` with `ShapeType.Group` acts as a canvas that can hold other shapes.
      Setting `Width` and `Height` defines the bounding box for the group. This is
      the core of **how to create group shape** in Aspose.Words.
  - name: – Add a rectangle to word
    text: A rectangle is created with `ShapeType.Rectangle`. Its `Left` and `Top`
      properties position it relative to the group’s origin. This step demonstrates
      **add rectangle to word** and shows how you can control exact placement.
  - name: – Add an ellipse (circle) to the group
    text: An ellipse is added the same way as the rectangle, but with `ShapeType.Ellipse`.
      The `Left = 210` moves it to the right of the rectangle, creating a visually
      distinct pair of shapes inside the same group.
  - name: – Insert the completed group shape into the document
    text: '`builder.InsertNode(groupShape)` places the whole group at the current
      cursor location. Because the group already contains its children, you do not
      need additional insert calls for the rectangle or ellipse.'
  - name: – Create a plain‑text StructuredDocumentTag (SDT)
    text: A StructuredDocumentTag is a content control that end users can fill in
      when the document is opened in Word. Setting `Title = "CustomerName"` gives
      the control a meaningful identifier, which is useful for later data extraction.
  - name: – Save the document
    text: '`doc.Save("GroupAndSDT.docx")` writes the file to disk. The resulting DOCX
      contains the grouped shapes and the SDT. Opening the file in Microsoft Word
      will show a rectangle next to a circle, both selectable as a single object,
      followed by a placeholder “Enter name here …”.'
  - name: Using different shape types
    text: You can replace `ShapeType.Rectangle` or `ShapeType.Ellipse` with any other
      `ShapeType` (e.g., `ShapeType.Polygon`, `ShapeType.Line`). The grouping logic
      remains identical.
  - name: Setting fill color and borders
    text: '```csharp rectangleShape.FillColor = System.Drawing.Color.LightBlue; rectangleShape.StrokeColor
      = System.Drawing.Color.DarkBlue; ellipseShape.FillColor = System.Drawing.Color.LightCoral;
      ``` Adding fill and stroke improves visual distinction, especially when the
      document is shared with non‑technical'
  - name: Rotating the entire group
    text: '```csharp groupShape.Rotation = 45; // rotates both shapes together ```
      Rotating the group is more efficient than rotating each child individually.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: Δημιουργία εγγράφου Word προγραμματιστικά και ομαδοποίηση σχημάτων σε C#
url: /el/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία εγγράφου Word προγραμματιστικά και ομαδοποίηση σχημάτων σε C#

Αν χρειάζεστε να **δημιουργήσετε έγγραφο Word προγραμματιστικά**, αυτό το tutorial σας δείχνει πώς να δημιουργήσετε ένα αρχείο DOCX με το Aspose.Words και να **ομαδοποιήσετε πολλαπλά σχήματα στο Word** μαζί. Θα καλύψουμε επίσης **προσθήκη ορθογωνίου στο Word** και **πώς να δημιουργήσετε ομαδικό σχήμα** που περιέχει τόσο ένα ορθογώνιο όσο και μια έλλειψη, συν ένα StructuredDocumentTag απλού κειμένου για είσοδο χρήστη.

Θα ολοκληρώσετε με ένα έτοιμο προς χρήση αρχείο Word που περιέχει ένα ομαδοποιημένο σχήμα ορθογωνίου‑έλλειψης και έναν έλεγχο περιεχομένου όπου ο χρήστης μπορεί να πληκτρολογήσει ένα όνομα. Δεν απαιτείται χειροκίνητη επεξεργασία στο Word μετά την εκτέλεση του κώδικα.

## Τι θα χρειαστείτε

- .NET 6.0 ή νεότερο (το παράδειγμα στοχεύει στο .NET 6, αλλά οποιαδήποτε πρόσφατη έκδοση του .NET λειτουργεί)
- Άδεια Aspose.Words for .NET (η δωρεάν δοκιμή λειτουργεί για δοκιμές)
- Visual Studio 2022 ή οποιοδήποτε IDE C# προτιμάτε
- Βασική εξοικείωση με τη σύνταξη C#

## Δημιουργία εγγράφου Word προγραμματιστικά – συνολική ροή εργασίας

Η διαδικασία αποτελείται από τρία λογικά στάδια:

1. **Initialize** ένα `Document` και ένα `DocumentBuilder` – το θεμέλιο για οποιοδήποτε αρχείο Word δημιουργείτε.
2. **Build a group shape** που περιέχει ένα ορθογώνιο και μια έλλειψη – δείχνει **group multiple shapes word** και **how to create group shape**.
3. **Insert a StructuredDocumentTag (SDT)** – ένας έλεγχος περιεχομένου απλού κειμένου που επιτρέπει στους τελικούς χρήστες να συμπληρώσουν δεδομένα, απεικονίζοντας **add rectangle to word** ως μέρος της συνολικής διάταξης του εγγράφου.

Παρακάτω βρίσκεται ο πλήρης, εκτελέσιμος κώδικας, ακολουθούμενος από ανάλυση βήμα προς βήμα.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1 – Initialize the document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2 – Create a group shape container
            Shape groupShape = new Shape(doc, ShapeType.Group)
            {
                Width = 400,
                Height = 200
            };

            // Step 3 – Add a rectangle to the group
            Shape rectangleShape = new Shape(doc, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100,
                Left = 0,
                Top = 0
            };
            groupShape.GroupShape.AddChild(rectangleShape);

            // Step 4 – Add an ellipse (circle) to the group
            Shape ellipseShape = new Shape(doc, ShapeType.Ellipse)
            {
                Width = 100,
                Height = 100,
                Left = 210, // Position next to the rectangle
                Top = 0
            };
            groupShape.GroupShape.AddChild(ellipseShape);

            // Step 5 – Insert the completed group shape into the document
            builder.InsertNode(groupShape);

            // Step 6 – Create a plain‑text StructuredDocumentTag for user input
            StructuredDocumentTag sdtTag = new StructuredDocumentTag(
                doc,
                SdtType.PlainText,
                MarkupLevel.Block)
            {
                Title = "CustomerName"
            };
            builder.InsertNode(sdtTag);
            builder.Writeln("Enter name here …");

            // Step 7 – Save the document
            doc.Save("GroupAndSDT.docx");
            Console.WriteLine("Document created successfully.");
        }
    }
}
```

### Βήμα 1 – Αρχικοποίηση του εγγράφου και του builder
Το αντικείμενο `Document` αντιπροσωπεύει ολόκληρο το αρχείο DOCX, ενώ το `DocumentBuilder` παρέχει ένα βολικό API για την προσθήκη περιεχομένου. Η αρχικοποίησή τους είναι η πρώτη απαίτηση όποτε **δημιουργείτε έγγραφο Word προγραμματιστικά**.

> **Συμβουλή:** Εάν σκοπεύετε να επαναχρησιμοποιήσετε το ίδιο έγγραφο σε πολλές λειτουργίες, διατηρήστε μια μόνο παρουσία του `DocumentBuilder` για να αποφύγετε περιττή δημιουργία αντικειμένων.

### Βήμα 2 – Δημιουργία κοντέινερ ομαδικού σχήματος
Ένα `Shape` με `ShapeType.Group` λειτουργεί ως καμβάς που μπορεί να περιέχει άλλα σχήματα. Ορίζοντας `Width` και `Height` καθορίζει το πλαίσιο περιβάλλοντος για την ομάδα. Αυτό είναι ο πυρήνας του **how to create group shape** στο Aspose.Words.

> **Ακρόατο σενάριο:** Εάν το πλάτος της ομάδας είναι μικρότερο από το συνολικό πλάτος των παιδιών της, τα παιδιά θα περικοπούν. Φροντίστε πάντα η ομάδα να είναι αρκετά μεγάλη ώστε να περιέχει κάθε σχήμα παιδί.

### Βήμα 3 – Προσθήκη ορθογωνίου στο Word
Ένα ορθογώνιο δημιουργείται με `ShapeType.Rectangle`. Οι ιδιότητες `Left` και `Top` το τοποθετούν σε σχέση με το αρχικό σημείο της ομάδας. Αυτό το βήμα δείχνει **add rectangle to word** και δείχνει πώς μπορείτε να ελέγξετε την ακριβή θέση.

> **Κοινό λάθος:** Η παράλειψη ορισμού των `Left`/`Top` οδηγεί στο ορθογώνιο να εμφανίζεται στο προεπιλεγμένο αρχικό σημείο της ομάδας (0,0), το οποίο μπορεί να επικαλύψει άλλα παιδιά.

### Βήμα 4 – Προσθήκη έλλειψης (κύκλου) στην ομάδα
Μια έλλειψη προστίθεται με τον ίδιο τρόπο όπως το ορθογώνιο, αλλά με `ShapeType.Ellipse`. Η τιμή `Left = 210` τη μετακινεί δεξιά του ορθογωνίου, δημιουργώντας ένα οπτικά διακριτό ζεύγος σχημάτων μέσα στην ίδια ομάδα.

> **Γιατί να χρησιμοποιήσετε ομάδα;** Η ομαδοποίηση σας επιτρέπει να μετακινήσετε, περιστρέψετε ή αλλάξετε το μέγεθος και των δύο σχημάτων μαζί με μια μόνο ενέργεια αργότερα, διατηρώντας τη σχετική τους διάταξη.

### Βήμα 5 – Εισαγωγή του ολοκληρωμένου ομαδικού σχήματος στο έγγραφο
`builder.InsertNode(groupShape)` τοποθετεί ολόκληρη την ομάδα στην τρέχουσα θέση του δρομέα. Επειδή η ομάδα περιέχει ήδη τα παιδιά της, δεν χρειάζονται πρόσθετες κλήσεις εισαγωγής για το ορθογώνιο ή την έλλειψη.

### Βήμα 6 – Δημιουργία StructuredDocumentTag (SDT) απλού κειμένου
Ένα StructuredDocumentTag είναι ένας έλεγχος περιεχομένου που οι τελικοί χρήστες μπορούν να συμπληρώσουν όταν το έγγραφο ανοίγει στο Word. Ορίζοντας `Title = "CustomerName"` δίνει στον έλεγχο ένα σημασιολογικό αναγνωριστικό, χρήσιμο για μετέπειτα εξαγωγή δεδομένων.

> **Γιατί ένα SDT απλού κειμένου;** Περιορίζει την εισαγωγή σε απλό κείμενο, αποτρέποντας τυχαία μορφοποίηση που θα μπορούσε να διακόψει την επεξεργασία downstream.

### Βήμα 7 – Αποθήκευση του εγγράφου
`doc.Save("GroupAndSDT.docx")` γράφει το αρχείο στο δίσκο. Το προκύπτον DOCX περιέχει τα ομαδοποιημένα σχήματα και το SDT. Ανοίγοντας το αρχείο στο Microsoft Word θα εμφανιστεί ένα ορθογώνιο δίπλα σε έναν κύκλο, και τα δύο επιλέξιμα ως ένα ενιαίο αντικείμενο, ακολουθούμενο από ένα placeholder “Enter name here …”.

#### Αναμενόμενο αποτέλεσμα
- Ένα αρχείο με όνομα **GroupAndSDT.docx** στον φάκελο εκτέλεσης.
- Στο Word: ένα ομαδοποιημένο σχήμα (ορθογώνιο + έλλειψη) που μπορείτε να μετακινήσετε ως μία μονάδα.
- Ακριβώς κάτω από την ομάδα, ένας γκρι-σκιασμένος έλεγχος περιεχομένου που ζητά από τον χρήστη να πληκτρολογήσει ένα όνομα.

## Πρόσθετες παραλλαγές και βέλτιστες πρακτικές

### Χρήση διαφορετικών τύπων σχημάτων
Μπορείτε να αντικαταστήσετε το `ShapeType.Rectangle` ή το `ShapeType.Ellipse` με οποιονδήποτε άλλο `ShapeType` (π.χ., `ShapeType.Polygon`, `ShapeType.Line`). Η λογική ομαδοποίησης παραμένει η ίδια.

### Ορισμός χρώματος γεμίσματος και περιγραμμάτων
```csharp
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```
Η προσθήκη γεμίσματος και περιγράμματος βελτιώνει την οπτική διάκριση, ειδικά όταν το έγγραφο μοιράζεται με μη‑τεχνικούς ενδιαφερόμενους.

### Περιστροφή ολόκληρης της ομάδας
```csharp
groupShape.Rotation = 45; // rotates both shapes together
```
Η περιστροφή της ομάδας είναι πιο αποδοτική από την περιστροφή κάθε παιδιού ξεχωριστά.

### Εξαγωγή σε PDF
Εάν χρειάζεστε μια έκδοση PDF, απλώς καλέστε:
```csharp
doc.Save("GroupAndSDT.pdf", SaveFormat.Pdf);
```
Όλα τα ομαδοποιημένα σχήματα και το SDT (απεικονιζόμενο ως πεδίο κειμένου) θα εμφανιστούν στο PDF.

## Συνηθισμένα προβλήματα και πώς να τα αποφύγετε

| Σύμπτωμα | Αιτία | Διόρθωση |
|----------|-------|----------|

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Δημιουργία ομαδικού σχήματος σε έγγραφο Word χρησιμοποιώντας Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Δημιουργία σχήματος ορθογωνίου σε Word με C# – Οδηγός βήμα‑βήμα](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Δημιουργία κενής εγγράφου Word με σχήμα ορθογωνίου με σκιά – Οδηγός βήμα‑βήμα](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}