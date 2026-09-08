---
category: general
date: 2026-09-08
description: Μάθετε πώς να εισάγετε έλεγχο περιεχομένου σε ένα έγγραφο Word χρησιμοποιώντας
  C# και Aspose.Words. Περιλαμβάνει βήματα για τη δημιουργία ελέγχου περιεχομένου,
  τον ορισμό του placeholder και την αποθήκευση του αρχείου.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert content control
- create content control
language: el
lastmod: 2026-09-08
og_description: Εισάγετε έλεγχο περιεχομένου σε αρχείο Word χρησιμοποιώντας C# και
  Aspose.Words. Ακολουθήστε αυτόν τον οδηγό για να δημιουργήσετε έλεγχο περιεχομένου,
  να ορίσετε κείμενο κράτησης θέσης και να αποθηκεύσετε το έγγραφο.
og_image_alt: Insert content control example in a Word document
og_title: Εισαγωγή ελέγχου περιεχομένου στο Word με C# – βήμα‑βήμα οδηγός
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to insert content control in a Word document using C# and
    Aspose.Words. Includes steps to create content control, set placeholder, and save
    the file.
  headline: How to insert content control in a Word document with C#
  type: TechArticle
tags:
- content control
- Aspose.Words
- C#
- Word automation
title: Πώς να εισάγετε έλεγχο περιεχομένου σε ένα έγγραφο Word με C#
url: /el/net/programming-with-sdt/how-to-insert-content-control-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να εισάγετε έλεγχο περιεχομένου σε ένα έγγραφο Word με C#

Αν χρειάζεστε **να εισάγετε έλεγχο περιεχομένου** σε ένα έγγραφο Word, αυτός ο οδηγός σας δείχνει μια πλήρη, εκτελέσιμη λύση. Θα μάθετε επίσης πώς να **δημιουργήσετε έλεγχο περιεχομένου** προγραμματιστικά, να ορίσετε κείμενο placeholder και να γράψετε το αρχείο στο δίσκο.

Οι έλεγχοι περιεχομένου σας επιτρέπουν να ορίσετε περιοχές που οι χρήστες μπορούν να συμπληρώσουν, να επαναλάβουν ή να κλειδώσουν. Χρησιμοποιούνται ευρέως για πρότυπα, φόρμες και δυναμικές αναφορές. Τα παρακάτω βήματα χρησιμοποιούν τη βιβλιοθήκη Aspose.Words for .NET, η οποία λειτουργεί με .NET 6+, .NET Framework 4.6+ και .NET Core.

## Πώς να εισάγετε έλεγχο περιεχομένου σε ένα έγγραφο Word

1. **Προσθέστε το Aspose.Words στο έργο σας**  
   Ανοίξτε ένα τερματικό στο φάκελο του έργου και εκτελέστε:

   ```bash
   dotnet add package Aspose.Words
   ```

   Το πακέτο περιέχει τις κλάσεις `Document`, `DocumentBuilder` και `StructuredDocumentTag` που απαιτούνται για ελέγχους περιεχομένου.

2. **Δημιουργήστε ένα νέο κενό έγγραφο**  

   ```csharp
   // Step 1: Create a new empty document and a DocumentBuilder
   Document doc = new Document();
   DocumentBuilder builder = new DocumentBuilder(doc);
   ```

   Το αντικείμενο `Document` αντιπροσωπεύει ολόκληρο το αρχείο .docx, ενώ το `DocumentBuilder` παρέχει έναν βολικό κέρσορα για την εισαγωγή κόμβων.

## Δημιουργία ελέγχου περιεχομένου με το Aspose.Words

Οι έλεγχοι περιεχομένου αντιπροσωπεύονται από την κλάση `StructuredDocumentTag` (SDT). Ο παρακάτω κώδικας δημιουργεί έναν έλεγχο περιεχομένου **απλού κειμένου** και του δίνει έναν τίτλο που μπορείτε να ερωτήσετε αργότερα.

```csharp
// Step 2: Create a plain‑text StructuredDocumentTag (content control)
//         - Set a title that can be used to identify the control
//         - Provide placeholder text that appears when the control is empty
StructuredDocumentTag sdt = new StructuredDocumentTag(
    doc,
    SdtType.PlainText,      // Plain‑text control
    MarkupLevel.Block);    // Block‑level control (behaves like a paragraph)

sdt.Title = "CustomerName";
sdt.PlaceholderName = "Enter name here";
```

*Γιατί αυτό είναι σημαντικό:*  
- `SdtType.PlainText` εξασφαλίζει ότι ο έλεγχος δέχεται μόνο απλούς χαρακτήρες.  
- `MarkupLevel.Block` κάνει τον έλεγχο να συμπεριφέρεται σαν μια πλήρης παράγραφος, κάτι που είναι ιδανικό για πεδία φόρμας.  
- Η ιδιότητα `Title` είναι ένας σταθερός αναγνωριστικός που μπορείτε να χρησιμοποιήσετε κατά την αναζήτηση ή τη σύνδεση δεδομένων.

## Ορισμός placeholder και προεπιλεγμένου κειμένου

Ένα placeholder καθοδηγεί τον χρήστη πριν πληκτρολογήσει οτιδήποτε. Μπορείτε επίσης να προ‑συμπληρώσετε τον έλεγχο με προεπιλεγμένο περιεχόμενο.

```csharp
// Step 4: Optionally set default content for the control
sdt.XmlMapping.SetXmlFragment("<text>John Doe</text>");
```

Το τμήμα XML πρέπει να ταιριάζει με τον τύπο δεδομένων του ελέγχου. Για ελέγχους απλού κειμένου, απαιτείται το στοιχείο `<text>`. Εάν παραλείψετε αυτό το βήμα, θα εμφανιστεί το placeholder που ορίστηκε νωρίτερα.

## Εισαγωγή του ελέγχου περιεχομένου στην επιθυμητή θέση

Ο κέρσορας `DocumentBuilder` καθορίζει πού εμφανίζεται ο έλεγχος. Από προεπιλογή, ο κέρσορας βρίσκεται στην αρχή του εγγράφου.

```csharp
// Step 3: Insert the StructuredDocumentTag into the document at the builder's current position
builder.InsertNode(sdt);
```

Αν χρειάζεστε τον έλεγχο μέσα σε πίνακα, κεφαλίδα ή μετά από υπάρχουσες παραγράφους, μετακινήστε πρώτα τον builder:

```csharp
builder.MoveToDocumentEnd();   // Example: place the control at the end of the file
builder.InsertNode(sdt);
```

## Αποθήκευση του εγγράφου με τον εισαχθέντα έλεγχο περιεχομένου

```csharp
// Step 5: Save the document with the content control
doc.Save(@"C:\Temp\SDT.docx");
```

Το αρχείο `SDT.docx` τώρα περιέχει έναν έλεγχο περιεχομένου απλού κειμένου με τίτλο **CustomerName** και το placeholder “Enter name here” και το προεπιλεγμένο κείμενο “John Doe”.

![Παράδειγμα εισαγωγής ελέγχου περιεχομένου σε έγγραφο Word](insert-content-control.png)

*Κείμενο εναλλακτικής εικόνας:* Παράδειγμα εισαγωγής ελέγχου περιεχομένου σε έγγραφο Word

### Αναμενόμενο αποτέλεσμα

Όταν ανοίξετε το `SDT.docx` στο Microsoft Word:

- Ένα γκρι placeholder “Enter name here” εμφανίζεται αν διαγράψετε το προεπιλεγμένο κείμενο.  
- Ο έλεγχος επισημαίνεται όταν κάνετε κλικ μέσα του, υποδεικνύοντας ότι μπορεί να επεξεργαστεί.  
- Η καρτέλα **Developer** (αν είναι ενεργοποιημένη) εμφανίζει τον τίτλο του ελέγχου **CustomerName** στον πίνακα Ιδιοτήτων.

## Πλήρες λειτουργικό παράδειγμα

Παρακάτω υπάρχει ένα ενιαίο, αυτόνομο πρόγραμμα που μπορείτε να αντιγράψετε, να μεταγλωττίσετε και να εκτελέσετε. Δείχνει κάθε βήμα από τη ρύθμιση του έργου μέχρι την αποθήκευση του αρχείου.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class InsertContentControlDemo
{
    static void Main()
    {
        // 1. Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Create a plain‑text content control (StructuredDocumentTag)
        StructuredDocumentTag sdt = new StructuredDocumentTag(
            doc,
            SdtType.PlainText,
            MarkupLevel.Block);

        sdt.Title = "CustomerName";          // Identifier for later use
        sdt.PlaceholderName = "Enter name here";

        // 3. Insert the control at the current cursor position
        builder.InsertNode(sdt);

        // 4. Set default text (optional)
        sdt.XmlMapping.SetXmlFragment("<text>John Doe</text>");

        // 5. Save the document
        string outputPath = @"C:\Temp\SDT.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Εκτελέστε το πρόγραμμα με `dotnet run`. Μετά την εκτέλεση, ανοίξτε το δημιουργημένο αρχείο για να επαληθεύσετε ότι ο έλεγχος περιεχομένου εμφανίζεται όπως περιγράφεται.

## Πρακτικές συμβουλές και συνηθισμένα προβλήματα

| Κατάσταση | Συνιστώμενη προσέγγιση |
|-----------|----------------------|
| **Πολλαπλοί έλεγχοι του ίδιου τύπου** | Δώστε σε κάθε έλεγχο ένα μοναδικό `Title`. Μπορείτε αργότερα να ανακτήσετε έναν έλεγχο με `doc.GetChildNodes(NodeType.StructuredDocumentTag, true).Cast<StructuredDocumentTag>().FirstOrDefault(s => s.Title == "YourTitle")`. |
| **Ο έλεγχος δεν είναι ορατός στο Word** | Βεβαιωθείτε ότι αποθηκεύσατε το έγγραφο με την επέκταση `.docx` και ότι η έκδοση `Aspose.Words` είναι συμβατή με την έκδοση του Office σας. |
| **Απαιτείται έλεγχος πλούσιου κειμένου** | Χρησιμοποιήστε `SdtType.RichText` αντί για `PlainText`. Το τμήμα XML τότε χρησιμοποιεί στοιχεία `<w:richText>`. |
| **Τοποθέτηση του ελέγχου μέσα σε κελί πίνακα** | Μετακινήστε πρώτα τον builder στο κελί: `builder.MoveTo(cell.FirstParagraph); builder.InsertNode(sdt);`. |
| **Απόδοση με μεγάλα έγγραφα** | Δημιουργήστε το `StructuredDocumentTag` μία φορά και επαναχρησιμοποιήστε το εάν χρειάζεστε πολλούς πανομοιότυπους ελέγχους· κλωνοποιήστε το μέσω `sdt.Clone(true)`. |

## Επόμενα βήματα

- **Δημιουργήστε επαναλαμβανόμενους ελέγχους περιεχομένου** (`SdtType.RepeatingSection`) για πίνακες που μεγαλώνουν δυναμικά.  
- **Συνδέστε ελέγχους περιεχομένου με δεδομένα XML** χρησιμοποιώντας `sdt.XmlMapping.LoadXml(xmlString)`.  
- **Κλειδώστε τον έλεγχο** (`sdt.LockContentControl = true`) για να αποτρέψετε τις επεμβάσεις του χρήστη ενώ εξακολουθείτε να επιτρέπετε προγραμματιστικές ενημερώσεις.  

Η εξερεύνηση αυτών των θεμάτων θα ενισχύσει την ικανότητά σας να δημιουργείτε ισχυρά πρότυπα Word με το Aspose.Words.

---

**Συμπέρασμα**  
Τώρα ξέρετε πώς να **εισάγετε έλεγχο περιεχομένου** σε ένα έγγραφο Word χρησιμοποιώντας C#. Ο οδηγός κάλυψε τη δημιουργία του ελέγχου, τον ορισμό placeholder και προεπιλεγμένου κειμένου, την εισαγωγή του στην επιθυμητή θέση και την αποθήκευση του τελικού αρχείου. Με αυτή τη βάση μπορείτε να δημιουργήσετε εξελιγμένες φόρμες, πρότυπα συγχώνευσης αλληλογραφίας και αυτοματοποιημένες αναφορές που αξιοποιούν τις ενσωματωμένες δυνατότητες ελέγχου περιεχομένου του Word.

## Τι θα πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Ορισμός στυλ ελέγχου περιεχομένου](/words/english/net/programming-with-sdt/set-content-control-style/)
- [Ορισμός χρώματος ελέγχου περιεχομένου](/words/english/net/programming-with-sdt/set-content-control-color/)
- [Πώς να δημιουργήσετε πεδία φόρμας και να προσθέσετε περιεχόμενο χρησιμοποιώντας DocumentBuilder στο Aspose.Words για Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}