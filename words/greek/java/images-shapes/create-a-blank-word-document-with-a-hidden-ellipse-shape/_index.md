---
category: general
date: 2026-09-18
description: Δημιουργήστε ένα κενό έγγραφο Word και κρύψτε ένα σχήμα έλλειψης χρησιμοποιώντας
  το Aspose.Words. Μάθετε πώς να κρύψετε ένα σχήμα στο Word, πώς να εισάγετε μια έλλειψη
  και πώς να δημιουργήσετε γρήγορα ένα κρυφό σχήμα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to hide shape
- how to insert ellipse
- hide shape in word
- create hidden shape
language: el
lastmod: 2026-09-18
og_description: Δημιουργήστε ένα κενό έγγραφο Word και κρύψτε ένα σχήμα έλλειψης στο
  Word. Αυτός ο οδηγός σας δείχνει βήμα‑βήμα πώς να εισάγετε έλλειψη, να κρύψετε το
  σχήμα στο Word και να δημιουργήσετε κρυφό σχήμα με το Aspose.Words.
og_image_alt: Screenshot of a blank Word document containing a hidden ellipse shape
  created with Aspose.Words
og_title: Δημιουργήστε ένα κενό έγγραφο Word με κρυφό σχήμα έλλειψης
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create a blank Word document and hide an ellipse shape using Aspose.Words.
    Learn how to hide shape in Word, how to insert ellipse, and create hidden shape
    quickly.
  headline: Create a blank Word document with a hidden ellipse shape
  type: TechArticle
- description: Create a blank Word document and hide an ellipse shape using Aspose.Words.
    Learn how to hide shape in Word, how to insert ellipse, and create hidden shape
    quickly.
  name: Create a blank Word document with a hidden ellipse shape
  steps:
  - name: Pro tip
    text: If you later need to make the shape visible again, simply set `ellipse.Hidden
      = false;` and save the document.
  - name: What if the shape still appears?
    text: '* Ensure you are using Aspose.Words 23.9 or later – older versions had
      a bug where `Hidden` was ignored for some shape types. * Verify that you are
      not applying any additional formatting (e.g., `WrapType`) that forces the shape
      to occupy layout space.'
  - name: Can I hide other shape types?
    text: Yes. The same `Hidden` property works for `ShapeType.Rectangle`, `ShapeType.Picture`,
      etc. Just replace `ShapeType.Ellipse` with the desired type.
  - name: How to list hidden shapes later?
    text: '```csharp foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
      { if (shape.Hidden) Console.WriteLine($"Hidden shape: {shape.ShapeType}"); }
      ```'
  - name: Next steps
    text: '* Explore **how to hide shape** conditionally based on document content.
      * Learn **how to unhide shape** when generating a final version of the document.
      * Combine hidden shapes with **custom document properties** to embed machine‑readable
      data.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Δημιουργήστε ένα κενό έγγραφο Word με κρυφό σχήμα έλλειψης
url: /el/java/images-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία κενού εγγράφου Word με κρυφό σχήμα έλλειψης

Αν χρειάζεστε **να δημιουργήσετε ένα κενό έγγραφο Word** που περιέχει ένα σχήμα που δεν θέλετε να εμφανίζεται στη διάταξη, αυτός ο οδηγός σας δείχνει ακριβώς πώς να το κάνετε. Χρησιμοποιώντας το Aspose.Words for .NET μπορείτε προγραμματιστικά να εισάγετε μια έλλειψη και στη συνέχεια να κρύψετε το σχήμα ώστε το έγγραφο να παραμένει οπτικά κενό ενώ διατηρεί τα δεδομένα του σχήματος.

Σε αυτό το tutorial θα μάθετε:

* πώς να **δημιουργήσετε αντικείμενα κενών εγγράφων Word**, 
* πώς να **εισάγετε έλλειψη** χρησιμοποιώντας `DocumentBuilder`,
* πώς να **κρύψετε σχήμα στο Word** ώστε να μην επηρεάζει τη σελίδα,
* πώς να **δημιουργήσετε κρυφά σχήματα** για επεξεργασία αργότερα.

Τα βήματα λειτουργούν με .NET 6+ και την πιο πρόσφατη έκδοση του Aspose.Words (23.9 τη στιγμή της συγγραφής). Δεν απαιτείται πρόσθετη εγκατάσταση του Office.

## Prerequisites

* Visual Studio 2022 (ή οποιοδήποτε IDE C#)
* .NET 6 SDK ή νεότερο
* Aspose.Words for .NET NuGet package  
  ```bash
  dotnet add package Aspose.Words
  ```
* Βασικές γνώσεις C# και εννοιών εγγράφων Word

## Step 1: Create a blank Word document

Το πρώτο πράγμα που πρέπει να κάνετε είναι να δημιουργήσετε ένα αντικείμενο `Document`. Αυτό το αντικείμενο αντιπροσωπεύει ένα κενό αρχείο `.docx` και αποτελεί τη βάση για όλες τις επόμενες λειτουργίες.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document
Document doc = new Document();   // <-- creates a blank Word document in memory
```

Η δημιουργία ενός **κενού εγγράφου Word** σας παρέχει έναν καθαρό καμβά – χωρίς παραγράφους, χωρίς ενότητες, μόνο τη βασική δομή του πακέτου. Αυτό είναι το ιδανικό σημείο εκκίνησης όταν χρειάζεστε μόνο ένα κρυφό σχήμα και τίποτα άλλο.

## Step 2: Initialise a DocumentBuilder

`DocumentBuilder` παρέχει ένα βολικό API για την προσθήκη περιεχομένου σε ένα `Document`. Λειτουργεί όπως ένας κέρσορας που κινείται μέσα στο έγγραφο.

```csharp
// Step 2: Initialise a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

Ο builder δημιουργεί αυτόματα μια προεπιλεγμένη πρώτη ενότητα και παράγραφο, ώστε να μπορείτε να αρχίσετε να εισάγετε σχήματα χωρίς να προσθέτετε ενότητες χειροκίνητα.

## Step 3: Insert an ellipse shape

Τώρα **εισάγουμε μια έλλειψη** χρησιμοποιώντας τη μέθοδο `InsertShape`. Η μέθοδος δέχεται μια απαρίθμηση `ShapeType`, το πλάτος και το ύψος (σε points).

```csharp
// Step 3: Insert an ellipse shape with a width of 100 points and a height of 50 points
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
```

Γιατί μια έλλειψη; Η έλλειψη είναι ένα διανυσματικό σχήμα που μπορεί να κρυφτεί χωρίς να επηρεάζει τη ροή του κειμένου γύρω του. Το πλάτος των 100 pt και το ύψος των 50 pt είναι αυθαίρετα· μπορείτε να τα προσαρμόσετε ανάλογα με τις ανάγκες της επόμενης επεξεργασίας.

## Step 4: Hide the shape so it does not appear in the layout

Για να **κρύψετε σχήμα στο Word**, ορίστε την ιδιότητα `Hidden` του αντικειμένου `Shape` σε `true`. Όταν το έγγραφο ανοίξει στο Microsoft Word, το σχήμα θα είναι αόρατο και δεν θα καταλαμβάνει χώρο στη διάταξη.

```csharp
// Step 4: Hide the shape so it does not appear in the layout
ellipse.Hidden = true;   // <-- this hides the shape in Word
```

Η σημαία `Hidden` αποθηκεύεται στο XML του σχήματος (`<w:hidden/>`). Το Word σέβεται αυτό το χαρακτηριστικό κατά την απόδοση, γι' αυτό το έγγραφο φαίνεται εντελώς κενό παρόλο που το σχήμα υπάρχει.

### Pro tip

Αν χρειαστείτε αργότερα να κάνετε το σχήμα ορατό ξανά, απλώς ορίστε `ellipse.Hidden = false;` και αποθηκεύστε το έγγραφο.

## Step 5: Save the document with the hidden shape

Τέλος, αποθηκεύστε το έγγραφο στο δίσκο. Το αρχείο θα είναι ένα κανονικό `.docx` που μπορεί να ανοίξει οποιοσδήποτε επεξεργαστής κειμένου Word.

```csharp
// Step 5: Save the document with the hidden shape
doc.Save(@"C:\Temp\HiddenEllipse.docx");
```

Το αποθηκευμένο αρχείο, `HiddenEllipse.docx`, είναι ένα **create blank word document** που περιέχει μια κρυφή έλλειψη. Το άνοιγμα του στο Microsoft Word εμφανίζει μια κενή σελίδα, αλλά το σχήμα παραμένει παρόν στη δομή Open XML.

## Full working example

Παρακάτω βρίσκεται το πλήρες, αυτόνομο πρόγραμμα που μπορείτε να αντιγράψετε, επικολλήσετε και εκτελέσετε.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace HiddenShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a blank Word document
            Document doc = new Document();

            // 2️⃣ Initialise DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert an ellipse shape (width: 100pt, height: 50pt)
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

            // 4️⃣ Hide the shape so it does not affect layout
            ellipse.Hidden = true;

            // 5️⃣ Save the result
            string outputPath = @"C:\Temp\HiddenEllipse.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Expected output**

* Ένα αρχείο με όνομα `HiddenEllipse.docx` εμφανίζεται στο `C:\Temp`.
* Το άνοιγμα του αρχείου στο Microsoft Word εμφανίζει μια εντελώς κενή σελίδα.
* Αν ελέγξετε το έγγραφο με το Open XML SDK ή έναν προβολέα zip, θα βρείτε το στοιχείο `<w:shape>` με `<w:hidden/>` μέσα στο τμήμα του εγγράφου.

## Common questions and edge cases

### What if the shape still appears?

* Βεβαιωθείτε ότι χρησιμοποιείτε Aspose.Words 23.9 ή νεότερη – παλαιότερες εκδόσεις είχαν ένα σφάλμα όπου η ιδιότητα `Hidden` αγνοούνταν για ορισμένους τύπους σχημάτων.
* Επαληθεύστε ότι δεν εφαρμόζετε επιπλέον μορφοποίηση (π.χ., `WrapType`) που αναγκάζει το σχήμα να καταλαμβάνει χώρο στη διάταξη.

### Can I hide other shape types?

Ναι. Η ίδια ιδιότητα `Hidden` λειτουργεί για `ShapeType.Rectangle`, `ShapeType.Picture`, κ.λπ. Απλώς αντικαταστήστε το `ShapeType.Ellipse` με τον επιθυμητό τύπο.

### How to list hidden shapes later?

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.Hidden)
        Console.WriteLine($"Hidden shape: {shape.ShapeType}");
}
```

Αυτό το απόσπασμα κώδικα διασχίζει όλα τα σχήματα και εκτυπώνει αυτά που είναι κρυφά, κάτι που είναι χρήσιμο για ροές εργασίας **create hidden shape** όπου αργότερα χρειάζεται να τα επεξεργαστείτε ή να τα εμφανίσετε.

## Conclusion

Τώρα γνωρίζετε πώς να **δημιουργήσετε ένα κενό έγγραφο Word**, **εισάγετε μια έλλειψη**, και **κρύψετε σχήμα στο Word** για να δημιουργήσετε ένα **create hidden shape** που παραμένει αόρατο για τον αναγνώστη. Αυτή η τεχνική είναι χρήσιμη για την αποθήκευση μεταδεδομένων, σελιδοδεικτών ή προσαρμοσμένου XML μέσα σε ένα έγγραφο χωρίς να αλλάζει η οπτική του εμφάνιση.

### Next steps

* Εξερευνήστε **πώς να κρύψετε σχήμα** υπό όρους βάσει του περιεχομένου του εγγράφου.
* Μάθετε **πώς να εμφανίσετε σχήμα** όταν δημιουργείτε την τελική έκδοση του εγγράφου.
* Συνδυάστε κρυφά σχήματα με **προσαρμοσμένες ιδιότητες εγγράφου** για ενσωμάτωση δεδομένων που διαβάζονται από μηχανές.

Μη διστάσετε να πειραματιστείτε με διαφορετικούς τύπους σχημάτων, μεγέθη και λογική κρυφής κατάστασης ώστε να ταιριάζουν στο σενάριο αυτοματοποίησής σας. Καλή προγραμματιστική!

## What Should You Learn Next?

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}