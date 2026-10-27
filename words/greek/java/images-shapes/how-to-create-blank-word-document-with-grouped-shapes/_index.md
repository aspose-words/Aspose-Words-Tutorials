---
category: general
date: 2026-09-08
description: Μάθετε πώς να δημιουργήσετε ένα κενό έγγραφο Word, να εισάγετε σχήμα
  ορθογωνίου και να ομαδοποιήσετε πολλαπλά σχήματα χρησιμοποιώντας C#. Ακολουθήστε
  αυτόν τον οδηγό βήμα‑βήμα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert rectangle shape
- group multiple shapes
- add shapes to group
language: el
lastmod: 2026-09-08
og_description: Δημιουργήστε κενό έγγραφο Word, εισάγετε σχήμα ορθογωνίου και ομαδοποιήστε
  πολλαπλά σχήματα σε C#. Αυτό το σεμινάριο σας καθοδηγεί σε όλη τη διαδικασία.
og_image_alt: Screenshot showing a blank Word document with a grouped rectangle and
  ellipse shape
og_title: Δημιουργία κενού εγγράφου Word με ομαδοποιημένα σχήματα σε C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to create blank Word document, insert rectangle shape and
    group multiple shapes using C#. Follow this step‑by‑step guide.
  headline: How to create blank Word document with grouped shapes
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Πώς να δημιουργήσετε κενό έγγραφο Word με ομαδοποιημένα σχήματα
url: /el/java/images-shapes/how-to-create-blank-word-document-with-grouped-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε κενό έγγραφο Word με ομαδοποιημένα σχήματα

Αν χρειάζεστε **να δημιουργήσετε κενό έγγραφο Word** που περιέχει προσαρμοσμένα γραφικά, αυτός ο οδηγός σας δείχνει ακριβώς πώς. Θα μάθετε να **εισάγετε σχήμα ορθογωνίου**, **ομαδοποιείτε πολλαπλά σχήματα**, και **προσθέτετε σχήματα στην ομάδα** χρησιμοποιώντας το Aspose.Words for .NET.

Ένα κενό έγγραφο σας παρέχει έναν καθαρό καμβά, και η ομαδοποίηση σχημάτων σας επιτρέπει να τα μετακινείτε, να αλλάζετε το μέγεθός τους ή να τα περιστρέφετε ως μία ενιαία μονάδα. Αυτό το tutorial καλύπτει κάθε βήμα — από την αρχικοποίηση του εγγράφου μέχρι την αποθήκευση του τελικού αρχείου — ώστε να μπορείτε να αντιγράψετε τον κώδικα στο δικό σας έργο και να δείτε άμεσα αποτελέσματα.

## Τι θα χρειαστείτε

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.6+)
* Ένα έγκυρο license του Aspose.Words for .NET (η δωρεάν αξιολόγηση λειτουργεί για δοκιμές)
* Ένα IDE όπως το Visual Studio 2022 ή το Visual Studio Code
* Βασική εξοικείωση με τη σύνταξη της C#

Δεν απαιτούνται πρόσθετα πακέτα NuGet πέρα από `Aspose.Words`.

## Πώς να δημιουργήσετε κενό έγγραφο Word

Το πρώτο βήμα είναι η δημιουργία ενός αντικειμένου `Document`. Αυτό το αντικείμενο αντιπροσωπεύει ένα κενό αρχείο `.docx` που μπορείτε να επεξεργαστείτε με έναν `DocumentBuilder`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document and a builder to edit it.
            Document doc = new Document();               // Blank Word document
            DocumentBuilder builder = new DocumentBuilder(doc);
```

Ο κατασκευαστής `Document` δημιουργεί ένα **κενό έγγραφο Word** στη μνήμη. Ο `DocumentBuilder` παρέχει ένα fluent API για την εισαγωγή κειμένου, εικόνων και αντικειμένων σχεδίασης.

## Εισαγωγή σχήματος ορθογωνίου στο έγγραφο

Στη συνέχεια, προσθέστε ένα σχήμα ορθογωνίου. Το ορθογώνιο θα είναι το πρώτο παιδί της ομάδας που θα δημιουργήσουμε αργότερα.

```csharp
            // Step 2: Insert a rectangle shape (100 pt wide, 50 pt high).
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            // Optional: give the rectangle a fill color for visibility.
            rectangle.FillColor = System.Drawing.Color.LightBlue;
```

Η κλήση `InsertShape` με `ShapeType.Rectangle` **εισάγει σχήμα ορθογωνίου** στη τρέχουσα θέση του κέρσορα. Το πλάτος και το ύψος εκφράζονται σε points (1 pt ≈ 1/72 in).

## Ομαδοποίηση πολλαπλών σχημάτων μαζί

Ένα `GroupShape` λειτουργεί ως κοντέινερ. Όλα τα παιδικά σχήματα μέσα στην ομάδα μετακινούνται και μετασχηματίζονται μαζί. Πρώτα, δημιουργήστε την ομάδα, μετά προσθέστε το ορθογώνιο που μόλις δημιουργήσαμε.

```csharp
            // Step 3: Create a group shape that will hold multiple child shapes.
            GroupShape group = builder.InsertGroupShape();
            // Append the rectangle as the first child of the group.
            group.AppendChild(rectangle);
```

Η μέθοδος `InsertGroupShape` τοποθετεί μια κενή ομάδα στον κέρσορα του builder. Προσθέτοντας το ορθογώνιο, **ομαδοποιούμε πολλαπλά σχήματα** — το ορθογώνιο γίνεται μέρος της εσωτερικής συλλογής κόμβων της ομάδας.

## Προσθήκη σχημάτων στην ομάδα και αποθήκευση του αρχείου

Τώρα προσθέστε ένα δεύτερο σχήμα — μια έλλειψη — για να δείξετε πώς πολλά αντικείμενα μοιράζονται το ίδιο κοντέινερ. Στη συνέχεια, αποθηκεύστε το έγγραφο.

```csharp
            // Step 4: Insert an ellipse shape (80 pt wide, 80 pt high).
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;

            // Append the ellipse to the same group.
            group.AppendChild(ellipse);

            // Step 5: Save the document containing the grouped shapes.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Η κλήση `InsertShape` **προσθέτει σχήματα στην ομάδα** όταν προσαρτήσετε το επιστρεφόμενο `Shape` στο `GroupShape`. Η αποθήκευση του `Document` γράφει ένα αρχείο `.docx` που μπορείτε να ανοίξετε στο Microsoft Word, LibreOffice ή οποιονδήποτε συμβατό προβολέα.

### Αναμενόμενο αποτέλεσμα

Όταν ανοίξετε *GroupShapeDemo.docx*, θα δείτε μια κενή σελίδα με ένα ομαδοποιημένο αντικείμενο που περιέχει ένα ανοιχτό‑μπλε ορθογώνιο και μια ροζ έλλειψη. Επιλέγοντας την ομάδα μπορείτε να μετακινήσετε και τα δύο σχήματα μαζί, επιβεβαιώνοντας ότι η **ομαδοποίηση πολλαπλών σχημάτων** λειτούργησε όπως αναμενόταν.

## Γιατί να χρησιμοποιήσετε ένα GroupShape;

* **Ατομικοί μετασχηματισμοί** — Η κλιμάκωση, η περιστροφή ή η μετακίνηση της ομάδας επηρεάζει όλα τα παιδιά ομοιόμορφα.
* **Λογική οργάνωση** — Κρατά τα σχετικά γραφικά μαζί, καθιστώντας τη δομή του εγγράφου πιο εύκολη στη συντήρηση.
* **Απόδοση** — Η απόδοση ενός ενιαίου κοντέινερ είναι συχνά ταχύτερη από την επεξεργασία πολλών ανεξάρτητων σχημάτων.

Αν χρειαστεί να τροποποιήσετε ένα μεμονωμένο παιδί αργότερα, μπορείτε να το ανακτήσετε από το `group.ChildNodes` με δείκτη ή με την ιδιότητα `Name`.

## Συνηθισμένες παραλλαγές και ειδικές περιπτώσεις

| Σενάριο                                   | Πώς να προσαρμόσετε τον κώδικα                                                   |
|-------------------------------------------|-----------------------------------------------------------------------------------|
| **Διαφορετικοί τύποι σχημάτων**            | Αντικαταστήστε το `ShapeType.Rectangle` ή `ShapeType.Ellipse` με οποιονδήποτε άλλο `ShapeType` |
| **Προσθήκη κειμένου μέσα σε σχήμα**       | Χρησιμοποιήστε `Shape.TextPath.Text = "Hello"` μετά την εισαγωγή του σχήματος      |
| **Ορισμός γωνίας περιστροφής**            | `group.Rotation = 45;` (μοίρες)                                                    |
| **Αποθήκευση ως PDF αντί για DOCX**       | `doc.Save("GroupShapeDemo.pdf");`                                                 |
| **Εφαρμογή περιγράμματος στην ομάδα**     | `group.LineStyle = LineStyle.Single;`<br>`group.LineWidth = 1.5;`               |

## Pro tips

* **Ονομάστε τα σχήματά σας** — `rectangle.Name = "MyRect";` κάνει πιο εύκολη την εντοπισμό τους αργότερα.
* **Χρησιμοποιήστε σχετική τοποθέτηση** — Ορίστε `group.RelativeHorizontalPosition` σε `RelativeHorizontalPosition.Page` αν θέλετε η ομάδα να παραμένει αγκυροβολημένη στα περιθώρια της σελίδας.
* **Αποδεσμεύστε πόρους** — Τυλίξτε το `Document` σε ένα `using` block όταν εργάζεστε σε μεγαλύτερες εφαρμογές για να ελευθερώσετε άμεσα τη μη διαχειριζόμενη μνήμη.

## Πλήρης κώδικας για γρήγορη αντιγραφή‑επικόλληση

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document and a builder to edit it.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a rectangle shape (100 pt × 50 pt) and give it a light‑blue fill.
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // Create a group shape and add the rectangle as its first child.
            GroupShape group = builder.InsertGroupShape();
            group.AppendChild(rectangle);

            // Insert an ellipse shape (80 pt × 80 pt) with a pink fill.
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;
            group.AppendChild(ellipse);

            // Save the document. The file will contain the grouped rectangle and ellipse.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Αντιγράψτε τον κώδικα σε ένα νέο έργο console, επαναφέρετε το πακέτο NuGet `Aspose.Words`, και εκτελέστε. Το αρχείο εξόδου εμφανίζεται στον φάκελο `bin/Debug/net6.0` (ή ισοδύναμο) του έργου.

## Επόμενα βήματα

Τώρα που μπορείτε να **δημιουργήσετε κενό έγγραφο Word**, **εισάγετε σχήμα ορθογωνίου**, και **ομαδοποιήσετε πολλαπλά σχήματα**, μπορείτε να εξερευνήσετε:

* Προσθήκη **πλαισίων κειμένου** μέσα σε μια ομάδα για δημιουργία διαγραμμάτων με ετικέτες.
* Εξαγωγή του ομαδοποιημένου γραφικού σε εικόνα με `doc.Save("image.png", SaveFormat.Png)`.
* Συνδυασμός ομάδων με πίνακες για πλούσια μορφοποιημένες αναφορές.

Πειραματιστείτε με διαφορετικές ιδιότητες σχημάτων, ιεραρχίες ομάδων και μορφές εξαγωγής για να αξιοποιήσετε πλήρως τις δυνατότητες σχεδίασης του Aspose.Words.

--- 

*Θυμηθείτε*: η ομαδοποίηση σχημάτων είναι ένας ισχυρός τρόπος να διατηρείτε τα έγγραφα Word σας οργανωμένα και τον κώδικά σας εύκολο στη συντήρηση. Καλή προγραμματιστική!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στην υλοποίηση στα δικά σας έργα.

- [Δημιουργία σχήματος ορθογωνίου στο Word με C# – Οδηγός βήμα‑βήμα](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Εισαγωγή σχημάτων σε έγγραφα Word χρησιμοποιώντας Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Δημιουργία Group Shape σε έγγραφο Word χρησιμοποιώντας Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}