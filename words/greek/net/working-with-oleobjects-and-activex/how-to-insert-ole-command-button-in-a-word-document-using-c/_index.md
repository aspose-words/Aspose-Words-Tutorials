---
category: general
date: 2026-10-07
description: Μάθετε πώς να εισάγετε ένα κουμπί εντολής OLE σε ένα έγγραφο Word με
  το Aspose.Words C#. Οδηγός βήμα‑βήμα που καλύπτει το DocumentBuilder, τις ιδιότητες
  και την αποθήκευση του αρχείου.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert OLE command button
- Aspose.Words OLE control
- C# DocumentBuilder InsertForms2OleControl
- OleControlType CommandButton
- Word OLE command button
language: el
lastmod: 2026-10-07
og_description: Εισαγάγετε κουμπί εντολής OLE σε ένα έγγραφο Word χρησιμοποιώντας
  C#. Ακολουθήστε αυτό το σύντομο σεμινάριο για να προσθέσετε, διαμορφώσετε και αποθηκεύσετε
  ένα λειτουργικό CommandButton με το Aspose.Words.
og_image_alt: Insert OLE command button example in Word document
og_title: Εισαγωγή κουμπιού εντολής OLE στο Word με C# – πλήρης οδηγός Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  headline: How to insert OLE command button in a Word document using C#
  type: TechArticle
- description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  name: How to insert OLE command button in a Word document using C#
  steps:
  - name: Why this works
    text: '* `DocumentBuilder` is the primary API for building Word documents programmatically.
      * `InsertForms2OleControl` tells Aspose.Words to embed a **Forms2 OLE control**,
      which is the legacy Word form technology that supports command buttons, check
      boxes, etc. * The `OleControlType.CommandButton` enum va'
  - name: 1. What if the button does not appear where I expect?
    text: '* Word uses points, not pixels. Convert screen pixels to points (`points
      = pixels * 72 / DPI`). * Ensure the rectangle does not intersect page margins;
      otherwise Word may shift the control.'
  - name: 2. Can I insert the button into an existing document?
    text: Yes. Load the document with `new Document("Existing.docx")` and use the
      same `DocumentBuilder` workflow. Just remember to move the builder’s cursor
      (`builder.MoveToDocumentEnd()`, `builder.MoveToBookmark("myBookmark")`, etc.)
      before calling `InsertForms2OleControl`.
  - name: 3. How do I attach a macro to the button?
    text: 'Aspose.Words does not create VBA code, but you can embed a macro after
      the document is generated:'
  - name: 4. Does this work with .NET Core on Linux?
    text: The OLE control is a Windows‑specific feature because it relies on COM.
      On Linux the button will be inserted, but it will appear as a static picture
      without interactive behavior. For cross‑platform interactive forms, consider
      using content controls (`StructuredDocumentTag`) instead.
  - name: 5. What if I need a different size or multiple buttons?
    text: Create additional `Rectangle` objects with unique coordinates and repeat
      the `InsertForms2OleControl` call. Each button can have its own `Caption` and
      `Name`.
  type: HowTo
tags:
- Aspose.Words
- C#
- OLE
- Word automation
title: Πώς να εισάγετε κουμπί εντολής OLE σε έγγραφο Word χρησιμοποιώντας C#
url: /el/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να εισάγετε κουμπί εντολής OLE σε έγγραφο Word χρησιμοποιώντας C#

Αν χρειάζεστε να **εισάγετε κουμπί εντολής OLE** σε αρχείο Word προγραμματιστικά, αυτός ο οδηγός σας δείχνει ακριβώς πώς να το κάνετε με το Aspose.Words for .NET. Είτε δημιουργείτε μια αναφορά με έντυπα είτε αυτοματοποιείτε ένα πρότυπο που απαιτεί αλληλεπίδραση χρήστη, τα παρακάτω βήματα σας παρέχουν μια πλήρη, εκτελέσιμη λύση.

Θα μάθετε πώς να δημιουργήσετε ένα κενό έγγραφο, να χρησιμοποιήσετε το `DocumentBuilder` για να τοποθετήσετε ένα `Forms2OleControl`, να ορίσετε τη λεζάντα και το όνομα του κουμπιού και, τέλος, να αποθηκεύσετε το `.docx`. Δεν απαιτούνται εξωτερικά εργαλεία πέρα από τη βιβλιοθήκη Aspose.Words.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* .NET 6.0 ή νεότερη έκδοση (ο κώδικας λειτουργεί επίσης με .NET Framework 4.7+)
* Ένα έγκυρο license του Aspose.Words for .NET ή ένα δωρεάν κλειδί αξιολόγησης
* Visual Studio 2022 (ή οποιοδήποτε IDE C# προτιμάτε)
* Βασική εξοικείωση με τη σύνταξη C# και τις έννοιες OLE του Word

> **Pro tip:** Εάν χρησιμοποιείτε την δωρεάν αξιολόγηση, το παραγόμενο έγγραφο θα περιέχει ένα μικρό υδατογράφημα. Μια αδειοδοτημένη έκδοση το αφαιρεί αυτόματα.

## Βήμα 1: Εγκατάσταση Aspose.Words

Προσθέστε το πακέτο Aspose.Words στο έργο σας μέσω NuGet:

```bash
dotnet add package Aspose.Words
```

Το πακέτο περιλαμβάνει τα namespaces `Aspose.Words.Drawing` και `Aspose.Words.Drawing.Ole` που απαιτούνται για τα OLE controls.

## Βήμα 2: Εισαγωγή κουμπιού εντολής OLE με DocumentBuilder

Ο πυρήνας του tutorial είναι η μέθοδος `InsertForms2OleControl`. Δημιουργεί ένα **Forms2 OLE CommandButton** σε συγκεκριμένη θέση και μέγεθος.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
using System.Drawing;

// Create a new blank document and a DocumentBuilder to edit it
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Define the rectangle where the button will appear (x, y, width, height)
// Values are in points (1 point = 1/72 inch)
Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

// Insert the Forms2 OLE CommandButton control
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // <-- OleControlType CommandButton (secondary keyword)
    buttonRect);

// Set the button's caption and name properties
commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";
```

### Γιατί λειτουργεί αυτό

* Το `DocumentBuilder` είναι το κύριο API για τη δημιουργία εγγράφων Word προγραμματιστικά.  
* Η `InsertForms2OleControl` λέει στο Aspose.Words να ενσωματώσει ένα **Forms2 OLE control**, που είναι η παλαιότερη τεχνολογία φορμών του Word που υποστηρίζει κουμπιά εντολών, πλαίσια ελέγχου κ.λπ.  
* Η τιμή του enum `OleControlType.CommandButton` καθορίζει ότι το εισαχθέν control είναι **κουμπί εντολής** — ακριβώς ο τύπος που ζητήσατε όταν ήθελατε να **εισάγετε κουμπί εντολής OLE**.  
* Το `Rectangle` καθορίζει την οπτική τοποθέτηση. Προσαρμόστε τις συντεταγμένες X/Y ή το πλάτος/ύψος ώστε να ταιριάζει με τη διάταξή σας.

## Βήμα 3: Αποθήκευση του εγγράφου

Αφού διαμορφώσετε το κουμπί, γράψτε το έγγραφο στο δίσκο. Μπορείτε να επιλέξετε οποιαδήποτε μορφή υποστηρίζεται από το Aspose.Words (`.docx`, `.pdf`, `.odt`, …). Για αυτό το tutorial θα αποθηκεύσουμε ως έγγραφο Word.

```csharp
// Choose a folder you have write access to
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");

// Save the document containing the button
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Όταν ανοίξετε το `CommandButton.docx` στο Microsoft Word, θα δείτε ένα κλικ-μεγαλό κουμπί με την ετικέτα **Click Me**. Πατώντας το στο Word ενεργοποιεί το προεπιλεγμένο διάλογο “Run Macro” επειδή το κουμπί είναι ένα OLE form control· μπορείτε αργότερα να προσθέσετε ένα μακροεντολή ή κώδικα VBA αν χρειαστεί.

## Βήμα 4: Επαλήθευση του αποτελέσματος (αναμενόμενη έξοδος)

Ανοίξτε το παραγόμενο αρχείο:

1. Το κουμπί εμφανίζεται στις συντεταγμένες που καθορίσατε (περίπου 1.4 ίντ από αριστερά και πάνω της σελίδας).  
2. Η λεζάντα είναι **Click Me**.  
3. Η ιδιότητα name (`cmdSubmit`) είναι ορατή στο παράθυρο **Developer → Properties** του Word, κάτι χρήσιμο όταν χρειάζεται να αναφερθείτε στο control από VBA.

![Insert OLE command button example in Word document](insert-ole-button.png)

*Κείμενο εναλλακτικής εικόνας*: **Παράδειγμα εισαγωγής κουμπιού εντολής OLE σε έγγραφο Word** (περιλαμβάνει την κύρια λέξη-κλειδί για προσβασιμότητα και SEO).

## Ακραίες περιπτώσεις & Συχνές ερωτήσεις

### 1. Τι γίνεται αν το κουμπί δεν εμφανίζεται εκεί που το περιμένω;

* Το Word χρησιμοποιεί μονάδες points, όχι pixels. Μετατρέψτε τα pixels της οθόνης σε points (`points = pixels * 72 / DPI`).  
* Βεβαιωθείτε ότι το rectangle δεν τέμνει τα περιθώρια της σελίδας· διαφορετικά το Word μπορεί να μετακινήσει το control.

### 2. Μπορώ να εισάγω το κουμπί σε υπάρχον έγγραφο;

Ναι. Φορτώστε το έγγραφο με `new Document("Existing.docx")` και χρησιμοποιήστε την ίδια ροή εργασίας `DocumentBuilder`. Απλώς θυμηθείτε να μετακινήσετε τον κέρσορα του builder (`builder.MoveToDocumentEnd()`, `builder.MoveToBookmark("myBookmark")`, κλπ.) πριν καλέσετε την `InsertForms2OleControl`.

### 3. Πώς συνδέω μια μακροεντολή στο κουμπί;

Το Aspose.Words δεν δημιουργεί κώδικα VBA, αλλά μπορείτε να ενσωματώσετε μια μακροεντολή μετά τη δημιουργία του εγγράφου:

```csharp
// Load the generated document
Document doc = new Document(outputPath);

// Add a VBA macro module (requires Aspose.Words licensing)
doc.VbaProject.Modules.Add("Module1", "Sub cmdSubmit_Click()\n MsgBox \"Button clicked!\"\nEnd Sub");

// Save again
doc.Save(outputPath);
```

### 4. Λειτουργεί αυτό με .NET Core σε Linux;

Ο έλεγχος OLE είναι χαρακτηριστικό ειδικό για Windows, επειδή βασίζεται σε COM. Σε Linux το κουμπί θα εισαχθεί, αλλά θα εμφανίζεται ως στατική εικόνα χωρίς διαδραστική συμπεριφορά. Για διαδραστικές φόρμες πολλαπλών πλατφορμών, εξετάστε τη χρήση content controls (`StructuredDocumentTag`) αντί αυτού.

### 5. Τι γίνεται αν χρειάζομαι διαφορετικό μέγεθος ή πολλαπλά κουμπιά;

Δημιουργήστε επιπλέον αντικείμενα `Rectangle` με μοναδικές συντεταγμένες και επαναλάβετε την κλήση `InsertForms2OleControl`. Κάθε κουμπί μπορεί να έχει το δικό του `Caption` και `Name`.

## Πλήρες λειτουργικό παράδειγμα

Παρακάτω είναι το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε‑επικολλήσετε σε μια εφαρμογή console. Περιλαμβάνει όλες τις απαραίτητες οδηγίες `using`, διαχείριση σφαλμάτων και σχόλια.

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

namespace OleCommandButtonDemo
{
    class Program
    {
        static void Main()
        {
            try
            {
                // 1️⃣ Create a new blank document
                Document document = new Document();
                DocumentBuilder builder = new DocumentBuilder(document);

                // 2️⃣ Define button rectangle (x, y, width, height) in points
                Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

                // 3️⃣ Insert the Forms2 OLE CommandButton control
                Forms2OleControl commandButton = builder.InsertForms2OleControl(
                    OleControlType.CommandButton,
                    buttonRect);

                // 4️⃣ Set visual properties
                commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
                commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";

                // 5️⃣ Save the document
                string outputPath = Path.Combine(
                    Environment.CurrentDirectory,
                    "CommandButton.docx");

                document.Save(outputPath);
                Console.WriteLine($"Document saved successfully: {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Error: {ex.Message}");
            }
        }
    }
}
```

Τρέξτε το πρόγραμμα, ανοίξτε το παραγόμενο `CommandButton.docx` και θα δείτε το κουμπί **Click Me** έτοιμο για περαιτέρω προσαρμογή.

## Συμπέρασμα

Τώρα ξέρετε πώς να **εισάγετε κουμπί εντολής OLE** σε έγγραφο Word χρησιμοποιώντας C# και Aspose.Words. Το tutorial κάλυψε:

* Εγκατάσταση του πακέτου Aspose.Words  
* Χρήση του `DocumentBuilder.InsertForms2OleControl` με `OleControlType.CommandButton`  
* Ορισμός ιδιοτήτων του κουμπιού (`Caption`, `Name`)  
* Αποθήκευση και επαλήθευση του αποτελέσματος  

Από εδώ μπορείτε να εξερευνήσετε συναφή θέματα όπως **Aspose.Words OLE control** για πλαίσια ελέγχου, combo boxes ή ενσωμάτωση ολόκληρων φύλλων Excel. Μπορείτε επίσης να πειραματιστείτε με την αυτοματοποίηση **Word OLE command button** σε μεγαλύτερα πρότυπα ή να αντικαταστήσετε τα OLE controls με σύγχρονα **content controls** για καλύτερη υποστήριξη πολλαπλών πλατφορμών.

Αισθανθείτε ελεύθεροι να προσαρμόσετε τις τιμές του rectangle, να προσθέσετε πολλαπλά κουμπιά ή να ενσωματώσετε μακροεντολές VBA ώστε να καλύψετε τις ανάγκες της εφαρμογής σας. Καλό κώδικα!

## Τι πρέπει να μάθετε στη συνέχεια;

Οι παρακάτω οδηγίες καλύπτουν στενά σχετικές θεματικές που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε επιπλέον δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Εισαγωγή αντικειμένου Ole σε έγγραφο Word](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object/)
- [Εισαγωγή αντικειμένου Ole σε έγγραφο Word ως εικονίδιο](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-as-icon/)
- [Εισαγωγή αντικειμένου Ole σε Word με Ole Package](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-with-ole-package/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}