---
category: general
date: 2026-01-08
description: Δημιουργήστε ένα κενό έγγραφο Word και μάθετε πώς να προσθέσετε σκιά
  σε ένα σχήμα ορθογωνίου. Εισάγετε αρχεία Word με σχήματα και προσθέστε σκιά στο
  σχήμα σε C# χρησιμοποιώντας το Aspose.Words.
draft: false
keywords:
- create blank word
- how to add shadow
- rectangle shape word
- insert shape word
- add shape shadow
language: el
og_description: Δημιουργήστε κενό έγγραφο Word και δείτε πώς να προσθέσετε σκιά σε
  σχήμα ορθογωνίου χρησιμοποιώντας C#. Πλήρης κώδικας, εξηγήσεις και συμβουλές.
og_title: Δημιουργία Κενής Εγγράφου Word – Προσθήκη Σκιώδους Ορθογωνίου Σχήματος
tags:
- Aspose.Words
- C#
- Document Automation
title: Δημιουργία Κενής Εγγράφου Word με Σχήμα Ορθογωνίου με Σκιά – Οδηγός Βήμα‑προς‑Βήμα
url: /el/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία Κενής Εγγράφου Word με Σχήμα Ορθογωνίου με Σκιά – Πλήρης Εκπαιδευτικό Σεμινάριο

Έχετε χρειαστεί ποτέ να **δημιουργήσετε κενά αρχεία Word** προγραμματιστικά και στη συνέχεια να τα διακοσμήσετε με ένα ωραίο ορθογώνιο με σκιά; Δεν είστε μόνοι. Πολλοί προγραμματιστές αντιμετωπίζουν πρόβλημα όταν ανακαλύπτουν ότι η εισαγωγή σχημάτων και η εφαρμογή εφέ δεν είναι τόσο απλή όσο η πληκτρολόγηση κειμένου.

Σε αυτόν τον οδηγό θα περάσουμε από τη δημιουργία ενός κεννού `.docx` έως το **πώς να προσθέσετε σκιά** σε ένα αντικείμενο **rectangle shape word**, και τελικά **να εισάγετε περιεχόμενο shape word** με ένα επεξεργασμένο εφέ **add shape shadow**. Στο τέλος θα έχετε ένα έτοιμο προς χρήση snippet που λειτουργεί με την τελευταία έκδοση του Aspose.Words for .NET.

---

## Τι Θα Χρειαστεί

- **Aspose.Words for .NET** (v24.10 ή νεότερη) – η βιβλιοθήκη που τροφοδοτεί όλα τα παρακάτω.  
- Ένα περιβάλλον ανάπτυξης .NET (Visual Studio, Rider ή το `dotnet` CLI).  
- Βασικές γνώσεις C# – αν μπορείτε να γράψετε “Hello World”, είστε έτοιμοι.  

Δεν απαιτούνται πρόσθετα πακέτα NuGet· όλα βρίσκονται μέσα στο `Aspose.Words` και το `System.Drawing`.

---

## Βήμα 1: Δημιουργία Κενής Εγγράφου Word

Το πρώτο βήμα είναι να δημιουργήσετε ένα κενό αντικείμενο `Document`. Σκεφτείτε το ως έναν φρέσκο καμβά—όπως το άνοιγμα ενός νέου αρχείου Word χειροκίνητα.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Initialize a brand‑new blank Word document
Document document = new Document();   // This creates an empty .docx in memory
```

*Γιατί είναι σημαντικό:*  
Μια παρουσία `Document` αντιπροσωπεύει ολόκληρο το αρχείο Word. Ξεκινώντας με ένα κενό έγγραφο έχετε πλήρη έλεγχο σε κάθε στοιχείο που θα προσθέσετε αργότερα, από παραγράφους έως σχήματα.

---

## Βήμα 2: Ορισμός Σχήματος Ορθογωνίου (Rectangle Shape Word)

Τώρα χρειαζόμαστε ένα σχήμα για να δουλέψουμε. Ένα ορθογώνιο είναι η πιο απλή γεωμετρία και λειτουργεί καλά για λογότυπα, placeholders ή απλά UI mock‑ups.

```csharp
// Step 2: Create a rectangle shape with specific dimensions
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width  = 200,   // Width in points (≈2.78 inches)
    Height = 100    // Height in points (≈1.39 inches)
};
```

*Γιατί είναι σημαντικό:*  
Ορίζοντας `Width` και `Height` ελέγχετε το οπτικό αποτύπωμα του σχήματος. Το `ShapeType.Rectangle` λέει στο Aspose να αποδώσει ένα κλασικό κουτί—ιδανικό για την επίδειξη του **add shape shadow** αργότερα.

---

## Βήμα 3: Εφαρμογή Σκιάς στο Σχήμα (How to Add Shadow)

Οι σκιές προσδίδουν βάθος, κάνοντας ένα επίπεδο ορθογώνιο να φαίνεται σαν φυσικό αντικείμενο. Το Aspose.Words εκθέτει μια ιδιότητα `Shadow` όπου μπορείτε να ρυθμίσετε το χρώμα, την απόσταση, το θόλωμα και τη διαφάνεια.

```csharp
// Step 3: Enable and configure the shadow effect
rectangleShape.Shadow.Enabled      = true;               // Turn the shadow on
rectangleShape.Shadow.Color        = Color.Gray;         // Shadow color
rectangleShape.Shadow.Distance    = 5.0;                // How far the shadow is offset
rectangleShape.Shadow.BlurRadius  = 3.0;                // Softness of the edge
rectangleShape.Shadow.Transparency = 0.2;               // 0 = opaque, 1 = fully transparent
```

*Γιατί είναι σημαντικό:*  
Κάθε ιδιότητα επηρεάζει το οπτικό αποτέλεσμα:

- **Enabled** – χωρίς αυτό οι άλλες ρυθμίσεις αγνοούνται.  
- **Color** – επιλέξτε μια απόχρωση που ταιριάζει με το θέμα του εγγράφου σας.  
- **Distance** – μεγαλύτερες τιμές σπρώχνουν τη σκιά πιο μακριά.  
- **BlurRadius** – υψηλότεροι αριθμοί κάνουν τη σκιά πιο μαλακή.  
- **Transparency** – ρυθμίστε την αδιαφάνεια για λεπτότητα.

Αισθανθείτε ελεύθεροι να πειραματιστείτε· για δραματικό αποτέλεσμα, αυξήστε το `Distance` στο `10` και ορίστε το `Transparency` στο `0.5`.

---

## Βήμα 4: Εισαγωγή του Σχήματος στο Έγγραφο (Insert Shape Word)

Με το ορθογώνιο έτοιμο, χρειαζόμαστε ένα σημείο για να το τοποθετήσουμε. Η πιο απλή θέση είναι η πρώτη παράγραφος του σώματος του εγγράφου.

```csharp
// Step 4: Append the shape to the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

*Γιατί είναι σημαντικό:*  
Το `FirstSection.Body.FirstParagraph` υπάρχει πάντα σε ένα νέο `Document`. Προσθέτοντας το σχήμα εδώ, εξασφαλίζετε ότι το σχήμα εμφανίζεται στην κορυφή του αρχείου—χρήσιμο για κεφαλίδες ή λογότυπα τίτλου.

Αν χρειαστεί να εισάγετε το σχήμα κάπου αλλού, μπορείτε να εντοπίσετε ένα συγκεκριμένο `Paragraph` ή `Run` και να χρησιμοποιήσετε `InsertAfter` ή `InsertBefore`.

---

## Βήμα 5: Αποθήκευση του Αρχείου Word

Το τελευταίο βήμα είναι η αποθήκευση του εγγράφου στη μνήμη στο δίσκο. Επιλέξτε έναν φάκελο στον οποίο έχετε δικαίωμα εγγραφής και δώστε στο αρχείο ένα περιγραφικό όνομα.

```csharp
// Step 5: Save the document with the shadowed rectangle
string outputPath = @"C:\Temp\ShadowedRectangle.docx";
document.Save(outputPath);
```

*Γιατί είναι σημαντικό:*  
Η κλήση του `Save` γράφει ένα πλήρως συμβατό αρχείο `.docx`. Ανοίξτε το στο Microsoft Word, LibreOffice ή οποιονδήποτε προβολέα και θα δείτε ένα ορθογώνιο με ήπια γκρι σκιά—ακριβώς όπως το ρυθμίσαμε.

---

## Πλήρες Παράδειγμα Λειτουργίας

Παρακάτω βρίσκεται το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε‑επικολλήσετε σε μια εφαρμογή κονσόλας. Περιλαμβάνει όλες τις οδηγίες `using`, τη δημιουργία του σχήματος, τη ρύθμιση της σκιάς, την εισαγωγή και την αποθήκευση.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Define a rectangle shape (rectangle shape word)
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
        {
            Width  = 200,
            Height = 100
        };

        // 3️⃣ How to add shadow – configure the shadow effect
        rectangleShape.Shadow.Enabled      = true;
        rectangleShape.Shadow.Color        = Color.Gray;
        rectangleShape.Shadow.Distance    = 5.0;
        rectangleShape.Shadow.BlurRadius  = 3.0;
        rectangleShape.Shadow.Transparency = 0.2;

        // 4️⃣ Insert shape word into the first paragraph
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // 5️⃣ Save the file (add shape shadow persisted)
        string outputPath = @"C:\Temp\ShadowedRectangle.docx";
        document.Save(outputPath);

        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Αναμενόμενη έξοδος:**  
Ανοίξτε το `ShadowedRectangle.docx` και θα δείτε ένα ανοιχτόγκρι ορθογώνιο κεντραρισμένο στην κορυφή της σελίδας με μια διακριτική σκιά μετατόπιση 5 pts. Χωρίς επιπλέον κείμενο, μόνο το σχήμα—ακριβώς όπως παράγει ο κώδικας.

---

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

### Τι γίνεται αν χρειάζομαι διαφορετικό σχήμα;

Αντικαταστήστε το `ShapeType.Rectangle` με οποιαδήποτε άλλη τιμή του enum `ShapeType` (`Ellipse`, `Triangle`, `Star`, κλπ.). Οι ιδιότητες της σκιάς λειτουργούν με τον ίδιο τρόπο.

### Μπορώ να προσθέσω πολλαπλές σκιές;

Το Aspose.Words υποστηρίζει μόνο μία σκιά ανά σχήμα. Αν χρειάζεστε στρωματοποιημένα εφέ, δημιουργήστε δύο επικαλυπτόμενα σχήματα με διαφορετικές ρυθμίσεις σκιάς.

### Πώς λειτουργεί αυτό στο .NET Core;

Το ίδιο API λειτουργεί σε .NET 6/7/8. Απλώς βεβαιωθείτε ότι αναφέρετε το πακέτο **Aspose.Words.NETCore** (ή το τυπικό πακέτο, το οποίο είναι πλέον cross‑platform).

### Υποστηρίζεται ακόμα το `System.Drawing` σε Linux;

`System.Drawing.Common` είναι μόνο για Windows ξεκινώντας από το .NET 6. Για cross‑platform έργα, χρησιμοποιήστε το `Aspose.Drawing` (ξεχωριστό NuGet) ή παραμείνετε στα χρώματα που ορίζει το ίδιο το `Aspose.Words`.

### Τι γίνεται με την κλιμάκωση DPI;

Οι διαστάσεις του σχήματος είναι σε points (1 pt = 1/72 inch). Αν χρειάζεστε ακριβή μέγεθος σε pixel για συγκεκριμένο DPI, υπολογίστε τα points ως `pixels * 72 / dpi`.

---

## Συμβουλές & Προειδοποιήσεις

- **Συμβουλή:** Ορίστε `rectangleShape.WrapType = WrapType.Inline;` αν θέλετε το σχήμα να ρέει με το κείμενο αντί να αιωρείται πάνω από αυτό.  
- **Προσοχή:** Ξεχάνοντας να ενεργοποιήσετε τη σκιά (`Enabled = true`). Οι άλλες ρυθμίσεις θα αγνοηθούν σιωπηρά.  
- **Σημείωση απόδοσης:** Η προσθήκη πολλών σχημάτων σε βρόχο μπορεί να είναι αργή. Ομαδοποιήστε τα σε ένα ενιαίο `Section` και καλέστε `document.UpdatePageLayout()` μία φορά στο τέλος.  
- **Έλεγχος έκδοσης:** Το API σκιάς εισήχθη στο Aspose.Words 20.2. Αν χρησιμοποιείτε παλαιότερη έκδοση, κάντε αναβάθμιση για να αποφύγετε την έλλειψη ιδιοτήτων.

---

## Συμπέρασμα

Δημιουργήσαμε **κενό έγγραφο Word**, κατασκευάσαμε ένα **rectangle shape word**, μάθαμε **πώς να προσθέσουμε σκιά**, και τελικά **εισάγαμε περιεχόμενο shape word** με ένα επεξεργασμένο εφέ **add shape shadow**—όλα χρησιμοποιώντας το Aspose.Words for .NET.  

Το snippet είναι πλήρως εκτελέσιμο, λειτουργεί σε Windows και cross‑platform .NET, και μπορεί να επεκταθεί σε άλλα σχήματα, χρώματα ή ακόμη και animated GIFs. Στη συνέχεια, μπορείτε να εξερευνήσετε την προσθήκη κειμένου μέσα στο ορθογώνιο, την εφαρμογή gradient fills, ή τη δημιουργία μιας ολόκληρης αναφοράς με πολλαπλά στυλιζαρισμένα σχήματα.

Έχετε περισσότερες ιδέες; Δοκιμάστε να αντικαταστήσετε τη γκρι σκιά με μια μπλε, αυξήστε το blur για ένα ονειρικό αποτέλεσμα, ή συνδυάστε πολλά σχήματα σε ένα προσαρμοσμένο λογότυπο. Ο ουρανός είναι το όριο, και τώρα έχετε τα δομικά στοιχεία για να το πετύχετε.

Καλή προγραμματιστική δουλειά, και εύχομαι τα έγγραφά σας να είναι πάντα κοφτερά (με τη σωστή ποσότητα σκιάς)!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}