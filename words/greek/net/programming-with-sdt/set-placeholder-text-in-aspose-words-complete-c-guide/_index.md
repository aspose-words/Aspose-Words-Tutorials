---
category: general
date: 2026-07-19
description: Ορίστε κείμενο κράτησης θέσης σε StructuredDocumentTag με το Aspose.Words.
  Μάθετε πώς να προσθέσετε έλεγχο, να μεταβείτε στον έλεγχο και να ορίσετε το χαρακτηριστικό
  ετικέτας σε C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set placeholder text
- move to control
- how to add control
- how to create sdt
- set tag attribute
language: el
lastmod: 2026-07-19
og_description: Ορίστε κείμενο κράτησης θέσης σε StructuredDocumentTag χρησιμοποιώντας
  το Aspose.Words. Ακολουθήστε αυτόν τον οδηγό βήμα‑βήμα για να προσθέσετε έλεγχο,
  να μεταβείτε στον έλεγχο και να ορίσετε την ιδιότητα της ετικέτας.
og_image_alt: Screenshot showing a Word document with placeholder text inside a content
  control created by Aspose.Words
og_title: Ορισμός κειμένου κράτησης θέσης στο Aspose.Words – Γρήγορο σεμινάριο C#
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Set placeholder text in a StructuredDocumentTag with Aspose.Words.
    Learn how to add control, move to control and set tag attribute in C#.
  headline: Set Placeholder Text in Aspose.Words – Complete C# Guide
  type: TechArticle
- description: Set placeholder text in a StructuredDocumentTag with Aspose.Words.
    Learn how to add control, move to control and set tag attribute in C#.
  name: Set Placeholder Text in Aspose.Words – Complete C# Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6+ (or .NET Framework 4.7.2) – the code works on any recent runtime.
      - Aspose.Words for .NET (NuGet package `Aspose.Words` version 23.12 or later).
      - A basic understanding of C# and Visual Studio (or your favorite IDE).'
  - name: Expected Result
    text: 'Open `SDTExample.docx` in Microsoft Word:'
  - name: What if I need a **dropdown** instead of plain text?
    text: Replace `SdtType.PlainText` with `SdtType.DropDownList` and populate the
      `ListItems` collection. The rest of the workflow—`InsertNode`, `MoveTo`, `SetTagAttribute`—remains
      the same.
  - name: Can I **set the tag attribute** after insertion?
    text: 'Absolutely. The `Tag` property can be modified at any time:'
  - name: How do I **find a control later** in a large document?
    text: Use the `Document.GetChildNodes(NodeType.StructuredDocumentTag, true)` method
      and filter by `Tag` or `Title`. This is handy when you need to replace placeholder
      text in bulk.
  - name: What if I want the placeholder to appear in **all languages**?
    text: Aspose.Words supports localized placeholder text via the `PlaceholderName`
      property. Set it to a resource string that varies per culture.
  type: HowTo
tags:
- Aspose.Words
- C#
- ContentControl
title: Ορισμός κειμένου κράτησης θέσης στο Aspose.Words – Πλήρης οδηγός C#
url: /el/net/programming-with-sdt/set-placeholder-text-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ορισμός Κειμένου Συμπλήρωσης σε Aspose.Words – Πλήρης Οδηγός C#

Έχετε αναρωτηθεί ποτέ πώς να **ορίσετε κείμενο συμπλήρωσης** μέσα σε έναν έλεγχο περιεχομένου Word χρησιμοποιώντας το Aspose.Words; Δεν είστε μόνοι. Είτε δημιουργείτε μια μηχανή παραγωγής εγγράφων είτε χρειάζεστε απλώς ένα επαναχρησιμοποιήσιμο πρότυπο, η γνώση του πώς να προσθέσετε έλεγχο, να μετακινηθείτε στον έλεγχο και να ορίσετε την ιδιότητα tag είναι απαραίτητη.

Σε αυτό το tutorial θα περάσουμε από ένα πραγματικό παράδειγμα που δείχνει ακριβώς πώς να δημιουργήσετε ένα SDT (StructuredDocumentTag), να του δώσετε tag, να ορίσετε κείμενο συμπλήρωσης και να γράψετε προεπιλεγμένο περιεχόμενο—όλα σε απλό C#. Στο τέλος θα έχετε ένα έτοιμο κομμάτι κώδικα που μπορείτε να ενσωματώσετε σε οποιοδήποτε .NET project.

## Τι Θα Μάθετε

- Πώς να **δημιουργήσετε SDT** (StructuredDocumentTag) προγραμματιστικά.
- Τον σωστό τρόπο **ορισμού κειμένου συμπλήρωσης** ώστε οι χρήστες να βλέπουν χρήσιμες προτροπές.
- Χρήση του **move to control** για τοποθέτηση του δρομέα μέσα στον νέο έλεγχο.
- Ανάθεση μιας **ιδιότητας tag** για μελλοντική ταυτοποίηση.
- Αποθήκευση του εγγράφου και επαλήθευση του αποτελέσματος.

### Προαπαιτούμενα

- .NET 6+ (ή .NET Framework 4.7.2) – ο κώδικας λειτουργεί σε οποιοδήποτε πρόσφατο runtime.
- Aspose.Words for .NET (πακέτο NuGet `Aspose.Words` έκδοση 23.12 ή νεότερη).
- Βασική κατανόηση του C# και του Visual Studio (ή του αγαπημένου σας IDE).

Δεν απαιτούνται άλλες εξωτερικές βιβλιοθήκες.

## Βήμα 1: Αρχικοποίηση του Εγγράφου και του Builder

Πρώτα απ’ όλα—δημιουργήστε ένα κενό `Document` και ένα `DocumentBuilder`. Ο builder είναι το πινέλο σας· το έγγραφο είναι ο καμβάς.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

// Create a brand‑new blank document.
Document document = new Document();

// DocumentBuilder lets us insert text, tables, and controls.
DocumentBuilder docBuilder = new DocumentBuilder(document);
```

> **Γιατί είναι σημαντικό:** Ξεκινώντας με ένα καθαρό `Document` εξασφαλίζει ότι το κείμενο συμπλήρωσης που θα ορίσουμε αργότερα δεν θα συγκρουστεί με υπάρχον περιεχόμενο.

## Βήμα 2: Δημιουργία του StructuredDocumentTag (SDT)

Τώρα θα **πώς να δημιουργήσετε sdt** – έναν έλεγχο περιεχομένου που μπορεί να περιέχει απλό κείμενο, ημερομηνίες, λίστες επιλογών κ.λπ. Σε αυτήν την περίπτωση χρειαζόμαστε έναν έλεγχο απλού κειμένου.

```csharp
// Create a plain‑text StructuredDocumentTag (content control).
StructuredDocumentTag plainTextSdt = new StructuredDocumentTag(
    document, SdtType.PlainText, true);

// Give the control a friendly name and a tag for later lookup.
plainTextSdt.Title = "CustomerName";
plainTextSdt.Tag   = "CustomerNameTag";

// Here’s the crucial part: set the placeholder text that the user sees.
plainTextSdt.PlaceholderText = "Enter name here";
```

> **Pro tip:** Η ιδιότητα `PlaceholderText` είναι αυτή που βλέπει ο χρήστης πριν πληκτρολογήσει οτιδήποτε. Είναι διαφορετική από το προεπιλεγμένο κείμενο που μπορεί να γράψετε αργότερα.

## Βήμα 3: Εισαγωγή του Ελέγχου στο Έγγραφο

Με το SDT έτοιμο, πρέπει να **πώς να προσθέσετε έλεγχο** στο έγγραφο. Η μέθοδος `InsertNode` κάνει ακριβώς αυτό.

```csharp
// Insert the content control at the current cursor position.
docBuilder.InsertNode(plainTextSdt);
```

> **Τι συμβαίνει στο παρασκήνιο;** Η `InsertNode` τοποθετεί το SDT ως παιδί της τρέχουσας παραγράφου, διατηρώντας τυχόν περιβάλλον μορφοποίηση.

## Βήμα 4: Μετακίνηση στον Έλεγχο και Εγγραφή Προεπιλεγμένου Περιεχομένου (Προαιρετικό)

Αν θέλετε να προ‑συμπληρώσετε τον έλεγχο με μια τιμή (π.χ. ένα προεπιλεγμένο όνομα πελάτη), πρώτα **μετακινηθείτε στον έλεγχο** και έπειτα γράψτε.

```csharp
// Optionally clear the placeholder and write a default name.
plainTextSdt.RemoveAllChildren();          // Remove the placeholder node.
docBuilder.MoveTo(plainTextSdt);           // Move cursor inside the SDT.
docBuilder.Write("John Doe");              // Write default text.
```

> **Γιατί αφαιρούμε το placeholder:** Το placeholder είναι οπτική ένδειξη, όχι πραγματικό περιεχόμενο του εγγράφου. Η αφαίρεσή του πριν τη γραφή εξασφαλίζει ότι το τελικό έγγραφο περιέχει μόνο το πραγματικό κείμενο.

## Βήμα 5: Αποθήκευση του Εγγράφου

Τέλος, αποθηκεύστε το αρχείο στο δίσκο. Μπορείτε επίσης να το στείλετε ως ροή σε απάντηση web‑app—απλώς αντικαταστήστε την κλήση `Save`.

```csharp
// Save the Word document to the desired location.
document.Save("C:/Temp/SDTExample.docx");
```

### Αναμενόμενο Αποτέλεσμα

Ανοίξτε το `SDTExample.docx` στο Microsoft Word:

- Θα δείτε έναν έλεγχο απλού κειμένου με τίτλο **CustomerName**.
- Ο έλεγχος εμφανίζει το κείμενο “Enter name here” ως αχνό placeholder (αν δεν γράψατε προεπιλεγμένο περιεχόμενο).
- Αν διατηρήσατε τη γραμμή `Write("John Doe")`, το “John Doe” εμφανίζεται μέσα στον έλεγχο και το placeholder εξαφανίζεται.

## Πλήρες Παράδειγμα Εργασίας

Παρακάτω είναι το πλήρες, έτοιμο για αντιγραφή‑και‑επικόλληση πρόγραμμα. Περιλαμβάνει όλα τα παραπάνω βήματα, καθώς και μερικούς ελέγχους ασφαλείας.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialise document and builder.
        Document document = new Document();
        DocumentBuilder docBuilder = new DocumentBuilder(document);

        // 2️⃣ Create a plain‑text SDT (content control).
        StructuredDocumentTag plainTextSdt = new StructuredDocumentTag(
            document, SdtType.PlainText, true);
        plainTextSdt.Title = "CustomerName";
        plainTextSdt.Tag   = "CustomerNameTag";
        plainTextSdt.PlaceholderText = "Enter name here";

        // 3️⃣ Insert the control into the document.
        docBuilder.InsertNode(plainTextSdt);

        // 4️⃣ (Optional) Move to the control and set default text.
        plainTextSdt.RemoveAllChildren();   // Clear placeholder.
        docBuilder.MoveTo(plainTextSdt);    // Move cursor inside.
        docBuilder.Write("John Doe");       // Write default value.

        // 5️⃣ Save the file.
        string outputPath = @"C:\Temp\SDTExample.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Τρέξτε το πρόγραμμα, ανοίξτε το παραγόμενο αρχείο και θα δείτε ότι όλα λειτουργούν ακριβώς όπως περιγράφηκε.

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

### Τι γίνεται αν χρειάζομαι **αναπτυσσόμενη λίστα** αντί για απλό κείμενο;

Αντικαταστήστε το `SdtType.PlainText` με `SdtType.DropDownList` και γεμίστε τη συλλογή `ListItems`. Το υπόλοιπο workflow—`InsertNode`, `MoveTo`, `SetTagAttribute`—παραμένει το ίδιο.

### Μπορώ να **ορίσω την ιδιότητα tag** μετά την εισαγωγή;

Απόλυτα. Η ιδιότητα `Tag` μπορεί να τροποποιηθεί οποιαδήποτε στιγμή:

```csharp
plainTextSdt.Tag = "NewTagValue";
```

Απλώς θυμηθείτε να αποθηκεύσετε ξανά το έγγραφο για να παραμείνει η αλλαγή.

### Πώς μπορώ να **βρω έναν έλεγχο αργότερα** σε μεγάλο έγγραφο;

Χρησιμοποιήστε τη μέθοδο `Document.GetChildNodes(NodeType.StructuredDocumentTag, true)` και φιλτράρετε κατά `Tag` ή `Title`. Αυτό είναι χρήσιμο όταν χρειάζεται να αντικαταστήσετε κείμενο συμπλήρωσης μαζικά.

```csharp
foreach (StructuredDocumentTag sdt in document.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
    if (sdt.Tag == "CustomerNameTag")
    {
        // Do something with this control.
    }
}
```

### Τι γίνεται αν θέλω το placeholder να εμφανίζεται σε **όλες τις γλώσσες**;

Το Aspose.Words υποστηρίζει τοπικοποιημένο κείμενο placeholder μέσω της ιδιότητας `PlaceholderName`. Ορίστε το σε μια συμβολοσειρά πόρου που διαφέρει ανά πολιτισμό.

## Συμβουλές & Τεχνάσματα (Pro Tips)

- **Επαναχρησιμοποίηση του ίδιου SDT** σε πολλαπλά έγγραφα με κλωνοποίηση (`plainTextSdt.Clone(true)`), έπειτα εισαγωγή του κλώνου όπου χρειάζεται.
- **Αποφύγετε διπλότυπα tags**· δημιουργούν ασάφεια στην επακόλουθη αναζήτηση. Κρατήστε τα tags μοναδικά ανά έγγραφο.
- **Συμβουλή απόδοσης:** Αν παράγετε χιλιάδες έγγραφα, επαναχρησιμοποιήστε ένα μόνο αντικείμενο `Document` ως πρότυπο και αντικαταστήστε μόνο το κείμενο συμπλήρωσης. Αυτό μειώνει το κόστος δημιουργίας αντικειμένων.

## Συμπέρασμα

Καλύψαμε όλα όσα χρειάζεστε για να **ορίσετε κείμενο συμπλήρωσης** σε ένα StructuredDocumentTag του Aspose.Words, από τη δημιουργία του ελέγχου, τη μετακίνηση σε αυτόν, τη γραφή προεπιλεγμένου περιεχομένου και την ανάθεση ιδιότητας tag. Με αυτή τη γνώση μπορείτε να δημιουργήσετε δυναμικά πρότυπα Word που καθοδηγούν τους χρήστες, επιβάλλουν κανόνες εισαγωγής δεδομένων και παραμένουν εύκολα στη συντήρηση.

Έτοιμοι για την επόμενη πρόκληση; Δοκιμάστε να αντικαταστήσετε το SDT απλού κειμένου με **επιλογέα ημερομηνίας** ή **combo box**, ή εξερευνήστε πώς να συνδέσετε SDT με πηγές δεδομένων XML για ακόμη πιο πλούσια αυτοματοποίηση εγγράφων.

Καλή προγραμματιστική δουλειά, και ας είναι τα έγγραφά σας πάντα τέλεια προτυποποιημένα!

## Τι Θα Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να κατακτήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στην υλοποίηση των δικών σας έργων.

- [Set Content Control Style](/words/hindi/net/programming-with-sdt/set-content-control-style/)
- [Set Content Control Color](/words/hindi/net/programming-with-sdt/set-content-control-color/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}