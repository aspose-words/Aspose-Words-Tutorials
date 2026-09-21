---
category: general
date: 2026-09-21
description: Μάθετε πώς να δημιουργήσετε κουμπί εντολής ActiveX σε ένα έγγραφο Word
  με το Aspose.Words και C#. Ο οδηγός βήμα‑βήμα καλύπτει την εισαγωγή, την τοποθέτηση
  και την αποθήκευση.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- aspose.words activex
- c# documentbuilder
- insertforms2olecontrol
- activeX control in word
- programmatically add button
language: el
lastmod: 2026-09-21
og_description: Δημιουργήστε κουμπί εντολής ActiveX σε ένα έγγραφο Word χρησιμοποιώντας
  C# και Aspose.Words. Ακολουθήστε αυτό το πλήρες σεμινάριο για να εισάγετε, τοποθετήσετε
  και αποθηκεύσετε το κουμπί προγραμματιστικά.
og_image_alt: Screenshot showing an ActiveX command button inserted in a Word document
  using C#
og_title: Δημιουργήστε ένα κουμπί εντολών ActiveX στο Word με C# – πλήρης οδηγός
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create ActiveX command button in a Word document with
    Aspose.Words and C#. Step‑by‑step guide covers insertion, positioning, and saving.
  headline: How to create ActiveX command button in Word using C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
- DocumentBuilder
title: Πώς να δημιουργήσετε κουμπί εντολής ActiveX στο Word χρησιμοποιώντας C#
url: /el/net/working-with-oleobjects-and-activex/how-to-create-activex-command-button-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε κουμπί εντολής ActiveX στο Word χρησιμοποιώντας C#

Αν χρειάζεται να **δημιουργήσετε κουμπί εντολής ActiveX** μέσα σε ένα αρχείο Word, αυτός ο οδηγός σας δείχνει τα ακριβή βήματα. Χρησιμοποιώντας το Aspose.Words for .NET μπορείτε να προσθέσετε, τοποθετήσετε και να διαμορφώσετε το κουμπί εξ ολοκλήρου από κώδικα C#.

Η προγραμματιστική εισαγωγή ενός κουμπιού ActiveX εξαλείφει την χειροκίνητη εργασία UI και επιτρέπει την αυτοματοποιημένη δημιουργία εγγράφων για φόρμες, αναφορές ή διαδραστικά πρότυπα. Σε αυτό το tutorial θα μάθετε πώς να χρησιμοποιήσετε το **DocumentBuilder**, τη μέθοδο **InsertForms2OleControl** και σχετικές ιδιότητες για να πετύχετε ένα πλήρως λειτουργικό κουμπί.

## Τι θα χρειαστείτε

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* .NET 6.0 SDK ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.7+)
* Aspose.Words for .NET (πακέτο NuGet `Aspose.Words`)
* Ένα IDE όπως το Visual Studio 2022 ή το VS Code
* Βασικές γνώσεις C# και εννοιών εγγράφων Word

Δεν απαιτείται πρόσθετη εγκατάσταση του Office, επειδή το Aspose.Words λειτουργεί ανεξάρτητα από το Microsoft Word.

## Βήμα 1: Ρυθμίστε το έργο C#

Δημιουργήστε ένα νέο πρότζεκτ κονσόλας και προσθέστε το πακέτο Aspose.Words.

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
dotnet add package Aspose.Words
```

Η βιβλιοθήκη `Aspose.Words` παρέχει την κλάση **DocumentBuilder** που θα χρησιμοποιήσουμε για να χειριστούμε το έγγραφο.

## Βήμα 2: Αρχικοποιήστε το έγγραφο και τον builder

Το πρώτο μπλοκ κώδικα δημιουργεί ένα κενό έγγραφο και μια παρουσία `DocumentBuilder`. Αυτό το αντικείμενο είναι το σημείο εισόδου για όλες τις λειτουργίες επεξεργασίας Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// Create a new blank document.
Document doc = new Document();

// Create a builder to edit the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Γιατί είναι σημαντικό:** Το `DocumentBuilder` διατηρεί τη θέση του τρέχοντος κέρσορα, ώστε οποιαδήποτε εισαγωγή ακολουθεί να εμφανίζεται ακριβώς εκεί που τοποθετείτε τον κέρσορα.

## Βήμα 3: Εισάγετε το κουμπί εντολής ActiveX

Η μέθοδος **InsertForms2OleControl** δημιουργεί έναν έλεγχο ActiveX του ζητούμενου τύπου. Εδώ ζητάμε ένα `CommandButton` και καθορίζουμε το μέγεθός του σε μονάδες σημείου (200 × 30 pt).

```csharp
// Insert an ActiveX CommandButton control (200 × 30 pt).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    OleControlType.CommandButton, 200, 30);
```

**Επεξήγηση:**  
* `OleControlType.CommandButton` λέει στο Aspose.Words να δημιουργήσει ένα κουμπί αντί για άλλο τύπο ελέγχου.  
* Η μέθοδος επιστρέφει ένα αντικείμενο `Forms2OleControl`, το οποίο εκθέτει πεδία τοποθέτησης και ιδιοτήτων.

## Βήμα 4: Τοποθετήστε το κουμπί και ορίστε τις ιδιότητές του

Μετά την εισαγωγή μπορείτε να μετακινήσετε το κουμπί σε οποιαδήποτε θέση στη σελίδα και να του δώσετε ένα προγραμματιστικό όνομα και ορατή λεζάντα.

```csharp
// Position the button (coordinates are in points).
cmdBtn.Left = 100;          // X‑coordinate
cmdBtn.Top = 150;           // Y‑coordinate

// Set the button's programmatic name and displayed text.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

**Συμβουλή:** Το σύστημα συντεταγμένων ξεκινά από την πάνω‑αριστερή γωνία της σελίδας. Προσαρμόστε τα `Left` και `Top` για να ευθυγραμμίσετε το κουμπί με άλλα πεδία φόρμας.

## Βήμα 5: Αποθηκεύστε το έγγραφο

Τέλος, γράψτε το έγγραφο στο δίσκο. Το αρχείο θα περιέχει το κουμπί ActiveX, έτοιμο να ανοιχτεί στο Microsoft Word όπου το κουμπί γίνεται διαδραστικό.

```csharp
// Save the document that now contains the ActiveX button.
doc.Save("ActiveXCommandButton.docx");
```

Όταν ανοίξετε το `ActiveXCommandButton.docx` στο Word, θα δείτε ένα κουμπί με την ετικέτα **Submit** στην καθορισμένη θέση. Κάνοντας κλικ σε αυτό στο Word θα ενεργοποιηθεί η προεπιλεγμένη συμπεριφορά του κουμπιού εντολής (που μπορείτε αργότερα να προσαρμόσετε με VBA ή πρόσθετα Word).

## Πλήρες, εκτελέσιμο παράδειγμα

Συνδυάζοντας όλα τα κομμάτια προκύπτει ένα αυτόνομο πρόγραμμα που μπορείτε να αντιγράψετε, επικολλήσετε και να εκτελέσετε.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // 1. Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX CommandButton (200 × 30 pt).
        Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
            OleControlType.CommandButton, 200, 30);

        // 3. Position and configure the button.
        cmdBtn.Left = 100;          // X‑coordinate (points)
        cmdBtn.Top = 150;           // Y‑coordinate (points)
        cmdBtn.Name = "btnSubmit";
        cmdBtn.Caption = "Submit";

        // 4. Save the document.
        doc.Save("ActiveXCommandButton.docx");

        Console.WriteLine("Document created successfully.");
    }
}
```

**Αναμενόμενο αποτέλεσμα:** Η κονσόλα εκτυπώνει *«Document created successfully.»* και ο φάκελος περιέχει τώρα το `ActiveXCommandButton.docx`. Ανοίγοντας το αρχείο στο Microsoft Word εμφανίζεται ένα κλικable κουμπί **Submit** τοποθετημένο 100 pt από το αριστερό περιθώριο και 150 pt από την κορυφή της σελίδας.

## Συνηθισμένα προβλήματα και πώς να τα αποφύγετε

| Πρόβλημα | Γιατί συμβαίνει | Διόρθωση |
|----------|----------------|----------|
| Το κουμπί εμφανίζεται εκτός σελίδας | Οι τιμές `Left`/`Top` υπερβαίνουν τις διαστάσεις της σελίδας | Χρησιμοποιήστε `doc.FirstSection.PageSetup.PageWidth` και `PageHeight` για να υπολογίσετε ασφαλείς συντεταγμένες |
| Το κουμπί δεν είναι ορατό στο Word | Το έγγραφο αποθηκεύτηκε σε μορφή που αφαιρεί ελέγχους ActiveX (π.χ., `.txt`) | Πάντα αποθηκεύετε ως `.docx` ή `.doc` |
| Σφάλμα χρόνου εκτέλεσης `ArgumentOutOfRangeException` | Το πλάτος ή το ύψος ορίστηκε σε μηδέν ή σε αρνητικό αριθμό | Βεβαιωθείτε ότι τα ορίσματα μεγέθους που περνιούνται στη `InsertForms2OleControl` είναι θετικοί αριθμοί |

## Επέκταση της λύσης

Μπορείτε να προσαρμόσετε περαιτέρω το κουμπί ορίζοντας πρόσθετες ιδιότητες όπως `Enabled`, `Visible`, ή συνδέοντας μια μακροεντολή μέσω VBA. Η κλάση **Forms2OleControl** σας επιτρέπει επίσης να εισάγετε άλλους ελέγχους ActiveX όπως πλαίσια ελέγχου (`OleControlType.CheckBox`) ή λίστες επιλογής (`OleControlType.ComboBox`).

Αν χρειάζεται να δημιουργήσετε πολλαπλά κουμπιά σε βρόχο, ενσωματώστε τη λογική εισαγωγής σε μια βοηθητική μέθοδο:

```csharp
static Forms2OleControl AddCommandButton(DocumentBuilder builder,
    string name, string caption, double left, double top)
{
    var btn = builder.InsertForms2OleControl(OleControlType.CommandButton, 200, 30);
    btn.Name = name;
    btn.Caption = caption;
    btn.Left = left;
    btn.Top = top;
    return btn;
}
```

## Συμπέρασμα

Τώρα ξέρετε πώς να **δημιουργήσετε κουμπί εντολής ActiveX** σε ένα έγγραφο Word χρησιμοποιώντας C# και Aspose.Words. Το tutorial κάλυψε τη ρύθμιση του πρότζεκτ, την εισαγωγή του κουμπιού με `InsertForms2OleControl`, την τοποθέτησή του και την αποθήκευση του τελικού αρχείου. Με αυτή τη βάση μπορείτε να αυτοματοποιήσετε σύνθετες φόρμες, να ενσωματώσετε διαδραστικούς ελέγχους και να ενσωματώσετε έγγραφα Word σε μεγαλύτερες λύσεις .NET.

Στη συνέχεια, εξερευνήστε σχετικά θέματα όπως **Aspose.Words ActiveX** πεδία φόρμας, **C# DocumentBuilder** προχωρημένη μορφοποίηση, ή προγραμματική προσθήκη **ActiveX control in Word** για πλαίσια ελέγχου και λίστες πτυσσόμενων επιλογών. Πειραματιστείτε με διαφορετικές συντεταγμένες και μεγέθη για να ταιριάξουν στις συγκεκριμένες απαιτήσεις διάταξης σας. Καλή προγραμματιστική δουλειά!

## What Should You Learn Next?

Οι παρακάτω οδηγίες καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Δημιουργία εγγράφου Word με Aspose.Words για .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Δημιουργία σχήματος ορθογωνίου στο Word με Aspose.Words – Οδηγός βήμα‑βήμα](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Δημιουργία εγγράφου Word με πίνακα χρησιμοποιώντας Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}