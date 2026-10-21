---
category: general
date: 2026-09-30
description: Προσθέστε έναν έλεγχο ActiveX σε ένα έγγραφο Word χρησιμοποιώντας C#.
  Μάθετε πώς να εισάγετε ένα κουμπί ActiveX, να προσθέσετε ένα κουμπί εντολής και
  να το κάνετε κλικ.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- activex control word
- how to insert activex
- how to add command button
- insert activex button
- add clickable button word
language: el
lastmod: 2026-09-30
og_description: Προσθέστε έναν έλεγχο ActiveX σε ένα έγγραφο Word με C#. Ακολουθήστε
  αυτόν τον πλήρη οδηγό για να εισάγετε ένα κουμπί ActiveX, να προσθέσετε ένα κουμπί
  εντολής και να το κάνετε κλικ.
og_image_alt: Word document displaying an inserted ActiveX command button
og_title: Προσθήκη ενός ελέγχου ActiveX σε έγγραφα Word – βήμα‑βήμα οδηγός C#
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Add an ActiveX control word to a Word document using C#. Learn how
    to insert an ActiveX button, add a command button, and make it clickable.
  headline: How to add an ActiveX control word in Word with C#
  type: TechArticle
tags:
- ActiveX
- Aspose.Words
- C#
- Word automation
title: Πώς να προσθέσετε έναν έλεγχο ActiveX στο Word με C#
url: /el/net/working-with-oleobjects-and-activex/how-to-add-an-activex-control-word-in-word-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να προσθέσετε μια λέξη ελέγχου ActiveX στο Word με C#

Αν χρειάζεστε να ενσωματώσετε μια **ActiveX control word** μέσα σε ένα αρχείο Microsoft Word, αυτός ο οδηγός σας δείχνει ακριβώς πώς να το κάνετε. Θα δείτε ένα πλήρες, εκτελέσιμο παράδειγμα που εισάγει ένα κουμπί με δυνατότητα κλικ, αποθηκεύει το έγγραφο και λειτουργεί με την τελευταία έκδοση του Aspose.Words for .NET.

Η προσθήκη μιας λέξης ελέγχου ActiveX σας επιτρέπει να δημιουργήσετε διαδραστικές φόρμες, προσαρμοσμένα διαλόγους ή απλά στοιχεία UI που συμπεριφέρονται όπως τα ενσωματωμένα στοιχεία του Word. Είτε δημιουργείτε ένα πρότυπο σύμβασης που απαιτεί αλληλεπίδραση χρήστη είτε μια αναφορά που χρειάζεται ένα κουμπί «Run», τα παρακάτω βήματα καλύπτουν όλα όσα χρειάζεστε.

## Προαπαιτούμενα

* .NET 6.0 SDK ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.8)
* Visual Studio 2022 (ή οποιοδήποτε IDE που υποστηρίζει C#)
* Aspose.Words for .NET εγκατεστημένο (`dotnet add package Aspose.Words`)
* Βασική κατανόηση της C# και της δομής εγγράφων Word

> **Συμβουλή επαγγελματία:** Η μέθοδος `InsertForms2OleControl` λειτουργεί μόνο με τα παλαιά στοιχεία “Forms 2.0”, τα οποία είναι τα ActiveX controls που χρησιμοποιεί το Word για πεδία φόρμας. Εάν στοχεύετε σε νεότερες εκδόσεις του Office, το στοιχείο εξακολουθεί να αποδίδεται σωστά στον πελάτη επιφάνειας εργασίας.

## Βήμα 1: Ρύθμιση του έργου και εισαγωγή namespaces

Δημιουργήστε ένα νέο έργο console και προσθέστε τις απαιτούμενες δηλώσεις `using`. Αυτό διασφαλίζει ότι ο μεταγλωττιστής μπορεί να βρει τις κλάσεις `Document`, `DocumentBuilder` και `OleControlType`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

Το namespace `Aspose.Words` παρέχει APIs υψηλού επιπέδου για επεξεργασία Word, ενώ το `Aspose.Words.Drawing` περιέχει την απαραίτητη απαρίθμηση `OleControlType` για τον καθορισμό του τύπου του ActiveX control.

## Βήμα 2: Φόρτωση του πηγαίου εγγράφου Word

Πρέπει να ξεκινήσετε με ένα αρχείο Word που θέλετε να τροποποιήσετε. Ο παρακάτω κώδικας φορτώνει το `input.docx` από έναν φάκελο που καθορίζετε.

```csharp
// Step 2: Load the Word document you want to modify
string inputPath = @"C:\Docs\input.docx";
Document doc = new Document(inputPath);
```

Εάν το αρχείο δεν υπάρχει, το Aspose.Words ρίχνει μια `FileNotFoundException`. Τυλίξτε την κλήση σε ένα μπλοκ `try/catch` εάν χρειάζεστε ευγενική διαχείριση σφαλμάτων.

## Βήμα 3: Δημιουργία DocumentBuilder για επεξεργασία του εγγράφου

`DocumentBuilder` είναι το βασικό εργαλείο για την εισαγωγή κειμένου, εικόνων και ελέγχων. Διατηρεί έναν κέρσορα που δείχνει στη θέση όπου θα τοποθετηθεί το επόμενο στοιχείο.

```csharp
// Step 3: Create a DocumentBuilder to work with the document's content
DocumentBuilder builder = new DocumentBuilder(doc);
```

Από προεπιλογή, ο κέρσορας του builder βρίσκεται στην αρχή της πρώτης ενότητας. Μπορείτε να τον μετακινήσετε με μεθόδους όπως `MoveToDocumentEnd()` ή `MoveToParagraph(index)` εάν θέλετε το κουμπί κάπου αλλού.

## Βήμα 4: Εισαγωγή ελέγχου ActiveX CommandButton

Τώρα έρχεται η ουσία του οδηγού: η εισαγωγή μιας **ActiveX control word** που εμφανίζεται ως κουμπί με δυνατότητα κλικ. Η μέθοδος `InsertForms2OleControl` δέχεται δύο ορίσματα — τον τύπο του ελέγχου και μια λεζάντα (ή όνομα) για το στοιχείο.

```csharp
// Step 4: Insert an ActiveX CommandButton control with the caption "ClickMe"
builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");
```

* **Γιατί να χρησιμοποιήσετε `OleControlType.CommandButton`;**  
  Δηλώνει στο Word να δημιουργήσει ένα κλασικό κουμπί Forms 2.0, το οποίο εμφανίζει λεζάντα και μπορεί αργότερα να συνδεθεί με μακροεντολή ή script VBA.

* **Τι κάνει η λεζάντα;**  
  Η συμβολοσειρά `"ClickMe"` γίνεται το ορατό κείμενο του κουμπιού. Μπορείτε να την αλλάξετε σε ό,τι ταιριάζει στο UI σας.

### Εισαγωγή του κουμπιού σε συγκεκριμένη θέση

Εάν χρειάζεστε το κουμπί μετά από μια συγκεκριμένη παράγραφο, μετακινήστε πρώτα το builder:

```csharp
builder.MoveToParagraph(2); // moves to the third paragraph (zero‑based index)
builder.InsertParagraph(); // optional: add a blank line before the button
builder.InsertForms2OleControl(OleControlType.CommandButton, "Submit");
```

## Βήμα 5: Αποθήκευση του τροποποιημένου εγγράφου

Μετά την εισαγωγή του ελέγχου, αποθηκεύστε τις αλλαγές σε νέο αρχείο (ή αντικαταστήστε το αρχικό).

```csharp
// Step 5: Save the modified document
string outputPath = @"C:\Docs\output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Όταν ανοίξετε το `output.docx` στην έκδοση desktop του Word, θα δείτε το κουμπί με την ετικέτα **ClickMe** (ή **Submit**, ανάλογα με τη λεζάντα που χρησιμοποιήσατε). Το κλικ στο κουμπί σε λειτουργία σχεδίασης δεν κάνει τίποτα από προεπιλογή· μπορείτε να αναθέσετε μια μακροεντολή αργότερα μέσω της καρτέλας “Developer” του Word.

## Πλήρες, εκτελέσιμο παράδειγμα

Παρακάτω υπάρχει ένα αυτόνομο πρόγραμμα που δείχνει ολόκληρη τη ροή εργασίας. Αντιγράψτε το στο `Program.cs` ενός νέου console app και εκτελέστε το.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXControlWordDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Paths – adjust to your environment
            string inputPath = @"C:\Docs\input.docx";
            string outputPath = @"C:\Docs\output.docx";

            // 1️⃣ Load the source document
            Document doc = new Document(inputPath);

            // 2️⃣ Create a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Optional: move to the end of the document
            builder.MoveToDocumentEnd();
            builder.Writeln(); // add a blank line before the button

            // 3️⃣ Insert the ActiveX CommandButton (the core of the activex control word)
            builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");

            // 4️⃣ Save the result
            doc.Save(outputPath);
            Console.WriteLine($"Successfully saved the document with an ActiveX button to: {outputPath}");
        }
    }
}
```

### Αναμενόμενο αποτέλεσμα

* Η κονσόλα εκτυπώνει το μήνυμα επιτυχίας με τη διαδρομή εξόδου.
* Ανοίγοντας το `output.docx` εμφανίζεται ένα κουμπί **ClickMe** στη θέση όπου το builder το εισήγαγε.
* Το κουμπί μπορεί να επιλεγεί, να αλλάξει μέγεθος ή να του ανατεθεί μακροεντολή μέσω του **Developer → Design Mode** του Word.

## Συχνές ερωτήσεις και αντιμετώπιση ειδικών περιπτώσεων

| Ερώτηση | Απάντηση |
|----------|--------|
| **Πώς να εισαγάγετε ένα κουμπί ActiveX στην κεφαλίδα/υποσέλιδο;** | Μετακινήστε το builder στην κεφαλίδα/υποσέλιδο με `builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` πριν καλέσετε το `InsertForms2OleControl`. |
| **Τι κάνω αν χρειάζομαι ένα checkbox αντί για κουμπί;** | Χρησιμοποιήστε `OleControlType.CheckBox` και δώστε μια λεζάντα όπως `"Agree"`. |
| **Θα λειτουργεί το κουμπί στο Word Online;** | Όχι. Το Word Online δεν υποστηρίζει τα παλαιά στοιχεία Forms 2.0 ActiveX. Το κουμπί αποδίδεται μόνο στην έκδοση desktop. |
| **Μπορώ να ορίσω το μέγεθος του κουμπιού προγραμματιστικά;** | Μετά την εισαγωγή, ανακτήστε το αντικείμενο `Shape` μέσω `builder.CurrentParagraph.Runs[0].GetShape()` και προσαρμόστε το `Width`/`Height`. |
| **Υπάρχει τρόπος να αναθέσετε μια μακροεντολή από κώδικα;** | Το Aspose.Words δεν παρέχει δυνατότητα επεξεργασίας μακροεντολών. Πρέπει να ανοίξετε το έγγραφο στο Word και να συνδέσετε μια μακροεντολή χειροκίνητα ή να χρησιμοποιήσετε το Office Interop API. |

## Συμβουλές για χρήση σε παραγωγή

* **Αποφύγετε τις σκληρά κωδικοποιημένες διαδρομές** – χρησιμοποιήστε `Path.Combine` και αρχεία ρυθμίσεων.
* **Αποδεσμεύστε το `Document`** – τυλίξτε το σε δήλωση `using` εάν εργάζεστε με μεγάλα αρχεία για άμεση απελευθέρωση μνήμης.
* **Επικυρώστε την έξοδο** – ελέγξτε προγραμματιστικά ότι το έγγραφο περιέχει ένα σχήμα τύπου `OleControl` διατρέχοντας `doc.GetChildNodes(NodeType.Shape, true)`.
* **Σημείωση ασφαλείας** – Τα ActiveX controls μπορούν να εκτελέσουν κώδικα στον υπολογιστή του πελάτη. Διανείμετε τα έγγραφα μόνο σε αξιόπιστους χρήστες και εξετάστε τη χρήση ψηφιακών υπογραφών.

## Συμπέρασμα

Τώρα γνωρίζετε πώς να προσθέσετε μια **ActiveX control word** σε έγγραφο Word χρησιμοποιώντας C#. Φορτώνοντας ένα έγγραφο, δημιουργώντας ένα `DocumentBuilder`, εισάγοντας ένα κουμπί εντολής με `InsertForms2OleControl` και αποθηκεύοντας το αρχείο, μπορείτε να αυτοματοποιήσετε τη δημιουργία διαδραστικών φορμών Word. Πειραματιστείτε με άλλες τιμές του `OleControlType`, τοποθετήστε ελέγχους σε κεφαλίδες ή πίνακες και συνδυάστε τα με μακροεντολές για πιο πλούσιες εμπειρίες χρήστη.

---

*Επόμενα βήματα*: εξερευνήστε **πώς να εισάγετε ActiveX** ελέγχους άλλων τύπων, μάθετε **πώς να προσθέσετε χειριστές συμβάντων για κουμπί εντολής** μέσω VBA, και διαβάστε για τις **καλύτερες πρακτικές εισαγωγής κουμπιού ActiveX** για συμβατότητα μεταξύ πλατφορμών.

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Ενσωμάτωση αντικειμένων OLE και ελέγχων ActiveX σε έγγραφα Word](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [Προσθήκη πεδίου φόρμας Combo Box σε έγγραφο Word με Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Προσθήκη πεδίου φόρμας Check Box σε έγγραφο Word με Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}