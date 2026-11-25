---
category: general
date: 2026-11-25
description: Μάθετε πώς να δημιουργήσετε ένα έγγραφο Word, να προσθέσετε σχήμα ορθογωνίου,
  να συνοψίσετε το έγγραφο με AI, να μεταφράσετε κείμενο χρησιμοποιώντας AI και να
  αποθηκεύσετε το έγγραφο ως DOCX χρησιμοποιώντας το Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- add rectangle shape
- summarize document with ai
- save document as docx
- translate text using ai
language: el
lastmod: 2026-11-25
og_description: Δημιουργήστε ένα έγγραφο Word, προσθέστε σχήμα ορθογωνίου, συνοψίστε
  το έγγραφο με AI, μεταφράστε το κείμενο χρησιμοποιώντας AI και αποθηκεύστε το ως
  DOCX—όλα σε έναν ενιαίο οδηγό C#.
og_image_alt: Screenshot showing a generated Word document with a rectangle shape
  and AI‑generated summary
og_title: Δημιουργήστε ένα έγγραφο Word με σχήματα, περίληψη AI και μετάφραση σε C#
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to create a Word document, add rectangle shape, summarize
    document with AI, translate text using AI, and save document as DOCX using Aspose.Words.
  headline: How to create a Word document with shapes, AI summarization, and translation
    in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- AI integration
title: Πώς να δημιουργήσετε ένα έγγραφο Word με σχήματα, σύνοψη AI και μετάφραση σε
  C#
url: /el/net/ai-powered-document-processing/how-to-create-a-word-document-with-shapes-ai-summarization-a/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε ένα έγγραφο Word με σχήματα, σύνοψη AI και μετάφραση σε C#

Αν χρειάζεται να **δημιουργήσετε ένα έγγραφο Word** προγραμματιστικά, αυτό το οδηγό σας δείχνει ακριβώς πώς. Χρησιμοποιώντας το Aspose.Words for .NET, θα μάθετε να **προσθέτετε σχήμα ορθογωνίου**, να καλέσετε μια υπηρεσία AI για **σύνοψη του εγγράφου με AI**, να **μεταφράσετε κείμενο με AI**, και τέλος να **αποθηκεύσετε το έγγραφο ως DOCX**.

Πολλοί προγραμματιστές δυσκολεύονται να συνδυάσουν την αυτοματοποίηση εγγράφων με σύγχρονες δυνατότητες AI. Στο τέλος αυτού του tutorial θα έχετε ένα ενιαίο, αυτόνομο έργο C# που παράγει ένα πλήρως μορφοποιημένο αρχείο *.docx*, με οπτικό σχήμα, σύνοψη που δημιουργήθηκε από AI και πολυγλωσσικό περιεχόμενο.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

- .NET 6.0 SDK ή νεότερη έκδοση εγκατεστημένη  
- Visual Studio 2022 (ή οποιοδήποτε IDE για C#)  
- Άδεια Aspose.Words for .NET (ή δωρεάν κλειδί αξιολόγησης)  
- Πρόσβαση στο Internet για τις κλήσεις σύνοψης και μετάφρασης AI  

Δεν απαιτούνται επιπλέον πακέτα NuGet εκτός από `Aspose.Words` και `Aspose.Words.AI`.

## Βήμα 1: Ρύθμιση του έργου και προσθήκη απαιτούμενων πακέτων

Δημιουργήστε ένα νέο console project και προσθέστε τις βιβλιοθήκες Aspose.Words.

```bash
dotnet new console -n WordAiDemo
cd WordAiDemo
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

> **Συμβουλή:** Αν σκοπεύετε να χρησιμοποιήσετε τη λειτουργία αξιολόγησης, καλέστε `Aspose.Words.License.SetLicense("Aspose.Words.lic");` νωρίς στο `Main` για να αποφύγετε τα υδατογραφήματα.

## Βήμα 2: Αρχικοποίηση του εγγράφου – ο πυρήνας της **δημιουργίας word εγγράφου**

Η πρώτη ενεργή γραμμή κώδικα δημιουργεί ένα νέο αντικείμενο **Word document**. Αυτό το αντικείμενο είναι ο καμβάς για όλες τις επόμενες λειτουργίες.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.AI;          // AI‑powered features
using Aspose.Words.Charts;     // chart‑related properties
using System;

class Program
{
    static void Main()
    {
        // Create a new, empty Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

Ο `DocumentBuilder` απλοποιεί την εισαγωγή κειμένου, σχημάτων και ελέγχων χωρίς να χρειάζεται χειρισμός χαμηλού επιπέδου δέντρων κόμβων.

## Βήμα 3: **Προσθήκη σχήματος ορθογωνίου** στο έγγραφο

Ένα σχήμα ορθογωνίου μπορεί να χρησιμοποιηθεί ως οπτικός χώρος κράτησης, φόντο ετικέτας ή απλό γραφικό. Πρώτα δημιουργούμε ένα `GroupShape`, έπειτα εισάγουμε ένα `Rectangle` μέσα σε αυτό.

```csharp
        // Step 3: Insert a group shape and add a rectangle inside it
        GroupShape groupShape = new GroupShape(document);
        builder.InsertNode(groupShape);
        builder.MoveTo(groupShape);
        builder.InsertShape(ShapeType.Rectangle, 100, 50); // width=100pt, height=50pt
```

Το ορθογώνιο έχει πλάτος 100 points και ύψος 50 points. Επειδή βρίσκεται μέσα σε `GroupShape`, μπορείτε αργότερα να προσθέσετε περισσότερα στοιχεία (π.χ. πλαίσια κειμένου) χωρίς να ανησυχείτε για συγκρούσεις διάταξης.

## Βήμα 4: Εισαγωγή StructuredDocumentTag (SDT) απλού κειμένου

Τα αντικείμενα StructuredDocumentTag είναι χρήσιμα για ελέγχους περιεχομένου που μπορούν αργότερα να δεσμευτούν σε πηγές δεδομένων.

```csharp
        // Step 4: Add a plain‑text StructuredDocumentTag (SDT) to the document
        StructuredDocumentTag plainTextTag = new StructuredDocumentTag(document, SdtType.PlainText, true);
        builder.InsertNode(plainTextTag);
```

Η σημαία `true` χαρακτηρίζει την ετικέτα ως **επαναλαμβανόμενο** έλεγχο, κάτι που είναι χρήσιμο για πρότυπα.

## Βήμα 5: Προσθήκη ελέγχου ActiveX CommandButton (προαιρετικό UI)

Αν το παραγόμενο έγγραφο θα χρησιμοποιηθεί σε περιβάλλον που υποστηρίζει ActiveX, μπορείτε να ενσωματώσετε ένα κουμπί.

```csharp
        // Step 5: Insert an ActiveX CommandButton control (Forms2 OLE control)
        builder.InsertForms2OleControl(OleControlType.CommandButton);
```

Αυτό το βήμα είναι προαιρετικό· μπορείτε να το αφαιρέσετε εάν το κοινό-στόχος σας δεν αλληλεπιδρά ποτέ με το έγγραφο σε περιβάλλον Windows.

## Βήμα 6: **Σύνοψη εγγράφου με AI**

Το Aspose.Words.AI παρέχει ένα βολικό wrapper γύρω από υπηρεσίες μεγάλων γλωσσικών μοντέλων. Εδώ καλούμε το `DocumentSummarizer.Summarize` με το backend του OpenAI.

```csharp
        // Step 6: Summarize the document content using an AI service
        string summary = DocumentSummarizer.Summarize(document, SummarizerOptions.OpenAI);
        Console.WriteLine("Document summary:");
        Console.WriteLine(summary);
```

Η μέθοδος αναλύει το τρέχον δέντρο κόμβων, εξάγει τις πιο σχετικές προτάσεις και επιστρέφει μια σύντομη παράγραφο. Αυτός είναι ο πυρήνας της λειτουργίας **summarize document with AI**.

## Βήμα 7: **Μετάφραση κειμένου με AI**

Στη συνέχεια δείχνουμε πώς να μεταφράσουμε μια δείγμα συμβολοσειράς από τα Αγγλικά στα Γαλλικά. Η μέθοδος `Translator.Translate` καλεί εσωτερικά ένα μοντέλο AI της Google.

```csharp
        // Step 7: Translate a sample paragraph to French using Google AI
        string translatedParagraph = Translator.Translate("Hello world", Language.French);
        Console.WriteLine("\nTranslated paragraph (English → French):");
        Console.WriteLine(translatedParagraph);
```

Μπορείτε να αντικαταστήσετε το `Language.French` με οποιαδήποτε υποστηριζόμενη τιμή enum γλώσσας, επιτρέποντας τη δημιουργία πολυγλωσσικού εγγράφου επί τόπου.

## Βήμα 8: **Αποθήκευση εγγράφου ως DOCX**

Τέλος, αποθηκεύστε το επεξεργασμένο έγγραφο στο δίσκο. Η μέθοδος `Save` γράφει αυτόματα ένα αρχείο *.docx* όταν καθορίζετε την επέκταση `.docx`.

```csharp
        // Step 8: Save the modified document
        document.Save("Result.docx"); // **save document as docx**
        Console.WriteLine("\nDocument saved as Result.docx");
    }
}
```

Το αρχείο `Result.docx` περιέχει τώρα:

- Ένα σχήμα ορθογωνίου μέσα σε group shape  
- Έναν έλεγχο περιεχομένου απλού κειμένου (SDT)  
- Ένα ActiveX CommandButton (αν διατηρήσατε το Βήμα 5)  
- Μια παράγραφο σύνοψης που δημιουργήθηκε από AI  
- Μια γαλλική μετάφραση του “Hello world”

Μπορείτε να ανοίξετε το αρχείο στο Microsoft Word για να επαληθεύσετε κάθε στοιχείο.

## Πλήρης κώδικας πηγής

Παρακάτω είναι το πλήρες, έτοιμο‑για‑εκτέλεση πρόγραμμα. Αντιγράψτε το στο `Program.cs` και τρέξτε `dotnet run`.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.AI;          // AI‑powered features
using Aspose.Words.Charts;     // chart‑related properties
using System;

class Program
{
    static void Main()
    {
        // 1. Create a new Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Insert a group shape and add a rectangle inside it
        GroupShape groupShape = new GroupShape(document);
        builder.InsertNode(groupShape);
        builder.MoveTo(groupShape);
        builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // 3. Add a plain‑text StructuredDocumentTag (SDT)
        StructuredDocumentTag plainTextTag = new StructuredDocumentTag(document, SdtType.PlainText, true);
        builder.InsertNode(plainTextTag);

        // 4. Insert an ActiveX CommandButton (optional)
        builder.InsertForms2OleControl(OleControlType.CommandButton);

        // 5. Summarize the document using AI
        string summary = DocumentSummarizer.Summarize(document, SummarizerOptions.OpenAI);
        Console.WriteLine("Document summary:");
        Console.WriteLine(summary);

        // 6. Translate a paragraph to French using AI
        string translatedParagraph = Translator.Translate("Hello world", Language.French);
        Console.WriteLine("\nTranslated paragraph (English → French):");
        Console.WriteLine(translatedParagraph);

        // 7. Save the document as DOCX
        document.Save("Result.docx");
        Console.WriteLine("\nDocument saved as Result.docx");
    }
}
```

### Αναμενόμενη έξοδος

```
Document summary:
[AI‑generated concise summary of the document’s current content]

Translated paragraph (English → French):
Bonjour le monde

Document saved as Result.docx
```

Όταν ανοίξετε το `Result.docx`, θα δείτε το σχήμα ορθογωνίου κοντά στην κορυφή, το placeholder SDT, το κουμπί, την παράγραφο σύνοψης και τη γαλλική μετάφραση που έχει εισαχθεί ως απλό κείμενο.

## Συμπέρασμα

Τώρα ξέρετε πώς να **δημιουργήσετε ένα έγγραφο Word** από το μηδέν, να **προσθέσετε σχήμα ορθογωνίου**, να **συνοψίσετε το έγγραφο με AI**, να **μεταφράσετε κείμενο με AI**, και να **αποθηκεύσετε το έγγραφο ως DOCX**—όλα με λίγες περιεκτικές γραμμές C#. Αυτό το μοτίβο κλιμακώνεται: μπορείτε να αντικαταστήσετε τις σκληρά κωδικοποιημένες συμβολοσειρές με δυναμικά δεδομένα, να προσθέσετε περισσότερα σχήματα ή διαγράμματα, και να αλλάξετε τον πάροχο AI προσαρμόζοντας τις παραμέτρους `SummarizerOptions` ή `Translator`.

### Τι ακολουθεί;

- Εξερευνήστε παραλλαγές **add rectangle shape**: αλλάξτε χρώμα γεμίσματος, στυλ γραμμής ή προσθέστε κείμενο μέσα στο σχήμα.  
- Χρησιμοποιήστε **summarize document with AI** σε μεγαλύτερα έγγραφα για αυτόματη δημιουργία εκτελεστικών περιλήψεων.  
- Επεκτείνετε **translate text using AI** για επεξεργασία ολόκληρων παραγράφων ή πινάκων σε πολυγλωσσικές αναφορές.  
- Συνδυάστε τα API δημιουργίας διαγραμμάτων του Aspose.Words για ενσωμάτωση οπτικών δεδομένων μαζί με τις AI‑γενόμενες πληροφορίες.  

Πειραματιστείτε ελεύθερα και μοιραστείτε τα αποτελέσματά σας στα σχόλια ή στο GitHub. Καλό κώδικα!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Create a blank word document and add a rectangle shape](/words/english/net/programming-with-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Add Text Watermark in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-watermark/add-text-watermark/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}