---
category: general
date: 2026-10-20
description: Ορίστε κείμενο κράτησης θέσης σε ένα έγγραφο Word χρησιμοποιώντας C#.
  Μάθετε πώς να προσθέσετε έλεγχο και να ορίσετε το placeholder γρήγορα με το Aspose.Words
  για .NET.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set placeholder text
- how to add control
- how to set placeholder
- generate word c#
language: el
lastmod: 2026-10-20
og_description: Ορίστε κείμενο κράτησης θέσης σε έγγραφο Word με C#. Αυτό το σεμινάριο
  δείχνει πώς να προσθέσετε έλεγχο, να ορίσετε κράτηση θέσης και να δημιουργήσετε
  αρχεία Word προγραμματιστικά.
og_image_alt: Screenshot of a Word document showing placeholder text created with
  C# code
og_title: Ορίστε κείμενο κράτησης θέσης σε έγγραφο Word με C# – οδηγός βήμα‑βήμα
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Set placeholder text in a Word document using C#. Learn how to add
    control and set placeholder quickly with Aspose.Words for .NET.
  headline: Set placeholder text in a Word document using C#
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for .NET is compatible with .NET Core, .NET 5, and .NET
      6+. The same code runs unchanged.
    question: Does this work with .NET Core?
  - answer: Use `sdt.SetText("Default value")` after creating the SDT. The placeholder
      disappears once a value is set.
    question: Can I set a default value in addition to the placeholder?
  - answer: 'Load the document, locate the SDT by its `Title` (`doc.GetChildNodes(NodeType.StructuredDocumentTag,
      true)`) and read `sdt.GetText()`. ## Conclusion You now know how to **set placeholder
      text** in a Word document using C#. By creating a plain‑text `StructuredDocumentTag`,
      assigning a title and place'
    question: What if I need to retrieve the entered value later?
  type: FAQPage
tags:
- C#
- Aspose.Words
- Word automation
- Content control
title: Ορισμός κειμένου κράτησης θέσης σε έγγραφο Word χρησιμοποιώντας C#
url: /el/net/programming-with-sdt/set-placeholder-text-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ορισμός κειμένου placeholder σε έγγραφο Word με C#

Αν χρειάζεστε να **ορίσετε κείμενο placeholder** σε αρχείο Microsoft Word ενώ το δημιουργείτε με C#, αυτός ο οδηγός σας δείχνει ακριβώς πώς. Θα δείτε μια σύντομη, ολοκληρωμένη λύση που προσθέτει έναν έλεγχο περιεχομένου, ορίζει το placeholder του και αποθηκεύει το έγγραφο—όλα με το Aspose.Words for .NET.

Πολλοί προγραμματιστές αναρωτιούνται **πώς να προσθέσουν έλεγχο** σε έγγραφο Word ή **πώς να ορίσουν placeholder** χωρίς να ανοίξουν το Word χειροκίνητα. Αυτό το tutorial απαντά σε αυτές τις ερωτήσεις και επίσης δείχνει έναν καθαρό τρόπο για **να δημιουργήσετε αρχεία Word C#** που είναι έτοιμα για εισαγωγή από τον χρήστη.

## Τι θα πετύχετε

* Δημιουργήστε ένα κενό έγγραφο Word προγραμματιστικά.
* Εισάγετε ένα plain‑text Structured Document Tag (SDT), το οποίο είναι το τεχνικό όνομα για έναν έλεγχο περιεχομένου.
* Αναθέστε έναν περιγραφικό τίτλο και κείμενο placeholder στο SDT.
* Αποθηκεύστε το παραγόμενο αρχείο `.docx` στο δίσκο.

Δεν απαιτούνται πρόσθετα εργαλεία πέρα από τη βιβλιοθήκη Aspose.Words και ένα περιβάλλον ανάπτυξης .NET 6 (ή νεότερο).

## Προαπαιτούμενα

* .NET 6 SDK ή νεότερο εγκατεστημένο.  
* Visual Studio 2022 (ή οποιοδήποτε IDE που υποστηρίζει .NET).  
* Πακέτο NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`).  

> **Συμβουλή:** Χρησιμοποιήστε τη δωρεάν έκδοση αξιολόγησης του Aspose.Words αν κάνετε μόνο δοκιμές· προσθέτει υδατογράφημα αλλά λειτουργεί το ίδιο με την άδεια έκδοση.

## Βήμα 1: Ρυθμίστε το έργο και εισάγετε τα namespaces

Δημιουργήστε ένα νέο έργο console και προσθέστε τις απαιτούμενες οδηγίες `using`. Αυτές φέρνουν τις βασικές κλάσεις του Aspose.Words και το namespace markup στο πεδίο ορατότητας.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // The complete solution starts here.
        }
    }
}
```

*Γιατί είναι σημαντικό αυτό το βήμα:* Η εισαγωγή του `Aspose.Words.Markup` σας δίνει πρόσβαση στα `StructuredDocumentTag`, `SdtType` και `MarkupLevel`—τα αντικείμενα που χρειάζονται για **να προσθέσετε έλεγχο** και **να ορίσετε placeholder**.

## Βήμα 2: Δημιουργήστε ένα κενό έγγραφο και έναν DocumentBuilder

Ένα `Document` αντιπροσωπεύει ολόκληρο το αρχείο Word, ενώ ένας `DocumentBuilder` παρέχει έναν βολικό κέρσορα για την εισαγωγή στοιχείων.

```csharp
// Step 2: Initialize a new empty document.
Document doc = new Document();

// DocumentBuilder starts at the beginning of the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Γιατί είναι σημαντικό αυτό το βήμα:* Ξεκινώντας με ένα καθαρό έγγραφο εξασφαλίζετε ότι το placeholder που ορίζετε εμφανίζεται ακριβώς εκεί που θέλετε, χωρίς παρεμβολή από υπάρχον περιεχόμενο.

## Βήμα 3: Δημιουργήστε τον έλεγχο περιεχομένου (Structured Document Tag)

Εδώ δημιουργούμε ένα plain‑text SDT, του δίνουμε έναν τίτλο και ορίζουμε το κείμενο placeholder που θα δει ο χρήστης όταν ο έλεγχος είναι κενός.

```csharp
// Step 3: Build a plain‑text Structured Document Tag (SDT).
StructuredDocumentTag sdt = new StructuredDocumentTag(
    doc,                     // Parent document
    SdtType.PlainText,       // Control type – plain text box
    MarkupLevel.Inline);     // Inline placement (behaves like a word)

sdt.Title = "CustomerName";                 // Logical name for the control
sdt.PlaceholderName = "Enter name here";    // Text shown when empty
```

*Γιατί είναι σημαντικό αυτό το βήμα:* Η ιδιότητα `Title` σας επιτρέπει να αναφέρετε τον έλεγχο αργότερα (π.χ., για δέσμευση δεδομένων). Το `PlaceholderName` είναι ακριβώς το **κείμενο placeholder** που θέλετε να εμφανίζεται, καθοδηγώντας τον τελικό χρήστη.

## Βήμα 4: Εισάγετε τον έλεγχο στη τρέχουσα θέση του κέρσορα

Χρησιμοποιώντας τον `DocumentBuilder`, εισάγετε το SDT στο έγγραφο εκεί που βρίσκεται αυτή τη στιγμή ο κέρσορας του builder.

```csharp
// Step 4: Insert the SDT into the document.
builder.InsertNode(sdt);
```

*Γιατί είναι σημαντικό αυτό το βήμα:* Η εισαγωγή του κόμβου συνδέει τον έλεγχο με το DOM του εγγράφου. Αν χρειαστεί να προσθέσετε πολλαπλά placeholders, μπορείτε να μετακινήσετε τον κέρσορα του builder και να επαναλάβετε αυτό το βήμα.

## Βήμα 5: Αποθηκεύστε το έγγραφο

Τέλος, γράψτε το έγγραφο στο δίσκο. Αντικαταστήστε το `YOUR_DIRECTORY` με μια πραγματική διαδρομή στον υπολογιστή σας.

```csharp
// Step 5: Save the .docx file.
string outputPath = @"C:\Temp\SDT.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Όταν ανοίξετε το `SDT.docx` στο Microsoft Word, θα δείτε ένα γκρι-σκιασμένο ενσωματωμένο πλαίσιο κειμένου που γράφει **Enter name here**. Κάνοντας κλικ μέσα στο πλαίσιο διαγράφεται το placeholder, επιτρέποντας στον χρήστη να πληκτρολογήσει ένα όνομα πελάτη.

### Αναμενόμενο αποτέλεσμα

| Τοποθεσία αρχείου | Προεπισκόπηση περιεχομένου |
|-------------------|----------------------------|
| `C:\Temp\SDT.docx` | Inline placeholder **Enter name here** μέσα σε έναν plain‑text έλεγχο περιεχομένου με τίτλο *CustomerName*. |

## Περιπτώσεις άκρων και παραλλαγές

| Κατάσταση | Συνιστώμενη προσαρμογή |
|-----------|------------------------|
| **Πολλαπλά placeholders** | Δημιουργήστε επιπλέον αντικείμενα `StructuredDocumentTag` με διαφορετικές τιμές `Title` και `PlaceholderName`, και στη συνέχεια εισάγετε το καθένα όπου χρειάζεται. |
| **Placeholder πλούσιου κειμένου** | Χρησιμοποιήστε `SdtType.RichText` αντί για `PlainText` για να επιτρέψετε μορφοποίηση μέσα στο placeholder. |
| **Έλεγχος σε επίπεδο block** | Αλλάξτε το `MarkupLevel.Inline` σε `MarkupLevel.Block` ώστε ο έλεγχος να συμπεριφέρεται σαν μια πλήρη παράγραφο. |
| **Το placeholder δεν είναι ορατό** | Βεβαιωθείτε ότι οι ρυθμίσεις προβολής του εγγράφου στο Word δεν είναι ρυθμισμένες να κρύβουν τους ελέγχους περιεχομένου (`File → Options → Advanced → Show content controls`). |
| **Αποθήκευση σε ροή** | Καλέστε `doc.Save(stream, SaveFormat.Docx)` εάν χρειάζεται να στείλετε το αρχείο μέσω HTTP αντί για εγγραφή στο δίσκο. |

## Πλήρες, εκτελέσιμο παράδειγμα

Παρακάτω βρίσκεται το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε, επικολλήσετε και εκτελέσετε. Περιλαμβάνει όλα τα παραπάνω βήματα σε μια ενιαία μέθοδο `Main`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank document.
            Document doc = new Document();

            // 2️⃣ Position a builder at the start of the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Define a plain‑text content control (SDT) with placeholder text.
            StructuredDocumentTag sdt = new StructuredDocumentTag(
                doc,
                SdtType.PlainText,
                MarkupLevel.Inline);

            sdt.Title = "CustomerName";                 // Logical identifier
            sdt.PlaceholderName = "Enter name here";    // The placeholder you see in Word

            // 4️⃣ Insert the SDT into the document.
            builder.InsertNode(sdt);

            // 5️⃣ Save the document to disk.
            string outputPath = @"C:\Temp\SDT.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document successfully saved to {outputPath}");
        }
    }
}
```

Εκτελέστε το πρόγραμμα, ανοίξτε το παραγόμενο αρχείο και θα δείτε το κείμενο placeholder έτοιμο για εισαγωγή από τον χρήστη.

## Συχνές ερωτήσεις απαντημένες

**Q: Λειτουργεί αυτό με .NET Core;**  
A: Ναι. Το Aspose.Words for .NET είναι συμβατό με .NET Core, .NET 5 και .NET 6+. Ο ίδιος κώδικας εκτελείται αμετάβλητος.

**Q: Μπορώ να ορίσω μια προεπιλεγμένη τιμή εκτός από το placeholder;**  
A: Χρησιμοποιήστε `sdt.SetText("Default value")` μετά τη δημιουργία του SDT. Το placeholder εξαφανίζεται μόλις οριστεί μια τιμή.

**Q: Τι γίνεται αν χρειαστεί να ανακτήσω την τιμή που εισήχθη αργότερα;**  
A: Φορτώστε το έγγραφο, εντοπίστε το SDT με βάση το `Title` του (`doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`) και διαβάστε `sdt.GetText()`.

## Συμπέρασμα

Τώρα γνωρίζετε πώς να **ορίσετε κείμενο placeholder** σε έγγραφο Word χρησιμοποιώντας C#. Δημιουργώντας ένα plain‑text `StructuredDocumentTag`, αναθέτοντας έναν τίτλο και placeholder, εισάγοντάς το με έναν `DocumentBuilder` και αποθηκεύοντας το αρχείο, μπορείτε να **προσθέσετε έλεγχο** και να **δημιουργήσετε αρχεία Word C#** προγραμματιστικά.

Από εδώ μπορείτε να εξερευνήσετε:

* Προσθήκη ελέγχων πλούσιου κειμένου ή λίστας επιλογών (`SdtType.RichText`, `SdtType.DropDownList`).  
* Συμπλήρωση πολλαπλών placeholders από μια βάση δεδομένων.  
* Μετατροπή του παραγόμενου `.docx` σε PDF με το Aspose.Words.

Πειραματιστείτε με διαφορετικούς τύπους ελέγχων και στυλ placeholder ώστε να ταιριάζουν στις ανάγκες της εφαρμογής σας. Καλή προγραμματιστική!

## Τι θα πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Ορισμός κειμένου Placeholder στο Aspose.Words – Πλήρης οδηγός C#](/words/english/net/programming-with-sdt/set-placeholder-text-in-aspose-words-complete-c-guide/)
- [Δημιουργία εγγράφου Word προγραμματιστικά – προσθήκη ελέγχου περιεχομένου και placeholder](/words/english/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/)
- [Πώς να προσθέσετε έλεγχο περιεχομένου και να δημιουργήσετε έγγραφο Word με Aspose – Πλήρης](/words/english/net/programming-with-sdt/how-to-add-content-control-and-create-word-document-with-asp/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}