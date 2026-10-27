---
category: general
date: 2026-09-27
description: Δημιουργήστε προγραμματιστικά ένα έγγραφο Word με ένα ομαδοποιημένο σχήμα
  χρησιμοποιώντας το Aspose.Words σε C#. Ακολουθήστε αυτόν τον οδηγό βήμα‑βήμα για
  να δημιουργήσετε το αρχείο και να μάθετε χρήσιμες συμβουλές.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically create word document
- how to create group shape word
- Aspose.Words group shape
- C# Word automation
- StructuredDocumentTag example
language: el
lastmod: 2026-09-27
og_description: Δημιουργήστε προγραμματιστικά ένα έγγραφο Word με μια ομάδα σχημάτων
  χρησιμοποιώντας το Aspose.Words. Αυτό το σεμινάριο σας καθοδηγεί μέσα από τον πλήρη
  κώδικα C#, εξηγεί κάθε βήμα και εμφανίζει το τελικό αποτέλεσμα.
og_image_alt: Screenshot of a Word document containing a group shape with a text placeholder
og_title: Προγραμματιστική δημιουργία εγγράφου Word με ομαδικό σχήμα – Οδηγός C#
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Programmatically create a Word document with a group shape using Aspose.Words
    in C#. Follow this step‑by‑step guide to generate the file and learn useful tips.
  headline: Programmatically create a Word document with a group shape
  type: TechArticle
- description: Programmatically create a Word document with a group shape using Aspose.Words
    in C#. Follow this step‑by‑step guide to generate the file and learn useful tips.
  name: Programmatically create a Word document with a group shape
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code also works with .NET Framework 4.7+). - Aspose.Words
      for .NET NuGet package (`Install-Package Aspose.Words`). - A C# IDE such as
      Visual Studio 2022 or VS Code with the C# extension.'
  - name: Expected output screenshot (conceptual)
    text: '``` +-----------------------------------------------------------+ | ┌───────────────────────────────────────────────┐
      | | │ [Enter text here] │ | | └───────────────────────────────────────────────┘
      | +-----------------------------------------------------------+ ```'
  - name: Adding more child shapes
    text: 'You can enrich the group by appending additional drawing objects, such
      as pictures or text boxes:'
  - name: Controlling wrapping style
    text: 'If you need the group shape to stay behind text or to have tight wrapping,
      set the `WrapType` property:'
  - name: 'Edge case: Empty group shape'
    text: A `GroupShape` without children renders as an invisible placeholder. Always
      verify that at least one child (e.g., an SDT or a picture) is added; otherwise
      Word may drop the group during saving.
  - name: Compatibility note
    text: Aspose.Words 23.10+ fully supports `GroupShape` and `StructuredDocumentTag`.
      If you target older versions, the `AppendChild` method may behave differently,
      and you might need to call `UpdatePageLayout` after saving.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Προγραμματιστική δημιουργία εγγράφου Word με ομαδικό σχήμα
url: /el/net/programming-with-shapes/programmatically-create-a-word-document-with-a-group-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία Word εγγράφου προγραμματιστικά με group shape

Αν χρειάζεστε **να δημιουργήσετε προγραμματιστικά ένα Word έγγραφο** που περιέχει μια ομαδοποιημένη σχεδίαση, αυτός ο οδηγός σας δείχνει ακριβώς πώς να το κάνετε με το Aspose.Words for .NET. Είτε δημιουργείτε έναν γεννήτορα συμβάσεων, έναν κατασκευαστή αναφορών, είτε ένα εργαλείο συμπλήρωσης φορμών, θα μάθετε τον πλήρη κώδικα C#, γιατί κάθε κλήση API είναι σημαντική και πώς να αντιμετωπίζετε κοινές ακραίες περιπτώσεις.

Η δημιουργία ενός ομαδοποιημένου σχήματος στο Word μπορεί να φαίνεται δύσκολη επειδή το μοντέλο αντικειμένων του Word αντιμετωπίζει τα group shapes ως containers για άλλα αντικείμενα σχεδίασης. Αυτό το tutorial δεν απαντά μόνο στο **πώς να δημιουργήσετε group shape word** έγγραφα, αλλά επίσης δείχνει πώς να ενσωματώσετε ένα plain‑text StructuredDocumentTag (SDT) μέσα στην ομάδα ώστε το σχήμα να μπορεί να περιέχει επεξεργάσιμο περιεχόμενο.

## Τι θα επιτύχετε

- Αρχικοποίηση ενός νέου κεντρικού Word εγγράφου με `Document` και `DocumentBuilder`.
- Εισαγωγή ενός `GroupShape` στην τρέχουσα θέση του δρομέα.
- Προσθήκη ενός plain‑text `StructuredDocumentTag` (SDT) στο group shape.
- Αποθήκευση του αρχείου ως `.docx` που μπορεί να ανοιχθεί στο Microsoft Word.
- Κατανόηση των βασικών ιδιοτήτων του `GroupShape` και του `StructuredDocumentTag` για μελλοντικές επεκτάσεις.

### Προαπαιτούμενα

- .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.7+).
- Πακέτο NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`).
- Ένα IDE C# όπως το Visual Studio 2022 ή το VS Code με την επέκταση C#.

---

## Δημιουργία Word εγγράφου προγραμματιστικά – ρύθμιση του έργου

1. **Δημιουργήστε ένα νέο κονσολικό έργο**  
   ```bash
   dotnet new console -n WordGroupShapeDemo
   cd WordGroupShapeDemo
   dotnet add package Aspose.Words
   ```
2. **Ανοίξτε το έργο στο IDE σας** και αντικαταστήστε το περιεχόμενο του `Program.cs` με τον κώδικα που φαίνεται στις επόμενες ενότητες.

> **Συμβουλή:** Κρατήστε το φάκελο του έργου σας καθαρό· το Aspose.Words γράφει το αρχείο εξόδου στον τρέχοντα φάκελο εργασίας εκτός εάν παρέχετε απόλυτη διαδρομή.

## Βήμα 1: Αρχικοποίηση του εγγράφου και του builder

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;

// Create a new blank document.
Document doc = new Document();

// DocumentBuilder gives you a cursor to insert nodes.
DocumentBuilder builder = new DocumentBuilder(doc);

// Optional: set the page size or margins if your shape must fit a specific area.
builder.PageSetup.PageWidth = 595;   // A4 width in points
builder.PageSetup.PageHeight = 842;  // A4 height in points
```

**Γιατί είναι σημαντικό:**  
`Document` αντιπροσωπεύει ολόκληρο το αρχείο Word, ενώ το `DocumentBuilder` σας επιτρέπει να τοποθετείτε νέα στοιχεία χωρίς να περιηγηθείτε χειροκίνητα στο δέντρο κόμβων. Ο καθορισμός των διαστάσεων της σελίδας νωρίς εξασφαλίζει ότι το group shape δεν θα υπερβαίνει τη σελίδα.

## Βήμα 2: Εισαγωγή GroupShape στην τρέχουσα θέση του δρομέα

```csharp
// Create an empty GroupShape container.
GroupShape groupShape = new GroupShape(doc)
{
    // Give the group a size that comfortably holds its children.
    Width = 300,
    Height = 150,

    // Position the group relative to the page (you can also use RelativeHorizontalPosition).
    Left = 100,
    Top = 100
};

// Insert the group shape into the document where the builder is currently positioned.
builder.InsertNode(groupShape);
```

**Επεξήγηση:**  
Ένα `GroupShape` είναι ένα αντικείμενο σχεδίασης που μπορεί να περιέχει άλλα σχήματα, εικόνες ή πλαίσια κειμένου. Με τον καθορισμό των `Width`, `Height`, `Left` και `Top`, ελέγχετε την ακριβή του θέση στη σελίδα. Η μέθοδος `InsertNode` τοποθετεί το σχήμα στην κύρια ροή του εγγράφου, συμπεριφερόμενο ως αιωρούμενο αντικείμενο.

## Βήμα 3: Προσθήκη plain‑text StructuredDocumentTag (SDT) μέσα στην ομάδα

```csharp
// Create a plain‑text SDT that will act as a content placeholder.
StructuredDocumentTag sdtTag = new StructuredDocumentTag(doc, SdtType.PlainText, true)
{
    // Provide a helpful tag title that appears as a tooltip in Word.
    Title = "GroupShapeText",
    // Set default placeholder text.
    PlaceholderName = "Enter text here"
};

// Append the SDT to the group shape's child collection.
groupShape.AppendChild(sdtTag);
```

**Γιατί να χρησιμοποιήσετε SDT;**  
Τα StructuredDocumentTags είναι οι εγγενείς έλεγχοι περιεχομένου του Word. Επιτρέπουν στους χρήστες να επεξεργάζονται το κείμενο απευθείας στο αποθηκευμένο έγγραφο και μπορούν να προσπελαστούν προγραμματιστικά αργότερα για εξαγωγή δεδομένων. Η τοποθέτηση ενός SDT μέσα σε ένα group shape σας επιτρέπει να συνδυάσετε οπτική ομαδοποίηση με επεξεργάσιμο περιεχόμενο.

## Βήμα 4: Αποθήκευση του εγγράφου

```csharp
// Define the output path – replace with your desired directory.
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShapeDemo.docx");

// Save the document in DOCX format.
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved to: {outputPath}");
```

**Αποτέλεσμα:**  
Ανοίγοντας το `GroupShapeDemo.docx` στο Microsoft Word εμφανίζεται ένα αιωρούμενο ορθογώνιο (το group shape) που περιέχει έναν χώρο κράτησης κειμένου με την ένδειξη “Enter text here”. Οι χρήστες μπορούν να κάνουν κλικ μέσα στο σχήμα και να πληκτρολογήσουν απευθείας.

### Αναμενόμενη εικόνα εξόδου (εννοιολογική)

```
+-----------------------------------------------------------+
|   ┌───────────────────────────────────────────────┐   |
|   │  [Enter text here]                               │   |
|   └───────────────────────────────────────────────┘   |
+-----------------------------------------------------------+
```

Το εξωτερικό πλαίσιο είναι το `GroupShape`; η εσωτερική γκρι περιοχή είναι το `StructuredDocumentTag`.

---

## Πώς να δημιουργήσετε group shape word – πρόσθετες παραμέτρους

### Προσθήκη περισσότερων παιδικών σχημάτων

```csharp
// Example: add a picture inside the same group.
Shape picture = new Shape(doc, ShapeType.Image)
{
    ImageData = ImageData.FromFile("logo.png"),
    Width = 100,
    Height = 50,
    Left = 10,
    Top = 80
};
groupShape.AppendChild(picture);
```

### Έλεγχος στυλ περιτύλιξης

```csharp
groupShape.WrapType = WrapType.Inline; // Makes the shape behave like a paragraph.
```

### Ακραία περίπτωση: Κενό group shape

Ένα `GroupShape` χωρίς παιδιά εμφανίζεται ως αόρατο placeholder. Πάντα βεβαιωθείτε ότι έχει προστεθεί τουλάχιστον ένα παιδί (π.χ. ένα SDT ή μια εικόνα); διαφορετικά το Word μπορεί να αφαιρέσει την ομάδα κατά την αποθήκευση.

### Σημείωση συμβατότητας

Το Aspose.Words 23.10+ υποστηρίζει πλήρως το `GroupShape` και το `StructuredDocumentTag`. Εάν στοχεύετε σε παλαιότερες εκδόσεις, η μέθοδος `AppendChild` μπορεί να συμπεριφέρεται διαφορετικά και ίσως χρειαστεί να καλέσετε `UpdatePageLayout` μετά την αποθήκευση.

---

## Πλήρες εκτελέσιμο παράδειγμα

Αντιγράψτε ολόκληρο το παρακάτω απόσπασμα στο `Program.cs` και εκτελέστε το έργο. Ο κώδικας περιλαμβάνει όλα τα παραπάνω βήματα σε ένα ενιαίο, αυτόνομο πρόγραμμα.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.PageSetup.PageWidth = 595;
        builder.PageSetup.PageHeight = 842;

        // 2️⃣ Create and insert a GroupShape.
        GroupShape groupShape = new GroupShape(doc)
        {
            Width = 300,
            Height = 150,
            Left = 100,
            Top = 100
        };
        builder.InsertNode(groupShape);

        // 3️⃣ Add a plain‑text StructuredDocumentTag (SDT) inside the group.
        StructuredDocumentTag sdtTag = new StructuredDocumentTag(doc, SdtType.PlainText, true)
        {
            Title = "GroupShapeText",
            PlaceholderName = "Enter text here"
        };
        groupShape.AppendChild(sdtTag);

        // 4️⃣ Optional: add a picture to demonstrate multiple children.
        // Uncomment and adjust the path if you want to test this.
        /*
        Shape picture = new Shape(doc, ShapeType.Image)
        {
            ImageData = ImageData.FromFile("logo.png"),
            Width = 100,
            Height = 50,
            Left


## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κατακτήσετε πρόσθετες δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Δημιουργία Group Shape σε έγγραφο Word χρησιμοποιώντας Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Δημιουργία σχήματος ορθογωνίου στο Word με C# – Οδηγός βήμα‑βήμα](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Δημιουργία κεντρικού Word εγγράφου με Aspose.Words – Οδηγός βήμα‑βήμα](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}