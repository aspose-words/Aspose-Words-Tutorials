---
category: general
date: 2026-09-08
description: Δημιουργήστε σχήμα ορθογωνίου σε έγγραφο Word με C#. Μάθετε πώς να ορίζετε
  το μέγεθος του σχήματος, να ομαδοποιείτε πολλαπλά σχήματα και να δημιουργείτε κενό
  έγγραφο Word προγραμματιστικά.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- set shape size
- group multiple shapes
- create blank word document
language: el
lastmod: 2026-09-08
og_description: Δημιουργήστε σχήμα ορθογωνίου σε έγγραφο Word με C#. Αυτός ο οδηγός
  δείχνει πώς να ορίσετε το μέγεθος του σχήματος, να ομαδοποιήσετε πολλαπλά σχήματα
  και να δημιουργήσετε ένα κενό έγγραφο Word προγραμματιστικά.
og_image_alt: Screenshot showing how to create rectangle shape in a Word document
  using C#
og_title: Δημιουργία σχήματος ορθογωνίου και ομαδοποίηση σχημάτων στο Word χρησιμοποιώντας
  C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Create rectangle shape in a Word document with C#. Learn to set shape
    size, group multiple shapes, and create blank Word document programmatically.
  headline: Create rectangle shape and group shapes in Word using C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Δημιουργία σχήματος ορθογωνίου και ομαδοποίηση σχημάτων στο Word χρησιμοποιώντας
  C#
url: /el/net/programming-with-shapes/create-rectangle-shape-and-group-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία σχήματος ορθογωνίου και ομαδοποίηση σχημάτων στο Word με C#

Αν χρειάζεστε **create rectangle shape** μέσα σε ένα αρχείο Word, αυτό το tutorial σας παρέχει μια πλήρη, έτοιμη προς εκτέλεση λύση. Θα δείτε πώς να ορίσετε το μέγεθος του σχήματος, να ομαδοποιήσετε πολλαπλά σχήματα και να δημιουργήσετε ένα κενό έγγραφο Word από το μηδέν—όλα με τη βιβλιοθήκη Aspose.Words for .NET.

Η εργασία με έγγραφα Word προγραμματιστικά συχνά μοιάζει με το να χειρίζεστε πολλά μικρά λεπτομέρειες. Στο τέλος αυτού του οδηγού θα έχετε μια μοναδική μέθοδο που παράγει ένα αρχείο `.docx` που περιέχει ένα ορθογώνιο και μια έλλειψη ομαδοποιημένα μαζί, έτοιμα για περαιτέρω επεξεργασία ή εκτύπωση.

## Προαπαιτούμενα

* .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.6+)
* Μια αδειοδοτημένη έκδοση του **Aspose.Words for .NET** (μπορείτε να χρησιμοποιήσετε ένα δωρεάν κλειδί αξιολόγησης)
* Ένα IDE όπως το Visual Studio 2022 ή το Visual Studio Code
* Βασική εξοικείωση με τη σύνταξη C#

Δεν απαιτούνται πρόσθετα πακέτα NuGet πέρα από το `Aspose.Words`.

## Βήμα 1: Δημιουργία κενής εγγράφου Word

Το πρώτο βήμα είναι η δημιουργία ενός κενό εγγράφου που θα φιλοξενήσει τα σχήματα. Αυτό ικανοποιεί την απαίτηση *create blank word document*.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty Word document
Document doc = new Document();

// The document already contains one section and one empty paragraph
// You can add additional sections later if needed
```

Η δημιουργία ενός κενό εγγράφου σας παρέχει έναν καθαρό καμβά. Το αντικείμενο `Document` αντιπροσωπεύει ολόκληρο το αρχείο `.docx`, και το `FirstSection.Body.FirstParagraph` είναι το προεπιλεγμένο σημείο εισαγωγής για νέους κόμβους.

## Βήμα 2: Δημιουργία σχήματος ορθογωνίου

Τώρα μπορείτε να προσθέσετε το ορθογώνιο. Εδώ πραγματοποιείται η λειτουργία **create rectangle shape**.

```csharp
// Initialize a DocumentBuilder to simplify node insertion
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape instance
Shape rectangle = new Shape(doc, ShapeType.Rectangle);

// Set the rectangle's size (width and height) and position
rectangle.Width  = 100;   // points; 1 point = 1/72 inch
rectangle.Height = 50;
rectangle.Left   = 10;    // distance from the left edge of the container
rectangle.Top    = 20;    // distance from the top edge of the container

// Optional: give the rectangle a visible border
rectangle.StrokeColor = Color.Blue;
rectangle.FillColor   = Color.LightGray;
```

Ο καθορισμός των διαστάσεων απευθείας ανταποκρίνεται στη λέξη‑κλειδί **set shape size**. Όλες οι τιμές μεγέθους εκφράζονται σε points, παρέχοντας ακριβή έλεγχο του πώς εμφανίζεται το σχήμα στο τελικό έγγραφο.

## Βήμα 3: Δημιουργία πρόσθετου σχήματος (έλλειψη)

Μια τυπική περίπτωση χρήσης είναι ο συνδυασμός πολλών σχημάτων. Εδώ προσθέτουμε μια έλλειψη που αργότερα θα μοιραστεί το ίδιο κοντέινερ.

```csharp
// Create an ellipse shape instance
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width  = 80;
ellipse.Height = 80;
ellipse.Left   = 120;   // Position it to the right of the rectangle
ellipse.Top    = 30;

// Give the ellipse a distinct border and fill
ellipse.StrokeColor = Color.DarkGreen;
ellipse.FillColor   = Color.LightYellow;
```

Και τα δύο σχήματα είναι ακόμη ανεξάρτητα σε αυτό το σημείο. Το επόμενο βήμα δείχνει πώς να **group multiple shapes** μαζί.

## Βήμα 4: Ομαδοποίηση σχημάτων στο Word

Η ομαδοποίηση σχημάτων σας επιτρέπει να τα μετακινήσετε, να αλλάξετε το μέγεθός τους ή να τα μορφοποιήσετε ως μια ενιαία μονάδα. Αυτό ικανοποιεί τις απαιτήσεις **group shapes in word** και **group multiple shapes**.

```csharp
// Create a GroupShape container that will hold the rectangle and ellipse
GroupShape group = new GroupShape(doc);

// Define the container's bounding box – it must be large enough for all children
group.Bounds = new RectangleF(0, 0, 300, 200);

// Append the group to the document's first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(group);

// Add the rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

Η ιδιότητα `GroupShape.Bounds` καθορίζει το σύστημα συντεταγμένων για τα παιδικά σχήματα. Τοποθετώντας το ορθογώνιο και την έλλειψη μέσα στο ίδιο `GroupShape`, μπορείτε αργότερα να τα μετακινήσετε ή να τα περιστρέψετε μαζί με μία κλήση.

## Βήμα 5: Αποθήκευση του εγγράφου

Τέλος, γράψτε το έγγραφο στο δίσκο. Το αρχείο θα περιέχει τα ομαδοποιημένα σχήματα που μόλις δημιουργήσατε.

```csharp
// Choose an output path – ensure the directory exists and you have write permission
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");

// Save the document in DOCX format
doc.Save(outputPath);
```

Αφού εκτελέσετε το πρόγραμμα, ανοίξτε το `GroupedShapes.docx` στο Microsoft Word. Θα πρέπει να δείτε ένα ορθογώνιο και μια έλλειψη ομαδοποιημένα μαζί· η επιλογή ενός σχήματος επιλέγει επίσης και το άλλο, επιβεβαιώνοντας ότι η ομαδοποίηση πέτυχε.

## Πλήρης κώδικας πηγής

Αντιγράψτε το παρακάτω πλήρες πρόγραμμα σε ένα νέο έργο console‑app και εκτελέστε το. Δεν απαιτείται επιπλέον κώδικας.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System;
using System.Drawing;
using System.IO;

class Program
{
    static void Main()
    {
        // Step 1: create a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: create rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width  = 100,
            Height = 50,
            Left   = 10,
            Top    = 20,
            StrokeColor = Color.Blue,
            FillColor   = Color.LightGray
        };

        // Step 3: create ellipse shape
        Shape ellipse = new Shape(doc, ShapeType.Ellipse)
        {
            Width  = 80,
            Height = 80,
            Left   = 120,
            Top    = 30,
            StrokeColor = Color.DarkGreen,
            FillColor   = Color.LightYellow
        };

        // Step 4: group the shapes
        GroupShape group = new GroupShape(doc)
        {
            Bounds = new RectangleF(0, 0, 300, 200)
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(group);
        group.AppendChild(rectangle);
        group.AppendChild(ellipse);

        // Step 5: save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### Αναμενόμενο αποτέλεσμα

Η εκτέλεση του προγράμματος παράγει το `GroupedShapes.docx`. Το άνοιγμα του αρχείου στο Word εμφανίζει:

* Ένα **rectangle** (100 pt × 50 pt) με μπλε περίγραμμα και γκρι‑ανοιχτό γέμισμα.
* Μια **ellipse** (80 pt × 80 pt) με σκούρο‑πράσινο περίγραμμα και ανοιχτό‑κίτρινο γέμισμα.
* Και τα δύο σχήματα βρίσκονται μέσα σε μία ενιαία ομάδα, έτσι η μετακίνηση του ενός μετακινεί και το άλλο.

## Συχνές ερωτήσεις και ειδικές περιπτώσεις

| Ερώτηση | Απάντηση |
|----------|--------|
| **Μπορώ να προσθέσω περισσότερα από δύο σχήματα στην ομάδα;** | Ναι. Δημιουργήστε επιπλέον αντικείμενα `Shape` και καλέστε `group.AppendChild(yourShape)` για κάθε ένα. |
| **Τι γίνεται αν χρειαστεί να περιστρέψω την ομάδα;** | Ορίστε `group.RotationAngle = 45;` (μοίρες). Όλα τα παιδικά σχήματα περιστρέφονται μαζί. |
| **Μπορεί να γίνει ομαδοποίηση σχημάτων μετά την αποθήκευση του εγγράφου;** | Πρέπει να τροποποιήσετε τη δομή του εγγράφου πριν την αποθήκευση· διαφορετικά θα πρέπει να φορτώσετε το αρχείο, να εντοπίσετε τα σχήματα και να δημιουργήσετε ξανά την ομάδα. |
| **Πρέπει να απελευθερώσω (dispose) κάποιο αντικείμενο;** | Το Aspose.Words διαχειρίζεται τους δικούς του πόρους, αλλά θα πρέπει να απελευθερώσετε (dispose) τα αντικείμενα `FileStream` εάν ανοίξετε ροές χειροκίνητα. |
| **Θα λειτουργήσει ο κώδικας με μορφή .doc (δυαδική);** | Ναι, αλλάξτε σε `doc.Save("output.doc")`. Η συμπεριφορά ομαδοποίησης είναι η ίδια. |

## Συμπέρασμα

Τώρα γνωρίζετε πώς να **create rectangle shape**, **set shape size**, και **group multiple shapes** μέσα σε ένα αρχείο Word χρησιμοποιώντας C#. Αυτή η προσέγγιση σας επιτρέπει να δημιουργείτε προγραμματιστικά σύνθετα διαγράμματα, υδατογραφήματα ή αναφορές βασισμένες σε πρότυπα χωρίς χειροκίνητη επεξεργασία.

### Επόμενα βήματα

* Εξερευνήστε περαιτέρω το **group shapes in word** προσθέτοντας πλαίσια κειμένου ή εικόνες στην ίδια ομάδα.
* Χρησιμοποιήστε το πρότυπο `SetShapeSize` για να υπολογίζετε δυναμικά τις διαστάσεις βάσει της διάταξης της σελίδας.
* Συνδυάστε αυτήν την τεχνική με πεδία συγχώνευσης αλληλογραφίας (mail‑merge) για να δημιουργήσετε εξατομικευμένα έγγραφα σε μεγάλη κλίμακα.

Μη διστάσετε να πειραματιστείτε με διαφορετικούς τύπους σχημάτων, χρώματα και μετασχηματισμούς ομάδας. Καλή προγραμματιστική!

## Τι Θα Μάθετε Στη Σύντομη Επόμενη Στιγμή;

Τα παρακάτω tutorials καλύπτουν στενά σχετικές θεματικές που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Δημιουργία Group Shape σε Έγγραφο Word Χρησιμοποιώντας Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Δημιουργία Κενό Έγγραφο Word με Σχήμα Ορθογωνίου με Σκιά – Οδηγός Βήμα‑βήμα](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Δημιουργία Εγγράφου Word με Σκιασμένο Ορθογώνιο – Οδηγός Βήμα‑βήμα](/words/english/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}