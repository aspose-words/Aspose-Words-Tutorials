---
category: general
date: 2026-03-22
description: Αποθήκευση εγγράφου Word και ανίχνευση ελλιπών γραμματοσειρών χρησιμοποιώντας
  το Aspose.Words. Μάθετε πώς να παρακολουθείτε τις ελλιπείς γραμματοσειρές και να
  καταγράφετε σφάλματα γραμματοσειρών σε C#.
draft: false
keywords:
- save word document
- detect missing fonts
- track missing fonts
- capture font errors
language: el
og_description: Αποθήκευση εγγράφου Word και ανίχνευση ελλειπόντων γραμματοσειρών
  σε C#. Αυτός ο οδηγός δείχνει πώς να εντοπίζετε ελλειπείς γραμματοσειρές και να
  καταγράφετε σφάλματα γραμματοσειρών μέσω μιας κλήσης προειδοποίησης.
og_title: Αποθήκευση εγγράφου Word – Εντοπισμός ελλιπών γραμματοσειρών με το Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: Αποθήκευση εγγράφου Word – Ανίχνευση ελλιπών γραμματοσειρών με το Aspose.Words
url: /el/net/working-with-fonts/save-word-document-detect-missing-fonts-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Αποθήκευση Εγγράφου Word – Ανίχνευση Ελλειπουσών Γραμματοσειρών με Aspose.Words

Έχετε χρειαστεί ποτέ να **αποθηκεύσετε ένα έγγραφο word** αλλά δεν ήσασταν σίγουροι αν κάποιες από τις γραμματοσειρές μέσα θα διατηρηθούν μετά το round‑trip; Συμβαίνει πιο συχνά απ' ό,τι νομίζετε, ειδικά όταν τα έγγραφα μετακινούνται μεταξύ μηχανών με διαφορετικές βιβλιοθήκες γραμματοσειρών. Τα καλά νέα; Το Aspose.Words σας παρέχει έναν ενσωματωμένο τρόπο για **ανίχνευση ελλειπουσών γραμματοσειρών** ενώ **αποθηκεύετε το έγγραφο word**, ώστε να μπορείτε να καταγράψετε, να προειδοποιήσετε ή ακόμη και να τις αντικαταστήσετε πριν το αρχείο φτάσει στην οθόνη του χρήστη.

Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα από ένα πλήρες, έτοιμο‑για‑εκτέλεση παράδειγμα που όχι μόνο αποθηκεύει ένα έγγραφο Word αλλά επίσης **εντοπίζει ελλειπούσες γραμματοσειρές** και **καταγράφει σφάλματα γραμματοσειρών** χρησιμοποιώντας έναν προσαρμοσμένο χειριστή προειδοποιήσεων. Στο τέλος θα γνωρίζετε ακριβώς γιατί είναι σημαντική η κλήση του callback, πώς να το συνδέσετε και πώς φαίνεται η έξοδος της κονσόλας όταν γίνεται αντικατάσταση. Χωρίς περιττά περιττά—απλώς ο κώδικας που μπορείτε να ενσωματώσετε σε ένα .NET project αμέσως.

> **Απαιτήσεις**  
> • .NET 6 (ή οποιοδήποτε πρόσφατο .NET Framework) εγκατεστημένο  
> • Visual Studio 2022 ή το αγαπημένο σας IDE  
> • Ένα αδειοδοτημένο αντίγραφο του **Aspose.Words for .NET** (η δωρεάν δοκιμή λειτουργεί για δοκιμές)  

Αν έχετε όλα αυτά, ας ξεκινήσουμε.

---

## Αποθήκευση Εγγράφου Word και Ανίχνευση Ελλειπουσών Γραμματοσειρών

Η βασική ιδέα είναι απλή: πριν καλέσετε `Document.Save`, ορίστε ένα αντικείμενο που υλοποιεί το `IWarningCallback` στο `Document.WarningCallback`. Το Aspose.Words θα καλέσει αυτό το αντικείμενο για κάθε προειδοποίηση που συναντά, συμπεριλαμβανομένων των προειδοποιήσεων **αντικατάστασης γραμματοσειράς** που εμφανίζονται όταν το πηγαίο έγγραφο αναφέρει μια γραμματοσειρά που το σύστημά σας δεν μπορεί να βρει.

```csharp
using Aspose.Words;
using Aspose.Words.Warning;

// Step 1: Create a warning handler that prints font substitution messages
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Only react to font‑substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

// Step 2: Load a document that may contain missing fonts
Document document = new Document("YOUR_DIRECTORY/input.docx");

// Step 3: Register the warning handler with the document
document.WarningCallback = new FontWarningHandler();

// Step 4: Save the document; any font substitution warnings will be output to the console
document.Save("YOUR_DIRECTORY/output.docx");
```

**Τι θα δείτε:**  
Αν το `input.docx` αναφέρει μια γραμματοσειρά που δεν είναι εγκατεστημένη, η κονσόλα εκτυπώνει κάτι σαν:

```
Font substitution: Font "Comic Sans MS" was substituted with "Arial".
```

Αυτή η γραμμή σας λέει ακριβώς ποια γραμματοσειρά λείπει και τι χρησιμοποίησε το Aspose.Words αντί της—τέλεια για **καταγραφή σφαλμάτων γραμματοσειρών** πριν διανείμετε το αρχείο.

---

## Καταγραφή Ελλειπουσών Γραμματοσειρών με Callback Προειδοποίησης (Βήμα‑Βήμα)

### 1️⃣ Εγκατάσταση Aspose.Words

Ανοίξτε το NuGet console του project σας και τρέξτε:

```bash
dotnet add package Aspose.Words
```

Αυτό θα κατεβάσει την πιο πρόσφατη σταθερή έκδοση (προς το παρόν 24.10). Η ενημέρωση της βιβλιοθήκης διασφαλίζει ότι έχετε τις πιο νέες δυνατότητες **ανίχνευσης ελλειπουσών γραμματοσειρών** και διορθώσεις σφαλμάτων.

### 2️⃣ Ορισμός του Χειριστή Προειδοποιήσεων

Γιατί χρειάζεται ξεχωριστή κλάση; Η υλοποίηση του `IWarningCallback` σας επιτρέπει να συγκεντρώσετε όλη τη λογική προειδοποιήσεων σε ένα σημείο. Μπορείτε επίσης να καταγράψετε σε αρχείο, να στείλετε τηλεμετρία ή να πετάξετε εξαίρεση αν μια ελλειπούσα γραμματοσειρά αποτελεί σκληρό σφάλμα για τη ροή εργασίας σας.

```csharp
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only the warnings we care about
        if (info.Type == WarningType.FontSubstitution)
        {
            // Here we simply write to the console,
            // but you could replace this with any logging framework.
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}
```

> **Pro tip:** Αν χρειάζεται να **καταγράψετε ελλειπούσες γραμματοσειρές** σε πολλά έγγραφα, αποθηκεύστε τα μηνύματα σε ένα `List<string>` μέσα στον χειριστή και εκθέστε το αργότερα για αναφορές.

### 3️⃣ Φόρτωση Πηγαίου Εγγράφου

Ο κατασκευαστής `Document` μπορεί να δεχτεί διαδρομή αρχείου, ροή ή ακόμη και ακατέργαστα bytes. Στις περισσότερες περιπτώσεις θα το δείξετε σε ένα `.docx` που λάβατε από χρήστη ή άλλο σύστημα.

```csharp
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Αν το αρχείο είναι μεγάλο, σκεφτείτε να χρησιμοποιήσετε `LoadOptions` για ενεργοποίηση lazy loading, που μειώνει την πίεση μνήμης.

### 4️⃣ Σύνδεση του Callback

Αναθέστε την παρουσία στο `doc.WarningCallback`. Από αυτό το σημείο και έπειτα, κάθε προειδοποίηση (συμπεριλαμβανομένων των αντικαταστάσεων γραμματοσειράς) θα περάσει από τον χειριστή σας.

```csharp
doc.WarningCallback = new FontWarningHandler();
```

### 5️⃣ Αποθήκευση του Εγγράφου

Τώρα μπορείτε με ασφάλεια να καλέσετε `Save`. Ο χειριστής προειδοποιήσεων εκτελείται **συγχρονισμένα** κατά τη διάρκεια της αποθήκευσης, οπότε θα δείτε την έξοδο αμέσως.

```csharp
doc.Save("YOUR_DIRECTORY/output.docx");
```

Αν προτιμάτε να αποθηκεύσετε σε διαφορετική μορφή (PDF, HTML, κ.λπ.), ο ίδιος μηχανισμός προειδοποιήσεων λειτουργεί—το Aspose.Words θα αναφέρει ακόμα ελλειπούσες γραμματοσειρές πριν τη μετατροπή.

---

## Καταγραφή Σφαλμάτων Γραμματοσειρών – Συνηθισμένες Ακραίες Περιπτώσεις

Αν και η βασική ροή καλύπτει τις περισσότερες καταστάσεις, τα πραγματικά έργα συχνά αντιμετωπίζουν μερικά εμπόδια. Παρακάτω είναι μερικές παραλλαγές που μπορεί να συναντήσετε και πώς να τις διαχειριστείτε.

### Ελλειπούσα Γραμματοσειρά σε Κεφαλίδα/Υποσέλιδο

Οι κεφαλίδες και τα υποσέλιδα είναι ξεχωριστοί κόμβοι, αλλά το σύστημα προειδοποιήσεων τα αντιμετωπίζει όπως το κυρίως κείμενο. Δεν χρειάζεται επιπλέον κώδικας· το callback θα ενεργοποιηθεί και για αυτές τις γραμματοσειρές. Απλώς βεβαιωθείτε ότι φορτώνετε ολόκληρο το έγγραφο (η προεπιλογή το κάνει).

### Πολλαπλές Αντικαταστάσεις σε Ένα Έγγραφο

Αν ένα έγγραφο χρησιμοποιεί πολλές άγνωστες γραμματοσειρές, ο χειριστής θα κληθεί μία φορά για κάθε αντικατάσταση. Για να αποφύγετε την υπερφόρτωση της κονσόλας, μπορείτε να αφαιρέσετε διπλότυπα μηνύματα:

```csharp
class FontWarningHandler : IWarningCallback
{
    private readonly HashSet<string> _seen = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution && _seen.Add(info.Description))
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}
```

### Μετατροπή Προειδοποιήσεων σε Εξαιρέσεις

Μερικές φορές μια ελλειπούσα γραμματοσειρά είναι αδιαπραγμάτευτη. Ρίξτε μια εξαίρεση μέσα στον χειριστή για να ακυρώσετε την αποθήκευση:

```csharp
if (info.Type == WarningType.FontSubstitution)
{
    throw new InvalidOperationException($"Missing font detected: {info.Description}");
}
```

Θυμηθείτε να τυλίξετε το `doc.Save` σε `try/catch` ώστε να διαχειριστείτε την εξαίρεση με χάρη.

---

## Επαλήθευση του Αποτελέσματος – Τι να Περιμένετε

Μετά την ολοκλήρωση της αποθήκευσης, ανοίξτε το `output.docx` στο Microsoft Word (ή σε οποιονδήποτε συμβατό προβολέα). Θα πρέπει να δείτε την ίδια οπτική διάταξη με το αρχικό, αλλά οι αντικατεστημένες γραμματοσειρές θα εμφανίζονται ως η εναλλακτική που παρατηρήσατε στην κονσόλα. Για διπλό έλεγχο, μπορείτε:

1. Ανοίξτε **File → Options → Advanced → Show document content → Use draft quality** – αυτό αναγκάζει το Word να αποκαλύψει τυχόν κρυφές αντικαταστάσεις γραμματοσειρών.  
2. Χρησιμοποιήστε το διάλογο **Replace Fonts** του Word (`Ctrl+Shift+F`) για να δείτε ποιες γραμματοσειρές είναι πραγματικά ενσωματωμένες.

Αν όλα ταιριάζουν, έχετε αποθηκεύσει επιτυχώς το **word document** ενώ **ανιχνεύσατε ελλειπούσες γραμματοσειρές** και **καταγράψατε σφάλματα γραμματοσειρών**. 🎉

---

## Πλήρες Παράδειγμα Εργασίας (Έτοιμο για Αντιγραφή‑Επικόλληση)

Παρακάτω είναι ολόκληρο το πρόγραμμα που μπορείτε να ενσωματώσετε σε ένα νέο Console App project. Απλώς αντικαταστήστε το `YOUR_DIRECTORY` με μια πραγματική διαδρομή φακέλου στο μηχάνημά σας.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Warning;

namespace FontWarningDemo
{
    // Step 1: Create a warning handler that prints font substitution messages
    class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            // Only handle font‑substitution warnings
            if (info.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Font substitution: {info.Description}");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // Step 2: Load a document that may contain missing fonts
            Document document = new Document("YOUR_DIRECTORY/input.docx");

            // Step 3: Register the warning handler with the document
            document.WarningCallback = new FontWarningHandler();

            // Step 4: Save the document; any font substitution warnings will be output to the console
            document.Save("YOUR_DIRECTORY/output.docx");

            Console.WriteLine("Document saved successfully.");
        }
    }
}
```

**Αναμενόμενη έξοδος κονσόλας** (παράδειγμα):

```
Font substitution: Font "Times New Roman" was substituted with "Arial".
Document saved successfully.
```

Αυτή είναι η πλήρης ιστορία—χωρίς κρυφά βήματα, χωρίς εξωτερικά έγγραφα που πρέπει να κυνηγήσετε.

---

## Συμπέρασμα

Σας δείξαμε πώς να **αποθηκεύσετε ένα word document** ενώ ενεργά **ανιχνεύετε ελλειπούσες γραμματοσειρές**, **καταγράφετε ελλειπούσες γραμματοσειρές**, και **συλλαμβάνετε σφάλματα γραμματοσειρών** χρησιμοποιώντας το callback προειδοποιήσεων του Aspose.Words. Συνδέοντας μια μικρή υλοποίηση `IWarningCallback`, αποκτάτε πλήρη διαφάνεια στις αντικαταστάσεις γραμματοσειρών κατά το χρόνο αποθήκευσης, δίνοντάς σας τη δυνατότητα να καταγράψετε, να αντικαταστήσετε ή να ακυρώσετε όπως χρειάζεται.  

Έτοιμοι για την επόμενη πρόκληση; Δοκιμάστε να επεκτείνετε τον χειριστή ώστε να γράφει προειδοποιήσεις σε δομημένο JSON log, ή συνδυάστε το με το Aspose.PDF για να μετατρέψετε το ίδιο έγγραφο διατηρώντας τις πληροφορίες γραμματοσειρών. Μπορείτε επίσης να εξερευνήσετε την ενσωμάτωση των ελλειπούσων γραμματοσειρών απευθείας στο αρχείο εξόδου—το Aspose.Words υποστηρίζει ενσωμάτωση γραμματοσειρών μέσω `LoadOptions.FontSettings`.  

Δοκιμάστε το, προσαρμόστε τον κώδικα στη δική σας αλυσίδα επεξεργασίας, και πείτε μας πώς σας φάνηκε. Καλό coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}