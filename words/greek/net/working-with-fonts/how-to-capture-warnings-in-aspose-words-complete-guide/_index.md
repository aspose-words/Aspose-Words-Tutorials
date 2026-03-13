---
category: general
date: 2026-03-13
description: Πώς να καταγράψετε προειδοποιήσεις κατά τη φόρτωση εγγράφων με το Aspose.Words,
  καθώς και συμβουλές για τη διαχείριση ελλιπών γραμματοσειρών και τη ρύθμιση προσαρμοσμένων
  ρυθμίσεων γραμματοσειράς. Μάθετε μια πλήρη λύση σε C#.
draft: false
keywords:
- how to capture warnings
- handle missing fonts
- set custom font settings
language: el
og_description: Πώς να καταγράψετε προειδοποιήσεις κατά τη φόρτωση αρχείων Word με
  το Aspose.Words, καθώς και πρακτικούς τρόπους διαχείρισης ελλιπών γραμματοσειρών
  και ρύθμισης προσαρμοσμένων ρυθμίσεων γραμματοσειράς.
og_title: Πώς να Συλλέξετε Προειδοποιήσεις στο Aspose.Words – Πλήρης Οδηγός
tags:
- Aspose.Words
- C#
- Document Processing
title: Πώς να καταγράψετε προειδοποιήσεις στο Aspose.Words – Πλήρης οδηγός
url: /el/net/working-with-fonts/how-to-capture-warnings-in-aspose-words-complete-guide/
---

sure not to translate those.

Now produce final output.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Καταγράψετε Προειδοποιήσεις στο Aspose.Words – Πλήρης Οδηγός

Έχετε αναρωτηθεί ποτέ **πώς να καταγράψετε προειδοποιήσεις** που εμφανίζονται όταν το Aspose.Words φορτώνει ένα έγγραφο; Σε πολλά πραγματικά έργα θα δείτε ειδοποιήσεις αντικατάστασης γραμματοσειράς, σημειώσεις για παρωχημένες λειτουργίες ή ακόμη και μηνύματα σχετικά με την ασφάλεια. Η αγνόησή τους είναι σαν να οδηγείτε με σπασμένο παρμπρίζ—μπορεί να φτάσετε στον προορισμό σας, αλλά δεν θα ξέρετε ποτέ πότε κάτι πρόκειται να σπάσει.

Το καλό νέο είναι ότι το Aspose.Words σας παρέχει έναν καθαρό, βασισμένο σε callbacks τρόπο για να παρεμβείτε σε αυτά τα μηνύματα. Σε αυτό το tutorial θα περάσουμε από ένα **πλήρες παράδειγμα C#** που όχι μόνο καταγράφει προειδοποιήσεις αλλά και σας δείχνει πώς να **χειρίζεστε ελλιπείς γραμματοσειρές** και **να ορίζετε προσαρμοσμένες ρυθμίσεις γραμματοσειράς** ώστε τα έγγραφά σας να αποδίδονται ακριβώς όπως αναμένετε.

---

## Τι Θα Μάθετε

- Διαμορφώστε το `LoadOptions` για να ενσωματώσετε ένα προσαρμοσμένο αντικείμενο `FontSettings`.  
- Καταχωρήστε ένα callback προειδοποίησης που φιλτράρει τα γεγονότα `FontSubstitution`.  
- Εξάγετε τις λεπτομέρειες της προειδοποίησης στην κονσόλα (ή σε οποιονδήποτε logger προτιμάτε).  
- Επεκτείνετε τη λύση ώστε να διαχειρίζεται με χάρη τις ελλιπείς γραμματοσειρές σε διαφορετικές πλατφόρμες.  

Στο τέλος αυτού του οδηγού θα έχετε ένα έτοιμο‑για‑εκτέλεση snippet που μπορείτε να ενσωματώσετε σε οποιοδήποτε .NET project, καθώς και μια σειρά από πρακτικές συμβουλές για την αποφυγή κοινών παγίδων.

---

## Προαπαιτούμενα

| Απαίτηση | Γιατί Είναι Σημαντικό |
|-------------|----------------|
| **Aspose.Words for .NET** (v23.12 or later) | Το API που χρησιμοποιούμε (`LoadOptions`, `IWarningCallback`) βρίσκεται εδώ. |
| **.NET 6+** (or .NET Framework 4.7.2+) | Οι σύγχρονες δυνατότητες της γλώσσας κάνουν τον κώδικα πιο καθαρό. |
| **A sample DOCX** (named `input.docx`) placed in a known folder | Χρειαζόμαστε κάτι για να φορτώσουμε και να προκαλέσουμε μια προειδοποίηση. |
| **A console or logging framework** (optional) | Για να δείτε τις καταγεγραμμένες προειδοποιήσεις σε δράση. |

Δεν απαιτούνται επιπλέον πακέτα NuGet πέρα από το ίδιο το Aspose.Words.

---

## Βήμα 1: Ρύθμιση Προσαρμοσμένων Ρυθμίσεων Γραμματοσειράς  

Πριν φορτώσετε ένα έγγραφο, μπορείτε να πείτε στο Aspose.Words πού να ψάξει για γραμματοσειρές. Αυτό είναι το τμήμα **ορισμού προσαρμοσμένων ρυθμίσεων γραμματοσειράς** του παζλ.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using System;

// 1️⃣ Create a FontSettings instance and point it at your font folder.
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

// 2️⃣ Plug the FontSettings into LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

**Γιατί είναι σημαντικό:**  
Αν ένα DOCX αναφέρει μια γραμματοσειρά που δεν είναι εγκατεστημένη στο σύστημα, το Aspose.Words θα αντικαταστήσει σιωπηρά μια εναλλακτική γραμματοσειρά *εκτός* αν έχετε ρυθμίσει έναν φάκελο με τις απαιτούμενες γραμματοσειρές. Ορίζοντας έναν προσαρμοσμένο φάκελο μειώνετε την πιθανότητα προειδοποιήσεων «αντικατάστασης γραμματοσειράς» από την αρχή.

> **Συμβουλή:** Σε Linux ίσως χρειαστεί να προσθέσετε το πακέτο `fonts-dejavu-core` ή οποιαδήποτε συλλογή TrueType που εξαρτώνται τα έγγραφά σας.

---

## Βήμα 2: Καταχώρηση Callback Προειδοποίησης  

Το Aspose.Words υλοποιεί το `IWarningCallback`. Θα δημιουργήσουμε έναν μικρό χειριστή που εκτυπώνει μόνο τις προειδοποιήσεις που μας ενδιαφέρουν: ελλιπείς ή αντικαταστημένες γραμματοσειρές.

```csharp
// 3️⃣ Register the callback.
loadOptions.WarningCallback = new FontWarningHandler();
```

```csharp
public class FontWarningHandler : IWarningCallback
{
    public void Warn(IWarningInfo info)
    {
        // Filter for font‑substitution warnings only.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // You could log to a file, send to telemetry, etc.
            Console.WriteLine($"[Font Substitution] {info.Description}");
        }
        // Optionally handle other warning types here.
    }
}
```

**Γιατί είναι σημαντικό:**  
Το σενάριο **διαχείρισης ελλιπών γραμματοσειρών** είναι τώρα ορατό για εσάς. Αντί να μαντεύετε ποια γραμματοσειρά αντικαταστάθηκε, λαμβάνετε μια σαφή περιγραφή όπως «Η γραμματοσειρά 'Calibri' αντικαταστάθηκε με 'Arial'». Αυτό είναι ανεκτίμητο όταν εντοπίζετε προβλήματα διάταξης σε παραγόμενα PDF ή εκτυπωμένες αναφορές.

---

## Βήμα 3: Φόρτωση του Εγγράφου με τις Διαμορφωμένες Επιλογές  

Τώρα τελικά φέρνουμε το έγγραφο στη μνήμη, χρησιμοποιώντας το `LoadOptions` που μόλις προετοιμάσαμε.

```csharp
// 4️⃣ Load the DOCX. Any warnings will flow through FontWarningHandler.
Document doc = new Document(@"C:\Docs\input.docx", loadOptions);

// Quick sanity check – render the first page to PDF (optional).
doc.Save(@"C:\Docs\output.pdf");
Console.WriteLine("Document loaded and saved successfully.");
```

Αν το αρχείο προέλευσης χρησιμοποιεί μια γραμματοσειρά που δεν υπάρχει στο `C:\MyFonts`, θα δείτε έξοδο παρόμοια με:

```
[Font Substitution] Font 'OpenSans-Regular' was substituted with 'Arial'.
Document loaded and saved successfully.
```

Αυτή η γραμμή είναι το αποτέλεσμα **πώς να καταγράψετε προειδοποιήσεις** που ζητούσατε.

---

## Βήμα 4: Πλήρες Παράδειγμα Εργασίας (Έτοιμο για Αντιγραφή‑Επικόλληση)

Παρακάτω βρίσκεται ολόκληρο το πρόγραμμα, έτοιμο για μεταγλώττιση. Επικολλήστε το σε ένα νέο project κονσόλας και τρέξτε το—απλώς βεβαιωθείτε ότι οι διαδρομές δείχνουν σε πραγματικές τοποθεσίες στο σύστημά σας.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using System;

namespace AsposeWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -------------------------------------------------
            // Step 1: Prepare LoadOptions with custom FontSettings.
            // -------------------------------------------------
            FontSettings fontSettings = new FontSettings();
            fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                // Step 2: Attach the warning callback.
                WarningCallback = new FontWarningHandler()
            };

            // -------------------------------------------------
            // Step 3: Load the document – warnings flow to handler.
            // -------------------------------------------------
            string inputPath = @"C:\Docs\input.docx";
            Document doc = new Document(inputPath, loadOptions);

            // Optional: Save as PDF to verify rendering.
            string outputPath = @"C:\Docs\output.pdf";
            doc.Save(outputPath);

            Console.WriteLine("Document processed. Check console for any warning messages.");
        }
    }

    // -------------------------------------------------
    // Warning handler that focuses on missing‑font events.
    // -------------------------------------------------
    public class FontWarningHandler : IWarningCallback
    {
        public void Warn(IWarningInfo info)
        {
            if (info.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"[Font Substitution] {info.Description}");
            }
            // You could add more branches for other warning types.
        }
    }
}
```

**Αναμενόμενη έξοδος:**  

- Αν όλες οι γραμματοσειρές είναι διαθέσιμες:  
  `Document processed. Check console for any warning messages.`  

- Αν λείπει μια γραμματοσειρά:  
  ```
  [Font Substitution] Font 'Times New Roman' was substituted with 'Arial'.
  Document processed. Check console for any warning messages.
  ```

---

## Βήμα 5: Συνηθισμένες Παραλλαγές & Ακραίες Περιπτώσεις  

| Κατάσταση | Τι να Προσαρμόσετε |
|-----------|----------------|
| **Πολλαπλοί φάκελοι γραμματοσειρών** | Call `fontSettings.AddFontFolder(@"C:\MoreFonts", true);` for each additional location. |
| **Καταστολή όλων των προειδοποιήσεων** | Implement `Warn` but leave the body empty, or set `loadOptions.WarningCallback = null;`. |
| **Καταγραφή άλλων τύπων προειδοποιήσεων** | Check `info.WarningType` against `WarningType.DeprecatedFeature`, `WarningType.UnexpectedContent`, etc. |
| **Εκτέλεση σε Linux/macOS** | Ensure the font folder contains Linux‑compatible `.ttf`/`.otf` files; you may need to install `libfontconfig`. |
| **Μεγάλα έγγραφα** | Consider streaming the document (`LoadOptions.LoadFormat = LoadFormat.Docx;`) to reduce memory pressure. |

Προβλέποντας αυτά τα σενάρια, θα αποφύγετε εκπλήξεις όταν μετακινείστε από έναν υπολογιστή ανάπτυξης σε μια CI pipeline ή σε μια VM στο cloud.

---

## Βήμα 6: Οπτική Επιβεβαίωση (Προαιρετικό)

Αν προτιμάτε μια γρήγορη οπτική ένδειξη, μπορείτε να αποθηκεύσετε τις καταγεγραμμένες προειδοποιήσεις σε μια μικρή αναφορά HTML. Εδώ είναι ένα μικρό snippet που γράφει τα μηνύματα στο `warnings.html`:

```csharp
using System.IO;
using System.Text;

public class HtmlWarningHandler : IWarningCallback
{
    private readonly StringBuilder _sb = new StringBuilder();

    public void Warn(IWarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            _sb.AppendLine($"<li>{info.Description}</li>");
        }
    }

    public void WriteReport(string path)
    {
        string html = $"<html><body><h2>Font Substitution Warnings</h2><ul>{_sb}</ul></body></html>";
        File.WriteAllText(path, html);
    }
}
```

Μετά τη φόρτωση του εγγράφου, καλέστε `handler.WriteReport(@"C:\Docs\warnings.html");` και ανοίξτε το σε έναν περιηγητή. Η εικόνα παρακάτω δείχνει πώς μπορεί να φαίνεται η αναφορά:

![How to capture warnings screenshot](/images/capture-warnings.png)

*Alt text:* **πώς να καταγράψετε προειδοποιήσεις** – στιγμιότυπο της εξόδου κονσόλας και της αναφοράς HTML.

---

## Συμπέρασμα  

Καλύψαμε **πώς να καταγράψετε προειδοποιήσεις** στο Aspose.Words, παρουσιάσαμε έναν αξιόπιστο τρόπο **διαχείρισης ελλιπών γραμματοσειρών**, και σας δείξαμε πώς να **ορίσετε προσαρμοσμένες ρυθμίσεις γραμματοσειράς** για καθοριστική απόδοση. Το πλήρες παράδειγμα είναι έτοιμο να ενσωματωθεί σε οποιαδήποτε .NET λύση, και ο μοντέλο `FontWarningHandler` μπορεί να επεκταθεί ώστε να ταιριάζει στη στρατηγική logging ή telemetry σας.

Επόμενα βήματα; Δοκιμάστε να αντικαταστήσετε τις κλήσεις `Console.WriteLine` με έναν δομημένο logger όπως το Serilog, ή στείλτε τις προειδοποιήσεις στο Application Insights για παρακολούθηση σε πραγματικό χρόνο. Μπορείτε επίσης να εξερευνήσετε το πρότυπο `DocumentVisitor` αν χρειάζεται να ελέγξετε το περιεχόμενο του εγγράφου μετά τη φόρτωση.

Έχετε ερωτήσεις σχετικά με άλλους τύπους προειδοποιήσεων ή στρατηγικές ενσωμάτωσης γραμματοσειρών; Αφήστε ένα σχόλιο παρακάτω—καλή προγραμματιστική!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}