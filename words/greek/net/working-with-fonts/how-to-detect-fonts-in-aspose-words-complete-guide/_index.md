---
category: general
date: 2026-04-21
description: Μάθετε πώς να εντοπίζετε γραμματοσειρές, να καταγράφετε προειδοποιήσεις,
  να ρυθμίζετε την κλήση επιστροφής και να απαριθμείτε τις προειδοποιήσεις με το Aspose.Words
  σε C#. Οδηγός βήμα‑βήμα για αξιόπιστη διαχείριση γραμματοσειρών.
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- how to configure callback
- how to enumerate warnings
- Aspose.Words font handling
language: el
og_description: Πώς να εντοπίσετε τις γραμματοσειρές στο Aspose.Words; Αυτό το σεμινάριο
  σας δείχνει πώς να συλλάβετε προειδοποιήσεις, να ρυθμίσετε μια κλήση επιστροφής
  και να απαριθμήσετε τις προειδοποιήσεις σε C#.
og_title: Πώς να εντοπίσετε γραμματοσειρές στο Aspose.Words – Πλήρης οδηγός
tags:
- Aspose.Words
- C#
- Document Processing
title: Πώς να ανιχνεύσετε τις γραμματοσειρές στο Aspose.Words – Πλήρης οδηγός
url: /el/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Εντοπίσετε Γραμματοσειρές στο Aspose.Words – Πλήρης Οδηγός

Έχετε αναρωτηθεί ποτέ **πώς να εντοπίσετε γραμματοσειρές** που λείπουν όταν φορτώνετε ένα έγγραφο Word; Είναι ένα σενάριο που εμφανίζεται πιο συχνά απ' ό,τι θα θέλατε, ειδικά όταν εργάζεστε με παλιά αρχεία ή διασυνοριακές αναπτύξεις. Σε αυτό το tutorial θα περάσουμε από ένα πλήρες, εκτελέσιμο παράδειγμα που **καταγράφει προειδοποιήσεις**, **ρυθμίζει μια callback**, και **απαριθμεί προειδοποιήσεις** ώστε να γνωρίζετε πάντα ποιες γραμματοσειρές αντικαταστάθηκαν.

Θα χρησιμοποιήσουμε Aspose.Words for .NET (v24.9 τη στιγμή της συγγραφής) και απλό C#. Χωρίς εξωτερικές υπηρεσίες, χωρίς μαγεία—μόνο το API και μερικές γραμμές κώδικα. Στο τέλος θα μπορείτε να εντοπίζετε κάθε αντικατάσταση γραμματοσειράς, να την καταγράφετε και ακόμη να αποφασίζετε αν θα ακυρώσετε τη φόρτωση όταν λείπει μια κρίσιμη γραμματοσειρά.

### Τι Θα Χρειαστείτε
- **Aspose.Words for .NET** (εγκατάσταση μέσω NuGet: `Install-Package Aspose.Words`)
- .NET 6.0 ή νεότερο (ο κώδικας λειτουργεί και σε .NET Framework)
- Ένα δείγμα DOCX που αναφέρει μια γραμματοσειρά που δεν υπάρχει στο μηχάνημα (π.χ., “MyCustomFont.ttf”)
- Visual Studio, Rider ή οποιονδήποτε επεξεργαστή C# προτιμάτε

> **Συμβουλή:** Αν δεν έχετε έγγραφο με ελλιπείς γραμματοσειρές, απλώς μετονομάστε ένα αρχείο γραμματοσειράς στο σύστημά σας ή επεξεργαστείτε το XML του DOCX ώστε να αναφέρει μια μη‑υπάρχουσα οικογένεια γραμματοσειρών.

---

## Πώς να Εντοπίσετε Γραμματοσειρές με το Aspose.Words

Η βασική ιδέα είναι να συνδέσετε το σύστημα προειδοποιήσεων του Aspose.Words. Όταν η βιβλιοθήκη δεν μπορεί να βρει τη ζητούμενη γραμματοσειρά, εκδίδει μια προειδοποίηση `WarningType.FontSubstitution`. Παρέχοντας μια προσαρμοσμένη υλοποίηση του `IWarningCallback`, μπορείτε **να εντοπίσετε γραμματοσειρές** που αντικαταστάθηκαν κατά τη διαδικασία φόρτωσης.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a collector that implements IWarningCallback
public class FontWarningCollector : IWarningCallback
{
    public List<WarningInfo> Warnings { get; } = new();

    public void Warning(WarningInfo info)
    {
        // Store every warning – we’ll filter later
        Warnings.Add(info);
    }
}
```

> **Γιατί λειτουργεί:** Το Aspose.Words καλεί τη μέθοδο `Warning` για κάθε μη‑κριτική κατάσταση. Αποθηκεύοντας τα αντικείμενα `WarningInfo` έχετε πλήρη πρόσβαση στον τύπο, το μήνυμα και το πλαίσιο, κάτι που είναι ακριβώς αυτό που χρειάζεστε για να **εντοπίσετε γραμματοσειρές** που αντικαταστάθηκαν.

---

## Πώς να Καταγράψετε Προειδοποιήσεις Κατά τη Φόρτωση ενός Εγγράφου

Τώρα που έχουμε έναν συλλέκτη, πρέπει να πούμε στο `LoadOptions` να τον χρησιμοποιήσει. Αυτό είναι το τμήμα **πώς να καταγράψετε προειδοποιήσεις** του γρίφου.

```csharp
// 2️⃣ Prepare LoadOptions with our warning collector
var warningCollector = new FontWarningCollector();
var loadOptions = new LoadOptions
{
    // Assign the callback – this is where warnings are captured
    WarningCallback = warningCollector
};

// 3️⃣ Load the document (replace the path with your own file)
Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFont.docx", loadOptions);
```

> **Ακραία περίπτωση:** Αν φορτώνετε ένα έγγραφο από ροή (`new Document(stream, loadOptions)`), η ίδια callback λειτουργεί—απλώς περάστε τη ροή αντί για διαδρομή αρχείου.

Σε αυτό το σημείο το έγγραφο είναι πλήρως φορτωμένο, αλλά οι προειδοποιήσεις αντικατάστασης γραμματοσειρών αποθηκεύονται με ασφάλεια μέσα στο `warningCollector.Warnings`.

---

## Πώς να Απαριθμήσετε Προειδοποιήσεις και να Αναφέρετε τις Αντικαταστάσεις Γραμματοσειρών

Τέλος, φιλτράρουμε τις συλλεγμένες προειδοποιήσεις και **απαριθμούμε προειδοποιήσεις** που αφορούν ειδικά την αντικατάσταση γραμματοσειρών. Αυτό το βήμα μετατρέπει τα ακατέργαστα δεδομένα σε μια αναγνώσιμη αναφορά.

```csharp
// 4️⃣ Iterate over the collected warnings
foreach (var warning in warningCollector.Warnings)
{
    // We're only interested in font substitution warnings
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Substituted font: {warning.Message}");
    }
}
```

**Αναμενόμενο αποτέλεσμα** (παράδειγμα):

```
Substituted font: Font 'Calibri' not found. Substituted with 'Arial'.
Substituted font: Font 'MyCustomFont' not found. Substituted with 'Times New Roman'.
```

Αν το έγγραφο δεν περιέχει ελλιπείς γραμματοσειρές, η επανάληψη δεν παράγει έξοδο—δεν υπάρχει κάτι για ανησυχία.

---

## Πλήρες Παράδειγμα Λειτουργίας (Όλα τα Βήματα σε Ένα Αρχείο)

Παρακάτω βρίσκεται το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε‑και‑επικολλήσετε σε ένα έργο κονσόλας. Συνδέει **πώς να εντοπίσετε γραμματοσειρές**, **πώς να καταγράψετε προειδοποιήσεις**, **πώς να ρυθμίσετε μια callback**, και **πώς να απαριθμήσετε προειδοποιήσεις** σε μια ενιαία, συνεκτική ροή.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontDetectionDemo
{
    // Custom warning collector (captures all warnings)
    public class FontWarningCollector : IWarningCallback
    {
        public List<WarningInfo> Warnings { get; } = new();

        public void Warning(WarningInfo info)
        {
            Warnings.Add(info);
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // -------------------------------------------------
            // Step 1: Set up the warning collector (how to configure callback)
            var collector = new FontWarningCollector();
            var loadOptions = new LoadOptions
            {
                WarningCallback = collector
            };

            // -------------------------------------------------
            // Step 2: Load the document (how to detect fonts)
            string filePath = "YOUR_DIRECTORY/DocumentWithMissingFont.docx";
            Document doc;
            try
            {
                doc = new Document(filePath, loadOptions);
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Failed to load document: {ex.Message}");
                return;
            }

            // -------------------------------------------------
            // Step 3: Enumerate warnings (how to enumerate warnings)
            bool anySubstitutions = false;
            foreach (var warning in collector.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    anySubstitutions = true;
                    Console.WriteLine($"Substituted font: {warning.Message}");
                }
            }

            if (!anySubstitutions)
            {
                Console.WriteLine("No font substitutions detected – all fonts are available.");
            }

            // Optional: Continue processing the document...
        }
    }
}
```

**Εκτελώντας αυτό το πρόγραμμα** θα εκτυπώσει κάθε γραμματοσειρά που το Aspose.Words έπρεπε να αντικαταστήσει. Μπορείτε να ανακατευθύνετε την έξοδο σε αρχείο καταγραφής, να ενεργοποιήσετε μια ειδοποίηση ή ακόμη να ακυρώσετε τη φόρτωση αν λείπει μια κρίσιμη γραμματοσειρά.

---

## Συχνές Ερωτήσεις & Παγίδες

### Τι γίνεται αν χρειαστεί να σταματήσετε τη φόρτωση όταν λείπει μια απαιτούμενη γραμματοσειρά;
Μπορείτε να ελέγξετε τα αντικείμενα `WarningInfo` μέσα στη callback και να ρίξετε μια εξαίρεση όταν εμφανιστεί ένα συγκεκριμένο όνομα γραμματοσειράς. Η εξαίρεση θα ακυρώσει τη φόρτωση, δίνοντάς σας πλήρη έλεγχο.

```csharp
public void Warning(WarningInfo info)
{
    if (info.Type == WarningType.FontSubstitution &&
        info.Message.Contains("MyCriticalFont"))
    {
        throw new InvalidOperationException("Critical font missing – aborting load.");
    }
    Warnings.Add(info);
}
```

### Λειτουργεί αυτό με PDF ή άλλες μορφές;
Ναι. Το Aspose.Words χρησιμοποιεί την ίδια υποδομή προειδοποιήσεων για PDF, RTF και HTML. Απλώς αλλάξτε την επέκταση του αρχείου και ο υπόλοιπος κώδικας παραμένει αμετάβλητος.

### Πώς μπορώ να καταγράψω τις προειδοποιήσεις σε αρχείο αντί για την κονσόλα;
Αντικαταστήστε το `Console.WriteLine` με οποιοδήποτε πλαίσιο καταγραφής προτιμάτε (`Serilog`, `NLog`, κ.λπ.). Η κλάση `WarningInfo` εκθέτει τα πεδία `Message`, `Source` και `Exception` για λεπτομερείς καταγραφές.

### Θα επηρεάσει αυτό την απόδοση;
Το πρόσθετο κόστος είναι αμελητέο—το Aspose.Words ήδη δημιουργεί τις προειδοποιήσεις εσωτερικά. Η προσθήκη μιας callback απλώς αποθηκεύει τις προειδοποιήσεις σε μια λίστα, που είναι O(n) ως προς τον αριθμό των προειδοποιήσεων. Για τυπικά έγγραφα, η επίπτωση είναι πολύ κάτω από 1 % του συνολικού χρόνου φόρτωσης.

---

## Οπτική Σύνοψη

![Πώς να Εντοπίσετε Γραμματοσειρές στο Aspose.Words – διάγραμμα ροής προειδοποιήσεων](https://example.com/images/font-detection-diagram.png "πώς να εντοπίσετε γραμματοσειρές")

*Κείμενο alt:* **πώς να εντοπίσετε γραμματοσειρές** – διάγραμμα που δείχνει το callback προειδοποίησης, τη συλλογή και τα βήματα απαρίθμησης.

---

## Συμπεράσματα

Καλύψαμε **πώς να εντοπίσετε γραμματοσειρές** στο Aspose.Words μέσω **καταγραφής προειδοποιήσεων**, **ρύθμισης μιας callback**, και **απαρίθμησης προειδοποιήσεων**. Το πλήρες δείγμα κώδικα παρουσιάζει ένα πρότυπο έτοιμο για παραγωγή που μπορείτε να ενσωματώσετε σε οποιαδήποτε εφαρμογή .NET.

Στη συνέχεια, ίσως θελήσετε να εξερευνήσετε:

- **Πώς να καταγράψετε προειδοποιήσεις** για άλλα ζητήματα (π.χ., προβλήματα μετατροπής εικόνων)
- **Πώς να ρυθμίσετε μια callback** για προσαρμοσμένα πλαίσια καταγραφής
- **Πώς να απαριθμήσετε προειδοποιήσεις** σε πολλαπλά έγγραφα σε μια παρτίδα εργασίας
- Χρήση του **Aspose.Words.Fonts.FontSettings** για παροχή φακέλων εφεδρικών γραμματοσειρών, κάτι που μπορεί να μειώσει τον αριθμό των αντικαταστάσεων από την αρχή.

Δοκιμάστε το, προσαρμόστε τον συλλέκτη ώστε να ταιριάζει στο στυλ καταγραφής σας, και δεν θα εκπλαγείτε ξανά από μια απρόσμενη αντικατάσταση γραμματοσειράς. Αν συναντήσετε οποιεσδήποτε ιδιαιτερότητες, αφήστε ένα σχόλιο παρακάτω—καλή κωδικοποίηση!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}