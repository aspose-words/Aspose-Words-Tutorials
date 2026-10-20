---
category: general
date: 2026-08-07
description: Μάθετε πώς να προσθέσετε έναν έλεγχο ActiveX σε ένα έγγραφο Word χρησιμοποιώντας
  C#. Περιλαμβάνει τη σύνδεση μιας μακροεντολής με κουμπί και την προσθήκη παραδειγμάτων
  κλικ‑πλήσιμου κουμπιού στο Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex control
- associate macro with button
- add clickable button word
- add command button word
language: el
lastmod: 2026-08-07
og_description: πώς να προσθέσετε έλεγχο ActiveX σε ένα έγγραφο Word χρησιμοποιώντας
  το Aspose.Words. Ακολουθήστε αυτόν τον οδηγό για να εισαγάγετε ένα κουμπί, να συσχετίσετε
  μακροεντολή με το κουμπί και να προσθέσετε κλικ‑δυνατό κουμπί στο Word.
og_image_alt: Screenshot showing a Word document with an ActiveX command button inserted
  via Aspose.Words
og_title: πώς να προσθέσετε έλεγχο ActiveX στο Word – πλήρες σεμινάριο C#
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Learn how to add activex control in a Word document using C#. Includes
    associate macro with button and add clickable button word examples.
  headline: how to add activex control in Word with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Learn how to add activex control in a Word document using C#. Includes
    associate macro with button and add clickable button word examples.
  name: how to add activex control in Word with Aspose.Words – step‑by‑step guide
  steps:
  - name: Why each line matters
    text: '| Line | Purpose | |------|---------| | `Document doc = new Document();`
      | Instantiates a fresh Word package in memory. | | `DocumentBuilder builder
      = new DocumentBuilder(doc);` | Provides a fluent API for inserting content,
      including ActiveX controls. | | `InsertForms2OleControl` | The only Aspose.'
  - name: Common pitfalls when associating a macro
    text: '* **Macro security settings** – If the document is opened on a machine
      with strict security policies, the macro may be blocked. Provide instructions
      to lower the security level or sign the macro. * **Naming conflicts** – The
      macro name must be unique within the document’s VBA project; otherwise Word'
  - name: 'Edge case: Long captions'
    text: Word truncates captions that exceed the button’s width. To avoid clipping,
      either increase the width argument in `InsertForms2OleControl` or shorten the
      text. Testing with different languages (e.g., German or Japanese) is advisable
      because character width varies.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Πώς να προσθέσετε έλεγχο ActiveX στο Word με το Aspose.Words – βήμα‑βήμα οδηγός
url: /el/net/working-with-oleobjects-and-activex/how-to-add-activex-control-in-word-with-aspose-words-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# πώς να προσθέσετε έλεγχο ActiveX σε Word με Aspose.Words

Αν χρειάζεστε **πώς να προσθέσετε έλεγχο ActiveX** σε αρχείο Microsoft Word προγραμματιστικά, αυτό το tutorial σας δείχνει τα ακριβή βήματα χρησιμοποιώντας το Aspose.Words για .NET. Θα δείτε πώς να εισάγετε ένα κουμπί εντολής, να ορίσετε τη λεζάντα του και **να συσχετίσετε μακροεντολή με το κουμπί** ώστε ο έλεγχος να αντιδρά όταν ο χρήστης κάνει κλικ. Στο τέλος θα έχετε ένα αρχείο `.docm` με ενεργοποιημένη μακροεντολή που περιέχει ένα πλήρως λειτουργικό κουμπί.

Η προσθήκη ενός κουμπιού ActiveX είναι συχνή απαίτηση όταν δημιουργείτε διαδραστικά πρότυπα όπως αιτήσεις δανείου, φόρμες ενσωμάτωσης υπαλλήλων ή αυτοματοποιημένες αναφορές. Αυτός ο οδηγός περνάει από κάθε γραμμή κώδικα, εξηγεί **γιατί** κάθε βήμα είναι σημαντικό και καλύπτει τα τυπικά προβλήματα που μπορεί να συναντήσετε.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* .NET 6 (ή .NET Core 3.1 / .NET Framework 4.8) εγκατεστημένο.
* Ένα έγκυρο license του Aspose.Words για .NET ή ένα προσωρινό κλειδί αξιολόγησης.
* Visual Studio 2022 (ή οποιοδήποτε IDE που υποστηρίζει C#).
* Βασική εξοικείωση με μακροεντολές Word (VBA) αν σκοπεύετε να γράψετε τη μακροεντολή που θα ενεργοποιεί το κουμπί.

> **Pro tip:** Όταν εκτελείτε το δείγμα, αποθηκεύστε το αποτέλεσμα σε φάκελο στον οποίο έχετε δικαιώματα εγγραφής, διαφορετικά το `doc.Save` θα πετάξει εξαίρεση.

## Πώς να προσθέσετε έλεγχο ActiveX σε έγγραφο Word χρησιμοποιώντας Aspose.Words

Ο πυρήνας της λύσης είναι ένα σύντομο πρόγραμμα C# που δημιουργεί ένα νέο έγγραφο, εισάγει έναν έλεγχο ActiveX **CommandButton** και αποθηκεύει το αρχείο ως έγγραφο με ενεργοποιημένη μακροεντολή (`.docm`). Ο κώδικας είναι πλήρης και έτοιμος για αντιγραφή‑επικόλληση.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert an ActiveX CommandButton control (Forms2OleControl)
        // Parameters: control type, left, top, width, height (in points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            0,   // left position (points)
            0,   // top position (points)
            150, // width (points)
            30   // height (points)
        );

        // Step 3: Set the button's visible caption – this is the add clickable button word
        commandButton.Caption = "Click Me";

        // Step 4 (optional): Associate a macro with the button's click action
        // This demonstrates how to associate macro with button
        commandButton.OnAction = "MyMacro";

        // Step 5: Save the document as a macro‑enabled file to preserve the button reference
        // The file extension .docm tells Word to keep ActiveX controls and macros
        doc.Save("CommandButton.docm");
    }
}
```

### Γιατί κάθε γραμμή είναι σημαντική

| Γραμμή | Σκοπός |
|------|---------|
| `Document doc = new Document();` | Δημιουργεί ένα νέο πακέτο Word στη μνήμη. |
| `DocumentBuilder builder = new DocumentBuilder(doc);` | Παρέχει μια ευέλικτη API για την εισαγωγή περιεχομένου, συμπεριλαμβανομένων των ελέγχων ActiveX. |
| `InsertForms2OleControl` | Η μοναδική μέθοδος του Aspose.Words που δημιουργεί έναν έλεγχο ActiveX· καθορίζετε τον τύπο ελέγχου (`CommandButton`) και τη γεωμετρία του. |
| `commandButton.Caption = "Click Me";` | Ορίζει το **κείμενο του κουμπιού** που βλέπει ο τελικός χρήστης. Χωρίς λεζάντα το κουμπί εμφανίζεται κενό. |
| `commandButton.OnAction = "MyMacro";` | **συσχέτιση μακροεντολής με το κουμπί** – λέει στο Word ποια μακροεντολή VBA να εκτελέσει όταν ο έλεγχος κλικάρεται. |
| `doc.Save("CommandButton.docm");` | Αποθηκεύει το έγγραφο ως αρχείο macro‑enabled· ένα κανονικό `.docx` θα αφαιρέσει τον έλεγχο και τη μακροεντολή. |

> **Σημείωση:** Οι συντεταγμένες (αριστερά, πάνω) μετρώνται σε σημεία (1 pt ≈ 1/72 in). Προσαρμόστε τις ώστε να τοποθετήσετε το κουμπί εκεί που χρειάζεστε στη σελίδα.

## Πώς να συσχετίσετε μακροεντολή με το κουμπί

Η ιδιότητα `OnAction` συνδέει το κουμπί με μια μακροεντολή VBA με όνομα `MyMacro`. Πρέπει ακόμη να δημιουργήσετε αυτή τη μακροεντολή μέσα στο αρχείο Word, είτε χειροκίνητα είτε ενσωματώνοντας κώδικα VBA προγραμματιστικά (το Aspose.Words δεν γράφει κώδικα VBA). Ακολουθεί μια ελάχιστη μακροεντολή που μπορείτε να προσθέσετε χρησιμοποιώντας τον επεξεργαστή **Developer → Visual Basic** του Word:

```vba
Sub MyMacro()
    MsgBox "Button clicked!", vbInformation, "ActiveX Demo"
End Sub
```

Όταν ο χρήστης ανοίξει το `CommandButton.docm` και κάνει κλικ στο κουμπί, το Word εκτελεί το `MyMacro` και εμφανίζει ένα παράθυρο μηνύματος. Αν η ασφάλεια μακροεντολών είναι ορισμένη σε **Disable all macros without notification**, το κουμπί θα εμφανιστεί απενεργοποιημένο. Συμβουλέψτε τους χρήστες να ενεργοποιήσουν τις μακροεντολές για το έγγραφο ή να υπογράψουν τη μακροεντολή με αξιόπιστο πιστοποιητικό.

### Συνηθισμένα προβλήματα κατά τη συσχέτιση μιας μακροεντολής

* **Ρυθμίσεις ασφαλείας μακροεντολών** – Αν το έγγραφο ανοιχτεί σε υπολογιστή με αυστηρές πολιτικές ασφαλείας, η μακροεντολή μπορεί να μπλοκαριστεί. Παρέχετε οδηγίες για μείωση του επιπέδου ασφαλείας ή υπογραφή της μακροεντολής.
* **Σύγκρουση ονομάτων** – Το όνομα της μακροεντολής πρέπει να είναι μοναδικό μέσα στο VBA project του εγγράφου· διαφορετικά το Word θα εμφανίσει σφάλμα “duplicate procedure name”.
* **64‑bit vs 32‑bit Word** – Οι έλεγχοι ActiveX λειτουργούν το ίδιο, αλλά ο επεξεργαστής VBA μπορεί να εμφανίσει διαφορετικά προειδοποιητικά μηνύματα ανάλογα με την έκδοση του Office.

## Πώς να προσθέσετε κείμενο κλικ-κουμπιού σε φόρμα Word

Η ιδιότητα `Caption` είναι αυτό που βλέπουν οι χρήστες στο κουμπί. Μπορείτε να την προσαρμόσετε περαιτέρω:

```csharp
commandButton.Caption = "Submit Form";
commandButton.Font.Size = 10;      // Adjust font size
commandButton.Font.Name = "Arial"; // Choose a readable font
```

Αν χρειάζεστε τη λεζάντα να αλλάζει δυναμικά βάσει εισόδου χρήστη, μπορείτε αργότερα να έχετε πρόσβαση στον έλεγχο μέσω του μοντέλου αντικειμένων του Word:

```vba
Sub UpdateButtonCaption()
    Dim btn As InlineShape
    Set btn = ActiveDocument.InlineShapes(1).OLEFormat.Object
    btn.Caption = "Updated Text"
End Sub
```

### Ακραία περίπτωση: Μακριές λεζάντες

Το Word περικόπτει τις λεζάντες που υπερβαίνουν το πλάτος του κουμπιού. Για να αποφύγετε το κόψιμο, είτε αυξήστε το όρισμα πλάτους στο `InsertForms2OleControl` είτε συντομεύστε το κείμενο. Συνίσταται δοκιμή με διαφορετικές γλώσσες (π.χ. Γερμανικά ή Ιαπωνικά) επειδή το πλάτος των χαρακτήρων διαφέρει.

## Πώς να προσθέσετε λέξη κουμπιού εντολής για αυτοματοποίηση φόρμας

Πέρα από τη οπτική λεζάντα, η έννοια **προσθήκη λέξης κουμπιού εντολής** καλύπτει το προγραμματιστικό όνομα του ελέγχου. Το Aspose.Words δεν εκθέτει άμεση ιδιότητα `Name` για ελέγχους ActiveX, αλλά μπορείτε να ορίσετε το πεδίο `AltText`, το οποίο το Word θεωρεί ως ταυτότητα του ελέγχου:

```csharp
commandButton.AltText = "SubmitButton";
```

Αργότερα στο VBA μπορείτε να αναφερθείτε στο κουμπί με την τιμή του `AltText`:

```vba
Sub FindButton()
    Dim shp As Shape
    For Each shp In ActiveDocument.Shapes
        If shp.AlternativeText = "SubmitButton" Then
            MsgBox "Found the Submit button!"
        End If
    Next shp
End Sub
```

Αυτή η τεχνική είναι χρήσιμη όταν έχετε πολλαπλά κουμπιά και χρειάζεται να τα διακρίνετε προγραμματιστικά.

## Πλήρες λειτουργικό παράδειγμα

Παρακάτω βρίσκεται το πλήρες πρόγραμμα που μπορείτε να μεταγλωττίσετε και να εκτελέσετε ως εφαρμογή κονσόλας. Περιλαμβάνει προαιρετικό στυλ, συσχέτιση μακροεντολής και ένα μπλοκ σχολίων που περιγράφει κάθε βήμα.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class AddActiveXButton
{
    static void Main()
    {
        // 1️⃣ Create a new document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert an ActiveX CommandButton.
        //    left=50pt, top=100pt places the button away from the margin.
        Forms2OleControl btn = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            50,   // left
            100,  // top
            200,  // width
            40    // height
        );

        // 3️⃣ Add clickable button word (caption) and style it.
        btn.Caption = "Submit Form";
        btn.Font.Size = 11;
        btn.Font.Name = "Calibri";

        // 4️⃣ Associate macro with button – this is how to associate macro with button.
        btn.OnAction = "SubmitMacro";

        // 5️⃣ Give the control a friendly identifier (add command button word).
        btn.AltText = "SubmitButton";

        // 6️⃣ Save as macro‑enabled document.
        doc.Save("SubmitForm.docm");
    }
}
```

**Αναμενόμενο αποτέλεσμα:** Το άνοιγμα του `SubmitForm.docm` στο Microsoft Word εμφανίζει ένα κουμπί με μπλε περίγραμμα με την ετικέτα *Submit Form*. Κάνοντας κλικ στο κουμπί ενεργοποιείται η μακροεντολή VBA `SubmitMacro` (εφόσον προσθέσατε τη μακροεντολή στο έγγραφο). Το κουμπί μπορεί να μετακινηθεί, να αλλάξει μέγεθος ή να μορφοποιηθεί περαιτέρω χρησιμοποιώντας το ίδιο αντικείμενο `Forms2OleControl`.

## Δοκιμή της λύσης

1. Κατασκευάστε και εκτελέστε την εφαρμογή κονσόλας C#.
2. Ανοίξτε το παραγόμενο `SubmitForm.docm` στο Word.
3. Εάν σας ζητηθεί, ενεργοποιήστε τις μακροεντολές.
4. Κάντε κλικ στο κουμπί *Submit Form* – θα πρέπει να δείτε το παράθυρο μηνύματος που ορίζεται στο `SubmitMacro`.

Αν το κουμπί εμφανίζεται αλλά δεν κάνει τίποτα, ελέγξτε ξανά ότι το όνομα της μακροεντολής ταιριάζει ακριβώς (`SubmitMacro`) και ότι η ασφάλεια μακροεντολών δεν εμποδίζει την εκτέλεση.

## Συχνές ερωτήσεις

| Ερώτηση | Απάντηση |
|----------|--------|
| *Μπορώ να προσθέσω περισσότερα από ένα κουμπί ActiveX;* | Ναι. Καλέστε το `InsertForms2OleControl` πολλές φορές με διαφορετικές συντεταγμένες. Χρησιμοποιήστε διαφορετικές τιμές `OnAction` και `AltText` για να τα διακρίνετε. |
| *Είναι ο έλεγχος ActiveX ορατός στο Word Online;* | Όχι. |

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετικές θεματικές που επεκτείνουν τις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Προσθήκη Περιεχομένου Χρησιμοποιώντας Document Builder στο Aspose.Words για .NET](/words/english/net/add-content-using-document-builder/)
- [Aspose.Words Shape Shadow Tutorial – Προσθήκη Σκιάς σε Σχήμα Word σε C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Προσθήκη Νέας Ενότητας σε Έγγραφο Word | Aspose.Words για .NET](/words/english/net/document-sections/add-section/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}