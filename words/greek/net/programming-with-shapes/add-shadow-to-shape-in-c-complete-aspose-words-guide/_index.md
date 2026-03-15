---
category: general
date: 2026-03-14
description: Προσθέστε γρήγορα σκιά σε σχήμα και μάθετε πώς να αλλάζετε τη γωνία της
  σκιάς, να αποθηκεύετε το έγγραφο με σκιά και πολλά άλλα σε αυτόν τον βήμα‑βήμα οδηγό
  C#.
draft: false
keywords:
- add shadow to shape
- change shadow angle
- how to add shape shadow
- save document with shadow
language: el
og_description: Προσθέστε σκιά σε σχήμα γρήγορα, μάθετε πώς να αλλάζετε τη γωνία της
  σκιάς και αποθηκεύστε το έγγραφο με σκιά χρησιμοποιώντας το Aspose.Words για .NET.
og_title: Προσθήκη σκιάς σε σχήμα στο C# – Πλήρης οδηγός Aspose.Words
tags:
- Aspose.Words
- C#
- Document Automation
title: Προσθήκη Σκιάς σε Σχήμα σε C# – Πλήρης Οδηγός Aspose.Words
url: /el/net/programming-with-shapes/add-shadow-to-shape-in-c-complete-aspose-words-guide/
---

Be careful to preserve markdown formatting exactly.

Let's craft translation.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Προσθήκη Σκιάς σε Σχήμα σε C# – Πλήρης Οδηγός Aspose.Words

Έχετε χρειαστεί ποτέ να **προσθέσετε σκιά σε σχήμα** αλλά δεν ήξερες ποιες ιδιότητες να ρυθμίσεις; Δεν είστε μόνοι· πολλοί προγραμματιστές αντιμετωπίζουν αυτό το πρόβλημα όταν στυλιζάρουν έγγραφα Word προγραμματιστικά. Τα καλά νέα είναι ότι με το Aspose.Words μπορείτε να ενεργοποιήσετε μια ρεαλιστική σκιά, να ρυθμίσετε τη γωνία της και να αποθηκεύσετε τις αλλαγές σε μια ενιαία, καθαρή ροή εργασίας.  

Σε αυτό το tutorial θα περάσουμε από όλα όσα χρειάζεται να ξέρετε: από τη φόρτωση ενός εγγράφου, την ενεργοποίηση της σκιάς, τη λεπτομερή ρύθμιση της εμφάνισής της, μέχρι τελικά **αποθήκευση εγγράφου με σκιά**. Στο τέλος θα μπορείτε να απαντήσετε στο “πώς να προσθέσετε σκιά σε σχήμα” χωρίς να σκάβετε σε διάσπαρτες δημοσιεύσεις φόρουμ.

## Τι Θα Χρειαστείτε

- **Aspose.Words for .NET** (v23.10 ή νεότερη – το API που χρησιμοποιούμε δεν έχει αλλάξει από τότε)
- Ένα IDE συμβατό με .NET (Visual Studio, Rider ή VS Code)
- Ένα απλό αρχείο Word (`input.docx`) που ήδη περιέχει τουλάχιστον ένα σχήμα (π.χ. ένα ορθογώνιο, εικόνα ή SmartArt)
- Βασικές γνώσεις C# – αν έχετε γράψει ένα “Hello World” πριν, είστε έτοιμοι

> **Pro tip:** Αν δεν έχετε έτοιμο έγγραφο, δημιουργήστε ένα γρήγορα στο Word, εισάγετε ένα σχήμα μέσω *Insert → Shapes*, και αποθηκεύστε το ως `input.docx` στο φάκελο του έργου σας.

## Βήμα 1 – Φόρτωση του Εγγράφου και Λήψη του Στόχου Σχήματος

Το πρώτο βήμα είναι να φέρετε το αρχείο Word στη μνήμη και να εντοπίσετε το σχήμα που θέλετε να διακοσμήσετε. Το Aspose.Words αντιμετωπίζει κάθε στοιχείο σχεδίασης ως κόμβο `Shape`, τον οποίο μπορείτε να ανακτήσετε με `GetChild`.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Load the Word document that contains a shape.
Document doc = new Document("YOUR_DIRECTORY/input.docx");

// Retrieve the first shape in the document (index 0). 
// If you have multiple shapes, change the index or loop through them.
Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
```

**Γιατί είναι σημαντικό:**  
`Document` είναι το σημείο εισόδου για οποιαδήποτε επεξεργασία. Η κλήση `GetChild` διασχίζει το δέντρο κόμβων βάθος‑πρώτο, εξασφαλίζοντας ότι παίρνετε το πρώτο σχήμα ανεξάρτητα από το πού βρίσκεται (κεφαλίδα, υποσέλιδο, σώμα). Αν παραλείψετε αυτό το βήμα και προσπαθήσετε να προσπελάσετε το `shape` απευθείας, θα αντιμετωπίσετε `NullReferenceException`.

## Βήμα 2 – Ενεργοποίηση του Εφέ Σκιάς

Οι σκιές είναι απενεργοποιημένες από προεπιλογή, οπότε πρέπει να τις ενεργοποιήσετε πριν ρυθμίσετε οποιεσδήποτε οπτικές ιδιότητες. Είναι μια μόνο γραμμή κώδικα, αλλά ξεκλειδώνει μια ολόκληρη σειρά επιλογών.

```csharp
// Turn the shadow on.
shape.Shadow.Enabled = true;
```

> **Το ήξερες;** Το αντικείμενο `Shadow` υπάρχει ακόμα και όταν η λειτουργία είναι απενεργοποιημένη, ώστε να μπορείτε να το προ‑ρυθμίσετε και να το ενεργοποιήσετε αργότερα χωρίς επιπλέον κώδικα.

## Βήμα 3 – Διαμόρφωση Βασικών Ιδιοτήτων Σκιάς

Τώρα φτάνουμε στο διασκεδαστικό μέρος: ορισμός χρώματος, διαφάνειας, θολώματος, απόστασης και μεγέθους. Αυτές οι τιμές εκφράζονται σε points ή ποσοστά, όπως στην UI του Word.

```csharp
// Basic visual settings
shape.Shadow.Color = Color.Black;          // Shadow colour
shape.Shadow.Transparency = 0.3f;          // 30 % transparent
shape.Shadow.BlurRadius = 5.0f;            // Softness of the edge
shape.Shadow.Distance = 3.0f;              // Gap between shape and shadow
shape.Shadow.Size = 100;                   // Scale of the shadow (percent)
```

**Εξήγηση:**  
- **Color** καθορίζει την απόχρωση· το μαύρο λειτουργεί στις περισσότερες περιπτώσεις, αλλά μπορείτε να ταιριάξετε τα χρώματα της μάρκας.  
- **Transparency** είναι μια τιμή τύπου float μεταξύ `0` (αδιαφανές) και `1` (πλήρως αόρατο).  
- **BlurRadius** ελέγχει πόσο «θολή» εμφανίζεται η σκιά· μεγαλύτεροι αριθμοί δίνουν πιο απαλό αποτέλεσμα.  
- **Distance** απομακρύνει τη σκιά από το σχήμα, δημιουργώντας βάθος.  
- **Size** κλιμακώνει τη σκιά αναλογικά – 100 % σημαίνει ότι η σκιά ταιριάζει με το μέγεθος του σχήματος.

## Βήμα 4 – Αλλαγή Γωνίας Σκιάς (Δευτερεύουσα Λέξη-Κλειδί)

Αν θέλετε η πηγή φωτός να φαίνεται από διαφορετική κατεύθυνση, προσαρμόστε την ιδιότητα `Angle`. Εδώ η λέξη‑κλειδί **change shadow angle** παίρνει τη θέση της.

```csharp
// Rotate the light source – 45 degrees is a common default.
shape.Shadow.Angle = 45;   // Angle in degrees (0‑360)
```

> **Τι γίνεται αν χρειάζεστε δραματικό εφέ;** Δοκιμάστε `0` για φως αριστερά‑προς‑δεξιά, `90` για πάνω‑προς‑κάτω, ή `180` για αντίστροφη σκιά. Θυμηθείτε ότι οι γωνίες κυκλώνουν, έτσι το `360` ισοδυναμεί με `0`.

## Βήμα 5 – Αποθήκευση Εγγράφου με Σκιά

Μόλις η σκιά φαίνεται όπως θέλετε, αποθηκεύστε τις αλλαγές. Η μέθοδος `Save` γράφει ένα νέο αρχείο αφήνοντας το αρχικό ανέπαφο.

```csharp
// Save the modified document.
doc.Save("YOUR_DIRECTORY/output.docx");
```

Τώρα έχετε ένα `output.docx` όπου το σχήμα διαθέτει μια επεξεργασμένη σκιά. Ανοίξτε το στο Word για να επαληθεύσετε – θα πρέπει να δείτε ένα διακριτικό, ημιδιαφανές halo που έχει μετατοπιστεί σύμφωνα με τη γωνία που ορίσατε.

## Πλήρες Παράδειγμα Λειτουργίας

Παρακάτω βρίσκεται ολόκληρο το πρόγραμμα, έτοιμο για αντιγραφή‑επικόλληση σε μια εφαρμογή console. Τα σχόλια εξηγούν κάθε μπλοκ.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the source document.
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Grab the first shape (adjust index if needed).
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            System.Console.WriteLine("No shape found in the document.");
            return;
        }

        // 3️⃣ Enable shadow.
        shape.Shadow.Enabled = true;

        // 4️⃣ Set visual properties.
        shape.Shadow.Color = Color.Black;
        shape.Shadow.Transparency = 0.3f;
        shape.Shadow.BlurRadius = 5.0f;
        shape.Shadow.Distance = 3.0f;
        shape.Shadow.Size = 100;

        // 5️⃣ Change shadow angle (how to add shape shadow from a different direction).
        shape.Shadow.Angle = 45; // Try 0, 90, 180, etc.

        // 6️⃣ Save the result – this is the step that lets you **save document with shadow**.
        doc.Save("YOUR_DIRECTORY/output.docx");

        System.Console.WriteLine("Shadow applied and document saved successfully!");
    }
}
```

### Αναμενόμενο Αποτέλεσμα

- Το άνοιγμα του `output.docx` δείχνει το αρχικό σχήμα τώρα περιτριγυρισμένο από μια απαλή, μαύρη σκιά.  
- Η αλλαγή του `Angle` σε `90` θα κάνει τη σκιά να εμφανίζεται ακριβώς κάτω από το σχήμα, μιμούμενη φωτισμό από πάνω.  
- Η ρύθμιση του `Transparency` σε `0.0f` δίνει μια αδιαφανή σκιά, ενώ το `1.0f` την κάνει αόρατη (χρήσιμο για εναλλαγή).

## Συνηθισμένα Προβλήματα & Πώς να τα Αποφύγετε

| Πρόβλημα | Γιατί Συμβαίνει | Διόρθωση |
|----------|----------------|----------|
| **`shape` is `null`** | Το έγγραφο δεν περιέχει σχήματα ή το δείκτη είναι λανθασμένος. | Επαληθεύστε ότι το αρχείο Word περιέχει σχήμα, ή κάντε βρόχο μέσω `doc.GetChildNodes(NodeType.Shape, true)` για να βρείτε το σωστό. |
| **Shadow doesn’t appear in Word** | Το `Shadow.Enabled` παραμένει `false` ή ο τύπος σχήματος δεν υποστηρίζει σκιές (π.χ. απλό κείμενο). | Βεβαιωθείτε ότι εργάζεστε με αντικείμενο `Shape` (εικόνες, σχέδια, SmartArt) και ότι `Enabled = true`. |
| **Unexpected colour** | Το `Color` έχει οριστεί σε τιμή διαφορετική από αυτή που βλέπετε στο Word λόγω παρακάμψεων θέματος. | Χρησιμοποιήστε `Color.FromArgb(0,0,0)` για καθαρό μαύρο, ή ταιριάξτε το θέμα του εγγράφου με `shape.Shadow.ThemeColor`. |
| **Performance slowdown** | Τροποποίηση πολλών σχημάτων σε μεγάλο έγγραφο χωρίς ομαδοποίηση. | Τυλίξτε τις αλλαγές σε `doc.BeginUpdateWords()` / `doc.EndUpdateWords()` (Aspose.Words v24+). |

## Επέκταση του Παραδείγματος

- **Multiple Shapes:** Κάντε βρόχο σε όλα τα σχήματα και εφαρμόστε ομοιόμορφη σκιά, ή διαφοροποιήστε το `Angle` ανά σχήμα για εφέ 3‑Δ.  
- **Dynamic Colours:** Αντλήστε τιμές χρώματος από αρχείο ρυθμίσεων ώστε να ταιριάζουν με την εταιρική ταυτότητα.  
- **Conditional Shadows:** Προσθέστε σκιά μόνο αν το πλάτος του σχήματος υπερβαίνει ένα όριο – ιδανικό για ανάδειξη μεγάλων διαγραμμάτων.

```csharp
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.Width > 200) // width in points
    {
        s.Shadow.Enabled = true;
        s.Shadow.Color = Color.Gray;
        s.Shadow.Angle = 30;
    }
}
```

## Συμπέρασμα

Καλύψαμε ολόκληρο τον κύκλο ζωής της **προσθήκης σκιάς σε σχήμα** χρησιμοποιώντας το Aspose.Words for .NET: φόρτωση του εγγράφου, ενεργοποίηση της σκιάς, προσαρμογή χρώματος, θολώματος, απόστασης, **αλλαγή γωνίας σκιάς**, και τελικά **αποθήκευση εγγράφου με σκιά**. Ο κώδικας είναι αυτόνομος, λειτουργεί με οποιαδήποτε πρόσφατη έκδοση του Aspose.Words, και δείχνει τόσο το “πώς” όσο και το “γιατί” πίσω από κάθε ιδιότητα.

Έτοιμοι για το επόμενο βήμα; Δοκιμάστε σκιές με διαβάθμιση ή συνδυάστε αυτήν την τεχνική με εφέ κειμένου για να δημιουργήσετε εντυπωσιακές αναφορές. Αν συναντήσετε ειδικές περιπτώσεις—όπως σχήματα μέσα σε κεφαλίδες ή υποσέλιδα—θυμηθείτε τα κόλπα διαπέρασης του δέντρου κόμβων που συζητήσαμε.  

Καλή προγραμματιστική δουλειά, και οι εγγραφές σας να έχουν πάντα το τέλειο βάθος!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}