---
category: general
date: 2026-10-23
description: Δημιουργήστε ένα κενό έγγραφο Word με C# και μάθετε πώς να εισάγετε ελέγχους
  ActiveX, συμπεριλαμβανομένου ενός κουμπιού, χρησιμοποιώντας το Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- create activex control
- word document activex button
language: el
lastmod: 2026-10-23
og_description: Δημιουργήστε κενό έγγραφο Word με C# και μάθετε πώς να εισάγετε ελέγχους
  ActiveX, συμπεριλαμβανομένου ενός κουμπιού, χρησιμοποιώντας το Aspose.Words.
og_image_alt: Result of creating a blank Word document with an ActiveX Submit button
og_title: Δημιουργήστε ένα κενό έγγραφο Word και προσθέστε ένα κουμπί ActiveX με C#
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button in C#
  type: TechArticle
- description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  name: Create a blank Word document and add an ActiveX button in C#
  steps:
  - name: Instantiate a `Document`.
    text: Instantiate a `Document`.
  - name: Use `DocumentBuilder` to work with the file.
    text: Use `DocumentBuilder` to work with the file.
  - name: Call `InsertForms2OleControl` to **how to insert activex** controls.
    text: Call `InsertForms2OleControl` to **how to insert activex** controls.
  - name: Configure the control’s properties (**create activex control**).
    text: Configure the control’s properties (**create activex control**).
  - name: Save the file, yielding a **word document activex button** ready for VBA
      integration.
    text: Save the file, yielding a **word document activex button** ready for VBA
      integration.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Δημιουργήστε ένα κενό έγγραφο Word και προσθέστε ένα κουμπί ActiveX σε C#
url: /el/java/document-manipulation/create-a-blank-word-document-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία κενής εγγράφου Word και προσθήκη κουμπιού ActiveX σε C#

Αν χρειάζεστε να **create blank Word document** προγραμματιστικά, αυτός ο οδηγός σας δείχνει ακριβώς πώς. Θα δείτε ένα πλήρες, εκτελέσιμο παράδειγμα που δημιουργεί ένα νέο έγγραφο, εισάγει ένα ActiveX CommandButton και αποθηκεύει το αρχείο—όλα με το Aspose.Words for .NET.

Η εργασία με αρχεία Word συχνά απαιτεί περισσότερα από απλό κείμενο. Η προσθήκη ενός **ActiveX button** σας επιτρέπει να ενσωματώσετε διαδραστική λειτουργικότητα που μπορεί να χρησιμοποιηθεί σε πρότυπα με ενεργοποιημένα μακροεντολές ή λύσεις μόνο για Windows. Στο τέλος αυτού του οδηγού θα μπορείτε να εισάγετε οποιοδήποτε ActiveX control, αλλά εστιάζουμε στο πιο κοινό σενάριο: ένα **word document activex button** που υποβάλλει μια φόρμα.

## Προαπαιτούμενα

* .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.7+)
* Visual Studio 2022 (ή οποιοδήποτε IDE C#)
* **Aspose.Words for .NET** πακέτο NuGet  
  ```bash
  dotnet add package Aspose.Words
  ```
* Βασική εξοικείωση με τη σύνταξη C#

> **Συμβουλή επαγγελματία:** Το Aspose.Words είναι εμπορική βιβλιοθήκη, αλλά προσφέρει δωρεάν προσωρινή άδεια για δοκιμές. Εγκαταστήστε την άδεια νωρίς για να αποφύγετε το υδατογράφημα αξιολόγησης.

## Βήμα 1: Δημιουργία κενής εγγράφου Word με Aspose.Words

Το πρώτο βήμα είναι η δημιουργία ενός αντικειμένου `Document`. Αυτό αντιπροσωπεύει ένα κενό αρχείο `.docx` στη μνήμη.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();
```

`Document` ξεκινά χωρίς ενότητες, σελίδες ή περιεχόμενο. Είναι το καθαρό φύλλο που χρειάζεστε για σενάρια **create blank word document** όπως η δημιουργία αναφορών από το μηδέν.

## Βήμα 2: Απόκτηση DocumentBuilder για επεξεργασία του εγγράφου

`DocumentBuilder` παρέχει ένα βολικό API για προσθήκη κειμένου, εικόνων και ελέγχων. Θα το χρησιμοποιήσουμε για την τοποθέτηση του ActiveX control.

```csharp
// Obtain a DocumentBuilder tied to the blank document
DocumentBuilder builder = new DocumentBuilder(document);
```

Ο builder προσθέτει αυτόματα μια προεπιλεγμένη ενότητα και την πρώτη σελίδα, ώστε να μπορείτε να αρχίσετε να εισάγετε αντικείμενα αμέσως.

## Βήμα 3: Πώς να εισάγετε ActiveX controls στο έγγραφο

Το Aspose.Words εκθέτει τη μέθοδο `InsertForms2OleControl` για ενσωμάτωση αντικειμένων OLE/ActiveX. Η μέθοδος απαιτεί τον τύπο του ελέγχου, το πλάτος και το ύψος (σε points). Παρακάτω εισάγουμε ένα **CommandButton**—το κλασικό κουμπί φόρμας που βλέπετε σε παλαιά πρότυπα Word.

```csharp
// Insert an ActiveX CommandButton control (100 × 30 points)
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.COMMANDBUTTON, 100, 30);
```

> **Γιατί αυτό λειτουργεί:** `Forms2OleControlType.COMMANDBUTTON` λέει στο Word να δημιουργήσει ένα κουμπί που μπορεί να ανταποκριθεί σε γεγονότα κλικ όταν το έγγραφο ανοίγει σε περιβάλλον Windows που υποστηρίζει ActiveX.

## Βήμα 4: Δημιουργία ActiveX control – ορισμός ιδιοτήτων του

Τώρα δίνουμε στο κουμπί ένα προγραμματιστικό όνομα και μια ορατή λεζάντα. Αυτό είναι το μέρος του **create activex control** που συχνά παραβλέπουν οι προγραμματιστές.

```csharp
// Set the button's name (used in VBA) and the text shown to users
commandButton.Name = "btnSubmit";
commandButton.Caption = "Submit";
```

* `Name` είναι το αναγνωριστικό που θα αναφέρετε από μακροεντολές VBA (`ActiveDocument.InlineShapes("btnSubmit")`).
* `Caption` είναι η ετικέτα που εμφανίζεται στο ίδιο το κουμπί.

## Βήμα 5: Αποθήκευση του εγγράφου Word με το κουμπί ActiveX

Τέλος, γράψτε το έγγραφο στο δίσκο. Η επέκταση αρχείου πρέπει να είναι `.docx` (ή `.docm` αν σκοπεύετε να προσθέσετε μακροεντολές αργότερα). Το παράδειγμα αποθηκεύει σε έναν φάκελο placeholder—αντικαταστήστε το με τη δική σας διαδρομή.

```csharp
// Save the document containing the ActiveX button
string outputPath = @"C:\Temp\ActiveXButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Όταν ανοίξετε το παραγόμενο αρχείο στο Microsoft Word (μόνο Windows), θα δείτε ένα λειτουργικό **word document activex button** που μπορεί να συνδεθεί με κώδικα VBA.

## Πλήρες λειτουργικό παράδειγμα

Παρακάτω βρίσκεται το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε‑και‑επικολλήσετε σε ένα νέο έργο console.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXButtonDemo
{
    class Program
    {
        static void Main()
        {
            // 1. Create a blank Word document
            Document document = new Document();

            // 2. Get a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // 3. Insert an ActiveX CommandButton (100 × 30 points)
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);

            // 4. Configure the button
            commandButton.Name = "btnSubmit";
            commandButton.Caption = "Submit";

            // 5. Save the file
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Αναμενόμενο αποτέλεσμα όταν εκτελέσετε το πρόγραμμα**

```
Document saved to C:\Temp\ActiveXButton.docx
```

Ανοίξτε το παραγόμενο `ActiveXButton.docx` στο Word, και θα δείτε ένα κουμπί με την ετικέτα **Submit** τοποθετημένο στην κορυφή της πρώτης σελίδας.

## Περιπτώσεις άκρων και συχνά προβλήματα

| Situation | What to watch for | Recommendation |
|-----------|-------------------|----------------|
| Λειτουργία σε macOS ή Linux | Το ActiveX είναι τεχνολογία μόνο για Windows, έτσι το κουμπί θα εμφανιστεί ως placeholder. | Χρησιμοποιήστε τον οδηγό μόνο για πρότυπα προορισμένα σε Windows. |
| Έγγραφο ανοιγμένο στο Word Online | Τα ActiveX controls δεν υποστηρίζονται στην προβολή του προγράμματος περιήγησης. | Παρέχετε εναλλακτικό UI ή καθοδηγήστε τους χρήστες να ανοίξουν το αρχείο στην επιφάνεια εργασίας. |
| Ανάγκη αρχείου με ενεργοποιημένα μακροεντολές | Τα αρχεία `.docx` δεν μπορούν να αποθηκεύσουν κώδικα VBA. | Αποθηκεύστε ως `.docm` (`document.Save("MyFile.docm", SaveFormat.Docm)`) και προσθέστε το μακροεντολή ξεχωριστά. |
| Ασυμφωνία μεγέθους ελέγχου | Οι τιμές πλάτους/ύψους είναι σε points (1 pt ≈ 1/72 in). | Ρυθμίστε τις αριθμητικές τιμές για να πετύχετε το οπτικό μέγεθος που θέλετε. |

## Συχνές ερωτήσεις

**Πώς να εισάγετε ActiveX controls εκτός από κουμπί;**  
Χρησιμοποιήστε την ίδια μέθοδο `InsertForms2OleControl` αλλά περάστε διαφορετική τιμή του enum `Forms2OleControlType`, όπως `COMBOBOX` ή `LISTBOX`.

**Μπορώ να αλλάξω τη γραμματοσειρά ή το χρώμα του κουμπιού;**  
Η εμφάνιση του κουμπιού ActiveX καθορίζεται από την εφαρμογή-ξενιστή (Word) και το υποκείμενο θέμα των Windows. Μπορείτε να τροποποιήσετε ιδιότητες όπως `ForeColor` και `BackColor` μέσω VBA μετά το άνοιγμα του εγγράφου.

**Υπάρχει τρόπος να προσθέσετε χειριστή κλικ απευθείας από C#;**  
Όχι. Το γεγονός κλικ πρέπει να διαχειρίζεται από VBA ή ένα πρόσθετο Word, επειδή το κουμπί εκτελείται μέσα στη διαδικασία του Word, όχι στην εφαρμογή .NET σας.

## Συμπέρασμα

Τώρα ξέρετε πώς να **create blank Word document** προγραμματιστικά και να ενσωματώσετε ένα **ActiveX button** χρησιμοποιώντας το Aspose.Words for .NET. Τα βήματα που καλύφθηκαν:

1. Δημιουργήστε ένα αντικείμενο `Document`.
2. Χρησιμοποιήστε το `DocumentBuilder` για εργασία με το αρχείο.
3. Καλέστε το `InsertForms2OleControl` για **how to insert activex** controls.
4. Ρυθμίστε τις ιδιότητες του ελέγχου (**create activex control**).
5. Αποθηκεύστε το αρχείο, παράγοντας ένα **word document activex button** έτοιμο για ενσωμάτωση VBA.

Από εδώ μπορείτε να εξερευνήσετε την προσθήκη άλλων τύπων ελέγχων, τη σύνδεση μακροεντολών VBA, ή τη μετατροπή του εγγράφου σε PDF διατηρώντας το κουμπί (ως στατική εικόνα). Πειραματιστείτε με διαφορετικά μεγέθη, λεζάντες και ονόματα.

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε σε πρόσθετες δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να προσθέσετε κουμπί ActiveX σε έγγραφο Word με Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [Δημιουργία εγγράφου Word με κουμπί ActiveX – Οδηγός C#](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}