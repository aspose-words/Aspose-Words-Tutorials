---
category: general
date: 2026-05-29
description: Μάθετε πώς να καλέσετε το CheckGrammar και να εφαρμόσετε τον AI έλεγχο
  γραμματικής σε έγγραφα Word χρησιμοποιώντας το Aspose.Words. Περιλαμβάνεται παράδειγμα
  βήμα‑βήμα.
draft: false
keywords:
- how to call checkgrammar
- apply ai grammar check
language: el
og_description: Πώς να καλέσετε το CheckGrammar και να εφαρμόσετε τον έλεγχο γραμματικής
  AI στα αρχεία Word σας με το Aspose.Words. Πλήρες παράδειγμα κώδικα και εξήγηση.
og_title: Πώς να καλέσετε το CheckGrammar σε C# – Πλήρης Οδηγός
schemas:
- author: Aspose
  dateModified: '2026-05-29'
  description: Learn how to call CheckGrammar and apply AI grammar check to Word documents
    using Aspose.Words. Step‑by‑step example included.
  headline: How to Call CheckGrammar in C# – Complete Guide
  type: TechArticle
- description: Learn how to call CheckGrammar and apply AI grammar check to Word documents
    using Aspose.Words. Step‑by‑step example included.
  name: How to Call CheckGrammar in C# – Complete Guide
  steps:
  - name: What Happens Under the Hood?
    text: 1. **Paragraph Extraction** – Aspose.Words iterates over every paragraph
      in `doc`. 2. **Model Invocation** – Each paragraph’s raw text is passed to `aiModel.Process`.
      3. **Result Integration** – The returned string replaces the original paragraph,
      preserving styles and formatting. 4. **Performance C
  - name: Expected Output
    text: 'Running the program prints something like:'
  - name: Why Use the `CheckGrammar` Method Directly?
    text: '* **Single Responsibility** – The method isolates grammar‑related logic,
      making your code easier to test. * **Future‑Proof** – If Aspose releases a newer
      AI model, the same call works without code changes. * **Performance** – Internally
      it streams text to the model, avoiding loading the whole docume'
  - name: Common Pitfalls & How to Dodge Them
    text: '| Pitfall | Symptoms | Fix | |--------|----------|-----| | Model returns
      `null` | Paragraph disappears | Ensure your `IAiModel` never returns `null`.
      Return the original text on failure. | | Large documents cause memory spikes
      | Out‑of‑memory exception | Process the document in sections (`doc.Sectio'
  type: HowTo
tags:
- Aspose.Words
- C#
- AI
title: Πώς να καλέσετε το CheckGrammar σε C# – Πλήρης Οδηγός
url: /el/net/ai-powered-document-processing/how-to-call-checkgrammar-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να καλέσετε το CheckGrammar σε C# – Πλήρης Οδηγός

Έχετε αναρωτηθεί ποτέ **πώς να καλέσετε το CheckGrammar** από την εφαρμογή .NET σας χωρίς να στέλνετε δεδομένα στο σύννεφο; Δεν είστε μόνοι. Πολλοί προγραμματιστές θέλουν έναν τρόπο με προτεραιότητα την ιδιωτικότητα για τη βελτίωση του στυλ του εγγράφου, και το Aspose.Words το καθιστά δυνατό με τη μηχανή γραμματικής που τροφοδοτείται από AI. Σε αυτό το tutorial θα περάσουμε από ένα πραγματικό παράδειγμα που **εφαρμόζει AI grammar check** σε ένα τοπικό αρχείο `.docx`, διατηρώντας τα δεδομένα σας εντός του περιβάλλοντος. Θα ξεκινήσουμε δείχνοντας τον πλήρη, έτοιμο‑για‑εκτέλεση κώδικα, και στη συνέχεια θα αναλύσουμε κάθε γραμμή ώστε να καταλάβετε **γιατί** είναι σημαντική, όχι μόνο **τι** κάνει. Στο τέλος θα μπορείτε να ενσωματώσετε αυτόν τον κώδικα σε οποιοδήποτε έργο C# και να επωφεληθείτε αμέσως από την επανεγγραφή με τη βοήθεια AI.

---

## Προαπαιτούμενα

* .NET 6+ SDK (ή .NET Framework 4.7.2+ αν προτιμάτε)
* Visual Studio 2022 (ή οποιοδήποτε IDE προτιμάτε)
* Άδεια Aspose.Words for .NET (η δωρεάν δοκιμή λειτουργεί για πειραματισμό)
* Τοπικά φιλοξενούμενο μοντέλο γλώσσας που υλοποιεί το `IAiModel` (μπορεί να είναι ένα μικρό open‑source μοντέλο ή ένας προσαρμοσμένος wrapper)

Καμία εξωτερική υπηρεσία, καμία κλήση στο διαδίκτυο — μόνο καθαρή τοπική επεξεργασία.

## Βήμα 1: Ρύθμιση του Έργου και Προσθήκη του Aspose.Words

Αρχικά, δημιουργήστε ένα νέο έργο console:

```bash
dotnet new console -n AiGrammarDemo
cd AiGrammarDemo
```

Προσθέστε το πακέτο NuGet Aspose.Words:

```bash
dotnet add package Aspose.Words
```

Αν σκοπεύετε να χρησιμοποιήσετε τις AI επεκτάσεις, προσθέστε επίσης:

```bash
dotnet add package Aspose.Words.AI
```

**Συμβουλή:** Κρατήστε τα πακέτα NuGet ενημερωμένα. Από τον Μάιο 2026 η τελευταία σταθερή έκδοση είναι `23.12`.

## Βήμα 2: Υλοποίηση ενός Απλού Τοπικού Wrapper για LLM

Το Aspose.Words αναμένει ένα αντικείμενο που υλοποιεί το `IAiModel`. Παρακάτω υπάρχει ένα ελάχιστο stub που προωθεί κλήσεις σε ένα υποθετικό τοπικό μοντέλο με όνομα `MyLocalLlm`. Αντικαταστήστε το σώμα με όποιο API εκθέτει το μοντέλο σας (π.χ., HTTP, gRPC ή άμεση κλήση βιβλιοθήκης).

```csharp
using Aspose.Words.AI;

public class MyLocalLlm : IAiModel
{
    // This method receives the raw text and should return the revised version.
    public string Process(string input)
    {
        // Placeholder: In a real scenario, you'd call your LLM here.
        // For demonstration, we'll just return the input unchanged.
        // Imagine this is a call to a local transformer model.
        return input;
    }

    // Optional: configure model settings, temperature, etc.
    public void SetOption(string name, object value) { /* ... */ }
}
```

**Γιατί είναι σημαντικό:** Παρέχοντας τη δική σας υλοποίηση του `IAiModel` αποκτάτε πλήρη έλεγχο της κατοικίας των δεδομένων και μπορείτε να **εφαρμόσετε AI grammar check** χωρίς ποτέ να αφήσετε τη μηχανή.

## Βήμα 3: Φόρτωση του Πηγαίου Εγγράφου

Τώρα φέρνουμε το αρχείο Word που θέλουμε να βελτιώσουμε. Το Aspose.Words μπορεί να διαβάσει σχεδόν οποιαδήποτε μορφή Office, αλλά για αυτό το παράδειγμα θα χρησιμοποιήσουμε το `.docx`.

```csharp
using Aspose.Words;

// ...

// Path to the original document (make sure the file exists)
string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document into memory
Document doc = new Document(inputPath);
```

Αν το αρχείο λείπει, το `Document` ρίχνει `FileNotFoundException`. Η περιτύλιξη της φόρτωσης σε try/catch παρέχει ευγενικό χειρισμό σφαλμάτων.

```csharp
try
{
    Document doc = new Document(inputPath);
}
catch (FileNotFoundException ex)
{
    Console.WriteLine($"Could not find the file: {ex.Message}");
    return;
}
```

## Βήμα 4: Πώς να Καλέσετε το CheckGrammar – Η Κεντρική Λειτουργία

Αυτή είναι η καρδιά του tutorial: **πώς να καλέσετε το CheckGrammar** χρησιμοποιώντας το μοντέλο που μόλις συνδέσατε.

```csharp
using Aspose.Words.AI;

// ...

// Create an instance of your locally hosted LLM
IAiModel aiModel = new MyLocalLlm();

// Run the AI‑driven rewrite. This method internally sends each paragraph
// to the IAiModel implementation, receives the revised text, and replaces it.
doc.CheckGrammar(aiModel);
```

### Τι Συμβαίνει Πίσω από τη Σκηνή;

1. **Εξαγωγή Παραγράφων** – Το Aspose.Words διασχίζει κάθε παράγραφο στο `doc`.
2. **Κλήση Μοντέλου** – Το ακατέργαστο κείμενο κάθε παραγράφου περνά στο `aiModel.Process`.
3. **Ενσωμάτωση Αποτελέσματος** – Η επιστρεφόμενη συμβολοσειρά αντικαθιστά την αρχική παράγραφο, διατηρώντας τα στυλ και τη μορφοποίηση.
4. **Παράγοντες Απόδοσης** – Για μεγάλα έγγραφα ίσως θέλετε να ομαδοποιήσετε παραγράφους ή να εκτελέσετε την λειτουργία ασύγχρονα. Το API υποστηρίζει επίσης tokens ακύρωσης.

**Γιατί να χρησιμοποιήσετε το CheckGrammar;**  
Παρέχει ένα ενιαίο σημείο εισόδου μιας γραμμής που αφαιρεί την ανάγκη για tokenization, περιορισμό αιτήσεων και συγχώνευση αποτελεσμάτων. Δεν χρειάζεται να γράψετε βρόχο μόνοι σας — το Aspose το διαχειρίζεται, επιτρέποντάς σας να εστιάσετε στο μοντέλο.

## Βήμα 5: Αποθήκευση του Ανανεωμένου Εγγράφου

Αφού το AI έχει βελτιώσει το κείμενο, γράψτε το αποτέλεσμα πίσω στο δίσκο.

```csharp
// Destination path
string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");

// Persist the changes
doc.Save(outputPath);

// Inform the user
Console.WriteLine($"AI grammar check applied. Saved to {outputPath}");
```

Το αποθηκευμένο αρχείο διατηρεί όλα τα αρχικά στοιχεία διάταξης (πίνακες, εικόνες, κεφαλίδες) ενώ αντικατοπτρίζει τις βελτιώσεις στυλ που έκανε το LLM σας.

## Πλήρες Παράδειγμα Λειτουργίας

Συνδυάζοντας όλα, εδώ είναι ένα έτοιμο‑για‑εκτέλεση πρόγραμμα. Αντιγράψτε‑επικολλήστε στο `Program.cs` και πατήστε **F5**.

```csharp
// Program.cs
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.AI;

public class MyLocalLlm : IAiModel
{
    public string Process(string input)
    {
        // Simulate a rewrite – in practice call your real model here.
        // Example: prepend "Rewritten: " to show change.
        return "Rewritten: " + input;
    }

    public void SetOption(string name, object value) { /* no‑op */ }
}

class Program
{
    static void Main()
    {
        // 1️⃣ Create the AI model instance
        IAiModel aiModel = new MyLocalLlm();

        // 2️⃣ Load the source document
        string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        Document doc;
        try
        {
            doc = new Document(inputPath);
        }
        catch (FileNotFoundException ex)
        {
            Console.WriteLine($"Error: {ex.Message}");
            return;
        }

        // 3️⃣ Apply AI grammar check (how to call CheckGrammar)
        doc.CheckGrammar(aiModel);

        // 4️⃣ Save the result
        string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Successfully applied AI grammar check. Output saved at: {outputPath}");
    }
}
```

### Αναμενόμενη Έξοδος

Η εκτέλεση του προγράμματος εκτυπώνει κάτι όπως:

```
Successfully applied AI grammar check. Output saved at: C:\Path\To\AiGrammarDemo\output.docx
```

Ανοίξτε το `output.docx` και θα παρατηρήσετε ότι κάθε παράγραφος τώρα αρχίζει με “Rewritten: ” — ένα σαφές σημάδι ότι το βήμα **apply AI grammar check** λειτούργησε.

## ## Πώς να Καλέσετε το CheckGrammar στο Aspose.Words – Βαθύτερη Εξέταση

### Γιατί να Χρησιμοποιήσετε τη Μέθοδο `CheckGrammar` Άμεσα;

* **Μοναδική Ευθύνη** – Η μέθοδος απομονώνει τη λογική που σχετίζεται με τη γραμματική, καθιστώντας τον κώδικά σας πιο εύκολο στη δοκιμή.
* **Μελλοντική Ασφάλεια** – Αν το Aspose κυκλοφορήσει ένα νεότερο AI μοντέλο, η ίδια κλήση λειτουργεί χωρίς αλλαγές κώδικα.
* **Απόδοση** – Εσωτερικά στέλνει κείμενο στο μοντέλο σε ροή, αποφεύγοντας τη φόρτωση ολόκληρου του εγγράφου σε μια τεράστια συμβολοσειρά.

### Συνηθισμένα Πιθανά Προβλήματα & Πώς να τα Αποφύγετε

| Πιθανό Πρόβλημα | Συμπτώματα | Διόρθωση |
|------------------|------------|----------|
| Το μοντέλο επιστρέφει `null` | Η παράγραφος εξαφανίζεται | Βεβαιωθείτε ότι το `IAiModel` σας δεν επιστρέφει ποτέ `null`. Επιστρέψτε το αρχικό κείμενο σε περίπτωση αποτυχίας. |
| Μεγάλα έγγραφα προκαλούν αυξήσεις μνήμης | Εξαίρεση Out‑of‑memory | Επεξεργαστείτε το έγγραφο σε ενότητες (`doc.Sections`) ή ενεργοποιήστε τη ροή εάν το μοντέλο σας το υποστηρίζει. |
| Η μορφοποίηση χάνεται μετά την επανεγγραφή | Χαμένα έντονα/πλάγια | Το `CheckGrammar` διατηρεί τη μορφοποίηση `Run`; αντικαθιστά μόνο το περιεχόμενο κειμένου, όχι τα αντικείμενα `Run`. |
| Εκτέλεση σε headless server προκαλεί σφάλματα UI | `System.InvalidOperationException` | Ορίστε τις `CompatibilityOptions` του `Document` για να αποφύγετε εξαρτήσεις UI. |

## ## Εφαρμόστε AI Grammar Check στην Εργασιακή Ροή – Καλές Πρακτικές

1. **Επικύρωση Εισόδου Πρώτα** – Εκτελέστε έναν γρήγορο έλεγχο ορθογραφίας (`doc.CheckSpelling`) πριν καλέσετε το AI. Καθαρή είσοδος δίνει καλύτερα αποτελέσματα AI.
2. **Ομαδοποίηση Κλήσεων** – Αν το LLM σας έχει καθυστέρηση ανά αίτηση 200 ms, ομαδοποιήστε 5–10 παραγράφους σε μία αίτηση για να μειώσετε το συνολικό χρόνο.
3. **Καταγραφή Αλλαγών** – Διατηρήστε ένα στιγμιότυπο πριν/μετά για συμμόρφωση. Το Aspose.Words μπορεί να εξάγει diff μέσω `doc.Compare`.
4. **Ασφαλίστε το**

## Τι Θα Μάθετε Στη Σειρά;

- [Πώς να Χρησιμοποιήσετε LoadOptions στο Aspose.Words – Πλήρης Οδηγός](/words/english/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/)
- [Πώς να Μετατρέψετε Word σε PDF Χρησιμοποιώντας Aspose.Words για Java](/words/english/java/document-converting/using-document-converting/)
- [Πώς να Συγχωνεύσετε Πολλαπλά Αρχεία DOCX Χρησιμοποιώντας Aspose.Words για Java](/words/english/java/document-merging/using-document-merging/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}