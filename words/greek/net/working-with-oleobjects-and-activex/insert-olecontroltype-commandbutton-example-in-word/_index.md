---
category: general
date: 2026-08-17
description: Εισαγωγή παραδείγματος OleControlType.CommandButton στο Word χρησιμοποιώντας
  το Aspose.Words. Μάθετε πώς να προσθέτετε στοιχεία ελέγχου φόρμας σε έγγραφο Word
  προγραμματιστικά.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert olecontroltype.commandbutton example
- how to add form controls to word document
- Aspose.Words ActiveX button
- C# Word automation
- programmatic form controls
language: el
lastmod: 2026-08-17
og_description: Εισαγάγετε το παράδειγμα OleControlType.CommandButton στο Word με
  το Aspose.Words. Ακολουθήστε αυτόν τον οδηγό για να προσθέσετε στοιχεία ελέγχου
  φόρμας σε ένα έγγραφο Word.
og_image_alt: Screenshot showing an ActiveX CommandButton inserted into a Word document
  using Aspose.Words
og_title: Εισαγωγή παραδείγματος OleControlType.CommandButton στο Word
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: Insert OleControlType.CommandButton example in Word using Aspose.Words.
    Learn how to add form controls to a Word document programmatically.
  headline: Insert OleControlType.CommandButton example in Word
  type: TechArticle
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Εισαγωγή παραδείγματος OleControlType.CommandButton στο Word
url: /el/net/working-with-oleobjects-and-activex/insert-olecontroltype-commandbutton-example-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Εισαγωγή παραδείγματος OleControlType.CommandButton στο Word

Αν χρειάζεστε **insert OleControlType.CommandButton example** σε ένα αρχείο Word, αυτός ο οδηγός σας δείχνει πώς. Θα μάθετε **πώς να προσθέτετε στοιχεία φόρμας σε ένα έγγραφο Word** χρησιμοποιώντας το Aspose.Words, με ένα πλήρες, εκτελέσιμο πρόγραμμα C#.

Στοιχεία φόρμας όπως τα κουμπιά ActiveX σας επιτρέπουν να δημιουργήσετε διαδραστικά πρότυπα Word—χρήσιμα για συμβάσεις, ερωτηματολόγια ή εσωτερικά εργαλεία. Τα παρακάτω βήματα καλύπτουν τα πάντα, από τη ρύθμιση του έργου μέχρι την επαλήθευση ότι το κουμπί εμφανίζεται σωστά στο αποθηκευμένο αρχείο `.docx`.

## Προαπαιτούμενα

- .NET 6.0 SDK ή νεότερο εγκατεστημένο  
- Visual Studio 2022 (ή οποιοδήποτε IDE C#)  
- Άδεια Aspose.Words για .NET ή δωρεάν προσωρινή άδεια  
- Βασική εξοικείωση με C# και έννοιες αρχείων Word  

> **Συμβουλή:** Εάν χρησιμοποιείτε τη δωρεάν δοκιμή, τοποθετήστε το αρχείο άδειας στον ίδιο φάκελο με το εκτελέσιμο και φορτώστε το στην αρχή του `Main`.

## Βήμα 1: Δημιουργήστε ένα νέο έργο console και προσθέστε το Aspose.Words

Ανοίξτε ένα τερματικό και εκτελέστε:

```bash
dotnet new console -n OleCommandButtonDemo
cd OleCommandButtonDemo
dotnet add package Aspose.Words
```

Αυτό δημιουργεί ένα καθαρό έργο και κατεβάζει το πιο πρόσφατο πακέτο Aspose.Words, το οποίο παρέχει τα API `Document`, `DocumentBuilder` και `InsertForms2OleControl` που απαιτούνται για το **insert OleControlType.CommandButton example**.

## Βήμα 2: Γράψτε το πλήρες πρόγραμμα

Δημιουργήστε ή αντικαταστήστε το `Program.cs` με τον παρακάτω κώδικα. Περιέχει όλες τις απαιτούμενες οδηγίες `using`, τη φόρτωση της άδειας και τη ροή εργασίας τεσσάρων βημάτων που φαίνεται στο αρχικό απόσπασμα.

```csharp
using System;
using System.Drawing;               // For Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;          // For OleControlType

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Optional: load a trial or commercial license.
        // -------------------------------------------------
        // var license = new Aspose.Words.License();
        // license.SetLicense("Aspose.Words.lic");

        // -------------------------------------------------
        // Step 1: Create a new blank document
        // -------------------------------------------------
        Document doc = new Document();

        // -------------------------------------------------
        // Step 2: Initialize a DocumentBuilder to work with the document
        // -------------------------------------------------
        DocumentBuilder builder = new DocumentBuilder(doc);

        // -------------------------------------------------
        // Step 3: Insert an ActiveX CommandButton control
        // -------------------------------------------------
        // OleControlType.CommandButton creates a CommandButton.
        // "ClickMe" is the control's name.
        // The Rectangle defines the button's position (x, y) and size (width, height).
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            "ClickMe",
            new Rectangle(100, 100, 80, 30));

        // -------------------------------------------------
        // Step 4: Save the document containing the ActiveX button
        // -------------------------------------------------
        string outputPath = "ActiveXButton.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### Γιατί κάθε γραμμή είναι σημαντική

* **License loading** – εξασφαλίζει ότι δεν περιορίζεστε από περιορισμούς αξιολόγησης.  
* **`Document doc = new Document();`** – δημιουργεί το δοχείο για όλο το περιεχόμενο Word· αυτό είναι η βάση του **insert OleControlType.CommandButton example**.  
* **`DocumentBuilder builder = new DocumentBuilder(doc);`** – παρέχει ένα fluent API για προσθήκη κειμένου, εικόνων και στοιχείων ελέγχου.  
* **`InsertForms2OleControl`** – η κύρια μέθοδος που υλοποιεί **how to add form controls to a Word document**. Η τιμή enum `OleControlType.CommandButton` λέει στο Aspose.Words να δημιουργήσει ένα κουμπί ActiveX.  
* **`new Rectangle(100, 100, 80, 30)`** – τοποθετεί το κουμπί 100 pt από τα αριστερά και πάνω περιθώρια, με πλάτος 80 pt και ύψος 30 pt. Προσαρμόστε αυτές τις τιμές ώστε να ταιριάζουν στη διάταξή σας.  
* **`doc.Save`** – γράφει το αρχείο .docx στο δίσκο· το αρχείο τώρα περιέχει το ενσωματωμένο κουμπί.

## Βήμα 3: Κατασκευάστε και εκτελέστε το πρόγραμμα

Από το φάκελο του έργου, εκτελέστε:

```bash
dotnet run
```

Θα πρέπει να δείτε το μήνυμα στην κονσόλα:

```
Document saved to ActiveXButton.docx
```

Ανοίξτε το `ActiveXButton.docx` στο Microsoft Word. Θα δείτε ένα κουμπί με την ετικέτα **ClickMe** τοποθετημένο περίπου στη μέση της σελίδας. Κάνοντας κλικ στο κουμπί ενεργοποιείται η προεπιλεγμένη συμπεριφορά του ActiveX (που συνήθως δεν κάνει τίποτα εκτός εάν συνδέσετε μια μακροεντολή).

![παράδειγμα insert olecontroltype.commandbutton](/images/activex-button.png "CommandButton ActiveX που έχει εισαχθεί σε έγγραφο Word")

*Κείμενο εναλλακτικής εικόνας:* παράδειγμα insert olecontroltype.commandbutton – ένα ActiveX CommandButton που εμφανίζεται σε έγγραφο Word.

## Βήμα 4: Προσαρμογή του κουμπιού (προαιρετικό)

Το βασικό **insert OleControlType.CommandButton example** δημιουργεί ένα προεπιλεγμένο κουμπί. Μπορείτε να τροποποιήσετε τη λεζάντα του, τη γραμματοσειρά ή ακόμη και να συνδέσετε μια μακροεντολή επεξεργάζοντας το υποκείμενο αντικείμενο OLE. Παρακάτω υπάρχει ένας σύντομος τρόπος για να αλλάξετε τη λεζάντα του κουμπιού μετά την εισαγωγή:

```csharp
// Retrieve the first shape (our button) from the document
Shape buttonShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

// Access the OLE format and set the caption
buttonShape.OleFormat.GetControl().SetProperty("Caption", "Submit");
```

> **Σημείωση:** Η άμεση διαχείριση των ιδιοτήτων OLE απαιτεί κατανόηση του υποκείμενου COM interface. Στις περισσότερες περιπτώσεις, η προεπιλεγμένη λεζάντα είναι επαρκής.

## Βήμα 5: Συνηθισμένα προβλήματα και πώς να τα αποφύγετε

| Πρόβλημα | Γιατί συμβαίνει | Διόρθωση |
|----------|------------------|----------|
| Το κουμπί δεν εμφανίζεται στο Word | Το έγγραφο αποθηκεύτηκε ως `.docx` αλλά ανοίχθηκε σε προβολέα που αφαιρεί τα στοιχεία OLE (π.χ., Google Docs). | Ανοίξτε το αρχείο στο Microsoft Word ή στο Word Online με δικαιώματα επεξεργασίας. |
| Σφάλμα χρόνου εκτέλεσης `ArgumentOutOfRangeException` | Οι συντεταγμένες `Rectangle` είναι εκτός των περιθωρίων της σελίδας. | Χρησιμοποιήστε τιμές εντός του μεγέθους σελίδας (π.χ., 0‑500 για A4). |
| Εξαίρεση άδειας | Μια δοκιμαστική άδεια λήγει μετά από 30 ημέρες. | Φορτώστε ένα έγκυρο αρχείο άδειας ή ζητήστε εκτεταμένη δοκιμή από την Aspose. |

## Βήμα 6: Πώς αυτό το παράδειγμα εντάσσεται σε μεγαλύτερα έργα αυτοματοποίησης

Όταν χρειάζεται να **how to add form controls to Word document** σε μεγάλη κλίμακα—όπως η δημιουργία εκατοντάδων προτύπων συμβάσεων—τυλίξτε τη λογική εισαγωγής σε μια επαναχρησιμοποιήσιμη μέθοδο:

```csharp
static void AddCommandButton(DocumentBuilder builder, string name, Rectangle bounds)
{
    builder.InsertForms2OleControl(OleControlType.CommandButton, name, bounds);
}
```

Μπορείτε στη συνέχεια να καλέσετε το `AddCommandButton` μέσα σε βρόχους που επεξεργάζονται σειρές δεδομένων, εξασφαλίζοντας ότι κάθε παραγόμενο έγγραφο περιέχει ένα μοναδικά ονομασμένο κουμπί (π.χ., `Approve_001`, `Approve_002`).

## Συμπέρασμα

Τώρα έχετε ένα πλήρες **insert OleControlType.CommandButton example** που δείχνει **how to add form controls to a Word document** χρησιμοποιώντας το Aspose.Words για .NET. Ο οδηγός κάλυψε τη ρύθμιση του έργου, τον πλήρη πηγαίο κώδικα, συμβουλές προσαρμογής και κοινά βήματα αντιμετώπισης προβλημάτων.

Από εδώ μπορείτε να εξερευνήσετε:

- Προσθήκη άλλων τύπων ελέγχου όπως **CheckBox** ή **ComboBox** (`OleControlType.CheckBox`, `OleControlType.ComboBox`).  
- Σύνδεση του κουμπιού με μια μακροεντολή VBA για πιο πλούσια διαδραστικότητα.  
- Δημιουργία PDF από το ίδιο έγγραφο διατηρώντας τα πεδία φόρμας.

Δοκιμάστε διαφορετικά μεγέθη, θέσεις και ονόματα ελέγχου ώστε να ταιριάζουν στην ειδική σας περίπτωση χρήσης. Καλή προγραμματιστική!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Εισαγωγή πεδίου φόρμας Combo Box σε έγγραφο Word](/words/english/net/add-content-using-documentbuilder/insert-combo-box-form-field/)
- [Εισαγωγή πεδίου φόρμας Check Box σε έγγραφο Word](/words/english/net/add-content-using-documentbuilder/insert-check-box-form-field/)
- [Εισαγωγή πεδίου φόρμας Text Input σε έγγραφο Word](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}