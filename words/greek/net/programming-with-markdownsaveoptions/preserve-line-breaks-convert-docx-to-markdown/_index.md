---
category: general
date: 2026-02-13
description: Διατηρήστε τις αλλαγές γραμμής κατά τη μετατροπή του DOCX σε markdown.
  Μάθετε πώς να αποθηκεύετε το Word ως markdown, να εξάγετε κενές παραγράφους και
  να διατηρείτε τη μορφοποίηση αμετάβλητη.
draft: false
keywords:
- preserve line breaks
- convert docx to markdown
- save word as markdown
- how to export empty
- how to preserve breaks
language: el
og_description: "Διατηρήστε τις αλλαγές γραμμής κατά τη μετατροπή DOCX σε markdown.
  \ \nΑυτός ο οδηγός δείχνει πώς να αποθηκεύσετε το Word ως markdown και να εξάγετε
  σωστά κενές παραγράφους."
og_title: 'Διατήρηση αλλαγών γραμμής: Μετατροπή DOCX σε Markdown'
tags:
- Aspose.Words
- C#
- Markdown
title: 'Διατήρηση αλλαγών γραμμής: Μετατροπή DOCX σε Markdown'
url: /el/net/programming-with-markdownsaveoptions/preserve-line-breaks-convert-docx-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Διατήρηση αλλαγών γραμμής: Μετατροπή DOCX σε Markdown

Έχετε ποτέ χρειαστεί να **διατηρήσετε τις αλλαγές γραμμής** όταν μετατρέπετε ένα αρχείο DOCX σε Markdown; Είναι ένα συνηθισμένο πρόβλημα—το όμορφο έγγραφο Word σας καταλήγει σε ένα τοίχος κειμένου, και οι σκόπιμες κενές γραμμές εξαφανίζονται. Τα καλά νέα; Μπορείτε να διατηρήσετε κάθε αλλαγή γραμμής, ακόμη και τις κενές παραγράφους, με μερικές απλές ρυθμίσεις.

Σε αυτό το tutorial θα περάσουμε από όλη τη διαδικασία **αποθήκευσης Word ως Markdown**, καλύπτοντας τα πάντα από τη φόρτωση του πηγαίου εγγράφου μέχρι τη ρύθμιση της σωστής λειτουργίας εξαγωγής. Στο τέλος θα γνωρίζετε *πώς να εξάγετε κενές* παραγράφους, *πώς να διατηρήσετε τις αλλαγές* σε σύνθετες διατάξεις, και θα έχετε ένα πλήρες, έτοιμο για αντιγραφή‑επικόλληση δείγμα κώδικα. Χωρίς ελλιπή στοιχεία, χωρίς «δείτε τα docs» αδιέξοδα.

## Τι θα μάθετε

- Γιατί η διατήρηση των αλλαγών γραμμής είναι σημαντική για την αναγνωσιμότητα και τα εργαλεία downstream.  
- Πώς να **μετατρέψετε DOCX σε markdown** χρησιμοποιώντας Aspose.Words for .NET.  
- Ποιες ρυθμίσεις του `MarkdownSaveOptions` ελέγχουν τη διαχείριση κενών παραγράφων.  
- Πρακτικές συμβουλές για την αντιμετώπιση ειδικών περιπτώσεων όπως πίνακες, λίστες και μπλοκ κώδικα.  
- Ένα πλήρες, εκτελέσιμο παράδειγμα που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο C# σήμερα.

### Προαπαιτούμενα

- .NET 6+ (ή .NET Framework 4.7.2+) εγκατεστημένο.  
- Άδεια για **Aspose.Words for .NET** (η δωρεάν δοκιμή λειτουργεί για αυτήν την επίδειξη).  
- Βασική εξοικείωση με C# και την έννοια του Markdown.  

Αν έχετε καλύψει αυτά, ας βουτήξουμε.

![Διάγραμμα διατήρησης αλλαγών γραμμής](preserve-line-breaks.png "Διάγραμμα που δείχνει πώς οι κενές παράγραφοι γίνονται αλλαγές γραμμής σε Markdown")

## Διατήρηση αλλαγών γραμμής – Γιατί είναι σημαντικό

Όταν ένα έγγραφο Word περιέχει σκόπιμες κενές γραμμές—σκεφτείτε τις ως οπτικούς διαχωριστές μεταξύ ενοτήτων—αυτά τα κενά συχνά αφαιρούνται κατά τη μετατροπή. Το Markdown, από τη φύση του, αντιμετωπίζει μια μοναδική αλλαγή γραμμής ως συνέχεια της ίδιας παραγράφου, έτσι μια κενή γραμμή πρέπει να αναπαρασταθεί ρητά. Αν δεν **διατηρήσετε τις αλλαγές γραμμής**, το αποτέλεσμα μπορεί να φαίνεται συμπιεσμένο, και οι επεξεργαστές downstream (όπως οι στατικοί δημιουργοί ιστοτόπων) μπορεί να συγχωνεύσουν ενότητες ακούσια.

Η διατήρηση αυτών των αλλαγών δεν αφορά μόνο την αισθητική· βοηθά επίσης εργαλεία που βασίζονται στα όρια παραγράφων για πράγματα όπως η τοποθέτηση υποσημειώσεων, η προσαρμοσμένη μορφοποίηση ή ακόμη και η εξαγωγή τίτλων φιλικών προς SEO. Συνοπτικά, μια πιστή μετατροπή σέβεται την πρόθεση του συγγραφέα.

## Μετατροπή DOCX σε Markdown με Aspose.Words

Το Aspose.Words σας παρέχει λεπτομερή έλεγχο της διαδικασίας μετατροπής. Η κύρια κλάση είναι `MarkdownSaveOptions`, η οποία σας επιτρέπει να αποφασίσετε πώς θα εξαχθούν οι κενές παράγραφοι. Παρακάτω θα ορίσουμε το `EmptyParagraphExportMode` σε `EmptyLine`, μια λειτουργία που μετατρέπει μια κενή παράγραφο Word σε μια κενή γραμμή Markdown.

### Υλοποίηση βήμα‑βήμα

### 1️⃣ Φόρτωση του Πηγαίου Εγγράφου

Πρώτα, δείξτε τη βιβλιοθήκη στο αρχείο `.docx`. Ο κατασκευαστής `Document` κάνει όλη τη βαριά δουλειά—ανάλυση στυλ, εικόνων και πληροφοριών διάταξης.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Adjust the path to match your environment
string inputPath  = @"C:\Docs\MyReport.docx";
Document doc = new Document(inputPath);
```

> **Γιατί είναι σημαντικό:** Η φόρτωση του εγγράφου νωρίς σας δίνει πρόσβαση στην εσωτερική του δομή, επιτρέποντάς σας να προσαρμόσετε τις επιλογές βάσει του τι ανακαλύπτετε (π.χ., αν το αρχείο περιέχει πραγματικά κενές παραγράφους).

### 2️⃣ Ρύθμιση επιλογών αποθήκευσης Markdown

Εδώ απαντάμε στην ερώτηση **«πώς να εξάγετε κενές»** παραγράφους. Η απαρίθμηση `EmptyParagraphExportMode` προσφέρει τρεις επιλογές:

| Mode | Αποτέλεσμα σε Markdown |
|------|------------------------|
| `EmptyLine` | Εισάγει μια κενή γραμμή (`\n\n`). |
| `PreserveLineBreaks` | Μετατρέπει κάθε αλλαγή γραμμής σε σκληρή αλλαγή (`  \n`). |
| `None` | Παραλείπει εντελώς την κενή παράγραφο. |

Για τις περισσότερες περιπτώσεις όπου απλώς θέλετε ένα οπτικό κενό, το `EmptyLine` κάνει τη δουλειά.

```csharp
MarkdownSaveOptions mdOpts = new MarkdownSaveOptions
{
    // Export empty paragraphs as a single empty line.
    // This is the most intuitive way to keep visual spacing.
    EmptyParagraphExportMode = MarkdownEmptyParagraphExportMode.EmptyLine,

    // Optional: keep original line breaks inside paragraphs.
    // Uncomment if you need finer control.
    // PreserveLineBreaks = true
};
```

> **Συμβουλή:** Αν χρειάζεστε επίσης να διατηρήσετε τις χειροκίνητες αλλαγές γραμμής (Shift + Enter στο Word), ορίστε `PreserveLineBreaks = true`. Με αυτόν τον τρόπο, τόσο οι κενές παράγραφοι όσο και οι ήπιες αλλαγές γραμμής επιβιώνουν το round‑trip.

### 3️⃣ Αποθήκευση του εγγράφου ως Markdown

Τώρα γράφουμε το αρχείο εξόδου. Μπορείτε να επιλέξετε οποιονδήποτε φάκελο θέλετε· απλώς βεβαιωθείτε ότι η επέκταση είναι `.md`.

```csharp
string outputPath = @"C:\Docs\MyReport.md";
doc.Save(outputPath, mdOpts);
Console.WriteLine($"✅ Conversion complete! Markdown saved to {outputPath}");
```

Αυτή είναι ολόκληρη η διαδικασία. Εκτελέστε το πρόγραμμα, ανοίξτε το αρχείο `.md`, και θα δείτε κενές γραμμές ακριβώς εκεί που υπήρχαν στο αρχικό αρχείο Word.

### Πλήρες λειτουργικό παράδειγμα

Συνδυάζοντας όλα τα παραπάνω, εδώ είναι μια αυτόνομη εφαρμογή κονσόλας που μπορείτε να μεταγλωττίσετε άμεσα:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the source DOCX
        string inputPath = @"C:\Docs\input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Set up Markdown options to preserve empty paragraphs
        MarkdownSaveOptions mdOpts = new MarkdownSaveOptions
        {
            EmptyParagraphExportMode = MarkdownEmptyParagraphExportMode.EmptyLine,
            // PreserveLineBreaks = true   // Uncomment if you need soft line breaks
        };

        // 3️⃣ Save as Markdown
        string outputPath = @"C:\Docs\WithEmptyParas.md";
        doc.Save(outputPath, mdOpts);

        Console.WriteLine($"✅ Document converted! Check: {outputPath}");
    }
}
```

**Αναμενόμενο αποτέλεσμα:** Ανοίξτε το `WithEmptyParas.md` σε οποιονδήποτε επεξεργαστή. Θα παρατηρήσετε ότι κάθε κενή γραμμή από το `input.docx` εμφανίζεται ως κενή γραμμή στο αρχείο Markdown, διατηρώντας το οπτικό διαχωρισμό που σχεδιάσατε.

## Αποθήκευση Word ως Markdown – Προχωρημένα σενάρια

### Διαχείριση πινάκων και λιστών

Οι πίνακες στο Word μετατρέπονται αυτόματα σε πίνακες Markdown, αλλά οι κενές γραμμές μπορεί να είναι δύσκολες. Αν μια γραμμή πίνακα περιέχει μόνο ένα κενό κελί, το Aspose.Words το θεωρεί ως κενή παράγραφο. Το `EmptyParagraphExportMode` εξακολουθεί να ισχύει, έτσι θα λάβετε μια κενή γραμμή **εκτός** του πίνακα—όχι μέσα σε αυτόν. Για να διατηρήσετε ένα οπτικό κενό *μέσα* στον πίνακα, εισάγετε ένα μη‑διασπώμενο κενό (`&nbsp;`) στο κελί.

```csharp
// Example: Adding a placeholder to an empty cell
Table table = doc.GetChild(NodeType.Table, 0, true) as Table;
Cell emptyCell = table.Rows[2].Cells[1];
emptyCell.AppendChild(new Paragraph(doc));
emptyCell.FirstParagraph.AppendChild(new Run(doc, "\u00A0")); // non‑breaking space
```

### Μπλοκ κώδικα και προμορφοποιημένο κείμενο

Αν το DOCX σας περιέχει προμορφοποιημένο κώδικα, το Aspose.Words θα τον τυλίξει σε τριπλά backticks. Οι κενές γραμμές μέσα σε μπλοκ κώδικα διατηρούνται αυτόματα, ανεξάρτητα από το `EmptyParagraphExportMode`. Ωστόσο, αν παρατηρήσετε ότι λείπουν κενές γραμμές, ελέγξτε ξανά ότι το αρχικό στυλ παραγράφου Word είναι ορισμένο σε «No Spacing». Με αυτόν τον τρόπο, η βιβλιοθήκη αντιμετωπίζει κάθε γραμμή ως ξεχωριστή παράγραφο.

### Πότε να χρησιμοποιήσετε το `PreserveLineBreaks` αντί αυτού

Μερικές φορές χρειάζεστε μια σκληρή αλλαγή γραμμής (`  `) αντί για μια πλήρη κενή παράγραφο. Για παράδειγμα, η ποίηση ή τα μπλοκ διευθύνσεων συχνά βασίζονται σε μοναδικές αλλαγές γραμμής. Αλλάξτε την επιλογή:

```csharp
mdOpts.PreserveLineBreaks = true;   // Turns soft breaks into Markdown hard breaks
mdOpts.EmptyParagraphExportMode = MarkdownEmptyParagraphExportMode.None; // optional
```

Τώρα κάθε `Shift+Enter` στο Word γίνεται `  \n` στο Markdown, ενώ οι πραγματικά κενές παράγραφοι εξαφανίζονται (εκτός αν διατηρήσετε επίσης το `EmptyLine`).

## Πώς να εξάγετε σωστά κενές παραγράφους

Η σύντομη απάντηση: ορίστε `EmptyParagraphExportMode = MarkdownEmptyParagraphExportMode.EmptyLine`. Η πιο εκτενής απάντηση περιλαμβάνει την κατανόηση *γιατί* λειτουργεί αυτό.

- **EmptyParagraphExportMode** λέει στον σειριοποιητή *τι* να κάνει με μια παράγραφο που δεν περιέχει κανένα run (κείμενο).  
- **EmptyLine** εισάγει ένα διπλό newline, το οποίο το Markdown ερμηνεύει ως διαχωριστικό παραγράφων.  
- Άλλες λειτουργίες είτε συμπτύσσουν την παράγραφο (`None`) είτε αντιμετωπίζουν τις αλλαγές γραμμής ως σκληρές αλλαγές (`PreserveLineBreaks`).  

Αν ξεχάσετε αυτή τη ρύθμιση, η προεπιλεγμένη συμπεριφορά είναι `None`, και όλες οι κενές γραμμές εξαφανίζονται—ακριβώς το πρόβλημα που προσπαθούμε να λύσουμε.

## Πώς να διατηρήσετε τις αλλαγές σε σύνθετα έγγραφα

Τα σύνθετα έγγραφα συχνά συνδυάζουν τίτλους, εικόνες και υποσημειώσεις. Εδώ είναι μια λίστα ελέγχου για να διασφαλίσετε ότι δεν θα χάσετε καμία αλλαγή γραμμής:

| Στοιχείο λίστας ελέγχου | Γιατί είναι σημαντικό |
|--------------------------|------------------------|
| **Validate empty paragraphs** | Χρησιμοποιήστε `doc.GetChildNodes(NodeType.Paragraph, true)` για να μετρήσετε τα κενά πριν από τη μετατροπή. |
| **Enable `PreserveLineBreaks` for poetry** | Εγγυάται ότι οι μοναδικές αλλαγές γραμμής επιβιώνουν. |
| **Check image captions** | Οι λεζάντες είναι ξεχωριστές παράγραφοι· χρειάζονται την ίδια λειτουργία εξαγωγής. |
| **Run a post‑conversion diff** | Συγκρίνετε το αρχικό κείμενο (εξαγόμενο μέσω `doc.GetText()`) με το αποτέλεσμα Markdown. |
| **Test with a Markdown viewer** | Ορισμένοι renderers αντιμετωπίζουν πολλαπλές κενές γραμμές διαφορετικά· επαληθεύστε το οπτικό αποτέλεσμα. |

### Δείγμα κώδικα επικύρωσης

```csharp
// Count empty paragraphs before saving
int emptyCount = 0;
NodeCollection paragraphs = doc.GetChildNodes(NodeType.Paragraph, true);
foreach (Paragraph p in paragraphs)
{
    if (p.GetText().Trim().Length == 0)
        emptyCount++;
}
Console.WriteLine($"Document contains {emptyCount} empty paragraph(s).");
```

Η εκτέλεση αυτού πριν από το βήμα αποθήκευσης σας δίνει την εμπιστοσύνη ότι η μετατροπή θα διαχειριστεί τον ακριβή αριθμό αλλαγών γραμμής που περιμένετε.

## Συνηθισμένα λάθη & επαγγελματικές συμβουλές

- **Pitfall:**

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}