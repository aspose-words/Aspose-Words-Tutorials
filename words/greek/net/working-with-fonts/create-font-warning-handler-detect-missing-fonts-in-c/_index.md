---
category: general
date: 2026-02-12
description: Δημιουργήστε διαχειριστή προειδοποιήσεων γραμματοσειράς για την ανίχνευση
  και παρακολούθηση ελλιπών γραμματοσειρών στο Aspose.Words. Μάθετε πώς να καταγράφετε
  αποτελεσματικά τις προειδοποιήσεις.
draft: false
keywords:
- create font warning handler
- detect missing fonts
- track missing fonts
- how to log warnings
language: el
og_description: Δημιουργήστε διαχειριστή προειδοποιήσεων γραμματοσειρών σε C# για
  να εντοπίζετε ελλείπουσες γραμματοσειρές και μάθετε πώς να καταγράφετε προειδοποιήσεις
  όταν το Aspose.Words αντικαθιστά γραμματοσειρές.
og_title: Δημιουργία Διαχειριστή Προειδοποιήσεων Γραμματοσειρών – Εντοπισμός Ελλειπόντων
  Γραμματοσειρών
tags:
- Aspose.Words
- C#
- Document Processing
title: Δημιουργία Διαχειριστή Προειδοποιήσεων Γραμματοσειρών – Ανίχνευση Ελλειπόντων
  Γραμματοσειρών σε C#
url: /el/net/working-with-fonts/create-font-warning-handler-detect-missing-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία Διαχειριστή Προειδοποιήσεων Γραμματοσειρών – Ανίχνευση Ελλειπουσών Γραμματοσειρών σε C#

Σας έχει ποτέ χρειαστεί να **create font warning handler** επειδή ένα έγγραφο Word αντικατέστησε σιωπηλά μια γραμματοσειρά που δεν περιμένατε; Δεν είστε ο μόνος. Όταν το Aspose.Words φορτώνει ένα DOCX που αναφέρει μια γραμματοσειρά που λείπει από τον διακομιστή, επιστρέφει σιωπηλά σε μια προεπιλεγμένη γραμματοσειρά — αφήνοντας τη διάταξή σας ελαφρώς χαλασμένη.  

Σε αυτό το tutorial θα σας δείξουμε ακριβώς πώς να **detect missing fonts**, **track missing fonts**, και **how to log warnings** ώστε να εντοπίζετε αυτές τις αντικαταστάσεις πριν σας επηρεάσουν. Στο τέλος θα έχετε έναν επαναχρησιμοποιήσιμο διαχειριστή προειδοποιήσεων που εκτυπώνει κάθε συμβάν αντικατάστασης γραμματοσειράς στην κονσόλα (ή σε οποιονδήποτε logger προτιμάτε). Χωρίς μυστήριο, μόνο σαφής, εφαρμόσιμος κώδικας.

## Prerequisites

- .NET 6.0 ή νεότερο (το API είναι το ίδιο για .NET Framework 4.6+)
- Aspose.Words for .NET εγκατεστημένο (`dotnet add package Aspose.Words`)
- Ένα αρχείο Word που αναφέρει μια γραμματοσειρά που δεν είναι εγκατεστημένη στο σύστημά σας (π.χ., `MissingFont.docx`)

Αν τα έχετε ήδη, υπέροχα — ας ξεκινήσουμε.

## Step 1: Set Up LoadOptions with a Warning Callback  

Το πρώτο πράγμα που κάνετε όταν θέλετε να **create font warning handler** είναι να πείτε στο Aspose.Words να εκτελεί ένα callback κάθε φορά που συναντά πρόβλημα. `LoadOptions` είναι το δοχείο για αυτή τη ρύθμιση.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Create LoadOptions and attach our custom handler
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

**Γιατί είναι σημαντικό:**  
`LoadOptions` είναι το μοναδικό σημείο όπου μπορείτε να συνδέσετε ένα `IWarningCallback`. Χωρίς αυτό, το Aspose.Words θα καταγράφει προειδοποιήσεις εσωτερικά αλλά δεν θα τις βλέπετε. Αναθέτοντας το `FontWarningHandler` αποκτάτε πλήρη έλεγχο πάνω σε ό,τι συμβαίνει όταν μια ελλειπούσα γραμματοσειρά αντικαθίσταται.

## Step 2: Implement the FontWarningHandler Class  

Τώρα δημιουργούμε πραγματικά τον κώδικα **create font warning handler**. Η κλάση υλοποιεί το `IWarningCallback` και λαμβάνει ένα αντικείμενο `WarningInfo` για κάθε προειδοποίηση που εγείρει το Aspose.Words.

```csharp
// Step 2: Implement the warning handler that logs substitution details.
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            // This is where we **track missing fonts** and **how to log warnings**
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**Εξήγηση:**  
- `info.Type` μας λέει την κατηγορία της προειδοποίησης. Ενδιαφερόμαστε για το `WarningType.FontSubstitution` επειδή υποδεικνύει μια ελλειπούσα γραμματοσειρά.  
- `info.Description` περιέχει ένα ανθρώπινα αναγνώσιμο μήνυμα όπως *«Η γραμματοσειρά 'Comic Sans MS' δεν βρέθηκε. Αντικαταστάθηκε με 'Arial'.»*  
- Με τη γραφή στο `Console.WriteLine` **log warnings** άμεσα. Σε μια πραγματική εφαρμογή μπορεί να το αντικαταστήσετε με `ILogger`, έναν συγγραφέα αρχείων ή μια υπηρεσία τηλεμετρίας.

> **Συμβουλή:** Αν χρειάζεται να συλλέξετε όλες τις ελλειπούσες γραμματοσειρές για μετέπειτα αναφορά, αποθηκεύστε το `info.Description` σε μια `List<string>` αντί να το εκτυπώνετε.

## Step 3: Load the Document Using the Configured LoadOptions  

Με το callback σε θέση, η φόρτωση ενός εγγράφου θα ενεργοποιεί αυτόματα τον διαχειριστή μας κάθε φορά που λείπει μια γραμματοσειρά.

```csharp
// Step 3: Load the document using the configured LoadOptions.
Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

**Τι θα δείτε:**  
Η εκτέλεση του προγράμματος εκτυπώνει κάτι παρόμοιο με:

```
Font substitution detected: Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

Αυτή η γραμμή επιβεβαιώνει ότι έχετε εντοπίσει επιτυχώς **detect missing fonts** και τώρα **track missing fonts** σε πραγματικό χρόνο.

## Step 4: Verify the Handler Works with Different Scenarios  

Είναι εύκολο να υποθέσετε ότι ο διαχειριστής λειτουργεί μόνο για αρχεία DOCX, αλλά το Aspose.Words υποστηρίζει πολλές μορφές. Δοκιμάστε να φορτώσετε ένα PDF που αναφέρει ενσωματωμένη γραμματοσειρά ή ένα παλαιότερο αρχείο `.doc`. Το ίδιο callback ενεργοποιείται για οποιαδήποτε μορφή περνάει από τη διαδικασία επίλυσης γραμματοσειρών.

```csharp
// Loading a PDF that uses an unavailable font
Document pdfDoc = new Document("MissingFont.pdf", loadOptions);
```

Αν το PDF αναφέρει μια γραμματοσειρά που δεν είναι εγκατεστημένη, θα δείτε την ίδια έξοδο στην κονσόλα. Αυτό δείχνει ότι η λύση **create font warning handler** είναι ανεξάρτητη από τη μορφή.

## Step 5: Extending the Handler – Logging to a File  

Η έξοδος στην κονσόλα είναι χρήσιμη για demos, αλλά ο κώδικας παραγωγής συνήθως γράφει σε αρχείο καταγραφής. Εδώ είναι μια γρήγορη τροποποίηση.

```csharp
using System.IO;

class FontWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] {info.Description}";
            // Append to the log file
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}
```

Τώρα κάθε φορά που αντικαθίσταται μια γραμματοσειρά, το μήνυμα προστίθεται στο `font-warnings.log`. Αυτό ικανοποιεί το τμήμα **how to log warnings** της εργασίας και σας παρέχει ένα μόνιμο αρχείο ελέγχου.

## Step 6: Putting It All Together – Full, Runnable Example  

Παρακάτω είναι το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε‑επικολλήσετε σε μια εφαρμογή console. Δεν λείπουν κομμάτια· απλώς αντικαταστήστε τη διαδρομή αρχείου με το δικό σας έγγραφο.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 2: Implement the warning handler
    class FontWarningHandler : IWarningCallback
    {
        private readonly string _logPath = "font-warnings.log";

        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                string message = $"[{DateTime.Now}] {info.Description}";
                Console.WriteLine(message);               // Immediate feedback
                File.AppendAllText(_logPath, message + Environment.NewLine);
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 1: Configure LoadOptions with our handler
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningHandler()
            };

            // Step 3: Load a document that likely has missing fonts
            string docPath = @"YOUR_DIRECTORY\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // Optional: Do something with the document (e.g., save as PDF)
            doc.Save("output.pdf");
            Console.WriteLine("Document processed. Check console and font-warnings.log for any font substitutions.");
        }
    }
}
```

**Αναμενόμενο αποτέλεσμα:**  

- Η κονσόλα εκτυπώνει κάθε γραμμή αντικατάστασης.  
- Το `font-warnings.log` περιέχει τώρα μια καταγραφή με χρονική σήμανση κάθε συμβάντος ελλειπούσας γραμματοσειράς.  
- Το αρχείο `output.pdf` δημιουργείται χρησιμοποιώντας τις αντικατεστημένες γραμματοσειρές, εξασφαλίζοντας ότι η μετατροπή ολοκληρώνεται ακόμη και όταν οι αρχικές γραμματοσειρές δεν είναι διαθέσιμες.

## Common Questions & Edge Cases  

| Ερώτηση | Απάντηση |
|----------|--------|
| *Τι γίνεται αν θέλω να αγνοήσω ορισμένες γραμματοσειρές;* | Μέσα στο `Warning`, ελέγξτε το `info.Description` για το όνομα της γραμματοσειράς και κάντε `return;` νωρίς για τις γραμματοσειρές που θεωρείτε αποδεκτές. |
| *Θα ενεργοποιηθεί ο διαχειριστής για ενσωματωμένες γραμματοσειρές;* | Όχι — οι ενσωματωμένες γραμματοσειρές είναι πάντα διαθέσιμες στο έγγραφο, επομένως δεν εμφανίζεται προειδοποίηση αντικατάστασης. |
| *Μπορώ να καταγράψω άλλους τύπους προειδοποιήσεων (π.χ., προβλήματα ανάλυσης εικόνας);* | Απολύτως. Αφαιρέστε την προϋπόθεση `if (info.Type == WarningType.FontSubstitution)` ή προσθέστε επιπλέον μπλοκ `if` για το `WarningType.ImageResolution`. |
| *Είναι ο διαχειριστής thread‑safe;* | Η προεπιλεγμένη υλοποίηση που φαίνεται γράφει σε αρχείο χωρίς συγχρονισμό. Για σενάρια πολλαπλών νημάτων, τυλίξτε τις εγγραφές σε αρχείο με ένα lock ή χρησιμοποιήστε έναν ταυτόχρονο logger. |

## Next Steps  

Τώρα που ξέρετε **how to log warnings** για ελλειπούσες γραμματοσειρές, ίσως θέλετε να:

- **Ανιχνεύσετε ελλειπούσες γραμματοσειρές** κατά τη διάρκεια μιας διαδικασίας μαζικής εισαγωγής και δημιουργήσετε μια σύνοψη αναφοράς.  
- **Καταγράψετε ελλειπούσες γραμματοσειρές** σε πολλά έγγραφα και στείλετε ειδοποίηση email όταν μια συγκεκριμένη γραμματοσειρά εμφανίζεται συχνά.  
- **Ενσωματώσετε με σύστημα παρακολούθησης** (π.χ., Azure Application Insights) για να εμφανίζετε τις τάσεις αντικατάστασης γραμματοσειρών με την πάροδο του χρόνου.  

Όλες αυτές οι επεκτάσεις βασίζονται στην ίδια βάση `IWarningCallback` που δημιουργήσαμε.

---

*Καλό κώδικα! Αν αντιμετωπίσετε ιδιαιτερότητες — ίσως ένας προσαρμοσμένος φάκελος γραμματοσειρών ή ένας δικτυακός κοινόχρηστος πόρος — αφήστε ένα σχόλιο παρακάτω. Η κοινότητα (και εγώ) είμαστε πάντα πρόθυμοι να σας βοηθήσουμε να βελτιώσετε τη στρατηγική προειδοποίησης γραμματοσειρών.* 

![παράδειγμα δημιουργίας διαχειριστή προειδοποιήσεων γραμματοσειρών](image-placeholder.png "παράδειγμα δημιουργίας διαχειριστή προειδοποιήσεων γραμματοσειρών")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}