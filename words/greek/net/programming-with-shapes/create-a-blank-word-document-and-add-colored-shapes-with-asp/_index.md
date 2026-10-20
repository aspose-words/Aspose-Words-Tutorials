---
category: general
date: 2026-09-21
description: Δημιουργήστε ένα κενό έγγραφο Word χρησιμοποιώντας το Aspose.Words, ορίστε
  το μέγεθος του σχήματος, τη θέση του σχήματος, το χρώμα του σχήματος και αποθηκεύστε
  το αρχείο docx σε μία ενιαία διαδικασία.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set shape size
- save docx file
- set shape position
- set shape color
language: el
lastmod: 2026-09-21
og_description: Δημιουργήστε ένα κενό έγγραφο Word, ορίστε το μέγεθος του σχήματος,
  τη θέση του σχήματος, το χρώμα του σχήματος και αποθηκεύστε το αρχείο docx με το
  Aspose.Words σε λίγα λεπτά.
og_image_alt: Screenshot of a blank Word document containing two colored rectangles
  grouped together
og_title: Δημιουργήστε ένα κενό έγγραφο Word και προσθέστε χρωματιστά σχήματα – Οδηγός
  Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create a blank Word document using Aspose.Words, set shape size, set
    shape position, set shape color, and save the docx file in a single walkthrough.
  headline: Create a blank Word document and add colored shapes with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Δημιουργήστε ένα κενό έγγραφο Word και προσθέστε χρωματιστά σχήματα με το Aspose.Words
url: /el/net/programming-with-shapes/create-a-blank-word-document-and-add-colored-shapes-with-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργήστε ένα κενό έγγραφο Word και προσθέστε χρωματιστά σχήματα με Aspose.Words

Αν χρειάζεστε **δημιουργία κενών εγγράφων Word** προγραμματιστικά, αυτός ο οδηγός σας δείχνει πώς να το κάνετε με το Aspose.Words. Θα μάθετε πώς να **ορίζετε το μέγεθος του σχήματος**, **ορίζετε τη θέση του σχήματος**, **ορίζετε το χρώμα του σχήματος**, και τέλος **αποθηκεύετε το αρχείο .docx** χωρίς να φύγετε από το IDE σας.

Η εργασία με αρχεία Word σε C# συχνά σημαίνει χειρισμό χαμηλού επιπέδου κλήσεων OpenXML, αλλά το Aspose.Words αφαιρεί την πολυπλοκότητα. Στο τέλος αυτού του tutorial θα έχετε ένα πλήρως λειτουργικό `.docx` που περιέχει ένα ομαδοποιημένο σχήμα αποτελούμενο από δύο χρωματιστά ορθογώνια—ιδανικό για αναφορές, πιστοποιητικά ή προσαρμοσμένα πρότυπα.

## Προαπαιτούμενα

- .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.7+)
- Aspose.Words for .NET 23.9 ή νεότερο (εγκατάσταση μέσω NuGet: `Install-Package Aspose.Words`)
- Βασική εξοικείωση με C# και Visual Studio (ή οποιονδήποτε επεξεργαστή C#)

Δεν απαιτείται υπάρχον αρχείο Word· το tutorial ξεκινά με **δημιουργία κενών εγγράφων Word** από το μηδέν.

## Δημιουργία κενών εγγράφων Word με Aspose.Words

Το πρώτο βήμα είναι η δημιουργία ενός αντικειμένου `Document`. Αυτό το αντικείμενο αντιπροσωπεύει ένα κενό αρχείο Word στη μνήμη.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty document.
Document document = new Document();

// DocumentBuilder gives you a cursor to add content.
DocumentBuilder builder = new DocumentBuilder(document);
```

Το `Document` ξεκινά κενό, που είναι ακριβώς αυτό που χρειάζεστε όταν **δημιουργείτε ένα κενό έγγραφο Word**. Ο `builder` θα χρησιμοποιηθεί αργότερα για την εισαγωγή της ομάδας σχημάτων στην τρέχουσα θέση του κέρσορα.

## Ορισμός μεγέθους σχήματος και δημιουργία GroupShape

Ένα `GroupShape` λειτουργεί ως κοντέινερ που μπορεί να περιέχει πολλαπλά μεμονωμένα σχήματα. Πρώτα, ορίστε τις συνολικές διαστάσεις του κοντέινερ.

```csharp
// Create a GroupShape that will hold multiple shapes.
// Width = 300 points, Height = 200 points.
GroupShape groupShape = new GroupShape(document, 300, 200);

// Position the group on the page: 100 points from the left, 100 points from the top.
groupShape.Left = 100;
groupShape.Top  = 100;
```

Εδώ **ορίζουμε το μέγεθος του σχήματος** για το ίδιο το group (300 × 200). Τα ίδια ονόματα ιδιοτήτων (`Width`, `Height`) χρησιμοποιούνται για κάθε παιδικό σχήμα, δίνοντάς σας ακριβή έλεγχο σε κάθε στοιχείο.

## Προσθήκη του πρώτου ορθογωνίου και ορισμός χρώματος σχήματος

Τώρα προσθέστε ένα ορθογώνιο στο group και δώστε του χρώμα φόντου.

```csharp
// First rectangle – light blue background.
Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 0,          // Position relative to the group’s left edge.
    Top = 0,           // Position relative to the group’s top edge.
    FillColor = Color.LightBlue
};

// Append the rectangle to the group.
groupShape.AppendChild(rectangle1);
```

Η ιδιότητα `FillColor` **ορίζει το χρώμα του σχήματος**. Η χρήση του `System.Drawing.Color` σας επιτρέπει να επιλέξετε οποιαδήποτε προ‑ορισμένη ή προσαρμοσμένη τιμή ARGB.

## Προσθήκη δεύτερου ορθογωνίου, ορισμός μεγέθους, θέσης και χρώματος

Ένα δεύτερο ορθογώνιο δείχνει πώς να **ορίζετε τη θέση του σχήματος** σε σχέση με το group και πώς να αλλάζετε το χρώμα του.

```csharp
// Second rectangle – light coral background.
Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 150,               // 150 points to the right of the group’s left edge.
    Top = 0,                  // Same vertical alignment as the first rectangle.
    FillColor = Color.LightCoral
};

groupShape.AppendChild(rectangle2);
```

Επειδή το πλάτος του group είναι 300 points, τα δύο ορθογώνια των 120 points ταιριάζουν άνετα με ένα κενό 30 points. Προσαρμόστε τις τιμές `Left` και `Top` αν χρειάζεστε διαφορετική διάταξη.

## Εισαγωγή του GroupShape στο έγγραφο

Με το group πλήρως διαμορφωμένο, τοποθετήστε το στην τρέχουσα θέση του κέρσορα.

```csharp
// Insert the completed group shape at the builder’s current location.
builder.InsertNode(groupShape);
```

Η `InsertNode` γράφει το σχήμα απευθείας στο σώμα του εγγράφου, διατηρώντας την ακριβή **θέση σχήματος** που ορίσατε προηγουμένως.

## Αποθήκευση του αρχείου .docx

Το τελευταίο βήμα είναι η αποθήκευση του εγγράφου στο δίσκο. Αυτό δείχνει τη λειτουργία **αποθήκευσης αρχείου .docx**.

```csharp
// Define the output path (ensure the directory exists).
string outputPath = @"C:\Temp\GroupShape.docx";

// Save the document in DOCX format.
document.Save(outputPath);
```

Αφού τρέξετε το πρόγραμμα, ανοίξτε το `GroupShape.docx` στο Microsoft Word. Θα πρέπει να δείτε μια κενή σελίδα με ένα ομαδοποιημένο σχήμα που περιέχει δύο χρωματιστά ορθογώνια τοποθετημένα πλάι‑πλάι.

### Αναμενόμενο αποτέλεσμα

- Ένα μονοσέλιδο αρχείο `.docx`.
- Η σελίδα περιέχει ένα group shape τοποθετημένο 100 pts από τα αριστερά και τα πάνω περιθώρια.
- Μέσα στο group, ένα ανοιχτό‑μπλε ορθογώνιο βρίσκεται στα αριστερά, και ένα ανοιχτό‑κοραλί σχήμα στα δεξιά, καθένα 120 × 80 pts.

## Πλήρες, εκτελέσιμο παράδειγμα

Παρακάτω είναι το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε‑επικολλήσετε σε μια εφαρμογή console. Δεν απαιτούνται επιπλέον αρχεία.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Define a GroupShape and set its size and position.
        GroupShape groupShape = new GroupShape(document, 300, 200)
        {
            Left = 100,
            Top = 100
        };

        // 3️⃣ First rectangle – set size, position, and color.
        Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 0,
            Top = 0,
            FillColor = Color.LightBlue
        };
        groupShape.AppendChild(rectangle1);

        // 4️⃣ Second rectangle – set size, position, and color.
        Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 150,
            Top = 0,
            FillColor = Color.LightCoral
        };
        groupShape.AppendChild(rectangle2);

        // 5️⃣ Insert the grouped shape into the document.
        builder.InsertNode(groupShape);

        // 6️⃣ Save the docx file.
        string outputPath = @"C:\Temp\GroupShape.docx";
        document.Save(outputPath);

        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Η εκτέλεση αυτού του προγράμματος δημιουργεί το ακριβές έγγραφο που περιγράφηκε παραπάνω, εκπληρώνοντας και τις τέσσερις στόχους: **δημιουργία κενών εγγράφων Word**, **ορισμός μεγέθους σχήματος**, **ορισμός θέσης σχήματος**, **ορισμός χρώματος σχήματος**, και **αποθήκευση αρχείου .docx**.

## Συνηθισμένες παραλλαγές και ειδικές περιπτώσεις

| Σενάριο | Τι να αλλάξετε | Γιατί είναι σημαντικό |
|----------|----------------|------------------------|
| **Διαφορετικοί τύποι σχημάτων** | Αντικαταστήστε `ShapeType.Rectangle` με `ShapeType.Ellipse`, `ShapeType.Triangle`, κ.λπ. | Σας επιτρέπει να δημιουργήσετε πιο σύνθετα γραφικά χωρίς εξωτερικές εικόνες. |
| **Δυναμικές διαστάσεις** | Υπολογίστε `Width` και `Height` από είσοδο χρήστη ή αρχεία ρυθμίσεων. | Κάνει τη λύση επαναχρησιμοποιήσιμη σε πολλαπλά πρότυπα εγγράφων. |
| **Αποθήκευση ως PDF** | Καλέστε `document.Save("output.pdf", SaveFormat.Pdf);` | Αν οι παραλήπτες χρειάζονται μη επεξεργάσιμο format, το PDF είναι ασφαλής επιλογή. |
| **Προσθήκη κειμένου μέσα σε σχήμα** | Δημιουργήστε σχήμα `TextBox` και ορίστε `TextBox.Text`. | Χρήσιμο για δημιουργία ετικετών ή callout. |
| **Πολλαπλές ομάδες σε μία σελίδα** | Επαναλάβετε τα βήματα 2‑5 με διαφορετικές τιμές `Left`/`Top`. | Σας επιτρέπει να χτίσετε dashboards ή πολυ‑τμηματικές διατάξεις. |

### Pro tip

Όταν χρειάζεται ακριβής στοίχιση σχημάτων, χρησιμοποιήστε την ιδιότητα `ShapeBase.WrapType = WrapType.Inline` πριν την εισαγωγή του group. Αυτό αναγκάζει το group να συμπεριφέρεται όπως μια παράγραφος, αποτρέποντας ανεπιθύμητη ροή κειμένου γύρω του.

## Συμπέρασμα

Τώρα ξέρετε πώς να **δημιουργήσετε ένα κενό έγγραφο Word** με το Aspose.Words, **να ορίσετε το μέγεθος σχήματος**, **να ορίσετε τη θέση σχήματος**, **να ορίσετε το χρώμα σχήματος**, και **να αποθηκεύσετε το αρχείο .docx**. Το πλήρες παράδειγμα δείχνει ένα καθαρό, επαναχρησιμοποιήσιμο μοτίβο για την προσθήκη ομαδοποιημένων γραφικών σε οποιοδήποτε έργο αυτοματοποίησης Word.

Από εδώ μπορείτε να εξερευνήσετε:

- Προσθήκη περισσότερων σχημάτων ή εικόνων στο ίδιο `GroupShape` (**ορισμός μεγέθους σχήματος**, **ορισμός χρώματος σχήματος** παραλλαγές).
- Χρήση του `ShapeBase.Rotation` για περιστροφή ορθογωνίων για διακοσμητικά εφέ.
- Εξαγωγή του ίδιου εγγράφου ως PDF ή HTML για ευρύτερη διανομή (**εναλλακτική αποθήκευση .docx**).

Μην διστάσετε να πειραματιστείτε με διαφορετικά χρώματα, μεγέθη και λογική διάταξης ώστε να ταιριάζουν στις συγκεκριμένες ανάγκες αναφοράς ή προτύπων σας. Καλή κωδικοποίηση!

## Τι πρέπει να μάθετε στη συνέχεια;

Οι παρακάτω οδηγίες καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στην υλοποίηση των δικών σας έργων.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}