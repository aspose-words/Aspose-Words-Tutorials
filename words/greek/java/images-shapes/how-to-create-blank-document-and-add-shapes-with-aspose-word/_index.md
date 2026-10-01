---
category: general
date: 2026-09-30
description: Δημιουργήστε ένα κενό έγγραφο και εισάγετε σχήμα ορθογωνίου, έλλειψη
  και ομαδοποιήστε πολλαπλά σχήματα σε C# χρησιμοποιώντας το Aspose.Words. Μάθετε
  πώς να εισάγετε σχήματα και πώς να δημιουργήσετε ομάδα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- insert rectangle shape
- group multiple shapes
- how to insert shapes
- how to create group
language: el
lastmod: 2026-09-30
og_description: Δημιουργήστε κενό έγγραφο σε C# και μάθετε πώς να εισάγετε σχήματα
  και να ομαδοποιείτε πολλαπλά σχήματα με το Aspose.Words. Ακολουθήστε το βήμα‑βήμα
  οδηγό.
og_image_alt: Screenshot of a C# program that creates a blank document, inserts a
  rectangle and ellipse, and groups them together.
og_title: Δημιουργία κενού εγγράφου και ομαδοποίηση σχημάτων σε C# – Οδηγός Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Create blank document and insert rectangle shape, ellipse, and group
    multiple shapes in C# using Aspose.Words. Learn how to insert shapes and how to
    create group.
  headline: How to create blank document and add shapes with Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- document automation
- shapes
title: Πώς να δημιουργήσετε κενό έγγραφο και να προσθέσετε σχήματα με το Aspose.Words
  σε C#
url: /el/java/images-shapes/how-to-create-blank-document-and-add-shapes-with-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε κενό έγγραφο και να προσθέσετε σχήματα με το Aspose.Words σε C#

Αν χρειάζεστε **να δημιουργήσετε κενό έγγραφο** και να το γεμίσετε με γραφικά, αυτός ο οδηγός σας δείχνει ακριβώς πώς. Θα δείτε πώς να **εισάγετε σχήμα ορθογωνίου**, να προσθέσετε άλλα αντικείμενα σχεδίασης και, στη συνέχεια, **ομαδοποιήσετε πολλαπλά σχήματα** ώστε να λειτουργούν ως μία ενιαία μονάδα.

Η εργασία με σχήματα είναι μια συχνή απαίτηση κατά τη δημιουργία συμβάσεων, πιστοποιητικών ή προσαρμοσμένων αναφορών. Σε αυτό το tutorial θα μάθετε τη πλήρη ροή εργασίας, από την αρχικοποίηση του εγγράφου μέχρι την αποθήκευση του τελικού αρχείου, χρησιμοποιώντας το Aspose.Words API για .NET.

## Προαπαιτούμενα

* .NET 6.0 (ή νεότερο) SDK εγκατεστημένο  
* Ένα έγκυρο άδεια Aspose.Words για .NET (η δωρεάν δοκιμή λειτουργεί για αυτό το παράδειγμα)  
* Ένα IDE όπως το Visual Studio 2022 ή το Visual Studio Code  

Δεν απαιτούνται επιπλέον πακέτα NuGet πέρα από το `Aspose.Words`.

## Πώς να δημιουργήσετε κενό έγγραφο και να εργαστείτε με σχήματα

Το πρώτο βήμα είναι η δημιουργία ενός αντικειμένου `Document`. Αυτό το αντικείμενο αντιπροσωπεύει το Word αρχείο στη μνήμη και σας δίνει πρόσβαση στο `DocumentBuilder`, το κύριο εργαλείο για την εισαγωγή περιεχομένου.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Γιατί είναι σημαντικό:** Ένα κενό έγγραφο σας παρέχει έναν καθαρό καμβά. Το `DocumentBuilder` διατηρεί το τρέχον σημείο εισαγωγής, έτσι κάθε σχήμα που προσθέτετε τοποθετείται αυτόματα στη σωστή σελίδα.

## Εισαγωγή σχήματος ορθογωνίου και άλλων σχημάτων

Στη συνέχεια, προσθέτουμε ένα ορθογώνιο και μια έλλειψη. Και οι δύο κλήσεις χρησιμοποιούν την ίδια μέθοδο `InsertShape`, η οποία είναι ο προτεινόμενος τρόπος **πώς να εισάγετε σχήματα** στο Aspose.Words.

```csharp
        // Step 2: Insert a rectangle shape (100 × 50 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;   // optional styling
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Insert an ellipse shape (80 × 80 points)
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;
```

*Η μέθοδος `InsertShape` τοποθετεί αυτόματα το σχήμα στην τρέχουσα θέση του κέρσορα.* Εάν χρειάζεστε ακριβή τοποθέτηση, μπορείτε να προσαρμόσετε τα `Shape.Left` και `Shape.Top` μετά την εισαγωγή.

## Ομαδοποίηση πολλαπλών σχημάτων σε ένα ενιαίο αντικείμενο

Τώρα συνδυάζουμε το ορθογώνιο και την έλλειψη σε μία λογική οντότητα. Η ομαδοποίηση είναι χρήσιμη όταν θέλετε να μετακινήσετε ή να αλλάξετε το μέγεθος πολλών σχημάτων μαζί.

```csharp
        // Step 4: Create a group shape that will hold multiple shapes
        GroupShape groupShape = builder.InsertGroupShape();

        // Step 5: Add the rectangle and ellipse to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional: Apply a border to the whole group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;
```

**Πώς λειτουργεί:** Η `InsertGroupShape` δημιουργεί ένα κοντέινερ που συμπεριφέρεται όπως οποιοδήποτε άλλο `Shape`. Καλώντας την `AppendChild`, μετακινείτε τα υπάρχοντα σχήματα στο κοντέινερ, το οποίο ενημερώνει αυτόματα τις σχετικές τους συντεταγμένες.

### Πρακτική συμβουλή

Εάν αργότερα χρειαστείτε **πώς να δημιουργήσετε ομάδα** προγραμματιστικά για περισσότερα από δύο σχήματα, απλώς επαναλάβετε την `AppendChild` για κάθε επιπλέον αντικείμενο `Shape`. Η ομάδα μπορεί να περιέχει οποιονδήποτε αριθμό αντικειμένων σχεδίασης, συμπεριλαμβανομένων εικόνων, πλαισίων κειμένου ή ακόμη και άλλων ομάδων.

## Πλήρες παράδειγμα – πώς να εισάγετε σχήματα και να αποθηκεύσετε το έγγραφο

Παρακάτω βρίσκεται το πλήρες, εκτελέσιμο πρόγραμμα που δείχνει κάθε βήμα που συζητήθηκε μέχρι τώρα. Η εκτέλεση του κώδικα παράγει ένα αρχείο `ShapesDemo.docx` που περιέχει ένα ορθογώνιο, μια έλλειψη και ένα ομαδοποιημένο σχήμα.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Insert rectangle shape
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // 3. Insert ellipse shape
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;

        // 4. Create a group shape
        GroupShape groupShape = builder.InsertGroupShape();

        // 5. Add shapes to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional styling for the group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;

        // 6. Save the document
        string outputPath = "ShapesDemo.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Αναμενόμενο αποτέλεσμα:** Το άνοιγμα του `ShapesDemo.docx` στο Microsoft Word εμφανίζει μία σελίδα με ένα μπλε ορθογώνιο, μια πράσινη έλλειψη και ένα περιβάλλον γκρι περίγραμμα που αντιπροσωπεύει την ομάδα. Η μετακίνηση της ομάδας μετακινεί και τα δύο σχήματα μαζί, επιβεβαιώνοντας ότι η λειτουργία **ομαδοποίησης πολλαπλών σχημάτων** πέτυχε.

## Συχνές ερωτήσεις και αντιμετώπιση ειδικών περιπτώσεων

| Ερώτηση | Απάντηση |
|----------|--------|
| *Τι γίνεται αν χρειάζομαι τα σχήματα σε συγκεκριμένη σελίδα;* | Κλήση `builder.MoveToDocumentEnd();` πριν την εισαγωγή των σχημάτων, ή χρήση `builder.MoveToSection(sectionIndex);` για στόχευση συγκεκριμένου τμήματος. |
| *Μπορώ να προσθέσω κείμενο μέσα σε ομαδοποιημένο σχήμα;* | Ναι. Δημιουργήστε ένα `Shape` τύπου `ShapeType.TextBox`, διαμορφώστε το κείμενό του και στη συνέχεια `AppendChild` στο `GroupShape`. |
| *Χρησιμοποιούν οι διαστάσεις των σχημάτων μονάδες point ή pixel;* | Το Aspose.Words χρησιμοποιεί **points** (1 pt = 1/72 inch). Αυτό εξασφαλίζει συνεπή μέγεθος σε εκτυπωτές και οθόνες. |
| *Πώς να αλλάξετε την περιστροφή της ομάδας;* | Ορίστε `groupShape.RotationAngle = 45;` (μοίρες). Όλα τα παιδικά σχήματα περιστρέφονται γύρω από το σημείο προέλευσης της ομάδας. |

## Συμπέρασμα

Τώρα γνωρίζετε πώς να **δημιουργήσετε κενό έγγραφο**, **εισάγετε σχήμα ορθογωνίου**, **πώς να εισάγετε σχήματα** όπως έλλειψεις, και **ομαδοποιήσετε πολλαπλά σχήματα** σε ένα ενιαίο αντικείμενο χρησιμοποιώντας το Aspose.Words για .NET. Το πλήρες παράδειγμα κώδικα δείχνει την προτεινόμενη προσέγγιση, και οι παραπάνω συμβουλές σας βοηθούν να προσαρμόσετε τη λύση σε πιο σύνθετα σενάρια όπως η προσθήκη πλαισίων κειμένου ή η περιστροφή ομάδων.

Έτοιμοι να εξερευνήσετε περισσότερα; Δοκιμάστε να προσθέσετε ένα σχήμα εικόνας στην ομάδα, πειραματιστείτε με διαφορετικά χρώματα γεμίσματος ή δημιουργήστε μια αναφορά πολλαπλών σελίδων όπου κάθε σελίδα περιέχει το δικό της ομαδοποιημένο διάγραμμα. Οι ίδιες αρχές ισχύουν, ώστε να μπορείτε να κλιμακώσετε αυτό το μοτίβο σε οποιοδήποτε έργο αυτοματοποίησης εγγράφων.

## Τι θα πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Δημιουργία Group Shape σε έγγραφο Word χρησιμοποιώντας Aspose.Words για .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Εισαγωγή σχημάτων σε έγγραφα Word χρησιμοποιώντας Aspose.Words για .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Δημιουργία κενού εγγράφου Word με Aspose.Words – Οδηγός βήμα‑βήμα](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}