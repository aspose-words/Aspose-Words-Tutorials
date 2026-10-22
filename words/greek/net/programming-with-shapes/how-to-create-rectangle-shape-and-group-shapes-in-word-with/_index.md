---
category: general
date: 2026-09-05
description: Δημιουργήστε σχήμα ορθογωνίου σε ένα έγγραφο Word χρησιμοποιώντας το
  Aspose.Words, μετά μάθετε πώς να εισάγετε ελλειπτικό σχήμα και να ομαδοποιείτε σχήματα
  στο Word για πιο πλούσιες διατάξεις.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- how to insert rectangle word
- how to insert ellipse word
- aspose.words create shapes
language: el
lastmod: 2026-09-05
og_description: Δημιουργήστε σχήμα ορθογωνίου σε ένα έγγραφο Word με το Aspose.Words,
  στη συνέχεια δείτε πώς να εισάγετε σχήμα έλλειψης και να ομαδοποιήσετε σχήματα στο
  Word για σύνθετες διατάξεις.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with Aspose.Words
og_title: Δημιουργία σχήματος ορθογωνίου και ομαδοποίηση σχημάτων στο Word – Οδηγός
  Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create rectangle shape in a Word document using Aspose.Words, then
    learn how to insert ellipse word and group shapes in Word for richer layouts.
  headline: How to create rectangle shape and group shapes in Word with Aspose.Words
  type: TechArticle
- description: Create rectangle shape in a Word document using Aspose.Words, then
    learn how to insert ellipse word and group shapes in Word for richer layouts.
  name: How to create rectangle shape and group shapes in Word with Aspose.Words
  steps:
  - name: Pro tip
    text: Always add shapes **before** you group them. If you try to group a shape
      that is already part of another group, Aspose.Words throws an `ArgumentException`.
      Building the group in a single method prevents this runtime error.
  - name: Watch out for
    text: '* **Coordinate system** – `Left` and `Top` are measured from the page’s
      left and top margins, not from the document edge. Misunderstanding this can
      place shapes off‑page. * **Licensing** – Without a valid license, the saved
      document will contain a watermark that says “Aspose.Words for .NET Evaluatio'
  - name: What’s next?
    text: '* Explore **aspose.words create shapes** for more complex geometry such
      as `Polygon` or `Freeform`. * Combine grouped shapes with **content controls**
      to build dynamic templates. * Convert the DOCX to PDF or HTML to see how vector
      shapes are rendered across formats.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Πώς να δημιουργήσετε σχήμα ορθογωνίου και να ομαδοποιήσετε σχήματα στο Word
  με το Aspose.Words
url: /el/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε σχήμα ορθογωνίου και να ομαδοποιήσετε σχήματα στο Word με Aspose.Words

Αν χρειάζεστε **να δημιουργήσετε σχήμα ορθογωνίου** σε ένα έγγραφο Word, αυτός ο οδηγός σας δείχνει τα ακριβή βήματα με το Aspose.Words για .NET. Θα δείτε επίσης πώς να εισάγετε λέξη έλλειψης, να ομαδοποιήσετε σχήματα στο Word και να αποθηκεύσετε το αποτέλεσμα ως αρχείο DOCX. Η λύση λειτουργεί σε οποιοδήποτε έργο .NET 6+ και δεν απαιτεί εγκατεστημένο Microsoft Office στον διακομιστή.

Το tutorial καλύπτει τα πάντα, από τη ρύθμιση του έργου μέχρι την αντιμετώπιση κοινών προβλημάτων διάταξης, ώστε να μπορείτε να αντιγράψετε τον κώδικα και να τον εκτελέσετε αμέσως.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* .NET 6 SDK ή νεότερο εγκατεστημένο  
* Ένα IDE συμβατό με NuGet (Visual Studio, Rider ή VS Code)  
* Άδεια Aspose.Words για .NET (ή προσωρινό κλειδί αξιολόγησης)  
* Βασικές γνώσεις C# και δομής εγγράφου Word  

Αυτά τα στοιχεία επιτρέπουν στον κώδικα να μεταγλωττιστεί και τα σχήματα να αποδοθούν σωστά.

## Βήμα 1: Ρύθμιση του έργου και προσθήκη Aspose.Words

Δημιουργήστε ένα νέο έργο console και προσθέστε το πακέτο Aspose.Words:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

Το πακέτο παρέχει τις κλάσεις `Document`, `DocumentBuilder`, `Shape` και `GroupShape` που χρησιμοποιούνται σε όλο το tutorial.

## Βήμα 2: Αρχικοποίηση κενού εγγράφου και builder

Το αντικείμενο `Document` αντιπροσωπεύει ολόκληρο το αρχείο Word, ενώ το `DocumentBuilder` σας επιτρέπει να εισάγετε περιεχόμενο προγραμματιστικά.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

Document doc = new Document();                 // creates an empty .docx container
DocumentBuilder builder = new DocumentBuilder(doc);
```

Η δημιουργία του εγγράφου πρώτα εξασφαλίζει ότι όλες οι επόμενες λειτουργίες σχήματος έχουν έγκυρο container.

## Βήμα 3: **Δημιουργία σχήματος ορθογωνίου** και ορισμός διαστάσεων

Ένα ορθογώνιο είναι το πιο κοινό container για κείμενο ή εικόνες. Ορίζετε το μέγεθός του σε points (1 pt ≈ 1/72 inch).

```csharp
// create a rectangle shape
Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
rectangleShape.Width = 100;      // 100 pt ≈ 1.39 in
rectangleShape.Height = 50;      // 50 pt ≈ 0.69 in

// optional: give the rectangle a light fill and a thin border
rectangleShape.FillColor = System.Drawing.Color.LightGray;
rectangleShape.Line.Width = 0.5;

// insert the rectangle into the document at the current cursor position
builder.InsertNode(rectangleShape);
```

Γιατί είναι σημαντικό αυτό το βήμα: η κλάση `Shape` περιλαμβάνει γεωμετρία, γέμισμα και ιδιότητες γραμμής. Ο ορισμός των `Width` και `Height` πριν από την εισαγωγή εγγυάται ότι το σχήμα εμφανίζεται με το αναμενόμενο μέγεθος.

## Βήμα 4: **Πώς να εισάγετε λέξη έλλειψης** – προσθήκη σχήματος έλλειψης

Μια έλλειψη μπορεί να χρησιμοποιηθεί για εικονίδια, δείκτες ή διακοσμητικά στοιχεία. Ο κώδικας είναι παρόμοιος με τη δημιουργία του ορθογωνίου, αλλά αλλάζει το `ShapeType`.

```csharp
// create an ellipse shape
Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
ellipseShape.Width = 80;      // 80 pt ≈ 1.11 in
ellipseShape.Height = 80;     // a perfect circle because width = height

// style the ellipse
ellipseShape.FillColor = System.Drawing.Color.CornflowerBlue;
ellipseShape.Line.Color = System.Drawing.Color.DarkBlue;

// place the ellipse after the rectangle
builder.InsertNode(ellipseShape);
```

Οι ιδιότητες `FillColor` και `Line.Color` δείχνουν πώς να προσαρμόσετε την εμφάνιση χωρίς εξωτερικές εικόνες.

## Βήμα 5: **Ομαδοποίηση σχημάτων στο Word** – συνδυασμός ορθογωνίου και έλλειψης

Η ομαδοποίηση σας επιτρέπει να μετακινείτε, να αλλάζετε μέγεθος ή να περιστρέφετε πολλαπλά σχήματα ως μία ενιαία μονάδα. Αυτό είναι απαραίτητο όταν χρειάζεστε ένα σύνθετο γραφικό (π.χ. εικονίδιο με ετικέτα).

```csharp
// create a group shape container
GroupShape groupShape = new GroupShape(doc);

// add the previously created shapes to the group
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);

// optional: set the group's position on the page
groupShape.Left = 150;   // distance from the left margin in points
groupShape.Top = 100;    // distance from the top margin in points

// insert the grouped shape into the document
builder.InsertNode(groupShape);
```

Όταν καλείτε `AppendChild`, τα αρχικά σχήματα αφαιρούνται από τη ροή του κύριου εγγράφου και γίνονται παιδιά του `GroupShape`. Η ομάδα συμπεριφέρεται σαν ένα μόνο σχήμα, κάτι που απλοποιεί τις μετέπειτα προσαρμογές διάταξης.

## Βήμα 6: Αποθήκευση του εγγράφου

Τέλος, γράψτε το έγγραφο στο δίσκο. Μπορείτε να επιλέξετε οποιαδήποτε υποστηριζόμενη μορφή (`.docx`, `.pdf`, `.html`, κ.λπ.). Για αυτό το tutorial κρατάμε τη φυσική μορφή Word.

```csharp
// replace "YOUR_DIRECTORY" with an absolute or relative path you control
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Αφού εκτελέσετε το πρόγραμμα, ανοίξτε το *GroupShape.docx* στο Microsoft Word. Θα δείτε ένα ορθογώνιο και μια έλλειψη ομαδοποιημένα μαζί, τοποθετημένα στις συντεταγμένες που καθορίσατε.

## Συνηθισμένες παραλλαγές και περιπτώσεις άκρων

| Κατάσταση | Τι να αλλάξετε | Λόγος |
|-----------|----------------|--------|
| **Διαφορετικές μονάδες μεγέθους** | Χρησιμοποιήστε `ConvertUtil.InchToPoint(2.5)` για ίντσες ή `ConvertUtil.MillimeterToPoint(30)` για χιλιοστά. | Κρατά τον κώδικα ευανάγνωστο όταν δουλεύετε με μετρήσεις εκτός points. |
| **Προσθήκη κειμένου μέσα στο ορθογώνιο** | Δημιουργήστε έναν κόμβο `Paragraph`, ορίστε την ιδιότητα `Text` και προσθέστε τον στο `rectangleShape` μέσω `AppendChild`. | Σας επιτρέπει να ετικετοποιήσετε το σχήμα χωρίς ξεχωριστά πλαίσια κειμένου. |
| **Περιστροφή της ομάδας** | Ορίστε `groupShape.Rotation = 45;` (μοίρες). | Χρήσιμο για δημιουργία διαγώνιων εμβλημάτων ή υδατογραφήσεων. |
| **Αποθήκευση ως PDF** | Καλέστε `doc.Save("GroupShape.pdf");`. | Το Aspose.Words αυτόματα rasterizes τα διανυσματικά σχήματα για έξοδο PDF. |
| **Πολλαπλές ομάδες** | Δημιουργήστε επιπλέον στιγμιότυπα `GroupShape` και επαναλάβετε τα βήματα προσθήκης/εισαγωγής. | Ενεργοποιεί σύνθετες διατάξεις σελίδας με αρκετά ανεξάρτητα σύνθετα στοιχεία. |

### Pro tip

Πάντα προσθέτετε σχήματα **πριν** τα ομαδοποιήσετε. Αν προσπαθήσετε να ομαδοποιήσετε ένα σχήμα που είναι ήδη μέρος μιας άλλης ομάδας, το Aspose.Words θα ρίξει `ArgumentException`. Η δημιουργία της ομάδας σε μία μέθοδο αποτρέπει αυτό το σφάλμα χρόνου εκτέλεσης.

### Προσέξτε

* **Σύστημα συντεταγμένων** – Τα `Left` και `Top` μετρώνται από τα αριστερά και πάνω περιθώρια της σελίδας, όχι από την άκρη του εγγράφου. Η παρερμηνεία μπορεί να τοποθετήσει σχήματα εκτός σελίδας.
* **Άδεια** – Χωρίς έγκυρη άδεια, το αποθηκευμένο έγγραφο θα περιέχει υδατογράφημα που λέει “Aspose.Words for .NET Evaluation”. Εφαρμόστε την άδειά σας νωρίς στον κώδικα (`License license = new License(); license.SetLicense("Aspose.Words.lic");`) για να το αποφύγετε.

## Πλήρης πηγαίος κώδικας (εκτελέσιμο)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Create rectangle shape
        Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
        rectangleShape.Width = 100;
        rectangleShape.Height = 50;
        rectangleShape.FillColor = System.Drawing.Color.LightGray;
        rectangleShape.Line.Width = 0.5;
        builder.InsertNode(rectangleShape);

        // 3️⃣ Create ellipse shape
        Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
        ellipseShape.Width = 80;
        ellipseShape.Height = 80;
        ellipseShape.FillColor = System.Drawing.Color.CornflowerBlue;
        ellipseShape.Line.Color = System.Drawing.Color.DarkBlue;
        builder.InsertNode(ellipseShape);

        // 4️⃣ Group rectangle and ellipse
        GroupShape groupShape = new GroupShape(doc);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        groupShape.Left = 150;
        groupShape.Top = 100;
        builder.InsertNode(groupShape);

        // 5️⃣ Save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Η εκτέλεση αυτού του προγράμματος παράγει το *GroupShape.docx* με τα ομαδοποιημένα σχήματα ακριβώς όπως περιγράφηκε.

## Συμπέρασμα

Τώρα ξέρετε πώς να **δημιουργήσετε σχήμα ορθογωνίου**, **πώς να εισάγετε λέξη έλλειψης** και **να ομαδοποιήσετε σχήματα στο Word** χρησιμοποιώντας το Aspose.Words. Το πλήρες παράδειγμα δείχνει τη συνολική ροή εργασίας—από την αρχικοποίηση ενός εγγράφου μέχρι την αποθήκευση του τελικού αρχείου—ώστε να ενσωματώσετε τη διαχείριση σχημάτων σε οποιαδήποτε αυτοματοποιημένη λύση αναφοράς ή δημιουργίας εγγράφων.

### Τι ακολουθεί;

* Εξερευνήστε **aspose.words create shapes** για πιο σύνθετη γεωμετρία όπως `Polygon` ή `Freeform`.  
* Συνδυάστε ομαδοποιημένα σχήματα με **content controls** για τη δημιουργία δυναμικών προτύπων.  
* Μετατρέψτε το DOCX σε PDF ή HTML για να δείτε πώς αποδίδονται τα διανυσματικά σχήματα σε διαφορετικές μορφές.  

Πειραματιστείτε με διαφορετικά μεγέθη, χρώματα και περιστροφές. Όταν κυριαρχήσετε στην ομαδοποίηση σχημάτων, μπορείτε να δημιουργήσετε σύνθετα διαγράμματα, εμβλήματα και προσαρμοσμένα UI στοιχεία απευθείας μέσα σε έγγραφα Word.

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}