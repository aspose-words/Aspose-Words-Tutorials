---
category: general
date: 2026-03-19
description: Δημιουργήστε έγγραφο Word σε C# με το Aspose.Words, μάθετε πώς να προσθέσετε
  σχήμα, προσθέστε σχήμα ορθογωνίου, εφαρμόστε σκιά και αποθηκεύστε το έγγραφο ως
  docx σε λίγα λεπτά.
draft: false
keywords:
- create word document
- how to add shape
- add rectangle shape
- save document as docx
- add shadow to shape
language: el
og_description: Δημιουργήστε έγγραφο Word με το Aspose.Words, προσθέστε σχήμα ορθογωνίου,
  εφαρμόστε εξωτερική σκιά και αποθηκεύστε το έγγραφο ως docx. Οδηγός βήμα‑βήμα.
og_title: Δημιουργία εγγράφου Word – Προσθήκη σχήματος ορθογωνίου & σκιά
tags:
- Aspose.Words
- C#
- Document Automation
title: Δημιουργία εγγράφου Word – Πώς να προσθέσετε σχήμα ορθογωνίου και σκιά
url: /el/net/programming-with-shapes/create-word-document-how-to-add-rectangle-shape-and-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία Εγγράφου Word – Πώς να Προσθέσετε Σχήμα Ορθογωνίου και Σκιά

Έχετε ποτέ χρειαστεί να **create word document** προγραμματιστικά και αναρωτηθήκατε από πού να ξεκινήσετε; Δεν είστε μόνοι. Πολλοί προγραμματιστές αντιμετωπίζουν το ίδιο πρόβλημα όταν προσπαθούν για πρώτη φορά να δημιουργήσουν ένα αρχείο .docx που περιέχει προσαρμοσμένα γραφικά. Σε αυτό το tutorial θα περάσουμε από όλη τη διαδικασία — πώς να προσθέσετε σχήμα, συγκεκριμένα ένα **add rectangle shape**, να του δώσετε μια κομψή **add shadow to shape**, και τέλος **save document as docx**.  

Στο τέλος του οδηγού θα έχετε ένα έτοιμο‑για‑χρήση απόσπασμα C# που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο .NET. Χωρίς ασαφείς αναφορές, μόνο ένα πλήρες, εκτελέσιμο παράδειγμα.  

## Προαπαιτούμενα

- .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί επίσης με .NET Framework).  
- Εγκατεστημένο Aspose.Words για .NET (πακέτο NuGet `Aspose.Words`).  
- Βασική κατανόηση της σύνταξης C# — δεν απαιτείται τίποτα περίπλοκο.  

Αν λείπει η βιβλιοθήκη, εκτελέστε:

```bash
dotnet add package Aspose.Words
```

Αυτό είναι—χωρίς επιπλέον SDKs, χωρίς COM interop, μόνο μια ενιαία αναφορά NuGet.

---

## Βήμα 1: Δημιουργία Εγγράφου Word (Κύριος Στόχος)

Το πρώτο που χρειαζόμαστε είναι ένας καθαρός καμβάς. Σκεφτείτε την κλάση `Document` ως μια φρέσκια σελίδα στο Microsoft Word· περιέχει ενότητες, παραγράφους και όλα τα άλλα που θα προσθέσετε αργότερα.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Step 1: Initialize a new blank document
Document doc = new Document();               // This creates an empty .docx in memory
```

Γιατί να ξεκινήσουμε με ένα κενό `Document`; Επειδή εγγυάται ότι δεν θα μπει κρυφή μορφοποίηση από κάποιο πρότυπο. Από την εμπειρία μου, η εκκίνηση από το μηδέν αποτρέπει μυστηριώδεις αλλαγές διάταξης όταν αργότερα εισάγετε σχήματα.

---

## Βήμα 2: Εισαγωγή Σχήματος Ορθογωνίου – Προσθήκη του Οπτικού Στοιχείου

Τώρα που έχουμε ένα έγγραφο, ας **add rectangle shape** στην πρώτη παράγραφο. Το αντικείμενο `Shape` είναι ευέλικτο· μπορείτε να επιλέξετε `ShapeType.Rectangle`, `Ellipse` ή ακόμη και προσαρμοσμένα σχέδια. Ακολουθεί ο ελάχιστος κώδικας:

```csharp
// Step 2: Create a rectangle and attach it to the first paragraph
Shape rect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,               // Width in points (≈2.78 inches)
    Height = 100,              // Height in points (≈1.39 inches)
    WrapType = WrapType.Inline // Makes the shape behave like a character
};

// Append the shape to the first paragraph (creates one if missing)
Paragraph firstPara = doc.FirstSection.Body.FirstParagraph;
firstPara.AppendChild(rect);
```

**Τι συμβαίνει στο παρασκήνιο;**

- `ShapeType.Rectangle` λέει στο Aspose ότι θέλουμε ένα απλό κουτί.  
- `WrapType.Inline` εξασφαλίζει ότι το ορθογώνιο κινείται μαζί με τη ροή του κειμένου, κάτι που συνήθως αναμένετε σε σενάριο επεξεργασίας κειμένου.  
- Με την προσθήκη στο `FirstParagraph`, αποφεύγουμε την ανάγκη χειροκίνητης εισαγωγής νέας παραγράφου· το Aspose δημιουργεί μία για εμάς αν το έγγραφο είναι πραγματικά κενό.  

> **Συμβουλή:** Αν χρειάζεστε το σχήμα να βρίσκεται *πίσω* από το κείμενο, αλλάξτε το `WrapType` σε `WrapType.Transparent`. Αυτή η μικρή αλλαγή μπορεί να κάνει τεράστια οπτική διαφορά.

---

## Βήμα 3: Εφαρμογή Εξωτερικής Σκιάς – Βελτίωση της Εμφάνισης

Ένα επίπεδο ορθογώνιο είναι… καλά, επίπεδο. Η προσθήκη ενός **add shadow to shape** του δίνει βάθος χωρίς επιπλέον εικόνες. Το `ShadowFormat` του Aspose το κάνει αυτό με μία γραμμή κώδικα.

```csharp
// Step 3: Configure an outer shadow for the rectangle
rect.ShadowFormat.Type = ShadowType.OuterShadow;
rect.ShadowFormat.Blur = 5.0;           // Softness of the shadow edge
rect.ShadowFormat.Distance = 3.0;      // How far the shadow is offset
rect.ShadowFormat.Angle = 45;          // Direction in degrees (45° = bottom‑right)
rect.ShadowFormat.Color = Color.Gray; // Classic gray shadow
```

Γιατί να ασχοληθούμε με αυτές τις συγκεκριμένες τιμές;

- **Blur** των `5.0` δίνει μια διακριτική θολή άκρη που φαίνεται επαγγελματική στα περισσότερα μοντέρνα.  
- **Distance** των `3.0` και **Angle** του `45` δημιουργούν μια φυσική πηγή φωτός από την πάνω‑αριστερή γωνία, μια κοινή σχεδιαστική σύμβαση.  
- `Color.Gray` λειτουργεί τόσο σε φωτεινά όσο και σε σκοτεινά θέματα· μπορείτε να το αντικαταστήσετε με `Color.Black` αν χρειάζεστε μεγαλύτερη αντίθεση.  

Αν ποτέ χρειαστείτε μια *εσωτερική* σκιά (σκεφτείτε ένα εσομένο κουμπί), απλώς αλλάξτε το `ShadowType.OuterShadow` σε `ShadowType.InnerShadow`. Οι ίδιες ιδιότητες ισχύουν ακόμη.

---

## Βήμα 4: Αποθήκευση του Εγγράφου ως DOCX – Διατήρηση της Εργασίας σας

Όλη η διασκέδαση είναι υπέροχη, αλλά τελικά θα θέλετε ένα αρχείο στον δίσκο. Το βήμα **save document as docx** είναι απλό:

```csharp
// Step 4: Persist the document to a .docx file
string outputPath = @"C:\Temp\ShadowedRectangle.docx";
doc.Save(outputPath, SaveFormat.Docx);
```

Μερικές σημειώσεις:

- Το enum `SaveFormat.Docx` εγγυάται τη σύγχρονη μορφή Office Open XML, η οποία είναι συμβατή με το Word 2007+.  
- Αν χρειάζεται να μεταφέρετε το αρχείο απευθείας σε απάντηση web, αντικαταστήστε τη διαδρομή αρχείου με ένα `MemoryStream` και γράψτε το στην HTTP response.  

Μετά την εκτέλεση του κώδικα, ανοίξτε το `ShadowedRectangle.docx` στο Microsoft Word. Θα πρέπει να δείτε ένα γκρι ορθογώνιο με ήπια σκιά, ενσωματωμένο στην πρώτη παράγραφο — ακριβώς αυτό που θέλαμε να πετύχουμε.

---

## Πώς να Προσθέσετε Σχήμα – Εναλλακτικές Προσεγγίσεις

Το παραπάνω παράδειγμα χρησιμοποιεί την προσέγγιση *inline*, αλλά μερικές φορές θέλετε ένα σχήμα που να αιωρείται πάνω από το κείμενο. Εκεί έρχεται σε παιχνίδι το **how to add shape** με διαφορετικό τύπο περιτύλιξης.

```csharp
Shape floatingRect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 250,
    Height = 120,
    WrapType = WrapType.Square, // Allows text to wrap around the shape
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    HorizontalAlignment = HorizontalAlignment.Center
};

doc.FirstSection.Body.FirstParagraph.AppendChild(floatingRect);
```

Εδώ αλλάξαμε το `WrapType` σε `Square` και κεντράραμε το σχήμα στη σελίδα. Αυτό το μοτίβο είναι χρήσιμο για εξώφυλλα ή διακοσμητικές λωρίδες. Θυμηθείτε: τα αιωρούμενα σχήματα αυξάνουν ελαφρώς το μέγεθος του αρχείου επειδή το Word αποθηκεύει πρόσθετα δεδομένα τοποθέτησης.

---

## Αναμενόμενο Αποτέλεσμα & Επαλήθευση

Όταν ανοίξετε το παραγόμενο αρχείο, θα πρέπει να δείτε:

- Μία μόνο παράγραφο που περιέχει ένα γκρι ορθογώνιο.  
- Το ορθογώνιο με διαστάσεις περίπου 2.8 × 1.4 ίντσες.  
- Μια διακριτική εξωτερική σκιά μετατοπισμένη προς τα κάτω‑δεξιά.  

Αν το σχήμα εμφανίζεται *εκτός* της παραγράφου, ελέγξτε ξανά το `WrapType`. Αν η σκιά φαίνεται πολύ σκληρή, μειώστε την τιμή `Blur` ή αλλάξτε το `Color` σε πιο ανοιχτό χρώμα.

---

## Συνηθισμένα Προβλήματα & Πώς να τα Αποφύγετε

| Πρόβλημα | Γιατί συμβαίνει | Διόρθωση |
|----------|------------------|----------|
| Το σχήμα εξαφανίζεται μετά την αποθήκευση | `WrapType` ορίστηκε σε `Inline` αλλά η παράγραφος αφαιρέθηκε | Βεβαιωθείτε ότι η παράγραφος υπάρχει· χρησιμοποιήστε `doc.FirstSection.Body.FirstParagraph` για να την εγγυηθείτε. |
| Η σκιά φαίνεται εικονοστοιχειωμένη | Χρήση πολύ χαμηλής τιμής `Blur` | Αυξήστε το `Blur` τουλάχιστον σε `3.0` για ομαλές άκρες. |
| Το μέγεθος του αρχείου αυξάνεται πολύ | Προσθήκη πολλών εικόνων υψηλής ανάλυσης μαζί με σχήματα | Χρησιμοποιήστε `doc.RemoveUnusedResources()` πριν την αποθήκευση αν προσθέσατε εικόνες. |
| Το χρώμα δεν εμφανίζεται σε σκοτεινή λειτουργία | Χρήση σκούρου `Color` για το ίδιο το σχήμα | Επιλέξτε ένα αντίθετο χρώμα (π.χ., `Color.White`) για καλύτερη ορατότητα. |

---

## Πλήρες Παράδειγμα Λειτουργίας

Παρακάτω είναι ο πλήρης κώδικας, έτοιμος για αντιγραφή‑και‑επικόλληση, που ενσωματώνει όλα όσα συζητήσαμε. Μπορείτε να τον εκτελέσετε ως εφαρμογή κονσόλας.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank Word document
        Document doc = new Document();

        // 2️⃣ Add a rectangle shape to the first paragraph
        Shape rect = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 200,
            Height = 100,
            WrapType = WrapType.Inline
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(rect);

        // 3️⃣ Apply an outer shadow to the rectangle
        rect.ShadowFormat.Type = ShadowType.OuterShadow;
        rect.ShadowFormat.Blur = 5.0;
        rect.ShadowFormat.Distance = 3.0;
        rect.ShadowFormat.Angle = 45;
        rect.ShadowFormat.Color = Color.Gray;

        // 4️⃣ Save the document as a .docx file
        string outPath = @"C:\Temp\ShadowShape.docx";
        doc.Save(outPath, SaveFormat.Docx);

        // Optional: Let the user know we’re done
        System.Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**Η εξήγηση κάθε τμήματος** είναι ενσωματωμένη ως σχόλια, ικανοποιώντας τόσο τους αναγνώστες SEO όσο και τους βοηθούς AI που αγαπούν τις αυτόνομες απαντήσεις.

---

## Συμπέρασμα

Μόλις **create word document** από την αρχή, μάθαμε **how to add shape**, συγκεκριμένα ένα **add rectangle shape**, του δώσαμε ένα **add shadow to shape**, και τέλος **save document as docx**. Τα βήματα είναι απλά, ο κώδικας συμπαγής, και το αποτέλεσμα φαίνεται επαγγελματικό.  

Αν είστε έτοιμοι να προχωρήσετε παραπέρα, δοκιμάστε να αντικαταστήσετε το ορθογώνιο με μια προσαρμοσμένη εικόνα, πειραματιστείτε με διαφορετικά χρώματα σκιάς, ή δημιουργήστε μια ολόκληρη αναφορά με πολλαπλές ενότητες σχήματος. Το API του Aspose.Words είναι αρκετά ευέλικτο για να διαχειριστεί τα πάντα, από τιμολόγια μέχρι διαφημιστικά φυλλάδια.  

Έχετε ερωτήσεις για άλλους τύπους σχημάτων ή χρειάζεστε βοήθεια για την ενσωμάτωση αυτού σε μια υπηρεσία ASP.NET Core; Αφήστε ένα σχόλιο παρακάτω, και καλή προγραμματιστική! 

![create word document with rectangle shape and shadow](placeholder-image.png "create word document with rectangle shape and shadow

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}