---
category: general
date: 2026-02-18
description: Μάθετε πώς να αποθηκεύετε ένα έγγραφο ως txt χρησιμοποιώντας το Aspose.Words
  για C#. Αυτός ο οδηγός βήμα‑βήμα δείχνει επίσης πώς να μετατρέψετε docx σε txt και
  να ορίσετε την κωδικοποίηση.
draft: false
keywords:
- save document as txt
- convert docx to txt
- how to convert docx
- how to export math
- how to set encoding
language: el
og_description: Αποθηκεύστε το έγγραφο ως txt με το Aspose.Words για C#. Μάθετε πώς
  να μετατρέψετε docx σε txt, να εξάγετε μαθηματικά ως απλό κείμενο και να ορίσετε
  τη σωστή κωδικοποίηση.
og_title: Αποθήκευση εγγράφου ως TXT σε C# – Μετατροπή DOCX σε TXT
tags:
- C#
- Aspose.Words
- Text Export
title: Αποθήκευση εγγράφου ως TXT σε C# – Μετατροπή DOCX σε TXT
url: /el/net/programming-with-txtsaveoptions/save-document-as-txt-in-c-convert-docx-to-txt/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Αποθήκευση Εγγράφου ως TXT σε C# – Μετατροπή DOCX σε TXT

Έχετε χρειαστεί ποτέ να **save document as txt** αλλά η πηγή σας είναι ένα αρχείο Word; Δεν είστε μόνοι. Σε πολλές γραμμές αυτοματοποίησης λαμβάνουμε αναφορές DOCX, ενώ τα συστήματα downstream καταλαβαίνουν μόνο plain‑text. Τα καλά νέα; Με λίγες γραμμές C# μπορείτε να **convert docx to txt**, να διατηρήσετε χαρακτήρες Unicode και ακόμη να εξάγετε Office Math ως αναγνώσιμα σύμβολα—όλα χωρίς να φύγετε από το IDE σας.

Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα ένα πλήρες, έτοιμο‑για‑εκτέλεση παράδειγμα που δείχνει *how to set encoding*, *how to export math* και *how to convert docx* σε ένα καθαρό αρχείο `.txt`. Στο τέλος θα έχετε ένα επαναχρησιμοποιήσιμο snippet που μπορείτε να ενσωματώσετε σε οποιοδήποτε .NET project.

## Τι Θα Χρειαστεί

- **Aspose.Words for .NET** (οποιαδήποτε πρόσφατη έκδοση· το API δεν έχει αλλάξει από το 2023)
- .NET 6 ή νεότερο (ο κώδικας λειτουργεί επίσης σε .NET Framework 4.7+)
- Ένα αρχείο DOCX που θέλετε να μετατρέψετε σε plain text  
  (κρατήστε το απλό στην αρχή—ίσως ένα συμβόλαιο μιας σελίδας ή ένα δείγμα αναφοράς)

Αυτό είναι όλο. Χωρίς επιπλέον πακέτα NuGet, χωρίς περίπλοκο COM interop, μόνο καθαρό C#.

## Υλοποίηση Βήμα‑Βήμα

Παρακάτω χωρίζουμε τη διαδικασία σε τρία λογικά στάδια. Κάθε στάδιο έχει τη δική του επικεφαλίδα H2, και η κύρια λέξη-κλειδί **save document as txt** εμφανίζεται ακριβώς στην πρώτη επικεφαλίδα για να ικανοποιήσει το SEO.

### Πώς να Αποθηκεύσετε Έγγραφο ως TXT – Φόρτωση του Πηγαίου DOCX

Πρώτα πρέπει να φορτώσουμε το αρχείο Word στη μνήμη. Το Aspose.Words αντιπροσωπεύει οποιοδήποτε έγγραφο με την κλάση `Document`, η οποία αφαιρεί τις λεπτομέρειες του μορφότυπου αρχείου.

```csharp
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.Saving;

class TxtExportDemo
{
    static void Main()
    {
        // 👉 Step 1: Load the source DOCX file
        // Replace the path with your actual file location.
        Document doc = new Document(@"C:\MyFiles\input.docx");
```

**Γιατί είναι σημαντικό:** Η φόρτωση του εγγράφου μία φορά μας επιτρέπει να επαναχρησιμοποιήσουμε το ίδιο αντικείμενο `doc` για πολλαπλές μορφές εξαγωγής αργότερα. Επίσης, επικυρώνει ότι το αρχείο είναι γνήσιο DOCX, ρίχνοντας εξαίρεση νωρίς αν κάτι δεν πάει καλά.

### Διαμόρφωση TxtSaveOptions – Ορισμός Κωδικοποίησης και Εξαγωγή Μαθηματικών

Τώρα έρχεται η ουσία: να πούμε στο Aspose πώς να γράψει το αρχείο plain‑text. Η κλάση `TxtSaveOptions` μας δίνει λεπτομερή έλεγχο της κωδικοποίησης χαρακτήρων και του τρόπου απόδοσης των αντικειμένων Office Math.

```csharp
        // 👉 Step 2: Configure TXT save options
        TxtSaveOptions txtOptions = new TxtSaveOptions
        {
            // Preserve Unicode characters (e.g., emojis, non‑Latin scripts)
            Encoding = Encoding.UTF8,

            // Export Office Math as plain text instead of LaTeX markup
            OfficeMathExportMode = TxtSaveOptions.OfficeMathExportMode.PlainText
        };
```

- **How to set encoding:** Αναθέτοντας `Encoding.UTF8` εγγυόμαστε ότι όλοι οι ειδικοί χαρακτήρες θα παραμείνουν μετά τη μετατροπή. Αν χρειάζεστε Windows‑1252 για παλαιά συστήματα, απλώς αλλάξτε την τιμή του enum—*how to set encoding* είναι τόσο απλό.
- **How to export math:** Η σημαία `OfficeMathExportMode` ελέγχει αν οι εξισώσεις θα γίνουν LaTeX (`LaTeX`) ή plain‑text (`PlainText`). Για τους περισσότερους downstream parsers, το plain text είναι η πιο ασφαλής επιλογή.

### Αποθήκευση του Εγγράφου ως TXT – Τελικό Αποτέλεσμα

Με τις επιλογές έτοιμες, η εγγραφή του αρχείου γίνεται με μία γραμμή κώδικα. Αυτή είναι η στιγμή που πραγματικά **save document as txt**.

```csharp
        // 👉 Step 3: Save the document as a plain‑text file
        string outputPath = @"C:\MyFiles\PlainText.txt";
        doc.Save(outputPath, txtOptions);

        Console.WriteLine($"Document successfully saved as TXT at: {outputPath}");
    }
}
```

Μετά την εκτέλεση, ανοίξτε το `PlainText.txt` σε οποιονδήποτε επεξεργαστή. Θα δείτε το ακατέργαστο κειμενικό περιεχόμενο του `input.docx`, τα σύμβολα Unicode άθικτα, και τις εξισώσεις αποδομένες ως κάτι όπως `a + b = c`.

> **Pro tip:** Αν επεξεργάζεστε πολλά αρχεία σε batch, τυλίξτε την κλήση `doc.Save` σε ένα μπλοκ `try/catch` και καταγράψτε τις αποτυχίες. Αυτό αποτρέπει ένα μόνο κατεστραμμένο DOCX να σταματήσει ολόκληρη τη γραμμή.

### Μετατροπή DOCX σε TXT με Διαφορετικές Κωδικοποιήσεις (Προαιρετικό)

Μερικές φορές τα παλαιά συστήματα απαιτούν ANSI ή UTF‑16. Ο ίδιος κώδικας λειτουργεί—απλώς αλλάξτε την ιδιότητα `Encoding`:

```csharp
txtOptions.Encoding = Encoding.Unicode; // UTF‑16 LE
// or
txtOptions.Encoding = Encoding.GetEncoding("windows-1252"); // ANSI
```

Αυτή είναι η απλή απάντηση στο *how to set encoding* για εξαγωγή TXT.

### Εξαγωγή Office Math ως Plain Text vs. LaTeX (Τι Αν Χρειάζεστε LaTeX;)

Αν ο downstream καταναλωτής σας είναι μια μηχανή επιστημονικής τυπογραφίας, ίσως προτιμάτε σήμανση LaTeX:

```csharp
txtOptions.OfficeMathExportMode = TxtSaveOptions.OfficeMathExportMode.LaTeX;
```

Η αλλαγή της σημαίας είναι ό,τι χρειάζεται—χωρίς επιπλέον βιβλιοθήκες. Αυτό απαντά στην περιέργεια “*how to export math*” που έχουν πολλοί προγραμματιστές όταν ασχολούνται με εξισώσεις.

## Αναμενόμενο Αποτέλεσμα & Επαλήθευση

Η εκτέλεση του προγράμματος δημιουργεί το `PlainText.txt`. Ένας γρήγορος έλεγχος λογικής:

```text
This is a sample paragraph from the original DOCX.
Here’s a bullet list:
• Item one
• Item two

Equation example (plain text):
a + b = c
```

Αν ανοίξετε το αρχείο και δείτε την ίδια δομή, έχετε μετατρέψει επιτυχώς **converted docx to txt**. Για μεγάλα έγγραφα, συγκρίνετε τα μεγέθη αρχείων πριν και μετά· το TXT θα πρέπει να είναι πολύ μικρότερο, επιβεβαιώνοντας ότι μόνο το κείμενο επέζησε της μετατροπής.

## Συνηθισμένα Πιθανά Προβλήματα & Ακραίες Περιπτώσεις

| Πρόβλημα | Γιατί Συμβαίνει | Διόρθωση |
|-------|----------------|-----|
| Missing Unicode characters | Using `Encoding.ASCII` by default | Switch to `Encoding.UTF8` (see *how to set encoding*) |
| Equations appear as `\\[...\\]` | `OfficeMathExportMode` left at default (`LaTeX`) | Set to `PlainText` to get readable symbols |
| File path not found | Hard‑coded path points to a non‑existent folder | Use `Path.Combine` or ensure the directory exists |
| Large DOCX (hundreds of MB) causes OOM | Loading whole document in memory | Process in chunks with `Document.Save` streaming options (advanced) |

Η γνώση αυτών των σεναρίων σας εξοικονομεί χρόνο εντοπισμού σφαλμάτων αργότερα.

## Πλήρες Παράδειγμα Εργασίας (Έτοιμο για Αντιγραφή‑Επικόλληση)

```csharp
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.Saving;

class TxtExportDemo
{
    static void Main()
    {
        // Load the source DOCX
        Document doc = new Document(@"C:\MyFiles\input.docx");

        // Configure save options: UTF‑8 encoding and plain‑text math export
        TxtSaveOptions txtOptions = new TxtSaveOptions
        {
            Encoding = Encoding.UTF8,
            OfficeMathExportMode = TxtSaveOptions.OfficeMathExportMode.PlainText
        };

        // Save as plain‑text
        string outputPath = @"C:\MyFiles\PlainText.txt";
        doc.Save(outputPath, txtOptions);

        Console.WriteLine($"Document successfully saved as TXT at: {outputPath}");
    }
}
```

Εκτελέστε αυτό το snippet και θα έχετε μια καθαρή έκδοση `.txt` οποιουδήποτε DOCX στο οποίο δείχνετε. Ο κώδικας είναι αυτόνομος· δεν απαιτούνται εξωτερικά αρχεία ρυθμίσεων ή πρόσθετες βιβλιοθήκες.

## Επόμενα Βήματα & Σχετικά Θέματα

- **Batch conversion:** Επανάληψη πάνω σε έναν φάκελο αρχείων DOCX και επαναχρησιμοποίηση του ίδιου αντικειμένου `TxtSaveOptions`.  
- **Streaming large files:** Εξερευνήστε το `Document.Save(Stream, SaveOptions)` για άμεση εγγραφή σε ροή δικτύου.  
- **Other export formats:** Το ίδιο αντικείμενο `Document` μπορεί να παράγει PDF, HTML ή Markdown—ιδανικό αν αργότερα αποφασίσετε *how to convert docx* σε πιο πλούσιες μορφές.  
- **Advanced encoding:** Για ασιατικές γλώσσες, σκεφτείτε `Encoding.GetEncoding("utf-8")` με BOM ή `Encoding.BigEndianUnicode`.

Κάθε ένα από αυτά βασίζεται στην κεντρική ιδέα του **save document as txt** ενώ επεκτείνει το εργαλείο σας για αυτοματοποίηση εγγράφων.

---

**Συνοπτικά:** Τώρα ξέρετε πώς να *save document as txt* σε C#, πώς να *convert docx to txt*, τον σωστό τρόπο για *set encoding*, και τη γρήγορη μέθοδο για *export math* ως plain text. Ενσωματώστε τον κώδικα στο project σας, προσαρμόστε τις επιλογές στο περιβάλλον σας, και θα διαχειρίζεστε εξαγωγές plain‑text σαν επαγγελματίας.

Έχετε ερωτήσεις ή ένα δύσκολο DOCX που δεν συνεργάζεται; Αφήστε ένα σχόλιο παρακάτω και ας το αντιμετωπίσουμε μαζί. Καλό προγραμματισμό!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}