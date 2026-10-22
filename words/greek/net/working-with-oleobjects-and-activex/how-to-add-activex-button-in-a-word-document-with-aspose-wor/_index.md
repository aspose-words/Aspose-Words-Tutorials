---
category: general
date: 2026-08-14
description: Πώς να προσθέσετε ένα κουμπί ActiveX σε ένα έγγραφο Word χρησιμοποιώντας
  το Aspose.Words – μάθετε πώς να δημιουργήσετε ένα κενό έγγραφο Word και να εισάγετε
  ένα κουμπί ActiveX προγραμματιστικά.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert activex button
- create empty word document
- create word document aspose
language: el
lastmod: 2026-08-14
og_description: Πώς να προσθέσετε κουμπί ActiveX σε ένα έγγραφο Word με το Aspose.Words.
  Αυτό το σεμινάριο σας δείχνει πώς να δημιουργήσετε ένα κενό έγγραφο Word, να εισάγετε
  ένα κουμπί ActiveX και να αποθηκεύσετε το αποτέλεσμα.
og_image_alt: Screenshot of an ActiveX button inserted into a Word document using
  Aspose.Words
og_title: Πώς να προσθέσετε κουμπί ActiveX στο Word – Οδηγός Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  headline: How to add ActiveX button in a Word document with Aspose.Words
  type: TechArticle
- description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  name: How to add ActiveX button in a Word document with Aspose.Words
  steps:
  - name: Does the button work in all Word versions?
    text: ActiveX controls are supported in the desktop version of Word on Windows.
      They are not rendered in Word Online, Word for macOS, or mobile clients. If
      you need cross‑platform interactivity, consider using content controls or HTML‑based
      solutions instead.
  - name: What if I need a different size or position?
    text: '`InsertForms2OleControl` places the control at the current builder cursor.
      To move it, adjust the cursor with `builder.MoveTo` before insertion, or modify
      the control’s `Left` and `Top` properties after creation:'
  - name: Can I add other ActiveX types?
    text: Yes. The `Forms2OleControlType` enumeration includes `CheckBox`, `OptionButton`,
      `ListBox`, and more. Replace `CommandButton` with the desired enum value and
      adjust properties accordingly.
  - name: Is a macro required for the button to do something?
    text: The button itself does nothing until you attach VBA code. In Word, press
      **Alt+F11** to open the VBA editor, locate `btnSubmit_Click`, and write the
      desired logic. The generated document will retain the VBA project if you enable
      the **SaveFormat.Doc** (legacy `.doc`) format, but `.docx` files cannot
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- Word automation
- C#
title: Πώς να προσθέσετε κουμπί ActiveX σε ένα έγγραφο Word με το Aspose.Words
url: /el/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να προσθέσετε κουμπί ActiveX σε ένα έγγραφο Word με Aspose.Words

Αν χρειάζεστε **πώς να προσθέσετε ActiveX** ελέγχους σε ένα παραγόμενο αρχείο Word, αυτός ο οδηγός σας δείχνει τα ακριβή βήματα. Θα μάθετε πώς να **εισάγετε κουμπί ActiveX** προγραμματιστικά, ξεκινώντας από ένα **δημιουργία κενού εγγράφου Word** και τελειώνοντας με ένα αποθηκευμένο αρχείο που μπορεί να ανοιχθεί στο Microsoft Word.

Η προσθήκη ενός κουμπιού που εκτελεί κώδικα VBA ή ενεργοποιεί μια μακροεντολή είναι μια κοινή απαίτηση για αυτόματους δημιουργούς αναφορών, πρότυπα φορμών ή διαδραστικές συμβάσεις. Η χρήση του Aspose.Words for .NET σας επιτρέπει να δημιουργήσετε το έγγραφο χωρίς να εκκινήσετε το Office, διατηρώντας τη διαδικασία γρήγορη και φιλική προς τον διακομιστή.

## Προαπαιτούμενα

* .NET 6.0 (ή νεότερο) SDK εγκατεστημένο.
* Visual Studio 2022 ή οποιοδήποτε IDE συμβατό με C#.
* Πακέτο NuGet Aspose.Words for .NET (`Aspose.Words` έκδοση 24.9 ή νεότερη).  
  Εγκαταστήστε το με:
  ```bash
  dotnet add package Aspose.Words
  ```
* Περιβάλλον Windows εάν σκοπεύετε να δοκιμάσετε το κουμπί ActiveX, επειδή οι έλεγχοι ActiveX απαιτούν την έκδοση Windows του Microsoft Word.

## Βήμα 1: Δημιουργία κενού εγγράφου Word

Η πρώτη εργασία είναι να **δημιουργήσετε κενό έγγραφο Word** στη μνήμη. Το Aspose.Words παρέχει την κλάση `Document` για αυτό το σκοπό.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, blank Word document.
Document doc = new Document();
```

`Document` αντιπροσωπεύει ολόκληρο το αρχείο .docx. Σε αυτό το σημείο το έγγραφο δεν περιέχει σελίδες, αλλά μπορείτε να αρχίσετε να προσθέτετε περιεχόμενο αμέσως.

## Βήμα 2: Αρχικοποίηση του DocumentBuilder

`DocumentBuilder` είναι ένας βοηθός που σας επιτρέπει να εισάγετε κείμενο, εικόνες και άλλα αντικείμενα στο έγγραφο. Λειτουργεί πάνω στην παρουσία `Document` που μόλις δημιουργήσατε.

```csharp
// Initialise the builder with the blank document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Ο builder διατηρεί τη θέση του κέρσορα· οτιδήποτε εισάγετε μετά από αυτή τη γραμμή εμφανίζεται στην αρχή της πρώτης σελίδας.

## Βήμα 3: Εισαγωγή ελέγχου ActiveX CommandButton

Το Aspose.Words εκθέτει τη μέθοδο `InsertForms2OleControl` για την προσθήκη παλαιών ελέγχων φόρμας, συμπεριλαμβανομένου του ActiveX. Η μέθοδος απαιτεί τον τύπο του ελέγχου και το μέγεθός του σε points.

```csharp
// Insert an ActiveX CommandButton (150x30 points).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton, 150, 30);
```

Το επιστρεφόμενο αντικείμενο `Forms2OleControl` σας επιτρέπει να ρυθμίσετε ιδιότητες όπως το όνομα και η λεζάντα του ελέγχου.

## Βήμα 4: Διαμόρφωση των ιδιοτήτων του κουμπιού

Ο ορισμός ενός περιγραφικού `Name` σας επιτρέπει να αναφέρετε τον έλεγχο από κώδικα VBA αργότερα. Η `Caption` είναι το κείμενο που βλέπει ο χρήστης στο κουμπί.

```csharp
// Set the button’s programmatic name (used in VBA) and displayed caption.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

> **Συμβουλή:** Κρατήστε το όνομα σύντομο και αλφαριθμητικό· το Word θα απορρίψει ονόματα που περιέχουν κενά ή ειδικούς χαρακτήρες.

## Βήμα 5: Αποθήκευση του εγγράφου

Τέλος, γράψτε το έγγραφο στο δίσκο. Χρησιμοποιήστε την επέκταση `.docx` για σύγχρονα αρχεία Word· το κουμπί ActiveX λειτουργεί με τον ίδιο τρόπο σε αρχεία `.doc`, αλλά το `.docx` είναι η προτιμώμενη μορφή για νέα έργα.

```csharp
// Save the document containing the ActiveX button.
doc.Save(@"C:\Temp\ActiveXButton.docx");
```

Όταν ανοίξετε το `ActiveXButton.docx` στο Microsoft Word, θα δείτε ένα κλικ‑δυνατό κουμπί **Submit**. Εάν ενεργοποιήσετε τις μακροεντολές, μπορείτε να συνδέσετε κώδικα VBA στο `btnSubmit_Click` και να τον εκτελέσετε όταν ο χρήστης κάνει κλικ στο κουμπί.

## Πλήρες, εκτελέσιμο παράδειγμα

Συνδυάζοντας όλα τα κομμάτια λαμβάνετε ένα αυτόνομο πρόγραμμα που μπορείτε να αντιγράψετε, επικολλήσετε και εκτελέσετε.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create an empty Word document.
            Document doc = new Document();

            // Step 2: Initialise DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Insert an ActiveX CommandButton control.
            Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, 150, 30);

            // Step 4: Set button properties.
            cmdBtn.Name = "btnSubmit";
            cmdBtn.Caption = "Submit";

            // Step 5: Save the document.
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Αναμενόμενη έξοδος** – Μετά την εκτέλεση του προγράμματος, η κονσόλα εκτυπώνει τη θέση αποθήκευσης, και το άνοιγμα του παραγόμενου αρχείου στο Word εμφανίζει ένα κουμπί με την ετικέτα **Submit** τοποθετημένο στην κορυφή της πρώτης σελίδας.

## Διαχείριση κοινών ερωτήσεων και ειδικών περιπτώσεων

### Λειτουργεί το κουμπί σε όλες τις εκδόσεις του Word;

Οι έλεγχοι ActiveX υποστηρίζονται στην επιτραπέζια έκδοση του Word στα Windows. Δεν εμφανίζονται στο Word Online, Word για macOS ή σε κινητές εφαρμογές. Εάν χρειάζεστε διαπλατφορμική αλληλεπίδραση, εξετάστε τη χρήση ελέγχων περιεχομένου ή λύσεων βασισμένων σε HTML.

### Τι γίνεται αν χρειάζομαι διαφορετικό μέγεθος ή θέση;

`InsertForms2OleControl` τοποθετεί τον έλεγχο στην τρέχουσα θέση του κέρσορα του builder. Για να τον μετακινήσετε, προσαρμόστε τον κέρσορα με `builder.MoveTo` πριν από την εισαγωγή, ή τροποποιήστε τις ιδιότητες `Left` και `Top` του ελέγχου μετά τη δημιουργία:

```csharp
cmdBtn.Left = 100;   // points from the left margin
cmdBtn.Top = 200;    // points from the top margin
```

### Μπορώ να προσθέσω άλλους τύπους ActiveX;

Ναι. Η απαρίθμηση `Forms2OleControlType` περιλαμβάνει `CheckBox`, `OptionButton`, `ListBox` και άλλα. Αντικαταστήστε το `CommandButton` με την επιθυμητή τιμή enum και προσαρμόστε τις ιδιότητες αναλόγως.

### Απαιτείται μακροεντολή για το κουμπί ώστε να κάνει κάτι;

Το ίδιο το κουμπί δεν κάνει τίποτα μέχρι να συνδέσετε κώδικα VBA. Στο Word, πατήστε **Alt+F11** για να ανοίξετε τον επεξεργαστή VBA, βρείτε το `btnSubmit_Click` και γράψτε τη λογική που θέλετε. Το παραγόμενο έγγραφο θα διατηρήσει το έργο VBA εάν ενεργοποιήσετε τη μορφή **SaveFormat.Doc** (παραδοσιακό `.doc`), αλλά τα αρχεία `.docx` δεν μπορούν να αποθηκεύσουν μακροεντολές VBA. Χρησιμοποιήστε τη μορφή `.doc` εάν χρειάζεστε ενσωματωμένο VBA.

## Συμπέρασμα

Τώρα ξέρετε **πώς να προσθέσετε ActiveX** ελέγχους σε ένα αρχείο Word χρησιμοποιώντας το Aspose.Words. Ακολουθώντας τα βήματα για **δημιουργία κενού εγγράφου Word**, αρχικοποίηση ενός `DocumentBuilder`, **εισαγωγή κουμπιού ActiveX**, διαμόρφωση των ιδιοτήτων του και αποθήκευση του αρχείου, μπορείτε να δημιουργήσετε διαδραστικά πρότυπα Word απευθείας από τον κώδικα .NET.

Στη συνέχεια, εξερευνήστε συναφή θέματα όπως η διαχείριση συμβάντων **insert ActiveX button**, η προσθήκη **create word document aspose** για πίνακες ή εικόνες, και η ασφάλιση εγγράφων με ενεργοποιημένες μακροεντολές για επιχειρησιακή ανάπτυξη. Πειραματιστείτε με διαφορετικούς τύπους ελέγχων και επιλογές διάταξης για να προσαρμόσετε την εμπειρία χρήστη στις ανάγκες της εφαρμογής σας.

Καλή προγραμματιστική!

## Τι Θα Πρέπει να Μάθετε Στη Σύντομη Μελλοντική

Τα παρακάτω tutorials καλύπτουν στενά σχετικές θεματικές που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Δημιουργία εγγράφου Word με κεφαλίδα και υποσέλιδο χρησιμοποιώντας Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Δημιουργία Group Shape σε έγγραφο Word χρησιμοποιώντας Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Δημιουργία εγγράφου Word με πίνακα χρησιμοποιώντας Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}