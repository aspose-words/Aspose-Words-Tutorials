---
category: general
date: 2026-09-18
description: Δημιουργήστε σχήμα ορθογωνίου σε έγγραφο Word χρησιμοποιώντας C#. Μάθετε
  πώς να προσθέτετε πολλαπλά σχήματα, να προσθέτετε σχήματα σε μια ομάδα και να εισάγετε
  σχήμα ομάδας με το Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add multiple shapes
- add shapes to group
- insert group shape
language: el
lastmod: 2026-09-18
og_description: Δημιουργήστε σχήμα ορθογωνίου σε αρχείο Word με C#. Αυτός ο οδηγός
  δείχνει πώς να προσθέσετε πολλαπλά σχήματα, να προσθέσετε σχήματα σε μια ομάδα και
  να εισάγετε σχήμα ομάδας χρησιμοποιώντας το Aspose.Words.
og_image_alt: Grouped rectangle and ellipse shapes displayed in a Word document
og_title: Δημιουργία σχήματος ορθογωνίου και ομαδοποίηση σχημάτων σε C#
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create rectangle shape in a Word document using C#. Learn how to add
    multiple shapes, add shapes to a group, and insert group shape with Aspose.Words.
  headline: Create rectangle shape and group multiple shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Shape
- GroupShape
title: Δημιουργία σχήματος ορθογωνίου και ομαδοποίηση πολλαπλών σχημάτων σε C#
url: /el/net/programming-with-shapes/create-rectangle-shape-and-group-multiple-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία σχήματος ορθογωνίου και ομαδοποίηση πολλαπλών σχημάτων σε C#

Αν χρειάζεστε **δημιουργία σχήματος ορθογωνίου** σε ένα έγγραφο Word, αυτό το tutorial παρουσιάζει μια πλήρη λύση. Θα δείτε πώς να **προσθέσετε πολλαπλά σχήματα**, **προσθέσετε σχήματα σε ομάδα** και **εισάγετε σχήμα ομάδας** χρησιμοποιώντας το Aspose.Words API για .NET.

Η εργασία με σχήματα είναι συχνή απαίτηση όταν δημιουργείτε αναφορές, συμβόλαια ή υλικό μάρκετινγκ προγραμματιστικά. Στο τέλος αυτού του οδηγού θα έχετε μια εκτελέσιμη εφαρμογή C# console που παράγει ένα αρχείο `.docx` που περιέχει ένα ορθογώνιο, μια έλλειψη και μια ομάδα που περιλαμβάνει και τα δύο σχήματα.

Οι μόνοι προαπαιτούμενοι είναι ένα πρόσφατο .NET SDK (6.0 ή νεότερο) και μια αδειοδοτημένη έκδοση του Aspose.Words for .NET. Δεν απαιτούνται επιπλέον εργαλεία.

## Προαπαιτούμενα

- .NET 6.0 SDK ή νεότερο  
- Aspose.Words for .NET (πακέτο NuGet `Aspose.Words`)  
- Βασική εξοικείωση με τη σύνταξη C#  

Μπορείτε να εγκαταστήσετε το πακέτο με την ακόλουθη εντολή:

```bash
dotnet add package Aspose.Words
```

## Βήμα 1: Δημιουργία σχήματος ορθογωνίου με Aspose.Words

Το πρώτο βήμα είναι η δημιουργία ενός αντικειμένου `Shape` τύπου `Rectangle`. Αυτό το αντικείμενο αντιπροσωπεύει το οπτικό ορθογώνιο που θα εμφανιστεί στο έγγραφο.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty document
Document doc = new Document();

// Initialize a DocumentBuilder for editing the document
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape: width = 100 points, height = 50 points
Shape rectangle = new Shape(doc, ShapeType.Rectangle);
rectangle.Width = 100;
rectangle.Height = 50;

// Optional: give the rectangle a fill color and a border
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.StrokeWeight = 1.0;

// Insert the rectangle at the current builder position
builder.InsertNode(rectangle);
```

**Γιατί είναι σημαντικό:** `ShapeType.Rectangle` λέει στο Aspose.Words να αποδώσει ένα γεωμετρικό ορθογώνιο. Ορίζοντας το `Width` και το `Height` καθορίζετε το μέγεθός του σε points (1 point = 1/72 ίντσα). Η προσθήκη χρωμάτων γεμίσματος και περιγράμματος κάνει το σχήμα ορατό χωρίς επιπλέον στυλ.

## Βήμα 2: Προσθήκη πολλαπλών σχημάτων στο έγγραφο

Μετά το ορθογώνιο, μπορείτε να δημιουργήσετε όποιον αριθμό επιπλέον σχημάτων θέλετε. Σε αυτό το παράδειγμα προσθέτουμε μια έλλειψη για να δείξουμε πώς λειτουργεί η **προσθήκη πολλαπλών σχημάτων**.

```csharp
// Create an ellipse shape: width = 80 points, height = 80 points
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width = 80;
ellipse.Height = 80;

// Style the ellipse
ellipse.FillColor = System.Drawing.Color.LightCoral;
ellipse.StrokeColor = System.Drawing.Color.Maroon;
ellipse.StrokeWeight = 1.0;

// Insert the ellipse after the rectangle
builder.InsertNode(ellipse);
```

**Γιατί είναι σημαντικό:** Κάθε κλήση στο `new Shape` δημιουργεί ένα ανεξάρτητο αντικείμενο σχεδίασης. Εισάγοντας τα διαδοχικά χτίζετε μια συλλογή σχημάτων που μπορεί αργότερα να ομαδοποιηθεί ή να τοποθετηθεί ξεχωριστά.

## Βήμα 3: Προσθήκη σχημάτων σε ομάδα

Η ομαδοποίηση σχημάτων απλοποιεί τη διαχείριση διάταξης, επειδή η ομάδα συμπεριφέρεται ως ένας ενιαίος κόμβος. Αυτό το βήμα δείχνει πώς να **προσθέσετε σχήματα σε ομάδα** χρησιμοποιώντας `GroupShape`.

```csharp
// Create a GroupShape with a bounding box of 200x200 points
GroupShape group = new GroupShape(doc, 200, 200);

// Move the builder's cursor back to the start of the document
builder.MoveToDocumentStart();

// Insert the empty group into the document
builder.InsertNode(group);

// Append the previously created rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

**Γιατί είναι σημαντικό:** Το `GroupShape` λειτουργεί σαν ένα δοχείο. Όταν μετακινείτε, περιστρέφετε ή αλλάζετε το μέγεθος της ομάδας, όλα τα παιδικά σχήματα ακολουθούν αυτόματα. Το πλαίσιο περιγράμματος (200 × 200 points) ορίζει το χώρο συντεταγμένων για τα παιδικά σχήματα.

## Βήμα 4: Εισαγωγή σχήματος ομάδας στο έγγραφο

Τώρα που η ομάδα περιέχει το ορθογώνιο και την έλλειψη, πρέπει να **εισάγετε σχήμα ομάδας** στην επιθυμητή θέση. Ο builder είχε ήδη τοποθετήσει την κενή ομάδα, αλλά μπορείτε επίσης να την εισάγετε αλλού αν χρειαστεί.

```csharp
// Position the group at a specific location (optional)
group.Left = 50;   // 50 points from the left margin
group.Top = 100;   // 100 points from the top margin

// Save the document with the grouped shapes
doc.Save("GroupShapeExample.docx");
```

**Γιατί είναι σημαντικό:** Η ρύθμιση των `Left` και `Top` μετακινεί ολόκληρη την ομάδα μέσα στη σελίδα. Η αποθήκευση του εγγράφου γράφει την ιεραρχία σχημάτων σε ένα αρχείο `.docx` που μπορεί να ανοιχθεί στο Microsoft Word, LibreOffice ή οποιονδήποτε συμβατό προβολέα.

## Πλήρες εκτελέσιμο παράδειγμα

Ακολουθεί το πλήρες πρόγραμμα που συνδυάζει όλα τα βήματα. Αντιγράψτε τον κώδικα σε ένα νέο console project και τρέξτε το για να δημιουργήσετε το `GroupShapeExample.docx`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document
            Document doc = new Document();

            // Step 2: Initialize a DocumentBuilder for editing the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle);
            rectangle.Width = 100;
            rectangle.Height = 50;
            rectangle.FillColor = Color.LightBlue;
            rectangle.StrokeColor = Color.DarkBlue;
            rectangle.StrokeWeight = 1.0;

            // Step 4: Create an ellipse shape
            Shape ellipse = new Shape(doc, ShapeType.Ellipse);
            ellipse.Width = 80;
            ellipse.Height = 80;
            ellipse.FillColor = Color.LightCoral;
            ellipse.StrokeColor = Color.Maroon;
            ellipse.StrokeWeight = 1.0;

            // Step 5: Create a GroupShape that will hold both shapes
            GroupShape group = new GroupShape(doc, 200, 200);
            group.Left = 50;   // optional positioning
            group.Top = 100;   // optional positioning

            // Add the rectangle and ellipse to the group
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Insert the group into the document at the current builder position
            builder.InsertNode(group);

            // Step 6: Save the document containing the grouped shapes
            doc.Save("GroupShapeExample.docx");

            Console.WriteLine("Document saved successfully.");
        }
    }
}
```

**Αναμενόμενο αποτέλεσμα:**  
Ανοίγοντας το `GroupShapeExample.docx` εμφανίζεται μια ενιαία ομάδα που περιέχει ένα ανοιχτό‑μπλε ορθογώνιο και μια ανοιχτό‑κόκκινη έλλειψη, και τα δύο τοποθετημένα μέσα σε ένα δοχείο 200 × 200 points. Η ομάδα μπορεί να επιλεγεί ως ένα αντικείμενο στο Word, επιβεβαιώνοντας ότι η **προσθήκη σχημάτων σε ομάδα** πέτυχε.

## Συνηθισμένες παραλλαγές και περιπτώσεις άκρων

| Κατάσταση | Προτεινόμενη προσαρμογή |
|-----------|------------------------|
| Διαφορετικοί τύποι σχημάτων (π.χ., `ShapeType.Line`) | Δημιουργήστε το σχήμα με τον επιθυμητό `ShapeType` και ορίστε τη γεωμετρία του αναλόγως. |
| Απαιτείται περιστροφή σχήματος | Χρησιμοποιήστε `shape.Rotation = 45;` (μοίρες) πριν το προσθέσετε στην ομάδα. |
| Μεγαλύτερα έγγραφα με πολλές ομάδες | Επαναχρησιμοποιήστε ένα μόνο αντικείμενο `DocumentBuilder`; αποφύγετε τη δημιουργία νέου builder για κάθε ομάδα ώστε να μειώσετε το φορτίο μνήμης. |
| Αποθήκευση σε PDF αντί για DOCX | Καλέστε `doc.Save("output.pdf", SaveFormat.Pdf);` μετά την εισαγωγή της ομάδας. |

**Συμβουλή:** Πάντα ορίζετε ρητές τιμές `Left` και `Top` για την ομάδα όταν χρειάζεστε ακριβή τοποθέτηση. Αν τις παραλείψετε, η ομάδα κληρονομεί τη τρέχουσα θέση του cursor του builder, κάτι που μπορεί να οδηγήσει σε απρόσμενα αποτελέσματα διάταξης.

## Συμπέρασμα

Τώρα ξέρετε πώς να **δημιουργήσετε σχήμα ορθογωνίου**, **προσθέσετε πολλαπλά σχήματα**, **προσθέσετε σχήματα σε ομάδα** και **εισάγετε σχήμα ομάδας** σε ένα έγγραφο Word χρησιμοποιώντας C#. Το πλήρες παράδειγμα δείχνει τη συνολική ροή εργασίας από τη δημιουργία του εγγράφου μέχρι την αποθήκευση του τελικού αρχείου.  

Στη συνέχεια, εξερευνήστε σχετικά θέματα όπως **τοποθέτηση σχημάτων σε σχέση με κείμενο**, **εφαρμογή αναδίπλωσης κειμένου** και **εξαγωγή ομαδοποιημένων σχημάτων σε PDF**. Αυτές οι επεκτάσεις σας επιτρέπουν να δημιουργήσετε σύνθετες, προγραμματιστικές διατάξεις εγγράφων με το Aspose.Words.

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στην υλοποίηση των δικών σας έργων.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}