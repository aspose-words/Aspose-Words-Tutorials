---
category: general
date: 2026-08-07
description: Εισαγωγή σχήματος ορθογωνίου σε C# χρησιμοποιώντας το Aspose.Words και
  μάθετε πώς να κρύβετε το σχήμα, να ορίζετε το χρώμα γεμίσματος και να προσθέτετε
  σχήμα ορθογωνίου σε έγγραφο Word αποδοτικά.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- how to insert shape
- how to set fill color
- add rectangle shape
language: el
lastmod: 2026-08-07
og_description: Εισαγωγή σχήματος ορθογωνίου σε έγγραφο Word με C#. Μάθετε πώς να
  κρύψετε το σχήμα, να ορίσετε χρώμα γεμίσματος και να προσθέσετε σχήμα ορθογωνίου
  χρησιμοποιώντας το Aspose.Words.
og_image_alt: Screenshot showing a hidden yellow rectangle shape inserted into a Word
  document
og_title: Εισαγωγή σχήματος ορθογωνίου σε C# – πλήρης οδηγός Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  headline: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  name: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  steps:
  - name: What each step does
    text: '| Step | Reason | |------|--------| | **Create a new document** | Provides
      a clean canvas; you can also load an existing .docx by passing a file path to
      `new Document(path)`. | | **Initialize DocumentBuilder** | `DocumentBuilder`
      is the high‑level helper that lets you insert text, tables, and shapes'
  - name: 1. Making the shape visible again
    text: 'If a later part of your workflow needs to reveal the hidden rectangle,
      you can toggle the flag:'
  - name: 2. Adding a border (stroke)
    text: 'A hidden shape can still have a visible border when you decide to show
      it. Set the `LineColor` and `LineWidth` properties:'
  - name: 3. Positioning the rectangle absolutely
    text: 'For precise layout control, switch the shape’s `WrapType` to `WrapType.Inline`
      (default) or `WrapType.TopBottom` and adjust `Left`/`Top` properties:'
  - name: 4. Using a different measurement unit
    text: 'Aspose.Words works in points (1 pt = 1/72 inch). If you prefer centimeters,
      convert first:'
  - name: Next steps
    text: '* Explore **how to insert shape** inside tables or headers/footers for
      watermarks. * Combine **add rectangle shape** with content controls to create
      dynamic placeholders. * Review Aspose.Words’ **shape manipulation** API for
      advanced features like rotation, gradient fills, and SVG import.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
- document generation
title: Εισαγωγή σχήματος ορθογωνίου σε C# με το Aspose.Words – βήμα‑βήμα οδηγός
url: /el/net/programming-with-shapes/insert-rectangle-shape-in-c-with-aspose-words-step-by-step-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Εισαγωγή σχήματος ορθογωνίου σε C# με Aspose.Words – οδηγός βήμα‑βήμα

Αν χρειάζεστε **εισαγωγή σχήματος ορθογωνίου** σε ένα έγγραφο Word από C#, αυτός ο οδηγός σας δείχνει ακριβώς πώς να το κάνετε. Θα δείτε πώς να ορίσετε το χρώμα γεμίσματος, να κρύψετε το σχήμα ώστε να μην εμφανίζεται στην τελική διάταξη, και να αποθηκεύσετε το αρχείο—όλα με λίγες μόνο γραμμές κώδικα.

Στις επόμενες ενότητες καλύπτουμε όλα όσα χρειάζεται να γνωρίζετε: προαπαιτούμενα, η πλήρης λίστα κώδικα, εξηγήσεις για κάθε βήμα, και συμβουλές για κοινές παραλλαγές όπως η επαναφορά ορατότητας του σχήματος ή η χρήση διαφορετικού χρώματος. Στο τέλος θα μπορείτε να **προσθέσετε σχήμα ορθογωνίου** σε οποιοδήποτε αρχείο .docx προγραμματιστικά.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* **Aspose.Words for .NET** (έκδοση 23.10 ή νεότερη). Μπορείτε να το εγκαταστήσετε μέσω NuGet:

  ```bash
  dotnet add package Aspose.Words
  ```

* .NET 6.0 SDK ή νεότερο εγκατεστημένο στο σύστημά σας.
* Βασική κατανόηση της C# και του Visual Studio (ή οποιουδήποτε IDE προτιμάτε).

Δεν απαιτούνται πρόσθετες βιβλιοθήκες—τα API που αφορούν σχήματα είναι μέρος του βασικού πακέτου Aspose.Words.

## Εισαγωγή σχήματος ορθογωνίου με Aspose.Words

Ο πυρήνας της λύσης είναι ένα σύντομο, αυτόνομο πρόγραμμα που δημιουργεί ένα κενό έγγραφο, εισάγει ένα ορθογώνιο, το χρωματίζει, το κρύβει και, τέλος, αποθηκεύει το αρχείο. Παρακάτω βρίσκεται ο πλήρης πηγαίος κώδικας με ενσωματωμένα σχόλια που εξηγούν το *γιατί* πίσω από κάθε γραμμή.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Required for Color struct

// 1️⃣ Create a new, empty Word document.
Document document = new Document();

// 2️⃣ Obtain a DocumentBuilder – the primary API for editing the document.
DocumentBuilder builder = new DocumentBuilder(document);

// 3️⃣ Insert a rectangle shape of 100 × 50 points.
//    ShapeType.Rectangle tells Aspose.Words to create a simple rectangular drawing object.
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Set the shape's fill color to yellow.
//    The FillColor property accepts a System.Drawing.Color value.
rectangleShape.FillColor = Color.Yellow;

// 5️⃣ Hide the shape so it does not appear in the rendered document.
//    When Hidden = true, the shape is stored in the file but omitted from layout.
//    This is useful for placeholders, bookmarks, or metadata.
rectangleShape.Hidden = true;

// 6️⃣ Save the document to disk.
//    Change the path to a folder you have write access to.
document.Save(@"C:\Temp\HiddenRectangleShape.docx");
```

### Τι κάνει κάθε βήμα

| Βήμα | Λόγος |
|------|--------|
| **Δημιουργία νέου εγγράφου** | Παρέχει καθαρό καμβά· μπορείτε επίσης να φορτώσετε ένα υπάρχον .docx περνώντας τη διαδρομή αρχείου στο `new Document(path)`. |
| **Αρχικοποίηση DocumentBuilder** | Το `DocumentBuilder` είναι ο υψηλού επιπέδου βοηθός που σας επιτρέπει να εισάγετε κείμενο, πίνακες και σχήματα χωρίς να ασχοληθείτε με το χαμηλού επιπέδου δέντρο κόμβων. |
| **Εισαγωγή σχήματος ορθογωνίου** | Η μέθοδος `InsertShape` επιστρέφει ένα αντικείμενο `Shape` που μπορείτε να προσαρμόσετε περαιτέρω (μέγεθος, θέση, περιγράμματα κλπ.). |
| **Ορισμός χρώματος γεμίσματος** | Η ιδιότητα `FillColor` ελέγχει το εσωτερικό χρώμα· μπορείτε να χρησιμοποιήσετε οποιαδήποτε τιμή `Color` (`Color.Red`, `Color.FromArgb(255, 0, 255, 0)`, κλπ.). |
| **Κρύψιμο του σχήματος** | `Hidden = true` λέει στο Word να αγνοήσει το σχήμα κατά τη διάταξη, ενώ το διατηρεί στο XML του εγγράφου. Αυτός είναι ο τυπικός τρόπος αποθήκευσης αόρατων αντικειμένων. |
| **Αποθήκευση του εγγράφου** | Καταγράφει τις αλλαγές σε ένα αρχείο .docx. Το αποθηκευμένο αρχείο θα περιέχει το κρυμμένο σχήμα ορθογωνίου. |

## Πώς να ορίσετε χρώμα γεμίσματος για ένα σχήμα

Η αλλαγή του χρώματος γεμίσματος είναι τόσο απλή όσο η ανάθεση ενός `System.Drawing.Color` στην ιδιότητα `FillColor`. Αν χρειάζεστε προσαρμοσμένη απόχρωση, χρησιμοποιήστε `Color.FromArgb`:

```csharp
// Example: set a semi‑transparent teal fill
rectangleShape.FillColor = Color.FromArgb(128, 0, 128, 128);
```

*Γιατί είναι σημαντικό*: Το χρώμα γεμίσματος αποθηκεύεται στο XML του σχήματος (`<w:fill>` attribute). Όταν το σχήμα είναι κρυφό, το χρώμα παραμένει, κάτι που μπορεί να είναι χρήσιμο για επεξεργασία downstream (π.χ., εξαγωγή μεταδεδομένων βάσει κωδικών χρώματος).

## Πώς να κρύψετε το σχήμα στο τελικό έγγραφο

Η σημαία `Hidden` είναι μια boolean ιδιότητα στην κλάση `Shape`. Ορίζοντάς την σε `true` διασφαλίζετε ότι το σχήμα αγνοείται από τη μηχανή διάταξης του Word.

```csharp
rectangleShape.Hidden = true;
```

**Συνηθισμένα λάθη**

* **Hidden vs. Visible** – Αν αργότερα χρειαστεί το σχήμα να εμφανιστεί, απλώς ορίστε `Hidden = false`.
* **Συμβατότητα** – Παλαιότερες εκδόσεις του Word (πριν το 2007) μπορεί να αντιμετωπίζουν διαφορετικά τα κρυμμένα αντικείμενα σχεδίασης. Το Aspose.Words διατηρεί τη συμβατότητα αποθηκεύοντας τη σημαία στο κατάλληλο στοιχείο OOXML.

## Πώς να εισάγετε σχήμα προγραμματιστικά

Αν και το παράδειγμα χρησιμοποιεί ορθογώνιο, η ίδια μέθοδος `InsertShape` λειτουργεί για πολλά άλλα σχήματα (έλλειψη, τρίγωνο, γραμμή κλπ.). Το πρώτο όρισμα είναι μια τιμή του enum `ShapeType`:

```csharp
// Insert an ellipse with the same dimensions
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
ellipse.FillColor = Color.LightBlue;
```

**Συμβουλή**: Αν χρειάζεται να τοποθετήσετε το σχήμα σε συγκεκριμένη θέση στη σελίδα, χρησιμοποιήστε `builder.MoveTo` για να ορίσετε το σημείο εισαγωγής πριν καλέσετε το `InsertShape`.

## Προσθήκη σχήματος ορθογωνίου σε υπάρχον έγγραφο

Συχνά θα ενισχύετε ένα πρότυπο αντί να ξεκινάτε από το μηδέν. Αντικαταστήστε το βήμα 1 με:

```csharp
// Load an existing .docx file
Document document = new Document(@"C:\Templates\ReportTemplate.docx");
```

Όλα τα επόμενα βήματα παραμένουν τα ίδια, και το ορθογώνιο θα προστεθεί όπου βρίσκεται ο κέρσορας του builder (συνήθως στο τέλος του εγγράφου από προεπιλογή).

## Διαχείριση ειδικών περιπτώσεων και παραλλαγών

### 1. Επαναφορά ορατότητας του σχήματος

Αν ένα μεταγενέστερο τμήμα της ροής εργασίας σας χρειάζεται να αποκαλύψει το κρυμμένο ορθογώνιο, μπορείτε να εναλλάξετε τη σημαία:

```csharp
rectangleShape.Hidden = false;   // Shape will now be rendered
```

### 2. Προσθήκη περιγράμματος (stroke)

Ένα κρυφό σχήμα μπορεί ακόμα να έχει ορατό περίγραμμα όταν αποφασίσετε να το εμφανίσετε. Ορίστε τις ιδιότητες `LineColor` και `LineWidth`:

```csharp
rectangleShape.LineColor = Color.Black;
rectangleShape.LineWeight = 1.5; // points
```

### 3. Απόλυτη τοποθέτηση του ορθογωνίου

Για ακριβή έλεγχο διάταξης, αλλάξτε το `WrapType` του σχήματος σε `WrapType.Inline` (προεπιλογή) ή `WrapType.TopBottom` και προσαρμόστε τις ιδιότητες `Left`/`Top`:

```csharp
rectangleShape.WrapType = WrapType.TopBottom;
rectangleShape.Left = 72;   // 1 inch from the left margin
rectangleShape.Top = 144;   // 2 inches from the top margin
```

### 4. Χρήση διαφορετικής μονάδας μέτρησης

Το Aspose.Words λειτουργεί σε points (1 pt = 1/72 inch). Αν προτιμάτε εκατοστά, μετατρέψτε πρώτα:

```csharp
float cmToPoints = 28.3465f; // 1 cm ≈ 28.3465 pt
float width = 5 * cmToPoints;   // 5 cm wide
float height = 2 * cmToPoints;  // 2 cm tall
Shape cmRectangle = builder.InsertShape(ShapeType.Rectangle, width, height);
```

## Πλήρες εκτελέσιμο παράδειγμα

Παρακάτω βρίσκεται το *πλήρες* πρόγραμμα που μπορείτε να αντιγράψετε, να επικολλήσετε και να τρέξετε. Περιλαμβάνει όλες τις απαραίτητες οδηγίες `using` και χρησιμοποιεί απόλυτες διαδρομές που πρέπει να προσαρμόσετε στο περιβάλλον σας.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class InsertRectangleShapeDemo
{
    static void Main()
    {
        // Create a blank document.
        Document doc = new Document();

        // Use DocumentBuilder to edit the document.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 100 × 50 pt rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // Set the fill color to yellow.
        rect.FillColor = Color.Yellow;

        // Hide the shape so it does not affect layout.
        rect.Hidden = true;

        // Save the result.
        string outputPath = @"C:\Temp\HiddenRectangleShape.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Αναμενόμενο αποτέλεσμα**: Το αρχείο `HiddenRectangleShape.docx` ανοίγει στο Microsoft Word χωρίς ορατό σχήμα, αλλά το κρυμμένο ορθογώνιο υπάρχει στο XML του εγγράφου. Μπορείτε να επαληθεύσετε την ύπαρξή του ανοίγοντας το .docx ως αρχείο zip και εξετάζοντας το `word/document.xml` για ένα στοιχείο `<w:shape>` με τα χαρακτηριστικά `w:fill="yellow"` και `w:hidden="true"`.

## Συμπέρασμα

Τώρα ξέρετε πώς να **εισάγετε σχήμα ορθογωνίου** σε έγγραφο Word χρησιμοποιώντας C# και Aspose.Words, πώς να **ορίσετε χρώμα γεμίσματος**, και πώς να **κρύψετε το σχήμα** ώστε να παραμένει αόρατο στην τελική διάταξη. Το ίδιο μοτίβο λειτουργεί για άλλους τύπους σχημάτων, προσαρμοσμένα χρώματα και υπάρχοντα πρότυπα. Πειραματιστείτε με περιγράμματα, απόλυτη τοποθέτηση και διαφορετικές μονάδες μέτρησης για να προσαρμόσετε το σχήμα στις ακριβείς απαιτήσεις σας.

### Επόμενα βήματα

* Εξερευνήστε **πώς να εισάγετε σχήμα** μέσα σε πίνακες ή κεφαλίδες/υποσέλιδα για υδατογραφήματα.
* Συνδυάστε **προσθήκη σχήματος ορθογωνίου** με ελέγχους περιεχομένου για τη δημιουργία δυναμικών placeholders.
* Ανασκοπήστε το API **shape manipulation** του Aspose.Words για προχωρημένα χαρακτηριστικά όπως περιστροφή, διαβαθμισμένα γεμίσματα και εισαγωγή SVG.

Αισθανθείτε ελεύθεροι να προσαρμόσετε τον κώδικα στο δικό σας έργο και ενημερώστε μας στα σχόλια ποια πρόκληση σχετική με σχήματα λύσατε στη συνέχεια!

## What Should You Learn Next?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}