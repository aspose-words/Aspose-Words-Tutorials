---
category: general
date: 2026-01-10
description: Αποθήκευση docx ως txt σε C# με εξισώσεις LaTeX. Μάθετε πώς να μετατρέπετε
  το Word σε txt, να διαχειρίζεστε εξισώσεις και να διατηρείτε τη μορφοποίηση.
draft: false
keywords:
- save docx as txt
- convert word to txt
- how to convert docx
- save word as text
- convert word equations
language: el
og_description: Αποθηκεύστε το docx ως txt χρησιμοποιώντας C#. Αυτό το σεμινάριο δείχνει
  πώς να μετατρέψετε το Word σε txt, να εξάγετε εξισώσεις σε LaTeX και να αντιμετωπίσετε
  κοινά προβλήματα.
og_title: Αποθήκευση docx ως txt – Σύντομος οδηγός C#
tags:
- Aspose.Words
- C#
- Document Conversion
title: Αποθήκευση docx ως txt – Σύντομος οδηγός για προγραμματιστές C#
url: /el/net/programming-with-txtsaveoptions/save-docx-as-txt-quick-guide-for-c-developers/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Αποθήκευση docx ως txt – Πλήρης Εγχειρίδιο C#

Έχετε ποτέ χρειαστεί να **αποθηκεύσετε docx ως txt** αλλά δεν ήξερες πώς να διατηρήσεις τις εξισώσεις ανέπαφες; Δεν είστε μόνοι. Σε πολλά αυτοματοποιημένα pipelines πρέπει να **μετατρέψουμε Word σε txt** διατηρώντας το μαθηματικό markup, και η συνηθισμένη τεχνική αντιγραφής‑επικόλλησης δεν αρκεί.  

Σε αυτόν τον οδηγό θα περάσουμε από μια καθαρή, ολοκληρωμένη λύση που όχι μόνο **αποθηκεύει docx ως txt** αλλά επίσης εξάγει τυχόν αντικείμενα Office Math ως LaTeX. Στο τέλος θα ξέρετε πώς να **μετατρέψετε docx**, γιατί η εξαγωγή σε LaTeX είναι σημαντική, και τι να κάνετε όταν αντιμετωπίζετε ειδικές περιπτώσεις.

> **Συμβουλή:** Αν ήδη χρησιμοποιείτε Aspose.Words στο έργο σας, ο παρακάτω κώδικας θα ενσωματωθεί αμέσως χωρίς επιπλέον εξαρτήσεις.

---

## Τι Θα Χρειαστεί

- **.NET 6+** (ή οποιοδήποτε πρόσφατο .NET Framework που υποστηρίζει C# 10)
- **Aspose.Words for .NET** πακέτο NuGet (`Install-Package Aspose.Words`)
- Ένα δείγμα αρχείου `.docx` που περιέχει τουλάχιστον μία εξίσωση (αντικείμενα “Office Math” του Word)
- Ένας επεξεργαστής κειμένου ή IDE (Visual Studio, Rider, VS Code – ό,τι προτιμάτε)

Δεν απαιτούνται πρόσθετες βιβλιοθήκες· η πλήρης μετατροπή διαχειρίζεται από το Aspose.Words.

## Υλοποίηση Βήμα‑Βήμα

### ## Αποθήκευση docx ως txt – Βασικά Βήματα

Παρακάτω βρίσκεται το πλήρες, εκτελέσιμο πρόγραμμα. Αντιγράψτε‑επικολλήστε το σε ένα νέο έργο κονσόλας και πατήστε **F5**.

```csharp
// ------------------------------------------------------------
// Save docx as txt – Complete Example
// ------------------------------------------------------------
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the source document
        // Replace YOUR_DIRECTORY with the actual path on your machine.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Configure TXT save options to export equations as LaTeX
        TxtSaveOptions txtOptions = new TxtSaveOptions
        {
            // This tells Aspose.Words to turn OfficeMath objects into LaTeX strings.
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };

        // 3️⃣ Save the document as a plain‑text file with the configured options
        string outputPath = @"YOUR_DIRECTORY\Equations.txt";
        doc.Save(outputPath, txtOptions);

        Console.WriteLine($"✅ Document saved as txt at: {outputPath}");
    }
}
```

#### Γιατί Αυτά τα Τρία Βήματα Είναι Σημαντικά

1. **Φόρτωση του Εγγράφου** – `new Document(inputPath)` αναλύει το αρχείο `.docx` σε ένα μοντέλο στη μνήμη. Είναι το ίδιο μοντέλο που θα χρησιμοποιούσατε για οποιαδήποτε άλλη λειτουργία του Aspose, ώστε να μπορείτε να ελέγξετε κόμβους, να αφαιρέσετε ενότητες ή να τροποποιήσετε στυλ πριν την αποθήκευση, αν το επιθυμείτε.

2. **Διαμόρφωση του `TxtSaveOptions`** – Η ιδιότητα `OfficeMathExportMode` είναι το μυστικό συστατικό. Από προεπιλογή, το Aspose.Words αφαιρεί τις εξισώσεις κατά την αποθήκευση σε απλό κείμενο. Ορίζοντάς το σε `LaTeX` μετατρέπει κάθε αντικείμενο Office Math σε συμβολοσειρά LaTeX (π.χ., `\int_{a}^{b} f(x)\,dx`). Αυτό ικανοποιεί την απαίτηση **convert word equations** χωρίς επιπλέον λογική ανάλυσης.

3. **Αποθήκευση του Αρχείου** – `doc.Save(outputPath, txtOptions)` γράφει την αναπαράσταση κειμένου στο δίσκο. Το προκύπτον αρχείο `.txt` περιέχει κανονικές παραγράφους συν αποσπάσματα LaTeX για κάθε εξίσωση, έτοιμο για επεξεργασία σε επόμενα στάδια (Markdown, Jupyter notebooks κ.λπ.).

---

### ## Μετατροπή Word σε txt – Διαχείριση Συνηθισμένων Προβλημάτων

| Πρόβλημα | Τι Συμβαίνει | Πώς να Διορθώσετε |
|-------|--------------|------------|
| **File not found** | `FileNotFoundException` ρίχνεται κατά την εκτέλεση. | Επαληθεύστε τη διαδρομή, χρησιμοποιήστε `Path.Combine` για ασφάλεια μεταξύ πλατφορμών, ή τυλίξτε τη φόρτωση σε μπλοκ `try/catch`. |
| **Large documents (>100 MB)** | Η χρήση μνήμης αυξάνεται επειδή φορτώνεται ολόκληρο το DOCX ταυτόχρονα. | Σκεφτείτε την επεξεργασία του εγγράφου ανά ενότητες: `doc.Sections` μπορεί να επαναληφθεί και να αποθηκευτεί ξεχωριστά. |
| **Equations not exported** | `OfficeMathExportMode` παραμένει στην προεπιλογή (`Text`). | Βεβαιωθείτε ότι έχετε ορίσει `OfficeMathExportMode = OfficeMathExportMode.LaTeX` **πριν** καλέσετε το `Save`. |
| **Non‑ASCII characters become garbled** | Η προεπιλεγμένη κωδικοποίηση μπορεί να μην ταιριάζει με την τοπική σας ρύθμιση. | Ορίστε `txtOptions.Encoding = System.Text.Encoding.UTF8` για καθολική υποστήριξη. |

#### Παράδειγμα Ασφαλούς Κώδικα

```csharp
try
{
    Document doc = new Document(inputPath);
    TxtSaveOptions txtOptions = new TxtSaveOptions
    {
        OfficeMathExportMode = OfficeMathExportMode.LaTeX,
        Encoding = System.Text.Encoding.UTF8
    };
    doc.Save(outputPath, txtOptions);
}
catch (Exception ex)
{
    Console.Error.WriteLine($"❌ Failed to convert: {ex.Message}");
}
```

---

### ## Αποθήκευση Word ως Κείμενο – Προσαρμογή Εξόδου

Αν χρειάζεστε ένα αρχείο απλού κειμένου **χωρίς** LaTeX (ίσως θέλετε μόνο το ακατέργαστο κείμενο), απλώς αλλάξτε τη λειτουργία εξαγωγής:

```csharp
txtOptions.OfficeMathExportMode = OfficeMathExportMode.Text; // strips equations
```

Ή, αν προτιμάτε MathML αντί για LaTeX:

```csharp
txtOptions.OfficeMathExportMode = OfficeMathExportMode.MathML;
```

Αυτές οι παραλλαγές σας επιτρέπουν να **μετατρέψετε docx** στη συγκεκριμένη μορφή που αναμένει το επόμενο εργαλείο σας.

---

### ## Μετατροπή Εξισώσεων Word – Προχωρημένα Σενάρια

1. **Πολλαπλές Μορφές Εξισώσεων** – Κάποια έγγραφα συνδυάζουν ενσωματωμένες εξισώσεις και εξισώσεις εμφάνισης. Το Aspose.Words τις αντιμετωπίζει ομοιόμορφα, έτσι θα λάβετε μια συμβολοσειρά LaTeX για κάθε μία—χωρίς επιπλέον επεξεργασία.

2. **Διατήρηση Σειράς Εξισώσεων** – Η σειρά των αποσπασμάτων LaTeX ακολουθεί την αρχική ροή του εγγράφου Word. Αν χρειάζεται να αντιστοιχίσετε κάθε απόσπασμα στην παράγραφό του, επαναλάβετε `doc.GetChildNodes(NodeType.OfficeMath, true)` και εξάγετε τα αντικείμενα `OfficeMath` χειροκίνητα.

3. **Μετα-Επεξεργασία** – Μετά τη μετατροπή μπορεί να θέλετε να αντικαταστήσετε τα placeholders LaTeX με αποδομένες εικόνες. Ένα απλό regex μπορεί να εντοπίσει τις συμβολοσειρές που αρχίζουν με `\` και να τις δώσει σε έναν renderer LaTeX.

---

## Οπτική Επισκόπηση

![παράδειγμα αποθήκευσης docx ως txt](/images/save-docx-as-txt.png "Εικονογράφηση της διαδικασίας μετατροπής docx‑σε‑txt που δείχνει εξισώσεις LaTeX στο αρχείο εξόδου")

*Κείμενο εναλλακτικής περιγραφής:* **save docx as txt example** – διάγραμμα που δείχνει το εισερχόμενο DOCX με εξισώσεις και το προκύπτον TXT με σήμανση LaTeX.

---

## Σύνοψη & Επόμενα Βήματα

Καλύψαμε πώς να **αποθηκεύσετε docx ως txt** χρησιμοποιώντας το Aspose.Words, εξετάσαμε τη ροή εργασίας **convert word to txt**, και παρουσιάσαμε την επιλογή **convert word equations** μέσω εξαγωγής LaTeX. Ο βασικός κώδικας είναι μόνο τρεις γραμμές, αλλά διαχειρίζεται ένα απρόσμενα ευρύ φάσμα πραγματικών σεναρίων.

Τι ακολουθεί;

- **Ομαδική μετατροπή:** Επανάληψη σε έναν φάκελο με αρχεία `.docx` και δημιουργία του αντίστοιχου συνόλου αρχείων `.txt`.
- **Ενσωμάτωση με CI/CD:** Προσθέστε τη μετατροπή ως βήμα κατασκευής για αυτόματη δημιουργία τεκμηριωτικών τεχνουργημάτων.
- **Εξερεύνηση άλλων μορφών:** Το Aspose.Words υποστηρίζει επίσης αποθήκευση σε Markdown, HTML και PDF—ιδανικό αν χρειάζεστε πιο πλούσια έξοδο.

Μη διστάσετε να πειραματιστείτε με τις ρυθμίσεις του `TxtSaveOptions` για να βελτιώσετε την κωδικοποίηση, τις αλλαγές γραμμής ή ακόμη και προσαρμοσμένους οριοθέτες. Και αν αντιμετωπίσετε κάποιο πρόβλημα, τα φόρουμ της κοινότητας Aspose είναι ένας αξιόπιστος τόπος για βοήθεια.

Καλό προγραμματισμό, και εύχομαι οι εξαγωγές κειμένου σας να είναι καθαρές και οι εξισώσεις σας να αποδίδονται όμορφα!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}