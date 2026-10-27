---
category: general
date: 2026-10-26
description: Μάθετε πώς να εισάγετε έλεγχο περιεχομένου απλού κειμένου χρησιμοποιώντας
  το Aspose.Words σε C#. Οδηγός βήμα‑βήμα που καλύπτει το StructuredDocumentTag, τους
  τίτλους και τα IDs ετικετών.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert plain text content control
- structured document tag
- Aspose.Words DocumentBuilder
- C# content control
- SDT appearance
language: el
lastmod: 2026-10-26
og_description: Εισαγάγετε έλεγχο περιεχομένου απλού κειμένου χρησιμοποιώντας το Aspose.Words
  σε C#. Ακολουθήστε αυτόν τον οδηγό για να προσθέσετε τίτλους, ID ετικετών και να
  προσαρμόσετε την εμφάνιση.
og_image_alt: Screenshot of a Word document showing an inserted plain text content
  control
og_title: Εισαγωγή ελέγχου περιεχομένου απλού κειμένου στο Word με C# – πλήρης οδηγός
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn to insert plain text content control using Aspose.Words in C#.
    Step‑by‑step guide covering StructuredDocumentTag, titles, and tag IDs.
  headline: How to insert plain text content control in a Word document with C#
  type: TechArticle
- description: Learn to insert plain text content control using Aspose.Words in C#.
    Step‑by‑step guide covering StructuredDocumentTag, titles, and tag IDs.
  name: How to insert plain text content control in a Word document with C#
  steps:
  - name: Initialize the document and builder
    text: '```csharp using System; using Aspose.Words; using Aspose.Words.Markup;'
  - name: Insert the plain‑text content control (SDT)
    text: '```csharp // Insert a plain‑text Structured Document Tag (SDT) with the
      default appearance. StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
      SdtType.PlainText, // The control type – plain text. SdtAppearance.Default);
      // Visual style; Default shows a light gray shading. ```'
  - name: Set a title and a tag identifier
    text: '```csharp // Give the SDT a friendly title that appears in the Content
      Controls pane. sdt.Title = "MyTag";'
  - name: Variations you might need
    text: '| Scenario | Code change | |----------|-------------| | **No visual shading**
      (border‑less) | Use `SdtAppearance.Hidden` instead of `Default`. | | **Read‑only
      field** | After insertion, set `sdt.LockContentControl = true`. | | **Pre‑populate
      with data** | Set `sdt.Text = "John Doe";` after creating '
  - name: What’s next?
    text: '- Explore other SDT types such as `RichText` or `ComboBox` for dropdowns.
      - Combine multiple content controls inside tables or repeat them using `RepeatingSection`.
      - Use `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` to read or modify
      control values programmatically.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Πώς να εισαγάγετε έλεγχο περιεχομένου απλού κειμένου σε έγγραφο Word με C#
url: /el/java/document-manipulation/how-to-insert-plain-text-content-control-in-a-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Εισαγωγή ελέγχου περιεχομένου απλού κειμένου σε έγγραφο Word με C#

Αν χρειάζεστε **να εισάγετε έλεγχο περιεχομένου απλού κειμένου** σε ένα αρχείο Word, αυτό το tutorial σας δείχνει ακριβώς πώς να το κάνετε χρησιμοποιώντας το Aspose.Words for .NET. Είτε δημιουργείτε μια υπηρεσία δημιουργίας εγγράφων είτε αυτοματοποιείτε τη δημιουργία φορμών, τα παρακάτω βήματα σας επιτρέπουν να προσθέσετε μια επαναχρησιμοποιήσιμη, επεξεργάσιμη περιοχή που οι τελικοί χρήστες μπορούν να συμπληρώσουν.

Θα μάθετε πώς να δημιουργήσετε ένα `Document`, να χρησιμοποιήσετε το `DocumentBuilder` για να τοποθετήσετε ένα Structured Document Tag (SDT) απλού κειμένου, να ορίσετε έναν φιλικό τίτλο και να εκχωρήσετε ένα μοναδικό αναγνωριστικό ετικέτας. Ο οδηγός εξηγεί επίσης κοινές παραλλαγές — όπως η αλλαγή της εμφάνισης ή η ένθεση ελέγχων — ώστε να προσαρμόσετε τη λύση σε οποιοδήποτε έργο.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

- .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.6+)
- Έγκυρη άδεια Aspose.Words for .NET (ή δωρεάν κλειδί αξιολόγησης)
- Visual Studio 2022 ή οποιοδήποτε IDE συμβατό με C#
- Βασική εξοικείωση με τη σύνταξη C#

> **Συμβουλή:** Αν χρησιμοποιείτε τη δωρεάν αξιολόγηση, θυμηθείτε ότι το παραγόμενο έγγραφο θα περιέχει υδατογράφημα. Μια έκδοση με άδεια το αφαιρεί αυτόματα.

## Πώς να εισάγετε έλεγχο περιεχομένου απλού κειμένου χρησιμοποιώντας το Aspose.Words

Ο πυρήνας της λύσης είναι μια διαδικασία τριών βημάτων:

1. **Δημιουργήστε ένα `Document` και ένα `DocumentBuilder`.**  
2. **Εισάγετε ένα Structured Document Tag (SDT) απλού κειμένου με προεπιλεγμένη εμφάνιση.**  
3. **Αναθέστε έναν τίτλο και ένα αναγνωριστικό ετικέτας στο SDT.**  

Κάθε βήμα εξηγείται παρακάτω, με πλήρη, εκτελέσιμο κώδικα.

### Βήμα 1: Αρχικοποίηση του εγγράφου και του builder

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Create a new empty document.
        Document doc = new Document();

        // DocumentBuilder lets you insert content into the document.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` αντιπροσωπεύει ολόκληρο το αρχείο Word, ενώ το `DocumentBuilder` παρέχει μεθόδους όπως `InsertParagraph`, `InsertImage` και, κρίσιμα για αυτό το tutorial, `InsertStructuredDocumentTag`. Η αρχικοποίησή τους πρώτα σας δίνει έναν καμβά στον οποίο μπορείτε να τοποθετήσετε τον **έλεγχο περιεχομένου απλού κειμένου**.

### Βήμα 2: Εισαγωγή του ελέγχου περιεχομένου απλού κειμένου (SDT)

```csharp
        // Insert a plain‑text Structured Document Tag (SDT) with the default appearance.
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            SdtType.PlainText,          // The control type – plain text.
            SdtAppearance.Default);    // Visual style; Default shows a light gray shading.
```

`SdtType.PlainText` λέει στο Aspose.Words να δημιουργήσει έναν **έλεγχο περιεχομένου απλού κειμένου**, που συμπεριφέρεται όπως ένα απλό πλαίσιο κειμένου που οι χρήστες μπορούν να επεξεργαστούν. Το `SdtAppearance.Default` αποδίδει τον έλεγχο με ένα διακριτικό φόντο, καθιστώντας σαφές στο έγγραφο ότι η περιοχή είναι επεξεργάσιμη.

> **Γιατί να χρησιμοποιήσετε το `SdtAppearance.Default`;**  
> Η προεπιλεγμένη εμφάνιση είναι το πιο καθολικά συμβατό στυλ σε όλες τις εκδόσεις του Word. Αν χρειάζεστε εμφάνιση χωρίς περίγραμμα, μπορείτε αργότερα να μεταβείτε στο `SdtAppearance.Hidden`.

### Βήμα 3: Ορισμός τίτλου και αναγνωριστικού ετικέτας

```csharp
        // Give the SDT a friendly title that appears in the Content Controls pane.
        sdt.Title = "MyTag";

        // Assign a unique tag identifier; this is useful for programmatic access later.
        sdt.Tag = "TagId";

        // (Optional) Add placeholder text inside the control.
        sdt.PlaceholderName = "Enter your text here";

        // Save the document to verify the result.
        doc.Save("output.docx");
    }
}
```

- **Τίτλος** (`sdt.Title`) εμφανίζεται στο πλαίσιο *Content Controls* του Word, βοηθώντας τους τελικούς χρήστες να καταλάβουν τον σκοπό του πεδίου.  
- **Ετικέτα** (`sdt.Tag`) είναι ένας αναγνωριστικός κωδικός προσανατολισμένος στον προγραμματιστή που μπορείτε να ερωτήσετε αργότερα μέσω `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`.  
- **PlaceholderName** παρέχει γκριζαρισμένο κείμενο καθοδήγησης, βελτιώνοντας την εμπειρία του χρήστη.

Το πλήρες απόσπασμα κώδικα παραπάνω σχηματίζει ένα αυτόνομο πρόγραμμα που μπορείτε να μεταγλωττίσετε και να εκτελέσετε. Μετά την εκτέλεση, το `output.docx` θα περιέχει έναν μοναδικό έλεγχο περιεχομένου απλού κειμένου με τον τίτλο *MyTag* και την ετικέτα *TagId*.

![Διάγραμμα που δείχνει την εισαγωγή ελέγχου περιεχομένου απλού κειμένου σε έγγραφο Word](image.png){alt="εισαγωγή ελέγχου περιεχομένου απλού κειμένου"}

## Κατανόηση του StructuredDocumentTag (SDT) και των ιδιοτήτων του

Ένα **Structured Document Tag** (SDT) είναι το υποκείμενο μοντέλο αντικειμένων για τους ελέγχους περιεχομένου του Word. Οι πιο σχετικές ιδιότητες για την εισαγωγή ελέγχου απλού κειμένου είναι:

| Ιδιότητα | Σκοπός | Τυπικές τιμές |
|----------|---------|----------------|
| `SdtType` | Καθορίζει τον τύπο του ελέγχου (απλό κείμενο, εμπλουτισμένο κείμενο, εικόνα κ.λπ.) | `PlainText`, `RichText`, `ComboBox`, `DatePicker` |
| `SdtAppearance` | Οπτικό στυλ του ελέγχου | `Default`, `Hidden`, `BoundingBox`, `Tags` |
| `Title` | Ανθρώπινα αναγνώσιμο όνομα που εμφανίζεται στο πλαίσιο *Content Controls* | Οποιοδήποτε σύντομο κείμενο |
| `Tag` | Αναγνωριστικό μηχανής που χρησιμοποιείται στον κώδικα | Αλφαριθμητικό κείμενο |
| `PlaceholderName` | Κείμενο που εμφανίζεται όταν ο έλεγχος είναι κενός | Προσαρμοσμένο κείμενο υπόδειξης |

Όταν ορίζετε `SdtType.PlainText`, το Word περιορίζει το περιεχόμενο σε απλούς χαρακτήρες, αποτρέποντας το εμπλουτισμένο μορφοποίηση. Αυτό κάνει τον έλεγχο ιδανικό για απλά πεδία φόρμας όπως *Όνομα*, *Email* ή *Αριθμός τηλεφώνου*.

### Παραλλαγές που μπορεί να χρειαστείτε

| Σενάριο | Αλλαγή κώδικα |
|----------|-------------|
| **Χωρίς οπτική σκίαση** (χωρίς περίγραμμα) | Χρησιμοποιήστε `SdtAppearance.Hidden` αντί για `Default`. |
| **Πεδίο μόνο για ανάγνωση** | Μετά την εισαγωγή, ορίστε `sdt.LockContentControl = true`. |
| **Προ-συμπλήρωση με δεδομένα** | Ορίστε `sdt.Text = "John Doe";` μετά τη δημιουργία της ετικέτας. |
| **Πολλαπλοί έλεγχοι σε πίνακα** | Εισάγετε το SDT μέσα σε κελί πίνακα χρησιμοποιώντας `builder.InsertCell();` πριν από την κλήση `InsertStructuredDocumentTag`. |

## Συνηθισμένα λάθη και πώς να τα αποφύγετε

1. **Ξεχάνοντας να ορίσετε τίτλο** – Το Word θα δημιουργήσει ακόμα τον έλεγχο, αλλά οι χρήστες δεν θα δουν περιγραφική ένδειξη στο πλαίσιο *Content Controls*. Πάντα να εκχωρείτε `sdt.Title`.  
2. **Χρήση λανθασμένου `SdtType`** – Αν χρειάζεστε απλό κείμενο αλλά επιλέξετε κατά λάθος `RichText`, ο έλεγχος θα επιτρέπει μορφοποίηση, κάτι που μπορεί να διακόψει την επεξεργασία downstream. Ελέγξτε ξανά την τιμή του enum.  
3. **Αποθήκευση σε φάκελο μόνο για ανάγνωση** – Η κλήση `doc.Save` θα ρίξει `UnauthorizedAccessException`. Βεβαιωθείτε ότι ο φάκελος προορισμού είναι εγγράψιμος ή χρησιμοποιήστε `Path.GetTempPath()` για δοκιμές.  
4. **Άδεια δεν εφαρμόστηκε** – Χωρίς έγκυρη άδεια, το παραγόμενο έγγραφο περιέχει υδατογράφημα αξιολόγησης. Εφαρμόστε την άδεια νωρίς στο πρόγραμμα:  

```csharp
License lic = new License();
lic.SetLicense("Aspose.Words.lic");
```

## Πλήρες, εκτελέσιμο παράδειγμα

Παρακάτω βρίσκεται ολόκληρο το πρόγραμμα, έτοιμο για αντιγραφή‑επικόλληση σε ένα νέο έργο κονσόλας.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace InsertPlainTextContentControl
{
    class Program
    {
        static void Main()
        {
            // Apply license (optional for evaluation)
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // 1️⃣ Create a new document and a builder to edit it
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a plain‑text Structured Document Tag (SDT) with default appearance
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText,          // Plain text control
                SdtAppearance.Default);    // Light gray shading

            // 3️⃣ Assign a title and a tag identifier to the SDT
            sdt.Title = "MyTag";          // Human‑readable title
            sdt.Tag = "TagId";            // Unique machine identifier
            sdt.PlaceholderName = "Enter your text here";

            // (Optional) Add some introductory text before the control
            builder.MoveToDocumentStart();
            builder.Writeln("Please fill in the following field:");

            // 4️⃣ Save the document
            string outputPath = "output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Αναμενόμενο αποτέλεσμα:** Το άνοιγμα του `output.docx` στο Microsoft Word εμφανίζει μια γραμμή κειμένου *«Παρακαλούμε συμπληρώστε το παρακάτω πεδίο:»* ακολουθούμενη από μια ανοιχτή περιοχή σε ανοιχτό γκρι χρώμα με ετικέτα *MyTag*. Το placeholder *Enter your text here* εμφανίζεται σε ανοιχτό γκρι μέχρι ο χρήστης πληκτρολογήσει.

## Συμπέρασμα

Τώρα ξέρετε πώς να **εισάγετε έλεγχο περιεχομένου απλού κειμένου** σε έγγραφο Word χρησιμοποιώντας το Aspose.Words for .NET. Το tutorial κάλυψε την αρχικοποίηση ενός `Document`, την εισαγωγή ενός `StructuredDocumentTag` τύπου `PlainText`, και την προσαρμογή του τίτλου, της ετικέτας και του placeholder. Κατανοώντας τις επιλογές `SdtAppearance` και τα συχνά λάθη, μπορείτε με σιγουριά να δημιουργήσετε φόρμες, πρότυπα και αυτοματοποιημένες αναφορές που βασίζονται σε επεξεργάσιμους ελέγχους περιεχομένου.

### Τι ακολουθεί;

- Εξερευνήστε άλλους τύπους SDT όπως `RichText` ή `ComboBox` για αναπτυσσόμενα μενού.  
- Συνδυάστε πολλαπλούς ελέγχους περιεχομένου μέσα σε πίνακες ή επαναλάβετε τους χρησιμοποιώντας `RepeatingSection`.  
- Χρησιμοποιήστε `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` για να διαβάσετε ή να τροποποιήσετε τις τιμές των ελέγχων προγραμματιστικά.

Μη διστάσετε να πειραματιστείτε με τις παραλλαγές που παρουσιάστηκαν παραπάνω και να ενσωματώσετε το μοτίβο στις μεγαλύτερες διαδικασίες δημιουργίας εγγράφων σας. Καλή προγραμματιστική!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να δημιουργήσετε έλεγχο περιεχομένου σε C# με Aspose.Words](/words/english/net/programming-with-sdt/how-to-create-content-control-in-c-with-aspose-words/)
- [Δημιουργία νέου εγγράφου Word και εισαγωγή ελέγχου περιεχομένου σε C#](/words/english/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/)
- [Προσθήκη περιεχομένου χρησιμοποιώντας Document Builder στο Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}