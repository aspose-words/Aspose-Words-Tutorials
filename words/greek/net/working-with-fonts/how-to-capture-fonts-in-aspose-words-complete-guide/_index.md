---
category: general
date: 2026-01-05
description: Πώς να καταγράψετε γρήγορα τις γραμματοσειρές και να διαχειριστείτε τις
  ελλιπείς γραμματοσειρές χρησιμοποιώντας το Aspose.Words. Μάθετε μια βήμα‑βήμα λύση
  με πλήρη κώδικα C#.
draft: false
keywords:
- how to capture fonts
- handle missing fonts
- Aspose.Words warnings
- font substitution callback
- missing font detection
language: el
og_description: Πώς να καταγράψετε τις γραμματοσειρές στο Aspose.Words και να αντιμετωπίσετε
  τις ελλιπείς γραμματοσειρές. Ακολουθήστε αυτόν τον λεπτομερή οδηγό για μια αξιόπιστη
  υλοποίηση σε C#.
og_title: Πώς να καταγράψετε τις γραμματοσειρές στο Aspose.Words – Πλήρης οδηγός
tags:
- Aspose.Words
- C#
- Document Processing
title: Πώς να καταγράψετε γραμματοσειρές στο Aspose.Words – Πλήρης οδηγός
url: /el/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Καταγράψετε τις Γραμματοσειρές στο Aspose.Words – Πλήρης Οδηγός

Έχετε αναρωτηθεί ποτέ **πώς να καταγράψετε τις γραμματοσειρές** όταν φορτώνετε ένα έγγραφο Word με το Aspose.Words; Δεν είστε οι μόνοι. Η έλλειψη γραμματοσειρών μπορεί να προκαλέσει λεπτές διαταραχές στη διάταξη, και χωρίς κατάλληλη προειδοποίηση μπορεί να μην το παρατηρήσετε μέχρι το τελικό PDF να φαίνεται λανθασμένο. Σε αυτό το tutorial θα σας δείξουμε ακριβώς πώς να **καταγράψετε τις γραμματοσειρές** **και** να διαχειριστείτε τις ελλιπείς γραμματοσειρές ώστε το αποτέλεσμα να παραμένει pixel‑perfect.

Θα περάσουμε από ένα πραγματικό σενάριο, θα ρυθμίσουμε ένα warning callback, και θα σας δώσουμε ένα έτοιμο παράδειγμα C# που μπορείτε να τρέξετε αμέσως. Στο τέλος θα γνωρίζετε γιατί είναι σημαντικό, πώς να το υλοποιήσετε, και τι πρέπει να προσέξετε όταν οι γραμματοσειρές εξαφανίζονται από το περιβάλλον σας.

## Τι Θα Μάθετε

- Πώς να διαμορφώσετε το **LoadOptions** ώστε να ακούει προειδοποιήσεις σχετικές με γραμματοσειρές.  
- Τον ρόλο του **IWarningCallback** και του **WarningInfo** στο Aspose.Words.  
- Πρακτικές συμβουλές για την αντιμετώπιση και την καταγραφή ελλιπών γραμματοσειρών.  
- Ένα πλήρες, αυτόνομο δείγμα κώδικα που μπορείτε να επικολλήσετε στο Visual Studio και να τρέξετε αμέσως.

**Προαπαιτούμενα:** .NET 6+ (ή .NET Framework 4.7.2+), Aspose.Words for .NET εγκατεστημένο μέσω NuGet, και βασική εξοικείωση με C#. Δεν απαιτούνται άλλες βιβλιοθήκες.

---

## Βήμα 1: Ρύθμιση Load Options για Καταγραφή Γραμματοσειρών

Το πρώτο που χρειάζεται είναι μια παρουσία του **LoadOptions**. Αυτό το αντικείμενο λέει στο Aspose.Words πώς να συμπεριφέρεται κατά την ανάγνωση ενός εγγράφου. Αναθέτοντας ένα προσαρμοσμένο **IWarningCallback** μπορούμε να παρεμβάλουμε σε οποιεσδήποτε προειδοποιήσεις αντικατάστασης γραμματοσειρών που εμφανίζονται κατά τη διαδικασία φόρτωσης.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Loading;

// Prepare load options and attach a warning callback
LoadOptions loadOptions = new LoadOptions
{
    // The callback will be invoked for every warning Aspose.Words raises
    WarningCallback = new FontWarningCollector()
};
```

**Γιατί είναι σημαντικό:**  
Το Aspose.Words αντικαθιστά σιωπηλά τις ελλιπείς γραμματοσειρές με μια προεπιλεγμένη, εκτός αν του ζητήσετε να σας το αναφέρει. Συνδέοντας ένα callback **καταγράψετε** τις πληροφορίες των γραμματοσειρών ακριβώς τη στιγμή της φόρτωσης, δίνοντάς σας την ευκαιρία να τις καταγράψετε, να τις αντικαταστήσετε ή ακόμη και να διακόψετε τη λειτουργία.

> **Pro tip:** Κρατήστε το `loadOptions` ως μεταβλητή που μπορεί να επαναχρησιμοποιηθεί αν επεξεργάζεστε πολλά έγγραφα σε batch. Αποφεύγει τη δημιουργία του ίδιου callback ξανά και ξανά.

---

## Βήμα 2: Φόρτωση του Εγγράφου με τις Διαμορφωμένες Επιλογές

Τώρα που το callback είναι σε θέση, φορτώνουμε το έγγραφο. Ο κατασκευαστής **Document** δέχεται τη διαδρομή και το **LoadOptions** που μόλις διαμορφώσαμε.

```csharp
// Replace with the actual path to your .docx file
string inputPath = @"C:\Docs\input.docx";

Document doc = new Document(inputPath, loadOptions);
```

Αν λείπει κάποια γραμματοσειρά, το Aspose.Words θα εκδώσει μια προειδοποίηση που θα λάβει ο `FontWarningCollector`. Το ίδιο το έγγραφο θα φορτωθεί, αλλά θα έχετε ένα σαφές αρχείο των γραμματοσειρών που αντικαταστάθηκαν.

---

## Βήμα 3: Υλοποίηση του FontWarningCollector – Διαχείριση Ελλιπών Γραμματοσειρών

Η καρδιά του **πώς να καταγράψετε τις γραμματοσειρές** βρίσκεται στην κλάση `FontWarningCollector`. Αυτή υλοποιεί το `IWarningCallback` και φιλτράρει μόνο τα γεγονότα `WarningType.FontSubstitution`.

```csharp
// Helper class that receives warning callbacks from Aspose.Words
class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We care exclusively about font substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            // Log the warning – you could also write to a file or database
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**Επεξήγηση:**  
- Το `info.Type` μας λέει την κατηγορία της προειδοποίησης. Ελέγχοντας για `FontSubstitution` **διαχειριζόμαστε τις ελλιπείς γραμματοσειρές** χωρίς να γεμίζουμε το output με άσχετα μηνύματα (π.χ. παρωχημένες λειτουργίες).  
- Το `info.Description` περιέχει ένα ανθρώπινα αναγνώσιμο μήνυμα όπως “Font 'Comic Sans MS' was substituted with 'Arial'.” Αυτό είναι ακριβώς το δεδομένο που χρειάζεστε για να ελέγξετε το απόθεμα γραμματοσειρών σας.

> **Προσοχή:** Αν χρειάζεται να διακόψετε την επεξεργασία όταν λείπει μια κρίσιμη γραμματοσειρά, ρίξτε μια εξαίρεση μέσα στο `if` αντί να τυπώσετε απλώς το μήνυμα.

---

## Βήμα 4: Επαλήθευση του Αποτελέσματος – Τι Να Περιμένετε

Τρέξτε το πρόγραμμα από τη γραμμή εντολών ή το IDE σας. Για κάθε ελλιπή γραμματοσειρά, θα δείτε μια γραμμή όπως:

```
Font substitution detected: Font 'Times New Roman' was substituted with 'Arial'.
```

Αν όλες οι γραμματοσειρές είναι παρούσες, το callback παραμένει σιωπηλό και το έγγραφο φορτώνεται χωρίς προβλήματα. Μπορείτε τώρα να προχωρήσετε με την αποθήκευση, τη μετατροπή ή την εκτύπωση του εγγράφου, σίγουροι ότι **καταγράψατε** τις πληροφορίες των γραμματοσειρών.

---

## Βήμα 5: Πλήρες Παράδειγμα Εργασίας (Όλα τα Τμήματα Μαζί)

Παρακάτω βρίσκεται το πλήρες πρόγραμμα, έτοιμο για αντιγραφή‑και‑επικόλληση. Περιλαμβάνει τις οδηγίες `using`, την υλοποίηση του callback, και μια μικρή επίδειξη αποθήκευσης του φορτωμένου εγγράφου ως PDF.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Loading;

namespace FontCaptureDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Configure load options with our warning collector
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // 2️⃣ Path to the source DOCX (adjust as needed)
            string inputPath = @"C:\Docs\input.docx";

            // 3️⃣ Load the document – any missing fonts trigger our callback
            Document doc = new Document(inputPath, loadOptions);

            // 4️⃣ Optional: Save as PDF to see the final result
            string outputPdf = @"C:\Docs\output.pdf";
            doc.Save(outputPdf);

            Console.WriteLine("Document processed successfully.");
        }
    }

    // 5️⃣ Our custom warning collector – handles missing fonts
    class FontWarningCollector : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                // You could log to a file, raise an event, or collect into a list
                Console.WriteLine($"Font substitution detected: {info.Description}");
            }
        }
    }
}
```

**Εκτέλεση του κώδικα:**  
1. Δημιουργήστε ένα νέο έργο console (`dotnet new console -n FontCaptureDemo`).  
2. Προσθέστε το πακέτο Aspose.Words (`dotnet add package Aspose.Words`).  
3. Αντικαταστήστε το παραγόμενο `Program.cs` με το παραπάνω απόσπασμα.  
4. Τοποθετήστε ένα DOCX που αναφέρεται σκόπιμα σε μια γραμματοσειρά που δεν έχετε (π.χ. “Papyrus”).  
5. Εκτελέστε (`dotnet run`). Παρακολουθήστε την κονσόλα για μηνύματα αντικατάστασης, έπειτα ανοίξτε το `output.pdf` για να επαληθεύσετε τη διάταξη.

---

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

### Τι κάνω αν χρειάζομαι τη λίστα των ελλιπών γραμματοσειρών αργότερα;

Αποθηκεύστε τα μηνύματα σε ένα `List<string>` μέσα στο `FontWarningCollector` και εκθέστε το μέσω μιας ιδιότητας. Έτσι μπορείτε να γράψετε τη λίστα σε αρχείο καταγραφής μετά την επεξεργασία πολλών εγγράφων.

### Λειτουργεί αυτό με κρυπτογραφημένα ή προστατευμένα με κωδικό αρχεία;

Ναι, αλλά πρέπει επίσης να παρέχετε τον κωδικό μέσω `LoadOptions.Password`. Το warning callback λειτουργεί με τον ίδιο τρόπο μόλις το έγγραφο αποκρυπτογραφηθεί.

### Μπορώ να αντικαταστήσω μια ελλιπή γραμματοσειρά με μια προσαρμοσμένη εναλλακτική;

Απόλυτα. Μέσα στη μέθοδο `Warning` μπορείτε να καλέσετε `doc.FontSettings.SubstitutionSettings.FontSubstitutes.AddMissing("MissingFont", "MyFallback")`. Αυτό εξασφαλίζει ότι η αντικατάσταση είναι προβλέψιμη.

### Θα επηρεάσει αυτό την απόδοση;

Το κόστος είναι ελάχιστο—βασικά μια κλήση μεθόδου ανά προειδοποίηση. Σε batch χιλιάδων εγγράφων η επίπτωση είναι αμελητέα σε σχέση με το κόστος I/O του φορτώματος κάθε αρχείου.

---

## Συμπέρασμα

Καλύψαμε **πώς να καταγράψετε τις γραμματοσειρές** στο Aspose.Words, σας δείξαμε πώς να **διαχειριστείτε τις ελλιπείς γραμματοσειρές** με ένα καθαρό warning callback, και σας παραδώσαμε ένα πλήρες, εκτελέσιμο παράδειγμα. Ενσωματώνοντας αυτό το μοτίβο στη ροή επεξεργασίας εγγράφων σας, δεν θα ξαφνιάζεστε ξανά από σιωπηλές αντικαταστάσεις γραμματοσειρών.

Έτοιμοι για το επόμενο βήμα; Δοκιμάστε να επεκτείνετε τον collector ώστε να γράφει logs σε JSON, να ενσωματώνεται σε πίνακα παρακολούθησης, ή να ενσωματώνει αυτόματα τις ελλιπείς γραμματοσειρές στο τελικό PDF. Οι δυνατότητες είναι ατελείωτες, και τώρα έχετε μια σταθερή βάση.

Καλή προγραμματιστική! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}