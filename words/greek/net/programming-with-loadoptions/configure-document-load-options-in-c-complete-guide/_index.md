---
category: general
date: 2026-06-05
description: Διαμορφώστε τις επιλογές φόρτωσης εγγράφου σε C# ώστε να διαχειρίζεστε
  τις προειδοποιήσεις αντικατάστασης γραμματοσειρών και να προσαρμόζετε τη συμπεριφορά
  φόρτωσης χρησιμοποιώντας μια συνάρτηση κλήσης επιστροφής προειδοποίησης.
draft: false
keywords:
- configure document load options
- warning callback
- font substitution warning
- LoadOptions usage
- Aspose.Words document loading
- C# document loading options
language: el
og_description: Διαμορφώστε τις επιλογές φόρτωσης εγγράφου σε C# για να διαχειριστείτε
  τις προειδοποιήσεις αντικατάστασης γραμματοσειρών και να ρυθμίσετε λεπτομερώς τη
  φόρτωση του εγγράφου με μια κλήση επιστροφής προειδοποίησης.
og_title: Διαμορφώστε τις επιλογές φόρτωσης εγγράφου σε C# – Πλήρης Οδηγός
schemas:
- author: Aspose
  dateModified: '2026-06-05'
  description: Configure document load options in C# to handle font substitution warnings
    and customize loading behavior using a warning callback.
  headline: Configure document load options in C# – Complete Guide
  type: TechArticle
- description: Configure document load options in C# to handle font substitution warnings
    and customize loading behavior using a warning callback.
  name: Configure document load options in C# – Complete Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code works with .NET Framework 4.6+ as well).
      - Aspose.Words for .NET installed (`dotnet add package Aspose.Words`). - Basic
      familiarity with C# syntax.'
  - name: Implement a Warning Callback for Font Substitution
    text: First things first—what’s a **warning callback**? In Aspose.Words it’s a
      delegate that gets invoked whenever the library encounters something worth flagging,
      like a missing font. By catching `WarningType.FontSubstitution` we can log the
      exact font the engine swapped out.
  - name: Set Up LoadOptions with the Callback
    text: Now that we have a callback, we need to **configure document load options**
      to actually use it. `LoadOptions` is a lightweight container that tells Aspose.Words
      how to behave during the `Document` constructor call.
  - name: Load the Document Using the Configured Options
    text: With the callback wired up, the final act is to actually **load the document**.
      The `Document` constructor accepts a file path and the `LoadOptions` we just
      prepared.
  - name: Optional – Verify Loaded Fonts (Edge Case Handling)
    text: Sometimes you might want to *pre‑validate* the document before loading it
      fully, especially in batch processing scenarios. Aspose.Words offers the `FontSettings`
      class that can enumerate required fonts.
  - name: What if the warning callback throws an exception?
    text: The callback runs on the same thread that loads the document. Throwing inside
      the delegate will abort the load and propagate the exception. Wrap your logic
      in a `try/catch` if you need resilience.
  - name: Can I suppress *all* warnings instead of handling them?
    text: Yes—set `loadOptions.WarningCallback = null;` or provide a callback that
      does nothing. Be aware you’ll lose visibility into potential problems.
  - name: Does this work with encrypted DOCX files?
    text: Absolutely. Just add `Password = "yourPassword"` to `LoadOptions` before
      creating the `Document`. The warning callback will still fire for font issues.
  - name: How does this differ from using `DocumentBuilder`?
    text: '`DocumentBuilder` is for *creating* or *modifying* a document after it’s
      loaded. **Configure document load options** influences the *initial* parsing
      stage, which is where font substitution decisions are made.'
  type: HowTo
tags:
- C#
- Aspose.Words
- LoadOptions
- DocumentProcessing
title: Διαμόρφωση επιλογών φόρτωσης εγγράφου σε C# – Πλήρης Οδηγός
url: /el/net/programming-with-loadoptions/configure-document-load-options-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Διαμόρφωση επιλογών φόρτωσης εγγράφου σε C# – Πλήρης Οδηγός

Σας έχει συμβεί ποτέ να χρειάζεται να **διαμορφώσετε επιλογές φόρτωσης εγγράφου** σε C# επειδή η προεπιλεγμένη συμπεριφορά φόρτωσης δεν ήταν επαρκής; Ίσως βλέπετε απροσδόκητες αντικαταστάσεις γραμματοσειρών ή θέλετε να καταγράψετε κάθε προειδοποίηση που εμφανίζεται κατά την εισαγωγή ενός αρχείου. Σε αυτό το σεμινάριο θα περάσουμε βήμα‑βήμα από μια πρακτική, ολοκληρωμένη λύση που όχι μόνο ρυθμίζει αυτές τις επιλογές, αλλά επίσης δείχνει ένα **callback προειδοποίησης** για προειδοποιήσεις αντικατάστασης γραμματοσειρών.

Θα καλύψουμε τα πάντα, από το μικρό απόσπασμα κώδικα που δημιουργεί το callback, μέχρι τη στιγμή που θα ανοίξετε το έγγραφο με τις προσαρμοσμένες ρυθμίσεις σας. Στο τέλος θα έχετε ένα επαναχρησιμοποιήσιμο πρότυπο που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο Aspose.Words, είτε επεξεργάζεστε τιμολόγια, νομικές συμβάσεις ή απλές αναφορές.

## Τι Θα Μάθετε

- Πώς να **διαμορφώσετε επιλογές φόρτωσης εγγράφου** με `LoadOptions`.
- Πώς να υλοποιήσετε ένα **callback προειδοποίησης** που συλλαμβάνει τις ειδοποιήσεις `FontSubstitution`.
- Γιατί η διαχείριση μιας **προειδοποίησης αντικατάστασης γραμματοσειράς** νωρίς μπορεί να σας προστατεύσει από εκπλήξεις διάταξης.
- Διαχείριση edge‑case για ελλιπείς γραμματοσειρές και πώς να κάνετε graceful fallback.
- Ένα πλήρες, έτοιμο για αντιγραφή‑επικόλληση δείγμα κώδικα που μπορείτε να εκτελέσετε σήμερα.

### Προαπαιτούμενα

- .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.6+).
- Aspose.Words for .NET εγκατεστημένο (`dotnet add package Aspose.Words`).
- Βασική εξοικείωση με τη σύνταξη C#.

Αν τα έχετε, ας ξεκινήσουμε.

## Διαμόρφωση Επιλογών Φόρτωσης Εγγράφου – Βήμα‑Βήμα

Παρακάτω είναι η πλήρης ροή εργασίας χωρισμένη σε τέσσερα σαφή βήματα. Κάθε βήμα εξηγείται και ακολουθείται από ένα σύντομο μπλοκ κώδικα που μπορείτε να επικολλήσετε απευθείας στο Visual Studio.

### Βήμα 1: Υλοποίηση Callback Προειδοποίησης για Αντικατάσταση Γραμματοσειράς

Πρώτα απ' όλα—τι είναι ένα **callback προειδοποίησης**; Στο Aspose.Words είναι ένας delegate που καλείται όποτε η βιβλιοθήκη συναντά κάτι που αξίζει να σημειωθεί, όπως μια ελλιπής γραμματοσειρά. Συλλαμβάνοντας το `WarningType.FontSubstitution` μπορούμε να καταγράψουμε την ακριβή γραμματοσειρά που αντικατέστησε η μηχανή.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Step 1: Define a warning callback that reports font substitution warnings
var fontWarningCallback = new IWarningCallback(
    warningInfo =>
    {
        // Check if the warning is about font substitution
        if (warningInfo.WarningType == WarningType.FontSubstitution)
        {
            // Log the warning – you could also write to a file or telemetry system
            Console.WriteLine($"Font substitution detected: {warningInfo.Description}");
        }
    });
```

**Γιατί είναι σημαντικό:** Χωρίς ένα callback, η βιβλιοθήκη αντικαθιστά σιωπηλά τις ελλιπείς γραμματοσειρές, κάτι που μπορεί να οδηγήσει σε ακατανόητο κείμενο στο τελικό PDF ή DOCX. Εμφανίζοντας την προειδοποίηση αποκτάτε ορατότητα και μπορείτε να αποφασίσετε αν θα ενσωματώσετε τη λείπουσα γραμματοσειρά, να μεταβείτε σε εναλλακτική ή να ειδοποιήσετε τον χρήστη.

> **Συμβουλή:** Αν χρειάζεται να καταγράψετε *όλες* τις προειδοποιήσεις, αφαιρέστε τον έλεγχο `if`. Απλώς καταγράψτε το `warningInfo.Description` για κάθε συμβάν.

### Βήμα 2: Ρύθμιση LoadOptions με το Callback

Τώρα που έχουμε ένα callback, πρέπει να **διαμορφώσουμε επιλογές φόρτωσης εγγράφου** ώστε να το χρησιμοποιήσουμε. Το `LoadOptions` είναι ένα ελαφρύ κοντέινερ που ενημερώνει το Aspose.Words πώς να συμπεριφέρεται κατά την κλήση του κατασκευαστή `Document`.

```csharp
// Step 2: Attach the callback to the LoadOptions object
var loadOptions = new LoadOptions
{
    WarningCallback = fontWarningCallback,
    // Optional: enforce strict loading mode (throws on any warning)
    // LoadFormat = LoadFormat.Docx,
    // LoadOptions.LoadFormat can be left null to auto-detect based on file extension
};
```

**Γιατί είναι σημαντικό:** Αναθέτοντας το `WarningCallback`, κάθε προειδοποίηση που εκδίδεται κατά τη φάση φόρτωσης περνάει από το delegate μας. Μπορείτε επίσης να ρυθμίσετε άλλες ιδιότητες του `LoadOptions` εδώ—όπως `LoadFormat` αν γνωρίζετε τον ακριβή τύπο αρχείου, ή `Password` για κρυπτογραφημένα έγγραφα.

### Βήμα 3: Φόρτωση του Εγγράφου Χρησιμοποιώντας τις Ρυθμισμένες Επιλογές

Με το callback συνδεδεμένο, η τελική ενέργεια είναι να **φορτώσετε το έγγραφο**. Ο κατασκευαστής `Document` δέχεται μια διαδρομή αρχείου και τα `LoadOptions` που μόλις προετοιμάσαμε.

```csharp
// Step 3: Load the document with our custom options
string inputPath = @"C:\Docs\input.docx";   // Adjust to your environment
Document doc = new Document(inputPath, loadOptions);
```

Αν το αρχείο προέλευσης αναφέρει μια γραμματοσειρά που δεν είναι εγκατεστημένη στο μηχάνημα, θα δείτε μια γραμμή όπως:

```
Font substitution detected: Font 'Calibri' was substituted with 'Arial'.
```

στην κονσόλα. Αυτό το άμεσο feedback σας επιτρέπει να αποφασίσετε αν θα συμπεριλάβετε τη λείπουσα γραμματοσειρά μαζί με την εφαρμογή σας ή αν θα την αντικαταστήσετε προγραμματιστικά.

### Βήμα 4: Προαιρετικό – Επαλήθευση Φορτωμένων Γραμματοσειρών (Διαχείριση Edge Cases)

Μερικές φορές μπορεί να θέλετε να *προ‑επαληθεύσετε* το έγγραφο πριν το φορτώσετε πλήρως, ειδικά σε σενάρια επεξεργασίας δέσμης. Το Aspose.Words προσφέρει την κλάση `FontSettings` που μπορεί να απαριθμήσει τις απαιτούμενες γραμματοσειρές.

```csharp
// Optional: Check required fonts before full load
var fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);
loadOptions.FontSettings = fontSettings;

// Re-load the document now that we have a custom font folder
Document docWithCustomFonts = new Document(inputPath, loadOptions);
```

**Πότε να το χρησιμοποιήσετε:** Αν διατηρείτε ένα ιδιωτικό αποθετήριο γραμματοσειρών (π.χ. εταιρικές γραμματοσειρές), η παραπομπή του `FontSettings` σε αυτόν τον φάκελο εξασφαλίζει ότι η μηχανή θα βρει τις σωστές γραμματοσειρές χωρίς να επιστρέφει σε γενικές.

## Πλήρες Παράδειγμα Λειτουργίας

Παρακάτω είναι ολόκληρο το πρόγραμμα—απλώς αντιγράψτε, επικολλήστε και εκτελέστε. Δείχνει τα πάντα, από τη δημιουργία του callback μέχρι τη τελική φόρτωση του εγγράφου.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;

class Program
{
    static void Main()
    {
        // 1️⃣ Define the warning callback
        var fontWarningCallback = new IWarningCallback(
            warningInfo =>
            {
                if (warningInfo.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font substitution detected: {warningInfo.Description}");
                }
            });

        // 2️⃣ Configure LoadOptions with the callback
        var loadOptions = new LoadOptions
        {
            WarningCallback = fontWarningCallback,
            // Uncomment the next line to point to a custom font folder
            // FontSettings = new FontSettings { SetFontsFolder(@"C:\MyFonts", true) }
        };

        // 3️⃣ Load the document using the custom options
        string inputFile = @"YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputFile, loadOptions);

        // 4️⃣ (Optional) Save as PDF to verify everything works
        string outputFile = @"YOUR_DIRECTORY/output.pdf";
        doc.Save(outputFile);
        Console.WriteLine($"Document loaded and saved to {outputFile}");
    }
}
```

**Αναμενόμενη έξοδος**

```
Font substitution detected: Font 'Times New Roman' was substituted with 'Arial'.
Document loaded and saved to C:\Your\Path\output.pdf
```

Αν δεν υπάρχουν ελλιπείς γραμματοσειρές, το callback παραμένει σιωπηλό—δεν υπάρχει κάτι για ανησυχία.

## Συχνές Ερωτήσεις & Edge Cases

### Τι γίνεται αν το callback προειδοποίησης ρίξει εξαίρεση;

Το callback εκτελείται στο ίδιο νήμα που φορτώνει το έγγραφο. Η ρίψη εξαίρεσης μέσα στο delegate θα διακόψει τη φόρτωση και θα διαδώσει την εξαίρεση. Τυλίξτε τη λογική σας σε `try/catch` αν χρειάζεστε ανθεκτικότητα.

### Μπορώ να καταστείλω *όλες* τις προειδοποιήσεις αντί να τις διαχειριστώ;

Ναι—ορίστε `loadOptions.WarningCallback = null;` ή παρέχετε ένα callback που δεν κάνει τίποτα. Να έχετε υπόψη ότι θα χάσετε την ορατότητα σε πιθανές προβλήματα.

### Λειτουργεί αυτό με κρυπτογραφημένα αρχεία DOCX;

Απολύτως. Απλώς προσθέστε `Password = "yourPassword"` στα `LoadOptions` πριν δημιουργήσετε το `Document`. Το callback προειδοποίησης θα εξακολουθεί να ενεργοποιείται για προβλήματα γραμματοσειρών.

### Πώς διαφέρει αυτό από τη χρήση του `DocumentBuilder`;

Το `DocumentBuilder` προορίζεται για *δημιουργία* ή *τροποποίηση* ενός εγγράφου μετά τη φόρτωσή του. Η **διαμόρφωση επιλογών φόρτωσης εγγράφου** επηρεάζει το *αρχικό* στάδιο ανάλυσης, όπου λαμβάνονται οι αποφάσεις αντικατάστασης γραμματοσειρών.

## Οπτική Επισκόπηση

![Διάγραμμα που δείχνει τη ροή διαμόρφωσης επιλογών φόρτωσης εγγράφου](https://example.com/images/load-options-flow.png "Διάγραμμα που δείχνει τη ροή διαμόρφωσης επιλογών φόρτωσης εγγράφου")

*Η εικόνα απεικονίζει τη ροή: callback → LoadOptions → κατασκευαστής Document → διαχείριση προειδοποιήσεων.*

## Συμπέρασμα

Τώρα ξέρετε πώς να **διαμορφώσετε επιλογές φόρτωσης εγγράφου** σε C# για να συλλαμβάνετε προειδοποιήσεις αντικατάστασης γραμματοσειρών, να ενσωματώνετε προσαρμοσμένους φακέλους γραμματοσειρών και να διατηρείτε πλήρη έλεγχο της διαδικασίας φόρτωσης. Αυτό το πρότυπο σας δίνει την εμπιστοσύνη ότι κάθε ελλιπής γραμματοσειρά θα αναφερθεί, επιτρέποντάς σας να διατηρήσετε την ακεραιότητα του εγγράφου σε οποιοδήποτε περιβάλλον.

Επόμενα βήματα; Δοκιμάστε να αντικαταστήσετε την καταγραφή στην κονσόλα με ένα πιο ισχυρό σύστημα τηλεμετρίας, ή συνδυάστε αυτήν την προσέγγιση με το `DocumentBuilder` για να αντικαταστήσετε αυτόματα τις ελλιπείς γραμματοσειρές με μια εταιρική προεπιλογή. Μπορείτε επίσης να εξερευνήσετε άλλες τιμές του `WarningType`, όπως το `DocumentStructure`, για ακόμη πιο βαθιά κατανόηση.

Καλή προγραμματιστική δουλειά, και εύχομαι τα έγγραφά σας να αποδίδουν πάντα ακριβώς όπως το επιθυμείτε!

## Τι Θα Μάθετε Στη Σύντομη Μελλοντική

Τα παρακάτω σεμινάρια καλύπτουν στενά συναφή θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε σε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Κατακτήστε τις Επιλογές Φόρτωσης Markdown του Aspose.Words σε Python για Βελτιωμένη Επεξεργασία Εγγράφων](/words/english/python-net/document-operations/aspose-words-markdown-load-options-python/)
- [Βελτιστοποίηση Φόρτωσης Εγγράφων με Επιλογές HTML, RTF και TXT](/words/english/java/word-processing/optimizing-document-loading-options/)
- [Χρήση Επιλογών και Ρυθμίσεων Εγγράφου στο Aspose.Words για Java](/words/english/java/document-manipulation/using-document-options-and-settings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}