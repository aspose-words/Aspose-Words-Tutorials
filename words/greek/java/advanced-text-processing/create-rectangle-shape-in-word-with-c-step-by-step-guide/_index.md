---
category: general
date: 2026-03-04
description: Learn how to create rectangle shape, add shadow to shape and apply shadow
  effect in a Word document, then save Word document automatically.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- apply shadow effect
- save word document
- create blank document
language: el
og_description: Δημιουργήστε σχήμα ορθογωνίου, προσθέστε σκιά στο σχήμα και εφαρμόστε
  το εφέ σκιάς σε ένα έγγραφο Word χρησιμοποιώντας C#. Ακολουθήστε αυτόν τον οδηγό
  για να αποθηκεύσετε το έγγραφο Word εύκολα.
og_title: Create rectangle shape in Word – Complete C# Tutorial
tags:
- C#
- Aspose.Words
- Document Automation
title: Δημιουργία σχήματος ορθογωνίου στο Word με C# – Οδηγός βήμα‑προς‑βήμα
url: /el/java/advanced-text-processing/create-rectangle-shape-in-word-with-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία σχήματος ορθογωνίου στο Word με C# – Πλήρης Προγραμματιστικός Οδηγός

Έχετε ποτέ χρειαστεί να **create rectangle shape** σε ένα αρχείο Word αλλά δεν ήξερτε από πού να ξεκινήσετε; Δεν είστε μόνοι—πολλοί προγραμματιστές αντιμετωπίζουν το ίδιο πρόβλημα όταν βυθίζονται για πρώτη φορά στη δημιουργία εγγράφων προγραμματιστικά. Τα καλά νέα είναι ότι με λίγες γραμμές C# μπορείτε να εισάγετε ένα ορθογώνιο, **add shadow to shape**, και **apply shadow effect** χωρίς καν να ανοίξετε το Word. Σε αυτόν τον οδηγό θα περάσουμε από όλη τη διαδικασία, από ένα φρέσκο **create blank document** μέχρι την αποθήκευση του τελικού **save word document** στο δίσκο.

Θα καλύψουμε όλα όσα χρειάζεστε: το απαιτούμενο πακέτο NuGet, τα ακριβή API, γιατί κάθε ιδιότητα είναι σημαντική, και μια σειρά από συμβουλές για να αποφύγετε τα πιο κοινά προβλήματα. Στο τέλος θα έχετε ένα πλήρως εκτελέσιμο παράδειγμα που μπορείτε να ενσωματώσετε σε οποιοδήποτε .NET project.

## Προαπαιτήσεις

- .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.7+)
- Visual Studio 2022 ή οποιοδήποτε IDE προτιμάτε
- **Aspose.Words for .NET** εγκατεστημένο μέσω NuGet (`Install-Package Aspose.Words`)
- Βασική εξοικείωση με τη σύνταξη C#

Δεν απαιτούνται πρόσθετες βιβλιοθήκες interop του Word—το Aspose.Words διαχειρίζεται τα πάντα στη μνήμη.

## Βήμα 1 – Create a blank document

Το πρώτο που κάνουμε είναι **create blank document**. Σκεφτείτε το ως τον κενό καμβά πάνω στον οποίο θα **create rectangle shape** αργότερα.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Initialize a new blank document
Document doc = new Document();   // This gives us a fresh Word file
```

> **Why this matters:** Ξεκινώντας με ένα καθαρό αντικείμενο `Document` εξασφαλίζετε ότι δεν υπάρχουν κρυφά στυλ ή ενότητες που να επηρεάζουν τη θέση του σχήματος αργότερα.

## Βήμα 2 – Insert a rectangle shape into the document

Τώρα δημιουργούμε πραγματικά **create rectangle shape**. Θα ορίσουμε το μέγεθός του, τη θέση του, και θα πούμε στο Word να μην περιτυλίγει κείμενο γύρω του.

```csharp
// Step 2: Add a rectangle shape
Shape rectangle = new Shape(doc, ShapeType.Rectangle);
rectangle.Width = 200;          // Width in points (1 point = 1/72 inch)
rectangle.Height = 100;         // Height in points
rectangle.WrapType = WrapType.None; // No text wrapping
```

> **Pro tip:** Αν χρειάζεται το ορθογώνιο να βρίσκεται μέσα σε κελί πίνακα, αλλάξτε το `WrapType` σε `WrapType.Inline`. Για τις περισσότερες αναφορές, το `None` κρατά το σχήμα να αιωρείται πάνω από το κείμενο.

## Βήμα 3 – Add shadow to shape and configure its appearance

Εδώ συμβαίνει η μαγεία: **add shadow to shape** και **apply shadow effect**. Η σκιά κάνει το ορθογώνιο να ξεχωρίζει στη σελίδα, ειδικά όταν εκτυπώνεται.

```csharp
// Step 3: Enable shadow and set its properties
rectangle.ShadowFormat.Visible = true;          // Turn on the shadow
rectangle.ShadowFormat.BlurRadius = 5.0;        // Softness of the shadow edge
rectangle.ShadowFormat.Transparency = 0.3;      // 30 % transparent
rectangle.ShadowFormat.OffsetX = 8;             // Horizontal shift
rectangle.ShadowFormat.OffsetY = 8;             // Vertical shift
rectangle.ShadowFormat.Color = Color.Blue;     // Shadow colour
```

> **Why these values?**  
> - **BlurRadius** ελέγχει πόσο θολές φαίνονται οι άκρες· μια τιμή γύρω στο `5` δίνει ένα διακριτικό, επαγγελματικό αποτέλεσμα.  
> - **Transparency** επιτρέπει στο κείμενο κάτω από τη σκιά να παραμένει αναγνώσιμο.  
> - **OffsetX/Y** μετακινούν τη σκιά μακριά από το σχήμα, δημιουργώντας βάθος.  
> - Η χρήση μιας **blue** απόχρωσης είναι μόνο παράδειγμα—οποιοδήποτε `System.Drawing.Color` λειτουργεί.

## Βήμα 4 – Add the configured shape to the document body

Με το ορθογώνιο πλήρως μορφοποιημένο, τώρα **add rectangle shape** στην πρώτη ενότητα του εγγράφου. Αυτό το βήμα τοποθετεί πραγματικά το σχήμα στο αρχείο.

```csharp
// Step 4: Append the shape to the first section's body
doc.FirstSection.Body.AppendChild(rectangle);
```

> **Edge case:** Αν το έγγραφό σας περιέχει ήδη ενότητες, ίσως θελήσετε να στοχεύσετε μια συγκεκριμένη (`doc.Sections[2]` για παράδειγμα). Ο παραπάνω κώδικας λειτουργεί για ένα έγγραφο με μία ενότητα, κάτι που είναι συχνό σε γρήγορες αναφορές.

## Βήμα 5 – Save the Word document

Τέλος, **save word document** στο δίσκο. Το αρχείο θα περιέχει το ορθογώνιο με τη σκιά του, έτοιμο να ανοίξει στο Microsoft Word.

```csharp
// Step 5: Persist the document
string outputPath = @"C:\Temp\shadowed_rectangle.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

> **Tip:** Χρησιμοποιήστε `doc.Save(outputPath, SaveFormat.Docx)` αν χρειάζεται να είστε σαφείς σχετικά με τη μορφή. Η μέθοδος `Save` ανιχνεύει αυτόματα την επέκταση, αλλά η ρητή δήλωση μπορεί να αποφύγει σύγχυση όταν η διαδρομή δημιουργείται προγραμματιστικά.

## Full, Runnable Example

Παρακάτω είναι το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε‑και‑επικολλήσετε σε μια εφαρμογή console. Περιλαμβάνει όλες τις δηλώσεις `using` και τη μέθοδο `Main`, ώστε να το τρέξετε αμέσως.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank document
            Document doc = new Document();

            // 2️⃣ Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle);
            rectangle.Width = 200;
            rectangle.Height = 100;
            rectangle.WrapType = WrapType.None;

            // 3️⃣ Apply shadow effect
            rectangle.ShadowFormat.Visible = true;
            rectangle.ShadowFormat.BlurRadius = 5.0;
            rectangle.ShadowFormat.Transparency = 0.3;
            rectangle.ShadowFormat.OffsetX = 8;
            rectangle.ShadowFormat.OffsetY = 8;
            rectangle.ShadowFormat.Color = Color.Blue;

            // 4️⃣ Insert the shape into the document body
            doc.FirstSection.Body.AppendChild(rectangle);

            // 5️⃣ Save the document
            string outputPath = @"C:\Temp\shadowed_rectangle.docx";
            doc.Save(outputPath);
            Console.WriteLine($"✅ Document saved at {outputPath}");
        }
    }
}
```

### Expected Result

Όταν ανοίξετε το *shadowed_rectangle.docx* στο Microsoft Word, θα δείτε ένα ορθογώνιο με μπλε περίγραμμα να αιωρείται κοντά στην κορυφή της πρώτης σελίδας, με μια απαλή μπλε σκιά μετατοπισμένη 8 pt προς τα δεξιά και κάτω. Δεν υπάρχει επιπλέον κείμενο γύρω του επειδή ορίσαμε `WrapType.None`.

## Frequently Asked Questions & Variations

| Question | Answer |
|----------|--------|
| **Can I change the shape to an ellipse?** | Yes—replace `ShapeType.Rectangle` with `ShapeType.Ellipse`. All shadow properties remain the same. |
| **What if I need multiple shapes?** | Simply repeat Steps 2‑4 for each new `Shape` instance, adjusting `OffsetX/Y` or `Left/Top` to avoid overlap. |
| **Is there a way to make the shadow color match the shape’s fill?** | Absolutely. Set `rectangle.FillColor` first, then assign `rectangle.ShadowFormat.Color = rectangle.FillColor;`. |
| **How do I insert the shape into a table cell?** | Use `cell.FirstParagraph.AppendChild(rectangle);` after locating the desired `Cell` object. |
| **Will this work on .NET Core?** | Yes—Aspose.Words is cross‑platform. Just ensure you reference the appropriate NuGet package version for .NET Core/5/6. |

## Common Pitfalls & Pro Tips

- **Pitfall:** Forgetting to set `ShadowFormat.Visible = true`. The shadow properties will be ignored silently.  
  **Fix:** Always enable visibility before tweaking other shadow parameters.

- **Pitfall:** Using a very large `BlurRadius` (e.g., 20) can make the shadow look fuzzy and unprofessional.  
  **Fix:** Stick to values between `3` and `8` for most business documents.

- **Pro tip:** If you need the shape to be selectable later (e.g., for end‑user editing), avoid setting `WrapType.Inline`. Floating shapes (`WrapType.None`) are easier to move around programmatically.

- **Pro tip:** When generating many documents in a loop, reuse a single `Document` instance and call `doc.Clone(true)` for each iteration to improve performance.

## Related Topics You Might Explore Next

- **Add text inside a rectangle shape** – learn how to use `Shape.TextPath` for labels.  
- **Create complex diagrams** – combine multiple shapes, connectors, and grouping.  
- **Export to PDF** – convert the same document to PDF with a single `doc.Save("output.pdf")`.  
- **Apply different fill styles** – gradients, textures, or even pictures inside shapes.

## Conclusion

Μόλις **create rectangle shape**, **add shadow to shape**, και **apply shadow effect** σε ένα αρχείο Word χρησιμοποιώντας C#. Ακολουθώντας τα πέντε σύντομα βήματα, έχετε τώρα ένα επαναχρησιμοποιήσιμο πρότυπο για οποιοδήποτε σενάριο αυτοματοποίησης εγγράφων, και ξέρετε πώς να **save word document** αξιόπιστα. Μη διστάσετε να προσαρμόσετε διαστάσεις, χρώματα ή ακόμη και να αντικαταστήσετε το ορθογώνιο με άλλη γεωμετρία—το Aspose.Words κάνει τα πάντα απλά.

Αν βρήκατε αυτόν τον οδηγό χρήσιμο, δώστε του ένα αστέρι στο GitHub ή μοιραστείτε τις δικές σας παραλλαγές στα σχόλια. Καλή προγραμματιστική, και τα έγγραφά σας να είναι πάντα τόσο γυαλισμένα όσο αυτό το σκιώδες ορθογώνιο!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}