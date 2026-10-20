---
category: general
date: 2026-07-29
description: Σχεδιάστε ορθογώνιο σε έγγραφο Word χρησιμοποιώντας το Aspose.Words.
  Μάθετε πώς να προσθέσετε σχήμα ορθογωνίου, σχήμα γραμμής και πώς να διαχειριστείτε
  πολλαπλά σχήματα σε ένα ενιαίο έγγραφο.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle word
- add rectangle shape
- add line shape
- how to add shapes
- multiple shapes word
language: el
lastmod: 2026-07-29
og_description: Σχεδιάστε ένα ορθογώνιο στο Word με το Aspose.Words. Ακολουθήστε αυτόν
  τον οδηγό βήμα‑βήμα για να προσθέσετε σχήμα ορθογωνίου, σχήμα γραμμής και να εργαστείτε
  με πολλαπλά σχήματα στο Word με ευκολία.
og_image_alt: Screenshot showing a Word document with a grouped rectangle and line
  shape – draw rectangle word example
og_title: Σχεδιάστε ορθογώνιο στο Word – Μάθετε να προσθέτετε σχήματα στο Word
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: draw rectangle word using Aspose.Words. Learn how to add rectangle
    shape, add line shape, and manage multiple shapes word in a single document.
  headline: draw rectangle word – Add Shapes in Word with Aspose
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: Σχεδίαση ορθογωνίου στο Word – Προσθήκη σχημάτων στο Word με το Aspose
url: /el/net/programming-with-shapes/draw-rectangle-word-add-shapes-in-word-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# draw rectangle word – Πλήρης Οδηγός για την Προσθήκη Σχημάτων στο Word

Έχετε αναρωτηθεί ποτέ πώς να **draw rectangle word** έγγραφα χωρίς να ανοίγετε το UI κάθε φορά; Δεν είστε μόνοι. Πολλοί προγραμματιστές χρειάζονται να δημιουργούν αρχεία Word επί τόπου, και ο πιο εύκολος τρόπος είναι να αφήσετε μια βιβλιοθήκη να κάνει το σκληρό έργο. Σε αυτό το tutorial θα σας δείξουμε ακριβώς **πώς να προσθέσετε σχήματα**—συγκεκριμένα ένα ορθογώνιο και μια γραμμή—χρησιμοποιώντας το Aspose.Words for .NET, και θα διατηρήσουμε την εστίαση στη φράση *draw rectangle word* ώστε να μην χαθείτε.

Σκεφτείτε το ως ένα μικρό στούντιο τέχνης που ζει μέσα στον κώδικά σας. Στο τέλος θα μπορείτε να **add rectangle shape**, **add line shape**, και ακόμη να τα συνδυάσετε σε ομάδες **multiple shapes word**. Χωρίς UI, χωρίς χειροκίνητη παρέμβαση, μόνο καθαρό, επαναλαμβανόμενο C#.

## Τι Θα Μάθετε

- Δημιουργία νέου εγγράφου Word με το Aspose.Words.  
- Δημιουργία ενός **GroupShape** που μπορεί να περιέχει πολλά αντικείμενα.  
- **Add rectangle shape** και **add line shape** μέσα σε αυτήν την ομάδα.  
- Εισαγωγή των ομαδοποιημένων σχημάτων στο σώμα του εγγράφου.  
- Αποθήκευση του αρχείου και άμεση προβολή του αποτελέσματος.  

Αν είστε άνετοι με τα βασικά του C# και έχετε ένα αντίγραφο του Aspose.Words, είστε έτοιμοι. Δεν απαιτούνται επιπλέον πακέτα NuGet εκτός από τη βασική βιβλιοθήκη.

> **Pro tip:** Το Aspose.Words λειτουργεί με .NET 6, .NET 7, και .NET Framework 4.6+. Επιλέξτε το runtime που ταιριάζει με το έργο σας.

![παράδειγμα draw rectangle word](https://example.com/placeholder-image.png "draw rectangle word – ομαδοποιημένα σχήματα σε αρχείο Word")

## draw rectangle word – Ρύθμιση του Εγγράφου

Πριν μπορέσουμε να **draw rectangle word** χρειάζεται ένας καθαρός καμβάς. Η κλάση `Document` είναι αυτός ο καμβάς· το `DocumentBuilder` είναι το πινέλο μας.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document doc = new Document();

// DocumentBuilder lets us insert nodes, paragraphs, tables, etc.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Οι δύο παραπάνω γραμμές μας δίνουν ένα νέο, εν ενέργεια `.docx`. Τίποτα δεν γράφεται στο δίσκο ακόμη, πράγμα που σημαίνει ότι μπορούμε να πειραματιστούμε χωρίς να γεμίσουμε το σύστημα αρχείων.

## Πώς να Προσθέσετε Σχήματα – Δημιουργία ενός Container GroupShape

Όταν θέλετε τα **multiple shapes word** να συμπεριφέρονται ως μια ενιαία μονάδα—να μετακινούνται μαζί, να περιστρέφονται μαζί—τα τυλίγετε σε ένα `GroupShape`. Σκεφτείτε μια ομάδα ως φάκελο που περιέχει άλλα σχήματα.

```csharp
// Define a GroupShape that will act as a container for other shapes.
// Width = 300 pts, Height = 200 pts (roughly 4.2" x 2.8").
GroupShape group = new GroupShape(doc, 300, 200)
{
    Left = 100,   // Position from the left margin.
    Top  = 100    // Position from the top margin.
};
```

Γιατί μια ομάδα; Επειδή αργότερα μπορεί να θέλετε να **add rectangle shape** και **add line shape** και μετά να τα μετακινήσετε μαζί. Χωρίς ομάδα, θα πρέπει να επανατοποθετήσετε κάθε σχήμα ξεχωριστά.

## add rectangle shape – Εισαγωγή Ορθογωνίου Μέσα στην Ομάδα

Τώρα που υπάρχει το container, ας **add rectangle shape**. Ένα ορθογώνιο είναι ένα `Shape` του οποίου το `ShapeType` είναι `Rectangle`.

```csharp
// Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width  = 120,   // 120 points ≈ 1.67 inches.
    Height = 80,    // 80 points ≈ 1.11 inches.
    Left   = 10,    // Offset inside the group.
    Top    = 10
};

// Append the rectangle to the group.
group.AppendChild(rectangle);
```

Παρατηρήστε ότι οι τιμές `Left` και `Top` είναι σχετικές με το αρχικό σημείο της ομάδας, όχι με τη σελίδα. Αυτό κάνει εύκολο το ακριβές ευθυγράμμιση των σχημάτων. Το ορθογώνιο θα εμφανιστεί κοντά στην επάνω‑αριστερή γωνία της ομάδας.

## add line shape – Προσθήκη Γραμμής στην Ίδια Ομάδα

Μια γραμμή είναι απλώς ένα άλλο `Shape`, αλλά το `ShapeType` της είναι `Line`. Θα την τοποθετήσουμε κάτω από το ορθογώνιο.

```csharp
// Create a line shape.
Shape line = new Shape(doc, ShapeType.Line)
{
    Width  = 150,   // Length of the line.
    Height = 0,     // Height is zero for a straight line.
    Left   = 10,
    Top    = 110    // Position it a bit lower than the rectangle.
};

// Append the line to the group.
group.AppendChild(line);
```

Επειδή το ύψος της γραμμής είναι μηδέν, η ιδιότητα `Top` καθορίζει πού βρίσκεται η γραμμή κάθετα. Το `Width` ελέγχει το πόσο μακριά εκτείνεται η γραμμή οριζόντια.

## multiple shapes word – Εισαγωγή της Ομάδας στο Σώμα του Εγγράφου

Έχουμε μια ομάδα που τώρα περιέχει **add rectangle shape** και **add line shape**. Το τελευταίο βήμα είναι να τοποθετήσουμε όλο το σύνολο στο έγγραφο.

```csharp
// Insert the completed group into the document body at the current cursor position.
builder.InsertNode(group);
```

`InsertNode` τοποθετεί την ομάδα ακριβώς εκεί που βρίσκεται αυτή τη στιγμή ο `DocumentBuilder`. Αν τη χρειάζεστε σε μια συγκεκριμένη παράγραφο, μετακινήστε πρώτα τον builder με `builder.MoveToParagraph(index)`.

## Αποθήκευση του Αποτελέσματος – Προβολή του draw rectangle word Αποτελέσματος

```csharp
// Save the document to disk. Change the path to a location that exists on your machine.
doc.Save("C:/Temp/GroupShape.docx");
```

Ανοίξτε το παραγόμενο αρχείο στο Microsoft Word και θα δείτε μια ενιαία ομάδα που περιέχει ένα ορθογώνιο και μια γραμμή. Μπορείτε να κάνετε κλικ στην ομάδα, να τη σύρετε ή ακόμη και να την αλλάξετε μέγεθος—όλα τα σχήματα μετακινούνται μαζί. Αυτή είναι η δύναμη των **multiple shapes word**.

### Αναμενόμενο Αποτέλεσμα

- Ένα αρχείο `.docx` με όνομα `GroupShape.docx`.  
- Μία σελίδα με ένα ομαδοποιημένο ορθογώνιο (120 × 80 pt) κοντά στην επάνω‑αριστερή γωνία.  
- Μία οριζόντια γραμμή (150 pt μήκος) τοποθετημένη ακριβώς κάτω από το ορθογώνιο.  
- Και τα δύο σχήματα είναι επιλέξιμα ως ένα ενιαίο αντικείμενο.

Αν κάνετε διπλό κλικ στην ομάδα, το Word θα σας επιτρέψει να επεξεργαστείτε κάθε σχήμα ξεχωριστά—ιδανικό για λεπτομερή ρύθμιση.

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

**Τι γίνεται αν χρειάζομαι περισσότερα από δύο σχήματα;**  
Απλώς συνεχίστε να καλείτε `group.AppendChild(yourShape)` για κάθε επιπλέον αντικείμενο. Η ομάδα μπορεί να περιέχει οποιονδήποτε αριθμό σχημάτων, καθιστώντας την ιδανική για σύνθετα διαγράμματα.

**Μπορώ να αλλάξω το χρώμα γεμίσματος του ορθογωνίου;**  
Απόλυτα. Μετά τη δημιουργία του ορθογωνίου, ορίστε `rectangle.FillColor = System.Drawing.Color.LightBlue;`. Αυτό λειτουργεί για οποιοδήποτε σχήμα υποστηρίζει γέμισμα.

**Πρέπει να ορίσω `Height = 0` για μια γραμμή;**  
Ναι, για μια ευθεία οριζόντια γραμμή το ύψος πρέπει να είναι μηδέν. Για μια κάθετη γραμμή, ορίστε `Width = 0` και δώστε στο `Height` μια θετική τιμή.

**Θα λειτουργήσει αυτό με αρχεία .doc (Word 97‑2003);**  
Το Aspose.Words μπορεί να αποθηκεύσει στην παλαιότερη μορφή `.doc`, αλλά ορισμένα σύγχρονα χαρακτηριστικά σχημάτων μπορεί να είναι περιορισμένα. Παραμείνετε στο `.docx` για πλήρη πιστότητα.

**Πώς μπορώ να περιστρέψω ολόκληρη την ομάδα;**  
Μπορείτε να ορίσετε `group.Rotation = 45;` (μοίρες) πριν την εισαγωγή. Η περιστροφή εφαρμόζεται σε κάθε παιδικό σχήμα.

## Ανακεφαλαίωση – Πώς να Προσθέσετε Σχήματα στο Word Προγραμματιστικά

- **draw rectangle word** ξεκινά με τη δημιουργία ενός `Document` και `DocumentBuilder`.  
- Δημιουργήστε ένα **GroupShape** για να κρατήσετε **multiple shapes word**.  
- **add rectangle shape** και **add line shape** προσαρτώνται στην ομάδα.  
- Εισάγετε την ομάδα στο σώμα με `builder.InsertNode`.  
- Αποθηκεύστε το αρχείο και ανοίξτε το για να επαληθεύσετε το οπτικό αποτέλεσμα.

Αυτή είναι η πλήρης ροή εργασίας, τυλιγμένη σε έναν ενιαίο, εύκολο‑ανάγνωστο κατάλογο κώδικα.

## Επόμενα Βήματα & Σχετικά Θέματα

Τώρα που γνωρίζετε **πώς να προσθέσετε σχήματα**, σκεφτείτε να εξερευνήσετε:

- **add rectangle shape** με στρογγυλεμένες γωνίες (`ShapeType.Rectangle` + `CornerRadius`).  
- Στυλιζάρισμα γραμμών με διαφορετικά μοτίβα παύλας (`line.LineFormat.DashStyle`).  
- Ενσωμάτωση εικόνων μαζί με σχήματα για πιο πλούσιες αναφορές.  
- Χρήση **multiple shapes word** για τη δημιουργία διαγραμμάτων ροής ή απλών διαγραμμάτων UML.  

Κάθε ένα από αυτά τα θέματα χτίζει φυσικά πάνω στο θεμέλιο που θέσαμε εδώ, και όλα ακολουθούν το ίδιο μοτίβο δημιουργίας σχημάτων, ρύθμισης τους, και ομαδοποίησης εάν χρειάζεται.

---

Καλό κώδικα! Αν αντιμετωπίσετε ιδιαιτερότητες ή έχετε μια ενδιαφέρουσα περίπτωση χρήσης να μοιραστείτε, αφήστε ένα σχόλιο παρακάτω. Η ανατροφοδότησή σας μας βοηθά όλους να κυριαρχήσουμε στην τέχνη του **draw rectangle word** και πέραν αυτού.

## Τι Πρέπει Να Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε σε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}