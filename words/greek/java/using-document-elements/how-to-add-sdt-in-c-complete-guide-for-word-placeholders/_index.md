---
category: general
date: 2026-08-14
description: Πώς να προσθέσετε γρήγορα SDT με το Aspose.Words. Μάθετε πώς να δημιουργήσετε
  πλαίσιο κράτησης λέξης και να εισάγετε έλεγχο απλού κειμένου σε αρχείο .docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add sdt
- create word placeholder
- insert plain text control
- Aspose.Words SDT
- C# Word automation
language: el
lastmod: 2026-08-14
og_description: Πώς να προσθέσετε SDT σε C# χρησιμοποιώντας το Aspose.Words. Ακολουθήστε
  αυτό το σεμινάριο για να δημιουργήσετε σύμβολο κράτησης θέσης Word και να εισάγετε
  έλεγχο απλού κειμένου για δυναμικά έγγραφα.
og_image_alt: Screenshot of a Word document showing a plain‑text Structured Document
  Tag placeholder
og_title: Πώς να προσθέσετε SDT σε C# – βήμα‑βήμα οδηγός για placeholders στο Word
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add SDT quickly with Aspose.Words. Learn to create word placeholder
    and insert plain text control in a .docx file.
  headline: How to add SDT in C# – complete guide for Word placeholders
  type: TechArticle
tags:
- Word
- C#
- Aspose.Words
- SDT
- Document Automation
title: Πώς να προσθέσετε SDT σε C# – πλήρης οδηγός για τα placeholders του Word
url: /el/java/using-document-elements/how-to-add-sdt-in-c-complete-guide-for-word-placeholders/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να προσθέσετε SDT σε C# – πλήρης οδηγός για placeholders Word

Αν χρειάζεστε **how to add sdt** σε ένα αρχείο Word, αυτό το tutorial σας δείχνει τα ακριβή βήματα χρησιμοποιώντας το Aspose.Words for .NET. Στο τέλος του οδηγού θα μπορείτε να **create word placeholder** ετικέτες που επιτρέπουν στους τελικούς χρήστες να πληκτρολογούν απευθείας σε ένα έγγραφο, και θα καταλάβετε πώς να **insert plain text control** αξιόπιστα.

Η εργασία με Structured Document Tags (SDTs) αφαιρεί την ανάγκη για χειροκίνητα πεδία φόρμας και σας παρέχει έναν καθαρό, προγραμματιστικό τρόπο για τη δημιουργία δυναμικών συμβάσεων, αναφορών ή επιστολών. Το παρακάτω παράδειγμα καλύπτει τα πάντα από τη ρύθμιση του έργου μέχρι την αποθήκευση του τελικού αρχείου .docx, ώστε να μπορείτε να αντιγράψετε‑επικολλήσετε τον κώδικα στη δική σας λύση χωρίς να λείπει καμία εξάρτηση.

## Προαπαιτούμενα

- .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.6+)
- Visual Studio 2022 ή οποιοδήποτε IDE C# προτιμάτε
- Άδεια Aspose.Words for .NET (μια δωρεάν προσωρινή άδεια λειτουργεί για δοκιμές)
- Βασική εξοικείωση με τη σύνταξη C# και την έννοια των SDT

> **Pro tip:** Εάν σκοπεύετε να διανείμετε τα παραγόμενα έγγραφα, ενσωματώστε ένα αρχείο άδειας για να αποφύγετε το υδατογράφημα αξιολόγησης.

## Βήμα 1: Ρύθμιση του έργου και εισαγωγή του Aspose.Words

Δημιουργήστε μια νέα εφαρμογή κονσόλας και προσθέστε το πακέτο NuGet Aspose.Words:

```bash
dotnet new console -n SdtDemo
cd SdtDemo
dotnet add package Aspose.Words
```

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
```

Αυτές οι οδηγίες `using` σας δίνουν πρόσβαση στις κλάσεις `Document`, `DocumentBuilder` και `StructuredDocumentTag` που απαιτούνται για τις λειτουργίες **insert plain text control**.

## Βήμα 2: Αρχικοποίηση του εγγράφου και του builder

Το πρώτο μπλοκ κώδικα δημιουργεί ένα κενό έγγραφο Word και ένα `DocumentBuilder` που σας επιτρέπει να γράψετε περιεχόμενο σε αυτό.

```csharp
// Step 2: Create a new document and a builder to edit it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` λειτουργεί όπως ένας κέρσορας· κάθε επόμενη κλήση προσθέτει περιεχόμενο στην τρέχουσα θέση. Η αρχικοποίηση του εγγράφου είναι η βάση για κάθε σενάριο **how to add sdt** επειδή το SDT πρέπει να ανήκει σε μια ενεργή παρουσία `Document`.

## Βήμα 3: Εισαγωγή ενός plain‑text Structured Document Tag (SDT)

Τώρα κάνουμε **insert plain text control** που λειτουργεί ως placeholder όπου ένας χρήστης μπορεί να πληκτρολογήσει ένα όνομα, μια ημερομηνία ή οποιαδήποτε προσαρμοσμένη τιμή.

```csharp
// Step 3: Insert a plain‑text Structured Document Tag (SDT)
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
        StructuredDocumentTagType.PlainText, SdtAppearanceTags.Default);
```

- `StructuredDocumentTagType.PlainText` λέει στο Aspose.Words να δημιουργήσει ένα απλό πεδίο κειμένου.
- `SdtAppearanceTags.Default` δίνει στην ετικέτα το τυπικό στυλ εμφάνισης του Word (ένα σκιασμένο κουτί όταν το έγγραφο ανοίγει στο Word).

## Βήμα 4: Διαμόρφωση του SDT με τίτλο και κείμενο placeholder

Ένα καλά ονομασμένο SDT κάνει το έγγραφο αυτοεξηγητικό για τους τελικούς χρήστες. Εδώ **create word placeholder** μεταδεδομένα και ορίζουμε την υπόδειξη που εμφανίζεται μέσα στο πεδίο.

```csharp
// Step 4: Give the SDT a meaningful title and placeholder text
plainTextTag.Title = "CustomerName";
plainTextTag.PlaceholderName = "Enter name here";
```

- `Title` είναι το εσωτερικό αναγνωριστικό που μπορείτε να χρησιμοποιήσετε αργότερα όταν εξάγετε ή ενημερώνετε την τιμή προγραμματιστικά.
- `PlaceholderName` είναι η γκριζαρισμένη υπόδειξη που εμφανίζεται στο Word, ενημερώνοντας τον χρήστη τι πρέπει να πληκτρολογήσει.

## Βήμα 5: Προσθήκη περιβάλλοντος περιεχομένου

Ένα έγγραφο σπάνια αποτελείται από ένα μόνο SDT. Συνήθως χρειάζεστε κανονικές παραγράφους πριν και μετά το placeholder. Χρησιμοποιήστε τη μέθοδο `WriteLine` του builder για να προσθέσετε στατικό κείμενο.

```csharp
// Step 5: Add regular content before and after the SDT
builder.Writeln("Dear ");
builder.InsertNode(plainTextTag);   // Re‑insert the tag at the current cursor position
builder.Writeln(",");
builder.Writeln("After the SDT");
```

Η κλήση στο `InsertNode` τοποθετεί το προηγουμένως δημιουργημένο SDT ακριβώς εκεί που το χρειάζεστε, διατηρώντας τη ροή του κειμένου γύρω του.

## Βήμα 6: Αποθήκευση του εγγράφου σε αρχείο .docx

Τέλος, αποθηκεύστε το έγγραφο στο δίσκο. Η διαδρομή μπορεί να είναι απόλυτη ή σχετική με το φάκελο του έργου.

```csharp
// Step 6: Save the document to a file
string outputPath = Path.Combine(Environment.CurrentDirectory, "SDT.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Ανοίγοντας το `SDT.docx` στο Microsoft Word εμφανίζεται ένα γκρι placeholder που γράφει **Enter name here**. Οι χρήστες μπορούν να κάνουν κλικ στο πεδίο, να πληκτρολογήσουν μια τιμή, και το έγγραφο θα διατηρήσει αυτήν την τιμή όταν αποθηκευτεί ξανά.

## Πλήρες, εκτελέσιμο παράδειγμα

Συνδυάζοντας όλα τα κομμάτια μαζί, παίρνετε ένα αυτόνομο πρόγραμμα που μπορείτε να εκτελέσετε αμέσως:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a plain‑text SDT
        StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
            StructuredDocumentTagType.PlainText, SdtAppearanceTags.Default);

        // Configure the SDT
        plainTextTag.Title = "CustomerName";
        plainTextTag.PlaceholderName = "Enter name here";

        // Add surrounding content
        builder.Writeln("Dear ");
        builder.InsertNode(plainTextTag);
        builder.Writeln(",");
        builder.Writeln("After the SDT");

        // Save the file
        string outputPath = Path.Combine(Environment.CurrentDirectory, "SDT.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Expected output** όταν εκτελείτε το πρόγραμμα:

```
Document saved to C:\YourProject\bin\Debug\net6.0\SDT.docx
```

Ανοίγοντας το παραγόμενο `SDT.docx` εμφανίζεται:

```
Dear [Enter name here],
After the SDT
```

Το κείμενο μέσα σε αγκύλες είναι το placeholder **insert plain text control** που οι χρήστες μπορούν να αντικαταστήσουν.

## Συνηθισμένες παραλλαγές και ειδικές περιπτώσεις

| Situation | How to adapt the code |
|-----------|-----------------------|
| **Multiple placeholders** | Καλέστε το `InsertStructuredDocumentTag` επανειλημμένα και δώστε σε κάθε ετικέτα ένα μοναδικό `Title`. |
| **Rich‑text SDT** | Χρησιμοποιήστε το `StructuredDocumentTagType.RichText` αντί για `PlainText`. |
| **Lock the placeholder** | Ορίστε `plainTextTag.LockContentControl = true;` για να αποτρέψετε τους χρήστες από τη διαγραφή του πεδίου. |
| **Pre‑populate with a value** | Αναθέστε `plainTextTag.Text = "John Doe";` πριν την αποθήκευση. |
| **Conditional appearance** | Χρησιμοποιήστε `plainTextTag.SdtType = StructuredDocumentTagType.CheckBox;` για έναν έλεγχο κουτιού επιλογής. |

Αυτές οι παραλλαγές σας επιτρέπουν να **create word placeholder** δομές που ταιριάζουν σχεδόν σε οποιοδήποτε σενάριο τύπου φόρμας.

## Συμβουλές αντιμετώπισης προβλημάτων

- **Placeholder not visible** – Βεβαιωθείτε ότι ανοίγετε το αρχείο στο Microsoft Word (ή σε έναν συμβατό προβολέα). Ορισμένοι ελαφροί επεξεργαστές κρύβουν τα SDT.
- **License warning** – Εάν δείτε ένα υδατογράφημα αξιολόγησης, επαληθεύστε ότι το αρχείο άδειας έχει φορτωθεί σωστά (`License license = new License(); license.SetLicense("Aspose.Words.lic");`).
- **Incorrect cursor position** – Μετά την εισαγωγή ενός SDT, ο κέρσορας του builder παραμένει *μετά* την ετικέτα. Εάν χρειάζεται να προσθέσετε κείμενο *μέσα* στην ετικέτα, χρησιμοποιήστε `builder.MoveTo(plainTextTag);` πριν τη γραφή.

## Συμπέρασμα

Τώρα γνωρίζετε **how to add sdt** σε ένα έγγραφο Word χρησιμοποιώντας το Aspose.Words for .NET, πώς να **create word placeholder** ετικέτες, και πώς να **insert plain text control** που οι χρήστες μπορούν να επεξεργαστούν απευθείας στο Word. Το πλήρες παράδειγμα δείχνει την αρχικοποίηση, την εισαγωγή ετικετών, τη διαμόρφωση, το περιβάλλον περιεχομένου και την αποθήκευση—όλα σε ένα ενιαίο, εκτελέσιμο πρόγραμμα.

Στη συνέχεια, εξερευνήστε συναφή θέματα όπως **insert rich text control**, **populate SDTs from a database**, ή **convert the final document to PDF**. Όλα αυτά βασίζονται στα ίδια θεμελιώδη στοιχεία που καλύφθηκαν εδώ, ώστε να μπορείτε να επεκτείνετε την αυτοματοποιημένη διαδικασία σας με σιγουριά.

Καλό προγραμματισμό, και μη διστάσετε να πειραματιστείτε με διαφορετικούς τύπους SDT για να ταιριάζουν στις ανάγκες αυτοματοποίησης εγγράφων σας!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετικά θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε σε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να δημιουργήσετε πεδία φόρμας και να προσθέσετε περιεχόμενο χρησιμοποιώντας DocumentBuilder στο Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Πώς να δημιουργήσετε Editable Ranges σε έγγραφα μόνο για ανάγνωση χρησιμοποιώντας Aspose.Words for Java](/words/english/java/security-protection/editable-ranges-aspose-words-java/)
- [Προσθήκη σελιδοδεικτών Word με Aspose.Words for Java – Εισαγωγή, Ενημέρωση, Διαγραφή](/words/english/java/content-management/aspose-words-java-manage-bookmarks/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}