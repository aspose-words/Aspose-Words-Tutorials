---
category: general
date: 2026-07-29
description: Δημιουργήστε ένα κενό έγγραφο Word και μάθετε πώς να κρύψετε σχήμα, να
  δημιουργήσετε κρυφό αντικείμενο και να δημιουργήσετε σχήμα έλλειψης χρησιμοποιώντας
  το Aspose.Words σε C#. Περιλαμβάνεται κώδικας βήμα‑προς‑βήμα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- blank word document
- how to hide shape
- create hidden object
- create ellipse shape
language: el
lastmod: 2026-07-29
og_description: Δημιουργήστε ένα κενό έγγραφο Word και κρύψτε το σχήμα αμέσως. Μάθετε
  πώς να δημιουργήσετε κρυφό αντικείμενο και να σχεδιάσετε ένα σχήμα έλλειψης χρησιμοποιώντας
  το Aspose.Words σε C#.
og_image_alt: Hidden ellipse shape inserted into a blank Word document
og_title: Δημιουργήστε ένα κενό έγγραφο Word με κρυφό σχήμα έλλειψης – Εγχειρίδιο
  C#
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Create a blank word document and learn how to hide shape, create hidden
    object, and create ellipse shape using Aspose.Words in C#. Step‑by‑step code included.
  headline: Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide
  type: TechArticle
- description: Create a blank word document and learn how to hide shape, create hidden
    object, and create ellipse shape using Aspose.Words in C#. Step‑by‑step code included.
  name: Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide
  steps:
  - name: What if the target Word version doesn’t support hidden shapes?
    text: The `Hidden` flag is part of the Office Open XML spec and is respected by
      Word 2007+ and LibreOffice. Older formats (e.g., `.doc`) ignore the flag, so
      always save as `.docx` when you need reliable hiding.
  - name: Can I hide other types of objects (pictures, tables)?
    text: Yes. Any node derived from `Shape`—including pictures, text boxes, and even
      SmartArt—exposes the `Hidden` property. Just set it to `true` before insertion.
  - name: Does hiding a shape affect document performance?
    text: Negligibly. The shape is stored as XML markup, and Word skips rendering
      hidden objects during layout. If you embed many hidden objects, the file size
      grows, but rendering stays fast.
  - name: How does this differ from using a bookmark or comment as a marker?
    text: Bookmarks are invisible by design, but they’re meant for navigation, not
      visual placeholders. Comments appear in the margin. A hidden shape gives you
      a visual object (size, position) that you can later reveal or manipulate, which
      is handy for templating scenarios.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
- Shapes
title: Δημιουργήστε ένα κενό έγγραφο Word με κρυφό σχήμα έλλειψης – Πλήρης οδηγός
  C#
url: /el/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία Κενής Εγγράφου Word με Κρυφή Σχήμα Έλλειψη – Πλήρης Οδηγός C#

Κάποτε χρειάστηκε να δημιουργήσετε ένα **κενό έγγραφο word** και στη συνέχεια να κρύψετε ένα σχήμα μέσα σε αυτό; Ίσως δημιουργείτε ένα πρότυπο όπου ορισμένοι δείκτες πρέπει να παραμείνουν αόρατοι μέχρι ένα μεταγενέστερο βήμα. Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα από το **πώς να κρύψετε σχήμα**, το **πώς να δημιουργήσετε κρυφό αντικείμενο**, και ακόμη το **πώς να δημιουργήσετε σχήμα έλλειψης** χρησιμοποιώντας το Aspose.Words για .NET. Στο τέλος θα έχετε ένα έτοιμο κομμάτι κώδικα C# που παράγει ένα αρχείο DOCX που περιέχει μια αόρατη έλλειψη.

## Τι Θα Μάθετε

- Αρχικοποίηση ενός φρέσκου κενό εγγράφου Word με το Aspose.Words.  
- Δημιουργία σχήματος έλλειψης, ορισμός διαστάσεων και τοποθέτηση στη σελίδα.  
- Σήμανση του σχήματος ως κρυφό ώστε να μην εμφανίζεται στην οθόνη ή στην εκτύπωση.  
- Αποθήκευση του αποτελέσματος στο δίσκο και επαλήθευση ότι το κρυφό αντικείμενο είναι πραγματικά αόρατο.  

Δεν απαιτούνται εξωτερικές βιβλιοθήκες εκτός από το Aspose.Words, και ο κώδικας λειτουργεί με την έκδοση 24.10 ή νεότερη (η ιδιότητα `Hidden` εισήχθη σε αυτή την έκδοση). Ας ξεκινήσουμε.

![Διάγραμμα μιας κρυφής έλλειψης μέσα σε ένα κενό έγγραφο Word](https://example.com/hidden-ellipse.png "Κρυφό σχήμα έλλειψης που εισάγεται σε ένα κενό έγγραφο Word")

## Δημιουργία Κενής Εγγράφου Word και Εισαγωγή Κρυφής Σχήματος Έλλειψης

Το πρώτο βήμα είναι η δημιουργία ενός ολοκαίνουργιου εγγράφου. Σκεφτείτε το `Document` ως ένα κενό καμβά· το `DocumentBuilder` είναι το πινέλο σας.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document and a DocumentBuilder to edit it.
Document document = new Document();               // This is your blank word document.
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Γιατί να ξεκινήσετε με κενό έγγραφο;**  
> Ένα καθαρό φύλλο εξασφαλίζει ότι κανένα προϋπάρχον περιεχόμενο δεν θα επηρεάσει το κρυφό σχήμα που πρόκειται να προσθέσετε. Επίσης κάνει το παράδειγμα πιο εύκολο στην αντιγραφή‑επικόλληση σε οποιοδήποτε έργο.

## Πώς να Κρύψετε Σχήμα: Ορισμός της Ιδιότητας Hidden

Το Aspose.Words 24.10 εισήγαγε τη σημαία `Hidden` στο `Shape`. Όταν οριστεί σε `true`, το Word αντιμετωπίζει το σχήμα όπως ένα σχόλιο—εντελώς αόρατο στη διεπαφή χρήστη και στην εκτύπωση.

```csharp
// Step 2: Create an ellipse shape and set its size and position.
Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
ellipseShape.Width = 100;   // Width in points
ellipseShape.Height = 80;   // Height in points
ellipseShape.Left = 150;    // Horizontal offset from the left margin
ellipseShape.Top = 150;     // Vertical offset from the top margin

// Step 3: Hide the shape so it does not appear when the document is viewed or printed.
ellipseShape.Hidden = true;   // This is the key to "how to hide shape"
```

> **Συμβουλή:** Αν αργότερα χρειαστεί να αποκαλύψετε το σχήμα προγραμματιστικά, απλώς αλλάξτε `ellipseShape.Hidden = false;` και αποθηκεύστε ξανά το έγγραφο.

## Δημιουργία Κρυφού Αντικειμένου: Εισαγωγή του Σχήματος στο Έγγραφο

Τώρα που η έλλειψη είναι προετοιμασμένη και κρυφή, την εισάγουμε στη θέση του κέρσορα του builder. Η προεπιλεγμένη θέση του builder είναι η αρχή της πρώτης παραγράφου, κάτι τέλειο για ένα κενό έγγραφο.

```csharp
// Step 4: Insert the hidden shape into the document at the current builder position.
builder.InsertNode(ellipseShape);
```

> **Τι αν χρειάζεστε το σχήμα σε συγκεκριμένη σελίδα;**  
> Μετακινήστε πρώτα τον builder στη ζητούμενη σελίδα (`builder.MoveToDocumentEnd();` ή `builder.MoveToPage(pageNumber);`) πριν καλέσετε το `InsertNode`.

## Αποθήκευση του Εγγράφου που Περιέχει το Κρυφό Σχήμα

Τέλος, γράψτε το αρχείο στο δίσκο. Το αποτέλεσμα θα είναι ένα τυπικό DOCX που μπορεί να ανοίξει οποιοσδήποτε επεξεργαστής κειμένου—εκτός από το ότι η έλλειψη θα παραμείνει αόρατη.

```csharp
// Step 5: Save the document containing the hidden shape.
document.Save("YOUR_DIRECTORY/HiddenShape.docx");
```

> **Αναμενόμενο αποτέλεσμα:** Ανοίξτε το `HiddenShape.docx` στο Microsoft Word. Δεν θα δείτε καμία γραφική παράσταση, αλλά το μέγεθος του αρχείου θα είναι ελαφρώς μεγαλύτερο από ένα πραγματικά κενό έγγραφο επειδή η κρυφή έλλειψη αποθηκεύεται στο XML.

## Επαλήθευση της Κρυφής Έλλειψης Προγραμματιστικά (Προαιρετικό)

Αν θέλετε να ελέγξετε διπλά ότι το σχήμα είναι πράγματι κρυφό, μπορείτε να φορτώσετε το αποθηκευμένο αρχείο και να ελέγξετε την ιδιότητα `Hidden` του σχήματος:

```csharp
Document loaded = new Document("YOUR_DIRECTORY/HiddenShape.docx");
Shape loadedShape = (Shape)loaded.GetChild(NodeType.Shape, 0, true);
Console.WriteLine($"Is shape hidden? {loadedShape.Hidden}"); // Should print True
```

Η εκτέλεση αυτού του αποσπάσματος εκτυπώνει `True`, επιβεβαιώνοντας ότι το κρυφό αντικείμενο επέζησε του κύκλου αποθήκευσης‑φόρτωσης.

## Ακραίες Περιπτώσεις και Συχνές Ερωτήσεις

### Τι γίνεται αν η έκδοση του Word δεν υποστηρίζει κρυφά σχήματα;

Η σημαία `Hidden` είναι μέρος του προτύπου Office Open XML και αναγνωρίζεται από το Word 2007+ και το LibreOffice. Παλαιότερες μορφές (π.χ., `.doc`) αγνοούν τη σημαία, γι' αυτό πάντα αποθηκεύετε ως `.docx` όταν χρειάζεστε αξιόπιστη απόκρυψη.

### Μπορώ να κρύψω άλλους τύπους αντικειμένων (εικόνες, πίνακες);

Ναι. Οποιοσδήποτε κόμβος προέρχεται από το `Shape`—συμπεριλαμβανομένων εικόνων, πλαισίων κειμένου και ακόμη SmartArt—έχει την ιδιότητα `Hidden`. Απλώς ορίστε την σε `true` πριν την εισαγωγή.

### Επηρεάζει η απόκρυψη σχήματος την απόδοση του εγγράφου;

Παραβρεθεί. Το σχήμα αποθηκεύεται ως XML markup, και το Word παραλείπει την απόδοση κρυφών αντικειμένων κατά τη διάταξη. Αν ενσωματώσετε πολλά κρυφά αντικείμενα, το μέγεθος του αρχείου αυξάνεται, αλλά η απόδοση παραμένει γρήγορη.

### Πώς διαφέρει αυτό από τη χρήση σελιδοδείκτη ή σχολίου ως δείκτη;

Οι σελιδοδείκτες είναι αόρατοι από τη φύση τους, αλλά προορίζονται για πλοήγηση, όχι για οπτικούς δείκτες. Τα σχόλια εμφανίζονται στο περιθώριο. Ένα κρυφό σχήμα σας δίνει ένα οπτικό αντικείμενο (μέγεθος, θέση) που μπορείτε αργότερα να αποκαλύψετε ή να χειριστείτε, κάτι χρήσιμο για σενάρια προτύπων.

## Πλήρες Παράδειγμα Λειτουργίας

Παρακάτω βρίσκεται το πλήρες, έτοιμο για αντιγραφή‑επικόλληση πρόγραμμα. Περιλαμβάνει όλες τις οδηγίες `using`, τη δημιουργία κρυφής έλλειψης και ένα βήμα επαλήθευσης.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HiddenEllipseDemo
{
    static void Main()
    {
        // 1️⃣ Create a blank word document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Build the ellipse shape.
        Shape ellipse = new Shape(doc, ShapeType.Ellipse)
        {
            Width = 100,
            Height = 80,
            Left = 150,
            Top = 150,
            Hidden = true               // ← how to hide shape
        };

        // 3️⃣ Insert the hidden shape.
        builder.InsertNode(ellipse);

        // 4️⃣ Save the file.
        string outPath = "HiddenEllipse.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");

        // 5️⃣ Optional: Verify that the shape is hidden.
        Document loaded = new Document(outPath);
        Shape loadedEllipse = (Shape)loaded.GetChild(NodeType.Shape, 0, true);
        Console.WriteLine($"Is the ellipse hidden? {loadedEllipse.Hidden}");
    }
}
```

Η εκτέλεση του προγράμματος δημιουργεί το `HiddenEllipse.docx` στον φάκελο εκτέλεσης. Ανοίξτε το—θα δείτε μια απολύτως κανονική κενή σελίδα, ενώ η κρυφή έλλειψη ζει ήσυχα μέσα.

## Σύνοψη

Καλύψαμε πώς να **δημιουργήσετε ένα κενό έγγραφο word**, **να κρύψετε ένα σχήμα**, **να δημιουργήσετε κρυφό αντικείμενο**, και **να δημιουργήσετε σχήμα έλλειψης** όλα με λίγες γραμμές C#. Το κλειδί είναι η ιδιότητα `Hidden` στο `Shape`, η οποία μετατρέπει οποιοδήποτε οπτικό στοιχείο σε αόρατο δείκτη χωρίς να διαταράσσει τη συμβατότητα του Word.

## Τι Ακολουθεί;

- **Στυλ του κρυφού σχήματος** (χρώμα γεμίσματος, στυλ γραμμής) ώστε όταν το αποκαλύψετε αργότερα, να φαίνεται ακριβώς όπως θέλετε.  
- **Συνδυασμός κρυφών σχημάτων με σελιδοδείκτες** για τη δημιουργία δυναμικών προτύπων που μπορούν να ενεργοποιηθούν ή να απενεργοποιηθούν.  
- **Εξερεύνηση άλλων τύπων σχημάτων**—ορθογώνια, βέλη ή ακόμη προσαρμοσμένες διαδρομές SVG—αλλάζοντας το `ShapeType.Ellipse`.  

Νιώστε ελεύθεροι να πειραματιστείτε: αλλάξτε το μέγεθος, μετακινήστε τη θέση, ή εισάγετε πολλαπλές κρυφές έλλειψεις. Το ίδιο μοτίβο λειτουργεί για οποιοδήποτε σχήμα Aspose.Words που χρειάζεται να παραμείνει εκτός οπτικής.

Αν αντιμετωπίσετε κάποιο πρόβλημα ή έχετε ιδέες για επέκταση αυτού του μοτίβου, αφήστε ένα σχόλιο παρακάτω. Καλή κωδικοποίηση!

## Τι Πρέπει Να Μάθετε Στη Σύντομη Μελλοντική

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στην υλοποίηση των δικών σας έργων.

- [Δημιουργία Κενής Εγγράφου Word με Σχήμα Ορθογωνίου με Σκιά – Οδηγός Βήμα‑Βήμα](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Δημιουργία Ομαδικού Σχήματος σε Έγγραφο Word Χρησιμοποιώντας το Aspose.Words για .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Δημιουργία Σχήματος Ορθογωνίου σε Word με Aspose.Words – Οδηγός Βήμα‑Βήμα](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}