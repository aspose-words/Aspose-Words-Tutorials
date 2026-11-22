---
category: general
date: 2026-11-22
description: Ορίστε κείμενο κράτησης θέσης σε έλεγχο περιεχομένου Word με C#. Μάθετε
  πώς να δημιουργήσετε προσαρμοσμένη ετικέτα, να εισάγετε έναν έλεγχο απλού κειμένου
  και να προσθέσετε κείμενο κράτησης θέσης στην ετικέτα χρησιμοποιώντας το Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set placeholder text
- create custom tag
- how to insert content control
- add placeholder to tag
- insert plain text control
language: el
lastmod: 2026-11-22
og_description: Ορίστε κείμενο placeholder σε ένα στοιχείο ελέγχου περιεχομένου του
  Word με C#. Αυτό το σεμινάριο δείχνει πώς να δημιουργήσετε μια προσαρμοσμένη ετικέτα,
  να εισάγετε ένα στοιχείο ελέγχου απλού κειμένου και να προσθέσετε placeholder στην
  ετικέτα για καλύτερη διαδραστικότητα του εγγράφου.
og_image_alt: Screenshot showing a Word document with a content control placeholder
  text set using C#
og_title: Ορισμός κειμένου κράτησης θέσης σε έλεγχο περιεχομένου του Word – Οδηγός
  C#
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Set placeholder text in a Word content control with C#. Learn how to
    create a custom tag, insert a plain text control, and add placeholder to tag using
    Aspose.Words.
  headline: Set placeholder text in a Word content control with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Content Control
- Word Automation
title: Ορισμός κειμένου κράτησης θέσης σε έλεγχο περιεχομένου του Word με C#
url: /el/java/using-document-elements/set-placeholder-text-in-a-word-content-control-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ορισμός κειμένου placeholder σε έλεγχο περιεχομένου Word με C#

Αν χρειάζεται να **ορίσετε κείμενο placeholder** σε ένα έγγραφο Word προγραμματιστικά, αυτός ο οδηγός δείχνει ακριβώς πώς να το κάνετε. Χρησιμοποιώντας το Aspose.Words for .NET μπορείτε να δημιουργήσετε μια προσαρμοσμένη ετικέτα, να εισάγετε έναν έλεγχο απλού κειμένου και να προσθέσετε placeholder στην ετικέτα ώστε το έγγραφο να είναι έτοιμο για εισαγωγή από τον χρήστη.

Σε αυτό το tutorial θα μάθετε πώς να **δημιουργήσετε προσαρμοσμένη ετικέτα**, **πώς να εισάγετε έλεγχο περιεχομένου**, και **να προσθέσετε placeholder στην ετικέτα** διατηρώντας τον κώδικα σύντομο και έτοιμο για παραγωγή. Δεν απαιτούνται εξωτερικά εργαλεία — μόνο ένα έργο .NET και η βιβλιοθήκη Aspose.Words.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* .NET 6.0 SDK ή νεότερο εγκατεστημένο  
* Ένα έγκυρο license του Aspose.Words for .NET (ή ένα δωρεάν κλειδί αξιολόγησης)  
* Βασική εξοικείωση με C# και Visual Studio (ή οποιοδήποτε IDE προτιμάτε)  

Οι παρακάτω ενότητες υποθέτουν ότι έχετε δημιουργήσει ένα console project με όνομα `WordPlaceholderDemo`.

## Βήμα 1: Εγκατάσταση Aspose.Words

Προσθέστε το πακέτο NuGet στο έργο σας:

```bash
dotnet add package Aspose.Words
```

> **Συμβουλή:** Χρησιμοποιήστε τη σημαία `--version` για να κλειδώσετε το πακέτο στην πιο πρόσφατη σταθερή έκδοση (π.χ., `Aspose.Words.NET 24.9`).

## Βήμα 2: Φόρτωση του πηγαίου εγγράφου και δημιουργία ενός `DocumentBuilder`

Το πρώτο βήμα είναι να φορτώσετε ένα υπάρχον αρχείο `.docx` (ή να δημιουργήσετε ένα νέο κενό έγγραφο) και να δημιουργήσετε ένα `DocumentBuilder`. Ο builder σας παρέχει ένα fluent API για την εισαγωγή ελέγχων και κειμένου.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Building;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // Load an existing Word file or create a new one
            Document doc = new Document("input.docx");   // <-- replace with your path
            DocumentBuilder builder = new DocumentBuilder(doc);
```

Αυτός ο κώδικας **ετοιμάζει το σκηνικό** για την εισαγωγή ενός ελέγχου περιεχομένου. Ο `DocumentBuilder` λειτουργεί απευθείας πάνω στο αντικείμενο `doc`, έτσι οποιεσδήποτε αλλαγές κάνετε αντικατοπτρίζονται αυτόματα.

## Βήμα 3: Δημιουργία προσαρμοσμένης ετικέτας (StructuredDocumentTag)

Μια *προσαρμοσμένη ετικέτα* στο Word ονομάζεται **StructuredDocumentTag (SDT)**. Μπορείτε να τη σκεφτείτε ως έναν έλεγχο περιεχομένου που μεταφέρει ένα μοναδικό αναγνωριστικό. Η δημιουργία της αποτελεί τον πυρήνα του βήματος **create custom tag**.

```csharp
            // Insert a plain‑text StructuredDocumentTag (SDT) with a tag identifier
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");
```

Η μέθοδος `InsertStructuredDocumentTag` δέχεται δύο παραμέτρους:

1. Τον τύπο του ελέγχου (`PlainText` σε αυτήν την περίπτωση).  
2. Μια συμβολοσειρά που ταυτοποιεί μοναδικά την ετικέτα (`"MyTag"`).  

Χρησιμοποιώντας μια **προσαρμοσμένη ετικέτα**, μπορείτε αργότερα να εντοπίσετε ή να χειριστείτε τον έλεγχο προγραμματιστικά.

## Βήμα 4: Ορισμός τίτλου για προσβασιμότητα

Ένας τίτλος βελτιώνει την προσβασιμότητα και κάνει τον έλεγχο πιο εύκολο να βρεθεί στη διεπαφή του Word.

```csharp
            // Set a descriptive title (used by screen readers)
            sdt.Title = "CustomerName";
```

Η ιδιότητα `Title` είναι προαιρετική, αλλά η προσθήκη της αποτελεί καλή πρακτική όταν **προσθέτετε placeholder στην ετικέτα** για καλύτερη εμπειρία χρήστη.

## Βήμα 5: Προσθήκη κειμένου placeholder στην ετικέτα

Τώρα φτάσαμε στον κύριο στόχο: **ορισμός κειμένου placeholder**. Αυτό το κείμενο εμφανίζεται όταν ο έλεγχος είναι κενός, καθοδηγώντας τον χρήστη τι πρέπει να πληκτρολογήσει.

```csharp
            // Provide placeholder text that shows when the tag is empty
            sdt.PlaceholderText = "Enter name…";
```

Η ιδιότητα `PlaceholderText` είναι ακριβώς αυτό που χρειάζεστε για **προσθήκη placeholder στην ετικέτα**. Συμπεριφέρεται όπως η γκρι υπόδειξη που βλέπετε σε σύγχρονα πεδία φόρμας.

## Βήμα 6: Αποθήκευση του τροποποιημένου εγγράφου

Αφού διαμορφώσετε τον έλεγχο, γράψτε το έγγραφο ξανά στο δίσκο.

```csharp
            // Save the document with the new content control
            doc.Save("output.docx");   // <-- replace with your desired path
        }
    }
}
```

Όταν ανοίξετε το `output.docx` στο Microsoft Word, θα δείτε έναν έλεγχο απλού κειμένου με ετικέτα “CustomerName” και το placeholder “Enter name…”. Κάνοντας κλικ μέσα στον έλεγχο αφαιρείται το placeholder, επιτρέποντας στον χρήστη να πληκτρολογήσει.

### Αναμενόμενο αποτέλεσμα

* Ένα αρχείο Word (`output.docx`) που περιέχει έναν μοναδικό έλεγχο απλού κειμένου.  
* Ο έλεγχος εμφανίζει το placeholder “Enter name…” μέχρι ο χρήστης πληκτρολογήσει κάτι.  
* Το αναγνωριστικό ετικέτας του ελέγχου είναι `MyTag`, το οποίο μπορείτε να ερωτήσετε αργότερα με `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`.

## Βήμα 7: Πώς να εισάγετε έλεγχο περιεχομένου αλλού (προχωρημένο)

Αν χρειάζεται να **πώς να εισάγετε έλεγχο περιεχομένου** σε συγκεκριμένη θέση — π.χ., μετά από μια συγκεκριμένη παράγραφο — χρησιμοποιήστε τη μέθοδο `MoveTo` πριν εισάγετε την ετικέτα:

```csharp
            // Move the cursor to the end of the first paragraph
            builder.MoveTo(doc.FirstSection.Body.Paragraphs[0].End);
            // Insert another plain‑text control with a different tag
            StructuredDocumentTag addressTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "AddressTag");
            addressTag.Title = "CustomerAddress";
            addressTag.PlaceholderText = "Enter address…";
```

Αυτό το απόσπασμα δείχνει **εισαγωγή ελέγχου απλού κειμένου** πολλές φορές μέσα στο ίδιο έγγραφο.

## Συνηθισμένα προβλήματα και πώς να τα αποφύγετε

| Πρόβλημα | Γιατί συμβαίνει | Διόρθωση |
|----------|----------------|----------|
| Το placeholder δεν εμφανίζεται | Ο έλεγχος περιέχει ήδη κείμενο (ακόμη και ένα κενό) | Βεβαιωθείτε ότι το `sdt.Text` είναι κενό πριν ορίσετε το `PlaceholderText`. |
| Σύγκρουση αναγνωριστικού ετικέτας | Επαναχρησιμοποίηση του ίδιου ονόματος ετικέτας (`MyTag`) στο ίδιο έγγραφο | Χρησιμοποιήστε μοναδικά αναγνωριστικά για κάθε `StructuredDocumentTag`. |
| Εξαίρεση άδειας | Εκτέλεση χωρίς έγκυρη άδεια Aspose.Words | Εφαρμόστε αρχείο άδειας (`license.SetLicense("Aspose.Words.lic")`) στην αρχή του `Main`. |
| Το έγγραφο δεν αποθηκεύεται | Λάθος ή ξεχασμένο `doc.Save` ή χρήση διαδρομής μόνο για ανάγνωση | Επαληθεύστε ότι η διαδρομή εξόδου είναι εγγράψιμη και καλέστε `doc.Save`. |

## Πλήρες λειτουργικό παράδειγμα

Παρακάτω βρίσκεται το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε‑και‑επικολλήσετε στο `Program.cs`. Περιλαμβάνει όλα τα βήματα — **create custom tag**, **how to insert content control**, **add placeholder to tag**, και **insert plain text control** — σε μια ενιαία ροή.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Building;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // Optional: apply your Aspose.Words license here
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // Load the source document (or create a new one)
            Document doc = new Document("input.docx");
            DocumentBuilder builder = new DocumentBuilder(doc);

            // --------- Create custom tag ----------
            StructuredDocumentTag nameTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");
            nameTag.Title = "CustomerName";
            nameTag.PlaceholderText = "Enter name…";

            // Insert a second control after the first paragraph
            builder.MoveTo(doc.FirstSection.Body.Paragraphs[0].End);
            StructuredDocumentTag addressTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "AddressTag");
            addressTag.Title = "CustomerAddress";
            addressTag.PlaceholderText = "Enter address…";

            // Save the result
            doc.Save("output.docx");
            Console.WriteLine("Document saved with placeholder text set.");
        }
    }
}
```

Τρέξτε το πρόγραμμα με `dotnet run`. Μετά την εκτέλεση, ανοίξτε το `output.docx` για να επαληθεύσετε ότι και οι δύο έλεγχοι εμφανίζουν τα αντίστοιχα placeholders τους.

## Επόμενα βήματα

* **Προσαρμογή εμφάνισης** – Χρησιμοποιήστε το `sdt.Font` για να αλλάξετε το μέγεθος, το χρώμα ή το στυλ της γραμματοσειράς μέσα στον έλεγχο.  
* **Σύνδεση με XML δεδομένα** – Εξερευνήστε το `sdt.XmlMapping` αν χρειάζεστε τον έλεγχο να χαρτογραφήσει

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Create word document programmatically – add content control and placeholder](/words/english/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/)
- [Set Placeholder Text in Aspose.Words – Complete C# Guide](/words/english/net/programming-with-sdt/set-placeholder-text-in-aspose-words-complete-c-guide/)
- [Create new Word document and insert content control in C#](/words/english/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}