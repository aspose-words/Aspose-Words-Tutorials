---
category: general
date: 2026-06-17
description: Διαχειριστείτε την αντικατάσταση γραμματοσειρών στο Aspose.Words και
  εντοπίστε γρήγορα τις ελλιπείς γραμματοσειρές με αυτόν τον οδηγό βήμα‑βήμα για προγραμματιστές
  .NET.
draft: false
keywords:
- handle font substitution
- detect missing fonts
- how to detect missing fonts
language: el
og_description: Διαχειριστείτε την αντικατάσταση γραμματοσειρών στο Aspose.Words και
  μάθετε πώς να εντοπίζετε τις ελλιπείς γραμματοσειρές στα έγγραφά σας με σαφή παραδείγματα
  κώδικα.
og_title: Διαχείριση αντικατάστασης γραμματοσειρών στο Aspose.Words – Πλήρης οδηγός
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Handle font substitution in Aspose.Words and detect missing fonts quickly
    with this step‑by‑step tutorial for .NET developers.
  headline: Handle Font Substitution in Aspose.Words – Complete Programming Guide
  type: TechArticle
- description: Handle font substitution in Aspose.Words and detect missing fonts quickly
    with this step‑by‑step tutorial for .NET developers.
  name: Handle Font Substitution in Aspose.Words – Complete Programming Guide
  steps:
  - name: '**Create a test DOCX** that references a font you know isn’t on the machine
      (e.g., “Comic Sans MS” on a minimal Docker image).'
    text: '**Create a test DOCX** that references a font you know isn’t on the machine
      (e.g., “Comic Sans MS” on a minimal Docker image).'
  - name: Run the console app or API endpoint.
    text: Run the console app or API endpoint.
  - name: Verify that the console (or HTTP response) lists the substitution warning.
    text: Verify that the console (or HTTP response) lists the substitution warning.
  - name: Optionally, open the resulting PDF and check the font properties—Aspose.Words
      should show the fallback font you configured.
    text: Optionally, open the resulting PDF and check the font properties—Aspose.Words
      should show the fallback font you configured.
  type: HowTo
tags:
- Aspose.Words
- .NET
- Font Management
title: Διαχείριση αντικατάστασης γραμματοσειρών στο Aspose.Words – Πλήρης οδηγός προγραμματισμού
url: /el/net/working-with-fonts/handle-font-substitution-in-aspose-words-complete-programmin/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Διαχείριση Αντικατάστασης Γραμματοσειρών στο Aspose.Words – Πλήρης Οδηγός Προγραμματισμού

Έχετε αναρωτηθεί ποτέ πώς να **διαχειριστείτε την αντικατάσταση γραμματοσειρών** όταν ένα έγγραφο Word αναφέρει μια γραμματοσειρά που δεν είναι εγκατεστημένη στον διακομιστή; Δεν είστε μόνοι. Σε πολλές πραγματικές εφαρμογές—σκεφτείτε γεννήτριες τιμολογίων ή αυτοματοποιημένες υπηρεσίες αναφορών—οι ελλείπουσες γραμματοσειρές προκαλούν σιωπηλές εναλλακτικές που χαλούν τη διάταξη.  

Τα καλά νέα είναι ότι το Aspose.Words σας παρέχει ένα ενσωματωμένο σύστημα προειδοποιήσεων που σας επιτρέπει να **εντοπίσετε ελλείπουσες γραμματοσειρές** και να αντιδράσετε όπως θέλετε. Σε αυτό το tutorial θα περάσουμε από την καταχώρηση ενός διαχειριστή προειδοποιήσεων, τη φόρτωση ενός εγγράφου και την εξαγωγή των ακριβών συμβάντων αντικατάστασης γραμματοσειρών που χρειάζεστε. Στο τέλος θα δείτε επίσης πώς να απαντήσετε στην κλασική ερώτηση “**πώς να εντοπίσετε ελλείπουσες γραμματοσειρές**?” με καθαρό, παραγωγικό κώδικα.

## Τι Καλύπτει Αυτός ο Οδηγός

* Ρύθμιση του Aspose.Words ώστε να εκδίδει προειδοποιήσεις για κάθε αντικατάσταση γραμματοσειράς.  
* Συλλογή αυτών των προειδοποιήσεων σε προσαρμοσμένο διαχειριστή ώστε να μπορείτε να καταγράψετε, αντικαταστήσετε ή ακυρώσετε.  
* Χρήση των συλλεγμένων δεδομένων για **εντοπισμό ελλείπουσων γραμματοσειρών** πριν αποθηκευτεί ή αποδοθεί το έγγραφο.  
* Συμβουλές για την αντιμετώπιση ακραίων περιπτώσεων—όπως όταν μια εναλλακτική γραμματοσειρά επιλέγεται σιωπηρά.  
* Ένα πλήρες, εκτελέσιμο παράδειγμα που μπορείτε να ενσωματώσετε σε οποιαδήποτε .NET console εφαρμογή.

> **Prerequisites** – Θα χρειαστείτε ένα πρόσφατο .NET SDK (η έκδοση 6.0+ λειτουργεί άψογα), μια έγκυρη άδεια Aspose.Words for .NET (ή ένα προσωρινό κλειδί αξιολόγησης), και ένα δείγμα DOCX που σκόπιμα αναφέρει μια γραμματοσειρά που δεν έχετε εγκατεστημένη. Δεν απαιτούνται άλλες βιβλιοθήκες τρίτων.

---

## ## Διαχείριση Αντικατάστασης Γραμματοσειρών με Προσαρμοσμένο Διαχειριστή Προειδοποιήσεων

Το Aspose.Words δημιουργεί ένα αντικείμενο `WarningInfo` κάθε φορά που δεν μπορεί να βρει τη ζητούμενη γραμματοσειρά. Από προεπιλογή αυτές οι προειδοποιήσεις αγνοούνται, γι' αυτό συχνά δεν παρατηρείτε την αντικατάσταση. Για να **διαχειριστείτε την αντικατάσταση γραμματοσειρών**, αντικαθιστάτε τον προεπιλεγμένο διαχειριστή προειδοποιήσεων με έναν που κάνει κάτι χρήσιμο.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // Register a custom warning handler that prints font‑substitution events.
        FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
            (sender, args) =>
            {
                // We're only interested in font‑substitution warnings.
                if (args.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ Font substituted: {args.Description}");
                }
            });

        // Load a document that deliberately references an unavailable font.
        Document doc = new Document("Samples/MissingFont.docx");

        // Force a save to trigger any pending warnings (e.g., PDF conversion).
        doc.Save("Output/Result.pdf");
    }
}
```

### Γιατί Λειτουργεί

* `FontSettings.DefaultWarningHandler` είναι μια παγκόσμια στατική ιδιότητα—αφού τη ρυθμίσετε, **κάθε** λειτουργία του Aspose.Words στο τρέχον AppDomain χρησιμοποιεί το delegate σας.  
* Ο `WarningInfoCollectionHandler` λαμβάνει ένα αντικείμενο `WarningInfo` που περιέχει `WarningType` και μια ανθρώπινα αναγνώσιμη `Description`. Η φιλτράρισμα με `WarningType.FontSubstitution` εξασφαλίζει ότι βλέπετε μόνο τα συμβάντα που σας ενδιαφέρουν.  
* Η κλήση `doc.Save` αναγκάζει τη βιβλιοθήκη να επιλύσει όλες τις γραμματοσειρές, και εκεί εκδίδονται οι προειδοποιήσεις. Αν χρειάζεστε μόνο την επιθεώρηση του εγγράφου χωρίς αποθήκευση, μπορείτε να καλέσετε `doc.UpdatePageLayout()` αντί αυτού.

**Αναμενόμενη έξοδος κονσόλας** (υποθέτοντας ότι η ελλείπουσα γραμματοσειρά είναι “Papyrus”):

```
⚠️ Font substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
```

Αυτή η γραμμή είναι η απόδειξή σας ότι η βιβλιοθήκη **εντόπισε ελλείπουσες γραμματοσειρές** και επέλεξε εναλλακτική.

---

## ## Ανίχνευση Ελλειπουσών Γραμματοσειρών Πριν από την Απόδοση

Μερικές φορές θέλετε να σταματήσετε τη διαδικασία εντελώς αν λείπει μια απαιτούμενη γραμματοσειρά—ίσως επειδή οι οδηγίες της μάρκας απαιτούν ακριβή τυπογραφία. Ο διαχειριστής προειδοποιήσεων μπορεί να επεκταθεί ώστε να συλλέγει όλα τα μηνύματα ελλείπουσας γραμματοσειράς σε μια λίστα, ώστε να μπορείτε να πάρετε μια απόφαση.

```csharp
using System.Collections.Generic;

// ...

static List<string> missingFonts = new List<string>();

static void Main()
{
    FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
        (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
            {
                // Store the description for later analysis.
                missingFonts.Add(args.Description);
                Console.WriteLine($"⚠️ Font substituted: {args.Description}");
            }
        });

    Document doc = new Document("Samples/MissingFont.docx");
    doc.UpdatePageLayout();   // Triggers warnings without saving.

    if (missingFonts.Count > 0)
    {
        Console.WriteLine("\n❗ Detected missing fonts:");
        foreach (var msg in missingFonts)
            Console.WriteLine($" - {msg}");

        // Optionally abort the operation.
        // throw new InvalidOperationException("Missing required fonts.");
    }
    else
    {
        Console.WriteLine("\n✅ No font substitution detected.");
    }

    // Continue with saving or further processing if you wish.
    doc.Save("Output/Result.pdf");
}
```

### Πώς Αυτό Απαντά στο “πώς να εντοπίσετε ελλείπουσες γραμματοσειρές”

* Η λίστα `missingFonts` λειτουργεί ως λογιστικό βιβλίο κάθε συμβάντος αντικατάστασης.  
* Μετά το `UpdatePageLayout`, μπορείτε να ελέγξετε τη λίστα και να αποφασίσετε αν θα συνεχίσετε, θα καταγράψετε ή θα ρίξετε εξαίρεση.  
* Αυτό το μοτίβο λειτουργεί για οποιαδήποτε μορφή εξόδου (PDF, HTML, εικόνες) επειδή το σύστημα προειδοποιήσεων είναι ανεξάρτητο από τη μορφή.

---

## ## Προηγμένη Συμβουλή: Αντικατάσταση Ελλειπουσών Γραμματοσειρών με Συγκεκριμένη Εναλλακτική

Αν έχετε μια εταιρική γραμματοσειρά που πρέπει να χρησιμοποιείται, μπορείτε να πείτε στο Aspose.Words να αντικαθιστά αυτόματα κάθε ελλείπουσα γραμματοσειρά με την εναλλακτική σας. Αυτό είναι χρήσιμο όταν θέλετε το έγγραφο να *παραμένει* αποδεκτό χωρίς χειροκίνητη επεξεργασία.

```csharp
// Configure a fallback font collection.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
    "AnyMissingFont", new string[] { "Calibri", "Arial" });

FontSettings.DefaultFontSettings = fontSettings;
```

Τοποθετήστε το παραπάνω απόσπασμα **πριν** τη φόρτωση του εγγράφου. Τώρα οποιαδήποτε ελλείπουσα γραμματοσειρά—ανεξάρτητα από το αρχικό της όνομα—θα αντικατασταθεί με το “Calibri” (ή “Arial” αν το Calibri δεν είναι διαθέσιμο). Θα συνεχίσετε να λαμβάνετε την προειδοποίηση, αλλά το έγγραφο θα αποδοθεί με τη γραμματοσειρά που ελέγχετε.

---

## ## Συνηθισμένα Πιθανά Σφάλματα & Πώς να τα Αποφύγετε

| Πρόβλημα | Γιατί Συμβαίνει | Διόρθωση |
|----------|----------------|----------|
| **Οι προειδοποιήσεις εξαφανίζονται μετά την πρώτη κλήση** | Το στατικό `DefaultWarningHandler` αντικαθίσταται αργότερα στην εφαρμογή. | Ορίστε τον διαχειριστή **μια φορά** στην εκκίνηση της εφαρμογής, ή αποθηκεύστε μια αναφορά και επανατοποθετήστε την αν την αλλάξετε. |
| **Μόνο η πρώτη ελλείπουσα γραμματοσειρά αναφέρεται** | Κάποια API ομαδοποιούν προειδοποιήσεις· πρέπει να καλέσετε `UpdatePageLayout` ή `Save` για να αδειάσετε την ουρά. | Επιβάλετε ενημέρωση διάταξης ή αποθηκεύστε στη μορφή που προτίθεστε να δημιουργήσετε. |
| **Η αντικατάσταση συνεχίζεται ακόμη και μετά την ακύρωση** | Ο διαχειριστής προειδοποιήσεων εκτελείται *μετά* την αντικατάσταση που ήδη συνέβη. | Χρησιμοποιήστε τον διαχειριστή για **καταγραφή** και στη συνέχεια ρίξτε εξαίρεση για να σταματήσετε περαιτέρω επεξεργασία. |
| **Ελλείπουσες γραμματοσειρές σε Linux containers** | Το Linux συχνά δεν διαθέτει τον κατάλογο γραμματοσειρών των Windows, οδηγώντας σε πολλές αντικαταστάσεις. | Τοποθετήστε τις απαιτούμενες γραμματοσειρές στο container ή χρησιμοποιήστε `FontSettings.SetFontsFolder` για να δείξετε σε έναν προσαρμοσμένο φάκελο γραμματοσειρών. |

---

## ## Ανίχνευση Αντικατάστασης Γραμματοσειρών σε Σενάριο Web API

Αν εξυπηρετείτε έγγραφα μέσω ASP.NET Core, πιθανότατα δεν θέλετε εγγραφές στην κονσόλα. Αντί αυτού, συλλέξτε τις προειδοποιήσεις και επιστρέψτε τις ως μέρος της HTTP απόκρισης.

```csharp
[ApiController]
[Route("api/[controller]")]
public class DocumentController : ControllerBase
{
    [HttpPost("convert")]
    public IActionResult Convert(IFormFile file)
    {
        var missingFonts = new List<string>();

        FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
            (s, e) =>
            {
                if (e.WarningType == WarningType.FontSubstitution)
                    missingFonts.Add(e.Description);
            });

        using var stream = file.OpenReadStream();
        var doc = new Document(stream);
        doc.UpdatePageLayout();

        if (missingFonts.Any())
        {
            return BadRequest(new { message = "Missing fonts detected", details = missingFonts });
        }

        // Convert to PDF and stream back.
        var pdfStream = new MemoryStream();
        doc.Save(pdfStream, SaveFormat.Pdf);
        pdfStream.Position = 0;
        return File(pdfStream, "application/pdf", "result.pdf");
    }
}
```

Τώρα το API **εντοπίζει ελλείπουσες γραμματοσειρές** και επιστρέφει ένα σαφές JSON payload πριν δημιουργηθεί οποιοδήποτε PDF. Αυτή είναι μια πρακτική εικονογράφηση του “πώς να εντοπίσετε ελλείπουσες γραμματοσειρές” σε μια υπηρεσία παραγωγικού επιπέδου.

---

## ## Δοκιμή της Υλοποίησής Σας

1. **Δημιουργήστε ένα δοκιμαστικό DOCX** που αναφέρει μια γραμματοσειρά που ξέρετε ότι δεν υπάρχει στη μηχανή (π.χ., “Comic Sans MS” σε μια ελαφριά Docker εικόνα).  
2. Εκτελέστε την console εφαρμογή ή το endpoint του API.  
3. Επαληθεύστε ότι η κονσόλα (ή η HTTP απόκριση) εμφανίζει την προειδοποίηση αντικατάστασης.  
4. Προαιρετικά, ανοίξτε το παραγόμενο PDF και ελέγξτε τις ιδιότητες γραμματοσειράς—το Aspose.Words θα πρέπει να δείχνει τη γραμματοσειρά εναλλακτική που διαμορφώσατε.

Αν δείτε την προειδοποίηση αλλά το PDF εξακολουθεί να χρησιμοποιεί μια απροσδόκητη γραμματοσειρά, ελέγξτε ξανά τη σειρά `SubstitutionSettings`; η πρώτη αντιστοιχία κερδίζει.

---

## ## Συμπέρασμα

Καλύψαμε όλα όσα χρειάζεστε για να **διαχειριστείτε την αντικατάσταση γραμματοσειρών** στο Aspose.Words, από την καταχώρηση ενός διαχειριστή προειδοποιήσεων μέχρι τον προγραμματιστικό **εντοπισμό ελλείπουσων γραμματοσειρών** και ακόμη και την αντικατάστασή τους με μια εταιρική γραμματοσειρά. Εκμεταλλευόμενοι το ενσωματωμένο σύστημα προειδοποιήσεων αποκτάτε πλήρη ορατότητα σε κάθε συμβάν “γραμματοσειρά δεν βρέθηκε”, το οποίο απαντά άμεσα στην ερώτηση “**πώς να εντοπίσετε ελλείπουσες γραμματοσειρές**?” που κάθε προγραμματιστής θέτει όταν αυτοματοποιεί τη δημιουργία εγγράφων.

Τι ακολουθεί; Δοκιμάστε να συνδυάσετε αυτή τη λογική με **δυναμική φόρτωση γραμματοσειρών** (`FontSettings.SetFontsFolder`) για να υποστηρίξετε γραμματοσειρές που ανεβάζουν οι χρήστες σε πραγματικό χρόνο, ή επεκτείνετε τον διαχειριστή προειδοποιήσεων ώστε να γράφει εγγραφές σε μια κεντρική υπηρεσία logging όπως το Serilog. Όσο περισσότερο instrumentarize τη διαχείριση γραμματοσειρών, τόσο πιο αξιόπιστη γίνεται η pipeline εγγράφων σας.

Έχετε κάποιο δύσκολο σενάριο αντικατάστασης γραμματοσειρών που προσπαθείτε να λύσετε; Αφήστε ένα σχόλιο παρακάτω και ας το αντιμετωπίσουμε μαζί. Καλό coding!

## Τι Πρέπει Να Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [Πώς να Εντοπίσετε Γραμματοσειρές στο Aspose.Words – Διαχείριση Προειδοποιήσεων & Ρυθμίσεων](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Ενεργοποίηση Προειδοποιήσεων Αντικατάστασης Γραμματοσειρών στο Aspose.Words – Πλήρης Οδηγός](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Πώς να Φορτώσετε DOCX και να Εντοπίσετε Ελλείπουσες Γραμματοσειρές – Πλήρης Οδηγός C#](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}