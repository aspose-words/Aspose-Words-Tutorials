---
category: general
date: 2026-10-23
description: Δημιουργήστε ένα κενό έγγραφο Word, προσθέστε ένα σχήμα ορθογωνίου και
  κρύψτε το σχήμα στο Word χρησιμοποιώντας το Aspose.Words. Κώδικας βήμα‑βήμα για
  προγραμματιστές .NET.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- how to insert shape
- hide shape word
language: el
lastmod: 2026-10-23
og_description: Δημιουργήστε ένα κενό έγγραφο Word, προσθέστε ένα σχήμα ορθογωνίου
  και κρύψτε το σχήμα στο Word με το Aspose.Words. Ακολουθήστε το πλήρες παράδειγμα
  C#.
og_image_alt: Screenshot of a Word document containing a hidden rectangle shape
og_title: Δημιουργήστε ένα κενό έγγραφο Word και προσθέστε ένα κρυφό σχήμα ορθογωνίου
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Create a blank Word document, add a rectangle shape, and hide the shape
    in Word using Aspose.Words. Step‑by‑step code for .NET developers.
  headline: Create a blank Word document and add a rectangle shape
  type: TechArticle
tags:
- Aspose.Words
- .NET
- Word automation
title: Δημιουργήστε ένα κενό έγγραφο Word και προσθέστε ένα σχήμα ορθογωνίου
url: /el/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργήστε ένα κενό έγγραφο Word και προσθέστε ένα σχήμα ορθογωνίου

Αν χρειάζεστε **να δημιουργήσετε ένα κενό έγγραφο Word**, αυτός ο οδηγός σας δείχνει πώς να το κάνετε με το Aspose.Words for .NET. Θα μάθετε επίσης **πώς να εισάγετε σχήμα**—συγκεκριμένα ένα ορθογώνιο—και **να κρύψετε το σχήμα** ώστε να μην επηρεάζει τη διάταξη.

Ο οδηγός περνάει από κάθε γραμμή κώδικα, εξηγεί γιατί κάθε βήμα είναι σημαντικό και καλύπτει κοινά προβλήματα όπως η ορατότητα κρυφών σχημάτων σε διαφορετικές λειτουργίες προβολής του Word. Στο τέλος θα έχετε ένα πλήρως λειτουργικό αρχείο `.docx` που περιέχει ένα κρυφό σχήμα ορθογωνίου που μπορείτε αργότερα να αποκαλύψετε ή να το χειριστείτε προγραμματιστικά.

## Προαπαιτούμενα

- .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.6+)
- Aspose.Words for .NET NuGet package (`Install-Package Aspose.Words`)
- Περιβάλλον ανάπτυξης όπως το Visual Studio 2022 ή το VS Code με επεκτάσεις C#
- Βασική εξοικείωση με τη σύνταξη C# και τις έννοιες εγγράφων Word

Δεν απαιτείται πρόσθετη εγκατάσταση του Office επειδή το Aspose.Words λειτουργεί πλήρως στη μνήμη.

## Δημιουργία κενού εγγράφου Word

Το πρώτο βήμα είναι η δημιουργία ενός κενό αντικειμένου `Document`. Αυτό το αντικείμενο αντιπροσωπεύει ένα αρχείο Word που δεν περιέχει ακόμη ενότητες, παραγράφους ή περιεχόμενο.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document
Document document = new Document();
```

**Γιατί είναι σημαντικό:**  
Ένα κενό `Document` σας παρέχει ένα καθαρό καμβά. Αν ξεκινήσετε από ένα υπάρχον πρότυπο, τα κρυφά σχήματα μπορεί να κληρονομήσουν ανεπιθύμητα στυλ. Ξεκινώντας από το μηδέν διασφαλίζετε ότι το σχήμα ορθογωνίου που θα προσθέσετε αργότερα είναι το μοναδικό περιεχόμενο που ελέγχετε.

## Προσθήκη σχήματος ορθογωνίου στο έγγραφο

Στη συνέχεια, χρειαζόμαστε ένα `DocumentBuilder` για να τοποθετήσουμε περιεχόμενο στο έγγραφο. Η μέθοδος `InsertShape` του builder είναι ο τυπικός τρόπος **να εισάγετε σχήματα** όπως ορθογώνια, κύκλους ή προσαρμοσμένες σχεδιάσεις.

```csharp
// Step 2: Initialize a DocumentBuilder to add content
DocumentBuilder builder = new DocumentBuilder(document);

// Step 3: Insert a rectangle shape of size 200x100 points
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

**Γιατί είναι σημαντικό:**  
`InsertShape` επιστρέφει ένα αντικείμενο `Shape` που μπορείτε να διαμορφώσετε περαιτέρω (χρώμα, στυλ γραμμής κ.λπ.). Οι διαστάσεις δίνονται σε points (1 point = 1/72 ίντσα), που ταιριάζει με το εσωτερικό σύστημα μέτρησης του Word.

### Προαιρετικό: μορφοποίηση του ορθογωνίου (προαιρετικό)

Αν θέλετε το ορθογώνιο να έχει ορατό περίγραμμα όταν το αποκρύψετε αργότερα, μπορείτε να ορίσετε το πάχος της γραμμής και το χρώμα του:

```csharp
rectangleShape.LineWeight = 0.5;               // Thin border
rectangleShape.LineColor = System.Drawing.Color.Blue;
```

Αυτές οι γραμμές είναι προαιρετικές επειδή το σχήμα θα κρυφτεί στο επόμενο βήμα.

## Απόκρυψη του σχήματος στο Word

Το Word επιτρέπει στα σχήματα να κρύβονται από τη διάταξη ενώ εξακολουθούν να αποτελούν μέρος του μοντέλου αντικειμένων του εγγράφου. Ορίζοντας την ιδιότητα `Hidden` σε `true` κάνει το σχήμα αόρατο στην κανονική προβολή αλλά παραμένει επιλέξιμο μέσω του API.

```csharp
// Step 4: Hide the shape so it does not appear in the layout
rectangleShape.Hidden = true;
```

**Γιατί είναι σημαντικό:**  
Ένα κρυφό σχήμα είναι χρήσιμο για την αποθήκευση μεταδεδομένων, placeholders για επεξεργασία αργότερα ή υπό όρους περιεχόμενο που αποκαλύπτεται μόνο υπό ορισμένες συνθήκες (π.χ., κατά τη δημιουργία τελικής αναφοράς). Το σχήμα παραμένει στο αρχείο, ώστε να μπορείτε προγραμματιστικά να το αποκαλύψετε αργότερα με `rectangleShape.Hidden = false;`.

## Αποθήκευση του εγγράφου

Τέλος, γράψτε το έγγραφο στο δίσκο. Η επέκταση του αρχείου καθορίζει τη μορφή Word· το `.docx` είναι η σύγχρονη μορφή Open XML.

```csharp
// Step 5: Save the document with the hidden shape
string outputPath = @"C:\Temp\HiddenShape.docx";
document.Save(outputPath);
```

**Αποτέλεσμα:**  
Ανοίγοντας το `HiddenShape.docx` στο Microsoft Word εμφανίζει μια κανονικά κενή σελίδα. Το ορθογώνιο δεν είναι ορατό, αλλά αν μεταβείτε στο **Home → Select → Selection Pane**, θα δείτε το σχήμα στη λίστα και μπορείτε να εναλλάξετε την ορατότητά του.

## Πλήρες λειτουργικό παράδειγμα

Παρακάτω βρίσκεται το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε, επικολλήσετε και εκτελέσετε. Περιλαμβάνει όλες τις απαραίτητες δηλώσεις `using` και σχόλια.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document
        Document document = new Document();

        // Initialize a DocumentBuilder for content insertion
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a rectangle shape (200x100 points)
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // Optional styling (comment out if not needed)
        rectangleShape.LineWeight = 0.5;
        rectangleShape.LineColor = System.Drawing.Color.Blue;

        // Hide the shape so it does not appear in the layout
        rectangleShape.Hidden = true;

        // Save the document
        string outputPath = @"C:\Temp\HiddenShape.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Αναμενόμενη έξοδος:**  

- Η κονσόλα εκτυπώνει τη διαδρομή αποθήκευσης.  
- `HiddenShape.docx` ανοίγει ως κενή σελίδα στο Word.  
- Το σχήμα ορθογωνίου υπάρχει αλλά είναι κρυφό· μπορείτε να το επαληθεύσετε μέσω του *Selection Pane* ή προγραμματιστικά ορίζοντας `Hidden = false` και ανοίγοντας ξανά το αρχείο.

## Συχνές ερωτήσεις και ειδικές περιπτώσεις

| Ερώτηση | Απάντηση |
|----------|--------|
| **Μπορώ να κρύψω άλλους τύπους σχημάτων;** | Ναι. Οποιοδήποτε `Shape` (π.χ., `ShapeType.Ellipse`, `ShapeType.Picture`) υποστηρίζει την ιδιότητα `Hidden`. |
| **Θα αυξήσει το κρυφό σχήμα το μέγεθος του αρχείου;** | Η αύξηση είναι αμελητέα (μερικά kilobytes) επειδή τα δεδομένα του σχήματος αποθηκεύονται ως XML στο πακέτο `.docx`. |
| **Τι αν θέλω το σχήμα να εμφανίζεται μόνο στην προβολή εκτύπωσης;** | Χρησιμοποιήστε την ιδιότητα `Shape.IsPrint` αντί για `Hidden`. Ορίζοντας `IsPrint = false` κρύβει το σχήμα από την εκτυπωμένη έξοδο αλλά το διατηρεί ορατό στην οθόνη. |
| **Πώς να αποκαλύψω το σχήμα αργότερα;** | Φορτώστε το έγγραφο, εντοπίστε το σχήμα (π.χ., με `Shape.Name`), στη συνέχεια ορίστε `shape.Hidden = false;` και αποθηκεύστε. |
| **Λειτουργεί αυτό με μορφή .doc (δυαδική);** | Ναι, το Aspose.Words μπορεί να αποθηκεύσει σε `.doc` χρησιμοποιώντας `document.Save("file.doc");`. Η σημαία κρυφού παραμένει. |

## Συμβουλές επαγγελματιών

- **Ονομάστε τα σχήματά σας**: `rectangleShape.Name = "PlaceholderRectangle";` κάνει πιο εύκολο να τα βρείτε αργότερα μέσω `document.GetChildNodes(NodeType.Shape, true).Cast<Shape>().FirstOrDefault(s => s.Name == "PlaceholderRectangle")`.
- **Επεξεργασία κατά παρτίδες**: Αν χρειαστεί να προσθέσετε κρυφά σχήματα σε πολλά έγγραφα, τυλίξτε τον κώδικα σε μια μέθοδο και επαναχρησιμοποιήστε το αντικείμενο `DocumentBuilder`.
- **Απόδοση**: Η δημιουργία ενός σχήματος είναι φθηνή, αλλά η συχνή αποθήκευση μεγάλων εγγράφων μπορεί να περιορίζεται από το I/O. Σκεφτείτε τη χρήση `MemoryStream` για ενδιάμεση επεξεργασία.

## Συμπέρασμα

Τώρα ξέρετε πώς να **δημιουργήσετε ένα κενό έγγραφο Word**, **προσθέσετε ένα σχήμα ορθογωνίου** και **να κρύψετε το σχήμα** χρησιμοποιώντας το Aspose.Words for .NET. Αυτή η τεχνική σας επιτρέπει να ενσωματώσετε αόρατα placeholders που μπορείτε να αποκαλύψετε ή να τα χειριστείτε αργότερα, ένα μοτίβο χρήσιμο για δυναμική δημιουργία αναφορών, υπό όρους περιεχόμενο και δημιουργία προτύπων εγγράφων.

- Αντικαταστήστε το ορθογώνιο με μια εικόνα ή γράφημα χρησιμοποιώντας `ShapeType.Picture`.
- Χρησιμοποιήστε **how to insert shape** σε ενότητες κεφαλίδας/υποσέλιδου για placeholders τύπου υδατογράφημα.
- Συνδυάστε κρυφά σχήματα με επικύρωση δεδομένων βασισμένη σε **add rectangle shape** (π.χ., αποθήκευση JSON στην ιδιότητα `AlternativeText` ενός σχήματος).

Καλό κώδικα, και μη διστάσετε να πειραματιστείτε με άλλους τύπους σχημάτων και επιλογές ορατότητας ώστε να ταιριάζουν στις ανάγκες αυτοματοποίησης εγγράφων σας!

## Τι θα πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Δημιουργία εγγράφου Word – Πώς να προσθέσετε σχήμα ορθογωνίου και σκιά](/words/english/net/programming-with-shapes/create-word-document-how-to-add-rectangle-shape-and-shadow/)
- [Δημιουργία ομαδικού σχήματος σε έγγραφο Word χρησιμοποιώντας Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Δημιουργία κενού εγγράφου Word με κρυφό σχήμα έλλειψης – Πλήρης οδηγός C#](/words/english/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}