---
category: general
date: 2026-10-04
description: Μάθετε πώς να ομαδοποιείτε σχήματα στο Word χρησιμοποιώντας C#. Αυτός
  ο οδηγός δείχνει πώς να εισάγετε σχήμα ορθογωνίου, να ομαδοποιήσετε πολλαπλά σχήματα
  και να δημιουργήσετε ένα κενό αρχείο Word προγραμματιστικά.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- insert rectangle shape
- group multiple shapes
- append child to group
- create blank word file
language: el
lastmod: 2026-10-04
og_description: Ομαδοποίηση σχημάτων στο Word χρησιμοποιώντας C#. Ακολουθήστε αυτόν
  τον οδηγό βήμα‑προς‑βήμα για να εισάγετε σχήμα ορθογωνίου, να ομαδοποιήσετε πολλαπλά
  σχήματα και να δημιουργήσετε ένα κενό αρχείο Word με το DocumentBuilder.
og_image_alt: Screenshot of grouped rectangle and ellipse shapes inside a Word document
og_title: Ομαδοποίηση σχημάτων στο Word με C# – πλήρης οδηγός DocumentBuilder
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to group shapes in Word using C#. This guide shows how to
    insert rectangle shape, group multiple shapes, and create a blank Word file programmatically.
  headline: How to group shapes in Word with C# and DocumentBuilder
  type: TechArticle
- description: Learn how to group shapes in Word using C#. This guide shows how to
    insert rectangle shape, group multiple shapes, and create a blank Word file programmatically.
  name: How to group shapes in Word with C# and DocumentBuilder
  steps:
  - name: '**Create a blank Word file** – Starting with a clean document guarantees
      that no hidden formatting interferes with shape positioning.'
    text: '**Create a blank Word file** – Starting with a clean document guarantees
      that no hidden formatting interferes with shape positioning.'
  - name: '**Initialize DocumentBuilder** – `DocumentBuilder` abstracts low‑level
      node manipulation, letting you focus on layout.'
    text: '**Initialize DocumentBuilder** – `DocumentBuilder` abstracts low‑level
      node manipulation, letting you focus on layout.'
  - name: '**Insert individual shapes** – You first need separate objects (`insert
      rectangle shape` and an ellipse) before you can group them. Adjusting `Left`
      and `Top` ensures they appear side‑by‑side.'
    text: '**Insert individual shapes** – You first need separate objects (`insert
      rectangle shape` and an ellipse) before you can group them. Adjusting `Left`
      and `Top` ensures they appear side‑by‑side.'
  - name: '**Group multiple shapes** – By creating a `GroupShape` and using **append
      child to group**, you turn two independent drawings into a single logical unit.
      Moving or resizing the group will affect both children simultaneously.'
    text: '**Group multiple shapes** – By creating a `GroupShape` and using **append
      child to group**, you turn two independent drawings into a single logical unit.
      Moving or resizing the group will affect both children simultaneously.'
  - name: '**Save the document** – The final file, `GroupedShapes.docx`, can be opened
      in Microsoft Word to verify that the rectangle and ellipse are indeed grouped
      (select one, and both move together).'
    text: '**Save the document** – The final file, `GroupedShapes.docx`, can be opened
      in Microsoft Word to verify that the rectangle and ellipse are indeed grouped
      (select one, and both move together).'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shape handling
- DocumentBuilder
title: Πώς να ομαδοποιήσετε σχήματα στο Word με C# και DocumentBuilder
url: /el/java/images-shapes/how-to-group-shapes-in-word-with-c-and-documentbuilder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να ομαδοποιήσετε σχήματα στο Word με C# και DocumentBuilder

Αν χρειάζεστε **ομαδοποίηση σχημάτων στο Word** από μια εφαρμογή C#, αυτό το tutorial σας δείχνει ακριβώς πώς να το κάνετε. Θα δείτε πώς να *εισάγετε σχήμα ορθογωνίου*, να συνδυάσετε πολλά σχέδια σε μία ομάδα και, τελικά, **δημιουργήσετε ένα κενό αρχείο Word** που περιέχει τα ομαδοποιημένα αντικείμενα.

Η εργασία με σχήματα είναι συχνή απαίτηση όταν δημιουργείτε αναφορές, τιμολόγια ή προσαρμοσμένα πρότυπα προγραμματιστικά. Στο τέλος αυτού του οδηγού θα έχετε ένα επαναχρησιμοποιήσιμο κομμάτι κώδικα που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο .NET που αναφέρεται στο Aspose.Words.

## Τι θα μάθετε

- Δημιουργήστε ένα κενό έγγραφο Word από την αρχή.  
- Εισάγετε ένα σχήμα ορθογωνίου και μια έλλειψη χρησιμοποιώντας `DocumentBuilder`.  
- **Ομαδοποιήστε πολλαπλά σχήματα** σε ένα `GroupShape`.  
- Χρησιμοποιήστε **append child to group** για να δημιουργήσετε την ιεραρχία.  
- Αποθηκεύστε το αρχείο στο δίσκο και επαληθεύστε το αποτέλεσμα.

Δεν απαιτείται προηγούμενη εμπειρία με το Aspose.Words, αλλά θα πρέπει να έχετε βασική κατανόηση της ανάπτυξης σε C# και .NET.

## Προαπαιτούμενα

| Απαίτηση | Λόγος |
|-------------|--------|
| .NET 6.0 ή νεότερο | Παρέχει το runtime για τον κώδικα C#. |
| Aspose.Words for .NET (τελευταία έκδοση) | Παρέχει τις κλάσεις `Document`, `DocumentBuilder` και σχήματος. |
| Ένα IDE όπως το Visual Studio 2022 (ή VS Code) | Διευκολύνει τη μεταγλώττιση και εκτέλεση του παραδείγματος. |
| Δικαίωμα εγγραφής σε φάκελο στον υπολογιστή σας | Απαιτείται για την κλήση `doc.save`. |

Install Aspose.Words via NuGet:

```bash
dotnet add package Aspose.Words
```

---

## Ομαδοποίηση σχημάτων στο Word – οδηγός βήμα‑βήμα

Παρακάτω βρίσκεται το πλήρες, εκτελέσιμο πρόγραμμα. Κάθε ενότητα εξηγείται λεπτομερώς ώστε να κατανοήσετε **γιατί** γράφεται ο κώδικας με αυτόν τον τρόπο, όχι μόνο **τι** κάνει.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

namespace WordShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // -------------------------------------------------
            // Step 1: create a blank Word file
            // -------------------------------------------------
            // The Document constructor creates an empty .docx container.
            Document doc = new Document();

            // -------------------------------------------------
            // Step 2: initialize DocumentBuilder to add content
            // -------------------------------------------------
            // DocumentBuilder is the high‑level API for inserting text,
            // images, tables, and shapes into the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // -------------------------------------------------
            // Step 3: insert individual shapes
            // -------------------------------------------------
            // Insert a rectangle shape – this demonstrates the
            // "insert rectangle shape" keyword in practice.
            Shape rectangle = builder.InsertShape(
                ShapeType.Rectangle,   // shape type
                100,                  // width in points
                50);                  // height in points

            // Position the rectangle a little away from the left margin.
            rectangle.Left = 100;   // points from the left edge
            rectangle.Top = 100;    // points from the top of the page

            // Insert an ellipse shape to accompany the rectangle.
            Shape ellipse = builder.InsertShape(
                ShapeType.Ellipse,
                80,
                80);
            ellipse.Left = rectangle.Left + rectangle.Width + 20; // place right of rectangle
            ellipse.Top = rectangle.Top; // align tops

            // -------------------------------------------------
            // Step 4: create a GroupShape and append children
            // -------------------------------------------------
            // A GroupShape acts like a container; any shape added to it
            // moves together with the group. This fulfills the
            // "group multiple shapes" requirement.
            GroupShape group = builder.InsertGroupShape();

            // The "append child to group" operation builds the hierarchy.
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Optional: give the group a name for later reference.
            group.Name = "MyShapeGroup";

            // -------------------------------------------------
            // Step 5: save the document containing the grouped shapes
            // -------------------------------------------------
            string outputPath = @"GroupedShapes.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Γιατί κάθε βήμα είναι σημαντικό

1. **Δημιουργήστε ένα κενό αρχείο Word** – Ξεκινώντας με ένα καθαρό έγγραφο εξασφαλίζετε ότι δεν υπάρχει κρυφή μορφοποίηση που να επηρεάζει τη θέση των σχημάτων.  
2. **Αρχικοποιήστε το DocumentBuilder** – Το `DocumentBuilder` αφαιρεί την χαμηλού επιπέδου διαχείριση κόμβων, επιτρέποντάς σας να εστιάσετε στη διάταξη.  
3. **Εισάγετε μεμονωμένα σχήματα** – Πρώτα χρειάζεστε ξεχωριστά αντικείμενα (`insert rectangle shape` και μια έλλειψη) πριν τα ομαδοποιήσετε. Η ρύθμιση των `Left` και `Top` εξασφαλίζει ότι εμφανίζονται πλάι-πλάι.  
4. **Ομαδοποιήστε πολλαπλά σχήματα** – Δημιουργώντας ένα `GroupShape` και χρησιμοποιώντας **append child to group**, μετατρέπετε δύο ανεξάρτητα σχέδια σε μία λογική μονάδα. Η μετακίνηση ή η αλλαγή μεγέθους της ομάδας θα επηρεάσει και τα δύο παιδιά ταυτόχρονα.  
5. **Αποθηκεύστε το έγγραφο** – Το τελικό αρχείο, `GroupedShapes.docx`, μπορεί να ανοιχθεί στο Microsoft Word για να επαληθεύσετε ότι το ορθογώνιο και η έλλειψη είναι πράγματι ομαδοποιημένα (επιλέξτε ένα και και τα δύο θα μετακινηθούν μαζί).

### Αναμενόμενο αποτέλεσμα

Ανοίξτε το `GroupedShapes.docx` στο Microsoft Word:

- Θα δείτε ένα ορθογώνιο και μια έλλειψη τοποθετημένα δίπλα-δίπλα.  
- Η επιλογή οποιουδήποτε σχήματος επισημαίνει και τα δύο, επιβεβαιώνοντας ότι ανήκουν στην ίδια ομάδα.  
- Η ομάδα μπορεί να μετακινηθεί, να αλλάξει μέγεθος ή να μορφοποιηθεί ως ένα ενιαίο αντικείμενο.

![Διάγραμμα ομαδοποιημένου ορθογωνίου και έλλειψης μέσα σε έγγραφο Word](https://example.com/grouped-shapes.png){: .center-image alt="Διάγραμμα ομαδοποιημένου ορθογωνίου και έλλειψης μέσα σε έγγραφο Word"}

*Το στιγμιότυπο οθόνης απεικονίζει τα τελικά ομαδοποιημένα σχήματα.*

---

## Εισαγωγή σχήματος ορθογωνίου – προσαρμογή μεγέθους και στυλ

Αν χρειάζεστε ένα ορθογώνιο με συγκεκριμένο χρώμα γεμίσματος ή περιθώριο, τροποποιήστε το αντικείμενο `Shape` μετά την εισαγωγή:

```csharp
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.LineWidth = 2.0; // points
```

Αυτές οι ιδιότητες είναι μέρος της κλάσης `Shape` και λειτουργούν για οποιοδήποτε τύπο σχήματος, όχι μόνο για ορθογώνια. Η ρύθμιση του στυλ πριν από το **append child to group** εξασφαλίζει ότι η ομάδα κληρονομεί τις οπτικές ιδιότητες που ορίσατε.

---

## Ομαδοποίηση πολλαπλών σχημάτων – διαχείριση περισσότερων από δύο αντικειμένων

Το παράδειγμα ομαδοποιεί ένα ορθογώνιο και μια έλλειψη, αλλά μπορείτε να προσθέσετε οποιονδήποτε αριθμό σχημάτων:

```csharp
// Create additional shapes as needed
Shape triangle = builder.InsertShape(ShapeType.Triangle, 60, 60);
triangle.Left = ellipse.Left + ellipse.Width + 20;
triangle.Top = ellipse.Top;

// Append the new shape to the existing group
group.AppendChild(triangle);
```

**Συμβουλή:** Αφού δημιουργήσετε μια σύνθετη ομάδα, μπορείτε να κλειδώσετε τη διάταξή της για να αποτρέψετε τυχαίες αλλαγές:

```csharp
group.LockAspectRatio = true;
group.RelativeHorizontalPosition = RelativeHorizontalPosition.Margin;
group.RelativeVerticalPosition = RelativeVerticalPosition.Margin;
```

---

## Append child to group – η σειρά έχει σημασία

Η σειρά με την οποία καλείτε το `AppendChild` καθορίζει τη σειρά Z (ποιο σχήμα εμφανίζεται από πάνω). Στο παράδειγμα, το ορθογώνιο προστίθεται πρώτο, έπειτα η έλλειψη, έτσι η έλλειψη καλύπτει το ορθογώνιο αν διασταυρώνονται. Η αλλαγή σειράς είναι τόσο απλή όσο η κλήση του `RemoveChild` και η επανεισαγωγή:

```csharp
group.RemoveChild(ellipse);
group.AppendChild(ellipse); // now ellipse is on top
```

---

## Δημιουργία κενής αρχείου Word – επαναχρησιμοποιήσιμη βοηθητική μέθοδος

Αν η εφαρμογή σας χρειάζεται συχνά ένα νέο έγγραφο, ενσωματώστε τη λογική δημιουργίας:

```csharp
/// <summary>
/// Returns a new empty Document with a single section.
/// </summary>
static Document CreateBlankWordFile()
{
    Document emptyDoc = new Document();
    // Optionally set default page size, margins, etc.
    emptyDoc.FirstSection.PageSetup.PageWidth = 595;  // A4 width in points
    emptyDoc.FirstSection.PageSetup.PageHeight = 842; // A4 height in points
    return emptyDoc;
}
```

Στη συνέχεια μπορείτε να αντικαταστήσετε τη γραμμή `new Document()` στο κύριο πρόγραμμα με `CreateBlankWordFile()`. Αυτό δείχνει την έννοια **create blank word file** με επαναχρησιμοποιήσιμο τρόπο.

---

## Συνηθισμένα προβλήματα και πώς να τα αποφύγετε

| Πρόβλημα | Γιατί συμβαίνει | Διόρθωση |
|----------|------------------|----------|
| Τα σχήματα εμφανίζονται εκτός σελίδας | Οι προεπιλεγμένες τιμές `Left`/`Top` είναι 0, κάτι που τοποθετεί το σχήμα στο περιθώριο. | Ορίστε ρητά τα `Left` και `Top` μετά την εισαγωγή. |
| Η ομάδα χάνει μορφοποίηση | Η αλλαγή ενός παιδικού σχήματος μετά την προσθήκη του σε ομάδα μπορεί να διασπάσει τη διάταξη της ομάδας. | Εφαρμόστε όλες τις οπτικές ιδιότητες **πριν** καλέσετε το `AppendChild`. |
| Το αποθηκευμένο αρχείο είναι κενό | `DocumentBuilder` δεν χρησιμοποιήθηκε ποτέ για να προσθέσει κόμβο, ή το `doc.Save` κλήθηκε σε διαφορετικό αντικείμενο `Document`. | Βεβαιωθείτε ότι αποθηκεύετε το ίδιο `Document` που δημιουργήσατε. |
| Προειδοποιήσεις συμβατότητας στο Word | Χρήση νεότερων χαρακτηριστικών σχήματος που δεν υποστηρίζονται |  |

---

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Δημιουργία Group Shape σε έγγραφο Word χρησιμοποιώντας Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Εισαγωγή Σχημάτων σε έγγραφα Word χρησιμοποιώντας Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Δημιουργία σχήματος ορθογωνίου σε Word χρησιμοποιώντας C# – Οδηγός βήμα‑βήμα](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}