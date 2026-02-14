---
category: general
date: 2026-02-13
description: Αποθηκεύστε το έγγραφο ως PDF γρήγορα με το Aspose.Words για .NET. Μάθετε
  πώς να μετατρέψετε το Word σε PDF, να εξάγετε docx σε PDF και να παρακολουθείτε
  τις αλλαγές γραμματοσειράς σε λίγα μόνο βήματα.
draft: false
keywords:
- save document as pdf
- convert word to pdf
- export docx to pdf
- monitor font changes
- Aspose.Words PDF options
- font substitution warning
language: el
og_description: Αποθηκεύστε το έγγραφο ως PDF με το Aspose.Words. Αυτός ο οδηγός δείχνει
  πώς να μετατρέψετε το Word σε PDF, να εξάγετε το docx σε PDF και να παρακολουθείτε
  τις αλλαγές γραμματοσειράς χωρίς κόπο.
og_title: Αποθήκευση εγγράφου ως PDF – Οδηγός C# βήμα‑βήμα
tags:
- C#
- Aspose.Words
- PDF generation
title: Αποθήκευση εγγράφου ως PDF σε C# – Πλήρης οδηγός για την εξαγωγή Docx και την
  παρακολούθηση αλλαγών γραμματοσειράς
url: /el/net/programming-with-pdfsaveoptions/save-document-as-pdf-in-c-complete-guide-to-export-docx-and/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Αποθήκευση Εγγράφου ως PDF – Ένα Πλήρες Μάθημα C#

Έχετε ποτέ χρειαστεί να **αποθηκεύσετε έγγραφο ως PDF** αλλά δεν ήξερες πώς να εντοπίσεις εκείνες τις πονηρές αντικαταστάσεις γραμματοσειρών; Δεν είστε μόνοι. Πολλοί προγραμματιστές συναντούν πρόβλημα όταν τα αρχεία Word τους περιέχουν γραμματοσειρές που δεν είναι ενσωματωμένες, και το παραγόμενο PDF φαίνεται εκτός κέντρου.  

Σε αυτό το μάθημα θα περάσουμε βήμα‑βήμα μια πρακτική λύση που όχι μόνο **μετατρέπει word σε pdf** αλλά επίσης σας επιτρέπει να **παρακολουθείτε τις αλλαγές γραμματοσειρών** ώστε να αντιδράσετε πριν το PDF φτάσει στα εισερχόμενα του πελάτη. Στο τέλος θα έχετε ένα έτοιμο προς εκτέλεση απόσπασμα κώδικα που **εξάγει docx σε pdf** ενώ παρακολουθεί κάθε προειδοποίηση αντικατάστασης γραμματοσειράς.

## Τι Θα Μάθετε

- Πώς να φορτώσετε ένα αρχείο *.docx* με το Aspose.Words for .NET.  
- Διαμόρφωση του `PdfSaveOptions` για ενεργοποίηση προειδοποιήσεων αντικατάστασης γραμματοσειρών.  
- Αποθήκευση του εγγράφου ως PDF και ανάγνωση της συλλογής προειδοποιήσεων.  
- Συμβουλές για τη διαχείριση ελλιπών γραμματοσειρών, την ενσωμάτωσή τους ή την αντικατάσταση με εναλλακτικές.  

**Προαπαιτούμενα** – μια πρόσφατη έκδοση του Visual Studio, .NET 6 ή νεότερη, και μια έγκυρη άδεια Aspose.Words (ή η δωρεάν δοκιμή). Δεν απαιτούνται επιπλέον πακέτα NuGet πέρα από το `Aspose.Words`.

---

## Βήμα 1: Ρύθμιση του Έργου και Προσθήκη του Aspose.Words

Για να ξεκινήσετε, δημιουργήστε μια νέα εφαρμογή κονσόλας:

```bash
dotnet new console -n PdfExportDemo
cd PdfExportDemo
dotnet add package Aspose.Words
```

> **Συμβουλή:** Εάν εργάζεστε σε εταιρικό υπολογιστή, βεβαιωθείτε ότι η πηγή NuGet είναι προσβάσιμη· διαφορετικά χρησιμοποιήστε το offline πακέτο.

Ανοίξτε το `Program.cs`. Οι πρώτες λίγες γραμμές εισάγουν τα namespaces που θα χρειαστείτε:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

Αυτές οι εισαγωγές σας δίνουν πρόσβαση στην κλάση `Document`, το κοντέινερ `PdfSaveOptions` και τη δομή προειδοποιήσεων.

## Βήμα 2: Φόρτωση του Πηγαίου Εγγράφου

Τώρα θα φορτώσουμε το αρχείο Word που θέλουμε να μετατρέψουμε. Αντικαταστήστε το `YOUR_DIRECTORY` με την πραγματική διαδρομή όπου βρίσκεται το *input.docx*.

```csharp
// Step 2: Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

**Γιατί είναι σημαντικό:** Η έγκαιρη φόρτωση του εγγράφου επιτρέπει στη βιβλιοθήκη να αναλύσει το στυλ, τις ενότητες και τους ενσωματωμένους πόρους του εγγράφου. Εάν το αρχείο δεν βρεθεί, το Aspose ρίχνει μια `FileNotFoundException`, οπότε ελέγξτε ξανά τη διαδρομή.

## Βήμα 3: Διαμόρφωση Επιλογών Αποθήκευσης PDF – Ενεργοποίηση Προειδοποιήσεων Αντικατάστασης Γραμματοσειράς

Η μαγεία συμβαίνει στο `PdfSaveOptions`. Ορίζοντας `FontSubstitutionWarning = true`, η βιβλιοθήκη θα στέλνει οποιαδήποτε συμβάντα αντικατάστασης γραμματοσειράς στη συλλογή `WarningCallback`.

```csharp
// Step 3: Configure PDF save options to capture font‑substitution warnings
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions
{
    SaveFormat = SaveFormat.Pdf,
    FontSubstitutionWarning = true
};
```

### Ποιο είναι το όφελος;

- **Ορατότητα:** Θα γνωρίζετε ακριβώς ποιες γραμματοσειρές αντικαταστάθηκαν, αποφεύγοντας ανεπιθύμητα PDFs.  
- **Έλεγχος:** Με αυτές τις πληροφορίες, μπορείτε είτε να ενσωματώσετε τη λείπουσα γραμματοσειρά είτε να επιλέξετε μια πιο κατάλληλη εναλλακτική.  

Εάν χρειάζεται επίσης να ενσωματώσετε όλες τις γραμματοσειρές, ορίστε `pdfSaveOptions.FontEmbeddingMode = FontEmbeddingMode.EmbedAll;` – αλλά να είστε ενήμεροι για περιορισμούς αδειοδότησης.

## Βήμα 4: Αποθήκευση του Εγγράφου ως PDF

Με τις επιλογές έτοιμες, η επόμενη γραμμή κάνει τη βαριά δουλειά:

```csharp
// Step 4: Save the document as a PDF using the configured options
doc.Save("YOUR_DIRECTORY/output.pdf", pdfSaveOptions);
```

Αυτή η κλήση γράφει το *output.pdf* στο δίσκο. Η διαδικασία είναι γρήγορη — συνήθως κάτω από ένα δευτερόλεπτο για μια τυπική αναφορά 10 σελίδων — αλλά μπορεί να διαρκέσει περισσότερο για έγγραφα με πολλές εικόνες υψηλής ανάλυσης.

## Βήμα 5: Εξέταση της Συλλογής Προειδοποιήσεων για Αντικαταστάσεις Γραμματοσειρών

Μετά την αποθήκευση, το Aspose γεμίζει το `doc.WarningCallback.Warnings`. Περάστε σε βρόχο για να εμφανίσετε τυχόν μηνύματα σχετιζόμενα με γραμματοσειρές:

```csharp
// Step 5: Examine the warning collection for any font substitutions
foreach (var warning in doc.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
        Console.WriteLine($"Substituted: {warning.Description}");
}
```

**Αναμενόμενη έξοδος** (παράδειγμα):

```
Substituted: The font 'Calibri Light' was not found. Substituted with 'Arial'.
Substituted: The font 'Cambria Math' was not found. Substituted with 'Times New Roman'.
```

Εάν η λίστα είναι κενή, συγχαρητήρια — δεν χάσατε καμία τυπογραφία στη μετατροπή.

## Διαχείριση Συνηθισμένων Ακραίων Περιπτώσεων

### 1. Ελλιπείς Γραμματοσειρές στον Διακομιστή

Εάν το περιβάλλον ανάπτυξης σας δεν διαθέτει ορισμένες γραμματοσειρές, μπορείτε:

- **Αντιγράψτε τα ελλιπή αρχεία TTF/OTF** σε έναν φάκελο και υποδείξτε το στο Aspose:

  ```csharp
  FontSettings fontSettings = new FontSettings();
  fontSettings.SetFontsFolder("YOUR_DIRECTORY/custom-fonts", recursive: true);
  doc.FontSettings = fontSettings;
  ```

- **Ενσωματώστε τις γραμματοσειρές** (εφόσον η άδεια το επιτρέπει) ενεργοποιώντας το `FontEmbeddingMode`.

### 2. Μεγάλα Έγγραφα και Χρήση Μνήμης

Για τεράστια αρχεία Word (εκατοντάδες σελίδες), σκεφτείτε τη χρήση του `SaveOptions` με `MemoryUsageSetting`:

```csharp
pdfSaveOptions.MemoryUsageSetting = MemoryUsageSetting.MemoryOptimized;
```

### 3. Μετατροπή Πολλαπλών Αρχείων σε Παρτίδα

Τυλίξτε τη βασική λογική σε μια μέθοδο:

```csharp
void ConvertDocxToPdf(string inputPath, string outputPath)
{
    Document d = new Document(inputPath);
    PdfSaveOptions opts = new PdfSaveOptions { FontSubstitutionWarning = true };
    d.Save(outputPath, opts);

    foreach (var w in d.WarningCallback.Warnings)
        if (w.Type == WarningType.FontSubstitution)
            Console.WriteLine($"[{inputPath}] {w.Description}");
}
```

Στη συνέχεια, επαναλάβετε πάνω σε έναν φάκελο με `Directory.GetFiles`.

## Πλήρες Παράδειγμα Λειτουργίας

Παρακάτω βρίσκεται το πλήρες, έτοιμο για αντιγραφή πρόγραμμα που ενώνει όλα τα παραπάνω. Περιλαμβάνει σχόλια, διαχείριση σφαλμάτων και την προαιρετική διαμόρφωση φακέλου γραμματοσειρών.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Paths – adjust these to your environment
        string inputFile  = @"YOUR_DIRECTORY\input.docx";
        string outputFile = @"YOUR_DIRECTORY\output.pdf";

        // 1️⃣ Load the source document
        Document doc;
        try
        {
            doc = new Document(inputFile);
        }
        catch (FileNotFoundException)
        {
            Console.WriteLine($"Error: Could not find '{inputFile}'.");
            return;
        }

        // Optional: tell Aspose where custom fonts live
        // FontSettings fonts = new FontSettings();
        // fonts.SetFontsFolder(@"YOUR_DIRECTORY\custom-fonts", true);
        // doc.FontSettings = fonts;

        // 2️⃣ Configure PDF options – we want to see font‑substitution warnings
        PdfSaveOptions pdfOpts = new PdfSaveOptions
        {
            SaveFormat = SaveFormat.Pdf,
            FontSubstitutionWarning = true,
            // Uncomment to embed all fonts (if allowed)
            // FontEmbeddingMode = FontEmbeddingMode.EmbedAll
        };

        // 3️⃣ Save as PDF
        try
        {
            doc.Save(outputFile, pdfOpts);
            Console.WriteLine($"Successfully saved PDF to '{outputFile}'.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to save PDF: {ex.Message}");
            return;
        }

        // 4️⃣ Check for font substitution warnings
        bool anyWarnings = false;
        foreach (var warning in doc.WarningCallback.Warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                anyWarnings = true;
                Console.WriteLine($"Substituted: {warning.Description}");
            }
        }

        if (!anyWarnings)
            Console.WriteLine("No font substitutions were detected – great!");
    }
}
```

Εκτελέστε το πρόγραμμα με `dotnet run`. Εάν κάποια γραμματοσειρά αντικαταστάθηκε, θα εμφανιστούν στην κονσόλα· διαφορετικά, θα δείτε το μήνυμα «Δεν εντοπίστηκαν αντικαταστάσεις γραμματοσειρών».

## Συχνές Ερωτήσεις (FAQ)

| Question | Answer |
|----------|--------|
| **Μπορώ να μετατρέψω ένα αρχείο *.doc* με τον ίδιο τρόπο;** | Απολύτως – η `Document` δέχεται οποιαδήποτε μορφή υποστηρίζεται από το Aspose.Words, συμπεριλαμβανομένων των *.doc*, *.rtf* και ακόμη *.html*. |
| **Χρειάζομαι άδεια για παραγωγική χρήση;** | Η δωρεάν δοκιμή λειτουργεί για αξιολόγηση, αλλά προσθέτει υδατογράφημα στο PDF. Αγοράστε άδεια για να αφαιρέσετε το υδατογράφημα και να ξεκλειδώσετε όλες τις δυνατότητες. |
| **Τι γίνεται αν θέλω να μετατρέψω σε άλλες μορφές όπως XPS;** | Αλλάξτε το `SaveFormat.Pdf` σε `SaveFormat.Xps` και χρησιμοποιήστε το αντίστοιχο `XpsSaveOptions`. Ο μηχανισμός προειδοποιήσεων λειτουργεί το ίδιο. |
| **Υπάρχει τρόπος να λάβω αναφορά JSON για τις προειδοποιήσεις γραμματοσειρών;** | Ναι – μπορείτε να σειριοποιήσετε το `doc.WarningCallback.Warnings` σε JSON χρησιμοποιώντας το `System.Text.Json`. Αυτό είναι χρήσιμο για pipelines καταγραφής. |
| **Θα αλλάξουν αυτόματα οι διαστάσεις των ενσωματωμένων εικόνων;** | Το Aspose διατηρεί τις αρχικές διαστάσεις των εικόνων εκτός εάν ορίσετε ρητά το `PdfSaveOptions.ImageCompression`. |

## Συμπέρασμα

Μόλις καλύψαμε έναν **πλήρη, από άκρη σε άκρη τρόπο αποθήκευσης εγγράφου ως PDF** διατηρώντας προσεκτικό έλεγχο των αντικαταστάσεων γραμματοσειρών. Το απόσπασμα κώδικα δείχνει πώς να **μετατρέψετε word σε pdf**, **εξάγετε docx σε pdf**, και **παρακολουθείτε τις αλλαγές γραμματοσειρών** σε μια ενιαία, καθαρή ροή.  

Από τη φόρτωση του πηγαίου αρχείου, τη διαμόρφωση του `PdfSaveOptions`, την αποθήκευση του PDF, έως την εξέταση της συλλογής προειδοποιήσεων — κάθε βήμα εξηγείται, γιατί είναι σημαντικό, και πώς μπορείτε να το προσαρμόσετε σε πραγματικές συνθήκες.  

Στο επόμενο βήμα, μπορείτε να εξερευνήσετε **την ενσωμάτωση ελλιπών γραμματοσειρών**, **τη βελτιστοποίηση του μεγέθους του PDF**, ή **τη δημιουργία ενός εργαλείου παρτίδας μετατροπής** που επεξεργάζεται ολόκληρο φάκελο αρχείων Word. Όλα αυτά τα θέματα επεκτείνουν φυσικά τις βασικές έννοιες που μόλις μάθατε.  

Έχετε κάποιο δικό σας κόλπο; Μοιραστείτε το στα σχόλια ή στείλτε μου μήνυμα στο Twitter @YourHandle. Καλή προγραμματιστική, και εύχομαι τα PDFs σας να φαίνονται πάντα ακριβώς όπως τα θέλετε!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}