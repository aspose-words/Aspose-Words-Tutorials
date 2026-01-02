---
category: general
date: 2026-01-02
description: Δημιουργήστε έγγραφο Word με σχήμα ορθογωνίου, ορίστε το χρώμα γεμίσματος
  του σχήματος και αποθηκεύστε το αρχείο docx χρησιμοποιώντας το Aspose.Words. Μάθετε
  πώς να δημιουργήσετε ορθογώνιο με σκιά σε λίγα λεπτά.
draft: false
keywords:
- create word document
- add rectangle shape
- set shape fill color
- save docx file
- how to create rectangle
language: el
og_description: Δημιουργήστε έγγραφο Word με προσαρμοσμένο ορθογώνιο, ορίστε το χρώμα
  γεμίσματος, προσθέστε σκιά και αποθηκεύστε ως DOCX. Πλήρης κώδικας και εξηγήσεις.
og_title: Δημιουργία εγγράφου Word με σχήμα ορθογωνίου – βήμα‑προς‑βήμα
tags:
- Aspose.Words
- C#
- Document Generation
title: Δημιουργία εγγράφου Word με σχήμα ορθογωνίου και σκιά – Πλήρης οδηγός
url: /el/net/programming-with-shapes/create-word-document-with-rectangle-shape-and-shadow-complet/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία Εγγράφου Word με Σχήμα Ορθογωνίου και Σκιά – Οδηγός Βήμα‑Βήμα

Έχετε αναρωτηθεί ποτέ πώς να **δημιουργήσετε έγγραφο word** που περιέχει ένα ωραία μορφοποιημένο ορθογώνιο; Ίσως χρειάζεστε έναν χώρο κράτησης για λογότυπο, μια χρωματιστή λωρίδα ή απλώς ένα οπτικό στοιχείο σε μια αναφορά. Σε αυτό το tutorial θα **προσθέσουμε σχήμα ορθογωνίου**, θα του δώσουμε χρώμα γεμίσματος, θα εφαρμόσουμε μια διακριτική σκιά και τελικά θα **αποθηκεύσουμε το αρχείο docx** – όλα με το Aspose.Words for .NET.

Θα αποκτήσετε ένα έτοιμο προς εκτέλεση απόσπασμα C#, μια σαφή εξήγηση κάθε γραμμής και μια σειρά συμβουλών που μπορείτε να επαναχρησιμοποιήσετε στα δικά σας έργα. Χωρίς περιττές πληροφορίες, μόνο μια πρακτική λύση που μπορείτε να αντιγράψετε‑και‑επικολλήσετε.

## Τι Θα Χρειαστείτε

- .NET 6 ή νεότερο (ο κώδικας λειτουργεί και σε .NET Framework)  
- Visual Studio 2022 (ή οποιονδήποτε επεξεργαστή προτιμάτε)  
- **Aspose.Words** πακέτο NuGet (`Install-Package Aspose.Words`)  

Αν τα έχετε ήδη, τέλεια – ας ξεκινήσουμε.

## Βήμα 1 – Αρχικοποίηση Νέου Εγγράφου (Πώς να δημιουργήσετε έγγραφο word)

Το πρώτο που πρέπει να κάνετε είναι **να δημιουργήσετε έγγραφο word** στη μνήμη. Σκεφτείτε το ως το άνοιγμα ενός κεννού καμβά όπου θα σχεδιάσετε αργότερα το ορθογώνιο σας.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // for Color struct

// Create a fresh, empty document
Document document = new Document();

// DocumentBuilder helps us add content step‑by‑step
DocumentBuilder builder = new DocumentBuilder(document);

// Write a simple heading so you can see something when you open the file
builder.Writeln("Shadow Demo");
```

> **Γιατί είναι σημαντικό:** `Document` αντιπροσωπεύει ολόκληρο το αρχείο DOCX, ενώ το `DocumentBuilder` είναι ένας βολικός βοηθός που σας επιτρέπει να εισάγετε κείμενο, πίνακες, εικόνες και σχήματα χωρίς να χειρίζεστε χειροκίνητα το υποκείμενο δέντρο κόμβων.

## Βήμα 2 – Εισαγωγή Σχήματος Ορθογωνίου (Προσθήκη σχήματος ορθογωνίου)

Τώρα θα **προσθέσουμε σχήμα ορθογωνίου** στο έγγραφο. Η μέθοδος `InsertShape` δέχεται τον τύπο του σχήματος και τις διαστάσεις του σε points (1 point = 1/72 ίντσα).

```csharp
// Insert a rectangle that will later receive a custom shadow
Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);

// Give the rectangle a light‑blue background so it stands out
rect.FillColor = Color.LightBlue;
```

> **Pro tip:** Αν χρειαστεί ποτέ να δημιουργήσετε διαφορετική γεωμετρία (έλλειψη, τρίγωνο κ.λπ.), απλώς αλλάξτε το `ShapeType.Rectangle` στην αντίστοιχη τιμή του enum.

## Βήμα 3 – Διαμόρφωση της Σκιάς (Ορισμός χρώματος γεμίσματος σχήματος & σκιά)

Μια σκιά μπορεί να κάνει ένα επίπεδο σχήμα να φαίνεται πιο τρισδιάστατο. Εδώ ενεργοποιούμε τη σκιά και ρυθμίζουμε την εμφάνισή της.

```csharp
// Turn the shadow on
rect.ShadowFormat.Enabled = true;

// Choose a subtle gray for the shadow color
rect.ShadowFormat.Color = Color.Gray;

// Blur softens the edge of the shadow – 8 points looks nice
rect.ShadowFormat.BlurRadius = 8;

// Distance controls how far the shadow is offset from the shape
rect.ShadowFormat.Distance = 5;

// Angle determines the direction; 45° gives a bottom‑right offset
rect.ShadowFormat.Angle = 45;

// Transparency makes the shadow partially see‑through (0 = opaque, 1 = invisible)
rect.ShadowFormat.Transparency = 0.3; // 30 % transparent
```

> **Γιατί αυτές οι τιμές;** Μια μέτρια ακτίνα θολώματος και απόσταση 5 points κρατούν τη σκιά από το να κυριαρχεί στο σχήμα, ενώ η γωνία 45° προσομοιώνει μια πηγή φωτός που έρχεται από πάνω‑αριστερά – μια κοινή σύμβαση UI.

## Βήμα 4 – Αποθήκευση του Εγγράφου (Αποθήκευση αρχείου docx)

Τέλος, **αποθηκεύουμε το αρχείο docx** στο δίσκο. Προσαρμόστε τη διαδρομή ώστε να ταιριάζει στο περιβάλλον σας.

```csharp
// Replace with the folder you actually want to use
string outputPath = @"C:\Temp\ShadowDemo.docx";

// Persist the document as a .docx file
document.Save(outputPath);
```

Όταν ανοίξετε το `ShadowDemo.docx` στο Word, θα δείτε ένα ανοιχτό‑μπλε ορθογώνιο με μια απαλή γκρι σκιά, όπως στην παρακάτω εικόνα.

![Create Word Document with rectangle shape and shadow](https://example.com/images/rectangle-shadow.png "Create Word Document with rectangle shape and shadow")

*Image alt text:* **Create Word Document** που εμφανίζει ένα σχήμα ορθογωνίου με σκιά.

## Πλήρες, Έτοιμο‑για‑Εκτέλεση Παράδειγμα (Πώς να δημιουργήσετε ορθογώνιο και να αποθηκεύσετε)

Συνδυάζοντας όλα τα παραπάνω, εδώ είναι το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε σε μια εφαρμογή console:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace AsposeRectangleDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 1: Initialize the document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);
            builder.Writeln("Shadow Demo");

            // Step 2: Insert the rectangle
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
            rect.FillColor = Color.LightBlue;   // set shape fill color

            // Step 3: Apply shadow formatting
            rect.ShadowFormat.Enabled = true;
            rect.ShadowFormat.Color = Color.Gray;
            rect.ShadowFormat.BlurRadius = 8;
            rect.ShadowFormat.Distance = 5;
            rect.ShadowFormat.Angle = 45;
            rect.ShadowFormat.Transparency = 0.3;

            // Step 4: Save the file
            string output = @"C:\Temp\ShadowDemo.docx";
            doc.Save(output);

            System.Console.WriteLine($"Document saved to {output}");
        }
    }
}
```

### Αναμενόμενο Αποτέλεσμα

- Ένα αρχείο με όνομα **ShadowDemo.docx** εμφανίζεται στον προορισμό.  
- Το άνοιγμα του στο Microsoft Word δείχνει μια μοναδική σελίδα με το κείμενο “Shadow Demo” ακολουθούμενο από ένα ανοιχτό‑μπλε ορθογώνιο.  
- Το ορθογώνιο ρίχνει μια απαλή γκρι σκιά με γωνία 45°, δίνοντάς του μια ελαφριά αίσθηση 3‑D.

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

### Τι γίνεται αν χρειαστώ διαφορετικό μέγεθος;

Απλώς αλλάξτε τα ορίσματα `200, 100` στη `InsertShape`. Αυτοί οι αριθμοί είναι το πλάτος και το ύψος σε points. Για τετράγωνο, χρησιμοποιήστε ίσες τιμές.

### Μπορώ να κάνω τη σκιά πιο έντονη;

Αυξήστε το `BlurRadius` για πιο ομαλή άκρη, αυξήστε το `Distance` για μεγαλύτερη μετατόπιση, ή μειώστε το `Transparency` (π.χ., `0.1`) για πιο σκούρο αποτέλεσμα.

### Πώς προσθέτω περιθώριο γύρω από το ορθογώνιο;

```csharp
rect.LineColor = Color.DarkBlue;   // border color
rect.LineWidth = 2;                // thickness in points
```

### Είναι συμβατό με παλαιότερες εκδόσεις του Aspose.Words;

Ναι. Η κλάση `ShadowFormat` υπάρχει από τις πρώτες εκδόσεις του 2020. Αν χρησιμοποιείτε πολύ παλιά έκδοση, ίσως χρειαστεί να κάνετε αναβάθμιση για πρόσβαση σε όλες τις ιδιότητες.

## Συμβουλές & Πιθανά Πάγια

- **Pro tip:** Πάντα απελευθερώνετε μεγάλα έγγραφα (`doc.Dispose()`) όταν τελειώσετε, ειδικά σε web εφαρμογές, ώστε να ελευθερώνονται οι εγγενείς πόροι.  
- **Προσοχή:** Η χρήση σχετικής διαδρομής χωρίς κατάλληλα δικαιώματα μπορεί να προκαλέσει `UnauthorizedAccessException`. Προτιμήστε απόλυτες διαδρομές ή εξασφαλίστε ότι η εφαρμογή έχει δικαιώματα εγγραφής.  
- **Θυμηθείτε:** Η ιδιότητα `FillColor` δέχεται οποιοδήποτε `System.Drawing.Color`. Μπορείτε να χρησιμοποιήσετε `Color.FromArgb(255, 173, 216, 230)` για ένα προσαρμοσμένο παστέλ χρώμα.

## Επόμενα Βήματα

Τώρα που ξέρετε πώς να **δημιουργήσετε έγγραφο word**, **προσθέσετε σχήμα ορθογωνίου**, **ορίσετε χρώμα γεμίσματος σχήματος** και **αποθηκεύσετε αρχείο docx**, μπορείτε να πειραματιστείτε περαιτέρω:

- Εισάγετε πολλαπλά σχήματα και τοποθετήστε τα με `RelativeHorizontalPosition` και `RelativeVerticalPosition`.  
- Συνδυάστε το ορθογώνιο με κείμενο χρησιμοποιώντας `Shape.TextBox` για λεζάντες.  
- Εξάγετε το ίδιο έγγραφο σε PDF (`doc.Save("output.pdf")`) για διανομή.

Αν σας ενδιαφέρουν πιο προχωρημένα γραφικά, ρίξτε μια ματιά στην υποστήριξη του Aspose.Words για **WordArt**, **charts** και **inline images**. Κάθε ένα ακολουθεί το ίδιο μοτίβο: δημιουργήστε έναν κόμβο, διαμορφώστε τις ιδιότητές του και αποθηκεύστε.

---

### TL;DR

- Χρησιμοποιήστε `Document` και `DocumentBuilder` για **να δημιουργήσετε έγγραφο word**.  
- Καλέστε `InsertShape(ShapeType.Rectangle, …)` για **να προσθέσετε σχήμα ορθογωνίου**.  
- Ορίστε `FillColor` για το επιθυμητό φόντο.  
- Ενεργοποιήστε `ShadowFormat` και ρυθμίστε τις ιδιότητές του για ένα επαγγελματικό αποτέλεσμα.  
- Ολοκληρώστε με `document.Save("yourPath.docx")` για **να αποθηκεύσετε το αρχείο docx**.

Καλό κώδικα και απολαύστε να κάνετε τα αρχεία Word σας λίγο πιο στυλιζαρισμένα!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}