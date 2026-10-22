---
category: general
date: 2026-08-04
description: Εισάγετε σχήμα ορθογωνίου σε έγγραφο Word με C#. Μάθετε πώς να ομαδοποιείτε
  σχήματα στο Word, να αποθηκεύετε το έγγραφο ως docx και να χρησιμοποιείτε το DocumentBuilder
  για προχωρημένες διατάξεις.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to group shapes
- group shapes in word
- save document as docx
- how to use builder
language: el
lastmod: 2026-08-04
og_description: Εισάγετε σχήμα ορθογωνίου σε αρχείο Word χρησιμοποιώντας C# και στη
  συνέχεια ομαδοποιήστε τα σχήματα για προηγμένες διατάξεις. Αυτό το σεμινάριο καλύπτει
  επίσης την αποθήκευση του εγγράφου ως docx και τη χρήση του DocumentBuilder αποδοτικά.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with C# DocumentBuilder
og_title: Εισαγωγή σχήματος ορθογωνίου στο Word – Οδηγός βήμα‑βήμα για C#
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Insert rectangle shape in a Word document with C#. Learn how to group
    shapes in Word, save document as docx, and use DocumentBuilder for advanced layouts.
  headline: Insert rectangle shape in Word using C# – complete guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Εισαγωγή σχήματος ορθογωνίου στο Word χρησιμοποιώντας C# – πλήρης οδηγός
url: /el/java/images-shapes/insert-rectangle-shape-in-word-using-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Εισαγωγή σχήματος ορθογωνίου σε Word με C# – πλήρης οδηγός

Αν χρειάζεστε **εισαγωγή σχήματος ορθογωνίου** σε ένα έγγραφο Word χρησιμοποιώντας C#, αυτό το tutorial σας δείχνει ακριβώς πώς. Θα μάθετε επίσης **πώς να ομαδοποιείτε σχήματα** στο Word, **πώς να αποθηκεύετε το έγγραφο ως docx**, και **πώς να χρησιμοποιείτε το Builder** για καθαρό, συντηρήσιμο κώδικα.

Η εργασία με σχήματα είναι συχνή απαίτηση όταν δημιουργείτε αναφορές, πιστοποιητικά ή προσαρμοσμένες διατάξεις προγραμματιστικά. Στο τέλος αυτού του οδηγού θα έχετε ένα πλήρως εκτελέσιμο παράδειγμα που δημιουργεί ένα ορθογώνιο, προσθέτει μια έλλειψη, τα ομαδοποιεί και αποθηκεύει το αποτέλεσμα ως αρχείο DOCX.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* .NET 6.0 ή νεότερη έκδοση εγκατεστημένη  
* Visual Studio 2022 (ή οποιοδήποτε IDE που υποστηρίζει C#)  
* Τη βιβλιοθήκη **Aspose.Words for .NET** (διαθέσιμη μέσω NuGet)  

Μπορείτε να προσθέσετε τη βιβλιοθήκη με την ακόλουθη εντολή:

```bash
dotnet add package Aspose.Words
```

## Εισαγωγή σχήματος ορθογωνίου με DocumentBuilder

Το πρώτο βήμα είναι να δημιουργήσετε ένα νέο `Document` και ένα `DocumentBuilder`. Ο builder παρέχει ένα fluent API για την εισαγωγή περιεχομένου, συμπεριλαμβανομένων των σχημάτων.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document.
        Document document = new Document();

        // Initialize the builder that will edit the document.
        DocumentBuilder builder = new DocumentBuilder(document);
```

Η παρουσία `DocumentBuilder` είναι το κεντρικό αντικείμενο που θα χρησιμοποιήσετε για **εισαγωγή σχήματος ορθογωνίου** και άλλων στοιχείων. Παρακολουθεί τη θέση του κέρσορα μέσα στο έγγραφο, ώστε κάθε εισαγωγή να συμβαίνει ακριβώς εκεί που τη χρειάζεστε.

## Πώς να εισάγετε ένα σχήμα ορθογωνίου

Με τον builder έτοιμο, καλέστε `InsertShape`. Καθορίζετε το `ShapeType`, το πλάτος και το ύψος σε points (1 pt ≈ 1/72 in).

```csharp
        // Insert a rectangle of 100 pt width and 50 pt height.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
```

*Γιατί είναι σημαντικό*: Ο ορισμός του `FillColor` και του `StrokeColor` κάνει το ορθογώνιο οπτικά διακριτό, κάτι που βοηθά όταν αργότερα το ομαδοποιήσετε με άλλα σχήματα.

## Πώς να ομαδοποιήσετε σχήματα στο Word

Η ομαδοποίηση σχημάτων σας επιτρέπει να μετακινείτε, περιστρέφετε ή μορφοποιείτε πολλά αντικείμενα ως μία ενιαία οντότητα. Αφού εισάγετε το ορθογώνιο, προσθέστε ένα ακόμη σχήμα (μια έλλειψη σε αυτό το παράδειγμα) και στη συνέχεια δημιουργήστε ένα `GroupShape`.

```csharp
        // Insert an ellipse of 80 pt diameter.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // Insert an empty group container.
        GroupShape groupShape = builder.InsertGroupShape();

        // Add the rectangle and ellipse to the group.
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
```

Η κλήση `InsertGroupShape` δημιουργεί έναν placeholder που μπορεί να κρατήσει οποιονδήποτε αριθμό παιδικών σχημάτων. Προσθέτοντας το ορθογώνιο και την έλλειψη, ουσιαστικά **ομαδοποιείτε σχήματα στο Word**. Η ομάδα συμπεριφέρεται σαν ένα μόνο σχήμα—μπορείτε να την επανατοποθετήσετε, να εφαρμόσετε περιθώριο ή να την αλλάξετε μέγεθος χωρίς να επηρεάσετε τη διάταξη των παιδικών αντικειμένων.

### Pro tip

Μετά την ομαδοποίηση, μπορείτε να αλλάξετε τη θέση της ομάδας σε σχέση με τη σελίδα:

```csharp
        // Move the whole group 150 pt right and 100 pt down.
        groupShape.Left = 150;
        groupShape.Top = 100;
```

## Αποθήκευση εγγράφου ως docx

Μόλις τα σχήματα είναι τοποθετημένα, πρέπει να αποθηκεύσετε το αρχείο. Η μέθοδος `Document.Save` καθορίζει αυτόματα τη μορφή από την επέκταση του αρχείου. Για **αποθήκευση εγγράφου ως docx**, περάστε μια διαδρομή που λήγει σε `.docx`.

```csharp
        // Save the document to the output folder.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

Η εκτέλεση του προγράμματος δημιουργεί το `output.docx`. Ανοίξτε το αρχείο στο Microsoft Word και θα δείτε ένα ανοιχτό‑μπλε ορθογώνιο και μια ανοιχτό‑κόκκινη έλλειψη ομαδοποιημένα μαζί. Μπορείτε να κάνετε κλικ στην ομάδα και να τη μετακινήσετε ως ένα ενιαίο αντικείμενο.

## Πώς να χρησιμοποιείτε το DocumentBuilder αποτελεσματικά

Το `DocumentBuilder` είναι κάτι περισσότερο από εισαγωγέα σχημάτων· διαχειρίζεται επίσης κείμενο, πίνακες, κεφαλίδες και υποσέλιδα. Όταν συνδυάζετε δημιουργία σχήματος με κείμενο, θυμηθείτε να επαναφέρετε τον κέρσορα αν χρειάζεται να εισάγετε περιεχόμενο αλλού:

```csharp
        // Move the cursor to a new paragraph after the group.
        builder.Writeln(); // Inserts a line break.
        builder.Font.Size = 12;
        builder.Writeln("Shapes have been added and grouped successfully.");
```

Η ρητή διαχείριση της κατάστασης του builder αποτρέπει τυχαίες αντικαταστάσεις και κάνει τον κώδικα πιο εύκολο στη συντήρηση.

## Ακραίες περιπτώσεις και παραλλαγές

| Situation | Recommended approach |
|-----------|----------------------|
| **More than two shapes** | Insert each shape, then call `AppendChild` for every shape before saving. |
| **Nested groups** | Create a group, add shapes, then insert that group into another `GroupShape`. |
| **Different measurement units** | Use `builder.ConvertPixelsToPoints` if you have dimensions in pixels. |
| **Compatibility with older Word versions** | Save as `.doc` by changing the extension; most shape features still work. |

## Πλήρες λειτουργικό παράδειγμα

Παρακάτω είναι το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε‑και‑επικολλήσετε σε ένα νέο έργο console. Δεν απαιτούνται επιπλέον αποσπάσματα κώδικα.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;

        // 3️⃣ Insert an ellipse shape.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // 4️⃣ Create a group shape and add both shapes.
        GroupShape groupShape = builder.InsertGroupShape();
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Optional: reposition the group.
        groupShape.Left = 150;
        groupShape.Top = 100;

        // 5️⃣ Add a caption below the group.
        builder.Writeln();
        builder.Font.Size = 12;
        builder.Writeln("Grouped rectangle and ellipse created with DocumentBuilder.");

        // 6️⃣ Save the document as DOCX.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

**Αναμενόμενο αποτέλεσμα**: Το άνοιγμα του `output.docx` εμφανίζει ένα ανοιχτό‑μπλε ορθογώνιο και μια ανοιχτό‑κόκκινη έλλειψη ομαδοποιημένα μαζί, τοποθετημένα 150 pt από το αριστερό περιθώριο και 100 pt από το πάνω. Η λεζάντα εμφανίζεται κάτω από την ομάδα.

## Συμπέρασμα

Τώρα ξέρετε πώς να **εισάγετε σχήμα ορθογωνίου** σε αρχείο Word χρησιμοποιώντας C#, **πώς να ομαδοποιείτε σχήματα στο Word**, και **πώς να αποθηκεύετε το έγγραφο ως docx** με το Aspose.Words `DocumentBuilder`. Με την εξάσκηση αυτών των βημάτων μπορείτε να δημιουργήσετε σύνθετες διατάξεις—πιστοποιητικά, αναφορές ή προσαρμοσμένες φόρμες—εντελώς μέσω κώδικα.

Στη συνέχεια, εξερευνήστε συναφή θέματα όπως **προσθήκη πλαισίων κειμένου**, **εργασία με πίνακες**, ή **εξαγωγή σε PDF**. Κάθε ένα από αυτά βασίζεται στα ίδια θεμέλια του `DocumentBuilder` που μόλις εξασκηθήκατε.

Έτοιμοι να αυτοματοποιήσετε τα έγγραφα Word σας; Δοκιμάστε να επεκτείνετε το παράδειγμα με περισσότερα σχήματα, εφαρμογή διαβαθμίσεων χρώματος ή βρόχους δεδομένων για τη δημιουργία πλήρους αναφοράς σε μία εκτέλεση. Καλή προγραμματιστική!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}