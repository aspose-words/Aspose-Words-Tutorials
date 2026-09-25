---
category: general
date: 2026-01-11
description: Ανακτήστε κατεστραμμένο έγγραφο σε C# χρησιμοποιώντας το Aspose.Words.
  Μάθετε πώς να ορίσετε τη λειτουργία ανάκτησης, να φορτώσετε το docx με ανάκτηση
  και να προειδοποιήσετε τον χρήστη σε περίπτωση σφάλματος σε λίγα απλά βήματα.
draft: false
keywords:
- recover corrupted document
- set recovery mode
- load docx with recovery
- prompt user on error
language: el
og_description: Ανάκτηση κατεστραμμένου εγγράφου σε C# ορίζοντας λειτουργία ανάκτησης,
  φορτώνοντας ένα DOCX με ανάκτηση και προειδοποιώντας τον χρήστη σε περίπτωση σφάλματος.
  Πλήρης βήμα‑βήμα οδηγός.
og_title: Ανάκτηση Κατεστραμμένου Εγγράφου σε C# – Σύντομος Οδηγός
tags:
- Aspose.Words
- C#
- Document Recovery
title: Ανάκτηση Κατεστραμμένου Εγγράφου σε C# – Ορισμός Λειτουργίας Ανάκτησης & Προτροπή
  Χρήστη
url: /el/net/programming-with-loadoptions/recover-corrupted-document-in-c-set-recovery-mode-prompt-use/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ανάκτηση Κατεστραμμένου Εγγράφου σε C# – Πλήρης Οδηγός

Προσπαθήσατε ποτέ να ανοίξετε ένα DOCX που φαίνεται εντάξει στο Word αλλά πετάει εξαίρεση στον κώδικά σας; Πιθανότατα αντιμετωπίζετε ένα σενάριο **recover corrupted document**. Το καλό νέο είναι ότι το Aspose.Words σας δίνει λεπτομερή έλεγχο για το πώς να διαχειριστείτε αυτά τα ενοχλητικά αρχεία — είτε θέλετε να τα διορθώσετε σιωπηρά, να πετάξετε εξαίρεση, είτε να ρωτήσετε τον χρήστη τι να κάνει.

Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα από την εγκατάσταση της βιβλιοθήκης μέχρι την επιλογή της σωστής **set recovery mode** επιλογής, **load docx with recovery**, και τελικά **prompt user on error** όταν κάτι πάει στραβά. Χωρίς περιττές πληροφορίες, μόνο ένα πλήρες, εκτελέσιμο παράδειγμα που μπορείτε να ενσωματώσετε σε οποιοδήποτε .NET project.

> **Γρήγορη προεπισκόπηση:** Στο τέλος θα έχετε μια εφαρμογή console που φορτώνει ένα πιθανώς κατεστραμμένο `corrupt.docx`, καταγράφει τυχόν προειδοποιήσεις και ρωτάει τον χρήστη αν θέλει να συνεχίσει όταν η ανάκτηση αποτύχει.

---

## Τι Θα Χρειαστείτε

- **.NET 6.0** ή νεότερο (ο κώδικας λειτουργεί επίσης σε .NET Framework 4.6+).  
- **Aspose.Words for .NET** – εγκαταστήστε μέσω NuGet (`Install-Package Aspose.Words`).  
- Ένα **corrupt DOCX** αρχείο για δοκιμές (μπορείτε να το καταστρέψετε σκόπιμα ανοίγοντάς το σε hex editor ή αλλάζοντας την επέκταση).  
- Οποιοδήποτε IDE προτιμάτε — Visual Studio, Rider ή ακόμη και VS Code.

> *Pro tip:* Κρατήστε αντίγραφο ασφαλείας του αρχικού αρχείου. Η ανάκτηση μπορεί να ξαναγράψει μέρη του εγγράφου και δεν θέλετε να χάσετε τα καλά τμήματα.

---

## Βήμα 1 – Εγκατάσταση Aspose.Words και Προσθήκη Namespaces

Πρώτα απ' όλα. Κατεβάστε τη βιβλιοθήκη από το NuGet και φέρετε τα απαραίτητα namespaces στο scope.

```csharp
// Install via Package Manager Console:
// Install-Package Aspose.Words

using System;
using Aspose.Words;
using Aspose.Words.Loading;
```

Αυτό είναι ό,τι χρειάζεστε για το υπόλοιπο του οδηγού. Το namespace `Aspose.Words.Loading` περιέχει την κλάση `LoadOptions`, η οποία είναι το κλειδί για **set recovery mode**.

---

## Βήμα 2 – Επιλογή Λειτουργίας Ανάκτησης (Primary H2 with Keyword)

### Recover Corrupted Document – Ορισμός της Σωστής Λειτουργίας Ανάκτησης

Το Aspose.Words προσφέρει τρεις συμπεριφορές ανάκτησης:

| Mode | Τι Συμβαίνει | Πότε Να Χρησιμοποιηθεί |
|------|--------------|------------------------|
| **PromptUser** | Εμφανίζει διάλογο (ή μπορείτε να υλοποιήσετε το δικό σας prompt) και προσπαθεί να διορθώσει το αρχείο. | Ιδανικό για διαδραστικά εργαλεία όπου ο χρήστης μπορεί να αποφασίσει. |
| **Silent** | Προσπαθεί να διορθώσει αυτόματα, χωρίς UI. | Κατάλληλο για batch jobs ή services. |
| **ThrowException** | Διακόπτει την επεξεργασία και πετάει εξαίρεση. | Χρησιμοποιήστε το όταν θέλετε αυστηρή επικύρωση. |

Παρακάτω φαίνεται πώς **set recovery mode** σε `PromptUser`. Αν προτιμάτε σιωπηλή διαχείριση, απλώς αλλάξτε την τιμή του enum.

```csharp
// Step 2: Configure LoadOptions with the desired recovery mode
LoadOptions loadOptions = new LoadOptions
{
    // Choose one of: RecoveryMode.PromptUser, RecoveryMode.Silent, RecoveryMode.ThrowException
    RecoveryMode = RecoveryMode.PromptUser
};
```

> **Γιατί είναι σημαντικό:** Με το ρητό **set recovery mode**, λέτε στο Aspose.Words πόσο επιθετική πρέπει να είναι η διαδικασία. Η προεπιλογή είναι `PromptUser`, αλλά το να το δηλώσετε ρητά κάνει την πρόθεσή σας ξεκάθαρη — τόσο για μελλοντικούς συντηρητές όσο και για τις μηχανές αναζήτησης που «σαρώνουν» τον κώδικα.

---

## Βήμα 3 – Φόρτωση του DOCX με Ανάκτηση

Τώρα θα **load docx with recovery** χρησιμοποιώντας το `LoadOptions` που μόλις διαμορφώσαμε. Αν το αρχείο είναι κατεστραμμένο, το Aspose.Words είτε θα το επισκευάσει είτε θα εγείρει προειδοποίηση, ανάλογα με τη λειτουργία.

```csharp
// Step 3: Load the potentially corrupted DOCX
string filePath = @"C:\Temp\corrupt.docx"; // adjust to your environment
Document document;

try
{
    document = new Document(filePath, loadOptions);
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to load document: {ex.Message}");
    // If you used ThrowException mode, you'll end up here.
    return;
}
```

Ο κατασκευαστής `Document` κάνει το βαριά δουλειά. Σε λειτουργία **PromptUser**, θα δείτε ένα prompt στην κονσόλα (ή προσαρμοσμένο UI αν συνδέσετε στα events του `LoadOptions`) που ρωτάει αν θα συνεχίσει. Σε λειτουργία **Silent**, η μέθοδος απλώς προσπαθεί το καλύτερο δυνατό και προχωρά.

---

## Βήμα 4 – Έλεγχος Προειδοποιήσεων και Ερώτηση του Χρήστη

Το Aspose.Words καταγράφει τυχόν προβλήματα που εντοπίζει στη συλλογή `Warnings`. Ας τα διασχίσουμε και δώσουμε στον χρήστη την ευκαιρία να αποφασίσει τι θα κάνει στη συνέχεια.

```csharp
// Step 4: Examine any warnings generated during loading
if (document.Warnings.Count > 0)
{
    Console.WriteLine("The following warnings were detected while loading the document:");
    foreach (WarningInfo warning in document.Warnings)
    {
        Console.WriteLine($"- {warning.Source}: {warning.Description}");
    }

    // Simple prompt – you can replace this with a GUI dialog if you prefer
    Console.Write("Do you want to continue processing this document? (y/n): ");
    string response = Console.ReadLine()?.Trim().ToLowerInvariant();

    if (response != "y")
    {
        Console.WriteLine("Operation aborted by the user.");
        return;
    }
}
else
{
    Console.WriteLine("Document loaded without any warnings.");
}
```

Το παραπάνω απόσπασμα **prompt user on error** με τρόπο φιλικό στην κονσόλα. Αν δημιουργείτε εφαρμογή Windows Forms ή WPF, αντικαταστήστε το `Console.ReadLine` με ένα `MessageBox` ή προσαρμοσμένο διάλογο.

---

## Βήμα 5 – Εργασία με το Ανακτημένο Έγγραφο

Σε αυτό το σημείο το έγγραφο βρίσκεται στη μνήμη, διορθωμένο όσο καλύτερα μπορούσε το Aspose.Words. Μπορείτε τώρα να διαβάσετε το περιεχόμενό του, να αποθηκεύσετε ένα καθαρό αντίγραφο ή να κάνετε οποιαδήποτε επεξεργασία χρειάζεστε.

```csharp
// Example: Save a clean copy next to the original
string cleanPath = System.IO.Path.Combine(
    System.IO.Path.GetDirectoryName(filePath)!,
    "clean_copy.docx");

document.Save(cleanPath);
Console.WriteLine($"Clean copy saved to: {cleanPath}");
```

Η εκτέλεση του πλήρους προγράμματος σε ένα κατεστραμμένο αρχείο θα παράγει έξοδο κονσόλας παρόμοια με αυτήν:

```
The following warnings were detected while loading the document:
- Document: The file contains an unexpected end tag.
Do you want to continue processing this document? (y/n): y
Clean copy saved to: C:\Temp\clean_copy.docx
```

Αν το αρχείο ήταν πράγματι εντάξει, θα δείτε το μήνυμα “Document loaded without any warnings.” και το καθαρό αντίγραφο θα είναι ταυτόσημο με το πηγαίο.

---

## Πλήρες Παράδειγμα Εργασίας

Ακολουθεί ολόκληρο το πρόγραμμα σε ένα μέρος. Αντιγράψτε‑και‑επικολλήστε το σε ένα νέο console project και πατήστε **F5**.

```csharp
// RecoverCorruptedDocument.cs
using System;
using Aspose.Words;
using Aspose.Words.Loading;

class RecoverCorruptedDocument
{
    static void Main()
    {
        // 1️⃣ Configure recovery mode
        LoadOptions loadOptions = new LoadOptions
        {
            RecoveryMode = RecoveryMode.PromptUser // alternatives: Silent, ThrowException
        };

        // 2️⃣ Path to the possibly corrupted DOCX
        string filePath = @"C:\Temp\corrupt.docx";

        // 3️⃣ Attempt to load the document
        Document document;
        try
        {
            document = new Document(filePath, loadOptions);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
            return;
        }

        // 4️⃣ Show warnings and ask the user what to do
        if (document.Warnings.Count > 0)
        {
            Console.WriteLine("The following warnings were detected while loading the document:");
            foreach (WarningInfo warning in document.Warnings)
            {
                Console.WriteLine($"- {warning.Source}: {warning.Description}");
            }

            Console.Write("Do you want to continue processing this document? (y/n): ");
            string response = Console.ReadLine()?.Trim().ToLowerInvariant();

            if (response != "y")
            {
                Console.WriteLine("Operation aborted by the user.");
                return;
            }
        }
        else
        {
            Console.WriteLine("Document loaded without any warnings.");
        }

        // 5️⃣ Save a clean copy
        string cleanPath = System.IO.Path.Combine(
            System.IO.Path.GetDirectoryName(filePath)!,
            "clean_copy.docx");

        document.Save(cleanPath);
        Console.WriteLine($"Clean copy saved to: {cleanPath}");
    }
}
```

Τρέξτε το, καταστρέψτε ένα αρχείο δοκιμής, και παρακολουθήστε την ανάκτηση σε δράση. 🎉

---

## Edge Cases & Variations

| Scenario | Τι Να Αλλάξετε | Γιατί |
|----------|----------------|-------|
| **Batch processing** (χωρίς αλληλεπίδραση χρήστη) | Ορίστε `RecoveryMode = RecoveryMode.Silent` και αφαιρέστε το prompt της κονσόλας. | Κρατάει τη ροή εργασίας αυτόματα. |
| **Strict validation** (fail fast) | Χρησιμοποιήστε `RecoveryMode.ThrowException`. Τυλίξτε την κλήση φόρτωσης σε try/catch και καταγράψτε την εξαίρεση. | Εξασφαλίζει ότι δεν θα δουλέψετε με μερικά διορθωμένο αρχείο. |
| **Custom UI** (WinForms/WPF) | Εγγραφείτε στο `LoadOptions.LoadingProgress` ή χρησιμοποιήστε τα events του `Document.LoadOptions` για να εμφανίσετε διάλογο. | Παρέχει πιο πλούσια εμπειρία από την κονσόλα. |
| **Large documents** (περιορισμοί μνήμης) | Φορτώστε με `LoadOptions.LoadFormat = LoadFormat.Docx` και σκεφτείτε `Document.SaveOptions` για ροή εξόδου. | Αποτρέπει εξαιρέσεις OutOfMemory. |

---

## Practical Tips (E‑E‑A‑T Signals)

- **Πάντα κρατήστε αντίγραφο ασφαλείας** πριν προσπαθήσετε ανάκτηση· η διαδικασία μπορεί να ξαναγράψει τμήματα του αρχείου.  
- **Καταγράψτε τις προειδοποιήσεις** σε αρχείο για μεταγενέστερη ανάλυση· συχνά υποδεικνύουν τη ρίζα του προβλήματος (π.χ. λείπουν μέρη, κατεστραμμένο XML).  
- **Δοκιμάστε με πολλούς τύπους κατεστραμμένων αρχείων** – περικόψτε το αρχείο, αλλοιώστε ετικέτες XML ή αλλάξτε τη δομή zip για να δείτε πώς συμπεριφέρεται κάθε λειτουργία.  
- **Αναβαθμίζετε τακτικά το Aspose.Words**· οι νεότερες εκδόσεις βελτιώνουν τους αλγόριθμους ανάκτησης και προσθέτουν νέους τύπους προειδοποιήσεων.  
- **Συνδυάστε με επικύρωση** – μετά την ανάκτηση, εκτελέστε γρήγορα `document.UpdateFields()` και `document.Save()` για να βεβαιωθείτε ότι το έγγραφο λειτουργεί πλήρως.

---

## Συμπέρασμα

Τώρα ξέρετε πώς να **recover corrupted document** αρχεία σε C# με **set recovery mode**, **load docx with recovery**, και **prompt user on error** όταν κάτι πάει στραβά. Το πλήρες παράδειγμα δείχνει μια καθαρή, end‑to‑end ροή που λειτουργεί σε console apps, services ή UI projects.

Τι θα κάνετε στη συνέχεια; Δοκιμάστε να αντικαταστήσετε το prompt της κονσόλας με έναν modal διάλογο σε εφαρμογή WinForms, πειραματιστείτε με τη λειτουργία **Silent** για εργασίες παρασκηνίου, ή ενσωματώστε τη λογική ανάκτησης σε ένα endpoint ASP.NET file‑upload ώστε οι χρήστες να μπορούν να ανεβάζουν σπασμένα DOCX και να λαμβάνουν άμεσα μια διορθωμένη έκδοση.

Καλή προγραμματιστική δουλειά, και εύχομαι τα έγγραφά σας να παραμείνουν άθραυστα!  

---

![Recover corrupted document example](/images/recover-corrupted-document.png "recover corrupted document")

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}