---
category: general
date: 2026-08-04
description: Δημιουργήστε έγγραφο Word προγραμματιστικά χρησιμοποιώντας C#. Μάθετε
  πώς να προσθέτετε έλεγχο περιεχομένου στο Word και να ορίζετε κείμενο κράτησης θέσης
  για δυναμικά πρότυπα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add content control to word
- set placeholder text word
- Aspose.Words content control
- dynamic Word template C#
language: el
lastmod: 2026-08-04
og_description: Δημιουργήστε έγγραφο Word προγραμματιστικά με C#. Αυτός ο οδηγός δείχνει
  πώς να προσθέσετε έλεγχο περιεχομένου στο Word και να ορίσετε κείμενο κράτησης θέσης
  για επαναχρησιμοποιήσιμα πρότυπα.
og_image_alt: Screenshot of a Word document with a highlighted content control placeholder
og_title: Δημιουργία εγγράφου Word προγραμματιστικά – προσθήκη ελέγχου περιεχομένου
  & κράτησης θέσης
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create word document programmatically using C#. Learn how to add content
    control to word and set placeholder text word for dynamic templates.
  headline: Create word document programmatically – add content control and placeholder
  type: TechArticle
tags:
- C#
- Aspose.Words
- Word automation
title: Δημιουργία εγγράφου Word προγραμματιστικά – προσθήκη ελέγχου περιεχομένου και
  κράτησης θέσης
url: /el/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία εγγράφου Word προγραμματιστικά – προσθήκη ελέγχου περιεχομένου και κράτησης θέσης

Αν χρειάζεστε **create word document programmatically**, αυτό το tutorial σας δείχνει μια πλήρη, έτοιμη‑για‑εκτέλεση λύση. Θα δείτε πώς να **add content control to word**, να του δώσετε έναν περιγραφικό τίτλο και να **set placeholder text word** ώστε οι τελικοί χρήστες να μπορούν να συμπληρώνουν δεδομένα αργότερα.

Ο οδηγός περνάει από κάθε γραμμή κώδικα, εξηγεί γιατί κάθε βήμα είναι σημαντικό και επισημαίνει κοινά λάθη. Στο τέλος θα έχετε ένα επαναχρησιμοποιήσιμο αρχείο .docx που μπορεί να λειτουργήσει ως πρότυπο για τιμολόγια, συμβόλαια ή οποιοδήποτε έγγραφο βασισμένο σε φόρμες.

## Προαπαιτούμενα

* .NET 6.0 (ή νεότερο) εγκατεστημένο – ο κώδικας χρησιμοποιεί τις πιο πρόσφατες δυνατότητες της γλώσσας C#.
* Άδεια Aspose.Words για .NET (η δωρεάν δοκιμή λειτουργεί για ανάπτυξη).
* Visual Studio 2022 ή οποιοδήποτε IDE που μπορεί να δημιουργήσει έργα .NET.
* Βασική εξοικείωση με C# και την έννοια των Structured Document Tags (SDTs).

> **Pro tip:** Αν εκτελέσετε το παράδειγμα χωρίς άδεια, το Aspose.Words προσθέτει ένα μικρό υδατογράφημα στο αποθηκευμένο αρχείο. Εφαρμόστε την άδειά σας νωρίς στο πρόγραμμα για να το αποφύγετε.

## Βήμα 1: Ρύθμιση του έργου και εισαγωγή namespaces

Δημιουργήστε ένα νέο έργο console και προσθέστε το πακέτο NuGet Aspose.Words.

```bash
dotnet new console -n WordTemplateDemo
cd WordTemplateDemo
dotnet add package Aspose.Words
```

Τώρα εισάγετε τα απαιτούμενα namespaces στο `Program.cs`:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
```

Αυτά τα namespaces σας δίνουν πρόσβαση στις κλάσεις `Document`, `DocumentBuilder` και `StructuredDocumentTag`, που είναι απαραίτητες για **creating word document programmatically**.

## Βήμα 2: Αρχικοποίηση κενής εγγράφου και builder

Η κλάση `Document` αντιπροσωπεύει ολόκληρο το αρχείο .docx, ενώ η `DocumentBuilder` σας επιτρέπει να τοποθετήσετε περιεχόμενο σε συγκεκριμένη θέση του κέρσορα.

```csharp
// Step 2: Create an empty Word document
Document document = new Document();

// Step 2b: Initialize a DocumentBuilder for editing the document
DocumentBuilder builder = new DocumentBuilder(document);
```

*Why this matters*: Ξεκινώντας με ένα κενό `Document` εξασφαλίζετε πλήρη έλεγχο σε κάθε στοιχείο που εισάγετε. Η `DocumentBuilder` διατηρεί έναν εσωτερικό κέρσορα, ώστε να μπορείτε να εισάγετε κόμβους ακριβώς όπου χρειάζεται.

## Βήμα 3: Δημιουργία Structured Document Tag (SDT) απλού κειμένου

Ένα Structured Document Tag είναι το τεχνικό όνομα για ένα **content control** στο Word. Θα δημιουργήσουμε μια ενσωματωμένη ετικέτα απλού κειμένου που λειτουργεί ως πεδίο κράτησης θέσης.

```csharp
// Step 3: Create a plain‑text Structured Document Tag (content control)
StructuredDocumentTag plainTextTag = new StructuredDocumentTag(
    document,
    StructuredDocumentTagType.PlainText,   // plain‑text content control
    MarkupLevel.Inline);                    // appears inside a paragraph
```

*Why this matters*: Η χρήση του `StructuredDocumentTagType.PlainText` λέει στο Word ότι ο έλεγχος θα δέχεται μόνο απλό κείμενο. Το `MarkupLevel.Inline` κάνει τον έλεγχο να συμπεριφέρεται σαν μια κανονική λέξη μέσα σε παράγραφο, κάτι ιδανικό για πεδία φόρμας.

## Βήμα 4: Ανάθεση τίτλου και κειμένου κράτησης θέσης

Το **title** είναι ο εσωτερικός αναγνωριστικός κωδικός που η εφαρμογή σας μπορεί να ερωτήσει αργότερα. Το **placeholder** είναι η γκριζαρισμένη υπόδειξη που εμφανίζεται στον χρήστη πριν πληκτρολογήσει κάτι.

```csharp
// Step 4: Set a title and placeholder text for the content control
plainTextTag.Title = "CustomerName";          // internal name used by code
plainTextTag.PlaceholderName = "Enter name here"; // visible hint in the UI
```

Εδώ **set placeholder text word** σε “Enter name here”. Όταν το έγγραφο ανοίξει στο Microsoft Word, η κράτηση θέσης εμφανίζεται σε ανοιχτό γκρι μέχρι ο χρήστης πληκτρολογήσει μια τιμή.

## Βήμα 5: Εισαγωγή του ελέγχου περιεχομένου στην τρέχουσα θέση του κέρσορα

`DocumentBuilder.InsertNode` τοποθετεί το SDT ακριβώς εκεί που βρίσκεται ο κέρσορας του builder. Από προεπιλογή, ο κέρσορας είναι στην αρχή της πρώτης παραγράφου.

```csharp
// Step 5: Insert the content control into the document at the builder's current position
builder.InsertNode(plainTextTag);
```

Αν χρειάζεστε τον έλεγχο μέσα σε συγκεκριμένη παράγραφο, μετακινήστε πρώτα τον κέρσορα:

```csharp
builder.Writeln("Please provide the customer name:");
builder.InsertNode(plainTextTag);
```

Αυτό το παράδειγμα δείχνει πώς να **add content control to word** διατηρώντας το περιβάλλον κείμενο.

## Βήμα 6: Αποθήκευση του εγγράφου

Τέλος, αποθηκεύστε το αρχείο στο δίσκο. Μπορείτε να επιλέξετε οποιονδήποτε φάκελο· απλώς βεβαιωθείτε ότι η εφαρμογή έχει δικαίωμα εγγραφής.

```csharp
// Step 6: Save the document with the content control
string outputPath = @"YOUR_DIRECTORY\SDT.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Όταν ανοίξετε το `SDT.docx` στο Microsoft Word, θα δείτε την κράτηση θέσης “Enter name here” μέσα σε ένα ανοιχτό‑γκρι πλαίσιο. Οι χρήστες μπορούν να κάνουν κλικ στο πλαίσιο και να αντικαταστήσουν την υπόδειξη με το πραγματικό όνομα πελάτη.

## Πλήρες, εκτελέσιμο παράδειγμα

Παρακάτω είναι το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε, επικολλήσετε και εκτελέσετε χωρίς τροποποιήσεις (εκτός από τη διαδρομή εξόδου).

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Optional: apply your Aspose.Words license here
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create a new empty document
        Document document = new Document();

        // 2. Initialize a DocumentBuilder for editing the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3. Write a brief instruction line (optional)
        builder.Writeln("Please enter the customer's name below:");

        // 4. Create a plain‑text Structured Document Tag (content control)
        StructuredDocumentTag plainTextTag = new StructuredDocumentTag(
            document,
            StructuredDocumentTagType.PlainText,
            MarkupLevel.Inline);

        // 5. Set a title and placeholder text for the content control
        plainTextTag.Title = "CustomerName";
        plainTextTag.PlaceholderName = "Enter name here";

        // 6. Insert the content control at the current cursor position
        builder.InsertNode(plainTextTag);

        // 7. Save the document
        string outputPath = @"C:\Temp\SDT.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Expected output** – Όταν εκτελέσετε το πρόγραμμα, η κονσόλα εκτυπώνει τη διαδρομή του αρχείου, και το παραγόμενο αρχείο Word περιέχει μια μόνο γραμμή κειμένου ακολουθούμενη από μια γκρι κράτηση θέσης που γράφει “Enter name here”.

## Συνηθισμένες παραλλαγές και ειδικές περιπτώσεις

| Σενάριο | Πώς να προσαρμόσετε τον κώδικα |
|----------|-----------------------|
| **Multi‑line placeholder** | Χρησιμοποιήστε το `StructuredDocumentTagType.RichText` αντί για `PlainText` και ορίστε `plainTextTag.MultipleLines = true;`. |
| **Repeating the same control** | Κλωνοποιήστε την ετικέτα με `plainTextTag.Clone(true)` και εισάγετε το κλώνο όπου χρειάζεται. |
| **Binding to data source** | Αφού ο χρήστης συμπληρώσει το έγγραφο, ανακτήστε την τιμή με `document.GetChildNodes(NodeType.StructuredDocumentTag, true).Cast<StructuredDocumentTag>().First(t => t.Title == "CustomerName").GetText();`. |
| **Locking the control** | Ορίστε `plainTextTag.LockContentControl = true;` για να αποτρέψετε τους χρήστες από το να διαγράψουν τον έλεγχο. |
| **Changing placeholder color** | Το Word δεν εκθέτει το στυλ της κράτησης θέσης μέσω του SDK· πρέπει να επεξεργαστείτε το πρότυπο χειροκίνητα ή να χρησιμοποιήσετε μια μακροεντολή Word. |

## Καλές πρακτικές και αντιμετώπιση προβλημάτων

* **Always set a title** – Χωρίς τίτλο, η εύρεση του ελέγχου αργότερα γίνεται δύσκολη.
* **Avoid empty placeholders** – Το Word κρύβει μια κενή κράτηση θέσης αν η ιδιότητα `ShowPlaceholderText` του ελέγχου είναι false. Κρατήστε την true για καλύτερη εμπειρία χρήστη.
* **Validate the output path** – Αν το `document.Save` ρίξει `UnauthorizedAccessException`, βεβαιωθείτε ότι ο φάκελος υπάρχει και ότι η διαδικασία σας έχει δικαιώματα εγγραφής.
* **License early** – Τοποθετήστε τον κώδικα άδειας πριν δημιουργηθούν οποιαδήποτε αντικείμενα Aspose.Words για να αποτρέψετε το υδατογράφημα δοκιμής.

## Συμπέρασμα

Τώρα ξέρετε πώς να **create word document programmatically**, **add content control to word**, και **set placeholder text word** χρησιμοποιώντας το Aspose.Words για .NET. Το πλήρες παράδειγμα δείχνει κάθε απαιτούμενο βήμα, από την αρχικοποίηση του εγγράφου μέχρι την αποθήκευση ενός προτύπου που οι τελικοί χρήστες μπορούν να συμπληρώσουν.

Στη συνέχεια, μπορείτε να εξερευνήσετε:

* Προσθήκη **repeating content controls** για πίνακες (δευτερεύων λέξη-κλειδί: add content control to word).
* Συμπλήρωση των κρατήσεων θέσης με δεδομένα από βάση δεδομένων (δευτερεύων λέξη-κλειδί: set placeholder text word).
* Μετατροπή του παραγόμενου .docx σε PDF ή HTML για επεξεργασία downstream.

Μη διστάσετε να πειραματιστείτε με διαφορετικούς τύπους ετικετών, στυλ και τεχνικές σύνδεσης δεδομένων. Καλή προγραμματιστική!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετικές θεματικές που επεκτείνουν τις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετα χαρακτηριστικά του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Δημιουργία Νέου Εγγράφου Word](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Δημιουργία Εγγράφου Word με Κεφαλίδα και Υποσέλιδο Χρησιμοποιώντας Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Δημιουργία Εγγράφου Word με Πίνακα Χρησιμοποιώντας Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}