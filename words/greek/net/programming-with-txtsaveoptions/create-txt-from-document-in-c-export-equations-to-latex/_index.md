---
category: general
date: 2026-06-02
description: Δημιουργία txt από έγγραφο σε C# και αποθήκευση απλού κειμένου Word ενώ
  εξάγετε εξισώσεις LaTeX χρησιμοποιώντας το Aspose.Words – βήμα‑βήμα οδηγός.
draft: false
keywords:
- create txt from document
- save word plain text
- export equations latex
language: el
og_description: Δημιουργήστε αρχείο txt από έγγραφο σε C# και αποθηκεύστε απλό κείμενο
  Word, ενώ εξάγετε εξισώσεις LaTeX χρησιμοποιώντας το Aspose.Words – πλήρης οδηγός.
og_title: Δημιουργία txt από έγγραφο σε C# – Εξαγωγή εξισώσεων σε LaTeX
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Create txt from document in C# and save Word plain text while export
    equations latex using Aspose.Words – step‑by‑step guide.
  headline: Create txt from document in C# – Export equations to LaTeX
  type: TechArticle
- description: Create txt from document in C# and save Word plain text while export
    equations latex using Aspose.Words – step‑by‑step guide.
  name: Create txt from document in C# – Export equations to LaTeX
  steps:
  - name: What if I need **save word plain text** without any LaTeX conversion?
    text: Simply omit the `OfficeMathExportMode` line or set it to `OfficeMathExportMode.Text`.
      The equations will be rendered as plain Unicode characters (e.g., “x = (‑b ±
      √(b²‑4ac)) / 2a”).
  - name: Can I export to other formats (Markdown, HTML) while keeping LaTeX?
    text: Yes. Aspose.Words also supports `MarkdownSaveOptions` and `HtmlSaveOptions`
      with similar `OfficeMathExportMode` settings. Switch the options class, keep
      the `OfficeMathExportMode = OfficeMathExportMode.LaTeX`, and you’ll get LaTeX
      embedded in the target markup.
  - name: How do I handle large documents (hundreds of MB)?
    text: 'Use `LoadOptions` with `LoadFormat.Auto` and consider streaming the output:'
  type: HowTo
tags:
- Aspose.Words
- C#
- LaTeX
title: Δημιουργία txt από έγγραφο σε C# – Εξαγωγή εξισώσεων σε LaTeX
url: /el/net/programming-with-txtsaveoptions/create-txt-from-document-in-c-export-equations-to-latex/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία txt από έγγραφο σε C# – Εξαγωγή εξισώσεων σε LaTeX

Έχετε αναρωτηθεί ποτέ πώς να **create txt from document** χωρίς να χάσετε τα μαθηματικά που πληκτρολόγησατε για ώρες; Δεν είστε ο μόνος. Σε πολλές αλυσίδες αναφορών χρειάζεστε μια έκδοση plain‑text ενός αρχείου Word, αλλά θέλετε ακόμα οι εξισώσεις να αποδίδονται ως LaTeX ώστε τα επόμενα εργαλεία να μπορούν να τις επεξεργαστούν.  

Σε αυτό το tutorial θα περάσουμε βήμα-βήμα τις ακριβείς ενέργειες για **save word plain text** ενώ **export equations latex** χρησιμοποιώντας τη δυνατή βιβλιοθήκη Aspose.Words για .NET. Στο τέλος θα έχετε ένα έτοιμο κομμάτι κώδικα που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο C#.

## Τι θα μάθετε

- Εγκαταστήστε και αναφέρετε το Aspose.Words σε ένα έργο .NET.  
- Φορτώστε ένα `.docx` που περιέχει αντικείμενα OfficeMath.  
- Διαμορφώστε το `TxtSaveOptions` ώστε ο εξαγωγέας να παράγει LaTeX για κάθε εξίσωση.  
- Γράψτε το παραγόμενο αρχείο plain‑text στο δίσκο.  
- Επαληθεύστε ότι οι εξισώσεις εμφανίζονται ως σήμανση LaTeX μέσα στο `.txt`.  

Δεν απαιτείται προηγούμενη εμπειρία με το Aspose· αρκεί μια βασική εξοικείωση με το C# και το Visual Studio.

---

## Προαπαιτούμενα

| Απαίτηση | Γιατί είναι σημαντική |
|-------------|----------------|
| .NET 6.0 ή νεότερο | Μοντέρνα χαρακτηριστικά της γλώσσας και καλύτερη απόδοση |
| Visual Studio 2022 (ή VS Code) | Βολικό debugging και δημιουργία δομής έργου |
| Aspose.Words for .NET (NuGet) | Η βιβλιοθήκη που διαχειρίζεται τη μετατροπή OfficeMath → LaTeX |
| Έγγραφο Word που περιέχει εξισώσεις | Για να δείτε την εξαγωγή LaTeX σε δράση |

Αν κάποιο από αυτά λείπει, κάντε παύση τώρα και εγκαταστήστε το· διαφορετικά ο κώδικας δεν θα μεταγλωττιστεί.

---

## Βήμα 1 – Εγκατάσταση Aspose.Words μέσω NuGet

Για αρχή, ανοίξτε τη λύση σας, κάντε δεξί‑κλικ στο έργο και επιλέξτε **Manage NuGet Packages**. Αναζητήστε το **Aspose.Words** και πατήστε **Install**.  

Ή, αν προτιμάτε τη γραμμή εντολών, εκτελέστε:

```powershell
dotnet add package Aspose.Words
```

> **Pro tip:** Χρησιμοποιήστε την πιο πρόσφατη σταθερή έκδοση· από τον Ιούνιο 2026 είναι η **23.9.0**. Αυτό εξασφαλίζει ότι θα έχετε τις νεότερες βελτιώσεις εξαγωγής OfficeMath.

---

## Βήμα 2 – Φόρτωση του Πηγαίου Εγγράφου Word

Τώρα χρειαζόμαστε ένα αντικείμενο `Document` που αντιπροσωπεύει το `.docx` που θέλετε να μετατρέψετε. Το παρακάτω απόσπασμα υποθέτει ότι το αρχείο βρίσκεται σε φάκελο με όνομα `Input`.

```csharp
using Aspose.Words;

// Load the Word file (change the path as needed)
Document doc = new Document(@"Input\sample_with_equations.docx");

// Quick sanity check – how many OfficeMath objects do we have?
int equationCount = doc.GetChildNodes(NodeType.OfficeMath, true).Count;
Console.WriteLine($"Found {equationCount} equation(s) to export.");
```

Η κλήση `GetChildNodes` είναι προαιρετική αλλά χρήσιμη· σας λέει αν το έγγραφο περιέχει πράγματι εξισώσεις πριν χάσετε χρόνο στην εξαγωγή.

---

## Βήμα 3 – Διαμόρφωση TxtSaveOptions για **export equations latex**

Αυτή είναι η ουσία. Το `TxtSaveOptions` σας επιτρέπει να ρυθμίσετε πώς δημιουργείται το plain‑text. Ορίζοντας το `OfficeMathExportMode` σε `LaTeX` λέτε στο Aspose να αντικαταστήσει κάθε αντικείμενο OfficeMath με την αναπαράστασή του σε LaTeX.

```csharp
using Aspose.Words.Saving;

// Step 3: Configure TXT save options to export OfficeMath as LaTeX
TxtSaveOptions txtOptions = new TxtSaveOptions
{
    // This flag converts every equation into LaTeX syntax.
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,

    // Optional: Preserve line breaks exactly as they appear in Word.
    PreserveTableLayout = true
};
```

Γιατί να ασχοληθείτε με το `PreserveTableLayout`; Αν το έγγραφό σας συνδυάζει εξισώσεις μέσα σε πίνακες, αυτή η σημαία διατηρεί την οπτική στοίχιση όταν αργότερα προβάλετε το `.txt`. Δεν είναι υποχρεωτικό, αλλά οι περισσότερες πραγματικές αναφορές το ωφελούνται.

---

## Βήμα 4 – **Save Word plain text** χρησιμοποιώντας τις ρυθμισμένες επιλογές

Με τις επιλογές έτοιμες, η πραγματική αποθήκευση είναι μια γραμμή κώδικα. Θα γράψουμε το αποτέλεσμα σε φάκελο `Output`.

```csharp
// Step 4: Save the document as a plain‑text file using the configured options
string outputPath = @"Output\exported.txt";
doc.Save(outputPath, txtOptions);

Console.WriteLine($"Document saved as plain text at: {outputPath}");
```

Όταν ανοίξετε το `exported.txt`, θα δείτε κανονικές παραγράφους εναλλασσόμενες με τμήματα LaTeX όπως `\int_{0}^{\infty} e^{-x} dx`. Το υπόλοιπο περιεχόμενο παραμένει αμετάβλητο, προσφέροντάς σας μια αληθινή εμπειρία **create txt from document**.

---

## Βήμα 5 – Επαλήθευση του Αποτελέσματος (και μια γρήγορη συμβουλή για αποσφαλμάτωση)

Ανοίξτε το παραγόμενο αρχείο σε οποιονδήποτε επεξεργαστή κειμένου. Θα πρέπει να δείτε κάτι παρόμοιο με:

```
This is a sample report.

The quadratic formula is given by:
\[
x = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}
\]

Another paragraph follows...
```

Αν τα τμήματα LaTeX λείπουν, ελέγξτε ξανά ότι το πηγαίο έγγραφό σας περιέχει πραγματικά αντικείμενα `OfficeMath` και ότι έχετε αναφερθεί στη σωστή έκδοση του Aspose. Επίσης, βεβαιωθείτε ότι η ιδιότητα `OfficeMathExportMode` δεν έχει αντικατασταθεί αλλού στον κώδικά σας.

---

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

### Τι κάνω αν χρειάζομαι **save word plain text** χωρίς καμία μετατροπή σε LaTeX;

Απλώς παραλείψτε τη γραμμή `OfficeMathExportMode` ή ορίστε την σε `OfficeMathExportMode.Text`. Οι εξισώσεις θα αποδοθούν ως απλοί χαρακτήρες Unicode (π.χ., “x = (‑b ± √(b²‑4ac)) / 2a”).

### Μπορώ να εξάγω σε άλλες μορφές (Markdown, HTML) διατηρώντας το LaTeX;

Ναι. Το Aspose.Words υποστηρίζει επίσης `MarkdownSaveOptions` και `HtmlSaveOptions` με παρόμοιες ρυθμίσεις `OfficeMathExportMode`. Αλλάξτε την κλάση επιλογών, διατηρήστε το `OfficeMathExportMode = OfficeMathExportMode.LaTeX`, και θα έχετε LaTeX ενσωματωμένο στο τελικό σήμα.

### Πώς να διαχειριστώ μεγάλα έγγραφα (εκατοντάδες MB);

Χρησιμοποιήστε `LoadOptions` με `LoadFormat.Auto` και σκεφτείτε τη ροή εξόδου:

```csharp
using (FileStream fs = new FileStream(outputPath, FileMode.Create))
{
    doc.Save(fs, txtOptions);
}
```

Η ροή μειώνει την πίεση μνήμης και επιταχύνει τη διαδικασία **create txt from document**.

---

## Πλήρες Παράδειγμα Εργασίας (Έτοιμο για Αντιγραφή‑Επικόλληση)

Παρακάτω είναι το πλήρες πρόγραμμα που μπορείτε να μεταγλωττίσετε και να εκτελέσετε αμέσως. Συγκεντρώνει όλα τα προηγούμενα βήματα σε μια μοναδική μέθοδο `Main`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the source Word document
        string inputPath = @"Input\sample_with_equations.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Optional sanity check – count equations
        int eqCount = doc.GetChildNodes(NodeType.OfficeMath, true).Count;
        Console.WriteLine($"Found {eqCount} equation(s).");

        // 3️⃣ Configure TxtSaveOptions to export equations as LaTeX
        TxtSaveOptions txtOptions = new TxtSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX,
            PreserveTableLayout = true
        };

        // 4️⃣ Save as plain‑text file
        string outputPath = @"Output\exported.txt";
        doc.Save(outputPath, txtOptions);

        Console.WriteLine($"✅ Finished! Plain‑text saved to: {outputPath}");
    }
}
```

**Αναμενόμενη έξοδος στην κονσόλα:**

```
Found 3 equation(s).
✅ Finished! Plain‑text saved to: Output\exported.txt
```

Ανοίξτε το `exported.txt` και θα δείτε τα τμήματα LaTeX εναλλασσόμενα με κανονικό κείμενο—ακριβώς αυτό που απαιτεί η απαίτηση **create txt from document**.

---

## Συμπέρασμα

Μόλις δείξαμε πώς να **create txt from document** σε C# ενώ με υπευθυνότητα **save word plain text** και **export equations latex** χρησιμοποιώντας το Aspose.Words. Το κύριο συμπέρασμα; Μερικές γραμμές ρύθμισης (`TxtSaveOptions`) ανοίγουν τη δυνατότητα διατήρησης της μαθηματικής ακεραιότητας ακόμη και σε ένα απλοποιημένο αρχείο `.txt`.

Από εδώ μπορείτε να:

- Ενσωματώσετε το παραγόμενο `.txt` σε έναν static‑site generator που καταλαβαίνει LaTeX.  
- Τροφοδοτήσετε το σε μια αλυσίδα επιστημονικής δημοσίευσης που αναμένει ακατέργαστο σήμα LaTeX.  
- Επεκτείνετε τον κώδικα για μαζική επεξεργασία δεκάδων αρχείων Word αυτόματα.

Ό,τι και αν είναι το επόμενο βήμα, έχετε τώρα μια σταθερή, αξιόπιστη βάση. Έχετε περισσότερες ερωτήσεις; Αφήστε ένα σχόλιο, και καλή προγραμματιστική!  

![Create txt from document example](/images/create-txt-from-document.png "Screenshot showing the exported txt with LaTeX equations – create txt from document")

---

## Τι Θα Μάθετε Στη Σύντομη Μελλοντική

Τα παρακάτω tutorials καλύπτουν στενά σχετικές θεματικές που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε σε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Αποθήκευση Εγγράφου ως Txt – Εξαγωγή Μαθηματικών Word σε LaTeX σε C#](/words/english/net/programming-with-officemath/save-document-as-txt-export-word-math-to-latex-in-c/)
- [Αποθήκευση docx ως txt – Εξαγωγή Μαθηματικών Word σε LaTeX με C#](/words/english/net/programming-with-officemath/save-docx-as-txt-export-word-math-to-latex-with-c/)
- [Αποθήκευση Εγγράφου ως TXT – Πλήρης Οδηγός C# για Μετατροπή DOCX σε Plain Text](/words/english/net/programming-with-txtsaveoptions/save-document-as-txt-complete-c-guide-to-convert-docx-to-pla/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}