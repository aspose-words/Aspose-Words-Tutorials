---
category: general
date: 2026-03-01
description: Προσθέστε γρήγορα ορθογώνιο σε PDF χρησιμοποιώντας το Aspose.Words. Μάθετε
  πώς να εισάγετε σχήμα σε PDF, να προσθέτετε γραφικά σε PDF και να δημιουργείτε έγγραφο
  PDF προγραμματιστικά με προσαρμοσμένη σκιά.
draft: false
keywords:
- add rectangle to pdf
- insert shape pdf
- add graphics to pdf
- create pdf document programmatically
- create pdf with shape
language: el
og_description: Προσθήκη ορθογωνίου σε PDF χρησιμοποιώντας το Aspose.Words. Αυτό το
  σεμινάριο δείχνει πώς να εισάγετε σχήμα σε PDF, να προσθέσετε γραφικά σε PDF και
  να δημιουργήσετε έγγραφο PDF προγραμματιστικά σε C#.
og_title: Προσθήκη ορθογωνίου σε PDF με το Aspose.Words – Πλήρης Οδηγός
tags:
- pdf
- aspnet
- csharp
- graphics
title: Προσθήκη ορθογωνίου σε PDF με το Aspose.Words – Οδηγός βήμα‑προς‑βήμα
url: /el/python/images-shapes/add-rectangle-to-pdf-with-aspose-words-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Προσθήκη ορθογωνίου σε PDF με Aspose.Words – Πλήρης Οδηγός

Έχετε χρειαστεί ποτέ να **προσθέσετε ορθογώνιο σε PDF** αλλά δεν ήξερατε ποια κλήση API κάνει τη δουλειά; Δεν είστε μόνοι—οι προγραμματιστές ρωτούν συνεχώς: «Πώς να εισάγω σχήμα σε PDF και να διατηρήσω το αρχείο ελαφρύ;» Τα καλά νέα είναι ότι το Aspose.Words το κάνει παιχνιδάκι. Σε αυτό το tutorial θα περάσουμε από όλη τη διαδικασία, από τη δημιουργία ενός PDF εγγράφου προγραμματιστικά μέχρι το στυλ του ορθογωνίου με σκιά.

Θα προσθέσουμε επίσης μερικά επιπλέον «γλυκίσματα»: θα μάθετε πώς να **προσθέσετε γραφικά σε PDF**, θα δείτε τα ακριβή βήματα για **εισαγωγή σχήματος σε PDF**, και θα ολοκληρώσουμε με ένα έτοιμο‑για‑εκτέλεση παράδειγμα που **δημιουργεί PDF με σχήμα**. Χωρίς εξωτερικές αναφορές, μόνο μια αυτόνομη λύση που μπορείτε να αντιγράψετε‑επικολλήσετε σήμερα.

## Προαπαιτούμενα

Πριν βάλουμε τα χέρια στη δουλειά, βεβαιωθείτε ότι έχετε:

- .NET 6.0 ή νεότερο (το Aspose.Words λειτουργεί με .NET Standard 2.0+)
- Ένα έγκυρο license του Aspose.Words for .NET ή ένα προσωρινό κλειδί αξιολόγησης
- Visual Studio 2022 (ή οποιοδήποτε IDE προτιμάτε)
- Βασικές γνώσεις C#—τίποτα περίπλοκο, μόνο την ικανότητα να τρέξετε μια εφαρμογή κονσόλας

Αυτό είναι όλο. Αν έχετε αυτά, είστε έτοιμοι.

## Βήμα 1: Δημιουργία PDF εγγράφου προγραμματιστικά

Το πρώτο πράγμα που κάνετε όταν θέλετε να **προσθέσετε ορθογώνιο σε PDF** είναι να δημιουργήσετε ένα κενό έγγραφο. Σκεφτείτε την κλάση `Document` ως ένα λευκό καμβά· όλα όσα θα προσθέσετε αργότερα ζουν μέσα του.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1 – initialise a new empty document
        Document doc = new Document();

        // The rest of the steps follow...
```

Γιατί να ξεκινήσετε με κενό έγγραφο; Επειδή σας δίνει πλήρη έλεγχο σε κάθε στοιχείο—χωρίς κρυφές κεφαλίδες ή υποσέλιδα που θα πρέπει να αντιμετωπίσετε αργότερα.

## Βήμα 2: Αρχικοποίηση DocumentBuilder για εισαγωγή σχήματος PDF

Ένας `DocumentBuilder` είναι το πινέλο σας. Ξέρει πώς να τοποθετεί κείμενο, εικόνες και, κρίσιμα για εμάς, σχήματα. Χωρίς αυτόν, θα έπρεπε να χειριστείτε το χαμηλού επιπέδου δέντρο κόμβων μόνοι σας—ένα εφιάλτης για τους περισσότερους προγραμματιστές.

```csharp
        // Step 2 – create a builder that will let us add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Παρατηρήστε ότι δεν έχουμε προσθέσει ακόμη σελίδες. Ο builder θα δημιουργήσει αυτόματα μια σελίδα την πρώτη φορά που θα εισάγετε κάτι, διατηρώντας τον κώδικα καθαρό.

## Βήμα 3: Εισαγωγή ορθογωνίου σχήματος – ο πυρήνας του «προσθήκη ορθογωνίου σε PDF»

Τώρα έρχεται το διασκεδαστικό κομμάτι: η εισαγωγή του ορθογωνίου. Η μέθοδος `InsertShape` υποστηρίζει δεκάδες τιμές `ShapeType`; θα επιλέξουμε `ShapeType.Rectangle` και θα του δώσουμε μέγεθος 200 × 100 points.

```csharp
        // Step 3 – insert a rectangle (200 × 100 points) into the document
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

Σε αυτό το σημείο το PDF περιέχει ήδη ένα απλό ορθογώνιο. Αν ανοίξετε το αρχείο τώρα, θα δείτε ένα απλό κουτί στην πάνω‑αριστερή γωνία της πρώτης σελίδας. Αυτό είναι το θεμέλιο για **προσθήκη γραφικών σε PDF**.

## Βήμα 4: Στυλιζάρισμα του ορθογωνίου – προσθήκη προσαρμοσμένης σκιάς

Ένα ορθογώνιο χωρίς στυλ είναι βαρετό. Ας του δώσουμε μια διακριτική σκιά ώστε να *αναδειχθεί* όταν το PDF αποδοθεί. Το αντικείμενο `ShadowFormat` ελέγχει τα πάντα—from την ακτίνα θολώματος μέχρι την αδιαφάνεια.

```csharp
        // Step 4 – configure a custom shadow for the shape
        ShadowFormat shadow = rectangle.ShadowFormat;
        shadow.Visible = true;
        shadow.BlurRadius = 8.0;          // pixels
        shadow.Distance = 5.0;           // points from the shape
        shadow.Direction = 45.0;         // degrees clockwise
        shadow.Opacity = 0.6;            // 0‑1 range
        shadow.Color = Color.Black;
```

Γιατί να ασχοληθούμε με σκιά; Εκτός από την αισθητική βελτίωση, μια σκιά μπορεί να βοηθήσει στη διάκριση επικαλυπτόμενων γραφικών—κάτι που μπορεί να χρειαστείτε όταν **προσθέτετε γραφικά σε PDF** σε πιο σύνθετες εκθέσεις.

## Βήμα 5: Αποθήκευση αρχείου – ολοκλήρωση της ροής «δημιουργία PDF με σχήμα»

Η τελική γραμμή γράφει τα πάντα στο δίσκο. Το Aspose.Words επιλέγει αυτόματα τη σωστή έκδοση PDF και ενσωματώνει τους απαραίτητους πόρους.

```csharp
        // Step 5 – save the document as a PDF file
        doc.Save(@"C:\Temp\ShapeWithShadow.pdf");
    }
}
```

Ανοίξτε το `ShapeWithShadow.pdf` και θα δείτε ένα όμορφα σκιασμένο ορθογώνιο να κάθεται περήφανα στη σελίδα. Αυτή είναι η πλήρης ροή **δημιουργίας PDF εγγράφου προγραμματιστικά**, σε λιγότερο από 30 γραμμές κώδικα.

## Πλήρες Παράδειγμα Εργασίας – δημιουργία PDF με σχήμα από την αρχή μέχρι το τέλος

Παρακάτω βρίσκεται το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε‑επικολλήσετε σε ένα νέο έργο Console App. Περιλαμβάνει όλες τις δηλώσεις `using`, τη μέθοδο `Main`, και ένα σύντομο σχόλιο κεφαλίδας για μελλοντική αναφορά.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectanglePdfDemo
{
    /// <summary>
    /// Demonstrates how to add a rectangle to PDF, configure a shadow,
    /// and save the result using Aspose.Words for .NET.
    /// </summary>
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create an empty PDF document
            Document doc = new Document();

            // 2️⃣ Initialise a DocumentBuilder – the tool that lets us add content
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert a rectangle shape (200 × 100 points) – this is the core of "add rectangle to pdf"
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);

            // 4️⃣ Apply a custom shadow – makes the graphic stand out
            ShadowFormat shadow = rect.ShadowFormat;
            shadow.Visible = true;
            shadow.BlurRadius = 8.0;   // pixels
            shadow.Distance = 5.0;    // points
            shadow.Direction = 45.0;  // degrees
            shadow.Opacity = 0.6;     // semi‑transparent
            shadow.Color = Color.Black;

            // 5️⃣ Save the document – the final step in creating a PDF with shape
            string outputPath = @"C:\Temp\ShapeWithShadow.pdf";
            doc.Save(outputPath);

            Console.WriteLine($"PDF saved successfully to {outputPath}");
        }
    }
}
```

**Αναμενόμενο αποτέλεσμα:** ένα PDF μιας σελίδας όπου ένα ορθογώνιο 200 × 100 points βρίσκεται κοντά στην πάνω‑αριστερή γωνία, διακοσμημένο με μια ήπια, 45‑μοίρες σκιά. Ανοίξτε το αρχείο σε οποιονδήποτε προβολέα PDF για να το επαληθεύσετε.

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

### Λειτουργεί αυτό με άλλους τύπους σχημάτων;
Απολύτως. Αντικαταστήστε το `ShapeType.Rectangle` με `ShapeType.Ellipse`, `ShapeType.Triangle`, ή οποιονδήποτε από τις 150+ επιλογές που υποστηρίζει το Aspose.Words. Οι ίδιες ιδιότητες `ShadowFormat` ισχύουν.

### Τι αν χρειάζομαι το ορθογώνιο σε συγκεκριμένη σελίδα;
Μετά την εισαγωγή του σχήματος, μπορείτε να το μετακινήσετε σε άλλη σελίδα ρυθμίζοντας την ιδιότητα `CurrentPage` του builder πριν καλέσετε `InsertShape`. Για παράδειγμα:

```csharp
builder.MoveToPage(3);
Shape rectOnPage3 = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

### Μπορώ να αλλάξω το χρώμα γεμίσματος του ορθογωνίου;
Βεβαίως. Χρησιμοποιήστε την ιδιότητα `FillColor`:

```csharp
rect.FillColor = Color.LightBlue;
```

### Πώς επηρεάζει αυτό το μέγεθος του αρχείου;
Η προσθήκη ενός απλού σχήματος και μιας σκιάς προσθέτει μόνο λίγα kilobytes. Αν αρχίσετε να στοιβάζετε πολλά γραφικά, σκεφτείτε τη συμπίεση εικόνων ή τη χρήση διανυσματικών σχημάτων για να κρατήσετε το PDF ελαφρύ.

### Απαιτείται άδεια για παραγωγή;
Το Aspose.Words λειτουργεί σε λειτουργία αξιολόγησης, αλλά το παραγόμενο PDF θα περιέχει υδατογράφημα. Αγοράστε άδεια για απεριόριστη χρήση και για την αφαίρεση του υδατογραφήματος.

## Συμβουλές & Τεχνάσματα (Επίπεδο Pro)

- **Μαζική εισαγωγή:** Αν χρειάζεστε δεκάδες ορθογώνια, κάντε βρόχο πάνω σε μια συλλογή συντεταγμένων και επαναχρησιμοποιήστε τον ίδιο `DocumentBuilder`—η απόδοση παραμένει γραμμική.
- **Στρώματα:** Ορίστε `rect.WrapType = WrapType.Inline` αν θέλετε το ορθογώνιο να ρέει με το κείμενο, ή `WrapType.Square` για να τυλίγεται το κείμενο γύρω του.
- **Συμμόρφωση PDF/A:** Καλέστε `doc.CompatibilityOptions.OptimizeForPdfA = true;` πριν την αποθήκευση αν χρειάζεστε ένα αρχείο φιλικό προς αρχειοθέτηση.

## Οπτική Σύνοψη

![προσθήκη ορθογωνίου σε pdf παράδειγμα](https://example.com/rectangle-shadow.png "προσθήκη ορθογωνίου σε pdf παράδειγμα")

Η εικόνα απεικονίζει τη τελική διάταξη του PDF: ένα καθαρό ορθογώνιο με διακριτική σκιά, ακριβώς ό,τι παράγει ο κώδικάς μας.

## Συμπέρασμα

Τώρα ξέρετε **πώς να προσθέσετε ορθογώνιο σε PDF** χρησιμοποιώντας το Aspose.Words, **πώς να εισάγετε σχήμα σε PDF**, και **πώς να προσθέσετε γραφικά σε PDF** με προσαρμοσμένο στυλ—όλα ενώ **δημιουργείτε PDF έγγραφο προγραμματιστικά** και ολοκληρώνετε με ένα παράδειγμα **δημιουργίας PDF με σχήμα** που μπορείτε να επαναχρησιμοποιήσετε αύριο.  

Στη συνέχεια, δοκιμάστε να αντικαταστήσετε το ορθογώνιο με ένα λογότυπο, ή συνδυάστε πολλαπλά σχήματα για να δημιουργήσετε ένα απλό διάγραμμα. Μπορείτε επίσης να εξερευνήσετε την αναδίπλωση κειμένου, την περιστροφή, ή ακόμη και την ενσωμάτωση υπερσυνδέσμου μέσα στο σχήμα. Το API είναι τόσο πλούσιο που σας επιτρέπει να μετατρέψετε ένα στατικό PDF σε μια διαδραστική, πλούσια σε γραφικά αναφορά χωρίς να φύγετε ποτέ από τη C#.

Πειραματιστείτε ελεύθερα, και αν αντιμετωπίσετε κάποιο πρόβλημα, αφήστε ένα σχόλιο παρακάτω. Καλή προγραμματιστική!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}