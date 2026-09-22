---
category: general
date: 2026-02-18
description: Δημιουργήστε σχήμα ορθογωνίου χρησιμοποιώντας το Aspose.Words και μάθετε
  πώς να προσθέσετε σκιά, να ορίσετε το μέγεθος του σχήματος και να αποθηκεύσετε το
  έγγραφο Word σε λίγα λεπτά.
draft: false
keywords:
- create rectangle shape
- how to add shadow
- save word document
- set shape size
- how to create document
language: el
og_description: Δημιουργήστε σχήμα ορθογωνίου σε αρχείο Word, μάθετε πώς να προσθέσετε
  σκιά, ορίστε το μέγεθος του σχήματος και αποθηκεύστε το έγγραφο με το Aspose.Words
  σε C#.
og_title: Δημιουργία σχήματος ορθογωνίου στο Word – Πλήρης οδηγός Aspose.Words
tags:
- Aspose.Words
- C#
- Word automation
title: Δημιουργία σχήματος ορθογωνίου στο Word με το Aspose.Words – Οδηγός βήμα‑προς‑βήμα
url: /el/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία σχήματος ορθογωνίου στο Word με Aspose.Words – Οδηγός βήμα‑βήμα

Κάποτε χρειάστηκε να **δημιουργήσετε σχήμα ορθογωνίου** σε ένα αρχείο Word αλλά δεν ήξερατε από πού να ξεκινήσετε; Δεν είστε μόνοι—οι προγραμματιστές συχνά ρωτούν: «πώς προσθέτω σκιά σε ένα σχήμα και ταυτόχρονα το έγγραφο παραμένει επεξεργάσιμο;» Σε αυτό το tutorial θα απαντήσουμε σε αυτό και θα σας δείξουμε επίσης **πώς να προσθέσετε σκιά**, **πώς να ορίσετε το μέγεθος του σχήματος**, και **πώς να αποθηκεύσετε το έγγραφο Word** όλα σε μία ομαλή ροή.

Θα περάσουμε από όλα όσα χρειάζεστε, από την αρχικοποίηση ενός νέου εγγράφου (ναι, αυτό είναι το πρώτο βήμα για **πώς να δημιουργήσετε έγγραφο**) μέχρι την αποθήκευση του τελικού *.docx* στο δίσκο. Χωρίς εξωτερικές αναφορές, μόνο ένα αυτόνομο παράδειγμα που μπορείτε να αντιγράψετε‑επικολλήσετε στο Visual Studio και να τρέξετε σήμερα.

---

## Προαπαιτούμενα

- .NET 6+ (ή .NET Framework 4.7+). Το Aspose.Words λειτουργεί με οποιοδήποτε πρόσφατο .NET runtime.
- Έγκυρη άδεια Aspose.Words (ή το δωρεάν κλειδί αξιολόγησης) – διαφορετικά θα εμφανίζεται υδατογράφημα.
- Visual Studio, Rider ή οποιονδήποτε επεξεργαστή C# προτιμάτε.
- Βασικές γνώσεις C#—τίποτα περίπλοκο, μόνο η δυνατότητα να τρέξετε μια εφαρμογή κονσόλας.

> **Pro tip:** Αν εργάζεστε σε Mac, ο ίδιος κώδικας τρέχει υπό .NET 6 με VS Code—απλώς βεβαιωθείτε ότι έχετε αναφερθεί στο πακέτο NuGet `Aspose.Words`.

---

## Βήμα 1: Αρχικοποίηση του εγγράφου – το θεμέλιο του **πώς να δημιουργήσετε έγγραφο**

Πριν μπορέσουμε να σχεδιάσουμε οτιδήποτε, χρειαζόμαστε έναν κενό καμβά. Το Aspose.Words το ονομάζει `Document`.  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Create a new blank document
Document document = new Document();
```

> **Γιατί είναι σημαντικό:** Το αντικείμενο `Document` αντιπροσωπεύει ολόκληρο το αρχείο *.docx*. Όλα τα σχήματα, οι παράγραφοι και οι ενότητες που προσθέτετε γίνονται παιδιά αυτού του αντικειμένου. Ξεκινώντας με ένα καθαρό έγγραφο εξασφαλίζετε ότι δεν υπάρχουν κρυφά στυλ που θα επηρεάσουν το ορθογώνιο σας.

---

## Βήμα 2: Ορισμός του ορθογωνίου και **ορισμός μεγέθους σχήματος**

Ένα ορθογώνιο είναι απλώς ένα `Shape` με `ShapeType.Rectangle`. Θα του δώσουμε ρητές διαστάσεις ώστε να φαίνεται ακριβώς όπως θέλουμε.

```csharp
// Step 2: Create a rectangular shape and define its size
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 200; // width in points (≈2.78 inches)
rectangleShape.Height = 100; // height in points (≈1.39 inches)
```

> **Τι σημαίνουν οι αριθμοί:** Το Aspose.Words χρησιμοποιεί μονάδες σημείου (1 pt = 1/72 in). Προσαρμόστε τις τιμές ώστε να ταιριάζουν στο layout σας· για μια τυπική σελίδα A4, 200 pt είναι ένα άνετο πλάτος.

---

## Βήμα 3: **Πώς να προσθέσετε σκιά** – κάντε το σχήμα να «αναδειχθεί»

Οι σκιές δίνουν μια οπτική ένδειξη ότι το σχήμα είναι «υψωμένο» από τη σελίδα. Η ιδιότητα `Shadow` σας επιτρέπει να ρυθμίσετε χρώμα, απόσταση, διαφάνεια και θολότητα.

```csharp
// Step 3: Apply a shadow to the shape
rectangleShape.Shadow.Color        = Color.Black; // Shadow color
rectangleShape.Shadow.Distance    = 5;           // Offset distance in points
rectangleShape.Shadow.Transparency = 0.4;        // 40 % transparent
rectangleShape.Shadow.BlurRadius  = 8;           // Soft edge radius
```

> **Γιατί η διαφάνεια:** Μια πλήρως αδιαφανής σκιά μπορεί να φαίνεται σκληρή. Ορίζοντάς την στο 0.4 το εφέ γίνεται πιο διακριτικό και επαγγελματικό.

---

## Βήμα 4: Τοποθέτηση του ορθογωνίου – ενσωμάτωση στη ροή κειμένου

Αν θέλετε το σχήμα να συμπεριφέρεται σαν χαρακτήρας σε μια παράγραφο, ορίστε το `WrapType` σε `Inline`. Αυτό διατηρεί τη διάταξη προβλέψιμη, ειδικά όταν το έγγραφο επεξεργαστεί αργότερα.

```csharp
// Step 4: Set the shape to flow inline with the surrounding text
rectangleShape.WrapType = WrapType.Inline;
```

> **Ακραία περίπτωση:** Αν χρειάζεστε το ορθογώνιο να «πλέει» πάνω από το κείμενο (π.χ. υδατογράφημα), αλλάξτε το `WrapType` σε `Square` ή `BehindText`.

---

## Βήμα 5: Εισαγωγή του σχήματος στο σώμα του εγγράφου

Τώρα τοποθετούμε πραγματικά το ορθογώνιο στην πρώτη παράγραφο. Αν το έγγραφο δεν έχει ακόμη περιεχόμενο, το `FirstParagraph` δημιουργείται αυτόματα.

```csharp
// Step 5: Insert the shape into the first paragraph of the document
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

> **Συμβουλή:** Μπορείτε επίσης να δημιουργήσετε μια νέα παράγραφο πρώτα και μετά να προσαρτήσετε το σχήμα—χρήσιμο όταν χρειάζεται περιβάλλον κείμενο.

---

## Βήμα 6: **Αποθήκευση εγγράφου Word** – το τελικό βήμα

Με όλα στη θέση τους, η αποθήκευση του αρχείου γίνεται με μία γραμμή κώδικα. Επιλέξτε οποιοδήποτε μονοπάτι θέλετε· το παράδειγμα χρησιμοποιεί ένα placeholder που πρέπει να αντικαταστήσετε με το δικό σας φάκελο.

```csharp
// Step 6: Save the document with the shadowed shape
document.Save(@"C:\Temp\ShadowShape.docx");
```

> **Αποτέλεσμα:** Ανοίξτε το παραγόμενο *.docx* στο Microsoft Word. Θα δείτε ένα ορθογώνιο με μαύρη σκιά, πλάτος 200 pt και ύψος 100 pt, ενσωματωμένο στην πρώτη παράγραφο.

---

## Αναμενόμενο αποτέλεσμα

Όταν ανοίξετε **ShadowShape.docx**, το έγγραφο εμφανίζει:

- Μία ενιαία παράγραφο που περιέχει ένα σχήμα ορθογωνίου.
- Το ορθογώνιο έχει μια διακριτική μαύρη σκιά με μετατόπιση 5 pt.
- Το μέγεθος του σχήματος ταιριάζει με τις διαστάσεις που ορίστηκαν στο Βήμα 2.
- Δεν εμφανίζεται επιπλέον κείμενο εκτός αν το προσθέσετε χειροκίνητα.

Αν το σχήμα δεν εμφανίζεται, ελέγξτε ξανά ότι έχετε αναφερθεί στη σωστή έκδοση του Aspose.Words και ότι η άδειά σας (ή η δοκιμαστική) είναι ενεργή.

---

## Συχνές ερωτήσεις & Παραλλαγές

| Ερώτηση | Απάντηση |
|----------|--------|
| *Μπορώ να αλλάξω το χρώμα της σκιάς σε κάτι άλλο εκτός του μαύρου;* | Φυσικά—ορίστε `rectangleShape.Shadow.Color = Color.Blue;` ή οποιοδήποτε `System.Drawing.Color`. |
| *Τι γίνεται αν χρειαστώ μεγαλύτερο ορθογώνιο;* | Προσαρμόστε τις τιμές `Width` και `Height`. Θυμηθείτε ότι είναι σε σημεία· 72 pt = 1 in. |
| *Μπορεί να τοποθετηθεί το σχήμα σε απόλυτη θέση;* | Ναι—χρησιμοποιήστε `WrapType = WrapType.Absolute` και ορίστε τις ιδιότητες `Top`/`Left`. |
| *Λειτουργεί αυτό με .NET Core;* | Ναι. Το Aspose.Words είναι cross‑platform· απλώς εγκαταστήστε το πακέτο NuGet για .NET Standard. |
| *Μπορώ να προσθέσω κείμενο μέσα στο ορθογώνιο;* | Όχι άμεσα· θα πρέπει να εισάγετε ένα σχήμα `TextBox` αντί για απλό ορθογώνιο. |

---

## Πλήρες λειτουργικό παράδειγμα (Έτοιμο για αντιγραφή‑επικόλληση)

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize a new document
        Document document = new Document();

        // 2️⃣ Create rectangle and set its size
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width  = 200;
        rectangleShape.Height = 100;

        // 3️⃣ Add a subtle black shadow
        rectangleShape.Shadow.Color         = Color.Black;
        rectangleShape.Shadow.Distance     = 5;
        rectangleShape.Shadow.Transparency = 0.4;
        rectangleShape.Shadow.BlurRadius   = 8;

        // 4️⃣ Make the shape flow inline with text
        rectangleShape.WrapType = WrapType.Inline;

        // 5️⃣ Insert the shape into the first paragraph
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // 6️⃣ Persist the file
        document.Save(@"C:\Temp\ShadowShape.docx");

        System.Console.WriteLine("Document saved successfully!");
    }
}
```

Τρέξτε το πρόγραμμα, μεταβείτε στο `C:\Temp\ShadowShape.docx` και θα δείτε το ορθογώνιο με σκιά ακριβώς όπως περιγράφηκε.

---

## Συμπέρασμα

Τώρα ξέρετε πώς να **δημιουργήσετε σχήμα ορθογωνίου** σε ένα αρχείο Word χρησιμοποιώντας το Aspose.Words, πώς να **ορίσετε το μέγεθος του σχήματος**, **προσθέσετε σκιά**, και τελικά **αποθηκεύσετε το έγγραφο Word** με τις αλλαγές. Η όλη διαδικασία—από το **πώς να δημιουργήσετε έγγραφο** μέχρι την αποθήκευση του αποτελέσματος—περιλαμβάνεται σε λίγες γραμμές C# και μπορεί να επεκταθεί για πιο σύνθετες διατάξεις.

Έτοιμοι για την επόμενη πρόκληση; Δοκιμάστε να αντικαταστήσετε το ορθογώνιο με σχήμα με στρογγυλεμένες γωνίες, πειραματιστείτε με διαφορετικά χρώματα σκιάς, ή ενσωματώστε το σχήμα μέσα σε κελί πίνακα. Κάθε τροποποίηση ενισχύει τις ίδιες βασικές έννοιες που καλύψαμε εδώ.

Αν βρήκατε αυτόν τον οδηγό χρήσιμο, μοιραστείτε τον, αφήστε ένα σχόλιο με τις δικές σας παραλλαγές, ή εξερευνήστε τα άλλα tutorials μας για αυτοματοποίηση Word, όπως η εισαγωγή εικόνων ή η δημιουργία πινάκων με Aspose.Words. Καλή κωδικοποίηση!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}