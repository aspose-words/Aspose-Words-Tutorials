---
category: general
date: 2026-11-18
description: Μάθετε πώς να δημιουργήσετε σχήμα ορθογωνίου σε ένα έγγραφο Word με C#.
  Ο οδηγός καλύπτει επίσης τον καθορισμό του μεγέθους του σχήματος, τη θέση του σχήματος
  και την ομαδοποίηση σχημάτων στο Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- set shape size
- group shapes in word
- set shape dimensions
- set shape position
language: el
lastmod: 2026-11-18
og_description: Δημιουργήστε σχήμα ορθογωνίου σε αρχείο Word χρησιμοποιώντας C# και
  μάθετε πώς να ορίζετε τις διαστάσεις του σχήματος, τη θέση του σχήματος και να ομαδοποιείτε
  σχήματα στο Word.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape created with C#
og_title: Δημιουργήστε σχήμα ορθογωνίου και ομαδοποιήστε σχήματα στο Word με C#
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  headline: How to create rectangle shape and group shapes in Word using C#
  type: TechArticle
- description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  name: How to create rectangle shape and group shapes in Word using C#
  steps:
  - name: Initialize the document and builder
    text: '```csharp using System; using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert a group shape
    text: '```csharp // Step 2: Insert a group shape that will hold multiple child
      shapes GroupShape group = builder.InsertGroupShape(); ```'
  - name: Create the rectangle and set its size
    text: '```csharp // Step 3: Create a rectangle shape, set its size, and add it
      to the group Shape rectangle = new Shape(doc, ShapeType.Rectangle); rectangle.Width
      = 100; // set shape size (width) in points rectangle.Height = 50; // set shape
      size (height) in points group.AppendChild(rectangle); ```'
  - name: Create the ellipse, set dimensions, and position it
    text: '```csharp // Step 4: Create an ellipse shape, set its size and position,
      and add it to the group Shape ellipse = new Shape(doc, ShapeType.Ellipse); ellipse.Width
      = 80; // set shape dimensions (width) ellipse.Height = 80; // set shape dimensions
      (height) ellipse.Left = 120; // set shape position rela'
  - name: Save the document
    text: '```csharp // Step 5: Save the document containing the grouped shapes doc.Save("GroupShape.docx");
      Console.WriteLine("Document saved successfully."); } } ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Πώς να δημιουργήσετε σχήμα ορθογωνίου και να ομαδοποιήσετε σχήματα στο Word
  χρησιμοποιώντας C#
url: /el/java/images-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-using/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε σχήμα ορθογωνίου και να ομαδοποιήσετε σχήματα στο Word με C#

Αν χρειάζεστε **create rectangle shape** σε ένα έγγραφο Word, αυτό το tutorial σας παρουσιάζει μια πλήρη, έτοιμη‑για‑εκτέλεση λύση. Θα δείτε πώς να ορίσετε το μέγεθος του σχήματος, τη θέση του σχήματος, και να ομαδοποιήσετε σχήματα στο Word ώστε να συμπεριφέρονται ως ένα ενιαίο αντικείμενο.

Η εργασία με σχήματα είναι μια κοινή απαίτηση όταν δημιουργείτε αναφορές, τιμολόγια ή διαγράμματα προγραμματιστικά. Στο τέλος αυτού του οδηγού θα μπορείτε να δημιουργήσετε ένα αρχείο `.docx` που περιέχει ένα ορθογώνιο, μια έλλειψη και ένα ομαδοποιημένο κοντέινερ—όλα δημιουργημένα με Aspose.Words for .NET.

## Προαπαιτούμενα

- .NET 6.0 SDK ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.7+)
- Πακέτο NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)
- Ένας επεξεργαστής κώδικα ή IDE (Visual Studio, VS Code, Rider, κ.λπ.)

Δεν απαιτούνται πρόσθετες βιβλιοθήκες.

## Πώς να δημιουργήσετε σχήμα ορθογωνίου και να ομαδοποιήσετε σχήματα στο Word

Τα βασικά βήματα είναι:

1. **Create a blank document** και ένα `DocumentBuilder`.
2. **Insert a `GroupShape`** που θα περιέχει τα μεμονωμένα σχήματα.
3. **Create a rectangle shape**, ορίστε τις διαστάσεις του και προσθέστε το στην ομάδα.
4. **Create an ellipse shape**, ορίστε το μέγεθος και τη θέση του, και προσθέστε το στην ομάδα.
5. **Save** το έγγραφο.

Κάθε βήμα εξηγείται παρακάτω, και ο πλήρης πηγαίος κώδικας ακολουθεί την εξήγηση.

### Βήμα 1: Αρχικοποίηση του εγγράφου και του builder

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` αντιπροσωπεύει ολόκληρο το αρχείο Word, ενώ `DocumentBuilder` παρέχει μια fluent API για την εισαγωγή περιεχομένου. Η αρχικοποίησή τους είναι υποχρεωτική πριν προσθέσετε οποιαδήποτε σχήματα.

### Βήμα 2: Εισαγωγή ομαδικού σχήματος

```csharp
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape group = builder.InsertGroupShape();
```

Ένα `GroupShape` λειτουργεί ως κοντέινερ· όλα τα παιδικά σχήματα κινούνται μαζί. Αυτή είναι η συνιστώμενη μέθοδος για **group shapes in Word** όταν χρειάζεστε συλλογικές μετασχηματισμούς (π.χ., μετακίνηση, περιστροφή ή διαγραφή).

### Βήμα 3: Δημιουργία του ορθογωνίου και ορισμός του μεγέθους

```csharp
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle);
```

Εδώ **create rectangle shape** και **set shape size** ορίζοντας `Width` και `Height`. Στο Aspose.Words, τα μεγέθη εκφράζονται σε points (1 pt ≈ 1/72 in). Ο καθορισμός των διαστάσεων ρητά εξασφαλίζει ότι το ορθογώνιο εμφανίζεται ακριβώς όπως προορίζεται.

### Βήμα 4: Δημιουργία της έλλειψης, ορισμός διαστάσεων και τοποθέτηση

```csharp
        // Step 4: Create an ellipse shape, set its size and position, and add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position relative to the group
        group.AppendChild(ellipse);
```

Οι **set shape dimensions** για την έλλειψη είναι ίδιες για πλάτος και ύψος, δημιουργώντας έναν τέλειο κύκλο. Η ιδιότητα `Left` δείχνει **set shape position**: η έλλειψη ξεκινά 120 pt δεξιά από το σημείο προέλευσης της ομάδας, ώστε να μην επικαλύπτεται με το ορθογώνιο.

### Βήμα 5: Αποθήκευση του εγγράφου

```csharp
        // Step 5: Save the document containing the grouped shapes
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document saved successfully.");
    }
}
```

Η αποθήκευση γράφει το αρχείο Word στο δίσκο. Μπορείτε να ανοίξετε το `GroupShape.docx` στο Microsoft Word για να επαληθεύσετε ότι το ορθογώνιο και η έλλειψη είναι ομαδοποιημένα και τοποθετημένα σωστά.

## Ορισμός διαστάσεων σχήματος και μεγέθους – πιο βαθιά ματιά

- **Points vs. inches**: 72 pt = 1 in. Αν προτιμάτε ίντσες, πολλαπλασιάστε με 72 (π.χ., `2.5 * 72` για 2.5 in).
- **Automatic scaling**: Εάν παραλείψετε το `Width` ή το `Height`, το σχήμα χρησιμοποιεί το προεπιλεγμένο του μέγεθος. Ορίστε ρητά **set shape size** για να αποφύγετε εκπλήξεις στη διάταξη.
- **Aspect ratio**: Για σχήματα όπως το `Ellipse`, η διατήρηση ίσου `Width` και `Height` διατηρεί την κυκλική εμφάνιση.

## Τοποθέτηση σχήματος στο Word

Οι ιδιότητες `Left` και `Top` ελέγχουν την απόσταση του σχήματος μέσα στο κοντέινερ του (η ομάδα ή η σελίδα). Θετικές τιμές μετακινούν το σχήμα δεξιά/κάτω, αρνητικές τιμές το μετακινούν αριστερά/πάνω. Όταν γίνεται ομαδοποίηση, οι θέσεις είναι σχετικές με το σημείο προέλευσης της ομάδας, κάτι που απλοποιεί τους υπολογισμούς διάταξης.

## Ομαδοποίηση σχημάτων στο Word χρησιμοποιώντας Aspose.Words

Η ομαδοποίηση είναι απαραίτητη όταν θέλετε πολλά σχήματα να λειτουργούν ως μία ενιαία μονάδα. Το αντικείμενο `GroupShape`:

- Υποστηρίζει `AppendChild` για την προσθήκη οποιουδήποτε `Shape` (rectangle, ellipse, image, κ.λπ.).
- Σας επιτρέπει να μετακινήσετε, περιστρέψετε ή διαγράψετε ολόκληρη την ομάδα με μία κλήση.
- Διατηρεί τις θέσεις των παιδικών σχημάτων σχετικές με την ομάδα, κάνοντας τα σύνθετα διαγράμματα πιο εύκολα στη διαχείριση.

**Pro tip:** Μετά την προσθήκη όλων των παιδικών σχημάτων, μπορείτε να προσαρμόσετε το `Width`, `Height`, `Left` και `Top` της ομάδας για να μετατοπίσετε ολόκληρη τη συλλογή σε ένα βήμα.

## Πλήρες εκτελέσιμο παράδειγμα

Παρακάτω είναι το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε, επικολλήσετε και εκτελέσετε. Περιλαμβάνει όλες τις οδηγίες `using`, μια μέθοδο `Main` και σχόλια που εξηγούν κάθε γραμμή.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a GroupShape to hold child shapes
        GroupShape group = builder.InsertGroupShape();

        // 3️⃣ Create a rectangle, set its dimensions, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle); // add rectangle to the group

        // 4️⃣ Create an ellipse, set size and position, then add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position inside the group
        group.AppendChild(ellipse); // add ellipse to the group

        // 5️⃣ Save the document
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document 'GroupShape.docx' created with a rectangle and an ellipse grouped together.");
    }
}
```

**Expected output:** Μετά την εκτέλεση του προγράμματος, το `GroupShape.docx` εμφανίζεται στο φάκελο εκτέλεσης. Ανοίγοντας το στο Word δείχνει ένα ορθογώνιο (100 pt × 50 pt) στα αριστερά και μια έλλειψη (80 pt × 80 pt) τοποθετημένη 120 pt δεξιά, και τα δύο μέσα σε ένα ενιαίο ομαδοποιημένο αντικείμενο.

![Έγγραφο Word με ομαδοποιημένο ορθογώνιο και έλλειψη](grouped_shapes.png){: .center alt="Στιγμιότυπο οθόνης ενός εγγράφου Word που εμφανίζει ένα ομαδοποιημένο ορθογώνιο και έλλειψη δημιουργημένα με C#" }

*Η παραπάνω εικόνα απεικονίζει το τελικό αποτέλεσμα· το ορθογώνιο και η έλλειψη μπορούν να επιλεγούν ως μία ομάδα.*

## Συχνές ερωτήσεις και ειδικές περιπτώσεις

| Question | Answer |
|----------|--------|
| **Μπορώ να προσθέσω περισσότερα από δύο σχήματα;** | Ναι. Καλέστε `group.AppendChild(yourShape)` για κάθε επιπλέον σχήμα. |
| **Τι γίνεται αν χρειαστεί να περιστρέψω την ομάδα;** | Χρησιμοποιήστε `group.RotationAngle = 45;` (μοίρες) μετά την προσθήκη όλων των παιδιών. |
| **Πώς μπορώ να αλλάξω το χρώμα φόντου της ομάδας;** | Ορίστε `group.FillColor = System.Drawing.Color.LightGray;`. |
| **Θα λειτουργήσει αυτό με αρχεία .doc;** | Το Aspose.Words υποστηρίζει `.doc` και `.docx`. Ο ίδιος κώδικας λειτουργεί· απλώς αλλάξτε την επέκταση αρχείου στην `Save`. |
| **Υπάρχει επίπτωση στη μνήμη όταν ομαδοποιούνται πολλά σχήματα;** | Η ομαδοποίηση προσθέτει ελάχιστο κόστος. Η κύρια ανησυχία είναι ο συνολικός αριθμός σχημάτων· διατηρήστε τον σε λογικά επίπεδα για μεγάλα έγγραφα. |

## Συμπέρασμα

Σε αυτόν τον οδηγό μάθατε πώς να **create rectangle shape** σε ένα αρχείο Word χρησιμοποιώντας C#, πώς να **set shape size**, **set shape dimensions**, **set shape position**, και τέλος πώς να **group shapes in Word** με Aspose.Words. Το πλήρες παράδειγμα δείχνει μια καθαρή, συντηρήσιμη προσέγγιση που μπορείτε να επεκτείνετε σε πιο σύνθετα διαγράμματα, γραφήματα ή προσαρμοσμένα γραφικά.

Next, you might explore:

- Προσθήκη κειμένου μέσα σε σχήματα (`Shape.TextPath.Text = "Hello"`).
- Εισαγωγή εικόνων σε ένα `GroupShape`.
- Εξαγωγή των ομαδοποιημένων σχημάτων σε PDF με `doc.Save("output.pdf")`.

Νιώστε ελεύθεροι να πειραματιστείτε με διαφορετικά μεγέθη, θέσεις και πρόσθετους τύπους σχημάτων για να ταιριάζουν στις ανάγκες του έργου σας. Καλή προγραμματιστική!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κατακτήσετε πρόσθετες δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να δημιουργήσετε σχήμα ορθογωνίου και να ομαδοποιήσετε σχήματα στο Word με Aspose.Words](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)
- [Δημιουργία Group Shape σε έγγραφο Word χρησιμοποιώντας Aspose.Words για .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}