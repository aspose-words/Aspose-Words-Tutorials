---
category: general
date: 2026-03-01
description: Δημιουργήστε έγγραφο Word χρησιμοποιώντας το Aspose.Words και μάθετε
  πώς να προσθέσετε σχήμα ορθογωνίου, πώς να προσθέσετε σκιά, πώς να ορίσετε διαφάνεια
  και πώς να δημιουργήσετε σχήμα—όλα σε C#.
draft: false
keywords:
- create word document
- add rectangle shape
- how to add shadow
- how to create shape
- how to set transparency
language: el
og_description: Δημιουργήστε έγγραφο Word με το Aspose.Words σε C#. Μάθετε πώς να
  προσθέσετε σχήμα ορθογωνίου, να εφαρμόσετε εξωτερική σκιά και να ορίσετε διαφάνεια
  σε λίγα μόνο βήματα.
og_title: Δημιουργία εγγράφου Word με σχήμα ορθογωνίου και σκιά – Οδηγός
tags:
- Aspose.Words
- C#
- Document Generation
title: Δημιουργία εγγράφου Word με σχήμα ορθογωνίου και σκιά – Οδηγός βήμα‑προς‑βήμα
url: /el/net/programming-with-shapes/create-word-document-with-a-rectangle-shape-and-shadow-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία Εγγράφου Word με Σχήμα Ορθογωνίου και Σκιά – Οδηγός Βήμα‑βήμα

Έχετε χρειαστεί ποτέ να **δημιουργήσετε έγγραφο Word** που περιέχει ένα προσαρμοσμένο σχήμα ορθογωνίου; Ίσως δημιουργείτε ένα πρότυπο αναφοράς και θέλετε μια διακριτική σκιά πτώσης για να κάνει τη διάταξη πιο εντυπωσιακή. Δεν είστε ο μόνος—οι προγραμματιστές ρωτούν συνεχώς, «Πώς μπορώ να προσθέσω σχήμα ορθογωνίου και σκιά προγραμματιστικά;» Τα καλά νέα είναι ότι με το Aspose.Words μπορείτε να το κάνετε σε λίγες γραμμές.

Σε αυτό το tutorial θα περάσουμε από όλη τη διαδικασία: από τη δημιουργία ενός κεντρικού αρχείου Word, μέχρι την προσθήκη ενός σχήματος ορθογωνίου, μέχρι τη διαμόρφωση μιας εξωτερικής σκιάς με διαφάνεια. Στο τέλος θα έχετε ένα έτοιμο προς χρήση `Shadow.docx` που μπορείτε να ανοίξετε στο Word και να δείτε το αποτέλεσμα άμεσα. Χωρίς εξωτερικά εργαλεία, χωρίς πολύπλοκο XML—μόνο καθαρός κώδικας C# και σαφείς εξηγήσεις.

## Τι Θα Μάθετε

- **Πώς να δημιουργήσετε shape** objects in a Word document using Aspose.Words.
- **Πώς να προσθέσετε rectangle shape** to a paragraph without messing up existing content.
- **Πώς να προσθέσετε shadow** (outer shadow) and control its color, offset, blur, and transparency.
- **Πώς να ορίσετε transparency** on the shadow so it looks professional.
- Συμβουλές, παγίδες και παραλλαγές που μπορεί να χρειαστείτε σε πραγματικά έργα.

### Προαπαιτούμενα

- .NET 6.0 ή νεότερο (το API λειτουργεί επίσης με .NET Framework 4.6+).
- Aspose.Words for .NET εγκατεστημένο μέσω NuGet (`Install-Package Aspose.Words`).
- Βασική κατανόηση της σύνταξης C#—τίποτα περίπλοκο, μόνο οι συνήθεις δηλώσεις `using` και η δημιουργία αντικειμένων.

> **Pro tip:** Αν χρησιμοποιείτε Visual Studio, ενεργοποιήστε τα “nullable reference types” για να εντοπίζετε έγκαιρα πιθανά σφάλματα null‑reference.

## Βήμα 1 – Δημιουργία Κεντρικού Εγγράφου Word

Για να **δημιουργήσετε έγγραφο Word** ξεκινάμε με την κλάση `Document`. Σκεφτείτε το ως έναν κενό καμβά· μπορείτε αργότερα να προσθέσετε ενότητες, παραγράφους, πίνακες ή σχήματα.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Initialize a new blank document
Document document = new Document();
```

Γιατί χρειάζεστε μια νέα παρουσία του `Document`; Επειδή κάθε shape, παράγραφος ή στυλ ζει μέσα σε ένα document object model (DOM). Ξεκινώντας με ένα καθαρό έγγραφο εξασφαλίζει ότι το ορθογώνιο που θα προσθέσετε δεν θα επηρεάσει το υπάρχον περιεχόμενο.

## Βήμα 2 – Ορισμός του Σχήματος Ορθογωνίου

Τώρα **πώς να δημιουργήσετε shape** ένα ορθογώνιο. Ο κατασκευαστής `Shape` λαμβάνει το έγγραφο ιδιοκτήτη και τον τύπο του σχήματος. Επίσης ορίζουμε το πλάτος και το ύψος του σε points (1 pt ≈ 1/72 in).

```csharp
// Create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width = 200;   // 200 pt ≈ 2.78 in
rectangleShape.Height = 100; // 100 pt ≈ 1.39 in
```

Μπορεί να αναρωτηθείτε, «Μπορώ να χρησιμοποιήσω εκατοστά αντί για points;» Το API δέχεται μόνο points, αλλά μπορείτε να μετατρέψετε: `points = centimeters * 28.35`. Αυτή η μικρή μετατροπή είναι χρήσιμη όταν ευθυγραμμίζετε σχήματα με τα περιθώρια της σελίδας.

## Βήμα 3 – Προσθήκη Εξωτερικής Σκιάς και Ορισμός Διαφάνειας

Εδώ συμβαίνει η μαγεία: **πώς να προσθέσετε shadow** και **πώς να ορίσετε transparency** σε αυτή τη σκιά. Η ιδιότητα `ShadowFormat` σας δίνει πλήρη έλεγχο.

```csharp
// Enable shadow visibility
rectangleShape.ShadowFormat.Visible = true;

// Choose a shadow color
rectangleShape.ShadowFormat.Color = System.Drawing.Color.DarkGray;

// Set transparency (0 = opaque, 1 = fully transparent)
rectangleShape.ShadowFormat.Transparency = 0.3; // 30 % transparent

// Position the shadow relative to the shape
rectangleShape.ShadowFormat.OffsetX = 5; // horizontal offset in points
rectangleShape.ShadowFormat.OffsetY = 5; // vertical offset in points

// Blur makes the shadow look softer
rectangleShape.ShadowFormat.BlurRadius = 4;

// Specify that this is an outer shadow (instead of inner)
rectangleShape.ShadowFormat.Style = ShadowStyle.OuterShadow;
```

**Γιατί αυτές οι ρυθμίσεις;**  
- **Transparency** επιτρέπει στην υφή της σελίδας να φαίνεται, αποτρέποντας τη σκιά να φαίνεται πολύ βαριά.  
- **OffsetX/Y** δημιουργούν την ψευδαίσθηση ότι το σχήμα είναι ανυψωμένο από τη σελίδα.  
- **BlurRadius** μαλακώνει τις άκρες—χωρίς αυτό η σκιά θα ήταν ένα σκληρό ορθογώνιο, που φαίνεται αφύσικο.

Αν χρειάζεστε πιο δραματικό αποτέλεσμα, αυξήστε το `OffsetX/Y` στα 10 και αυξήστε το `BlurRadius` στα 8. Αντίστροφα, για μια διακριτική υπόδειξη, κρατήστε τα στα 2 και 2 αντίστοιχα.

## Βήμα 4 – Εισαγωγή του Σχήματος στο Έγγραφο

Τώρα **προσθέτουμε rectangle shape** στην πρώτη παράγραφο του εγγράφου. Αν το έγγραφο δεν έχει περιεχόμενο, το `FirstParagraph` δημιουργείται αυτόματα για εσάς.

```csharp
// Append the rectangle to the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

Τι γίνεται αν θέλετε το σχήμα μέσα σε συγκεκριμένο κελί πίνακα ή σε μεταγενέστερη παράγραφο; Απλώς εντοπίστε το κόμβο (`doc.GetChild(NodeType.Paragraph, index, true)`) και καλέστε `AppendChild` σε αυτόν. Το ίδιο αντικείμενο shape μπορεί να κλωνοποιηθεί αν χρειάζεστε πολλαπλά αντίγραφα.

## Βήμα 5 – Αποθήκευση του Εγγράφου

Τέλος, **δημιουργούμε έγγραφο word** στο δίσκο. Χρησιμοποιήστε μια διαδρομή που ταιριάζει στο περιβάλλον σας· το παράδειγμα χρησιμοποιεί ένα placeholder.

```csharp
// Save the document as a .docx file
document.Save(@"YOUR_DIRECTORY/Shadow.docx");
```

Όταν ανοίξετε το `Shadow.docx` στο Microsoft Word, θα δείτε ένα ανοιχτό-γκρι ορθογώνιο με μια ήπια εξωτερική σκιά μετατοπισμένη προς τα κάτω‑δεξιά. Η διαφάνεια της σκιάς 30 % εξασφαλίζει ότι δεν κυριαρχεί στη σελίδα.

![Δημιουργία εγγράφου Word με σχήμα ορθογωνίου με σκιά](image.png "Δημιουργία εγγράφου Word με σχήμα ορθογωνίου με σκιά")

*Κείμενο εναλλακτικής εικόνας: δημιουργία εγγράφου word με σχήμα ορθογωνίου με σκιά*

## Πλήρης, Έτοιμος‑για‑Εκτέλεση Κώδικας

Παρακάτω βρίσκεται το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε‑επικολλήσετε σε μια εφαρμογή console. Χωρίς ελλιπή μέρη, χωρίς “δείτε την τεκμηρίωση για περισσότερα”.

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

        // Step 2: Add a rectangular shape and define its size
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width = 200;   // width in points
        rectangleShape.Height = 100;  // height in points

        // Step 3: Configure an outer shadow for the shape
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = System.Drawing.Color.DarkGray;
        rectangleShape.ShadowFormat.Transparency = 0.3;   // 30 % transparent
        rectangleShape.ShadowFormat.OffsetX = 5;          // horizontal offset
        rectangleShape.ShadowFormat.OffsetY = 5;          // vertical offset
        rectangleShape.ShadowFormat.BlurRadius = 4;
        rectangleShape.ShadowFormat.Style = ShadowStyle.OuterShadow;

        // Step 4: Insert the shape into the first paragraph of the document
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // Step 5: Save the document with the shadowed shape
        document.Save(@"YOUR_DIRECTORY/Shadow.docx");

        Console.WriteLine("Word document created successfully at YOUR_DIRECTORY/Shadow.docx");
    }
}
```

### Αναμενόμενο Αποτέλεσμα

- Ένα αρχείο με όνομα **Shadow.docx** εμφανίζεται στον φάκελο προορισμού.
- Ανοίγοντάς το στο Word εμφανίζεται ένα ορθογώνιο (200 × 100 pt) με σκούρο‑γκρι εξωτερική σκιά.
- Η σκιά είναι μετατοπισμένη κατά 5 pt οριζόντια και κάθετα, θολή, και 30 % διαφανής.

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

| Question | Answer |
|----------|--------|
| **Μπορώ να αλλάξω το χρώμα της σκιάς ώστε να ταιριάζει με το brand μου;** | Απολύτως—απλώς αντικαταστήστε το `System.Drawing.Color.DarkGray` με οποιοδήποτε `Color` προτιμάτε, π.χ., `Color.FromArgb(255, 0, 120, 215)` για μια μπλε απόχρωση. |
| **Τι γίνεται αν χρειάζομαι εσωτερική σκιά αντί για εξωτερική;** | Ορίστε `ShadowFormat.Style = ShadowStyle.InnerShadow`. Οι υπόλοιπες ιδιότητες λειτουργούν με τον ίδιο τρόπο. |
| **Υποστηρίζεται η διαφάνεια σε παλαιότερες εκδόσεις του Word;** | Ναι. Το Aspose.Words γράφει το κατάλληλο XML που καταλαβαίνει το Word 2007+. Οι παλαιότερες εκδόσεις μπορεί να αγνοήσουν την τιμή διαφάνειας αλλά θα εμφανίσουν τη σκιά. |
| **Μπορώ να προσθέσω πολλαπλά σχήματα με διαφορετικές σκιές;** | Φυσικά—απλώς δημιουργήστε νέες εμφανίσεις `Shape`, διαμορφώστε κάθε σκιά ανεξάρτητα, και προσθέστε τις στους επιθυμητούς κόμβους. |
| **Τι γίνεται με την απόδοση όταν υπάρχουν εκατοντάδες σχήματα;** | Η δημιουργία πολλών σχημάτων μπορεί να αυξήσει τη χρήση μνήμης. Επαναχρησιμοποιήστε μια μοναδική παρουσία `Document` και προσθέστε σχήματα σε βρόχο· απελευθερώστε προσωρινά αντικείμενα αν αντιμετωπίσετε πίεση. |

## Συμβουλές για Πραγματικά Έργα

- **Δημιουργία σε παρτίδες:** Κατά τη δημιουργία αναφορών για πολλούς χρήστες, δημιουργήστε ένα μοναδικό πρότυπο `Document` και κλωνοποιήστε το για κάθε επανάληψη. Αντικαταστήστε τα placeholders πριν προσθέσετε σχήματα.
- **Δυναμικό μέγεθος:** Χρησιμοποιήστε τις διαστάσεις της σελίδας (`document.FirstSection.PageSetup.PageWidth`) για να υπολογίσετε το μέγεθος του σχήματος σε σχέση με τη σελίδα, εξασφαλίζοντας συνεπή διάταξη σε διαφορετικά μεγέθη χαρτιού.
- **Δοκιμή:** Ανοίξτε πάντα το παραγόμενο `.docx` στο Word μετά από αλλαγή στις παραμέτρους της σκιάς. Η οπτική ανατροφοδότηση είναι πιο γρήγορη από το να μαντεύετε αριθμούς.

## Επόμενα Βήματα

Τώρα που γνωρίζετε **πώς να προσθέσετε rectangle shape**, **πώς να προσθέσετε shadow**, και **πώς να ορίσετε transparency**, σκεφτείτε να εξερευνήσετε:

- Προσθήκη **gradient fills** σε σχήματα (`Shape.FillFormat`).
- Ενσωμάτωση **pictures** μέσα σε σχήματα για εφέ υδατογραφήματος.
- Χρήση **tables** για ευθυγράμμιση πολλαπλών σχημάτων με σκιά σε πλέγμα.
- Εξαγωγή του ίδιου εγγράφου σε PDF (`document.Save("output.pdf")`) διατηρώντας τις σκιές.

Κάθε ένα από αυτά βασίζεται στις ίδιες βασικές έννοιες, έτσι θα νιώσετε άνετα να επεκτείνετε τον κώδικα.

### Περίληψη

Ξεκινήσαμε με **δημιουργήσετε έγγραφο word** με Aspose.Words, μετά **πώς να δημιουργήσετε shape** ένα ορθογώνιο, εφαρμόσαμε **πώς να προσθέσετε shadow**, ρυθμίσαμε **πώς να ορίσετε transparency**, και αποθηκεύσαμε το αποτέλεσμα. Ολόκληρη η διαδικασία ταιριάζει σε ένα συμπαγές, επαναχρησιμοποιήσιμο μοτίβο που μπορείτε να προσαρμόσετε σε οποιοδήποτε σενάριο αυτοματοποίησης.

Νιώστε ελεύθεροι να πειραματιστείτε—αλλάξτε χρώματα, παίξτε με τις μετατοπίσεις, ή στοιβάξτε πολλά σχήματα μαζί. Όταν αντιμετωπίσετε πρόβλημα, επιστρέψτε στις παραπάνω ενότητες· έχουν σχεδιαστεί ως γρήγορη αναφορά. Καλή προγραμματιστική, και εύχομαι τα έγγραφά σας να είναι πάντα άψογα!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}