---
category: general
date: 2026-03-24
description: Μάθετε πώς να εξάγετε συνδέσμους από ένα αρχείο Word και να αποθηκεύσετε
  το Word ως markdown. Αυτός ο οδηγός δείχνει πώς να μετατρέψετε το docx σε markdown
  και να δημιουργήσετε markdown από το Word γρήγορα.
draft: false
keywords:
- how to export links
- convert docx to markdown
- how to convert docx
- save word as markdown
- create markdown from word
language: el
og_description: Πώς να εξάγετε συνδέσμους από ένα DOCX και να αποθηκεύσετε το Word
  ως markdown. Οδηγός βήμα‑βήμα για τη μετατροπή docx σε markdown και τη δημιουργία
  markdown από το Word.
og_title: 'Πώς να εξάγετε συνδέσμους: Μετατροπή DOCX σε Markdown με C#'
tags:
- C#
- Aspose.Words
- Markdown
- Document Conversion
title: 'Πώς να εξάγετε συνδέσμους: Μετατροπή DOCX σε Markdown με C#'
url: /el/net/programming-with-markdownsaveoptions/how-to-export-links-convert-docx-to-markdown-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Εξάγετε Συνδέσμους: Μετατροπή DOCX σε Markdown σε C#

Έχετε αναρωτηθεί ποτέ **πώς να εξάγετε συνδέσμους** από ένα έγγραφο Word χωρίς να χάσετε τις διευθύνσεις URL τους; Ίσως χρειάζεται να μεταφέρετε το περιεχόμενο σε έναν static‑site generator, ή απλώς θέλετε ένα καθαρό αρχείο Markdown που εξακολουθεί να δείχνει στα σωστά μέρη. Σε αυτό το tutorial θα περάσουμε βήμα προς βήμα τις ακριβείς ενέργειες για να φορτώσετε ένα *.docx*, να ρυθμίσετε τη συμπεριφορά εξαγωγής συνδέσμων, και **να αποθηκεύσετε το Word ως markdown**. Στο τέλος θα ξέρετε επίσης πώς να **μετατρέψετε docx σε markdown** για οποιοδήποτε έργο, και θα δείτε ένα γρήγορο μοτίβο για **δημιουργία markdown από word** αρχεία.

> **Γιατί αυτό είναι σημαντικό:** Το Markdown είναι η lingua franca της σύγχρονης τεκμηρίωσης, των blogs και των αρχείων read‑me. Η διατήρηση των υπερσυνδέσμων σας ανέπαφη όταν μεταβαίνετε από Word σε Markdown σας εξοικονομεί ώρες χειροκίνητης διόρθωσης.

## Τι Θα Χρειαστεί

- .NET 6+ (ή .NET Framework 4.7+)
- **Aspose.Words for .NET** πακέτο NuGet (έκδοση 23.5 ή νεότερη)
- Ένα δείγμα `input.docx` που περιέχει μερικούς υπερσυνδέσμους
- Ένα IDE ή επεξεργαστή με τον οποίο αισθάνεστε άνετα (Visual Studio, VS Code, Rider…)

Αυτό είναι όλο—χωρίς επιπλέον βιβλιοθήκες, χωρίς εξωτερικές υπηρεσίες. Ας βουτήξουμε.

---

## Πώς να Εξάγετε Συνδέσμους από το Word σε Markdown

Παρακάτω βρίσκεται ο πλήρης, έτοιμος για εκτέλεση κώδικας. Δείχνει **πώς να εξάγετε συνδέσμους** ενώ μετατρέπει ένα αρχείο DOCX σε έγγραφο Markdown.

```csharp
// ------------------------------------------------------------
// Step 0: Add required namespaces
// ------------------------------------------------------------
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // ------------------------------------------------------------
        // Step 1: Load the source document
        // ------------------------------------------------------------
        // Replace YOUR_DIRECTORY with the actual folder path.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

        // ------------------------------------------------------------
        // Step 2: Configure Markdown save options
        // ------------------------------------------------------------
        // LinkExportMode determines how hyperlinks are written:
        //   Absolute – full URL (e.g., https://example.com/page)
        //   Relative – relative path based on the document location
        //   PlainText – only the link text, no URL
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            // For most web‑centric workflows we want absolute URLs.
            LinkExportMode = LinkExportMode.Absolute
        };

        // ------------------------------------------------------------
        // Step 3: Save the document as a Markdown file
        // ------------------------------------------------------------
        doc.Save(@"YOUR_DIRECTORY\Links.md", mdOptions);

        Console.WriteLine("✅ Conversion complete! Links have been exported.");
    }
}
```

### Εξήγηση των τριών βασικών βημάτων

1. **Load the DOCX** – `Document` είναι το σημείο εισόδου του Aspose.Words. Αναλύει το αρχείο `.docx`, δημιουργεί ένα μοντέλο αντικειμένων στη μνήμη, και σας δίνει πρόσβαση σε κάθε παράγραφο, πίνακα και υπερσύνδεσμο.  
2. **Configure `MarkdownSaveOptions`** – Το enum `LinkExportMode` είναι το κλειδί για **πώς να εξάγετε συνδέσμους**.  
   - `Absolute` γράφει το πλήρες URL, που είναι ιδανικό όταν το Markdown θα φιλοξενηθεί σε διαφορετικό domain.  
   - `Relative` είναι χρήσιμο για εσωτερικούς συνδέσμους που βρίσκονται δίπλα στο αρχείο Markdown.  
   - `PlainText` αφαιρεί εντελώς το URL, αφήνοντας μόνο το κείμενο εμφάνισης.  
3. **Save as Markdown** – Η μέθοδος `Save` γράφει ένα αρχείο `.md` που αντικατοπτρίζει την αρχική δομή του Word, συμπεριλαμβανομένων των επικεφαλίδων, λιστών με κουκίδες, και **εξαγόμενων συνδέσμων**.

> **Συμβουλή:** Αν μετατρέπετε πολλά έγγραφα σε batch, επαναχρησιμοποιήστε ένα μόνο αντικείμενο `MarkdownSaveOptions` για να αποφύγετε επαναλαμβανόμενες εκχωρήσεις.

---

## Μετατροπή DOCX σε Markdown – Σύντομη Ανασκόπηση

Αν και ο παραπάνω κώδικας ήδη **μετατρέπει docx σε markdown**, ας αναλύσουμε τη γενικότερη ροή εργασίας ώστε να την επαναχρησιμοποιήσετε σε άλλα πλαίσια:

| Φάση | Τι κάνετε | Γιατί είναι σημαντικό |
|------|-----------|------------------------|
| **Ανάγνωση** | `new Document(path)` | Φορτώνει το αρχείο Word στη μνήμη. |
| **Διαμόρφωση** | Set `MarkdownSaveOptions` (link mode, image handling, etc.) | Ελέγχει την ακριβή έξοδο Markdown. |
| **Εγγραφή** | `doc.Save(outputPath, options)` | Δημιουργεί το τελικό αρχείο `.md`. |

Μπορείτε να αλλάξετε το `LinkExportMode` σε `Relative` αν προτιμάτε **να αποθηκεύσετε το word ως markdown** με σχετικούς συνδέσμους, ή σε `PlainText` όταν χρειάζεστε μόνο το κείμενο του συνδέσμου. Το ίδιο μοτίβο λειτουργεί για άλλες μορφές (HTML, PDF) απλώς αλλάζοντας την κλάση `SaveOptions`.

---

## Προαιρετικό: Διαχείριση Εικόνων και Ενσωματωμένων Πόρων

Αν το έγγραφο Word περιέχει εικόνες, το Aspose.Words θα τις ενσωματώνει, από προεπιλογή, ως συμβολοσειρές base‑64 στο Markdown. Αυτό διατηρεί το αρχείο φορητό αλλά μπορεί να αυξήσει το μέγεθός του. Για να κρατήσετε τις εικόνες ως εξωτερικά αρχεία:

```csharp
mdOptions.ExportImagesAsBase64 = false;   // Store images as separate files
mdOptions.ImagesFolder = @"YOUR_DIRECTORY\Images"; // Folder for extracted images
```

Τώρα κάθε εικόνα αποθηκεύεται στο φάκελο `Images`, και το Markdown τις αναφέρει με σχετική διαδρομή—ιδανικό για static‑site generators που περιμένουν πόρους δίπλα στο περιεχόμενο.

---

## Ακραίες Περιπτώσεις & Συνηθισμένα Πιθανά Σφάλματα

| Κατάσταση | Τι πρέπει να προσέξετε | Προτεινόμενη λύση |
|-----------|------------------------|-------------------|
| **Απουσία προορισμού υπερσυνδέσμου** | Το Aspose.Words μπορεί να αφήσει κενό URL, με αποτέλεσμα `[]()` στο Markdown. | Επικυρώστε το `LinkExportMode` και ελέγξτε το αρχικό αρχείο Word για σπασμένους συνδέσμους πριν από τη μετατροπή. |
| **Πολύ μακριές διευθύνσεις URL** | Οι γραμμές Markdown μπορεί να γίνουν δύσκολες στη διαχείριση. | Χρησιμοποιήστε `LinkExportMode.Relative` όταν είναι δυνατόν, ή επεξεργαστείτε μεταγενέστερα το `.md` για να τυλίξετε τις URL. |
| **Μη‑ASCII χαρακτήρες σε URL** | Ορισμένοι αναλυτές ερμηνεύουν λανθασμένα τους χαρακτήρες με ποσοστιαία κωδικοποίηση. | Βεβαιωθείτε ότι το έγγραφό σας χρησιμοποιεί κωδικοποίηση UTF‑8 (προεπιλογή στο Aspose.Words) και δοκιμάστε το αποτέλεσμα με τον στόχο σας renderer. |
| **Μεγάλα έγγραφα (>100 MB)** | Η κατανάλωση μνήμης αυξάνεται απότομα. | Μεταφέρετε το έγγραφο χρησιμοποιώντας `LoadOptions` με `LoadFormat.Docx` και σκεφτείτε την επεξεργασία σε τμήματα. |

---

## Επαλήθευση του Αποτελέσματος

Αφού εκτελέσετε το πρόγραμμα, ανοίξτε το `Links.md`. Θα πρέπει να δείτε κάτι σαν:

```markdown
# Sample Document

Welcome to our guide. Visit the [Aspose website](https://www.aspose.com) for more info.

Check out the [GitHub repo](https://github.com/aspose-words/Aspose.Words-for-.NET) for source code.
```

Κάθε υπερσύνδεσμος διατηρείται ακριβώς όπως εμφανίστηκε στο αρχικό DOCX. Αν είχατε επιλέξει `Relative`, οι URL θα ήταν σχετικές διαδρομές.

---

## Συχνές Ερωτήσεις

**Q: Λειτουργεί αυτό με αρχεία .doc (παλαιότερη μορφή Word);**  
A: Ναι. Το Aspose.Words ανιχνεύει αυτόματα τη μορφή, έτσι μπορείτε να περάσετε μια διαδρομή `.doc` στο `new Document()` και οι ίδιες `MarkdownSaveOptions` ισχύουν.

**Q: Μπορώ να μετατρέψω ολόκληρο φάκελο αρχείων DOCX με τη μία;**  
A: Απόλυτα. Τυλίξτε τον κώδικα μέσα σε έναν βρόχο `foreach (var file in Directory.GetFiles(folder, "*.docx"))`, επαναχρησιμοποιώντας το ίδιο αντικείμενο `mdOptions`.

**Q: Τι γίνεται αν χρειάζομαι να διατηρήσω τις αρχικές αλλαγές γραμμής;**  
A: Ορίστε `mdOptions.ExportHeadersFooters = true` και `mdOptions.ExportTableStructure = true` για να διατηρήσετε τις λεπτομέρειες διάταξης.

---

## Επόμενα Βήματα: Από το Markdown σε Στατικό Site

Τώρα που **δημιουργείτε markdown από word**, ίσως θέλετε να σπρώξετε το αποτέλεσμα σε έναν static‑site generator όπως Hugo ή Jekyll. Εδώ είναι μια γρήγορη λίστα ελέγχου:

- Τοποθετήστε τα παραγόμενα αρχεία `.md` στον φάκελο `content/` του site Hugo.  
- Βεβαιωθείτε ότι ο φάκελος `Images` (αν χρησιμοποιείται) βρίσκεται κάτω από `static/` ώστε το site να μπορεί να τους σερβίρει.  
- Εκτελέστε `hugo server` για να προεπισκοπήσετε το site τοπικά· όλοι οι σύνδεσμοι πρέπει να λύνουν σωστά.  

Αν ενδιαφέρεστε για πιο προχωρημένες μετατροπές—όπως η διατήρηση προσαρμοσμένων στυλ ή η μετατροπή πινάκων σε HTML—εξετάστε τις άλλες ιδιότητες του `MarkdownSaveOptions`.

---

## Συμπέρασμα

Συζητήσαμε **πώς να εξάγετε συνδέσμους** από ένα έγγραφο Word, παρουσιάσαμε έναν καθαρό τρόπο **να μετατρέψετε docx σε markdown**, και δείξαμε τη πλήρη διαδικασία **να αποθηκεύσετε το word ως markdown** χρησιμοποιώντας το Aspose.Words για .NET. Με μόνο τρεις γραμμές κώδικα μπορείτε να **δημιουργήσετε markdown από word**, να διατηρήσετε τους υπερσυνδέσμους ανέπαφους, και να τροφοδοτήσετε το αποτέλεσμα σε οποιαδήποτε σύγχρονη ροή τεκμηρίωσης.

Δοκιμάστε το σε μία από τις δικές σας αναφορές, προσαρμόστε το `LinkExportMode` ώστε να ταιριάζει στις ανάγκες σας, και θα δείτε γρήγορα πόσο αβίαστη μπορεί να είναι η μετάβαση από Word σε Markdown. Έχετε κάποια παραλλαγή που θέλετε να μοιραστείτε; Αφήστε ένα σχόλιο, και καλή προγραμματιστική!

---

![παράδειγμα εξαγωγής συνδέσμων]()

*Το κείμενο alt της εικόνας περιέχει τη βασική λέξη-κλειδί για SEO.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}