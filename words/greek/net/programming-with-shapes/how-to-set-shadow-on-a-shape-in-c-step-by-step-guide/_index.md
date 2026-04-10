---
category: general
date: 2026-04-10
description: πώς να ορίσετε σκιά σε σχήμα σε C# – μάθετε πώς να εφαρμόζετε σκιά πτώσης,
  να αλλάζετε τη διαφάνεια, να ρυθμίζετε το θόλωμα και να προσθέτετε σκιά σχήματος
  χρησιμοποιώντας το Aspose.Words.
draft: false
keywords:
- how to set shadow
- apply drop shadow
- how to change transparency
- how to adjust blur
- add shape shadow
language: el
og_description: πώς να ορίσετε σκιά σε ένα σχήμα σε C# – αυτό το σεμινάριο δείχνει
  πώς να εφαρμόσετε σκιά πτώσης, να αλλάξετε τη διαφάνεια, να ρυθμίσετε τη θόλωση
  και να προσθέσετε σκιά σχήματος με σαφή παραδείγματα κώδικα.
og_title: πώς να ορίσετε σκιά σε ένα σχήμα στο C# – Πλήρης Οδηγός
tags:
- Aspose.Words
- C#
- Document Automation
title: πώς να ορίσετε σκιά σε ένα σχήμα σε C# – βήμα‑βήμα οδηγός
url: /el/net/programming-with-shapes/how-to-set-shadow-on-a-shape-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# πώς να ορίσετε σκιά σε σχήμα στο C# – Πλήρης Οδηγός

Έχετε αναρωτηθεί ποτέ **πώς να ορίσετε σκιά** σε ένα σχήμα όταν δημιουργείτε προγραμματιστικά ένα έγγραφο Word; Δεν είστε μόνοι. Πολλοί προγραμματιστές συναντούν δυσκολίες όταν χρειάζονται μια διακριτική σκιά για ένα πλαίσιο κειμένου, ένα λογότυπο ή ένα πλαίσιο επεξήγησης, και η τεκμηρίωση του API φαίνεται λίγο ασαφής.  

Σε αυτό το tutorial θα περάσουμε από όλη τη διαδικασία: από τη φόρτωση ενός `.docx`, την ανάκτηση του πρώτου `Shape`, την εφαρμογή μιας σκιάς, τη ρύθμιση της διαφάνειας, την προσαρμογή της ακτίνας θολώματος και, τέλος, τη σωστή τοποθέτησή της. Στο τέλος θα έχετε ένα επαναχρησιμοποιήσιμο snippet που λειτουργεί με Aspose.Words .NET 2023 ή νεότερο, και θα καταλάβετε *γιατί* κάθε ιδιότητα είναι σημαντική.

## Τι Θα Χρειαστείτε

- **Aspose.Words for .NET** (πακέτο NuGet `Aspose.Words`) – η βιβλιοθήκη που μας παρέχει τις κλάσεις `Document`, `Shape` και `ShadowFormat`.  
- **.NET 6+** (ή .NET Framework 4.7.2) – οποιοδήποτε πρόσφατο runtime αρκεί.  
- Ένα απλό αρχείο Word (`input.docx`) που περιέχει τουλάχιστον ένα σχήμα, όπως ένα πλαίσιο κειμένου.  
- Visual Studio, VS Code ή το αγαπημένο σας IDE.

Αυτό είναι όλο. Χωρίς επιπλέον εργαλεία τρίτων, χωρίς COM interop, μόνο καθαρό C#.

![how to set shadow example](image-placeholder.png){:alt="πώς να ορίσετε σκιά σε σχήμα σε έγγραφο Word"}

## Πώς να Ορίσετε Σκιά – Επισκόπηση

Η βασική ιδέα πίσω από **πώς να ορίσετε σκιά** είναι η διαχείριση του αντικειμένου `ShadowFormat` που ανήκει σε ένα `Shape`. Σκεφτείτε το `ShadowFormat` ως ένα μικροσκοπικό “στυλ” για τη σκιά: λέει στον renderer αν η σκιά είναι ορατή, ποιο χρώμα πρέπει να έχει, πόσο διαφανής είναι, πόσο θολή, και πού βρίσκεται σε σχέση με το σχήμα.  

Παρακάτω είναι το *πλήρες* εκτελέσιμο πρόγραμμα. Μπορείτε να το αντιγράψετε σε μια εφαρμογή κονσόλας, να πατήσετε **F5**, και να δείτε τη σκιά να εμφανίζεται στο αποθηκευμένο `output.docx`.

```csharp
using System;
using System.Drawing;               // For Color
using Aspose.Words;                 // Core document classes
using Aspose.Words.Drawing;         // Shape & ShadowFormat

class ShadowDemo
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1: Load the Word document that contains the shape.
        // -------------------------------------------------
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // -------------------------------------------------
        // Step 2: Retrieve the first shape (e.g., a textbox) from the document.
        // -------------------------------------------------
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found – make sure input.docx has a textbox.");
            return;
        }

        // -------------------------------------------------
        // Step 3: Make the shadow visible.
        // -------------------------------------------------
        shape.ShadowFormat.Visible = true;

        // -------------------------------------------------
        // Step 4: Set the shadow colour to a dark gray.
        // -------------------------------------------------
        shape.ShadowFormat.Color = Color.DarkGray;

        // -------------------------------------------------
        // Step 5: Define the shadow's transparency (30 % transparent).
        // -------------------------------------------------
        shape.ShadowFormat.Transparency = 0.3;   // 0 = opaque, 1 = fully transparent

        // -------------------------------------------------
        // Step 6: Configure the blur radius (size) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Size = 6;            // Larger value = softer edges

        // -------------------------------------------------
        // Step 7: Set the offset distance and direction (angle) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Distance = 2;        // How far the shadow is from the shape
        shape.ShadowFormat.Angle = 45;          // Angle in degrees (0 = right, 90 = down)

        // -------------------------------------------------
        // Save the modified document.
        // -------------------------------------------------
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Shadow applied successfully! Check output.docx.");
    }
}
```

### Γιατί Αυτές οι Ρυθμίσεις Είναι Σημαντικές

- **Visible** – Χωρίς την ενεργοποίηση αυτής της σημαίας, όλες οι άλλες ιδιότητες αγνοούνται.  
- **Color** – Ένα σκούρο γκρι μιμείται μια τυπική UI σκιά· μπορείτε να αντικαταστήσετε με οποιοδήποτε `Color`.  
- **Transparency** – 0.3 δίνει μια *μαλακή* εμφάνιση ενώ διατηρεί το σχήμα αναγνώσιμο.  
- **Size** – Ελέγχει το θόλωμα· μια τιμή 6 είναι συνήθως αρκετή για επαγγελματικό αποτέλεσμα.  
- **Distance & Angle** – Μαζί ορίζουν το *offset*· 2 pts σε 45° δημιουργούν μια διακριτική διαγώνια σκιά.

Αυτή είναι η ουσία του **πώς να ορίσετε σκιά**. Στη συνέχεια, θα αναλύσουμε κάθε μέρος ώστε να μπορείτε να **εφαρμόσετε σκιά**, **αλλάξετε τη διαφάνεια**, **ρυθμίσετε το θόλωμα**, και **προσθέσετε σκιά σε σχήμα** ξεχωριστά.

---

## Εφαρμόστε Drop Shadow σε Σχήμα

Όταν οι άνθρωποι ρωτούν “πώς **εφαρμόζω drop shadow** σε C#;”, συχνά χρειάζονται μόνο την ενεργοποίηση της ορατότητας και ένα χρώμα. Το παρακάτω snippet απομονώνει αυτές τις δύο γραμμές:

```csharp
shape.ShadowFormat.Visible = true;          // Turns the shadow on
shape.ShadowFormat.Color   = Color.Black;   // Classic black drop shadow
```

> **Pro tip:** Αν στοχεύετε σε παλαιότερες εκδόσεις του Word (2003‑2007), χρησιμοποιήστε τυπικά χρώματα. Ορισμένες εξωτικές τιμές ARGB μπορεί να αγνοηθούν από τον παλαιό renderer.

---

## Πώς να Αλλάξετε τη Διαφάνεια της Σκιάς

Η διαφάνεια εκφράζεται ως **float μεταξύ 0 και 1**. Μια τιμή **0** σημαίνει εντελώς αδιαφανή σκιά· **1** την κάνει αόρατη. Οι περισσότεροι σχεδιαστές επιλέγουν τιμές γύρω στο **0.2‑0.4** για φυσική εμφάνιση.

```csharp
shape.ShadowFormat.Transparency = 0.35; // 35 % transparent
```

### Ακραίες Περιπτώσεις

- **Αρνητικές τιμές** – Το Aspose.Words θα τις περιορίσει σε 0, αλλά είναι καλύτερο να επικυρώνετε την είσοδο.  
- **Τιμές > 1** – Περιορίζονται σε 1, κρύβοντας ουσιαστικά τη σκιά.  

Αν χρειάζεται να επιτρέψετε στους χρήστες να επιλέγουν ποσοστό, μετατρέψτε το πρώτα:

```csharp
float percent = 30;                     // User enters 30 %
shape.ShadowFormat.Transparency = percent / 100f;
```

---

## Πώς να Ρυθμίσετε το Θόλωμα (Size) της Σκιάς

Η ιδιότητα **Size** ελέγχει την ακτίνα θολώματος. Μεγαλύτεροι αριθμοί παράγουν πιο μαλακή, πιο διασκορπισμένη σκιά. Μετράται σε points (pt), όχι σε pixels.

```csharp
shape.ShadowFormat.Size = 10;  // A generous blur for a “soft” effect
```

#### Πότε να Χρησιμοποιήσετε Μικρό vs. Μεγάλο Θόλωμα

- **Μικρό θόλωμα (2‑4 pt)** – Κατάλληλο για UI‑στυλ callouts όπου θέλετε καθαρή άκρη.  
- **Μεγάλο θόλωμα (8‑12 pt)** – Λειτουργεί καλά για εκτυπωμένες αναφορές ή όταν το σχήμα είναι μακριά από το φόντο.

---

## Προσθήκη Σκιάς σε Σχήμα – Τοποθέτηση και Κατεύθυνση

Το τελικό κομμάτι του **add shape shadow** είναι το offset. Δύο ιδιότητες λειτουργούν μαζί:

| Property | Meaning |
|----------|---------|
| **Distance** | Πόσο μακριά βρίσκεται η σκιά από το σχήμα (σε points). |
| **Angle**    | Κατεύθυνση του offset (0° = δεξιά, 90° = κάτω, 180° = αριστερά, 270° = πάνω). |

Παράδειγμα που δημιουργεί μια διακριτική σκιά κάτω‑δεξιά:

```csharp
shape.ShadowFormat.Distance = 1.5; // Slight lift
shape.ShadowFormat.Angle    = 135; // Down‑left direction (135°)
```

Μπορείτε να πειραματιστείτε με γωνίες για να προσομοιώσετε φως από διαφορετικές πηγές. Ένα κοινό κόλπο είναι να αφήσετε τον χρήστη να επιλέγει μια “πηγή φωτός” από ένα dropdown και να τη χαρτογραφήσετε σε τιμή γωνίας.

---

## Πλήρες Παράδειγμα (Όλα τα Βήματα Συνδυασμένα)

Παρακάτω είναι το ίδιο πρόγραμμα όπως πριν, αλλά με **πρόσθετα σχόλια** που κάνουν τη λογική απόλυτα σαφή. Αντιγράψτε το στο `Program.cs` και τρέξτε το· το αρχείο εξόδου θα περιέχει ένα πλαίσιο κειμένου με τέλεια ρυθμισμένη σκιά.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeShadowDemo
{
    class Program
    {
        static void Main()
        {
            // Load the source document (must contain at least one shape)
            Document doc = new Document("YOUR_DIRECTORY/input.docx");

            // Grab the first shape we encounter – usually a textbox or picture
            Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
            if (shape == null)
            {
                Console.WriteLine("No shape found in the document.");
                return;
            }

            // ---------- Apply Drop Shadow ----------
            shape.ShadowFormat.Visible = true;          // Turn it on
            shape.ShadowFormat.Color   = Color.DarkGray; // Soft dark colour

            // ---------- How to Change Transparency ----------
            shape.ShadowFormat.Transparency = 0.3; // 30 % transparent – looks natural

            // ---------- How to Adjust Blur ----------
            shape.ShadowFormat.Size = 6; // Moderate blur for a professional feel

            // ---------- Add Shape Shadow (position) ----------
            shape.ShadowFormat.Distance = 2; // Slight offset
            shape.ShadowFormat.Angle    = 45; // Diagonal down‑right

            // Save the result
            doc.Save("YOUR_DIRECTORY/output.docx");
            Console.WriteLine("Document saved with shadow. Open output.docx to verify.");
        }
    }
}
```

**Αναμενόμενο αποτέλεσμα:** Ανοίξτε το `output.docx`. Το πρώτο πλαίσιο κειμένου θα εμφανίζει μια σκούρο γκρι, 30 % διαφανή σκιά που είναι ελαφρώς θολή (size = 6) και μετατοπισμένη 2 pt σε γωνία 45°. Το αποτέλεσμα είναι διακριτικό αλλά εμφανές—ακριβώς αυτό που επιδιώκουν οι περισσότεροι UI σχεδιαστές.

---

## Συχνές Ερωτήσεις & Πιθανά Προβλήματα

- **“Λειτουργεί αυτό και με εικόνες επίσης?”**  
  Ναι. Οποιοδήποτε `Shape`—είτε είναι πλαίσιο κειμένου, εικόνα ή auto‑shape—έχει `ShadowFormat`. Απλώς αντικαταστήστε τη λογική ανάκτησης σχήματος με το κατάλληλο index ή όνομα.

- **“Τι γίνεται αν το έγγραφο έχει πολλά σχήματα?”**  
  Κάντε βρόχο μέσω `doc.GetChildNodes(NodeType.Shape, true)` και εφαρμόστε τις ίδιες ρυθμίσεις σε καθένα. Μπορείτε επίσης να φιλτράρετε με `shape.Name` ή `shape

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}