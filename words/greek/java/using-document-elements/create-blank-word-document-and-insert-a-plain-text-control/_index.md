---
category: general
date: 2026-09-18
description: Δημιουργήστε κενό έγγραφο Word χρησιμοποιώντας C# και ορίστε κείμενο
  κράτησης θέσης, στη συνέχεια αποθηκεύστε το έγγραφο ως docx. Μάθετε πώς να εισάγετε
  έλεγχο απλού κειμένου και να προσθέσετε όνομα κράτησης θέσης.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set placeholder text
- save document as docx
- insert plain text control
- add placeholder name
language: el
lastmod: 2026-09-18
og_description: Δημιουργήστε κενό έγγραφο Word χρησιμοποιώντας C#. Ορίστε κείμενο
  κράτησης θέσης, εισάγετε έλεγχο απλού κειμένου, προσθέστε όνομα κράτησης θέσης και
  αποθηκεύστε το έγγραφο ως docx.
og_image_alt: Screenshot of a Word document showing a plain‑text content control with
  placeholder text
og_title: Δημιουργήστε κενό έγγραφο Word με κείμενο κράτησης θέσης – Οδηγός C#
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank Word document using C# and set placeholder text, then
    save document as docx. Learn to insert plain text control and add placeholder
    name.
  headline: Create blank Word document and insert a plain‑text control
  type: TechArticle
- description: Create blank Word document using C# and set placeholder text, then
    save document as docx. Learn to insert plain text control and add placeholder
    name.
  name: Create blank Word document and insert a plain‑text control
  steps:
  - name: An empty Word file (the **blank Word document** you created)
    text: An empty Word file (the **blank Word document** you created)
  - name: A plain‑text content control (the **insert plain text control** step)
    text: A plain‑text content control (the **insert plain text control** step)
  - name: Placeholder text that appears inside the control until the user types something
      (the **set placeholder text** step)
    text: Placeholder text that appears inside the control until the user types something
      (the **set placeholder text** step)
  - name: A placeholder name that can be used for programmatic access later (the **add
      placeholder name** step)
    text: A placeholder name that can be used for programmatic access later (the **add
      placeholder name** step)
  - name: A line of regular text after the control, demonstrating that normal content
      can follow
    text: A line of regular text after the control, demonstrating that normal content
      can follow
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Δημιουργήστε κενό έγγραφο Word και εισάγετε έναν έλεγχο απλού κειμένου
url: /el/java/using-document-elements/create-blank-word-document-and-insert-a-plain-text-control/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία κενής εγγράφου Word και εισαγωγή ελέγχου απλού κειμένου

Αν χρειάζεστε να **δημιουργήσετε κενό έγγραφο Word** προγραμματιστικά, αυτός ο οδηγός σας δείχνει πώς να το κάνετε με C#. Θα μάθετε να **εισάγετε έλεγχο απλού κειμένου**, **ορίσετε κείμενο placeholder**, **προσθέσετε όνομα placeholder**, και τελικά **αποθηκεύσετε το έγγραφο ως docx**. Τα βήματα είναι πλήρως αυτόνομα, ώστε να μπορείτε να αντιγράψετε τον κώδικα σε οποιοδήποτε έργο .NET και να το εκτελέσετε αμέσως.

Η εργασία με αρχεία Word συχνά απαιτεί ένα καθαρό σημείο εκκίνησης — ένα κενό έγγραφο που ήδη περιέχει τους ελέγχους που οι χρήστες σας θα συμπληρώσουν. Στο τέλος αυτού του οδηγού θα έχετε ένα αρχείο `.docx` που περιέχει έναν έλεγχο περιεχομένου απλού κειμένου με ένα χρήσιμο placeholder, ακολουθούμενο από κανονικό περιεχόμενο.

## Προαπαιτούμενα

- .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.6+)
- Αναφορά στη βιβλιοθήκη **Aspose.Words for .NET** (διαθέσιμη μέσω NuGet `Install-Package Aspose.Words`)
- Βασική εξοικείωση με εφαρμογές κονσόλας C#
- Δικαίωμα εγγραφής στον φάκελο εξόδου που καθορίζετε στο `doc.save(...)`

## Τι θα δημιουργήσετε

Το τελικό έγγραφο (`SDT.docx`) περιέχει:

1. Ένα κενό αρχείο Word (το **blank Word document** που δημιουργήσατε)
2. Έναν έλεγχο περιεχομένου απλού κειμένου (το βήμα **insert plain text control**)
3. Κείμενο placeholder που εμφανίζεται μέσα στον έλεγχο μέχρι ο χρήστης να πληκτρολογήσει κάτι (το βήμα **set placeholder text**)
4. Ένα όνομα placeholder που μπορεί να χρησιμοποιηθεί για προγραμματιστική πρόσβαση αργότερα (το βήμα **add placeholder name**)
5. Μια γραμμή κανονικού κειμένου μετά τον έλεγχο, που δείχνει ότι το κανονικό περιεχόμενο μπορεί να ακολουθήσει

## Βήμα 1: Δημιουργία κενής εγγράφου Word

Η πρώτη ενέργεια είναι η δημιουργία ενός κενό αντικειμένου `Document`. Αυτό το αντικείμενο αντιπροσωπεύει ένα εντελώς νέο, **blank Word document** στη μνήμη.

```csharp
using Aspose.Words;
using Aspose.Words.BuildingBlocks;

// Step 1: Create a new blank document
Document doc = new Document();
```

*Γιατί είναι σημαντικό:* Ένα κενό `Document` σας δίνει πλήρη έλεγχο σε κάθε στοιχείο που προσθέτετε, εξασφαλίζοντας ότι δεν υπάρχουν κρυφά στυλ ή ενότητες που να παρεμβαίνουν στον έλεγχο περιεχομένου που θα εισάγετε αργότερα.

## Βήμα 2: Αρχικοποίηση DocumentBuilder

`DocumentBuilder` είναι η βοηθητική κλάση που σας επιτρέπει να γράψετε στο `Document`. Παρακολουθεί τη θέση του τρέχοντος κέρσορα και παρέχει μεθόδους για την εισαγωγή όλων των ειδών αντικειμένων Word.

```csharp
// Step 2: Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Γιατί είναι σημαντικό:* Η χρήση ενός `DocumentBuilder` απλοποιεί τη διαδικασία προσθήκης ενός **plain‑text control** επειδή ο builder γνωρίζει το ακριβές σημείο εισαγωγής.

## Βήμα 3: Εισαγωγή ελέγχου απλού κειμένου

Τώρα προσθέτουμε έναν **plain‑text content control** (γνωστό επίσης ως Structured Document Tag ή SDT). Ο τύπος ελέγχου `StructuredDocumentTagType.PLAIN_TEXT` λέει στο Word να αντιμετωπίζει το περιεχόμενο ως απλό κείμενο, όχι πλούσια μορφοποίηση.

```csharp
// Step 3: Insert a plain‑text StructuredDocumentTag (SDT) with a tag ID
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "MyTag");
```

*Γιατί είναι σημαντικό:* Η μέθοδος `InsertStructuredDocumentTag` δημιουργεί τον έλεγχο και επιστρέφει μια αναφορά (`sdt`) που μπορείτε να διαμορφώσετε περαιτέρω, όπως η προσθήκη κειμένου placeholder ή προσαρμοσμένου ονόματος.

## Βήμα 4: Ορισμός κειμένου placeholder και προσθήκη ονόματος placeholder

Το κείμενο placeholder δίνει στους χρήστες μια οπτική ένδειξη για το τι πρέπει να πληκτρολογήσουν. Το βήμα **add placeholder name** εκχωρεί έναν προγραμματιστικό αναγνωριστικό που μπορείτε να ερωτήσετε αργότερα με `doc.GetChildNodes` ή παρόμοιες API.

```csharp
// Step 4a: Set a placeholder text that appears when the SDT is empty
sdt.SetPlaceholderName("Enter text…");

// Step 4b: Add a placeholder name (tag ID) for later retrieval
sdt.Tag = "MyTag";
```

*Γιατί είναι σημαντικό:* Η `SetPlaceholderName` ελέγχει το γκρι κείμενο υπόδειξης που εμφανίζεται μέσα στον έλεγχο περιεχομένου. Ο ορισμός του `Tag` (η ενέργεια **add placeholder name**) σας επιτρέπει να εντοπίσετε τον έλεγχο στο δέντρο του εγγράφου χωρίς να σαρώσετε ολόκληρο το αρχείο.

## Βήμα 5: Προσθήκη κανονικού περιεχομένου μετά τον έλεγχο

Για να αποδείξουμε ότι το έγγραφο συνεχίζεται κανονικά μετά τον έλεγχο, γράφουμε μια απλή γραμμή κειμένου.

```csharp
// Step 5: Add regular content after the SDT
builder.Writeln("After the tag.");
```

## Βήμα 6: Αποθήκευση εγγράφου ως docx

Τέλος, αποθηκεύουμε το έγγραφο στη μνήμη στο δίσκο. Αυτή είναι η ενέργεια **save document as docx** που παράγει το αρχείο που μπορείτε να ανοίξετε στο Microsoft Word.

```csharp
// Step 6: Save the document as a .docx file
string outputPath = @"YOUR_DIRECTORY/SDT.docx";
doc.Save(outputPath);
```

*Γιατί είναι σημαντικό:* Η χρήση της μορφής `.docx` εξασφαλίζει μέγιστη συμβατότητα με τις σύγχρονες εκδόσεις του Word, Google Docs και άλλα εργαλεία συμβατά με το Office.

## Πλήρες, εκτελέσιμο παράδειγμα

Παρακάτω βρίσκεται το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε σε ένα έργο console‑app. Αντικαταστήστε το `YOUR_DIRECTORY` με μια πραγματική διαδρομή φακέλου στον υπολογιστή σας.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.BuildingBlocks;

namespace WordSdtExample
{
    class Program
    {
        static void Main()
        {
            // Create a new blank Word document
            Document doc = new Document();

            // Initialize a DocumentBuilder to work with the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a plain‑text StructuredDocumentTag (SDT) with a tag ID
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");

            // Set a placeholder text that appears when the SDT is empty
            sdt.SetPlaceholderName("Enter text…");

            // Add a placeholder name (tag) for later retrieval
            sdt.Tag = "MyTag";

            // Add regular content after the SDT
            builder.Writeln("After the tag.");

            // Save the document as a .docx file
            string outputPath = @"C:\Temp\SDT.docx"; // change to your folder
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

### Αναμενόμενο αποτέλεσμα

- Το άνοιγμα του `SDT.docx` στο Word εμφανίζει ένα κενό γκρι πλαίσιο με το κείμενο **Enter text…** μέσα.
- Το πλαίσιο είναι ένας έλεγχος περιεχομένου απλού κειμένου· μπορείτε να πληκτρολογήσετε απευθείας σε αυτό.
- Κάτω από το πλαίσιο, η γραμμή **After the tag.** εμφανίζεται ως κανονικό κείμενο παραγράφου.

Αν το placeholder δεν εμφανίζεται, βεβαιωθείτε ότι χρησιμοποιείτε μια πρόσφατη έκδοση του Aspose.Words (v23.1 ή νεότερη) και ότι το έγγραφο ανοίγει σε έκδοση του Word που υποστηρίζει ελέγχους περιεχομένου (Word 2007+).

## Συνηθισμένες παραλλαγές και ειδικές περιπτώσεις

| Σενάριο | Πώς να προσαρμόσετε τον κώδικα |
|----------|-----------------------|
| **Multiple placeholders** | Καλέστε ξανά το `InsertStructuredDocumentTag` με διαφορετικό ID ετικέτας και όνομα placeholder. |
| **Rich‑text control** | Χρησιμοποιήστε `StructuredDocumentTagType.RichText` αντί για `PlainText`. |
| **Setting default text** | Μετά την εισαγωγή, ορίστε `sdt.Text = "Default value";` – αυτό το κείμενο αντικαθιστά το placeholder όταν φορτώνεται το έγγραφο. |
| **Saving to a stream** | Αντικαταστήστε το `doc.Save(outputPath);` με `doc.Save(stream, SaveFormat.Docx);` για να στείλετε το αρχείο μέσω HTTP. |
| **Changing placeholder color** | Χρησιμοποιήστε `sdt.PlaceholderTextColor = System.Drawing.Color.Gray;` (απαιτεί `using System.Drawing`). |

## Συμβουλές επαγγελματιών

- **Reuse the tag ID**: Η διατήρηση της ετικέτας (`MyTag`) συνεπούς σε όλα τα έγγραφα σας επιτρέπει να αυτοματοποιήσετε την πληρότητα δεδομένων αργότερα με `doc.Range.Replace` ή το `StructuredDocumentTagCollection`.
- **Avoid hard‑coded paths**: Χρησιμοποιήστε `Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments), "SDT.docx")` για μια φορητή τοποθεσία εξόδου.
- **Performance**: Εάν χρειάζεται να δημιουργήσετε χιλιάδες έγγραφα, δημιουργήστε ένα ενιαίο πρότυπο `Document` με το SDT ήδη παρόν, και στη συνέχεια κλωνοποιήστε το με `doc.Clone()` για κάθε επανάληψη.

## Συμπέρασμα

Τώρα γνωρίζετε πώς να **create blank Word document**, **insert plain text control**, **set placeholder text**, **add placeholder name**, και **save document as docx** χρησιμοποιώντας το Aspose.Words for .NET. Αυτό το μοτίβο αποτελεί τη βάση για τη δημιουργία προτύπων Word με φόρμες, αυτοματοποιημένων αναφορών ή οποιασδήποτε λύσης που απαιτεί επεξεργάσιμα placeholders από τον χρήστη.

Μη διστάσετε να πειραματιστείτε με άλλους τύπους ελέγχων, να συνδυάσετε πολλαπλά placeholders, ή να ενσωματώσετε αυτόν τον κώδικα σε ένα web API που επιστρέφει το παραγόμενο αρχείο `.docx` απευθείας στους καλούντες. Για το επόμενο βήμα, εξερευνήστε το **populate a content control with data programmatically** ή το **convert the generated Word file to PDF** χρησιμοποιώντας τις ενσωματωμένες δυνατότητες μετατροπής του Aspose.Words. Καλή προγραμματιστική!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Εισαγωγή πεδίου κειμένου φόρμας σε έγγραφο Word](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)
- [Δημιουργία εγγράφου Word με πίνακα χρησιμοποιώντας Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [Δημιουργία εγγράφου Word με κεφαλίδα και υποσέλιδο χρησιμοποιώντας Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}