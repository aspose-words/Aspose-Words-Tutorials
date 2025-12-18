---
category: general
date: 2025-12-18
description: Πώς να ανακτήσετε γρήγορα αρχεία DOCX, ακόμη και όταν το έγγραφο είναι
  κατεστραμμένο, και να μάθετε να μετατρέπετε DOCX σε Markdown χρησιμοποιώντας το
  Aspose.Words. Περιλαμβάνει εξαγωγή PDF και ρυθμίσεις σκιάς σχήματος.
draft: false
keywords:
- how to recover docx
- recover corrupted document
- convert docx to markdown
- Aspose.Words recovery
- markdown export with LaTeX
language: el
og_description: Πώς να ανακτήσετε αρχεία DOCX εξηγείται βήμα‑βήμα, συμπεριλαμβανομένου
  του πώς να χειριστείτε κατεστραμμένα έγγραφα και να τα εξάγετε ως Markdown με μαθηματικά
  LaTeX.
og_title: Πώς να ανακτήσετε αρχεία DOCX και να τα μετατρέψετε σε Markdown – Πλήρης
  οδηγός
tags:
- Aspose.Words
- C#
- Document Conversion
title: Πώς να Ανακτήσετε Αρχεία DOCX και να τα Μετατρέψετε σε Markdown – Πλήρης Οδηγός
url: /el/net/document-operations/how-to-recover-docx-files-and-convert-to-markdown-complete-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Ανακτήσετε Αρχεία DOCX και να τα Μετατρέψετε σε Markdown – Πλήρης Οδηγός

**How to recover DOCX files** είναι μια συχνή ερώτηση για όποιον έχει ανοίξει ποτέ ένα κατεστραμμένο έγγραφο Word. Σε αυτό το tutorial θα σας δείξουμε βήμα‑βήμα πώς να ανακτήσετε ένα DOCX, ακόμη και όταν υποπτεύεστε ότι το έγγραφο είναι κατεστραμμένο, και στη συνέχεια να το μετατρέψετε σε Markdown χωρίς να χάσετε κανένα Office Math.  

Θα δείτε επίσης πώς να εξάγετε το ίδιο αρχείο ως PDF με διαχείριση ενσωματωμένων σχημάτων και πώς να ρυθμίσετε τη σκιά ενός σχήματος για ένα πιο επαγγελματικό αποτέλεσμα. Στο τέλος θα έχετε ένα ενιαίο, επαναλήψιμο πρόγραμμα C# που κάνει τα πάντα, από την ανάκτηση μέχρι τη μετατροπή.

## Τι Θα Μάθετε

- Φόρτωση ενός πιθανώς κατεστραμμένου **DOCX** σε λειτουργία ανάκτησης.  
- Εξαγωγή του ανακτημένου εγγράφου σε **Markdown** ενώ μετατρέπεται το Office Math σε LaTeX.  
- Αποθήκευση ενός καθαρού PDF που σηματοδοτεί τα αιωρούμενα σχήματα ως ενσωματωμένα στοιχεία.  
- Προσαρμογή της σκιάς ενός σχήματος προγραμματιστικά.  
- (Προαιρετικά) Αποθήκευση των εξαγόμενων εικόνων σε προσαρμοσμένο φάκελο.  

Καμία εξωτερική script, καμία χειροκίνητη αντιγραφή‑επικόλληση — μόνο καθαρός κώδικας C# που τροφοδοτείται από το **Aspose.Words for .NET**.

### Προαπαιτούμενα

- .NET 6.0 ή νεότερο (το API λειτουργεί επίσης με .NET Framework 4.6+).  
- Ένα έγκυρο license του Aspose.Words (ή μπορείτε να τρέξετε σε λειτουργία αξιολόγησης).  
- Visual Studio 2022 (ή οποιοδήποτε IDE προτιμάτε).  

Αν λείπει κάποιο από τα παραπάνω, κατεβάστε το πακέτο NuGet τώρα:

```bash
dotnet add package Aspose.Words
```

---

## Πώς να Ανακτήσετε Αρχεία DOCX με Aspose.Words

Το πρώτο που πρέπει να κάνουμε είναι να πούμε στο Aspose.Words να είναι επιεικές. Η σημαία `RecoveryMode.TryRecover` αναγκάζει τη βιβλιοθήκη να αγνοήσει τα μη‑κριτικά σφάλματα και να προσπαθήσει να ξαναχτίσει τη δομή του εγγράφου.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Words.Drawing;

// Step 1: Load the document with recovery mode to handle corrupted files
LoadOptions recoveryOptions = new LoadOptions { RecoveryMode = RecoveryMode.TryRecover };
Document doc = new Document(@"C:\Docs\input.docx", recoveryOptions);
```

**Γιατί είναι σημαντικό:**  
Όταν ένα αρχείο είναι μερικώς κατεστραμμένο — ίσως το ZIP container είναι σπασμένο ή ένα τμήμα XML είναι κακόμορφο — η κανονική φόρτωση πετάει εξαίρεση. Η λειτουργία ανάκτησης περνάει από κάθε τμήμα, παραλείπει τα «σκουπίδια» και ράβει ό,τι απομένει, δίνοντάς σας ένα χρήσιμο αντικείμενο `Document`.

> **Pro tip:** Αν επεξεργάζεστε πολλά αρχεία σε batch, τυλίξτε τη φόρτωση σε ένα `try/catch` και καταγράψτε όσα εξακολουθούν να αποτυγχάνουν μετά την ανάκτηση. Έτσι μπορείτε να επανεξετάσετε τα πραγματικά ακατάσβεστα αρχεία αργότερα.

---

## Μετατροπή DOCX σε Markdown – Εξαγωγή Office Math ως LaTeX

Μόλις το έγγραφο βρίσκεται στη μνήμη, η μετατροπή του σε Markdown είναι απλή. Το κλειδί είναι να ορίσετε το `OfficeMathExportMode` ώστε οποιεσδήποτε ενσωματωμένες εξισώσεις να γίνουν LaTeX, το οποίο καταλαβαίνουν οι περισσότεροι Markdown renderers.

```csharp
// Step 2: Configure Markdown export – export Office Math as LaTeX
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    OfficeMathExportMode = OfficeMathExportMode.LaTeX
};

// Optional: customize resource saving (e.g., store images in a specific folder)
markdownOptions.ResourceSavingCallback = (sender, args) =>
{
    // Place all extracted images into a sub‑folder called MyImages
    args.FileName = Path.Combine(@"C:\Docs\MyImages", args.FileName);
    args.SaveToStream = true; // let Aspose write the stream
};

// Step 3: Save the document as Markdown using the configured options
doc.Save(@"C:\Docs\output.md", markdownOptions);
```

**Τι παίρνετε:**  
- Απλό κείμενο με επικεφαλίδες, λίστες και πίνακες μετατρεπόμενα σε σύνταξη Markdown.  
- Εικόνες που εξάγονται στο `MyImages` (αν διατηρήσατε το callback).  
- Όλες οι εξισώσεις Office Math αποδίδονται ως μπλοκ LaTeX `$...$`.

### Ακραίες Περιπτώσεις & Παραλλαγές

| Κατάσταση | Προσαρμογή |
|-----------|------------|
| Δεν χρειάζεστε εξισώσεις LaTeX | Ορίστε `OfficeMathExportMode = OfficeMathExportMode.Image` |
| Προτιμάτε ενσωματωμένες εικόνες αντί για ξεχωριστά αρχεία | Παραλείψτε το `ResourceSavingCallback` και αφήστε το Aspose να ενσωματώσει data‑URI base‑64 |
| Πολύ μεγάλα έγγραφα προκαλούν πίεση μνήμης | Χρησιμοποιήστε `doc.Save` με `FileStream` και `markdownOptions` για ροή εξόδου |

---

## Ανάκτηση Κατεστραμμένου Εγγράφου και Αποθήκευση ως PDF με Ενσωματωμένα Σχήματα

Μερικές φορές χρειάζεστε επίσης μια έκδοση PDF για διανομή. Ένα κοινό λάθος είναι ότι τα αιωρούμενα σχήματα (πλαίσια κειμένου, εικόνες) γίνονται ξεχωριστά στρώματα που σπάζουν όταν το PDF ανοίγει σε παλαιότερους αναγνώστες. Η ρύθμιση `ExportFloatingShapesAsInlineTag` αναγκάζει αυτά τα σχήματα να θεωρηθούν ενσωματωμένα στοιχεία, διατηρώντας τη διάταξη.

```csharp
// Step 4: Configure PDF export – tag floating shapes as inline
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    ExportFloatingShapesAsInlineTag = true
};

// Step 5: Save the document as PDF with the inline‑shape setting
doc.Save(@"C:\Docs\output.pdf", pdfOptions);
```

**Γιατί θα το αγαπήσετε:**  
Το παραγόμενο PDF φαίνεται ακριβώς όπως το αρχικό αρχείο Word, ακόμη και αν η πηγή είχε πολύπλοκες αγκυροβολημένες εικόνες. Δεν εμφανίζονται επιπλέον «αιωρούμενα» αντικείμενα στο τελικό PDF.

---

## Προσαρμογή Σκιάς Σχήματος – Μικρή Οπτική Βελτίωση

Αν το έγγραφό σας περιέχει σχήματα (π.χ. ένα callout ή λογότυπο) μπορεί να θέλετε να ρυθμίσετε τη σκιά για καλύτερη οπτική επίδραση. Το παρακάτω απόσπασμα παίρνει το πρώτο σχήμα στο έγγραφο και ενημερώνει τις παραμέτρους της σκιάς.

```csharp
// Step 6: Adjust the shadow effect of the first shape in the document
Shape firstShape = doc.GetChild(NodeType.Shape, 0, true) as Shape;
if (firstShape != null)
{
    firstShape.ShadowFormat.Distance = 5.0;   // points from the shape
    firstShape.ShadowFormat.BlurRadius = 3.0;
    firstShape.ShadowFormat.Color = System.Drawing.Color.Black;
}

// (Optional) Save again to see the shadow changes
doc.Save(@"C:\Docs\output_with_shadow.pdf", pdfOptions);
```

**Πότε να το χρησιμοποιήσετε:**  
- Οι οδηγίες branding απαιτούν ήπια drop‑shadow.  
- Θέλετε να διακρίνετε ένα επισημασμένο callout από το υπόλοιπο κείμενο.  

> **Watch out:** Δεν όλοι οι PDF viewers σέβονται σύνθετες ρυθμίσεις σκιάς. Αν χρειάζεστε εγγυημένο αποτέλεσμα, εξάγετε το σχήμα ως PNG και επανεισάγετε το.

---

## Πλήρες Παράδειγμα End‑to‑End (Έτοιμο για Εκτέλεση)

Παρακάτω είναι το πλήρες πρόγραμμα που ενώνει όλα τα παραπάνω. Αντιγράψτε το σε ένα νέο console project και πατήστε **F5**.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Words.Drawing;

namespace DocxRecoveryAndConversion
{
    class Program
    {
        static void Main(string[] args)
        {
            // ---------- 1️⃣ Load with recovery ----------
            LoadOptions loadOpts = new LoadOptions { RecoveryMode = RecoveryMode.TryRecover };
            Document doc = new Document(@"C:\Docs\input.docx", loadOpts);

            // ---------- 2️⃣ Markdown export (LaTeX for equations) ----------
            MarkdownSaveOptions mdOpts = new MarkdownSaveOptions
            {
                OfficeMathExportMode = OfficeMathExportMode.LaTeX
            };
            mdOpts.ResourceSavingCallback = (sender, eventArgs) =>
            {
                eventArgs.FileName = Path.Combine(@"C:\Docs\MyImages", eventArgs.FileName);
                eventArgs.SaveToStream = true;
            };
            doc.Save(@"C:\Docs\output.md", mdOpts);

            // ---------- 3️⃣ PDF export with inline shapes ----------
            PdfSaveOptions pdfOpts = new PdfSaveOptions
            {
                ExportFloatingShapesAsInlineTag = true
            };
            doc.Save(@"C:\Docs\output.pdf", pdfOpts);

            // ---------- 4️⃣ Optional: tweak first shape's shadow ----------
            Shape shape = doc.GetChild(NodeType.Shape, 0, true) as Shape;
            if (shape != null)
            {
                shape.ShadowFormat.Distance = 5.0;
                shape.ShadowFormat.BlurRadius = 3.0;
                shape.ShadowFormat.Color = System.Drawing.Color.Black;
            }

            // Save PDF with shadow changes
            doc.Save(@"C:\Docs\output_with_shadow.pdf", pdfOpts);

            Console.WriteLine("All files generated successfully!");
        }
    }
}
```

**Αναμενόμενη έξοδος:**  

- `output.md` – ένα καθαρό αρχείο Markdown με εξισώσεις LaTeX.  
- `MyImages\*.*` – οποιεσδήποτε εικόνες εξήχθησαν από το αρχικό DOCX.  
- `output.pdf` – ένα PDF που διατηρεί την αρχική διάταξη, τα αιωρούμενα σχήματα τώρα ενσωματωμένα.  
- `output_with_shadow.pdf` – ίδιο με το παραπάνω αλλά με τη σκιά του πρώτου σχήματος ενισχυμένη.

---

## Συχνές Ερωτήσεις (FAQ)

**Ε: Θα λειτουργήσει αυτό σε ένα DOCX που είναι 0 KB;**  
Α: Η λειτουργία ανάκτησης δεν μπορεί να δημιουργήσει περιεχόμενο από το πουθενά, αλλά θα δημιουργήσει ένα κενό αντικείμενο `Document` αντί να πετάξει εξαίρεση. Θα έχετε κενό Markdown/PDF, που είναι σαφής ένδειξη να ερευνήσετε το αρχείο προέλευσης.

**Ε: Χρειάζομαι άδεια για το Aspose.Words ώστε να χρησιμοποιήσω τη λειτουργία ανάκτησης;**  
Α: Η έκδοση αξιολόγησης υποστηρίζει όλες τις δυνατότητες, συμπεριλαμβανομένου του `RecoveryMode`. Ωστόσο, τα παραγόμενα αρχεία περιέχουν υδατογράφημα. Για παραγωγική χρήση, εφαρμόστε άδεια για να το αφαιρέσετε.

**Ε: Πώς μπορώ να επεξεργαστώ κατά batch έναν φάκελο κατεστραμμένων εγγράφων;**  
Α: Τυλίξτε τη βασική λογική σε έναν βρόχο `foreach (var file in Directory.GetFiles(@"C:\Docs\ToProcess", "*.docx"))` και πιάστε εξαιρέσεις ανά αρχείο. Καταγράψτε τις αποτυχίες σε CSV για μετέπειτα ανασκόπηση.

**Ε: Τι γίνεται αν το Markdown μου χρειάζεται front‑matter για static site generator;**  
Α: Μετά το `doc.Save`, προσθέστε χειροκίνητα ένα YAML block στην αρχή:

```yaml
---
title: "Recovered Document"
date: 2025-12-18
---
```

**Ε: Μπορώ να εξάγω σε άλλες μορφές όπως HTML;**  
Α: Φυσικά — αντικαταστήστε το `MarkdownSaveOptions` με `HtmlSaveOptions`. Το ίδιο βήμα ανάκτησης ισχύει.

---

## Συμπέρασμα

Διασχίσαμε **πώς να ανακτήσετε αρχεία DOCX**, αντιμετωπίσαμε το δύσκολο σενάριο **ανάκτησης κατεστραμμένου εγγράφου**, και σας δείξαμε τα ακριβή βήματα για **μετατροπή DOCX σε Markdown** διατηρώντας τις εξισώσεις ως LaTeX. Επιπλέον, μάθατε πώς να εξάγετε ένα καθαρό PDF με ενσωματωμένα σχήματα και πώς να δώσετε σε ένα σχήμα μια επαγγελματική σκιά.  

Δοκιμάστε το σε ένα πραγματικό αρχείο — ίσως εκείνη την αναφορά που κατέστρεψε τον πελάτη σας την περασμένη εβδομάδα. Θα δείτε ότι με το Aspose.Words, η διάσωση είναι εφικτή.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}