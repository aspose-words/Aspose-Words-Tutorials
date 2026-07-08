---
category: general
date: 2026-07-03
description: Αποθήκευση docx ως pdf και αυτόματη ανίχνευση ελλιπών γραμματοσειρών
  με το Aspose.Words – ένας οδηγός βήμα‑βήμα για τη μετατροπή του Word σε PDF και
  την παρακολούθηση προβλημάτων γραμματοσειρών.
draft: false
keywords:
- save docx as pdf
- convert word to pdf
- extract font info
- detect missing fonts
- track missing fonts
language: el
og_description: Αποθηκεύστε docx ως pdf και εντοπίστε αυτόματα τις ελλιπείς γραμματοσειρές
  με το Aspose.Words – ένας πλήρης οδηγός για τη μετατροπή του Word σε PDF και την
  παρακολούθηση προβλημάτων γραμματοσειρών.
og_title: Αποθήκευση docx ως pdf & εντοπισμός ελλιπών γραμματοσειρών με το Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Save docx as pdf and automatically detect missing fonts with Aspose.Words
    – a step‑by‑step guide to convert Word to PDF and track font issues.
  headline: Save docx as pdf & detect missing fonts using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- PDF conversion
title: Αποθήκευση docx ως pdf & ανίχνευση ελλιπών γραμματοσειρών με το Aspose.Words
url: /el/net/working-with-fonts/save-docx-as-pdf-detect-missing-fonts-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Αποθήκευση docx ως pdf & ανίχνευση ελλιπών γραμματοσειρών με Aspose.Words

Έχετε χρειαστεί ποτέ να **αποθηκεύσετε docx ως pdf** αλλά να ανησυχείτε ότι το παραγόμενο PDF μπορεί σιωπηρά να αντικαταστήσει γραμματοσειρές που δεν έχετε; Δεν είστε μόνοι. Σε πολλά επιχειρησιακά pipelines, μια προειδοποίηση για ελλιπής γραμματοσειρά είναι η διαφορά μεταξύ ενός επαγγελματικού αναφοράς και ενός ακατάστατου κειμένου.  

Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα από ένα συγκεκριμένο, end‑to‑end παράδειγμα που **μετατρέπει Word σε PDF**, εξάγει πληροφορίες γραμματοσειρών και **ανιχνεύει ελλιπείς γραμματοσειρές** ώστε να μπορείτε να **παρακολουθείτε τις ελλιπείς γραμματοσειρές** πριν γίνουν πρόβλημα. Ο κώδικας είναι έτοιμος‑για‑εκτέλεση, η λογική εξηγείται λεπτομερώς, και θα αποκτήσετε ένα επαναχρησιμοποιήσιμο μοτίβο για οποιοδήποτε .NET project.

> **Τι θα πάρετε:** μια λειτουργική εφαρμογή C# console που φορτώνει ένα `.docx`, συνδέει μια callback προειδοποίησης, αποθηκεύει το αρχείο ως PDF και εκτυπώνει κάθε συμβάν αντικατάστασης γραμματοσειράς στην κονσόλα.

---

## Προαπαιτούμενα

- .NET 6 SDK (ή οποιαδήποτε πρόσφατη έκδοση .NET) – παλαιότερα frameworks λειτουργούν επίσης, αλλά θα στοχεύσουμε στο .NET 6 για σύγχρονη σύνταξη.  
- Άδεια Aspose.Words for .NET (ή ένα δωρεάν κλειδί αξιολόγησης).  
- Ένα δείγμα εγγράφου Word που σκόπιμα αναφέρει μια γραμματοσειρά που δεν έχετε εγκατεστημένη (π.χ., “Comic Sans MS” σε Linux CI runner).  
- Visual Studio 2022, VS Code ή το αγαπημένο σας IDE.

Δεν απαιτούνται εξωτερικά πακέτα NuGet εκτός από το Aspose.Words.

---

## Αποθήκευση docx ως pdf – Ρύθμιση Aspose.Words

Το πρώτο βήμα είναι να αναφερθείτε στο assembly του Aspose.Words και να δημιουργήσετε ένα αντικείμενο `Document`. Αυτό το αντικείμενο είναι το σημείο εισόδου για **αποθήκευση docx ως pdf**.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Load the source DOCX – it may contain fonts that are missing on the host machine.
Document doc = new Document(@"C:\Samples\MissingFont.docx");

// Optional: if you have a license, apply it now.
License license = new License();
license.SetLicense(@"C:\Licenses\Aspose.Words.NET.lic");
```

> **Γιατί είναι σημαντικό:** Το `Document` αφηρεί ολόκληρο το αρχείο Word, διαχειριζόμενο τα πάντα από παραγράφους μέχρι ενσωματωμένες εικόνες. Φορτώνοντάς το πρώτα, επιτρέπετε στο Aspose.Words να αναλύσει τους πίνακες γραμματοσειρών, κάτι που αργότερα ενεργοποιεί το σύστημα προειδοποιήσεων για εντοπισμό αντικαταστάσεων.

---

## Σύνδεση callback προειδοποίησης για **ανίχνευση ελλιπών γραμματοσειρών**

Το Aspose.Words παρέχει μια διεπαφή `IWarningCallback`. Υλοποιήστε την και θα λαμβάνετε ένα αντικείμενο `WarningInfo` για κάθε συμβάν, συμπεριλαμβανομένης της αντικατάστασης γραμματοσειράς.

```csharp
// Attach a custom warning handler that will be invoked during PDF conversion.
doc.WarningCallback = new FontSubstitutionWarningHandler();
```

```csharp
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // This line prints the missing‑font details to the console.
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}
```

> **Εξήγηση:** Η μέθοδος `Warning` καλείται *μία φορά ανά αντικατάσταση*. Η ιδιότητα `Description` περιέχει ένα ανθρώπινα αναγνώσιμο μήνυμα όπως “Font substitution: 'Comic Sans MS' was substituted with 'Arial'”. Φιλτράροντας με `WarningType.FontSubstitution` **παρακολουθούμε τις ελλιπείς γραμματοσειρές** χωρίς να γεμίζει η έξοδος με άσχετες προειδοποιήσεις.

---

## Μετατροπή Word σε PDF – το τελικό βήμα **αποθήκευση docx ως pdf**

Τώρα που η callback είναι ενεργή, η μετατροπή είναι μια εντολή μίας γραμμής:

```csharp
// Save the document as PDF. Any font substitutions trigger the callback above.
doc.Save(@"C:\Output\Result.pdf", SaveFormat.Pdf);
```

Όταν εκτελέσετε το πρόγραμμα, θα δείτε έξοδο παρόμοια με:

```
Font substitution: Font 'Comic Sans MS' was substituted with 'Arial'.
Font substitution: Font 'Papyrus' was substituted with 'Times New Roman'.
```

Αυτή η έξοδος είναι η αναφορά **extract font info**, και μπορείτε να την ανακατευθύνετε σε αρχείο καταγραφής, βάση δεδομένων ή ακόμη και να ενεργοποιήσετε μια ειδοποίηση σε pipeline CI.

---

## Πλήρες, εκτελέσιμο παράδειγμα

Συνδυάζοντας όλα τα παραπάνω, εδώ είναι μια ελάχιστη εφαρμογή console που μπορείτε να αντιγράψετε‑και‑επικολλήσετε στο `Program.cs` και να εκτελέσετε.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace WordToPdfWithFontTracking
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the DOCX that may contain missing fonts.
            Document doc = new Document(@"C:\Samples\MissingFont.docx");

            // 2️⃣ Register the warning handler to capture font substitution events.
            doc.WarningCallback = new FontSubstitutionWarningHandler();

            // 3️⃣ Save as PDF – this triggers the callback for every missing font.
            doc.Save(@"C:\Output\Result.pdf", SaveFormat.Pdf);

            Console.WriteLine("Conversion complete. Check console for font substitution details.");
        }
    }

    // 👇 Custom callback that logs only font‑substitution warnings.
    class FontSubstitutionWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Font substitution: {info.Description}");
            }
        }
    }
}
```

**Αναμενόμενο αποτέλεσμα**

- Το `Result.pdf` εμφανίζεται στο `C:\Output`. Ανοίξτε το – το κείμενο φαίνεται σωστό.
- Η κονσόλα εκτυπώνει μια γραμμή για κάθε ελλιπή γραμματοσειρά, παρέχοντάς σας μια σαφή αναφορά **extract font info**.

---

## Συνηθισμένες παραλλαγές & edge cases

| Σενάριο | Τι να προσαρμόσετε | Γιατί |
|----------|----------------|-----|
| **Πολλαπλά έγγραφα** | Επανάληψη πάνω σε μια συλλογή αρχείων `.docx` και επαναχρησιμοποίηση του ίδιου `FontSubstitutionWarningHandler`. | Διατηρεί τη συνοχή των καταγραφών σε batch jobs. |
| **Καταστολή όλων των προειδοποιήσεων** | Ορίστε `doc.WarningCallback = null;` ή υλοποιήστε τον handler ώστε να αγνοεί τα πάντα. | Χρήσιμο για σενάρια one‑off όπου εμπιστεύεστε τα πηγαία αρχεία. |
| **Ανακατεύθυνση εξόδου σε αρχείο** | Μέσα στη `Warning`, γράψτε στο `File.AppendAllText("font-warnings.log", …)`. | Διευκολύνει τον έλεγχο μεγάλων μετατροπών. |
| **Εκτέλεση σε Linux** | Βεβαιωθείτε ότι έχετε εγκαταστήσει το πακέτο `libgdiplus` για το Aspose.Words ώστε να αποδίδει γραμματοσειρές. | Χωρίς αυτό, μπορεί να εμφανιστούν επιπλέον προειδοποιήσεις αντικατάστασης. |
| **Προσαρμοσμένος φάκελος γραμματοσειρών** | Χρησιμοποιήστε `FontSettings.FontFolders.Add(@"C:\MyFonts");` πριν φορτώσετε το έγγραφο. | Σας επιτρέπει να συμπεριλάβετε ιδιωτικές γραμματοσειρές στην εφαρμογή, μειώνοντας τα περιστατικά ελλιπών γραμματοσειρών. |

---

## Pro συμβουλές & παγίδες

- **Pro tip:** Καταχωρίστε ένα αντικείμενο `FontSettings` με fallback γραμματοσειρά (π.χ., `Arial`) για να εξασφαλίσετε ένα καθορισμένο αποτέλεσμα αντικατάστασης.  
- **Προσοχή:** Αν ξεχάσετε να ορίσετε `doc.WarningCallback` *πριν* το `Save`, τα συμβάντα αντικατάστασης θα χαθούν — χωρίς παρακολούθηση, χωρίς καταγραφές.  
- **Σημείωση απόδοσης:** Η callback προσθέτει αμελητέο φόρτο· το bottleneck παραμένει ο PDF rasterizer, όχι το σύστημα προειδοποιήσεων.  
- **Υπενθύμιση άδειας:** Η δωρεάν έκδοση αξιολόγησης προσθέτει υδατογράφημα σε κάθε PDF. Βεβαιωθείτε ότι η άδειά σας έχει εφαρμοστεί, αλλιώς θα δείτε “Aspose.Words Evaluation” στην πρώτη σελίδα.

---

## Συμπέρασμα

Τώρα έχετε ένα στιβαρό, έτοιμο για παραγωγή μοτίβο για **αποθήκευση docx ως pdf**, **μετατροπή Word σε PDF**, και **ανίχνευση ελλιπών γραμματοσειρών** σε μια αδιάσπαστη ροή. Συνδέοντας μια callback προειδοποίησης μπορείτε να **εξάγετε πληροφορίες γραμματοσειρών**, **παρακολουθείτε ελλιπείς γραμματοσειρές**, και να τροφοδοτήσετε αυτά τα δεδομένα στις διαδικασίες ελέγχου ποιότητας.  

Τι θα κάνετε στη συνέχεια; Δοκιμάστε να προσθέσετε έναν προσαρμοσμένο φάκελο γραμματοσειρών, αυτοματοποιήστε την εισαγωγή των καταγραφών στο Azure Monitor, ή επεκτείνετε τον handler ώστε να ρίχνει εξαιρέσεις για κρίσιμες περιπτώσεις έλλειψης γραμματοσειράς. Η ίδια προσέγγιση λειτουργεί για άλλες μορφές εξόδου (π.χ., XPS, HTML) – απλώς αντικαταστήστε το `SaveFormat.Pdf` με την επιθυμητή τιμή enum.

Καλό coding, και εύχομαι τα PDFs σας να αποδίδουν πάντα με τις γραμματοσειρές που προτίθεστε!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας projects.

- [How to Load DOCX and Detect Missing Fonts – Complete C# Guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)
- [convert word to pdf in C# using Aspose.Words – Guide](/words/english/net/basic-conversions/convert-word-to-pdf-in-c-using-aspose-words-guide/)
- [Save PDF To Word Format (Docx)](/words/english/net/basic-conversions/pdf-to-docx/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}