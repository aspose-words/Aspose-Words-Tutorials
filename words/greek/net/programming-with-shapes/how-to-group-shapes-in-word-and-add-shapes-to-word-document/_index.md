---
category: general
date: 2026-08-07
description: Πώς να ομαδοποιήσετε σχήματα στο Word με το Aspose.Words και να προσθέσετε
  σχήματα σε έγγραφο Word χρησιμοποιώντας C#. Ακολουθήστε αυτόν τον οδηγό βήμα‑βήμα
  για καθαρό, επαναχρησιμοποιήσιμο κώδικα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes in word
- add shapes to word document
language: el
lastmod: 2026-08-07
og_description: Πώς να ομαδοποιήσετε σχήματα στο Word χρησιμοποιώντας το Aspose.Words
  για .NET. Αυτό το σεμινάριο σας δείχνει πώς να προσθέσετε σχήματα σε ένα έγγραφο
  Word, να τα ομαδοποιήσετε και να αποθηκεύσετε το αρχείο με σαφή κώδικα C#.
og_image_alt: Screenshot of a rectangle and ellipse grouped in a Word document created
  with Aspose.Words
og_title: Πώς να ομαδοποιήσετε σχήματα στο Word – γρήγορος οδηγός C#
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to group shapes in Word with Aspose.Words and add shapes to Word
    document using C#. Follow this step‑by‑step guide for clean, reusable code.
  headline: How to group shapes in Word and add shapes to Word document
  type: TechArticle
- description: How to group shapes in Word with Aspose.Words and add shapes to Word
    document using C#. Follow this step‑by‑step guide for clean, reusable code.
  name: How to group shapes in Word and add shapes to Word document
  steps:
  - name: Create a document and a builder
    text: A `Document` object represents the entire DOCX file. `DocumentBuilder` provides
      a convenient API for editing the document.
  - name: Add the rectangle shape
    text: A rectangle is created by specifying `ShapeType.Rectangle`. Width, height,
      and location are set in points (1 pt ≈ 1/72 in).
  - name: Add the ellipse shape
    text: The ellipse uses `ShapeType.Ellipse`. Its size and position are independent
      of the rectangle, which allows you to control the final layout of the group.
  - name: Group the two shapes
    text: '`GroupShape` acts as a container that treats its children as a single object.
      This is the essential operation for **how to group shapes in Word**.'
  - name: Insert the grouped shape into the document
    text: '`DocumentBuilder.InsertNode` places the `GroupShape` at the current cursor
      location. Because we have not moved the builder, the group appears at the start
      of the first page.'
  - name: Save the document
    text: Finally, write the DOCX file to disk. Use a full path that your application
      can write to.
  - name: Expected output
    text: Open `GroupShape.docx`. You will see a single visual object that contains
      a blue rectangle on the left and a green ellipse on the right. Selecting the
      object in Word highlights both shapes simultaneously—proof that **how to group
      shapes in Word** succeeded.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Πώς να ομαδοποιήσετε σχήματα στο Word και να προσθέσετε σχήματα σε έγγραφο
  Word
url: /el/net/programming-with-shapes/how-to-group-shapes-in-word-and-add-shapes-to-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να ομαδοποιήσετε σχήματα στο Word και να προσθέσετε σχήματα σε έγγραφο Word

Αν χρειάζεστε **how to group shapes in Word**, αυτός ο οδηγός σας καθοδηγεί μέσα από τη διαδικασία χρησιμοποιώντας το Aspose.Words for .NET. Θα μάθετε επίσης **add shapes to Word document** με μερικές γραμμές κώδικα C#, ώστε το αποτέλεσμα να είναι έτοιμο για οποιοδήποτε σενάριο αναφοράς ή δημιουργίας προτύπων.

Το tutorial καλύπτει όλα όσα χρειάζεστε: τα απαιτούμενα πακέτα NuGet, ένα πλήρες αρχείο πηγαίου κώδικα και μια εξήγηση του γιατί κάθε βήμα είναι σημαντικό. Στο τέλος θα μπορείτε να δημιουργήσετε ένα DOCX που περιέχει ένα ορθογώνιο και μια έλλειψη συνδυασμένα σε ένα ενιαίο group shape.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* .NET 6.0 SDK ή νεότερη έκδοση εγκατεστημένη  
* Visual Studio 2022 (ή οποιοδήποτε IDE που υποστηρίζει .NET)  
* Πακέτο NuGet Aspose.Words for .NET (`Aspose.Words`) – η δωρεάν δοκιμή λειτουργεί για δοκιμές, αλλά μια άδεια αφαιρεί τα υδατογραφήματα αξιολόγησης  

Αυτά τα στοιχεία είναι οι μόνες εξωτερικές εξαρτήσεις για **add shapes to Word document**.

## Πώς να ομαδοποιήσετε σχήματα στο Word

Ο πυρήνας της λύσης είναι η δημιουργία μεμονωμένων σχημάτων, η τοποθέτησή τους στη σελίδα και, στη συνέχεια, η συσπείρωση τους σε ένα `GroupShape`. Τα παρακάτω βήματα αντικατοπτρίζουν τη λογική σειρά του κώδικα.

### Βήμα 1: Δημιουργία εγγράφου και builder

Ένα αντικείμενο `Document` αντιπροσωπεύει ολόκληρο το αρχείο DOCX. Το `DocumentBuilder` παρέχει ένα βολικό API για την επεξεργασία του εγγράφου.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create an empty Word document
Document doc = new Document();

// DocumentBuilder lets you insert nodes, text, and shapes
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Γιατί είναι σημαντικό*: Το `Document` είναι το δοχείο για όλα τα στοιχεία του Word. Το `DocumentBuilder` παρακολουθεί τη θέση του τρέχοντος κέρσορα, κάτι που απαιτείται όταν αργότερα εισάγετε το ομαδοποιημένο σχήμα.

### Βήμα 2: Προσθήκη του σχήματος ορθογωνίου

Ένα ορθογώνιο δημιουργείται με την καθορισμένη τιμή `ShapeType.Rectangle`. Το πλάτος, το ύψος και η θέση ορίζονται σε μονάδες σημείου (1 pt ≈ 1/72 in).

```csharp
Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
rectangleShape.Width = 100;               // 100 pt wide
rectangleShape.Height = 50;               // 50 pt tall
rectangleShape.Left = 0;                  // X‑coordinate
rectangleShape.Top = 0;                   // Y‑coordinate
rectangleShape.StrokeColor = Color.Blue; // Outline color
```

*Γιατί είναι σημαντικό*: Ο ορισμός του `StrokeColor` κάνει το σχήμα ορατό όταν ανοίγει το έγγραφο. Μπορείτε επίσης να γεμίσετε το σχήμα με `FillColor` εάν απαιτείται στερεό εσωτερικό.

### Βήμα 3: Προσθήκη του σχήματος έλλειψης

Η έλλειψη χρησιμοποιεί `ShapeType.Ellipse`. Το μέγεθος και η θέση της είναι ανεξάρτητα από το ορθογώνιο, επιτρέποντάς σας να ελέγξετε τη τελική διάταξη της ομάδας.

```csharp
Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
ellipseShape.Width = 80;
ellipseShape.Height = 80;
ellipseShape.Left = 120;                  // Placed to the right of the rectangle
ellipseShape.Top = 0;
ellipseShape.StrokeColor = Color.Green;
```

*Γιατί είναι σημαντικό*: Τοποθετώντας την έλλειψη στο `Left = 120`, δεν επικαλύπτεται με το ορθογώνιο, καθιστώντας την ομάδα οπτικά διακριτή.

### Βήμα 4: Ομαδοποίηση των δύο σχημάτων

Το `GroupShape` λειτουργεί ως δοχείο που αντιμετωπίζει τα παιδιά του ως ένα ενιαίο αντικείμενο. Αυτή είναι η βασική ενέργεια για **how to group shapes in Word**.

```csharp
GroupShape groupShape = new GroupShape(doc);
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);
```

*Γιατί είναι σημαντικό*: Η ομαδοποίηση σας επιτρέπει να μετακινήσετε, να αλλάξετε μέγεθος ή να περιστρέψετε και τα δύο σχήματα μαζί. Οποιαδήποτε μετασχηματισμός εφαρμοστεί στο `groupShape` μεταδίδεται στα παιδιά του.

### Βήμα 5: Εισαγωγή του ομαδοποιημένου σχήματος στο έγγραφο

Το `DocumentBuilder.InsertNode` τοποθετεί το `GroupShape` στη τρέχουσα θέση του κέρσορα. Επειδή δεν μετακινήσαμε το builder, η ομάδα εμφανίζεται στην αρχή της πρώτης σελίδας.

```csharp
builder.InsertNode(groupShape);
```

*Γιατί είναι σημαντικό*: Η άμεση εισαγωγή του κόμβου αποφεύγει την ανάγκη για ξεχωριστή παράγραφο ή κελί πίνακα. Η ομάδα γίνεται μέρος της ροής του εγγράφου.

### Βήμα 6: Αποθήκευση του εγγράφου

Τέλος, γράψτε το αρχείο DOCX στο δίσκο. Χρησιμοποιήστε πλήρη διαδρομή στην οποία η εφαρμογή σας μπορεί να γράψει.

```csharp
doc.Save(@"C:\Temp\GroupShape.docx");
```

*Γιατί είναι σημαντικό*: Η `doc.Save` ολοκληρώνει όλες τις αλλαγές. Το παραγόμενο αρχείο μπορεί να ανοιχθεί στο Microsoft Word, LibreOffice ή οποιονδήποτε προβολέα που υποστηρίζει DOCX.

## Πλήρες αρχείο πηγαίου κώδικα

Αντιγράψτε τον κώδικα παρακάτω σε ένα νέο έργο κονσόλας (`dotnet new console`) και εκτελέστε το. Το πρόγραμμα δημιουργεί ένα αρχείο με όνομα `GroupShape.docx` που περιέχει ένα ομαδοποιημένο ορθογώνιο και μια έλλειψη.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordShapeGrouping
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new document and a builder to edit it
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Define a rectangle shape
            Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
            rectangleShape.Width = 100;
            rectangleShape.Height = 50;
            rectangleShape.Left = 0;
            rectangleShape.Top = 0;
            rectangleShape.StrokeColor = Color.Blue;

            // Step 3: Define an ellipse shape
            Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
            ellipseShape.Width = 80;
            ellipseShape.Height = 80;
            ellipseShape.Left = 120;
            ellipseShape.Top = 0;
            ellipseShape.StrokeColor = Color.Green;

            // Step 4: Group the two shapes together
            GroupShape groupShape = new GroupShape(doc);
            groupShape.AppendChild(rectangleShape);
            groupShape.AppendChild(ellipseShape);

            // Step 5: Insert the grouped shape into the document
            builder.InsertNode(groupShape);

            // Step 6: Save the document
            doc.Save(@"C:\Temp\GroupShape.docx");
        }
    }
}
```

### Αναμενόμενο αποτέλεσμα

Ανοίξτε το `GroupShape.docx`. Θα δείτε ένα ενιαίο οπτικό αντικείμενο που περιέχει ένα μπλε ορθογώνιο στα αριστερά και μια πράσινη έλλειψη στα δεξιά. Επιλέγοντας το αντικείμενο στο Word επισημαίνονται και τα δύο σχήματα ταυτόχρονα — απόδειξη ότι **how to group shapes in Word** ολοκληρώθηκε με επιτυχία.

## Συχνές ερωτήσεις και ειδικές περιπτώσεις

* **Μπορώ να προσθέσω περισσότερα από δύο σχήματα;**  
  Ναι. Καλέστε `groupShape.AppendChild` για κάθε επιπλέον `Shape` πριν εισάγετε την ομάδα.

* **Τι γίνεται αν χρειαστεί να περιστρέψω την ομάδα;**  
  Ορίστε `groupShape.RotationAngle = 45;` (γωνία σε μοίρες) μετά τη δημιουργία της ομάδας.

* **Πρέπει να καλέσω τη `doc.UpdatePageLayout()`;**  
  Όχι για αυτό το σενάριο. Η διάταξη ενημερώνεται αυτόματα όταν αποθηκευτεί το έγγραφο.

* **Πώς η άδεια χρήσης επηρεάζει τον κώδικα;**  
  Με μια έγκυρη άδεια Aspose.Words (`License license = new License(); license.SetLicense("Aspose.Words.lic");`) το παραγόμενο έγγραφο δεν περιέχει υδατογράφημα αξιολόγησης.

## Συμπέρασμα

Τώρα γνωρίζετε **how to group shapes in Word** και **add shapes to Word document** χρησιμοποιώντας το Aspose.Words for .NET. Ο οδηγός κάλυψε τη δημιουργία εγγράφου, τον ορισμό μεμονωμένων σχημάτων, την ομαδοποίησή τους, την εισαγωγή της ομάδας και την αποθήκευση του αρχείου.  

Από εδώ μπορείτε να πειραματιστείτε με:

* Προσθήκη πλαισίων κειμένου ή εικόνων στην ομάδα  
* Αλλαγή χρωμάτων γεμίσματος, στυλ γραμμής ή εφέ σκιάς  
* Ομαδοποίηση σχημάτων μέσα σε πίνακες ή κεφαλίδες  

Αυτές οι επεκτάσεις σας επιτρέπουν να δημιουργήσετε σύνθετα πρότυπα Word προγραμματιστικά, διατηρώντας τον κώδικα καθαρό και συντηρήσιμο. Καλή προγραμματιστική!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Word Document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}