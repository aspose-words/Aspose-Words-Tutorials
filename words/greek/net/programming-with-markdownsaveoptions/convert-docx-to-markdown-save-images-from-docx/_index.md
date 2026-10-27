---
category: general
date: 2026-06-27
description: Μετατρέψτε το docx σε markdown και αποθηκεύστε τις εικόνες από το docx
  χρησιμοποιώντας το Aspose.Words. Μάθετε πώς να εξάγετε εικόνες από αρχείο Word και
  να εξάγετε το έγγραφο Word ως markdown.
draft: false
keywords:
- convert docx to markdown
- save images from docx
- extract images from word file
- export word document as markdown
language: el
og_description: Μετατρέψτε το docx σε markdown και αποθηκεύστε τις εικόνες από το
  docx. Αυτός ο οδηγός δείχνει πώς να εξάγετε εικόνες από αρχείο Word και να εξάγετε
  το έγγραφο Word ως markdown.
og_title: Μετατροπή docx σε markdown & αποθήκευση εικόνων από docx
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Convert docx to markdown and save images from docx using Aspose.Words.
    Learn how to extract images from Word file and export Word document as markdown.
  headline: Convert docx to markdown & save images from docx
  type: TechArticle
- description: Convert docx to markdown and save images from docx using Aspose.Words.
    Learn how to extract images from Word file and export Word document as markdown.
  name: Convert docx to markdown & save images from docx
  steps:
  - name: How the code works
    text: '- **Loading the document** (`new Document(inputPath)`) gives us an in‑memory
      representation of the Word file, complete with all its parts—paragraphs, tables,
      and **images**. - **`MarkdownSaveOptions`** is where the magic happens. By attaching
      a `ResourceSavingCallback`, we gain full control over eve'
  - name: Quick sanity check
    text: '- Does the Markdown file open without errors in VS Code’s preview pane?
      ✅ - Are all pictures displayed when you view the file on GitHub? ✅ - Did the
      `Images` directory contain one file per picture from the original `.docx`? ✅'
  - name: What’s next?
    text: '- **Style the Markdown** – add a front‑matter block for Jekyll or Hugo.
      - **Automate the pipeline** – embed this code in an Azure DevOps or GitHub Action
      step. - **Handle tables and footnotes** – explore other `MarkdownSaveOptions`
      flags like `ExportTableBorderStyles`.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Markdown
- Word
title: Μετατροπή docx σε markdown & αποθήκευση εικόνων από docx
url: /el/net/programming-with-markdownsaveoptions/convert-docx-to-markdown-save-images-from-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Μετατροπή docx σε markdown & αποθήκευση εικόνων από docx

Έχετε σκεφτεί ποτέ πώς να **μετατρέψετε docx σε markdown** χωρίς να χάσετε τις εικόνες που είναι ενσωματωμένες στο αρχείο Word; Δεν είστε μόνοι—οι προγραμματιστές συχνά χρειάζονται μια καθαρή έκδοση Markdown μιας αναφοράς, διατηρώντας κάθε διάγραμμα, λογότυπο ή στιγμιότυπο ακριβώς όπως είναι.

Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα από ένα πλήρες, έτοιμο‑για‑εκτέλεση παράδειγμα που **μετατρέπει ένα .docx σε Markdown**, **αποθηκεύει εικόνες από το docx** σε φάκελο της επιλογής σας, και δείχνει πώς να **εξάγετε εικόνες από αρχείο Word** χρησιμοποιώντας τη δυναμική βιβλιοθήκη Aspose.Words. Στο τέλος θα ξέρετε επίσης πώς να **εξάγετε έγγραφο Word ως markdown** με μία μόνο γραμμή κώδικα.

## Τι θα χρειαστείτε

- .NET 6+ (ή .NET Framework 4.7.2+) εγκατεστημένο στο μηχάνημά σας  
- Μια αναφορά NuGet στο `Aspose.Words` (η δωρεάν δοκιμή λειτουργεί)  
- Ένα δείγμα `input.docx` που περιέχει τουλάχιστον μία εικόνα  
- Ένα IDE που προτιμάτε—Visual Studio, Rider, ή ακόμη και VS Code αρκεί  

Χωρίς πρόσθετα εργαλεία τρίτων, χωρίς περίπλοκες εντολές γραμμής εντολών. Απλώς καθαρός κώδικας C#.

## Μετατροπή docx σε markdown – Επισκόπηση

Η βασική ιδέα είναι απλή:

1. Φορτώστε το πηγαίο έγγραφο Word.  
2. Πείτε στο Aspose.Words πώς θέλετε να διαχειριστεί τους εξωτερικούς πόρους (όπως εικόνες).  
3. Αποθηκεύστε το έγγραφο ως Markdown, αφήνοντας τη βιβλιοθήκη να κάνει το σκληρό έργο.

Παρακάτω είναι το **πλήρες, εκτελέσιμο πρόγραμμα**. Μπορείτε να το αντιγράψετε‑και‑επικολλήσετε σε ένα νέο έργο κονσόλας και να πατήσετε `Ctrl+F5`.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // Step 1: Load the source document that contains images
        // -----------------------------------------------------------------
        string inputPath = Path.Combine("YOUR_DIRECTORY", "input.docx");
        Document doc = new Document(inputPath);

        // -----------------------------------------------------------------
        // Step 2: Configure Markdown save options with a custom callback
        // -----------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            // This callback runs for each external resource (images, CSS, etc.)
            ResourceSavingCallback = (sender, args) =>
            {
                // ---------------------------------------------------------
                // Step 3a: Save images to a custom folder using a unique name
                // ---------------------------------------------------------
                if (args.ResourceType == ResourceType.Image)
                {
                    string imageFolder = Path.Combine("YOUR_DIRECTORY", "Images");
                    Directory.CreateDirectory(imageFolder); // ensures folder exists

                    // Use a GUID so we never clash with existing files
                    string uniqueName = Guid.NewGuid().ToString() + args.Extension;
                    args.SavePath = Path.Combine(imageFolder, uniqueName);
                }

                // ---------------------------------------------------------
                // Step 3b: Skip CSS files – they aren't needed for plain Markdown
                // ---------------------------------------------------------
                if (args.ResourceType == ResourceType.CssStyleSheet)
                    args.Cancel = true;
            }
        };

        // -----------------------------------------------------------------
        // Step 4: Export the document to Markdown, applying the options
        // -----------------------------------------------------------------
        string outputPath = Path.Combine("YOUR_DIRECTORY", "output.md");
        doc.Save(outputPath, mdOptions);

        Console.WriteLine("Conversion complete! Markdown saved to " + outputPath);
        Console.WriteLine("Images extracted to " + Path.Combine("YOUR_DIRECTORY", "Images"));
    }
}
```

### Πώς λειτουργεί ο κώδικας

- **Φόρτωση του εγγράφου** (`new Document(inputPath)`) μας δίνει μια αναπαράσταση στη μνήμη του αρχείου Word, με όλα του τα μέρη—παραγράφους, πίνακες και **εικόνες**.  
- **`MarkdownSaveOptions`** είναι όπου συμβαίνει η μαγεία. Συνδέοντας ένα `ResourceSavingCallback`, αποκτούμε πλήρη έλεγχο πάνω σε κάθε εξωτερικό πόρο που προσπαθεί να γράψει το Aspose.Words.  
- Μέσα στο callback **εξάγουμε εικόνες από το αρχείο Word** ελέγχοντας `args.ResourceType == ResourceType.Image`. Το callback λαμβάνει τα bytes της εικόνας, την αρχική της επέκταση, και μια ιδιότητα `SavePath` που ορίζουμε σε φάκελο που δημιουργούμε επί τόπου. Η χρήση του `Guid.NewGuid()` εγγυάται μοναδικό όνομα αρχείου, ώστε να μην αντικαταστήσετε κατά λάθος προηγούμενες εκτελέσεις.  
- **Παραλείπουμε το CSS** (`ResourceType.CssStyleSheet`) επειδή το απλό Markdown δεν χρειάζεται φύλλο στυλ. Αυτό διατηρεί το αποτέλεσμα καθαρό.  
- Τέλος, το `doc.Save(outputPath, mdOptions)` γράφει το αρχείο Markdown, αντικαθιστώντας τις δομές του Word με ισοδύναμα του Markdown (οι επικεφαλίδες γίνονται `#`, οι πίνακες γίνονται σειρές χωρισμένες με pipes κ.λπ.).

## Αποθήκευση εικόνων από docx – Στρατηγική προσαρμοσμένου φακέλου

Γιατί να χρησιμοποιήσετε προσαρμοσμένο φάκελο; Σκεφτείτε ότι δημιουργείτε τεκμηρίωση για μια CI pipeline. Θέλετε το αρχείο Markdown και τα περιουσιακά του στοιχεία να βρίσκονται δίπλα‑δίπλα σε μια καθαρή, επαναλήψιμη δομή.

```csharp
string imageFolder = Path.Combine("YOUR_DIRECTORY", "Images");
Directory.CreateDirectory(imageFolder);
```

Μερικές **συμβουλές pro**:

- **Κρατήστε τη διαδρομή του φακέλου σχετική** με τη ρίζα του έργου σας. Έτσι το αρχείο Markdown μπορεί να αναφέρει τις εικόνες με σχετικό σύνδεσμο (`![Alt text](Images/abc123.png)`), που λειτουργεί σε GitHub, GitLab ή οποιονδήποτε static‑site generator.  
- **Αν χρειάζεστε ντετερμινιστικά ονόματα** (π.χ. η ίδια εικόνα να παίρνει πάντα το ίδιο όνομα αρχείου), αντικαταστήστε το GUID με ένα hash των bytes της εικόνας: `MD5.Create().ComputeHash(args.Data)`. Είναι μια μικρή τροποποίηση αλλά χρήσιμη για caching.

## Εξαγωγή εικόνων από αρχείο Word – Ακραίες περιπτώσεις

1. **Πολλαπλές μορφές εικόνας** – Το Aspose.Words υποστηρίζει PNG, JPEG, GIF, BMP και ακόμη SVG. Η ιδιότητα `args.Extension` περιέχει ήδη τη σωστή επέκταση, οπότε δεν χρειάζεται να μαντέψετε.  
2. **Πολύ μεγάλες εικόνες** – Αν το πηγαίο έγγραφο περιέχει φωτογραφίες υψηλής ανάλυσης, τα παραγόμενα αρχεία μπορεί να είναι μεγάλου μεγέθους. Σκεφτείτε να προσθέσετε ένα βήμα συμπίεσης μετά το callback, χρησιμοποιώντας `System.Drawing` ή `ImageSharp`.  
3. **Κρυμμένες εικόνες** – Το Word μπορεί να αποθηκεύει εικόνες σε κεφαλίδες/υποσέλιδα ή ακόμη και σε πλαίσια κειμένου. Το callback τις βλέπει όλες, οπότε θα εξάγετε **κάθε** εικόνα, όχι μόνο τις ορατές. Αν θέλετε μόνο εικόνες του σώματος, προσθέστε ένα φίλτρο στο `args.ImageIndex` ή ελέγξτε το `args.ImageType`.

## Εξαγωγή εγγράφου Word ως markdown – Επαλήθευση του αποτελέσματος

Μετά την εκτέλεση του προγράμματος, ανοίξτε το `output.md` σε οποιονδήποτε προβολέα Markdown. Θα πρέπει να δείτε κάτι σαν:

```markdown
# My Report

Here is an introductory paragraph.

![Image1](Images/3f9c2d1e-7a5b-4c9e-9f6a-2b4e5d6f7a8b.png)

More text follows...
```

Παρατηρήστε πως ο σύνδεσμος εικόνας δείχνει στον φάκελο **Images** που δημιουργήσαμε. Αυτό είναι το χαρακτηριστικό μιας επιτυχημένης **εξαγωγής εγγράφου Word ως markdown**.

### Γρήγορος έλεγχος λογικής

- Το αρχείο Markdown ανοίγει χωρίς σφάλματα στο παράθυρο προεπισκόπησης του VS Code; ✅  
- Εμφανίζονται όλες οι εικόνες όταν προβάλετε το αρχείο στο GitHub; ✅  
- Περιέχει ο φάκελος `Images` ένα αρχείο ανά εικόνα από το αρχικό `.docx`; ✅  

Αν κάποιος από αυτούς τους ελέγχους αποτύχει, ελέγξτε ξανά τη λογική του `ResourceSavingCallback` και βεβαιωθείτε ότι το placeholder `YOUR_DIRECTORY` δείχνει σε θέση με δικαιώματα εγγραφής.

## Συνηθισμένα προβλήματα και πώς να τα αποφύγετε

| Πρόβλημα | Γιατί συμβαίνει | Διόρθωση |
|----------|----------------|----------|
| **Οι εικόνες δεν εμφανίζονται** | Το callback δεν εκτελείται επειδή δεν έχει οριστεί το `ResourceSavingCallback`. | Ορίστε το callback **πριν** καλέσετε `doc.Save`. |
| **Ο φάκελος Images είναι κενός** | Το `args.Cancel = true` είχε οριστεί για όλους τους πόρους κατά λάθος. | Ακυρώστε μόνο το CSS (`ResourceType.CssStyleSheet`), αφήνοντας τις εικόνες ανέπαφες. |
| **Διαδρομή αρχείου πολύ μεγάλη στα Windows** | Η χρήση βαθιά ενσωματωμένων φακέλων μαζί με GUIDs μπορεί να υπερβεί τα 260 χαρακτήρες. | Κρατήστε τη δομή του φακέλου ρηχή ή ενεργοποιήστε την υποστήριξη long‑path στα Windows 10+. |
| **Διπλότυπα ονόματα εικόνων** | Χρήση `DateTime.Now.Ticks` αντί για GUID μπορεί να συγκρούεται σε γρήγορους βρόχους. | Παραμείνετε στο `Guid.NewGuid()` για μοναδικότητα. |

## Συμπέρασμα

Μόλις **μετατρέψαμε docx σε markdown**, **αποθηκεύσαμε εικόνες από docx**, και δείξαμε πώς να **εξάγουμε εικόνες από αρχείο Word** ενώ **εξάγουμε έγγραφο Word ως markdown** με έναν καθαρό, επαναλήψιμο τρόπο. Όλη η διαδικασία βασίζεται στο `ResourceSavingCallback` του Aspose.Words, που σας δίνει λεπτομερή έλεγχο πάνω σε κάθε εξωτερικό περιουσιακό στοιχείο.

### Τι ακολουθεί;

- **Στυλιζάτε το Markdown** – προσθέστε ένα front‑matter block για Jekyll ή Hugo.  
- **Αυτοματοποιήστε τη pipeline** – ενσωματώστε αυτόν τον κώδικα σε βήμα Azure DevOps ή GitHub Action.  
- **Διαχειριστείτε πίνακες και υποσημειώσεις** – εξερευνήστε άλλες σημαίες του `MarkdownSaveOptions` όπως `ExportTableBorderStyles`.  

Μπορείτε να τροποποιήσετε τη δομή των φακέλων, να προσθέσετε συμπίεση εικόνων, ή ακόμη και να αλλάξετε τη μορφή εξόδου σε HTML αντικαθιστώντας το `MarkdownSaveOptions` με `HtmlSaveOptions`. Οι δυνατότητες είναι απεριόριστες όταν έχετε μια σταθερή βάση για **convert docx to markdown**.

Καλή προγραμματιστική, και ας παραμείνει η τεκμηρίωσή σας πάντα τόσο όμορφη **και** μηχανικά αναγνώσιμη!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [Save Word Images – Convert Word to Markdown with Aspose](/words/english/net/programming-with-markdownsaveoptions/save-word-images-convert-word-to-markdown-with-aspose/)
- [Convert Word to Markdown – Embed Images as Base64](/words/english/net/programming-with-markdownsaveoptions/convert-word-to-markdown-embed-images-as-base64/)
- [How to Rename Images When Converting DOCX to Markdown](/words/english/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}