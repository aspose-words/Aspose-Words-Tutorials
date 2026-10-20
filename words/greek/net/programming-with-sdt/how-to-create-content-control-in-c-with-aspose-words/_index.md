---
category: general
date: 2026-08-07
description: Πώς να δημιουργήσετε έλεγχο περιεχομένου σε C# χρησιμοποιώντας το Aspose.Words
  – μάθετε πώς να προσθέσετε SDT, να ορίσετε εικονικό κείμενο, να γράψετε προεπιλεγμένο
  κείμενο και να εισάγετε έλεγχο απλού κειμένου.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to create content control
- how to add sdt
- how to set placeholder
- how to write default text
- insert plain text control
language: el
lastmod: 2026-08-07
og_description: Πώς να δημιουργήσετε έλεγχο περιεχομένου σε C# με το Aspose.Words.
  Αυτό το σεμινάριο δείχνει πώς να προσθέσετε SDT, να ορίσετε θέση κράτησης, να γράψετε
  προεπιλεγμένο κείμενο και να εισάγετε έλεγχο απλού κειμένου.
og_image_alt: Screenshot of a Word document showing a plain‑text content control with
  placeholder text
og_title: Πώς να δημιουργήσετε έλεγχο περιεχομένου σε C# – πλήρης οδηγός Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to create content control in C# using Aspose.Words – learn how
    to add SDT, set placeholder, write default text, and insert plain text control.
  headline: How to create content control in C# with Aspose.Words
  type: TechArticle
- description: How to create content control in C# using Aspose.Words – learn how
    to add SDT, set placeholder, write default text, and insert plain text control.
  name: How to create content control in C# with Aspose.Words
  steps:
  - name: Expected output
    text: '- A `.docx` file on the desktop named `CustomerNameControl.docx`. - Inside
      the file, a single content control containing the text **John Doe**. - The placeholder
      text appears in light gray until the user types a new value.'
  - name: Adding multiple content controls
    text: You can repeat the **how to add sdt** steps to insert several controls in
      the same document. Just create a new `StructuredDocumentTag` for each field
      and move the builder accordingly.
  - name: Reading a placeholder programmatically
    text: 'If you need to verify that a placeholder was set correctly, inspect the
      `PlaceholderName` property:'
  - name: Using other SDT types
    text: Aspose.Words supports dropdown lists, date pickers, and rich‑text controls.
      Replace `SdtType.PlainText` with `SdtType.DropDownList` or `SdtType.RichText`
      to change the control type.
  type: HowTo
tags:
- Aspose.Words
- C#
- Content Control
- SDT
title: Πώς να δημιουργήσετε έλεγχο περιεχομένου σε C# με το Aspose.Words
url: /el/net/programming-with-sdt/how-to-create-content-control-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε έλεγχο περιεχομένου σε C# με Aspose.Words

Αν χρειάζεστε **how to create content control** σε ένα έγγραφο Word προγραμματιστικά, αυτός ο οδηγός σας δείχνει ακριβώς αυτό. Θα δείτε πώς να προσθέσετε ένα SDT, να ορίσετε ένα placeholder, να γράψετε προεπιλεγμένο κείμενο και να εισάγετε έναν έλεγχο απλού κειμένου—όλα με το Aspose.Words για .NET.

Ο οδηγός καλύπτει κάθε βήμα από τη ρύθμιση του έργου μέχρι την αποθήκευση του τελικού αρχείου `.docx`. Στο τέλος θα μπορείτε να δημιουργήσετε έγγραφα που περιέχουν πλήρως διαμορφωμένους ελέγχους περιεχομένου, έτοιμους για επεξεργασία downstream ή αλληλεπίδραση με τον χρήστη.

## Προαπαιτούμενα

- .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.7+)
- Άδεια Aspose.Words for .NET ή προσωρινό κλειδί αξιολόγησης
- Visual Studio 2022 (ή οποιοδήποτε IDE που υποστηρίζει C#)
- Βασική εξοικείωση με τη σύνταξη C#

Δεν απαιτούνται πρόσθετα πακέτα NuGet πέρα από το `Aspose.Words`.

## Πώς να δημιουργήσετε έλεγχο περιεχομένου – βήμα 1: ρύθμιση του έργου

Δημιουργήστε μια νέα εφαρμογή κονσόλας και προσθέστε το πακέτο Aspose.Words:

```bash
dotnet new console -n ContentControlDemo
cd ContentControlDemo
dotnet add package Aspose.Words
```

Η διαδικασία **how to create content control** ξεκινά με ένα νέο αντικείμενο `Document`. Αυτό το αντικείμενο αντιπροσωπεύει το αρχείο Word που θα επεξεργαστείτε.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Initialize a blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

> **Pro tip:** Κρατήστε το στιγμιότυπο `DocumentBuilder` ενεργό για ολόκληρο τον κύκλο ζωής του εγγράφου· η επανδημιουργία του χωρίς ανάγκη προσθέτει επιπλέον φόρτο.

## Πώς να προσθέσετε SDT – βήμα 2: εισαγωγή ετικέτας Structured Document Tag απλού κειμένου

Ένα SDT (Structured Document Tag) είναι το τεχνικό όνομα για έναν έλεγχο περιεχομένου. Για **how to add sdt**, δημιουργήστε ένα `StructuredDocumentTag` με τον επιθυμητό τύπο.

```csharp
        // Create a plain‑text SDT (content control)
        StructuredDocumentTag sdt = new StructuredDocumentTag(
            document,
            SdtType.PlainText,   // Plain‑text control
            true);               // Is it a repeating section? false for single use

        // Give the control a title – this is how you reference it later
        sdt.Title = "CustomerName";

        // Insert the SDT at the current cursor position
        builder.InsertNode(sdt);
```

Η επιλογή `SdtType.PlainText` δημιουργεί ένα απλό πλαίσιο κειμένου που οι χρήστες μπορούν να επεξεργαστούν. Ο ορισμός του `Title` σας βοηθά να εντοπίσετε τον έλεγχο όταν χρειαστεί να ανακτήσετε ή να τροποποιήσετε το περιεχόμενό του αργότερα.

## Πώς να ορίσετε placeholder – βήμα 3: διαμόρφωση κειμένου placeholder

Ένα placeholder καθοδηγεί τον τελικό χρήστη εμφανίζοντας δείγμα κειμένου πριν πληκτρολογήσει οτιδήποτε. Για **how to set placeholder**, εκχωρήστε την ιδιότητα `PlaceholderName`.

```csharp
        // Define the placeholder that appears when the control is empty
        sdt.PlaceholderName = "Enter name here";
```

Όταν το έγγραφο ανοίξει στο Microsoft Word, το γκρι κείμενο placeholder εμφανίζεται μέσα στον έλεγχο μέχρι ο χρήστης να εισάγει μια τιμή.

## Πώς να γράψετε προεπιλεγμένο κείμενο – βήμα 4: προσθήκη αρχικού περιεχομένου μέσα στο SDT

Αν θέλετε ο έλεγχος να περιέχει προκαθορισμένο περιεχόμενο, πρέπει να μετακινήσετε το builder μέσα στο SDT και να γράψετε το κείμενο. Αυτό δείχνει **how to write default text**.

```csharp
        // Position the builder inside the SDT so we can add content
        builder.MoveTo(sdt);

        // Write the default text that will be visible initially
        builder.Write("John Doe");
```

Η κλήση στο `MoveTo` αλλάζει τη θέση του δρομέα στο εσωτερικό του SDT. Μετά το `Write`, ο έλεγχος εμφανίζει το “John Doe” ως αρχική του τιμή.

## Εισαγωγή ελέγχου απλού κειμένου – βήμα 5: αποθήκευση του εγγράφου

Τέλος, αποθηκεύστε το έγγραφο στο δίσκο. Αυτό ολοκληρώνει τη λειτουργία **insert plain text control**.

```csharp
        // Save the document with the content control embedded
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "CustomerNameControl.docx");

        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Όταν ανοίξετε το `CustomerNameControl.docx` στο Word, θα δείτε έναν έλεγχο περιεχομένου απλού κειμένου με τίτλο **CustomerName**, που εμφανίζει το placeholder “Enter name here” και το προεπιλεγμένο κείμενο “John Doe”.

### Αναμενόμενο αποτέλεσμα

- Ένα αρχείο `.docx` στην επιφάνεια εργασίας με όνομα `CustomerNameControl.docx`.
- Μέσα στο αρχείο, ένας μοναδικός έλεγχος περιεχομένου που περιέχει το κείμενο **John Doe**.
- Το κείμενο placeholder εμφανίζεται σε ανοιχτό γκρι μέχρι ο χρήστης να πληκτρολογήσει μια νέα τιμή.

## Πρόσθετες παραλλαγές και ειδικές περιπτώσεις

### Προσθήκη πολλαπλών ελέγχων περιεχομένου

Μπορείτε να επαναλάβετε τα βήματα **how to add sdt** για να εισάγετε πολλούς ελέγχους στο ίδιο έγγραφο. Απλώς δημιουργήστε ένα νέο `StructuredDocumentTag` για κάθε πεδίο και μετακινήστε το builder αναλόγως.

```csharp
// Example: add a second control for "OrderNumber"
StructuredDocumentTag orderTag = new StructuredDocumentTag(document, SdtType.PlainText, true);
orderTag.Title = "OrderNumber";
orderTag.PlaceholderName = "Enter order #";
builder.InsertNode(orderTag);
builder.MoveTo(orderTag);
builder.Write("12345");
```

### Ανάγνωση placeholder προγραμματιστικά

Αν χρειάζεται να επαληθεύσετε ότι το placeholder έχει οριστεί σωστά, ελέγξτε την ιδιότητα `PlaceholderName`:

```csharp
string placeholder = sdt.PlaceholderName; // returns "Enter name here"
```

### Χρήση άλλων τύπων SDT

Το Aspose.Words υποστηρίζει λίστες dropdown, επιλογείς ημερομηνίας και ελέγχους rich‑text. Αντικαταστήστε το `SdtType.PlainText` με `SdtType.DropDownList` ή `SdtType.RichText` για να αλλάξετε τον τύπο του ελέγχου.

## Συνηθισμένα προβλήματα και πώς να τα αποφύγετε

| Σύμπτωμα | Αιτία | Διόρθωση |
|----------|-------|----------|
| Το placeholder δεν εμφανίζεται ποτέ | Το έγγραφο αποθηκεύτηκε πριν οριστεί το placeholder | Βεβαιωθείτε ότι το `PlaceholderName` έχει οριστεί **πριν** καλέσετε το `Save`. |
| Το προεπιλεγμένο κείμενο λείπει | Ο builder δεν μετακινήθηκε μέσα στο SDT | Καλέστε `builder.MoveTo(sdt)` πριν το `builder.Write`. |
| Ο τίτλος του ελέγχου είναι κενός | Η ιδιότητα `Title` δεν έχει οριστεί | Πάντα να εκχωρείτε έναν περιγραφικό `Title` για μελλοντική ανάκτηση. |

## Συμπέρασμα

Τώρα γνωρίζετε **how to create content control** σε C# χρησιμοποιώντας το Aspose.Words, συμπεριλαμβανομένων των **how to add sdt**, **how to set placeholder**, **how to write default text** και **insert plain text control**. Το πλήρες παράδειγμα μεταγλωττίζεται σε ένα έτοιμο προς χρήση αρχείο Word που δείχνει κάθε έννοια.

Από εδώ μπορείτε να εξερευνήσετε πιο προχωρημένα σενάρια όπως η σύνδεση ελέγχων περιεχομένου με δεδομένα XML, η διαχείριση επαναλαμβανόμενων τμημάτων ή η μετατροπή του εγγράφου σε PDF διατηρώντας τους ελέγχους. Κάθε ένα από αυτά τα θέματα βασίζεται άμεσα στα θεμέλια που καλύπτονται σε αυτόν τον οδηγό.

Καλό κώδικα!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Rich Text Box Content Control](/words/hindi/net/programming-with-sdt/rich-text-box-content-control/)
- [Rich Text Box Content Control](/words/hongkong/net/programming-with-sdt/rich-text-box-content-control/)
- [Rich Text Box Content Control](/words/spanish/net/programming-with-sdt/rich-text-box-content-control/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}