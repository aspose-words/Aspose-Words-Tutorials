---
category: general
date: 2026-07-29
description: Προσθέστε κουμπί εντολής σε έγγραφο Word χρησιμοποιώντας το Aspose.Words.
  Μάθετε πώς να ορίσετε τις ιδιότητες του ελέγχου ActiveX και να ορίσετε τη λεζάντα
  του κουμπιού εντολής σε λίγα εύκολα βήματα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button to word document
- set activex control properties
- set command button caption
- Aspose.Words ActiveX example
- C# insert ActiveX control
language: el
lastmod: 2026-07-29
og_description: Προσθέστε κουμπί εντολής σε έγγραφο Word με το Aspose.Words. Αυτό
  το σεμινάριο δείχνει πώς να ορίσετε τις ιδιότητες του ελέγχου ActiveX και να θέσετε
  γρήγορα τη λεζάντα του κουμπιού εντολής.
og_image_alt: Screenshot of a Word document with a Submit command button inserted
  via C#
og_title: Προσθήκη κουμπιού εντολής σε έγγραφο Word – Aspose.Words βήμα‑βήμα
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  headline: Add Command Button to Word Document with Aspose.Words – Complete Guide
  type: TechArticle
- description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  name: Add Command Button to Word Document with Aspose.Words – Complete Guide
  steps:
  - name: Setting the Caption
    text: 'The caption is the text that appears on the button itself. To **set command
      button caption**, simply assign a string to the `Caption` property:'
  - name: Naming the Control
    text: 'Giving the control a meaningful name makes it easier to reference later
      (for example, when automating Word macros). We’ll set the `Name` property:'
  - name: Positioning on the Page
    text: 'Word uses points (1/72 of an inch) for layout. Adjust the `Left` and `Top`
      properties to place the button where you need it:'
  - name: Expected Result
    text: 1. The Word document opens with a single page. 2. A rectangular button labeled
      **Submit** appears at the coordinates you specified. 3. If you right‑click the
      button and choose **Properties**, you’ll see the name `btnSubmit` and other
      properties you set.
  - name: Inserting Other ActiveX Types
    text: 'The `InsertForms2OleControl` method isn’t limited to command buttons. You
      can embed check boxes, option buttons, or even custom ActiveX objects:'
  - name: Handling Word Versions
    text: Older Word versions (pre‑2007) use the binary `.doc` format, which stores
      ActiveX controls differently. Aspose.Words automatically converts the control
      when you save as `.doc`, but some properties (like precise positioning) may
      shift. If you target legacy formats, test the output in the specific Wor
  - name: Security Settings
    text: 'Word may disable ActiveX controls on machines with strict macro security.
      To avoid a “Security Warning” dialog, consider:'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Προσθήκη κουμπιού εντολής σε έγγραφο Word με το Aspose.Words – Πλήρης οδηγός
url: /el/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Προσθήκη Κουμπιού Εντολής σε Έγγραφο Word – Πλήρης Οδηγός Προγραμματισμού

Έχετε ποτέ χρειαστεί να **add command button to word document** αλλά δεν ήσασταν σίγουροι ποιες κλήσεις API να χρησιμοποιήσετε; Δεν είστε μόνοι· πολλοί προγραμματιστές αντιμετωπίζουν αυτό το εμπόδιο όταν προσπαθούν για πρώτη φορά να ενσωματώσουν διαδραστικούς ελέγχους σε ένα αρχείο DOCX. Τα καλά νέα είναι ότι το Aspose.Words το κάνει απροσδόκητα εύκολο. Σε αυτόν τον οδηγό θα περάσουμε από τη δημιουργία ενός ελέγχου CommandButton ActiveX, **set activex control properties**, και **set command button caption**—όλα με καθαρό κώδικα C# που μπορείτε να αντιγράψετε‑επικολλήσετε αμέσως.

Στο τέλος αυτού του σεμινάριου θα έχετε ένα πλήρως λειτουργικό αρχείο Word που περιέχει ένα κλικ‑αξιό κουμπί “Submit”, έτοιμο να ανοιχτεί στο Microsoft Word. Χωρίς εξωτερικά σενάρια VBA, χωρίς χειροκίνητη τροποποίηση UI—απλώς καθαρός προγραμματιστικός έλεγχος.

## Τι Θα Μάθετε

* Πώς να δημιουργήσετε ένα κενό έγγραφο Word και ένα `DocumentBuilder`.
* Την ακριβή κλήση μεθόδου για **add command button to word document** χρησιμοποιώντας το Aspose.Words.
* Τρόπους για **set activex control properties** όπως μέγεθος, θέση και όνομα.
* Τη σωστή τεχνική για **set command button caption** ώστε το κουμπί να εμφανίζει ακριβώς ό,τι θέλετε.
* Συμβουλές για τη διαχείριση ακραίων περιπτώσεων όπως διαφορετικοί τύποι κουμπιών, κλιμάκωση DPI και συμβατότητα με εκδόσεις του Word.

> **Προαπαιτούμενο:** Visual Studio (ή οποιοδήποτε IDE C#) με εγκατεστημένο το Aspose.Words for .NET (πακέτο NuGet `Aspose.Words`). Δεν απαιτείται προηγούμενη εμπειρία με ActiveX.

---

## Βήμα 1: Ρύθμιση του Έργου και Εισαγωγή Namespaces

Πριν μπορέσουμε να **add command button to word document**, χρειαζόμαστε ένα έργο C# που να αναφέρει το Aspose.Words. Δημιουργήστε μια νέα εφαρμογή .NET console, μετά προσθέστε το πακέτο NuGet:

```bash
dotnet add package Aspose.Words
```

Τώρα εισάγετε τα απαιτούμενα namespaces στο αρχείο πηγαίου κώδικα:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;
```

Αυτές οι τρεις οδηγίες `using` σας δίνουν πρόσβαση στις κλάσεις `Document`, `DocumentBuilder` και `Forms2OleControl` που ενεργοποιούν την εισαγωγή ActiveX.

*Συμβουλή:* Αν χρησιμοποιείτε Visual Studio, το IDE θα προτείνει την αυτόματη προσθήκη αυτών όταν πληκτρολογείτε τα ονόματα των κλάσεων.

---

## Βήμα 2: Δημιουργία Κενού Εγγράφου και Builder

Ένα νέο αντικείμενο `Document` αντιπροσωπεύει ένα κενό αρχείο Word. Το `DocumentBuilder` είναι το βολικό μας “στυλό” που μας επιτρέπει να σχεδιάζουμε, να εισάγουμε κείμενο και—κυρίως—να τοποθετούμε ελέγχους ActiveX.

```csharp
// Initialize a new, empty Word document.
Document doc = new Document();

// Attach a builder to the document for editing.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Σε αυτό το σημείο το έγγραφο είναι απλώς ένας κενός καμβάς—σκεφτείτε το ως ένα καθαρό φύλλο χαρτί που περιμένει το κουμπί εντολής σας.

---

## Βήμα 3: Εισαγωγή του Ελέγχου CommandButton ActiveX

Τώρα τελικά **add command button to word document**. Το Aspose.Words παρέχει τη μέθοδο `InsertForms2OleControl`, η οποία δέχεται τον τύπο ελέγχου και τις διαστάσεις. Θα χρησιμοποιήσουμε το `Forms2OleControlType.CommandButton` και θα του δώσουμε ένα άνετο πλάτος 150 σημείων και ύψος 30 σημείων.

```csharp
// Insert a CommandButton ActiveX control with a specific size.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton,
    width: 150,
    height: 30);
```

Η μέθοδος επιστρέφει ένα αντικείμενο `Forms2OleControl`, το οποίο θα χρησιμοποιήσουμε για **set activex control properties** στο επόμενο βήμα.

---

## Βήμα 4: Διαμόρφωση του Ελέγχου – Όνομα, Λεζάντα και Θέση

### Ορισμός της Λεζάντας

Η λεζάντα είναι το κείμενο που εμφανίζεται στο ίδιο το κουμπί. Για **set command button caption**, απλώς εκχωρήστε μια συμβολοσειρά στην ιδιότητα `Caption`:

```csharp
commandButton.Caption = "Submit";
```

Μπορείτε να αλλάξετε το `"Submit"` σε οτιδήποτε—“Save”, “Export”, “Launch”, κλπ.—και το Word θα εμφανίσει ακριβώς αυτό το κείμενο.

### Ονομασία του Ελέγχου

Η ανάθεση ενός περιγραφικού ονόματος στο έλεγχο το κάνει πιο εύκολο να αναφερθεί αργότερα (π.χ., όταν αυτοματοποιείτε μακροεντολές Word). Θα ορίσουμε την ιδιότητα `Name`:

```csharp
commandButton.Name = "btnSubmit";
```

### Τοποθέτηση στη Σελίδα

Το Word χρησιμοποιεί μονάδες σημείων (1/72 ίντσας) για τη διάταξη. Ρυθμίστε τις ιδιότητες `Left` και `Top` για να τοποθετήσετε το κουμπί όπου το χρειάζεστε:

```csharp
commandButton.Left = 100; // 100 points from the left margin
commandButton.Top  = 200; // 200 points from the top of the page
```

Αν χρειάζεται να ευθυγραμμίσετε το κουμπί σε σχέση με μια παράγραφο, μπορείτε πρώτα να μετακινήσετε τον κέρσορα του builder, μετά να εισάγετε το έλεγχο· οι συντεταγμένες θα είναι σχετικές με αυτή τη θέση.

*Ακραία περίπτωση:* Σε οθόνες υψηλής DPI το οπτικό μέγεθος μπορεί να φαίνεται ελαφρώς διαφορετικό στο Word. Για να διατηρήσετε το φυσικό μέγεθος του κουμπιού σταθερό σε όλες τις συσκευές, μπορείτε να υπολογίσετε τα σημεία βάσει του στόχου DPI (συνήθως 96 DPI για το Word).

---

## Βήμα 5: Αποθήκευση του Εγγράφου

Με το κουμπί πλήρως διαμορφωμένο, η αποθήκευση του αρχείου γίνεται με μία γραμμή κώδικα:

```csharp
// Save the document; the ActiveX control is stored inside the DOCX.
doc.Save("CommandButton.docx");
```

Το προκύπτον `CommandButton.docx` περιέχει ένα πλήρως λειτουργικό κουμπί ActiveX. Ανοίξτε το στο Microsoft Word και θα δείτε ένα κουμπί “Submit” τοποθετημένο ακριβώς εκεί που το θέσατε.

### Αναμενόμενο Αποτέλεσμα

1. Το έγγραφο Word ανοίγει με μία μόνο σελίδα.  
2. Ένα ορθογώνιο κουμπί με την ετικέτα **Submit** εμφανίζεται στις συντεταγμένες που καθορίσατε.  
3. Αν κάνετε δεξί κλικ στο κουμπί και επιλέξετε **Properties**, θα δείτε το όνομα `btnSubmit` και άλλες ιδιότητες που ορίσατε.

---

## Βήμα 6: Προχωρημένες Παραλλαγές και Συνηθισμένα Πιθανά Προβλήματα

### Εισαγωγή Άλλων Τύπων ActiveX

Η μέθοδος `InsertForms2OleControl` δεν περιορίζεται μόνο στα κουμπιά εντολής. Μπορείτε να ενσωματώσετε πλαίσια ελέγχου, κουμπιά επιλογής ή ακόμη και προσαρμοσμένα αντικείμενα ActiveX:

```csharp
// Example: Insert a CheckBox instead of a CommandButton.
Forms2OleControl checkBox = builder.InsertForms2OleControl(
    Forms2OleControlType.CheckBox,
    width: 20,
    height: 20);
checkBox.Name = "chkAgree";
checkBox.Caption = "I Agree";
```

Το ίδιο πρότυπο **set activex control properties** ισχύει—απλώς αλλάξτε το enum τύπου.

### Διαχείριση Εκδόσεων Word

Οι παλαιότερες εκδόσεις του Word (πριν το 2007) χρησιμοποιούν τη δυαδική μορφή `.doc`, η οποία αποθηκεύει τα ActiveX controls διαφορετικά. Το Aspose.Words μετατρέπει αυτόματα το control όταν αποθηκεύετε ως `.doc`, αλλά ορισμένες ιδιότητες (όπως η ακριβής θέση) μπορεί να μετατοπιστούν. Αν στοχεύετε σε παλαιές μορφές, δοκιμάστε το αποτέλεσμα στην συγκεκριμένη έκδοση του Word που χρειάζεστε.

### Ρυθμίσεις Ασφαλείας

Το Word μπορεί να απενεργοποιήσει τα ActiveX controls σε μηχανές με αυστηρή ασφάλεια μακροεντολών. Για να αποφύγετε το παράθυρο διαλόγου “Security Warning”, σκεφτείτε:

* Υπογραφή του εγγράφου με αξιόπιστο πιστοποιητικό.  
* Οδηγίες στους χρήστες να ενεργοποιήσουν το περιεχόμενο ActiveX για αυτή τη θέση αρχείου.  
* Χρήση εναλλακτικής λύσης χωρίς μακροεντολές (π.χ., απλούς ελέγχους περιεχομένου) εάν η ασφάλεια είναι ζήτημα.

---

## Βήμα 7: Πλήρες Παράδειγμα Λειτουργίας

Παρακάτω βρίσκεται το πλήρες, έτοιμο‑για‑εκτέλεση πρόγραμμα που ενσωματώνει κάθε βήμα που συζητήσαμε. Αντιγράψτε το στο `Program.cs`, προσαρμόστε τη διαδρομή εξόδου αν χρειάζεται, και πατήστε **Run**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            width: 150,   // Width in points
            height: 30);  // Height in points

        // Step 3: Set the control's name and caption.
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Step 4: Position the control on the page.
        commandButton.Left = 100; // 100 points from left edge
        commandButton.Top  = 200; // 200 points from top edge

        // Optional: Add a paragraph above the button for context.
        builder.MoveToDocumentEnd();
        builder.Writeln("Click the button below to submit the form:");

        // Step 5: Save the document.
        string outputPath = "CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved successfully to {outputPath}");
    }
}
```

**Τι κάνει αυτός ο κώδικας:**

* Ξεκινά με ένα νέο έγγραφο.  
* Εισάγει ένα κουμπί εντολής, **sets activex control properties**, και **sets command button caption**.  
* Προσθέτει μια σύντομη επεξηγηματική παράγραφο.  
* Αποθηκεύει το αρχείο ως `CommandButton.docx`.

Εκτελέστε το πρόγραμμα, ανοίξτε το παραγόμενο αρχείο, και θα δείτε το κουμπί να βρίσκεται κάτω από το επεξηγηματικό κείμενο.

---

## Συμπέρασμα

Μόλις δείξαμε πώς να **add command button to word document** χρησιμοποιώντας το Aspose.Words, πώς να **set activex control properties**, και πώς να **set command button caption**—όλα σε ένα σύντομο, έτοιμο για παραγωγή απόσπασμα C#. Η προσέγγιση κλιμακώνεται: αλλάξτε τον τύπο του ελέγχου, προσαρμόστε τις διαστάσεις, ή κάντε βρόχο πάνω σε πηγή δεδομένων για να ενσωματώσετε αυτόματα δεκάδες κουμπιά.

Θέλετε να προχωρήσετε παραπέρα; Δοκιμάστε:

* Σύνδεση του κουμπιού με μια μακροεντολή που ενεργοποιεί εξαγωγή δεδομένων.  
* Προσθήκη εικόνων ή προσαρμοσμένων εικονιδίων μέσα στο κουμπί χρησιμοποιώντας την ιδιότητα `Picture`.  
* Δημιουργία πλήρους φόρμας με πολλαπλούς ελέγχους ActiveX (πλαίσια κειμένου, λίστες επιλογής κλπ.).

Η πειραματική προσέγγιση είναι ο καλύτερος τρόπος να κυριαρχήσετε στην αυτοματοποίηση του Word. Αν αντιμετωπίσετε πρόβλημα, θυμηθείτε να ελέγξετε ξανά τους υπολογισμούς DPI και τις ρυθμίσεις ασφαλείας του Word. Καλή προγραμματιστική δουλειά, και εύχομαι τα έγγραφά σας να γίνονται όλο και πιο διαδραστικά!

## Τι Θα Πρέπει Να Μάθετε Στη Σύντομη Μελλοντική

Τα παρακάτω σεμινάρια καλύπτουν στενά συναφή θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Προσθήκη Περιεχομένου Χρησιμοποιώντας Document Builder στο Aspose.Words για .NET](/words/english/net/add-content-using-document-builder/)
- [Δημιουργία Ομαδικού Σχήματος σε Έγγραφο Word Χρησιμοποιώντας Aspose.Words για .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Δημιουργία Εγγράφου Word με Κεφαλίδα και Υποσέλιδο Χρησιμοποιώντας Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}