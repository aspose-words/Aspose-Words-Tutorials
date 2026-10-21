---
category: general
date: 2026-08-04
description: Αποθήκευση αρχείου docx προγραμματιστικά ενώ προσθέτετε σχήμα ορθογωνίου
  και ομαδοποιείτε σχήματα στο Word. Μάθετε πώς να ορίζετε τις διαστάσεις του σχήματος
  και να δημιουργείτε πλαίσιο κειμένου προγραμματιστικά.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save docx file
- add rectangle shape
- group shapes word
- set shape dimensions
- create textbox programmatically
language: el
lastmod: 2026-08-04
og_description: Αποθήκευση αρχείου docx χρησιμοποιώντας C# με προσθήκη σχήματος ορθογωνίου,
  ομαδοποίηση σχημάτων στο Word, ορισμό διαστάσεων σχήματος και δημιουργία πεδίου
  κειμένου προγραμματιστικά.
og_image_alt: Screenshot of a saved docx file that contains a grouped rectangle and
  textbox
og_title: Αποθήκευση αρχείου docx με ομαδοποιημένα σχήματα στο Word – Οδηγός βήμα‑βήμα
  για C#
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  headline: Save docx file with grouped shapes in Word using C#
  type: TechArticle
- description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  name: Save docx file with grouped shapes in Word using C#
  steps:
  - name: 1. Create a new document and a builder
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing; using Aspose.Words.Drawing.Shapes;'
  - name: 2. Add rectangle shape to a group
    text: '```csharp // Create a group container that will hold all shapes. GroupShape
      group = new GroupShape(doc) { Width = 400, // Set shape dimensions for the group.
      Height = 200 };'
  - name: 3. Group shapes in Word document
    text: The `GroupShape` class aggregates multiple drawing objects. Grouping is
      useful when you want to treat several objects as a single unit (e.g., moving,
      rotating, or copying them together).
  - name: 4. Set shape dimensions for precise layout
    text: Both the group and its child shapes need explicit dimensions; otherwise
      Word applies default sizes that may not match your design.
  - name: 5. Create textbox programmatically inside the group
    text: '```csharp // Add a textbox shape with custom text. Shape textBox = new
      Shape(doc, ShapeType.TextBox) { Width = 180, Height = 100, Left = 210, // Position
      relative to the group’s coordinate system. Top = 10 };'
  - name: 6. Insert group shape and **save docx file**
    text: '```csharp // Insert the completed group into the document at the current
      cursor position. builder.InsertNode(group);'
  - name: Expected output
    text: '* A file named **GroupShape.docx** appears in the output directory. * Opening
      the file shows a rectangular shape on the left and a textbox containing “Grouped
      text” on the right, both locked together. * Selecting either shape moves the
      entire group, confirming that **group shapes word** functionalit'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Αποθήκευση αρχείου docx με ομαδοποιημένα σχήματα στο Word χρησιμοποιώντας C#
url: /el/net/programming-with-shapes/save-docx-file-with-grouped-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Αποθήκευση αρχείου docx με ομαδοποιημένα σχήματα στο Word χρησιμοποιώντας C#

Αν χρειάζεστε να **αποθηκεύσετε αρχείο docx** που περιέχει αρκετά σχήματα τοποθετημένα μαζί, αυτός ο οδηγός σας δείχνει πώς να το κάνετε με C#. Θα μάθετε πώς να **προσθέσετε σχήμα ορθογωνίου**, να ομαδοποιήσετε πολλαπλά σχήματα σε ένα έγγραφο Word, **ορίσετε διαστάσεις σχήματος**, και **δημιουργήσετε πλαίσιο κειμένου προγραμματιστικά**. Η λύση λειτουργεί με την πιο πρόσφατη έκδοση του Aspose.Words for .NET και τρέχει σε .NET 6 ή νεότερο.

Ο οδηγός περνάει από κάθε βήμα, από τη ρύθμιση του έργου μέχρι την τελική κλήση `doc.Save`. Στο τέλος θα έχετε ένα επαναχρησιμοποιήσιμο κομμάτι κώδικα που μπορείτε να επικολλήσετε σε οποιοδήποτε έργο console ή ASP.NET. Δεν απαιτούνται εξωτερικά scripts ή χειροκίνητη επεξεργασία του αρχείου DOCX.

## Προαπαιτούμενα

* .NET 6 SDK (ή νεότερο) εγκατεστημένο.
* Ένα έγκυρο license για **Aspose.Words for .NET** (η δωρεάν δοκιμή λειτουργεί για δοκιμές).
* Visual Studio 2022, VS Code, ή οποιοδήποτε IDE που μπορεί να δημιουργήσει έργα .NET.

Ο κώδικας χρησιμοποιεί μόνο το namespace Aspose.Words, επομένως δεν απαιτούνται επιπλέον πακέτα NuGet.

## Αποθήκευση αρχείου docx με ομαδοποιημένα σχήματα στο Word

Ο πυρήνας της λύσης είναι η δημιουργία ενός `GroupShape` που περιέχει ένα ορθογώνιο και ένα πλαίσιο κειμένου, στη συνέχεια η εισαγωγή της ομάδας στο έγγραφο και η κλήση του `doc.Save`. Οι παρακάτω ενότητες χωρίζουν τη διαδικασία σε διαχειρίσιμα κομμάτια.

### 1. Δημιουργία νέου εγγράφου και builder

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // Initialize a blank document.
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for editing the document.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Γιατί είναι σημαντικό αυτό το βήμα* – Ένα νέο αντικείμενο `Document` αντιπροσωπεύει ένα κενό αρχείο *.docx*. Το `DocumentBuilder` παρέχει μεθόδους υψηλού επιπέδου όπως `InsertNode`, τις οποίες θα χρησιμοποιήσουμε για να τοποθετήσουμε το σχήμα ομάδας.

### 2. Προσθήκη σχήματος ορθογωνίου σε ομάδα

```csharp
        // Create a group container that will hold all shapes.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,   // Set shape dimensions for the group.
            Height = 200
        };

        // Add a rectangle shape that will be part of the group.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,   // Set shape dimensions for the rectangle.
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);
```

*Γιατί είναι σημαντικό αυτό το βήμα* – Η ενέργεια **add rectangle shape** δείχνει πώς να ορίσετε ένα οπτικό στοιχείο με ακριβές μέγεθος και θέση. Το ορθογώνιο βρίσκεται μέσα στο `group`, έτσι η μετακίνηση της ομάδας αργότερα μετακινεί αυτόματα το ορθογώνιο.

### 3. Ομαδοποίηση σχημάτων σε έγγραφο Word

Η κλάση `GroupShape` συγκεντρώνει πολλαπλά αντικείμενα σχεδίασης. Η ομαδοποίηση είναι χρήσιμη όταν θέλετε να αντιμετωπίζετε πολλά αντικείμενα ως μια ενιαία μονάδα (π.χ., μετακίνηση, περιστροφή ή αντιγραφή τους μαζί).

```csharp
        // The group now contains the rectangle; we will add more shapes next.
```

*Γιατί ομαδοποιούμε* – Η ομαδοποίηση μειώνει την πολυπλοκότητα της διάταξης. Αντί να τοποθετείτε κάθε σχήμα ξεχωριστά στη σελίδα, ρυθμίζετε μία φορά τις ιδιότητες `Left`, `Top`, `Width` και `Height` της ομάδας.

### 4. Ορισμός διαστάσεων σχήματος για ακριβή διάταξη

Τanto η ομάδα όσο και τα παιδικά της σχήματα χρειάζονται ρητές διαστάσεις· διαφορετικά το Word εφαρμόζει προεπιλεγμένα μεγέθη που μπορεί να μην ταιριάζουν με το σχέδιό σας.

```csharp
        // Example of adjusting the group’s overall size.
        group.Width = 400;   // Overall width of the grouped area.
        group.Height = 200;  // Overall height of the grouped area.
```

*Γιατί ορίζουμε διαστάσεις* – Η ακριβής μέτρηση εξασφαλίζει ότι το ορθογώνιο και το πλαίσιο κειμένου δεν επικαλύπτονται ακούσια και ότι το τελικό **save docx file** ταιριάζει με την προγραμματισμένη διάταξη.

### 5. Δημιουργία πλαισίου κειμένου προγραμματιστικά μέσα στην ομάδα

```csharp
        // Add a textbox shape with custom text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,   // Position relative to the group’s coordinate system.
            Top = 10
        };

        // Populate the textbox with a paragraph containing a run.
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);

        // Append the textbox to the same group.
        group.AppendChild(textBox);
```

*Γιατί είναι σημαντικό αυτό το βήμα* – Το τμήμα **create textbox programmatically** δείχνει πώς να ενσωματώσετε πλούσιο κείμενο μέσα σε ένα σχήμα. Η χρήση ενός `Paragraph` και `Run` σας δίνει πλήρη έλεγχο της μορφοποίησης αργότερα.

### 6. Εισαγωγή σχήματος ομάδας και **αποθήκευση αρχείου docx**

```csharp
        // Insert the completed group into the document at the current cursor position.
        builder.InsertNode(group);

        // Save the document to the file system.
        doc.Save("GroupShape.docx");   // The file now contains a rectangle and a textbox grouped together.
    }
}
```

*Γιατί είναι σημαντικό αυτό το τελικό βήμα* – Η κλήση `InsertNode` τοποθετεί τα ομαδοποιημένα σχήματα ακριβώς εκεί που βρίσκεται ο κέρσορας του builder. Η μέθοδος `doc.Save` εκτελεί τη λειτουργία **save docx file**, γράφοντας ένα πλήρες έγγραφο Word στο δίσκο.

> **Αποτέλεσμα:** Το άνοιγμα του *GroupShape.docx* στο Microsoft Word εμφανίζει ένα ορθογώνιο στα αριστερά και ένα πλαίσιο κειμένου στα δεξιά, και τα δύο κλειδωμένα μαζί μέσα σε μία ενιαία ομάδα. Μπορείτε να μετακινήσετε την ομάδα ως μονάδα, να αλλάξετε το μέγεθός της ή να εφαρμόσετε πρόσθετη μορφοποίηση.

## Πλήρες, εκτελέσιμο παράδειγμα

Αντιγράψτε τον παρακάτω κώδικα σε ένα νέο έργο console (`dotnet new console`) και εκτελέστε `dotnet run`. Το πρόγραμμα δημιουργεί το `GroupShape.docx` στον φάκελο εξόδου του έργου.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // 1. Initialize document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Create a group shape container.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,
            Height = 200
        };

        // 3. Add rectangle shape.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);

        // 4. Add textbox shape with text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,
            Top = 10
        };
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);
        group.AppendChild(textBox);

        // 5. Insert the group into the document.
        builder.InsertNode(group);

        // 6. Save the document.
        doc.Save("GroupShape.docx");
    }
}
```

### Αναμενόμενο αποτέλεσμα

* Ένα αρχείο με όνομα **GroupShape.docx** εμφανίζεται στον φάκελο εξόδου.
* Το άνοιγμα του αρχείου δείχνει ένα ορθογώνιο σχήμα στα αριστερά και ένα πλαίσιο κειμένου που περιέχει “Grouped text” στα δεξιά, και τα δύο κλειδωμένα μαζί.
* Η επιλογή οποιουδήποτε σχήματος μετακινεί ολόκληρη την ομάδα, επιβεβαιώνοντας ότι η λειτουργία **group shapes word** λειτουργεί όπως προβλέπεται.

## Συνηθισμένες παραλλαγές και ειδικές περιπτώσεις

| Κατάσταση | Σύσταση |
|-----------|----------------|
| Χρειάζεστε περισσότερα από δύο σχήματα | Προσθέστε επιπλέον αντικείμενα `Shape` στο `group` πριν καλέσετε `builder.InsertNode`. |
| Θέλετε η ομάδα να εμφανιστεί σε συγκεκριμένη σελίδα | Μετακινήστε τον κέρσορα του builder με `builder.MoveToDocumentEnd()` ή `builder.MoveToPage(pageNumber)`. |
| Απαιτούνται διαφορετικές μονάδες (π.χ., εκατοστά) | Χρησιμοποιήστε `ConvertUtil.InchToPoint(1.0)` για να μετατρέψετε ίντσες σε points, τη μονάδα που αναμένει το Word. |
| Θέλετε το πλαίσιο κειμένου να περιτυλίγει το κείμενο | Ορίστε `textBox.TextBoxWrap = TextBoxWrapType.Square` μετά τη δημιουργία του πλαισίου κειμένου. |
| Εργασία με παλαιότερες εκδόσεις του .NET Framework | Το ίδιο API λειτουργεί με .NET Framework 4.7+, αλλά βεβαιωθείτε ότι αναφέρετε τη σωστή έκδοση του Aspose.Words. |

**Συμβουλή:** Πάντα ορίζετε το `Width` και `Height` της ομάδας *μετά* την προσθήκη όλων των παιδικών σχημάτων. Αυτό εγγυάται ότι η ομάδα περιβάλλει πλήρως το περιεχόμενό της, αποτρέποντας το κόψιμο όταν το έγγραφο ανοίγει στο Word.

## Συμπέρασμα

Τώρα ξέρετε πώς να **αποθηκεύσετε αρχείο docx** ενώ **προσθέτετε σχήμα ορθογωνίου**, **ομαδοποιείτε σχήματα word**, **ορίζετε διαστάσεις σχήματος**, και **δημιουργείτε πλαίσιο κειμένου προγραμματιστικά** χρησιμοποιώντας το Aspose.Words for .NET. Το πλήρες παράδειγμα δείχνει ένα καθαρό, επαναλαμβανόμενο μοτίβο που μπορείτε να προσαρμόσετε σε πιο σύνθετες διατάξεις, όπως διαγράμματα, εικόνες,

## Τι Θα Πρέπει Να Μάθετε Στη Σύντομη Μελλοντική;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}