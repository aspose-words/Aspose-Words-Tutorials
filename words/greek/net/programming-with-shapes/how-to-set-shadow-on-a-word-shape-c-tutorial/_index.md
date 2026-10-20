---
category: general
date: 2026-03-30
description: Μάθετε πώς να ορίσετε σκιά σε σχήμα του Word χρησιμοποιώντας C#. Αυτός
  ο οδηγός δείχνει επίσης πώς να προσθέσετε σκιά σε σχήμα, να ρυθμίσετε τη διαφάνεια
  του σχήματος και να προσθέσετε σκιά σε ορθογώνιο.
draft: false
keywords:
- how to set shadow
- adjust shape transparency
- add shape shadow
- how to add shadow
- add rectangle shadow
language: el
og_description: Πώς να ορίσετε σκιά σε σχήμα Word σε C#; Ακολουθήστε αυτόν τον οδηγό
  βήμα‑βήμα για να προσθέσετε σκιά σε σχήμα, να ρυθμίσετε τη διαφάνεια του σχήματος
  και να προσθέσετε σκιά σε ορθογώνιο.
og_title: Πώς να ορίσετε σκιά σε σχήμα Word – Εκπαίδευση C#
tags:
- Aspose.Words
- C#
- Word Automation
- Shapes
title: Πώς να ορίσετε σκιά σε σχήμα Word – C# Tutorial
url: /el/net/programming-with-shapes/how-to-set-shadow-on-a-word-shape-c-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Ορίσετε Σκιά σε Σχήμα Word – Εγχειρίδιο C#

Έχετε αναρωτηθεί ποτέ **πώς να ορίσετε σκιά** σε ένα σχήμα μέσα σε ένα έγγραφο Word χωρίς να παίζετε με το UI; Δεν είστε ο μόνος. Σε πολλές αναφορές ή παρουσιάσεις μάρκετινγκ, μια διακριτική σκιά‑πτώση κάνει ένα ορθογώνιο να ξεχωρίζει, και η προγραμματιστική υλοποίηση εξοικονομεί ώρες.

Σε αυτόν τον οδηγό θα περάσουμε από ένα πλήρες, έτοιμο‑για‑εκτέλεση παράδειγμα που όχι μόνο δείχνει **πώς να ορίσετε σκιά**, αλλά καλύπτει επίσης **προσθήκη σκιάς σε σχήμα**, **ρύθμιση διαφάνειας σχήματος**, και ακόμη **προσθήκη σκιάς σε ορθογώνιο** για εκείνα τα κλασικά πλαίσια επεξήγησης. Στο τέλος θα έχετε ένα αρχείο Word (`output.docx`) που φαίνεται επαγγελματικό, και θα καταλάβετε γιατί κάθε ιδιότητα είναι σημαντική.

## Προαπαιτούμενα

- .NET 6+ (ή .NET Framework 4.7.2) με μεταγλωττιστή C#  
- Πακέτο NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)  
- Βασική εξοικείωση με C# και το μοντέλο αντικειμένων του Word  

Δεν απαιτούνται πρόσθετες βιβλιοθήκες—όλα βρίσκονται μέσα στο Aspose.Words.

---

## Πώς να Ορίσετε Σκιά σε Σχήμα Word με C#

Παρακάτω βρίσκεται το πλήρες αρχείο πηγαίου κώδικα. Αποθηκεύστε το ως `Program.cs` και εκτελέστε το από το IDE σας ή με `dotnet run`. Ο κώδικας φορτώνει ένα υπάρχον `.docx`, βρίσκει το πρώτο σχήμα (ένα ορθογώνιο από προεπιλογή), ενεργοποιεί τη σκιά του, ρυθμίζει μερικές οπτικές παραμέτρους, και αποθηκεύει το αποτέλεσμα.

```csharp
// Program.cs
using System;
using System.Drawing;               // For Color
using Aspose.Words;                // Core document API
using Aspose.Words.Drawing;        // Shape and shadow classes

class ShadowDemo
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the shape.
        // Replace YOUR_DIRECTORY with the folder where your files live.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Retrieve the first shape in the document.
        // If you have multiple shapes, you can loop or use GetChild with a different index.
        Shape rectangleShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (rectangleShape == null)
        {
            Console.WriteLine("No shape found – make sure input.docx contains at least one shape.");
            return;
        }

        // 3️⃣ Enable the shape's shadow and choose a base color.
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = Color.Black;   // You can pick any System.Drawing.Color

        // 4️⃣ Fine‑tune the shadow appearance.
        rectangleShape.ShadowFormat.Transparency = 0.3;     // 30 % transparent (adjust shape transparency)
        rectangleShape.ShadowFormat.OffsetX = 5;           // Horizontal offset in points
        rectangleShape.ShadowFormat.OffsetY = 5;           // Vertical offset in points
        rectangleShape.ShadowFormat.BlurRadius = 4;       // Soft edge radius

        // 5️⃣ Save the updated document.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Shadow applied! Check {outputPath}");
    }
}
```

> **Τι θα δείτε** – Το ορθογώνιο τώρα εμφανίζει μια μαύρη σκιά‑πτώσης που είναι 30 % διαφανής, μετατοπισμένη 5 pt δεξιά και κάτω, με ήπια θολούρα. Ανοίξτε το `output.docx` στο Word για να το επαληθεύσετε.

## Ρύθμιση Διαφάνειας Σχήματος – Γιατί Είναι Σημαντική

Η διαφάνεια δεν είναι μόνο μια αισθητική ρύθμιση· επηρεάζει την αναγνωσιμότητα. Μια τιμή 0.0 κάνει τη σκιά πλήρως αδιαφανή, ενώ 1.0 την κρύβει εντελώς. Στο παραπάνω απόσπασμα χρησιμοποιήσαμε `0.3` για να πετύχουμε ένα διακριτικό αποτέλεσμα που λειτουργεί τόσο σε ανοιχτά όσο και σε σκούρα φόντα. Μη διστάσετε να πειραματιστείτε:

```csharp
rectangleShape.ShadowFormat.Transparency = 0.1; // Almost solid shadow
rectangleShape.ShadowFormat.Transparency = 0.6; // Very faint
```

Θυμηθείτε, **ρύθμιση διαφάνειας σχήματος** μπορεί επίσης να εφαρμοστεί στο χρώμα γεμίσματος του σχήματος αν χρειάζεστε ένα ημιδιαφανές ορθογώνιο.

## Προσθήκη Σκιάς σε Σχήμα σε Διάφορα Αντικείμενα

Ο κώδικας που χρησιμοποιήσαμε στοχεύει σε αντικείμενο `Shape`, αλλά οι ίδιες ιδιότητες `ShadowFormat` υπάρχουν σε αντικείμενα **Image**, **Chart**, και ακόμη **TextBox**. Ακολουθεί ένα γρήγορο πρότυπο που μπορείτε να αντιγράψετε‑επικολλήσετε:

```csharp
// Assuming 'image' is an Aspose.Words.Drawing.Image object
image.ShadowFormat.Visible = true;
image.ShadowFormat.Color = Color.Gray;
image.ShadowFormat.OffsetX = 3;
image.ShadowFormat.OffsetY = 3;
image.ShadowFormat.BlurRadius = 2;
```

Έτσι, είτε **προσθέτετε σκιά σε σχήμα** σε ένα λογότυπο είτε σε ένα διακοσμητικό εικονίδιο, η προσέγγιση παραμένει η ίδια.

## Πώς να Προσθέσετε Σκιά σε Οποιοδήποτε Σχήμα – Ακραίες Περιπτώσεις

1. **Σχήμα χωρίς πλαίσιο περιβάλλοντος** – Ορισμένα σχήματα Word (όπως ελεύθερα σχέδια) δεν υποστηρίζουν σκιές. Η προσπάθεια ορισμού του `ShadowFormat.Visible` θα αποτύχει σιωπηρά. Ελέγξτε το `shape.IsShadowSupported` αν χρειάζεστε ασφάλεια.  
2. **Παλαιότερες εκδόσεις Word** – Οι ιδιότητες σκιάς αντιστοιχούν σε δυνατότητες Word 2007+. Αν πρέπει να υποστηρίξετε Word 2003, η σκιά θα αγνοηθεί όταν ανοίξει το αρχείο.  
3. **Πολλαπλές σκιές** – Το Aspose.Words υποστηρίζει επί του παρόντος μία μόνο σκιά ανά σχήμα. Αν χρειάζεστε διπλό‑επίπεδο εφέ, διπλασιάστε το σχήμα, μετατοπίστε το, και εφαρμόστε διαφορετικές ρυθμίσεις σκιάς.

## Προσθήκη Σκιάς σε Ορθογώνιο – Πραγματική Περίπτωση Χρήσης

Φανταστείτε ότι δημιουργείτε μια τριμηνιαία αναφορά και κάθε επικεφαλίδα ενότητας είναι ένα χρωματιστό ορθογώνιο. Η προσθήκη **προσθήκη σκιάς σε ορθογώνιο** δίνει στη σελίδα μια εμφάνιση «καρτέλας». Τα βήματα είναι τα ίδια με το βασικό παράδειγμα· απλώς βεβαιωθείτε ότι το σχήμα που στοχεύετε είναι πράγματι ένα ορθογώνιο (`shape.ShapeType == ShapeType.Rectangle`). Αν χρειάζεται να δημιουργήσετε το ορθογώνιο από την αρχή, δείτε το απόσπασμα παρακάτω:

```csharp
// Create a new rectangle shape programmatically
Shape newRect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,
    Height = 50,
    WrapType = WrapType.Inline
};
newRect.FillColor = Color.LightBlue;

// Apply shadow (same settings as before)
newRect.ShadowFormat.Visible = true;
newRect.ShadowFormat.Color = Color.Black;
newRect.ShadowFormat.Transparency = 0.25;
newRect.ShadowFormat.OffsetX = 4;
newRect.ShadowFormat.OffsetY = 4;
newRect.ShadowFormat.BlurRadius = 3;

// Insert into the first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(newRect);
```

Η εκτέλεση του πλήρους προγράμματος με αυτήν την προσθήκη θα σας δώσει ένα νέο ορθογώνιο που ήδη περιλαμβάνει το επιθυμητό εφέ **προσθήκη σκιάς σε ορθογώνιο**.

---

![Word shape with shadow](placeholder-image.png){alt="πώς να ορίσετε σκιά σε σχήμα στο Word"}

*Σχήμα: Το ορθογώνιο μετά την εφαρμογή των ρυθμίσεων σκιάς.*

## Σύντομη Ανακεφαλαίωση (Λίστα Συμβουλών σε Σημεία)

- **Φόρτωση** του εγγράφου με `new Document(path)`.  
- **Εντοπισμός** του σχήματος μέσω `doc.GetChild(NodeType.Shape, index, true)`.  
- **Ενεργοποίηση** σκιάς: `shape.ShadowFormat.Visible = true;`.  
- **Ορισμός χρώματος** με οποιοδήποτε `System.Drawing.Color`.  
- **Ρύθμιση διαφάνειας** (`0.0–1.0`) για έλεγχο της αδιαφάνειας.  
- **OffsetX / OffsetY** μετακινούν τη σκιά οριζόντια/κατακόρυφα (points).  
- **BlurRadius** μαλακώνει την άκρη—υψηλότερες τιμές = πιο θολή σκιά.  
- **Αποθήκευση** του αρχείου και άνοιγμα στο Word για να δείτε το αποτέλεσμα.

## Τι να Δοκιμάσετε Στη Σύντομη Επόμενη Φάση;

- **Δυναμικά χρώματα** – Λάβετε το χρώμα σκιάς από ένα θέμα ή εισαγωγή χρήστη.  
- **Σκιές υπό όρους** – Εφαρμόστε σκιά μόνο όταν το πλάτος του σχήματος υπερβαίνει ένα όριο.  
- **Επεξεργασία κατά παρτίδες** – Επανάληψη σε όλα τα σχήματα ενός εγγράφου και **προσθήκη σκιάς σε σχήμα** αυτόματα.  

Αν ακολουθήσατε, τώρα γνωρίζετε **πώς να ορίσετε σκιά**, πώς να **ρυθμίσετε τη διαφάνεια σχήματος**, και πώς να **προσθέσετε σκιά σε ορθογώνιο** για αυτό το επαγγελματικό φινίρισμα. Μη διστάσετε να πειραματιστείτε, να σπάσετε πράγματα, και μετά να τα διορθώσετε—ο προγραμματισμός είναι ο καλύτερος δάσκαλος.

*Καλό προγραμματισμό! Αν αυτό το εγχειρίδιο σας βοήθησε, αφήστε ένα σχόλιο ή μοιραστείτε τις δικές σας τεχνικές σκιάς. Όσο περισσότερο μαθαίνουμε ο ένας από τον άλλο, τόσο πιο όμορφα γίνονται τα έγγραφα Word μας.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}