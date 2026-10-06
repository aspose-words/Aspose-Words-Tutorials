---
category: general
date: 2026-03-06
description: Δημιουργήστε σχήμα ορθογωνίου στο Word και προσθέστε σκιά στο σχήμα με
  το Aspose.Words. Μάθετε πώς να εισάγετε ορθογώνιο στο Word και πώς να προσθέσετε
  σκιά σε σχήμα σε C#.
draft: false
keywords:
- create rectangle shape
- add shape shadow
- how to insert rectangle in word
- how to add shadow to shape
language: el
og_description: Δημιουργήστε σχήμα ορθογωνίου στο Word και προσθέστε σκιά στο σχήμα
  με το Aspose.Words. Οδηγός βήμα‑βήμα για το πώς να εισάγετε ορθογώνιο στο Word και
  πώς να προσθέσετε σκιά στο σχήμα.
og_title: Δημιουργία σχήματος ορθογωνίου με σκιά στο Word χρησιμοποιώντας το Aspose.Words
tags:
- Aspose.Words
- C#
- Word Automation
title: Δημιουργία σχήματος ορθογωνίου με σκιά στο Word χρησιμοποιώντας το Aspose.Words
url: /el/net/programming-with-shapes/create-rectangle-shape-with-shadow-in-word-using-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία σχήματος ορθογωνίου με σκιά στο Word χρησιμοποιώντας Aspose.Words

Έχετε ποτέ χρειαστεί να **create rectangle shape** σε ένα έγγραφο Word αλλά δεν ήξερτε πώς να του δώσετε αυτήν την επαγγελματική εμφάνιση; Δεν είστε μόνοι—οι περισσότεροι προγραμματιστές αντιμετωπίζουν το ίδιο πρόβλημα όταν προσπαθούν για πρώτη φορά να προσθέσουν οπτικό στυλ σε αυτόματα έγγραφα. Τα καλά νέα; Με το Aspose.Words for .NET μπορείτε τόσο να **create rectangle shape** όσο και να **add shape shadow** με λίγες γραμμές C#.

Σε αυτό το tutorial θα δούμε ακριβώς **how to insert rectangle in Word**, έπειτα θα δείξουμε **how to add shadow to shape** ώστε να ξεχωρίζει από τη σελίδα. Στο τέλος θα έχετε ένα έτοιμο‑για‑αποθήκευση `Shadow.docx` που μπορείτε να ανοίξετε στο Word και να δείτε ένα γκρι‑χρωματιστό ορθογώνιο με ήπια σκιά. Χωρίς επιπλέον αρχεία εικόνας, χωρίς χειροκίνητες ρυθμίσεις—απλώς κώδικας.

## Τι θα μάθετε

- Οι ακριβείς δηλώσεις C# που απαιτούνται για **create rectangle shape** με Aspose.Words.  
- Πώς να ενεργοποιήσετε και να διαμορφώσετε μια σκιά χρησιμοποιώντας το αντικείμενο `Shadow`.  
- Γιατί κάθε ιδιότητα είναι σημαντική (π.χ., `Transparency`, `Blur`, `Angle`).  
- Κοινές παγίδες (μονάδες, συμβατότητα εκδόσεων) και γρήγορες λύσεις.  
- Ένα πλήρες, έτοιμο για αντιγραφή‑και‑επικόλληση πρόγραμμα που μπορείτε να εκτελέσετε σήμερα.

### Προαπαιτούμενα

- .NET 6+ (ή .NET Framework 4.7+).  
- Aspose.Words for .NET 23.10 ή νεότερη (το πακέτο NuGet είναι `Aspose.Words`).  
- Βασική κατανόηση του C# και του Visual Studio (ή οποιουδήποτε IDE προτιμάτε).  

Αν τα έχετε ήδη, ας ξεκινήσουμε αμέσως.

---

## Βήμα 1: Ρύθμιση του έργου και εισαγωγή namespaces

Πρώτα, δημιουργήστε μια νέα εφαρμογή console (ή χρησιμοποιήστε μια υπάρχουσα) και προσθέστε το πακέτο NuGet Aspose.Words:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

Τώρα εισάγετε τα απαιτούμενα namespaces στο `Program.cs` σας:

```csharp
using System.Drawing;               // For Color
using Aspose.Words;                  // Core document classes
using Aspose.Words.Drawing;          // Shape and Shadow types
```

> **Pro tip:** Αν στοχεύετε στο .NET 6+, μπορείτε να ενεργοποιήσετε τις καθολικές οδηγίες `using` για να αποφύγετε την επανάληψη αυτών των γραμμών σε κάθε αρχείο.

## Βήμα 2: **Create rectangle shape** σε ένα κενό έγγραφο Word

Θα ξεκινήσουμε με ένα νέο αντικείμενο `Document` και έναν `DocumentBuilder` για να το επεξεργαστούμε. Η μέθοδος `InsertShape` του builder είναι όπου συμβαίνει η μαγεία.

```csharp
// Step 2: Initialize a new document and builder
Document document = new Document();                     // Blank Word file
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle – 200 × 100 points (≈2.78 × 1.39 inches)
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

Γιατί 200 × 100 points; Στο Word, ένα point ισούται με 1/72 ίντσας, έτσι το ορθογώνιο είναι περίπου 2,8 × 1,4 ίντσες—αρκετά μεγάλο για να το παρατηρήσετε αλλά όχι υπερβολικό. Μπορείτε να αλλάξετε αυτούς τους αριθμούς ώστε να ταιριάζουν στο σχέδιό σας· απλώς θυμηθείτε ότι μετρώνται σε **points**, όχι pixels.

## Βήμα 3: **Add shape shadow** – διαμόρφωση της εμφάνισης

Τώρα που έχουμε ένα ορθογώνιο, ας του δώσουμε μια ήπια γκρι σκιά. Το αντικείμενο `Shadow` ανήκει στο `Shape` και εκθέτει αρκετές χρήσιμες ιδιότητες.

```csharp
// Step 3: Turn on the shadow and tweak its appearance
rectangle.Shadow.Enabled = true;               // Switch the shadow on
rectangle.Shadow.Color = Color.Gray;           // Shadow hue
rectangle.Shadow.Transparency = 0.3;           // 30 % transparent – looks softer
rectangle.Shadow.Blur = 5;                     // Blur radius (points)
rectangle.Shadow.Distance = 4;                 // How far the shadow sits from the shape
rectangle.Shadow.Angle = 45;                   // Direction in degrees (45° = down‑right)
rectangle.Shadow.Size = 100;                   // 100 % of the original shape size
```

### Τι κάνει κάθε ιδιότητα

| Ιδιότητα | Επίδραση | Τυπικές τιμές |
|----------|----------|----------------|
| **Enabled** | Ενεργοποιεί/απενεργοποιεί τη σκιά | `true` ή `false` |
| **Color** | Βασικό χρώμα της σκιάς | Οποιοδήποτε `System.Drawing.Color` |
| **Transparency** | Διαφάνεια (0 = αδιαφανής, 1 = αόρατη) | 0.0 – 1.0 |
| **Blur** | Απαλότητα της άκρης | 0 – 10 (υψηλότερο = πιο απαλό) |
| **Distance** | Απόσταση μεταξύ σχήματος και σκιάς | 0 – 20 points |
| **Angle** | Κατεύθυνση από την οποία φαίνεται να έρχεται το φως | 0 – 360 μοίρες |
| **Size** | Κλίμακα της σκιάς σε σχέση με το σχήμα | 0 – 200 % |

> **Γιατί να ασχοληθείτε με αυτές τις ρυθμίσεις;**  
> Η λεπτομερής ρύθμιση της σκιάς σας επιτρέπει να ταιριάξετε τις οδηγίες εταιρικής ταυτότητας (π.χ., μια ήπια διαφάνεια 20 % για επαγγελματική εμφάνιση) χωρίς να χρειάζεται να χρησιμοποιήσετε εξωτερικούς επεξεργαστές εικόνας.

## Βήμα 4: Αποθήκευση του εγγράφου και επαλήθευση του αποτελέσματος

Τέλος, γράψτε το αρχείο στο δίσκο. Μπορείτε να επιλέξετε οποιονδήποτε φάκελο θέλετε· απλώς αντικαταστήστε το `YOUR_DIRECTORY` με μια πραγματική διαδρομή.

```csharp
// Step 4: Persist the document
string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Ανοίξτε το `Shadow.docx` στο Microsoft Word και θα πρέπει να δείτε ένα γκρι ορθογώνιο με ήπια σκιά που είναι μετατοπισμένη κατά 45° γωνία. Αυτό το οπτικό στοιχείο κάνει το σχήμα να φαίνεται «υψωμένο» από τη σελίδα—ακριβώς όπως θα περιμένατε από μια επαγγελματική αναφορά ή τιμολόγιο.

## Πλήρες Παράδειγμα Λειτουργίας

Παρακάτω είναι το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε‑και‑επικολλήσετε στο `Program.cs`. Δεν λείπουν κομμάτια· μεταγλωττίζει και εκτελείται όπως είναι.

```csharp
using System;
using System.Drawing;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape (200 × 100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // 3️⃣ Enable the shape's shadow and configure its appearance
        rectangle.Shadow.Enabled = true;               // Turn the shadow on
        rectangle.Shadow.Color = Color.Gray;           // Shadow colour
        rectangle.Shadow.Transparency = 0.3;           // 30 % transparent
        rectangle.Shadow.Blur = 5;                     // Blur radius
        rectangle.Shadow.Distance = 4;                 // Offset from the shape
        rectangle.Shadow.Angle = 45;                   // Direction in degrees
        rectangle.Shadow.Size = 100;                   // Shadow size as a percentage

        // 4️⃣ Save the document with the shadowed shape
        string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### Αναμενόμενο Αποτέλεσμα

- **Αρχείο:** `Shadow.docx` τοποθετημένο στον φάκελο εκτέλεσης του έργου.  
- **Οπτικό:** Ένα μόνο ορθογώνιο κεντραρισμένο στη σελίδα, γεμάτο με το προεπιλεγμένο λευκό, και μια γκρι σκιά μετατοπισμένη 4 points προς τα κάτω‑δεξιά, ελαφρώς θολή για φυσική εμφάνιση.

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

### 1. Τι γίνεται αν χρειάζομαι διαφορετική μονάδα (π.χ., εκατοστά);

Το Aspose.Words λειτουργεί σε points, αλλά μπορείτε να μετατρέψετε εκατοστά σε points με τον απλό τύπο:
`points = centimeters * 28.3465`.

```csharp
double cmWidth = 5.0; // 5 cm
double cmHeight = 2.5; // 2.5 cm
Shape rectCm = builder.InsertShape(ShapeType.Rectangle,
                                   (float)(cmWidth * 28.3465),
                                   (float)(cmHeight * 28.3465));
```

### 2. Λειτουργεί αυτό με παλαιότερες εκδόσεις του Aspose.Words;

Το API `Shadow` εισήχθη στην έκδοση 14.0. Αν χρησιμοποιείτε παλαιότερη έκδοση, θα χρειαστεί να κάνετε αναβάθμιση μέσω NuGet. Το υπόλοιπο του κώδικα (δημιουργία σχημάτων) είναι σταθερό εδώ και πολλά χρόνια, οπότε δεν θα αντιμετωπίσετε breaking changes.

### 3. Μπορώ να προσθέσω σκιά σε άλλα σχήματα (π.χ., κύκλους);

Απολύτως—οποιοδήποτε αντικείμενο `Shape` εκθέτει την ιδιότητα `Shadow`. Απλώς αντικαταστήστε το `ShapeType.Rectangle` με `ShapeType.Ellipse` ή `ShapeType.Cloud`, και εφαρμόστε τις ίδιες ρυθμίσεις σκιάς.

### 4. Τι γίνεται αν χρειάζομαι χρωματιστή σκιά (π.χ., μπλε για μια μάρκα);

Αντικαταστήστε το `Color.Gray` με οποιοδήποτε `Color` θέλετε:

```csharp
rectangle.Shadow.Color = Color.FromArgb(30, 0, 120); // Dark blue
```

Θυμηθείτε να προσαρμόσετε το `Transparency` ώστε το χρώμα να μην γίνει υπερβολικά κυρίαρχο.

## 🎨 Οπτική Σύνοψη

![δημιουργία σχήματος ορθογωνίου με σκιά στο Word χρησιμοποιώντας Aspose.Words](image-placeholder.png "δημιουργία σχήματος ορθογωνίου με σκιά στο Word χρησιμοποιώντας Aspose.Words")

*Κείμενο alt: δημιουργία σχήματος ορθογωνίου με σκιά στο Word χρησιμοποιώντας Aspose.Words*

Το στιγμιότυπο (placeholder) δείχνει το τελικό έγγραφο—μόνο το ορθογώνιο και τη μαλακή γκρι σκιά του.

## Συμπέρασμα

Τώρα ξέρετε πώς να **create rectangle shape** σε ένα αρχείο Word, **add shape shadow**, και να ρυθμίσετε λεπτομερώς κάθε οπτικό στοιχείο χρησιμοποιώντας το Aspose.Words for .NET. Το σύντομο πρόγραμμα που δημιουργήσαμε καλύπτει ολόκληρη τη ροή εργασίας—από

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}