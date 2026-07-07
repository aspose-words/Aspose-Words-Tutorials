---
category: general
date: 2026-07-06
description: Ενεργοποιήστε τη λειτουργία ανάκτησης για να ανοίξετε ένα κατεστραμμένο
  αρχείο docx με το Aspose.Words. Μάθετε πώς να ανακτήσετε γρήγορα ένα κατεστραμμένο
  έγγραφο Word.
draft: false
keywords:
- enable recovery mode
- recover corrupted word document
- recover damaged docx file
- how to open corrupted docx
language: el
og_description: Η ενεργοποίηση της λειτουργίας ανάκτησης σάς επιτρέπει να ανοίξετε
  ένα κατεστραμμένο αρχείο docx και να προσπαθήσετε να ανακτήσετε ένα κατεστραμμένο
  έγγραφο Word.
og_title: Ενεργοποίηση λειτουργίας ανάκτησης – Ανάκτηση κατεστραμμένου εγγράφου Word
schemas:
- author: Aspose
  dateModified: '2026-07-06'
  description: Enable recovery mode to open a corrupted docx file with Aspose.Words.
    Learn how to recover corrupted Word document quickly.
  headline: Enable recovery mode – Recover corrupted Word document
  type: TechArticle
- questions:
  - answer: No. It only affects how the library reads the file in memory. The source
      remains untouched unless you explicitly call `Save`.
    question: Does enabling recovery mode modify the original file?
  - answer: Usually yes, as long as the underlying ZIP entry isn’t broken. If an image
      stream is missing, Aspose.Words will skip it and continue.
    question: Can I recover images that were embedded in the corrupted docx?
  - answer: Slightly, because the parser performs additional checks. The overhead
      is negligible for typical documents (<10 MB).
    question: Is recovery mode slower?
  - answer: '`RecoveryMode.Auto` (default) tries to recover only when an error occurs.
      `RecoveryMode.None` disables any recovery attempts. `RecoveryMode.Recover` forces
      the attempt every time. ## Full Working Example Below is a self‑contained console
      app you can copy‑paste into a new .NET project. It demonstrate'
    question: What other recovery options exist?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Document Recovery
- Word
title: Ενεργοποίηση λειτουργίας ανάκτησης – Ανάκτηση κατεστραμμένου εγγράφου Word
url: /el/net/programming-with-loadoptions/enable-recovery-mode-recover-corrupted-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ενεργοποίηση λειτουργίας ανάκτησης – Ανάκτηση κατεστραμμένου εγγράφου Word

Προσπαθήσατε ποτέ να ανοίξετε ένα **κατεστραμμένο docx** και να δείτε το παράθυρο σφάλματος να σας κοιτάζει; Είναι απογοητευτικό, ειδικά όταν το αρχείο περιέχει εβδομάδες δουλειά. Ευτυχώς, το Aspose.Words σας παρέχει έναν τρόπο *ενεργοποίησης της λειτουργίας ανάκτησης* ώστε να προσπαθήσετε να σώσετε το περιεχόμενο χωρίς χειροκίνητο copy‑paste.

Σε αυτόν τον οδηγό θα περάσουμε βήμα‑βήμα τις ακριβείς ενέργειες για **ενεργοποίηση της λειτουργίας ανάκτησης**, φόρτωση του κατεστραμμένου αρχείου και αποθήκευση ενός χρήσιμου αντιγράφου. Στο τέλος θα ξέρετε πώς να *ανακτήσετε κατεστραμμένα Word έγγραφα* προγραμματιστικά και ακόμη να χειριστείτε μια κατάσταση *ανάκτησης κατεστραμμένου docx αρχείου* με χάρη.

## Τι θα χρειαστείτε

- .NET 6 (ή οποιοδήποτε πρόσφατο .NET runtime) – η βιβλιοθήκη λειτουργεί και σε .NET Framework.
- Visual Studio 2022 ή VS Code – το αγαπημένο σας IDE αρκεί.
- **Aspose.Words for .NET** πακέτο NuGet (`Install-Package Aspose.Words`) – αυτή είναι η μόνη εξωτερική εξάρτηση.
- Ένα δείγμα κατεστραμμένου `docx` (θα το ονομάσουμε `corrupted.docx`).

Αυτό είναι όλο. Χωρίς επιπλέον εργαλεία, χωρίς χειροκίνητη επεξεργασία XML. Μόνο λίγες γραμμές C#.

![enable recovery mode in Aspose.Words](image-url-placeholder.png)

*Image alt text: enable recovery mode in Aspose.Words*

## Βήμα 1: Εγκατάσταση Aspose.Words και ρύθμιση του έργου

Ανοίξτε το τερματικό σας (ή το Package Manager Console) και εκτελέστε:

```bash
dotnet add package Aspose.Words
```

Εναλλακτικά, στο Visual Studio ανοίξτε **Tools → NuGet Package Manager → Manage NuGet Packages** και αναζητήστε *Aspose.Words*. Μόλις εγκατασταθεί, προσθέστε το namespace στην κορυφή του αρχείου σας:

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
```

> **Pro tip:** Κρατήστε τα πακέτα σας ενημερωμένα. Η λογική ανάκτησης βελτιώνεται με κάθε έκδοση.

## Βήμα 2: Ενεργοποίηση λειτουργίας ανάκτησης με `LoadOptions`

Η καρδιά της λύσης είναι η κλάση `LoadOptions`. Ορίζοντας την ιδιότητα `RecoveryMode` σε `RecoveryMode.Recover`, λέτε στο Aspose.Words να *ενεργοποιήσει τη λειτουργία ανάκτησης* κατά την ανάλυση του εγγράφου.

```csharp
// Step 2: Create LoadOptions and enable recovery mode
LoadOptions loadOptions = new LoadOptions
{
    RecoveryMode = RecoveryMode.Recover   // <-- this line turns on recovery
};
```

Γιατί είναι σημαντικό; Χωρίς λειτουργία ανάκτησης, το Aspose.Words διακόπτει την εκτέλεση στην πρώτη ένδειξη κατεστραμμένου αρχείου. Με αυτήν, η βιβλιοθήκη προσπαθεί να παρακάμψει τα κατεστραμμένα τμήματα και να δημιουργήσει ένα χρήσιμο αντικείμενο `Document`.

## Βήμα 3: Φόρτωση του πιθανώς κατεστραμμένου αρχείου

Τώρα φορτώνουμε πραγματικά το αρχείο. Αν το έγγραφο είναι πέρα από τη διόρθωση, το Aspose.Words θα επιστρέψει ακόμη ένα αντικείμενο `Document`, αλλά ορισμένα στοιχεία μπορεί να λείπουν.

```csharp
// Step 3: Load the potentially corrupted document using the recovery options
Document doc = new Document(@"C:\Temp\corrupted.docx", loadOptions);
```

Παρατηρήστε ότι η διαδρομή είναι μια απόλυτη συμβολοσειρά· προσαρμόστε τη στο φάκελο όπου βρίσκεται το δοκιμαστικό αρχείο σας. Ο κατασκευαστής `Document` διαβάζει το αρχείο **με ενεργοποιημένη τη λειτουργία ανάκτησης**, δίνοντάς σας την ευκαιρία να *ανακτήσετε κατεστραμμένο Word έγγραφο*.

## Βήμα 4: Επαλήθευση του τι ανακτήθηκε (προαιρετικό αλλά χρήσιμο)

Είναι καλή πρακτική να ελέγχετε το φορτωμένο έγγραφο πριν αποφασίσετε να το αντικαταστήσετε. Για έναν γρήγορο έλεγχο, μπορείτε να εκτυπώσετε τις πρώτες παραγράφους στην κονσόλα:

```csharp
// Optional: Print first 3 paragraphs to verify recovery
for (int i = 0; i < Math.Min(3, doc.FirstSection.Body.Paragraphs.Count); i++)
{
    Console.WriteLine($"Paragraph {i + 1}: {doc.FirstSection.Body.Paragraphs[i].GetText().Trim()}");
}
```

Αν δείτε ακατάληπτο κείμενο ή πολλές κενές συμβολοσειρές, το αρχείο μπορεί να είναι **πολύ κατεστραμμένο**. Παρόλα αυτά, έχετε πλέον ένα αντικείμενο `Document` που μπορείτε να επεξεργαστείτε—να προσθέσετε κεφαλίδα, να αντικαταστήσετε ελλιπείς εικόνες κ.λπ.

## Βήμα 5: Αποθήκευση του ανακτηθέντος εγγράφου

Αν ο γρήγορος έλεγχος φαίνεται εντάξει, γράψτε την ανακτημένη έκδοση σε νέο αρχείο. Αυτό το βήμα ουσιαστικά *ανακτά κατεστραμμένο docx αρχείο* και σας δίνει ένα καθαρό αντίγραφο που μπορείτε να ανοίξετε στο Word.

```csharp
// Step 5: Save the recovered document
string outputPath = @"C:\Temp\recovered.docx";
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Recovered document saved to: {outputPath}");
```

Αν το αρχικό αρχείο ήταν `.doc` ή άλλη μορφή, μπορείτε να αλλάξετε το `SaveFormat` αντίστοιχα (π.χ., `SaveFormat.Pdf` για έξοδο PDF).

## Βήμα 6: Διαχείριση εξαιρέσεων και ειδικών περιπτώσεων

Ακόμη και με τη λειτουργία ανάκτησης, ορισμένα καταστροφικά σενάρια είναι ακατάβλητα (π.χ., εντελώς κομμένα zip structures). Τυλίξτε τη φόρτωση σε μπλοκ try‑catch για να εμφανίσετε αυτά τα ζητήματα:

```csharp
try
{
    Document doc = new Document(@"C:\Temp\corrupted.docx", loadOptions);
    // proceed with saving...
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to recover the document: {ex.Message}");
    // You might log the stack trace or notify the user.
}
```

Μια συχνή ερώτηση είναι **«πώς να ανοίξετε κατεστραμμένο docx»** όταν το αρχείο είναι κωδικοποιημένο με κωδικό. Η λειτουργία ανάκτησης **δεν** παρακάμπτει την κρυπτογράφηση· θα χρειαστείτε ακόμα τον κωδικό. Σε αυτήν την περίπτωση, ορίστε `LoadOptions.Password` πριν τη φόρτωση.

## Συχνές Ερωτήσεις (FAQ)

**Ε: Η ενεργοποίηση της λειτουργίας ανάκτησης τροποποιεί το αρχικό αρχείο;**  
Α: Όχι. Επηρεάζει μόνο τον τρόπο που η βιβλιοθήκη διαβάζει το αρχείο στη μνήμη. Η πηγή παραμένει αμετάβλητη εκτός αν εσείς καλέσετε ρητά το `Save`.

**Ε: Μπορώ να ανακτήσω εικόνες που ήταν ενσωματωμένες στο κατεστραμμένο docx;**  
Α: Συνήθως ναι, εφόσον η υποκείμενη καταχώρηση ZIP δεν είναι κατεστραμμένη. Αν λείπει το ρεύμα εικόνας, το Aspose.Words θα το παραλείψει και θα συνεχίσει.

**Ε: Η λειτουργία ανάκτησης είναι πιο αργή;**  
Α: Λίγο πιο αργή, επειδή ο parser εκτελεί επιπλέον ελέγχους. Η επιβάρυνση είναι αμελητέα για τυπικά έγγραφα (<10 MB).

**Ε: Ποιες άλλες επιλογές ανάκτησης υπάρχουν;**  
Α: `RecoveryMode.Auto` (προεπιλογή) προσπαθεί να ανακτήσει μόνο όταν προκύψει σφάλμα. `RecoveryMode.None` απενεργοποιεί οποιεσδήποτε προσπάθειες ανάκτησης. `RecoveryMode.Recover` επιβάλλει την προσπάθεια κάθε φορά.

## Πλήρες Παράδειγμα Εργασίας

Παρακάτω υπάρχει μια αυτόνομη εφαρμογή κονσόλας που μπορείτε να αντιγράψετε‑επικολλήσετε σε νέο .NET project. Δείχνει ολόκληρη τη ροή—από την εγκατάσταση του πακέτου μέχρι την αποθήκευση του ανακτηθέντος αρχείου.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

namespace RecoverCorruptedDocx
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the corrupted document
            string inputPath = @"C:\Temp\corrupted.docx";
            // Where the recovered file will be written
            string outputPath = @"C:\Temp\recovered.docx";

            // Step 1: Create LoadOptions and enable recovery mode
            LoadOptions loadOptions = new LoadOptions
            {
                RecoveryMode = RecoveryMode.Recover
            };

            try
            {
                // Step 2: Load the document with recovery enabled
                Document doc = new Document(inputPath, loadOptions);

                // Optional sanity check – print first three paragraphs
                Console.WriteLine("=== First three paragraphs after recovery ===");
                for (int i = 0; i < Math.Min(3, doc.FirstSection.Body.Paragraphs.Count); i++)
                {
                    Console.WriteLine($"Paragraph {i + 1}: {doc.FirstSection.Body.Paragraphs[i].GetText().Trim()}");
                }

                // Step 3: Save the recovered document
                doc.Save(outputPath, SaveFormat.Docx);
                Console.WriteLine($"\nRecovered document saved to: {outputPath}");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Failed to open or recover the document: {ex.Message}");
            }
        }
    }
}
```

**Αναμενόμενο αποτέλεσμα (αν η ανάκτηση πετύχει):**

```
=== First three paragraphs after recovery ===
Paragraph 1: Project Overview
Paragraph 2: This document outlines...
Paragraph 3: ...

Recovered document saved to: C:\Temp\recovered.docx
```

Αν το αρχείο είναι πέρα από τη βοήθεια, θα δείτε ένα μήνυμα σφάλματος αντί για την εκτύπωση των παραγράφων.

## Συμπέρασμα

Δείξαμε πώς να **ενεργοποιήσετε τη λειτουργία ανάκτησης** στο Aspose.Words, να φορτώσετε ένα κατεστραμμένο `docx` και να **ανακτήσετε δεδομένα κατεστραμμένου Word εγγράφου** σε νέο αρχείο. Το ίδιο μοτίβο σας επιτρέπει να *ανακτήσετε κατεστραμμένο docx αρχείο* σε μαζικές εργασίες, αυτοματοποιημένα συνημμένα email, ή

## Τι Θα Πρέπει Να Μάθετε Στη Σύντομη Μελλοντική

Τα παρακάτω tutorials καλύπτουν στενά σχετικές θεματικές που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη κώδικα με βήμα‑βήμα εξηγήσεις για να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [how to recover docx – set recovery mode & open corrupted Word files](/words/english/net/programming-with-loadoptions/how-to-recover-docx-set-recovery-mode-open-corrupted-word-fi/)
- [how to recover docx with Aspose.Words – step by step](/words/english/net/programming-with-loadoptions/how-to-recover-docx-with-aspose-words-step-by-step/)
- [Recover Damaged Word File – Complete Guide to Open Corrupted DOCX & Get Page](/words/english/net/programming-with-loadoptions/recover-damaged-word-file-complete-guide-to-open-corrupted-d/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}