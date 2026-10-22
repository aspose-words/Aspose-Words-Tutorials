---
category: general
date: 2026-10-13
description: Μάθετε πώς να προσθέσετε ένα κουμπί εντολής προγραμματιστικά χρησιμοποιώντας
  το Aspose.Words. Αυτός ο οδηγός δείχνει επίσης πώς να δημιουργήσετε ένα κουμπί σε
  έγγραφο Word με πλήρη κώδικα C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button programmatically
- create word document button
language: el
lastmod: 2026-10-13
og_description: Προσθέστε ένα κουμπί εντολής προγραμματιστικά σε ένα έγγραφο Word
  χρησιμοποιώντας το Aspose.Words. Ακολουθήστε αυτό το πλήρες σεμινάριο για να δημιουργήσετε
  ένα κουμπί σε έγγραφο Word με C#.
og_image_alt: Screenshot of a Word document with a command button inserted programmatically
og_title: Προσθήκη κουμπιού εντολής προγραμματιστικά σε έγγραφο Word – οδηγός βήμα‑προς‑βήμα
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  headline: How to add a command button programmatically in a Word document
  type: TechArticle
- description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  name: How to add a command button programmatically in a Word document
  steps:
  - name: 'Create a new console project:'
    text: 'Create a new console project:'
  - name: 'Add the Aspose.Words NuGet package:'
    text: 'Add the Aspose.Words NuGet package:'
  - name: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
    text: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Πώς να προσθέσετε προγραμματιστικά ένα κουμπί εντολής σε έγγραφο Word
url: /el/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να προσθέσετε ένα κουμπί εντολής προγραμματιστικά σε ένα έγγραφο Word  

Αν χρειάζεται να **προσθέσετε ένα κουμπί εντολής προγραμματιστικά**, το Aspose.Words παρέχει ένα καθαρό API που σας επιτρέπει να ενσωματώσετε ελέγχους φόρμας OLE απευθείας σε ένα αρχείο .docx. Αυτό το tutorial σας καθοδηγεί βήμα-βήμα για να **δημιουργήσετε ένα κουμπί σε έγγραφο Word** που συμπεριφέρεται όπως ένα κανονικό κουμπί φόρμας όταν το έγγραφο ανοίγει στο Microsoft Word.  

Θα μάθετε πώς να ρυθμίσετε το περιβάλλον ανάπτυξης, να εισάγετε το κουμπί, να διαμορφώσετε τις ιδιότητές του και να επαληθεύσετε το αποτέλεσμα. Δεν απαιτούνται εξωτερικά εργαλεία—μόνο ένα έργο .NET και η βιβλιοθήκη Aspose.Words for .NET.  

## Προαπαιτούμενα  

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:  

* .NET 6.0 SDK ή νεότερη έκδοση εγκατεστημένη.  
* Μια πρόσφατη έκδοση του Aspose.Words for .NET (τα παραδείγματα χρησιμοποιούν 23.12, αλλά οποιαδήποτε έκδοση 22.x+ λειτουργεί).  
* Ένα IDE όπως το Visual Studio 2022 ή το Visual Studio Code.  

Ο κώδικας εκτελείται σε Windows, macOS και Linux επειδή το Aspose.Words είναι ανεξάρτητο από την πλατφόρμα.  

## Βήμα 1: Ρυθμίστε το έργο και αναφέρετε το Aspose.Words  

1. Δημιουργήστε ένα νέο κονσολικό έργο:  

   ```bash
   dotnet new console -n WordButtonDemo
   cd WordButtonDemo
   ```  

2. Προσθέστε το πακέτο NuGet Aspose.Words:  

   ```bash
   dotnet add package Aspose.Words
   ```  

3. Ανοίξτε το **Program.cs** και αντικαταστήστε το περιεχόμενό του με το σκελετό που φαίνεται στα επόμενα βήματα.  

Η ρύθμιση του έργου με αυτόν τον τρόπο εξασφαλίζει ότι ο μεταγλωττιστής μπορεί να εντοπίσει τα namespaces `Aspose.Words` και `Aspose.Words.Drawing.Forms` που απαιτούνται για τους ελέγχους φόρμας.  

## Βήμα 2: Αρχικοποιήστε ένα κενό έγγραφο και ένα DocumentBuilder  

Η κλάση `Document` αντιπροσωπεύει ολόκληρο το αρχείο Word, ενώ το `DocumentBuilder` παρέχει ένα ευέλικτο API για την προσθήκη περιεχομένου.  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;
using System.Drawing;   // required for RectangleF

// Create an empty document.
Document doc = new Document();

// Create a builder linked to the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```  

*Γιατί αυτό το βήμα είναι σημαντικό* – Χωρίς ένα `DocumentBuilder` δεν μπορείτε να τοποθετήσετε το κουμπί ακριβώς στη σελίδα. Ο builder επίσης σέβεται τη τρέχουσα θέση του κέρσορα, καθιστώντας εύκολη την εισαγωγή πολλαπλών ελέγχων αργότερα.  

## Βήμα 3: Εισαγάγετε τον έλεγχο OLE κουμπιού εντολής  

Το Aspose.Words αντιμετωπίζει ένα κουμπί εντολής ως έλεγχο OLE τύπου `ControlType.CommandButton`. Ορίζετε τη θέση και το μέγεθός του με ένα `RectangleF` που μετράται σε points (1 point = 1/72 ίντσα).  

```csharp
// Define the button rectangle: X=100, Y=150, Width=120, Height=30 (points)
RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

// Insert the command button at the current cursor position.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    buttonRect);
```  

**Κύρια σημεία**  

* Η αρχή του ορθογωνίου (X, Y) είναι σχετική με την επάνω‑αριστερή γωνία της σελίδας.  
* Η αλλαγή του `Width` ή `Height` τροποποιεί το οπτικό μέγεθος του κουμπιού.  
* Η μέθοδος `InsertForms2OleControl` επιστρέφει ένα αντικείμενο `Forms2OleControl` που μπορείτε να διαμορφώσετε περαιτέρω.  

## Βήμα 4: Διαμορφώστε το όνομα και τη λεζάντα του κουμπιού  

Το **name** χρησιμοποιείται από τη μηχανή μακροεντολών του Word για την ταυτοποίηση του ελέγχου, ενώ το **caption** είναι το κείμενο που βλέπει ο χρήστης.  

```csharp
// Set a unique identifier for the button.
commandButton.Name = "cmdSubmit";

// Set the text displayed on the button.
commandButton.Caption = "Submit";
```  

Αν σκοπεύετε να προσθέσετε VBA μακροεντολές αργότερα, χρησιμοποιήστε ένα περιγραφικό όνομα επειδή ο καταγραφέας μακροεντολών του Word αναφέρεται σε αυτήν την ιδιότητα.  

## Βήμα 5: (Προαιρετικό) Αποθηκεύστε το έγγραφο και επαληθεύστε το αποτέλεσμα  

Η αποθήκευση του αρχείου σας επιτρέπει να το ανοίξετε στο Microsoft Word για να επιβεβαιώσετε ότι το κουμπί εμφανίζεται και λειτουργεί.  

```csharp
// Save the document to the output folder.
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButtonDemo.docx");
doc.Save(outputPath);

Console.WriteLine($"Document saved to: {outputPath}");
```  

Όταν ανοίξετε το *CommandButtonDemo.docx* στο Word, θα πρέπει να δείτε ένα κουμπί με την ετικέτα **Submit** τοποθετημένο περίπου 1.4 ίντσες από το αριστερό περιθώριο και 2.1 ίντσες από την κορυφή της σελίδας. Το κλικ στο κουμπί δεν κάνει τίποτα από προεπιλογή επειδή δεν έχει συνδεθεί μακροεντολή, αλλά ο οπτικός έλεγχος είναι πλήρως λειτουργικός.  

## Βήμα 6: Περιπτώσεις άκρων και κοινά προβλήματα  

| Κατάσταση | Σε τι πρέπει να προσέξετε | Προτεινόμενη διόρθωση |
|-----------|---------------------------|-----------------------|
| **Το κουμπί επικαλύπτει υπάρχον κείμενο** | Το ορθογώνιο μπορεί να διασταυρώνεται με μια παράγραφο, προκαλώντας προβλήματα διάταξης. | Εισάγετε το κουμπί μετά την κλήση του `builder.Writeln()` για να μετακινήσετε τον κέρσορα σε νέα γραμμή, ή προσαρμόστε τη συντεταγμένη `Y`. |
| **Το έγγραφο ανοίγει με προειδοποίηση** | Ορισμένες εκδόσεις του Word επισημαίνουν ελέγχους OLE που δεν έχουν συνδεδεμένο πρόγραμμα. | Βεβαιωθείτε ότι ο τύπος ελέγχου είναι `CommandButton`; το Word το θεωρεί ως τυπικό στοιχείο φόρμας και δεν απαιτεί εξωτερικό πρόγραμμα. |
| **Εκτέλεση σε Linux με περιβάλλον headless** | Το Word δεν μπορεί να εκκινηθεί για δοκιμή του UI, αλλά το αρχείο παραμένει έγκυρο. | Χρησιμοποιήστε μια μονάδα δοκιμής που διαβάζει τις ιδιότητες του ελέγχου (`commandButton.Name`, `commandButton.Caption`) για να επαληθεύσετε ότι έχουν οριστεί σωστά. |
| **Απαιτούνται πολλαπλά κουμπιά** | Η επαναχρησιμοποίηση του ίδιου `DocumentBuilder` χωρίς μετακίνηση του κέρσορα προσθέτει το κουμπί πάνω στο προηγούμενο. | Καλέστε `builder.MoveToDocumentEnd()` ή προσαρμόστε την τιμή `Y` του ορθογωνίου πριν από κάθε εισαγωγή. |

Η αντιμετώπιση αυτών των περιπτώσεων άκρων νωρίς εξοικονομεί χρόνο όταν κλιμακώνετε τη λύση σε πλήρεις φόρμες με δεκάδες ελέγχους.  

## Βήμα 7: Πλήρες, εκτελέσιμο παράδειγμα  

Παρακάτω υπάρχει ένα αυτόνομο πρόγραμμα που μπορείτε να αντιγράψετε, επικολλήσετε και εκτελέσετε χωρίς τροποποίηση (εκτός από την επαναφορά του NuGet).  

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

namespace WordButtonDemo
{
    class Program
    {
        static void Main()
        {
            // 1. Create a new empty document.
            Document doc = new Document();

            // 2. Create a DocumentBuilder to work with the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Define the button rectangle (position + size).
            RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

            // 4. Insert the command button OLE control.
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                buttonRect);

            // 5. Set identifying properties.
            commandButton.Name = "cmdSubmit";
            commandButton.Caption = "Submit";

            // 6. Save the document.
            string outputPath = Path.Combine(
                Environment.CurrentDirectory,
                "CommandButtonDemo.docx");
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

**Αναμενόμενη έξοδος**  

Η εκτέλεση του προγράμματος εκτυπώνει μια διαδρομή παρόμοια με:  

```
Document saved to: C:\Path\To\WordButtonDemo\CommandButtonDemo.docx
```  

Ανοίγοντας το παραγόμενο *CommandButtonDemo.docx* εμφανίζεται ένα μόνο κουμπί **Submit** τοποθετημένο στις συντεταγμένες που ορίστηκαν στον κώδικα. Δεν εμφανίζονται επιπλέον στοιχεία UI, επιβεβαιώνοντας ότι η διαδικασία **προσθήκης κουμπιού εντολής προγραμματιστικά** ολοκληρώθηκε με επιτυχία.  

## Συμπέρασμα  

Τώρα γνωρίζετε πώς να **προσθέσετε ένα κουμπί εντολής προγραμματιστικά** σε ένα έγγραφο Word χρησιμοποιώντας το Aspose.Words, και επίσης καταλαβαίνετε πώς να **δημιουργήσετε ένα κουμπί σε έγγραφο Word** που μπορεί αργότερα να συνδεθεί με μακροεντολές VBA ή εξωτερικά εργαλεία αυτοματοποίησης. Η διαδικασία αποτελείται από την αρχικοποίηση ενός εγγράφου, την εισαγωγή ενός ελέγχου OLE `CommandButton`, τη διαμόρφωση των ιδιοτήτων του και την αποθήκευση του αρχείου.  

Από εδώ μπορείτε:  

* Προσθέστε περισσότερους ελέγχους (checkboxes, πεδία κειμένου) επαναλαμβάνοντας το βήμα 3 με διαφορετικές τιμές `ControlType`.  
* Συνδέστε μακροεντολές VBA στο κουμπί για να εκτελεί ενέργειες όπως αποθήκευση φόρμας ή αποστολή email.  
* Δημιουργήστε ολόκληρες φόρμες δυναμικά επαναλαμβάνοντας μια συλλογή πεδίων που καθορίζεται από δεδομένα.  

Πειραματιστείτε με τις συντεταγμένες του ορθογωνίου και τη λεζάντα του κουμπιού για να ταιριάζουν με το UI design σας. Καλή προγραμματιστική!  

## Τι Θα Μάθετε Στη Σειρά;  

Τα παρακάτω tutorials καλύπτουν στενά σχετικούς τομείς που επεκτείνουν τις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα-βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Προσθήκη πεδίου φόρμας Combo Box σε έγγραφο Word με Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Προσθήκη πεδίου φόρμας Check Box σε έγγραφο Word με Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)
- [Δημιουργία κενής λέξης εγγράφου με Aspose.Words – Οδηγός βήμα‑βήμα](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}