---
category: general
date: 2026-06-08
description: Ανοίξτε ένα κατεστραμμένο αρχείο Word σε C# χρησιμοποιώντας το Aspose.Words.
  Μάθετε πώς να ορίσετε τη λειτουργία ανάκτησης και να επαναφέρετε το κατεστραμμένο
  έγγραφο αποδοτικά.
draft: false
keywords:
- open corrupted word file
- set recovery mode
- recover corrupted document
- Aspose.Words recovery
- handling damaged docx
language: el
og_description: Ανοίξτε κατεστραμμένο αρχείο Word σε C# με το Aspose.Words. Αυτός
  ο οδηγός δείχνει πώς να ορίσετε τη λειτουργία ανάκτησης και να ανακτήσετε με ασφάλεια
  το κατεστραμμένο έγγραφο.
og_title: Άνοιγμα κατεστραμμένου αρχείου Word σε C# – Οδηγός βήμα‑προς‑βήμα
schemas:
- author: Aspose
  dateModified: '2026-06-08'
  description: Open corrupted word file in C# using Aspose.Words. Learn how to set
    recovery mode and recover corrupted document efficiently.
  headline: Open Corrupted Word File in C# – Complete Guide
  type: TechArticle
- description: Open corrupted word file in C# using Aspose.Words. Learn how to set
    recovery mode and recover corrupted document efficiently.
  name: Open Corrupted Word File in C# – Complete Guide
  steps:
  - name: '**Create `LoadOptions`** – decide how strict the loader should be.'
    text: '**Create `LoadOptions`** – decide how strict the loader should be.'
  - name: '**Pick a `RecoveryMode`** – *Passthrough* for a raw load, *Recover* for
      auto‑fix, or *Throw* to catch problems early.'
    text: '**Pick a `RecoveryMode`** – *Passthrough* for a raw load, *Recover* for
      auto‑fix, or *Throw* to catch problems early.'
  - name: '**Load the document** – give the path and the options you just built.'
    text: '**Load the document** – give the path and the options you just built.'
  - name: '**Validate** – check that the document tree isn’t empty, optionally save
      a repaired copy.'
    text: '**Validate** – check that the document tree isn’t empty, optionally save
      a repaired copy.'
  type: HowTo
tags:
- C#
- Aspose.Words
- Document Recovery
title: Άνοιγμα κατεστραμμένου αρχείου Word σε C# – Πλήρης οδηγός
url: /el/net/programming-with-loadoptions/open-corrupted-word-file-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Άνοιγμα κατεστραμμένου αρχείου Word σε C# – Πλήρης Οδηγός

Κάποτε χρειάστηκε να **open corrupted word file** σε ένα .NET project και αναρωτηθήκατε αν το αρχείο είναι ακατάσβεστο; Δεν είστε οι πρώτοι—η καταστροφή εγγράφων εμφανίζεται πιο συχνά απ' ό,τι νομίζετε, ειδικά όταν τα αρχεία μεταφέρονται μέσω ασταθών δικτύων ή επεξεργάζονται από παλαιότερες εκδόσεις του Office.  

Τα καλά νέα; Με το Aspose.Words μπορείτε να **set recovery mode** ώστε να καθορίζετε ακριβώς πώς θα συμπεριφέρεται η βιβλιοθήκη, και ακόμη να **recover corrupted document** χωρίς να γράψετε έναν προσαρμοσμένο parser. Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα από τη ρύθμιση των επιλογών μέχρι την επαλήθευση ότι το αρχείο άνοιξε σωστά.

> **Τι θα αποκομίσετε**  
> • Ένα λειτουργικό snippet C# που ανοίγει οποιοδήποτε .docx, ακόμα και ένα κατεστραμμένο.  
> • Κατανόηση των τριών τιμών `RecoveryMode` και πότε να χρησιμοποιείτε καθεμία.  
> • Συμβουλές για διαχείριση εξαιρέσεων, έλεγχο του αποτελέσματος και προαιρετική αποθήκευση μιας καθαρής αντιγράφου.

## Πώς να ανοίξετε κατεστραμμένο αρχείο Word με Aspose.Words

Παρακάτω φαίνεται μια υψηλού επιπέδου εικόνα της ροής.  
![Diagram illustrating open corrupted word file process](/images/open-corrupted-word-file-flow.png){: .center alt="διάγραμμα ροής ανοίγματος κατεστραμμένου αρχείου Word"}

1. **Create `LoadOptions`** – αποφασίστε πόσο αυστηρός θα είναι ο φορτωτής.  
2. **Pick a `RecoveryMode`** – *Passthrough* για ακατέργαστη φόρτωση, *Recover* για αυτόματη διόρθωση, ή *Throw* για άμεσο εντοπισμό προβλημάτων.  
3. **Load the document** – δώστε τη διαδρομή και τις επιλογές που μόλις δημιουργήσατε.  
4. **Validate** – ελέγξτε ότι το δέντρο του εγγράφου δεν είναι κενό, προαιρετικά αποθηκεύστε ένα διορθωμένο αντίγραφο.

Ας εμβαθύνουμε σε κάθε κομμάτι.

## Κατανόηση των Recovery Modes

Το Aspose.Words ορίζει τρεις διαφορετικές συμπεριφορές:

| Λειτουργία | Τι κάνει | Πότε να το χρησιμοποιήσετε |
|------------|----------|----------------------------|
| `RecoveryMode.Recover` | Προσπαθεί να διορθώσει δομικά προβλήματα, ελλείποντα τμήματα ή κακοδιατυπωμένο XML. Αυτή είναι η **προεπιλογή** και λειτουργεί για τις περισσότερες μικρές καταστροφές. | Θέλετε μια προσπάθεια αποκατάστασης χωρίς χειροκίνητη παρέμβαση. |
| `RecoveryMode.Passthrough` | Φορτώνει το αρχείο **ακριβώς** όπως υπάρχει, ακόμη και αν περιέχει σπασμένα τμήματα. Δεν εφαρμόζονται αυτόματες διορθώσεις. | Χρειάζεστε να εξετάσετε το ακατέργαστο περιεχόμενο ή σκοπεύετε να εφαρμόσετε δική σας λογική αποκατάστασης αργότερα. |
| `RecoveryMode.Throw` | Αποκλείει αμέσως μια εξαίρεση εάν εντοπιστεί οποιοδήποτε πρόβλημα. | Προτιμάτε μια προσέγγιση fail‑fast για να απορρίψετε άμεσα τα κατεστραμμένα αρχεία. |

Η σωστή επιλογή λειτουργίας αποτελεί την ουσία του **set recovery mode** σωστά. Οι περισσότεροι προγραμματιστές ξεκινούν με `Recover`, αλλά αν αντιμετωπίζετε ένα επίμονο αρχείο, το `Passthrough` μπορεί να σας δώσει ορατότητα στο τι πήγε στραβά.

## Βήμα‑βήμα: Set Recovery Mode

Παρακάτω είναι το πρώτο μπλοκ κώδικα που θα επικολλήσετε σε μια νέα εφαρμογή console ή σε οποιοδήποτε έργο C# που ήδη αναφέρει το `Aspose.Words`.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

// Step 1: Create LoadOptions and choose a recovery behavior
LoadOptions loadOptions = new LoadOptions
{
    // Choose the desired recovery behavior:
    //   RecoveryMode.Recover      – attempt to fix the file (default)
    //   RecoveryMode.Passthrough – load the file exactly as it is
    //   RecoveryMode.Throw       – throw an exception if the file is damaged
    RecoveryMode = RecoveryMode.Passthrough   // <-- we are explicitly setting it
};
```

**Γιατί είναι σημαντικό:** Αναθέτοντας ρητά το `RecoveryMode.Passthrough`, λέμε στο Aspose.Words **set recovery mode** σε μια μη‑προεπιλεγμένη τιμή. Αυτό αφαιρεί τυχόν εικασίες και κάνει την πρόθεση ξεκάθαρη για τους μελλοντικούς συντηρητές.

> **Pro tip:** Αν χρειαστεί ποτέ να επιστρέψετε στην αυτόματη διόρθωση, απλώς αλλάξτε το enum σε `RecoveryMode.Recover` και ξανατρέξτε—δεν απαιτούνται άλλες αλλαγές κώδικα.

## Ασφαλής Φόρτωση του Εγγράφου

Τώρα που οι επιλογές είναι έτοιμες, το επόμενο βήμα είναι να **open corrupted word file**. Το παρακάτω snippet δείχνει τη διαδικασία φόρτωσης και περιλαμβάνει έναν μικρό έλεγχο λογικής.

```csharp
// Step 2: Load the possibly‑corrupted document using the configured options
try
{
    // Replace the path with the location of your damaged DOCX
    Document doc = new Document(@"C:\Temp\Corrupted.docx", loadOptions);

    // Quick validation – make sure the document contains at least one section
    if (doc.Sections.Count == 0)
    {
        Console.WriteLine("The document appears empty after loading. It may be severely corrupted.");
    }
    else
    {
        Console.WriteLine($"Successfully opened the file. Sections found: {doc.Sections.Count}");
    }
}
catch (Exception ex)
{
    // If you used RecoveryMode.Throw, you'll land here for any problem.
    Console.WriteLine($"Failed to open the file: {ex.Message}");
}
```

**Επεξήγηση:**  
* Το μπλοκ `try/catch` μας προστατεύει από τη λειτουργία `Throw`, αλλά είναι επίσης ένα δίχτυ ασφαλείας για απρόσμενα σφάλματα I/O.  
* Μετά τη φόρτωση, εξετάζουμε το `doc.Sections.Count`. Ένας αριθμός μηδέν είναι ένδειξη ότι το αρχείο δεν ανέκτησε κάποιο ουσιώδες περιεχόμενο—τέλειο για να επιβεβαιώσουμε αν η **recover corrupted document** επέτυχε.

## Διαχείριση Εξαιρέσεων και Επαλήθευση Ανάκτησης

Ακόμη και με `Passthrough`, η βιβλιοθήκη μπορεί να ρίξει εξαίρεση αν το υποκείμενο πακέτο ZIP είναι μη αναγνώσιμο. Δείτε πώς να διακρίνετε ένα *recoverable* πρόβλημα από ένα *fatal*:

```csharp
catch (CorruptedFileException cfe)
{
    // This exception means the file's internal structure is broken.
    Console.WriteLine("CorruptedFileException caught – the file cannot be read at all.");
}
catch (Exception ex)
{
    // Any other exception (e.g., FileNotFound, UnauthorizedAccess)
    Console.WriteLine($"General error: {ex.GetType().Name} – {ex.Message}");
}
```

Αν δείτε μια `CorruptedFileException`, ίσως θελήσετε να επιστρέψετε σε διαφορετική στρατηγική ανάκτησης, όπως:

* Δοκιμή `RecoveryMode.Recover` αντί για `Passthrough`.  
* Χρήση εργαλείου τρίτου μέρους για επισκευή ZIP πριν τροφοδοτήσετε το αρχείο στο Aspose.Words.  
* Ζήτηση από τον χρήστη να ανεβάσει ένα φρέσκο αντίγραφο.

## Bonus: Αποθήκευση Διορθωμένου Εγγράφου

Μόλις **recover corrupted document** το περιεχόμενο, συχνά θέλετε να αποθηκεύσετε μια καθαρή έκδοση. Ο παρακάτω κώδικας γράφει το διορθωμένο αρχείο σε νέα τοποθεσία:

```csharp
// Assuming 'doc' was loaded successfully
string outputPath = @"C:\Temp\Repaired.docx";

doc.Save(outputPath, SaveFormat.Docx);
Console.WriteLine($"Repaired document saved to: {outputPath}");
```

Η αποθήκευση λειτουργεί επίσης ως έμμεσο βήμα επαλήθευσης—αν το `doc.Save` ρίξει εξαίρεση, κάτι ακόμα δεν είναι εντάξει με το εσωτερικό δέντρο κόμβων.

## Συμβουλές για Σενάρια Recover Corrupted Document

| Κατάσταση | Προτεινόμενη Ενέργεια |
|-----------|----------------------|
| Μικρό τυπογραφικό σφάλμα XML (π.χ., λείπει κλείσιμο ετικέτας) | Διατηρήστε `RecoveryMode.Recover`; το Aspose.Words θα το διορθώσει αυτόματα. |
| Πλήρως σπασμένο αρχείο ZIP | Χρησιμοποιήστε εξωτερική επισκευή ZIP, μετά φορτώστε με `Passthrough`. |
| Μικτή λειτουργία (κάποια τμήματα εντάξουν, άλλα σπασμένα) | Φορτώστε με `Passthrough`, εξετάστε τα προβληματικά nodes, και στη συνέχεια αφαιρέστε ή αντικαταστήστε τα χειροκίνητα. |
| Συχνή καταστροφή από συγκεκριμένη πηγή | Αυτοματοποιήστε έναν προ‑έλεγχο που τρέχει `RecoveryMode.Recover` και καταγράφει τυχόν `CorruptedFileException`. |

Θυμηθείτε, το **set recovery mode** δεν είναι μαγικό ραβδί—η κατανόηση της φύσης της καταστροφής σας βοηθά να επιλέξετε τη σωστή στρατηγική.

## Πλήρες Παράδειγμα Εφαρμογής

Συνδυάζοντας όλα, εδώ είναι μια αυτόνομη εφαρμογή console που μπορείτε να επικολλήσετε στο `Program.cs` και να τρέξετε αμέσως (μετά την προσθήκη του πακέτου NuGet Aspose.Words).

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

namespace OpenCorruptedWordFileDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure load options – we explicitly set the recovery mode.
            LoadOptions loadOptions = new LoadOptions
            {
                RecoveryMode = RecoveryMode.Passthrough // change to Recover if you prefer auto‑fix
            };

            // 2️⃣ Attempt to load the possibly damaged DOCX.
            string sourcePath = @"C:\Temp\Corrupted.docx";
            Document doc = null;

            try
            {
                doc = new Document(sourcePath, loadOptions);
                Console.WriteLine($"File loaded. Sections: {doc.Sections.Count}");
            }
            catch (CorruptedFileException)
            {
                Console.WriteLine("The file is too damaged to be opened even in Passthrough mode.");
                return;
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Unexpected error: {ex.Message}");
                return;
            }

            // 3️⃣ Simple verification – ensure we have at least one paragraph.
            if (doc.GetChildNodes(NodeType.Paragraph, true).Count == 0)
            {
                Console.WriteLine("No paragraphs were recovered – the document may be empty.");
            }
            else
            {
                Console.WriteLine("Paragraphs recovered – the document appears usable.");
            }

            // 4️⃣ Optionally save a clean copy.
            string cleanPath = @"C:\Temp\Repaired.docx";
            doc.Save(cleanPath, SaveFormat.Docx);
            Console.WriteLine($"Clean copy saved to: {cleanPath}");
        }
    }
}
```

**Αναμενόμενη έξοδος (όταν το αρχείο μπορεί να ανοιχθεί):**



## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε επιπλέον δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [πώς να ανακτήσετε docx – ορίστε τη λειτουργία ανάκτησης & ανοίξτε κατεστραμμένα αρχεία Word](/words/english/net/programming-with-loadoptions/how-to-recover-docx-set-recovery-mode-open-corrupted-word-fi/)
- [Recover Damaged Word File – Complete Guide to Open Corrupted DOCX & Get Page](/words/english/net/programming-with-loadoptions/recover-damaged-word-file-complete-guide-to-open-corrupted-d/)
- [Recover Word Document with Aspose.Words in C#](/words/english/net/programming-with-loadoptions/recover-word-document-with-aspose-words-in-c/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}