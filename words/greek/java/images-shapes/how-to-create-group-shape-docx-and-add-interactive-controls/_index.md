---
category: general
date: 2026-09-05
description: Μάθετε πώς να δημιουργήσετε ομάδα σχημάτων σε docx, να εισάγετε κουμπί
  εντολής ActiveX και να φορτώσετε Markdown σε έγγραφο Word με ένα πλήρες παράδειγμα
  C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create group shape docx
- insert activex command button
- load markdown into word document
language: el
lastmod: 2026-09-05
og_description: Δημιουργήστε ένα group shape σε αρχείο docx, εισάγετε ένα κουμπί εντολής
  ActiveX και φορτώστε Markdown σε ένα έγγραφο Word χρησιμοποιώντας C#. Ακολουθήστε
  αυτόν τον βήμα‑βήμα οδηγό.
og_image_alt: Screenshot of a Word document showing a grouped shape and an ActiveX
  button
og_title: Δημιουργία ομαδικού σχήματος docx και ενσωμάτωση ελέγχων ActiveX – Οδηγός
  C#
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create group shape docx, insert ActiveX command button,
    and load Markdown into a Word document with a complete C# example.
  headline: How to create group shape docx and add interactive controls in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document automation
title: Πώς να δημιουργήσετε ομαδικό σχήμα docx και να προσθέσετε διαδραστικούς ελέγχους
  σε C#
url: /el/java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε group shape docx και να προσθέσετε διαδραστικούς ελέγχους σε C#

Αν χρειάζεστε να **create group shape docx** αρχεία προγραμματιστικά, αυτός ο οδηγός σας δείχνει ακριβώς πώς. Θα δείτε επίσης πώς να **insert ActiveX command button** ελέγχους και **load Markdown into a Word document** χωρίς να χάσετε τη μορφοποίηση υπογράμμισης. Στο τέλος του tutorial θα έχετε ένα πλήρως λειτουργικό `.docx` που συνδυάζει διανυσματικά γραφικά, διαδραστικά στοιχεία UI και περιεχόμενο βασισμένο σε markdown.

Αυτό το tutorial υποθέτει ότι έχετε ένα βασικό περιβάλλον ανάπτυξης C# και τη βιβλιοθήκη Aspose.Words for .NET εγκατεστημένη. Δεν απαιτούνται εξωτερικά εργαλεία — όλα εκτελούνται μέσα σε μια τυπική εφαρμογή .NET console ή desktop.

## Προαπαιτούμενα

- .NET 6.0 SDK ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.7+)
- Aspose.Words for .NET (πακέτο NuGet `Aspose.Words`)
- Ένα έγκυρο πιστοποιητικό X.509 (`.pfx`) αν θέλετε να δοκιμάσετε το βήμα υπογραφής
- Ένα αρχείο εικόνας (π.χ., `logo.png`) και ένα αρχείο markdown (`sample.md`) τοποθετημένα σε γνωστό φάκελο

> **Pro tip:** Κρατήστε όλα τα αρχεία εισόδου σε έναν ενιαίο φάκελο *resources* για να απλοποιήσετε τις σχετικές διαδρομές.

## Βήμα 1: Ρυθμίστε το έργο και εισάγετε τα ονόματα χώρων

Δημιουργήστε ένα νέο project console και προσθέστε τις απαιτούμενες οδηγίες `using`. Αυτό το τμήμα δείχνει επίσης πώς να αναφερθείτε στις κλάσεις Aspose.Words που θα χρησιμοποιήσετε αργότερα.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Loading;
using Aspose.Words.Saving;
using Aspose.Words.Saving.XpsSaveOptions; // only needed for signing example
using Aspose.Words.Saving.Signature;

// Ensure the license is applied if you have one
// Aspose.Words.License license = new Aspose.Words.License();
// license.SetLicense("Aspose.Words.lic");
```

Οι δηλώσεις `using` σας δίνουν άμεση πρόσβαση στα `Document`, `DocumentBuilder`, `GroupShape`, `Forms2OleControl` και άλλους τύπους που χρησιμοποιούνται σε όλο το tutorial.

## Βήμα 2: **Create group shape docx** – προσθέστε ένα ομαδοποιημένο σχήμα με στοιχεία-παιδιά

Ένα *group shape* σας επιτρέπει να αντιμετωπίζετε πολλαπλά αντικείμενα σχεδίασης ως μία ενιαία μονάδα. Αυτό είναι χρήσιμο για τη μετακίνηση ή την αλλαγή μεγέθους σχετικών γραφικών μαζί.

```csharp
// Initialize a new empty document
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a group shape container
GroupShape group = builder.InsertGroupShape();

// Add a rectangle (100 × 50 points) as the first child
Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);
group.AppendChild(rect);

// Add an ellipse (80 × 40 points) as the second child
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 40);
group.AppendChild(ellipse);

// Optional: set a fill color for visual distinction
rect.FillColor = System.Drawing.Color.LightBlue;
ellipse.FillColor = System.Drawing.Color.LightCoral;

// Save the intermediate document so you can inspect the group
document.Save("Output/GroupShape.docx");
```

**Γιατί ένα group shape;**  
Η ομαδοποίηση διατηρεί το ορθογώνιο και την έλλειψη ευθυγραμμισμένα όταν ο χρήστης τα σύρει στο Word. Επίσης απλοποιεί μεταγενέστερες λειτουργίες όπως η εφαρμογή κοινής περιγράμματος ή η μετακίνηση ολόκληρου του γραφικού προγραμματικά.

## Βήμα 3: Εισαγωγή ελέγχου περιεχομένου απλού κειμένου (placeholder για είσοδο χρήστη)

Οι έλεγχοι περιεχομένου παρέχουν στους τελικούς χρήστες μια δομημένη περιοχή για πληκτρολόγηση κειμένου. Το κείμενο placeholder εξαφανίζεται μόλις ο χρήστης αρχίσει να πληκτρολογεί.

```csharp
// Insert a plain‑text StructuredDocumentTag (SDT) after the group shape
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText, "MyTag");

// Set a friendly placeholder that appears in the UI
sdt.PlaceholderName = "Enter text here";

// Optionally, lock the content control to prevent deletion
sdt.LockContents = false;
sdt.LockContentControl = false;
```

Η ιδιότητα `PlaceholderName` είναι αυτό που εμφανίζει το Word ως ανοιχτό‑γκρι υπόδειγμα. Οι χρήστες μπορούν να το αντικαταστήσουν με το δικό τους κείμενο, και το υποκείμενο XML παραμένει σωστά δομημένο.

## Βήμα 4: **Insert ActiveX command button** – προσθέστε διαδραστικό UI στο έγγραφο

Οι έλεγχοι ActiveX υποστηρίζονται ακόμη σε σύγχρονα αρχεία Word και μπορούν να ενεργοποιούν μακροεντολές ή εξωτερικό αυτοματισμό. Παρακάτω προσθέτουμε ένα *command button* και ορίζουμε τη λεζάντα του.

```csharp
// Insert an ActiveX Forms2OleControl at the current cursor position
Forms2OleControl commandBtn = builder.InsertForms2OleControl();

// Define the control type as a command button
commandBtn.ControlType = Forms2OleControl.ControlType.CommandButton;

// Set the visible caption
commandBtn.Caption = "Click Me";

// Position the button relative to the page (optional)
commandBtn.Left = 150;   // points from the left margin
commandBtn.Top = 300;    // points from the top margin
```

**Πότε να χρησιμοποιήσετε ένα κουμπί ActiveX;**  
Αν διανέμετε το έγγραφο σε εταιρικό περιβάλλον που βασίζεται σε μακροεντολές VBA, ένα κουμπί ActiveX μπορεί να εκκινήσει μια μακροεντολή ή μια εξωτερική εφαρμογή. Για καθαρά HTML‑βασισμένη διαδραστικότητα, εξετάστε τη χρήση *content controls* με *Office.js*.

## Βήμα 5: Εισαγωγή κρυμμένης εικόνας (π.χ., λογότυπο) για branding ή μεταγενέστερη πρόσβαση μέσω script

Τα κρυμμένα σχήματα δεν εμφανίζονται στο εκτυπωμένο έγγραφο αλλά παραμένουν στο XML, επιτρέποντάς σας να τα ανακτήσετε προγραμματιστικά αργότερα.

```csharp
// Insert an image from disk
Shape logo = builder.InsertImage("Resources/logo.png");

// Hide the image from the view/layout
logo.Hidden = true;

// You can still reference the image via its ShapeId if needed
string logoId = logo.Name;
```

## Βήμα 6: **Load markdown into a Word document** ενώ διατηρείτε τη μορφοποίηση υπογράμμισης

Η Aspose.Words μπορεί να εισάγει απευθείας Markdown. Η ενεργοποίηση του `ImportUnderlineFormatting` εξασφαλίζει ότι οι υπογραμμίσεις markdown (`<u>` ή `__text__`) γίνονται στυλ υπογράμμισης του Word αντί για απλό κείμενο.

```csharp
// Configure markdown load options
MarkdownLoadOptions mdOptions = new MarkdownLoadOptions
{
    ImportUnderlineFormatting = true
};

// Load the markdown file into a new Document instance
Document markdownDoc = new Document("Resources/sample.md", mdOptions);

// Append the markdown content to the main document after the previous elements
builder.MoveToDocumentEnd();
builder.InsertDocument(markdownDoc, ImportFormatMode.KeepSourceFormatting);
```

**Edge case:** Αν το αρχείο markdown περιέχει πίνακες, αυτομάτως μετατρέπονται σε πίνακες Word. Αν χρειάζεστε προσαρμοσμένο στυλ πίνακα, εφαρμόστε έναν `DocumentBuilder` μετά την εισαγωγή.

## Βήμα 7: Υπογράψτε το έγγραφο με XAdES‑EPES (προαιρετικό βήμα ασφαλείας)

Οι ψηφιακές υπογραφές εγγυώνται την ακεραιότητα του εγγράφου. Ο παρακάτω κώδικας υπογράφει το **create group shape docx** αρχείο χρησιμοποιώντας προφίλ XAdES‑EPES.

```csharp
// Initialize the signature object for the current document
Signature signature = new Signature(document);

// Choose the XAdES‑EPES level
signature.XmlDsigLevel = XmlDsigLevel.XAdES_EPES;

// Sign using a .pfx certificate (replace path and password)
signature.Sign("Resources/cert.pfx", "password");

// Save the signed document
document.Save("Output/SignedGroupShape.docx");
```

> **Security note:** Κρατήστε τον κωδικό του πιστοποιητικού εκτός ελέγχου πηγαίου κώδικα. Χρησιμοποιήστε μεταβλητές περιβάλλοντος ή ασφαλή θησαυροφυλάκια σε παραγωγή.

## Πλήρες εκτελέσιμο παράδειγμα

Συνδυάζοντας όλα τα βήματα δημιουργείται ένα ενιαίο, αυτόνομο πρόγραμμα. Αποθηκεύστε το αρχείο ως `Program.cs` και εκτελέστε το από τη γραμμή εντολών.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Loading;
using Aspose.Words.Saving.Signature;

class Program
{
    static void Main()
    {
        // 1️⃣ Create the document and group shape
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        GroupShape group = builder.InsertGroupShape();
        group.AppendChild(builder.InsertShape(ShapeType.Rectangle, 100, 50));
        group.AppendChild(builder.InsertShape(ShapeType.Ellipse, 80, 40));

        // 2️⃣ Add a plain‑text content control
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            SdtType.PlainText, "MyTag");
        sdt.PlaceholderName = "Enter text here";

        // 3️⃣ Insert an ActiveX command button
        Forms2OleControl btn = builder.InsertForms2OleControl();
        btn.ControlType = Forms2OleControl.ControlType.CommandButton;
        btn.Caption = "Click Me";

        // 4️⃣ Insert a hidden logo image
        Shape logo = builder.InsertImage("Resources/logo.png");
        logo.Hidden = true;

        // 5️⃣ Load markdown while keeping underline formatting
        MarkdownLoadOptions mdOpts = new MarkdownLoadOptions
        {
            ImportUnderlineFormatting = true
        };
        Document mdDoc = new Document("Resources/sample.md", mdOpts);
        builder.MoveToDocumentEnd();
        builder.InsertDocument(mdDoc, ImportFormatMode.KeepSourceFormatting);

        // 6️⃣ Sign the document (optional)
        Signature sig = new Signature(doc);
        sig.XmlDsigLevel = XmlDsigLevel.XAdES_EPES;
        sig.Sign("Resources/cert.pfx", "password");

        // Save the final file
        doc.Save("Output/CompleteGroupShape.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

Η εκτέλεση του προγράμματος δημιουργεί το `CompleteGroupShape.docx` που περιέχει:

- Ένα ομαδοποιημένο ορθογώνιο + έλλειψη (ο πυρήνας του **create group shape docx**)
- Έναν έλεγχο περιεχομένου απλού κειμένου με κείμενο placeholder
- Ένα **insert ActiveX command button** με την ετικέτα “Click Me”
- Μια κρυφή εικόνα λογότυπου
- Περιεχόμενο markdown με διατηρημένες υπογραμμίσεις
- Μια ψηφιακή υπογραφή XAdES‑EPES (αν παρέχεται πιστοποιητικό)

## Συχνές ερωτήσεις και αντιμετώπιση προβλημάτων

| Ερώτηση | Απάντηση |
|---|---|
| **Θα λειτουργήσει το κουμπί ActiveX σε Word macOS;** | Το Word macOS δεν υποστηρίζει ελέγχους ActiveX. Το κουμπί θα εμφανιστεί ως στατική εικόνα. Χρησιμοποιήστε content controls με Office.js για διαδραστικότητα πολλαπλών πλατφορμών. |
| **Τι γίνεται αν το αρχείο markdown περιέχει προσαρμοσμένο CSS;** | Η Aspose.Words αγνοεί το CSS· επεξεργάζεται μόνο την τυπική σύνταξη markdown. Μετατρέψτε τα στοιχεία με CSS σε στυλ Word χειροκίνητα μετά την εισαγωγή. |
| **Μπορώ να προσθέσω περισσότερα σχήματα στην ίδια ομάδα αργότερα;** | Ναι. Ανακτήστε το `GroupShape` με το όνομα ή το δείκτη του, έπειτα καλέστε `AppendChild(newShape)`. Θυμηθείτε να αποθηκεύσετε ξανά το έγγραφο μετά τις τροποποιήσεις. |
| **Πώς αλλάζω τον αλγόριθμο υπογραφής;** | Ορίστε `signature.SignatureAlgorithm` πριν καλέσετε `Sign`. Η προεπιλογή είναι SHA‑256, που καλύπτει τις περισσότερες απαιτήσεις συμμόρφωσης. |
| **Είναι η κρυφή εικόνα ορατή στη διεπαφή του Word;** | Όχι, αλλά μπορεί να εμφανιστεί ενεργοποιώντας *Show hidden text* στις επιλογές του Word. Αυτό είναι χρήσιμο για αποθήκευση μεταδεδομένων χωρίς να γεμίζει τη διάταξη. |

## Επόμενα βήματα

Τώρα που μπορείτε να **create group shape docx**, **insert ActiveX command button** και **load markdown into a Word document**, μπορείτε να εξερευνήσετε:

- **Ενσωμάτωση VBA μακροεντολών** που αντιδρούν στο κλικ του κουμπιού ActiveX.
- **Εφαρμογή προσαρμοσμένων στυλ** στις παραγράφους που δημιουργούνται από markdown.
- **Δημιουργία PDF** από το ίδιο έγγραφο χρησιμοποιώντας `doc.Save("output.pdf", SaveFormat.Pdf)`.
- **Αυτοματοποίηση επεξεργασίας παρτίδας** πολλαπλών αρχείων markdown σε μια ενιαία αναφορά.

Αυτές οι επεκτάσεις σας επιτρέπουν να χτίσετε πλήρως αυτοματοποιημένες pipelines εγγράφων που συνδυάζουν πλούσια γραφικά, διαδραστικούς ελέγχους και περιεχόμενο βασισμένο σε markdown — όλα από C#.

---

*Καλή προγραμματιστική! Αν βρήκατε αυτό το tutorial

## Τι Θα Πρέπει Να Μάθετε Στη Σύντομη Μελλοντική?

Τα παρακάτω tutorials καλύπτουν στενά σχετικές θεματικές που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στην υλοποίηση των δικών σας έργων.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create markdown from word – Complete C# Guide](/words/english/java/document-conversion-and-export/create-markdown-from-word-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}