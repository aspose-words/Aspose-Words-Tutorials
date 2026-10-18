---
category: general
date: 2026-03-16
description: Μάθετε πώς να χρησιμοποιείτε το FontSettings στο Aspose.Words για να
  διαχειρίζεστε τα ελλιπή γραμματοσειρές με χάρη—πλήρης κώδικας, διαχείριση συμβάντων
  και συμβουλές βέλτιστων πρακτικών.
draft: false
keywords:
- how to use fontsettings
- handle missing fonts
- Aspose.Words font substitution
- missing font detection C#
- document loading options
language: el
og_description: Πώς να χρησιμοποιήσετε το FontSettings στο Aspose.Words για να αντιμετωπίσετε
  τις ελλείπουσες γραμματοσειρές—βήμα‑βήμα οδηγός με πλήρες παράδειγμα C# και πρακτικές
  συμβουλές.
og_title: Πώς να χρησιμοποιήσετε το FontSettings για τη διαχείριση ελλιπών γραμματοσειρών
  στο Aspose.Words
tags:
- Aspose.Words
- C#
- Font Management
title: Πώς να χρησιμοποιήσετε το FontSettings για τη διαχείριση ελλειπών γραμματοσειρών
  στο Aspose.Words
url: /el/net/working-with-fonts/how-to-use-fontsettings-to-handle-missing-fonts-in-aspose-wo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να χρησιμοποιήσετε το FontSettings για να διαχειριστείτε τις ελλιπείς γραμματοσειρές στο Aspose.Words

Έχετε αναρωτηθεί ποτέ **πώς να χρησιμοποιήσετε το FontSettings** όταν τα έγγραφα Word σας αναφέρονται σε γραμματοσειρές που δεν είναι εγκατεστημένες στον διακομιστή; Δεν είστε μόνοι. Οι ελλιπείς γραμματοσειρές μπορούν να προκαλέσουν άσχημες εναλλακτικές ή ακόμη και να ρίξουν εξαιρέσεις, και οι περισσότεροι προγραμματιστές απλώς αγνοούν το πρόβλημα μέχρι να εμφανιστεί στην παραγωγή.  

Σε αυτό το tutorial θα σας δείξουμε ακριβώς **πώς να χρησιμοποιήσετε το FontSettings** για να **διαχειριστείτε τις ελλιπείς γραμματοσειρές** στο Aspose.Words, να συλλάβετε λεπτομερείς προειδοποιήσεις και να διασφαλίσετε προβλέψιμη απόδοση του εγγράφου. Στο τέλος θα έχετε ένα έτοιμο δείγμα C#, θα καταλάβετε γιατί κάθε γραμμή είναι σημαντική και θα ξέρετε πώς να προσαρμόσετε τη λύση για μεγαλύτερα έργα.

## Τι καλύπτει αυτός ο οδηγός

- Ρύθμιση **FontSettings** και εγγραφή στο γεγονός `SubstitutionWarning`.  
- Σύνδεση των ρυθμίσεων με `LoadOptions` ώστε να γίνονται σεβαστές κατά τη φόρτωση του εγγράφου.  
- Εκτέλεση δοκιμαστικού εγγράφου που σκόπιμα λείπουν γραμματοσειρές και ανάγνωση της εξόδου της κονσόλας.  
- Συμβουλές για logging, απενεργοποίηση αυτόματης αντικατάστασης και διαχείριση ακραίων περιπτώσεων όπως πολλαπλές ελλιπείς γραμματοσειρές.  

Δεν απαιτείται εξωτερική τεκμηρίωση—όλα όσα χρειάζεστε είναι εδώ.

## Προαπαιτήσεις

- .NET 6+ (ή .NET Framework 4.6.2+).  
- Aspose.Words for .NET 23.9 ή νεότερη (το API που χρησιμοποιούμε είναι σταθερό στις πρόσφατες εκδόσεις).  
- Ένα απλό αρχείο `.docx` που αναφέρει μια γραμματοσειρά που γνωρίζετε ότι δεν είναι εγκατεστημένη (π.χ., *Comic Sans MS* σε Linux container).  

Αυτό είναι όλο—δεν χρειάζονται επιπλέον πακέτα NuGet εκτός από το Aspose.Words.

## Γιατί η διαχείριση ελλιπών γραμματοσειρών είναι σημαντική

Όταν ένα έγγραφο αναφέρει μια γραμματοσειρά που το runtime δεν μπορεί να βρει, το Aspose.Words αντικαθιστά αυτόματα το πιο κοντινό αντίστοιχο. Αυτή η αντικατάσταση είναι συχνά αποδεκτή, αλλά μερικές φορές χρειάζεται να **καταγράψετε** ποιες γραμματοσειρές λείπουν (για συμμόρφωση) ή να **αποτρέψετε** εντελώς την αντικατάσταση (π.χ., για PDFs με συγκεκριμένο brand). Με την προσέγγιση του `FontSettings.SubstitutionWarning` αποκτάτε πλήρη ορατότητα και έλεγχο.

## Βήμα 1: Δημιουργία FontSettings και εγγραφή στο γεγονός Substitution‑Warning

Το πρώτο βήμα είναι η δημιουργία ενός αντικειμένου `FontSettings`. Αυτό το αντικείμενο περιέχει όλες τις ρυθμίσεις που αφορούν τις γραμματοσειρές για τη βιβλιοθήκη. Το κρίσιμο μέρος είναι η σύνδεση του γεγονότος `SubstitutionWarning`, το οποίο ενεργοποιείται **κάθε φορά** που το Aspose.Words δεν μπορεί να εντοπίσει τη ζητούμενη γραμματοσειρά.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1 – Initialise FontSettings and listen for missing‑font warnings
FontSettings fontSettings = new FontSettings();

// The lambda receives detailed info about the missing font and the chosen substitute.
fontSettings.SubstitutionWarning += (sender, e) =>
{
    // e.MissingFontName  → the name Aspose.Words tried to load.
    // e.SubstitutedFontName → the font that was actually used instead.
    // e.WarningType → the enum describing why the warning was raised.
    Console.WriteLine($"Missing font: {e.MissingFontName}");
    Console.WriteLine($"Substituted with: {e.SubstitutedFontName}");
    Console.WriteLine($"Reason: {e.WarningType}");
};
```

**Γιατί είναι σημαντικό:**  
- **Ορατότητα:** Μάθετε αμέσως ποιες γραμματοσειρές λείπουν.  
- **Αξιοπιστία:** Η κονσόλα (ή ένας logger) μπορεί να ανακατευθυνθεί σε αρχείο για αναφορές συμμόρφωσης.  
- **Έλεγχος:** Αργότερα μπορείτε να αποφασίσετε να αντικαταστήσετε την αυτόματη αντικατάσταση με μια προσαρμοσμένη γραμματοσειρά της επιλογής σας.

> **Pro tip:** Αν προτιμάτε ένα πλαίσιο logging (Serilog, NLog κ.λπ.), αντικαταστήστε τις κλήσεις `Console.WriteLine` με `logger.Information(...)`.

## Βήμα 2: Σύνδεση FontSettings με LoadOptions

`LoadOptions` είναι το μέσο που λέει στο Aspose.Words πώς να αντιμετωπίσει το αρχείο κατά τη φάση φόρτωσης. Αναθέτοντας το αντικείμενο `FontSettings`, εξασφαλίζετε ότι ο χειριστής προειδοποιήσεων είναι ενεργός *πριν* γίνει η ανάλυση του περιεχομένου.

```csharp
// Step 2 – Bind FontSettings to LoadOptions so the loader knows about our event handler
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

**Γιατί είναι σημαντικό:**  
- Αν φορτώσετε ένα έγγραφο χωρίς να περάσετε `LoadOptions`, ενεργοποιείται η προεπιλεγμένη διαχείριση γραμματοσειρών και θα χάσετε τις προειδοποιήσεις.  
- Αυτή η προσέγγιση σας επιτρέπει επίσης να ρυθμίσετε άλλες συμπεριφορές φόρτωσης (π.χ., προστασία με κωδικό) στο ίδιο αντικείμενο.

## Βήμα 3: Φόρτωση του εγγράφου με τις ρυθμισμένες επιλογές

Τώρα διαβάζουμε το αρχείο Word. Η διαδρομή μπορεί να είναι απόλυτη ή σχετική· το Aspose.Words θα σεβαστεί τα `LoadOptions` που μόλις προετοιμάσαμε.

```csharp
// Step 3 – Load the document while applying our FontSettings
string docPath = @"YOUR_DIRECTORY/MissingFonts.docx";   // <-- adjust to your environment
Document document = new Document(docPath, loadOptions);
```

Αν το έγγραφο περιέχει μια γραμματοσειρά που δεν είναι εγκατεστημένη, το γεγονός `SubstitutionWarning` ενεργοποιείται και θα δείτε έξοδο παρόμοια με το παρακάτω παράδειγμα.

### Αναμενόμενη έξοδος κονσόλας

```
Missing font: Comic Sans MS
Substituted with: Arial
Reason: FontSubstitution
```

Η ακριβής αντικατάσταση μπορεί να διαφέρει ανάλογα με την αλυσίδα εναλλακτικών γραμματοσειρών του λειτουργικού συστήματος, αλλά το **όνομα της ελλιπούσας γραμματοσειράς** θα αναφέρεται πάντα.

## Βήμα 4: Επαλήθευση του αποτελέσματος (Προαιρετική απόδοση)

Συχνά θέλετε να βεβαιωθείτε ότι το έγγραφο εξακολουθεί να φαίνεται σωστό μετά την αντικατάσταση. Ένας γρήγορος τρόπος είναι να το αποθηκεύσετε ως PDF και να ανοίξετε το αποτέλεσμα.

```csharp
// Optional: Save as PDF to visually confirm the substitution
document.Save(@"OUTPUT/Result.pdf", SaveFormat.Pdf);
Console.WriteLine("Document saved as PDF – check the rendering.");
```

Αν χρειάζεται να **αποτρέψετε** εντελώς την αντικατάσταση, ορίστε `FontSettings.SubstitutionSettings.TableSubstitution = false` πριν από τη φόρτωση. Τότε το Aspose.Words θα ρίξει εξαίρεση για ελλιπείς γραμματοσειρές, την οποία μπορείτε να πιάσετε και να διαχειριστείτε.

```csharp
// Disable automatic substitution – will raise an exception on missing fonts
fontSettings.SubstitutionSettings.TableSubstitution = false;
```

## Πλήρες λειτουργικό παράδειγμα

Παρακάτω βρίσκεται το πλήρες, έτοιμο‑για‑εκτέλεση πρόγραμμα. Επικολλήστε το σε μια εφαρμογή console, προσαρμόστε τη διαδρομή του αρχείου και πατήστε **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSettingsDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create FontSettings and hook the warning event
            FontSettings fontSettings = new FontSettings();
            fontSettings.SubstitutionWarning += (sender, e) =>
            {
                Console.WriteLine($"Missing font: {e.MissingFontName}");
                Console.WriteLine($"Substituted with: {e.SubstitutedFontName}");
                Console.WriteLine($"Reason: {e.WarningType}");
            };

            // 2️⃣ Attach FontSettings to LoadOptions
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings
                // Uncomment the next line to *disable* substitution and force an exception
                // , FontSettings = { SubstitutionSettings = { TableSubstitution = false } }
            };

            // 3️⃣ Load the document
            string docPath = @"YOUR_DIRECTORY/MissingFonts.docx";
            Document doc = new Document(docPath, loadOptions);

            // 4️⃣ (Optional) Save as PDF to see the visual result
            doc.Save(@"OUTPUT/Result.pdf", SaveFormat.Pdf);
            Console.WriteLine("Processing complete. Check the console for missing‑font warnings.");
        }
    }
}
```

### Τι να περιμένετε

- Η κονσόλα εκτυπώνει κάθε ελλιπής γραμματοσειρά μαζί με την επιλεγμένη αντικατάσταση.  
- Το παραγόμενο PDF (αν διατηρήσατε την προαιρετική αποθήκευση) εμφανίζει το έγγραφο χρησιμοποιώντας τη γραμματοσειρά εναλλακτική, διασφαλίζοντας την ακεραιότητα της διάταξης.

## Συχνές ερωτήσεις & Ακραίες περιπτώσεις

| Ερώτηση | Απάντηση |
|----------|--------|
| **Τι γίνεται αν λείπουν πολλές γραμματοσειρές;** | Το γεγονός ενεργοποιείται μία φορά ανά ελλιπής γραμματοσειρά, οπότε θα λάβετε ξεχωριστή γραμμή καταγραφής για κάθε μία. |
| **Μπορώ να αντικαταστήσω την εναλλακτική με μια προσαρμοσμένη γραμματοσειρά;** | Ναι. Μέσα στον χειριστή του γεγονότος μπορείτε να καλέσετε `e.SubstitutedFont = new FontInfo("MyCustomFont")`. |
| **Εγείρεται η προειδοποίηση για ενσωματωμένες γραμματοσειρές που δεν φορτώνονται;** | Απόλυτα—είτε η γραμματοσειρά είναι εξωτερική είτε ενσωματωμένη, η προειδοποίηση παραμένει η ίδια. |
| **Πρέπει να απελευθερώσω το `Document`;** | Το `Document` υλοποιεί το `IDisposable`. Τυλίξτε τη χρήση του σε ένα `using` block αν φορτώνετε πολλά αρχεία σε βρόχο. |
| **Θα λειτουργήσει αυτό σε Linux containers;** | Εφόσον το Aspose.Words μπορεί να εντοπίσει τις συστημικές γραμματοσειρές (π.χ., μέσω `fontconfig`), ο ίδιος μηχανισμός γεγονότων λειτουργεί. |

## Καλές πρακτικές & Pro Tips

- **Κεντρικοποίηση logging:** Δημιουργήστε μια βοηθητική μέθοδο που γράφει τόσο στην κονσόλα όσο και σε ένα μόνιμο αρχείο καταγραφής.  
- **Επεξεργασία σε batch:** Όταν μετατρέπετε δεκάδες έγγραφα, επαναχρησιμοποιήστε ένα ενιαίο αντικείμενο `FontSettings` για να αποφύγετε επαναλαμβανόμενες εγγραφές γεγονότων.  
- **Απόδοση:** Οι προειδοποιήσεις αντικατάστασης προσθέτουν αμελητέο κόστος, αλλά αν επεξεργάζεστε χιλιάδες αρχεία, σκεφτείτε να τις απενεργοποιήσετε μετά τον έλεγχο του συνόλου γραμματοσειρών.  
- **Ασφάλεια έκδοσης:** Το API `SubstitutionWarning` είναι σταθερό από το Aspose.Words 16.0, οπότε μπορείτε να βασιστείτε σε αυτό για μελλοντικές αναβαθμίσεις.

## Συμπέρασμα

Διασχίσαμε **πώς να χρησιμοποιήσετε το FontSettings** στο Aspose.Words για **να διαχειριστείτε τις ελλιπείς γραμματοσειρές** με κομψό τρόπο. Δημιουργώντας ένα αντικείμενο `FontSettings`, εγγραφόμενοι στο `SubstitutionWarning` και φορτώνοντας έγγραφα μέσω `LoadOptions`, αποκτάτε πλήρη ορατότητα στα προβλήματα γραμματοσειρών και μπορείτε να αποφασίσετε αν θα καταγράψετε, αντικαταστήσετε ή διακόψετε την επεξεργασία.  

Από την απλή έξοδο στην κονσόλα μέχρι την προσαρμοσμένη λογική αντικατάστασης, το πρότυπο κλιμακώνεται σε μεγάλες παρτίδες εγγράφων, διασφαλίζοντας ότι το αποτέλεσμα παραμένει συνεπές και ελεγχόμενο.

**Επόμενα βήματα:**  

- Εξερευνήστε **προσαρμοσμένη αντικατάσταση γραμματοσειρών** ορίζοντας `e.SubstitutedFont` μέσα στο γεγονός.  
- Συνδυάστε αυτήν την προσέγγιση με **απόδοση εγγράφου σε εικόνες** για δημιουργία μικρογραφιών.  
- Ρίξτε μια ματιά στο **Aspose.PDF** αν χρειάζεται να ενσωματώσετε τις αντικατεστημένες γραμματοσειρές απευθείας στο τελικό PDF για πλήρη φορητότητα.

Καλή προγραμματιστική δουλειά, και να μην αντιμετωπίζετε ποτέ ξανά ένα άγριο πρόβλημα ελλιπών γραμματοσειρών!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}