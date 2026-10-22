---
category: general
date: 2026-09-05
description: Δημιουργήστε έγγραφο Word με το Aspose.Words, ορίστε κείμενο κράτησης
  θέσης, προσθέστε έλεγχο και αποθηκεύστε το έγγραφο ως docx σε C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- set placeholder text
- save document as docx
- how to add control
- how to create tag
language: el
lastmod: 2026-09-05
og_description: Δημιουργήστε έγγραφο Word χρησιμοποιώντας το Aspose.Words για .NET,
  ορίστε κείμενο κράτησης θέσης, προσθέστε έλεγχο και αποθηκεύστε το έγγραφο ως docx.
  Ακολουθήστε αυτό το πλήρες σεμινάριο.
og_image_alt: Screenshot showing a word document created with a content control placeholder
og_title: Δημιουργήστε ένα έγγραφο Word με ελέγχους περιεχομένου σε C# – οδηγός βήμα‑προς‑βήμα
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create word document with Aspose.Words, set placeholder text, add control,
    and save document as docx in C#.
  headline: How to create word document with content controls in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Content Control
- Document Generation
title: Πώς να δημιουργήσετε έγγραφο Word με ελέγχους περιεχομένου σε C#
url: /el/net/programming-with-sdt/how-to-create-word-document-with-content-controls-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε έγγραφο Word με ελέγχους περιεχομένου σε C#

Αν χρειάζεστε **να δημιουργήσετε έγγραφο Word** που περιλαμβάνει δομημένους ελέγχους περιεχομένου, αυτός ο οδηγός σας δείχνει πώς να προσθέσετε μια ετικέτα plain‑text, **να ορίσετε κείμενο placeholder**, και **να αποθηκεύσετε το έγγραφο ως docx** χρησιμοποιώντας το Aspose.Words for .NET. Το παράδειγμα είναι πλήρως εκτελέσιμο και παρουσιάζει την προτεινόμενη προσέγγιση για προγραμματισμένη δημιουργία Word.

Θα μάθετε πώς να:

* Αρχικοποιήσετε ένα κενό αρχείο Word με `Document` και `DocumentBuilder`.
* **Πώς να προσθέσετε έλεγχο** (ένα `StructuredDocumentTag`) στο σώμα του εγγράφου.
* **Πώς να δημιουργήσετε ετικέτα** με τίτλο και placeholder που καθοδηγούν τον τελικό χρήστη.
* Διατηρήσετε το αποτέλεσμα με `document.Save`, εξασφαλίζοντας ότι το αρχείο είναι έγκυρο `.docx`.

Το tutorial υποθέτει ότι έχετε ένα βασικό περιβάλλον ανάπτυξης C# και άδεια για το Aspose.Words (η δωρεάν αξιολόγηση λειτουργεί για εκπαιδευτικούς σκοπούς).

---

## Προαπαιτούμενα

| Απαίτηση | Λόγος |
|----------|-------|
| .NET 6.0 ή νεότερο | Παρέχει το runtime για το Aspose.Words for .NET. |
| Πακέτο NuGet Aspose.Words for .NET | Παρέχει τις κλάσεις `Document`, `DocumentBuilder` και `StructuredDocumentTag`. |
| IDE όπως το Visual Studio 2022 | Διευκολύνει την εκτέλεση και τον εντοπισμό σφαλμάτων του δείγματος. |

Εγκαταστήστε το πακέτο με τη .NET CLI:

```bash
dotnet add package Aspose.Words
```

---

## Βήμα 1: Ρύθμιση του έργου για **δημιουργία εγγράφου Word**

Δημιουργήστε ένα νέο έργο console (ή προσθέστε τον κώδικα σε υπάρχον). Οι πρώτες γραμμές δημιουργούν ένα κενό αρχείο Word και ένα `DocumentBuilder` που σας επιτρέπει να γράφετε περιεχόμενο.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

// Initialize a new empty document.
Document document = new Document();

// Obtain a builder positioned at the start of the document.
DocumentBuilder builder = new DocumentBuilder(document);
```

Το `Document` αντιπροσωπεύει τη δομή του αρχείου, ενώ το `DocumentBuilder` παρακολουθεί το σημείο εισαγωγής. Αυτό το μοτίβο είναι η βάση για οποιοδήποτε σενάριο δημιουργίας Word.

---

## Βήμα 2: **Πώς να προσθέσετε έλεγχο** – δημιουργία ελέγχου περιεχομένου plain‑text (ετικέτα)

Ένας έλεγχος περιεχομένου στο Word ονομάζεται *structured document tag* (SDT). Ο παρακάτω κώδικας δημιουργεί ένα plain‑text SDT, ορίζει έναν τίτλο και καθορίζει το placeholder που εμφανίζεται όταν ανοίγει το έγγραφο.

```csharp
// Create a plain‑text StructuredDocumentTag (SDT) at block level.
StructuredDocumentTag contentControl = new StructuredDocumentTag(
    document, SdtType.PlainText, MarkupLevel.Block);

// Assign a meaningful title – useful for later retrieval.
contentControl.Title = "CustomerName";

// Define the placeholder text that prompts the user.
contentControl.PlaceholderName = "Enter name";

// Insert the tag at the builder's current cursor location.
builder.InsertNode(contentControl);
```

**Γιατί είναι σημαντικό:**  
* Η ιδιότητα `Title` λειτουργεί ως σταθερό αναγνωριστικό, επιτρέποντάς σας να εντοπίζετε ή να αντικαθιστάτε τον έλεγχο προγραμματιστικά αργότερα.  
* Η `PlaceholderName` παρέχει οπτική καθοδήγηση στον αναγνώστη του εγγράφου χωρίς να απαιτείται επιπλέον κώδικας UI.

![Create word document with content control placeholder](image.png)

*Κείμενο alt εικόνας: Δημιουργία εγγράφου Word με έλεγχο περιεχομένου που εμφανίζει κείμενο placeholder.*

---

## Βήμα 3: Μετακίνηση του δρομέα μέσα στον έλεγχο και εγγραφή προεπιλεγμένου κειμένου

Μετά την εισαγωγή του ελέγχου, ο δρομέας του builder εξακολουθεί να βρίσκεται εκτός αυτού. Μετακινήστε τον δρομέα μέσα στην ετικέτα ώστε οι επόμενες εγγραφές να γίνουν μέρος του περιεχομένου του ελέγχου.

```csharp
// Position the builder inside the newly added content control.
builder.MoveTo(contentControl);

// Write default text that appears when the placeholder is cleared.
builder.Write("John Doe");
```

Αν προτιμάτε να αφήσετε τον έλεγχο κενό, παραλείψτε την κλήση `Write`. Το placeholder παραμένει ορατό μέχρι ο χρήστης πληκτρολογήσει μια τιμή.

---

## Βήμα 4: **Ορισμός κειμένου placeholder** (εναλλακτική προσέγγιση)

Μερικές φορές χρειάζεται να αλλάξετε το placeholder μετά τη δημιουργία της ετικέτας. Μπορείτε να τροποποιήσετε άμεσα την ιδιότητα `PlaceholderName`:

```csharp
contentControl.PlaceholderName = "Type the customer's full name here";
```

Η αλλαγή του placeholder **δεν** επηρεάζει το υπάρχον περιεχόμενο, καθιστώντας ασφαλή την ενημέρωση των υποδείξεων UI χωρίς να τροποποιηθεί το δεδομένο από τον χρήστη.

---

## Βήμα 5: **Αποθήκευση εγγράφου ως docx**

Αποθηκεύστε το έγγραφο στη μνήμη σε ένα φυσικό αρχείο. Η μέθοδος `Save` καθορίζει αυτόματα τη μορφή από την επέκταση του αρχείου.

```csharp
// Save the document in DOCX format.
document.Save("YOUR_DIRECTORY/SdtExample.docx");
```

Αν χρειάζεστε διαφορετική μορφή (π.χ., PDF ή HTML), περάστε μια τιμή του enum `SaveFormat`:

```csharp
document.Save("SdtExample.pdf", SaveFormat.Pdf);
```

---

## Βήμα 6: Πλήρες, εκτελέσιμο παράδειγμα

Συνδυάζοντας όλα τα παραπάνω προκύπτει ένα σύντομο πρόγραμμα που δείχνει **πώς να δημιουργήσετε ετικέτα**, να ορίσετε το placeholder της, και **να αποθηκεύσετε το έγγραφο ως docx**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // 1. Initialize document and builder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Create a plain‑text content control (tag).
        StructuredDocumentTag sdt = new StructuredDocumentTag(
            document, SdtType.PlainText, MarkupLevel.Block);
        sdt.Title = "CustomerName";
        sdt.PlaceholderName = "Enter name";

        // 3. Insert the control and move inside it.
        builder.InsertNode(sdt);
        builder.MoveTo(sdt);

        // 4. Write default text (optional).
        builder.Write("John Doe");

        // 5. Save the file as DOCX.
        document.Save("SdtExample.docx");
        Console.WriteLine("Word document created successfully.");
    }
}
```

**Αναμενόμενο αποτέλεσμα:**  
Η εκτέλεση του προγράμματος δημιουργεί το `SdtExample.docx` που περιέχει μια παράγραφο με έναν plain‑text έλεγχο περιεχομένου με τίτλο *CustomerName*. Ο έλεγχος εμφανίζει το κείμενο “John Doe” ως αρχικό του περιεχόμενο· αν αφαιρεθεί το προεπιλεγμένο κείμενο, το placeholder “Enter name” εμφανίζεται σε ανοιχτό γκρι όταν το αρχείο ανοίξει στο Microsoft Word.

---

## Συνηθισμένες παραλλαγές και ειδικές περιπτώσεις

| Σενάριο | Συνιστώμενη προσαρμογή |
|----------|------------------------|
| **Πολλαπλοί έλεγχοι** | Επαναλάβετε τα βήματα 2‑4 για κάθε πεδίο, δίνοντας σε κάθε έναν μοναδικό `Title`. |
| **Rich‑text έλεγχος** | Χρησιμοποιήστε `SdtType.RichText` αντί για `PlainText`. |
| **Ενότητα επανάληψης** | Επιλέξτε `SdtType.RepeatingSection` και προσθέστε παιδικούς ελέγχους μέσα στην ενότητα. |
| **Υπάρχον έγγραφο** | Φορτώστε ένα υπάρχον αρχείο με `new Document("template.docx")` και εισάγετε ελέγχους στην επιθυμητή θέση. |
| **Unicode placeholder** | Ορίστε `PlaceholderName` σε οποιοδήποτε Unicode string· το Word το αποδίδει σωστά. |
| **Μεγάλα έγγραφα** | Αποδεσμεύστε το `DocumentBuilder` μετά τη χρήση για ελευθέρωση μνήμης (`builder.Dispose();`). |

**Pro tip:** Όταν χρειάζεται να ανακτήσετε την τιμή που εισήγαγε ο χρήστης, καλέστε `StructuredDocumentTag.GetText()` μετά την αποθήκευση και επαναφόρτωση του εγγράφου. Αυτή η μέθοδος επιστρέφει το εσωτερικό κείμενο χωρίς το placeholder.

**Προσοχή:** Η χρήση placeholder που ταιριάζει με το προεπιλεγμένο κείμενο μπορεί να προκαλέσει σύγχυση, επειδή το Word κρύβει το placeholder όταν υπάρχει οποιοδήποτε κείμενο. Κρατήστε τα διαφορετικά.

---

## Συμπέρασμα

Τώρα γνωρίζετε πώς να **δημιουργήσετε έγγραφο Word** προγραμματιστικά, **πώς να προσθέσετε έλεγχο**, **πώς να δημιουργήσετε ετικέτα**, **να ορίσετε κείμενο placeholder**, και **να αποθηκεύσετε το έγγραφο ως docx** χρησιμοποιώντας το Aspose.Words for .NET. Το πλήρες παράδειγμα μπορεί να αντιγραφεί σε οποιοδήποτε έργο C# και να επεκταθεί για υποστήριξη πρόσθετων τύπων ελέγχων, επαναλαμβανόμενων ενοτήτων ή ενσωμάτωσης με πηγές δεδομένων.

Επόμενα βήματα που μπορείτε να εξερευνήσετε:

* Προσθήκη **ελέγχων περιεχομένου εικόνας** (`SdtType.Picture`) για ενσωμάτωση γραφικών που παρέχει ο χρήστης.  
* Χρήση **binding** για αντιστοίχιση των SDT σε XML δεδομένα για σενάρια mail‑merge.  
* Μετατροπή του παραγόμενου DOCX σε PDF (`SaveFormat.Pdf`) για διανομή.

Δοκιμάστε διαφορετικούς τύπους ετικετών και μηνύματα placeholder ώστε να ταιριάζουν στη ροή εργασίας της εφαρμογής σας. Καλή προγραμματιστική!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετικούς τομείς που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}