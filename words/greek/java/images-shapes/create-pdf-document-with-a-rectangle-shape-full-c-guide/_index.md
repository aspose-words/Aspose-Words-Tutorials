---
category: general
date: 2026-03-25
description: Δημιουργήστε έγγραφο PDF σε C# και μάθετε πώς να προσθέσετε σχήμα ορθογωνίου,
  να ορίσετε χρώμα γεμίσματος, να προσαρμόσετε το μέγεθος του σχήματος και να ορίσετε
  τη διαφάνεια του σχήματος σε λίγα μόνο βήματα.
draft: false
keywords:
- create pdf document
- set shape transparency
- add rectangle shape
- set fill color
- set shape size
language: el
og_description: Δημιουργήστε έγγραφο PDF σε C# και δείτε πώς να προσθέσετε ένα ορθογώνιο,
  να ορίσετε το χρώμα γεμίσματος, το μέγεθος και τη διαφάνεια για ένα επαγγελματικό
  αποτέλεσμα PDF.
og_title: Δημιουργία εγγράφου PDF με σχήμα ορθογωνίου – Οδηγός C#
tags:
- C#
- PDF
- Aspose.Words
title: Δημιουργία εγγράφου PDF με σχήμα ορθογωνίου – Πλήρης οδηγός C#
url: /el/java/images-shapes/create-pdf-document-with-a-rectangle-shape-full-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία Εγγράφου PDF με Σχήμα Ορθογωνίου – Πλήρης Οδηγός C#

Έχετε ποτέ χρειαστεί να **δημιουργήσετε έγγραφο PDF** που περιέχει ένα σχήμα με προσαρμοσμένο στυλ, αλλά δεν ήξερες από πού να ξεκινήσεις; Δεν είστε μόνοι. Είτε δημιουργείτε έναν γεννήτρια αναφορών είτε ένα διαφημιστικό φυλλάδιο, η δυνατότητα να σχεδιάζετε προγραμματιστικά ένα ορθογώνιο, να ορίζετε το χρώμα γεμίσματος, να ρυθμίζετε το μέγεθός του και ακόμη να προσαρμόζετε τη διαφάνειά του μπορεί να κάνει τα PDF σας να φαίνονται πολύ πιο επαγγελματικά.

Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα ένα πλήρες, έτοιμο‑για‑εκτέλεση παράδειγμα C# που **δημιουργεί ένα έγγραφο PDF**, **προσθέτει ένα σχήμα ορθογωνίου**, **ορίζει το χρώμα γεμίσματος**, **καθορίζει το μέγεθος του σχήματος**, και **ορίζει τη διαφάνεια του σχήματος** για μια διακριτική εξωτερική σκιά. Στο τέλος θα έχετε ένα μόνο αρχείο PDF (`shadow.pdf`) που μπορείτε να ανοίξετε για να δείτε το αποτέλεσμα.

> **Συμβουλή:** Η ίδια προσέγγιση λειτουργεί με άλλους τύπους σχημάτων (ellipse, line, κ.λπ.)—απλώς αντικαταστήστε το `ShapeType.RECTANGLE` με αυτό που χρειάζεστε.

---

## Τι Θα Χρειαστείτε

| Προαπαιτούμενο | Γιατί είναι σημαντικό |
|----------------|-----------------------|
| **.NET 6+** (or .NET Framework 4.6+) | Η βιβλιοθήκη Aspose.Words στοχεύει σε σύγχρονα runtime. |
| **Aspose.Words for .NET** NuGet package | Παρέχει τις κλάσεις `Document`, `Shape`, `ShadowEffect` και σχετικές. |
| **A C# IDE** (Visual Studio, Rider, VS Code) | Κάνει το debugging και την εκτέλεση του δείγματος εύκολη. |
| **Basic C# knowledge** | Θα κατανοήσετε τη σύνταξη χωρίς να χρειάζεται εκτενής εμβάθυνση. |

```bash
dotnet add package Aspose.Words
```

Αυτό είναι—χωρίς επιπλέον DLLs, χωρίς εγγενείς εξαρτήσεις. Μόλις το πακέτο είναι στη θέση του, ο κώδικας παρακάτω θα μεταγλωττιστεί και θα εκτελεστεί.

---

## Υλοποίηση Βήμα‑Βήμα

Παρακάτω χωρίζουμε τη διαδικασία σε πέντε λογικά βήματα. Κάθε βήμα έχει σαφή επικεφαλίδα (ώστε τα μοντέλα AI να το ευρετηριάσουν) και ένα σύντομο μπλοκ κώδικα που μπορείτε να αντιγράψετε‑και‑επικολλήσετε απευθείας.

### ## 1. Δημιουργία Εγγράφου PDF και Προετοιμασία Καμβά

Το πρώτο πράγμα που κάνουμε είναι να δημιουργήσουμε ένα αντικείμενο `Document`. Σκεφτείτε το ως έναν κενό καμβά που τελικά θα γίνει το αρχείο PDF σας.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document – this is the PDF document we will build.
        Document document = new Document();

        // The rest of the steps follow inside this method.
```

> **Γιατί;** Το `Document` περιέχει όλα τα sections, paragraphs και shapes. Ξεκινώντας με ένα καθαρό αντικείμενο εξασφαλίζετε ότι δεν υπάρχουν κρυφά υπολείμματα από προηγούμενες εκτελέσεις.

### ## 2. Προσθήκη Σχήματος Ορθογωνίου – Ορισμός Χρώματος Γεμίσματος και Μεγέθους Σχήματος

Τώρα δημιουργούμε ένα ορθογώνιο, του δίνουμε ένα φωτεινό κίτρινο γέμισμα και ορίζουμε τις διαστάσεις του. Αυτό καλύπτει τόσο το **add rectangle shape** όσο και το **set fill color** καθώς και το **set shape size**.

```csharp
        // Step 2: Create a rectangle shape.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Set the width and height – this is where we set the shape size.
        rectangle.Width = 200;   // 200 points (≈2.78 inches)
        rectangle.Height = 100;  // 100 points (≈1.39 inches)

        // Apply a fill color – here we use a vivid yellow.
        rectangle.FillColor = Color.Yellow;
```

> **Σημείωση:** Το πλάτος/ύψος μετρώνται σε points (1 point = 1/72 ίντσα). Προσαρμόστε αυτούς τους αριθμούς ώστε να ταιριάζουν στο layout σας.

### ## 3. Εφαρμογή Εξωτερικής Σκιάς και Ορισμός Διαφάνειας Σχήματος

Οι σκιές προσθέτουν βάθος, και ο έλεγχος της αδιαφάνειά τους αποτελεί την ουσία του **set shape transparency**. Παρακάτω διαμορφώνουμε μια γκρι εξωτερική σκιά με 30 % διαφάνεια.

```csharp
        // Step 3: Configure the outer shadow effect.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;          // Shadow hue
        shadow.BlurRadius = 5.0;            // How fuzzy the shadow appears
        shadow.DistanceX = 4;               // Horizontal offset
        shadow.DistanceY = 4;               // Vertical offset
        shadow.Transparency = 0.3;          // 0 = opaque, 1 = fully transparent
        shadow.Style = ShadowStyle.Outer;   // Make it an outer shadow
```

> **Γιατί να ορίσετε διαφάνεια;** Μια σκιά με 30 % διαφάνεια φαίνεται διακριτική, αποτρέποντας το ορθογώνιο να φαίνεται «επίπεδο» στη σελίδα.

### ## 4. Εισαγωγή του Σχήματος στο Σώμα του Εγγράφου

Τώρα τοποθετούμε το ορθογώνιο στην πρώτη παράγραφο του πρώτου section του εγγράφου. Αυτό το βήμα ενώνει όλα τα παραπάνω.

```csharp
        // Step 4: Insert the rectangle into the first paragraph.
        // If the document has no paragraphs yet, Aspose creates one automatically.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);
```

> **Ακρόατο σενάριο:** Αν χρειάζεστε το σχήμα σε νέα σελίδα, προσθέστε πριν από την προσθήκη του σχήματος την εντολή `document.Sections[0].PageSetup.SectionStart = SectionStart.NewPage;`.

### ## 5. Αποθήκευση του Εγγράφου ως Αρχείο PDF

Τέλος, αποθηκεύουμε τη δομή στη μνήμη σε ένα φυσικό αρχείο PDF. Το αρχείο θα γραφτεί στον φάκελο που θα ορίσετε.

```csharp
        // Step 5: Save the document as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF saved successfully to {outputPath}");
    }
}
```

Όταν εκτελέσετε το πρόγραμμα, εμφανίζεται ένα αρχείο με όνομα `shadow.pdf`. Ανοίγοντάς το, βλέπετε ένα κίτρινο ορθογώνιο με μια απαλή γκρι σκιά μετατοπισμένη κατά 4 points—ακριβώς όπως περιγράφει ο κώδικάς μας.

> **Αναμενόμενο αποτέλεσμα:** Ένα PDF μονής σελίδας όπου το ορθογώνιο βρίσκεται κοντά στην επάνω‑αριστερή γωνία της σελίδας, γεμάτο κίτρινο, με μέγεθος 200 × 100 points, και ρίχνει μια ημιδιαφανή εξωτερική σκιά.

---

## Πλήρες Παράδειγμα Εργασίας (Έτοιμο για Αντιγραφή‑Επικόλληση)

Παρακάτω βρίσκεται ολόκληρο το αρχείο πηγαίου κώδικα, έτοιμο για να το ενσωματώσετε σε ένα νέο έργο console.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new empty document – this will become the PDF.
        Document document = new Document();

        // 2️⃣ Add a rectangle shape, set its size and fill color.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.Width = 200;          // shape size – width
        rectangle.Height = 100;         // shape size – height
        rectangle.FillColor = Color.Yellow; // set fill color

        // 3️⃣ Apply an outer shadow and adjust transparency.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;
        shadow.BlurRadius = 5.0;
        shadow.DistanceX = 4;
        shadow.DistanceY = 4;
        shadow.Transparency = 0.3;      // set shape transparency
        shadow.Style = ShadowStyle.Outer;

        // 4️⃣ Insert the shape into the first paragraph of the document.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);

        // 5️⃣ Save everything as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF created at: {outputPath}");
    }
}
```

> **Συμβουλή:** Αντικαταστήστε το `YOUR_DIRECTORY` με μια απόλυτη διαδρομή όπως `C:\Temp` ή μια σχετική όπως `.\output`. Το πρόγραμμα θα δημιουργήσει το φάκελο αν δεν υπάρχει ήδη.

---

## Συχνές Ερωτήσεις (FAQ)

**Q: Μπορώ να αλλάξω τη θέση του ορθογωνίου στη σελίδα;**  
A: Απόλυτα. Ορίστε `rectangle.Left` και `rectangle.Top` (και τα δύο μετρώνται σε points) πριν το προσθέσετε στην παράγραφο.

**Q: Τι γίνεται αν χρειάζομαι διαφανές γέμισμα αντί για διαφανή σκιά;**  
A: Χρησιμοποιήστε `rectangle.FillColor = Color.FromArgb(128, Color.Yellow);` – το πρώτο όρισμα είναι το κανάλι άλφα (0‑255), όπου 128 δίνει περίπου 50 % διαφάνεια.

**Q: Λειτουργεί αυτό με .NET Core;**  
A: Ναι. Το Aspose.Words υποστηρίζει .NET Standard 2.0+, ώστε να μπορείτε να εκτελέσετε τον ίδιο κώδικα σε .NET 6, .NET 7 ή .NET Framework 4.6+.

**Q: Πώς μπορώ να προσθέσω πολλαπλά σχήματα;**  
A: Απλώς επαναλάβετε τα βήματα 2‑4 για κάθε σχήμα, ενδεχομένως τοποθετώντας τα σε διαφορετικές παραγράφους ή sections.

---

## Συμπέρασμα

Μόλις **δημιουργήσαμε ένα έγγραφο PDF** από την αρχή, **προσθέσαμε ένα σχήμα ορθογωνίου**, **ορίσαμε το χρώμα γεμίσματος**, **καθορίσαμε το μέγεθός του**, και **ρυθμίσαμε τη διαφάνεια του σχήματος** για να πετύχουμε ένα επαγγελματικό εφέ σκιάς. Ο κώδικας παραδείγματος είναι αυτόνομος, εκτελείται σε λιγότερο από ένα λεπτό, και δείχνει τις βασικές έννοιες που θα χρειαστείτε για πιο σύνθετες διατάξεις PDF.

Έτοιμοι για την επόμενη πρόκληση; Δοκιμάστε να αντικαταστήσετε το ορθογώνιο με σχήμα με στρογγυλεμένες γωνίες, να ενσωματώσετε μια εικόνα μέσα στο σχήμα, ή να δημιουργήσετε αυτόματα έναν πίνακα περιεχομένων. Το ίδιο API σας επιτρέπει να στρώσετε κείμενο, εικόνες και διανύσματα—οπότε δεν υπάρχουν όρια.

Αν βρήκατε αυτόν τον οδηγό χρήσιμο, δώστε του ένα αστέρι στο GitHub, μοιραστείτε τον με έναν συνεργάτη, ή αφήστε ένα σχόλιο με τις δικές σας παραλλαγές. Καλή προγραμματιστική!

---

![παράδειγμα δημιουργίας εγγράφου pdf με σχήμα ορθογωνίου](/images/rectangle-shadow.png "Στιγμιότυπο που δείχνει το δημιουργημένο PDF με κίτρινο ορθογώνιο και γκρι εξωτερική σκιά")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}