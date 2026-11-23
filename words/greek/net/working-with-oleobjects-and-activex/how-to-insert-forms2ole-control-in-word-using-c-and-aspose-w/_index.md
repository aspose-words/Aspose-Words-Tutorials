---
category: general
date: 2026-11-22
description: Μάθετε πώς να εισάγετε έναν έλεγχο Forms2Ole στο Word με C#. Αυτός ο
  οδηγός βήμα‑βήμα καλύπτει το DocumentBuilder, την τοποθέτηση κουμπιού εντολής και
  την αποθήκευση του .docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert forms2ole control word
- Aspose.Words
- DocumentBuilder
- command button
- C# Word automation
language: el
lastmod: 2026-11-22
og_description: Εισαγάγετε τον έλεγχο Forms2Ole στο Word με C#. Ακολουθήστε αυτόν
  τον οδηγό για να προσθέσετε ένα κουμπί εντολής χρησιμοποιώντας το Aspose.Words και
  το DocumentBuilder.
og_image_alt: Screenshot of a Word document showing an inserted Forms2Ole command
  button created with C#
og_title: Εισαγωγή του ελέγχου Forms2Ole στο Word με C# – πλήρης οδηγός
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn to insert a Forms2Ole control in Word with C#. This step‑by‑step
    guide covers DocumentBuilder, command button placement, and saving the .docx.
  headline: How to insert Forms2Ole control in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Πώς να εισαγάγετε τον έλεγχο Forms2Ole στο Word χρησιμοποιώντας C# και Aspose.Words
url: /el/net/working-with-oleobjects-and-activex/how-to-insert-forms2ole-control-in-word-using-c-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να εισαγάγετε το Forms2Ole control στο Word χρησιμοποιώντας C# και Aspose.Words

Αν χρειάζεστε να **εισάγετε το Forms2Ole control στο Word**, αυτό το tutorial σας δείχνει ακριβώς πώς να το κάνετε με C#. Είτε δημιουργείτε ένα συμπληρώσιμο πρότυπο είτε αυτοματοποιείτε τη δημιουργία φορμών, η παρακάτω λύση σας επιτρέπει να προσθέσετε ένα κουμπί εντολής προγραμματιστικά.

Θα μάθετε πώς να δημιουργήσετε ένα κενό έγγραφο, να χρησιμοποιήσετε το `DocumentBuilder` για να τοποθετήσετε το control, και να αποθηκεύσετε το αποτέλεσμα ως `.docx`. Ο οδηγός καλύπτει επίσης κοινά προβλήματα, όπως τα συστήματα συντεταγμένων και τη συμβατότητα με παλαιότερες εκδόσεις του Word.

## Προαπαιτούμενα

* .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.6+)
* Aspose.Words for .NET (πακέτο NuGet `Aspose.Words`)
* Βασική κατανόηση του C# και του μοντέλου αντικειμένων του Word
* Ένα IDE όπως το Visual Studio ή το VS Code

## Βήμα 1: Ρύθμιση του έργου και εισαγωγή namespaces

Δημιουργήστε μια νέα εφαρμογή κονσόλας και προσθέστε το πακέτο Aspose.Words:

```bash
dotnet new console -n InsertForms2OleDemo
cd InsertForms2OleDemo
dotnet add package Aspose.Words
```

Στο `Program.cs` εισάγετε τα απαιτούμενα namespaces:

```csharp
using System;
using System.Drawing;               // for Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;        // for Forms2OleControl
```

> **Συμβουλή:** Χρησιμοποιήστε την πιο πρόσφατη έκδοση του Aspose.Words για πλήρη υποστήριξη του API `Forms2OleControl`.

## Βήμα 2: Δημιουργία κενής εγγράφου και αρχικοποίηση του DocumentBuilder

Η κλάση `Document` αντιπροσωπεύει το αρχείο Word, ενώ το `DocumentBuilder` παρέχει μεθόδους για την εισαγωγή περιεχομένου.

```csharp
// Step 2: Create a new blank document
Document doc = new Document();

// Initialize DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` λειτουργεί όπως ένας κέρσορας· μετά από αυτή τη γραμμή μπορείτε να αρχίσετε να τοποθετείτε στοιχεία οπουδήποτε στο έγγραφο.

## Βήμα 3: Καθορισμός θέσης και μεγέθους του κουμπιού

Το Word μετρά τις συντεταγμένες σε σημεία (1 pt ≈ 1/72 in). Η δομή `Rectangle` από το `System.Drawing` περιγράφει τα όρια του control.

```csharp
// Step 3: Define the button's position and size (x, y, width, height)
Rectangle buttonBounds = new Rectangle(0, 0, 100, 30); // 100 pt wide, 30 pt tall
```

* `0,0` τοποθετεί το control στην επάνω‑αριστερή γωνία της τρέχουσας σελίδας.
* Προσαρμόστε τα `x` και `y` για να μετακινήσετε το κουμπί αλλού (π.χ., `new Rectangle(150, 200, 100, 30)`).

## Βήμα 4: Εισαγωγή του κουμπιού εντολής Forms2Ole

Τώρα χρησιμοποιήστε το `InsertForms2OleControl` για να προσθέσετε το control. Η μέθοδος απαιτεί τον τύπο του control, ένα όνομα και τα όρια που ορίστηκαν παραπάνω.

```csharp
// Step 4: Insert a Forms2Ole command button named "ClickMe"
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,   // type of control
    "ClickMe",                  // internal name (used for VBA or macros)
    buttonBounds);              // position and size
```

Το αντικείμενο `Forms2OleControl` που επιστρέφεται σας επιτρέπει να τροποποιήσετε ιδιότητες όπως `Enabled`, `Visible`, ή ακόμη και να συνδέσετε ένα όνομα μακροεντολής αργότερα.

### Γιατί να χρησιμοποιήσετε Forms2Ole;

* **Legacy compatibility** – Τα Controls Forms2Ole λειτουργούν σε Word 97‑2003 (`.doc`) και σε νεότερα αρχεία `.docx`.
* **Macro support** – Μπορούν να ενεργοποιήσουν μακροεντολές VBA, καθιστώντας τα ιδανικά για διαδραστικά πρότυπα.
* **Precise placement** – Σε αντίθεση με τα content controls, ελέγχετε ακριβείς συντεταγμένες.

## Βήμα 5: Αποθήκευση του εγγράφου

Τέλος, γράψτε το αρχείο στο δίσκο. Επιλέξτε έναν φάκελο στον οποίο έχετε δικαίωμα εγγραφής.

```csharp
// Step 5: Save the document to see the inserted button
string outputPath = @"./output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Ανοίξτε το `output.docx` στο Microsoft Word. Θα δείτε ένα κουμπί με την ετικέτα **ClickMe** στην επάνω‑αριστερή γωνία της πρώτης σελίδας. Κάνοντας κλικ σε αυτό στο Word δεν θα συμβεί τίποτα μέχρι να αντιστοιχίσετε μια μακροεντολή, αλλά το control λειτουργεί πλήρως.

## Διαχείριση κοινών περιπτώσεων άκρων

| Situation | How to address it |
|-----------|-------------------|
| **Το κουμπί εμφανίζεται εκτός σελίδας** | Επαληθεύστε ότι οι συντεταγμένες του `Rectangle` βρίσκονται εντός των περιθωρίων της σελίδας. Χρησιμοποιήστε `builder.PageSetup.PageWidth` και `PageHeight` για να υπολογίσετε ασφαλή όρια. |
| **Το control δεν είναι ορατό σε παλαιότερες εκδόσεις του Word** | Αποθηκεύστε το έγγραφο ως `.doc` (`doc.Save("output.doc", SaveFormat.Doc)`) για να εξασφαλίσετε τη συμβατότητα Forms2Ole με το Word 97‑2003. |
| **Απαιτείται αλλαγή της λεζάντας** | Μετά την εισαγωγή, ορίστε `commandButton.Caption = "Submit";`. |
| **Ανάθεση μακροεντολής** | Ορίστε `commandButton.MacroName = "MyMacro"`· η μακροεντολή πρέπει να υπάρχει στο VBA project του εγγράφου. |
| **Πολλαπλά κουμπιά** | Επαναλάβετε το Βήμα 4 με διαφορετικές τιμές `Rectangle` και μοναδικά ονόματα. |

## Πλήρες, εκτελέσιμο παράδειγμα

Συνδυάζοντας όλα, εδώ είναι ένα αυτόνομο πρόγραμμα που μπορείτε να αντιγράψετε, να επικολλήσετε και να εκτελέσετε:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace InsertForms2OleDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document
            Document doc = new Document();

            // Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Define button bounds (x, y, width, height) in points
            Rectangle buttonBounds = new Rectangle(0, 0, 100, 30);

            // Insert a Forms2Ole command button named "ClickMe"
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                "ClickMe",
                buttonBounds);

            // Optional: set button caption
            commandButton.Caption = "Click Me!";

            // Save the document
            string outputPath = "output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Αναμενόμενο αποτέλεσμα:** Μετά την εκτέλεση του προγράμματος, το `output.docx` ανοίγει στο Word με ένα κλικ‑με δυνατό κουμπί με ετικέτα *Click Me!* τοποθετημένο στην επάνω‑αριστερή γωνία της πρώτης σελίδας.

## Συμπέρασμα

Τώρα ξέρετε πώς να **εισάγετε το Forms2Ole control στο Word** χρησιμοποιώντας C# και Aspose.Words. Η διαδικασία περιλαμβάνει τη δημιουργία ενός `Document`, την τοποθέτηση ενός `Rectangle` και την κλήση του `InsertForms2OleControl` μέσω του `DocumentBuilder`. Με το πλήρες παράδειγμα κώδικα και τις οδηγίες για ειδικές περιπτώσεις, μπορείτε να ενσωματώσετε κουμπιά εντολής σε οποιαδήποτε αυτοματοποιημένη ροή εργασίας του Word.

### Επόμενα βήματα

* Εξερευνήστε άλλες τιμές `ControlType` όπως `CheckBox` ή `OptionButton`.
* Συνδυάστε τα Forms2Ole controls με μακροεντολές VBA για διαδραστικές φόρμες.
* Χρησιμοποιήστε το `DocumentBuilder.MoveTo` για να τοποθετήσετε κουμπιά σε συγκεκριμένες παραγράφους ή πίνακες.
* Ανασκοπήστε την τεκμηρίωση **Forms2Ole** του Aspose.Words για προχωρημένες ρυθμίσεις ιδιοτήτων.

Καλό προγραμματισμό, και απολαύστε τη δημιουργία πιο πλούσιων εγγράφων Word με C# και Aspose.Words!

## Τι Θα Πρέπει Να Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να εισαγάγετε κουμπί εντολής OLE σε έγγραφο Word χρησιμοποιώντας C#](/words/english/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/)
- [πώς να προσθέσετε activex control στο Word με Aspose.Words – οδηγός βήμα‑βήμα](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-control-in-word-with-aspose-words-step-by/)
- [Προσθήκη κουμπιού εντολής σε έγγραφο Word με Aspose.Words – Πλήρης Οδηγός](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}