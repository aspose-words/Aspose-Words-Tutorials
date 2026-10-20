---
category: general
date: 2026-09-11
description: Προσθέστε έλεγχο περιεχομένου σε έγγραφο Word χρησιμοποιώντας το Aspose.Words.
  Ακολουθήστε αυτόν τον οδηγό βήμα‑βήμα για να εισάγετε προγραμματιστικά μια ετικέτα
  δομημένου εγγράφου (SDT) απλού κειμένου.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add content control in word document
- StructuredDocumentTag
- DocumentBuilder
- Aspose.Words
- plain‑text SDT
- word automation
language: el
lastmod: 2026-09-11
og_description: Προσθέστε έλεγχο περιεχομένου σε έγγραφο Word με το Aspose.Words.
  Αυτός ο οδηγός σας δείχνει πώς να εισάγετε προγραμματιστικά μια απλή ετικέτα δομημένου
  εγγράφου (SDT) κειμένου και να την προσαρμόσετε.
og_image_alt: Screenshot of a Word document showing a content control placeholder
og_title: Προσθήκη ελέγχου περιεχομένου σε έγγραφο Word – πλήρης οδηγός Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Add content control in Word document using Aspose.Words. Follow this
    step‑by‑step guide to insert a plain‑text Structured Document Tag (SDT) programmatically.
  headline: Add content control in Word document with Aspose.Words
  type: TechArticle
tags:
- word
- content‑control
- csharp
- aspose
title: Προσθήκη ελέγχου περιεχομένου σε έγγραφο Word με το Aspose.Words
url: /el/java/document-manipulation/add-content-control-in-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Προσθήκη ελέγχου περιεχομένου σε έγγραφο Word με Aspose.Words

Αν χρειάζεστε να **add content control in Word document** προγραμματιστικά, αυτό το tutorial σας δείχνει ακριβώς πώς να το κάνετε με το Aspose.Words για .NET. Είτε δημιουργείτε μια υπηρεσία δημιουργίας εγγράφων είτε αυτοματοποιείτε τη δημιουργία φορμών, θα μάθετε πώς να εισάγετε ένα Structured Document Tag (SDT) απλού κειμένου και να του δώσετε έναν περιγραφικό τίτλο.

Σε αυτόν τον οδηγό θα δείτε ένα πλήρες, εκτελέσιμο παράδειγμα που καλύπτει όλες τις απαιτούμενες εισαγωγές, εξηγεί γιατί κάθε κλήση API είναι σημαντική και δείχνει πώς να επαληθεύσετε το αποτέλεσμα. Δεν απαιτούνται εξωτερικές αναφορές — απλώς αντιγράψτε τον κώδικα, εκτελέστε τον και ανοίξτε το παραγόμενο αρχείο *.docx*.

## Προαπαιτούμενα

* .NET 6.0 SDK ή νεότερο εγκατεστημένο  
* Visual Studio 2022 (ή οποιοδήποτε IDE C#)  
* Aspose.Words for .NET 23.5 ή νεότερο – μπορείτε να αποκτήσετε το δωρεάν δοκιμαστικό πακέτο NuGet  

Αυτά τα στοιχεία αποτελούν την ελάχιστη διαμόρφωση για **word automation** με το Aspose.Words.

## Βήμα 1: Ρύθμιση του έργου και εισαγωγή namespaces

Δημιουργήστε ένα νέο έργο console και προσθέστε το πακέτο Aspose.Words:

```bash
dotnet new console -n ContentControlDemo
cd ContentControlDemo
dotnet add package Aspose.Words
```

Τώρα ανοίξτε το `Program.cs` και προσθέστε τις απαιτούμενες οδηγίες `using`:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Builders;
using Aspose.Words.Markup;
```

Αυτά τα namespaces σας παρέχουν πρόσβαση στα `DocumentBuilder`, `StructuredDocumentTag` και άλλους βασικούς τύπους που απαιτούνται για **add content control in Word document**.

## Βήμα 2: Δημιουργία νέου εγγράφου και DocumentBuilder

Ένα `DocumentBuilder` είναι το κύριο σημείο εισόδου για τη δημιουργία αρχείων Word. Διατηρεί έναν κέρσορα που παρακολουθεί πού θα εισαχθεί το επόμενο στοιχείο.

```csharp
// Step 2: Initialize a new blank document and a builder
Document doc = new Document();                 // creates an empty .docx
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Γιατί είναι σημαντικό*: Το αντικείμενο `Document` αντιπροσωπεύει ολόκληρο το αρχείο Word, ενώ το `DocumentBuilder` απλοποιεί την εισαγωγή παραγράφων, πινάκων και **content controls** όπως τα Structured Document Tags.

## Βήμα 3: Εισαγωγή Structured Document Tag (SDT) απλού κειμένου

Ο πυρήνας της λύσης μας είναι η μέθοδος `insertStructuredDocumentTag`. Δημιουργεί ένα **content control** που μπορεί να περιέχει απλό κείμενο, ημερομηνίες, λίστες επιλογής κ.λπ. Εδώ χρησιμοποιούμε την τιμή enum `SdtType.PLAIN_TEXT`.

```csharp
// Step 3: Insert a plain‑text SDT at the current cursor position
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText,   // the type of control – plain‑text here
    true);               // true = the tag is shown as a placeholder in the UI
```

*Γιατί είναι σημαντικό*: Ορίζοντας `true` το control εμφανίζεται ως γκρι-ανοιχτό placeholder, το οποίο υποδεικνύει στους τελικούς χρήστες ότι πρέπει να συμπληρώσουν το πεδίο.

## Βήμα 4: Δώστε στον SDT έναν τίτλο για μελλοντική ταυτοποίηση

Ένας τίτλος (ή ετικέτα) σας επιτρέπει να εντοπίσετε το control αργότερα, για παράδειγμα όταν χρειάζεται να αντικαταστήσετε το περιεχόμενό του προγραμματιστικά.

```csharp
// Step 4: Assign a title so you can find the control later
sdt.Title = "CustomerName";
```

Ο τίτλος δεν εμφανίζεται στη διεπαφή του εγγράφου, αλλά αποθηκεύεται στο υποκείμενο XML και μπορεί να ανακτηθεί μέσω του API του Aspose.Words.

## Βήμα 5: Προσθήκη κειμένου placeholder μέσα στο SDT

Για να κάνετε το control πιο φιλικό προς τον χρήστη, εισάγετε ένα προεπιλεγμένο run που λέει στον χρήστη τι πρέπει να πληκτρολογήσει.

```csharp
// Step 5: Add placeholder text inside the SDT
Run placeholder = new Run(builder.Document, "Enter name here");
sdt.AppendChild(placeholder);
```

*Γιατί είναι σημαντικό*: Το αντικείμενο `Run` αντιπροσωπεύει ένα κομμάτι κειμένου. Προσθέτοντάς το στο SDT δημιουργείτε μια ορατή υπόδειξη που εξαφανίζεται μόλις ο χρήστης αρχίσει να πληκτρολογεί.

## Βήμα 6: Αποθήκευση του εγγράφου

Τέλος, γράψτε το έγγραφο στο δίσκο ώστε να μπορείτε να το ανοίξετε στο Microsoft Word.

```csharp
// Step 6: Save the finished document
string outPath = "ContentControlExample.docx";
doc.Save(outPath);
Console.WriteLine($"Document saved to {outPath}");
```

Όταν ανοίξετε το `ContentControlExample.docx`, θα δείτε ένα γκρι-σκιασμένο content control με τίτλο **CustomerName** και το κείμενο placeholder *Enter name here*.

## Πλήρες λειτουργικό παράδειγμα

Παρακάτω βρίσκεται το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε‑επικολλήσετε στο `Program.cs`. Περιλαμβάνει όλα τα βήματα, σχόλια και την απαραίτητη διαχείριση σφαλμάτων.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Builders;
using Aspose.Words.Markup;

namespace ContentControlDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new empty document
            Document doc = new Document();

            // Initialize the DocumentBuilder – this controls where we insert content
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a plain‑text Structured Document Tag (SDT)
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText,   // type of content control
                true);               // show as placeholder

            // Assign a title for later lookup (not visible in the UI)
            sdt.Title = "CustomerName";

            // Add placeholder text that instructs the user
            Run placeholder = new Run(builder.Document, "Enter name here");
            sdt.AppendChild(placeholder);

            // Save the document to the file system
            string outPath = "ContentControlExample.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Αναμενόμενη έξοδος

Η εκτέλεση του προγράμματος εκτυπώνει:

```
Document saved to ContentControlExample.docx
```

Ανοίγοντας το παραγόμενο αρχείο στο Word εμφανίζει ένα μόνο content control με το γκρι placeholder **Enter name here**. Το control μπορεί να επεξεργαστεί, διαγραφεί ή να προσπελαστεί προγραμματιστικά αργότερα χρησιμοποιώντας τον τίτλο του *CustomerName*.

## Συνηθισμένες παραλλαγές και ειδικές περιπτώσεις

| Σενάριο | Πώς να προσαρμόσετε τον κώδικα |
|----------|----------------------|
| **Multiple content controls** | Καλέστε το `InsertStructuredDocumentTag` επανειλημμένα, αναθέτοντας ένα μοναδικό `Title` κάθε φορά. |
| **Rich‑text content control** | Χρησιμοποιήστε το `SdtType.RichText` αντί για `PlainText`. |
| **Date picker control** | Χρησιμοποιήστε το `SdtType.Date` και προαιρετικά ορίστε το `sdt.DateDisplayFormat`. |
| **Locking the control** | Ορίστε `sdt.LockContentControl = true` για να αποτρέψετε τους χρήστες από το να το αφαιρέσουν. |
| **Finding a control later** | Χρησιμοποιήστε το `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` και φιλτράρετε κατά `Title`. |

Αυτές οι παραλλαγές δείχνουν την ευελιξία του **Aspose.Words** όταν χρειάζεται να **add content control in Word document** για διαφορετικά σενάρια συμπλήρωσης φορμών.

## Συμβουλές επαγγελματία

* **Performance** – Εάν δημιουργείτε πολλά έγγραφα σε βρόχο, επαναχρησιμοποιήστε ένα μόνο αντικείμενο `DocumentBuilder` και καλέστε `doc.Clone()` για κάθε επανάληψη ώστε να αποφύγετε την επαναλαμβανόμενη δημιουργία αντικειμένων.  
* **Styling** – Μπορείτε να εφαρμόσετε ένα `ParagraphFormat` ή `Font` στο placeholder `Run` ώστε να ταιριάζει με το οπτικό θέμα του εγγράφου σας.  
* **Validation** – Μετά την εισαγωγή ενός control, μπορείτε να ελέγξετε το `sdt.IsShowingPlaceholderText` για να επιβεβαιώσετε ότι το placeholder εμφανίζεται σωστά.  

## Συμπέρασμα

Τώρα γνωρίζετε πώς να **add content control in Word document** με το Aspose.Words, από τη δημιουργία ενός `DocumentBuilder` μέχρι την εισαγωγή ενός `StructuredDocumentTag` απλού κειμένου, την ανάθεση τίτλου και την προσθήκη κειμένου placeholder. Το πλήρες παράδειγμα μπορεί να επεκταθεί σε άλλους τύπους SDT, πολλαπλά controls και σε προχωρημένες επιλογές κλειδώματος ή στυλ.

Έτοιμοι να προχωρήσετε περαιτέρω; Εξερευνήστε αυτά τα συναφή θέματα:

* **Working with tables inside content controls** – use `DocumentBuilder.InsertTable` after the SDT.  
* **Extracting data from filled controls** – retrieve the `Sdt` node by title and read its `Text` property.  
* **Using OpenXML SDK** – an alternative approach if you prefer a free, Microsoft‑supported library.  

Πειραματιστείτε με τον κώδικα, προσαρμόστε τον στη δική σας ροή εργασίας δημιουργίας φορμών και απολαύστε τη δύναμη του προγραμματιστικού Word automation.

## Τι Θα Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά σχετικά θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Προσθήκη Περιεχομένου Χρησιμοποιώντας Document Builder στο Aspose.Words για .NET](/words/english/net/add-content-using-document-builder/)
- [Εισαγωγή Ενσωματωμένης Εικόνας σε Έγγραφο Word χρησιμοποιώντας Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Δημιουργία Εγγράφου Word με Πίνακα Χρησιμοποιώντας Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}