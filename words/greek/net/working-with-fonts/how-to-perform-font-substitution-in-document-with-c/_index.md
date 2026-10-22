---
category: general
date: 2026-10-13
description: Μάθετε την αντικατάσταση γραμματοσειρών σε έγγραφο χρησιμοποιώντας C#.
  Αυτός ο οδηγός δείχνει πώς να ορίσετε κωδικοποίηση big5, να φορτώσετε ένα DOCX και
  να αντικαταστήσετε τις παλαιές γραμματοσειρές με σύγχρονες.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- font substitution in document
- big5 encoding
- C# LoadOptions
- legacy font replacement
- document encoding for Chinese
- Docx loading C#
language: el
lastmod: 2026-10-13
og_description: Η αντικατάσταση γραμματοσειρών σε έγγραφο είναι ουσιώδης όταν εργάζεστε
  με παλαιές κινεζικές αρχεία. Ακολουθήστε αυτό το βήμα‑προς‑βήμα οδηγό για να φορτώσετε
  ένα DOCX με κωδικοποίηση big5 και να αντικαταστήσετε τις παλιές γραμματοσειρές.
og_image_alt: Screenshot of C# code that performs font substitution in document
og_title: Αντικατάσταση γραμματοσειράς σε έγγραφο με C# – πλήρης οδηγός
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn font substitution in document using C#. This guide shows how
    to set big5 encoding, load a DOCX, and replace legacy fonts with modern ones.
  headline: How to perform font substitution in document with C#
  type: TechArticle
tags:
- C#
- Aspose.Words
- Unicode
- Chinese text
title: Πώς να πραγματοποιήσετε αντικατάσταση γραμματοσειράς σε έγγραφο με C#
url: /el/net/working-with-fonts/how-to-perform-font-substitution-in-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Αντικατάσταση γραμματοσειράς σε έγγραφο – πλήρης οδηγός C#

Αν χρειάζεστε **font substitution in document** για να αποδώσετε σωστά παλαιά κινεζικά αρχεία, αυτός ο οδηγός σας δείχνει ακριβώς πώς να το κάνετε. Διαμορφώνοντας την κατάλληλη κωδικοποίηση κειμένου και αντικαθιστώντας μια παλιά γραμματοσειρά με μια σύγχρονη, εξασφαλίζετε ότι το τελικό DOCX εμφανίζεται όπως προβλέπεται.

Η επεξεργασία εγγράφων συχνά αποτυγχάνει όταν η πηγή χρησιμοποιεί μια παλιά κωδικοποίηση όπως **big5** ή αναφέρεται σε γραμματοσειρά που δεν υπάρχει πλέον στο σύστημα. Αυτό το tutorial σας οδηγεί βήμα-βήμα στη φόρτωση ενός DOCX με τη σωστή **big5 encoding**, στην εφαρμογή **legacy font replacement**, και στην παραγωγή ενός καθαρού αποτελέσματος που λειτουργεί σε οποιονδήποτε υπολογιστή Windows.

Θα μάθετε:

* Πώς να δημιουργήσετε ένα αντικείμενο `LoadOptions` με **big5 encoding**.  
* Πώς να ανοίξετε ένα αρχείο DOCX χρησιμοποιώντας **C# LoadOptions**.  
* Πώς να εκτελέσετε **font substitution in document** χαρτογραφώντας μια παλιά γραμματοσειρά σε μια σύγχρονη ισοδύναμη.  
* Διαχείριση edge‑case για ελλιπείς γραμματοσειρές και πολλαπλές οικογένειες γραμματοσειρών.

Δεν απαιτούνται εξωτερικά εργαλεία πέρα από τη βιβλιοθήκη Aspose.Words for .NET, και ο πλήρης κώδικας μπορεί να αντιγραφεί σε ένα έργο κονσόλας και να εκτελεστεί αμέσως.

## Προαπαιτούμενα

* .NET 6.0 ή νεότερο (το παράδειγμα χρησιμοποιεί σύνταξη κονσόλας .NET 6).  
* Aspose.Words for .NET – εγκατάσταση μέσω `dotnet add package Aspose.Words`.  
* Ένα αρχείο DOCX αποθηκευμένο με **big5 encoding** που αναφέρει τη γραμματοσειρά κληρονομιάς `MingLiU-ExtB`.  
* Βασική εξοικείωση με C# και Visual Studio ή οποιοδήποτε IDE της επιλογής σας.

## Βήμα 1: Ρύθμιση του έργου και εισαγωγή namespaces

Δημιουργήστε μια νέα εφαρμογή κονσόλας και προσθέστε τις απαιτούμενες οδηγίες `using`. Αυτό εξασφαλίζει ότι ο κώδικας θα μεταγλωττιστεί χωρίς επιπλέον τροποποιήσεις.

```csharp
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSubstitutionDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The tutorial steps are called from here.
            PerformFontSubstitution();
        }

        static void PerformFontSubstitution()
        {
            // Steps 2‑4 are implemented inside this method.
        }
    }
}
```

> **Pro tip:** Κρατήστε τη μέθοδο `Main` όσο το δυνατόν πιο απλή· βελτιώνει την αναγνωσιμότητα και κάνει το tutorial πιο εύκολο στην παρακολούθηση.

## Βήμα 2: Ορισμός load options με τη σωστή κωδικοποίηση κειμένου (big5 για Παραδοσιακά Κινέζικα)

Η κλάση `LoadOptions` ενημερώνει το Aspose.Words πώς να ερμηνεύσει τα ακατέργαστα byte του αρχείου προέλευσης. Η χρήση **big5 encoding** είναι κρίσιμη για τους χαρακτήρες Παραδοσιακών Κινέζικων που αποθηκεύτηκαν με αυτήν τη κληρονομική κωδική σελίδα.

```csharp
// Step 2: Define load options with big5 encoding.
LoadOptions loadOptions = new LoadOptions
{
    // Explicitly set the encoding to the traditional Chinese code page.
    Encoding = Encoding.GetEncoding("big5")
};
```

**Why this matters:** Αν παραλείψετε την κωδικοποίηση ή χρησιμοποιήσετε το προεπιλεγμένο UTF‑8, οι χαρακτήρες μπορεί να εμφανιστούν ως ακατάληπτα σύμβολα (mojibake). Η καθορισμένη `big5` διατηρεί τα αρχικά γλύφους πριν γίνει οποιαδήποτε αντικατάσταση γραμματοσειράς.

## Βήμα 3: Φόρτωση του αρχείου DOCX χρησιμοποιώντας την καθορισμένη κωδικοποίηση

Περάστε το αντικείμενο `loadOptions` στον κατασκευαστή `Document`. Αυτό φορτώνει το αρχείο σεβόμενος τη **document encoding for Chinese** που ορίσατε νωρίτερα.

```csharp
// Step 3: Load the DOCX file with the big5 encoding.
string inputPath = @"C:\Docs\big5_doc.docx"; // Update this path to your file location.
Document doc = new Document(inputPath, loadOptions);
```

Αν το αρχείο δεν βρεθεί, το πρόγραμμα θα ρίξει μια `FileNotFoundException`. Βεβαιωθείτε ότι η διαδρομή είναι σωστή και ότι η εφαρμογή έχει δικαιώματα ανάγνωσης.

## Βήμα 4: Αντικατάσταση μιας παλαιάς γραμματοσειράς με μια σύγχρονη ισοδύναμη

Πολλά παλαιότερα κινεζικά έγγραφα αναφέρουν το `MingLiU-ExtB`, το οποίο μπορεί να μην υπάρχει σε νεότερες εγκαταστάσεις των Windows. Η αντιστοίχιση του με το `Microsoft JhengHei` (μια ευρέως διαθέσιμη γραμματοσειρά Unicode) εξασφαλίζει σωστή απόδοση.

```csharp
// Step 4: Perform font substitution in document.
doc.FontInfos.Substitution.Add("MingLiU-ExtB", "Microsoft JhengHei");

// Optional: Verify that the substitution succeeded.
foreach (FontInfo fontInfo in doc.FontInfos)
{
    Console.WriteLine($"Original: {fontInfo.FontFamilyName}, Substituted: {fontInfo.SubstitutedFontFamilyName}");
}
```

**Explanation:**  
* `FontInfos.Substitution.Add(oldFont, newFont)` καταχωρεί έναν παγκόσμιο κανόνα αντικατάστασης. Κάθε φορά που το Aspose.Words συναντά το `MingLiU-ExtB`, το αντικαθιστά με το `Microsoft JhengHei`.  
* Ο προαιρετικός βρόχος εκτυπώνει την αντιστοίχιση, κάτι που είναι χρήσιμο για εντοπισμό σφαλμάτων σε μεγάλα έγγραφα με πολλαπλές οικογένειες γραμματοσειρών.

## Βήμα 5: Αποθήκευση του επεξεργασμένου εγγράφου

Μετά την αντικατάσταση, γράψτε το έγγραφο σε νέο αρχείο. Η έξοδος θα εμφανίζει το κινεζικό κείμενο χρησιμοποιώντας τη σύγχρονη γραμματοσειρά, εξαλείφοντας τις προειδοποιήσεις για ελλιπείς γλύφους.

```csharp
// Step 5: Save the updated document.
string outputPath = @"C:\Docs\big5_doc_fixed.docx";
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved to {outputPath}");
```

Ανοίξτε το παραγόμενο αρχείο στο Microsoft Word ή σε οποιονδήποτε προβολέα DOCX· θα πρέπει να δείτε τους χαρακτήρες Παραδοσιακών Κινέζικων να αποδίδονται καθαρά με το `Microsoft JhengHei`.

## Διαχείριση edge cases και κοινών παγίδων

| Κατάσταση | Συνιστώμενη προσέγγιση |
|-----------|----------------------|
| **The source font is not listed in the document** | Χρησιμοποιήστε `doc.FontInfos.Substitution.Add` με μοτίβο μπαλαντέρ, π.χ., `doc.FontInfos.Substitution.Add("*MingLiU*", "Microsoft JhengHei")`. |
| **Multiple legacy fonts need replacement** | Κλήση `Add` για κάθε ζεύγος, ή φόρτωση λεξικού αντικατάστασης από αρχείο ρυθμίσεων. |
| **The target font is unavailable on the target machine** | Επιλέξτε μια γραμματοσειρά που περιλαμβάνεται στα Windows (π.χ., `Arial Unicode MS`) ή ενσωματώστε τη γραμματοσειρά χρησιμοποιώντας `doc.FontInfos.EmbeddingMode = FontEmbeddingMode.EmbedAll`. |
| **Encoding errors still appear** | Επαληθεύστε ότι το αρχείο προέλευσης χρησιμοποιεί πραγματικά **big5**· μπορείτε να το ελέγξετε με έναν επεξεργαστή hex ή με `File.ReadAllBytes` και σύγκριση των προτύπων byte. |

## Πλήρες λειτουργικό παράδειγμα

Παρακάτω βρίσκεται το ολοκληρωμένο, αυτόνομο πρόγραμμα. Αντιγράψτε το στο `Program.cs`, προσαρμόστε τις διαδρομές αρχείων και εκτελέστε το.

```csharp
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSubstitutionDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            PerformFontSubstitution();
        }

        static void PerformFontSubstitution()
        {
            // 1️⃣ Define big5 encoding for Traditional Chinese.
            LoadOptions loadOptions = new LoadOptions
            {
                Encoding = Encoding.GetEncoding("big5")
            };

            // 2️⃣ Load the DOCX that uses the legacy font.
            string inputPath = @"C:\Docs\big5_doc.docx";
            Document doc = new Document(inputPath, loadOptions);

            // 3️⃣ Substitute MingLiU-ExtB with Microsoft JhengHei.
            doc.FontInfos.Substitution.Add("MingLiU-ExtB", "Microsoft JhengHei");

            // 4️⃣ (Optional) Log substitution details for verification.
            foreach (FontInfo fontInfo in doc.FontInfos)
            {
                Console.WriteLine($"Original: {fontInfo.FontFamilyName}, Substituted: {fontInfo.SubstitutedFontFamilyName}");
            }

            // 5️⃣ Save the corrected document.
            string outputPath = @"C:\Docs\big5_doc_fixed.docx";
            doc.Save(outputPath, SaveFormat.Docx);

            Console.WriteLine($"✅ Font substitution in document completed. Output saved to {outputPath}");
        }
    }
}
```

**Expected result:** Το άνοιγμα του `big5_doc_fixed.docx` εμφανίζει όλους τους χαρακτήρες Παραδοσιακών Κινέζικων σωστά αποδομένους, χωρίς προειδοποιήσεις για ελλιπείς γλύφους, επειδή το `MingLiU-ExtB` έχει αντικατασταθεί από το `Microsoft JhengHei`.

## Συμπέρασμα

Τώρα διαθέτετε μια αξιόπιστη μέθοδο για εργασίες **font substitution in document** χρησιμοποιώντας C#. Με τη ρύθμιση της **big5 encoding**, τη φόρτωση του DOCX με `LoadOptions` και την αντιστοίχιση κληρονομικών γραμματοσειρών σε σύγχρονες ισοδύναμες, εξαλείφετε τα προβλήματα απόδοσης που επηρεάζουν τα παλαιότερα κινεζικά αρχεία.  

Από εδώ μπορείτε:

* Να επεκτείνετε τον χάρτη αντικατάστασης ώστε να καλύπτει επιπλέον κληρονομικές γραμματοσειρές.  
* Να αυτοματοποιήσετε τη διαδικασία για ομάδες εγγράφων (βρόχος πάνω σε έναν φάκελο).  
* Να συνδυάσετε την αντικατάσταση γραμματοσειράς με άλλες μετασχηματισμούς εγγράφων, όπως υδατογράφημα ή μετατροπή σε PDF.

Νιώστε ελεύθεροι να πειραματιστείτε με διαφορετικές γραμματοσειρές-στόχους ή να ενσωματώσετε προσαρμοσμένες γραμματοσειρές για πλήρη φορητότητα. Αν αντιμετωπίσετε προβλήματα, επανεξετάστε τον πίνακα edge‑case παραπάνω ή συμβουλευτείτε την τεκμηρίωση του Aspose.Words για προχωρημένη διαχείριση γραμματοσειρών.

Happy coding!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετικές θεματικές που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Log Font Substitution Warnings – Complete Aspose.Words Guide](/words/english/net/working-with-fonts/log-font-substitution-warnings-complete-aspose-words-guide/)
- [Load With Encoding In Word Document](/words/english/net/programming-with-loadoptions/load-with-encoding/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}