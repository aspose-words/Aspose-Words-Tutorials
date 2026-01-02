---
category: general
date: 2026-01-02
description: Πώς να ανακτήσετε DOCX χρησιμοποιώντας το Aspose.Words LoadOptions. Μάθετε
  πώς να ορίσετε τη λειτουργία ανάκτησης, να διορθώσετε κατεστραμμένα έγγραφα Word
  και να διαχειριστείτε με ασφάλεια τα κατεστραμμένα αρχεία.
draft: false
keywords:
- how to recover docx
- set recovery mode
- recover corrupted word document
- recover damaged word file
- aspose words loadoptions
language: el
og_description: Πώς να ανακτήσετε αρχεία DOCX με το Aspose.Words. Αυτός ο οδηγός σας
  δείχνει πώς να ορίσετε τη λειτουργία ανάκτησης, να επισκευάσετε κατεστραμμένα έγγραφα
  Word και να φορτώνετε με ασφάλεια τα κατεστραμμένα αρχεία.
og_title: Πώς να ανακτήσετε αρχεία DOCX – Εκπαιδευτικό πρόγραμμα Aspose.Words LoadOptions
tags:
- Aspose.Words
- C#
- Document Recovery
title: Πώς να ανακτήσετε αρχεία DOCX με το Aspose.Words – Οδηγός βήμα‑προς‑βήμα
url: /el/net/programming-with-loadoptions/how-to-recover-docx-files-with-aspose-words-step-by-step-gui/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Ανακτήσετε Αρχεία DOCX με το Aspose.Words – Πλήρης Οδηγός Προγραμματισμού

Έχετε αναρωτηθεί ποτέ **πώς να ανακτήσετε αρχεία docx** που δεν ανοίγουν επειδή είναι κατεστραμμένα; Δεν είστε ο μόνος που αντιμετωπίζει αυτό το πρόβλημα. Σε πολλά πραγματικά έργα ένα κατεστραμμένο αρχείο Word μπορεί να σταματήσει τη ροή εργασίας, αλλά το Aspose.Words σας παρέχει έναν αξιόπιστο τρόπο να φέρετε αυτά τα έγγραφα ξανά στη ζωή.

Σε αυτό το tutorial θα περάσουμε από τα ακριβή βήματα για **να ορίσουμε τη λειτουργία ανάκτησης**, να φορτώσουμε ένα κατεστραμμένο αρχείο και να επαληθεύσουμε ότι το έγγραφο ανακτήθηκε επιτυχώς. Στο τέλος θα ξέρετε πώς να **ανακτήσετε κατεστραμμένο word document**, **να ανακτήσετε damaged word file**, και να χρησιμοποιήσετε την κλάση `Aspose.Words.LoadOptions` σαν επαγγελματίας.

## Τι Θα Μάθετε

- Τον σκοπό του `LoadOptions.RecoveryMode` και γιατί είναι σημαντικός.  
- Πώς να διαμορφώσετε την επιλογή για **ανακτήσετε corrupted docx** αρχεία.  
- Ένα πλήρες, εκτελέσιμο παράδειγμα C# που μπορείτε να αντιγράψετε‑και‑επικολλήσετε στο Visual Studio.  
- Συνηθισμένα προβλήματα (π.χ. ελλιπείς γραμματοσειρές, αρχεία με κωδικό) και πώς να τα αντιμετωπίσετε.  
- Συμβουλές για δοκιμή της λογικής ανάκτησης και καταγραφή αποτελεσμάτων.

### Προαπαιτούμενα

- .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.7+).  
- Ένα έγκυρο license του Aspose.Words for .NET (ή δωρεάν δοκιμή).  
- Βασική εξοικείωση με C# και το μοντέλο εφαρμογών console.  

> **Pro tip:** Αν χρησιμοποιείτε τη δωρεάν δοκιμή, θυμηθείτε ότι προσθέτει υδατογράφημα στην πρώτη σελίδα των ανακτηθέντων εγγράφων—τέλειο για δοκιμές αλλά όχι για παραγωγή.

---

## Βήμα 1: Εγκατάσταση Aspose.Words και Προετοιμασία του Έργου Σας

Πρώτα απ’ όλα, προσθέστε το πακέτο NuGet Aspose.Words στο έργο σας:

```bash
dotnet add package Aspose.Words
```

Αφού εγκατασταθεί το πακέτο, δημιουργήστε μια νέα εφαρμογή console (ή ενσωματώστε τον κώδικα σε υπάρχουσα υπηρεσία). Οι οδηγίες `using` που θα χρειαστείτε είναι:

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
```

Αυτοί οι χώροι ονομάτων σας δίνουν πρόσβαση στην κλάση `Document` και στο αντικείμενο `LoadOptions` που σας επιτρέπει να **ορίσετε τη λειτουργία ανάκτησης**.

---

## Βήμα 2: Διαμόρφωση LoadOptions για **Ορισμό Recovery Mode**

Η καρδιά της διαδικασίας ανάκτησης είναι το αντικείμενο `LoadOptions`. Από προεπιλογή το Aspose.Words ρίχνει εξαίρεση όταν συναντά κατεστραμμένη δομή. Η αλλαγή του `RecoveryMode` σε `Recover` λέει στη βιβλιοθήκη να κάνει το καλύτερο δυνατό για να διατηρήσει το έγγραφο ακέραιο.

```csharp
// Step 2: Create LoadOptions with RecoveryMode = Recover
LoadOptions loadOptions = new LoadOptions
{
    // Keep as much content as possible despite corruption
    RecoveryMode = RecoveryMode.Recover
};
```

### Γιατί `RecoveryMode.Recover`;

- **Διατηρεί τη διάταξη:** Προσπαθεί να διατηρήσει τη μορφοποίηση παραγράφων, πίνακες και εικόνες.  
- **Αποτρέπει απώλεια δεδομένων:** Αντί να διακόψει, η βιβλιοθήκη παραλείπει μόνο τα κατεστραμμένα τμήματα.  
- **Απλοποιεί τη διαχείριση σφαλμάτων:** Μπορείτε να φορτώσετε το έγγραφο μέσα σε try/catch και να έχετε ακόμα ένα χρήσιμο αντικείμενο `Document`.

Αν χρειάζεστε πιο αυστηρή προσέγγιση (π.χ. να απορρίψετε οποιοδήποτε κατεστραμμένο αρχείο), μπορείτε να αλλάξετε σε `RecoveryMode.Strict`. Για τις περισσότερες περιπτώσεις ανάκτησης, όμως, το `Recover` είναι η ιδανική επιλογή.

---

## Βήμα 3: Φόρτωση του Κατεστραμμένου DOCX με τις Διαμορφωμένες Επιλογές

Τώρα ανοίγουμε πραγματικά το αρχείο. Αντικαταστήστε το `"YOUR_DIRECTORY/input.docx"` με τη διαδρομή του αρχείου που υποπτεύεστε ότι είναι κατεστραμμένο.

```csharp
// Step 3: Load the possibly corrupted DOCX
string inputPath = @"C:\Docs\input.docx";

Document doc;
try
{
    doc = new Document(inputPath, loadOptions);
    Console.WriteLine($"Successfully loaded '{Path.GetFileName(inputPath)}' with RecoveryMode = {loadOptions.RecoveryMode}");
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to load document: {ex.Message}");
    return;
}
```

Το μπλοκ `try/catch` είναι απαραίτητο όταν **ανακτήσετε corrupted word document** αρχεία, επειδή κάποια κατεστραμμένα τμήματα μπορεί να είναι πέρα από ό,τι μπορεί να σώσει το Aspose. Το catch παρέχει μια χαλαρή πτώση αντί για σκληρό κρεμάσιμο.

---

## Βήμα 4: Επαλήθευση του Αποτελέσματος Ανάκτησης (Προαιρετικό αλλά Χρήσιμο)

Ένας γρήγορος τρόπος για να επιβεβαιώσετε ότι το έγγραφο ανακτήθηκε είναι να ελέγξετε μερικές ιδιότητες ή να αποθηκεύσετε ένα αντίγραφο για οπτική επιθεώρηση.

```csharp
// Step 4: Simple verification – print page count and first paragraph text
Console.WriteLine($"Page count after recovery: {doc.PageCount}");
if (doc.FirstSection?.Body?.Paragraphs?.Count > 0)
{
    Console.WriteLine("First paragraph preview:");
    Console.WriteLine(doc.FirstSection.Body.Paragraphs[0].GetText());
}

// Optional: Save a copy for manual review
string outputPath = @"C:\Docs\recovered_output.docx";
doc.Save(outputPath);
Console.WriteLine($"Recovered document saved to: {outputPath}");
```

Αν το `PageCount` είναι μεγαλύτερο του μηδενός και η πρώτη παράγραφος περιέχει αναγνώσιμο κείμενο, πιθανότατα **ανακτήσατε ένα damaged word file** επιτυχώς. Το άνοιγμα του αποθηκευμένου `recovered_output.docx` στο Microsoft Word θα πρέπει να δείχνει ένα κυρίως ακέραιο έγγραφο.

---

## Βήμα 5: Διαχείριση Ακραίων Περιπτώσεων και Συνηθισμένων Παγίδων

### Ελλιπείς Γραμματοσειρές

Όταν ένα κατεστραμμένο αρχείο αναφέρει γραμματοσειρές που δεν είναι εγκατεστημένες, το Aspose μπορεί να τις αντικαταστήσει αυτόματα. Για να αποφύγετε απρόσμενες αλλαγές διάταξης, μπορείτε να ενσωματώσετε τις γραμματοσειρές πριν την αποθήκευση:

```csharp
doc.FontInfos.FontEmbeddingMode = FontEmbeddingMode.EmbedAll;
```

### Αρχεία με Κωδικό

Αν το πηγαίο DOCX είναι κρυπτογραφημένο, το `LoadOptions` δέχεται επίσης κωδικό πρόσβασης:

```csharp
loadOptions.Password = "yourPassword";
```

Συνδυάστε αυτό με `RecoveryMode.Recover` για να προσπαθήσετε αποσυμπίεση *και* ανάκτηση σε μία κλήση.

### Μεγάλα Αρχεία

Για πολύ μεγάλα έγγραφα, σκεφτείτε τη ροή (streaming) του αρχείου αντί να το φορτώσετε ολόκληρο στη μνήμη:

```csharp
using (FileStream fs = new FileStream(inputPath, FileMode.Open, FileAccess.Read))
{
    doc = new Document(fs, loadOptions);
}
```

Το streaming λειτουργεί απρόσκοπτα με `aspose words loadoptions` και κρατά την εφαρμογή σας ανταποκρινόμενη.

---

## Πλήρες Παράδειγμα Λειτουργίας

Συνδυάζοντας όλα τα παραπάνω, εδώ είναι μια αυτόνομη εφαρμογή console που μπορείτε να μεταγλωττίσετε και να εκτελέσετε:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1: Prepare LoadOptions – set recovery mode
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            RecoveryMode = RecoveryMode.Recover,
            // Uncomment if you know the file is password protected
            // Password = "mySecret"
        };

        // -------------------------------------------------
        // Step 2: Define input and output paths
        // -------------------------------------------------
        string inputPath = @"C:\Docs\input.docx";
        string outputPath = @"C:\Docs\recovered_output.docx";

        // -------------------------------------------------
        // Step 3: Load the document with recovery options
        // -------------------------------------------------
        Document doc;
        try
        {
            doc = new Document(inputPath, loadOptions);
            Console.WriteLine($"Document loaded with RecoveryMode = {loadOptions.RecoveryMode}");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Unable to load document: {ex.Message}");
            return;
        }

        // -------------------------------------------------
        // Step 4: Quick verification
        // -------------------------------------------------
        Console.WriteLine($"Page count after recovery: {doc.PageCount}");
        if (doc.FirstSection?.Body?.Paragraphs?.Count > 0)
        {
            Console.WriteLine("First paragraph preview:");
            Console.WriteLine(doc.FirstSection.Body.Paragraphs[0].GetText());
        }

        // -------------------------------------------------
        // Step 5: Save the recovered file
        // -------------------------------------------------
        doc.Save(outputPath);
        Console.WriteLine($"Recovered file saved to: {outputPath}");
    }
}
```

**Αναμενόμενο αποτέλεσμα** (όταν το αρχείο μπορεί να σωθεί):

```
Document loaded with RecoveryMode = Recover
Page count after recovery: 3
First paragraph preview:
Hello world!
Recovered file saved to: C:\Docs\recovered_output.docx
```

Αν το αρχείο είναι πέρα από την επισκευή, το μπλοκ catch θα εμφανίσει μήνυμα σφάλματος.

---

## Συχνές Ερωτήσεις

**Ε: Λειτουργεί αυτό με αρχεία .doc (δυαδικά);**  
Α: Ναι. Η ίδια κλάση `LoadOptions` ισχύει για `.doc`, `.docx`, `.rtf`, και ακόμη `.odt`. Απλώς αλλάξτε την επέκταση του αρχείου στη διαδρομή.

**Ε: Μπορώ να ανακτήσω μόνο ένα συγκεκριμένο τμήμα του εγγράφου (π.χ. έναν πίνακα);**  
Α: Το Aspose.Words δεν προσφέρει επιλογική ανάκτηση από μόνο του, αλλά μπορείτε να φορτώσετε ολόκληρο το αρχείο, να ελέγξετε `doc.GetChild(NodeType.Table, 0, true)`, και να εξάγετε ό,τι έχει επιβιώσει.

**Ε: Θα διατηρήσει το ανακτημένο αρχείο τα αρχικά μεταδεδομένα (συγγραφέας, ημερομηνία δημιουργίας);**  
Α: Τα περισσότερα μεταδεδομένα επιβιώνουν τη διαδικασία ανάκτησης, αλλά σοβαρά κατεστραμμένα τμήματα μπορεί να χαθούν. Μπορείτε πάντα να επαναεφαρμόσετε τα μεταδεδομένα μετά τη φόρτωση:

```csharp
doc.BuiltInDocumentProperties.Author = "Recovered by Aspose";
```

---

## Συμπέρασμα

Καλύψαμε **πώς να ανακτήσετε αρχεία docx** χρησιμοποιώντας το Aspose.Words, από τη διαμόρφωση του `LoadOptions` μέχρι την επαλήθευση του αποτελέσματος και τη διαχείριση ακραίων περιπτώσεων. Με το **ορισμό recovery mode** σε `Recover`, δίνετε στη βιβλιοθήκη την άδεια να συνδέσει ό,τι τμήματα του εγγράφου είναι ακόμα χρήσιμα, μετατρέποντας ένα σπασμένο `.docx` σε ένα αναγνώσιμο, επεξεργάσιμο αρχείο.

Τώρα μπορείτε με σιγουριά **να ανακτήσετε corrupted word document** παραδείγματα στις δικές σας εφαρμογές, να αυτοματοποιήσετε μαζικές επισκευές, ή να δημιουργήσετε UI που επιτρέπει στους τελικούς χρήστες να ανεβάζουν κατεστραμμένα αρχεία και να λαμβάνουν μια καθαρή έκδοση πίσω.

**Επόμενα βήματα:**  
- Πειραματιστείτε με `RecoveryMode.Strict` για να δείτε τη διαφορά στην αναφορά σφαλμάτων.  
- Συνδυάστε αυτήν την προσέγγιση με Aspose.PDF για να μετατρέψετε αυτόματα το ανακτηθέν DOCX σε PDF.  
- Εξερευνήστε τις ιδιότητες του `LoadOptions` για διαχείριση κρυπτογραφημένων αρχείων, προσαρμοσμένων φακέλων γραμματοσειρών ή βελτιστοποιημένης φόρτωσης μνήμης.

Έχετε περισσότερες ερωτήσεις σχετικά με σενάρια **recover damaged word file**; Αφήστε ένα σχόλιο, και καλή προγραμματιστική!  

![Screenshot of a recovered DOCX displayed in Microsoft Word – how to recover docx](/images/recover-docx-screenshot.png)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}