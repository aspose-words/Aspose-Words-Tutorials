---
category: general
date: 2026-02-24
description: Δημιουργήστε σχήμα ορθογωνίου σε C# χρησιμοποιώντας το Aspose.Words,
  προσθέστε σκιά στο σχήμα και αποθηκεύστε το έγγραφο ως PDF. Μάθετε πώς να προσθέτετε
  σκιά και πώς να αποθηκεύετε PDF σε λίγα λεπτά.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- how to save pdf
language: el
og_description: Δημιουργήστε σχήμα ορθογωνίου σε C# με το Aspose.Words, στη συνέχεια
  προσθέστε σκιά στο σχήμα και αποθηκεύστε το έγγραφο ως PDF – ένας πλήρης, βήμα‑προς‑βήμα
  οδηγός.
og_title: Δημιουργήστε σχήμα ορθογωνίου, προσθέστε σκιά & αποθηκεύστε PDF
tags:
- Aspose.Words
- C#
- PDF generation
title: Δημιουργήστε σχήμα ορθογωνίου, προσθέστε σκιά & αποθηκεύστε PDF
url: /el/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία σχήματος ορθογωνίου, προσθήκη σκιάς & αποθήκευση PDF

Έχετε ποτέ χρειαστεί να **δημιουργήσετε σχήμα ορθογωνίου** σε ένα έγγραφο Word αλλά θέλετε επίσης μια ωραία σκιά και εξαγωγή σε PDF; Δεν είστε ο μόνος. Σε πολλά έργα αναφορών ή δημιουργίας τιμολογίων, η οπτική τελειοποίηση — όπως μια διακριτική σκιά — κάνει τη διαφορά μεταξύ «απλώς ενός ακόμη αρχείου» και «εγγράφου επαγγελματικού επιπέδου».

Σε αυτό το tutorial θα περάσουμε ακριβώς από αυτό: χρησιμοποιώντας **Aspose.Words for .NET** για να δημιουργήσουμε ένα σχήμα ορθογωνίου, να προσθέσουμε σκιά στο σχήμα και, τελικά, **να αποθηκεύσουμε το έγγραφο ως PDF**. Στο τέλος θα έχετε μια έτοιμη για εκτέλεση εφαρμογή C# console που παράγει ένα PDF με ένα σκιασμένο ορθογώνιο, και θα κατανοήσετε πώς να ρυθμίσετε τη σκιά ή να αλλάξετε τις επιλογές εξαγωγής.

## Τι θα χρειαστείτε

- .NET 6 SDK (ή οποιαδήποτε πρόσφατη έκδοση .NET) – το API λειτουργεί το ίδιο και σε .NET Framework 4.x.  
- Πακέτο NuGet Aspose.Words for .NET (`Aspose.Words`) – εγκαταστήστε το με `dotnet add package Aspose.Words`.  
- Ένας επεξεργαστής κώδικα – Visual Studio, VS Code ή Rider είναι επαρκείς.  

Δεν απαιτούνται επιπλέον βήματα αδειοδότησης για αυτό το παράδειγμα· η δωρεάν λειτουργία αξιολόγησης είναι αρκετή για να δείτε το αποτέλεσμα σε PDF.

## Βήμα 1: Ρύθμιση του έργου και εισαγωγή namespaces

Πρώτα απ' όλα, ας δημιουργήσουμε ένα console project και να φέρουμε τις κλάσεις που θα χρειαστούμε.

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The rest of the code lives here – see the following steps.
        }
    }
}
```

*Γιατί είναι σημαντικό:* `Document` και `DocumentBuilder` μας παρέχουν το καμβά, ενώ `Shape` και `ShadowFormat` μας επιτρέπουν να σχεδιάσουμε και να μορφοποιήσουμε το ορθογώνιο. Η εισαγωγή τους από την αρχή διατηρεί τον επόμενο κώδικα καθαρό.

## Βήμα 2: **Δημιουργία σχήματος ορθογωνίου** με τις επιθυμητές διαστάσεις

Τώρα δημιουργούμε πραγματικά ένα κενό έγγραφο και εισάγουμε ένα ορθογώνιο. Παρατηρήστε πώς η μέθοδος `InsertShape` επιστρέφει ένα αντικείμενο `Shape` που μπορούμε αμέσως να μορφοποιήσουμε.

```csharp
// Inside Main()
Document document = new Document();               // blank Word document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle of 200x100 points (≈2.78" × 1.39")
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
rectangle.FillColor = System.Drawing.Color.LightBlue;
```

*Επεξήγηση*: Το μέγεθος εκφράζεται σε points (1 pt = 1/72 in). Προσαρμόστε τους αριθμούς ώστε να ταιριάζουν στη διάταξή σας. Δίνουμε επίσης στο σχήμα γέμισμα ανοιχτό-μπλε ώστε η σκιά να ξεχωρίζει.

## Βήμα 3: **Προσθήκη σκιάς στο σχήμα** – λεπτομερής ρύθμιση του εφέ

Μια σκιά δεν είναι απλώς «on/off». Μπορείτε να ελέγξετε το χρώμα, το blur, την απόσταση, την κατεύθυνση και ακόμη τη διαφάνεια. Ακολουθεί μια πρακτική διαμόρφωση που λειτουργεί καλά για τις περισσότερες αναφορές.

```csharp
// Access the shape's shadow format
ShadowFormat shadow = rectangle.ShadowFormat;
shadow.Visible = true;                     // turn the shadow on
shadow.Color = System.Drawing.Color.Gray;  // shadow colour
shadow.BlurRadius = 5.0;                    // soft edges (higher = blurrier)
shadow.Distance = 4.0;                      // how far the shadow is from the shape
shadow.Direction = 45;                     // angle in degrees (45° = down‑right)
shadow.Transparency = 0.3;                  // 30 % transparent for a subtle look
```

*Γιατί μπορεί να αλλάξετε αυτές τις τιμές:*  
- **BlurRadius** – αυξήστε για ένα ονειρικό εφέ, μειώστε για πιο καθαρή άκρη.  
- **Direction** – 0° δείχνει προς τα δεξιά, 90° κάτω, 180° αριστερά κ.λπ. Περιστρέψτε ώστε να ταιριάζει με τη διάταξη της σελίδας.  
- **Transparency** – ορίστε σε `0` για στερεή σκιά, `0.5` για ημιδιαφανή κ.λπ.

### Πώς να προσθέσετε σκιά – εναλλακτικές προσεγγίσεις

Αν χρειάζεστε **πολύπλοκη σκιά** (π.χ. μια πιο σκούρα εξωτερική σκιά συν μια πιο ανοιχτή εσωτερική), μπορείτε να δημιουργήσετε δεύτερο σχήμα, να το μετατοπίσετε και να ορίσετε διαφορετικό `ShadowFormat`. Ή, για γρήγορη εμφάνιση «χωρίς blur», ορίστε `BlurRadius = 0`.

## Βήμα 4: **Αποθήκευση εγγράφου ως PDF** – η τελική εξαγωγή

Με το ορθογώνιο και τη σκιά του έτοιμα, το τελευταίο βήμα είναι να γράψετε το αρχείο ως PDF. Το Aspose.Words διαχειρίζεται τη μετατροπή εσωτερικά· απλώς καλείτε `Save` με τη μορφή που θέλετε.

```csharp
// Define the output path – adjust to your environment
string outputPath = @"C:\Temp\ShadowRectangle.pdf";

// Save as PDF (the format is inferred from the extension)
document.Save(outputPath);
Console.WriteLine($"PDF saved to {outputPath}");
```

*Συμβουλή*: Αν χρειάζεται να ελέγξετε τη συμμόρφωση του PDF (PDF/A, PDF/X) ή να ενσωματώσετε γραμματοσειρές, χρησιμοποιήστε την υπερφόρτωση:

```csharp
PdfSaveOptions options = new PdfSaveOptions
{
    Compliance = PdfCompliance.PdfA1b,
    EmbedFullFonts = true
};
document.Save(outputPath, options);
```

Αυτό είναι το **πώς να αποθηκεύσετε PDF** συνοπτικά.

## Πλήρες, εκτελέσιμο παράδειγμα

Παρακάτω είναι το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε‑και‑επικολλήσετε στο `Program.cs`. Συγκεντώνεται και εκτελείται όπως είναι (απλώς βεβαιωθείτε ότι ο φάκελος εξόδου υπάρχει).

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank document and a builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert a rectangle shape
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // 3️⃣ Add a shadow to the shape
            ShadowFormat shadow = rectangle.ShadowFormat;
            shadow.Visible = true;
            shadow.Color = System.Drawing.Color.Gray;
            shadow.BlurRadius = 5.0;
            shadow.Distance = 4.0;
            shadow.Direction = 45;
            shadow.Transparency = 0.3;

            // 4️⃣ Save the document as PDF
            string outputPath = @"C:\Temp\ShadowRectangle.pdf";
            document.Save(outputPath);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

### Αναμενόμενο αποτέλεσμα

Ανοίξτε το παραγόμενο `ShadowRectangle.pdf`. Θα δείτε μια μονή σελίδα με ένα ανοιχτό‑μπλε ορθογώνιο, μια απαλή γκρι σκιά μετατοπισμένη 45° κάτω‑δεξιά, και καθαρές άκρες. Το PDF πρέπει να είναι αναγνώσιμο σε οποιονδήποτε σύγχρονο αναγνώστη (Adobe Acrobat, Edge, Chrome).

![Δημιουργία σχήματος ορθογωνίου με σκιά σε PDF](/images/shadow-rectangle.png "Δημιουργία σχήματος ορθογωνίου με σκιά")

*(Το κείμενο alt της εικόνας περιλαμβάνει τη βασική λέξη-κλειδί για SEO.)*

## Συχνές ερωτήσεις & αντιμετώπιση ειδικών περιπτώσεων

**Τι γίνεται αν η σκιά εξαφανιστεί στο PDF;**  
Βεβαιωθείτε ότι χρησιμοποιείτε πρόσφατη έκδοση του Aspose.Words (≥23.3). Παλαιότερες εκδόσεις είχαν σφάλμα όπου ορισμένες ιδιότητες σκιάς αγνοούνταν κατά τη μετατροπή σε PDF.

**Μπορώ να αλλάξω το χρώμα της σκιάς ώστε να ταιριάζει με το brand μου;**  
Απολύτως—απλώς αντικαταστήστε το `System.Drawing.Color.Gray` με οποιοδήποτε `Color` θέλετε, π.χ. `Color.FromArgb(128, 0, 0, 255)` για ημιδιαφανές μπλε.

**Πώς προσθέτω σκιά σε άλλα σχήματα (ellipse, star κ.λπ.;)**  
Το ίδιο `ShadowFormat` λειτουργεί για οποιοδήποτε αντικείμενο `Shape`. Αφού δημιουργήσετε το σχήμα, πάρτε το `ShadowFormat` του και ορίστε τις ιδιότητες.

**Τι γίνεται με προβλήματα DPI ή κλιμάκωσης;**  
Η απόδοση PDF σέβεται το μέγεθος του σχήματος σε points. Αν χρειάζεστε υψηλότερη ανάλυση (για εκτύπωση), προσαρμόστε τις διαστάσεις του σχήματος ανάλογα ή ορίστε `PdfSaveOptions.ImageResolution`.

**Μπορώ να εξάγω σε άλλες μορφές, όπως PNG;**  
Ναι—απλώς καλέστε `document.Save("output.png", SaveFormat.Png)`. Η σκιά θα αποδοθεί με τον ίδιο τρόπο.

## Επαγγελματικές συμβουλές & βέλτιστες πρακτικές

- **Επαναχρησιμοποίηση του builder**: Αν προσθέτετε πολλά σχήματα, διατηρήστε μία μόνο παρουσία `DocumentBuilder`; είναι πιο οικονομικό από το να δημιουργείτε πολλές.  
- **Αποθήκευση σε παρτίδες**: Όταν δημιουργείτε πολλά PDF σε βρόχο, επαναχρησιμοποιήστε το αντικείμενο `PdfSaveOptions` για να αποφύγετε επαναλαμβανόμενες εκχωρήσεις.  
- **Δοκιμή**: Πάντα ανοίξτε το PDF μετά την αποθήκευση για να επαληθεύσετε ότι η σκιά εμφανίζεται όπως αναμένεται. Ορισμένα προγράμματα προβολής PDF αποδίδουν τις σκιές ελαφρώς διαφορετικά· το Adobe Acrobat είναι η πιο αξιόπιστη αναφορά.  
- **Απόδοση**: Για μεγάλα έγγραφα, απενεργοποιήστε τις αυτόματες αλλαγές σελίδας του `DocumentBuilder.InsertShape` ορίζοντας `builder.PageSetup.DifferentFirstPageHeaderFooter = false` εάν δεν τις χρειάζεστε.

## Συμπέρασμα

Καλύψαμε όλα όσα χρειάζεστε για να **δημιουργήσετε σχήμα ορθογωνίου**, **προσθέσετε σκιά στο σχήμα**, και **αποθηκεύσετε το έγγραφο ως PDF** χρησιμοποιώντας Aspose.Words for .NET. Ο κώδικας είναι σύντομος, οι έννοιες εξηγημένες, και τώρα έχετε μια σταθερή βάση για να πειραματιστείτε με άλλα σχήματα, στυλ σκιάς και επιλογές εξαγωγής.  

Επόμενα βήματα; Δοκιμάστε να αντικαταστήσετε το ορθογώνιο με ένα στρογγυλεμένο‑

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}