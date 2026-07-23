---
category: general
date: 2026-07-23
description: Δημιουργία κουμπιού εγγράφου Word χρησιμοποιώντας το Aspose.Words – βήμα‑βήμα
  οδηγός για την εισαγωγή ενός ActiveX CommandButton σε αρχείο .docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document button
- ActiveX CommandButton
- DocumentBuilder
- InsertForms2OleControl
- Aspose.Words
language: el
lastmod: 2026-07-23
og_description: 'Δημιουργήστε κουμπί εγγράφου Word με το Aspose.Words: μάθετε πώς
  να ενσωματώσετε ένα ActiveX CommandButton σε αρχείο Word σε λίγα λεπτά.'
og_image_alt: Screenshot of a Word document showing an inserted CommandButton control
og_title: Δημιουργία κουμπιού εγγράφου Word – Πλήρης οδηγός Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: create word document button using Aspose.Words – step‑by‑step guide
    to insert an ActiveX CommandButton into a .docx file.
  headline: create word document button with Aspose.Words – Full Code Example
  type: TechArticle
- description: create word document button using Aspose.Words – step‑by‑step guide
    to insert an ActiveX CommandButton into a .docx file.
  name: create word document button with Aspose.Words – Full Code Example
  steps:
  - name: '**Creates** an OLE object inside the Word file.'
    text: '**Creates** an OLE object inside the Word file.'
  - name: '**Registers** it as an ActiveX CommandButton, which Word will render as
      a clickable UI element.'
    text: '**Registers** it as an ActiveX CommandButton, which Word will render as
      a clickable UI element.'
  - name: '**Positions** it according to the rectangle we supplied.'
    text: '**Positions** it according to the rectangle we supplied.'
  - name: Launch Microsoft Word.
    text: Launch Microsoft Word.
  - name: Navigate to **File → Open** and select `CommandButton.docx`.
    text: Navigate to **File → Open** and select `CommandButton.docx`.
  - name: You should see a rectangular button labeled “CommandButton1”.
    text: You should see a rectangular button labeled “CommandButton1”.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- ActiveX
- CommandButton
title: Δημιουργία κουμπιού εγγράφου Word με το Aspose.Words – Πλήρες παράδειγμα κώδικα
url: /el/net/working-with-oleobjects-and-activex/create-word-document-button-with-aspose-words-full-code-exam/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# δημιουργία κουμπιού word εγγράφου με Aspose.Words – Πλήρης Οδηγός Προγραμματισμού

Κάποτε χρειάστηκε να **δημιουργήσετε κουμπί word εγγράφου** αλλά δεν ήξερες ποιο API να χρησιμοποιήσεις; Δεν είσαι μόνος—πολλοί προγραμματιστές συναντούν δυσκολίες όταν προσπαθούν να ενσωματώσουν διαδραστικούς ελέγχους σε ένα αρχείο .docx. Τα καλά νέα; Με το Aspose.Words for .NET μπορείς να τοποθετήσεις ένα πλήρως λειτουργικό ActiveX CommandButton σε ένα έγγραφο Word με λίγες μόνο γραμμές κώδικα.

Σε αυτό το tutorial θα περάσουμε από όλη τη διαδικασία: από τη ρύθμιση του έργου, την αρχικοποίηση ενός `DocumentBuilder`, την εισαγωγή του κουμπιού με `InsertForms2OleControl`, και τέλος την αποθήκευση του αρχείου ώστε το Word να αναγνωρίζει τον έλεγχο. Στο τέλος θα έχεις ένα έτοιμο Word αρχείο που περιέχει ένα κλικable κουμπί—χωρίς καμία ανάγκη για COM interop.

## Τι Θα Χρειαστείς

Πριν ξεκινήσουμε, βεβαιώσου ότι έχεις τα παρακάτω προαπαιτούμενα:

- **.NET 6.0** ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.6+).  
- **Aspose.Words for .NET** πακέτο NuGet (έκδοση 23.9 ή νεότερη).  
- Βασική κατανόηση της C# (θα κρατήσουμε τη σύνταξη φιλική για αρχάριους).  
- Visual Studio 2022 ή οποιοδήποτε IDE προτιμάς.

Αυτό είναι όλο—χωρίς επιπλέον αναφορές COM, χωρίς Office interop, μόνο καθαρός διαχειριζόμενος κώδικας.

---

## Βήμα 1: Ρύθμιση του Aspose.Words για **δημιουργία κουμπιού word εγγράφου**

Πρώτα απ' όλα, πρόσθεσε το πακέτο Aspose.Words στο έργο σου:

```bash
dotnet add package Aspose.Words
```

Ή, αν χρησιμοποιείς το Visual Studio NuGet UI, αναζήτησε το “Aspose.Words” και πάτησε **Install**. Αυτή η εντολή σου δίνει πρόσβαση στα `Document`, `DocumentBuilder` και τη μέθοδο `InsertForms2OleControl` που θα χρειαστούμε αργότερα.

> **Συμβουλή:** Κράτησε τα πακέτα NuGet ενημερωμένα· οι νεότερες εκδόσεις συχνά περιλαμβάνουν διορθώσεις σφαλμάτων για τη διαχείριση ActiveX.

---

## Βήμα 2: Αρχικοποίηση του **DocumentBuilder** για ένα **ActiveX CommandButton**

Τώρα δημιουργούμε ένα νέο Word έγγραφο και δημιουργούμε ένα `DocumentBuilder`. Σκέψου το `DocumentBuilder` ως πινέλο που σου επιτρέπει να σχεδιάζεις περιεχόμενο στον καμβά.

```csharp
using System;
using System.Drawing;               // For Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 2.1: Create a new empty document
        Document document = new Document();

        // Step 2.2: Initialize DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

Παρατήρησε πώς εισάγουμε το `System.Drawing`—η δομή `Rectangle` ορίζει τη θέση και το μέγεθος του κουμπιού. Εδώ θα ζήσει το **ActiveX CommandButton**.

---

## Βήμα 3: Χρήση του **InsertForms2OleControl** για **προσθήκη CommandButton**

Αυτή είναι η καρδιά του tutorial: η εισαγωγή του ίδιου του κουμπιού. Η μέθοδος `InsertForms2OleControl` δέχεται τρία ορίσματα—τύπο ελέγχου, ένα `Rectangle` και προαιρετικά ένα όνομα. Θα χρησιμοποιήσουμε το `OleControlType.CommandButton` για να ορίσουμε τον ακριβή έλεγχο που θέλουμε.

```csharp
        // Step 3: Insert an ActiveX CommandButton at (0,0) with width=100, height=30
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new Rectangle(0, 0, 100, 30));
```

Αυτή η εντολή κάνει πολλά:

1. **Δημιουργεί** ένα αντικείμενο OLE μέσα στο αρχείο Word.  
2. **Καταχωρεί** το ως ActiveX CommandButton, το οποίο το Word θα εμφανίσει ως κλικable UI στοιχείο.  
3. **Τοποθετεί** το σύμφωνα με το rectangle που δώσαμε.

Αν χρειαστεί να αλλάξεις τη λεζάντα του κουμπιού ή άλλες ιδιότητες, μπορείς να το κάνεις μετά την εισαγωγή προσπελαύνοντας το υποκείμενο `OleFormat`. Για τις περισσότερες περιπτώσεις, η προεπιλεγμένη λεζάντα (“CommandButton1”) είναι επαρκής.

---

## Βήμα 4: Αποθήκευση του Word Εγγράφου που Περιέχει το **CommandButton**

Η αποθήκευση είναι απλή—απλώς δείξε σε έναν φάκελο όπου έχεις δικαίωμα εγγραφής. Η επέκταση του αρχείου πρέπει να είναι `.docx` για να παραμείνει το κουμπί.

```csharp
        // Step 4: Save the document with the embedded button
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Όταν ανοίξεις το `CommandButton.docx` στο Microsoft Word, θα δεις ένα μικρό κουμπί στην πάνω‑αριστερή γωνία της πρώτης σελίδας. Το κλικ δεν κάνει τίποτα από μόνο του (θα απαιτούσε VBA), αλλά ο έλεγχος είναι πλήρως λειτουργικός και μπορεί να συνδεθεί αργότερα.

> **Γιατί λειτουργεί:** Το Aspose.Words γράφει το OLE stream απευθείας στο πακέτο DOCX, παρακάμπτοντας την ανάγκη του Word να δημιουργήσει τον έλεγχο κατά το χρόνο εκτέλεσης. Αυτό εγγυάται ότι το κουμπί εμφανίζεται ακριβώς εκεί που το τοποθέτησες.

---

## Βήμα 5: Επαλήθευση του Κουμπιού στο Word

Άνοιξε το παραγόμενο αρχείο:

1. Εκκίνησε το Microsoft Word.  
2. Πήγαινε στο **File → Open** και επίλεξε το `CommandButton.docx`.  
3. Θα πρέπει να δεις ένα ορθογώνιο κουμπί με την ετικέτα “CommandButton1”.  

Αν δεν βλέπεις το κουμπί, βεβαιώσου ότι είναι ενεργοποιημένη η **Design Mode** (Developer → Design Mode). Αυτό εναλλάσσει την οπτική αναπαράσταση των ActiveX ελέγχων.

---

## Βήμα 6: Προχωρημένες Επιλογές – Προσαρμογή του **ActiveX CommandButton**

Παρακάτω είναι μερικές γρήγορες ρυθμίσεις που μπορεί να σου φανούν χρήσιμες:

| Στόχος | Απόσπασμα Κώδικα |
|------|--------------|
| Αλλαγή λεζάντας | ```csharp<br/>OleFormat ole = builder.CurrentParagraph.Runs[0].OleFormat;<br/>ole.OleControlCaption = "Submit";``` |
| Ορισμός ονόματος μακροεντολής (απαιτεί υποστήριξη μακροεντολών Word) | ```csharp<br/>ole.OleControlMacroName = "MyMacro";``` |
| Αλλαγή μεγέθους μετά την εισαγωγή | ```csharp<br/>builder.MoveToDocumentEnd();<br/>builder.InsertForms2OleControl(OleControlType.CommandButton, new Rectangle(0,0,150,40));``` |

Αυτά τα αποσπάσματα δείχνουν την ευελιξία του `InsertForms2OleControl`. Μπορείς ακόμη να ενσωματώσεις άλλους ActiveX ελέγχους όπως `CheckBox` ή `ListBox` αλλάζοντας το enum `OleControlType`.

---

## Πλήρες Παράδειγμα Λειτουργίας

Ακολουθεί το ολοκληρωμένο πρόγραμμα, έτοιμο για αντιγραφή‑επικόλληση, που **δημιουργεί ένα κουμπί word εγγράφου** από το μηδέν:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class CreateWordDocumentButton
{
    static void Main()
    {
        // 1️⃣ Create a new empty document
        Document document = new Document();

        // 2️⃣ Initialize DocumentBuilder – the tool that lets us edit the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Insert an ActiveX CommandButton at position (0,0) with size 100x30
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new Rectangle(0, 0, 100, 30));

        // 4️⃣ Save the .docx file – this is where the button lives
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);

        Console.WriteLine($"✅ Document with button saved to: {outputPath}");
    }
}
```

**Αναμενόμενο αποτέλεσμα όταν τρέξεις το πρόγραμμα:**

```
✅ Document with button saved to: C:\Temp\CommandButton.docx
```

Άνοιξε το παραγόμενο αρχείο και θα δεις το κουμπί ακριβώς εκεί που τοποθέτησε ο κώδικας.

---

## Συχνά Προβλήματα & Πώς να τα Αποφύγεις

- **Λείπει η αναφορά `System.Drawing`** – Η δομή `Rectangle` βρίσκεται εκεί· χωρίς αυτήν ο μεταγλωττιστής θα παραπονεθεί.  
- **Χρήση παλαιότερης έκδοσης Aspose.Words** – Οι πρώτες εκδόσεις δεν υποστήριζαν πλήρως το `InsertForms2OleControl`. Αναβάθμισε στην πιο πρόσφατη σταθερή έκδοση.  
- **Αποθήκευση ως `.doc` αντί για `.docx`** – Το OLE stream αφαιρείται στην παλαιότερη δυαδική μορφή, με αποτέλεσμα το κουμπί να εξαφανίζεται.  
- **Εκτέλεση σε server χωρίς εγκατεστημένο Word** – Το κουμπί θα παραμείνει στο αρχείο, αλλά δεν μπορείς να το προεπισκοπήσεις χωρίς Word. Αυτό είναι αποδεκτό για αυτοματοποιημένες γραμμές παραγωγής.

---

## Επόμενα Βήματα – Επέκταση της Ροής **δημιουργία κουμπιού word εγγράφου**

Τώρα που έ掌掌 mastered τα βασικά, σκέψου τις παρακάτω ιδέες για επόμενα επίπεδα:

- **Σύνδεση VBA μακροεντολών** στο κουμπί για προσαρμοσμένη επιχειρηματική λογική.  
- **Δημιουργία πολλαπλών κουμπιών** σε βρόχο για δυναμικές φόρμες.  
- **Συνδυασμός με Aspose.PDF** για εξαγωγή του ίδιου εγγράφου σε PDF διατηρώντας την οπτική διάταξη (το κουμπί γίνεται στατική εικόνα στο PDF).  
- **


## Τι Πρέπει Να Μάθεις Στη Σύντομη Μελλοντική

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σε βοηθήσουν να κυριαρχήσεις πρόσθετες δυνατότητες του API και να εξερευνήσεις εναλλακτικές προσεγγίσεις στα δικά σου έργα.

- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}