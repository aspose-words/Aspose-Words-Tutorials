---
category: general
date: 2026-02-21
description: Μάθετε πώς να ενεργοποιείτε προειδοποιήσεις, να εντοπίζετε ελλιπείς γραμματοσειρές
  και πώς να φορτώνετε ασφαλώς αρχεία docx χρησιμοποιώντας το Aspose.Words σε C#.
  Ακολουθήστε τον οδηγό βήμα‑προς‑βήμα.
draft: false
keywords:
- how to enable warnings
- detect missing fonts
- how to load docx
- font substitution handling
- Aspose.Words warnings
language: el
og_description: Πώς να ενεργοποιήσετε τις προειδοποιήσεις, να εντοπίσετε τις ελλείπουσες
  γραμματοσειρές και να φορτώσετε σωστά αρχεία docx με το Aspose.Words. Περιλαμβάνεται
  πλήρες παράδειγμα κώδικα.
og_title: Πώς να ενεργοποιήσετε τις προειδοποιήσεις και να εντοπίσετε τις ελλείπουσες
  γραμματοσειρές κατά τη φόρτωση του DOCX
tags:
- C#
- Aspose.Words
- Document processing
title: Πώς να ενεργοποιήσετε τις προειδοποιήσεις και να εντοπίσετε τις ελλειπούσες
  γραμματοσειρές κατά τη φόρτωση αρχείων DOCX
url: /el/net/working-with-fonts/how-to-enable-warnings-and-detect-missing-fonts-when-loading/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να ενεργοποιήσετε προειδοποιήσεις και να εντοπίσετε ελλιπείς γραμματοσειρές κατά τη φόρτωση αρχείων DOCX

Έχετε αναρωτηθεί **πώς να ενεργοποιήσετε προειδοποιήσεις** για ελλιπείς γραμματοσειρές πριν αυτές επηρεάσουν σιωπηλά την απόδοση του εγγράφου σας; Δεν είστε μόνοι—πολλοί προγραμματιστές υποθέτουν ότι η βιβλιοθήκη θα «κάνει το σωστό», μόνο για να διαπιστώσουν αργότερα ότι μια γραμματοσειρά αντικαταστάθηκε χωρίς κανένα ίχνος.  

Σε αυτό το tutorial θα σας δείξουμε ακριβώς **πώς να ενεργοποιήσετε προειδοποιήσεις**, πώς να **εντοπίσετε ελλιπείς γραμματοσειρές**, και τον σωστό τρόπο **πώς να φορτώσετε docx** χρησιμοποιώντας το Aspose.Words for .NET. Στο τέλος θα έχετε ένα έτοιμο δείγμα που εκτυπώνει κάθε προειδοποίηση αντικατάστασης γραμματοσειράς στην κονσόλα, ώστε να μην χρειάζεται ποτέ να μαντεύετε τι συνέβη μέσα στο αρχείο.

## Προαπαιτούμενα

- .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης σε .NET Framework 4.7+)  
- Visual Studio 2022 ή οποιοδήποτε IDE C# προτιμάτε  
- Το **Aspose.Words** πακέτο NuGet (`Install-Package Aspose.Words`)  
- Ένα αρχείο DOCX που μπορεί να περιέχει γραμματοσειρές που δεν είναι εγκατεστημένες στο σύστημά σας (θα το ονομάσουμε `input.docx`)

> **Pro tip:** Αν δεν έχετε αρχείο δοκιμής, ανοίξτε ένα έγγραφο Word που χρησιμοποιεί μια προσαρμοσμένη εταιρική γραμματοσειρά και αποθηκεύστε το ως `input.docx`. Αυτό θα ενεργοποιήσει την προειδοποίηση που θέλουμε να καταγράψουμε.

## Επισκόπηση της λύσης

1. **Δημιουργήστε** ένα αντικείμενο `LoadOptions` με την ιδιότητα `FontSubstitutionWarnings` ενεργοποιημένη.  
2. **Φορτώστε** το αρχείο DOCX χρησιμοποιώντας αυτές τις επιλογές.  
3. **Εξετάστε** τη συλλογή `WarningCallback` για τυχόν καταχωρήσεις `FontSubstitution`.  
4. **Αντιδράστε** – μπορείτε να καταγράψετε, να εμφανίσετε ή ακόμη και να αντικαταστήσετε προγραμματιστικά τη λείπουσα γραμματοσειρά.

Παρακάτω θα αναλύσουμε κάθε βήμα, θα εξηγήσουμε *γιατί* είναι σημαντικό και θα σας δώσουμε ένα πλήρες, εκτελέσιμο απόσπασμα κώδικα.

---

## Βήμα 1: Εγκατάσταση Aspose.Words και ρύθμιση του έργου

Πριν μπορέσουμε **πώς να ενεργοποιήσετε προειδοποιήσεις**, χρειαζόμαστε τη βιβλιοθήκη που τις υποστηρίζει.

```bash
# Using the .NET CLI
dotnet add package Aspose.Words
```

Ή, στην κονσόλα Διαχειριστή Πακέτων του Visual Studio:

```powershell
Install-Package Aspose.Words
```

> **Γιατί αυτό το βήμα;**  
> Χωρίς το πακέτο, οι κλάσεις `LoadOptions`, `Document` και η υποδομή προειδοποιήσεων δεν υπάρχουν. Η προσθήκη της αναφοράς NuGet εξασφαλίζει ότι θα χρησιμοποιήσετε την πιο πρόσφατη σταθερή έκδοση (στην ώρα της συγγραφής, 24.5).

---

## Βήμα 2: Δημιουργία επιλογών φόρτωσης που ενεργοποιούν προειδοποιήσεις αντικατάστασης γραμματοσειράς

Η καρδιά του **πώς να ενεργοποιήσετε προειδοποιήσεις** βρίσκεται στην κλάση `LoadOptions`. Ορίζοντας το `FontSubstitutionWarnings` σε `true` λέτε στη μηχανή να καταγράφει κάθε φορά που πρέπει να αντικαταστήσει μια λείπουσα γραμματοσειρά.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Step 2: Build the options object
LoadOptions loadOptions = new LoadOptions
{
    // This flag makes the library emit warnings for any font it cannot find.
    FontSubstitutionWarnings = true
};
```

> **Γιατί να ενεργοποιήσετε αυτήν τη σημαία;**  
> Από προεπιλογή, το Aspose.Words αντικαθιστά σιωπηλά τις λείπουσες γραμματοσειρές με μια εφεδρική (συνήθως Arial). Αυτό μπορεί να προκαλέσει μετατοπίσεις διάταξης, αόρατους χαρακτήρες ή παραβιάσεις branding. Η ενεργοποίηση της σημαίας σας δίνει πλήρη διαφάνεια.

---

## Βήμα 3: Φόρτωση του αρχείου DOCX χρησιμοποιώντας τις ρυθμισμένες επιλογές

Τώρα που ξέρουμε **πώς να φορτώσουμε docx** με ενεργές προειδοποιήσεις, πραγματοποιούμε την πραγματική φόρτωση.

```csharp
// Step 3: Load the document – replace the path with your own file location.
string docPath = @"YOUR_DIRECTORY\input.docx";
Document document = new Document(docPath, loadOptions);
```

> **Τι συμβαίνει στο παρασκήνιο;**  
> Κατά την ανάλυση του DOCX, το Aspose.Words ελέγχει κάθε στοιχείο `<w:rFonts>`. Αν η καθορισμένη γραμματοσειρά δεν είναι εγκατεστημένη, καταγράφει μια προειδοποίηση `FontSubstitution` και χρησιμοποιεί μια προεπιλεγμένη γραμματοσειρά. Επειδή ενεργοποιήσαμε τις προειδοποιήσεις, αυτές οι καταχωρήσεις προστίθενται στο `document.WarningCallback.Warnings`.

---

## Βήμα 4: Ανάκτηση και εμφάνιση προειδοποιήσεων αντικατάστασης γραμματοσειράς

Η ιδιότητα `WarningCallback` περιέχει ένα `WarningInfoCollection`. Διατρέξτε το, φιλτράρετε για `WarningType.FontSubstitution` και εκτυπώστε τα μηνύματα.

```csharp
// Step 4: Iterate over warnings and print font‑substitution details.
foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substituted: {warning.Message}");
    }
}
```

**Αναμενόμενη έξοδος** (παράδειγμα):

```
⚠️ Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
⚠️ Font substituted: Font 'CorporateLogo' was not found. Substituted with 'Times New Roman'.
```

> **Τι να κάνετε με αυτά τα μηνύματα;**  
> Μπορείτε να τα καταγράψετε σε αρχείο, να τα εμφανίσετε σε UI, ή ακόμη και να ενεργοποιήσετε μια προσαρμοσμένη ρουτίνα εφεδρικής γραμματοσειράς. Το σημαντικό είναι ότι τώρα *εντοπίζετε τις λείπουσες γραμματοσειρές* αντί να μαντεύετε αργότερα.

---

## Βήμα 5: (Προαιρετικό) Αντικατάσταση λείπωντων γραμματοσειρών με συγκεκριμένη εφεδρεία

Αν έχετε μια εταιρική γραμματοσειρά που θέλετε να επιβάλλετε, μπορείτε να διαχειριστείτε τις προειδοποιήσεις και να τις αντικαταστήσετε άμεσα.

```csharp
// Optional: Custom fallback font
string fallbackFont = "Calibri";

foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        // Extract the missing font name from the warning message
        string missingFont = warning.Message.Split('\'')[1];
        Console.WriteLine($"Replacing missing font '{missingFont}' with '{fallbackFont}'");
        document.FontInfos[missingFont].SubstitutedFont = fallbackFont;
    }
}
```

> **Γιατί να το εξετάσετε;**  
> Εξασφαλίζει οπτική συνέπεια σε όλα τα παραγόμενα έγγραφα, κάτι κρίσιμο για τη συμμόρφωση με το brand.

---

## Πλήρες, εκτελέσιμο παράδειγμα

Παρακάτω υπάρχει ένα μοναδικό αρχείο C# που μπορείτε να αντιγράψετε‑επικολλήσετε σε μια εφαρμογή console. Καλύπτει τα πάντα—από την εγκατάσταση του πακέτου μέχρι την εκτύπωση των προειδοποιήσεων.

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create LoadOptions with warnings enabled
            LoadOptions loadOptions = new LoadOptions
            {
                FontSubstitutionWarnings = true
            };

            // 2️⃣ Load the DOCX (adjust the path as needed)
            string docPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Show all font‑substitution warnings
            Console.WriteLine("=== Font Substitution Warnings ===");
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Message}");
                }
            }

            // 4️⃣ (Optional) Replace missing fonts with Calibri
            string fallback = "Calibri";
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    string missingFont = warning.Message.Split('\'')[1];
                    Console.WriteLine($"Replacing '{missingFont}' with '{fallback}'");
                    doc.FontInfos[missingFont].SubstitutedFont = fallback;
                }
            }

            // 5️⃣ Save the corrected document (optional)
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

**Τρέξτε το**: `dotnet run` από το φάκελο του έργου. Αν λείπουν γραμματοσειρές, θα δείτε τις προειδοποιήσεις στην κονσόλα και η προαιρετική αντικατάσταση θα εφαρμοστεί πριν αποθηκευτεί το αρχείο.

---

## Συχνές ερωτήσεις

### Λειτουργεί αυτό και με μετατροπή σε PDF;

Ναι. Αφού διαχειριστείτε τις προειδοποιήσεις, μπορείτε να καλέσετε `doc.Save("output.pdf")` και οι αντικατεστημένες γραμματοσειρές θα εμφανιστούν στο PDF όπως στο DOCX.

### Τι γίνεται αν θέλω να καταστέλλω προειδοποιήσεις για μια συγκεκριμένη γραμματοσειρά;

Μπορείτε να τις φιλτράρετε στον βρόχο—απλώς παραλείψτε το `WarningInfo` του οποίου το `Message` περιέχει το όνομα της γραμματοσειράς που θέλετε να αγνοήσετε.

### Είναι διαθέσιμη η `FontSubstitutionWarnings` σε παλαιότερες εκδόσεις του Aspose.Words;

Εισήχθη στην έκδοση 20.5. Αν χρησιμοποιείτε παλαιότερη έκδοση, αναβαθμίστε μέσω NuGet· η αλλαγή API είναι συμβατή με παλαιότερες εκδόσεις.

---

## Συμπέρασμα

Διασχίσαμε **πώς να ενεργοποιήσετε προειδοποιήσεις**, σας δείξαμε **πώς να εντοπίσετε ελλιπείς γραμματοσειρές**, και παρουσιάσαμε τον σωστό τρόπο **πώς να φορτώσετε docx** με το Aspose.Words διατηρώντας πλήρη ορατότητα στις αντικαταστάσεις γραμματοσειρών. Εξετάζοντας το `document.WarningCallback.Warnings` έχετε ένα αξιόπιστο αποδεικτικό ίχνος—χωρίς σιωπηλές εναλλακτικές.

Τι θα κάνετε στη συνέχεια; Δοκιμάστε να ενσωματώσετε τη λογική προειδοποιήσεων σε ένα σύστημα logging όπως το Serilog, ή δημιουργήστε ένα UI που επισημαίνει τις λείπουσες γραμματοσειρές πριν παραδώσετε το έγγραφο στους χρήστες. Μπορείτε επίσης να εξερευνήσετε την κλάση `FontSettings` για πιο λεπτομερή έλεγχο των πολιτικών αντικατάστασης γραμματοσειρών.

Καλή προγραμματιστική δουλειά, και εύχομαι τα έγγραφά σας να αποδίδουν πάντα ακριβώς όπως τα φαντάζεστε! 

![Διάγραμμα που απεικονίζει τη ροή από τη φόρτωση ενός αρχείου DOCX στην καταγραφή προειδοποιήσεων αντικατάστασης γραμματοσειράς – πώς να ενεργοποιήσετε προειδοποιήσεις στο Aspose.Words](/images/font-warning-flow.png)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}