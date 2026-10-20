---
category: general
date: 2026-10-20
description: Δημιουργήστε έγγραφο Word προγραμματιστικά και προσθέστε ένα κουμπί εντολής
  χρησιμοποιώντας το Aspose.Words. Μάθετε πώς να εισάγετε έναν έλεγχο ActiveX και
  να ορίσετε τη λεζάντα του κουμπιού.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add command button
- add activex control
- insert activex button
- set button caption
language: el
lastmod: 2026-10-20
og_description: Δημιουργήστε έγγραφο Word προγραμματιστικά και ενσωματώστε ένα κουμπί
  εντολής ActiveX. Αυτό το σεμινάριο εξηγεί πώς να εισάγετε τον έλεγχο και να ορίσετε
  τη λεζάντα του με το Aspose.Words.
og_image_alt: Word file showing an ActiveX command button inserted by Aspose.Words
og_title: Δημιουργία εγγράφου Word προγραμματιστικά – προσθήκη κουμπιού ActiveX
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  headline: Create Word document programmatically with an ActiveX button
  type: TechArticle
- description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  name: Create Word document programmatically with an ActiveX button
  steps:
  - name: 'Open a terminal or Visual Studio and create a new console project:'
    text: 'Open a terminal or Visual Studio and create a new console project:'
  - name: 'Add the Aspose.Words package:'
    text: 'Add the Aspose.Words package:'
  - name: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
    text: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
  - name: Open `ActiveXCommandButton.docx` in Microsoft Word.
    text: Open `ActiveXCommandButton.docx` in Microsoft Word.
  - name: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
    text: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
  - name: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
    text: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
  - name: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
    text: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Δημιουργία εγγράφου Word προγραμματιστικά με κουμπί ActiveX
url: /el/net/working-with-oleobjects-and-activex/create-word-document-programmatically-with-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία εγγράφου Word προγραμματιστικά με κουμπί ActiveX

Δημιουργήστε ένα έγγραφο Word προγραμματιστικά με το Aspose.Words και, στη συνέχεια, προσθέστε ένα κουμπί εντολής που οι χρήστες μπορούν να πατήσουν. Αυτός ο οδηγός σας καθοδηγεί στη εισαγωγή ενός ελέγχου ActiveX, στη διαμόρφωση των ιδιοτήτων του και στην αποθήκευση του αποτελέσματος ως αρχείο **.docx**.

Θα δείτε ένα πλήρες, εκτελέσιμο παράδειγμα που μπορείτε να αντιγράψετε σε μια εφαρμογή κονσόλας. Στο τέλος του tutorial θα μπορείτε να δημιουργήσετε ένα αρχείο Word που περιέχει ένα πλήρως λειτουργικό κουμπί εντολής και θα κατανοήσετε πώς να **προσθέσετε κουμπί εντολής**, **προσθέσετε έλεγχο ActiveX**, **εισάγετε κουμπί ActiveX** και **ορίσετε λεζάντα κουμπιού** χωρίς να φύγετε από τον κώδικα C#.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* .NET 6.0 SDK ή νεότερη έκδοση εγκατεστημένη  
* Visual Studio 2022 (ή οποιοδήποτε IDE συμβατό με C#)  
* Αρχείο άδειας χρήσης Aspose.Words for .NET (η δωρεάν δοκιμή λειτουργεί για αυτό το παράδειγμα)  
* Βασική εξοικείωση με τη γλώσσα C# και το σύστημα έργων .NET  

Δεν απαιτούνται επιπλέον πακέτα NuGet εκτός από το **Aspose.Words**, καθώς η υποστήριξη ActiveX είναι ενσωματωμένη στη βιβλιοθήκη.

## Βήμα 1: Ρύθμιση του έργου και προσθήκη Aspose.Words

1. Ανοίξτε ένα τερματικό ή το Visual Studio και δημιουργήστε ένα νέο έργο κονσόλας:

   ```bash
   dotnet new console -n WordActiveXDemo
   cd WordActiveXDemo
   ```

2. Προσθέστε το πακέτο Aspose.Words:

   ```bash
   dotnet add package Aspose.Words
   ```

3. (Προαιρετικά) Εάν διαθέτετε αρχείο άδειας, τοποθετήστε το στη ρίζα του έργου και προσθέστε την παρακάτω γραμμή στην αρχή του `Program.cs` για να αποφύγετε τα υδατογράμματα αξιολόγησης:

   ```csharp
   Aspose.Words.License license = new Aspose.Words.License();
   license.SetLicense("Aspose.Words.lic");
   ```

## Βήμα 2: Δημιουργία εγγράφου Word προγραμματιστικά – αρχικοποίηση του εγγράφου

Η πρώτη ενέργεια είναι η **δημιουργία εγγράφου Word προγραμματιστικά**. Το κάνετε δημιουργώντας ένα αντικείμενο `Document` και έναν `DocumentBuilder` που σας επιτρέπει να επεξεργάζεστε το περιεχόμενο του εγγράφου.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;   // Provides ActiveX control types
using System.Drawing;        // For Point and Size structs

// Initialize a new blank document
Document document = new Document();

// DocumentBuilder gives a cursor‑based API for inserting elements
DocumentBuilder builder = new DocumentBuilder(document);
```

Το `Document` αντιπροσωπεύει ολόκληρο το αρχείο, ενώ ο `DocumentBuilder` διατηρεί έναν κέρσορα που μπορείτε να μετακινήσετε σε οποιαδήποτε θέση του εγγράφου. Αυτή η διάσπαση διατηρεί το API καθαρό και σας επιτρέπει να **προσθέσετε έλεγχο ActiveX** αργότερα χωρίς να διαχειρίζεστε χειροκίνητα δομές χαμηλού επιπέδου.

## Βήμα 3: Προσθήκη κουμπιού εντολής – εισαγωγή ελέγχου ActiveX

Τώρα θα **προσθέσετε κουμπί εντολής** εισάγοντας έναν έλεγχο ActiveX τύπου `OleControlType.CommandButton`. Η μέθοδος `InsertForms2OleControl` απαιτεί τον τύπο του ελέγχου, μια θέση (`Point`) και ένα μέγεθος (`Size`).

```csharp
// Define where the button will appear (X = 100 pt, Y = 150 pt)
Point buttonPosition = new Point(100, 150);

// Define the button dimensions (width = 120 pt, height = 30 pt)
Size buttonSize = new Size(120, 30);

// Insert the ActiveX command button at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton, // control type
    buttonPosition,              // position
    buttonSize);                 // size
```

Η παραπάνω κλήση **εισάγει κουμπί ActiveX** στο έγγραφο στις ακριβείς συντεταγμένες που καθορίζετε. Οι συντεταγμένες μετρώνται σε σημεία (1 pt ≈ 1/72 in). Εάν χρειάζεστε το κουμπί σε συγκεκριμένη παράγραφο, μετακινήστε πρώτα τον κέρσορα του builder:

```csharp
builder.Writeln("Click the button below:");
builder.MoveToDocumentEnd(); // places the cursor after the paragraph
```

## Βήμα 4: Ορισμός λεζάντας κουμπιού – προσαρμογή του κειμένου του κουμπιού εντολής

Ένα κουμπί χωρίς ετικέτα είναι συγκεχυμένο, γι' αυτό θα **ορίσετε λεζάντα κουμπιού** σε κάτι περιγραφικό. Η ιδιότητα `Caption` ορίζει το κείμενο που εμφανίζεται στο κουμπί, ενώ η `Name` δίνει στον έλεγχο έναν προγραμματιστικό αναγνωριστικό.

```csharp
// Give the button a unique name for later reference
commandButton.Name = "btnSubmit";

// Set the visible text on the button
commandButton.Caption = "Submit";

// Optional: assign a macro name that Word will call when the button is clicked
commandButton.OnClick = "SubmitForm()";
```

Εάν αργότερα εξάγετε το έγγραφο σε μορφή με μακροεντολές (`.docm`), η τιμή `OnClick` πρέπει να ταιριάζει με το όνομα μιας μακροεντολής VBA. Για ένα απλό `.docx`, η ιδιότητα αποθηκεύεται αλλά δεν εκτελείται, κάτι που είναι αποδεκτό για τις περισσότερες περιπτώσεις αυτοματοποίησης.

## Βήμα 5: Αποθήκευση του εγγράφου που περιέχει το κουμπί ActiveX

Αφού διαμορφώσετε τον έλεγχο, μπορείτε να **αποθηκεύσετε το έγγραφο**. Επιλέξτε έναν φάκελο στον οποίο έχετε δικαίωμα εγγραφής και χρησιμοποιήστε την επέκταση `.docx` για μέγιστη συμβατότητα.

```csharp
// Replace with your desired output folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ActiveXCommandButton.docx");

// Save the document to disk
document.Save(outputPath);
```

Όταν ανοίξετε το παραγόμενο αρχείο στο Microsoft Word, θα δείτε ένα κουμπί με την ετικέτα **Submit** στις συντεταγμένες που καθορίσατε. Κάνοντας κλικ στο κουμπί στην επιφάνεια εργασίας, θα προσπαθήσει να εκτελέσει τη μακροεντολή `SubmitForm` (εφόσον υπάρχει).

## Βήμα 6: Επαλήθευση του αποτελέσματος και αντιμετώπιση κοινών προβλημάτων

1. Ανοίξτε το `ActiveXCommandButton.docx` στο Microsoft Word.  
2. Μεταβείτε σε **Λειτουργία Σχεδίασης** (καρτέλα Developer → **Λειτουργία Σχεδίασης**) για να δείτε τα περιγράμματα του κουμπιού.  
3. Εάν το κουμπί δεν εμφανίζεται, ελέγξτε ότι η καρτέλα **Developer** είναι ενεργοποιημένη και ότι η έκδοση του Word υποστηρίζει ελέγχους ActiveX.  
4. Για αρχεία με μακροεντολές (`.docm`), βεβαιωθείτε ότι το όνομα της μακροεντολής στο `OnClick` ταιριάζει με μια ρουτίνα VBA· διαφορετικά το Word θα εμφανίσει προειδοποίηση ασφαλείας.

### Συμβουλή επαγγελματία

Οι έλεγχοι ActiveX λειτουργούν μόνο σε Windows. Εάν χρειάζεστε διαπλατφορμική αλληλεπίδραση, σκεφτείτε τη χρήση **Content Controls** (`RichTextContentControl`) αντί για κουμπί ActiveX.

## Πλήρης κώδικας

Παρακάτω βρίσκεται το πλήρες, έτοιμο‑για‑εκτέλεση πρόγραμμα. Αντιγράψτε το στο `Program.cs` και εκτελέστε `dotnet run`.

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Optional: apply a license to remove evaluation watermarks
        // var license = new Aspose.Words.License();
        // license.SetLicense("Aspose.Words.lic");

        // Step 2: Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a paragraph to give context
        builder.Writeln("Please click the button below to submit the form:");
        builder.MoveToDocumentEnd();

        // Step 3: Add command button – insert ActiveX control
        Point position = new Point(100, 150);
        Size size = new Size(120, 30);
        Forms2OleControl commandButton = builder.InsertForms2OleControl(


## Τι Θα Μάθετε Στη Στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Δημιουργία εγγράφου Word με κουμπί ActiveX – Οδηγός C#](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)
- [Προσθήκη κουμπιού εντολής σε έγγραφο Word με Aspose.Words – Πλήρης Οδηγός](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)
- [Δημιουργία κουμπιού σε έγγραφο Word με Aspose.Words – Πλήρες Παράδειγμα Κώδικα](/words/english/net/working-with-oleobjects-and-activex/create-word-document-button-with-aspose-words-full-code-exam/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}