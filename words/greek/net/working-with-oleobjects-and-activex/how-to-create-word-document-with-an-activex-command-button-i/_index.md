---
category: general
date: 2026-09-05
description: Δημιουργήστε έγγραφο Word χρησιμοποιώντας το Aspose.Words C# και μάθετε
  πώς να εισάγετε κουμπί εντολής ActiveX, να ορίσετε το μέγεθος του κουμπιού και να
  προσθέσετε διαδραστική λειτουργία κουμπιού.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to insert activex
- add command button
- add interactive button
- set button size
language: el
lastmod: 2026-09-05
og_description: Δημιουργήστε έγγραφο Word σε C# και εισάγετε ένα κουμπί εντολής ActiveX.
  Αυτό το σεμινάριο δείχνει πώς να ορίσετε το μέγεθος του κουμπιού και να προσθέσετε
  διαδραστικές λειτουργίες κουμπιού.
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
  created with C#
og_title: Δημιουργία εγγράφου Word με κουμπί εντολής ActiveX σε C# – οδηγός βήμα‑προς‑βήμα
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  headline: How to create Word document with an ActiveX command button in C#
  type: TechArticle
- description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  name: How to create Word document with an ActiveX command button in C#
  steps:
  - name: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
    text: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
  - name: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
    text: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
  - name: '**Configure the button** – caption, size, and position.'
    text: '**Configure the button** – caption, size, and position.'
  - name: '**Save** the document to disk.'
    text: '**Save** the document to disk.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
- UI controls
title: Πώς να δημιουργήσετε έγγραφο Word με κουμπί εντολής ActiveX σε C#
url: /el/net/working-with-oleobjects-and-activex/how-to-create-word-document-with-an-activex-command-button-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε έγγραφο Word με κουμπί εντολής ActiveX σε C#

Αν χρειάζεστε να **δημιουργήσετε έγγραφο Word** προγραμματιστικά και να ενσωματώσετε ένα κλικαρίσιμο στοιχείο UI, αυτός ο οδηγός σας δείχνει ακριβώς πώς. Χρησιμοποιώντας το Aspose.Words for .NET μπορείτε να **δημιουργήσετε έγγραφο Word**, **προσθέσετε κουμπί εντολής**, και να ελέγξετε την εμφάνισή του—όλα χωρίς να ανοίξετε το Microsoft Word.

Θα μάθετε **πώς να εισάγετε ελέγχους ActiveX**, **να ορίσετε το μέγεθος του κουμπιού**, και να κάνετε το κουμπί να συμπεριφέρεται ως διαδραστικό στοιχείο UI. Δεν απαιτείται προγενέστερη εμπειρία με COM ή VBA· απλώς ένα περιβάλλον ανάπτυξης .NET και η βιβλιοθήκη Aspose.Words.

## Τι θα επιτύχετε

* **Δημιουργήστε ένα έγγραφο Word** από το μηδέν με C#.
* **Εισάγετε ένα κουμπί εντολής ActiveX** (ο κλασικός έλεγχος “Click Me”).
* **Ορίστε το μέγεθος του κουμπιού** και τη θέση του με ακρίβεια.
* Προαιρετικά προσθέστε απλή λογική **διαδραστικού κουμπιού** (π.χ., ένα placeholder μακροεντολής).
* Αποθηκεύστε το αρχείο ως `.docx` που μπορεί να ανοιχθεί στο Microsoft Word ή σε οποιονδήποτε συμβατό προβολέα.

### Προαπαιτούμενα

| Απαίτηση | Αιτία |
|-------------|--------|
| .NET 6.0 ή νεότερο | Παρέχει το runtime για κώδικα C#. |
| Aspose.Words for .NET (latest version) | Παρέχει τα API `Document`, `DocumentBuilder` και `Forms2OleControl` που χρησιμοποιούνται στο παράδειγμα. |
| Visual Studio 2022 (or any C# IDE) | Διευκολύνει τη μεταγλώττιση και την εκτέλεση του δείγματος. |
| Basic C# knowledge | Απαιτείται για την κατανόηση της ροής του κώδικα. |

> **Συμβουλή:** Εάν χρησιμοποιείτε δοκιμαστική έκδοση του Aspose.Words, βεβαιωθείτε ότι έχετε ορίσει την άδεια πριν τρέξετε τον κώδικα για να αποφύγετε υδατογραφήματα αξιολόγησης.

## Πώς να δημιουργήσετε έγγραφο Word – γενική ροή εργασίας

Η διαδικασία αποτελείται από τέσσερα λογικά βήματα:

1. **Αρχικοποιήστε ένα νέο έγγραφο** και ένα `DocumentBuilder` για την επεξεργασία του.  
2. **Εισάγετε ένα κουμπί εντολής ActiveX** χρησιμοποιώντας το `InsertForms2OleControl`.  
3. **Διαμορφώστε το κουμπί** – λεζάντα, μέγεθος και θέση.  
4. **Αποθηκεύστε** το έγγραφο στο δίσκο.

Κάθε βήμα εξηγείται στην δική του ενότητα παρακάτω.

![Έγγραφο Word με κουμπί ActiveX](/images/activex-button.png "Στιγμιότυπο οθόνης ενός εγγράφου Word που περιέχει κουμπί εντολής ActiveX δημιουργημένο με C#")

## Πώς να εισάγετε κουμπί εντολής ActiveX

Το τμήμα **πώς να εισάγετε activex** ξεκινά με τη μέθοδο `InsertForms2OleControl`. Αυτή η μέθοδος δημιουργεί έναν έλεγχο βασισμένο σε COM που το Word αντιμετωπίζει ως αντικείμενο ActiveX.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// 1️⃣ Create a blank document and a builder.
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 2️⃣ Insert an ActiveX CommandButton control.
//    Parameters: control type, width, height, left, top (all in points).
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // ActiveX type
    150,                           // Width (points)
    100,                           // Height (points)
    50,                            // Left offset from page margin
    50);                           // Top offset from page margin
```

**Γιατί λειτουργεί:** `OleControlType.CommandButton` λέει στο Aspose.Words να δημιουργήσει το κλασικό κουμπί τύπου VB. Το μέγεθος και η θέση εκφράζονται σε points (1 point = 1/72 ίντσας), κάτι που παρέχει ακριβή έλεγχο της διάταξης.

## Πώς να προσθέσετε κουμπί εντολής και να ορίσετε το μέγεθος του κουμπιού

Αφού εισαχθεί ο έλεγχος, μπορείτε να προσαρμόσετε τις οπτικές του ιδιότητες. Το βήμα **προσθήκη κουμπιού εντολής** καλύπτει επίσης **ορισμό μεγέθους κουμπιού**.

```csharp
// 3️⃣ Set the button's caption – the text the user sees.
commandButton.Caption = "Click Me";

// 4️⃣ Optionally change size after insertion (if you need dynamic sizing).
//    Width and height are mutable properties.
commandButton.Width = 200;   // New width in points
commandButton.Height = 80;   // New height in points

// 5️⃣ Move the button if you need a different position.
commandButton.Left = 100;    // New left offset
commandButton.Top = 120;     // New top offset
```

**Explanation:**  

* `Caption` είναι η ετικέτα που εμφανίζεται στο κουμπί.  
* `Width` και `Height` σας επιτρέπουν να **ορίσετε το μέγεθος του κουμπιού** μετά την αρχική εισαγωγή—χρήσιμο όταν το μέγεθος εξαρτάται από δεδομένα χρόνου εκτέλεσης.  
* `Left` και `Top` μετατοπίζουν τον έλεγχο χωρίς να δημιουργήσετε ξανά το έγγραφο.

> **Κοινό λάθος:** Η παράλειψη χρήσης points αντί για pixels θα κάνει το κουμπί να εμφανίζεται πολύ μικρό ή πολύ μεγάλο. Πάντα μετατρέψτε τις τιμές pixel (`px * 72 / DPI`) εάν ξεκινάτε από μετρήσεις οθόνης.

## Πώς να προσθέσετε διαδραστικό κουμπί (προαιρετικό)

Ένα κουμπί ActiveX μπορεί να εκτελεί μια μακροεντολή όταν κάνετε κλικ, αλλά η ενσωμάτωση κώδικα VBA από C# δεν περιλαμβάνεται σε μια καθαρή ροή εργασίας Aspose.Words. Αντίθετα, μπορείτε να προσθέσετε μια ιδιότητα placeholder που το Word θα αναγνωρίσει ως όνομα μακροεντολής.

```csharp
// 6️⃣ Assign a macro name (the macro must exist in the Word template).
commandButton.OleFormat.Object = "MyMacroName";
```

Όταν ο χρήστης ανοίξει το παραγόμενο `.docx` στο Word, το κλικ στο κουμπί θα προσπαθήσει να εκτελέσει το `MyMacroName`. Εάν η μακροεντολή δεν υπάρχει, το Word θα ζητήσει από τον χρήστη να τη δημιουργήσει.

**Γιατί μπορεί να το χρησιμοποιήσετε:** Για εταιρικές φόρμες όπου μια μακροεντολή συμπληρώνει πεδία, ο κώδικας C# χρειάζεται μόνο να τοποθετήσει το κουμπί· η λογική της μακροεντολής ζει στο VBA project του εγγράφου.

## Αποθηκεύστε το έγγραφο και επαληθεύστε το αποτέλεσμα

```csharp
// 7️⃣ Save the document to the desired folder.
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), "CommandButton.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

**Αναμενόμενο αποτέλεσμα:** Το άνοιγμα του `CommandButton.docx` στο Microsoft Word εμφανίζει ένα κουμπί με την ετικέτα **Click Me** τοποθετημένο 100 pts από το αριστερό περιθώριο και 120 pts από την κορυφή. Οι διαστάσεις του κουμπιού είναι **200 pts × 80 pts**. Το κλικ στο κουμπί ενεργοποιεί το placeholder της μακροεντολής (εάν υπάρχει).

## Πλήρες λειτουργικό παράδειγμα

Παρακάτω βρίσκεται το πλήρες, εκτελέσιμο πρόγραμμα που συνδυάζει όλα. Αντιγράψτε το σε ένα νέο έργο Console App, προσθέστε το πακέτο NuGet Aspose.Words, και τρέξτε το.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton, // ActiveX type
            150,                         // Initial width
            100,                         // Initial height
            50,                          // Left offset
            50);                         // Top offset

        // Set button caption and resize.
        commandButton.Caption = "Click Me";
        commandButton.Width = 200;   // Set button size (width)
        commandButton.Height = 80;   // Set button size (height)
        commandButton.Left = 100;    // Re‑position horizontally
        commandButton.Top = 120;     // Re‑position vertically

        // Optional: link to a macro named MyMacroName.
        commandButton.OleFormat.Object = "MyMacroName";

        // Save the document.
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Τρέξτε το πρόγραμμα, μετά ανοίξτε το παραγόμενο αρχείο. Θα δείτε το **διαδραστικό κουμπί** έτοιμο για περαιτέρω προσαρμογή.

## Συχνές ερωτήσεις

| Ερώτηση | Απάντηση |
|----------|--------|
| **Λειτουργεί αυτό με .NET Core;** | Ναι. Το Aspose.Words υποστηρίζει .NET Standard, έτσι ο ίδιος κώδικας εκτελείται σε .NET 5/6/7. |
| **Μπορώ να χρησιμοποιήσω άλλους ελέγχους ActiveX (π.χ., CheckBox);** | Απολύτως. Αντικαταστήστε το `OleControlType.CommandButton` με `OleControlType.CheckBox`, `OleControlType.OptionButton`, κ.λπ. |
| **Τι γίνεται αν χρειάζομαι μεγαλύτερο κουμπί σε σελίδα τοπίου;** | Ρυθμίστε τις ιδιότητες `Width`, `Height`, `Left` και `Top` αναλογικά. Θυμηθείτε ότι τα points παραμένουν τα ίδια ανεξάρτητα από την προσανατολισμό της σελίδας. |
| **Απαιτείται μακροεντολή για να είναι κλικαρίσιμο το κουμπί;** | Όχι. Το κουμπί λειτουργεί πλήρως ως στοιχείο UI· μια μακροεντολή προσθέτει μόνο προσαρμοσμένη συμπεριφορά όταν γίνεται κλικ. |

## Συμπέρασμα

Τώρα γνωρίζετε πώς να **δημιουργήσετε έγγραφο Word** με το Aspose.Words, **προσθέσετε κουμπί εντολής**, **ορίσετε το μέγεθος του κουμπιού**, και προαιρετικά να συνδέσετε το κουμπί με μια μακροεντολή για συμπεριφορά **προσθήκης διαδραστικού κουμπιού**. Αυτή η προσέγγιση σας επιτρέπει να αυτοματοποιήσετε τη δημιουργία φορμών, να παράγετε δυναμικές αναφορές ή να δημιουργήσετε πρωτότυπα UI βασισμένα σε Word απευθείας από C#.

Στη συνέχεια, μπορείτε να εξερευνήσετε:

* **Πώς να εισάγετε ActiveX check boxes** για φόρμες έρευνας.  
* **Πώς να προσθέσετε περιεχόμενο εμπλουτισμένου κειμένου** γύρω από το κουμπί χρησιμοποιώντας το `DocumentBuilder`.  
* **Πώς να προστατεύσετε το έγγραφο** διατηρώντας το κουμπί λειτουργικό.  

Μη διστάσετε να πειραματιστείτε με διαφορετικούς τύπους ελέγχων, μεγέθη και ονόματα μακροεντολών ώστε να ταιριάζουν στο συγκεκριμένο σενάριό σας. Καλή προγραμματιστική!

## Τι θα πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετικά θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Δημιουργία εγγράφου Word με Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Εισαγωγή ενσωματωμένης εικόνας σε έγγραφο Word χρησιμοποιώντας Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Δημιουργία εγγράφου Word με πίνακα χρησιμοποιώντας Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}