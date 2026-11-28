---
category: general
date: 2026-04-04
description: Μάθετε πώς να συλλαμβάνετε προειδοποιήσεις, να εντοπίζετε ελλείπουσες
  γραμματοσειρές και πώς να καταγράφετε συμβάντα αντικατάστασης χρησιμοποιώντας το
  Aspose.Words LoadOptions σε C#.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to log substitution
- Aspose.Words warning handling
- font substitution monitoring
language: el
og_description: Πώς να καταγράψετε προειδοποιήσεις, να εντοπίσετε ελλείπουσες γραμματοσειρές
  και πώς να καταγράψετε συμβάντα αντικατάστασης χρησιμοποιώντας το Aspose.Words LoadOptions
  σε C#.
og_title: Πώς να καταγράψετε προειδοποιήσεις σε C# – Εντοπίστε ελλείποντες γραμματοσειρές
  & καταγράψτε την αντικατάσταση
tags:
- C#
- Aspose.Words
- Document Loading
- Font Management
title: Πώς να καταγράψετε προειδοποιήσεις σε C# – Εντοπίστε ελλείπουσες γραμματοσειρές
  & Καταγράψτε την αντικατάσταση
url: /el/net/programming-with-loadoptions/how-to-capture-warnings-in-c-detect-missing-fonts-log-substi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Συλλέξετε Προειδοποιήσεις σε C# – Ανίχνευση Ελλειπούσων Γραμματοσειρών & Καταγραφή Αντικατάστασης

Έχετε αναρωτηθεί ποτέ **πώς να συλλέξετε προειδοποιήσεις** που εμφανίζονται όταν φορτώνετε ένα έγγραφο Word με ελλειπούσες γραμματοσειρές; Δεν είστε μόνοι. Σε πολλά πραγματικά έργα, οι γραμματοσειρές χάνονται κατά τη μετάβαση, και η σιωπηλή εναλλακτική μπορεί να διαταράξει τη διάταξή σας. Τα καλά νέα; Το Aspose.Words σας παρέχει έναν καθαρό τρόπο να ακούτε αυτές τις προειδοποιήσεις, να ανιχνεύετε ελλειπούσες γραμματοσειρές και ακόμη να καταγράφετε κάθε αντικατάσταση ώστε να διορθώσετε την πηγή αργότερα.

Σε αυτό το tutorial θα περάσουμε βήμα-βήμα από μια πλήρη, έτοιμη προς εκτέλεση λύση που δείχνει **πώς να συλλέξετε προειδοποιήσεις**, επιδεικνύει **την ανίχνευση ελλειπούσων γραμματοσειρών** και εξηγεί **πώς να καταγράψετε γεγονότα αντικατάστασης**. Στο τέλος, θα έχετε έναν επαναχρησιμοποιήσιμο διαχειριστή προειδοποιήσεων, ένα πλήρως διαμορφωμένο αντικείμενο `LoadOptions` και ένα παράδειγμα εξόδου κονσόλας που μπορείτε να επαληθεύσετε.

> **Προαπαιτούμενο:** Χρειάζεστε το Aspose.Words for .NET (v24.x ή νεότερο) εγκατεστημένο μέσω NuGet και ένα βασικό περιβάλλον ανάπτυξης C# (Visual Studio 2022 ή VS Code λειτουργούν καλά).

---

## Πώς να Συλλέξετε Προειδοποιήσεις Κατά τη Φόρτωση Εγγράφων

Ο πυρήνας της λύσης είναι μια κλάση που υλοποιεί το `IWarningCallback`. Το Aspose.Words καλεί αυτό το callback αυτόματα για κάθε προειδοποίηση που δημιουργείται κατά τη φόρτωση του εγγράφου, συμπεριλαμβανομένων των προειδοποιήσεων αντικατάστασης γραμματοσειράς.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

/// <summary>
/// Handles warning callbacks from Aspose.Words.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We're only interested in font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // This line prints the warning to the console.
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

> **Γιατί αυτό το βήμα;**  
> Φιλτράροντας με `WarningType.FontSubstitution` αποφεύγουμε την ακαταστασία από άσχετες προειδοποιήσεις (όπως παρωχημένες λειτουργίες). Αυτό κάνει το αρχείο καταγραφής εστιασμένο στο ακριβές πρόβλημα που σας ενδιαφέρει — τις ελλειπούσες γραμματοσειρές.

---

## Ανίχνευση Ελλειπούσων Γραμματοσειρών με το Aspose.Words

Όταν ένα έγγραφο αναφέρει μια γραμματοσειρά που δεν είναι εγκατεστημένη στο σύστημα, το Aspose.Words αντικαθιστά την πιο κοντινή και δημιουργεί μια προειδοποίηση. Ο παραπάνω διαχειριστής μας θα πιάσει κάθε εμφάνιση, επιτρέποντας αποτελεσματικά την **ανίχνευση ελλειπούσων γραμματοσειρών**.

Για να το δείτε σε δράση, πρέπει να διαμορφώσουμε το `LoadOptions` και να συνδέσουμε τον διαχειριστή:

```csharp
// Configure load options and attach the warning callback.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

> **Συμβουλή:** Αν προτιμάτε να συλλέγετε προειδοποιήσεις για μεταγενέστερη επεξεργασία (π.χ., να τις γράψετε σε αρχείο), αντικαταστήστε το `Console.WriteLine` με κώδικα που προσθέτει το μήνυμα σε μια `List<string>`.

---

## Πώς να Καταγράψετε Γεγονότα Αντικατάστασης

Η καταγραφή είναι τόσο απλή όσο η κατεύθυνση της εξόδου προειδοποιήσεων σε μόνιμο αποθηκευτικό μέσο. Παρακάτω υπάρχει ένα γρήγορο παράδειγμα που γράφει κάθε προειδοποίηση αντικατάστασης σε ένα αρχείο κειμένου με όνομα `font-warnings.log`.

```csharp
using System.IO;

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            // Append the message to the log file.
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

// Later, when creating LoadOptions:
var loadOptions = new LoadOptions
{
    WarningCallback = new FileLoggingWarningHandler()
};
```

> **Γιατί να καταγράψετε σε αρχείο;**  
> Τα μόνιμα αρχεία καταγραφής σας επιτρέπουν να ελέγχετε προβλήματα γραμματοσειρών σε πολλαπλές εκτελέσεις, να αυτοματοποιείτε ειδοποιήσεις ή να τροφοδοτείτε τα δεδομένα σε έλεγχο της αλυσίδας κατασκευής.

---

## Πλήρες Παράδειγμα Λειτουργίας

Συνδυάζοντας όλα, εδώ είναι μια αυτόνομη εφαρμογή κονσόλας που μπορείτε να αντιγράψετε, να επικολλήσετε και να εκτελέσετε. Δείχνει **πώς να συλλέξετε προειδοποιήσεις**, **να ανιχνεύσετε ελλειπούσες γραμματοσειρές**, και **πώς να καταγράψετε αντικατάσταση** σε ένα βήμα.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

class Program
{
    static void Main()
    {
        // Choose which handler you want:
        // var handler = new FontWarningHandler();          // console output
        var handler = new FileLoggingWarningHandler();    // file logging

        var loadOptions = new LoadOptions
        {
            WarningCallback = handler
        };

        // Path to the document that may contain missing fonts.
        string docPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

        try
        {
            // Load the document – warnings are raised automatically.
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
        }

        // If you used the file logger, show where the log lives.
        if (handler is FileLoggingWarningHandler)
        {
            Console.WriteLine($"Font warnings have been written to 'font-warnings.log'.");
        }
    }
}
```

### Αναμενόμενη Έξοδος Κονσόλας

Αν το `input.docx` αναφέρει μια γραμματοσειρά που δεν είναι εγκατεστημένη, θα δείτε κάτι όπως:

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document loaded successfully.
```

Αν αλλάξετε σε `FileLoggingWarningHandler`, οι ίδιες γραμμές θα εμφανιστούν μέσα στο `font-warnings.log` με χρονικές σήμανσεις.

![πώς να συλλέξετε προειδοποιήσεις έξοδος κονσόλας](image-placeholder.png)

---

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

### Τι γίνεται αν χρειάζεται να συλλέξω *όλες* τις προειδοποιήσεις, όχι μόνο τις αντικαταστάσεις γραμματοσειρών;

Απλώς αφαιρέστε τον έλεγχο `if (info.Type == WarningType.FontSubstitution)`. Το callback θα λαμβάνει κάθε τύπο προειδοποίησης (`WarningType.DegradedDocument`, `WarningType.UnexpectedContent`, κλπ.). Μπορείτε τότε να διακλαδώσετε με βάση το `info.Type` για να χειριστείτε κάθε περίπτωση διαφορετικά.

### Λειτουργεί αυτό με PDF ή μόνο με έγγραφα Word;

`LoadOptions` και `IWarningCallback` είναι μέρος του Aspose.Words, οπότε ισχύουν για μορφές συμβατές με Word (`.docx`, `.doc`, `.rtf`, `.html`). Για PDF θα χρησιμοποιούσατε τους δικούς μηχανισμούς προειδοποίησης του Aspose.PDF.

### Πώς μπορώ να καταστείλω τις προειδοποιήσεις αντί να τις καταγράψω;

Ορίστε `LoadOptions.WarningCallback = null` ή υλοποιήστε το callback αλλά αφήστε το σώμα της μεθόδου κενό. Η βιβλιοθήκη θα συνεχίσει να κάνει την αντικατάσταση σιωπηρά.

### Τι γίνεται με την ασφάλεια νήματος;

Η παρουσία του callback εκτελείται στο ίδιο νήμα που φορτώνει το έγγραφο, οπότε δεν χρειάζεστε επιπλέον συγχρονισμό εκτός αν μοιράζεστε τον διαχειριστή μεταξύ παράλληλων φορτώσεων. Σε αυτήν την περίπτωση, προστατέψτε τους κοινόχρηστους πόρους (π.χ., το αρχείο καταγραφής) με κλείδωμα ή χρησιμοποιήστε συλλογές ταυτόχρονου (concurrent collections).

---

## Συμπέρασμα

Καλύψαμε **πώς να συλλέξετε προειδοποιήσεις** από το Aspose.Words, σας δείξαμε πώς να **ανιχνεύσετε ελλειπούσες γραμματοσειρές**, και εξηγήσαμε **πώς να καταγράψετε γεγονότα αντικατάστασης** για μεταγενέστερη ανάλυση. Ενσωματώνοντας μια απλή υλοποίηση `IWarningCallback` στο `LoadOptions`, αποκτάτε πλήρη ορατότητα στα προβλήματα που σχετίζονται με τις γραμματοσειρές χωρίς να γεμίζετε τον κώδικά σας.

Επόμενα βήματα; Δοκιμάστε να επεκτείνετε τον καταγραφέα ώστε να στέλνει email, να ενσωματώνεται με το Azure Monitor, ή να εγκαθιστά αυτόματα τις ελλειπούσες γραμματοσειρές σε έναν διακομιστή κατασκευής. Μπορείτε επίσης να εξερευνήσετε άλλους τύπους προειδοποιήσεων — το `WarningType.DegradedDocument` μπορεί να σας ειδοποιήσει για λειτουργίες που δεν επιβίωσαν στη διαδικασία μετατροπής.

Έχετε περισσότερες ερωτήσεις σχετικά με τη διαχείριση γραμματοσειρών ή το Aspose.Words γενικά; Αφήστε ένα σχόλιο ή ανοίξτε ένα νέο θέμα στα φόρουμ του Aspose. Καλή προγραμματιστική δουλειά, και εύχομαι τα έγγραφά σας να αποδίδουν πάντα με τη σωστή γραμματοσειρά!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}