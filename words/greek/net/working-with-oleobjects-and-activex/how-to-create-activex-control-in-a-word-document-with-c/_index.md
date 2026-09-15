---
category: general
date: 2026-09-14
description: Δημιουργήστε έλεγχο ActiveX σε έγγραφο Word με C#. Μάθετε πώς να εισάγετε
  ActiveX, να προσθέσετε διαδραστικό κουμπί και να δημιουργήσετε το αρχείο .docx προγραμματιστικά.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- how to insert activex
- add interactive button
- create word document
- create button with code
language: el
lastmod: 2026-09-14
og_description: Δημιουργήστε έλεγχο ActiveX σε έγγραφο Word με C#. Ακολουθήστε αυτό
  το πλήρες παράδειγμα για να εισαγάγετε ActiveX, να προσθέσετε διαδραστικό κουμπί
  και να αποθηκεύσετε το αρχείο.
og_image_alt: Screenshot of a Word document containing a newly created ActiveX CommandButton
og_title: Δημιουργία ελέγχου ActiveX στο Word με χρήση C# – οδηγός βήμα‑προς‑βήμα
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Create ActiveX control in a Word document with C#. Learn how to insert
    ActiveX, add interactive button, and generate the .docx file programmatically.
  headline: How to create ActiveX control in a Word document with C#
  type: TechArticle
tags:
- ActiveX
- C#
- Word automation
title: Πώς να δημιουργήσετε έλεγχο ActiveX σε έγγραφο Word με C#
url: /el/net/working-with-oleobjects-and-activex/how-to-create-activex-control-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε έλεγχο ActiveX σε έγγραφο Word με C#

Αν χρειάζεται να **δημιουργήσετε έλεγχο ActiveX** μέσα σε αρχείο Microsoft Word, αυτός ο οδηγός σας παρουσιάζει μια πλήρη, έτοιμη‑για‑εκτέλεση λύση. Θα δείτε ακριβώς πώς να εισάγετε ένα ActiveX CommandButton, να ορίσετε τις ιδιότητές του και να αποθηκεύσετε το προκύπτον `.docx` αρχείο χρησιμοποιώντας μόνο κώδικα C#.

Η προσθήκη ενός διαδραστικού κουμπιού σε έγγραφο Word είναι συχνή απαίτηση όταν θέλετε οι τελικοί χρήστες να ενεργοποιούν μακροεντολές ή προσαρμοσμένη λογική απευθείας από το UI του εγγράφου. Το παρακάτω παράδειγμα δείχνει **πώς να εισάγετε ActiveX** χωρίς εξωτερικά εργαλεία, και καλύπτει επίσης **πώς να δημιουργήσετε έγγραφο Word** προγραμματιστικά.

Στο τέλος αυτού του tutorial θα μπορείτε να **δημιουργήσετε κουμπί με κώδικα**, να προσαρμόσετε τη λεζάντα του και να παράγετε ένα φορητό αρχείο Word που διατηρεί τον έλεγχο ActiveX.

## Προαπαιτούμενα

- .NET 6.0 ή νεότερο (η βιβλιοθήκη Aspose.Words for .NET λειτουργεί με .NET Core και .NET Framework)
- Αναφορά στο πακέτο NuGet `Aspose.Words`  
  ```bash
  dotnet add package Aspose.Words
  ```
- Βασικές γνώσεις C# και αντικειμενοστραφούς προγραμματισμού

## Βήμα 1: Ρύθμιση του έργου και εισαγωγή ονομάτων χώρου

Δημιουργήστε ένα νέο έργο console (ή ενσωματώστε τον κώδικα σε οποιαδήποτε υπάρχουσα εφαρμογή C#). Εισάγετε τα απαιτούμενα namespaces ώστε ο μεταγλωττιστής να μπορεί να εντοπίσει τις κλάσεις επεξεργασίας Word.

```csharp
using System;
using System.Drawing;               // Provides RectangleF
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
```

> **Γιατί είναι σημαντικό αυτό το βήμα** – Το API `Aspose.Words` παρέχει τις κλάσεις `Document`, `DocumentBuilder` και `Forms2OleControl` που σας επιτρέπουν να χειρίζεστε αρχεία Word σε επίπεδο αντικειμένου. Χωρίς αυτές τις αναφορές ο υπόλοιπος κώδικας δεν θα μπορούσε να μεταγλωττιστεί.

## Βήμα 2: Δημιουργία νέου εγγράφου Word και DocumentBuilder

Το αντικείμενο `Document` αντιπροσωπεύει ολόκληρο το πακέτο `.docx`, ενώ το `DocumentBuilder` προσφέρει ένα fluent API για την εισαγωγή περιεχομένου.

```csharp
// Step 2: Initialize a fresh Word document
Document document = new Document();

// Attach a builder to the document – the builder knows where to write next
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Επεξήγηση** – Η δημιουργία ενός νέου `Document` σας δίνει ένα καθαρό καμβά. Ο κέρσορας του builder ξεκινά στην αρχή της πρώτης ενότητας, έτοιμος για την επόμενη εισαγωγή.

## Βήμα 3: Εισαγωγή του ActiveX CommandButton

Χρησιμοποιήστε το `InsertForms2OleControl` για να τοποθετήσετε έναν έλεγχο ActiveX σε συγκεκριμένη θέση. Η μέθοδος απαιτεί τον τύπο του ελέγχου και ένα `RectangleF` που ορίζει τις συντεταγμένες X/Y και το μέγεθος (σε points).

```csharp
// Step 3: Add an ActiveX CommandButton at (100,100) with width 120 and height 30
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **Γιατί λειτουργεί** – Το `OleControlType.CommandButton` λέει στο API να δημιουργήσει ένα τυπικό Windows CommandButton. Το ορθογώνιο τοποθετεί το κουμπί σε σχέση με την πάνω‑αριστερή γωνία της σελίδας, επιτρέποντάς σας να **προσθέσετε διαδραστικό κουμπί** ακριβώς όπου το χρειάζεστε.

## Βήμα 4: Διαμόρφωση των ιδιοτήτων του κουμπιού

Τώρα ορίστε το εμφανιζόμενο κείμενο του κουμπιού (`Caption`) και το εσωτερικό του όνομα (`Name`). Αυτές οι ιδιότητες είναι ό,τι βλέπουν οι χρήστες και τι μπορεί να αναφερθεί ο κώδικας VBA αργότερα.

```csharp
// Step 4: Define the button’s caption and programmatic name
commandButton.Caption = "Click Me";
commandButton.Name = "btnClick";
```

> **Πρακτική συμβουλή** – Το `Name` πρέπει να είναι μοναδικό μέσα στο έγγραφο· διαφορετικά, οι μακροεντολές VBA μπορεί να αναφερθούν στο λάθος έλεγχο.

## Βήμα 5: Αποθήκευση του εγγράφου

Τέλος, γράψτε το αρχείο στο δίσκο. Ο έλεγχος ActiveX αποθηκεύεται μέσα στο πακέτο Word, έτσι το αποθηκευμένο αρχείο θα διατηρήσει πλήρη λειτουργικότητα όταν ανοίξει στο Microsoft Word.

```csharp
// Step 5: Persist the document – the ActiveX control stays embedded
string outputPath = @"C:\Temp\CommandButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

> **Αποτέλεσμα** – Το άνοιγμα του `CommandButton.docx` στο Word εμφανίζει ένα κλικ-μεγαλύτερο CommandButton με την ετικέτα “Click Me”. Ο έλεγχος μπορεί να συνδεθεί με μια μακροεντολή μέσω του UI του Word (`Developer → Design Mode → Properties`).

## Πλήρης λίστα πηγαίου κώδικα

Συνδυάζοντας όλα τα βήματα προκύπτει ένα ενιαίο, αυτόνομο πρόγραμμα που μπορείτε να αντιγράψετε, να επικολλήσετε και να εκτελέσετε.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert an ActiveX CommandButton at the desired location
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new RectangleF(100, 100, 120, 30));

        // Set the button's caption and internal name
        commandButton.Caption = "Click Me";
        commandButton.Name = "btnClick";

        // Save the document – the control is preserved
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### Αναμενόμενη έξοδος

Η εκτέλεση του προγράμματος εκτυπώνει μια γραμμή επιβεβαίωσης:

```
Document saved to C:\Temp\CommandButton.docx
```

Όταν ανοίξετε το παραγόμενο αρχείο στο Microsoft Word, θα δείτε ένα **CommandButton** τοποθετημένο στις καθορισμένες συντεταγμένες. Κάνοντας κλικ στο κουμπί σε λειτουργία σχεδίασης το επισημαίνει· σε λειτουργία εκτέλεσης συμπεριφέρεται όπως οποιοδήποτε τυπικό κουμπί ActiveX.

## Συνηθισμένες παραλλαγές και ειδικές περιπτώσεις

| Σενάριο | Προσαρμογή |
|----------|------------|
| **Διαφορετικός τύπος ελέγχου** | Αντικαταστήστε `OleControlType.CommandButton` με `OleControlType.CheckBox`, `OleControlType.OptionButton`, κ.λπ. |
| **Πολλαπλά κουμπιά** | Καλέστε `InsertForms2OleControl` επανειλημμένα, ενημερώνοντας τις συντεταγμένες του `RectangleF` για κάθε νέο κουμπί. |
| **Δυναμικό μέγεθος** | Υπολογίστε τις διαστάσεις του ορθογωνίου βάσει του μεγέθους σελίδας (`builder.PageSetup.PageWidth`). |
| **Αποθήκευση σε ροή** | Χρησιμοποιήστε `document.Save(stream, SaveFormat.Docx)` όταν χρειάζεται να επιστρέψετε το αρχείο από ένα web API. |
| **Μορφή Word 97‑2003** | Αλλάξτε τη μορφή αποθήκευσης σε `SaveFormat.Doc` για να παραγάγετε αρχείο `.doc` που εξακολουθεί να ενσωματώνει τον έλεγχο ActiveX. |

> **Pro tip:** Πάντα δοκιμάζετε το παραγόμενο έγγραφο στην έκδοση του Word-στόχο, επειδή παλαιότερες εκδόσεις μπορεί να επιβάλλουν ρυθμίσεις ασφαλείας που απενεργοποιούν τους ελέγχους ActiveX από προεπιλογή.

## Συχνές ερωτήσεις

**Λειτουργεί αυτό με .NET Core;**  
Ναι. Η βιβλιοθήκη Aspose.Words είναι cross‑platform και πλήρως συμβατή με .NET Core και .NET 5/6+.

**Μπορώ να αντιστοιχίσω μια μακροεντολή στο κουμπί προγραμματιστικά;**  
Το API δεν ενσωματώνει κώδικα VBA άμεσα. Αφού δημιουργηθεί το έγγραφο, ανοίξτε το στο Word, ενεργοποιήστε την καρτέλα Developer και καταγράψτε ή γράψτε μια μακροεντολή που αναφέρεται στο `btnClick`.

**Τι γίνεται αν το κουμπί δεν εμφανίζεται;**  
Βεβαιωθείτε ότι η καρτέλα `Developer` είναι ενεργοποιημένη στο Word και ότι το έγγραφο δεν είναι ανοιγμένο σε **Protected View**. Επίσης, ελέγξτε ότι οι συντεταγμένες του ορθογωνίου βρίσκονται εντός των περιθωρίων της σελίδας.

## Συμπέρασμα

Τώρα ξέρετε πώς να **δημιουργήσετε έλεγχο ActiveX** μέσα σε αρχείο Word χρησιμοποιώντας C#. Το tutorial κάλυψε **πώς να εισάγετε ActiveX**, επέδειξε **προσθήκη διαδραστικού κουμπιού**, έδειξε **πώς να δημιουργήσετε έγγραφο Word** από το μηδέν, και εικονογράφησε **δημιουργία κουμπιού με κώδικα** που παραμένει μετά την αποθήκευση.  

Από εδώ μπορείτε να εξερευνήσετε πρόσθετους τύπους ActiveX, να συνδέσετε το κουμπί με μακροεντολές VBA ή να ενσωματώσετε τη λογική σε μια μεγαλύτερη υπηρεσία δημιουργίας εγγράφων. Πειραματιστείτε με διαφορετικά μεγέθη, θέσεις και ιδιότητες ελέγχου για να ταιριάξετε ακριβώς την εμπειρία χρήστη που χρειάζεστε.

---


## Τι πρέπει να μάθετε στη συνέχεια;

Οι παρακάτω οδηγίες καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στην υλοποίηση των δικών σας έργων.

- [Create New Word Document](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Create Vba Project in Word Document](/words/english/net/working-with-vba-macros/create-vba-project/)
- [Create and Style a Word Document in Aspose.Words for .NET](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}