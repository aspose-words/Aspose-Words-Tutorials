---
category: general
date: 2026-08-10
description: Εισαγωγή σχήματος ορθογωνίου στο Word με χρήση C#. Μάθετε πώς να κρύψετε
  το σχήμα, να κρύψετε το σχήμα στο Word και να δημιουργήσετε κρυφό σχήμα με το Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- hide shape in word
- create hidden shape
language: el
lastmod: 2026-08-10
og_description: Εισαγωγή σχήματος ορθογωνίου στο Word χρησιμοποιώντας C#. Αυτό το
  σεμινάριο εξηγεί πώς να κρύψετε το σχήμα, πώς να κρύψετε το σχήμα στο Word και πώς
  να δημιουργήσετε κρυφό σχήμα με πλήρη παραδείγματα κώδικα.
og_image_alt: Screenshot showing a hidden rectangle shape inserted into a Word document
  using C#
og_title: Εισαγωγή σχήματος ορθογωνίου στο Word με C# – βήμα‑βήμα οδηγός
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Insert rectangle shape in Word using C#. Learn how to hide shape, hide
    shape in Word, and create hidden shape with Aspose.Words.
  headline: Insert rectangle shape in Word with C# – complete guide
  type: TechArticle
- description: Insert rectangle shape in Word using C#. Learn how to hide shape, hide
    shape in Word, and create hidden shape with Aspose.Words.
  name: Insert rectangle shape in Word with C# – complete guide
  steps:
  - name: Can I hide only the outline but keep the fill visible?
    text: Yes. Instead of setting `Hidden = true`, you can set `rectangle.LineFormat.Visible
      = false` to hide the border while keeping the fill color. This is a variation
      of **how to hide shape** that preserves part of the visual appearance.
  - name: Does the hidden flag work in older Word versions (2003, 2007)?
    text: The hidden attribute is part of the Open XML specification introduced with
      Word 2007. Documents saved in the older binary `.doc` format will not preserve
      the flag. To support legacy formats, save the document as `.docx` and, if needed,
      convert it later using Aspose.Words’ `SaveFormat.Doc`.
  - name: What if I need to hide multiple shapes at once?
    text: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection
      and set `Hidden = true` on each shape that meets your criteria (e.g., a specific
      `ShapeType` or a custom `AlternativeText` value).
  - name: Is there a performance impact when hiding shapes?
    text: The hidden flag adds a tiny XML attribute; it does not affect rendering
      speed. However, a very large number of hidden objects can increase file size
      marginally. Remove shapes you never need to keep the document lean.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Εισαγωγή σχήματος ορθογωνίου στο Word με C# – πλήρης οδηγός
url: /el/net/programming-with-shapes/insert-rectangle-shape-in-word-with-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Εισαγωγή σχήματος ορθογωνίου στο Word με C# – πλήρης οδηγός

Αν χρειάζεστε **εισαγωγή σχήματος ορθογωνίου** σε έγγραφο Word χρησιμοποιώντας C#, αυτός ο οδηγός σας δείχνει τα ακριβή βήματα. Θα μάθετε επίσης **πώς να κρύψετε το σχήμα** ώστε να μην εμφανίζεται στο τελικό αρχείο, απαντώντας στο συχνό ερώτημα **hide shape in Word** και δείχνοντας πώς να **create hidden shape** προγραμματιστικά.

Το tutorial καλύπτει όλα, από τη ρύθμιση του Aspose.Words SDK μέχρι την επαλήθευση ότι το σχήμα είναι κρυφό. Στο τέλος του άρθρου θα έχετε ένα επαναχρησιμοποιήσιμο κομμάτι κώδικα που μπορείτε να ενσωματώσετε σε οποιοδήποτε .NET project.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

- .NET 6.0 ή νεότερο εγκατεστημένο (ο κώδικας λειτουργεί επίσης με .NET Framework 4.6+)
- Ένα έγκυρο license του Aspose.Words for .NET ή ένα προσωρινό evaluation key
- Visual Studio 2022 (ή οποιοδήποτε IDE που υποστηρίζει C#)
- Βασική εξοικείωση με τη σύνταξη C# και το Document Object Model (DOM) των αρχείων Word

Δεν απαιτούνται πρόσθετα πακέτα NuGet πέρα από `Aspose.Words`.

## Βήμα 1: Δημιουργία νέου κενού εγγράφου και DocumentBuilder

Η πρώτη ενέργεια είναι η δημιουργία ενός αντικειμένου `Document`. Το `DocumentBuilder` παρέχει ένα βολικό API για την εισαγωγή περιεχομένου όπως σχήματα, παραγράφους και πίνακες.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document document = new Document();

// DocumentBuilder lets you add elements to the document.
DocumentBuilder builder = new DocumentBuilder(document);
```

**Γιατί είναι σημαντικό:** Το `Document` αντιπροσωπεύει ολόκληρο το αρχείο .docx, ενώ το `DocumentBuilder` διατηρεί έναν κέρσορα που παρακολουθεί πού θα τοποθετηθεί το επόμενο στοιχείο. Η αρχικοποίηση και των δύο αντικειμένων αποτελεί τη βάση για κάθε εργασία αυτοματοποίησης του Word.

## Βήμα 2: Εισαγωγή σχήματος ορθογωνίου

Τώρα εισάγετε το ορθογώνιο. Η μέθοδος `InsertShape` απαιτεί τον τύπο του σχήματος και τις διαστάσεις του σε points (1 point ≈ 1/72 inch). Ένα μέγεθος **200 × 100 points** αποδίδει ένα ορθογώνιο περίπου 2.78 × 1.39 ίντσες.

```csharp
// Insert a rectangle of 200x100 points.
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

**Γιατί είναι σημαντικό:** Το αντικείμενο `Shape` που λαμβάνετε είναι πλήρως παραμετροποιήσιμο—χρώμα, περίγραμμα, κείμενο και ορατότητα μπορούν να τροποποιηθούν πριν αποθηκευτεί το έγγραφο.

## Βήμα 3: Απόκρυψη του σχήματος

Για να αποτρέψετε την εμφάνιση ή εκτύπωση του ορθογωνίου, ορίστε την ιδιότητα `Hidden` σε `true`. Αυτή η ιδιότητα αντιστοιχεί άμεσα στο χαρακτηριστικό “Hidden” του Word, το οποίο το Word σέβεται τόσο στην προβολή όσο και στην εκτύπωση.

```csharp
// Hide the shape so it never appears.
rectangle.Hidden = true;
```

**Γιατί είναι σημαντικό:** Ο ορισμός του `Hidden` είναι ο τυπικός τρόπος για **hide shape in Word** χωρίς να αφαιρείται το σχήμα από τη δομή του εγγράφου. Το σχήμα παραμένει προσβάσιμο στον κώδικα, επιτρέποντας μελλοντικές επεμβάσεις όπως υπό όρους μορφοποίηση ή εναλλαγές ορατότητας βάσει δεδομένων.

## Βήμα 4: Αποθήκευση του εγγράφου

Τέλος, αποθηκεύστε το έγγραφο στο δίσκο. Επιλέξτε οποιονδήποτε φάκελο θέλετε· το παράδειγμα χρησιμοποιεί ένα placeholder μονοπάτι που πρέπει να αντικαταστήσετε με πραγματικό.

```csharp
// Save the document with the hidden rectangle.
document.Save(@"C:\Temp\HiddenShape.docx");
```

**Γιατί είναι σημαντικό:** Η αποθήκευση ολοκληρώνει το αρχείο και γράφει τη σημαία hidden στο υποκείμενο Open XML. Όταν ανοίξετε το έγγραφο στο Microsoft Word, το ορθογώνιο θα είναι αόρατο, επιβεβαιώνοντας ότι έχετε δημιουργήσει επιτυχώς **created hidden shape**.

## Βήμα 5: Επαλήθευση του κρυφού σχήματος

Ανοίξτε το παραγόμενο `HiddenShape.docx` στο Microsoft Word:

1. Μεταβείτε στο **File → Options → Display** και βεβαιωθείτε ότι η επιλογή *“Show hidden text”* είναι **unchecked**.  
2. Το ορθογώνιο δεν πρέπει να είναι ορατό σε καμία σελίδα.  
3. Για διπλό έλεγχο, ενεργοποιήστε *“Show hidden text”*· το ορθογώνιο θα εμφανιστεί με ένα αχνό διακεκομμένο περίγραμμα, αποδεικνύοντας ότι το σχήμα υπάρχει αλλά είναι κρυφό.

Αν το ορθογώνιο παραμένει ορατό, ελέγξτε ότι αποθηκεύσατε το αρχείο μετά τον ορισμό `Hidden = true` και ότι ανοίγετε το σωστό αρχείο.

## Πλήρες εκτελέσιμο παράδειγμα

Παρακάτω βρίσκεται το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε, επικολλήσετε και εκτελέσετε άμεσα.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a rectangle shape of 200x100 points.
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // Step 3: Hide the shape so it does not appear when viewed or printed.
        rectangle.Hidden = true;

        // Step 4: Save the document with the hidden shape.
        string outputPath = @"C:\Temp\HiddenShape.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
        Console.WriteLine("Open the file in Word to verify that the rectangle is hidden.");
    }
}
```

**Αναμενόμενο αποτέλεσμα:** Η κονσόλα εκτυπώνει τη διαδρομή του αρχείου και μια σύντομη υπενθύμιση. Όταν το αρχείο ανοίξει στο Word, το ορθογώνιο είναι αόρατο εκτός εάν είναι ενεργοποιημένο το κρυφό κείμενο.

## Συχνές ερωτήσεις και ειδικές περιπτώσεις

### Μπορώ να κρύψω μόνο το περίγραμμα ενώ το γέμισμα παραμένει ορατό;

Ναι. Αντί για `Hidden = true`, μπορείτε να ορίσετε `rectangle.LineFormat.Visible = false` ώστε να κρύψετε το περίγραμμα ενώ διατηρείτε το χρώμα γέμισης. Αυτό είναι μια παραλλαγή του **how to hide shape** που διατηρεί μέρος της οπτικής εμφάνισης.

### Λειτουργεί η σημαία hidden σε παλαιότερες εκδόσεις του Word (2003, 2007);

Το χαρακτηριστικό hidden είναι μέρος του προτύπου Open XML που εισήχθη με το Word 2007. Έγγραφα αποθηκευμένα σε παλαιότερη δυαδική μορφή `.doc` δεν διατηρούν τη σημαία. Για υποστήριξη παλαιών μορφών, αποθηκεύστε το έγγραφο ως `.docx` και, αν χρειάζεται, μετατρέψτε το αργότερα χρησιμοποιώντας το `SaveFormat.Doc` του Aspose.Words.

### Τι γίνεται αν χρειαστεί να κρύψω πολλά σχήματα ταυτόχρονα;

Κάντε επανάληψη στη συλλογή `Document.GetChildNodes(NodeType.Shape, true)` και ορίστε `Hidden = true` σε κάθε σχήμα που πληροί τα κριτήριά σας (π.χ., συγκεκριμένο `ShapeType` ή προσαρμοσμένη τιμή `AlternativeText`).

```csharp
foreach (Shape shp in document.GetChildNodes(NodeType.Shape, true))
{
    if (shp.AlternativeText == "HideMe")
        shp.Hidden = true;
}
```

### Υπάρχει επίπτωση στην απόδοση όταν κρύβουμε σχήματα;

Η σημαία hidden προσθέτει ένα μικρό XML attribute· δεν επηρεάζει την ταχύτητα απόδοσης. Ωστόσο, ένας πολύ μεγάλος αριθμός κρυφών αντικειμένων μπορεί να αυξήσει ελαφρώς το μέγεθος του αρχείου. Αφαιρέστε σχήματα που δεν χρειάζεστε για να διατηρήσετε το έγγραφο ελαφρύ.

## Συμβουλές και βέλτιστες πρακτικές

- **Δώστε στο σχήμα ένα περιγραφικό όνομα** χρησιμοποιώντας `rectangle.Name = "MyHiddenRectangle"`· αυτό βοηθά όταν αργότερα ψάχνετε το σχήμα στο DOM.  
- **Ορίστε `AlternativeText`** σε μια προσαρμοσμένη ετικέτα (π.χ., `"HiddenShape"`). Αυτό σας επιτρέπει να εντοπίζετε το σχήμα χωρίς να βασίζεστε στο δείκτη του.  
- **Τυλίξτε τον κώδικα σε try‑catch block** για να διαχειρίζεστε ευγενικά σφάλματα αδειοδότησης ή εξαιρέσεις I/O.  
- **Κλείστε (Dispose) το Document** μετά την αποθήκευση αν επεξεργάζεστε πολλά αρχεία σε βρόχο, ώστε να ελευθερώσετε μη διαχειριζόμενους πόρους: `document.Dispose();`.

## Συμπέρασμα

Τώρα ξέρετε πώς να **insert rectangle shape** σε έγγραφο Word με C#, πώς να **hide shape in Word**, και πώς να **create hidden shape** που παραμένει μέρος της δομής του εγγράφου αλλά είναι αόρατο στους τελικούς χρήστες. Το πλήρες, εκτελέσιμο παράδειγμα δείχνει ολόκληρη τη ροή εργασίας, από τη δημιουργία του εγγράφου μέχρι την επαλήθευση.

Στη συνέχεια, μπορείτε να εξερευνήσετε **how to hide shape** βάσει εισόδου χρήστη ή να συνδυάσετε κρυφά σχήματα με content controls για δυναμική δημιουργία εγγράφων. Η ίδια τεχνική εφαρμόζεται και σε άλλα είδη σχημάτων όπως έλλειψη, βέλη ή προσαρμοσμένα σχέδια.

Πειραματιστείτε με διαφορετικές διαστάσεις, χρώματα και ρυθμίσεις ορατότητας. Αν αντιμετωπίσετε προβλήματα, επανεξετάστε τα παραπάνω βήματα ή συμβουλευτείτε την τεκμηρίωση του Aspose.Words για πιο λεπτομερείς πληροφορίες API. Καλή προγραμματιστική διασκέδαση!

## Τι πρέπει να μάθετε στη συνέχεια;

Οι παρακάτω οδηγίες καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να κυριαρχήσετε σε πρόσθετες δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}