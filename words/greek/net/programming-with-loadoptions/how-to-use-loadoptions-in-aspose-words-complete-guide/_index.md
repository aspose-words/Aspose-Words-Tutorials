---
category: general
date: 2026-01-10
description: Μάθετε πώς να χρησιμοποιείτε το LoadOptions για να αντιμετωπίζετε τις
  ελλιπείς γραμματοσειρές στο Aspose.Words. Κώδικας βήμα‑βήμα, συμβουλές και βέλτιστες
  πρακτικές για αξιόπιστη φόρτωση εγγράφων.
draft: false
keywords:
- how to use loadoptions
- handle missing fonts
- Aspose.Words warning callback
- font substitution handling
- document loading options
language: el
og_description: Πώς να χρησιμοποιήσετε το LoadOptions για να αντιμετωπίσετε τις ελλείπουσες
  γραμματοσειρές στο Aspose.Words. Λάβετε ένα πλήρες, λειτουργικό παράδειγμα με επεξηγήσεις
  και πρακτικές συμβουλές.
og_title: Πώς να χρησιμοποιήσετε το LoadOptions στο Aspose.Words – Πλήρης Οδηγός
tags:
- Aspose.Words
- C#
- .NET
title: Πώς να χρησιμοποιήσετε το LoadOptions στο Aspose.Words – Πλήρης οδηγός
url: /el/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Χρησιμοποιήσετε το LoadOptions στο Aspose.Words – Πλήρης Οδηγός

Έχετε αναρωτηθεί ποτέ **πώς να χρησιμοποιήσετε το LoadOptions** όταν φορτώνετε ένα έγγραφο Word που μπορεί να λείπουν μερικές γραμματοσειρές; Δεν είστε ο μόνος που σκεπάζει το κεφάλι του για αυτό. Σε πολλά πραγματικά έργα, τα έγγραφα μεταφέρονται μεταξύ μηχανών, και το σύστημα‑στόχος συχνά δεν διαθέτει τις ακριβείς γραμματοσειρές που χρησιμοποίησε ο συγγραφέας. Το αποτέλεσμα; Απρόσμενες αντικαταστάσεις γραμματοσειρών που μπορούν να διαταράξουν τη διάταξη, να κρύψουν σημαντικούς χαρακτήρες ή απλώς να φαίνονται εκτός στυλ.  

Ευτυχώς, το Aspose.Words μας παρέχει έναν καθαρό τρόπο για *να διαχειριστούμε τις ελλιπείς γραμματοσειρές* εκθέτοντας ένα αντικείμενο `LoadOptions` με μια κλήση προειδοποίησης. Σε αυτό το tutorial θα μάθετε ακριβώς **πώς να χρησιμοποιήσετε το LoadOptions** για να συλλάβετε τις προειδοποιήσεις αντικατάστασης γραμματοσειρών, να τις καταγράψετε και να διατηρήσετε το pipeline επεξεργασίας σας ανθεκτικό.

Θα καλύψουμε:

* Ρύθμιση της κλάσης προειδοποίησης callback  
* Διαμόρφωση του `LoadOptions` με αυτό το callback  
* Φόρτωση εγγράφου ενώ παρακολουθείτε τις ελλιπείς γραμματοσειρές  
* Συμβουλές για αντιμετώπιση προβλημάτων και επέκταση της λύσης  

Δεν απαιτείται εξωτερική τεκμηρίωση — όλα όσα χρειάζεστε είναι εδώ.

---

## Τι Θα Χρειαστεί

Πριν βουτήξουμε, βεβαιωθείτε ότι έχετε:

* **Aspose.Words for .NET** (τελευταία έκδοση έως το 2026) εγκατεστημένο μέσω NuGet  
* Ένα .NET περιβάλλον ανάπτυξης (Visual Studio, Rider ή VS Code)  
* Ένα δείγμα DOCX που αναφέρεται σε γραμματοσειρά που δεν έχετε εγκατεστημένη (θα το ονομάσουμε `input.docx`)  

Αυτό είναι όλο — δεν απαιτούνται πρόσθετες βιβλιοθήκες.

---

## Βήμα 1 – Ορισμός Callback Προειδοποίησης για Καταγραφή Αντικατάστασης Γραμματοσειράς

Το πρώτο κομμάτι του παζλ είναι μια κλάση που υλοποιεί `IWarningCallback`. Το Aspose.Words θα καλέσει τη μέθοδο `Warning` της κάθε φορά που συναντήσει κάτι αξιοσημείωτο — όπως μια ελλιπή γραμματοσειρά.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Custom warning handler that prints font‑substitution messages to the console.
/// </summary>
class FontWarningCallback : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We're only interested in font‑substitution warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution detected: {info.Description}");
        }
    }
}
```

**Γιατί είναι σημαντικό:**  
Φιλτράροντας με `WarningType.FontSubstitution` αποφεύγουμε την ακαταστασία από άσχετες προειδοποιήσεις (π.χ., παρωχημένες λειτουργίες). Το callback σας δίνει πλήρη έλεγχο — μπορείτε να καταγράψετε σε αρχείο, να ρίξετε εξαίρεση ή ακόμη και να προσπαθήσετε να ενσωματώσετε μια εναλλακτική γραμματοσειρά προγραμματιστικά.

---

## Βήμα 2 – Διαμόρφωση LoadOptions με το Callback

Τώρα που έχουμε έναν χειριστή, πρέπει να πούμε στο Aspose.Words να το χρησιμοποιήσει. Εδώ είναι που **πώς να χρησιμοποιήσετε το LoadOptions** στην πράξη.

```csharp
// Create a LoadOptions instance and attach our custom callback.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCallback()
};
```

**Συμβουλή:** `LoadOptions` προσφέρει πολλές άλλες ρυθμίσεις (π.χ., `Password`, `LoadFormat`, `Encoding`). Μπορείτε να τις συνδυάσετε, αλλά για τη διαχείριση ελλιπών γραμματοσειρών το `WarningCallback` είναι το αστέρι της παράστασης.

---

## Βήμα 3 – Φόρτωση του Εγγράφου Χρησιμοποιώντας τις Διαμορφωμένες Επιλογές

Με το `LoadOptions` έτοιμο, η φόρτωση του εγγράφου είναι απλή. Το Aspose.Words θα καλέσει αυτόματα το callback για κάθε γραμματοσειρά που δεν μπορεί να βρει.

```csharp
// Path to the DOCX that may reference unavailable fonts.
string docPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document while the warning callback monitors font issues.
Document doc = new Document(docPath, loadOptions);

// At this point you can continue processing the document—saving, editing, etc.
Console.WriteLine("✅ Document loaded successfully.");
```

**Αναμενόμενη έξοδος:**  

Αν το `input.docx` χρησιμοποιεί μια γραμματοσειρά που ονομάζεται *“GothicBold”* και δεν είναι εγκατεστημένη, θα δείτε κάτι σαν:

```
⚠️ Font substitution detected: Font substitution applied. Original font: GothicBold, Substituted font: Arial.
✅ Document loaded successfully.
```

Η γραμμή προειδοποίησης εμφανίζεται **ακριβώς όταν εντοπίζεται η ελλιπής γραμματοσειρά**, παρέχοντάς σας άμεση ανατροφοδότηση.

---

## Βήμα 4 – (Προαιρετικό) Συνέχεια Επεξεργασίας του Εγγράφου

Συνήθως θέλετε να κάνετε περισσότερα από το απλό φόρτωμα του αρχείου. Παρακάτω είναι μερικές κοινές ενέργειες μετά το φόρτωμα που λειτουργούν άψογα με τη ρύθμιση προειδοποίησης.

### 4.1 Αποθήκευση του Εγγράφου ως PDF

```csharp
// Convert to PDF – the substituted fonts are already baked into the layout.
doc.Save("output.pdf", SaveFormat.Pdf);
Console.WriteLine("📄 PDF saved as output.pdf");
```

### 4.2 Αντικατάσταση Ελλιπών Γραμματοσειρών με Γνωστή Εναλλακτική

Αν προτιμάτε μια συγκεκριμένη εναλλακτική (π.χ., *“Calibri”*), μπορείτε να προσαρμόσετε το `FontSettings` πριν την αποθήκευση:

```csharp
var fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionRules.AddSubstitutes(
    "GothicBold", new[] { "Calibri", "Arial" });

doc.FontSettings = fontSettings;
doc.Save("output-with-fallback.pdf", SaveFormat.Pdf);
Console.WriteLine("🔄 PDF saved with explicit fallback fonts.");
```

### 4.3 Καταγραφή Όλων των Προειδοποιήσεων σε Αρχείο

```csharp
class FileLoggingWarningCallback : IWarningCallback
{
    private readonly string _logPath = "load-warnings.log";

    public void Warning(WarningInfo info)
    {
        File.AppendAllText(_logPath,
            $"{DateTime.Now:u} - {info.WarningType}: {info.Description}{Environment.NewLine}");
    }
}

// Use it:
var loadOptionsWithFileLog = new LoadOptions
{
    WarningCallback = new FileLoggingWarningCallback()
};
```

Αυτά τα αποσπάσματα δείχνουν **πώς να χρησιμοποιήσετε το LoadOptions** πέρα από το βασικό σενάριο, δίνοντάς σας ευελιξία για λύσεις παραγωγικού επιπέδου.

---

## Συνηθισμένα Παράπλευρα Προβλήματα & Πώς να **Διαχειριστείτε τις Ελλιπείς Γραμματοσειρές** με Ευγένεια

| Πρόβλημα | Γιατί Συμβαίνει | Πώς να Διορθώσετε / Μετριάσετε |
|----------|----------------|--------------------------------|
| **Δεν έχει προσαρτηθεί callback** | Ξεχάσατε να ορίσετε το `WarningCallback`. | Πάντα δημιουργήστε μια παρουσία `LoadOptions` και αναθέστε το handler σας πριν τη φόρτωση. |
| **Το callback μόνο εκτυπώνει, δεν αποθηκεύει** | Σε μια web υπηρεσία, η έξοδος της κονσόλας εξαφανίζεται. | Αντικαταστήστε το `Console.WriteLine` με έναν logger (Serilog, NLog) ή γράψτε σε μόνιμη αποθήκη. |
| **Πολλές ελλιπείς γραμματοσειρές, μόνο η πρώτη αναφέρεται** | Το callback σας ρίχνει εξαίρεση στην πρώτη προειδοποίηση. | Κρατήστε το callback ελαφρύ· αποφύγετε το throw εκτός αν θέλετε πραγματικά να τερματίσετε. |
| **Η αντικατεστημένη γραμματοσειρά φαίνεται λανθασμένη** | Η προεπιλεγμένη αντικατάσταση μπορεί να επιλέξει μια γραμματοσειρά που διαφέρει οπτικά. | Χρησιμοποιήστε `FontSettings.SubstitutionSettings.FontSubstitutionRules` για να προτεραιοποιήσετε την προτιμώμενη εναλλακτική σας. |
| **Περιορισμός απόδοσης σε τεράστια έγγραφα** | Το callback προειδοποίησης καλείται χιλιάδες φορές. | Συγκεντρώστε τις προειδοποιήσεις σε λίστα και επεξεργαστείτε τις μετά τη φόρτωση, ή φιλτράρετε μόνο μοναδικά ονόματα γραμματοσειρών. |

---

## Πλήρες Παράδειγμα Εργασίας – Όλα τα Μέρη Μαζί

Παρακάτω είναι το πλήρες, έτοιμο‑για‑εκτέλεση πρόγραμμα που δείχνει όλη τη ροή. Αντιγράψτε‑και‑επικολλήστε σε ένα console project, προσθέστε το πακέτο NuGet Aspose.Words, και θα λειτουργήσει αμέσως.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class FontWarningCallback : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // 1️⃣ Configure LoadOptions with our warning handler.
        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningCallback()
        };

        // 2️⃣ Path to the source DOCX.
        string sourcePath = Path.Combine(Environment.CurrentDirectory, "input.docx");

        // 3️⃣ Load the document – any missing fonts trigger our callback.
        Document doc = new Document(sourcePath, loadOptions);
        Console.WriteLine("✅ Document loaded.");

        // 4️⃣ Optional: Save as PDF to see the final appearance.
        string pdfPath = Path.Combine(Environment.CurrentDirectory, "output.pdf");
        doc.Save(pdfPath, SaveFormat.Pdf);
        Console.WriteLine($"📄 PDF saved to {pdfPath}");

        // 5️⃣ (Bonus) Set explicit fallback font for a known missing font.
        var fontSettings = new FontSettings();
        fontSettings.SubstitutionSettings.FontSubstitutionRules.AddSubstitutes(
            "GothicBold", new[] { "Calibri", "Arial" });
        doc.FontSettings = fontSettings;
        doc.Save("output-with-fallback.pdf", SaveFormat.Pdf);
        Console.WriteLine("🔄 PDF with explicit fallback saved.");
    }
}
```

**Η εκτέλεση αυτού του προγράμματος** θα:

1. Εκτυπώνει τυχόν προειδοποιήσεις αντικατάστασης γραμματοσειρών στην κονσόλα.  
2. Αποθηκεύει την αρχική διάταξη ως `output.pdf`.  
3. Αποθηκεύει ένα δεύτερο PDF (`output-with-fallback.pdf`) που επιβάλλει την εναλλακτική σε *Calibri* ή *Arial*.

---

## Συχνές Ερωτήσεις (FAQs)

**Q: Does this work for DOC, RTF, or HTML files?**  
A: Yes. `LoadOptions` is format‑agnostic; as long as you pass the correct file path, the warning callback will fire for missing fonts across all supported formats.  
**Q: Can I suppress the warnings entirely?**  
A: You could assign a no‑op callback (`new IWarningCallback { Warning = _ => {} }`) or set `LoadOptions.WarningCallback = null`. However, losing visibility means you might miss critical font issues.  
**Q: What if I need to replace missing fonts with embedded ones?**  
A: Use `FontSettings` to embed a substitute font file (`AddFontSource`). Combine that with the substitution rules for a seamless experience.  
**Q: Is the callback thread‑safe?**  
A: The callback may be invoked from multiple threads when loading large documents in parallel. Ensure any shared resources (e.g., log files) are synchronized.

---

## Συμπέρασμα

Διασχίσαμε **πώς να χρησιμοποιήσετε το LoadOptions** στο Aspose.Words για **να διαχειριστείτε τις ελλιπείς γραμματοσειρές** με κομψότητα. Ορίζοντας ένα προσαρμοσμένο `IWarningCallback`, το συνδέοντας με μια παρουσία `LoadOptions` και φορτώνοντας το έγγραφό σας με αυτή τη διαμόρφωση, αποκτάτε άμεση εικόνα για τυχόν συμβάντα αντικατάστασης γραμματοσειρών. Από εκεί μπορείτε να καταγράψετε, να αντικαταστήσετε ή να ενσωματώσετε εναλλακτικές γραμματοσειρές ώστε το αποτέλεσμα να φαίνεται ακριβώς όπως θέλετε.

Θυμηθείτε, τα βασικά βήματα είναι:

1. Υλοποιήστε ένα callback προειδοποίησης που εστιάζει στο `WarningType.FontSubstitution`.  
2. Συνδέστε το callback σε ένα αντικείμενο `LoadOptions`.  
3. Φορτώστε το έγγραφό σας με αυτές τις επιλογές.  
4. (Προαιρετικό) Εφαρμόστε περαιτέρω κανόνες αντικατάστασης γραμματοσειρών ή καταγραφή όπως απαιτείται.

Μη διστάσετε να πειραματιστείτε — αντικαταστήστε τον logger της κονσόλας με έναν δομημένο logger, προσθέστε ειδοποιήσεις email για κρίσιμες ελλιπείς γραμματοσειρές, ή ενσωματώστε αυτό το μοτίβο σε ένα μεγαλύτερο pipeline επεξεργασίας εγγράφων. Η προσέγγιση κλιμακώνεται άψογα είτε επεξεργάζεστε ένα μόνο αρχείο είτε χιλιάδες σε batch.

Καλή προγραμματιστική δουλειά, και εύχομαι τα έγγραφά σας να αποδίδουν πάντα με τις σωστές γραμματοσειρές!  

---

![how to use loadoptions example]

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}