---
category: general
date: 2026-01-13
description: Δημιουργήστε έγγραφο Word χρησιμοποιώντας το Aspose.Words και μάθετε
  πώς να εισάγετε σχήμα ορθογωνίου, πώς να προσθέσετε σκιά και πώς να προσθέσετε σκιά
  σχήματος σε C#. Περιλαμβάνεται πλήρες παράδειγμα.
draft: false
keywords:
- create word document
- insert rectangle shape
- how to add shadow
- how to insert shape
- add shape shadow
language: el
og_description: Δημιουργήστε έγγραφο Word με το Aspose.Words, δείτε πώς να εισάγετε
  σχήμα ορθογωνίου και πώς να προσθέσετε σκιά. Ακολουθήστε το πλήρες παράδειγμα C#.
og_title: Δημιουργία εγγράφου Word με σκιώδη ορθογώνιο – Πλήρης οδηγός
tags:
- Aspose.Words
- C#
- Document Automation
title: Δημιουργία εγγράφου Word με ορθογώνιο με σκιά – Οδηγός βήμα‑προς‑βήμα
url: /el/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία Εγγράφου Word με Σκιασμένο Ορθογώνιο – Οδηγός Βήμα‑Βήμα

Κάποτε χρειάστηκε να **create word document** που περιέχει ένα ωραία σκιασμένο ορθογώνιο, αλλά δεν ήξερες από πού να ξεκινήσεις; Δεν είσαι μόνος σου—πολλοί προγραμματιστές αντιμετωπίζουν το ίδιο εμπόδιο όταν αρχίζουν να δουλεύουν με Aspose.Words.  

Σε αυτό το tutorial θα περάσουμε από όλα όσα χρειάζεσαι για να **create word document** προγραμματιστικά, **insert rectangle shape**, και να δείξουμε **how to add shadow** ώστε το σχήμα να ξεχωρίζει. Στο τέλος θα έχεις ένα έτοιμο απόσπασμα C# που μπορείς να ενσωματώσεις σε οποιοδήποτε .NET project.

## Τι θα μάθετε

- Τον ακριβή κώδικα για **how to insert shape** (ένα ορθογώνιο) σε αρχείο Word.
- Οι ιδιότητες που πρέπει να ρυθμίσεις για **add shape shadow** και να ελέγξετε την εμφάνισή του.
- Πώς να αποθηκεύσεις το αποτέλεσμα και να επαληθεύσεις ότι η σκιά είναι ορατή.
- Μερικές πρακτικές συμβουλές και σημειώσεις edge‑case που θα σώσουν από προβλήματα αργότερα.

Δεν χρειάζεται εξωτερική τεκμηρίωση—όλα είναι εδώ.

## Προαπαιτούμενα

Πριν βουτήξουμε, βεβαιώσου ότι έχεις:

1. **.NET 6.0** (ή πρόσφατη έκδοση .NET) εγκατεστημένη.
2. Μια **license** για Aspose.Words for .NET, ή μπορεί να χρησιμοποιηθεί τη δωρεάν αξιολόγηση λειτουργίας για δοκιμές.
3. Περιβάλλον ανάπτυξη—το Visual Studio 2022 λειτουργεί άψογα, αλλά οποιοσδήποτε επεξεργαστής που μπορεί να μεταταγλωττίσει C# αρκεί.

Αυτό είναι όλο. Δεν απαιτούνται επιπλέον πακέτα NuGet εκτός από `Aspose.Words`.

## Βήμα 1 – Ρύθμιση του έργου και της αναφοράς Aspose.Words

Πρώτα, δημιούργησε μια νέα console app και πρόσθεσε το πακέτο Aspose.Words:

```bash
dotnet new console -n ShadowRectangleDemo
cd ShadowRectangleDemo
dotnet add package Aspose.Words
```

> **Pro tip:** Αν χρησιμοποιείς τη δωρεάν δοκιμή, θυμήσου να καλέσεις `License.SetLicense` με το αρχείο άδειας· διαφορετικά η βιβλιοθήκη θα προσθέσει υδατογράφημα.

## Βήμα 2 – Αρχικοποίηση του Εργαλείου Δημιουργίας Εγγράφων

Τώρα θα ξεκινήσουμε τη διαδικασία **create word document**. Η κλάση `Document` μας δίνει ένα κενό καμβά, και ο `DocumentBuilder` μας επιτρέπει να ζωγραφίσουμε πάνω του.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing; // For Color

// Initialise a new blank document
Document document = new Document();

// Initialise a builder to start adding content
DocumentBuilder builder = new DocumentBuilder(document);
```

Γιατί χρειάζεται ένας builder; Απομονώνει τις λεπτομέρειες του OpenXML, ώστε να εστιάσεις στο *τι* θέλεις αντί για το *πώς* είναι δομημένο το αρχείο. Αυτό είναι το βασικό στοιχείο για **how to insert shape** γρήγορα.

## Βήμα 3 – Εισαγωγή Σχήματος Ορθογώνιου

Εδώ είναι που πραγματικά **insert rectangle shape**. Το ορθογώνιο θα είναι 150 × 100 points (περίπου 2 in × 1.3 in).

```csharp
// Insert a rectangle shape at the current cursor position
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 100);
```

Η μέθοδος `InsertShape` επιστρέφει ένα αντικείμενο `Shape`, το οποίο μπορούμε να προσαρμόσουμε περαιτέρω. Σε αυτό το σημείο, το ορθογώνιο είναι απλώς ένα λευκό κουτί—χωρίς σκιά ακόμα.

## Βήμα 4 – Πώς να Προσθέσετε Σκιά (Προσθήκη Σκιάς Σχήματος)

Η προσθήκη σκιάς είναι απρόσμενα απλή μόλις ξέρεις ποια properties πρέπει να ρυθμίσεις. Το αντικείμενο `ShadowFormat` ελέγχει την ορατότητα, το χρώμα, το blur, το offset και το μέγεθος.

```csharp
// Make the shadow visible
rectangleShape.ShadowFormat.Visible = true;

// Choose a subtle gray tone
rectangleShape.ShadowFormat.Color = Color.Gray;

// Set 30 % transparency – the shadow will be faint but noticeable
rectangleShape.ShadowFormat.Transparency = 0.3;

// Offset the shadow 5 points right and 5 points down
rectangleShape.ShadowFormat.OffsetX = 5;
rectangleShape.ShadowFormat.OffsetY = 5;

// Soften the edges with a blur radius of 4 points
rectangleShape.ShadowFormat.BlurRadius = 4;

// Scale the shadow to 75 % of the shape size (percentage)
rectangleShape.ShadowFormat.Size = 75;
```

Αυτό το τμήμα εξηγεί **how to add shadow** στα απλά λόγια: ενεργοποίησέ το, διάλεξε χρώμα, ρύθμισε τη διαφάνεια, το offset, το blur και το μέγεθος. Μπορείς να πειραματιστείς με αυτές τις τιμές για να πάρεις μια βαριά σκιά ή μια ελαφριά, διακριτική.

### Συνήθεις Παραλλαγές

- **Διαφορετικά χρώματα:** Χρησιμοποίησε `Color.Black` για κλασική σκιά ή `Color.BlueViolet` για πιο στυλιζαρισμένο αποτέλεσμα.  
- **Μηδενικό blur:** Θέσε `BlurRadius = 0` για καθαρή, αιχμηρή άκρη.  
- **Μεγαλύτερα offsets:** Αυξήστε `OffsetX`/`OffsetY` για να απομακρύνετε τη σκιά πιο μακριά από το σχήμα.

## Βήμα 5 – Αποθήκευση του Εγγράφου και Επαλήθευση

Τέλος, γράψτε το έγγραφο στο δίσκο. Το αρχείο θα είναι ένα τυπικό `.docx` που μπορεί να ανοίξει οποιοσδήποτε σύγχρονος επεξεργαστής κειμένου.

```csharp
// Save the document to the desired folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowRectangle.docx");
document.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Ανοίξτε το παραγόμενο *ShadowRectangle.docx* στο Microsoft Word. Θα πρέπει να δείτε ένα ορθογώνιο με μια απαλή γκρι σκιά που είναι μετατοπισμένη προς τα κάτω‑δεξιά—ακριβώς όπως ο κώδικας το καθόρισε.

> **Expected output:** Ένα αρχείο Word μιας σελίδας που περιέχει ένα ορθογώνιο 150 × 100 points με σκιά γκρι 30 % διαφάνειας, μετατοπισμένη κατά 5 pts, με blur 4 pts και μέγεθος 75 % του σχήματος.

## Πλήρες παράδειγμα εργασίας

Συνδυάζοντας τα παραπάνω, εδώ είναι το πλήρες, έτοιμο‑για‑εκτέλεση πρόγραμμα:

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialise a new blank document
        Document document = new Document();

        // 2️⃣ Create a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Insert a rectangle shape (150 × 100 points)
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 100);

        // 4️⃣ How to add shadow – configure the ShadowFormat
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = Color.Gray;
        rectangleShape.ShadowFormat.Transparency = 0.3; // 30 % transparent
        rectangleShape.ShadowFormat.OffsetX = 5;        // horizontal offset
        rectangleShape.ShadowFormat.OffsetY = 5;        // vertical offset
        rectangleShape.ShadowFormat.BlurRadius = 4;    // softer edge
        rectangleShape.ShadowFormat.Size = 75;         // size as a percentage

        // 5️⃣ Save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowRectangle.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Τρέξτε το πρόγραμμα (`dotnet run`) και θα έχετε ένα νέο αρχείο Word με ένα ωραία σκιασμένο ορθογώνιο—ιδανικό για αναφορές, πιστοποιητικά ή οποιοδήποτε οπτικό στοιχείο χρειάζεστε.

## Συχνές Ερωτήσεις (FAQ)

**Q: Μπορώ να εισάγω άλλα σχήματα (έλλειψη, αστέρι) και να χρησιμοποιήσω τον ίδιο κώδικα σκιάς;**
Α: Απόλυτα. Η μέθοδος `InsertShape` δέχεται την τιμή του enum `SpeType`. Μόλις έχεις ένα αντικείμενο `Shape`, οι ίδιοι `ShadowFormat` λειτουργούν με τον ίδιο τρόπο, έτσι το **how to add shadow** δεν εξαρτάται από το σχήμα.

**Q: Τι γίνεται αν χρειάζομαι τη σκιά και στις δύο πλευρές του σχήματος;**
A: Το Aspose.Words υποστηρίζει μόνο μία σκιά ανά σχήμα. Για να προσομοιώσεις διπλή σκιά, διπλασίασε το σχήμα, μετατόπισε κάθε αντίγραφο διαφορετικά, και όρισε το `ShadowFormat.Visible` ενός σε `false` ενώ κρατάς τη σκιά του άλλου ενεργού.

**Ε: Λειτουργεί αυτό σε .NET Framework 4.8;**
Α: Ναι. Το API είναι ανεξάρτητο από την έκδοση· απλώς έκανε αναφορά στο κατάλληλο Aspose.Words DLL για το target framework σου.

## Συμβουλές και παγίδες

- **Μην ξεχάσεις να θέσεις `Visible = true`**—διαφορετικά οι σκιές αγνοούνται.
- **Οι τιμές διαφανειών κυμαίνονται από 0,0 (αδιαφανές) έως 1,0 (πλήρως διαφανών).** Συχνό λάθος είναι η χρήση `30` αντί για `0,3`.
- **Η αποθήκευση σε φάκελο μόνο για ανάγνωση προκαλεί εξαίρεση.** Βεβαιώσου ότι ο φάκελος εξόδου είναι εγγράψιμος.

## Επόμενα βήματα

Τώρα που ξέρεις **how to insert shape**, **add shape shadow**, και **create word document** με Aspose.Words, μπορείς να εξερευνήσεις:

- Προσθήκη **κειμένου μέσα στο ορθογώνιο** χρησιμοποιώντας `builder.InsertParagraph()` πριν την εισαγωγή του σχήματος.  
- Εφαρμογή **gradient fills** ή **patterned borders** για πιο πλούσια οπτική εμφάνιση.  
- Αυτοματοποίηση της δημιουργίας πολλαπλών σελίδων, καθεμίας με διαφορετικό σκιασμένο σχήμα, για δυναμικές αναφορές.

Πειραματίσου ελεύθερα—αλλάζοντας το χρώμα, το blur ή το μέγεθος της σκιάς μπορεί να αλλάξει δραματικά την εμφάνιση του εγγράφου σου.

---

*Έτοιμος να το βάλεις σε παραγωγή; Πάρε τον κώδικα, ρύθμισε τις παραμέτρους, και δες τα αρχεία Word σου να αποκτούν επαγγελματικό φινίρισμα σε δευτερόλεπτα.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}