---
category: general
date: 2026-09-14
description: Μάθετε πώς να κρύβετε σχήμα στο Word χρησιμοποιώντας C#—συμπεριλαμβανομένου
  του κώδικα δημιουργίας εγγράφου Word, εισαγωγής σχήματος ορθογωνίου στο Word και
  κρυψίματος του σχήματος στο Word προγραμματιστικά.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape
- hide shape in word
- create word document code
- insert rectangle shape word
language: el
lastmod: 2026-09-14
og_description: Πώς να κρύψετε ένα σχήμα στο Word χρησιμοποιώντας C# — βήμα‑βήμα οδηγός
  που δείχνει επίσης πώς να δημιουργήσετε κώδικα εγγράφου Word και να εισάγετε σχήμα
  ορθογωνίου στο Word.
og_image_alt: Word document preview with a visible rectangle shape and a hidden ellipse
  shape
og_title: Πώς να κρύψετε σχήμα σε ένα έγγραφο Word με κώδικα C#
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Learn how to hide shape in Word using C#—including create word document
    code, insert rectangle shape word, and hide shape in word programmatically.
  headline: How to hide shape in a Word document with C# code
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Πώς να κρύψετε σχήμα σε έγγραφο Word με κώδικα C#
url: /el/net/programming-with-shapes/how-to-hide-shape-in-a-word-document-with-c-code/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να κρύψετε σχήμα σε έγγραφο Word με κώδικα C#

Αν χρειάζεστε **πώς να κρύψετε σχήμα** σε αρχείο Word, αυτό το tutorial παρουσιάζει τη πλήρη λύση. Θα δείτε πώς να δημιουργήσετε ένα έγγραφο Word, να εισάγετε ένα σχήμα ορθογωνίου, να προσθέσετε μια έλλειψη και να κρύψετε αυτήν την έλλειψη ώστε να εμφανίζεται μόνο το ορθογώνιο όταν ανοίξει το αρχείο.

Ο οδηγός καλύπτει όλα όσα χρειάζεστε — χωρίς εξωτερικές αναφορές, μόνο ο κώδικας και οι εξηγήσεις. Στο τέλος θα μπορείτε να ενσωματώσετε κρυφά γραφικά σε οποιοδήποτε έγγραφο Word δημιουργείτε προγραμματιστικά.

## Προαπαιτούμενα

- .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.7+)
- Aspose.Words for .NET (δωρεάν δοκιμή ή έκδοση με άδεια)  
  Εγκαταστήστε το μέσω NuGet: `dotnet add package Aspose.Words`
- Βασική εξοικείωση με C# και Visual Studio ή οποιοδήποτε IDE προτιμάτε

## Βήμα 1: Ρύθμιση του έργου και εισαγωγή namespaces

Δημιουργήστε μια νέα εφαρμογή console και προσθέστε τις απαιτούμενες δηλώσεις `using`. Αυτές οι εισαγωγές σας δίνουν πρόσβαση στις κλάσεις `Document`, `DocumentBuilder` και σχεδίασης που χρειάζονται για τη διαχείριση σχημάτων.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The rest of the code follows in the next steps
        }
    }
}
```

**Γιατί είναι σημαντικό** – Η εισαγωγή των σωστών namespaces αποτρέπει σφάλματα μεταγλώττισης και καθιστά διαθέσιμη τη διεπαφή API για τη δημιουργία σχήματος και τον έλεγχο ορατότητας.

## Βήμα 2: Δημιουργία νέου εγγράφου Word και builder

Ένα `Document` αντιπροσωπεύει το αρχείο, ενώ ένα `DocumentBuilder` παρέχει μια ευέλικτη API για την προσθήκη περιεχομένου. Εδώ εφαρμόζετε την λογική **πώς να κρύψετε σχήμα**: χρειάζεστε ένα πλαίσιο εγγράφου πριν μπορέσει να υπάρξει οποιοδήποτε σχήμα.

```csharp
// Step 2: Create a new blank document and a builder to edit it
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);
```

**Εξήγηση** – Το αντικείμενο `Document` ξεκινά κενό. Ο `DocumentBuilder` τοποθετείται στην αρχή της πρώτης παραγράφου, έτοιμος να εισάγει σχήματα ή κείμενο.

## Βήμα 3: Εισαγωγή ορατού σχήματος ορθογωνίου

Το ορθογώνιο θα είναι το σχήμα που παραμένει ορατό όταν ανοίξει το έγγραφο. Μπορείτε να ελέγξετε το μέγεθος, τη θέση και τη μορφοποίηση απευθείας μέσω του αντικειμένου σχήματος.

```csharp
// Step 3: Insert a visible rectangle shape and position it
Shape visibleRectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
visibleRectangle.Left = 50;                 // 50 points from the left margin
visibleRectangle.Top = 100;                 // 100 points from the top of the page
visibleRectangle.FillColor = System.Drawing.Color.LightBlue;
visibleRectangle.LineColor = System.Drawing.Color.DarkBlue;
```

**Γιατί αυτό το βήμα** – Η προσθήκη ενός ορθογωνίου επιδεικνύει την απαίτηση **insert rectangle shape word**. Ο καθορισμός του `FillColor` και του `LineColor` κάνει το σχήμα εύκολο να εντοπιστεί στο τελικό έγγραφο.

## Βήμα 4: Εισαγωγή σχήματος έλλειψης και απόκρυψή του

Τώρα προσθέτετε το σχήμα που θέλετε να κρύψετε. Η ιδιότητα `Hidden` λέει στο Word να μην αποδώσει το σχήμα στη διεπαφή, ενώ παραμένει μέρος της δομής του εγγράφου.

```csharp
// Step 4: Insert an ellipse shape, position it, and hide it from view
Shape hiddenEllipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
hiddenEllipse.Left = 200;      // Position away from the rectangle
hiddenEllipse.Top = 100;
hiddenEllipse.Hidden = true;   // This flag implements how to hide shape
```

**Εξήγηση** – Ο ορισμός `Hidden = true` είναι η καρδιά του **hide shape in word**. Το Word σέβεται αυτή τη σημαία κατά την κανονική προβολή και εκτύπωση, αλλά το σχήμα μπορεί ακόμη να προσπελαστεί προγραμματιστικά αν χρειαστεί.

## Βήμα 5: Αποθήκευση του εγγράφου

Τέλος, γράψτε το έγγραφο στο δίσκο. Επιλέξτε έναν φάκελο στον οποίο έχετε δικαίωμα εγγραφής και δώστε στο αρχείο ένα σαφές όνομα που να αντανακλά τον σκοπό του tutorial.

```csharp
// Step 5: Save the document with both shapes
string outputPath = @"C:\Temp\ShapeVisibility.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

**Αποτέλεσμα** – Το άνοιγμα του `ShapeVisibility.docx` στο Microsoft Word εμφανίζει μόνο το ανοιχτό‑μπλε ορθογώνιο. Η κρυφή έλλειψη δεν εμφανίζεται, επιβεβαιώνοντας ότι έχετε καταφέρει με επιτυχία το **πώς να κρύψετε σχήμα** σε αρχείο Word.

## Πλήρες λειτουργικό παράδειγμα

Συνδυάζοντας όλα τα αποσπάσματα παίρνετε ένα ενιαίο, εκτελέσιμο πρόγραμμα:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a new document and builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert a visible rectangle
            Shape visibleRectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            visibleRectangle.Left = 50;
            visibleRectangle.Top = 100;
            visibleRectangle.FillColor = System.Drawing.Color.LightBlue;
            visibleRectangle.LineColor = System.Drawing.Color.DarkBlue;

            // Insert a hidden ellipse
            Shape hiddenEllipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
            hiddenEllipse.Left = 200;
            hiddenEllipse.Top = 100;
            hiddenEllipse.Hidden = true; // hides the shape

            // Save the document
            string outputPath = @"C:\Temp\ShapeVisibility.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Αναμενόμενο αποτέλεσμα

- **Οπτικό**: Όταν ανοίξετε το `ShapeVisibility.docx`, βλέπετε ένα ανοιχτό‑μπλε ορθογώνιο τοποθετημένο κοντά στο αριστερό περιθώριο. Καμία έλλειψη δεν είναι ορατή.
- **Προγραμματιστικό**: Η κρυφή έλλειψη παραμένει στο XML του εγγράφου (`<w:drawing>` στοιχείο) με το χαρακτηριστικό `w:hidden` ορισμένο, το οποίο μπορείτε να επαληθεύσετε ανοίγοντας το αρχείο ως zip και εξετάζοντας το `document.xml`.

## Συχνές ερωτήσεις και ειδικές περιπτώσεις

| Ερώτηση | Απάντηση |
|----------|--------|
| *Μπορώ να κρύψω πολλαπλά σχήματα;* | Ναι. Ορίστε `Hidden = true` σε κάθε σχήμα που θέλετε να κρύψετε. |
| *Θα εκτυπώνονται τα κρυφά σχήματα;* | Από προεπιλογή το Word δεν εκτυπώνει κρυφά αντικείμενα. Αν χρειάζεστε εκτύπωση, αφαιρέστε τη σημαία `Hidden` πριν την εκτύπωση. |
| *Υποστηρίζεται η ιδιότητα hidden σε παλαιότερες εκδόσεις του Word;* | Η ιδιότητα `Hidden` είναι μέρος του προτύπου Office Open XML και λειτουργεί σε Word 2007 και νεότερα. |
| *Τι γίνεται αν χρειαστεί να αλλάζω την ορατότητα κατά την εκτέλεση;* | Ανακτήστε το σχήμα μέσω `document.GetChildNodes(NodeType.Shape, true)` και αλλάξτε την ιδιότητα `Hidden` βάσει της λογικής σας. |

## Pro tips

- **Απόδοση**: Αν δημιουργείτε πολλά έγγραφα, επαναχρησιμοποιήστε ένα ενιαίο αντικείμενο `DocumentBuilder` αντί να δημιουργείτε νέο για κάθε αρχείο.
- **Έλεγχος εκδόσεων**: Αποθηκεύετε τα παραγόμενα `.docx` σε φάκελο ελεγχόμενης έκδοσης· τα κρυφά σχήματα μπορούν να λειτουργήσουν ως μετα-δεδομένα για επεξεργασία downstream.
- **Δοκιμή**: Αυτοματοποιήστε μια γρήγορη οπτική δοκιμή μετατρέποντας το DOCX σε PDF με Aspose.Words (`document.Save("out.pdf")`). Το PDF θα κρύβει επίσης την έλλειψη, επιβεβαιώνοντας ότι η σημαία hidden μεταφέρεται στις μετατροπές μορφής.

## Συμπέρασμα

Τώρα ξέρετε **πώς να κρύψετε σχήμα** σε έγγραφο Word χρησιμοποιώντας C#. Το tutorial σας οδήγησε στη δημιουργία εγγράφου, **insert rectangle shape word**, προσθήκη έλλειψης και εφαρμογή της σημαίας `Hidden` για να επιτύχετε τη συμπεριφορά **hide shape in word**. Με τον πλήρη, εκτελέσιμο κώδικα μπορείτε να ενσωματώσετε κρυφά γραφικά σε οποιαδήποτε αυτοματοποιημένη ροή αναφορών ή προτύπων.

### Επόμενα βήματα

- Εξερευνήστε άλλες ιδιότητες σχήματος όπως περιστροφή, σκιά και περιτύλιξη κειμένου.  
- Συνδυάστε κρυφά σχήματα με προσαρμοσμένες ιδιότητες εγγράφου για ενσωμάτωση δεδομένων αναγνώσιμων από μηχανές.  
- Δείτε πρότυπα **create word document code** για πίνακες, διαγράμματα και ελέγχους περιεχομένου ώστε να επεκτείνετε το εργαλείο αυτοματοποίησής σας.

Πειραματιστείτε με διαφορετικούς τύπους σχήματος και ρυθμίσεις ορατότητας — το επόμενο έργο αυτοματοποίησης Word είναι μόλις μερικές γραμμές κώδικα μακριά!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στην υλοποίηση των δικών σας έργων.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}