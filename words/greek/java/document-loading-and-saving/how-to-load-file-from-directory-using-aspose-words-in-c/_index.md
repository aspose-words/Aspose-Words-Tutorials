---
category: general
date: 2026-09-11
description: Φορτώστε αρχείο από κατάλογο με το Aspose.Words χρησιμοποιώντας τις προεπιλεγμένες
  επιλογές φόρτωσης και μάθετε πώς να ορίσετε την κωδικοποίηση του εγγράφου ή να προσαρμόσετε
  τις επιλογές φόρτωσης σε C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- load file from directory
- default load options
- set document encoding
- set load options
language: el
lastmod: 2026-09-11
og_description: Φορτώστε αρχείο από φάκελο με το Aspose.Words χρησιμοποιώντας τις
  προεπιλεγμένες επιλογές φόρτωσης, ορίστε την κωδικοποίηση του εγγράφου και προσαρμόστε
  τις επιλογές φόρτωσης για οποιοδήποτε έγγραφο Word.
og_image_alt: Diagram illustrating load file from directory process with Aspose.Words
og_title: Φόρτωση αρχείου από φάκελο με το Aspose.Words – πλήρης οδηγός C#
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Load file from directory with Aspose.Words using default load options
    and learn how to set document encoding or customize load options in C#.
  headline: How to load file from directory using Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document processing
title: Πώς να φορτώσετε αρχείο από φάκελο χρησιμοποιώντας το Aspose.Words σε C#
url: /el/java/document-loading-and-saving/how-to-load-file-from-directory-using-aspose-words-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να φορτώσετε αρχείο από κατάλογο χρησιμοποιώντας το Aspose.Words σε C#

Εάν χρειάζεται να **φορτώσετε αρχείο από κατάλογο** σε μια ροή επεξεργασίας Word, το Aspose.Words το κάνει απλό. Αυτός ο οδηγός δείχνει πώς να χρησιμοποιήσετε τις **προεπιλεγμένες επιλογές φόρτωσης**, **να ορίσετε την κωδικοποίηση του εγγράφου**, και **να ορίσετε επιλογές φόρτωσης** ώστε να ταιριάζουν στο συγκεκριμένο σενάριό σας.

Η φόρτωση εγγράφων συχνά προκαλεί προβλήματα στους προγραμματιστές όταν το αρχείο προέρχεται από προσαρμοσμένο φάκελο ή χρησιμοποιεί κωδικοποίηση διαφορετική από UTF‑8. Στο τέλος αυτού του tutorial θα μπορείτε να φορτώσετε οποιοδήποτε αρχείο `.docx` από οποιονδήποτε κατάλογο, να ελέγξετε την κωδικοποίησή του και να προσαρμόσετε τη συμπεριφορά φόρτωσης χωρίς επιπλέον κώδικα υποδομής.

## Τι θα επιτύχετε

- Φόρτωση ενός εγγράφου Word από οποιονδήποτε κατάλογο με μία μόνο γραμμή κώδικα.  
- Κατανόηση του τι παρέχουν οι **προεπιλεγμένες επιλογές φόρτωσης** και πότε χρειάζεται να τις αλλάξετε.  
- Εφαρμογή **ορισμού κωδικοποίησης εγγράφου** για σωστή ερμηνεία παλαιών συνόλων χαρακτήρων όπως το Big5.  
- Προσαρμογή **επιλογών φόρτωσης** για λεπτομερή ρύθμιση χρήσης μνήμης, διαχείρισης κωδικού πρόσβασης κ.λπ.  

### Προαπαιτούμενα

- .NET 6.0 ή νεότερο (το παράδειγμα στοχεύει .NET 6, αλλά λειτουργεί με οποιαδήποτε πρόσφατη έκδοση .NET).  
- Aspose.Words for .NET 23.9 ή νεότερο – προσθέστε το πακέτο NuGet `Aspose.Words`.  
- Βασική εξοικείωση με C# και Visual Studio ή το προτιμώμενο IDE σας.

---

## Πώς να φορτώσετε αρχείο από κατάλογο με Aspose.Words

Ο πυρήνας της λειτουργίας είναι ένας μόνο κατασκευαστής `Document` που δέχεται διαδρομή αρχείου και προαιρετικό αντικείμενο `LoadOptions`. Όταν παραλείψετε το `LoadOptions`, το Aspose.Words εφαρμόζει αυτόματα τις **προεπιλεγμένες επιλογές φόρτωσης**, οι οποίες αρκούν για τα περισσότερα σύγχρονα έγγραφα.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;

class Program
{
    static void Main()
    {
        // Step 1: Define the absolute path to the .docx file you want to load.
        string filePath = @"C:\MyDocuments\big5.docx";

        // Step 2: Load the document using the default load options.
        Document doc = new Document(filePath, new LoadOptions());

        // Verify that the document loaded by outputting the page count.
        Console.WriteLine($"Document loaded. Page count: {doc.PageCount}");
    }
}
```

**Γιατί λειτουργεί αυτό:**  
- Ο κατασκευαστής `Document` διαβάζει το αρχείο που βρίσκεται στο `filePath`.  
- Η μεταβίβαση `new LoadOptions()` λέει στο Aspose.Words να χρησιμοποιήσει τις **προεπιλεγμένες επιλογές φόρτωσης**, οι οποίες ανιχνεύουν αυτόματα τη μορφή του αρχείου, επιλέγουν την κατάλληλη κωδικοποίηση και εφαρμόζουν τυπικούς ελέγχους ασφαλείας.  

Η εκτέλεση του προγράμματος εκτυπώνει τον αριθμό σελίδων, επιβεβαιώνοντας ότι η λειτουργία **φόρτωσης αρχείου από κατάλογο** ολοκληρώθηκε με επιτυχία.

---

## Χρήση προεπιλεγμένων επιλογών φόρτωσης

Αν και μπορείτε να παραλείψετε εντελώς το όρισμα `LoadOptions`, η ρητή δημιουργία ενός αντικειμένου `LoadOptions` διευκρινίζει την πρόθεση και σας προετοιμάζει για μελλοντικές προσαρμογές.

```csharp
// Create a LoadOptions instance with the default configuration.
LoadOptions loadOptions = new LoadOptions();

// Load the document with those options.
Document doc = new Document(@"C:\MyDocuments\sample.docx", loadOptions);
```

**Βασικά σημεία για τις προεπιλεγμένες επιλογές φόρτωσης**

| Χαρακτηριστικό | Προεπιλεγμένη συμπεριφορά |
|----------------|---------------------------|
| **Ανίχνευση μορφής** | Ανιχνεύει αυτόματα DOC, DOCX, ODT, RTF, HTML και πολλές άλλες μορφές. |
| **Κωδικοποίηση** | Ανιχνεύει UTF‑8, UTF‑16 και κοινές παλαιότερες κωδικοποιήσεις· επιστρέφει σε UTF‑8. |
| **Διαχείριση κωδικού πρόσβασης** | Ρίχνει `IncorrectPasswordException` εάν το αρχείο είναι προστατευμένο με κωδικό. |
| **Χρήση μνήμης** | Φορτώνει ολόκληρο το έγγραφο στη μνήμη, κάτι που είναι βέλτιστο για αρχεία κάτω των 100 MB. |

Εάν το έγγραφό σας είναι κωδικοποιημένο με παλαιό σύνολο χαρακτήρων (π.χ., Big5) και η αυτόματη ανίχνευση αποτύχει, πρέπει να **ορίσετε την κωδικοποίηση του εγγράφου** χειροκίνητα.

---

## Ορισμός κωδικοποίησης εγγράφου

Όταν ένα αρχείο περιέχει γραμματοσειρές ή κείμενο κωδικοποιημένο με παλαιό code page, μπορείτε να υποδείξετε στο Aspose.Words ποια κωδικοποίηση να χρησιμοποιήσει μέσω της ιδιότητας `LoadOptions.Encoding`. Αυτός είναι ο τυπικός τρόπος για **ορισμό κωδικοποίησης εγγράφου** για αρχεία που ο προεπιλεγμένος ανιχνευτής δεν μπορεί να διαβάσει.

```csharp
using System.Text;

// Step 1: Create LoadOptions and specify the encoding.
LoadOptions loadOptions = new LoadOptions
{
    // Big5 is code page 950.
    Encoding = Encoding.GetEncoding(950)
};

// Step 2: Load the document from the target directory.
Document doc = new Document(@"C:\MyDocuments\big5.docx", loadOptions);

// Step 3: Verify that the special characters are preserved.
Console.WriteLine($"First paragraph text: {doc.FirstSection.Body.Paragraphs[0].GetText()}");
```

**Γιατί το χρειάζεστε:**  
- Χωρίς ρητό ορισμό του `Encoding`, το Aspose.Words μπορεί να ερμηνεύσει τα bytes ως UTF‑8, οδηγώντας σε ακατάλληλους χαρακτήρες.  
- Παρέχοντας το σωστό code page, η βιβλιοθήκη διαβάζει το κείμενο ακριβώς όπως το είχε σκοπό ο δημιουργός.

**Συμβουλή:** Χρησιμοποιήστε `Encoding.GetEncoding("big5")` ή τον αριθμητικό κωδικό (`950`) για παραδοσιακά κινέζικα (Big5) έγγραφα.

---

## Προσαρμογή επιλογών φόρτωσης (set load options)

Πέρα από την κωδικοποίηση, το `LoadOptions` εκθέτει πολλές ιδιότητες που σας επιτρέπουν να **ορίσετε επιλογές φόρτωσης** για προχωρημένα σενάρια:

```csharp
// Create a LoadOptions object with several custom settings.
LoadOptions loadOptions = new LoadOptions
{
    // Force the document to be treated as a DOCX file, even if the extension is wrong.
    LoadFormat = LoadFormat.Docx,

    // Limit memory usage for very large files (e.g., 200 MB+).
    LoadOptionsMemoryUsage = LoadOptionsMemoryUsage.LowMemory,

    // Provide a password if the file is encrypted.
    Password = "MySecretPassword"
};

// Load the document using the customized options.
Document doc = new Document(@"C:\MyDocuments\protected.docx", loadOptions);
```

**Επεξήγηση των επιλεγμένων ιδιοτήτων**

| Ιδιότητα | Σκοπός |
|----------|--------|
| `LoadFormat` | Αναγκάζει μια συγκεκριμένη μορφή, παρακάμπτοντας την αυτόματη ανίχνευση. Χρήσιμο όταν οι επεκτάσεις αρχείων είναι παραπλανητικές. |
| `LoadOptionsMemoryUsage` | Επιλέγει μια στρατηγική εξοικονόμησης μνήμης (`LowMemory`) για τεράστια έγγραφα. |
| `Password` | Παρέχει κωδικό πρόσβασης για κρυπτογραφημένα αρχεία, αποφεύγοντας μια εξαίρεση. |
| `ValidateDocumentStructure` | Όταν είναι `true`, ο φορτωτής επικυρώνει τη εσωτερική δομή XML και ρίχνει εξαίρεση αν είναι κατεστραμμένη. |

Μπορείτε να συνδυάσετε οποιαδήποτε από αυτές τις ρυθμίσεις με **ορισμό κωδικοποίησης εγγράφου** για να αντιμετωπίσετε τις πιο απαιτητικές διαδικασίες εισαγωγής.

---

## Πλήρες εκτελέσιμο παράδειγμα

Παρακάτω βρίσκεται ένα αυτόνομο πρόγραμμα που επιδεικνύει όλες τις έννοιες σε μία ροή:

```csharp
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.Loading;

class LoadFileDemo
{
    static void Main()
    {
        // ------------------------------------------------------------------
        // 1️⃣ Define the directory and file name.
        // ------------------------------------------------------------------
        string directory = @"C:\MyDocuments";
        string fileName   = "big5.docx";               // Change as needed.
        string fullPath   = System.IO.Path.Combine(directory, fileName);

        // ------------------------------------------------------------------
        // 2️⃣ Create LoadOptions with explicit encoding (Big5) and low‑memory mode.
        // ------------------------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            Encoding = Encoding.GetEncoding(950), // Big5 code page.
            LoadOptionsMemoryUsage = LoadOptionsMemoryUsage.LowMemory
        };

        // ------------------------------------------------------------------
        // 3️⃣ Load the document from the directory using the custom options.
        // ------------------------------------------------------------------
        Document doc = new Document(fullPath, loadOptions);

        // ------------------------------------------------------------------
        // 4️⃣ Verify the load succeeded.
        // ------------------------------------------------------------------
        Console.WriteLine($"Document loaded from \"{fullPath}\"");
        Console.WriteLine($"Page count: {doc.PageCount}");
        Console.WriteLine($"First paragraph: {doc.FirstSection.Body.Paragraphs[0].GetText().Trim()}");

        // ------------------------------------------------------------------
        // 5️⃣ (Optional) Save as PDF to confirm visual fidelity.
        // ------------------------------------------------------------------
        string pdfPath = System.IO.Path.ChangeExtension(fullPath, ".pdf");
        doc.Save(pdfPath);
        Console.WriteLine($"Saved PDF version to \"{pdfPath}\"");
    }
}
```

**Αναμενόμενη έξοδος κονσόλας**

```
Document loaded from "C:\MyDocuments\big5.docx"
Page count: 3
First paragraph: 這是一個測試文件
Saved PDF version to "C:\MyDocuments\big5.pdf"
```

Η εκτέλεση του προγράμματος δείχνει πώς να **φορτώσετε αρχείο από κατάλογο**, **ορίσετε κωδικοποίηση εγγράφου**, και **ορίσετε επιλογές φόρτωσης** σε μια σαφή, ενιαία διαδικασία.

---

## Συνηθισμένα προβλήματα και πώς να τα αποφύγετε

| Σύμπτωμα | Πιθανή αιτία | Διόρθωση |
|----------|--------------|----------|
| Ασυνεπείς κινέζοι χαρακτήρες | Η κωδικοποίηση δεν έχει οριστεί ή είναι λάθος κωδική σελίδα | **Ορίστε κωδικοποίηση εγγράφου** σε `Encoding.GetEncoding(950)` για Big5. |
| `IncorrectPasswordException` ακόμη και αν το αρχείο δεν είναι προστατευμένο με κωδικό | Ο φορτωτής ανίχνευσε λανθασμένα ένα δυαδικό αρχείο ως κρυπτογραφημένο | **Ορίστε ρητά** το `LoadFormat` στον σωστό τύπο (π.χ., `LoadFormat.Docx`). |
| Out |

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [recover damaged docx with Aspose.Words – set recovery mode and load options](/words/english/net/programming-with-loadoptions/recover-damaged-docx-with-aspose-words-set-recovery-mode-and/)
- [How to Load RTF Documents with Configuring RTF Load Options in Aspose.Words for Java](/words/english/java/document-loading-and-saving/configuring-rtf-load-options/)
- [Master Markdown Load Options with Aspose.Words for Java](/words/english/java/document-operations/master-markdown-load-options-aspose-words-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}