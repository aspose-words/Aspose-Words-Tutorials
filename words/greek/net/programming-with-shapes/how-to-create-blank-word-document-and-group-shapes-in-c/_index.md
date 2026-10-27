---
category: general
date: 2026-10-07
description: Δημιουργήστε κενό έγγραφο Word σε C# και μάθετε πώς να προσθέτετε σχήμα
  ορθογωνίου, να εισάγετε σχήμα εικόνας και να ομαδοποιείτε πολλαπλά σχήματα για δυναμικές
  αναφορές.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- insert image shape
- group multiple shapes
- add image to word
language: el
lastmod: 2026-10-07
og_description: Δημιουργήστε κενό έγγραφο Word σε C# με το Aspose.Words. Μάθετε πώς
  να προσθέσετε σχήμα ορθογωνίου, να εισάγετε σχήμα εικόνας και να ομαδοποιήσετε πολλαπλά
  σχήματα για επαγγελματικά έγγραφα.
og_image_alt: Screenshot of a Word file showing a grouped rectangle and logo created
  with C#
og_title: Δημιουργήστε κενό έγγραφο Word και ομαδοποιήστε σχήματα σε C# – οδηγός βήμα
  προς βήμα
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create blank Word document in C# and learn to add rectangle shape,
    insert image shape, and group multiple shapes for dynamic reports.
  headline: How to create blank Word document and group shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Πώς να δημιουργήσετε κενό έγγραφο Word και να ομαδοποιήσετε σχήματα σε C#
url: /el/net/programming-with-shapes/how-to-create-blank-word-document-and-group-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε κενό έγγραφο Word και να ομαδοποιήσετε σχήματα σε C#

Αν χρειάζεστε **να δημιουργήσετε κενό έγγραφο Word** προγραμματιστικά, αυτός ο οδηγός σας δείχνει ακριβώς πώς. Θα δείτε πώς να **προσθέσετε σχήμα ορθογωνίου**, **εισάγετε σχήμα εικόνας**, και **ομαδοποιήσετε πολλαπλά σχήματα** ώστε να συμπεριφέρονται ως ένα ενιαίο αντικείμενο όταν **προσθέσετε εικόνα στο Word** αργότερα.

Η εργασία με αρχεία Word από κώδικα μπορεί να φαίνεται τρομακτική, αλλά το Aspose.Words κάνει τη διαδικασία απλή. Στο τέλος αυτού του tutorial θα έχετε ένα επαναχρησιμοποιήσιμο απόσπασμα C# που δημιουργεί ένα καθαρό, κενό αρχείο Word που περιέχει ένα ομαδοποιημένο ορθογώνιο και λογότυπο. Μπορείτε να ενσωματώσετε το αποτέλεσμα σε τιμολόγια, αναφορές ή οποιαδήποτε αυτοματοποιημένη ροή εγγράφων.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.7+).  
* Ένα έγκυρο license του Aspose.Words for .NET ή ένα δωρεάν κλειδί αξιολόγησης.  
* Ένα αρχείο εικόνας (π.χ., `logo.png`) τοποθετημένο σε φάκελο που μπορείτε να αναφέρετε από τον κώδικα.  
* Visual Studio 2022 ή οποιοδήποτε IDE συμβατό με C#.

Δεν απαιτούνται πρόσθετα πακέτα NuGet πέρα από το `Aspose.Words`.

## Πώς να δημιουργήσετε κενό έγγραφο Word με το Aspose.Words

Το πρώτο βήμα είναι πάντα **να δημιουργήσετε κενό έγγραφο Word**. Αυτό το αντικείμενο θα φιλοξενήσει όλα τα επόμενα σχήματα.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// 1️⃣ Initialize a new empty document.
Document doc = new Document();

// 2️⃣ Prepare a DocumentBuilder – it simplifies adding content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` αντιπροσωπεύει ολόκληρο το αρχείο `.docx`. Σε αυτό το σημείο το αρχείο είναι κενό, ικανοποιώντας την απαίτηση *να δημιουργήσετε κενό έγγραφο Word*.

## Δημιουργία ενός περιέκτη για ομαδοποίηση πολλαπλών σχημάτων

Η ομαδοποίηση σχημάτων σας επιτρέπει να τα μετακινείτε, περιστρέφετε ή αλλάζετε το μέγεθός τους μαζί. Το Aspose.Words παρέχει την κλάση `GroupShape` για αυτό το σκοπό.

```csharp
// 3️⃣ Create a GroupShape that will hold our drawing objects.
GroupShape group = new GroupShape(doc)
{
    // Define the container’s position and size on the page.
    Bounds = new Rectangle(50, 50, 300, 200)
};

// Append the group to the first paragraph of the first section.
doc.FirstSection.Body.FirstParagraph.AppendChild(group);
```

Το ορθογώνιο `Bounds` καθορίζει πού εμφανίζεται η ομάδα στη σελίδα. Τοποθετώντας την ομάδα στην πρώτη παράγραφο, εξασφαλίζετε ότι το **να δημιουργήσετε κενό έγγραφο Word** θα περιέχει αμέσως ένα οπτικό περιέκτη.

## Πώς να προσθέσετε σχήμα ορθογωνίου μέσα στην ομάδα

Μια συχνή απαίτηση είναι **να προσθέσετε σχήμα ορθογωνίου** ως φόντο ή περίγραμμα. Ο παρακάτω κώδικας δημιουργεί ένα ορθογώνιο και το προσθέτει στην προηγουμένως ορισμένη ομάδα.

```csharp
// 4️⃣ Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width = 100,
    Height = 80,
    Left = 20,
    Top = 20,
    // Optional: give the rectangle a light gray fill.
    FillColor = Color.LightGray
};

// Add the rectangle to the group.
group.AppendChild(rectangle);
```

Επειδή το ορθογώνιο βρίσκεται μέσα στο `GroupShape`, θα μετακινείται μαζί με τυχόν άλλα σχήματα που προσθέτετε αργότερα. Αυτό αποτελεί τον πυρήνα της λειτουργίας **ομαδοποίησης πολλαπλών σχημάτων**.

## Πώς να εισάγετε σχήμα εικόνας μέσα στην ομάδα

Στη συνέχεια, θα **εισάγετε σχήμα εικόνας** (το λογότυπο) και θα το τοποθετήσετε δίπλα στο ορθογώνιο. Αυτό επιδεικνύει τη ροή εργασίας **προσθήκη εικόνας στο Word**.

```csharp
// 5️⃣ Create an image shape.
Shape picture = new Shape(doc, ShapeType.Image)
{
    Width = 80,
    Height = 80,
    Left = 150,
    Top = 30
};

// Load the image from disk. Replace the path with your actual image location.
picture.ImageData.SetImage(Image.FromFile(@"YOUR_DIRECTORY/logo.png"));

// Add the image shape to the same group.
group.AppendChild(picture);
```

Η μέθοδος `SetImage` διαβάζει το αρχείο και το ενσωματώνει απευθείας στο έγγραφο Word, εξασφαλίζοντας ότι η εικόνα παραμένει ακόμη και όταν το αρχικό αρχείο μετακινηθεί. Αυτό ολοκληρώνει το βήμα **εισαγωγής σχήματος εικόνας** και τελειοποιεί την απαίτηση **προσθήκη εικόνας στο Word**.

## Αποθήκευση του εγγράφου

Τέλος, αποθηκεύστε το αρχείο στο δίσκο. Το αποθηκευμένο αρχείο περιέχει το κενό έγγραφο, το ομαδοποιημένο ορθογώνιο και το ενσωματωμένο λογότυπο.

```csharp
// 6️⃣ Save the document with the grouped shapes.
doc.Save(@"YOUR_DIRECTORY/GroupShape.docx");
```

Όταν ανοίξετε το `GroupShape.docx` στο Microsoft Word, θα δείτε μια ενιαία ομάδα που περιλαμβάνει ένα ανοιχτό‑γκρι ορθογώνιο και το λογότυπο τοποθετημένο πλάι‑πλάι. Επιλέγοντας οποιοδήποτε μέρος της ομάδας μπορείτε να μετακινήσετε ή να αλλάξετε το μέγεθός της, αποδεικνύοντας ότι τα σχήματα είναι πράγματι **ομαδοποιημένα πολλαπλά σχήματα**.

## Πλήρες, εκτελέσιμο παράδειγμα

Παρακάτω βρίσκεται το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε, επικολλήσετε και να εκτελέσετε. Αντικαταστήστε το `YOUR_DIRECTORY` με μια απόλυτη ή σχετική διαδρομή που υπάρχει στον υπολογιστή σας.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank Word document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Create a GroupShape to hold the rectangle and image.
        GroupShape group = new GroupShape(doc)
        {
            Bounds = new Rectangle(50, 50, 300, 200)
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(group);

        // Step 3: Add a rectangle shape inside the group.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 100,
            Height = 80,
            Left = 20,
            Top = 20,
            FillColor = Color.LightGray
        };
        group.AppendChild(rectangle);

        // Step 4: Insert an image shape inside the group.
        Shape picture = new Shape(doc, ShapeType.Image)
        {
            Width = 80,
            Height = 80,
            Left = 150,
            Top = 30
        };
        picture.ImageData.SetImage(Image.FromFile(@"YOUR_DIRECTORY/logo.png"));
        group.AppendChild(picture);

        // Step 5: Save the document.
        doc.Save(@"YOUR_DIRECTORY/GroupShape.docx");
    }
}
```

### Αναμενόμενο αποτέλεσμα

* Ένα αρχείο με όνομα `GroupShape.docx` τοποθετημένο στο `YOUR_DIRECTORY`.  
* Το άνοιγμα του αρχείου στο Word εμφανίζει μια ενιαία οπτική ομάδα που περιέχει ένα γκρι ορθογώνιο στα αριστερά και το `logo.png` στα δεξιά.  
* Επιλέγοντας οποιοδήποτε μέρος της οπτικής ομάδας μπορείτε να μετακινήσετε ή να αλλάξετε το μέγεθός της, επιβεβαιώνοντας ότι τα σχήματα είναι σωστά **ομαδοποιημένα πολλαπλά σχήματα**.

## Συχνές ερωτήσεις και αντιμετώπιση ειδικών περιπτώσεων

| Ερώτηση | Απάντηση |
|---|---|
| **Μπορώ να προσθέσω περισσότερα από δύο σχήματα στην ίδια ομάδα;** | Ναι. Καλέστε `group.AppendChild(yourShape)` για κάθε επιπλέον `Shape`. Η ομάδα μπορεί να περιέχει οποιονδήποτε αριθμό αντικειμένων σχεδίασης. |
| **Τι γίνεται αν λείπει το αρχείο εικόνας;** | Η `SetImage` θα ρίξει `FileNotFoundException`. Περιβάλλετε την κλήση με try‑catch και παρέχετε εναλλακτική (π.χ., σχήμα placeholder). |
| **Πρέπει να ορίσω `WrapType` για τα σχήματα;** | Από προεπιλογή τα σχήματα είναι inline. Αν χρειάζεστε αιωρούμενη συμπεριφορά, ορίστε `picture.WrapType = WrapType.Inline;` ή άλλο wrap mode πριν τα προσθέσετε στην ομάδα. |
| **Πώς το μέγεθος του εγγράφου επηρεάζει τα όρια της ομάδας;** | Το ορθογώνιο `Bounds` ορίζεται σε points (1 pt ≈ 1/72 in). Προσαρμόστε το μέγεθος αν τοποθετήσετε την ομάδα σε διαφορετική διάταξη σελίδας (π.χ., A4 vs. Letter). |
| **Μπορώ να επαναχρησιμοποιήσω την ίδια ομάδα σε άλλο έγγραφο;** | Ναι. Κλωνοποιήστε την ομάδα με `GroupShape cloned = (GroupShape)group.Clone(true);` και εισάγετέ την σε διαφορετικό `Document`. |

## Συμβουλές επαγγελματιών

* **Επαναχρησιμοποιήστε το `DocumentBuilder`** για προσθήκη κειμένου πριν ή μετά την ομάδα. Αυτό σέβεται αυτόματα τη τρέχουσα θέση του κέρσορα.  
* **Ορίστε `Shape.StrokeColor`** αν χρειάζεστε ορατό περίγραμμα γύρω από το ορθογώνιο.  
* **Χρησιμοποιήστε PNG υψηλής ανάλυσης** για το λογότυπο ώστε να αποφύγετε την εμφάνιση εικονοστοιχείων όταν  

## Τι πρέπει να μάθετε στη συνέχεια;

Οι παρακάτω οδηγίες καλύπτουν στενά σχετικές θεματικές που επεκτείνουν τις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}