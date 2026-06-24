---
category: general
date: 2026-05-04
description: Μάθετε πώς να χρησιμοποιείτε την αντικατάσταση γραμματοσειρών Aspose
  για να εντοπίζετε τις ελλιπείς γραμματοσειρές όταν φορτώνετε ένα έγγραφο Word και
  να ανακτάτε λεπτομέρειες για τις ελλιπείς γραμματοσειρές — οδηγός βήμα‑προς‑βήμα.
draft: false
keywords:
- aspose font substitution
- detect missing fonts
- load word document
- retrieve missing font
language: el
og_description: Αποκτήστε πλήρη έλεγχο της αντικατάστασης γραμματοσειρών Aspose για
  την ανίχνευση ελλιπών γραμματοσειρών κατά τη φόρτωση ενός εγγράφου Word και την
  ανάκτηση πληροφοριών ελλιπών γραμματοσειρών με πλήρη κώδικα C#.
og_title: Αντικατάσταση Γραμματοσειρών Aspose – Εντοπισμός Ελλειπουσών Γραμματοσειρών
  σε Έγγραφα Word
tags:
- Aspose.Words
- C#
- Font Management
title: 'Αντικατάσταση γραμματοσειρών Aspose: Εντοπισμός ελλιπών γραμματοσειρών σε
  έγγραφα Word'
url: /el/net/working-with-fonts/aspose-font-substitution-detect-missing-fonts-in-word-docs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution – Εντοπισμός Ελλειπουσών Γραμματοσειρών σε Έγγραφα Word

Έχετε αναρωτηθεί ποτέ γιατί ένα έγγραφο Word φαίνεται λανθασμένο σε διαφορετικό υπολογιστή; Συχνά ο ένοχος είναι μια ελλιπής γραμματοσειρά, και η **Aspose font substitution** είναι το εργαλείο που σας επιτρέπει να εντοπίζετε αυτά τα κενά πριν γίνουν οπτική καταστροφή. Σε αυτό το tutorial θα δούμε πώς να **εντοπίσετε ελλιπείς γραμματοσειρές** τη στιγμή που **φορτώνετε ένα έγγραφο Word**, και στη συνέχεια να **ανακτήσετε λεπτομέρειες ελλιπούσας γραμματοσειράς** ώστε να μπορείτε να τις διορθώσετε ή να τις αντικαταστήσετε.

Θα καλύψουμε τα πάντα, από τη ρύθμιση του callback προειδοποίησης μέχρι την εξαγωγή μιας καθαρής λίστας ελλιπούσων γραμματοσειρών. Στο τέλος, θα έχετε ένα έτοιμο προς εκτέλεση απόσπασμα C# που σας λέει ακριβώς ποιες γραμματοσειρές δεν βρέθηκαν, και θα καταλάβετε γιατί αυτό είναι σημαντικό για την πιστότητα του εγγράφου.

---

## Προαπαιτήσεις – Τι Χρειάζεστε Πριν Ξεκινήσετε

- **Aspose.Words for .NET** (συνιστάται η έκδοση v23.12 ή νεότερη).  
- Ένα .NET περιβάλλον ανάπτυξης (Visual Studio, Rider ή το `dotnet` CLI).  
- Ένα δείγμα DOCX που σκόπιμα χρησιμοποιεί μια γραμματοσειρά που δεν έχετε εγκατεστημένη — ονομάστε το `DocumentWithMissingFont.docx`.  
- Βασικές γνώσεις C# — τίποτα περίπλοκο, μόνο η δυνατότητα εκτέλεσης μιας εφαρμογής κονσόλας.

Αν κάτι από τα παραπάνω σας φαίνεται άγνωστο, κάντε παύση και εγκαταστήστε το πακέτο NuGet:

```bash
dotnet add package Aspose.Words
```

Αυτό είναι όλο. Δεν χρειάζονται επιπλέον γραμματοσειρές, ούτε εξωτερικές υπηρεσίες.

---

## Βήμα 1: Φόρτωση του Εγγράφου Word (και Έναρξη Ελέγχων Γραμματοσειρών)

Το πρώτο πράγμα που κάνετε είναι **να φορτώσετε ένα έγγραφο Word**. Το Aspose.Words αναλύει το αρχείο και, αν δεν μπορεί να εντοπίσει μια αναφερόμενη γραμματοσειρά, προσθέτει μια προειδοποίηση *FontSubstitution*. Ακολουθεί ο κώδικας που κάνει τη φόρτωση:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Path to the DOCX that may contain missing fonts
string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";

// Load the document – this is where Aspose starts checking fonts
Document doc = new Document(docPath);
```

> **Γιατί είναι σημαντικό:** Η πρώιμη φόρτωση του εγγράφου δίνει στο Aspose την ευκαιρία να σαρώσει κάθε τμήμα κειμένου, στυλ και ενσωματωμένο αντικείμενο. Αν μια γραμματοσειρά δεν βρεθεί στο σύστημα ή στον προσαρμοσμένο φάκελο γραμματοσειρών, θα λάβετε προειδοποίηση αργότερα.

---

## Βήμα 2: Σύνδεση Callback Προειδοποίησης για Καταγραφή Συμβάντων Αντικατάστασης

Το Aspose.Words χρησιμοποιεί έναν μηχανισμό callback για να σας ενημερώνει για προβλήματα όπως ελλιπείς γραμματοσειρές. Αναθέτοντας μια υλοποίηση του `IWarningCallback` στο `doc.WarningCallback`, μπορείτε να παγιδεύετε κάθε προειδοποίηση καθώς συμβαίνει.

```csharp
// Register the callback that will handle font substitution warnings
doc.WarningCallback = new FontSubstitutionWarningCallback();
```

> **Pro tip:** Μπορείτε να συνδέσετε πολλαπλά callbacks (π.χ. logging, ενημερώσεις UI) τυλίγοντας τα σε ένα σύνθετο pattern, αλλά για αυτό το tutorial ένα μόνο callback κρατά τα πράγματα σαφή.

---

## Βήμα 3: Υλοποίηση του Callback Προειδοποίησης για Αντικατάσταση Γραμματοσειρών

Τώρα ορίζουμε την κλάση που πραγματικά κάνει τη δουλειά. Το callback λαμβάνει ένα αντικείμενο `WarningInfo`; φιλτράρουμε για `WarningType.FontSubstitution` και αποθηκεύουμε την περιγραφή για μετέπειτα χρήση.

```csharp
class FontSubstitutionWarningCallback : IWarningCallback
{
    // A thread‑safe list to collect all missing‑font messages
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        // We only care about font substitution warnings
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write to console for immediate feedback
            Console.WriteLine($"Font substituted: {info.Description}");
            // Keep the message for later retrieval
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

> **Τι συμβαίνει:** Όταν το Aspose συναντά μια ελλιπή γραμματοσειρά, δημιουργεί μια προειδοποίηση όπως “Font substitution: 'Comic Sans MS' was not found, using 'Arial' instead.” Το callback μας εκτυπώνει αυτή τη γραμμή και την αποθηκεύει.

---

## Βήμα 4: Επεξεργασία του Εγγράφου (Προαιρετικό) και Συλλογή Ελλιπούσων Γραμματοσειρών

Αν χρειάζεστε μόνο **εντοπισμό ελλιπούσων γραμματοσειρών**, το βήμα φόρτωσης είναι αρκετό — οι προειδοποιήσεις εκδίδονται αυτόματα. Ωστόσο, πολλοί προγραμματιστές χρειάζονται επίσης **ανάκτηση πληροφοριών ελλιπούσας γραμματοσειράς** μετά από κάποιες ενέργειες (π.χ. αποθήκευση, μετατροπή). Παρακάτω αναγκάζουμε μια μικρή ενέργεια — αποθήκευση σε PDF — ώστε να διασφαλίσουμε ότι όλες οι προειδοποιήσεις έχουν εκδοθεί, και στη συνέχεια παίρνουμε τα συλλεγμένα μηνύματα.

```csharp
// Force a save to trigger any lazy warnings (optional but safe)
doc.Save("output.pdf");

// After processing, retrieve the list of missing fonts
if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
{
    Console.WriteLine("\n=== Missing Fonts Summary ===");
    foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
    {
        Console.WriteLine(msg);
    }
}
else
{
    Console.WriteLine("\nNo missing fonts were detected.");
}
```

> **Αναμενόμενη έξοδος κονσόλας** (παράδειγμα):
> ```
> Font substituted: Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substituted: Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> 
> === Missing Fonts Summary ===
> Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> ```

Παρατηρήστε πώς κάθε γραμμή δηλώνει σαφώς τη αρχική γραμματοσειρά και τη εναλλακτική που επέλεξε το Aspose. Αυτό αποτελεί τον πυρήνα της αναφοράς **aspose font substitution**.

---

## Βήμα 5: Προχωρημένο – Χρήση Προσαρμοσμένων Πηγών Γραμματοσειρών για Μείωση των Αντικαταστάσεων

Μερικές φορές *έχετε* τις ελλιπείς γραμματοσειρές, απλώς δεν βρίσκονται στον προεπιλεγμένο φάκελο συστήματος. Το Aspose.Words σας επιτρέπει να δείξετε σε έναν προσαρμοσμένο κατάλογο μέσω `FontSettings`. Η προσθήκη αυτού του βήματος μπορεί να μειώσει δραστικά τον αριθμό των προειδοποιήσεων αντικατάστασης.

```csharp
// Optional: Add a folder that contains your custom fonts
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
doc.FontSettings = fontSettings;
```

> **Γιατί να το προσθέσετε;** Αν διανέμετε έγγραφα σε διαφορετικούς υπολογιστές, η συσσωμάτωση των απαιτούμενων γραμματοσειρών σε έναν γνωστό φάκελο εξασφαλίζει την ίδια οπτική εμφάνιση παντού. Επίσης κάνει τη ρουτίνα **detect missing fonts** πιο ακριβή, επειδή το Aspose ελέγχει αυτόν τον φάκελο πριν καταφύγει σε εναλλακτική.

---

## Πλήρες Παράδειγμα Λειτουργίας

Συνδυάζοντας όλα τα παραπάνω, εδώ είναι ένα πλήρες, έτοιμο για αντιγραφή πρόγραμμα κονσόλας. Αποθηκεύστε το ως `Program.cs` και τρέξτε το με `dotnet run`.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // ---------- Step 1: Load the Word document ----------
        string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";
        Document doc = new Document(docPath);

        // ---------- Optional: Point to a custom font folder ----------
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
        doc.FontSettings = fontSettings;

        // ---------- Step 2: Register the warning callback ----------
        doc.WarningCallback = new FontSubstitutionWarningCallback();

        // ---------- Step 3: Force a save to trigger all warnings ----------
        doc.Save("output.pdf");

        // ---------- Step 4: Retrieve and display missing fonts ----------
        if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
        {
            Console.WriteLine("\n=== Missing Fonts Summary ===");
            foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
            {
                Console.WriteLine(msg);
            }
        }
        else
        {
            Console.WriteLine("\nNo missing fonts were detected.");
        }
    }
}

// ---------- Callback implementation ----------
class FontSubstitutionWarningCallback : IWarningCallback
{
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

**Τι θα δείτε:** Αν το πηγαίο DOCX αναφέρει γραμματοσειρές που δεν έχετε, η κονσόλα θα εκτυπώσει κάθε γραμμή αντικατάστασης ακολουθούμενη από μια σύντομη σύνοψη. Αν όλες οι γραμματοσειρές είναι παρούσες, θα εμφανιστεί το μήνυμα “No missing fonts were detected.”.

---

## Συνηθισμένα Προβλήματα & Πώς να τα Αποφύγετε

| Πρόβλημα | Γιατί Συμβαίνει | Διόρθωση |
|----------|----------------|----------|
| **Δεν εμφανίζονται προειδοποιήσεις** | Το έγγραφο χρησιμοποιεί μόνο σύστημα γραμματοσειρών, ή έχετε ήδη προσθέσει έναν προσαρμοσμένο φάκελο που περιέχει τις ελλιπείς γραμματοσειρές. | Επαληθεύστε ότι το DOCX πράγματι αναφέρει μια μη διαθέσιμη γραμματοσειρά. Μπορείτε να το ανοίξετε στο Word και να αλλάξετε μια παράγραφο σε μια σπάνια γραμματοσειρά (π.χ. “Papyrus”). |
| **Διπλότυπα μηνύματα** | Η ίδια γραμματοσειρά χρησιμοποιείται σε πολλαπλές εκτελέσεις, προκαλώντας πολλαπλές προειδοποιήσεις. | Απο-διπλοεπιλέξτε τη λίστα με `Distinct()` αν χρειάζεστε μόνο ένα μοναδικό σύνολο. |
| **Πρόσπτωση στην απόδοση σε μεγάλα έγγραφα** | Κάθε προειδοποίηση επεξεργάζεται στο UI thread. | Εκτελέστε τη φόρτωση σε ένα background task ή χρησιμοποιήστε `Parallel.ForEach` για την επεξεργασία μετά. |
| **Λάθος εναλλακτική γραμματοσειρά** | Η προεπιλεγμένη εναλλακτική του Aspose μπορεί να μην ταιριάζει με το branding σας. | Ορίστε `FontSettings.SubstitutionSettings.DefaultFontName` σε μια προτιμώμενη εναλλακτική (π.χ. “Calibri”). |

---

## Επέκταση της Λύσης – Εξαγωγή Ελλιπούσων Γραμματοσειρών σε JSON

Αν δημιουργείτε μια web υπηρεσία που πρέπει να αναφέρει τις ελλιπείς γραμματοσειρές σε έναν πελάτη, η σειριοποίηση της λίστας είναι τετριμμένη:

```csharp
using System.Text.Json;

// After gathering messages...
string json = JsonSerializer.Serialize(FontSubstitutionWarningCallback.MissingFontMessages);
File.WriteAllText("missing-fonts.json", json);
Console.WriteLine("Missing fonts exported to missing-fonts.json");
```

Τώρα το API σας μπορεί να επιστρέψει ένα καθαρό JSON payload που ένα άλλο σύστημα μπορεί να καταναλώσει.

---

## Συμπέρασμα

Σε αυτόν τον οδηγό παρουσιάσαμε την **Aspose font substitution** από την αρχή μέχρι το τέλος: φόρτωση ενός εγγράφου Word, σύνδεση ενός callback προειδοποίησης, καταγραφή κάθε συμβάντος *detect missing fonts*, και τελικά **retrieve missing font** πληροφορίες για αναφορά ή αποκατάσταση. Προσθέτοντας προαιρετικούς προσαρμοσμένους φακέλους γραμματοσειρών μπορείτε να μειώσετε τη λίστα των αντικαταστάσεων, και με λίγες επιπλέον γραμμές μπορείτε ακόμη και να εξάγετε τα αποτελέσματα ως JSON.

Θυμηθείτε, η οπτική ακεραιότητα των εγγράφων σας εξαρτάται από τις γραμματοσειρές που χρησιμοποιούν. Με την τεχνική που παρουσιάστηκε εδώ, δεν θα εκπλαγείτε ξανά από μια απρόσμενη εναλλακτική.  

Έτοιμοι για το επόμενο βήμα; Δοκιμάστε να ενσωματώσετε αυτή τη λογική σε μια μεγαλύτερη αλυσίδα επεξεργασίας εγγράφων, ή εξερευνήστε άλλες δυνατότητες του Aspose.Words όπως η ενσωμάτωση γραμματοσειρών (`doc.FontSettings.EmbeddedFonts`). Οι δυνατότητες είναι ατελείωτες, και οι χρήστες σας θα σας ευχαριστήσουν για το άψογο αποτέλεσμα.

---

![Screenshot of

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}