---
category: general
date: 2026-04-10
description: Πώς να χρησιμοποιήσετε το LoadOptions στο Aspose.Words για να καταγράψετε
  προειδοποιήσεις αντικατάστασης γραμματοσειρών κατά τη φόρτωση εγγράφων. Μάθετε μια
  λύση βήμα‑βήμα σε C# με πλήρες παράδειγμα κώδικα.
draft: false
keywords:
- how to use loadoptions
- warningcallback
- font substitution warning
- aspose.words loadoptions example
- c# document loading
language: el
og_description: Πώς να χρησιμοποιήσετε το LoadOptions στο Aspose.Words για να καταγράψετε
  προειδοποιήσεις αντικατάστασης γραμματοσειρών κατά τη φόρτωση εγγράφων. Αυτός ο
  οδηγός σας καθοδηγεί βήμα-βήμα σε μια πλήρη υλοποίηση C#.
og_title: Πώς να χρησιμοποιήσετε το LoadOptions στο Aspose.Words – Πλήρης οδηγός C#
tags:
- Aspose.Words
- C#
- Document Processing
- Font Management
title: Πώς να χρησιμοποιήσετε το LoadOptions στο Aspose.Words – Πλήρης οδηγός C#
url: /el/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Χρησιμοποιήσετε το LoadOptions στο Aspose.Words – Πλήρης Οδηγός C#

Η χρήση του LoadOptions στο Aspose.Words αποτελεί συχνό εμπόδιο όταν χρειάζεστε ακριβή έλεγχο της φόρτωσης εγγράφων. Σε αυτό το tutorial θα δείξουμε ακριβώς **πώς να χρησιμοποιήσετε το LoadOptions** για να εντοπίζετε προειδοποιήσεις αντικατάστασης γραμματοσειρών και να αντιδράτε σε αυτές σε C#.  

Αν έχετε ανοίξει ποτέ ένα DOCX που αναφερόταν σε μια γραμματοσειρά που λείπει και αναρωτηθήκατε γιατί το αποτέλεσμα φαίνεται παράξενο, βρίσκεστε στο σωστό μέρος. Θα περάσουμε από όλη τη διαδικασία, από τη δημιουργία μιας στιγμής `LoadOptions` μέχρι την εκτύπωση των λεπτομερειών προειδοποίησης στην κονσόλα. Στο τέλος θα έχετε ένα έτοιμο τμήμα κώδικα που μπορείτε να ενσωματώσετε σε οποιοδήποτε .NET project.

## Τι Θα Μάθετε

- Γιατί το `LoadOptions` είναι σημαντικό για αξιόπιστη εισαγωγή εγγράφων.  
- Πώς να συνδέσετε ένα **WarningCallback** που παρακολουθεί ειδικά τις **προειδοποιήσεις αντικατάστασης γραμματοσειρών**.  
- Τον ακριβή κώδικα που απαιτείται για τη φόρτωση ενός αρχείου Word με αυτές τις επιλογές ενεργοποιημένες.  
- Συμβουλές για τη διαχείριση ακραίων περιπτώσεων, όπως έγγραφα που περιέχουν πολλές ελλιπείς γραμματοσειρές.  

Δεν απαιτείται εξωτερική τεκμηρίωση — όλα όσα χρειάζεστε είναι εδώ.

## Προαπαιτούμενα

| Απαίτηση | Αιτία |
|-------------|--------|
| .NET 6.0 ή νεότερο | Παρέχει το runtime για τη σύνταξη C# 10 που χρησιμοποιείται στα παραδείγματα. |
| Aspose.Words for .NET (τελευταία έκδοση) | Η βιβλιοθήκη που περιλαμβάνει το `LoadOptions` και την υποδομή προειδοποιήσεων. |
| Ένα αρχείο DOCX που μπορεί να αναφέρει γραμματοσειρές που δεν έχετε εγκαταστήσει | Για να δείτε το callback προειδοποίησης σε δράση. |
| Visual Studio 2022 (ή οποιοδήποτε IDE προτιμάτε) | Κάνει το debugging και το testing πιο απλό. |

Αν έχετε ήδη όλα αυτά, υπέροχα — ας ξεκινήσουμε.

## Βήμα 1 – Δημιουργία Αντικειμένου LoadOptions και Σύνδεση του WarningCallback

Το πρώτο πράγμα που κάνετε όταν **πώς να χρησιμοποιήσετε το LoadOptions** είναι να το δημιουργήσετε. Το κρίσιμο μέρος είναι η ανάθεση ενός delegate στο `WarningCallback`. Αυτό το delegate ενεργοποιείται κάθε φορά που το Aspose.Words συναντά μια κατάσταση που θέλει να σας ενημερώσει — κυρίως, όταν λείπει μια γραμματοσειρά.

```csharp
using System;
using Aspose.Words;

// Step 1: Build LoadOptions with a warning listener.
LoadOptions loadOptions = new LoadOptions
{
    // The lambda receives the sender (unused) and a WarningInfo object.
    WarningCallback = (sender, args) =>
    {
        // We'll filter for font‑substitution warnings later.
        if (args.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution: {args.Description}");
        }
    }
};
```

**Γιατί είναι σημαντικό:** Χωρίς το callback, το Aspose.Words αντικαθιστά σιωπηλά τις ελλιπείς γραμματοσειρές με προεπιλεγμένες, και μπορεί να μην παρατηρήσετε ποτέ τη μεταβολή στην εμφάνιση. Με την καταγραφή ενός `WarningCallback`, λαμβάνετε σε πραγματικό χρόνο ένα log κάθε αντικατάστασης, κάτι απαραίτητο για pipelines εγγράφων με διασφάλιση ποιότητας.

## Βήμα 2 – Αντίδραση Μόνο σε Προειδοποιήσεις Αντικατάστασης Γραμματοσειρών

Μπορεί να αναρωτιέστε αν το callback θα σας κατακλύσει με άσχετες προειδοποιήσεις (π.χ. παρωχημένες λειτουργίες). Η απάντηση είναι *ναι* — αλλά μπορούμε να τις φιλτράρουμε. Στο παραπάνω απόσπασμα κώδικα ελέγχουμε ήδη `args.WarningType == WarningType.FontSubstitution`. Αυτή η γραμμή είναι η **προειδοποίηση αντικατάστασης γραμματοσειράς**, μια δευτερεύουσα συνθήκη που κρατά το output εστιασμένο.

Αν χρειαστεί ποτέ να διαχειριστείτε άλλους τύπους προειδοποιήσεων, απλώς επεκτείνετε το μπλοκ `if`:

```csharp
if (args.WarningType == WarningType.FontSubstitution)
{
    // Existing handling…
}
else if (args.WarningType == WarningType.UnknownFileFormat)
{
    Console.WriteLine($"❓ Unknown format: {args.Description}");
}
```

Αυτό το μοτίβο δείχνει πόσο ευέλικτος είναι ο μηχανισμός **warningcallback**, επιτρέποντάς σας να προσαρμόζετε τις αντιδράσεις ακριβώς στις περιπτώσεις που σας ενδιαφέρουν.

## Βήμα 3 – Φόρτωση του Εγγράφου Χρησιμοποιώντας τις Διαμορφωμένες LoadOptions

Τώρα που ο ακροατής είναι έτοιμος, το τελευταίο βήμα είναι να περάσετε την παρουσία `LoadOptions` στον κατασκευαστή `Document`. Αυτή είναι η στιγμή που το **παράδειγμα Aspose.Words LoadOptions** λάμπει πραγματικά.

```csharp
// Step 3: Load the DOCX while the warning callback is active.
try
{
    Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
    Console.WriteLine("✅ Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"🚨 Failed to load document: {ex.Message}");
}
```

**Τι θα δείτε:** Αν το DOCX αναφέρει μια γραμματοσειρά που δεν είναι εγκατεστημένη στο μηχάνημα, η κονσόλα θα εμφανίσει μια γραμμή όπως:

```
⚠️ Font substitution: Font 'Calibri Light' has been substituted with 'Arial'.
✅ Document loaded successfully.
```

Αυτή η έξοδος επιβεβαιώνει ότι έχετε επιτυχώς **πώς να χρησιμοποιήσετε το LoadOptions** για την παρακολούθηση προβλημάτων γραμματοσειρών.

## Πλήρες Παράδειγμα Εργασίας (Έτοιμο για Αντιγραφή‑Επικόλληση)

Παρακάτω είναι το πλήρες πρόγραμμα που μπορείτε να μεταγλωττίσετε και να τρέξετε αμέσως. Συνδυάζει και τα τρία βήματα, προσθέτει μερικές ευχάριστες λεπτομέρειες (όπως ένα φιλικό banner) και δείχνει διαχείριση σφαλμάτων.

```csharp
using System;
using Aspose.Words;

class Program
{
    static void Main()
    {
        Console.WriteLine("=== Aspose.Words LoadOptions Demo ===");

        // 1️⃣ Create LoadOptions with a warning callback.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = (sender, args) =>
            {
                if (args.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ Font substitution: {args.Description}");
                }
            }
        };

        // 2️⃣ Attempt to load the document.
        try
        {
            // Replace the path with your own file that may contain missing fonts.
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
            Console.WriteLine("✅ Document loaded without fatal errors.");

            // Optional: Do something with the document, e.g., save as PDF.
            // doc.Save("output.pdf");
        }
        catch (Exception e)
        {
            Console.WriteLine($"🚨 Error: {e.Message}");
        }

        Console.WriteLine("=== End of Demo ===");
    }
}
```

### Αναμενόμενη Έξοδος

Η εκτέλεση του προγράμματος σε ένα μηχάνημα που δεν διαθέτει τη γραμματοσειρά που αναφέρεται στο `input.docx` δίνει κάτι παρόμοιο με:

```
=== Aspose.Words LoadOptions Demo ===
⚠️ Font substitution: Font 'Times New Roman' has been substituted with 'Arial'.
✅ Document loaded without fatal errors.
=== End of Demo ===
```

Αν όλες οι γραμματοσειρές είναι παρούσες, θα δείτε μόνο τα μηνύματα επιτυχίας — δεν εμφανίζονται γραμμές προειδοποίησης.

## Συνηθισμένα Λάθη & Επαγγελματικές Συμβουλές

- **Λάθος:** Ξέχνατε να ορίσετε το `WarningCallback`. Ο κώδικας θα φορτώσει ακόμη, αλλά θα χάσετε τις λεπτομέρειες αντικατάστασης.  
  **Συμβουλή:** Πάντα να αναθέτετε το callback αμέσως μετά τη δημιουργία του `LoadOptions`; είναι φθηνό και αποδίδει αργότερα.

- **Λάθος:** Χρήση σχετικού μονοπατιού που δείχνει σε λάθος φάκελο.  
  **Συμβουλή:** Χρησιμοποιήστε `Path.Combine(Environment.CurrentDirectory, "input.docx")` για πιο αξιόπιστη αναζήτηση αρχείου.

- **Λάθος:** Υποθέτετε ότι η προειδοποίηση θα σταματήσει τη φόρτωση.  
  **Συμβουλή:** Οι προειδοποιήσεις αντικατάστασης γραμματοσειρών είναι *πληροφοριακές*· δεν ακυρώνουν τη φόρτωση. Αν χρειάζεστε αυστηρότερη επικύρωση, ρίξτε εξαίρεση μέσα στο callback όταν συμβεί αντικατάσταση.

- **Λάθος:** Εκτέλεση σε διακομιστή χωρίς εγκατεστημένες γραμματοσειρές (π.χ. ελαφρύ Docker image).  
  **Συμβουλή:** Προ‑εγκαταστήστε τις απαιτούμενες γραμματοσειρές ή συμπεριλάβετε τες στην εφαρμογή σας, και επαληθεύστε με το callback ότι δεν συμβαίνουν αντικαταστάσεις στην παραγωγή.

## Πότε να Χρησιμοποιήσετε LoadOptions έναντι Ελέγχου Μετά τη Φόρτωση

Μπορεί να αναρωτηθείτε, “Γιατί να μην ελέγξω το έγγραφο μετά τη φόρτωση;” Η απάντηση κρύβεται στην απόδοση και την ορθότητα. Με την αντιμετώπιση των προειδοποιήσεων **κατά τη διάρκεια** της φόρτωσης, εντοπίζετε προβλήματα νωρίς — πριν γίνουν υπολογισμοί διάταξης ή μετατροπές σε PDF. Αυτό είναι ιδιαίτερα πολύτιμο σε δέσμες επεξεργασίας όπου κάθε επιπλέον βήμα προσθέτει χρόνο.

## Επέκταση του Παραδείγματος: Αποθήκευση Αναφοράς Όλων των Αντικατασταμένων Γραμματοσειρών

Αν χρειάζεστε μόνιμο αρχείο (π.χ. για συμμόρφωση), τροποποιήστε το callback ώστε να συλλέγει τα μηνύματα σε λίστα και να τα γράφει σε αρχείο μετά τη φόρτωση:

```csharp
var substitutions = new List<string>();

loadOptions.WarningCallback = (s, a) =>
{
    if (a.WarningType == WarningType.FontSubstitution)
    {
        substitutions.Add(a.Description);
        Console.WriteLine($"⚠️ {a.Description}");
    }
};

// After loading:
File.WriteAllLines("font-substitutions.txt", substitutions);
```

Τώρα έχετε τόσο ανατροφοδότηση στην κονσόλα όσο και ένα ανθεκτικό log.

## Σχετικά Θέματα που Μπορείτε να Εξερευνήσετε Στη Σειρά

- **Πώς να ενσωματώσετε προσαρμοσμένες γραμματοσειρές στο Aspose.Words** — εξαλείφει εντελώς την αντικατάσταση.  
- **Χρήση LoadOptions για περιορισμό μεγέθους εγγράφου** — βοηθά στην προστασία από κακόβουλα μεγάλα αρχεία.  
- **Μετατροπή Word σε PDF με διατηρημένη τυπογραφία** — ταιριάζει τέλεια με την προσέγγιση του warning‑callback.  

Κάθε ένα από αυτά βασίζεται στο θεμέλιο που μόλις δημιουργήσατε με το `LoadOptions`.

## Συμπέρασμα

Καλύψαμε **πώς να χρησιμοποιήσετε το LoadOptions** στο Aspose.Words από την αρχή μέχρι το τέλος: δημιουργήστε τις επιλογές, συνδέστε ένα `WarningCallback` που εστιάζει στις **προειδοποιήσεις αντικατάστασης γραμματοσειρών**, και φορτώστε ένα έγγραφο με σιγουριά. Το πλήρες παράδειγμα λειτουργεί αμέσως, και οι επιπλέον συμβουλές σας βοηθούν να αποφύγετε κοινά εμπόδια.  

Μη διστάσετε να πειραματιστείτε — αντικαταστήστε το callback με άλλους τύπους προειδοποιήσεων, καταγράψτε σε βάση δεδομένων, ή ενσωματώστε τη λογική σε μια web υπηρεσία που επικυρώνει ανεβασμένα αρχεία Word. Το μοτίβο είναι ευέλικτο, αξιόπιστο και, το πιο σημαντικό, σας δίνει ορατότητα στη διαδικασία αντικατάστασης γραμματοσειρών που διαφορετικά μπορεί να χαλάσει την απόδοση των εγγράφων σας.

Καλή προγραμματιστική δουλειά, και εύχομαι τα έγγραφά σας να αποδίδουν πάντα ακριβώς όπως προορίζονται! 

![Διάγραμμα που δείχνει τη ροή χρήσης του LoadOptions με ένα warning callback στο Aspose.Words](https://example.com/images/loadoptions-flow.png "Διάγραμμα πώς να χρησιμοποιήσετε το LoadOptions")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}