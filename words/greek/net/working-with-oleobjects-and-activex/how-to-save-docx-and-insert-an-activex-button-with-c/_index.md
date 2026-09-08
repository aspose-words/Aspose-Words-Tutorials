---
category: general
date: 2026-09-08
description: Πώς να αποθηκεύσετε ένα docx ενώ εισάγετε έναν έλεγχο ActiveX σε C#.
  Ακολουθήστε αυτόν τον βήμα‑βήμα οδηγό για να προσθέσετε ένα κουμπί εντολής προγραμματιστικά.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to save docx
- insert activex control
- add activex button
- create word document programmatically
- how to add command button
language: el
lastmod: 2026-09-08
og_description: Πώς να αποθηκεύσετε ένα docx ενώ εισάγετε έναν έλεγχο ActiveX σε C#.
  Αυτό το σεμινάριο σας καθοδηγεί στη δημιουργία ενός εγγράφου Word προγραμματιστικά,
  στην προσθήκη ενός κουμπιού εντολής και στην αποθήκευση του αρχείου.
og_image_alt: How to save docx with an ActiveX command button displayed in the document
og_title: Πώς να αποθηκεύσετε ένα αρχείο docx και να ενσωματώσετε ένα κουμπί ActiveX
  σε C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: How to save docx while inserting an ActiveX control in C#. Follow this
    step‑by‑step guide to add a command button programmatically.
  headline: How to save docx and insert an ActiveX button with C#
  type: TechArticle
tags:
- C#
- Word automation
- ActiveX
- Docx
title: Πώς να αποθηκεύσετε ένα αρχείο docx και να εισάγετε ένα κουμπί ActiveX με C#
url: /el/net/working-with-oleobjects-and-activex/how-to-save-docx-and-insert-an-activex-button-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να αποθηκεύσετε docx και να εισάγετε ένα κουμπί ActiveX με C#

Αν χρειάζεστε να δημιουργήσετε προγραμματιστικά ένα έγγραφο Word και στη συνέχεια να αποθηκεύσετε docx με ένα διαδραστικό κουμπί, αυτός ο οδηγός σας δείχνει πώς να το κάνετε. Θα μάθετε πώς να εισάγετε έναν έλεγχο ActiveX, να προσθέσετε ένα κουμπί ActiveX και να αποθηκεύσετε το παραγόμενο αρχείο .docx χρησιμοποιώντας C# και τη βιβλιοθήκη Aspose.Words.

Ο οδηγός καλύπτει κάθε βήμα που απαιτείται για **να δημιουργήσετε έγγραφο Word προγραμματιστικά**, να ενσωματώσετε ένα **κουμπί εντολής**, και να αποθηκεύσετε το αρχείο στο δίσκο. Δεν απαιτείται προηγούμενη εμπειρία με αντικείμενα COM, αλλά θα πρέπει να έχετε βασικές γνώσεις C# και εγκατεστημένο το Visual Studio.

## Προαπαιτούμενα

* .NET 6.0 SDK ή νεότερο  
* Visual Studio 2022 (ή οποιοδήποτε IDE C#)  
* Aspose.Words for .NET NuGet package (`Install-Package Aspose.Words`)  
* Κατανόηση της δομής έργου C#  

Αυτά τα στοιχεία εξασφαλίζουν ότι ο κώδικας θα μεταγλωττιστεί και θα εκτελεστεί χωρίς πρόσθετη διαμόρφωση.

## Βήμα 1: Ρύθμιση νέου έργου κονσόλας C#

Δημιουργήστε μια εφαρμογή κονσόλας που θα φιλοξενήσει τη λογική αυτοματισμού του Word.

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
dotnet add package Aspose.Words
```

Η παραπάνω εντολή δημιουργεί έναν φάκελο με όνομα **WordActiveXDemo**, προσθέτει την αναφορά Aspose.Words και προετοιμάζει το έργο για μεταγλώττιση.

## Βήμα 2: Δημιουργία εγγράφου Word προγραμματιστικά

Ανοίξτε το παραγόμενο αρχείο `Program.cs` και προσθέστε τις απαιτούμενες δηλώσεις `using`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;   // not used directly but required for some overloads
```

Τώρα δημιουργήστε ένα κενό αντικείμενο `Document`. Αυτό το αντικείμενο αντιπροσωπεύει ολόκληρο το αρχείο Word στη μνήμη.

```csharp
// Step 2: Create a new blank document
Document document = new Document();
```

Η κλάση `Document` είναι το σημείο εισόδου για όλες τις λειτουργίες επεξεργασίας Word. Σε αυτό το στάδιο το έγγραφο δεν περιέχει σελίδες, αλλά το Aspose.Words θα δημιουργήσει αυτόματα μια προεπιλεγμένη ενότητα όταν προσθέσετε περιεχόμενο.

## Βήμα 3: Εισαγωγή ελέγχου ActiveX – προσθήκη κουμπιού activex

Ένα αντικείμενο **Forms2OleControl** σας επιτρέπει να ενσωματώσετε έναν έλεγχο ActiveX μέσα σε μια παράγραφο Word. Ο παρακάτω κώδικας εισάγει ένα **CommandButton** με πλάτος 150 pt και ύψος 30 pt.

```csharp
// Step 3: Initialize a DocumentBuilder to edit the document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert an ActiveX CommandButton control with the desired size
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton, 150, 30);
```

`InsertForms2OleControl` δημιουργεί τον έλεγχο και επιστρέφει μια ισχυρά τυποποιημένη παρουσία `Forms2OleControl`, την οποία μπορείτε να διαμορφώσετε περαιτέρω. Η μέθοδος προσθέτει αυτόματα μια νέα παράγραφο για τη φιλοξενία του ελέγχου, οπότε δεν χρειάζεται να διαχειριστείτε χειροκίνητα αντικείμενα παραγράφου.

## Βήμα 4: Διαμόρφωση του κουμπιού εντολής – πώς να προσθέσετε ιδιότητες κουμπιού εντολής

Ορίστε τις ιδιότητες **Name** και **Caption** του κουμπιού ώστε να είναι αναγνωρίσιμο κατά την εκτέλεση και φιλικό προς τον χρήστη στη διεπαφή.

```csharp
// Step 4: Set the control's name and caption
commandButton.Name = "cmdSubmit";
commandButton.Caption = "Submit";
```

Το χαρακτηριστικό `Name` είναι χρήσιμο όταν αργότερα χειρίζεστε το γεγονός κλικ του κουμπιού μέσω VBA ή μακροεντολής Word. Το `Caption` είναι το κείμενο που βλέπει ο τελικός χρήστης στην επιφάνεια του κουμπιού.

### Συμβουλή επαγγελματία
Αν σκοπεύετε να αυτοματοποιήσετε τη διαχείριση του κλικ από C#, ενσωματώστε μια μακροεντολή VBA που αναφέρεται στο `cmdSubmit`. Το Word θα ζητήσει από τον χρήστη να ενεργοποιήσει τις μακροεντολές όταν ανοίξει το έγγραφο, κάτι που είναι τυπική συμπεριφορά ασφαλείας για ελέγχους ActiveX.

## Βήμα 5: Πώς να αποθηκεύσετε docx

Αφού τοποθετηθεί ο έλεγχος, αποθηκεύστε το έγγραφο σε αρχείο .docx. Η μέθοδος `Save` επιλέγει αυτόματα τη σωστή μορφή βάσει της επέκτασης του αρχείου.

```csharp
// Step 5: Save the document containing the CommandButton
string outputPath = @"C:\Temp\CommandButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Η αποθήκευση του αρχείου ολοκληρώνει τη ροή εργασίας **πώς να αποθηκεύσετε docx**. Το παραγόμενο αρχείο μπορεί να ανοιχθεί στο Microsoft Word, όπου το κουμπί ActiveX θα εμφανιστεί στην πρώτη σελίδα. Όταν κάνετε κλικ στο κουμπί, το Word θα εμφανίσει ένα μήνυμα placeholder εκτός εάν έχει προσαρτηθεί μια μακροεντολή.

## Βήμα 6: Εκτελέστε το πρόγραμμα και επαληθεύστε το αποτέλεσμα

Μεταγλωττίστε και εκτελέστε την εφαρμογή κονσόλας:

```bash
dotnet run
```

Αφού ολοκληρωθεί το πρόγραμμα, ανοίξτε το `C:\Temp\CommandButton.docx` στο Microsoft Word:

* Το έγγραφο περιέχει μία σελίδα με ένα κουμπί **Submit** κοντά στην κορυφή.  
* Με το ποντίκι πάνω από το κουμπί εμφανίζεται το tooltip με το όνομα `cmdSubmit`.  
* Δεν χάθηκε περιεχόμενο και το μέγεθος του αρχείου είναι συγκρίσιμο με ένα τυπικό κενό .docx.

Αν το κουμπί δεν εμφανίζεται, βεβαιωθείτε ότι:

1. Οι ρυθμίσεις του **Trust Center** του Word επιτρέπουν ελέγχους ActiveX.  
2. Το αρχείο αποθηκεύτηκε με την επέκταση `.docx` (όχι `.doc`).  

## Περιπτώσεις άκρων και κοινές παραλλαγές

| Κατάσταση | Συνιστώμενη προσαρμογή |
|-----------|------------------------|
| Χρειάζεστε διαφορετικό μέγεθος κουμπιού | Αλλάξτε τα επιχειρήματα πλάτους και ύψους στην `InsertForms2OleControl`. |
| Θέλετε το κουμπί σε συγκεκριμένη σελίδα | Χρησιμοποιήστε `builder.MoveToDocumentEnd();` μετά την προσθήκη σελίδων, ή εισάγετε αλλαγή σελίδας πριν από τον έλεγχο. |
| Πρέπει να υποστηρίξετε περιβάλλοντα χωρίς Aspose.Words | Χρησιμοποιήστε το Open XML SDK για να εισάγετε ένα στοιχείο `w:object`, αλλά ο κώδικας γίνεται σημαντικά πιο πολύπλοκος. |
| Απαιτείται έγγραφο με ενεργοποιημένες μακροεντολές | Αποθηκεύστε με την επέκταση `.docm` (`document.Save("MyDoc.docm");`) και ενσωματώστε ένα μοντέλο VBA που διαχειρίζεται το `cmdSubmit_Click`. |

## Πλήρης πηγαίος κώδικας

Παρακάτω βρίσκεται το πλήρες, αυτόνομο πρόγραμμα που μπορείτε να αντιγράψετε στο `Program.cs` και να εκτελέσετε χωρίς τροποποιήσεις (εκτός από τη διαδρομή εξόδου).

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document
            Document document = new Document();

            // Initialize a DocumentBuilder to edit the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert an ActiveX CommandButton control with the desired size
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, 150, 30);

            // Set the control's name and caption
            commandButton.Name = "cmdSubmit";
            commandButton.Caption = "Submit";

            // Save the document containing the CommandButton
            string outputPath = @"C:\Temp\CommandButton.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Αναμενόμενη έξοδος στην κονσόλα

```
Document saved to C:\Temp\CommandButton.docx
```

Το άνοιγμα του αρχείου στο Word εμφανίζει ένα κουμπί με την ετικέτα **Submit**. Κάνοντας κλικ στο κουμπί ενεργοποιείται η προεπιλεγμένη συμπεριφορά ActiveX (ένα παράθυρο μηνύματος που υποδεικνύει ότι δεν υπάρχει συνδεδεμένη μακροεντολή).

## Συμπέρασμα

Αυτός ο οδηγός επέδειξε **πώς να αποθηκεύσετε docx** ενώ ενσωματώνεται ένας **έλεγχος ActiveX**, συγκεκριμένα ένα **προσθήκη κουμπιού activex** που λειτουργεί ως κουμπί εντολής. Τώρα γνωρίζετε πώς να **δημιουργήσετε έγγραφο Word προγραμματιστικά**, να διαμορφώσετε τις ιδιότητες του κουμπιού και να αποθηκεύσετε το αρχείο για αλληλεπίδραση με τον τελικό χρήστη.

Από εδώ μπορείτε να εξερευνήσετε:

* Προσθήκη μακροεντολών VBA για τη διαχείριση του `cmdSubmit_Click`.  
* Εισαγωγή άλλων ελέγχων ActiveX όπως πλαίσια ελέγχου ή πτυσσόμενα κουτιά.  
* Δημιουργία εγγράφων πολλαπλών σελίδων με πολλαπλά διαδραστικά στοιχεία.  

Πειραματιστείτε με διαφορετικούς τύπους ελέγχων και επιλογές διάταξης για να δημιουργήσετε πλούσια, διαδραστικά πρότυπα Word που βελτιστοποιούν τις επιχειρηματικές σας διαδικασίες.

## Τι Θα Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά σχετικές θεματικές που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κατακτήσετε πρόσθετες δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Aspose.Words – Αποθήκευση docx ως txt και Εξαγωγή Εξισώσεων Word ως LaTeX – Πλήρης Οδηγός](/words/english/net/basic-conversions/save-docx-as-txt-complete-guide-to-export-word-equations-as/)
- [πώς να ανακτήσετε docx – οδηγός C# για κατεστραμμένα αρχεία Word](/words/english/net/programming-with-loadoptions/how-to-recover-docx-c-guide-for-corrupted-word-files/)
- [Πώς να Αποθηκεύσετε Word ως Markdown – Πλήρης Οδηγός C#](/words/english/net/programming-with-markdownsaveoptions/how-to-save-word-as-markdown-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}