---
category: general
date: 2026-09-21
description: Μάθετε πώς να ομαδοποιείτε σχήματα στο Word χρησιμοποιώντας το Aspose.Words
  για C#. Αυτός ο οδηγός βήμα‑βήμα καλύπτει τη δημιουργία, την τοποθέτηση και την
  αποθήκευση ομαδοποιημένων σχημάτων.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in Word
- Aspose.Words shape grouping
- C# Word shape manipulation
- DocumentBuilder insert shape
- GroupShape container
language: el
lastmod: 2026-09-21
og_description: Ομαδοποιήστε σχήματα στο Word χρησιμοποιώντας το Aspose.Words για
  C#. Ακολουθήστε αυτόν τον σύντομο οδηγό για να δημιουργήσετε, τοποθετήσετε και αποθηκεύσετε
  ομαδοποιημένα σχήματα προγραμματιστικά.
og_image_alt: Screenshot of grouped shapes in Word document created with Aspose.Words
og_title: Ομαδοποίηση σχημάτων στο Word με το Aspose.Words – πλήρης οδηγός C#
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  headline: How to group shapes in Word with Aspose.Words for C#
  type: TechArticle
- description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  name: How to group shapes in Word with Aspose.Words for C#
  steps:
  - name: Create a blank document and a `DocumentBuilder`
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert the first rectangle shape
    text: '```csharp // Insert a rectangle that is 100 points wide and 50 points tall.
      Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50); ```'
  - name: Insert the second rectangle and offset it
    text: '```csharp // Insert the second rectangle with the same dimensions. Shape
      shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);'
  - name: Create a `GroupShape` large enough for both rectangles
    text: '```csharp // The group must be wide enough to contain both shapes (100
      pt + 120 pt + 100 pt = 320 pt). // We give a little extra margin, so the group
      width is set to 300 pt and height to 100 pt. GroupShape group = new GroupShape(doc,
      300, 100); ```'
  - name: Append the individual shapes to the group
    text: '```csharp group.AppendChild(shape1); group.AppendChild(shape2); ```'
  - name: Insert the grouped shape back into the document
    text: '```csharp // Insert the GroupShape at the current builder position. builder.InsertNode(group);
      ```'
  - name: Save the document
    text: '```csharp // Replace YOUR_DIRECTORY with an absolute or relative path where
      you have write permission. doc.Save("YOUR_DIRECTORY/GroupedShapes.docx"); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Πώς να ομαδοποιήσετε σχήματα στο Word με το Aspose.Words για C#
url: /el/net/programming-with-shapes/how-to-group-shapes-in-word-with-aspose-words-for-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να ομαδοποιήσετε σχήματα στο Word με Aspose.Words για C#

Εάν χρειάζεται να **ομαδοποιήσετε σχήματα στο Word** προγραμματιστικά, το Aspose.Words το καθιστά απλό. Αυτό το tutorial σας δείχνει πώς να δημιουργήσετε δύο ορθογώνια σχήματα, να τα τοποθετήσετε δίπλα‑δίπλα, να τα συνδυάσετε σε ένα `GroupShape` και να αποθηκεύσετε το αποτέλεσμα ως αρχείο DOCX.

Θα δείτε ένα πλήρες, εκτελέσιμο παράδειγμα, εξηγήσεις για το γιατί κάθε βήμα είναι σημαντικό, και συμβουλές για την αντιμετώπιση κοινών περιπτώσεων όπως επικαλυπτόμενα σχήματα ή δυναμικό μέγεθος. Στο τέλος αυτού του οδηγού μπορείτε να ενσωματώσετε την ομαδοποίηση σχημάτων σε οποιοδήποτε έργο αυτοματοποίησης του Word.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* .NET 6.0 (ή νεότερη) εγκατεστημένη – το Aspose.Words υποστηρίζει .NET Standard 2.0+, .NET Core και .NET Framework.
* Ένα έγκυρο license του Aspose.Words for .NET (ή ένα προσωρινό κλειδί αξιολόγησης) – η βιβλιοθήκη λειτουργεί χωρίς άδεια αλλά προσθέτει υδατογράφημα.
* Visual Studio 2022 (ή οποιοδήποτε IDE C#) για τη μεταγλώττιση και εκτέλεση του δείγματος.

Δεν απαιτούνται επιπλέον πακέτα NuGet πέρα από το `Aspose.Words`.

## Πώς να ομαδοποιήσετε σχήματα στο Word χρησιμοποιώντας Aspose.Words

Ο πυρήνας της λύσης είναι ένα αντικείμενο **`GroupShape`** που λειτουργεί ως κοντέινερ για τα μεμονωμένα σχήματα. Παρακάτω χωρίζουμε τη διαδικασία σε σαφή βήματα.

### Βήμα 1: Δημιουργία ενός κεντρικού εγγράφου και ενός `DocumentBuilder`

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty Word document.
Document doc = new Document();

// DocumentBuilder provides convenient methods for inserting content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Γιατί αυτό το βήμα;*  
`Document` αντιπροσωπεύει ολόκληρο το αρχείο DOCX, ενώ το `DocumentBuilder` παρέχει μεθόδους fluent (π.χ., `InsertShape`) που τοποθετούν αυτόματα νέα στοιχεία στη τρέχουσα θέση του κέρσορα.

### Βήμα 2: Εισαγωγή του πρώτου ορθογωνίου σχήματος

```csharp
// Insert a rectangle that is 100 points wide and 50 points tall.
Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

Η κλήση `InsertShape` προσθέτει το σχήμα στο έγγραφο και επιστρέφει ένα αντικείμενο `Shape` που μπορείτε να διαμορφώσετε περαιτέρω (χρώμα, περίγραμμα κ.λπ.). Το μέγεθος εκφράζεται σε points (1 pt ≈ 1/72 in).

### Βήμα 3: Εισαγωγή του δεύτερου ορθογωνίου και μετατόπισή του

```csharp
// Insert the second rectangle with the same dimensions.
Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// Move the second shape 120 points to the right so the two rectangles do not overlap.
shape2.Left = 120; // Horizontal offset from the left edge of the page.
```

Η ρύθμιση `Left` τοποθετεί το σχήμα σε σχέση με το περιθώριο της σελίδας. Η μετατόπιση πρέπει να είναι μεγαλύτερη από το πλάτος του πρώτου σχήματος (100 pt) για να αποφευχθεί η επικάλυψη· χρησιμοποιούμε 120 pt για να αφήσουμε ένα μικρό κενό.

### Βήμα 4: Δημιουργία ενός `GroupShape` αρκετά μεγάλου για τα δύο ορθογώνια

```csharp
// The group must be wide enough to contain both shapes (100 pt + 120 pt + 100 pt = 320 pt).
// We give a little extra margin, so the group width is set to 300 pt and height to 100 pt.
GroupShape group = new GroupShape(doc, 300, 100);
```

Το `GroupShape` λαμβάνει το ιδιοκτησιακό `Document` και τις διαστάσεις του κοντέινερ. Το πλάτος του κοντέινερ πρέπει να υπερβαίνει την πιο δεξιά άκρη του πιο απομακρυσμένου σχήματος· διαφορετικά, το δεύτερο σχήμα θα περικοπεί.

### Βήμα 5: Προσθήκη των μεμονωμένων σχημάτων στην ομάδα

```csharp
group.AppendChild(shape1);
group.AppendChild(shape2);
```

Η προσθήκη (append) μετακινεί τα σχήματα στη συλλογή του `GroupShape`. Μετά από αυτήν την κλήση, τα σχήματα δεν είναι πλέον ανεξάρτητα αντικείμενα στο δέντρο του εγγράφου· ανήκουν στην ομάδα.

### Βήμα 6: Εισαγωγή του ομαδοποιημένου σχήματος πίσω στο έγγραφο

```csharp
// Insert the GroupShape at the current builder position.
builder.InsertNode(group);
```

Η `InsertNode` τοποθετεί ολόκληρο το `GroupShape` στη θέση όπου βρίσκεται ο κέρσορας. Εάν χρειάζεστε την ομάδα σε συγκεκριμένη παράγραφο, μετακινήστε πρώτα τον builder σε αυτήν την παράγραφο.

### Βήμα 7: Αποθήκευση του εγγράφου

```csharp
// Replace YOUR_DIRECTORY with an absolute or relative path where you have write permission.
doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
```

Το παραγόμενο αρχείο περιέχει δύο ορθογώνια που συμπεριφέρονται ως ένα ενιαίο αντικείμενο—μπορείτε να τα μετακινήσετε, να αλλάξετε το μέγεθός τους ή να τα διαγράψετε μαζί στο Microsoft Word.

## Πλήρης κώδικας

Συνδυάζοντας όλα τα βήματα προκύπτει ένα αυτόνομο πρόγραμμα:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first rectangle (100 pt × 50 pt).
        Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // 3️⃣ Insert the second rectangle and offset it horizontally.
        Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        shape2.Left = 120; // Prevent overlap.

        // 4️⃣ Create a GroupShape container large enough for both.
        GroupShape group = new GroupShape(doc, 300, 100);

        // 5️⃣ Add both rectangles to the group.
        group.AppendChild(shape1);
        group.AppendChild(shape2);

        // 6️⃣ Insert the grouped shape back into the document.
        builder.InsertNode(group);

        // 7️⃣ Save the document.
        doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
    }
}
```

**Αναμενόμενο αποτέλεσμα:** Το άνοιγμα του *GroupedShapes.docx* στο Microsoft Word εμφανίζει δύο ορθογώνια δίπλα‑δίπλα, αντιμετωπισμένα ως ένα ενιαίο επιλέξιμο αντικείμενο. Η μετακίνηση της ομάδας μετακινεί και τα δύο ορθογώνια μαζί.

## Συνηθισμένες παραλλαγές και περιπτώσεις άκρων

| Κατάσταση | Συνιστώμενη προσαρμογή |
|-----------|------------------------|
| **Περισσότερα από δύο σχήματα** | Δημιουργήστε επιπλέον αντικείμενα `Shape`, τοποθετήστε τα αναλόγως και προσθέστε καθένα στο ίδιο `GroupShape`. |
| **Δυναμικό μέγεθος** | Υπολογίστε το πλάτος/ύψος της ομάδας βάσει των μέγιστων τιμών `Right` και `Bottom` των παιδικών σχημάτων. |
| **Διαφορετικοί τύποι σχημάτων** | `ShapeType.Ellipse`, `ShapeType.Triangle` κ.λπ. μπορούν να εισαχθούν με τον ίδιο τρόπο· το κοντέινερ της ομάδας δεν ενδιαφέρεται για τον τύπο. |
| **Περιστροφικά σχήματα** | Ορίστε `shape.Rotation = 45;` πριν την προσθήκη· η περιστροφή διατηρείται μέσα στην ομάδα. |
| **Αποθήκευση ως PDF** | Κλήση `doc.Save("GroupedShapes.pdf");` – η ομάδα διατηρείται στην απόδοση PDF. |

**Pro tip:** Μετά την ομαδοποίηση, μπορείτε ακόμη να τροποποιήσετε μεμονωμένα σχήματα προσπερνώντας το `group.GetChildNodes(NodeType.Shape, true)`. Αυτό είναι χρήσιμο όταν θέλετε να αλλάξετε το χρώμα γεμίσματος ενός ορθογωνίου χωρίς να σπάσετε την ομάδα.

## Πώς να επαληθεύσετε την ομαδοποίηση προγραμματιστικά

Εάν χρειάζεται να επιβεβαιώσετε ότι τα σχήματα έχουν ομαδοποιηθεί σωστά (π.χ., σε μονάδες δοκιμών), εξετάστε την ιεραρχία κόμβων του εγγράφου:

```csharp
NodeCollection groups = doc.GetChildNodes(NodeType.GroupShape, true);
Console.WriteLine($"Number of groups: {groups.Count}");
Console.WriteLine($"Children in first group: {groups[0].GetChildNodes(NodeType.Shape, true).Count}");
```

Η έξοδος πρέπει να είναι:

```
Number of groups: 1
Children in first group: 2
```

Αυτό επιβεβαιώνει ότι **group shapes in Word** δημιουργήθηκαν όπως αναμενόταν.

## Συμπέρασμα

Τώρα γνωρίζετε πώς να **ομαδοποιήσετε σχήματα στο Word** με το Aspose.Words για C#. Η διαδικασία περιλαμβάνει τη δημιουργία μεμονωμένων σχημάτων, την τοποθέτησή τους, τη συσφράγιση τους σε ένα `GroupShape` και την εισαγωγή της ομάδας πίσω στο έγγραφο. Με το πλήρες παράδειγμα παραπάνω μπορείτε να επεκτείνετε την τεχνική σε οποιονδήποτε αριθμό σχημάτων, διαφορετικούς τύπους ή ακόμη και να τη συνδυάσετε με πλαίσια κειμένου και εικόνες.

Στη συνέχεια, εξερευνήστε σχετικά θέματα όπως **Aspose.Words shape grouping**, **C# Word shape manipulation**, και **DocumentBuilder insert shape** για πιο προχωρημένα σενάρια αυτοματοποίησης εγγράφων. Πειραματιστείτε με δυναμικό μέγεθος, συνθήκες ομαδοποίησης και εξαγωγή σε PDF για να αξιοποιήσετε πλήρως τη δύναμη του Aspose.Words.

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στην υλοποίηση των δικών σας έργων.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}