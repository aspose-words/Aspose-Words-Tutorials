---
category: general
date: 2026-09-05
description: Μάθετε πώς να δημιουργήσετε ένα κενό έγγραφο Word και να προσθέσετε ένα
  σχήμα ορθογωνίου που μπορεί να κρυφτεί χρησιμοποιώντας το Aspose.Words σε C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- blank word document
- add rectangle shape
- how to hide shape
- hide shape word
- create hidden shape
language: el
lastmod: 2026-09-05
og_description: Δημιουργία κενού εγγράφου Word και εισαγωγή κρυφού σχήματος ορθογωνίου
  χρησιμοποιώντας το Aspose.Words – βήμα‑βήμα οδηγός για προγραμματιστές C#.
og_image_alt: Screenshot of a blank Word document with a hidden rectangle shape created
  by Aspose.Words in C#
og_title: Δημιουργήστε ένα κενό έγγραφο Word με κρυφό σχήμα ορθογωνίου
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  headline: Create a blank word document and add a rectangle shape
  type: TechArticle
- description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  name: Create a blank word document and add a rectangle shape
  steps:
  - name: Expected result
    text: 'Open `HiddenRectangle.docx` in Word:'
  - name: Can I hide multiple shapes at once?
    text: Yes. Create each shape, set `Hidden = true`, and insert them sequentially.
      The hidden flag works per node, so mixing hidden and visible shapes in the same
      document is supported.
  - name: What if I need the shape to be hidden only in the print view?
    text: 'Word distinguishes between **display** and **print** visibility through
      the `DisplayWhen` property. Aspose.Words does not expose a direct API for that
      flag, but you can modify the underlying XML:'
  - name: Does the hidden shape affect file size?
    text: A hidden shape adds the same XML payload as a visible one, so the file size
      increase is identical. However, because the shape
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: Δημιουργήστε ένα κενό έγγραφο Word και προσθέστε ένα σχήμα ορθογωνίου
url: /el/net/programming-with-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργήστε ένα κενό έγγραφο Word και προσθέστε ένα σχήμα ορθογωνίου

Αν χρειάζεστε δημιουργία **κενό έγγραφο Word** που περιλαμβάνει επίσης ένα σχήμα που δεν θέλετε να εμφανίζεται στη διάταξη, αυτός ο οδηγός σας δείχνει ακριβώς πώς να το κάνετε με το Aspose.Words για .NET. Θα δείτε ένα πλήρες, εκτελέσιμο παράδειγμα που δημιουργεί ένα νέο έγγραφο, προσθέτει ένα σχήμα ορθογωνίου, το κρύβει και αποθηκεύει το αρχείο—χωρίς επιπλέον εργαλεία.

Ο οδηγός καλύπτει όλα, από τη ρύθμιση του έργου μέχρι την αντιμετώπιση κοινών προβλημάτων. Στο τέλος θα μπορείτε να δημιουργήσετε ένα αρχείο Word που φαίνεται κενό στον αναγνώστη αλλά εξακολουθεί να περιέχει κρυφά μεταδεδομένα, χρήσιμο για υδατογραφήματα, αποθήκευση προσαρμοσμένου XML ή άγκυρες διάταξης.

## Προαπαιτήσεις

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* .NET 6.0 SDK ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.7+)
* Visual Studio 2022 (ή οποιοδήποτε IDE που υποστηρίζει C#)
* Ένα ενεργό **Aspose.Words** άδεια NuGet (η δωρεάν δοκιμή λειτουργεί για δοκιμές)
* Βασική εξοικείωση με C# και την έννοια των κόμβων εγγράφου

Μπορείτε να εγκαταστήσετε τη βιβλιοθήκη με την ακόλουθη εντολή CLI:

```bash
dotnet add package Aspose.Words
```

> **Συμβουλή:** Διατηρήστε την έκδοση του Aspose.Words ενημερωμένη· το API που χρησιμοποιείται σε αυτόν τον οδηγό είναι σταθερό από την έκδοση 23.10.

## Πώς να δημιουργήσετε ένα κενό έγγραφο Word με το Aspose.Words

Το πρώτο βήμα είναι η δημιουργία ενός αντικειμένου `Document`. Ένα νέο `Document` αντιπροσωπεύει ένα κενό **κενό έγγραφο Word**—χωρίς παραγράφους, χωρίς ενότητες, μόνο το δοχείο του αρχείου.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, empty Word document
Document document = new Document();
```

> **Γιατί είναι σημαντικό:** Ξεκινώντας με ένα καθαρό έγγραφο εξασφαλίζει ότι το κρυφό σχήμα που θα προσθέσετε αργότερα δεν θα επηρεάσει το υπάρχον περιεχόμενο ή τα στυλ.

## Προσθήκη σχήματος ορθογωνίου στο έγγραφο

Στη συνέχεια δημιουργούμε ένα σχήμα ορθογωνίου. Στο Aspose.Words ένα σχήμα είναι ένας κόμβος που μπορεί να τοποθετηθεί οπουδήποτε στο δέντρο του εγγράφου και μπορεί να ρυθμιστεί με μέγεθος, γέμισμα, στυλ γραμμής και ορατότητα.

```csharp
// Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(document);

// Define a rectangle shape (the "add rectangle shape" step)
Shape rectangle = new Shape(document, ShapeType.Rectangle)
{
    Width = 150,   // Width in points (1 point = 1/72 inch)
    Height = 80,   // Height in points
    FillColor = System.Drawing.Color.LightGray,
    StrokeColor = System.Drawing.Color.DarkGray,
    StrokeWeight = 0.5
};
```

Ο παραπάνω κώδικας δημιουργεί ένα ορατό ορθογώνιο. Σε αυτό το σημείο θα μπορούσατε να το εισάγετε στο έγγραφο με `builder.InsertNode(rectangle)`. Ωστόσο, επειδή θέλουμε το σχήμα να παραμείνει κρυφό, θα προσαρμόσουμε την ιδιότητα `Hidden` πριν από την εισαγωγή.

## Πώς να κρύψετε σχήμα σε έγγραφο Word

Το Word παρέχει ένα χαρακτηριστικό `Hidden` για τους κόμβους σχήματος. Όταν οριστεί σε `true`, το σχήμα δεν εμφανίζεται στη διάταξη της σελίδας, αλλά παραμένει μέρος του XML του εγγράφου. Αυτό αποτελεί τον πυρήνα της απαίτησης **πώς να κρύψετε σχήμα**.

```csharp
// Hide the shape so it won't be displayed
rectangle.Hidden = true;
```

> **Επεξήγηση:** Ορίζοντας `Hidden = true` προσθέτει το χαρακτηριστικό `<w:hide>` στο XML του σχήματος. Οι επεξεργαστές Word αγνοούν το σχήμα κατά την απόδοση, ενώ το σχήμα μπορεί ακόμη να προσπελαστεί προγραμματιστικά ή μέσω της προβολής XML του Word.

## Εισαγωγή του κρυμμένου σχήματος στο κενό έγγραφο

Τώρα τοποθετούμε το κρυφό ορθογώνιο στο δέντρο του εγγράφου. Επειδή το έγγραφο είναι ακόμα κενό, το σχήμα γίνεται ο πρώτος κόμβος στην κύρια ιστορία.

```csharp
// Insert the hidden rectangle at the current cursor position
builder.InsertNode(rectangle);
```

Αν ανοίξετε το παραγόμενο αρχείο στο Microsoft Word, θα δείτε μια φαινομενικά κενή σελίδα. Το σχήμα είναι εκεί, αλλά είναι αόρατο.

## Αποθήκευση του εγγράφου

Τέλος, γράφουμε το έγγραφο στο δίσκο. Μπορείτε να επιλέξετε οποιαδήποτε υποστηριζόμενη μορφή (`.docx`, `.pdf`, `.odt`, κ.λπ.). Για αυτόν τον οδηγό θα χρησιμοποιήσουμε τη σύγχρονη μορφή DOCX.

```csharp
// Save the file – adjust the path as needed
string outputPath = Path.Combine(Environment.CurrentDirectory, "HiddenRectangle.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

### Αναμενόμενο αποτέλεσμα

Ανοίξτε το `HiddenRectangle.docx` στο Word:

* Το έγγραφο εμφανίζεται κενό (χωρίς ορατά σχήματα ή κείμενο).
* Αν ελέγξετε το αρχείο με ένα εργαλείο όπως το **Open XML SDK** ή το **Word XML Viewer**, θα δείτε το στοιχείο `<w:pict>` που περιέχει το ορθογώνιο με το χαρακτηριστικό `hidden`.

![blank word document with hidden rectangle shape](image.png){: .align-center alt="κενό έγγραφο Word με κρυφό σχήμα ορθογωνίου"}

## Πλήρες, εκτελέσιμο παράδειγμα

Παρακάτω βρίσκεται το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε‑και‑επικολλήσετε σε μια εφαρμογή κονσόλας. Περιλαμβάνει όλες τις απαραίτητες οδηγίες `using`, διαχείριση σφαλμάτων και σχόλια.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Prepare a DocumentBuilder to manipulate the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Define a rectangle shape (add rectangle shape)
        Shape rectangle = new Shape(document, ShapeType.Rectangle)
        {
            Width = 150,
            Height = 80,
            FillColor = System.Drawing.Color.LightGray,
            StrokeColor = System.Drawing.Color.DarkGray,
            StrokeWeight = 0.5,
            // 4️⃣ Hide the shape (how to hide shape)
            Hidden = true
        };

        // 5️⃣ Insert the hidden shape into the blank document
        builder.InsertNode(rectangle);

        // 6️⃣ Save the document (create hidden shape)
        string outputPath = Path.Combine(
            Environment.CurrentDirectory, "HiddenRectangle.docx");
        document.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Εκτελέστε το πρόγραμμα (`dotnet run`) και επαληθεύστε το αρχείο εξόδου. Η κονσόλα θα επιβεβαιώσει τη θέση αποθήκευσης.

## Συχνές ερωτήσεις και ειδικές περιπτώσεις

### Μπορώ να κρύψω πολλαπλά σχήματα ταυτόχρονα;

Ναι. Δημιουργήστε κάθε σχήμα, ορίστε `Hidden = true` και εισάγετέ τα διαδοχικά. Η σημαία κρυφής εμφάνισης λειτουργεί ανά κόμβο, οπότε η ανάμειξη κρυφών και ορατών σχημάτων στο ίδιο έγγραφο υποστηρίζεται.

### Τι γίνεται αν χρειάζομαι το σχήμα να είναι κρυφό μόνο στην προβολή εκτύπωσης;

Το Word διακρίνει μεταξύ **display** και **print** ορατότητας μέσω της ιδιότητας `DisplayWhen`. Το Aspose.Words δεν εκθέτει άμεσο API για αυτή τη σημαία, αλλά μπορείτε να τροποποιήσετε το υποκείμενο XML:

```csharp
rectangle.GetShapeRenderer().GetShapeXml()
    .SetAttribute("w:display", "print");
```

Χρησιμοποιήστε το μόνο όταν χρειάζεστε ορατότητα μόνο στην εκτύπωση.

### Επηρεάζει το κρυφό σχήμα το μέγεθος του αρχείου;

Ένα κρυφό σχήμα προσθέτει το ίδιο XML payload όπως ένα ορατό, έτσι η αύξηση του μεγέθους του αρχείου είναι ίδια. Ωστόσο, επειδή το σχήμα

## Τι Θα Πρέπει Να Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}