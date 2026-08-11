---
category: general
date: 2026-08-10
description: Δημιουργήστε έγγραφο Word προγραμματιστικά με το Aspose.Words, στη συνέχεια
  προσθέστε ένα κουμπί ελέγχου ActiveX. Εισάγετε κουμπί εντολής ActiveX σε λίγα λεπτά.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add activex control word
- insert activex command button
language: el
lastmod: 2026-08-10
og_description: Δημιουργήστε έγγραφο Word προγραμματιστικά χρησιμοποιώντας το Aspose.Words,
  στη συνέχεια προσθέστε ένα κουμπί ελέγχου ActiveX. Μάθετε πώς να εισάγετε γρήγορα
  ένα κουμπί εντολής ActiveX.
og_image_alt: Screenshot of a Word document created programmatically with an ActiveX
  command button
og_title: Δημιουργία εγγράφου Word προγραμματιστικά – προσθήκη κουμπιού ActiveX σε
  C#
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  headline: Create word document programmatically and add ActiveX button
  type: TechArticle
- description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  name: Create word document programmatically and add ActiveX button
  steps:
  - name: Open `ActiveX_CommandButton.docx` in Microsoft Word.
    text: Open `ActiveX_CommandButton.docx` in Microsoft Word.
  - name: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
    text: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
  - name: Click **Design Mode**. The button should appear with the label “Submit”.
    text: Click **Design Mode**. The button should appear with the label “Submit”.
  - name: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
    text: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- C#
title: Δημιουργία εγγράφου Word προγραμματιστικά και προσθήκη κουμπιού ActiveX
url: /el/net/working-with-oleobjects-and-activex/create-word-document-programmatically-and-add-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία εγγράφου Word προγραμματιστικά και προσθήκη κουμπιού ActiveX

Αν χρειάζεστε **δημιουργία εγγράφου Word προγραμματιστικά**, αυτός ο οδηγός σας καθοδηγεί βήμα‑βήμα στη διαδικασία με το Aspose.Words for .NET. Θα μάθετε επίσης πώς να **προσθέσετε στοιχεία ελέγχου ActiveX** και **εισάγετε αντικείμενα κουμπιού εντολής ActiveX** σε ένα ενιαίο, αυτόνομο παράδειγμα.

Η δημιουργία αρχείων Word από κώδικα αφαιρεί το χειροκίνητο βήμα του ανοίγματος του Microsoft Word, επιτρέποντάς σας να δημιουργείτε αυτόματα αναφορές, τιμολόγια ή συμβόλαια βασισμένα σε δεδομένα. Στο τέλος αυτού του tutorial θα έχετε μια έτοιμη για εκτέλεση εφαρμογή κονσόλας C# που παράγει ένα αρχείο `.docx` που περιέχει ένα διαδραστικό κουμπί ActiveX CommandButton.

## Προαπαιτούμενα

* .NET 6.0 SDK ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.6+)
* Visual Studio 2022 ή οποιοδήποτε IDE που υποστηρίζει ανάπτυξη .NET
* Ένα έγκυρο άδεια χρήσης Aspose.Words for .NET (μπορείτε να χρησιμοποιήσετε το δωρεάν κλειδί αξιολόγησης για δοκιμές)
* Βασική εξοικείωση με τη σύνταξη C# και την έννοια των ελέγχων COM/ActiveX

> **Συμβουλή:** Εάν σκοπεύετε να διανείμετε το παραγόμενο έγγραφο σε χρήστες που δεν έχουν εγκατεστημένο το Word, ενσωματώστε τα αρχεία χρόνου εκτέλεσης του ελέγχου ActiveX μαζί με το `.docx` ή παρέχετε ένα πρότυπο με ενεργοποιημένα μακροεντολές.

## Δημιουργία εγγράφου Word προγραμματιστικά – αρχική ρύθμιση

Πρώτα, προσθέστε το πακέτο NuGet Aspose.Words στο έργο σας:

```bash
dotnet add package Aspose.Words
```

Στη συνέχεια, δημιουργήστε ένα νέο έργο κονσόλας (αν δεν έχετε ήδη ένα):

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
```

Ανοίξτε το παραγόμενο αρχείο `Program.cs` – θα αντικαταστήσουμε το περιεχόμενό του με τη πλήρη λύση παρακάτω.

## Βήμα 1: Εισαγωγή χώρων ονομάτων και διαμόρφωση της άδειας

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // OPTIONAL: Apply your Aspose.Words license to remove evaluation watermarks.
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");
```

*Γιατί είναι σημαντικό*: Η εισαγωγή του `Aspose.Words.Drawing` σας δίνει πρόσβαση στο `Forms2OleControl`, την κλάση που αντιπροσωπεύει έναν έλεγχο ActiveX μέσα σε ένα έγγραφο Word. Η προημεροληπτική ρύθμιση άδειας αποτρέπει προειδοποιήσεις χρόνου εκτέλεσης στην παραγωγή.

## Βήμα 2: Δημιουργία κενού εγγράφου και DocumentBuilder

```csharp
            // Create a new empty Word document.
            Document doc = new Document();

            // DocumentBuilder provides a convenient API for inserting text, tables, and controls.
            DocumentBuilder builder = new DocumentBuilder(doc);
```

Το αντικείμενο `Document` είναι η αναπαράσταση στη μνήμη ενός αρχείου `.docx`. Το `DocumentBuilder` λειτουργεί σαν δείκτης που μετακινείτε μέσα στο έγγραφο για να εισάγετε στοιχεία.

## Βήμα 3: Εισαγωγή ελέγχου ActiveX CommandButton

```csharp
            // Insert an ActiveX CommandButton.
            // Parameters: control type, width, height, left position, top position (all in points).
            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, // ActiveX type
                100,   // Width in points
                50,    // Height in points
                150,   // Left offset from the page margin
                200);  // Top offset from the page margin
```

Η μέθοδος `InsertForms2OleControl` δημιουργεί ένα αντικείμενο OLE που το Word αντιμετωπίζει ως έλεγχο ActiveX. Το σύστημα συντεταγμένων χρησιμοποιεί μονάδες point (1 point = 1/72 ίντσα), που ταιριάζει με τη μηχανή διάταξης του Word.

## Βήμα 4: Ορισμός λεζάντας κουμπιού και προαιρετικών ιδιοτήτων

```csharp
            // Set the text that appears on the button.
            commandBtn.Caption = "Submit";

            // Optional: assign a macro name that Word will call when the button is clicked.
            // commandBtn.OnAction = "MyMacroName";
```

Ο ορισμός της ιδιότητας `Caption` είναι ο πιο συνηθισμένος τρόπος για να ονομάσετε το κουμπί. Εάν χρειάζεστε το κουμπί να εκτελεί μια μακροεντολή VBA, αντιστοιχίστε το όνομα της μακροεντολής στην `OnAction`. Αυτός ο οδηγός εστιάζει στο οπτικό μέρος· η ενσωμάτωση μακροεντολών καλύπτεται στην ενότητα «Επόμενα βήματα».

## Βήμα 5: Αποθήκευση του εγγράφου

```csharp
            // Define the output path – change this to a folder that exists on your machine.
            string outputPath = @"ActiveX_CommandButton.docx";

            // Save the document with the embedded ActiveX control.
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Όταν εκτελέσετε το πρόγραμμα, θα δείτε ένα μήνυμα στην κονσόλα που επιβεβαιώνει ότι το `ActiveX_CommandButton.docx` έχει γραφτεί στο δίσκο.

### Πλήρης κώδικας πηγής (έτοιμος για αντιγραφή‑επικόλληση)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton,
                100, 50, 150, 200);

            commandBtn.Caption = "Submit";
            // commandBtn.OnAction = "MyMacroName";

            string outputPath = @"ActiveX_CommandButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Η εκτέλεση του αποσπάσματος δημιουργεί ένα αρχείο Word που περιέχει ένα κλικ-μενού **ActiveX command button**. Ανοίξτε το αρχείο στο Microsoft Word, μεταβείτε σε **Design Mode** (καρτέλα Developer → Design Mode) και θα δείτε το κουμπί να εμφανίζεται ακριβώς στη θέση που το τοποθετήσατε.

## Βήμα 6: Επαλήθευση του αποτελέσματος

1. Ανοίξτε το `ActiveX_CommandButton.docx` στο Microsoft Word.  
2. Ενεργοποιήστε την καρτέλα **Developer** εάν δεν είναι ορατή (`File → Options → Customize Ribbon → check Developer`).  
3. Κάντε κλικ στο **Design Mode**. Το κουμπί θα πρέπει να εμφανίζεται με τη λεζάντα “Submit”.  
4. Εάν προσθέσατε μια μακροεντολή `OnAction`, κάντε κλικ στο κουμπί ενώ το Design Mode είναι απενεργοποιημένο για να ενεργοποιήσετε τη μακροεντολή.

Εάν το κουμπί δεν εμφανίζεται, βεβαιωθείτε ότι οι ρυθμίσεις ασφαλείας του Word επιτρέπουν ελέγχους ActiveX (`File → Options → Trust Center → Trust Center Settings → ActiveX Settings`).

## Συχνές ερωτήσεις και ειδικές περιπτώσεις

| Ερώτηση | Απάντηση |
|----------|--------|
| **Μπορώ να εισάγω άλλους τύπους ActiveX;** | Ναι. Η απαρίθμηση `Forms2OleControlType` περιλαμβάνει `CheckBox`, `OptionButton`, `ComboBox`, κλπ. Αντικαταστήστε το `CommandButton` με την επιθυμητή τιμή της απαρίθμησης |

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε επιπλέον λειτουργίες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Δημιουργία ομαδικού σχήματος σε έγγραφο Word χρησιμοποιώντας Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Δημιουργία εγγράφου Word με κεφαλίδα και υποσέλιδο χρησιμοποιώντας Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Εισαγωγή ενσωματωμένης εικόνας σε έγγραφο Word χρησιμοποιώντας Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}