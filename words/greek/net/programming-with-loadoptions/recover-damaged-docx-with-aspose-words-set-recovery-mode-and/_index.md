---
category: general
date: 2026-01-13
description: Μάθετε πώς να ανακτήσετε κατεστραμμένα αρχεία docx χρησιμοποιώντας το
  Aspose.Words. Ορίστε τη λειτουργία ανάκτησης, χρησιμοποιήστε τις επιλογές φόρτωσης
  του Aspose και φορτώστε την ανάκτηση εγγράφου Word σε λίγα λεπτά.
draft: false
keywords:
- recover damaged docx
- set recovery mode
- recover corrupted word
- aspose load options
- load word document recovery
language: el
og_description: Ανακτήστε άμεσα κατεστραμμένα αρχεία docx. Αυτός ο οδηγός δείχνει
  πώς να ορίσετε τη λειτουργία ανάκτησης, να χρησιμοποιήσετε τις επιλογές φόρτωσης
  του Aspose και να ανακτήσετε κατεστραμμένα έγγραφα Word.
og_title: Ανάκτηση κατεστραμμένου docx – Οδηγός Aspose.Words για ορισμό λειτουργίας
  ανάκτησης
tags:
- Aspose.Words
- C#
- Document Recovery
title: Ανάκτηση κατεστραμμένου docx με το Aspose.Words – ορισμός λειτουργίας ανάκτησης
  και επιλογών φόρτωσης
url: /el/net/programming-with-loadoptions/recover-damaged-docx-with-aspose-words-set-recovery-mode-and/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ανάκτηση κατεστραμμένου docx – Πλήρης Οδηγός για τη Λειτουργία Ανάκτησης του Aspose.Words

Έχετε βρεθεί ποτέ αντιμέτωποι με ένα **κατεστραμμένο docx** αρχείο που αρνείται να ανοίξει; Δεν είστε μόνοι—κατεστραμμένα έγγραφα Word εμφανίζονται πιο συχνά απ' ό,τι θα θέλαμε, ειδικά μετά από ξαφνικές διακοπές ή προβλήματα δικτύου. Τα καλά νέα; Με το Aspose.Words μπορείτε να **ανακτήσετε κατεστραμμένα docx** αρχεία με λίγες γραμμές κώδικα C#, και θα είστε ξανά σε επεξεργασία σε ελάχιστο χρόνο.

Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα από τις ακριβείς ενέργειες για **ανάκτηση κατεστραμμένου docx** αρχείων, θα σας δείξουμε πώς να **ρυθμίσετε τη λειτουργία ανάκτησης**, θα εξερευνήσουμε τις λεπτομέρειες των **aspose load options**, και ακόμη θα συζητήσουμε τι να κάνετε όταν χρειάζεται να **ανακτήσετε κατεστραμμένα word** έγγραφα που φαίνονται ακατάσπαστα. Στο τέλος, θα έχετε ένα σταθερό, έτοιμο για παραγωγή snippet που μπορείτε να ενσωματώσετε σε οποιοδήποτε .NET project.

> **Pro tip:** Ακόμη και αν το αρχείο σας δεν είναι εντελώς κατεστραμμένο, η ενεργοποίηση της λειτουργίας ανάκτησης μπορεί να βελτιώσει την ταχύτητα φόρτωσης παρακάμπτοντας περιττές επικυρώσεις.

---

## Τι Θα Χρειαστείτε

Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε:

- **Aspose.Words for .NET** (το πιο πρόσφατο πακέτο NuGet, έκδοση 24.5 ή νεότερη).  
- Ένα .NET περιβάλλον ανάπτυξης (Visual Studio, Rider ή VS Code).  
- Το **κατεστραμμένο docx** που θέλετε να διορθώσετε (θα το ονομάσουμε `input.docx`).  

Καμία επιπλέον βιβλιοθήκη, καμία πολύπλοκη ρύθμιση—μόνο τα βασικά.

---

## recover damaged docx – ρύθμιση LoadOptions

Η καρδιά της λύσης βρίσκεται στο **Aspose.LoadOptions**. Αυτό το αντικείμενο λέει στο Aspose.Words πώς να αντιμετωπίσει προβληματικά τμήματα ενός αρχείου. Από προεπιλογή, η βιβλιοθήκη πετάει εξαίρεση όταν συναντά κατεστραμμένα δεδομένα. Θα αλλάξουμε αυτή τη συμπεριφορά.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

// Step 1: Create LoadOptions and tell Aspose how to behave
LoadOptions loadOptions = new LoadOptions
{
    // Step 2: Choose the recovery mode – skip corrupted parts and load the rest
    RecoveryMode = RecoveryMode.SkipCorruptedParts   // alternatives: RecoverAll, ThrowException
};
```

**Γιατί είναι σημαντικό:**  
- `RecoveryMode.SkipCorruptedParts` λέει στη μηχανή να αγνοήσει τα μη αναγνώσιμα τμήματα ενώ συνεχίζει να κατασκευάζει το υπόλοιπο του εγγράφου.  
- `RecoveryMode.RecoverAll` προσπαθεί μια πιο βαθιά διόρθωση αλλά μπορεί να είναι πιο αργή.  
- `RecoveryMode.ThrowException` είναι η αυστηρή προεπιλογή—χρησιμοποιήστε το μόνο όταν θέλετε να τερματίσετε σε οποιοδήποτε σφάλμα.

Αν αντιμετωπίζετε ένα σενάριο **recover corrupted word** όπου χρειάζεστε κάθε παράγραφο άθικτη, ίσως προτιμήσετε το `RecoverAll`. Για γρήγορες προεπισκοπήσεις, το `SkipCorruptedParts` είναι συνήθως η ιδανική επιλογή.

---

## set recovery mode – φόρτωση του εγγράφου

Τώρα που έχουμε το `LoadOptions`, το περνάμε απλώς στον κατασκευαστή του `Document`. Εδώ συμβαίνει η **load word document recovery** στην πράξη.

```csharp
// Step 3: Load the potentially damaged DOCX using the configured options
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

Όταν εκτελεστεί αυτή η γραμμή, το Aspose.Words διαβάζει το `input.docx`, εφαρμόζει τη στρατηγική ανάκτησης που επιλέξατε, και επιστρέφει ένα αντικείμενο `Document` που μπορείτε να χειριστείτε—να αποθηκεύσετε, να επεξεργαστείτε ή να εξάγετε σε PDF, HTML κ.λπ.

**Συχνή ερώτηση:** *Τι γίνεται αν η διαδρομή του αρχείου είναι λανθασμένη;*  
Το Aspose θα πετάξει `FileNotFoundException` πριν καν αγγίξει τη λογική ανάκτησης, οπότε ελέγξτε ξανά τη διαδρομή ή χρησιμοποιήστε `Path.Combine` για ασφάλεια.

---

## aspose load options – λεπτομερής ρύθμιση για ακραίες περιπτώσεις

Η κλάση `LoadOptions` προσφέρει περισσότερα από το `RecoveryMode`. Ακολουθούν μερικές ρυθμίσεις που μπορεί να βρείτε χρήσιμες όταν **ανακτάτε κατεστραμμένα docx** αρχεία:

| Ιδιότητα | Τυπική Χρήση | Παράδειγμα |
|----------|-------------|------------|
| `Password` | Άνοιγμα αρχείων με κωδικό | `loadOptions.Password = "mySecret";` |
| `Encoding` | Εξαναγκασμός συγκεκριμένης κωδικοποίησης κειμένου (σπάνιο για DOCX) | `loadOptions.Encoding = Encoding.UTF8;` |
| `ValidateStructure` | Παράλειψη επικύρωσης δομής για ταχύτητα | `loadOptions.ValidateStructure = false;` |

Πρακτικό σενάριο: λαμβάνετε ένα DOCX ένα παλιό σύστημα που μερικές φορές προσθέτει αόρατους χαρακτήρες ελέγχου. Η ρύθμιση `ValidateStructure = false` μπορεί να αποτρέψει περιττές αποτυχίες κατά τις προσπάθειες **recover corrupted word**.

---

## load word document recovery – αποθήκευση του διορθωμένου αρχείου

Μόλις το έγγραφο φορτωθεί, μπορείτε να το αποθηκεύσετε στην ίδια μορφή ή να το μετατρέψετε σε νέο αρχείο. Η αποθήκευση ουσιαστικά ξαναγράφει το εσωτερικό XML, αφαιρώντας τα κατεστραμμένα τμήματα που παραλήφθηκαν.

```csharp
// Step 4: Save the recovered document to a new file
document.Save("YOUR_DIRECTORY/output_recovered.docx");
```

Αν προτιμάτε διαφορετική μορφή (PDF, HTML κ.λπ.), απλώς αλλάξτε την επέκταση ή χρησιμοποιήστε μια υπερφόρτωση:

```csharp
document.Save("output.pdf", SaveFormat.Pdf);
```

**Γιατί να αποθηκεύσετε;**  
Αν και το `Document` στη μνήμη είναι χρησιμοποιήσιμο, η μόνιμη αποθήκευση καθαρίζει τα σπασμένα τμήματα, δίνοντάς σας ένα καθαρό αρχείο που μπορείτε να μοιραστείτε με συναδέλφους που δεν έχουν εγκατεστημένο το Aspose.

---

## Πρακτικές Συμβουλές & Πιθανά Προβλήματα

- **Pro tip:** Πάντα κρατήστε αντίγραφο ασφαλείας του αρχικού αρχείου. Η παράλειψη κατεστραμμένων τμημάτων είναι μη αναστρέψιμη μόλις αντικαταστήσετε την πηγή.  
- **Προσοχή σε:** Μεγάλα έγγραφα (>100 MB) μπορεί να καταναλώσουν σημαντική μνήμη κατά την ανάκτηση. Σκεφτείτε να φορτώσετε με `LoadOptions.LoadFormat = LoadFormat.Docx` ρητά για να αποφύγετε το κόστος αυτόματης ανίχνευσης.  
- **Ακραία περίπτωση:** Κάποια κατεστραμμένα αρχεία περιέχουν σπασμένες εικόνες. Αν χρειάζεται να τις διατηρήσετε, χρησιμοποιήστε `RecoveryMode.RecoverAll` και μετά ελέγξτε χειροκίνητα το `document.GetChildNodes(NodeType.Shape, true)`.  
- **Συμβουλή απόδοσης:** Απενεργοποιήστε το `ValidateStructure` όταν είστε σίγουροι ότι το βασικό XML του αρχείου είναι άθικτο· αυτό μπορεί να μειώσει δευτερόλεπτα από τον χρόνο φόρτωσης.

---

## Πλήρες Παράδειγμα Εφαρμογής

Παρακάτω υπάρχει μια αυτόνομη εφαρμογή κονσόλας που δείχνει όλη τη ροή εργασίας—από τη ρύθμιση της λειτουργίας ανάκτησης μέχρι την αποθήκευση του διορθωμένου εγγράφου.

```csharp
// ------------------------------------------------------------
// recover damaged docx – full console example
// ------------------------------------------------------------
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // Path to the possibly corrupted DOCX
        string inputPath = @"C:\Docs\input.docx";
        string outputPath = @"C:\Docs\output_recovered.docx";

        // 1️⃣ Create LoadOptions with the desired recovery mode
        LoadOptions loadOptions = new LoadOptions
        {
            RecoveryMode = RecoveryMode.SkipCorruptedParts, // change as needed
            // Optional tweaks:
            // Password = "secret", 
            // ValidateStructure = false
        };

        try
        {
            // 2️⃣ Load the document using the configured options
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");

            // 3️⃣ Save the recovered version
            doc.Save(outputPath);
            Console.WriteLine($"Recovered file saved to: {outputPath}");
        }
        catch (Exception ex)
        {
            Console.WriteLine("An error occurred while recovering the document:");
            Console.WriteLine(ex.Message);
        }
    }
}
```

**Αναμενόμενο αποτέλεσμα:**  
```
Document loaded successfully.
Recovered file saved to: C:\Docs\output_recovered.docx
```

Αν το αρχικό `input.docx` περιείχε κατεστραμμένες παραγράφους, αυτές θα παραλειφθούν στο `output_recovered.docx`, ενώ το υπόλοιπο περιεχόμενο (στυλ, πίνακες, εικόνες) παραμένει άθικτο.

---

## Συχνές Ερωτήσεις

**Ε: Λειτουργεί αυτό με αρχεία .doc (δυαδικά);**  
Α: Ναι. Το `LoadOptions` λειτουργεί με οποιαδήποτε μορφή υποστηρίζει το Aspose.Words. Απλώς αλλάξτε την επέκταση του αρχείου· η ίδια λειτουργία ανάκτησης εφαρμόζεται.

**Ε: Μπορώ να ανακτήσω ένα DOCX προστατευμένο με κωδικό;**  
Α: Απόλυτα. Ορίστε `loadOptions.Password` πριν τη φόρτωση. Η λειτουργία ανάκτησης θα ισχύει και μετά την αποκρυπτογράφηση.

**Ε: Τι κάνω αν χρειάζομαι το κατεστραμμένο κείμενο για δικανική ανάλυση;**  
Α: Χρησιμοποιήστε `RecoveryMode.RecoverAll`. Προσπαθεί να διατηρήσει όσο το δυνατόν περισσότερα δεδομένα, αν και ίσως χρειαστεί να αναλύσετε το παραγόμενο XML χειροκίνητα.

---

## Συμπέρασμα

Καλύψαμε όλα όσα χρειάζεστε για να **ανακτήσετε κατεστραμμένα docx** αρχεία χρησιμοποιώντας το Aspose.Words: ρύθμιση **aspose load options**, **set recovery mode**, αντιμετώπιση σεναρίων **recover corrupted word**, και τελικά αποθήκευση ενός καθαρού εγγράφου. Ο κώδικας είναι σύντομος, οι έννοιες σαφείς, και η προσέγγιση κλιμακώνεται από μικρές αναφορές μέχρι τεράστιες συμβάσεις.

Τι θα κάνετε μετά; Δοκιμάστε να αλλάξετε τη μορφή εξόδου σε PDF, εξερευνήστε προσαρμοσμένη καταγραφή σφαλμάτων, ή ενσωματώστε αυτή τη λογική σε ένα web API που αυτο‑διορθώνει τα ανεβασμένα έγγραφα. Οι δυνατότητες είναι ατελείωτες, και με τη σωστή **load word document recovery** στρατηγική, τα κατεστραμμένα αρχεία Word δεν θα αποτελούν πια εμπόδιο.

Καλή προγραμματιστική δουλειά, και να είναι πάντα έτοιμα τα έγγραφά σας!  

---

![Ανάκτηση κατεστραμμένου docx χρησιμοποιώντας Aspose LoadOptions](https://example.com/images/recover-damaged-docx.png "παράδειγμα ανάκτησης κατεστραμμένου docx")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}