---
category: general
date: 2026-08-14
description: Πώς να ομαδοποιήσετε σχήματα σε ένα έγγραφο Word χρησιμοποιώντας C#.
  Μάθετε πώς να δημιουργήσετε έγγραφο Word, να εισάγετε σχήμα ορθογωνίου, να ομαδοποιήσετε
  σχήματα στο Word και να αποθηκεύσετε το έγγραφο ως docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- create word document
- insert rectangle shape
- group shapes in word
- save document as docx
language: el
lastmod: 2026-08-14
og_description: Πώς να ομαδοποιήσετε σχήματα σε ένα έγγραφο Word χρησιμοποιώντας C#.
  Ακολουθήστε αυτό το πλήρες σεμινάριο για να δημιουργήσετε ένα αρχείο Word, να εισάγετε
  σχήμα ορθογωνίου, να ομαδοποιήσετε σχήματα στο Word και να αποθηκεύσετε το αποτέλεσμα
  ως docx.
og_image_alt: Screenshot showing how to group shapes in a Word document using C#
og_title: Πώς να ομαδοποιήσετε σχήματα σε ένα έγγραφο Word με C# – βήμα‑βήμα οδηγός
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to group shapes in a Word document using C#. Learn to create Word
    document, insert rectangle shape, group shapes in Word, and save document as docx.
  headline: How to group shapes in a Word document with C#
  type: TechArticle
- description: How to group shapes in a Word document using C#. Learn to create Word
    document, insert rectangle shape, group shapes in Word, and save document as docx.
  name: How to group shapes in a Word document with C#
  steps:
  - name: Create a new blank document
    text: The first thing you do when you want to **create Word document** programmatically
      is instantiate a `Document` object. This object represents the entire .docx
      file in memory.
  - name: Insert a rectangle shape
    text: To demonstrate **insert rectangle shape**, we use the `InsertShape` method.
      The rectangle will act as the first member of the group.
  - name: Insert an ellipse shape
    text: Next, we **insert ellipse shape** (the API calls it `Ellipse`). This will
      be the second member of the group.
  - name: Group the rectangle and ellipse
    text: Now we answer the central question **how to group shapes** in a Word document.
      Aspose.Words provides `AppendGroupShape` to create a group container, and then
      you call `Group()` on that container.
  - name: Save the document as a DOCX file
    text: The final step is to **save document as docx**. You can choose any path
      you like; the example uses a placeholder `"YOUR_DIRECTORY"` that you should
      replace with a real folder.
  - name: Expected output
    text: When you open `groupedShapes.docx` in Microsoft Word, you will see a light‑blue
      rectangle and a light‑coral ellipse locked together. Clicking either shape selects
      both, allowing you to move or resize them as a single unit.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: Πώς να ομαδοποιήσετε σχήματα σε ένα έγγραφο Word με C#
url: /el/net/programming-with-shapes/how-to-group-shapes-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να ομαδοποιήσετε σχήματα σε ένα έγγραφο Word με C#

Αν χρειάζεστε **πώς να ομαδοποιήσετε σχήματα** σε ένα έγγραφο Word, αυτός ο οδηγός σας δείχνει τα ακριβή βήματα χρησιμοποιώντας C# και τη βιβλιοθήκη Aspose.Words. Θα δείτε πώς να δημιουργήσετε ένα έγγραφο Word, να εισάγετε σχήμα ορθογωνίου, να ομαδοποιήσετε σχήματα στο Word και τελικά **να αποθηκεύσετε το έγγραφο ως docx**—όλα σε ένα ενιαίο, εκτελέσιμο πρόγραμμα.

Η δημιουργία και η διαχείριση σχημάτων είναι συχνή απαίτηση όταν παράγετε αναφορές, συμβάσεις ή διαφημιστικά φυλλάδια προγραμματιστικά. Στο τέλος αυτού του σεμιναρίου θα έχετε ένα επαναχρησιμοποιήσιμο απόσπασμα κώδικα που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο .NET.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

- .NET 6.0 ή νεότερη έκδοση εγκατεστημένη  
- Visual Studio 2022 (ή οποιοδήποτε IDE που υποστηρίζει .NET)  
- Άδεια Aspose.Words for .NET (ή δωρεάν δοκιμή)  
- Βασική εξοικείωση με τη σύνταξη της C#  

Δεν απαιτούνται πρόσθετα πακέτα NuGet πέρα από `Aspose.Words`.

## Πώς να ομαδοποιήσετε σχήματα σε ένα έγγραφο Word

Ο πυρήνας της λύσης είναι μια διαδικασία πέντε βημάτων. Κάθε βήμα εξηγείται λεπτομερώς, και ο πλήρης πηγαίος κώδικας παρέχεται στο τέλος του άρθρου.

### Βήμα 1: Δημιουργία νέου κενού εγγράφου

Το πρώτο πράγμα που κάνετε όταν θέλετε να **δημιουργήσετε έγγραφο Word** προγραμματιστικά είναι να δημιουργήσετε ένα αντικείμενο `Document`. Αυτό το αντικείμενο αντιπροσωπεύει ολόκληρο το αρχείο .docx στη μνήμη.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document doc = new Document();

// Obtain a DocumentBuilder to add content
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Γιατί είναι σημαντικό:** Το `DocumentBuilder` είναι ένας υψηλού επιπέδου βοηθός που σας επιτρέπει να εισάγετε κείμενο, πίνακες και σχήματα χωρίς να χειρίζεστε χειροκίνητα το υποκείμενο δέντρο κόμβων.

### Βήμα 2: Εισαγωγή σχήματος ορθογωνίου

Για να δείξουμε **εισαγωγή σχήματος ορθογωνίου**, χρησιμοποιούμε τη μέθοδο `InsertShape`. Το ορθογώνιο θα λειτουργήσει ως το πρώτο μέλος της ομάδας.

```csharp
// Insert a rectangle (100x50 points) at the current cursor position
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// Optional: set a fill color so the shape is visible
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
```

**Γιατί είναι σημαντικό:** Τα σχήματα τοποθετούνται σχετικά με το σημείο εισαγωγής. Ο καθορισμός χρώματος γεμίσματος σας βοηθά να δείτε το σχήμα όταν ανοίξετε το παραγόμενο έγγραφο.

### Βήμα 3: Εισαγωγή σχήματος έλλειψης

Στη συνέχεια, **εισάγουμε σχήμα έλλειψης** (το API το ονομάζει `Ellipse`). Αυτό θα είναι το δεύτερο μέλος της ομάδας.

```csharp
// Insert an ellipse (80x40 points) right after the rectangle
Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 40);
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```

**Γιατί είναι σημαντικό:** Εισάγοντας το έλλειψο αμέσως μετά το ορθογώνιο, και τα δύο σχήματα καταλήγουν στην ίδια παράγραφο, κάτι που απλοποιεί την ομαδοποίηση αργότερα.

### Βήμα 4: Ομαδοποίηση του ορθογωνίου και του έλλειψης

Τώρα απαντάμε στο κεντρικό ερώτημα **πώς να ομαδοποιήσετε σχήματα** σε ένα έγγραφο Word. Η Aspose.Words παρέχει τη μέθοδο `AppendGroupShape` για τη δημιουργία ενός κοντέινερ ομάδας, και στη συνέχεια καλείτε `Group()` σε αυτό το κοντέινερ.

```csharp
// Get the first paragraph of the document (where the shapes live)
Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;

// Create a group shape that contains the rectangle and ellipse
Shape groupedShape = firstParagraph.AppendGroupShape(new[] { rectangleShape, ellipseShape });

// Turn the container into a true group – the shapes will move and scale together
groupedShape.Group();
```

**Γιατί είναι σημαντικό:** Μόλις ομαδοποιηθούν, οποιαδήποτε μετασχηματισμός (μετακίνηση, αλλαγή μεγέθους, περιστροφή) που εφαρμόζεται στο `groupedShape` επηρεάζει αυτόματα τόσο το ορθογώνιο όσο και το έλλειψο. Αυτό είναι απαραίτητο για τη διατήρηση της συνέπειας της διάταξης σε παραγόμενα έγγραφα.

### Βήμα 5: Αποθήκευση του εγγράφου ως αρχείο DOCX

Το τελευταίο βήμα είναι να **αποθηκεύσετε το έγγραφο ως docx**. Μπορείτε να επιλέξετε οποιοδήποτε μονοπάτι θέλετε· το παράδειγμα χρησιμοποιεί έναν δείκτη `"YOUR_DIRECTORY"` που πρέπει να αντικαταστήσετε με έναν πραγματικό φάκελο.

```csharp
// Define the output path (ensure the directory exists)
string outputPath = @"C:\Temp\groupedShapes.docx";

// Save the document in DOCX format
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved successfully to {outputPath}");
```

**Γιατί είναι σημαντικό:** Η αποθήκευση ως DOCX διατηρεί τα μεταδεδομένα ομαδοποίησης, ώστε όταν ανοίξετε το αρχείο στο Microsoft Word να δείτε το ορθογώνιο και το έλλειψο να λειτουργούν ως ένα ενιαίο αντικείμενο.

## Πλήρες, εκτελέσιμο παράδειγμα

Ακολουθεί το πλήρες πρόγραμμα που συνδυάζει και τα πέντε βήματα. Αντιγράψτε το σε ένα νέο έργο κονσόλας, επαναφέρετε το πακέτο NuGet Aspose.Words και τρέξτε το.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Insert a rectangle shape (100x50 points)
            Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            rectangleShape.FillColor = System.Drawing.Color.LightBlue;

            // Step 3: Insert an ellipse shape (80x40 points)
            Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 40);
            ellipseShape.FillColor = System.Drawing.Color.LightCoral;

            // Step 4: Group the rectangle and ellipse
            Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
            Shape groupedShape = firstParagraph.AppendGroupShape(new[] { rectangleShape, ellipseShape });
            groupedShape.Group();

            // Step 5: Save the document as DOCX
            string outputPath = @"C:\Temp\groupedShapes.docx";
            doc.Save(outputPath, SaveFormat.Docx);

            Console.WriteLine($"Document saved successfully to {outputPath}");
        }
    }
}
```

### Αναμενόμενο αποτέλεσμα

Όταν ανοίξετε το `groupedShapes.docx` στο Microsoft Word, θα δείτε ένα ανοιχτό‑μπλε ορθογώνιο και ένα ανοιχτό‑κοραλί έλλειψο κλειδωμένα μαζί. Κάνοντας κλικ σε οποιοδήποτε σχήμα θα επιλέγονται και τα δύο, επιτρέποντάς σας να τα μετακινήσετε ή να τα αλλάξετε σε μέγεθος ως μία ενιαία μονάδα.

## Συχνές ερωτήσεις και ειδικές περιπτώσεις

| Ερώτηση | Απάντηση |
|----------|--------|
| **Μπορώ να ομαδοποιήσω περισσότερα από δύο σχήματα;** | Ναι. Περάστε όποιον αριθμό αντικειμένων `Shape` θέλετε στη `AppendGroupShape`. Η μέθοδος δέχεται έναν πίνακα, ώστε να μπορείτε να δημιουργήσετε μια συλλογή δυναμικά. |
| **Τι γίνεται αν χρειαστεί η ομάδα να αγκυροβοληθεί σε κελί πίνακα;** | Εισάγετε τα σχήματα μέσα στην παράγραφο του κελιού, έπειτα καλέστε `AppendGroupShape` σε αυτήν την παράγραφο. Η ομάδα κληρονομεί την αγκύρωση του κελιού. |
| **Επηρεάζει η ομαδοποίηση το υποκείμενο XML;** | Η Aspose.Words γράφει ένα στοιχείο `<w:grpSp>` που περιέχει τα παιδικά σχήματα. Το Word το αναγνωρίζει ως ομάδα, διατηρώντας τη σχετική θέση. |
| **Πώς να αποομαδοποιήσω αργότερα;** | Καλέστε `groupedShape.Ungroup()`· η μέθοδος επιστρέφει τα μεμονωμένα σχήματα ώστε να τα επεξεργαστείτε ξεχωριστά. |
| **Υπάρχει επίπτωση στην απόδοση όταν ομαδοποιώ πολλά σχήματα;** | Η ίδια η ομαδοποίηση είναι ελαφριά, αλλά η απόδοση μπορεί να μειωθεί όταν αποδίδονται πολύ μεγάλες ομάδες (εκατοντάδες σχήματα), αυξάνοντας το μέγεθος του αρχείου. Σκεφτείτε την εξομάλυνση εικόνων αν το μέγεθος γίνει πρόβλημα. |

## Επαγγελματικές συμβουλές

- **Ορίστε ρητές θέσεις** (`Left`, `Top`) αν χρειάζεστε ακριβή ευθυγράμμιση πριν την ομαδοποίηση.  
- **Χρησιμοποιήστε `Shape.WrapType = WrapType.Inline`** όταν θέλετε η ομάδα να συμπεριφέρεται σαν στοιχείο παραγράφου αντί για αιωρούμενο αντικείμενο.  
- **Εφαρμόστε στυλ γραμμής** στην ομάδα (`groupedShape.LineFormat`) για να δώσετε στο σύνολο ένα περίγραμμα.  
- **Επαναχρησιμοποίηση της ομάδας**: μετά την κλήση `Group()`, μπορείτε να κλωνοποιήσετε το `groupedShape` και να εισάγετε το κλώνο αλλού στο έγγραφο.

## Επόμενα βήματα

Τώρα που ξέρετε **πώς να ομαδοποιήσετε σχήματα** σε ένα έγγραφο Word, μπορείτε να εξερευνήσετε σχετικά θέματα όπως:

- **Εισαγωγή σχήματος ορθογωνίου** με προσαρμοσμένο κείμενο ή εικόνες μέσα στο σχήμα.  
- **Δημιουργία σύνθετων διαγραμμάτων** με ενσωμάτωση ομάδων (ομάδα μέσα σε ομάδα).  
- **Εξαγωγή του εγγράφου ως PDF** διατηρώντας την ομαδοποίηση σχημάτων (`doc.Save("output.pdf", SaveFormat.Pdf)`).  

Κάθε ένα από αυτά βασίζεται στα ίδια θεμέλια που καλύφθηκαν εδώ, ώστε να είστε έτοιμοι να επεκτείνετε το εργαλείο αυτοματοποίησης του Word.

## Συμπέρασμα

Αυτός ο οδηγός έδειξε **πώς να ομαδοποιήσετε σχήματα** σε ένα έγγραφο Word χρησιμοποιώντας C#. Μάθατε να **δημιουργήσετε έγγραφο Word**, να **εισάγετε σχήμα ορθογωνίου**, να **ομαδοποιήσετε σχήματα στο Word**, και τελικά να **αποθηκεύσετε το έγγραφο ως docx**. Με το πλήρες, εκτελέσιμο παράδειγμα και τις πρακτικές συμβουλές, μπορείτε να ενσωματώσετε την ομαδοποίηση σχημάτων σε οποιαδήποτε ροή παραγωγής εγγράφων. Καλή προγραμματιστική!

## Τι πρέπει να μάθετε στη συνέχεια;

Οι παρακάτω εκπαιδευτικές ενότητες καλύπτουν στενά σχετικά θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [Δημιουργία ομαδικού σχήματος σε έγγραφο Word χρησιμοποιώντας Aspose.Words για .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Εισαγωγή σχημάτων σε έγγραφα Word χρησιμοποιώντας Aspose.Words για .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Δημιουργία σχήματος ορθογωνίου σε Word με C# – Οδηγός βήμα‑βήμα](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}