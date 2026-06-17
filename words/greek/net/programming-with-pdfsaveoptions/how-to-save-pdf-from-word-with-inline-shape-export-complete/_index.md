---
category: general
date: 2026-06-02
description: Πώς να αποθηκεύσετε PDF από ένα DOCX χρησιμοποιώντας το Aspose.Words,
  να εξάγετε σχήματα ως ενσωματωμένες ετικέτες span και να μετατρέψετε το Word σε
  PDF σε λίγα μόνο βήματα.
draft: false
keywords:
- how to save pdf
- save docx as pdf
- convert word to pdf
- how to export shapes
- inline span tags
language: el
og_description: Πώς να αποθηκεύσετε PDF από ένα έγγραφο Word χρησιμοποιώντας το Aspose.Words,
  εξάγοντας τα πλωτά σχήματα ως ενσωματωμένες ετικέτες span για ένα καθαρό αποτέλεσμα
  μετατροπής Word σε PDF.
og_title: Πώς να αποθηκεύσετε PDF από το Word – Οδηγός εξαγωγής ενσωματωμένου σχήματος
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: How to save PDF from a DOCX using Aspose.Words, export shapes as inline
    span tags, and convert Word to PDF in just a few steps.
  headline: How to Save PDF from Word with Inline Shape Export – Complete Guide
  type: TechArticle
- description: How to save PDF from a DOCX using Aspose.Words, export shapes as inline
    span tags, and convert Word to PDF in just a few steps.
  name: How to Save PDF from Word with Inline Shape Export – Complete Guide
  steps:
  - name: What if my document contains **SmartArt** or **Charts**?
    text: SmartArt and charts are treated as drawing objects. The `ExportFloatingShapesAsInlineTag`
      flag will still wrap them in `<span>` tags, but complex graphics may lose some
      fidelity. In those cases, consider exporting the chart as an image first (`Chart.ToImage()`)
      and then inserting it inline.
  - name: Can I **preserve hyperlinks** and **bookmarks**?
    text: Absolutely. Those elements are not affected by the `ExportFloatingShapesAsInlineTag`
      setting. Aspose.Words retains all hyperlink and bookmark information automatically.
  - name: How do I **change PDF compression** or **embed fonts**?
    text: '`PdfSaveOptions` offers many additional properties:'
  type: HowTo
tags:
- Aspose.Words
- C#
- PDF conversion
title: Πώς να αποθηκεύσετε PDF από το Word με εξαγωγή ενσωματωμένου σχήματος – Πλήρης
  οδηγός
url: /el/net/programming-with-pdfsaveoptions/how-to-save-pdf-from-word-with-inline-shape-export-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να αποθηκεύσετε PDF από το Word με εξαγωγή ενσωματωμένων σχημάτων – Πλήρης Οδηγός

Έχετε αναρωτηθεί ποτέ **πώς να αποθηκεύσετε PDF** από ένα αρχείο Word ενώ διατηρείτε κάθε αιωρούμενο σχήμα τακτοποιημένο στη ροή; Δεν είστε ο μόνος. Σε πολλές επιχειρησιακές εφαρμογές πρέπει να *μετατρέψουμε το Word σε PDF* χωρίς να καταλήξουμε με λανθασμένες εικόνες ή αδέσποτα αντικείμενα σχεδίασης. Τα καλά νέα; Το Aspose.Words το κάνει εύκολο, και μπορείτε ακόμη να πείτε στη βιβλιοθήκη να **εξάγει σχήματα ως ενσωματωμένες ετικέτες `<span>`** ώστε το PDF να φαίνεται ακριβώς όπως το αρχικό DOCX.

Σε αυτό το tutorial θα περάσουμε από όλη τη διαδικασία — φόρτωση ενός DOCX, ρύθμιση του `PdfSaveOptions`, και τελικά αποθήκευση ενός καθαρού PDF. Στο τέλος θα γνωρίζετε **πώς να αποθηκεύσετε PDF**, **να αποθηκεύσετε docx ως pdf**, και ακόμη **πώς να εξάγετε σχήματα** χρησιμοποιώντας *ενσωματωμένες ετικέτες span*.

## Τι Θα Χρειαστεί

- **Aspose.Words for .NET** (τελευταία έκδοση, 24.x τη στιγμή της συγγραφής).  
- **.NET 6.0** ή νεότερο — ο κώδικας λειτουργεί και σε .NET Framework 4.7.2, αλλά το .NET 6 είναι η ιδανική επιλογή.  
- Ένα απλό έγγραφο Word που περιέχει τουλάχιστον ένα αιωρούμενο σχήμα (εικόνα, πλαίσιο κειμένου ή σχέδιο).  
- Οποιοδήποτε IDE προτιμάτε (Visual Studio, Rider, VS Code + C# extension).  

Αυτό είναι όλο — χωρίς επιπλέον πακέτα NuGet, χωρίς περίπλοκο COM interop. Έτοιμοι; Ας βουτήξουμε.

## Βήμα 1: Ρύθμιση του Έργου και Προσθήκη του Aspose.Words

Πρώτα, δημιουργήστε μια εφαρμογή κονσόλας (ή ενσωματώστε τον κώδικα στην υπάρχουσα υπηρεσία σας).

```bash
dotnet new console -n WordToPdfDemo
cd WordToPdfDemo
dotnet add package Aspose.Words
```

> **Συμβουλή:** Αν χρησιμοποιείτε Visual Studio, μπορείτε να προσθέσετε το πακέτο μέσω του UI του NuGet Package Manager — απλώς αναζητήστε *Aspose.Words*.

## Βήμα 2: Φόρτωση του Πηγαίου Εγγράφου

Τώρα που η βιβλιοθήκη έχει αναφερθεί, μπορούμε να φορτώσουμε το DOCX. Αυτό είναι το πρώτο συγκεκριμένο βήμα του **πώς να αποθηκεύσετε pdf** — η λήψη του πηγαίου αρχείου στη μνήμη.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Step 2: Load the source document
        // Replace YOUR_DIRECTORY with the actual path on your machine.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
        Console.WriteLine("Document loaded successfully.");
```

**Γιατί είναι σημαντικό:** Η φόρτωση του αρχείου επαληθεύει ότι η διαδρομή είναι σωστή και ότι το Aspose μπορεί να αναλύσει τη δομή του Word. Αν το αρχείο περιέχει αιωρούμενα σχήματα, θα είναι μέρος του δέντρου κόμβων του αντικειμένου `Document`.

## Βήμα 3: Διαμόρφωση των Ρυθμίσεων Αποθήκευσης PDF — Εξαγωγή Σχημάτων ως Ενσωματωμένες Ετικέτες

Αυτή είναι η ουσία του **πώς να εξάγετε σχήματα**. Από προεπιλογή, το Aspose.Words αποδίδει τα αιωρούμενα σχήματα ως ξεχωριστά αντικείμενα στο PDF, κάτι που μπορεί να μετατοπίσει τη διάταξη. Ορίζοντας το `ExportFloatingShapesAsInlineTag` σε `true` λέτε στη μηχανή να τυλίξει κάθε σχήμα σε μια ενσωματωμένη ετικέτα `<span>`, διατηρώντας τη ροή.

```csharp
        // Step 3: Configure PDF save options to export floating shapes as inline <span> tags
        PdfSaveOptions pdfOpts = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true,
            // Optional: keep the original page size
            PageMode = PdfPageMode.UseTrimBox
        };
        Console.WriteLine("PDF save options configured – shapes will be inline.");
```

**Γιατί να ενεργοποιήσετε αυτή τη σημαία;** Φανταστείτε ένα συμβόλαιο με πλαίσιο υπογραφής που αιωρείται πάνω από το κείμενο. Όταν το μετατρέπετε σε PDF χωρίς αυτή τη ρύθμιση, το πλαίσιο μπορεί να εμφανιστεί σε διαφορετική σελίδα. Οι ενσωματωμένες ετικέτες `<span>` κρατούν το σχήμα δεσμευμένο στην παραγράφου του, δημιουργώντας μια πιστή οπτική αναπαραγωγή.

## Βήμα 4: Αποθήκευση του Εγγράφου ως PDF

Τέλος, καλούμε το `doc.Save` με τις επιλογές που μόλις δημιουργήσαμε. Αυτή είναι η στιγμή που πραγματικά **αποθηκεύετε docx ως pdf**.

```csharp
        // Step 4: Save the document as a PDF using the configured options
        string outputPath = @"YOUR_DIRECTORY\output.pdf";
        doc.Save(outputPath, pdfOpts);
        Console.WriteLine($"PDF saved successfully to: {outputPath}");
    }
}
```

Εκτελέστε το πρόγραμμα (`dotnet run`) και ελέγξτε το `output.pdf`. Θα πρέπει να δείτε τα αιωρούμενα σχήματά σας αποδομένα ενσωματωμένα, όπως εμφανίστηκαν στο Word.

## Βήμα 5: Επαλήθευση του Αποτελέσματος — Γρήγορη Λίστα Ελέγχου

1. **Όλο το κείμενο είναι παρόν** — χωρίς ελλιπείς παραγράφους.  
2. **Τα αιωρούμενα σχήματα εμφανίζονται όπου πρέπει** — είναι τώρα μέρος της ροής του κειμένου.  
3. **Το μέγεθος του PDF είναι λογικό** — η εξαγωγή ως ενσωματωμένες ετικέτες συνήθως μειώνει το βάρος του αρχείου σε σύγκριση με ξεχωριστά ρεύματα εικόνων.  

Αν κάτι φαίνεται λανθασμένο, ελέγξτε ξανά ότι το πηγαίο DOCX χρησιμοποιεί πραγματικά *αιωρούμενα* σχήματα (δεξί κλικ → Διάταξη → “Σε σειρά με το κείμενο” vs “Τετράγωνο/Πίσω από το κείμενο”). Η αλλαγή ενός σχήματος σε “Σε σειρά” πριν τη μετατροπή λειτουργεί επίσης, αλλά η επιλογή ενσωματωμένης ετικέτας σας δίνει έλεγχο χωρίς να επεξεργαστείτε το αρχικό αρχείο.

## Περιπτώσεις Άκρων & Συχνές Ερωτήσεις

### Τι γίνεται αν το έγγραφό μου περιέχει **SmartArt** ή **Charts**;

Το SmartArt και τα διαγράμματα αντιμετωπίζονται ως αντικείμενα σχεδίασης. Η σημαία `ExportFloatingShapesAsInlineTag` θα τα τυλίξει ακόμη σε ετικέτες `<span>`, αλλά τα πολύπλοκα γραφικά μπορεί να χάσουν κάποια πιστότητα. Σε αυτές τις περιπτώσεις, σκεφτείτε να εξάγετε το διάγραμμα ως εικόνα πρώτα (`Chart.ToImage()`) και μετά να το ενσωματώσετε inline.

### Μπορώ να **διατηρήσω υπερσυνδέσμους** και **σελιδοδείκτες**;

Απολύτως. Αυτά τα στοιχεία δεν επηρεάζονται από τη ρύθμιση `ExportFloatingShapesAsInlineTag`. Το Aspose.Words διατηρεί αυτόματα όλες τις πληροφορίες υπερσυνδέσμων και σελιδοδεικτών.

### Πώς μπορώ να **αλλάξω τη συμπίεση PDF** ή να **ενσωματώσω γραμματοσειρές**;

`PdfSaveOptions` προσφέρει πολλές επιπλέον ιδιότητες:

```csharp
pdfOpts.JpegQuality = 90;               // Adjust image compression
pdfOpts.FontEmbeddingMode = FontEmbeddingMode.EmbedAll; // Embed all used fonts
```

## Πλήρες Παράδειγμα Εργασίας (Έτοιμο για Αντιγραφή‑Επικόλληση)

Παρακάτω είναι το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε στο `Program.cs`. Αντικαταστήστε το `YOUR_DIRECTORY` με μια πραγματική διαδρομή φακέλου.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Load the source DOCX (contains floating shapes)
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
        Console.WriteLine("Document loaded.");

        // Configure PDF save options – export shapes as inline <span> tags
        PdfSaveOptions pdfOpts = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true,
            PageMode = PdfPageMode.UseTrimBox,
            // Optional tweaks
            JpegQuality = 90,
            FontEmbeddingMode = FontEmbeddingMode.EmbedAll
        };
        Console.WriteLine("PDF options set – shapes will be inline.");

        // Save as PDF
        string outputPath = @"YOUR_DIRECTORY\output.pdf";
        doc.Save(outputPath, pdfOpts);
        Console.WriteLine($"PDF saved to {outputPath}");
    }
}
```

**Αναμενόμενη έξοδος στην κονσόλα:**

```
Document loaded.
PDF options set – shapes will be inline.
PDF saved to C:\MyDocs\output.pdf
```

Ανοίξτε το `output.pdf` — θα δείτε την αρχική διάταξη, με κάθε αιωρούμενο σχήμα τοποθετημένο στενά μέσα στη ροή του κειμένου.

## Συμπέρασμα

Καλύψαμε **πώς να αποθηκεύσετε PDF** από ένα έγγραφο Word διασφαλίζοντας ότι τα αιωρούμενα σχήματα γίνονται ενσωματωμένες ετικέτες `<span>`. Φορτώνοντας το DOCX, διαμορφώνοντας το `PdfSaveOptions` και καλώντας το `doc.Save`, μπορείτε αξιόπιστα να **αποθηκεύσετε docx ως pdf** και να **μετατρέψετε το word σε pdf** χωρίς εκπλήξεις στη διάταξη.  

Τι επόμενο; Δοκιμάστε να συνδυάσετε αυτήν την προσέγγιση με συμμόρφωση **PDF/A** για αρχειοθέτηση, ή να επεξεργαστείτε μαζικά έναν φάκελο αρχείων DOCX με έναν απλό βρόχο `foreach`. Μπορείτε επίσης να εξερευνήσετε **προσαρμοστική απόδοση** (π.χ., προσθήκη υδατογραφήματος) αξιοποιώντας το API `DocumentVisitor` του Aspose.Words.

Έχετε περισσότερες ερωτήσεις σχετικά με τη διαχείριση σχημάτων, την ενσωμάτωση γραμματοσειρών ή τη βελτιστοποίηση απόδοσης; Αφήστε ένα σχόλιο παρακάτω, και καλή προγραμματιστική!

## Τι Θα Μάθετε Στη Σύντομη Μελλοντική

Τα παρακάτω tutorials καλύπτουν στενά σχετικές θεματικές που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να αποθηκεύσετε έγγραφο ως pdf με Aspose.Words για Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Μετατροπή Word σε PDF με Aspose.Words για Java](/words/english/java/document-converting/exporting-documents-to-pdf/)
- [aspose word to pdf – Μετατροπή DOCX σε PDF σε Java](/words/english/java/document-conversion-and-export/aspose-word-to-pdf-convert-docx-to-pdf-in-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}