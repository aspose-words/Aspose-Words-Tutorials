---
category: general
date: 2026-03-27
description: Δημιουργήστε έγγραφο Word με C# και μάθετε πώς να προσθέσετε σχήμα, να
  εφαρμόσετε σκιά στο σχήμα και να ορίσετε την απόσταση της σκιάς. Οδηγός βήμα‑βήμα
  για το Aspose.Words.
draft: false
keywords:
- create word document c#
- how to add shape
- apply shadow to shape
- how to create rectangle
- set shadow distance
language: el
og_description: Δημιουργήστε έγγραφο Word με C# με σχήμα ορθογωνίου και προσαρμοσμένη
  σκιά. Ακολουθήστε αυτό το πλήρες σεμινάριο για να ορίσετε την απόσταση και το στυλ
  της σκιάς.
og_title: Δημιουργία εγγράφου Word C# – Προσθήκη σχήματος με σκιά
tags:
- Aspose.Words
- C#
- Document Automation
title: Δημιουργία εγγράφου Word C# – Προσθήκη σχήματος με σκιά
url: /el/net/programming-with-shapes/create-word-document-c-add-shape-with-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία Word Document C# – Προσθήκη Σχήματος με Σκιά

Έχετε ποτέ χρειαστεί να **create word document c#** που περιέχει ένα ωραία μορφοποιημένο ορθογώνιο; Ίσως δημιουργείτε ένα πρότυπο αναφοράς και θέλετε μια διακριτική σκιά πτώσης για να αναδείξετε τη διάταξη. Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα από αυτό – πώς να προσθέσετε σχήμα, να εφαρμόσετε σκιά στο σχήμα και ακόμη να ρυθμίσετε την απόσταση της σκιάς χρησιμοποιώντας το Aspose.Words.

Θα ξεκινήσουμε με ένα κενό έγγραφο, θα προσθέσουμε ένα ορθογώνιο, θα του δώσουμε μια προεπιλεγμένη σκιά και θα ολοκληρώσουμε αποθηκεύοντας το αρχείο. Στο τέλος θα έχετε ένα έτοιμο .docx που μπορείτε να ανοίξετε στο Word και να δείτε το αποτέλεσμα αμέσως. Χωρίς εξωτερικά εργαλεία, μόνο καθαρός κώδικας C#.

## Προαπαιτούμενα

- .NET 6 (ή οποιοδήποτε πρόσφατο .NET Framework) εγκατεστημένο.
- Visual Studio 2022 ή VS Code με επέκταση C#.
- Πακέτο NuGet Aspose.Words για .NET (`Aspose.Words` έκδοση 23.12 ή νεότερη).  
  Μπορείτε να το προσθέσετε μέσω του Package Manager Console:

  ```powershell
  Install-Package Aspose.Words
  ```

Αυτό είναι όλο – δεν απαιτούνται επιπλέον DLL ή COM interop.

## Βήμα 1: Αρχικοποίηση Νέου Εγγράφου και Builder – *create word document c#* Βασικά

Αρχικά χρειαζόμαστε ένα αντικείμενο `Document` που αντιπροσωπεύει το αρχείο Word και ένα `DocumentBuilder` για την επεξεργασία του.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create a blank Word document
Document document = new Document();

// DocumentBuilder lets us add content programmatically
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Γιατί είναι σημαντικό αυτό το βήμα:** Η κλάση `Document` είναι ο κοντέινερ για όλα τα μέρη του Word (σελίδες, στυλ, εικόνες). Ο builder είναι το υψηλού επιπέδου API που αφαιρεί την ανάγκη για χαμηλού επιπέδου χειρισμό κόμβων, κάνοντας εύκολο το **create word document c#** χωρίς να ασχοληθείτε άμεσα με XML.

## Βήμα 2: Εισαγωγή Σχήματος Ορθογωνίου – *how to create rectangle*  

Τώρα θα τοποθετήσουμε ένα ορθογώνιο στη σελίδα. Το μέγεθος εκφράζεται σε points (1 pt ≈ 1/72 in).

```csharp
// Insert a rectangle 200 pt wide and 100 pt tall
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);

// Give the rectangle a light‑blue fill so we can see it clearly
rectangleShape.FillColor = Color.LightBlue;
```

> **Συμβουλή:** Αν χρειάζεστε διαφορετικό σχήμα, απλώς αντικαταστήστε το `ShapeType.Rectangle` με `ShapeType.Ellipse`, `ShapeType.Triangle`, κ.λπ. Ο ίδιος κώδικας λειτουργεί για **how to add shape** οποιουδήποτε τύπου.

## Βήμα 3: Εφαρμογή Προεπιλεγμένης Σκιάς και Λεπτομερής Ρύθμιση – *apply shadow to shape*  

Το Aspose.Words περιλαμβάνει αρκετές προεπιλεγμένες μορφές σκιάς. Θα χρησιμοποιήσουμε το `Preset1` και στη συνέχεια θα προσαρμόσουμε την απόσταση, το θολό, τη διαφάνεια και το χρώμα.

```csharp
// Choose a predefined shadow style
rectangleShape.Shadow.Format = ShadowFormat.Preset1;

// Adjust the shadow distance – this is the offset from the shape
rectangleShape.Shadow.Distance = 5; // measured in points

// Make the edge of the shadow a little fuzzy
rectangleShape.Shadow.BlurRadius = 3;

// Set the shadow to be 40 % transparent (0 = opaque, 1 = fully transparent)
rectangleShape.Shadow.Transparency = 0.4;

// Pick a gray tone for the shadow color
rectangleShape.Shadow.Color = Color.Gray;
```

> **Γιατί να προσαρμόσετε τη σκιά;** Η ιδιότητα `Distance` ελέγχει πόσο μακριά βρίσκεται η σκιά από το ορθογώνιο – σκεφτείτε το ως το «υψόμετρο» που βλέπετε σε μια 3‑Δ απόδοση. Η αλλαγή του `BlurRadius` μαλακώνει τις άκρες, ενώ η `Transparency` σας επιτρέπει να δημιουργήσετε ένα διακριτικό, επαγγελματικό αποτέλεσμα. Αυτό καλύπτει την απαίτηση **set shadow distance** και σας δείχνει πώς να **apply shadow to shape** με ευέλικτο τρόπο.

## Βήμα 4: Αποθήκευση Εγγράφου – *create word document c#* Ολοκλήρωση

Τέλος, γράψτε το έγγραφο στο δίσκο. Προσαρμόστε τη διαδρομή σε έναν φάκελο στον οποίο έχετε δικαιώματα εγγραφής.

```csharp
// Save the document as a .docx file
string outputPath = @"C:\Temp\ShadowShape.docx";
document.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Ανοίξτε το παραγόμενο αρχείο στο Microsoft Word και θα δείτε ένα ανοιχτό‑μπλε ορθογώνιο με μια απαλή γκρι σκιά μετατοπισμένη κατά 5 pt. Αυτό είναι η οπτική απόδειξη ότι δημιουργήσατε επιτυχώς **create word document c#** με ένα μορφοποιημένο σχήμα.

![Δημιουργία Word Document C# με Σχήμα με Σκιά](shadow-example.png){: .img alt="παράδειγμα δημιουργίας word document c# με ορθογώνιο και σκιά"}

## Προαιρετικές Παραλλαγές & Περιπτώσεις Ορίων

| Scenario | What to Change | Why it Matters |
|----------|----------------|----------------|
| **Διαφορετικό στυλ σκιάς** | `rectangleShape.Shadow.Format = ShadowFormat.Preset3;` | Σας δίνει πιο δραματική εμφάνιση χωρίς επιπλέον κώδικα. |
| **Χωρίς προεπιλογή – προσαρμοσμένη σκιά** | Omit `Format` and set `OffsetX`, `OffsetY` manually. | Πλήρης έλεγχος πάνω στην κατεύθυνση και το βάθος. |
| **Πολλαπλά σχήματα** | Call `builder.InsertShape` again before saving. | Χρήσιμο για σύνθετα πρότυπα με εικονίδια, λογότυπα κ.λπ. |
| **Συμβατότητα με παλαιότερες εκδόσεις Aspose** | Use `ShadowEffect` class (available in v20.x). | Εξασφαλίζει ότι ο κώδικάς σας λειτουργεί σε παλαιά έργα. |
| **Αποθήκευση ως PDF** | `document.Save("ShadowShape.pdf");` | Η ίδια απόδοση σκιάς εμφανίζεται στην έξοδο PDF. |

> **Συχνή ερώτηση:** *Τι γίνεται αν η σκιά δεν εμφανίζεται στο Word;*  
> Βεβαιωθείτε ότι χρησιμοποιείτε μια πρόσφατη έκδοση του Aspose.Words (≥ 22.9). Οι παλαιότερες εκδόσεις είχαν περιορισμένη υποστήριξη σκιάς. Επίσης, ελέγξτε ότι το έγγραφο ανοίγει σε μια πρόσφατη έκδοση του Word (2016+).

## Πλήρες Παράδειγμα Λειτουργίας

Παρακάτω βρίσκεται το πλήρες πρόγραμμα, έτοιμο για αντιγραφή‑επικόλληση. Περιλαμβάνει όλες τις οδηγίες `using`, σχόλια και διαχείριση σφαλμάτων για μια ομαλή εμπειρία.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShadowShapeDemo
{
    class Program
    {
        static void Main()
        {
            try
            {
                // 1️⃣ Create a new blank document and a builder
                Document doc = new Document();
                DocumentBuilder builder = new DocumentBuilder(doc);

                // 2️⃣ Insert a rectangle (200 pt × 100 pt) and fill it
                Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
                rect.FillColor = Color.LightBlue;

                // 3️⃣ Apply a preset shadow and tweak its properties
                rect.Shadow.Format = ShadowFormat.Preset1;   // predefined style
                rect.Shadow.Distance = 5;                    // set shadow distance
                rect.Shadow.BlurRadius = 3;                  // soften edges
                rect.Shadow.Transparency = 0.4;              // semi‑transparent
                rect.Shadow.Color = Color.Gray;              // shadow color

                // 4️⃣ Save the document
                string outPath = @"C:\Temp\ShadowShape.docx";
                doc.Save(outPath);

                Console.WriteLine($"✅ Document created successfully at {outPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"❌ Error: {ex.Message}");
            }
        }
    }
}
```

Εκτελέστε το πρόγραμμα, μεταβείτε στο `C:\Temp\ShadowShape.docx` και θα δείτε το ορθογώνιο με την ακριβή σκιά που διαμορφώσαμε.

## Ανακεφαλαίωση & Επόμενα Βήματα

- Τώρα ξέρετε πώς να **create word document c#**, να εισάγετε ένα ορθογώνιο και να **apply shadow to shape** με μια προσαρμοσμένη **set shadow distance**.  
- Το παράδειγμα χρησιμοποιεί το Aspose.Words, το οποίο αφαιρεί τις πολυπλοκότητες του OpenXML και εγγυάται συνεπή απόδοση σε όλες τις εκδόσεις του Word.  
- Θέλετε να προχωρήσετε παραπέρα; Δοκιμάστε να συνδυάσετε πολλαπλά σχήματα, να προσθέσετε κείμενο μέσα στο ορθογώνιο ή να εξάγετε το ίδιο έγγραφο ως PDF για να δείτε πώς μεταφράζεται η σκιά.

### Σχετικά Θέματα που Μπορείτε Να Εξερευνήσετε

- **How to add shape** σε μια κεφαλίδα/υποσέλιδο για branding.  
- Χρήση του **Aspose.Words** για εισαγωγή διαγραμμάτων και πινάκων προγραμματιστικά.  
- Προσαρμογή **shadow effects** σε εικόνες αντί για διανυσματικά σχήματα.  
- Αυτοματοποίηση μαζικής δημιουργίας εγγράφων για τιμολόγια ή πιστοποιητικά.

Μη διστάσετε να πειραματιστείτε, να σπάσετε τον κώδικα και μετά να τον ξαναχτίσετε – αυτός είναι ο πιο γρήγορος τρόπος να εδραιώσετε τις έννοιες. Αν αντιμετωπίσετε πρόβλημα, αφήστε ένα σχόλιο παρακάτω ή ελέγξτε την επίσημη τεκμηρίωση του Aspose.Words για πιο λεπτομερείς πληροφορίες API.

Καλό κώδικα και απολαύστε το να κάνετε τα Word αρχεία σας να φαίνονται λίγο πιο επαγγελματικά!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}