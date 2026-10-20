---
category: general
date: 2026-06-30
description: Αποθήκευση εγγράφου ως PDF σε C# ενώ μετατρέπετε docx σε PDF και διαχειρίζεστε
  ενσωματωμένα σχήματα. Ακολουθήστε αυτόν τον οδηγό βήμα‑βήμα για να εξάγετε σωστά
  το Word σε PDF.
draft: false
keywords:
- save document as pdf
- convert docx to pdf
- convert word to pdf
- save word as pdf
- how to export inline
language: el
og_description: Αποθήκευση εγγράφου ως PDF σε C# με το Aspose.Words. Μάθετε πώς να
  μετατρέψετε docx σε PDF και να εξάγετε τα αιωρούμενα σχήματα ως ενσωματωμένα στοιχεία.
og_title: Αποθήκευση εγγράφου ως PDF σε C# – Εξαγωγή ενσωματωμένων σχημάτων
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Save document as PDF in C# while converting docx to PDF and handling
    inline shapes. Follow this step‑by‑step guide to export Word to PDF correctly.
  headline: Save Document as PDF in C# – Export Inline Shapes
  type: TechArticle
- description: Save document as PDF in C# while converting docx to PDF and handling
    inline shapes. Follow this step‑by‑step guide to export Word to PDF correctly.
  name: Save Document as PDF in C# – Export Inline Shapes
  steps:
  - name: '**.NET 6+** (or .NET Framework 4.6+).'
    text: '**.NET 6+** (or .NET Framework 4.6+).'
  - name: The **Aspose.Words for .NET** NuGet package (`Install-Package Aspose.Words`).
    text: The **Aspose.Words for .NET** NuGet package (`Install-Package Aspose.Words`).
  - name: A sample `input.docx` that contains at least one floating picture or text
      box.
    text: A sample `input.docx` that contains at least one floating picture or text
      box.
  type: HowTo
tags:
- C#
- PDF
- Aspose.Words
title: Αποθήκευση εγγράφου ως PDF σε C# – Εξαγωγή ενσωματωμένων σχημάτων
url: /el/net/programming-with-pdfsaveoptions/save-document-as-pdf-in-c-export-inline-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Αποθήκευση Εγγράφου ως PDF σε C# – Εξαγωγή Σχημάτων Inline

Έχετε αναρωτηθεί ποτέ πώς να **αποθηκεύσετε ένα έγγραφο ως PDF** απευθείας από C# χωρίς να χάσετε τη διάταξη των πλωτών εικόνων; Δεν είστε οι μόνοι. Πολλοί προγραμματιστές συναντούν πρόβλημα όταν ένα αρχείο Word περιέχει εικόνες ή πλαίσια κειμένου που «πλέουν» πάνω από το κείμενο — αυτά τα στοιχεία συχνά εξαφανίζονται ή μετατοπίζονται όταν απλώς καλέσετε `doc.Save("output.pdf")`.  

Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα τις ακριβείς ενέργειες για **μετατροπή docx σε pdf** διατηρώντας τα πλωτά αντικείμενα ως στοιχεία inline, απαντώντας ουσιαστικά στο *πώς να εξάγετε σχήματα inline*. Στο τέλος θα έχετε ένα έτοιμο‑για‑εκτέλεση snippet που **αποθηκεύει το Word ως pdf** όπως περιμένετε.

## Τι Θα Μάθετε

- Φόρτωση αρχείου `.docx` με Aspose.Words (ή οποιαδήποτε συμβατή βιβλιοθήκη).  
- Διαμόρφωση του `PdfSaveOptions` ώστε τα πλωτά σχήματα να γίνουν inline.  
- Εκτέλεση της λειτουργίας αποθήκευσης για **μετατροπή word σε pdf**.  
- Διαχείριση κοινών προβλημάτων όπως ελλιπείς γραμματοσειρές ή μεγάλες εικόνες.  

Χωρίς εξωτερικά εργαλεία, χωρίς χειροκίνητη παρέμβαση σε COM αντικείμενα Word‑automation — μόνο καθαρός, αγνός κώδικας C#.

---

## Προαπαιτούμενα

Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε:

1. **.NET 6+** (ή .NET Framework 4.6+).  
2. Το **Aspose.Words for .NET** πακέτο NuGet (`Install-Package Aspose.Words`).  
3. Ένα δείγμα `input.docx` που περιέχει τουλάχιστον μία πλωτή εικόνα ή πλαίσιο κειμένου.  

Αν χρησιμοποιείτε διαφορετική βιβλιοθήκη PDF, οι έννοιες παραμένουν ίδιες — ψάξτε για μια ιδιότητα παρόμοια με `ExportFloatingShapesAsInlineTag`.

---

## Βήμα 1: Φόρτωση του Πηγής Εγγράφου – Βασικά της Αποθήκευσης Εγγράφου ως PDF  

Το πρώτο πράγμα είναι να φέρετε το αρχείο Word στη μνήμη. Εδώ αρχίζει η διαδικασία **αποθήκευσης εγγράφου ως pdf**.

```csharp
using Aspose.Words;

// Step 1: Load the source DOCX file
string inputPath = @"C:\MyDocs\input.docx";
Document doc = new Document(inputPath);
```

*Γιατί είναι σημαντικό*: Η φόρτωση του εγγράφου επαληθεύει ότι το αρχείο υπάρχει και αναλύει όλα τα τμήματά του (στυλ, εικόνες, κεφαλίδες). Αν η φόρτωση αποτύχει, η μετατροπή σε PDF δεν θα εκτελεστεί ποτέ, οπότε ο εντοπισμός σφαλμάτων εδώ σας εξοικονομεί πολύ χρόνο.

---

## Βήμα 2: Διαμόρφωση Επιλογών PDF Save – Πώς να Εξάγετε Σχήματα Inline  

Τώρα λέμε στη βιβλιοθήκη πώς να αντιμετωπίζει τα πλωτά σχήματα. Η βασική σημαία είναι `ExportFloatingShapesAsInlineTag`. Ορίζοντάς την σε `true` εξαναγκάζουμε κάθε πλωτή εικόνα ή πλαίσιο κειμένου να αποδοθεί **inline**, όπως ένα κανονικό τμήμα παραγράφου.

```csharp
// Step 2: Prepare PDF save options
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    // true → inline (text‑flow); false → keep as block‑level floating objects
    ExportFloatingShapesAsInlineTag = true,

    // Optional: improve compatibility with older PDF viewers
    Compliance = PdfCompliance.PdfA1b
};
```

*Γιατί είναι σημαντικό*: Από προεπιλογή, το Aspose.Words διατηρεί τα πλωτά σχήματα στη θέση τους, κάτι που μπορεί να τα κόψει ή να τα αφαιρέσει στο τελικό PDF. Η ενεργοποίηση της εξαγωγής inline εξασφαλίζει ότι τα σχήματα γίνονται μέρος της ροής κειμένου, διατηρώντας την οπτική πιστότητα σε όλους τους αναγνώστες PDF.

---

## Βήμα 3: Αποθήκευση του Εγγράφου ως PDF – Μετατροπή Word σε PDF  

Με το έγγραφο φορτωμένο και τις επιλογές ρυθμισμένες, το τελευταίο βήμα είναι μια γραμμή κώδικα που πραγματικά **αποθηκεύει το έγγραφο ως pdf**.

```csharp
// Step 3: Save the document as a PDF file
string outputPath = @"C:\MyDocs\FloatingShapes.pdf";
doc.Save(outputPath, pdfOptions);
```

Αυτό είναι! Η κλήση `doc.Save` γράφει ένα PDF που αντικατοπτρίζει την αρχική διάταξη του Word, με τις πλωτές εικόνες τώρα ενσωματωμένες ομαλά μέσα στο κείμενο.

---

## Πλήρες Παράδειγμα Λειτουργίας  

Συνδυάζοντας τα παραπάνω, εδώ είναι μια αυτόνομη εφαρμογή κονσόλας που μπορείτε να αντιγράψετε‑επικολλήσετε, να μεταγλωττίσετε και να τρέξετε:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

namespace WordToPdfInlineExport
{
    class Program
    {
        static void Main(string[] args)
        {
            // Paths – adjust to your environment
            string inputPath = @"C:\MyDocs\input.docx";
            string outputPath = @"C:\MyDocs\FloatingShapes.pdf";

            // Load the DOCX file
            Document doc = new Document(inputPath);

            // Configure PDF options to export floating shapes as inline
            PdfSaveOptions pdfOptions = new PdfSaveOptions
            {
                ExportFloatingShapesAsInlineTag = true,
                Compliance = PdfCompliance.PdfA1b // optional, ensures PDF/A‑1b compliance
            };

            // Save as PDF
            doc.Save(outputPath, pdfOptions);

            Console.WriteLine($"Document successfully saved as PDF: {outputPath}");
        }
    }
}
```

**Αναμενόμενη έξοδος** (στην κονσόλα):

```
Document successfully saved as PDF: C:\MyDocs\FloatingShapes.pdf
```

Ανοίξτε το `FloatingShapes.pdf` σε οποιονδήποτε προβολέα· θα δείτε την προηγούμενη πλωτή εικόνα τώρα ενσωματωμένη μέσα στην παράγραφο, όπως προοριζόταν.

---

## Γιατί να Εξάγετε Πλωτά Σχήματα ως Inline;  

Τα πλωτά σχήματα είναι χρήσιμα στο Word επειδή σας επιτρέπουν να τοποθετείτε εικόνες οπουδήποτε στη σελίδα. Ωστόσο, το PDF είναι μορφή *προσανατολισμένη στη σελίδα* — δεν υπάρχει η έννοια του «float» όπως στο Word. Όταν η μηχανή μετατροπής τα αφήνει ως αντικείμενα block‑level, μπορούν:

- Να επικαλύψουν άλλο περιεχόμενο.  
- Να κοπούν στα περιθώρια της σελίδας.  
- Να εξαφανιστούν εντελώς σε παλαιότερους αναγνώστες PDF.

Με τη μετατροπή τους σε **inline** στοιχεία, εξασφαλίζετε ότι το PDF σέβεται τη σειρά ανάγνωσης και ότι οι αναγνώστες οθόνης μπορούν να ερμηνεύσουν το έγγραφο σωστά — σημαντικό για συμμόρφωση προσβασιμότητας.

---

## Συνηθισμένα Προβλήματα Κατά τη Μετατροπή Docx σε PDF  

| Πρόβλημα | Συμπτωμα | Διόρθωση |
|----------|----------|----------|
| Ελλιπείς γραμματοσειρές | Το κείμενο εμφανίζεται ως “□” ή επιστρέφει σε Arial | Ενσωματώστε γραμματοσειρές μέσω `PdfSaveOptions.FontEmbeddingMode = FontEmbeddingMode.Always`. |
| Μεγάλες εικόνες προκαλούν άλματα μνήμης | Εξαίρεση Out‑of‑memory σε μεγάλο DOCX | Μειώστε την ανάλυση των εικόνων πριν τη μετατροπή ή ορίστε `PdfSaveOptions.ImageCompression = PdfImageCompression.Jpeg;` |
| Η εξαγωγή inline δεν εφαρμόζεται | Τα πλωτά σχήματα παραμένουν πλωτά στο PDF | Βεβαιωθείτε ότι χρησιμοποιείτε την πιο πρόσφατη έκδοση του Aspose.Words· το όνομα της ιδιότητας άλλαξε σε παλαιότερες εκδόσεις. |
| Σφάλματα διαδρομής | `FileNotFoundException` | Χρησιμοποιήστε `Path.Combine` και βεβαιωθείτε ότι ο φάκελος υπάρχει (`Directory.CreateDirectory`). |

---

## Προχωρημένο: Εξαγωγή Μόνο Συγκεκριμένων Σχημάτων Inline  

Μερικές φορές θέλετε *επιλεκτική* μετατροπή σε inline — μόνο ορισμένες εικόνες, όχι όλες. Μπορείτε να το πετύχετε αυτό διασχίζοντας τους κόμβους του εγγράφου πριν την αποθήκευση:

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.WrapType == WrapType.Inline)
        continue; // already inline

    // Example condition: only convert pictures larger than 300px
    if (shape.HasImage && shape.Width > 300)
        shape.WrapType = WrapType.Inline;
}
```

Αφού προσαρμόσετε το `WrapType`, εκτελέστε ξανά την κλήση `doc.Save`. Αυτό σας δίνει λεπτομερή έλεγχο στη συμπεριφορά **πώς να εξάγετε inline**.

---

## Pro Συμβουλές & Καλές Πρακτικές  

- **Pro tip:** Ορίστε `pdfOptions.Compliance = PdfCompliance.PdfA1b` αν η εταιρεία σας απαιτεί PDF/A για αρχειοθέτηση.  
- **Προσοχή σε:** Κρυφά τμήματα (`SectionBreakContinuous`) που μπορεί να κρύβουν πλωτά σχήματα· εκτελέστε `doc.UpdatePageLayout()` πριν την αποθήκευση.  
- **Συμβουλή απόδοσης:** Επαναχρησιμοποιήστε ένα μόνο αντικείμενο `PdfSaveOptions` αν μετατρέπετε πολλά αρχεία σε batch· μειώνει το κόστος κατανομής μνήμης.  
- **Δοκιμή:** Ανοίξτε πάντα το παραγόμενο PDF σε τουλάχιστον δύο προβολείς (Adobe Reader, Edge) για να επαληθεύσετε τη συνέπεια της διάταξης.

---

## Οπτική Επισκόπηση  

![Διάγραμμα ροής αποθήκευσης εγγράφου ως PDF που δείχνει βήματα φόρτωσης → διαμόρφωσης → αποθήκευσης](https://example.com/flowchart.png "Διάγραμμα ροής αποθήκευσης εγγράφου ως PDF")

*Κείμενο alt:* **Διάγραμμα ροής αποθήκευσης εγγράφου ως PDF** – απεικονίζει τη διαδικασία τριών βημάτων: φόρτωση DOCX, διαμόρφωση εξαγωγής inline, και αποθήκευση ως PDF.

---

## Συμπέρασμα  

Τώρα διαθέτετε μια σταθερή, έτοιμη για παραγωγή μέθοδο για **αποθήκευση εγγράφου ως PDF** σε C# ενώ διαχειρίζεστε σωστά τα πλωτά αντικείμενα. Με τη ρύθμιση `ExportFloatingShapesAsInlineTag`, εξασφαλίζετε ότι κάθε εικόνα, διάγραμμα ή πλαίσιο κειμένου γίνεται μέρος της ροής κειμένου, εξαλείφοντας τα τυπικά σφάλματα που εμφανίζονται σε μια αφελή προσέγγιση **μετατροπής word σε pdf**.  

Δοκιμάστε το: μετατρέψτε μια σύνθετη αναφορά με πολλαπλές πλωτές εικόνες, και πειραματιστείτε με τη λογική επιλεκτικής inline μετατροπής για να κρατήσετε κάποια σχήματα πλωτά όπου χρειάζεται. Την επόμενη φορά που θα χρειαστεί να **μετατρέψετε docx σε pdf**, θα ξέρετε ακριβώς πώς να διατηρήσετε κάθε οπτικό στοιχείο.

Μη διστάσετε να αφήσετε σχόλιο αν αντιμετωπίσετε δυσκολίες ή ανακαλύψετε κάποιο έξυπνο κόλπο. Καλός κώδικας!

## Τι Θα Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα επεξηγήσεις για να κατακτήσετε πρόσθετα χαρακτηριστικά API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [save docx as pdf with Aspose.Words – Complete C# Guide](/words/english/net/basic-conversions/save-docx-as-pdf-with-aspose-words-complete-c-guide/)
- [Save Word as PDF with Aspose.Words – Complete C# Guide](/words/english/net/basic-conversions/save-word-as-pdf-with-aspose-words-complete-c-guide/)
- [convert word to pdf in C# using Aspose.Words – Guide](/words/english/net/basic-conversions/convert-word-to-pdf-in-c-using-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}