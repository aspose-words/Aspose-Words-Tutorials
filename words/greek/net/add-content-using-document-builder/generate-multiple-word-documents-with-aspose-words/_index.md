---
category: general
date: 2026-08-10
description: Δημιουργήστε πολλαπλά έγγραφα Word με το Aspose.Words σε C#. Μάθετε πώς
  να δημιουργείτε τιμολόγια από πρότυπο και να παράγετε μαζικά αρχεία Word αποδοτικά.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- generate multiple word documents
- create invoices from template
- batch generate word files
- Aspose.Words mail merge
- C# document automation
language: el
lastmod: 2026-08-10
og_description: Δημιουργήστε πολλαπλά έγγραφα Word με το Aspose.Words. Αυτό το σεμινάριο
  δείχνει πώς να δημιουργήσετε τιμολόγια από πρότυπο και να δημιουργήσετε μαζικά αρχεία
  Word σε C#.
og_image_alt: Screenshot of generate multiple word documents result
og_title: Δημιουργία πολλαπλών εγγράφων Word – Οδηγός βήμα‑βήμα για το Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Generate multiple word documents with Aspose.Words in C#. Learn how
    to create invoices from template and batch generate word files efficiently.
  headline: Generate multiple word documents with Aspose.Words
  type: TechArticle
- description: Generate multiple word documents with Aspose.Words in C#. Learn how
    to create invoices from template and batch generate word files efficiently.
  name: Generate multiple word documents with Aspose.Words
  steps:
  - name: Prepare the data that will populate the merge fields
    text: The mail‑merge engine expects a collection of objects whose property names
      match the `MERGEFIELD` names in the template. In this example we use an anonymous
      type array, but you can replace it with a list of strongly‑typed DTOs.
  - name: Load the Word template that contains MERGEFIELD placeholders
    text: '```csharp // Step 2 – load template Document template = new Document("YOUR_DIRECTORY/InvoiceTemplate.docx");
      ```'
  - name: Merge the data into the template – one‑line call creates a single document
    text: '```csharp // Step 3 – perform the merge Document mergedDocument = MailMerger.Merge(template,
      invoiceData); ```'
  - name: Split the merged document into separate files and save each one
    text: '```csharp // Step 4 – split and save each invoice int invoiceNumber = 1;
      foreach (Document singleInvoice in mergedDocument.Split()) { string outputPath
      = $"YOUR_DIRECTORY/Invoice_{invoiceNumber++}.docx"; singleInvoice.Save(outputPath);
      } ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- MailMerge
- Document Automation
title: Δημιουργία πολλαπλών εγγράφων Word με το Aspose.Words
url: /el/net/add-content-using-document-builder/generate-multiple-word-documents-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία πολλαπλών εγγράφων Word με Aspose.Words

Αν χρειάζεστε **να δημιουργήσετε πολλαπλά έγγραφα Word** σε C#, το Aspose.Words παρέχει μια συνοπτική API που αφαιρεί το boilerplate της διαχείρισης αρχείων. Είτε χτίζετε ένα σύστημα τιμολόγησης είτε χρειάζεστε να παραγάγετε ένα σύνολο εξατομικευμένων επιστολών, αυτός ο οδηγός σας δείχνει πώς να **δημιουργήσετε τιμολόγια από πρότυπο** και **να δημιουργήσετε μαζικά αρχεία Word** με μερικές μόνο γραμμές κώδικα.

Θα μάθετε πώς να:

* Προετοιμάσετε δεδομένα για μια λειτουργία mail‑merge.  
* Φορτώσετε ένα πρότυπο Word που περιέχει placeholders `MERGEFIELD`.  
* Συγχωνεύσετε τα δεδομένα σε ένα ενιαίο έγγραφο και το χωρίσετε σε ξεχωριστά αρχεία.  
* Αποθηκεύσετε κάθε παραγόμενο αρχείο με μοναδικό όνομα.

Δεν απαιτείται εξωτερικό εργαλείο πέραν της βιβλιοθήκης Aspose.Words for .NET, και το πλήρες παράδειγμα κώδικα εκτελείται σε .NET 6 ή νεότερο.

## Προαπαιτούμενα και ρύθμιση

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

| Απαίτηση | Αιτία |
|-------------|--------|
| .NET 6 SDK (or newer) | Ο κώδικας χρησιμοποιεί σύγχρονα χαρακτηριστικά C# όπως το target‑typed `new`. |
| Aspose.Words for .NET NuGet package | Παρέχει τις API `Document`, `MailMerger` και `Split`. |
| A Word template (`InvoiceTemplate.docx`) containing `MERGEFIELD` tags | Λειτουργεί ως πηγή για **δημιουργία τιμολογίων από πρότυπο**. |
| An IDE (Visual Studio, Rider, or VS Code) | Για τη δημιουργία και αποσφαλμάτωση του έργου. |

Εγκαταστήστε το πακέτο NuGet με την παρακάτω εντολή:

```bash
dotnet add package Aspose.Words
```

Τοποθετήστε το `InvoiceTemplate.docx` σε έναν φάκελο που μπορείτε να αναφέρετε από τον κώδικα, για παράδειγμα `YOUR_DIRECTORY`.

## Πώς να δημιουργήσετε πολλαπλά έγγραφα Word με mail merge

Ο πυρήνας της λύσης αποτελείται από τέσσερα λογικά βήματα. Κάθε βήμα είναι ενσωματωμένο σε μια σαφή κλήση μεθόδου, κάτι που κάνει τον κώδικα εύκολο στην ανάγνωση και συντήρηση.

### Βήμα 1: Προετοιμάστε τα δεδομένα που θα γεμίσουν τα πεδία συγχώνευσης

Η μηχανή mail‑merge αναμένει μια συλλογή αντικειμένων των οποίων τα ονόματα ιδιοτήτων ταιριάζουν με τα ονόματα `MERGEFIELD` στο πρότυπο. Σε αυτό το παράδειγμα χρησιμοποιούμε έναν πίνακα ανώνυμων τύπων, αλλά μπορείτε να τον αντικαταστήσετε με μια λίστα από ισχυρά τυποποιημένα DTOs.

```csharp
// Step 1 – data preparation
var invoiceData = new[]
{
    new { Name = "Alice", Amount = 123.45 },
    new { Name = "Bob",   Amount = 678.90 }
};
```

**Γιατί είναι σημαντικό:**  
Η παροχή μιας ισχυρά τυποποιημένης πηγής δεδομένων εγγυάται ότι κάθε placeholder λαμβάνει τη σωστή τιμή, κάτι που είναι ουσιώδες όταν **δημιουργείτε μαζικά αρχεία Word** για πολλούς παραλήπτες.

### Βήμα 2: Φορτώστε το πρότυπο Word που περιέχει placeholders MERGEFIELD

```csharp
// Step 2 – load template
Document template = new Document("YOUR_DIRECTORY/InvoiceTemplate.docx");
```

**Γιατί είναι σημαντικό:**  
Η κλάση `Document` αντιπροσωπεύει ολόκληρο το αρχείο Word στη μνήμη. Φορτώνοντας το πρότυπο μία φορά (όπως φαίνεται στο Βήμα 2) αποτρέπει επαναλαμβανόμενες αναγνώσεις δίσκου όταν αργότερα **δημιουργείτε πολλαπλά έγγραφα Word**.

### Βήμα 3: Συγχωνεύστε τα δεδομένα στο πρότυπο – κλήση μιας γραμμής δημιουργεί ένα ενιαίο έγγραφο

```csharp
// Step 3 – perform the merge
Document mergedDocument = MailMerger.Merge(template, invoiceData);
```

`MailMerger.Merge` διατρέχει τη συλλογή δεδομένων, εισάγοντας ένα αντίγραφο του προτύπου για κάθε γραμμή και γεμίζοντας τις τιμές `MERGEFIELD`. Το αποτέλεσμα είναι ένα ενιαίο `Document` που περιέχει όλα τα τιμολόγια το ένα μετά το άλλο.

### Βήμα 4: Χωρίστε το συγχωνευμένο έγγραφο σε ξεχωριστά αρχεία και αποθηκεύστε το καθένα

```csharp
// Step 4 – split and save each invoice
int invoiceNumber = 1;
foreach (Document singleInvoice in mergedDocument.Split())
{
    string outputPath = $"YOUR_DIRECTORY/Invoice_{invoiceNumber++}.docx";
    singleInvoice.Save(outputPath);
}
```

Η επέκταση `Split()` διασχίζει το συγχωνευμένο έγγραφο και επιστρέφει ένα νέο αντικείμενο `Document` για κάθε γραμμή δεδομένων. Η αποθήκευση κάθε `singleInvoice` παράγει ένα ξεχωριστό αρχείο, ολοκληρώνοντας τη ροή εργασίας **δημιουργίας μαζικών αρχείων Word**.

#### Πλήρες εκτελέσιμο παράδειγμα

Ακολουθεί το πλήρες πρόγραμμα που ενώνει τα τέσσερα βήματα. Αντιγράψτε το σε ένα νέο έργο console και τρέξτε το αφού προσαρμόσετε τις διαδρομές.

```csharp
using Aspose.Words;
using Aspose.Words.LowCode;

class Program
{
    static void Main()
    {
        // Step 1 – prepare data
        var invoiceData = new[]
        {
            new { Name = "Alice", Amount = 123.45 },
            new { Name = "Bob",   Amount = 678.90 }
        };

        // Step 2 – load the template
        Document template = new Document("YOUR_DIRECTORY/InvoiceTemplate.docx");

        // Step 3 – merge data into a single document
        Document mergedDocument = MailMerger.Merge(template, invoiceData);

        // Step 4 – split and save each invoice
        int invoiceNumber = 1;
        foreach (Document singleInvoice in mergedDocument.Split())
        {
            string outputPath = $"YOUR_DIRECTORY/Invoice_{invoiceNumber++}.docx";
            singleInvoice.Save(outputPath);
        }

        System.Console.WriteLine("Invoices generated successfully.");
    }
}
```

**Αναμενόμενο αποτέλεσμα:**  
Η εκτέλεση του προγράμματος δημιουργεί τα `Invoice_1.docx`, `Invoice_2.docx`, … στον καθορισμένο φάκελο. Κάθε αρχείο περιέχει τα δεδομένα τιμολογίου για έναν πελάτη, με τα πεδία συγχώνευσης να έχουν αντικατασταθεί από τις τιμές του `invoiceData`.

## Δημιουργία τιμολογίων από πρότυπο – αντιμετώπιση κοινών παγίδων

Όταν **δημιουργείτε τιμολόγια από πρότυπο**, μπορεί να αντιμετωπίσετε μερικά προβλήματα. Παρακάτω υπάρχουν πρακτικές συμβουλές για να τα αποφύγετε.

| Πρόβλημα | Λύση |
|-------|----------|
| Τα ονόματα πεδίων του προτύπου δεν ταιριάζουν με τα ονόματα ιδιοτήτων | Βεβαιωθείτε ότι τα ονόματα ιδιοτήτων (`Name`, `Amount`) ταιριάζουν ακριβώς με τις ετικέτες `MERGEFIELD` στο αρχείο Word. |
| Μεγάλα σύνολα δεδομένων προκαλούν υψηλή χρήση μνήμης | Επεξεργαστείτε τα δεδομένα σε τμήματα: συγχωνεύστε ένα υποσύνολο, χωρίστε, αποθηκεύστε, και στη συνέχεια απορρίψτε το ενδιάμεσο έγγραφο πριν το επόμενο batch. |
| Ειδικοί χαρακτήρες (π.χ., “&”, “<”) εμφανίζονται παραμορφωμένοι | Το Aspose.Words αυτόματα διαφύγει χαρακτήρες που δεν είναι ασφαλείς για XML, αλλά ελέγξτε την κωδικοποίηση του προτύπου αν το φορτώνετε από πηγή που δεν είναι UTF‑8. |
| Απαιτούνται προσαρμοσμένα ονόματα αρχείων (π.χ., να περιλαμβάνεται το όνομα πελάτη) | Αντικαταστήστε τη συμβολοσειρά `outputPath` με `$"YOUR_DIRECTORY/Invoice_{singleInvoice.MailMergeData[\"Name\"]}.docx"` αφού εξάγετε την τιμή του πεδίου από το χωρισμένο έγγραφο. |

## Μαζική δημιουργία αρχείων Word – ζητήματα απόδοσης

Αν σκοπεύετε να **δημιουργήσετε μαζικά αρχεία Word** για χιλιάδες εγγραφές, κρατήστε αυτές τις οδηγίες στο μυαλό:

1. **Επαναχρησιμοποίηση του αντικειμένου προτύπου** – η φόρτωση του προτύπου μία φορά (όπως φαίνεται στο Βήμα 2) αποτρέπει επαναλαμβανόμενες αναγνώσεις δίσκου.  
2. **Απόρριψη ενδιάμεσων εγγράφων** – ο βρόχος `foreach` απελευθερώνει αυτόματα τη μνήμη μετά από κάθε `singleInvoice.Save`, αλλά μπορείτε να καλέσετε ρητά `singleInvoice.Dispose()` για πολύ μεγάλα batch.  
3. **Παραλληλοποίηση του βήματος αποθήκευσης** – η λειτουργία split παράγει ανεξάρτητα αντικείμενα `Document`, έτσι μπορείτε να χρησιμοποιήσετε `Parallel.ForEach` για να γράψετε τα αρχεία ταυτόχρονα, εφόσον το μέσο αποθήκευσης μπορεί να διαχειριστεί παράλληλο I/O.

```csharp
using System.Threading.Tasks;

// ...

Parallel.ForEach(mergedDocument.Split(), (singleInvoice, state, index) =>
{
    string outputPath = $"YOUR_DIRECTORY/Invoice_{index + 1}.docx";
    singleInvoice.Save(outputPath);
});
```

**Γιατί λειτουργεί:**  
Η `Split()` επιστρέφει ένα `IEnumerable<Document>` που μπορεί να διαβαστεί με ασφάλεια παράλληλα επειδή κάθε αντικείμενο `Document` κατέχει τη δική του μνήμη.

## Αναμενόμενα αποτελέσματα και επαλήθευση

Αφού ολοκληρωθεί το πρόγραμμα, ανοίξτε οποιοδήποτε παραγόμενο τιμολόγιο στο Microsoft Word:

* Το placeholder `«Name»` αντικαθίσταται με “Alice” ή “Bob”.  
* Το placeholder `«Amount»` εμφανίζει την αντίστοιχη αριθμητική τιμή μορφοποιημένη με το προεπιλεγμένο μορφότυπο αριθμού του εγγράφου.  
* Η διάταξη σελίδας, οι κεφαλίδες και τα υποσέλιδα από το αρχικό πρότυπο διατηρούνται.

Αν κάποιο πεδίο παραμείνει μη συμπληρωμένο, ελέγξτε ξανά τα ονόματα `MERGEFIELD` στο πρότυπο σε σχέση με τα ονόματα ιδιοτήτων στο `invoiceData`.

## Συμπέρασμα

Τώρα γνωρίζετε πώς να **δημιουργήσετε πολλαπλά έγγραφα Word** χρησιμοποιώντας το Aspose.Words, πώς να **δημιουργήσετε τιμολόγια από πρότυπο**, και πώς να **δημιουργήσετε μαζικά αρχεία Word** αποδοτικά. Το μοτίβο τεσσάρων βημάτων — προετοιμασία δεδομένων, φόρτωση προτύπου, συγχώνευση, διαχωρισμός & αποθήκευση — καλύπτει τις πιο κοινές περιπτώσεις αυτοματοποίησης εγγράφων.  

Από εδώ μπορείτε να επεκτείνετε τη λύση προσθέτοντας εικόνες, πίνακες ή λογική υπό συνθήκη στο πρότυπο, ή ενσωματώνοντας τη ροή εργασίας σε ένα web API που εξυπηρετεί τιμολόγια κατ' απαίτηση.

---

![Generate multiple word documents screenshot](generate-multiple-word-documents.png){: .align-center alt="Στιγμιότυπο οθόνης του αποτελέσματος δημιουργίας πολλαπλών εγγράφων Word"}

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κατακτήσετε πρόσθετα χαρακτηριστικά API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Προσθήκη και Προσάρτηση Περιεχομένου σε Έγγραφα Word χρησιμοποιώντας Aspose.Words](/words/english/net/document-sections/append-section-content/)
- [Συνδυασμός Πολλαπλών Αρχείων Word με Aspose.Words για Java](/words/english/java/document-manipulation/cloning-and-combining-documents/)
- [Εφαρμογή Μορφοποίησης Γραμμής σε Έγγραφα Word με Aspose.Words για .NET](/words/english/net/working-with-table-styles-and-formatting/apply-row-formatting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}