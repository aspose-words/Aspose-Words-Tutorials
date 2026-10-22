---
category: general
date: 2026-09-08
description: Ορίστε το όνομα ετικέτας και δημιουργήστε έναν έλεγχο περιεχομένου (SDT)
  σε ένα έγγραφο Word χρησιμοποιώντας C#. Μάθετε πώς να προσθέσετε SDT, να γράψετε
  κείμενο στην ετικέτα και να τροποποιήσετε το έγγραφο.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set tag name
- how to add sdt
- modify word document
- create content control
- write text to tag
language: el
lastmod: 2026-09-08
og_description: Ορίστε το όνομα ετικέτας και δημιουργήστε έναν έλεγχο περιεχομένου
  (SDT) σε ένα έγγραφο Word χρησιμοποιώντας C#. Ακολουθήστε αυτόν τον οδηγό βήμα‑προς‑βήμα
  για να προσθέσετε SDT, να γράψετε κείμενο στην ετικέτα και να τροποποιήσετε το έγγραφο.
og_image_alt: Screenshot showing a Word document with a StructuredDocumentTag whose
  tag name is set
og_title: Ορισμός ονόματος ετικέτας και προσθήκη SDT σε έγγραφο Word – Οδηγός C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Set tag name and create a content control (SDT) in a Word document
    using C#. Learn how to add SDT, write text to tag, and modify the document.
  headline: How to set tag name and add SDT in a Word document with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Πώς να ορίσετε το όνομα ετικέτας και να προσθέσετε SDT σε έγγραφο Word με C#
url: /el/java/document-manipulation/how-to-set-tag-name-and-add-sdt-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να ορίσετε το όνομα ετικέτας και να προσθέσετε SDT σε έγγραφο Word με C#

Εάν χρειάζεστε να **ορίσετε το όνομα ετικέτας** για ένα StructuredDocumentTag (SDT) ενώ εργάζεστε με αρχεία Word, αυτός ο οδηγός σας δείχνει ακριβώς πώς. Θα δείτε ένα πλήρες, εκτελέσιμο παράδειγμα που **δημιουργεί έναν έλεγχο περιεχομένου**, γράφει κείμενο στην ετικέτα και **τροποποιεί το έγγραφο Word** από την αρχή μέχρι το τέλος.

Οι προγραμματιστές συχνά ρωτούν, *«πώς να προσθέσετε sdt* σε ένα υπάρχον .docx και στη συνέχεια *να γράψετε κείμενο στην ετικέτα*; – η απάντηση βρίσκεται στη χρήση του Aspose.Words for .NET API. Στο τέλος αυτού του tutorial θα μπορείτε να ανοίξετε ένα αρχείο Word, να εισάγετε ένα plain‑text SDT, να ορίσετε το όνομα ετικέτας του, να το γεμίσετε με περιεχόμενο και να αποθηκεύσετε τις αλλαγές χωρίς να αφήσετε ανεπιθύμητους πόρους.

## Προαπαιτούμενα

* .NET 6.0 ή νεότερο εγκατεστημένο.
* Ένα έγκυρο license του Aspose.Words for .NET (ή μπορείτε να δουλέψετε με την έκδοση αξιολόγησης).
* Visual Studio 2022 (ή οποιοδήποτε IDE που υποστηρίζει C#).
* Ένα αρχείο εισόδου Word (`input.docx`) τοποθετημένο σε φάκελο που μπορείτε να αναφέρετε από τον κώδικα.

## Βήμα 1: Ρυθμίστε το έργο και εισάγετε τα namespaces

Δημιουργήστε ένα νέο έργο Console App και προσθέστε το πακέτο NuGet Aspose.Words:

```bash
dotnet new console -n WordSdtDemo
cd WordSdtDemo
dotnet add package Aspose.Words
```

Στη συνέχεια, προσθέστε τις απαραίτητες οδηγίες `using` στην αρχή του `Program.cs`:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Markup;
```

Αυτά τα namespaces σας δίνουν πρόσβαση στα `Document`, `DocumentBuilder` και την κλάση `StructuredDocumentTag`, που είναι απαραίτητα για **τροποποίηση ενός εγγράφου Word**.

## Βήμα 2: Φορτώστε το υπάρχον έγγραφο Word

Η πρώτη ενέργεια είναι να φορτώσετε το αρχείο που θέλετε να επεξεργαστείτε. Αυτό το βήμα απαιτείται για κάθε σενάριο όπου **τροποποιείτε περιεχόμενα εγγράφου Word**.

```csharp
// Load an existing Word document from disk
string inputPath = @"YOUR_DIRECTORY\input.docx";
Document doc = new Document(inputPath);
Console.WriteLine($"Loaded document: {inputPath}");
```

> **Γιατί φορτώνουμε πρώτα το έγγραφο** – Το αντικείμενο `Document` αντιπροσωπεύει ολόκληρο το πακέτο .docx στη μνήμη. Μόνο μετά τη φόρτωση μπορείτε με ασφάλεια να εισάγετε νέους κόμβους όπως ένα SDT.

## Βήμα 3: Εισάγετε ένα StructuredDocumentTag (SDT) και ορίστε το όνομα ετικέτας του

Τώρα απαντάμε στην κεντρική ερώτηση: **πώς να προσθέσετε sdt** και **να ορίσετε το όνομα ετικέτας**. Χρησιμοποιούμε το `DocumentBuilder.InsertStructuredDocumentTag` με `SdtType.PlainText`. Το δεύτερο όρισμα είναι το όνομα ετικέτας, το οποίο μπορείτε αργότερα να αναφέρετε προγραμματιστικά ή μέσω του UI του Word.

```csharp
// Create a DocumentBuilder attached to the loaded document
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a plain‑text StructuredDocumentTag (content control) at the cursor position
// The second parameter ("MyTag") is the tag name we are setting.
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText, "MyTag");

// Confirm that the tag name has been set
Console.WriteLine($"Inserted SDT with tag name: {sdt.Tag}");
```

> **Επεξήγηση** – Το `InsertStructuredDocumentTag` επιστρέφει μια παρουσία `StructuredDocumentTag`. Με το πέρασμα του `"MyTag"` **ορίζουμε το όνομα ετικέτας** άμεσα κατά τη δημιουργία. Εάν χρειαστεί να το αλλάξετε αργότερα, μπορείτε να αναθέσετε μια νέα τιμή στο `sdt.Tag`.

## Βήμα 4: Γράψτε κείμενο στη νεοδημιουργημένη ετικέτα

Αφού υπάρχει το SDT, συνήθως θέλετε να **γράψετε κείμενο στην ετικέτα** ώστε οι τελικοί χρήστες να βλέπουν placeholder ή προεπιλεγμένο περιεχόμενο. Η μέθοδος `SetText` κάνει ακριβώς αυτό.

```csharp
// Populate the SDT with sample content
sdt.SetText("Sample content");

// Optionally, you can also set the placeholder text that appears when the tag is empty
sdt.PlaceholderName = "Enter your text here";
Console.WriteLine("Text written to the SDT.");
```

> **Γιατί να χρησιμοποιήσετε το SetText** – Η άμεση ανάθεση στην ιδιότητα `Text` θα αντικαθιστούσε ολόκληρη τη ιεραρχία των κόμβων. Το `SetText` ενημερώνει με ασφάλεια το εσωτερικό κείμενο του ελέγχου περιεχομένου διατηρώντας τη δομή του.

## Βήμα 5: Αποθηκεύστε το τροποποιημένο έγγραφο

Τέλος, αποθηκεύστε τις αλλαγές σε ένα νέο αρχείο. Αυτό ολοκληρώνει τη ροή εργασίας **τροποποίησης εγγράφου Word**.

```csharp
// Define the output path
string outputPath = @"YOUR_DIRECTORY\output.docx";

// Save the document with the inserted content control
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Όταν ανοίξετε το `output.docx` στο Microsoft Word, θα δείτε έναν plain‑text έλεγχο περιεχομένου με ετικέτα **MyTag** που περιέχει το κείμενο “Sample content”. Ο έλεγχος μπορεί να επεξεργαστεί χειροκίνητα, και το όνομα ετικέτας παραμένει προσβάσιμο μέσω των εργαλείων προγραμματιστή του Word.

## Πλήρης κώδικας πηγής

Παρακάτω είναι το πλήρες, αυτόνομο πρόγραμμα. Αντιγράψτε το στο `Program.cs` και εκτελέστε το· δεν απαιτούνται επιπλέον αποσπάσματα.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Markup;

namespace WordSdtDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the existing Word document
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(inputPath);
            Console.WriteLine($"Loaded document: {inputPath}");

            // 2️⃣ Create a DocumentBuilder to work with the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert a plain‑text StructuredDocumentTag (SDT) and set its tag name
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText, "MyTag");
            Console.WriteLine($"Inserted SDT with tag name: {sdt.Tag}");

            // 4️⃣ Write text to the tag (and optionally set a placeholder)
            sdt.SetText("Sample content");
            sdt.PlaceholderName = "Enter your text here";
            Console.WriteLine("Text written to the SDT.");

            // 5️⃣ Save the modified document
            string outputPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

### Αναμενόμενη έξοδος στην κονσόλα

```
Loaded document: YOUR_DIRECTORY\input.docx
Inserted SDT with tag name: MyTag
Text written to the SDT.
Document saved to: YOUR_DIRECTORY\output.docx
```

### Πώς φαίνεται το τελικό αρχείο Word

![Έγγραφο Word που εμφανίζει έναν έλεγχο περιεχομένου με όνομα MyTag και το κείμενο “Sample content”](/images/word-sdt-example.png){: .img-fluid alt="Παράδειγμα ορισμού ονόματος ετικέτας σε έγγραφο Word"}

*Το στιγμιότυπο οθόνης δείχνει το SDT με το **όνομα ετικέτας** ορισμένο σε *MyTag* και το ενσωματωμένο κείμενο ορατό.*

## Συνηθισμένες παραλλαγές και ειδικές περιπτώσεις

| Κατάσταση | Πώς να το αντιμετωπίσετε |
|-----------|--------------------------|
| **Δημιουργία rich‑text SDT** | Χρησιμοποιήστε `SdtType.RichText` αντί για `PlainText`. |
| **Ορισμός διαφορετικού ονόματος ετικέτας μετά την εισαγωγή** | `sdt.Tag = "NewTag";` – μπορείτε να επαναορίσετε το όνομα ετικέτας οποτεδήποτε. |
| **Προσθήκη του SDT μέσα σε συγκεκριμένη παράγραφο** | Μετακινήστε τον κέρσορα του builder (`builder.MoveToParagraph(index)`) πριν καλέσετε το `InsertStructuredDocumentTag`. |
| **Πολλαπλά SDT στο ίδιο έγγραφο** | Επαναλάβετε τα βήματα 3‑4 για κάθε έλεγχο· καθένας μπορεί να έχει μοναδικό όνομα ετικέτας. |
| **Εργασία με προστατευμένα έγγραφα** | Βεβαιωθείτε ότι το έγγραφο είναι μη προστατευμένο (`doc.Unprotect()`) πριν την εισαγωγή ενός SDT. |

## Επαγγελματικές συμβουλές για αξιόπιστη αυτοματοποίηση Word

* **Άδεια νωρίς** – Καλέστε `Aspose.Words.License license = new Aspose.Words.License(); license.SetLicense("Aspose.Words.lic");` στην αρχή του `Main` για να αποφύγετε τα υδατογράμματα αξιολόγησης.
* **Απελευθέρωση αντικειμένων** – Τυλίξτε το `Document` σε ένα μπλοκ `using` εάν στοχεύετε στο .NET Framework για να εγγυηθείτε ότι οι χειριστές αρχείων απελευθερώνονται.
* **Επικύρωση ύπαρξης ετικέτας** – Όταν διαβάζετε αργότερα ένα έγγραφο, χρησιμοποιήστε `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` για να εντοπίσετε ετικέτες με βάση την ιδιότητα `Tag`.
* **Απόδοση** – Για μεγάλα έγγραφα, φορτώστε μόνο τις απαιτούμενες ενότητες χρησιμοποιώντας `LoadOptions` με `LoadFormat.Docx` και `LoadFormat.Auto`.  

## Συμπέρασμα

Τώρα ξέρετε πώς να **ορίσετε το όνομα ετικέτας**, **δημιουργήσετε έναν έλεγχο περιεχομένου**, **γράψετε κείμενο στην ετικέτα**, και **τροποποιήσετε ένα έγγραφο Word** χρησιμοποιώντας C#. Το πλήρες παράδειγμα δείχνει το τυπικό μοτίβο για **πώς να προσθέσετε sdt** και να αποθηκεύσετε τις αλλαγές με ασφάλεια.  

Από εδώ

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετικούς θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Προσθήκη περιεχομένου χρησιμοποιώντας Document Builder στο Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Έγγραφο Word - Πώς να αφαιρέσετε περιεχόμενο](/words/english/net/remove-content/)
- [Δημιουργία εγγράφου Word με Aspose.Words – Οδηγός βήμα‑βήμα](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}