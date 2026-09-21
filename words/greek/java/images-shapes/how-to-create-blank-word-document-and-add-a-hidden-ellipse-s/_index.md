---
category: general
date: 2026-09-21
description: Δημιουργήστε κενό έγγραφο Word με κρυφή έλλειψη χρησιμοποιώντας C#. Μάθετε
  πώς να κρύψετε σχήμα στο Word και να δημιουργήσετε ένα κρυφό σχήμα προγραμματιστικά.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to create ellipse
- hide shape in word
- create hidden shape
language: el
lastmod: 2026-09-21
og_description: Δημιουργήστε κενό έγγραφο Word με κρυφή έλλειψη χρησιμοποιώντας C#.
  Αυτός ο οδηγός δείχνει πώς να κρύψετε σχήμα στο Word και να δημιουργήσετε κρυφά
  σχήματα προγραμματιστικά.
og_image_alt: Screenshot of a blank Word document that contains a hidden ellipse shape
  created with C#
og_title: Δημιουργία κενού εγγράφου Word με κρυφό σχήμα έλλειψης σε C#
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create blank Word document with a hidden ellipse using C#. Learn how
    to hide shape in Word and generate a hidden shape programmatically.
  headline: How to create blank Word document and add a hidden ellipse shape in C#
  type: TechArticle
- questions:
  - answer: The shape’s XML adds a few hundred bytes, which is negligible for most
      use cases. The file remains essentially the same size as a truly empty document.
    question: Does hiding a shape affect document size?
  - answer: Yes. Load the document, locate the shape (`doc.GetChildNodes(NodeType.Shape,
      true)`), and set `shape.Hidden = false`.
    question: Can I unhide the shape later programmatically?
  - answer: No. Hidden objects are excluded from the print layout, so the printed
      page stays blank.
    question: Will the hidden shape appear when printing?
  - answer: 'The `Hidden` property is part of the OOXML spec, so any Word processor
      that fully implements OOXML (Word, LibreOffice, Google Docs) will respect the
      hidden flag. --- ## Conclusion You now know how to **create blank Word document**,
      **how to create ellipse**, **hide shape in Word**, and **create hidd'
    question: Is this approach compatible with Office Open XML (OOXML) only?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Word automation
title: Πώς να δημιουργήσετε ένα κενό έγγραφο Word και να προσθέσετε ένα κρυφό σχήμα
  έλλειψης σε C#
url: /el/java/images-shapes/how-to-create-blank-word-document-and-add-a-hidden-ellipse-s/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε κενό έγγραφο Word και να προσθέσετε ένα κρυφό σχήμα έλλειψης σε C#

Αν χρειάζεται να **δημιουργήσετε κενό έγγραφο Word** που περιέχει ένα αόρατο γραφικό, αυτός ο οδηγός σας δείχνει ακριβώς πώς. Στο τέλος του tutorial θα έχετε ένα αρχείο .docx που φαίνεται κενό, αλλά στην πραγματικότητα αποθηκεύει ένα σχήμα έλλειψης που είναι κρυφό από τη διάταξη.

Θα χρησιμοποιήσουμε το Aspose.Words for .NET για να δημιουργήσουμε το έγγραφο, να εισάγουμε ένα έλλειψη, να το κρύψουμε και να αποθηκεύσουμε το αρχείο. Τα βήματα καλύπτουν επίσης **πώς να δημιουργήσετε σχήματα έλλειψης**, τον σωστό τρόπο **να κρύψετε σχήμα στο Word**, και πώς να **δημιουργήσετε κρυφό σχήμα** με κώδικα που λειτουργεί σε οποιοδήποτε έργο .NET.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* .NET 6.0 SDK ή νεότερη έκδοση εγκατεστημένη  
* Visual Studio 2022 (ή οποιονδήποτε επεξεργαστή C#)  
* Άδεια Aspose.Words for .NET ή δωρεάν έκδοση αξιολόγησης  
* Βασική εξοικείωση με τη σύνταξη C#  

Δεν απαιτούνται πρόσθετα πακέτα NuGet εκτός από `Aspose.Words`.

## Δημιουργία κενού εγγράφου Word με Aspose.Words

Το πρώτο βήμα είναι η δημιουργία ενός άδειου αρχείου Word. Αυτό μας παρέχει έναν καθαρό καμβά όπου θα μπορέσουμε αργότερα να εισάγουμε κρυφά γραφικά.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document doc = new Document();

        // The document is currently empty – it contains no paragraphs or shapes.
        // This is the foundation for all further operations.
```

**Γιατί ξεκινάμε με κενό έγγραφο** – Ξεκινώντας από ένα άδειο αρχείο εξασφαλίζουμε ότι κανένα ανεπιθύμητο περιεχόμενο δεν θα επηρεάσει το κρυφό σχήμα. Επίσης διατηρεί το μέγεθος του αρχείου στο ελάχιστο, κάτι χρήσιμο όταν το έγγραφο χρησιμοποιείται αργότερα ως πρότυπο.

## Πώς να δημιουργήσετε έλλειψη μέσα στο κενό έγγραφο

Στη συνέχεια χρειαζόμαστε ένα `DocumentBuilder` για να προσθέσουμε περιεχόμενο. Ο builder μας επιτρέπει να τοποθετήσουμε σχήματα ακριβώς εκεί που θέλουμε.

```csharp
        // Step 2: Initialize a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert an ellipse shape (width: 100 points, height: 50 points)
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

        // The ellipse now exists on the page, but it is visible by default.
```

**Εξήγηση** – `ShapeType.Ellipse` λέει στο Aspose.Words να σχεδιάσει ένα σχήμα σχεδόν κυκλικό. Το πλάτος και το ύψος μετρώνται σε points (1 pt ≈ 1/72 inch). Μπορείτε να προσαρμόσετε αυτές τις τιμές ώστε να ταιριάζουν στις ανάγκες του σχεδίου σας.

## Κρύψιμο σχήματος στο Word ώστε να μην εμφανίζεται στη διάταξη

Ένα σχήμα που είναι κρυφό παραμένει στο XML του εγγράφου, κάτι που μπορεί να είναι χρήσιμο για μεταδεδομένα, υπό όρους μορφοποίηση ή μεταγενέστερες προγραμματιστικές τροποποιήσεις. Για να το κρύψουμε, ορίζουμε την ιδιότητα `Hidden` σε `true`.

```csharp
        // Step 4: Hide the shape so it does not appear in the layout
        ellipse.Hidden = true;

        // When Hidden = true, Word treats the shape as if it were not there.
        // The shape remains in the document’s DOM, allowing you to retrieve or modify it later.
```

**Γιατί κρύβουμε το σχήμα** – Τα κρυφά σχήματα αγνοούνται από τη μηχανή διάταξης, έτσι η σελίδα φαίνεται εντελώς κενή. Ωστόσο, τα δεδομένα του σχήματος παραμένουν, κάτι που μπορεί να είναι χρήσιμο για αποθήκευση δεικτών, σελιδοδεικτών ή προσαρμοσμένου XML που μπορούν να διαβάσουν downstream διαδικασίες.

## Αποθήκευση του εγγράφου με το κρυφό σχήμα

Τέλος, γράφουμε το αρχείο στο δίσκο. Το αποθηκευμένο `.docx` θα ανοίξει στο Microsoft Word χωρίς ορατό περιεχόμενο, ενώ το κρυφό έλλειψη παραμένει παρόν.

```csharp
        // Step 5: Save the document with the hidden shape
        doc.Save(@"C:\Temp\HiddenEllipse.docx");

        // The file now contains a hidden ellipse and appears empty when opened.
    }
}
```

**Επαλήθευση** – Ανοίξτε το παραγόμενο αρχείο στο Word, μετά πατήστε `Alt+F9` για εναλλαγή κωδίκων πεδίου και `Ctrl+A` → `Ctrl+Shift+F9` για προβολή κρυφών αντικειμένων. Θα δείτε το έλλειψη στο XML του εγγράφου (`word/document.xml`) αλλά τίποτα στη σελίδα.

---

## Πλήρες, εκτελέσιμο παράδειγμα

Παρακάτω βρίσκεται το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε‑επικολλήσετε σε ένα νέο έργο κονσόλας. Περιλαμβάνει όλες τις οδηγίες `using` και τη μέθοδο `Main` ώστε να το τρέξετε χωρίς επιπλέον σκελετό.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace HiddenShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank Word document
            Document doc = new Document();

            // 2️⃣ Prepare a builder to insert content
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert an ellipse (100 pt × 50 pt)
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

            // 4️⃣ Hide the ellipse so the page stays empty
            ellipse.Hidden = true;

            // 5️⃣ Save the file
            string outPath = @"C:\Temp\HiddenEllipse.docx";
            doc.Save(outPath);

            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

**Αναμενόμενο αποτέλεσμα** – Όταν εκτελέσετε το πρόγραμμα, η κονσόλα εκτυπώνει τη διαδρομή του αρχείου και το παραγόμενο αρχείο Word δεν περιέχει ορατά αντικείμενα. Αν εξετάσετε το έγγραφο με ένα εργαλείο zip (`.docx` είναι αρχείο zip), θα βρείτε το στοιχείο `<w:pict>` που περιγράφει το έλλειψη μέσα στο `word/document.xml`.

---

## Συνηθισμένες παραλλαγές και ειδικές περιπτώσεις

| Σενάριο | Τι να αλλάξετε | Γιατί είναι σημαντικό |
|----------|----------------|------------------------|
| **Διαφορετικό σχήμα** | Αντικαταστήστε `ShapeType.Ellipse` με `ShapeType.Rectangle`, `ShapeType.Line`, κ.λπ. | Σας επιτρέπει να κρύψετε άλλα γραφικά διατηρώντας την ίδια ροή εργασίας. |
| **Πολλαπλά κρυφά σχήματα** | Καλέστε `InsertShape` πολλές φορές και ορίστε `Hidden = true` σε καθένα. | Χρήσιμο για ενσωμάτωση μιας συλλογής δεικτών ή placeholders. |
| **Υπό όρους ορατότητα** | Χρησιμοποιήστε `shape.Visible = false` μαζί με `shape.Hidden = true` για επιπλέον ασφάλεια. | Ορισμένες παλαιότερες εκδόσεις του Word αντιμετωπίζουν διαφορετικά το `Visible`; ορίζοντας και τα δύο καλύπτει όλες τις περιπτώσεις. |
| **Αποθήκευση σε ροή** | Αντικαταστήστε `doc.Save(path)` με `doc.Save(stream, SaveFormat.Docx)`. | Επιτρέπει την αποστολή του εγγράφου απευθείας μέσω HTTP ή την αποθήκευσή του σε βάση δεδομένων. |
| **Εφαρμογή στυλ** | Μετά την εισαγωγή, τροποποιήστε `ellipse.FillColor`, `ellipse.LineWeight`, κ.λπ. πριν το κρύψετε. | Το στυλ του σχήματος διατηρείται στο XML, κάτι που μπορεί να είναι χρήσιμο για μελλοντική αποκρυπτογράφηση. |

**Pro tip:** Πάντα δοκιμάζετε το κρυφό σχήμα στην έκδοση του Word-στόχου (π.χ. Word 2019, Word 365) επειδή ενδέχεται να εμφανιστούν ιδιαιτερότητες απόδοσης όταν κρυφά αντικείμενα αλληλεπιδρούν με σύνθετες διατάξεις σελίδας.

---

## Συχνές ερωτήσεις

**Ε: Επηρεάζει το κρύψιμο ενός σχήματος το μέγεθος του εγγράφου;**  
Α: Το XML του σχήματος προσθέτει μερικές εκατοντάδες bytes, κάτι που είναι αμελητέο για τις περισσότερες περιπτώσεις. Το αρχείο παραμένει ουσιαστικά του ίδιου μεγέθους με ένα πραγματικά κενό έγγραφο.

**Ε: Μπορώ να αποκρύψω το σχήμα αργότερα προγραμματιστικά;**  
Α: Ναι. Φορτώστε το έγγραφο, εντοπίστε το σχήμα (`doc.GetChildNodes(NodeType.Shape, true)`) και ορίστε `shape.Hidden = false`.

**Ε: Θα εμφανιστεί το κρυφό σχήμα κατά την εκτύπωση;**  
Α: Όχι. Τα κρυφά αντικείμενα εξαιρούνται από τη διάταξη εκτύπωσης, έτσι η εκτυπωμένη σελίδα παραμένει κενή.

**Ε: Είναι αυτή η προσέγγιση συμβατή μόνο με το Office Open XML (OOXML);**  
Α: Η ιδιότητα `Hidden` αποτελεί μέρος του προτύπου OOXML, έτσι οποιοσδήποτε επεξεργαστής Word που υλοποιεί πλήρως το OOXML (Word, LibreOffice, Google Docs) θα σεβαστεί τη σημαία κρυψίματος.

---

## Συμπέρασμα

Τώρα γνωρίζετε πώς να **δημιουργήσετε κενό έγγραφο Word**, **πώς να δημιουργήσετε έλλειψη**, **να κρύψετε σχήμα στο Word** και **να δημιουργήσετε κρυφό σχήμα** χρησιμοποιώντας το Aspose.Words for .NET. Το tutorial κάλυψε ολόκληρο τον κύκλο ζωής — από την αρχικοποίηση ενός άδειου αρχείου, μέχρι την εισαγωγή, το κρύψιμο και την αποθήκευση του σχήματος — καθώς και βήματα επαλήθευσης και κοινές παραλλαγές.

Στη συνέχεια, μπορείτε να εξερευνήσετε:

* Προσθήκη κρυφών πλαισίων κειμένου για μεταδεδομένα (τεχνική `hide shape in word` εφαρμοσμένη σε κείμενο)  
* Χρήση προσαρμοσμένων τμημάτων XML για αποθήκευση δομημένων δεδομένων παράλληλα με κρυφά σχήματα  
* Μετατροπή του εγγράφου με κρυφό σχήμα σε PDF διατηρώντας τα κρυφά στοιχεία  

Πειραματιστείτε με διαφορετικά σχήματα και ρυθμίσεις ορατότητας για να δείτε πώς το κρυφό περιεχόμενο μπορεί να λειτουργήσει ως ελαφρύ αποθηκευτικό μέσο μέσα σε αρχεία Word.

Καλή προγραμματιστική!

## Τι πρέπει να μάθετε στη συνέχεια;

Οι παρακάτω οδηγίες καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document with a Shadowed Rectangle – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}