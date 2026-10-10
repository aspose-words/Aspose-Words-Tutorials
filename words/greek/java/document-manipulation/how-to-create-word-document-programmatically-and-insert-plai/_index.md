---
category: general
date: 2026-10-10
description: Δημιουργήστε έγγραφο Word προγραμματιστικά με το Aspose.Words και εισάγετε
  έλεγχο περιεχομένου απλού κειμένου – ένας βήμα‑προς‑βήμα οδηγός για προγραμματιστές
  .NET.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- insert plain text content control
language: el
lastmod: 2026-10-10
og_description: Δημιουργήστε έγγραφο Word προγραμματιστικά με το Aspose.Words και
  προσθέστε έναν έλεγχο περιεχομένου απλού κειμένου που εμφανίζει κείμενο κράτησης
  θέσης, επιτρέποντας δυναμικά πεδία φόρμας σε αρχεία .docx.
og_image_alt: Screenshot of a Word document displaying a plain text content control
  placeholder
og_title: Δημιουργία εγγράφου Word προγραμματιστικά και προσθήκη ελέγχου περιεχομένου
  απλού κειμένου
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Create word document programmatically with Aspose.Words and insert
    plain text content control – a step‑by‑step guide for .NET developers.
  headline: How to create word document programmatically and insert plain text content
    control
  type: TechArticle
tags:
- word
- document automation
- content control
- Aspose.Words
- C#
title: Πώς να δημιουργήσετε έγγραφο Word προγραμματιστικά και να εισάγετε έλεγχο περιεχομένου
  απλού κειμένου
url: /el/java/document-manipulation/how-to-create-word-document-programmatically-and-insert-plai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε πρόγραμμα έγγραφο Word και να εισάγετε έλεγχο περιεχομένου απλού κειμένου

Αν χρειάζεται να **δημιουργήσετε πρόγραμμα έγγραφο Word**, αυτός ο οδηγός σας δείχνει ακριβώς πώς να το κάνετε με το Aspose.Words for .NET. Σε λίγες γραμμές κώδικα θα μάθετε επίσης πώς να **εισάγετε έλεγχο περιεχομένου απλού κειμένου** (επίσης γνωστό ως Structured Document Tag) ώστε το έγγραφο να λειτουργεί ως φορμα που μπορεί να συμπληρωθεί.

Θα περάσετε από τη πλήρη ροή εργασίας — από την αρχικοποίηση ενός νέου αντικειμένου `Document` μέχρι την αποθήκευση του τελικού αρχείου .docx. Δεν απαιτούνται εξωτερικά εργαλεία, και το παράδειγμα λειτουργεί με .NET 6, .NET 7 ή οποιοδήποτε πρόσφατο .NET runtime.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* Ένα έγκυρο license του Aspose.Words for .NET (ή χρησιμοποιήστε τη δωρεάν λειτουργία αξιολόγησης).  
* Το .NET 6+ SDK εγκατεστημένο.  
* Ένα IDE όπως το Visual Studio 2022, Rider ή VS Code.  

Αν δεν έχετε εγκαταστήσει ακόμη το πακέτο NuGet Aspose.Words, εκτελέστε:

```bash
dotnet add package Aspose.Words
```

## Βήμα 1: Δημιουργία προγράμματος εγγράφου Word

Το πρώτο βήμα είναι η δημιουργία ενός κενών `Document` και ενός `DocumentBuilder`. Ο builder παρέχει ένα βολικό API για την προσθήκη περιεχομένου, σελίδων και Structured Document Tags (SDTs).

```csharp
using Aspose.Words;
using Aspose.Words.BuildingBlocks;
using Aspose.Words.Markup;

// Create an empty document and a builder attached to it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Γιατί είναι σημαντικό** – Το `Document` αντιπροσωπεύει ολόκληρο το αρχείο .docx στη μνήμη. Δημιουργώντας το προγραμματιστικά αποφεύγετε το κόστος ανοίγματος ενός αρχείου προτύπου, κάτι που είναι χρήσιμο για τη δημιουργία αναφορών, τιμολογίων ή οποιουδήποτε εγγράφου «on‑the‑fly».

## Βήμα 2: Εισαγωγή ελέγχου περιεχομένου απλού κειμένου

Ένας **έλεγχος περιεχομένου απλού κειμένου** (SDT) επιτρέπει στους χρήστες να πληκτρολογούν κείμενο σε μια προ‑ορισμένη περιοχή. Υποστηρίζει επίσης κείμενο placeholder που εμφανίζεται όταν ο έλεγχος είναι κενός.

```csharp
// Insert a plain‑text Structured Document Tag (SDT) with an identifier "MyTag"
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "MyTag");

// Set placeholder text that shows inside the control when it is empty
plainTextTag.PlaceholderName = "Enter name";
```

**Επεξήγηση** – Η `InsertStructuredDocumentTag` δημιουργεί το SDT στη τρέχουσα θέση του κέρσορα του `DocumentBuilder`. Η τιμή enum `StructuredDocumentTagType.PlainText` λέει στο Aspose.Words να αποδώσει ένα πλαίσιο απλού κειμένου αντί για combo box ή date picker. Η ιδιότητα `PlaceholderName` παρέχει οπτική υπόδειξη στον χρήστη, παρόμοια με το γκρι κείμενο υπόδειξης που βλέπετε σε σύγχρονες φόρμες Word.

### Συνηθισμένες παραλλαγές

| Παραλλαγή | Πώς να την υλοποιήσετε |
|-----------|-----------------------|
| **Rich‑text content control** | Χρησιμοποιήστε `StructuredDocumentTagType.RichText` αντί για `PlainText`. |
| **Repeating section** | Χρησιμοποιήστε `StructuredDocumentTagType.Group` και ενσωματώστε άλλες ετικέτες μέσα. |
| **Custom XML mapping** | Καλέστε `plainTextTag.SetXmlMapping(xmlPart, xpath, false)` μετά τη δημιουργία ενός `XmlPart`. |

## Βήμα 3: Προσθήκη πρόσθετου περιεχομένου εγγράφου (προαιρετικό)

Μπορείτε να προσθέσετε κανονικές παραγράφους, πίνακες ή εικόνες πριν ή μετά τον έλεγχο περιεχομένου. Ακολουθεί ένα γρήγορο παράδειγμα που προσθέτει έναν τίτλο και μια παράγραφο:

```csharp
// Add a heading above the content control
builder.Font.Size = 16;
builder.Font.Bold = true;
builder.Writeln("Employee Information");

// Move the cursor back to the placeholder location (already set by InsertStructuredDocumentTag)
builder.Font.Size = 12;
builder.Font.Bold = false;
builder.Writeln(); // Adds a line break after the control
```

**Συμβουλή** – Ο κέρσορας του builder μετακινείται αυτόματα στο τέλος του εισαχθέντος SDT, έτσι οποιεσδήποτε επόμενες κλήσεις `Writeln` θα εμφανιστούν μετά τον έλεγχο.

## Βήμα 4: Αποθήκευση του εγγράφου που περιέχει τον έλεγχο περιεχομένου

Τέλος, γράψτε το έγγραφο στο δίσκο. Μπορείτε να επιλέξετε οποιαδήποτε υποστηριζόμενη μορφή (`.docx`, `.pdf`, `.html`, κ.λπ.). Για αυτόν τον οδηγό αποθηκεύουμε ως αρχείο Word.

```csharp
// Save the document to the specified path
string outputPath = Path.Combine(Environment.CurrentDirectory, "SdtExample.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

### Αναμενόμενο αποτέλεσμα

Όταν ανοίξετε το *SdtExample.docx* στο Microsoft Word θα δείτε:

1. Έναν τίτλο **Employee Information**.  
2. Έναν έλεγχο περιεχομένου απλού κειμένου με το γκρι placeholder **Enter name**.  

Αν κάνετε κλικ μέσα στον έλεγχο, το placeholder εξαφανίζεται και μπορείτε να πληκτρολογήσετε οποιοδήποτε κείμενο. Το αναγνωριστικό ετικέτας του ελέγχου (`MyTag`) μπορεί αργότερα να προσπελαστεί προγραμματιστικά για εξαγωγή δεδομένων ή επικύρωση.

## Πλήρες, εκτελέσιμο παράδειγμα

Παρακάτω υπάρχει μια αυτόνομη εφαρμογή κονσόλας που συνδυάζει όλα τα βήματα. Αντιγράψτε τον κώδικα σε ένα νέο .NET project κονσόλας και τρέξτε το.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordContentControlDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create an empty document and a DocumentBuilder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a plain‑text content control (SDT) with a tag identifier
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");

            // 3️⃣ Set placeholder text that appears when the control is empty
            sdt.PlaceholderName = "Enter name";

            // Optional: add a heading above the control
            builder.MoveToDocumentStart(); // Ensure heading appears before the control
            builder.Font.Size = 16;
            builder.Font.Bold = true;
            builder.Writeln("Employee Information");

            // Move back to the end of the control to continue writing
            builder.MoveToDocumentEnd();
            builder.Font.Size = 12;
            builder.Font.Bold = false;
            builder.Writeln(); // Adds a line break after the control

            // 4️⃣ Save the document
            string outputPath = Path.Combine(Environment.CurrentDirectory, "SdtExample.docx");
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

Η εκτέλεση του προγράμματος εκτυπώνει τη πλήρη διαδρομή του παραγόμενου αρχείου. Ανοίξτε το αρχείο στο Word για να επαληθεύσετε ότι ο **έλεγχος περιεχομένου απλού κειμένου** εμφανίζεται με το placeholder του.

## Αντιμετώπιση προβλημάτων και ειδικές περιπτώσεις

| Πρόβλημα | Αιτία | Διόρθωση |
|----------|-------|----------|
| Το κείμενο placeholder δεν εμφανίζεται | Ο έλεγχος είναι ήδη γεμάτος με κείμενο ή το έγγραφο ανοίγει σε λειτουργία που κρύβει τα placeholders. | Βεβαιωθείτε ότι το SDT είναι κενό πριν την αποθήκευση, ή ορίστε `sdt.IsShowingPlaceholder = true` (διαθέσιμο σε νεότερες εκδόσεις Aspose.Words). |
| Ο έλεγχος περιεχομένου εξαφανίζεται μετά την αποθήκευση ως PDF | Η εξαγωγή PDF δεν διατηρεί τα διαδραστικά πεδία φόρμας από προεπιλογή. | Χρησιμοποιήστε `PdfSaveOptions` με `SaveFormat.Pdf` και ορίστε `ExportDocumentStructure = true`. |
| Δεν βρέθηκε το αναγνωριστικό ετικέτας κατά την επεξεργασία | Το όνομα ετικέτας γράφτηκε λανθασμένα ή αντικαταστάθηκε. | Επαληθεύστε ότι το αναγνωριστικό που περάστηκε στη `InsertStructuredDocumentTag` ταιριάζει με το όνομα που ερωτάτε αργότερα (`MyTag`). |

## Καλές πρακτικές για τη δημιουργία εγγράφων Word προγραμματιστικά

* **Επαναχρησιμοποίηση ενός μόνο `DocumentBuilder`** ανά έγγραφο για αποφυγή περιττών κατανομών μνήμης.  
* **Ορίστε γραμματοσειρές και στυλ πριν γράψετε κείμενο**· η αλλαγή τους μετά την προσθήκη περιεχομένου μπορεί να προκαλέσει ασυνεπή μορφοποίηση.  
* **Αποδεσμεύστε μεγάλα αντικείμενα** (π.χ. `MemoryStream` αν μεταδίδετε το έγγραφο) με δηλώσεις `using`.  
* **Επικυρώστε το έγγραφο** με `doc.UpdateFields()` και `doc.UpdatePageLayout()` πριν την αποθήκευση, ειδικά όταν προσθέτετε πίνακες ή εικόνες.  

## Συμπέρασμα

Τώρα ξέρετε πώς να **δημιουργήσετε πρόγραμμα έγγραφο Word** και να **εισάγετε έλεγχο περιεχομένου απλού κειμένου** χρησιμοποιώντας το Aspose.Words for .NET. Το πλήρες παράδειγμα δείχνει την αρχικοποίηση του εγγράφου, την εισαγωγή SDT με placeholder, προαιρετικό πρόσθετο περιεχόμενο και την αποθήκευση σε αρχείο .docx.  

Από εδώ μπορείτε:

* Να αντικαταστήσετε τον έλεγχο απλού κειμένου με **rich‑text** ή **date picker** ελέγχους.  
* Να γεμίσετε το έγγραφο με δεδομένα από βάση και στη συνέχεια να εξάγετε τις τιμές που εισήχθησαν χρησιμοποιώντας `StructuredDocumentTag.GetText()`.  
* Να εξάγετε το ίδιο έγγραφο σε PDF, HTML ή OpenXML μορφές διατηρώντας τα πεδία φόρμας.

Πειραματιστείτε με διαφορετικούς τύπους ετικετών και εξερευνήστε το API του Aspose.Words για να δημιουργήσετε εξελιγμένα, συμπληρώσιμα πρότυπα Word που ενσωματώνονται άψογα στις .NET εφαρμογές σας. Καλή προγραμματιστική!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στην υλοποίηση στα δικά σας έργα.

- [Add a Combo Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Insert Text Input Form Field In Word Document](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)
- [Add a Check Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}