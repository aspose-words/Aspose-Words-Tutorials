---
category: general
date: 2026-09-11
description: Μάθετε πώς να δημιουργήσετε έγγραφο Word, να προσθέσετε σχήμα ορθογωνίου
  και να ορίσετε τις διαστάσεις του σχήματος με το Aspose.Words. Οδηγός βήμα‑προς‑βήμα
  σε C# για ακριβή μέτρηση σχήματος.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- add rectangle shape
- set shape size
- create shapes in word
- set shape dimensions
language: el
lastmod: 2026-09-11
og_description: Δημιουργήστε έγγραφο Word με το Aspose.Words σε C#. Αυτός ο οδηγός
  δείχνει πώς να προσθέσετε σχήμα ορθογωνίου, να ορίσετε το μέγεθος του σχήματος και
  να διαχειριστείτε τις διαστάσεις του σχήματος προγραμματιστικά.
og_image_alt: Screenshot of a rectangle shape inside a grouped shape in a newly created
  Word document
og_title: Δημιουργία εγγράφου Word με σχήματα – Aspose.Words C# οδηγός
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create word document, add rectangle shape, and set shape
    dimensions with Aspose.Words. Step‑by‑step C# guide for precise shape sizing.
  headline: How to create word document with shapes using Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Πώς να δημιουργήσετε έγγραφο Word με σχήματα χρησιμοποιώντας το Aspose.Words
  σε C#
url: /el/net/programming-with-shapes/how-to-create-word-document-with-shapes-using-aspose-words-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε έγγραφο Word με σχήματα χρησιμοποιώντας Aspose.Words σε C#

Αν χρειάζεστε **να δημιουργήσετε έγγραφο word** που περιέχει προσαρμοσμένα γραφικά, μπορείτε να το κάνετε εξ ολοκλήρου με κώδικα. Αυτό το tutorial σας καθοδηγεί στη δημιουργία ενός αρχείου Word, στην προσθήκη ενός σχήματος ορθογωνίου και στον έλεγχο κάθε διάστασης του σχήματος. Στο τέλος θα έχετε ένα επαναχρησιμοποιήσιμο snippet που μπορείτε να ενσωματώσετε σε οποιοδήποτε .NET project.

Θα μάθετε πώς να **προσθέσετε σχήμα ορθογωνίου**, **ορίσετε το μέγεθος του σχήματος** και **ορίσετε τις διαστάσεις του σχήματος** μέσα σε ένα ομαδοποιημένο container. Το παράδειγμα χρησιμοποιεί Aspose.Words 13.9, αλλά οι έννοιες ισχύουν και για μεταγενέστερες εκδόσεις. Δεν απαιτείται προηγούμενη εμπειρία με το Aspose drawing API—απλώς βασικές γνώσεις C#.

## Προαπαιτούμενα

- .NET 6.0 ή νεότερη έκδοση εγκατεστημένη  
- Πακέτο NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)  
- Ένα IDE όπως το Visual Studio 2022 (οποιοσδήποτε επεξεργαστής που υποστηρίζει C# λειτουργεί)  

Η διαθεσιμότητα αυτών των εργαλείων σας επιτρέπει να εκτελέσετε τον κώδικα αμέσως χωρίς πρόσθετη διαμόρφωση.

## Βήμα 1: Αρχικοποίηση του εγγράφου και του builder – βασικά δημιουργίας εγγράφου word

Η πρώτη ενέργεια είναι η δημιουργία ενός αντικειμένου `Document` και ενός `DocumentBuilder`. Το `Document` αντιπροσωπεύει το αρχείο, ενώ ο `DocumentBuilder` παρέχει ένα fluent API για την εισαγωγή περιεχομένου.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Create a new, empty Word document
        Document doc = new Document();

        // DocumentBuilder gives us a cursor to insert nodes
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Γιατί είναι σημαντικό:**  
Η δημιουργία του εγγράφου εκ των προτέρων σας δίνει έναν καθαρό καμβά. Ο κέρσορας του builder ξεκινά στην πρώτη παράγραφο, που είναι το σημείο όπου αργότερα θα **δημιουργήσουμε σχήματα στο word**.

## Βήμα 2: Δημιουργία GroupShape για τη συγκράτηση πολλαπλών γραφικών

Ένα `GroupShape` λειτουργεί ως container· μπορείτε να μετακινήσετε, περιστρέψετε ή αλλάξετε το μέγεθός του ως ενιαία μονάδα. Εδώ ορίζουμε το πλάτος και το ύψος του container σε points (1 pt ≈ 1/72 in).

```csharp
        // Define a group that is 300 pt wide and 200 pt high
        GroupShape group = new GroupShape(doc, 300, 200);

        // Position the group 50 pt from the left and top margins
        group.Left = 50;
        group.Top  = 50;
```

**Γιατί είναι σημαντικό:**  
Η ομαδοποίηση σχήματος απλοποιεί τη διαχείριση διάταξης. Αν αργότερα χρειαστεί να προσθέσετε περισσότερα σχήματα (π.χ. κύκλους ή πλαίσια κειμένου), θα κληρονομήσουν τη θέση και την κλίμακα του group.

## Βήμα 3: Δημιουργία σχήματος ορθογωνίου και ρύθμιση των διαστάσεών του

Τώρα προσθέτουμε το πραγματικό ορθογώνιο. Ο κατασκευαστής `Shape` απαιτεί την αναφορά του εγγράφου και τον τύπο του σχήματος. Μετά τη δημιουργία ορίζουμε ρητά **το μέγεθος του σχήματος** και **τις διαστάσεις του σχήματος**.

```csharp
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);

        // Set the rectangle’s width to 100 pt and height to 50 pt
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height

        // Position the rectangle 10 pt from the group’s left/top edges
        rectangle.Left = 10;
        rectangle.Top  = 10;
```

**Γιατί είναι σημαντικό:**  
Ο καθορισμός του πλάτους, του ύψους, του αριστερού και του άνω περιθωρίου σας δίνει έλεγχο pixel‑perfect πάνω στο σχήμα. Αυτό είναι απαραίτητο όταν το έγγραφο πρέπει να ταιριάζει με προδιαγραφή σχεδίου ή έντυπο.

## Βήμα 4: Συναρμολόγηση του group προσθέτοντας το ορθογώνιο

Η προσθήκη του ορθογωνίου στο `GroupShape` το κάνει παιδί του node. Μπορείτε να προσθέσετε όσους παιδικούς κόμβους χρειάζεστε πριν ενσωματώσετε το group στο έγγραφο.

```csharp
        // Add the rectangle to the group
        group.AppendChild(rectangle);
```

**Συμβουλή:** Αν σκοπεύετε να προσθέσετε δεύτερο σχήμα, δημιουργήστε το με τον ίδιο τρόπο και καλέστε `group.AppendChild(secondShape)`. Όλα τα παιδιά μοιράζονται το σύστημα συντεταγμένων του group.

## Βήμα 5: Εισαγωγή του ομαδοποιημένου σχήματος στο έγγραφο και αποθήκευση

Με το group πλήρως δομημένο, το τοποθετούμε στην τρέχουσα παράγραφο. Η ιδιότητα `CurrentParagraph` του builder παρέχει άμεση πρόσβαση στο υποκείμενο δέντρο κόμβων.

```csharp
        // Insert the group into the first paragraph of the document
        builder.CurrentParagraph.AppendChild(group);

        // Save the document to disk (adjust the path as needed)
        doc.Save("GroupShape.docx");

        // Optional: open the file automatically (Windows only)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**Γιατί είναι σημαντικό:**  
Η προσθήκη του group σε μια παράγραφο εξασφαλίζει ότι το σχήμα εμφανίζεται ενσωματωμένο στη ροή του κειμένου. Η αποθήκευση του εγγράφου ολοκληρώνει τη λειτουργία **create word document**.

## Συνηθισμένες παραλλαγές και ειδικές περιπτώσεις

| Σενάριο | Προσαρμογή |
|----------|------------|
| **Διαφορετική προσανατολισμός σελίδας** | Ορίστε `doc.FirstSection.PageSetup.Orientation = Orientation.Landscape;` πριν δημιουργήσετε το group. |
| **Πολλαπλά ορθογώνια** | Δημιουργήστε επιπλέον αντικείμενα `Shape` και καλέστε `group.AppendChild(newRect)` για το καθένα. |
| **Δυναμικό μέγεθος βάσει περιεχομένου** | Υπολογίστε πλάτος/ύψος από διαστάσεις εικόνας ή μετρικές κειμένου, στη συνέχεια εκχωρήστε στο `rectangle.Width` / `rectangle.Height`. |
| **Εξαγωγή σε PDF** | Μετά το `doc.Save`, καλέστε `doc.Save("GroupShape.pdf", SaveFormat.Pdf);`. |
| **Συμβατότητα με παλαιότερες εκδόσεις του Word** | Αποθηκεύστε χρησιμοποιώντας `SaveFormat.Doc` αντί για `Docx` για συμβατότητα με Word 97‑2003. |

Αυτές οι παραλλαγές δείχνουν πώς η ίδια βασική λογική μπορεί να προσαρμοστεί σε πολλές πραγματικές απαιτήσεις.

## Πλήρες, εκτελέσιμο παράδειγμα

Παρακάτω βρίσκεται το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε, επικολλήσετε και εκτελέσετε. Περιλαμβάνει όλες τις οδηγίες `using`, ένα σημείο εισόδου `Main` και σχόλια που εξηγούν κάθε γραμμή.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Define a group shape (300 pt × 200 pt) positioned at (50, 50)
        GroupShape group = new GroupShape(doc, 300, 200);
        group.Left = 50;
        group.Top  = 50;

        // 3️⃣ Create a rectangle (100 pt × 50 pt) positioned at (10, 10) inside the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height
        rectangle.Left = 10;
        rectangle.Top  = 10;

        // 4️⃣ Add the rectangle to the group
        group.AppendChild(rectangle);

        // 5️⃣ Insert the group into the first paragraph and save the file
        builder.CurrentParagraph.AppendChild(group);
        doc.Save("GroupShape.docx");

        // Open the resulting file automatically (optional)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**Αναμενόμενο αποτέλεσμα:**  
Όταν ανοίξετε το *GroupShape.docx*, η πρώτη σελίδα θα εμφανίζει ένα ορθογώνιο με γκρι περίγραμμα, τοποθετημένο 50 pt από το αριστερό/επάνω περιθώριο, με το ίδιο το ορθογώνιο να έχει μετατόπιση 10 pt μέσα στο group. Οι διαστάσεις ταιριάζουν με τις τιμές που ορίστηκαν στον κώδικα.

## Συμπέρασμα

Τώρα ξέρετε πώς να **δημιουργήσετε έγγραφο word**, **προσθέσετε σχήμα ορθογωνίου** και με ακρίβεια **ορίσετε το μέγεθος του σχήματος** και **τις διαστάσεις του σχήματος** χρησιμοποιώντας Aspose.Words. Η προσέγγιση με ομαδοποιημένα σχήματα κρατά τη διάταξη ευέλικτη και έτοιμη για μελλοντικές επεκτάσεις, όπως πρόσθετα γραφικά ή πλαίσια κειμένου.

Στη συνέχεια, εξερευνήστε συναφή θέματα όπως **create shapes in word** για κύκλους, βέλη ή προσαρμοσμένα SVG paths, και μάθετε πώς να **ορίσετε χρώμα γεμίσματος σχήματος** ή **εφαρμόσετε περιστροφή**. Πειραματιστείτε με διαφορετικές μονάδες μέτρησης για να δείτε πώς το Word αποδίδει points έναντι εκατοστών, και ενσωματώστε τον κώδικα σε μεγαλύτερους σωλήνες δημιουργίας εγγράφων.

Καλή προγραμματιστική δουλειά, και μη διστάσετε να προσαρμόσετε αυτό το μοτίβο σε οποιοδήποτε σενάριο αυτοματοποιημένης αναφοράς ή συμπλήρωσης φορμών!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στην υλοποίηση των δικών σας έργων.

- [Δημιουργία σχήματος ορθογωνίου σε Word με C# – Οδηγός βήμα‑βήμα](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Δημιουργία κενής εγγράφου Word με σχήμα ορθογωνίου με σκιά – Οδηγός βήμα‑βήμα](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Προσθήκη σκιάς σε σχήμα Word σε C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}