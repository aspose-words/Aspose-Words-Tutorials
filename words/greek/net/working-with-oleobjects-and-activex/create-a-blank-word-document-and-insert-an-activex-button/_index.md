---
category: general
date: 2026-11-18
description: Δημιουργήστε ένα κενό έγγραφο Word και εισάγετε ένα κουμπί ActiveX με
  C#. Μάθετε πώς να προσθέσετε έλεγχο, να ορίσετε τη λεζάντα του κουμπιού και να αποθηκεύσετε
  το αρχείο.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- how to add control
- insert activex button
- set button caption
language: el
lastmod: 2026-11-18
og_description: Δημιουργήστε ένα κενό έγγραφο Word και εισάγετε ένα κουμπί ActiveX
  χρησιμοποιώντας C#. Ακολουθήστε αυτό το πλήρες σεμινάριο για να προσθέσετε τον έλεγχο,
  να ορίσετε τη λεζάντα του κουμπιού και να αποθηκεύσετε το αποτέλεσμα.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX button with
  the caption “Press”
og_title: Δημιουργήστε ένα κενό έγγραφο Word και εισάγετε ένα κουμπί ActiveX – οδηγός
  βήμα‑προς‑βήμα
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  headline: Create a blank Word document and insert an ActiveX button
  type: TechArticle
- description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  name: Create a blank Word document and insert an ActiveX button
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 or later (the code also works with .NET Framework 4.6+). * Aspose.Words
      for .NET installed (`Install-Package Aspose.Words`). * Basic familiarity with
      C# and Visual Studio or any .NET‑compatible IDE.'
  - name: Tip
    text: 'If you need the button to appear on a specific page, move the builder’s
      cursor first:'
  - name: Expected result
    text: Opening `with_button.docx` in Word shows a blank page with a rectangular
      button labeled **Press**. Clicking the button does nothing by default because
      no VBA macro is attached, but the control is fully functional and can be wired
      to code later.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Δημιουργήστε ένα κενό έγγραφο Word και εισάγετε ένα κουμπί ActiveX
url: /el/net/working-with-oleobjects-and-activex/create-a-blank-word-document-and-insert-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργήστε ένα κενό έγγραφο Word και εισάγετε ένα κουμπί ActiveX

Αν χρειάζεστε **να δημιουργήσετε ένα κενό έγγραφο Word** και να τοποθετήσετε ένα διαδραστικό κουμπί ActiveX μέσα του, αυτός ο οδηγός σας δείχνει ακριβώς πώς να το κάνετε με το Aspose.Words for .NET. Θα δείτε τον πλήρη κώδικα, θα καταλάβετε γιατί κάθε γραμμή είναι σημαντική και θα μάθετε πώς να **ορίσετε τη λεζάντα του κουμπιού** ώστε ο έλεγχος να φαίνεται έτοιμος για αλληλεπίδραση με τον χρήστη.

Εκτός από τον κύριο στόχο, θα καλύψουμε **πώς να εισάγετε ActiveX**, τα βήματα **πώς να προσθέσετε έλεγχο** σε ένα αρχείο Word, και τις λεπτομέρειες του **εισαγωγής κουμπιού ActiveX** με προσαρμοσμένη λεζάντα. Στο τέλος θα έχετε ένα επαναχρησιμοποιήσιμο πρότυπο για οποιοδήποτε σενάριο αυτοματοποίησης εγγράφων που απαιτεί ενσωματωμένα στοιχεία UI.

## Τι θα μάθετε

* Πώς να **δημιουργήσετε ένα κενό έγγραφο Word** προγραμματιστικά.  
* Οι ακριβείς κλήσεις API που απαιτούνται για **εισαγωγή κουμπιού ActiveX** και διαμόρφωση των ιδιοτήτων του.  
* Πώς να **ορίσετε τη λεζάντα του κουμπιού** ώστε ο έλεγχος να εμφανίζει το επιθυμητό κείμενο.  
* Συμβουλές για αποθήκευση του αρχείου σε θέση της επιλογής σας και αντιμετώπιση κοινών προβλημάτων.

### Προαπαιτούμενα

* .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.6+).  
* Το Aspose.Words for .NET εγκατεστημένο (`Install-Package Aspose.Words`).  
* Βασική εξοικείωση με C# και Visual Studio ή οποιοδήποτε IDE συμβατό με .NET.

---

## Δημιουργία κενού εγγράφου Word με Aspose.Words

Το πρώτο βήμα είναι η δημιουργία ενός κενό αντικειμένου `Document`. Αυτό το αντικείμενο αντιπροσωπεύει ένα αρχείο Word που δεν περιέχει περιεχόμενο μέχρι να προσθέσουμε κάτι.

```csharp
// Step 1: Create a new blank document
Document document = new Document();
```

*Γιατί είναι σημαντικό*: Ένα κενό `Document` σας παρέχει έναν καθαρό καμβά. Μπορείτε αργότερα να προσθέσετε παραγράφους, πίνακες ή ελέγχους χωρίς να ανησυχείτε για υπάρχουσα μορφοποίηση.

---

## Αρχικοποίηση DocumentBuilder για εργασία με το έγγραφο

`DocumentBuilder` είναι μια βοηθητική κλάση που σας επιτρέπει να εισάγετε περιεχόμενο στη τρέχουσα θέση του δρομέα. Παρακολουθεί αυτόματα πού βρίσκεστε στο έγγραφο.

```csharp
// Step 2: Initialise a DocumentBuilder for the empty document
DocumentBuilder builder = new DocumentBuilder(document);
```

*Γιατί είναι σημαντικό*: Χωρίς ένα `DocumentBuilder` θα έπρεπε να χειριστείτε το δέντρο κόμβων χαμηλού επιπέδου χειροκίνητα. Ο builder απλοποιεί την εισαγωγή κειμένου, εικόνων και ελέγχων ActiveX.

---

## Πώς να εισάγετε ένα κουμπί ActiveX (insert activex button)

Τώρα χρησιμοποιούμε το `InsertForms2OleControl` για να ενσωματώσουμε έναν έλεγχο ActiveX. Η μέθοδος απαιτεί τρία ορίσματα:

1. Ο τύπος του ελέγχου (`OleControlType.CommandButton`).  
2. Ένα εσωτερικό όνομα για τον έλεγχο (χρησιμοποιείται από VBA ή κώδικα μακροεντολών).  
3. Ένα `RectangleF` που ορίζει τη θέση και το μέγεθος στη σελίδα.

```csharp
// Step 3: Insert a CommandButton ActiveX control at the current cursor position
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,          // type of control
    "ClickMe",                             // internal name (identifier)
    new System.Drawing.RectangleF(0, 0, 100, 30)); // x, y, width, height
```

*Γιατί είναι σημαντικό*: Αυτό είναι ο πυρήνας του **πώς να εισάγετε activex** σε ένα έγγραφο Word. Οι συντεταγμένες του ορθογωνίου εκφράζονται σε points (1 point = 1/72 ίντσα). Προσαρμόστε τις ώστε να τοποθετήσετε το κουμπί όπου το χρειάζεστε.

### Συμβουλή

Αν χρειάζεστε το κουμπί να εμφανιστεί σε συγκεκριμένη σελίδα, μετακινήστε πρώτα τον δρομέα του builder:

```csharp
builder.MoveToSection(0);  // moves to the first (and only) section
builder.InsertParagraph(); // ensures there is a paragraph to host the control
```

---

## Πώς να ορίσετε τη λεζάντα του κουμπιού (set button caption)

Αφού τοποθετηθεί ο έλεγχος, μπορείτε να τροποποιήσετε τις ιδιότητές του. Η πιο εμφανής ιδιότητα είναι το `Caption`, που καθορίζει το κείμενο που εμφανίζεται στο κουμπί.

```csharp
// Step 4: Set the visible caption of the button
commandButton.Caption = "Press";
```

*Γιατί είναι σημαντικό*: Οι χρήστες βλέπουν τη λεζάντα, όχι το εσωτερικό όνομα. Η αλλαγή της κάνει το κουμπί σημαντικό στο τελικό έγγραφο.

---

## Αποθήκευση του εγγράφου που περιέχει το κουμπί

Τέλος, γράψτε το έγγραφο στο δίσκο. Μπορείτε να επιλέξετε οποιαδήποτε υποστηριζόμενη μορφή (`.docx`, `.pdf`, κλπ.). Εδώ αποθηκεύουμε ως έγγραφο Word.

```csharp
// Step 5: Save the document with the ActiveX button
string outputPath = @"C:\Temp\with_button.docx";
document.Save(outputPath);
```

*Γιατί είναι σημαντικό*: Η διατήρηση του αρχείου σας επιτρέπει να το ανοίξετε στο Microsoft Word και να δοκιμάσετε το κουμπί. Όταν το έγγραφο ανοίξει, το κουμπί θα εμφανιστεί με τη λεζάντα “Press”.

### Αναμενόμενο αποτέλεσμα

Ανοίγοντας το `with_button.docx` στο Word εμφανίζει μια κενή σελίδα με ένα ορθογώνιο κουμπί με την ετικέτα **Press**. Κάνοντας κλικ στο κουμπί δεν συμβαίνει τίποτα από προεπιλογή επειδή δεν υπάρχει συνδεδεμένη μακροεντολή VBA, αλλά ο έλεγχος είναι πλήρως λειτουργικός και μπορεί να συνδεθεί με κώδικα αργότερα.

---

## Πώς να προσθέσετε έλεγχο σε συγκεκριμένη παράγραφο (how to add control)

Μερικές φορές θέλετε το κουμπί μέσα σε μια συγκεκριμένη παράγραφο, για παράδειγμα μετά από κάποιο κείμενο οδηγιών. Χρησιμοποιήστε το `MoveTo` για να τοποθετήσετε τον builder πριν την εισαγωγή του ελέγχου.

```csharp
// Example: add a paragraph, then insert the button after it
builder.Writeln("Click the button below to continue:");
builder.InsertParagraph(); // creates a new empty paragraph
builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    "ContinueBtn",
    new System.Drawing.RectangleF(0, 0, 120, 35));
```

*Γιατί είναι σημαντικό*: Αυτό το πρότυπο δείχνει **πώς να προσθέσετε έλεγχο** στο πλαίσιο, διασφαλίζοντας ότι η διάταξη του εγγράφου παραμένει λογική.

---

## Συνηθισμένα προβλήματα και πώς να τα αποφύγετε

| Issue | Why it happens | Fix |
|-------|----------------|-----|
| Το κουμπί εμφανίζεται εκτός σελίδας | Οι συντεταγμένες του ορθογωνίου είναι εκτός των περιθωρίων της σελίδας | Χρησιμοποιήστε το `builder.PageSetup` για να λάβετε τις διαστάσεις της σελίδας και να υπολογίσετε ένα ασφαλές `RectangleF`. |
| Η λεζάντα δεν εμφανίζεται | `Caption` ορίζεται πριν ο έλεγχος είναι πλήρως αρχικοποιημένος | Ορίστε το `Caption` **μετά** την κλήση `InsertForms2OleControl`, όπως φαίνεται στο Βήμα 4. |
| Το έγγραφο αποθηκεύεται χωρίς το κουμπί | Ο δρομέας του builder μετακινήθηκε μετά την εισαγωγή χωρίς να γίνει δέσμευση των αλλαγών | Διατηρήστε τον builder στην ίδια σελίδα ή καλέστε το `builder.Document.UpdatePageLayout()` πριν την αποθήκευση. |

---

## Πλήρες, εκτελέσιμο παράδειγμα

Παρακάτω βρίσκεται το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε, επικολλήσετε και εκτελέσετε. Δημιουργεί ένα κενό αρχείο Word, εισάγει ένα κουμπί ActiveX, ορίζει τη λεζάντα του και αποθηκεύει το αποτέλεσμα.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Initialise DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(document);

        // Optional: add some explanatory text
        builder.Writeln("Below is an ActiveX button created programmatically:");
        builder.InsertParagraph();

        // 3️⃣ Insert the ActiveX CommandButton
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            "MyButton",
            new RectangleF(0, 0, 100, 30));

        // 4️⃣ Set the button caption
        commandButton.Caption = "Press";

        // 5️⃣ Save the document
        string outputPath = @"C:\Temp\with_button.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Αποτέλεσμα**: Μετά την εκτέλεση του προγράμματος, ανοίξτε το `C:\Temp\with_button.docx` στο Microsoft Word. Θα δείτε μια ενιαία σελίδα με το κείμενο “Below is an ActiveX button created programmatically:” ακολουθούμενο από ένα κουμπί με την ετικέτα **Press**.

---

## Συμπέρασμα

Τώρα γνωρίζετε πώς να **δημιουργήσετε ένα κενό έγγραφο Word**, **εισάγετε ένα κουμπί ActiveX**, **ορίσετε τη λεζάντα του κουμπιού**, και **αποθηκεύσετε** το αποτέλεσμα χρησιμοποιώντας το Aspose.Words for .NET. Το ίδιο πρότυπο μπορεί να επεκταθεί σε άλλους ελέγχους ActiveX (checkboxes, list boxes κλπ.) αλλάζοντας το `OleControlType`.  

Στη συνέχεια, μπορείτε να εξερευνήσετε **πώς να εισάγετε συμβάντα κουμπιού ActiveX** με VBA, ή **πώς να προσθέσετε έλεγχο** σε υπάρχοντα έγγραφα που ήδη περιέχουν περιεχόμενο. Και τα δύο θέματα βασίζονται άμεσα στις έννοιες που καλύφθηκαν εδώ.

Καλή προγραμματιστική δουλειά, και μη διστάσετε να πειραματιστείτε με διαφορετικά μεγέθη, θέσεις και λεζάντες ώστε να ταιριάζουν στις απαιτήσεις UI της εφαρμογής σας!

## Τι θα πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να δημιουργήσετε έγγραφο Word C# με κουμπί εντολής ActiveX](/words/english/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/)
- [Πώς να προσθέσετε κουμπί ActiveX σε έγγραφο Word με το Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}