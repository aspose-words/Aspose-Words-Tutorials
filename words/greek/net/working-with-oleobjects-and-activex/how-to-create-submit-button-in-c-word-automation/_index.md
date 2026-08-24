---
category: general
date: 2026-08-23
description: Δημιουργήστε κουμπί υποβολής σε αυτοματοποίηση Word με C#. Μάθετε πώς
  να προσθέτετε ένα κουμπί ActiveX, να ορίζετε το όνομα του κουμπιού, τη λεζάντα και
  το κείμενο προγραμματιστικά.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create submit button
- set button text
- set button name
- add activex button
- set button caption
language: el
lastmod: 2026-08-23
og_description: Δημιουργία κουμπιού υποβολής σε αυτοματοποίηση Word με C#. Αυτός ο
  οδηγός δείχνει πώς να προσθέσετε ένα κουμπί ActiveX, να ορίσετε το όνομά του, τη
  λεζάντα και το κείμενο χρησιμοποιώντας το Aspose.Words.
og_image_alt: Screenshot of a Word document showing a created submit button
og_title: Δημιουργία κουμπιού υποβολής στην αυτοματοποίηση Word με C#
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Create submit button in C# Word automation. Learn to add an ActiveX
    button, set button name, caption, and text programmatically.
  headline: How to create submit button in C# Word automation
  type: TechArticle
- description: Create submit button in C# Word automation. Learn to add an ActiveX
    button, set button name, caption, and text programmatically.
  name: How to create submit button in C# Word automation
  steps:
  - name: Expected output
    text: 'Running the program creates `SubmitButton.docx`. When you open the file
      in Microsoft Word:'
  - name: Handling naming collisions
    text: 'If you run the routine multiple times on the same document, Word may auto‑rename
      duplicate controls. To guarantee uniqueness, you can prepend a GUID:'
  - name: Localizing the button caption
    text: 'For multilingual documents, store captions in a resource file and assign
      them at runtime:'
  - name: Responding to the button click
    text: 'The button itself does not contain click logic in C#. You typically attach
      a VBA macro:'
  type: HowTo
tags:
- C#
- Word automation
- ActiveX
- Aspose.Words
title: Πώς να δημιουργήσετε κουμπί υποβολής στην αυτοματοποίηση του Word με C#
url: /el/net/working-with-oleobjects-and-activex/how-to-create-submit-button-in-c-word-automation/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε κουμπί υποβολής σε C# Word automation

Αν χρειάζεστε **create submit button** μέσα σε ένα έγγραφο Word χρησιμοποιώντας C#, αυτός ο οδηγός σας καθοδηγεί βήμα-βήμα. Θα δείτε πώς να προσθέσετε ένα κουμπί ActiveX, να ορίσετε ένα προγραμματιστικό όνομα και να θέσετε την λεζάντα του κουμπιού ώστε να μοιάζει με έναν κανονικό *Submit* control.

Η αυτοματοποίηση των στοιχείων φόρμας στο Word μπορεί να αντικαταστήσει την χειροκίνητη εργασία διάταξης και να εξασφαλίσει συνέπεια σε εκατοντάδες έγγραφα. Σ τα βήματα παρακάτω θα μάθετε επίσης πώς να **set button text**, **set button name**, και **set button caption** — όλα απαραίτητα όταν το κουμπί συμμετέχει σε μια ροή εργασίας που οδηγείται από μακροεντολές.

## Προαπαιτούμενα

* .NET 6.0 (ή νεότερη) εγκατεστημένο.
* Μια αναφορά στο **Aspose.Words for .NET** (η βιβλιοθήκη που παρέχει `DocumentBuilder.InsertForms2OleControl`).
* Βασική εξοικείωση με C# και τα ActiveX στοιχεία φόρμας του Word.

Μπορείτε να εγκαταστήσετε το Aspose.Words μέσω NuGet:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** Χρησιμοποιήστε την πιο πρόσφατη σταθερή έκδοση του Aspose.Words για να επωφεληθείτε από διορθώσεις σφαλμάτων και νέες δυνατότητες σχετικές με τα ActiveX controls.

## Επισκόπηση της λύσης

Ο οδηγός είναι οργανωμένος σε τρία σαφή βήματα:

1. **Add ActiveX button** – χρησιμοποιήστε τη μέθοδο `InsertForms2OleControl` για να τοποθετήσετε ένα κουμπί εντολής στο έγγραφο.  
2. **Set button name** – εκχωρήστε ένα μοναδικό προγραμματιστικό αναγνωριστικό με την ιδιότητα `Name`.  
3. **Set button caption** – ορίστε το ορατό κείμενο στο κουμπί μέσω της ιδιότητας `Caption` (η οποία επίσης ελέγχει το **set button text** που βλέπετε στη διεπαφή).

Στο τέλος του οδηγού θα έχετε μια πλήρως λειτουργική ρουτίνα **create submit button** που μπορείτε να επαναχρησιμοποιήσετε σε οποιοδήποτε έργο αυτοματοποίησης Word.

## Βήμα 1: Προσθήκη κουμπιού ActiveX στο έγγραφο

Το πρώτο καθήκον είναι να **add activex button** στο αρχείο Word. Το Aspose.Words εκθέτει την απαρίθμηση `Forms2OleControlType.CommandButton` για αυτόν τον σκοπό.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Load or create a new document
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a CommandButton ActiveX control at the cursor position
Forms2OleControl commandBtn = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton);
```

**Γιατί αυτό το βήμα είναι σημαντικό:**  
Τα ActiveX controls είναι τα μόνα στοιχεία φόρμας του Word που μπορούν να εκτελέσουν μακροεντολές VBA ή να αλληλεπιδράσουν με εξωτερικό κώδικα. Η προσθήκη του ελέγχου δημιουργεί έναν placeholder που τα επόμενα βήματα μπορούν να διαμορφώσουν.

> **Edge case:** Εάν το έγγραφο περιέχει ήδη ένα στοιχείο ελέγχου με το ίδιο όνομα, το Word θα μετονομάσει αυτόματα το νέο (π.χ., `CommandButton1`). Ο ρητός ορισμός του ονόματος στο επόμενο βήμα αποφεύγει τέτοιες συγκρούσεις.

## Βήμα 2: Ορισμός ονόματος κουμπιού

Ένα αξιόπιστο **set button name** είναι κρίσιμο όταν χρειάζεται να αναφερθείτε στο στοιχείο ελέγχου από VBA ή από άλλα μέρη του κώδικα C#. Η ιδιότητα `Name` παρέχει στο κουμπί ένα προγραμματιστικό αναγνωριστικό.

```csharp
// Assign a unique programmatic name
commandBtn.Name = "btnSubmit";
```

**Γιατί πρέπει να ορίσετε ένα όνομα:**  
Όταν το έγγραφο ανοίξει, το VBA μπορεί να ανακτήσει το κουμπί μέσω `ActiveDocument.InlineShapes("btnSubmit")`. Ένα περιγραφικό όνομα όπως `btnSubmit` επίσης διευκρινίζει την πρόθεση όταν ελέγχετε το XML του εγγράφου.

> **Pro tip:** Κρατήστε τα ονόματα σύντομα, αλφαριθμητικά και να ξεκινούν με γράμμα για να παραμείνουν συμβατά με τους κανόνες ονοματοδοσίας του VBA.

## Βήμα 3: Ορισμός λεζάντας κουμπιού (ορατό κείμενο)

Το κείμενο που βλέπουν οι χρήστες στο κουμπί ελέγχεται από την ιδιότητα **set button caption**. Στη διεπαφή του Word αυτό εμφανίζεται ως η ετικέτα του κουμπιού, η οποία είναι επίσης το **set button text** που θέλετε να εμφανίσετε.

```csharp
// Define the text shown on the button
commandBtn.Caption = "Submit";
```

**Γιατί η λεζάντα είναι σημαντική:**  
Η λεζάντα είναι η ετικέτα που βλέπει ο χρήστης. Η αλλαγή της αργότερα δεν επηρεάζει το όνομα του κουμπιού, έτσι μπορείτε να τοποθετήσετε το UI σε διαφορετικές γλώσσες χωρίς να σπάσει ο κώδικας που εξαρτάται από το `btnSubmit`.

> **Common question:** *Μπορώ να ορίσω τόσο Caption όσο και Value;*  
> Για ένα `CommandButton`, το `Caption` ελέγχει την ετικέτα, ενώ το `Value` δεν χρησιμοποιείται. Εάν χρειάζεστε μια κρυφή τιμή, αποθηκεύστε την σε μια προσαρμοσμένη ιδιότητα εγγράφου.

## Πλήρες λειτουργικό παράδειγμα

Συνδυάζοντας τα τρία βήματα λαμβάνετε μια πλήρη ρουτίνα που μπορείτε να ενσωματώσετε σε οποιαδήποτε εφαρμογή console ή Windows:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert the ActiveX command button
        Forms2OleControl commandBtn = builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton);

        // 3. Set a meaningful name for later reference
        commandBtn.Name = "btnSubmit";

        // 4. Set the visible caption (this is the button text)
        commandBtn.Caption = "Submit";

        // Optional: position the button (in points)
        commandBtn.Left = 100;   // distance from left margin
        commandBtn.Top = 200;    // distance from top margin
        commandBtn.Width = 80;
        commandBtn.Height = 30;

        // Save the document
        doc.Save("SubmitButton.docx");
        Console.WriteLine("Document with submit button created successfully.");
    }
}
```

### Αναμενόμενο αποτέλεσμα

Η εκτέλεση του προγράμματος δημιουργεί το `SubmitButton.docx`. Όταν ανοίξετε το αρχείο στο Microsoft Word:

* Εμφανίζεται ένα κουμπί **Submit** στην καθορισμένη θέση.
* Το όνομα του κουμπιού είναι `btnSubmit` (ελέγξτε μέσω *Developer → Design Mode → Properties*).
* Κάνοντας κλικ στο κουμπί σε λειτουργία σχεδίασης εμφανίζεται η λεζάντα *Submit*.

Τώρα έχετε ένα επαναχρησιμοποιήσιμο δομικό στοιχείο για οποιαδήποτε λύση Word που βασίζεται σε φόρμες.

## Πρόσθετες παρατηρήσεις

### Διαχείριση συγκρούσεων ονομάτων

Εάν εκτελέσετε τη ρουτίνα πολλές φορές στο ίδιο έγγραφο, το Word μπορεί να μετονομάσει αυτόματα τα διπλότυπα στοιχεία ελέγχου. Για να εξασφαλίσετε μοναδικότητα, μπορείτε να προσθέσετε ένα GUID στην αρχή:

```csharp
commandBtn.Name = $"btnSubmit_{Guid.NewGuid():N}";
```

### Τοπικοποίηση της λεζάντας του κουμπιού

Για πολυγλωσσικά έγγραφα, αποθηκεύστε τις λεζάντες σε αρχείο πόρων και αντιστοιχίστε τις κατά την εκτέλεση:

```csharp
commandBtn.Caption = Resources.SubmitButtonLabel;
```

### Απόκριση στο κλικ του κουμπιού

Το ίδιο το κουμπί δεν περιέχει λογική κλικ σε C#. Συνήθως συνδέετε μια μακροεντολή VBA:

```vba
Sub btnSubmit_Click()
    MsgBox "Form submitted!"
End Sub
```

Επειδή έχετε **set button name** στο `btnSubmit`, το όνομα της μακροεντολής ακολουθεί αυτόματα τη σύμβαση `<Name>_Click`.

## Συχνές ερωτήσεις αντιμετώπισης προβλημάτων

| Ερώτηση | Απάντηση |
|----------|--------|
| **Γιατί εμφανίζεται το κουμπί κενό;** | Βεβαιωθείτε ότι έχετε ορίσει την ιδιότητα `Caption`; χωρίς αυτή το κουμπί δεν εμφανίζει κείμενο. |
| **Μπορώ να χρησιμοποιήσω διαφορετικό ActiveX control;** | Ναι. Αντικαταστήστε το `Forms2OleControlType.CommandButton` με `CheckBox`, `OptionButton` κ.λπ., αλλά οι ιδιότητες διαφέρουν. |
| **Είναι συμβατό με .NET Core;** | Το Aspose.Words for .NET υποστηρίζει .NET 6+, έτσι ο ίδιος κώδικας λειτουργεί σε .NET Core και .NET Framework. |
| **Τι γίνεται αν το έγγραφο έχει ήδη ένα κουμπί;** | Χρησιμοποιήστε ένα μοναδικό `Name` (π.χ., προσθέστε ένα GUID) για να αποφύγετε συγκρούσεις. |

## Συμπέρασμα

Τώρα ξέρετε πώς να **create submit button** προγραμματιστικά σε ένα έγγραφο Word χρησιμοποιώντας C#. Ακολουθώντας τα τρία βήματα — **add activex button**, **set button name**, και **set button caption** — μπορείτε αξιόπιστα να **set button text**, **set button name**, και **set button caption** για οποιαδήποτε αυτοματοποιημένη λύση φόρμας.

Από εδώ μπορείτε να εξερευνήσετε:

* Προσθήκη μακροεντολών VBA που αντιδρούν στο κλικ του **submit button**.
* Στυλιζάρισμα του κουμπιού με προσαρμοσμένες γραμματοσειρές ή χρώματα μέσω του υποκείμενου XML.
* Δημιουργία πολλαπλών κουμπιών σε βρόχο για δυναμικές φόρμες.

Μη διστάσετε να πειραματιστείτε με διαφορετικές λεζάντες, ονόματα και θέσεις για να ταιριάζουν στη συγκεκριμένη ροή εργασίας σας. Καλή αυτοματοποίηση!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετικές θεματικές που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα-βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create a Line Chart in Word using Aspose.Words for .NET](/words/english/net/working-with-charts/create-chart-using-shape/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}