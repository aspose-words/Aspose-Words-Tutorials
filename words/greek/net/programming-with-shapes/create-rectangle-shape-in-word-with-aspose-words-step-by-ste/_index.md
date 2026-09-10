---
category: general
date: 2025-12-29
description: Δημιουργήστε σχήμα ορθογωνίου σε ένα έγγραφο Word χρησιμοποιώντας το
  Aspose.Words C#. Μάθετε πώς να ορίζετε τη διαφάνεια του σχήματος, το χρώμα της σκιάς
  και να αποθηκεύετε το έγγραφο Word χωρίς κόπο.
draft: false
keywords:
- create rectangle shape
- set shape transparency
- set shadow color
- save word document
- create word document
language: el
og_description: Δημιουργήστε σχήμα ορθογωνίου σε έγγραφο Word με το Aspose.Words C#.
  Αυτός ο οδηγός δείχνει πώς να ορίσετε τη διαφάνεια του σχήματος, να ορίσετε το χρώμα
  της σκιάς και να αποθηκεύσετε το έγγραφο Word.
og_title: Δημιουργία σχήματος ορθογωνίου στο Word – Πλήρες σεμινάριο Aspose.Words
tags:
- Aspose.Words
- C#
- Word Automation
title: Δημιουργία σχήματος ορθογωνίου στο Word με το Aspose.Words – Οδηγός βήμα‑προς‑βήμα
url: /el/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία σχήματος ορθογωνίου στο Word – Πλήρης Οδηγός Aspose.Words

Κάποτε χρειάστηκε να **δημιουργήσετε σχήμα ορθογωνίου** σε ένα έγγραφο Word αλλά δεν ήξερατε από πού να ξεκινήσετε; Δεν είστε μόνοι· πολλοί προγραμματιστές αντιμετωπίζουν αυτό το εμπόδιο όταν αυτοματοποιούν αναφορές ή τιμολόγια. Σε αυτόν τον οδηγό θα περάσουμε βήμα‑βήμα από τη δημιουργία του σχήματος, τη ρύθμιση της διαφάνειας, το χρώμα της σκιάς και, τέλος, την **αποθήκευση του εγγράφου Word** χρησιμοποιώντας το Aspose.Words για .NET.

Θα καλύψουμε τα πάντα, από το αρχικό αντικείμενο Document μέχρι το τελικό αρχείο `.docx` στο δίσκο, ώστε στο τέλος να μπορείτε να **δημιουργήσετε έγγραφο Word** προγραμματιστικά χωρίς εικασίες. Χωρίς εξωτερικές αναφορές, μόνο μια αυτόνομη λύση που μπορείτε να αντιγράψετε‑επικολλήσετε στο έργο σας.

## Προαπαιτούμενα

- .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.7+)
- Πακέτο NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)
- Βασική εξοικείωση με τη σύνταξη C#
- Ένα IDE της επιλογής σας (Visual Studio, Rider, VS Code κ.λπ.)

> **Pro tip:** Αν χρησιμοποιείτε δωρεάν δοκιμαστική έκδοση του Aspose.Words, η βιβλιοθήκη θα προσθέσει υδατογράφημα στο αρχείο εξόδου. Για παραγωγή θα χρειαστείτε έγκυρη άδεια.

## Βήμα 1: Αρχικοποίηση του Document και του Builder

Το πρώτο που κάνουμε είναι να δημιουργήσουμε ένα νέο, κενό έγγραφο Word και έναν `DocumentBuilder` που μας επιτρέπει την εισαγωγή περιεχομένου. Σκεφτείτε τον builder ως ένα εικονικό στυλό που σχεδιάζει στη σελίδα.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();

// The builder provides methods to add text, tables, shapes, etc.
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Why this matters:** Χωρίς έναν `DocumentBuilder` θα έπρεπε να χειρίζεστε το δέντρο κόμβων χαμηλού επιπέδου απευθείας, κάτι που είναι επιρρεπές σε σφάλματα και πιο δύσκολο στην ανάγνωση.

## Βήμα 2: Δημιουργία σχήματος ορθογωνίου

Τώρα δημιουργούμε πραγματικά **σχήμα ορθογωνίου**. Η μέθοδος `InsertShape` δέχεται μια τιμή του enum `ShapeType`, πλάτος και ύψος (σε points). Το αντικείμενο `Shape` που επιστρέφεται μας επιτρέπει να ρυθμίσουμε οπτικές ιδιότητες αργότερα.

```csharp
// Insert a rectangle 150 pts wide and 80 pts tall
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

Σε αυτό το σημείο το ορθογώνιο είναι ένα συμπαγές μαύρο κουτί που είναι δεσμευμένο στην τρέχουσα παράγραφο. Μπορείτε να το μετακινήσετε, να αλλάξετε το μέγεθός του ή ακόμη και να το περιστρέψετε αργότερα αν χρειαστεί.

![δημιουργία σχήματος ορθογωνίου με σκιά](/images/rectangle-shadow.png "Έγγραφο Word που εμφανίζει σχήμα ορθογωνίου με γκρι σκιά")

*Image alt text: δημιουργία σχήματος ορθογωνίου με σκιά σε έγγραφο Word*

## Βήμα 3: Ρύθμιση διαφάνειας σχήματος

Η διαφάνεια είναι το επίπεδο «διάφανο‑πέρασμα» του γεμίσματος του σχήματος. Το Aspose.Words χρησιμοποιεί την ιδιότητα `Transparency` με τιμές από `0.0` (αδιαφανές) έως `1.0` (πλήρως διαφανές). Εδώ **ρυθμίζουμε τη διαφάνεια του σχήματος** στο 40 % ώστε το κείμενο κάτω να παραμένει αναγνώσιμο.

```csharp
// Make the rectangle 40 % transparent
rectangleShape.Fill.Transparency = 0.4; // 0.0 = opaque, 1.0 = invisible
```

> **Edge case:** Αν χρειάζεστε ένα εντελώς αόρατο σχήμα αλλά θέλετε να εμφανίζεται η σκιά, ορίστε `Transparency` στο `1.0` και δώ στο σχήμα μη‑μηδενικό πάχος περιγράμματος.

## Βήμα 4: Διαμόρφωση της σκιάς

Μια διακριτική σκιά προσθέτει βάθος. Θα **ορίσουμε το χρώμα της σκιάς** σε μεσαίο γκρι, θα ρυθμίσουμε την ακτίνα θολώματος και θα τοποθετήσουμε την σκιά με μερικά points οριζόντια και κάθετα.

```csharp
// Enable the shadow effect
rectangleShape.Shadow.Enabled = true;

// Shadow color – a neutral gray
rectangleShape.Shadow.Color = System.Drawing.Color.Gray;

// 40 % transparent shadow (same as shape's fill)
rectangleShape.Shadow.Transparency = 0.4;

// Blur radius makes the edge softer
rectangleShape.Shadow.Blur = 6;

// Horizontal and vertical offsets (in points)
rectangleShape.Shadow.OffsetX = 5;
rectangleShape.Shadow.OffsetY = 5;
```

> **Why this matters:** Μια σκιά που είναι πολύ οξεία ή πολύ σκοτεινή μπορεί να μοιάζει με ελάττωμα εκτύπωσης. Ρυθμίστε το `Blur` και τη `Transparency` μέχρι να φαίνεται φυσική.

## Βήμα 5: Αποθήκευση του εγγράφου Word

Τέλος **αποθηκεύουμε το έγγραφο Word** στον δίσκο. Η μέθοδος `Save` καθορίζει αυτόματα τη μορφή αρχείου από την επέκταση· το `.docx` είναι η σύγχρονη μορφή OpenXML.

```csharp
// Save the document to the desired folder
document.Save(@"C:\Temp\ShadowRectangle.docx");
```

Αν ο φάκελος δεν υπάρχει, το Aspose.Words θα πετάξει `ArgumentException`. Βεβαιωθείτε ότι η διαδρομή είναι έγκυρη ή δημιουργήστε το φάκελο εκ των προτέρων.

## Πλήρες Παράδειγμα Εργασίας

Παρακάτω είναι το πλήρες, έτοιμο‑για‑εκτέλεση πρόγραμμα που συνδυάζει όλα τα βήματα. Αντιγράψτε το σε ένα νέο έργο κονσόλας και πατήστε **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace AsposeRectangleDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Initialize document and builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert rectangle shape
            Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Set shape transparency (40 % transparent)
            rectangleShape.Fill.Transparency = 0.4;

            // 4️⃣ Configure shadow (color, blur, offset, transparency)
            rectangleShape.Shadow.Enabled = true;
            rectangleShape.Shadow.Color = System.Drawing.Color.Gray;
            rectangleShape.Shadow.Transparency = 0.4;
            rectangleShape.Shadow.Blur = 6;
            rectangleShape.Shadow.OffsetX = 5;
            rectangleShape.Shadow.OffsetY = 5;

            // 5️⃣ Save the document
            string outputPath = @"C:\Temp\ShadowRectangle.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Αναμενόμενο αποτέλεσμα

Ανοίξτε το `ShadowRectangle.docx` στο Microsoft Word. Θα πρέπει να δείτε ένα ανοιχτό‑γκρι ορθογώνιο με μια ήπια, ελαφρώς μετατοπισμένη σκιά, και όλα τα στοιχεία να είναι σε 40 % διαφάνεια. Το σχήμα βρίσκεται σε μια κενή σελίδα, έτοιμο για επιπλέον περιεχόμενο.

## Συχνές Ερωτήσεις Παραλλαγές

**Τι γίνεται αν χρειάζομαι διαφορετικό σχήμα;**  
Αντικαταστήστε το `ShapeType.Rectangle` με οποιαδήποτε άλλη τιμή του enum (`Ellipse`, `Triangle`, `Star`, κ.λπ.). Το υπόλοιπο του κώδικα παραμένει ίδιο.

**Μπορώ να αλλάξω το χρώμα του περιγράμματος;**  
Ναι—χρησιμοποιήστε `rectangleShape.StrokeColor = System.Drawing.Color.Blue;` και προαιρετικά ορίστε `rectangleShape.StrokeWeight = 1.5;`.

**Πώς τοποθετώ το σχήμα σε συγκεκριμένη θέση στη σελίδα;**  
Ορίστε `rectangleShape.WrapType = WrapType.None;` και στη συνέχεια προσαρμόστε τιςιότητες `rectangleShape.Left` και `rectangleShape.Top` (τιμές σε points).

**Μπορεί να προστεθεί κείμενο μέσα στο ορθογώνιο;**  
Απόλυτα. Μετά τη δημιουργία του σχήματος, μπορείτε να καλέσετε `rectangleShape.AppendChild(new Paragraph(document))` και μετά να προσθέσετε ένα `Run` με το κείμενό σας. Θυμηθείτε να ορίσετε τις ιδιότητες `rectangleShape.TextBox` αν θέλετε πιο πλούσια μορφοποίηση.

## Pro Tips & Pitfalls

- **License early:** Αν ξεχάσετε να εφαρμόσετε άδεια, το Aspose.Words θα εισάγει υδατογράφημα στην πρώτη σελίδα, κάτι που μπορεί να προκαλέσει σύγχυση κατά τη δοκιμή.
- **Performance tip:** Όταν δημιουργείτε πολλά έγγραφα σε βρόχο, επαναχρησιμοποιήστε ένα μόνο αντικείμενο `Document` και καλέστε `document.RemoveAllChildren();` μετά από κάθε αποθήκευση για να αποφύγετε υπερβολική πίεση στο GC.
- **Shadow visibility:** Σε οθόνες χαμηλής ανάλυσης μια διακριτική σκιά μπορεί να φαίνεται αόρατη. Αυξήστε το `Blur` ή τα `OffsetX/Y` για εντοπισμό σφαλμάτων, μετά μειώστε τα για παραγωγή.

## Επόμενα Βήματα

Τώρα που ξέρετε πώς να **δημιουργήσετε σχήμα ορθογωνίου**, **ρυθμίσετε τη διαφάνεια του σχήματος**, **ορίσετε το χρώμα της σκιάς** και **αποθηκεύσετε το έγγραφο Word**, σκεφτείτε να επεκτείνετε τον οδηγό:

- Προσθέστε πολλαπλά σχήματα και ομαδοποιήστε τα.
- Εισάγετε το ορθογώνιο μέσα σε κελί πίνακα για διάταξη αναφοράς.
- Συνδυάστε το σχήμα με `DocumentBuilder.InsertHtml` για επικάλυψη περιεχομένου HTML‑styled.
- Εξερευνήστε άλλα οπτικά εφέ όπως `Glow` ή `Reflection` για πιο πλούσια έγγραφα τύπου UI.

Πειραματιστείτε, σπάστε πράγματα, και μετά βελτιώστε—η προγραμματιστική δημιουργία εγγράφων είναι ένα εργαστήριο όπου ο οπτικός σχεδιασμός συναντά τον κώδικα.

---

*Καλή προγραμματιστική! Αν αντιμετωπίσατε κάποιο πρόβλημα, αφήστε ένα σχόλιο παρακάτω και θα το λύσουμε μαζί.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}