---
category: general
date: 2026-10-13
description: Δημιουργήστε νέο έγγραφο Word σε C# και εισάγετε έναν έλεγχο περιεχομένου
  με κείμενο κράτησης θέσης. Μάθετε πώς να ορίσετε κείμενο κράτησης θέσης και να αποθηκεύσετε
  το έγγραφο Word αποδοτικά.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create new word document
- insert content control
- set placeholder text
- how to create sdt
- save word document c#
language: el
lastmod: 2026-10-13
og_description: Δημιουργήστε νέο έγγραφο Word σε C# με το Aspose.Words, εισάγετε έναν
  έλεγχο περιεχομένου, ορίστε κείμενο κράτησης θέσης και αποθηκεύστε το έγγραφο Word—όλα
  σε έναν ενιαίο οδηγό.
og_image_alt: Screenshot of a Word document showing a content control placeholder
og_title: Δημιουργήστε νέο έγγραφο Word και εισάγετε έλεγχο περιεχομένου σε C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Create new Word document in C# and insert a content control with placeholder
    text. Learn how to set placeholder text and save the Word document efficiently.
  headline: Create new Word document and insert content control in C#
  type: TechArticle
- description: Create new Word document in C# and insert a content control with placeholder
    text. Learn how to set placeholder text and save the Word document efficiently.
  name: Create new Word document and insert content control in C#
  steps:
  - name: Run the console app.
    text: Run the console app.
  - name: Open `output.docx` in Microsoft Word.
    text: Open `output.docx` in Microsoft Word.
  - name: Verify that the placeholder text appears inside a gray‑shaded box.
    text: Verify that the placeholder text appears inside a gray‑shaded box.
  - name: Click the box, type a name, and save the file. The entered text replaces
      the placeholder.
    text: Click the box, type a name, and save the file. The entered text replaces
      the placeholder.
  type: HowTo
tags:
- Aspose.Words
- C#
- Content Control
- Word Automation
title: Δημιουργήστε νέο έγγραφο Word και εισάγετε έλεγχο περιεχομένου σε C#
url: /el/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία νέου εγγράφου Word και εισαγωγή ελέγχου περιεχομένου σε C#

Αν χρειάζεστε να **δημιουργήσετε νέο έγγραφο Word** προγραμματιστικά, αυτός ο οδηγός σας δείχνει πώς να το κάνετε με το Aspose.Words for .NET. Θα μάθετε να **εισάγετε έλεγχο περιεχομένου**, να ορίσετε **κείμενο placeholder**, και τελικά **αποθηκεύσετε έγγραφο Word C#** κώδικα που μπορείτε να αντιγράψετε στο έργο σας.

Ο οδηγός περνάει βήμα‑βήμα, εξηγεί γιατί κάθε κλήση API είναι σημαντική και καλύπτει κοινές παραλλαγές όπως η προσθήκη SDT πλούσιου κειμένου ή η διαχείριση υπαρχόντων εγγράφων. Στο τέλος θα έχετε ένα πλήρες, εκτελέσιμο παράδειγμα που μπορείτε να προσαρμόσετε σε τιμολόγια, συμβόλαια ή οποιαδήποτε προτυποποιημένη έξοδο Word.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.7+)
* Πακέτο NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)
* Ένα IDE όπως το Visual Studio 2022 ή το Visual Studio Code

Δεν απαιτούνται πρόσθετες βιβλιοθήκες.

## Δημιουργία νέου εγγράφου Word με Aspose.Words

Το πρώτο βήμα είναι η δημιουργία ενός αντικειμένου `Document`. Αυτό το αντικείμενο αντιπροσωπεύει ένα κενό αρχείο Word στη μνήμη.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

// Step 1: Create a new, empty document
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` σας παρέχει μια fluent API για την εισαγωγή στοιχείων στη τρέχουσα θέση του δρομέα. Επειδή το έγγραφο είναι κενό, ο δρομέας ξεκινά στην αρχή της πρώτης (και μοναδικής) ενότητας.

## Εισαγωγή ελέγχου περιεχομένου (StructuredDocumentTag)

Ένας **έλεγχος περιεχομένου** στο Word ονομάζεται Structured Document Tag (SDT). Ο παρακάτω κώδικας δημιουργεί ένα SDT απλού κειμένου, ορίζει τον τίτλο του και καθορίζει κείμενο placeholder που εμφανίζεται όταν ο χρήστης ανοίξει το αρχείο.

```csharp
// Step 2: Create a plain‑text StructuredDocumentTag (SDT)
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PlainText, true)
{
    // Title is used for identification in the document outline
    Title = "CustomerName",
    // Placeholder text is visible until the user types a value
    PlaceholderName = "Enter name here"
};

// Step 3: Insert the SDT at the builder's current insertion point
builder.InsertNode(sdt);
```

**Γιατί είναι σημαντικό:**  
* `SdtType.PlainText` περιορίζει το περιεχόμενο σε μία γραμμή απλού κειμένου, ιδανικό για απλά πεδία όπως όνομα ή email.  
* Ορίζοντας `PlaceholderName` παρέχει οπτική υπόδειξη (`Enter name here`) που καθοδηγεί τον τελικό χρήστη.  

Αν χρειάζεστε πιο πλούσιο πεδίο (π.χ. κείμενο πολλαπλών γραμμών ή επιλογέα ημερομηνίας), αντικαταστήστε το `SdtType.PlainText` με `SdtType.RichText` ή `SdtType.Date`.

## Προσθήκη προαιρετικού κειμένου γύρω

Τα περισσότερα πρότυπα περιλαμβάνουν μια ετικέτα πριν από τον έλεγχο περιεχομένου. Μπορείτε να την προσθέσετε με το ίδιο αντικείμενο `DocumentBuilder`:

```csharp
// Optional: add a label before the content control
builder.Writeln("Customer Name:");
builder.InsertNode(sdt);   // Re‑insert the SDT after the label
```

Το παραγόμενο αρχείο Word εμφανίζει:

```
Customer Name: [Enter name here]
```

## Αποθήκευση εγγράφου Word σε στυλ C#

Τέλος, γράψτε το έγγραφο στο δίσκο. Το Aspose.Words καθορίζει αυτόματα τη μορφή από την επέκταση του αρχείου.

```csharp
// Step 4: Save the document to verify the result
string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Όταν ανοίξετε το `output.docx` στο Microsoft Word, θα δείτε το κείμενο placeholder μέσα σε έναν γκρι‑χρωματιστό έλεγχο περιεχομένου. Οι χρήστες μπορούν να κάνουν κλικ στον έλεγχο και να αντικαταστήσουν το placeholder με τη δική τους τιμή.

## Πλήρες, εκτελέσιμο παράδειγμα

Παρακάτω υπάρχει ένα αυτόνομο πρόγραμμα κονσόλας που συνδυάζει όλα τα παραπάνω. Αντιγράψτε τον κώδικα σε ένα νέο πρότζεκτ κονσόλας και τρέξτε το.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordSdtDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Add a descriptive label
            builder.Writeln("Customer Name:");

            // Create and configure a plain‑text content control (SDT)
            StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PlainText, true)
            {
                Title = "CustomerName",
                PlaceholderName = "Enter name here"
            };

            // Insert the SDT after the label
            builder.InsertNode(sdt);

            // Save the document
            string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Αναμενόμενη έξοδος** (κονσόλα):

```
Document saved to C:\YourProject\bin\Debug\net6.0\output.docx
```

Ανοίγοντας το `output.docx` εμφανίζεται μια μοναδική γραμμή με την ετικέτα *Customer Name:* ακολουθούμενη από έναν έλεγχο περιεχομένου που εμφανίζει *Enter name here*.

## Κοινές παραλλαγές και ειδικές περιπτώσεις

| Σενάριο | Αλλαγή κώδικα | Αιτία |
|----------|-------------|--------|
| **Πεδίο πλούσιου κειμένου** | `new StructuredDocumentTag(doc, SdtType.RichText, true)` | Επιτρέπει εισαγωγή πολλαπλών γραμμών και βασική μορφοποίηση. |
| **Έλεγχος μόνο για ανάγνωση** | `sdt.LockContentControl = true;` | Αποτρέπει τους χρήστες από την επεξεργασία του περιεχομένου του ελέγχου. |
| **Προσυμπλήρωση με δεδομένα** | `sdt.AppendChild(new Run(doc, "John Doe"));` | Εισάγει μια προεπιλεγμένη τιμή που αντικαθιστά το placeholder. |
| **Προσθήκη σε υπάρχον έγγραφο** | Load with `new Document("template.docx")` instead of an empty `Document` | Ενεργοποιεί σενάρια προτύπων όπου ο έλεγχος τοποθετείται σε προκαθορισμένη διάταξη. |
| **Πολλαπλοί έλεγχοι** | Repeat the creation block with different titles and placeholders | Χρήσιμο για φόρμες που συλλέγουν πολλές πληροφορίες. |

### Συμβουλή επαγγελματία

Κατά τη δημιουργία μεγάλων εγγράφων, επαναχρησιμοποιήστε ένα μόνο αντικείμενο `DocumentBuilder` αντί να δημιουργείτε νέο για κάθε έλεγχο. Αυτό μειώνει το φορτίο μνήμης και βελτιώνει την απόδοση.

## Δοκιμή του αποτελέσματος

1. Εκτελέστε την εφαρμογή κονσόλας.  
2. Ανοίξτε το `output.docx` στο Microsoft Word.  
3. Επαληθεύστε ότι το κείμενο placeholder εμφανίζεται μέσα σε ένα γκρι‑χρωματιστό πλαίσιο.  
4. Κάντε κλικ στο πλαίσιο, πληκτρολογήστε ένα όνομα και αποθηκεύστε το αρχείο. Το εισαχθέν κείμενο αντικαθιστά το placeholder.

Αν το placeholder δεν εμφανιστεί, βεβαιωθείτε ότι χρησιμοποιείτε την έκδοση 23.9 ή νεότερη του Aspose.Words, καθώς παλαιότερες εκδόσεις είχαν σφάλμα με το `PlaceholderName` σε SDT απλού κειμένου.

## Συμπέρασμα

Τώρα ξέρετε πώς να **δημιουργήσετε νέο έγγραφο Word**, **εισάγετε έλεγχο περιεχομένου**, **ορίσετε κείμενο placeholder** και **αποθηκεύσετε έγγραφο Word C#** χρησιμοποιώντας το Aspose.Words. Το πλήρες παράδειγμα δείχνει το τυπικό μοτίβο, ενώ ο πίνακας παραλλαγών δείχνει πώς να προσαρμόσετε τη λύση για πιο πλούσιες περιπτώσεις.

Στη συνέχεια, μπορείτε να εξερευνήσετε:

* **Εισαγωγή ελέγχου περιεχομένου για ημερομηνίες** – χρησιμοποιήστε την απαρίθμηση `SdtType.Date`.  
* **Συμπλήρωση προτύπου με δεδομένα** – συνδυάστε `StructuredDocumentTag` με πεδία συγχώνευσης αλληλογραφίας.  
* **Εξαγωγή σε PDF** – καλέστε `doc.Save("output.pdf")` μετά την προσθήκη των ελέγχων.

Νιώστε ελεύθεροι να πειραματιστείτε με διαφορετικούς τύπους SDT, ρυθμίσεις κλειδώματος και στυλ για να ταιριάζουν στις απαιτήσεις του έργου σας. Καλή προγραμματιστική!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετα χαρακτηριστικά API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας πρότζεκτ.

- [Δημιουργία νέου εγγράφου Word](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Εισαγωγή πεδίου κειμένου φόρμας σε έγγραφο Word](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)
- [Δημιουργία εγγράφου Word με Aspose.Words για .NET](/words/english/net/add-content-using-documentbuilder/insert-paragraph/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}