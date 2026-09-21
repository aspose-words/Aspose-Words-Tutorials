---
category: general
date: 2026-09-21
description: Μάθετε πώς να δημιουργήσετε ένα κενό έγγραφο Word, να προσθέσετε έναν
  έλεγχο απλού κειμένου, να ορίσετε κείμενο κράτησης θέσης και να αποθηκεύσετε το
  αρχείο docx χρησιμοποιώντας το Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set placeholder text
- save docx file
- add plain text control
language: el
lastmod: 2026-09-21
og_description: Δημιουργήστε ένα κενό έγγραφο Word, προσθέστε έναν έλεγχο απλού κειμένου,
  ορίστε κείμενο κράτησης θέσης και αποθηκεύστε το αρχείο docx με το Aspose.Words.
  Ακολουθήστε αυτό το πλήρες σεμινάριο.
og_image_alt: Screenshot showing a blank Word document created to set placeholder
  text in a text control
og_title: Δημιουργήστε ένα κενό έγγραφο Word και προσθέστε έναν έλεγχο κειμένου –
  οδηγός βήμα‑προς‑βήμα
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create a blank Word document, add a plain text control,
    set placeholder text, and save the docx file using Aspose.Words.
  headline: How to create a blank Word document with a text control
  type: TechArticle
tags:
- Aspose.Words
- Word automation
- .NET
- Document generation
title: Πώς να δημιουργήσετε ένα κενό έγγραφο Word με έλεγχο κειμένου
url: /el/java/document-manipulation/how-to-create-a-blank-word-document-with-a-text-control/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε ένα κενό έγγραφο Word με έλεγχο κειμένου

Αν χρειάζεστε να **δημιουργήσετε ένα κενό έγγραφο Word** προγραμματιστικά, αυτός ο οδηγός σας δείχνει ακριβώς πώς. Θα δείτε πώς να προσθέσετε έναν έλεγχο απλού κειμένου, να ορίσετε κείμενο placeholder και τελικά να **αποθηκεύσετε το αρχείο docx** στο δίσκο.

Στις παρακάτω ενότητες θα μάθετε τη πλήρη ροή εργασίας, από την αρχικοποίηση του εγγράφου μέχρι την επαλήθευση ότι το placeholder εμφανίζεται όταν το αρχείο ανοίγει στο Microsoft Word. Τα βήματα λειτουργούν με Aspose.Words .NET 2024‑R2, αλλά οι έννοιες ισχύουν για οποιαδήποτε βιβλιοθήκη .NET δημιουργίας εγγράφων.

## Τι θα χρειαστείτε

- .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης σε .NET Framework 4.8)  
- Aspose.Words for .NET (πακέτο NuGet `Aspose.Words`)  
- Ένα IDE όπως το Visual Studio ή το VS Code  
- Βασικές γνώσεις C#  

> **Pro tip:** Εγκαταστήστε το πακέτο NuGet με `dotnet add package Aspose.Words` για να διατηρήσετε το έργο σας οργανωμένο.

## Βήμα 1: Δημιουργήστε ένα κενό έγγραφο Word

Η πρώτη ενέργεια είναι η δημιουργία ενός κενών `Document`. Αυτό το αντικείμενο αντιπροσωπεύει ένα **κενό έγγραφο Word** που δεν περιέχει ενότητες, παραγράφους ή στυλ.

```csharp
using Aspose.Words;
using Aspose.Words.BuildingBlocks;

// Create a new blank document
Document doc = new Document();
```

Η δημιουργία ενός κεννού εγγράφου σας παρέχει έναν καθαρό καμβά, κάτι που είναι απαραίτητο όταν θέλετε πλήρη έλεγχο πάνω στη διάταξη των εισαχθέντων ελέγχων.

## Βήμα 2: Προσθέστε έναν έλεγχο απλού κειμένου

Ένα Structured Document Tag (SDT) απλού κειμένου λειτουργεί όπως ένας έλεγχος περιεχομένου στο Word. Σας επιτρέπει να επιβάλλετε έναν συγκεκριμένο τύπο δεδομένων και να εμφανίσετε μια υπόδειξη όταν το πεδίο είναι κενό.

```csharp
using Aspose.Words.Markup;

// Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a plain‑text StructuredDocumentTag at block level
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, MarkupLevel.Block);
```

Η μέθοδος `InsertStructuredDocumentTag` επιστρέφει ένα αντικείμενο `StructuredDocumentTag`, το οποίο μπορείτε να διαμορφώσετε περαιτέρω. Η προσθήκη ενός **ελέγχου απλού κειμένου** σε επίπεδο block εξασφαλίζει ότι ο έλεγχος συμπεριφέρεται σαν ξεχωριστή παράγραφος, καθιστώντας εύκολη τη μετέπειτα μορφοποίηση.

## Βήμα 3: Ορίστε κείμενο placeholder για τον έλεγχο

Το κείμενο placeholder καθοδηγεί τον χρήστη να εισάγει τις σωστές πληροφορίες. Στο Word αυτό εμφανίζεται ως ανοιχτό-γκρι κείμενο μέχρι ο χρήστης να πληκτρολογήσει κάτι.

```csharp
// Set a title (used for identification in the Word UI)
sdt.Title = "CustomerName";

// Set the placeholder that the user sees
sdt.PlaceholderName = "Enter name";
```

Εδώ **ορίζουμε κείμενο placeholder** χρησιμοποιώντας την ιδιότητα `PlaceholderName`. Η ιδιότητα `Title` είναι προαιρετική αλλά χρήσιμη για προγραμματιστική πρόσβαση αργότερα, ειδικά αν χρειαστεί να εντοπίσετε τον έλεγχο σε ένα μεγαλύτερο έγγραφο.

## Βήμα 4: Προσθέστε κανονικό περιεχόμενο μετά τον έλεγχο

Συχνά χρειάζεται να συνεχίσετε τη γραφή μετά τον έλεγχο. Η μέθοδος `DocumentBuilder.Writeln` προσθέτει μια νέα παράγραφο με το κείμενο που δίνετε.

```csharp
// Write a normal paragraph after the SDT
builder.Writeln("After the SDT");
```

Αυτό δείχνει ότι το έγγραφο παραμένει επεξεργάσιμο μετά την εισαγωγή του ελέγχου, και μπορείτε να συνδυάσετε κανονικές παραγράφους με ελέγχους περιεχομένου ελεύθερα.

## Βήμα 5: Αποθηκεύστε το αρχείο docx

Τέλος, αποθηκεύστε το έγγραφο που βρίσκεται στη μνήμη σε ένα φυσικό αρχείο. Η μέθοδος `Save` καθορίζει αυτόματα τη μορφή από την επέκταση του αρχείου.

```csharp
// Save the document to a .docx file
string outputPath = @"C:\Temp\SDTExample.docx";
doc.Save(outputPath);
```

Αφού εκτελέσετε το πρόγραμμα, ανοίξτε το `SDTExample.docx` στο Microsoft Word. Θα δείτε ένα κενό έγγραφο με έναν **έλεγχο απλού κειμένου** που εμφανίζει το “Enter name” ως κείμενο placeholder, ακολουθούμενο από τη γραμμή “After the SDT”.

### Αναμενόμενο αποτέλεσμα

Όταν το αρχείο ανοίξει:

1. Η πρώτη γραμμή είναι ένα γκριζαρισμένο placeholder με κείμενο **Enter name** μέσα σε πλαίσιο ελέγχου περιεχομένου.  
2. Η δεύτερη γραμμή εμφανίζει **After the SDT** ως κανονική παράγραφο.

Αν πληκτρολογήσετε ένα όνομα και πατήσετε **Enter**, το placeholder εξαφανίζεται, επιβεβαιώνοντας ότι ο έλεγχος λειτουργεί όπως αναμένεται.

## Κοινές παραλλαγές και ειδικές περιπτώσεις

| Κατάσταση | Τι να αλλάξετε |
|-----------|----------------|
| **Πολλαπλά placeholders** | Καλέστε επανειλημμένα το `InsertStructuredDocumentTag` και ορίστε διαφορετικές τιμές `Title`/`PlaceholderName`. |
| **Inline έλεγχος** | Χρησιμοποιήστε `MarkupLevel.Inline` αντί για `MarkupLevel.Block`. |
| **Rich‑text έλεγχος** | Αντικαταστήστε το `StructuredDocumentTagType.PlainText` με `StructuredDocumentTagType.RichText`. |
| **Αποθήκευση σε ροή** | Χρησιμοποιήστε `doc.Save(stream, SaveFormat.Docx)` όταν χρειάζεται να στείλετε το αρχείο μέσω HTTP. |

> **Προσοχή:** Η προσπάθεια ορισμού `PlaceholderName` σε ένα `RichText` SDT προκαλεί `ArgumentException`. Μόνο οι έλεγχοι απλού κειμένου υποστηρίζουν placeholders.

## Πλήρες λειτουργικό παράδειγμα

```csharp
using System;
using Aspose.Words;
using Aspose.Words.BuildingBlocks;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank document
        Document doc = new Document();

        // Step 2: Prepare a builder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a plain‑text control (SDT)
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            StructuredDocumentTagType.PlainText, MarkupLevel.Block);

        // Step 4: Set title and placeholder text
        sdt.Title = "CustomerName";
        sdt.PlaceholderName = "Enter name";

        // Step 5: Add normal content after the control
        builder.Writeln("After the SDT");

        // Step 6: Save the document
        string path = @"C:\Temp\SDTExample.docx";
        doc.Save(path);

        Console.WriteLine($"Document saved to {path}");
    }
}
```

Η εκτέλεση του προγράμματος παράγει το αρχείο που περιγράφεται στην ενότητα *Αναμενόμενο αποτέλεσμα* παραπάνω.

## Συμπέρασμα

Τώρα ξέρετε πώς να **δημιουργήσετε ένα κενό έγγραφο Word**, να **προσθέσετε έναν έλεγχο απλού κειμένου**, να **ορίσετε κείμενο placeholder** και να **αποθηκεύσετε το αρχείο docx** χρησιμοποιώντας το Aspose.Words. Αυτή η ολοκληρωμένη λύση σας επιτρέπει να δημιουργείτε πρότυπα Word που καθοδηγούν τους χρήστες με σαφείς υποδείξεις, καθιστώντας την αυτοματοποίηση εγγράφων αξιόπιστη και φιλική προς τον χρήστη.

**Επόμενα βήματα**

- Εξερευνήστε παραλλαγές **προσθήκης ελέγχου απλού κειμένου** όπως inline έλεγχοι ή ετικέτες rich‑text.  
- Συνδυάστε πολλαπλά placeholders για να δημιουργήσετε πλήρεις φόρμες (π.χ. τμήματα διεύθυνσης, ημερομηνίες).  
- Χρησιμοποιήστε το `DocumentBuilder` για να εφαρμόσετε στυλ ή να συγχωνεύσετε δεδομένα από βάση, επεκτείνοντας τη ροή **αποθήκευσης αρχείου docx**.

Πειραματιστείτε με διαφορετικές τιμές placeholder και τύπους ελέγχων — η δημιουργία εγγράφων είναι ένας ισχυρός τρόπος να αυτοματοποιήσετε αναφορές, συμβόλαια και οποιαδήποτε επαναλαμβανόμενη έξοδο Word. Καλό κώδικα!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στην δική σας υλοποίηση.

- [Δημιουργία εγγράφου Word με Aspose.Words για .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Δημιουργία εγγράφου Word με Πίνακα χρησιμοποιώντας Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [Δημιουργία εγγράφου Word με Κεφαλίδα και Υποσέλιδο χρησιμοποιώντας Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}