---
category: general
date: 2026-08-04
description: Δημιουργήστε έγγραφο Word προγραμματιστικά χρησιμοποιώντας C#. Μάθετε
  πώς να προσθέτετε προγραμματιστικά κουμπί εντολής με το Aspose.Words σε λίγα μόνο
  βήματα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- programmatically add command button
- Aspose.Words InsertForms2OleControl
- C# Word automation
- OLE command button in Word
language: el
lastmod: 2026-08-04
og_description: Δημιουργήστε έγγραφο Word προγραμματιστικά με το Aspose.Words. Αυτός
  ο οδηγός δείχνει πώς να προσθέσετε προγραμματιστικά ένα κουμπί εντολής, να το διαμορφώσετε
  και να αποθηκεύσετε το αρχείο.
og_image_alt: Screenshot of a Word document that contains a Command Button added programmatically
og_title: Δημιουργία εγγράφου Word προγραμματιστικά – πλήρες σεμινάριο C#
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create word document programmatically using C#. Learn how to programmatically
    add command button with Aspose.Words in just a few steps.
  headline: Create word document programmatically – step‑by‑step guide
  type: TechArticle
- description: Create word document programmatically using C#. Learn how to programmatically
    add command button with Aspose.Words in just a few steps.
  name: Create word document programmatically – step‑by‑step guide
  steps:
  - name: The `ControlType` enum value (here `CommandButton`).
    text: The `ControlType` enum value (here `CommandButton`).
  - name: A `RectangleF` that defines the X‑Y position and the width‑height of the
      control (measured in points, where 72 pt = 1 inch).
    text: A `RectangleF` that defines the X‑Y position and the width‑height of the
      control (measured in points, where 72 pt = 1 inch).
  - name: Optionally, additional OLE properties (not needed for the basic button).
    text: Optionally, additional OLE properties (not needed for the basic button).
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Δημιουργία εγγράφου Word προγραμματιστικά – οδηγός βήμα‑προς‑βήμα
url: /el/net/working-with-form-fields/create-word-document-programmatically-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία εγγράφου Word προγραμματιστικά – πλήρης οδηγός C#

Αν χρειάζεστε **create word document programmatically**, αυτός ο οδηγός σας δείχνει ακριβώς πώς να το κάνετε με το Aspose.Words for .NET. Με λίγες μόνο γραμμές C# μπορείτε να δημιουργήσετε ένα κενό αρχείο `.docx`, **programmatically add command button** ελέγχους, να ορίσετε τις ιδιότητές τους και να αποθηκεύσετε το αποτέλεσμα.  

Τα παρακάτω βήματα καλύπτουν όλα, από τη ρύθμιση του έργου μέχρι την αντιμετώπιση ειδικών περιπτώσεων, ώστε να μπορείτε να αντιγράψετε τον κώδικα στην δική σας εφαρμογή και να τον εκτελέσετε χωρίς τροποποιήσεις.

## Τι θα πετύχετε

* Αρχικοποιήστε ένα νέο έγγραφο Word εξ ολοκλήρου στη μνήμη.  
* **Programmatically add command button** OLE ελέγχους σε οποιαδήποτε θέση και μέγεθος.  
* Διαμορφώστε τη λεζάντα του κουμπιού, το εσωτερικό όνομα και άλλες ιδιότητες OLE.  
* Αποθηκεύστε το παραγόμενο έγγραφο σε δίσκο ή σε ροή για περαιτέρω επεξεργασία.

### Προαπαιτούμενα

* .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.6+).  
* Έγκυρη άδεια Aspose.Words for .NET (ή δωρεάν αξιολόγηση).  
* Βασική εξοικείωση με C# και Visual Studio (ή οποιοδήποτε IDE προτιμάτε).  

> **Pro tip:** Εάν εκτελέσετε το δείγμα χωρίς άδεια, το Aspose.Words θα προσθέσει ένα μικρό υδατογράφημα αξιολόγησης στην πρώτη σελίδα.

## Step 1: Set up the project and import required namespaces

Δημιουργήστε μια νέα Console App (ή ενσωματώστε την σε υπάρχουσα υπηρεσία) και προσθέστε το πακέτο NuGet Aspose.Words:

```bash
dotnet add package Aspose.Words
```

Στη συνέχεια, συμπεριλάβετε τα απαραίτητα namespaces στην κορυφή του αρχείου `.cs` σας:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
```

Αυτές οι εισαγωγές σας δίνουν πρόσβαση στα `Document`, `DocumentBuilder`, `Forms2OleControl` και στη δομή `RectangleF` που χρησιμοποιείται για τοποθέτηση.

## Step 2: Initialize a fresh Word document

Η πρώτη ενέργεια σε οποιαδήποτε ροή **create word document programmatically** είναι η δημιουργία ενός αντικειμένου `Document`. Αυτό το αντικείμενο ζει μόνο στη μνήμη μέχρι να το αποθηκεύσετε ρητά.

```csharp
// Step 2: Create a new blank document
Document doc = new Document();

// Attach a DocumentBuilder to simplify content insertion
DocumentBuilder builder = new DocumentBuilder(doc);
```

Το `DocumentBuilder` λειτουργεί σαν κέρσορας που παρακολουθεί πού θα τοποθετηθεί το επόμενο στοιχείο. Η χρήση του κρατά τον κώδικα σύντομο και αντικατοπτρίζει τον τρόπο που θα πληκτρολογούσατε απευθείας στο Word.

## Step 3: Insert a command button OLE control

Το Aspose.Words παρέχει τη μέθοδο `InsertForms2OleControl` για την ενσωμάτωση αντικειμένων OLE όπως κουμπιά εντολών, πλαίσια ελέγχου ή λίστες. Η μέθοδος απαιτεί τρία ορίσματα:

1. Την τιμή του enum `ControlType` (εδώ `CommandButton`).  
2. Ένα `RectangleF` που ορίζει τη θέση X‑Y και το πλάτος‑ύψος του ελέγχου (μετρημένα σε points, όπου 72 pt = 1 inch).  
3. Προαιρετικά, επιπλέον ιδιότητες OLE (δεν απαιτούνται για το βασικό κουμπί).

```csharp
// Step 3: Programmatically add command button at (100,100) with size 120×30 points
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **Why this works:** Η `InsertForms2OleControl` δημιουργεί ένα κοντέινερ OLE στο έγγραφο και επιστρέφει ένα wrapper `Forms2OleControl`. Το wrapper σας επιτρέπει να χειριστείτε το υποκείμενο αντικείμενο OLE (το πραγματικό κουμπί) χωρίς να ασχοληθείτε με χαμηλού επιπέδου COM interop.

## Step 4: Configure the button’s caption and internal name

Μετά την εισαγωγή, συνήθως θέλετε να δώσετε στο κουμπί μια ετικέτα ορατή στον χρήστη και ένα εσωτερικό αναγνωριστικό που το macro ή το add‑in σας θα μπορεί να αναφέρει αργότερα.

```csharp
// Step 4: Set caption and name of the button
commandButton.OleFormat.OleObject.Caption = "Click Me";
commandButton.OleFormat.OleObject.Name = "cmdClickMe";
```

* `Caption` είναι το κείμενο που εμφανίζεται στο κουμπί στη διεπαφή του Word.  
* `Name` είναι το προγραμματιστικό αναγνωριστικό που χρησιμοποιείται από VBA ή εξωτερικά σενάρια αυτοματισμού.

### Προαιρετικό: Ανάθεση macro στο κουμπί

Εάν σκοπεύετε να εκτελείται ένα macro VBA όταν πατηθεί το κουμπί, μπορείτε να συνδέσετε το όνομα του macro:

```csharp
commandButton.OleFormat.OleObject.MacroName = "MyMacro";
```

> **Edge case:** Όταν το στόχο έγγραφο ανοίξει σε μηχάνημα χωρίς το macro, το Word θα εμφανίσει προειδοποίηση ασφαλείας. Πάντα υπογράψτε τα macros ή ενημερώστε τους χρήστες για τις απαιτούμενες ρυθμίσεις.

## Step 5: Save the document

Μπορείτε να γράψετε το αρχείο σε δίσκο, σε `MemoryStream`, ή απευθείας σε αντικείμενο response σε web API. Η πιο απλή προσέγγιση για μια demo κονσόλα είναι η αποθήκευση σε τοπικό φάκελο:

```csharp
// Step 5: Persist the document containing the button
string outputPath = @"C:\Temp\CommandButton.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Το παραγόμενο `.docx` ανοίγει στο Microsoft Word με ένα λειτουργικό κουμπί εντολής που εμφανίζει “Click Me”. Κάνοντας κλικ στο κουμπί θα ενεργοποιηθεί το ανατεθειμένο macro (αν υπάρχει) ή απλώς θα εμφανίσει ένα προεπιλεγμένο μήνυμα.

## Full working example

Αντιγράψτε το παρακάτω πρόγραμμα στο `Program.cs` και εκτελέστε το. Δείχνει ολόκληρη τη ροή **create word document programmatically**, συμπεριλαμβανομένου του χειρισμού σφαλμάτων.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        try
        {
            // 1️⃣ Initialise a new document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a CommandButton OLE control
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                new RectangleF(100, 100, 120, 30));

            // 3️⃣ Set button properties
            commandButton.OleFormat.OleObject.Caption = "Click Me";
            commandButton.OleFormat.OleObject.Name = "cmdClickMe";
            // Optional macro assignment (uncomment if needed)
            // commandButton.OleFormat.OleObject.MacroName = "MyMacro";

            // 4️⃣ Save the document
            string outputPath = @"C:\Temp\CommandButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"✅ Document created successfully at {outputPath}");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"❌ Error: {ex.Message}");
        }
    }
}
```

**Expected result:** Το άνοιγμα του `CommandButton.docx` στο Word εμφανίζει ένα κουμπί με την ετικέτα “Click Me”. Η τοποθέτηση του ποντικιού πάνω στο κουμπί αποκαλύπτει το όνομα `cmdClickMe` στο παράθυρο ιδιοτήτων.

## Common questions and troubleshooting

| Question | Answer |
|----------|--------|
| *Μπορώ να προσθέσω το κουμπί σε υπάρχον έγγραφο;* | Ναι. Φορτώστε το αρχείο με `new Document("Existing.docx")`, έπειτα χρησιμοποιήστε την ίδια κλήση `InsertForms2OleControl`. |
| *Τι μονάδες χρησιμοποιεί το `RectangleF`;* | Points (1 inch = 72 pt). Προσαρμόστε τις τιμές για ακριβή τοποθέτηση του κουμπιού. |
| *Θα λειτουργήσει το κουμπί σε Word για Mac;* | Οι έλεγχοι OLE υποστηρίζονται μόνο στο Word για Windows. Στο Mac το κουμπί εμφανίζεται ως στατική εικόνα. |
| *Χρειάζομαι άδεια για παραγωγική χρήση;* | Μια εμπορική άδεια αφαιρεί τα υδατογραφήματα αξιολόγησης και ξεκλειδώνει πλήρη λειτουργικότητα. |
| *Πώς μπορώ να αλλάξω το μέγεθος του κουμπιού μετά την εισαγωγή;* | Τροποποιήστε `commandButton.Width` και `commandButton.Height` ή επανεισάγετε με νέο `RectangleF`. |

## Extending the solution

Τώρα που ξέρετε πώς να **programmatically add command button** ελέγχους, μπορείτε να εξερευνήσετε τα παρακάτω σχετικά θέματα:

* **Εισαγωγή άλλων ελέγχων φόρμας** – χρησιμοποιήστε `ControlType.CheckBox`, `ControlType.OptionButton`, κ.λπ. (συμπεριλαμβάνει τη δευτερεύουσα λέξη-κλειδί *Aspose.Words InsertForms2OleControl*).  
* **Συμπλήρωση εγγράφου με δυναμικά δεδομένα** – συγχωνεύστε δεδομένα από βάση σε πίνακες ή πεδία mail‑merge.  
* **Εξαγωγή σε PDF** – μετά την προσθήκη του κουμπιού, καλέστε `doc.Save("output.pdf", SaveFormat.Pdf)` για να δημιουργήσετε έκδοση PDF (σχετικό με *C# Word automation*).  

## Conclusion

Τώρα έχετε ένα πλήρες, έτοιμο για παραγωγή πρότυπο για **create word document programmatically** και **programmatically add command button** χρησιμοποιώντας το Aspose.Words for .NET. Ο οδηγός κάλυψε τη ρύθμιση του έργου, την αρχικοποίηση του εγγράφου, την εισαγωγή του κουμπιού OLE, τη διαμόρφωση ιδιοτήτων και την αποθήκευση του αρχείου. Μη διστάσετε να προσαρμόσετε τον κώδικα για να εισάγετε άλλους ελέγχους φόρμας, να συνδέσετε macros ή να ενσωματώσετε τη λογική σε web services ή background jobs.

Καλή προγραμματιστική, και απολαύστε την αυτοματοποίηση εγγράφων Word!

## What Should You Learn Next?

Οι παρακάτω οδηγοί καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετα χαρακτηριστικά του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [Δημιουργία Εγγράφου Word με Aspose.Words – Οδηγός Βήμα‑Βήμα](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)
- [Δημιουργία Εγγράφου Word με Πίνακα Χρησιμοποιώντας Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [Δημιουργία Group Shape σε Έγγραφο Word Χρησιμοποιώντας Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}