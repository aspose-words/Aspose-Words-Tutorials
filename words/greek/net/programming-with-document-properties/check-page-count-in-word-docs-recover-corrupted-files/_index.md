---
category: general
date: 2026-03-30
description: Ελέγξτε τον αριθμό σελίδων σε έγγραφα Word ενώ μαθαίνετε να επαναφέρετε
  κατεστραμμένο αρχείο Word και να εντοπίζετε κατεστραμμένο αρχείο Word χρησιμοποιώντας
  το Aspose.Words.
draft: false
keywords:
- check page count
- recover corrupted word file
- detect corrupted word file
- Aspose.Words
- C# document loading
language: el
og_description: Ελέγξτε τον αριθμό σελίδων σε έγγραφα Word και μάθετε πώς να επαναφέρετε
  ένα κατεστραμμένο αρχείο Word με το Aspose.Words. Βήμα‑βήμα οδηγός C#.
og_title: Έλεγχος αριθμού σελίδων σε έγγραφα Word – Πλήρης οδηγός
tags:
- Aspose.Words
- C#
- document processing
title: Έλεγχος αριθμού σελίδων σε έγγραφα Word – Ανάκτηση κατεστραμμένων αρχείων
url: /el/net/programming-with-document-properties/check-page-count-in-word-docs-recover-corrupted-files/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Έλεγχος Αριθμού Σελίδων σε Έγγραφα Word – Ανάκτηση Κατεστραμμένων Αρχείων

Ποτέ χρειάστηκε να **ελέγξετε τον αριθμό σελίδων** σε ένα έγγραφο Word αλλά δεν ήσασταν σίγουροι αν το αρχείο ήταν ακόμη υγιές; Δεν είστε μόνοι. Σε πολλές αλυσίδες αυτοματισμού το πρώτο που κάνουμε είναι να επαληθεύσουμε το μήκος του εγγράφου, και ταυτόχρονα συχνά πρέπει να **ανιχνεύσουμε προβλήματα κατεστραμμένου αρχείου word** πριν ολόκληρη η διαδικασία καταρρεύσει.  

Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα από ένα πλήρες, εκτελέσιμο παράδειγμα C# που δείχνει πώς να **ελέγξετε τον αριθμό σελίδων**, ενώ ταυτόχρονα παρουσιάζει τον καλύτερο τρόπο **ανάκτησης κατεστραμμένου αρχείου word** χρησιμοποιώντας Aspose.Words LoadOptions. Στο τέλος θα γνωρίζετε ακριβώς γιατί κάθε ρύθμιση έχει σημασία, πώς να χειριστείτε ακραίες περιπτώσεις και τι να ψάχνετε όταν ένα αρχείο αρνείται να ανοίξει.

---

## Τι Θα Μάθετε

- Πώς να διαμορφώσετε το `LoadOptions` για **ανίχνευση προβλημάτων κατεστραμμένου αρχείου word**.  
- Τη διαφορά μεταξύ `RecoveryMode.Strict` και `RecoveryMode.Auto`.  
- Ένα αξιόπιστο μοτίβο για τη φόρτωση ενός εγγράφου και τον ασφαλή **έλεγχο αριθμού σελίδων**.  
- Συνηθισμένες παγίδες (απουσία αρχείου, σφάλματα δικαιωμάτων, μη αναμενόμενη μορφή) και πώς να τις αποφύγετε.  
- Ένα πλήρες, έτοιμο για αντιγραφή‑επικόλληση δείγμα κώδικα που μπορείτε να τρέξετε σήμερα.

> **Προαπαιτούμενα**: .NET 6+ (ή .NET Framework 4.7+), Visual Studio 2022 (ή οποιοδήποτε IDE C#), και άδεια Aspose.Words for .NET (η δωρεάν δοκιμή λειτουργεί για αυτήν την επίδειξη).

---

## Βήμα 1 – Εγκατάσταση Aspose.Words

Πρώτα απ’ όλα, χρειάζεστε το πακέτο NuGet Aspose.Words. Ανοίξτε ένα τερματικό στον φάκελο του έργου σας και εκτελέστε:

```bash
dotnet add package Aspose.Words
```

Αυτή η εντολή κατεβάζει όλα όσα χρειάζεστε — χωρίς επιπλέον αναζήτηση DLL. Αν χρησιμοποιείτε Visual Studio, μπορείτε επίσης να εγκαταστήσετε μέσω του UI του NuGet Package Manager.

---

## Βήμα 2 – Ρύθμιση LoadOptions για **Ανίχνευση Κατεστραμμένου Αρχείου Word**

Η καρδιά της λύσης είναι η κλάση `LoadOptions`. Σας επιτρέπει να πείτε στην Aspose.Words πόσο αυστηρή πρέπει να είναι όταν συναντά ένα προβληματικό αρχείο.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

// Choose a recovery strategy.
// Strict → throws an exception the moment corruption is spotted.
// Auto   → tries to salvage what it can and keeps loading.
var loadOptions = new LoadOptions
{
    RecoveryMode = RecoveryMode.Strict   // <‑‑ change to Auto if you prefer auto‑recovery
};
```

**Γιατί είναι σημαντικό**: Αν αφήσετε τη βιβλιοθήκη να μαντεύει σιωπηλά, μπορεί να καταλήξετε με ένα έγγραφο που λείπουν σελίδες — καθιστώντας οποιαδήποτε επόμενη λειτουργία **ελέγχου αριθμού σελίδων** αναξιόπιστη. Η χρήση του `Strict` σας αναγκάζει να αντιμετωπίσετε το πρόβλημα εκ των προτέρων, κάτι που είναι πιο ασφαλές για παραγωγικές αλυσίδες.

---

## Βήμα 3 – Φόρτωση του Εγγράφου και **Έλεγχος Αριθμού Σελίδων**

Τώρα ανοίγουμε πραγματικά το αρχείο. Ο κατασκευαστής `Document` δέχεται τη διαδρομή και το `LoadOptions` που μόλις διαμορφώσαμε.

```csharp
try
{
    // Replace the placeholder with the real path to your .docx file.
    const string filePath = @"C:\Docs\maybeCorrupt.docx";

    // Load the document using the strict recovery mode we set above.
    Document doc = new Document(filePath, loadOptions);

    // If we reach this line, the file is considered healthy enough.
    Console.WriteLine($"✅ Document loaded successfully. Page count: {doc.PageCount}");

    // You can now safely use the page count for any downstream logic.
    // Example: abort processing if the document is unexpectedly short.
    if (doc.PageCount < 2)
    {
        Console.WriteLine("⚠️ Document seems too short – double‑check the source.");
    }
}
catch (Exception ex) when (ex is FileCorruptedException || ex is LoadOptionsException)
{
    // This block runs only when Strict mode catches corruption.
    Console.WriteLine($"❌ Failed to load document: {ex.Message}");
    // Optional: switch to Auto mode on the fly, then retry.
    loadOptions.RecoveryMode = RecoveryMode.Auto;
    Console.WriteLine("🔄 Retrying with Auto recovery mode…");
    // Recursive retry is omitted for brevity—see Step 5 for a reusable method.
}
```

**Αυτό που βλέπετε**:

- Το μοτίβο `try/catch` σας δίνει έναν καθαρό τρόπο **ανίχνευσης κατεστραμμένου αρχείου word**.  
- Η ιδιότητα `doc.PageCount` είναι αυτή που πραγματικά **ελέγχει τον αριθμό σελίδων**.  
- Η συνθήκη μετά το `Console.WriteLine` δείχνει ένα ρεαλιστικό σενάριο όπου μπορεί να χρειαστεί να τερματίσετε τη διαδικασία αν το έγγραφο είναι απροσδόκητα σύντομο.

---

## Βήμα 4 – Χειρισμός Ακραίων Περιπτώσεων με Ευγένεια

Ο κώδικας σε πραγματικές συνθήκες σπάνια τρέχει σε απομόνωση. Παρακάτω τρία κοινά σενάρια “τι‑εάν” και πώς να τα αντιμετωπίσετε.

### 4.1 Αρχείο Δεν Βρέθηκε

```csharp
if (!File.Exists(filePath))
{
    Console.WriteLine($"❗ File not found: {filePath}");
    return; // Bail out early – nothing to load.
}
```

### 4.2 Ανεπαρκή Δικαιώματα

```csharp
try
{
    // Attempt to open with read‑only sharing.
    using var stream = new FileStream(filePath, FileMode.Open, FileAccess.Read, FileShare.Read);
    Document doc = new Document(stream, loadOptions);
    Console.WriteLine($"📄 Page count: {doc.PageCount}");
}
catch (UnauthorizedAccessException)
{
    Console.WriteLine("🔐 You don’t have permission to read this file.");
}
```

### 4.3 Εφεδρική Αυτόματη Ανάκτηση

Αν θεωρείτε αποδεκτή η σιωπηλή αποκατάσταση ενός αρχείου, τυλίξτε την αυτόματη ανάκτηση σε μια βοηθητική μέθοδο:

```csharp
static Document LoadWithFallback(string path)
{
    var options = new LoadOptions { RecoveryMode = RecoveryMode.Strict };
    try
    {
        return new Document(path, options);
    }
    catch
    {
        // Switch to Auto and try again.
        options.RecoveryMode = RecoveryMode.Auto;
        return new Document(path, options);
    }
}
```

Τώρα έχετε μια γραμμή `Document doc = LoadWithFallback(filePath);` που πάντα επιστρέφει ένα αντικείμενο `Document` — είτε άψογο είτε αποκατεστημένο με τη μέγιστη δυνατή προσπάθεια.

---

## Βήμα 5 – Πλήρες Παράδειγμα Εργασίας (Έτοιμο για Αντιγραφή‑Επικόλληση)

Παρακάτω βρίσκεται ολόκληρο το πρόγραμμα, έτοιμο να τοποθετηθεί σε ένα έργο console app. Συμπεριλαμβάνει όλες τις συμβουλές από τα προηγούμενα βήματα.

```csharp
// ------------------------------------------------------------
// Check Page Count in Word Docs – Recover Corrupted Files
// ------------------------------------------------------------
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        const string filePath = @"C:\Docs\maybeCorrupt.docx";

        // 1️⃣ Verify the file exists.
        if (!File.Exists(filePath))
        {
            Console.WriteLine($"❗ File not found: {filePath}");
            return;
        }

        // 2️⃣ Try loading with strict recovery mode.
        Document doc = LoadDocument(filePath, RecoveryMode.Strict);

        // 3️⃣ If we have a document, we can safely check page count.
        Console.WriteLine($"✅ Document loaded. Page count: {doc.PageCount}");

        // 4️⃣ Example business rule – abort if too few pages.
        if (doc.PageCount < 2)
        {
            Console.WriteLine("⚠️ Document seems too short – investigate the source file.");
        }
    }

    /// <summary>
    /// Loads a Word document using the specified recovery mode.
    /// Falls back to Auto mode if Strict fails.
    /// </summary>
    static Document LoadDocument(string path, RecoveryMode mode)
    {
        var options = new LoadOptions { RecoveryMode = mode };

        try
        {
            return new Document(path, options);
        }
        catch (Exception ex) when (ex is FileCorruptedException || ex is LoadOptionsException)
        {
            Console.WriteLine($"❌ Strict mode failed: {ex.Message}");
            Console.WriteLine("🔄 Switching to Auto recovery mode…");
            options.RecoveryMode = RecoveryMode.Auto;
            return new Document(path, options); // Auto will attempt to salvage.
        }
    }
}
```

**Αναμενόμενη έξοδος (υγιές αρχείο)**:

```
✅ Document loaded. Page count: 12
```

**Αναμενόμενη έξοδος (κατεστραμμένο αρχείο, αυστηρή λειτουργία)**:

```
❌ Strict mode failed: The file is corrupted and cannot be opened.
🔄 Switching to Auto recovery mode…
✅ Document loaded. Page count: 8   // Might be less than original.
```

---

## Βήμα 6 – Pro Συμβουλές & Συνηθισμένες Παγίδες

- **Pro tip:** Πάντα να καταγράφετε το `RecoveryMode` που χρησιμοποιήσατε. Όταν αργότερα ελέγχετε μια παρτίδα, θα ξέρετε ποια αρχεία ανακτήθηκαν αυτόματα.  
- **Προσοχή σε:** Έγγραφα που περιέχουν ενσωματωμένα αντικείμενα (γράφημα, SmartArt). Η αυτόματη λειτουργία μπορεί να τα αφαιρέσει, επηρεάζοντας τη διάταξη των σελίδων και, κατά συνέπεια, το αποτέλεσμα του **ελέγχου αριθμού σελίδων**.  
- **Σημείωση απόδοσης:** Το `RecoveryMode.Auto` είναι ελαφρώς πιο αργό επειδή η Aspose.Words εκτελεί επιπλέον βήματα επικύρωσης. Αν επεξεργάζεστε χιλιάδες αρχεία, προτιμήστε το `Strict` και χρησιμοποιήστε το `Auto` μόνο σε ατομική βάση.  
- **Έλεγχος έκδοσης:** Ο παραπάνω κώδικας λειτουργεί με Aspose.Words 22.12 και νεότερες. Παλαιότερες εκδόσεις είχαν διαφορετικό όνομα enum (`LoadOptions.RecoveryMode` εισήχθη στην 20.10).

---

## Συμπέρασμα

Τώρα διαθέτετε ένα σταθερό, έτοιμο για παραγωγή μοτίβο για **έλεγχο αριθμού σελίδων** σε έγγραφα Word, ενώ ταυτόχρονα έχετε μάθει πώς να **ανακτήσετε κατεστραμμένο αρχείο word** και να **ανιχνεύσετε καταστροφές** χρησιμοποιώντας Aspose.Words. Τα κύρια σημεία είναι:

1. Διαμορφώστε το `LoadOptions` με το κατάλληλο `RecoveryMode`.  
2. Τυλίξτε τη φόρτωση σε `try/catch` για έγκαιρη ανίχνευση καταστροφής.  
3. Χρησιμοποιήστε την ιδιότητα `PageCount` ως την τελική πηγή για τον αριθμό σελίδων.  
4. Υλοποιήστε ευγενικές εναλλακτικές (αυτόματη ανάκτηση, διαχείριση δικαιωμάτων, έλεγχος ύπαρξης αρχείου).

Από εδώ μπορείτε να εξερευνήσετε:

- Εξαγωγή κειμένου από κάθε σελίδα (`doc.GetText()` με περιοχές σελίδων).  
- Μετατροπή του εγγράφου σε PDF μετά την επιβεβαίωση του αριθμού σελίδων.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}