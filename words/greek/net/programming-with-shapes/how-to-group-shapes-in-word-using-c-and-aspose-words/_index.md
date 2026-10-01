---
category: general
date: 2026-09-30
description: Ομαδοποίηση σχημάτων στο Word με C# – μάθετε πώς να ομαδοποιείτε σχήματα,
  να προσθέτετε ορθογώνιο και έλλειψη, και να εισάγετε σχήμα ορθογωνίου σε έγγραφα
  Word προγραμματιστικά.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- how to add rectangle
- how to add ellipse
- insert rectangle shape word
language: el
lastmod: 2026-09-30
og_description: Ομαδοποίηση σχημάτων στο Word χρησιμοποιώντας C# και Aspose.Words.
  Ακολουθήστε αυτόν τον πλήρη οδηγό για να προσθέσετε ορθογώνιο, να προσθέσετε έλλειψη
  και να μάθετε πώς να ομαδοποιείτε τα σχήματα αποδοτικά.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape
og_title: Ομαδοποίηση σχημάτων στο Word με C# – βήμα‑βήμα οδηγός
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: group shapes in Word with C# – learn how to group shapes, add rectangle
    and ellipse, and insert rectangle shape Word documents programmatically.
  headline: How to group shapes in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Πώς να ομαδοποιήσετε σχήματα στο Word χρησιμοποιώντας C# και Aspose.Words
url: /el/net/programming-with-shapes/how-to-group-shapes-in-word-using-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να ομαδοποιήσετε σχήματα στο Word χρησιμοποιώντας C# και Aspose.Words

Αν χρειάζεστε **ομαδοποίηση σχημάτων στο Word** προγραμματιστικά, αυτός ο οδηγός σας δείχνει ακριβώς πώς. Θα δείτε πώς να προσθέσετε ένα ορθογώνιο, ένα έλλειψο και στη συνέχεια να τα συνδυάσετε σε ένα ενιαίο ομαδικό σχήμα χρησιμοποιώντας τη βιβλιοθήκη Aspose.Words για .NET.

Η εργασία με σχήματα είναι συχνή απαίτηση όταν δημιουργείτε αυτόματα αναφορές, συμβόλαια ή υλικό μάρκετινγκ. Στο τέλος αυτού του tutorial θα έχετε μια επαναχρησιμοποιήσιμη μέθοδο C# που φορτώνει ένα αρχείο DOCX, εισάγει ένα ορθογώνιο και ένα έλλειψο, τα ομαδοποιεί και αποθηκεύει το αποτέλεσμα—όλα χωρίς να ανοίξετε το Word χειροκίνητα.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* .NET 6.0 SDK ή νεότερη έκδοση εγκατεστημένη  
* Περιβάλλον ανάπτυξης όπως το Visual Studio 2022 (η έκδοση Community λειτουργεί)  
* Άδεια Aspose.Words για .NET ή μια δωρεάν έκδοση αξιολόγησης (το API λειτουργεί χωρίς άδεια αλλά προσθέτει υδατογράφημα)  

Χρειάζεστε επίσης ένα πηγαίο έγγραφο Word (`input.docx`) σε φάκελο που μπορείτε να αναφέρετε από τον κώδικα. Το έγγραφο μπορεί να είναι κενό· το tutorial εστιάζει στη διαχείριση σχημάτων.

## Βήμα 1: Δημιουργία νέου έργου console και προσθήκη Aspose.Words

Ανοίξτε ένα τερματικό ή το command prompt του Visual Studio και εκτελέστε:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

Αυτό δημιουργεί μια νέα εφαρμογή console με όνομα **WordShapeDemo** και προσθέτει το πακέτο NuGet `Aspose.Words`, το οποίο περιέχει τις κλάσεις `Document` και `DocumentBuilder` που χρησιμοποιούνται για την επεξεργασία αρχείων Word.

## Βήμα 2: Φόρτωση ή δημιουργία εγγράφου

Η πρώτη ενέργεια όταν δουλεύετε με **ομαδικά σχήματα στο Word** είναι η απόκτηση ενός αντικειμένου `Document`. Μπορείτε είτε να φορτώσετε ένα υπάρχον αρχείο DOCX είτε να ξεκινήσετε από ένα κενό έγγραφο.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Load an existing document (replace the path with your own)
        Document document = new Document(@"YOUR_DIRECTORY\input.docx");

        // If you prefer a brand‑new document, uncomment the next line:
        // Document document = new Document();
```

Η κλάση `Document` αντιπροσωπεύει ολόκληρο το αρχείο Word. Η φόρτωση ενός αρχείου σας παρέχει έναν έτοιμο καμβά για την εισαγωγή σχημάτων.

## Βήμα 3: Έναρξη ομαδικού σχήματος

Ένα *ομαδικό σχήμα* σας επιτρέπει να αντιμετωπίζετε πολλά ανεξάρτητα σχήματα ως μία ενιαία μονάδα—ιδανικό για μετακίνηση ή αλλαγή μεγέθους τους μαζί. Για να ξεκινήσετε μια ομάδα, καλέστε `StartGroupShape()` σε ένα `DocumentBuilder`.

```csharp
        // Create a builder to edit the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Begin a group shape that will contain multiple shapes
        builder.StartGroupShape();
```

Η κλήση του `StartGroupShape` ενημερώνει το Aspose.Words ότι κάθε επόμενη εισαγωγή σχήματος ανήκει στην ίδια λογική ομάδα μέχρι να καλέσετε `EndGroupShape`.

## Βήμα 4: Πώς να προσθέσετε σχήμα ορθογωνίου στο Word

Τώρα που η ομάδα είναι ανοιχτή, εισάγετε ένα ορθογώνιο. Η μέθοδος `InsertShape` δέχεται μια παράμετρο enum `ShapeType`, ακολουθούμενη από το πλάτος και το ύψος (σε points).

```csharp
        // Add a rectangle shape to the group (100 pt wide, 50 pt high)
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

Το ορθογώνιο γίνεται το πρώτο μέλος της ομάδας. Μπορείτε να προσαρμόσετε το γέμισμα, το περίγραμμα ή το κείμενο αργότερα, αν χρειαστεί.

## Βήμα 5: Πώς να προσθέσετε σχήμα έλλειψης στο Word

Στη συνέχεια, προσθέστε ένα έλλειψο (κύκλο όταν το πλάτος ισούται με το ύψος). Αυτό δείχνει **πώς να προσθέσετε έλλειψο** χρησιμοποιώντας τον ίδιο builder.

```csharp
        // Add an ellipse shape to the same group (80 pt wide, 80 pt high)
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

Και τα δύο σχήματα μοιράζονται πλέον τον ίδιο χώρο συντεταγμένων μέσα στην ομάδα, καθιστώντας εύκολη την οπτική τους ευθυγράμμιση.

## Βήμα 6: Κλείσιμο του ορισμού ομαδικού σχήματος

Όταν έχετε προσθέσει όλα τα επιθυμητά μέλη, κλείστε την ομάδα. Αυτό ολοκληρώνει τη συλλογή σχημάτων ώστε το Word να τα αντιμετωπίζει ως ένα αντικείμενο.

```csharp
        // End the group shape definition
        builder.EndGroupShape();
```

Σε αυτό το σημείο το έγγραφο περιέχει ένα ενιαίο ομαδικό σχήμα που αποτελείται από ένα ορθογώνιο και ένα έλλειψο.

## Βήμα 7: Αποθήκευση του τροποποιημένου εγγράφου

Τέλος, γράψτε τις αλλαγές στο δίσκο. Μπορείτε να αντικαταστήσετε το αρχικό αρχείο ή να δημιουργήσετε ένα νέο.

```csharp
        // Save the document with the grouped shapes
        document.Save(@"YOUR_DIRECTORY\output.docx");

        Console.WriteLine("Document saved with grouped shapes.");
    }
}
```

Η εκτέλεση του προγράμματος παράγει το `output.docx`. Ανοίξτε το αρχείο στο Microsoft Word, επιλέξτε το σχήμα και θα δείτε ότι το ορθογώνιο και το έλλειψο μετακινούνται μαζί—απόδειξη ότι η λειτουργία **ομαδοποίησης σχημάτων στο Word** ολοκληρώθηκε επιτυχώς.

### Αναμενόμενο αποτέλεσμα

* Το αρχείο Word περιέχει ένα ενιαίο ομαδικό αντικείμενο.  
* Η επιλογή της ομάδας σας επιτρέπει να σύρετε, να αλλάξετε μέγεθος ή να περιστρέψετε ταυτόχρονα τόσο το ορθογώνιο όσο και το έλλειψο.  
* Δεν απαιτείται χειροκίνητη αλληλεπίδραση με το Word· όλα γίνονται μέσω κώδικα C#.

![Grouped shapes in Word document](grouped-shapes.png "Screenshot of a Word document showing a grouped rectangle and ellipse shape")

*Image alt text: “Screenshot of a Word document showing a grouped rectangle and ellipse shape”* (πληροί την απαίτηση για alt‑text εικόνας).

## Γιατί η ομαδοποίηση σχημάτων είναι σημαντική

Η ομαδοποίηση σχημάτων είναι περισσότερο από μια οπτική ευκολία. Σας επιτρέπει να:

* **Διατηρείτε τη συνοχή της διάταξης** – η μετακίνηση μιας ομάδας διατηρεί τις σχετικές θέσεις αμετάβλητες.  
* **Εφαρμόζετε μετασχηματισμούς μία φορά** – περιστρέψτε ή κλιμακώστε ολόκληρη την ομάδα αντί για κάθε σχήμα ξεχωριστά.  
* **Απλοποιείτε την επεξεργασία downstream** – όταν άλλα εργαλεία διαβάζουν το DOCX, βλέπουν ένα ενιαίο σύνθετο σχήμα, μειώνοντας την πολυπλοκότητα.

Αν χρειαστεί ποτέ να προσθέσετε περισσότερα σχήματα (π.χ. μια γραμμή ή ένα πλαίσιο κειμένου) στην ίδια λογική μονάδα, αρκεί να καλέσετε ξανά το `InsertShape` πριν το `EndGroupShape`.

## Συνηθισμένες παραλλαγές και ειδικές περιπτώσεις

| Situation | How to handle it |
|-----------|-----------------|
| **Different units** – you have measurements in centimeters | Convert centimeters to points (`1 cm ≈ 28.35 pt`) before calling `InsertShape`. |
| **Adding a text label** – you want a caption inside the group | Insert a `ShapeType.TextBox` after the rectangle and ellipse, then set its `Text` property. |
| **Applying a fill color** – you need a blue rectangle | After `InsertShape`, retrieve the last shape via `builder.CurrentParagraph.Runs[0].Font` and set `shape.FillColor = System.Drawing.Color.Blue;`. |
| **Using a different document format** – you target `.doc` instead of `.docx` | The same code works; just change the file extension when calling `Save`. Aspose.Words automatically handles the format. |

## Pro tips

* **Reuse the builder** – μπορείτε να ξεκινάτε και να κλείνετε πολλαπλές ομάδες στο ίδιο έγγραφο· απλώς καλέστε ξανά το `StartGroupShape` μετά το `EndGroupShape`.  
* **Performance** – η μαζική εισαγωγή σχημάτων μέσα σε ένα ενιαίο μπλοκ `StartGroupShape/EndGroupShape` είναι ταχύτερη από την εισαγωγή σχημάτων ξεχωριστά εκτός ομάδας.  
* **Licensing** – μια άδεια αξιολόγησης προσθέτει υδατογράφημα στην πρώτη σελίδα. Εγκαταστήστε μια πλήρη άδεια για να το αφαιρέσετε σε παραγωγικά περιβάλλοντα.

## Συμπέρασμα

Τώρα ξέρετε πώς να **ομαδοποιήσετε σχήματα στο Word** με C#, πώς να **προσθέσετε ορθογώνιο**, πώς να **προσθέσετε έλλειψο**, και πώς να **εισάγετε σχήμα ορθογωνίου σε έγγραφα Word** χρησιμοποιώντας το Aspose.Words. Το πλήρες, εκτελέσιμο παράδειγμα δείχνει κάθε βήμα από τη ρύθμιση του έργου μέχρι την αποθήκευση του τελικού αρχείου.

Από εδώ μπορείτε να εξερευνήσετε πρόσθετους τύπους σχημάτων, να εφαρμόσετε στυλ ή να συνδυάσετε ομαδοποιημένα σχήματα με πίνακες και εικόνες για τη δημιουργία πολύπλοκων, προγραμματιστικά παραγόμενων εγγράφων.

---

**Επόμενα βήματα**

* Μάθετε πώς να **περιστρέφετε ομαδοποιημένα σχήματα**: χρησιμοποιήστε το `Shape.RotationAngle` μετά το κλείσιμο της ομάδας.  
* Εξερευνήστε **προσαρμογή γεμίσματος και περιγράμματος** για ορθογώνια και έλλειψη.  
* Ενσωματώστε αυτή τη λογική σε ένα API ASP.NET Core για τη δημιουργία αναφορών κατ' απαίτηση.  

Καλή προγραμματιστική δημιουργία!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στην δική σας υλοποίηση.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Rectangle Shape in Word – Full Aspose.Words Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}