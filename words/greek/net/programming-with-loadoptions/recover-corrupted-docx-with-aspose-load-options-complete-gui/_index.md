---
category: general
date: 2026-01-06
description: Μάθετε πώς να ανακτήσετε κατεστραμμένα αρχεία docx χρησιμοποιώντας τις
  Επιλογές Φόρτωσης της Aspose. Αυτό το σεμινάριο σας δείχνει πώς να ορίσετε τη λειτουργία
  ανάκτησης και να διαχειριστείτε αποτελεσματικά τα κατεστραμμένα τμήματα.
draft: false
keywords:
- recover corrupted docx
- set recovery mode
- aspose load options
- Aspose.Words recovery
- handling corrupted docx
language: el
og_description: Ανακτήστε κατεστραμμένα αρχεία docx χωρίς κόπο. Ανακαλύψτε πώς να
  ορίσετε τη λειτουργία ανάκτησης με τις επιλογές φόρτωσης Aspose και να διατηρήσετε
  τα έγγραφά σας χρήσιμα.
og_title: Ανάκτηση κατεστραμμένου docx – Βήμα‑βήμα επιλογές φόρτωσης Aspose
tags:
- Aspose.Words
- C#
- Document Processing
title: Ανάκτηση κατεστραμμένου docx με τις επιλογές φόρτωσης της Aspose – Πλήρης οδηγός
url: /el/net/programming-with-loadoptions/recover-corrupted-docx-with-aspose-load-options-complete-gui/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# ανάκτηση κατεστραμμένου docx – πλήρης οδηγός με χρήση Aspose Load Options

Έχετε αναρωτηθεί ποτέ πώς να **ανακτήσετε κατεστραμμένα αρχεία docx** χωρίς να χάσετε τα καλά τμήματα; Δεν είστε οι μόνοι. Η κατεστραμμένη κατάσταση μπορεί να προκύψει από κακή αποθήκευση, σφάλμα δικτύου ή απροσδόκητο τερματισμό, αφήνοντάς σας με ένα έγγραφο που αρνείται να ανοίξει.  

Τα καλά νέα; Το Aspose.Words σας παρέχει έναν ενσωματωμένο τρόπο να πείτε στον φορτωτή τι να κάνει με τα σπασμένα τμήματα—απλώς ρυθμίζοντας την ιδιότητα **set recovery mode** σε ένα αντικείμενο `LoadOptions`. Σε αυτόν τον οδηγό θα περάσουμε από όλη τη διαδικασία, από τη διαμόρφωση των επιλογών μέχρι την επαλήθευση ότι το έγγραφο είναι ξανά χρησιμοποιήσιμο.

Θα προσθέσουμε επίσης μερικές επιπλέον συμβουλές, όπως πώς να καταγράψετε ποια τμήματα επισκευάστηκαν και τι να κάνετε όταν χρειάζεται να παραλείψετε εντελώς τα κατεστραμμένα κομμάτια. Στο τέλος, θα έχετε ένα αξιόπιστο μοτίβο για τη διαχείριση οποιουδήποτε ασταθούς DOCX που διασχίζει τη βάση κώδικά σας.

## Τι Θα Μάθετε

- Τον σκοπό των **Aspose Load Options** κατά το άνοιγμα πιθανώς κατεστραμμένων αρχείων Word.  
- Πώς να **set recovery mode** σε `RecoverAll`, `SkipCorruptedParts` ή `ThrowException`.  
- Ένα πλήρες, εκτελέσιμο παράδειγμα C# που φορτώνει, επικυρώνει και αποθηκεύει ένα επισκευασμένο έγγραφο.  
- Διαχείριση edge‑case: έλεγχος του αποτελέσματος `LoadOptions.RecoveryMode`, καταγραφή και στρατηγικές fallback.  

Δεν απαιτείται προηγούμενη εμπειρία με το Aspose.Words—απλώς ένα λειτουργικό περιβάλλον .NET και βασική γνώση C#.

## Προαπαιτούμενα

- .NET 6.0 (ή νεότερο) SDK εγκατεστημένο.  
- Visual Studio 2022 (Community ή υψηλότερη) ή οποιοσδήποτε επεξεργαστής προτιμάτε.  
- Πακέτο NuGet **Aspose.Words for .NET** (`Install-Package Aspose.Words`).  
- Ένα αρχείο DOCX που υποπτεύεστε ότι είναι κατεστραμμένο (θα το ονομάσουμε `maybeCorrupt.docx`).  

Αν έχετε ήδη όλα αυτά, τέλεια—ας ξεκινήσουμε.

## Βήμα 1: Εγκατάσταση Aspose.Words και Προετοιμασία του Έργου

Πρώτα απ’ όλα. Ανοίξτε το τερματικό ή το Package Manager Console και προσθέστε τη βιβλιοθήκη:

```powershell
dotnet add package Aspose.Words
```

Ή, μέσα στον διαχειριστή NuGet του Visual Studio, αναζητήστε **Aspose.Words** και πατήστε *Install*. Αυτό θα προσθέσει το namespace `Aspose.Words` μαζί με όλες τις βοηθητικές κλάσεις που θα χρειαστούμε.

> **Pro tip:** Χρησιμοποιήστε την πιο πρόσφατη σταθερή έκδοση (από Ιαν 2026 είναι η 24.9) για να επωφεληθείτε από τους νεότερους αλγόριθμους ανάκτησης.

## Βήμα 2: Διαμόρφωση LoadOptions – **set recovery mode** σε RecoverAll

Τώρα δημιουργούμε μια παρουσία `LoadOptions` και λέμε στο Aspose πώς να συμπεριφερθεί όταν συναντήσει κακοδιατυπωμένο XML, ελλιπή τμήματα ή σπασμένες σχέσεις μέσα στο πακέτο DOCX.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

// Step 2: Define how corrupted parts should be treated
var loadOptions = new LoadOptions
{
    // Choose one of the three strategies:
    //   RecoverAll           – tries to fix everything it can.
    //   SkipCorruptedParts   – drops the broken pieces and keeps the rest.
    //   ThrowException       – aborts loading, useful for strict validation.
    RecoveryMode = RecoveryMode.RecoverAll
};
```

Γιατί `RecoverAll`; Επειδή προσπαθεί να ξαναχτίσει κάθε σπασμένο κομμάτι, παρέχοντάς σας το πιο πλήρες αποτέλεσμα. Αν εργάζεστε με τεράστια αρχεία όπου η ταχύτητα έχει προτεραιότητα έναντι της τελειότητας, το `SkipCorruptedParts` μπορεί να είναι πιο κατάλληλο. Και αν χρειάζεστε άμεσο τερματισμό για έλεγχο, το `ThrowException` θα εμφανίσει το ακριβές πρόβλημα.

## Βήμα 3: Φόρτωση του Πιθανώς Κατεστραμμένου Εγγράφου

Με τις επιλογές μας έτοιμες, προσπαθούμε τώρα να ανοίξουμε το αρχείο. Αν το έγγραφο είναι πραγματικά ακατάλληλο για αποκατάσταση, το Aspose θα σας δώσει ακόμη ένα αντικείμενο `Document`—αν και κάποιο περιεχόμενο μπορεί να λείπει.

```csharp
// Step 3: Load the DOCX using the configured LoadOptions
string inputPath = @"C:\Docs\maybeCorrupt.docx";

Document doc;
try
{
    doc = new Document(inputPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    Console.Error.WriteLine($"Failed to load document: {ex.Message}");
    // If you used ThrowException, you might want to fallback here.
    return;
}
```

Παρατηρήστε το `try/catch`. Ακόμη και με `RecoverAll`, απρόσμενα σφάλματα μορφής zip μπορούν να εξαπλωθούν. Η ευγενική διαχείρισή τους αποτρέπει την κατάρρευση της υπηρεσίας σας.

## Βήμα 4: Επαλήθευση του Τις Έχει Ανακτηθεί (Προαιρετικό αλλά Συνιστώμενο)

Το Aspose.Words δεν εκθέτει άμεση “αναφορά ανάκτησης”, αλλά μπορείτε να εξετάσετε το έγγραφο για κοινά σημάδια απώλειας—όπως ελλιπή ενότητες, κενές παραγράφους ή σπασμένες εικόνες.

```csharp
// Simple sanity check: count sections and paragraphs
int sectionCount = doc.Sections.Count;
int paragraphCount = doc.GetChildNodes(NodeType.Paragraph, true).Count;

Console.WriteLine($"Sections: {sectionCount}, Paragraphs: {paragraphCount}");

// Look for empty sections that might indicate dropped content
foreach (Section sec in doc.Sections)
{
    if (!sec.Body.HasChildNodes)
        Console.WriteLine($"Warning: Section {sec.Index} appears empty after recovery.");
}
```

Αν παρατηρήσετε πολλές κενές ενότητες, μπορείτε να αποφασίσετε να καταγράψετε το αρχείο για χειροκίνητη ανασκόπηση ή να δοκιμάσετε διαφορετική λειτουργία ανάκτησης.

## Βήμα 5: Αποθήκευση του Επισκευασμένου Εγγράφου

Αν οι έλεγχοι υγείας περάσουν, γράψτε το διορθωμένο αρχείο πίσω στο δίσκο. Μπορείτε να κρατήσετε το αρχικό όνομα με ένα επίθημα ή να το αντικαταστήσετε—όπως προτιμάτε.

```csharp
// Step 5: Persist the recovered document
string outputPath = @"C:\Docs\maybeCorrupt_recovered.docx";

doc.Save(outputPath, SaveFormat.Docx);
Console.WriteLine($"Recovered document saved to: {outputPath}");
```

Όταν ανοίξετε το `maybeCorrupt_recovered.docx` στο Word, θα πρέπει να δείτε το μεγαλύτερο μέρος του αρχικού περιεχομένου, με τυχόν ακατάλληλα τμήματα είτε να έχουν αφαιρεθεί είτε να έχουν αντικατασταθεί από placeholders.

## Βήμα 6: Προχωρημένα Σενάρια – Αλλαγή Λειτουργίας Ανάκτησης Δυναμικά

Μερικές φορές θέλετε πρώτα να δοκιμάσετε μια πιο ήπια προσέγγιση, και μετά να περάσετε σε πιο αυστηρή αν το αποτέλεσμα δεν είναι ικανοποιητικό. Ακολουθεί ένα σύντομο μοτίβο που προσπαθεί `RecoverAll`, έπειτα `SkipCorruptedParts` ως εφεδρική επιλογή:

```csharp
Document TryRecover(string path)
{
    var attempts = new[]
    {
        RecoveryMode.RecoverAll,
        RecoveryMode.SkipCorruptedParts
    };

    foreach (var mode in attempts)
    {
        var opts = new LoadOptions { RecoveryMode = mode };
        try
        {
            var candidate = new Document(path, opts);
            Console.WriteLine($"Loaded with {mode}");
            return candidate; // success!
        }
        catch
        {
            Console.WriteLine($"Failed with {mode}, trying next mode...");
        }
    }

    throw new InvalidOperationException("All recovery attempts failed.");
}

// Usage
var recoveredDoc = TryRecover(inputPath);
```

Αυτό το snippet δείχνει **set recovery mode** εν κινήσει, δίνοντάς σας λεπτομερή έλεγχο χωρίς να χρειάζεται να διπλασιάζετε μεγάλα τμήματα κώδικα.

## Βήμα 7: Καταγραφή και Παρακολούθηση (Συμβουλή Έτοιμη για Παραγωγή)

Σε μια πραγματική υπηρεσία θα θέλετε να καταγράψετε ποια αρχεία χρειάστηκαν ανάκτηση και ποια λειτουργία πέτυχε. Ένα ελαφρύ JSON log λειτουργεί καλά:

```csharp
var logEntry = new
{
    File = Path.GetFileName(inputPath),
    RecoveryMode = loadOptions.RecoveryMode.ToString(),
    Timestamp = DateTime.UtcNow,
    Sections = doc.Sections.Count,
    Paragraphs = doc.GetChildNodes(NodeType.Paragraph, true).Count
};

File.AppendAllText(@"C:\Logs\doc_recovery_log.json",
    JsonSerializer.Serialize(logEntry) + Environment.NewLine);
```

Αυτά τα δεδομένα σας επιτρέπουν να εντοπίζετε μοτίβα—ίσως ένα συγκεκριμένο σύστημα upstream καταστρέφει συνεχώς αρχεία, απαιτώντας πιο βαθιά διερεύνηση.

## Οπτική Σύνοψη

![recover corrupted docx process diagram](https://example.com/images/recover-docx-diagram.png "recover corrupted docx workflow")

*Image alt text:* *recover corrupted docx* – διάγραμμα που δείχνει τα βήματα φόρτωσης, επιλογής λειτουργίας ανάκτησης, επικύρωσης και αποθήκευσης.

## Πλήρες Παράδειγμα (Όλα Μαζί)

Παρακάτω βρίσκεται το ολοκληρωμένο πρόγραμμα που μπορείτε να αντιγράψετε‑επικολλήσετε σε μια console app με όνομα `DocxRecoveryDemo`. Συγκομποιείται και εκτελείται ακριβώς όπως είναι, εφόσον το πακέτο NuGet είναι εγκατεστημένο.

```csharp
using System;
using System.IO;
using System.Text.Json;
using Aspose.Words;
using Aspose.Words.LoadOptions;

namespace DocxRecoveryDemo
{
    class Program
    {
        static void Main()
        {
            string inputPath = @"C:\Docs\maybeCorrupt.docx";
            string outputPath = @"C:\Docs\maybeCorrupt_recovered.docx";

            // 1️⃣ Configure LoadOptions – set recovery mode
            var loadOptions = new LoadOptions
            {
                RecoveryMode = RecoveryMode.RecoverAll // try to fix everything
            };

            // 2️⃣ Load the document with error handling
            Document doc;
            try
            {
                doc = new Document(inputPath, loadOptions);
                Console.WriteLine("✅ Document loaded.");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"❌ Load failed: {ex.Message}");
                return;
            }

            // 3️⃣ Simple sanity check
            int sections = doc.Sections.Count;
            int paragraphs = doc.GetChildNodes(NodeType.Paragraph, true).Count;
            Console.WriteLine($"Sections: {sections}, Paragraphs: {paragraphs}");

            // 4️⃣ Save the repaired file
            doc.Save(outputPath, SaveFormat.Docx);
            Console.WriteLine($"📁 Recovered file saved to {outputPath}");

            // 5️⃣ Log the operation (optional)
            var log = new
            {
                File = Path.GetFileName(inputPath),
                RecoveryMode = loadOptions.RecoveryMode.ToString(),
                TimeUtc = DateTime.UtcNow,
                Sections = sections,
                Paragraphs = paragraphs
            };
            File.AppendAllText(@"C:\Logs\doc_recovery_log.json",
                JsonSerializer.Serialize(log) + Environment.NewLine);
        }
    }
}
```

### Αναμενόμενο Αποτέλεσμα

- Η κονσόλα εκτυπώνει μήνυμα επιτυχίας, τον αριθμό ενοτήτων/παραγράφων και τη διαδρομή του αποθηκευμένου αρχείου.  
- Το άνοιγμα του `maybeCorrupt_recovered.docx` στο Microsoft Word εμφανίζει το αρχικό περιεχόμενο, εκτός από τυχόν ακατάλληλα τμήματα.  
- Μια γραμμή JSON προστίθεται στο `doc_recovery_log.json` για μεταγενέστερη ανάλυση.

## Συχνές Ερωτήσεις & Edge Cases

**Q: Τι γίνεται αν το αρχείο είναι .doc (δυαδικό) αντί για .docx;**  
A: Το `LoadOptions` λειτουργεί και για τις δύο μορφές. Απλώς αλλάξτε την επέκταση του αρχείου· οι ίδιες τιμές `RecoveryMode` ισχύουν.

**Q: Μπορώ να ανακτήσω ενσωματωμένες εικόνες που είναι κατεστραμμένες;**  
A: Το Aspose προσπαθεί να ξαναχτίσει τα ρεύματα εικόνας. Αν το υποκείμενο αρχείο εικόνας είναι μη αναγνώσιμο, θα παραλειφθεί. Μπορείτε να εντοπίσετε ελλείπουσες εικόνες επαναλαμβάνοντας `doc.GetChildNodes(NodeType.Shape, true)` και ελέγχοντας κάθε `Shape.HasImage`.

**Q: Είναι το `RecoverAll` ασφαλές για μεγάλα έγγραφα;**  
A: Είναι απαιτητικό σε μνήμη, επειδή το Aspose φορτώνει ολόκληρο το πακέτο. Για αρχεία πολλαπλών gigabytes, σκεφτείτε τη ροή με `LoadOptions.LoadFormat` ορισμένο σε `LoadFormat.Docx` και παρακολουθήστε τη χρήση μνήμης.

**Q: Πώς μπορώ να αναγκάσω το Aspose να ρίξει εξαίρεση σε οποιαδήποτε κατεστραμμένη κατάσταση;**  
A: Ορίστε `loadOptions.RecoveryMode = RecoveryMode.ThrowException;` – χρήσιμο για pipelines επικύρωσης όπου απαιτείται καθαρή κατάσταση πριν από περαιτέρω επεξεργασία.

## Συμπέρασμα

Μόλις διασχίσαμε έναν πλήρη, έτοιμο για παραγωγή τρόπο **ανάκτησης κατεστραμμένων docx** αρχείων χρησιμοποιώντας το Aspose.Words. Με τη ρύθμιση του **set

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}