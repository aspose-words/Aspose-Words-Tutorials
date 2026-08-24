---
category: general
date: 2026-08-23
description: Μάθετε πώς να ομαδοποιείτε σχήματα σε C# χρησιμοποιώντας το Aspose.Words.
  Ο οδηγός καλύπτει επίσης πώς να εισάγετε σχήμα ορθογωνίου και να προσθέσετε σχήματα
  σε έγγραφα Word για σύνθετα έγγραφα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert rectangle shape
- add shapes word
- group multiple shapes
- how to start group
language: el
lastmod: 2026-08-23
og_description: Πώς να ομαδοποιήσετε σχήματα σε C# με το Aspose.Words. Ακολουθήστε
  αυτό το πλήρες σεμινάριο για να εισάγετε σχήμα ορθογωνίου, να προσθέσετε σχήματα
  σε έγγραφο Word και να ομαδοποιήσετε πολλαπλά σχήματα αποδοτικά.
og_image_alt: How to group shapes in C# using Aspose.Words
og_title: Πώς να ομαδοποιήσετε σχήματα σε C# – οδηγός βήμα‑προς‑βήμα
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Learn how to group shapes in C# using Aspose.Words. The guide also
    covers how to insert rectangle shape and add shapes word for complex documents.
  headline: How to group shapes in C# with Aspose.Words
  type: TechArticle
- description: Learn how to group shapes in C# using Aspose.Words. The guide also
    covers how to insert rectangle shape and add shapes word for complex documents.
  name: How to group shapes in C# with Aspose.Words
  steps:
  - name: '**Nested groups** – Aspose.Words allows groups within groups. To create
      a nested group, call `StartGroupShape` again before calling `EndGroupShape`
      for the inner group.'
    text: '**Nested groups** – Aspose.Words allows groups within groups. To create
      a nested group, call `StartGroupShape` again before calling `EndGroupShape`
      for the inner group.'
  - name: '**Empty groups** – If you start a group but never insert a shape, `EndGroupShape`
      will still create an empty container. This is harmless but may increase file
      size slightly.'
    text: '**Empty groups** – If you start a group but never insert a shape, `EndGroupShape`
      will still create an empty container. This is harmless but may increase file
      size slightly.'
  - name: '**Compatibility** – The generated DOCX works with Word 2010 and later.
      Older versions may ignore grouping metadata, so always test with the target
      Word version.'
    text: '**Compatibility** – The generated DOCX works with Word 2010 and later.
      Older versions may ignore grouping metadata, so always test with the target
      Word version.'
  type: HowTo
- questions:
  - answer: Yes. Retrieve the existing `Shape` objects, call `builder.StartGroupShape()`,
      re‑insert them with `builder.InsertShape(existingShape)`, then call `EndGroupShape()`.
    question: Can I group shapes that already exist in the document?
  - answer: Aspose.Words adds a `<w:grpSp>` element that contains each shape’s `<w:sp>`
      node. This is fully compliant with the Office Open XML specification.
    question: Does grouping affect the underlying XML?
  - answer: 'There is no direct “ungroup” API, but you can iterate through the child
      shapes of the group (`group.GroupShape.Children`) and copy them out to the document
      body. ## Next steps Now that you know **how to group shapes**, consider exploring
      these related topics: - **Apply complex formatting to grouped '
    question: What if I need to ungroup later?
  type: FAQPage
tags:
- Aspose.Words
- C#
- shapes
- document automation
title: Πώς να ομαδοποιήσετε σχήματα σε C# με το Aspose.Words
url: /el/net/programming-with-shapes/how-to-group-shapes-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να ομαδοποιήσετε σχήματα σε C# με το Aspose.Words

Αν χρειάζεστε **how to group shapes** σε ένα έγγραφο Word προγραμματιστικά, αυτό το tutorial σας δείχνει τα ακριβή βήματα χρησιμοποιώντας το Aspose.Words για .NET. Είτε δημιουργείτε έναν γεννήτρια αναφορών, μια μηχανή προτύπων ή ένα εργαλείο διαγράμματος, θα μάθετε πώς να ξεκινήσετε μια ομάδα, να εισάγετε ένα σχήμα ορθογωνίου και να προσθέσετε περιεχόμενο σε επίπεδο Word σε σχήματα χωρίς να αφήσετε τον κώδικά σας.

Θα δείτε επίσης πώς να **group multiple shapes** μαζί, κάτι που είναι απαραίτητο όταν θέλετε να μετακινήσετε, να περιστρέψετε ή να μορφοποιήσετε μια συλλογή αντικειμένων ως μία ενιαία οντότητα. Το παρακάτω παράδειγμα λειτουργεί με την πιο πρόσφατη έκδοση Aspose.Words 24.x και απαιτεί μόνο .NET 6 ή νεότερο.

## Προαπαιτούμενα

- .NET 6 SDK (ή οποιαδήποτε έκδοση .NET υποστηρίζεται από το Aspose.Words)
- Visual Studio 2022 ή VS Code
- Πακέτο NuGet Aspose.Words για .NET (`Install-Package Aspose.Words`)
- Βασική εξοικείωση με C# και το μοντέλο αντικειμένων Aspose.Words

> **Pro tip:** Χρησιμοποιήστε την δωρεάν άδεια αξιολόγησης από το Aspose για να αποφύγετε περιορισμούς υδατογραφήματος κατά τη δοκιμή.

## Πώς να ομαδοποιήσετε σχήματα με το Aspose.Words

Παρακάτω υπάρχει ένα πλήρες, εκτελέσιμο πρόγραμμα που δείχνει **how to start group**, προσθέτει ένα ορθογώνιο και ολοκληρώνει την ομάδα. Ο κώδικας ακολουθεί την ίδια λογική ροή με το απόσπασμα που παρείχατε, αλλά προσθέτει πλαίσιο, διαχείριση σφαλμάτων και σχόλια για σαφήνεια.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank document.
            Document doc = new Document();

            // 2️⃣ Get a DocumentBuilder to insert content.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Start a group shape – all shapes added after this call belong to the group.
            // This is the “how to start group” step.
            Shape group = builder.StartGroupShape();

            // 4️⃣ Insert individual shapes inside the group.
            //    a) Insert a rectangle shape (demonstrates “insert rectangle shape”).
            builder.InsertShape(ShapeType.Rectangle, 150, 80);
            //    b) Insert a simple ellipse for visual variety.
            builder.InsertShape(ShapeType.Ellipse, 100, 60);
            //    c) Add a WordArt‑style text shape – shows “add shapes word”.
            builder.InsertShape(ShapeType.TextPlainText, 200, 40);
            builder.Writeln("Grouped Text"); // adds text inside the last shape

            // 5️⃣ Close the group shape to finalize the grouping.
            builder.EndGroupShape();

            // Optional: Save the document to verify the result.
            string outPath = "GroupedShapes.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Γιατί κάθε βήμα είναι σημαντικό

| Βήμα | Σκοπός | Πώς σχετίζεται με τις λέξεις-κλειδιά |
|------|---------|--------------------------------|
| **Create a new blank document** | Παρέχει έναν καθαρό καμβά για τις λειτουργίες σχήματος. | Θέτει τη βάση για **add shapes word** αργότερα. |
| **Initialize DocumentBuilder** | Ο builder είναι το κύριο API για την εισαγωγή αντικειμένων. | Απαιτείται πριν μπορέσετε να **how to start group**. |
| **StartGroupShape** | Ξεκινά ένα λογικό κοντέινερ· όλα τα επόμενα σχήματα γίνονται μέλη αυτής της ομάδας. | Απαντά άμεσα στο **how to start group**. |
| **InsertShape** (rectangle, ellipse, text) | Τοποθετεί μεμονωμένα σχήματα μέσα στην ομάδα. Η κλήση ορθογωνίου ικανοποιεί το **insert rectangle shape**· το σχήμα κειμένου ικανοποιεί το **add shapes word**. | Δείχνει **group multiple shapes**. |
| **EndGroupShape** | Ολοκληρώνει την ομάδα ώστε να μπορείτε να τη μετακινήσετε ή να τη μορφοποιήσετε ως ενότητα. | Ολοκληρώνει τη ροή εργασίας **how to group shapes**. |

## Εισαγωγή σχήματος ορθογωνίου – πιο βαθιά ανάλυση

Η μέθοδος `InsertShape` δέχεται ένα enum `ShapeType`, πλάτος και ύψος. Για να **insert rectangle shape** με προσαρμοσμένο στυλ, μπορείτε να επεκτείνετε το παράδειγμα:

```csharp
// Insert a styled rectangle
Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
rect.FillColor = System.Drawing.Color.LightBlue;
rect.StrokeColor = System.Drawing.Color.DarkBlue;
rect.LineWidth = 2.0;
```

> **Why style it?** Το στυλ εξασφαλίζει ότι το ορθογώνιο ξεχωρίζει όταν η ομάδα μετατοπιστεί αργότερα. Επίσης δείχνει ότι οι ιδιότητες του σχήματος μπορούν να οριστούν *πριν* κλείσει η ομάδα.

## Προσθήκη σχήματος σε επίπεδο Word (add shapes word)

Αν χρειάζεστε να ενσωματώσετε κείμενο απευθείας μέσα σε ένα σχήμα—συχνά αποκαλούμενο “WordArt” ή “πλαίσιο κειμένου”—χρησιμοποιήστε `ShapeType.TextPlainText`. Μετά την εισαγωγή, μπορείτε να γράψετε κείμενο στο σχήμα με `DocumentBuilder.Writeln` ή προσπερνώντας την ιδιότητα `TextBox` του σχήματος:

```csharp
Shape textBox = builder.InsertShape(ShapeType.TextPlainText, 250, 50);
textBox.TextBox.Text = "Hello, grouped world!";
```

Αυτό ικανοποιεί τη λέξη-κλειδί **add shapes word** και δείχνει πώς το κείμενο μπορεί να μεταφερθεί με την ομάδα.

## Ομαδοποίηση πολλαπλών σχημάτων – πρακτικά σενάρια

Όταν **group multiple shapes**, μπορείτε να τα αντιμετωπίζετε ως ένα ενιαίο αντικείμενο για τοποθέτηση, περιστροφή ή κλιμάκωση. Για παράδειγμα, μετά το κλείσιμο της ομάδας, μπορείτε να μετακινήσετε ολόκληρη την ομάδα:

```csharp
// Move the entire group 100 points to the right and 50 points down.
group.Left += 100;
group.Top += 50;
```

Ή να περιστρέψετε την ομάδα:

```csharp
group.Rotation = 45; // degrees
```

Αυτές οι λειτουργίες είναι δυνατόν μόνο επειδή τα σχήματα μοιράζονται την ίδια γονική ομάδα.

## Διαχείριση ειδικών περιπτώσεων

1. **Nested groups** – Το Aspose.Words επιτρέπει ομάδες μέσα σε ομάδες. Για να δημιουργήσετε μια ένθετη ομάδα, καλέστε ξανά το `StartGroupShape` πριν καλέσετε το `EndGroupShape` για την εσωτερική ομάδα.
2. **Empty groups** – Αν ξεκινήσετε μια ομάδα αλλά δεν εισάγετε ποτέ σχήμα, το `EndGroupShape` θα δημιουργήσει ακόμη και ένα κενό κοντέινερ. Αυτό δεν είναι επιβλαβές αλλά μπορεί να αυξήσει ελαφρώς το μέγεθος του αρχείου.
3. **Compatibility** – Το παραγόμενο DOCX λειτουργεί με Word 2010 και νεότερα. Παλαιότερες εκδόσεις μπορεί να αγνοούν τα μεταδεδομένα ομαδοποίησης, οπότε δοκιμάζετε πάντα με την έκδοση Word-στόχο.

## Πλήρες αρχείο πηγαίου κώδικα για αναφορά

Αποθηκεύστε το παρακάτω ως `Program.cs` σε ένα .NET console project. Ο κώδικας μεταγλωττίζεται και εκτελείται χωρίς τροποποίηση.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document.
            Document doc = new Document();

            // Step 2: Initialize DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Start the group – “how to start group”.
            Shape group = builder.StartGroupShape();

            // Step 4a: Insert a rectangle – “insert rectangle shape”.
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 150, 80);
            rect.FillColor = System.Drawing.Color.LightCoral;
            rect.StrokeColor = System.Drawing.Color.DarkRed;
            rect.LineWidth = 1.5;

            // Step 4b: Insert an ellipse (additional shape for grouping).
            builder.InsertShape(ShapeType.Ellipse, 100, 60);

            // Step 4c: Add a text box – “add shapes word”.
            Shape txt = builder.InsertShape(ShapeType.TextPlainText, 200, 40);
            txt.TextBox.Text = "Grouped Text";

            // Step 5: End the group – completes “how to group shapes”.
            builder.EndGroupShape();

            // Optional: Adjust group position.
            group.Left += 50;
            group.Top += 30;

            // Save the result.
            string outPath = "GroupedShapes.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Αναμενόμενο αποτέλεσμα

Ανοίγοντας το `GroupedShapes.docx` στο Microsoft Word θα δείτε:

- Ένα ελαφρύ κοραλί (light‑coral) ορθογώνιο, μια έλλειψη και ένα πλαίσιο κειμένου—όλα οπτικά δεσμευμένα μαζί.
- Επιλέγοντας οποιοδήποτε μέρος της ομάδας επιλέγεται επίσης ολόκληρη η ομάδα (εμφανίζεται ένα ενιαίο πλαίσιο περιγράμματος).
- Η μετακίνηση ή η περιστροφή της ομάδας μετακινεί και τα τρία σχήματα μαζί.

## Συχνές ερωτήσεις

**Q: Μπορώ να ομαδοποιήσω σχήματα που ήδη υπάρχουν στο έγγραφο;**  
A: Ναι. Ανακτήστε τα υπάρχοντα αντικείμενα `Shape`, καλέστε `builder.StartGroupShape()`, επανεισάγετέ τα με `builder.InsertShape(existingShape)`, και στη συνέχεια καλέστε `EndGroupShape()`.

**Q: Επηρεάζει η ομαδοποίηση το υποκείμενο XML;**  
A: Το Aspose.Words προσθέτει ένα στοιχείο `<w:grpSp>` που περιέχει το `<w:sp>` κόμβο κάθε σχήματος. Αυτό είναι πλήρως συμβατό με την προδιαγραφή Office Open XML.

**Q: Τι γίνεται αν χρειαστεί να αποομαδοποιήσω αργότερα;**  
A: Δεν υπάρχει άμεσο API “ungroup”, αλλά μπορείτε να διασχίσετε τα παιδικά σχήματα της ομάδας (`group.GroupShape.Children`) και να τα αντιγράψετε στο σώμα του εγγράφου.

## Επόμενα βήματα

Τώρα που γνωρίζετε **how to group shapes**, εξετάστε το ενδεχόμενο να εξερευνήσετε τα παρακάτω συναφή θέματα:

- **Apply complex formatting to grouped shapes** – μάθετε πώς να ορίσετε διαβαθμιστικές γεμίσεις, σκιές και στυλ γραμμής.
- **Export grouped shapes as images** – χρησιμοποιήστε `Shape.GetShapeRenderer().Save(...)` για να ραστεροποιήσετε μια ομάδα.
- **Create dynamic diagrams** – συνδυάστε τοποθέτηση βάσει δεδομένων με ομαδοποίηση για να δημιουργήσετε αυτόματα διαγράμματα ροής.

Κάθε ένα από αυτά βασίζεται στο θεμέλιο που καλύφθηκε εδώ και θα σας βοηθήσει να δημιουργήσετε πιο πλούσια, πιο διαδραστικά έγγραφα Word.

---

*Καλή προγραμματιστική! Αν βρήκατε αυτόν τον οδηγό χρήσιμο, μοιραστείτε τον με συναδέλφους ή δώστε αστέρι στο αποθετήριο που περιέχει το δείγμα έργου.*

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}