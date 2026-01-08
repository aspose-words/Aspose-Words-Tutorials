---
category: general
date: 2025-12-25
description: Πώς να προσθέσετε σκιά σε C# με ένα απλό παράδειγμα κώδικα. Μάθετε πώς
  να ορίσετε την απόσταση της σκιάς, να προσαρμόσετε το χρώμα και να δημιουργήσετε
  βάθος για τα γραφικά σας.
draft: false
keywords:
- how to add shadow
- how to set shadow distance
language: el
og_description: Πώς να προσθέσετε σκιά σε C# εξηγείται βήμα‑προς‑βήμα. Ακολουθήστε
  τον οδηγό για να ορίσετε την απόσταση σκιάς, το χρώμα και το θόλωμα για σχήματα
  με επαγγελματική εμφάνιση.
og_title: Πώς να προσθέσετε σκιά σε C# – Πλήρης οδηγός προγραμματισμού
tags:
- C#
- graphics
- Aspose.Words
- shadows
title: Πώς να προσθέσετε σκιά σε C# – Πλήρης οδηγός προγραμματισμού
url: /el/python/images-shapes/how-to-add-shadow-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Προσθέσετε Σκιά σε C# – Πλήρης Οδηγός Προγραμματισμού

Η προσθήκη σκιάς σε C# είναι μια συχνή ανάγκη όταν θέλετε τα γραφικά σας να ξεχωρίζουν από τη σελίδα. Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα τις ακριβείς διαδικασίες για να ρυθμίσετε τη σκιά ενός σχήματος, συμπεριλαμβανομένου του πώς να ορίσετε την απόσταση σκιάς, να προσαρμόσετε τη θόλωση και να επιλέξετε το σωστό χρώμα.

Αν έχετε ποτέ κοίταξει ένα επίπεδο ορθογώνιο και σκεφτείτε «αυτό θα μπορούσε να έχει λίγο βάθος», βρίσκεστε στο σωστό μέρος. Θα ξεκινήσουμε από ένα κενό έγγραφο, θα προσθέσουμε ένα σχήμα και θα ολοκληρώσουμε με μια επεξεργασμένη σκιά που φαίνεται σαν να την τοποθέτησε ένας σχεδιαστής. Χωρίς περιττές πληροφορίες, μόνο ένα πρακτικό, εκτελέσιμο παράδειγμα που μπορείτε να αντιγράψετε‑επικολλήσετε σήμερα.

## Τι Θα Μάθετε

- Δημιουργήστε ένα νέο έγγραφο και εισάγετε ένα σχήμα προγραμματιστικά.  
- Εφαρμόστε μια ήπια θόλωση στη σκιά του σχήματος.  
- **Πώς να ορίσετε την απόσταση σκιάς** ώστε η σκιά να εμφανίζεται φυσικά μετατοπισμένη.  
- Επιλέξτε ένα χρώμα σκιάς που λειτουργεί σε οποιοδήποτε φόντο.  
- Αποθηκεύστε το αποτέλεσμα ως PDF (ή οποιαδήποτε μορφή χρειάζεστε).  

### Προαπαιτούμενα

- .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί με .NET Core και .NET Framework).  
- Aspose.Words for .NET (δωρεάν δοκιμή ή έκδοση με άδεια).  
- Βασική κατανόηση της σύνταξης C#.

Αυτό είναι όλο—χωρίς επιπλέον βιβλιοθήκες, χωρίς μαγεία. Ας βουτήξουμε.

![Παράδειγμα σχήματος με ήπια μαύρη σκιά – πώς να προσθέσετε σκιά](https://example.com/placeholder-shadow.png "παράδειγμα προσθήκης σκιάς")

## Βήμα 1: Ρύθμιση του Έργου και Εισαγωγή Ονομάτων Χώρων

Πρώτα, δημιουργήστε μια νέα εφαρμογή κονσόλας (ή οποιοδήποτε έργο C#) και προσθέστε το πακέτο NuGet Aspose.Words:

```bash
dotnet new console -n ShadowDemo
cd ShadowDemo
dotnet add package Aspose.Words
```

Τώρα ανοίξτε το `Program.cs` και φέρτε τα απαιτούμενα ονόματα χώρων στην εμβέλεια:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shadows;
using Aspose.Words.Drawing.Shapes;
using Aspose.Words.Saving;
```

> **Συμβουλή:** Εάν χρησιμοποιείτε το Visual Studio, το IDE θα προτείνει τις δηλώσεις `using` καθώς πληκτρολογείτε `Document`.

## Βήμα 2: Δημιουργία Νέου Εγγράφου και Προσθήκη Σχήματος

Με τις βιβλιοθήκες έτοιμες, μπορούμε να δημιουργήσουμε ένα αντικείμενο `Document` και να τοποθετήσουμε ένα απλό ορθογώνιο στην πρώτη σελίδα.

```csharp
// Step 2: Initialize the document
Document doc = new Document();

// Add a blank page (Aspose.Words creates one automatically)
Section section = doc.FirstSection;

// Insert a rectangle shape – this will be the object we give a shadow
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    // Size the shape (width, height) in points (1 point = 1/72 inch)
    Width = 200,
    Height = 100,
    
    // Position the shape 100 points from the left and 150 from the top
    Left = 100,
    Top = 150,
    
    // Fill the shape with a light gray so the shadow stands out
    FillColor = System.Drawing.Color.LightGray
};

// Add the shape to the document's first page
section.Body.FirstParagraph.AppendChild(rectangle);
```

Γιατί ένα ορθογώνιο; Είναι ένας ουδέτερος καμβάς που επιτρέπει την αξιολόγηση του εφέ της σκιάς χωρίς περισπασμούς. Μπορείτε να αντικαταστήσετε το `ShapeType.Rectangle` με `Ellipse` ή `Star`—η λογική της σκιάς παραμένει η ίδια.

## Βήμα 3: Πώς να Προσθέσετε Σκιά – Εφαρμογή Θόλωσης, Απόστασης και Χρώματος

Τώρα έρχεται η καρδιά του tutorial: **πώς να προσθέσετε σκιά** σε αυτό το ορθογώνιο. Το Aspose.Words εκθέτει ένα αντικείμενο `Shadow` σε κάθε σχήμα, επιτρέποντάς σας να ρυθμίσετε τη θόλωση, την απόσταση και το χρώμα.

```csharp
// Step 3: Access the shape's shadow settings
Shadow shadow = rectangle.Shadow;

// 3a) Apply a soft blur – larger values make the shadow fuzzier
shadow.Blur = 5.0;          // 5 points blur gives a subtle, professional look

// 3b) Set the shadow's offset distance – this determines how far the shadow is displaced
shadow.Distance = 3.0;      // 3 points offset is enough to suggest depth without looking detached

// 3c) Choose a shadow color – black works on most backgrounds, but you can experiment
shadow.Color = Color.Black; // Solid black; you could use Color.FromArgb(128, 0, 0, 0) for semi‑transparent

// OPTIONAL: Rotate the shadow to match a light source direction (45 degrees works well)
shadow.Angle = 45.0;
```

Παρατηρήστε το σχόλιο `// 3b) Set the shadow's offset distance`. Αυτή η γραμμή απαντά άμεσα στο **πώς να ορίσετε την απόσταση σκιάς**. Με την προσαρμογή του `shadow.Distance`, ελέγχετε το οπτικό κενό μεταξύ του σχήματος και της σκιάς του, μιμούμενοι μια πηγή φωτός τοποθετημένη σε συγκεκριμένη γωνία.

### Γιατί Αυτές οι Τιμές;

- **Blur = 5.0** – Μια ήπια θόλωση αποτρέπει μια σκληρή σιλουέτα ενώ παραμένει ορατή.  
- **Distance = 3.0** – Κρατά τη σκιά αρκετά κοντά ώστε να φαίνεται ότι προέρχεται από το ίδιο το σχήμα.  
- **Color = Black** – Εξασφαλίζει αντίθεση τόσο σε φωτεινά όσο και σε σκούρα φόντα.  

Νιώστε ελεύθεροι να τροποποιήσετε αυτούς τους αριθμούς· το API δέχεται οποιαδήποτε τιμή `double` χρειάζεστε.

## Βήμα 4: Αποθήκευση του Εγγράφου και Επαλήθευση του Αποτελέσματος

Με τη σκιά ρυθμισμένη, απλώς γράφουμε το αρχείο στο δίσκο. Το Aspose.Words μπορεί να εξάγει σε πολλές μορφές· το PDF είναι μια κοινή επιλογή για κοινή χρήση.

```csharp
// Step 4: Save the document as a PDF (you could also use .docx, .png, etc.)
string outputPath = "ShadowedShape.pdf";
doc.Save(outputPath, SaveFormat.Pdf);

Console.WriteLine($"Document saved to {outputPath}. Open it to see the shadow effect.");
```

Ανοίξτε το `ShadowedShape.pdf` και θα δείτε ένα γκρι ορθογώνιο με μια ήπια μαύρη σκιά ελαφρώς μετατοπισμένη προς τα κάτω‑δεξιά. Αν η σκιά φαίνεται πολύ αχνή, αυξήστε το `shadow.Blur` ή το `shadow.Distance` και ξανατρέξτε.

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

### Τι γίνεται αν χρειάζομαι διαφανή σκιά;

Χρησιμοποιήστε ένα χρώμα ARGB με κανάλι άλφα μικρότερο από 255:

```csharp
shadow.Color = Color.FromArgb(80, 0, 0, 0); // 80/255 opacity = ~31% transparent
```

### Μπορώ να εφαρμόσω την ίδια σκιά σε πολλαπλά σχήματα;

Απόλυτα. Δημιουργήστε μια βοηθητική μέθοδο:

```csharp
static void ApplyStandardShadow(Shape shape)
{
    shape.Shadow.Blur = 5.0;
    shape.Shadow.Distance = 3.0;
    shape.Shadow.Color = Color.Black;
}
```

Καλέστε το `ApplyStandardShadow(rectangle);` για κάθε σχήμα που προσθέτετε.

### Λειτουργεί αυτό με παλαιότερες εκδόσεις του .NET Framework;

Ναι. Το Aspose.Words 22.9+ υποστηρίζει .NET Framework 4.5 και άνω. Απλώς προσαρμόστε το αρχείο έργου ανάλογα.

## Πλήρες Παράδειγμα Εργασίας

Παρακάτω είναι ολόκληρο το πρόγραμμα που μπορείτε να αντιγράψετε στο `Program.cs`. Συγκεντρώνεται και εκτελείται αμέσως (υπό την προϋπόθεση ότι το πακέτο NuGet είναι εγκατεστημένο).

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shadows;
using Aspose.Words.Drawing.Shapes;
using Aspose.Words.Saving;

namespace ShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Initialize the document
            Document doc = new Document();
            Section section = doc.FirstSection;

            // Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100,
                Left = 100,
                Top = 150,
                FillColor = System.Drawing.Color.LightGray
            };
            section.Body.FirstParagraph.AppendChild(rectangle);

            // Apply shadow – this is the core of "how to add shadow"
            Shadow shadow = rectangle.Shadow;
            shadow.Blur = 5.0;                // Soft blur
            shadow.Distance = 3.0;            // How to set shadow distance
            shadow.Color = Color.Black;       // Classic black shadow
            shadow.Angle = 45.0;              // Light source direction

            // Save as PDF
            string outputPath = "ShadowedShape.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);

            Console.WriteLine($"Document saved to {outputPath}. Open it to see the shadow effect.");
        }
    }
}
```

Τρέξτε το πρόγραμμα:

```bash
dotnet run
```

Θα βρείτε το `ShadowedShape.pdf` στον φάκελο του έργου. Ανοίξτε το με οποιονδήποτε προβολέα PDF για να επιβεβαιώσετε ότι η σκιά φαίνεται όπως περιγράφηκε.

## Συμπέρασμα

Καλύψαμε **πώς να προσθέσετε σκιά** σε ένα σχήμα σε C# από την αρχή μέχρι το τέλος, και δείξαμε **πώς να ορίσετε την απόσταση σκιάς** μαζί με τη θόλωση και το χρώμα. Με λίγες μόνο γραμμές κώδικα μπορείτε να δώσετε στα γραφικά σας μια επαγγελματική, τρισδιάστατη αίσθηση—χωρίς εξωτερικά εργαλεία σχεδίασης.

Τώρα που έχετε κατακτήσει τα βασικά, δοκιμάστε να πειραματιστείτε:

- Αλλάξτε το χρώμα της σκιάς σε ένα ήπιο μπλε για πιο δροσερή αίσθηση.  
- Αυξήστε τη θόλωση για ένα ονειρικό, διάχυτο αποτέλεσμα.  
- Εφαρμόστε την ίδια τεχνική σε διαγράμματα, εικόνες ή πλαίσια κειμένου.  

Κάθε παραλλαγή ενισχύει τις ίδιες βασικές έννοιες, ώστε να αισθάνεστε άνετα να προσαρμόζετε σκιάς για οποιοδήποτε σενάριο.  

Έχετε περισσότερες ερωτήσεις; Αφήστε ένα σχόλιο, και καλή προγραμματιστική δουλειά!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}