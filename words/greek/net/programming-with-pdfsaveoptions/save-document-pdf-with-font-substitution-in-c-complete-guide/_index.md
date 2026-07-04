---
category: general
date: 2026-06-05
description: Αποθηκεύστε το έγγραφο PDF ενώ αντικαθιστάτε τις γραμματοσειρές χρησιμοποιώντας
  C#. Μάθετε πώς να αλλάξετε τη γραμματοσειρά PDF, να αντικαταστήσετε τη γραμματοσειρά
  PDF και να διαχειριστείτε την αντικατάσταση γραμματοσειρών PDF με το Aspose.Words.
draft: false
keywords:
- save document pdf
- replace font pdf
- word to pdf font
- change font pdf
- pdf font substitution
language: el
og_description: Αποθηκεύστε το έγγραφο PDF γρήγορα και αξιόπιστα. Αυτό το σεμινάριο
  δείχνει πώς να αντικαταστήσετε τη γραμματοσειρά PDF, να αλλάξετε τη γραμματοσειρά
  PDF και να πραγματοποιήσετε αντικατάσταση γραμματοσειράς PDF χρησιμοποιώντας το
  Aspose.Words.
og_title: Αποθήκευση εγγράφου PDF με αντικατάσταση γραμματοσειράς σε C# – Πλήρης οδηγός
schemas:
- author: Aspose
  dateModified: '2026-06-05'
  description: Save document PDF while replacing fonts using C#. Learn how to change
    font PDF, replace font PDF, and handle PDF font substitution with Aspose.Words.
  headline: Save Document PDF with Font Substitution in C# – Complete Guide
  type: TechArticle
tags:
- C#
- Aspose.Words
- PDF
- Font Substitution
title: Αποθήκευση εγγράφου PDF με αντικατάσταση γραμματοσειράς σε C# – Πλήρης οδηγός
url: /el/net/programming-with-pdfsaveoptions/save-document-pdf-with-font-substitution-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Αποθήκευση εγγράφου PDF με αντικατάσταση γραμματοσειράς σε C# – Πλήρης Οδηγός

Έχετε χρειαστεί ποτέ να **save document PDF** από ένα αρχείο Word αλλά οι γραμματοσειρές φαίνονται λανθασμένες στο τελικό PDF; Δεν είστε μόνοι—οι ασυμφωνίες γραμματοσειρών είναι ένα κοινό πρόβλημα, ειδικά όταν ο υπολογιστής‑στόχος δεν έχει εγκατεστημένες τις αρχικές γραμματοσειρές.  

Τα καλά νέα είναι ότι μπορείτε να **replace font pdf** προγραμματιστικά, να διατηρήσετε το branding σας αμετάβλητο, και να αποφύγετε αυτές τις άσχημες εναλλακτικές γραμματοσειρές. Σε αυτό το tutorial θα περάσουμε από ένα πρακτικό παράδειγμα που δείχνει ακριβώς πώς να αλλάξετε τη γραμματοσειρά PDF χρησιμοποιώντας το Aspose.Words, συν με μερικά επιπλέον κόλπα για αξιόπιστη αντικατάσταση γραμματοσειράς PDF.

## Τι καλύπτει αυτό το tutorial

Θα ξεκινήσουμε φορτώνοντας ένα έγγραφο Word, έπειτα θα ρυθμίσουμε **PdfSaveOptions** ώστε κάθε εμφάνιση μιας πηγαίας γραμματοσειράς (π.χ. *MyFont*) να αντικατασταθεί με μια έκδοση variable‑font (*MyFontVF*). Μετά θα αποθηκεύσουμε το αρχείο ως PDF και θα επαληθεύσουμε ότι η αντικατάσταση λειτούργησε. Στο τέλος θα είστε άνετοι με:

* Η ροή εργασίας **save document pdf** σε C#.
* Χρήση των ρυθμίσεων **replace font pdf** για αντιστοίχιση παλιών γραμματοσειρών σε νέες.
* Μετατροπή **word to pdf font** χωρίς χειροκίνητη επεξεργασία.
* Διαχείριση περιπτώσεων όπου μια γραμματοσειρά δεν βρέθηκε.
* Επέκταση της προσέγγισης σε πολλαπλά ζεύγη γραμματοσειρών με **pdf font substitution**.

Χωρίς εξωτερικά εργαλεία, μόνο με λίγες γραμμές κώδικα και τη βιβλιοθήκη Aspose.Words.

![Diagram illustrating the save document pdf process with font substitution](https://example.com/save-pdf-diagram.png "Save Document PDF Flow")

## Προαπαιτούμενα

* .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης σε .NET Framework 4.7+).  
* Μια αναφορά στο **Aspose.Words for .NET** (πακέτο NuGet `Aspose.Words`).  
* Τουλάχιστον ένα αρχείο γραμματοσειράς TrueType ή OpenType που θέλετε να ενσωματώσετε (π.χ., `MyFontVF.ttf`).  
* Ένα αρχείο Word (`sample.docx`) που χρησιμοποιεί την αρχική γραμματοσειρά που σκοπεύετε να αντικαταστήσετε.

Αν λείπει κάποιο από αυτά, αποκτήστε το πακέτο NuGet με:

```bash
dotnet add package Aspose.Words
```

## Βήμα 1 – Φόρτωση του πηγαίου εγγράφου Word

Πρώτα απ' όλα: χρειαζόμαστε ένα αντικείμενο `Document` που αντιπροσωπεύει το αρχείο Word που προτιθέμεθα να μετατρέψουμε. Αυτό το βήμα είναι η βάση κάθε λειτουργίας **save document pdf**, επειδή το υπόλοιπο pipeline λειτουργεί πάνω σε αυτήν την αναπαράσταση στη μνήμη.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Saving;

// Load the .docx you want to convert.
Document doc = new Document(@"C:\Docs\sample.docx");

// Optional sanity check – print how many sections we have.
Console.WriteLine($"Document loaded with {doc.Sections.Count} section(s).");
```

> **Γιατί είναι σημαντικό:** Η φόρτωση του εγγράφου σας δίνει πρόσβαση στο πλήρες μοντέλο αντικειμένων, επιτρέποντάς σας να χειριστείτε γραμματοσειρές, στυλ ή ακόμη και τη διάταξη της σελίδας πριν τελικά **save document pdf**.

## Βήμα 2 – Δημιουργία PDF Save Options και ενεργοποίηση της αντικατάστασης γραμματοσειράς

Τώρα δημιουργούμε μια παρουσία `PdfSaveOptions`. Αυτό το αντικείμενο περιέχει κάθε ρύθμιση που μπορείτε να προσαρμόσετε κατά την εξαγωγή σε PDF, από τη συμπίεση εικόνας μέχρι το επίπεδο συμμόρφωσης. Για τον σκοπό μας το κρίσιμο μέρος είναι η ιδιότητα `FontSettings`, η οποία μας επιτρέπει να ορίσουμε κανόνες **replace font pdf**.

```csharp
// Step 2: Create PDF save options.
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();

// Enable font substitution.
pdfSaveOptions.FontSettings = new FontSettings();

// Map the source font ("MyFont") to the target variable‑font ("MyFontVF").
pdfSaveOptions.FontSettings.SubstitutionSettings.FontInfoSubstitutions
    .Add("MyFont", new FontInfo("MyFontVF"));
```

> **Εξήγηση:**  
> * `PdfSaveOptions` καθορίζει στο Aspose.Words πώς θα αποδοθεί το PDF.  
> * `FontSettings.SubstitutionSettings.FontInfoSubstitutions` είναι ένα λεξικό όπου το **key** είναι το όνομα της γραμματοσειράς που εμφανίζεται στο έγγραφο Word, και το **value** είναι ένα `FontInfo` που δείχνει στο αρχείο αντικατάστασης γραμματοσειράς (ή απλώς το όνομα οικογένειας αν η γραμματοσειρά είναι ήδη στο OS).  
> * Προσθέτοντας αυτήν την καταχώρηση επιτυγχάνουμε **pdf font substitution** χωρίς να αγγίξουμε το αρχικό αρχείο Word.

### Συμβουλή: Διαχείριση πολλαπλών αντικαταστάσεων

Αν χρειάζεται να αντικαταστήσετε πολλές γραμματοσειρές, απλώς προσθέστε περισσότερες καταχωρήσεις:

```csharp
pdfSaveOptions.FontSettings.SubstitutionSettings.FontInfoSubstitutions
    .Add("OldSans", new FontInfo("NewSans"))
    .Add("OldSerif", new FontInfo("NewSerifVF"));
```

## Βήμα 3 – (Προαιρετικό) Λεπτομερής ρύθμιση ενσωμάτωσης γραμματοσειράς

Μερικές φορές θέλετε να βεβαιωθείτε ότι η γραμματοσειρά αντικατάστασης είναι πραγματικά ενσωματωμένη στο PDF. Αυτό αποτρέπει τους προγράμματα προβολής από το να επιστρέψουν σε διαφορετική γραμματοσειρά.

```csharp
// Ensure the target font is embedded.
pdfSaveOptions.FontEmbeddingMode = FontEmbeddingMode.EmbedAllFonts;

// If you want to embed only the subset that is used, use:
// pdfSaveOptions.FontEmbeddingMode = FontEmbeddingMode.EmbedSubset;
```

> **Πότε να το χρησιμοποιήσετε:** Αν το κοινό‑στόχος μπορεί να μην έχει εγκατεστημένη τη γραμματοσειρά αντικατάστασης, η ενσωμάτωση εγγυάται μια συνεπή εμφάνιση—κλειδί για μια αξιόπιστη εμπειρία **change font pdf**.

## Βήμα 4 – Αποθήκευση του εγγράφου ως PDF με τις ρυθμισμένες επιλογές

Τέλος, καλούμε το `Document.Save`, περνώντας τόσο τη διαδρομή εξόδου όσο και το `PdfSaveOptions` που μόλις ρυθμίσαμε. Αυτή η μοναδική γραμμή κάνει τη σκληρή δουλειά: αποδίδει τη διάταξη του Word, εφαρμόζει τη χαρτογράφηση **replace font pdf**, και γράφει ένα αρχείο PDF στο δίσκο.

```csharp
// Step 4: Save the document as a PDF using the options we set.
string outputPath = @"C:\Docs\vf.pdf";
doc.Save(outputPath, pdfSaveOptions);

Console.WriteLine($"PDF saved successfully to {outputPath}");
```

Όταν ανοίξετε το `vf.pdf`, οποιοδήποτε κείμενο που αρχικά χρησιμοποιούσε *MyFont* θα εμφανιστεί τώρα με *MyFontVF*. Η οπτική διαφορά μπορεί να είναι λεπτή (αν ανταλλάσσετε με μια έκδοση variable‑font) ή δραματική (αν ανταλλάσσετε μια διακοσμητική γραμματοσειρά εμφάνισης με μια εταιρική).

## Βήμα 5 – Επαλήθευση του αποτελέσματος (Τι να ψάξετε)

Ένας γρήγορος τρόπος για να επιβεβαιώσετε την αντικατάσταση είναι να ελέγξετε τη λίστα γραμματοσειρών του PDF. Οι περισσότεροι προβολείς PDF σας επιτρέπουν να δείτε τις ιδιότητες του εγγράφου· θα πρέπει να δείτε το `MyFontVF` στη λίστα και **όχι** το `MyFont`. Εναλλακτικά, μπορείτε να χρησιμοποιήσετε ένα εργαλείο όπως το **pdfinfo** (μέρος του Poppler) για να εξάγετε τον πίνακα γραμματοσειρών:

```bash
pdfinfo -f 1 -l 1 -box vf.pdf | grep Font
```

Αν η έξοδος δείχνει `Font: MyFontVF`, έχετε εκτελέσει επιτυχώς **pdf font substitution**.

## Συνηθισμένα προβλήματα και πώς να τα αποφύγετε

| Issue | Why it Happens | Fix |
|-------|----------------|-----|
| **Font not found** | Το αρχείο γραμματοσειράς αντικατάστασης δεν βρίσκεται στο φάκελο γραμματοσειρών του συστήματος ούτε παρέχεται μέσω `FontInfo`. | Φορτώστε τη γραμματοσειρά χειροκίνητα: `FontSettings.FontSources.Add(new FileFontSource(@"C:\Fonts\MyFontVF.ttf"));` |
| **Text disappears** | Η γραμματοσειρά αντικατάστασης δεν περιέχει ορισμένα γλύφους που χρησιμοποιούνται στο πηγαίο έγγραφο. | Βεβαιωθείτε ότι η γραμματοσειρά‑στόχος υποστηρίζει όλα τα απαιτούμενα εύρη Unicode, ή επαναφέρετε την ενσωμάτωση της αρχικής γραμματοσειράς ως δευτερεύουσα επιλογή. |
| **PDF size balloons** | Η ενσωμάτωση πλήρων γραμματοσειρών για μεγάλες οικογένειες μπορεί να αυξήσει το μέγεθος του αρχείου. | Αλλάξτε σε λειτουργία `EmbedSubset` ώστε να ενσωματώνονται μόνο οι χρησιμοποιημένοι χαρακτήρες. |
| **Styling lost** | Η γραμματοσειρά αντικατάστασης δεν υποστηρίζει το βάρος της αρχικής γραμματοσειράς (π.χ., bold). | Επιλέξτε μια οικογένεια αντικατάστασης που ταιριάζει στο στυλ, ή χαρτογραφήστε πολλαπλά βάρη ξεχωριστά. |

## Προχωρημένο: Δυναμική χαρτογράφηση γραμματοσειρών βάσει περιεχομένου εγγράφου

Αν χρειάζεται να αντικαταστήσετε γραμματοσειρές μόνο όταν πληρούται μια συγκεκριμένη προϋπόθεση (π.χ., μόνο σε επικεφαλίδες), μπορείτε να διασχίσετε το δέντρο του εγγράφου και να εφαρμόσετε προσωρινά `FontSettings` πριν από την αποθήκευση. Ακολουθεί ένα σύντομο παράδειγμα:

```csharp
// Find all runs that use "MyFont" in headings and replace them on the fly.
foreach (Paragraph para in doc.GetChildNodes(NodeType.Paragraph, true))
{
    if (para.ParagraphFormat.StyleIdentifier == StyleIdentifier.Heading1)
    {
        foreach (Run run in para.Runs)
        {
            if (run.Font.Name == "MyFont")
                run.Font.Name = "MyFontVF";
        }
    }
}

// Save as before – no extra substitution needed because we already changed the runs.
doc.Save(outputPath, pdfSaveOptions);
```

> **Γιατί να το χρησιμοποιήσετε;** Σας δίνει λεπτομερή έλεγχο, επιτρέποντας να **change font pdf** μόνο σε συγκεκριμένα συμφραζόμενα ενώ αφήνει το υπόλοιπο άθικτο.

## Ανακεφαλαίωση: Πλήρες λειτουργικό παράδειγμα

Συνδυάζοντας όλα, εδώ είναι το πλήρες, έτοιμο‑για‑εκτέλεση πρόγραμμα:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Load the source Word document.
        Document doc = new Document(@"C:\Docs\sample.docx");

        // Prepare PDF save options with font substitution.
        PdfSaveOptions pdfSaveOptions = new PdfSaveOptions
        {
            FontSettings = new FontSettings(),
            FontEmbeddingMode = FontEmbeddingMode.EmbedAllFonts // ensure fonts are embedded
        };

        // Map "MyFont" -> "MyFontVF".
        pdfSaveOptions.FontSettings.SubstitutionSettings.FontInfoSubstitutions
            .Add("MyFont", new FontInfo("MyFontVF"));

        // OPTIONAL: Add a custom font folder if the font isn’t installed system‑wide.
        // pdfSaveOptions.FontSettings.FontSources.Add(new FileFontSource(@"C:\Fonts\MyFontVF.ttf"));

        // Save the PDF.
        string outputPath = @"C:\Docs\vf.pdf";
        doc.Save(outputPath, pdfSaveOptions);

        Console.WriteLine($"PDF saved to {outputPath}");
    }
}
```

Εκτελέστε το πρόγραμμα, ανοίξτε το `vf.pdf`, και θα δείτε τη νέα γραμματοσειρά εφαρμοσμένη παντού όπου εμφανιζόταν το αρχικό *MyFont*.

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετικές θεματικές που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κατακτήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Αποθήκευση Word ως PDF με Aspose.Words – Πλήρης οδηγός C#](/words/english/net/basic-conversions/save-word-as-pdf-with-aspose-words-complete-c-guide/)
- [Ενσωμάτωση υποσυνόλου γραμματοσειρών σε έγγραφο PDF](/words/english/net/programming-with-pdfsaveoptions/embedded-subset-fonts/)
- [Ενσωμάτωση γραμματοσειρών σε έγγραφο PDF](/words/english/net/programming-with-pdfsaveoptions/embedded-all-fonts/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}