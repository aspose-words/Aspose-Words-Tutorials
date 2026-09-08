---
category: general
date: 2026-09-08
description: Μάθετε πώς να ομαδοποιείτε σχήματα στο Word με το DocumentBuilder, να
  δημιουργήσετε ένα κενό έγγραφο Word και να εισάγετε ένα ορθογώνιο σχήμα με λίγες
  μόνο γραμμές κώδικα C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create blank word doc
- insert rectangle shape word
- how to use documentbuilder
language: el
lastmod: 2026-09-08
og_description: Ομαδοποίηση σχημάτων στο Word χρησιμοποιώντας το DocumentBuilder.
  Αυτό το σεμινάριο δείχνει πώς να δημιουργήσετε ένα κενό έγγραφο Word, να εισάγετε
  ένα σχήμα ορθογωνίου και να συνδυάσετε σχήματα σε ένα GroupShape.
og_image_alt: Screenshot of a Word document showing grouped shapes – group shapes
  in Word example
og_title: Ομαδοποίηση σχημάτων στο Word με το DocumentBuilder – πλήρες παράδειγμα
  C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to group shapes in Word with a DocumentBuilder, create a
    blank Word doc, and insert a rectangle shape in just a few lines of C# code.
  headline: How to group shapes in Word using DocumentBuilder – step‑by‑step guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Πώς να ομαδοποιήσετε σχήματα στο Word χρησιμοποιώντας το DocumentBuilder –
  οδηγός βήμα‑βήμα
url: /el/net/programming-with-shapes/how-to-group-shapes-in-word-using-documentbuilder-step-by-st/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να ομαδοποιήσετε σχήματα στο Word χρησιμοποιώντας το DocumentBuilder – οδηγός βήμα‑βήμα

Αν χρειάζεται να **ομαδοποιήσετε σχήματα στο Word** προγραμματιστικά, αυτό το tutorial παρουσιάζει μια πλήρη λύση σε C#. Θα δείτε πώς να **δημιουργήσετε ένα κενό έγγραφο Word**, να χρησιμοποιήσετε το **DocumentBuilder** και να **εισάγετε ένα σχήμα ορθογωνίου** πριν το ομαδοποιήσετε με μια έλλειψη. Το αποτέλεσμα είναι ένα ενιαίο `GroupShape` που μπορείτε να μετακινήσετε, να αλλάξετε το μέγεθός του ή να το μορφοποιήσετε ως ένα αντικείμενο.

Αυτός ο οδηγός καλύπτει όλα όσα χρειάζεστε για να δημιουργήσετε ένα έγγραφο Word με ομαδοποιημένα γραφικά χρησιμοποιώντας τη βιβλιοθήκη Aspose.Words for .NET. Στο τέλος του άρθρου θα έχετε ένα εκτελέσιμο έργο που παράγει το `GroupedShapes.docx` που περιέχει ένα ορθογώνιο και μια έλλειψη συνδυασμένα σε ένα σχήμα.

## Προαπαιτούμενα

- .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.7.2+)
- Πακέτο NuGet Aspose.Words for .NET (`Aspose.Words`) – έκδοση 23.12 ή νεότερη
- Ένα IDE C# όπως το Visual Studio 2022 ή το Visual Studio Code
- Βασική εξοικείωση με τη σύνταξη C# και τον αντικειμενοστραφή προγραμματισμό

> **Pro tip:** Εγκαταστήστε το πακέτο NuGet από τη γραμμή εντολών για να διατηρήσετε το έργο σας καθαρό:  
> `dotnet add package Aspose.Words --version 23.12.0`

## Βήμα 1: Δημιουργία κενής εγγράφου Word

Η πρώτη ενέργεια είναι η δημιουργία ενός αντικειμένου `Document`, που αντιπροσωπεύει ένα άδειο αρχείο Word, και ενός `DocumentBuilder` που σας επιτρέπει να προσθέτετε περιεχόμενο.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Step 1: Create a blank Word document and a DocumentBuilder
        Document document = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Γιατί είναι σημαντικό:** Το `Document` παρέχει το δοχείο του αρχείου, ενώ το `DocumentBuilder` προσφέρει ένα ευέλικτο API για την εισαγωγή κειμένου, εικόνων και σχημάτων. Χωρίς το `DocumentBuilder` θα έπρεπε να χειρίζεστε το δέντρο κόμβων του εγγράφου χειροκίνητα, κάτι που είναι επιρρεπές σε σφάλματα.

## Βήμα 2: Εισαγωγή σχήματος ορθογωνίου

Ένα ορθογώνιο είναι ένα κοινό δομικό στοιχείο για διαγράμματα. Χρησιμοποιήστε `InsertShape` με `ShapeType.Rectangle` και ορίστε το πλάτος και το ύψος σε σημεία (1 pt ≈ 1/72 in).

```csharp
        // Step 2: Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;   // distance from the left margin (points)
        rectangleShape.Top = 50;    // distance from the top margin (points)
```

**Γιατί είναι σημαντικό:** Ορίζοντας τις ιδιότητες `Left` και `Top` τοποθετείτε το ορθογώνιο ακριβώς στη σελίδα, κάτι που είναι απαραίτητο όταν αργότερα το ομαδοποιήσετε με άλλα σχήματα. Η μέθοδος `InsertShape` προσθέτει αυτόματα το σχήμα στην τρέχουσα παράγραφο.

## Βήμα 3: Εισαγωγή σχήματος έλλειψης

Στη συνέχεια, προσθέστε μια έλλειψη που θα τοποθετηθεί δίπλα στο ορθογώνιο.

```csharp
        // Step 3: Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;
```

**Γιατί είναι σημαντικό:** Η χρήση διαφορετικού `ShapeType` δείχνει πώς το ίδιο API του `DocumentBuilder` μπορεί να δημιουργήσει διαφορετικά γραφικά. Η τοποθέτηση της έλλειψης ώστε να επικαλύπτεται με το ορθογώνιο κάνει το εφέ ομαδοποίησης προφανές.

## Βήμα 4: Ομαδοποίηση των δύο σχημάτων

Ένα `GroupShape` λειτουργεί σαν κοντέινερ. Προσθέτοντας το ορθογώνιο και την έλλειψη ως παιδιά, συμπεριφέρονται ως ένα ενιαίο αντικείμενο.

```csharp
        // Step 4: Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        // Define the bounding rectangle that encloses all child shapes
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Insert the group into the document body
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);
```

**Γιατί είναι σημαντικό:** Η ιδιότητα `Bounds` λέει στο Word πού βρίσκεται η ομάδα στη σελίδα. Προσθέτοντας τα παιδικά σχήματα, διατηρείτε τη μορφοποίηση τους ενώ επιτρέπετε συλλογικές μετασχηματίσεις (μετακίνηση, περιστροφή, αλλαγή μεγέθους).

## Βήμα 5: Αποθήκευση του εγγράφου

Τέλος, γράψτε το έγγραφο στο δίσκο. Μπορείτε να αλλάξετε τη διαδρομή σε οποιονδήποτε φάκελο προτιμάτε.

```csharp
        // Step 5: Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Όταν ανοίξετε το `GroupedShapes.docx` στο Microsoft Word, θα δείτε ένα ορθογώνιο και μια έλλειψη ομαδοποιημένα μαζί. Επιλέγοντας την ομάδα θα επισημαίνονται και τα δύο σχήματα, επιτρέποντάς σας να τα σύρετε ή να αλλάξετε το μέγεθός τους ως μία μονάδα.

### Αναμενόμενο αποτέλεσμα

- Ένα αρχείο Word με όνομα **GroupedShapes.docx**
- Η πρώτη σελίδα περιέχει ένα **ορθογώνιο** (100 pt × 50 pt) στη θέση (50, 50)
- Μια **έλλειψη** (80 pt × 80 pt) στη θέση (200, 70)
- Και τα δύο σχήματα είναι μέρος ενός **GroupShape** με πλαίσιο περιγράμματος 300 pt × 200 pt

## Συνηθισμένες παραλλαγές και περιπτώσεις άκρων

| Σενάριο | Προσαρμογή |
|----------|------------|
| **Διαφορετικό μέγεθος σελίδας** | Ορίστε `document.Sections[0].PageSetup.PageWidth` και `PageHeight` πριν την εισαγωγή σχημάτων. |
| **Περισσότερα από δύο σχήματα** | Δημιουργήστε επιπλέον αντικείμενα `Shape` και καλέστε `groupShape.AppendChild(newShape)` για καθένα. |
| **Εφαρμογή χρώματος γεμίσματος** | `rectangleShape.FillColor = System.Drawing.Color.LightBlue;` |
| **Περιστροφή της ομάδας** | `groupShape.Rotation = 45;` (μοίρες) |
| **Εξαγωγή σε PDF** | Μετά την αποθήκευση του DOCX, καλέστε `document.Save("GroupedShapes.pdf");` |

## Πλήρης κώδικας (έτοιμος για εκτέλεση)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Create a blank Word document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;
        rectangleShape.Top = 50;

        // Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;

        // Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);

        // Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Αντιγράψτε τον κώδικα σε ένα νέο έργο κονσόλας, επαναφέρετε το πακέτο NuGet Aspose.Words και τρέξτε το. Η κονσόλα θα επιβεβαιώσει τη θέση του αρχείου και το άνοιγμα του θα εμφανίσει τα ομαδοποιημένα γραφικά.

## Συμπέρασμα

Τώρα ξέρετε **πώς να ομαδοποιείτε σχήματα στο Word** με το Aspose.Words `DocumentBuilder`. Ο οδηγός διέσχισε τη δημιουργία ενός **κενό εγγράφου Word**, την **εισαγωγή σχήματος ορθογωνίου**, την προσθήκη μιας έλλειψης και τη συνένωση τους σε ένα `GroupShape`. Με αυτή τη βάση μπορείτε να δημιουργήσετε πιο πλούσια διαγράμματα, ροές εργασίας ή προσαρμοσμένα γραφικά απευθείας από C#.

### Τι ακολουθεί;

- Εξερευνήστε **πώς να χρησιμοποιήσετε το DocumentBuilder** για πίνακες, κεφαλίδες και υποσέλιδα.
- Συνδυάστε τις τεχνικές **εισαγωγής σχήματος ορθογωνίου Word** με πλαίσια κειμένου για σχολιασμένα διαγράμματα.
- Χρησιμοποιήστε το **δημιουργία κενό word doc** ως πρότυπο για αυτοματοποιημένη δημιουργία αναφορών.

Μη διστάσετε να πειραματιστείτε με χρώματα, διαβαθμίσεις και επιπλέον σχήματα. Καλή κωδικοποίηση!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στην υλοποίηση των δικών σας έργων.

- [Δημιουργία Group Shape σε έγγραφο Word χρησιμοποιώντας Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Εισαγωγή σχημάτων σε έγγραφα Word χρησιμοποιώντας Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Δημιουργία σχήματος ορθογωνίου σε Word με C# – Οδηγός βήμα‑βήμα](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}