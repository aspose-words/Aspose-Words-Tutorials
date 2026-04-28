---
category: general
date: 2026-04-28
description: Συνδέστε το τοπικό LLM από C# και ζητήστε από το μεγάλο μοντέλο γλώσσας
  να φορτώσει έγγραφο Word, καλέστε το τοπικό LLM και ξαναγράψτε το κείμενο αυτόματα.
  Περιλαμβάνεται κώδικας βήμα‑βήμα.
draft: false
keywords:
- connect to local llm
- prompt large language model
- load word document
- call local llm
- rewrite text automatically
language: el
og_description: Συνδεθείτε με το τοπικό LLM από C# και δείτε πώς να δώσετε εντολή
  σε μεγάλο μοντέλο γλώσσας, να φορτώσετε έγγραφο Word, να καλέσετε το τοπικό LLM
  και να ξαναγράψετε το κείμενο αυτόματα σε λίγα λεπτά.
og_title: Σύνδεση με τοπικό LLM σε C# – Πλήρης Οδηγός Προγραμματισμού
tags:
- Aspose.Words
- C#
- LLM
- AI Automation
title: Σύνδεση με τοπικό LLM σε C# – Πλήρης Οδηγός Προγραμματισμού
url: /el/net/ai-powered-document-processing/connect-to-local-llm-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Σύνδεση με το Τοπικό LLM σε C# – Πλήρης Οδηγός Προγραμματισμού

Έχετε ποτέ χρειαστεί να **συνδέσετε το τοπικό llm** από μια εφαρμογή .NET και να αναρωτηθείτε πώς να το κάνετε να «μιλήσει» με ένα αρχείο Word; Δεν είστε μόνοι. Σε αυτόν τον οδηγό θα περάσουμε από όλη τη διαδικασία — σύνδεση με το τοπικό llm, **prompt large language model**, φόρτωση ενός εγγράφου Word, **call local llm**, και τέλος **rewrite text automatically**. Στο τέλος θα έχετε ένα εκτελέσιμο παράδειγμα που μετατρέπει οποιαδήποτε παράγραφο σε επίσημο τόνο χωρίς εξωτερικά κλειδιά API.

## Τι καλύπτει αυτό το tutorial

Θα ξεκινήσουμε εγκαθιστώντας τα απαραίτητα πακέτα NuGet, μετά θα δημιουργήσουμε ένα απλό τοπικό LLM endpoint (σκεφτείτε το Ollama στη θύρα 11434). Στη συνέχεια θα φορτώσουμε ένα αρχείο `.docx` χρησιμοποιώντας το Aspose.Words, θα στείλουμε μια παράγραφο στο LLM, θα λάβουμε μια επανεγγραμμένη έκδοση και θα την γράψουμε πίσω στο ίδιο έγγραφο. Θα δείτε επίσης πώς να αντιμετωπίσετε κοινά προβλήματα — κενές παραγράφους, async διαχείριση πόρων, και ιδιαιτερότητες κωδικοποίησης — ώστε ο κώδικας να λειτουργεί σε παραγωγή, όχι μόνο σε demo.

### Προαπαιτούμενα

- .NET 6.0 SDK ή νεότερο (μπορείτε επίσης να χρησιμοποιήσετε .NET 8 αν θέλετε)
- Visual Studio 2022 ή VS Code με επέκταση C#
- **Aspose.Words for .NET** (η δωρεάν δοκιμή λειτουργεί καλά)
- Ένα τοπικά φιλοξενούμενο LLM που ακολουθεί το συμβόλαιο `/api/generate` (π.χ., Ollama, LMStudio)
- Βασική εξοικείωση με async/await σε C#

> **Pro tip:** Αν δεν έχετε εγκαταστήσει ακόμα το Ollama, εκτελέστε `ollama serve` και κατεβάστε ένα μοντέλο με `ollama pull llama3`. Το προεπιλεγμένο HTTP endpoint θα είναι `http://localhost:11434/api/generate`.

---

## Βήμα 1: Εγκατάσταση Απαιτούμενων Πακέτων

Αρχικά, προσθέστε τα πακέτα NuGet Aspose.Words και Aspose.Words.AI στο πρόγραμμά σας.

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

Αυτές οι βιβλιοθήκες μας παρέχουν τη δυνατότητα **load word document** και ένα ελαφρύ wrapper για **call local llm** χωρίς να χρειάζεται να δημιουργήσουμε χειροκίνητα HTTP αιτήματα.

---

## Βήμα 2: Σύνδεση με το Τοπικό LLM Endpoint

Η σύνδεση με ένα τοπικά φιλοξενούμενο μοντέλο είναι τόσο απλή όσο η δημιουργία ενός αντικειμένου `LocalLargeLanguageModel`. Ο κατασκευαστής αναμένει το πλήρες URL του endpoint δημιουργίας.

```csharp
using Aspose.Words.AI;
using Aspose.Words;
using System.Threading.Tasks;

// Create a client that talks to the LLM running on localhost
var localLlm = new LocalLargeLanguageModel("http://localhost:11434/api/generate");
```

Γιατί τυλίγουμε το endpoint σε μια κλάση; Η `LocalLargeLanguageModel` διαχειρίζεται τη σειριοποίηση JSON, τις επαναπροσπάθειες και τις ροές απαντήσεων για εσάς — ώστε να μπορείτε να εστιάσετε στη λογική του prompt αντί να ασχολείστε με το `HttpClient`.

---

## Βήμα 3: Φόρτωση Πηγαίου Εγγράφου Word

Στη συνέχεια, φέρνουμε το έγγραφο στη μνήμη. Το Aspose.Words υποστηρίζει σχεδόν κάθε μορφή Word, έτσι το `Document` θα αναλύσει το `input.docx` χωρίς να χρειάζεται εγκατεστημένο Office.

```csharp
// Path to the source file – adjust as needed
string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document; throws if the file is missing or corrupted
Document sourceDocument = new Document(inputPath);
```

Αν χρειάζεται να δουλέψετε με ροή (π.χ., ένα αρχείο που ανεβάστηκε μέσω ASP.NET), απλώς αντικαταστήστε τη διαδρομή αρχείου με ένα `MemoryStream` και περάστε το στον κατασκευαστή `Document`.

---

## Βήμα 4: Εξαγωγή Κειμένου Τρέχουσας Παραγράφου

Θα χρησιμοποιήσουμε το `DocumentBuilder` για να περιηγηθούμε στο έγγραφο. Σε αυτό το παράδειγμα επανεγγράφουμε **την πρώτη παράγραφο**, αλλά μπορείτε να επαναλάβετε το `sourceDocument.GetChildNodes(NodeType.Paragraph, true)` για να επεξεργαστείτε πολλές.

```csharp
// Builder gives us a cursor inside the document
DocumentBuilder docBuilder = new DocumentBuilder(sourceDocument);

// Grab the text of the paragraph where the builder is currently positioned
string originalParagraph = docBuilder.CurrentParagraph?.GetText() ?? string.Empty;

// Safety check – avoid sending empty strings to the LLM
if (string.IsNullOrWhiteSpace(originalParagraph))
{
    Console.WriteLine("No paragraph found at the current cursor position.");
    return;
}
```

Ο τελεστής `?.` αποτρέπει ένα `NullReferenceException` αν το έγγραφο είναι κενό. Αυτό είναι ένα από εκείνα τα **edge cases** που παγιδεύουν τους αρχάριους.

---

## Βήμα 5: Prompt το LLM για Επανεγγραφή της Παραγράφου

Τώρα πραγματικά **prompt large language model**. Το prompt είναι απλή αγγλική; το wrapper θα το στείλει ως JSON στο τοπικό endpoint.

```csharp
// Build a friendly instruction for the model
string prompt = $"Rewrite the following sentence in a more formal tone:\n{originalParagraph}";

// Await the model's response – this is an async call
string rewrittenParagraph = await localLlm.PromptAsync(prompt);
```

Γιατί διατυπώνουμε το αίτημα έτσι; Τα LLM ανταποκρίνονται καλύτερα σε σαφείς, μονο‑εργασίες οδηγίες. Η προσθήκη μιας νέας γραμμής μετά το άνω‑κάτω τελεία χωρίζει την οδηγία από το περιεχόμενο, μειώνοντας την πιθανότητα το μοντέλο να επαναλάβει το prompt.

**Expected output** – Αν το `originalParagraph` ήταν `"Hey, what's up?"`, το LLM μπορεί να επιστρέψει:

> “Καλημέρα, πώς μπορώ να σας βοηθήσω;”

Μπορείτε να επαληθεύσετε το αποτέλεσμα εκτυπώνοντάς το:

```csharp
Console.WriteLine("Original:  " + originalParagraph);
Console.WriteLine("Rewritten: " + rewrittenParagraph);
```

---

## Βήμα 6: Εισαγωγή του Επανεγγραμμένου Κειμένου Πίσω στο Έγγραφο

Με το νέο κείμενο στα χέρια, αντικαθιστούμε την παλιά παράγραφο. Η `DocumentBuilder.Writeln` γράφει μια νέα γραμμή και προχωρά το cursor, κάτι τέλειο για προσθήκη. Αν χρειάζεται να *αντικαταστήσετε* ακριβώς την ίδια παράγραφο, μπορείτε να χρησιμοποιήσετε `docBuilder.CurrentParagraph.RemoveAllChildren()` πριν τη γραφή.

```csharp
// Option A – Append a new paragraph (keeps the original)
docBuilder.Writeln(rewrittenParagraph);

// Option B – Replace the existing paragraph (uncomment to use)
// docBuilder.CurrentParagraph.RemoveAllChildren();
// docBuilder.CurrentParagraph.AppendChild(new Run(docBuilder.Document, rewrittenParagraph));
```

Και οι δύο προσεγγίσεις εμφανίζονται ώστε να μπορείτε να επιλέξετε αυτή που ταιριάζει στη ροή εργασίας σας.

---

## Βήμα 7: Αποθήκευση του Ενημερωμένου Εγγράφου

Τέλος, αποθηκεύουμε τις αλλαγές σε ένα νέο αρχείο. Το Aspose.Words επιλέγει αυτόματα τη μορφή βάσει της επέκτασης του αρχείου.

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
sourceDocument.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Ανοίξτε το `output.docx` στο Word, και θα δείτε ότι η παράγραφος τώρα διαβάζεται σε επίσημο τόνο.

---

## Πλήρες Παράδειγμα Λειτουργίας

Παρακάτω βρίσκεται το **complete, self‑contained program**. Αντιγράψτε‑και‑επικολλήστε το σε ένα console project, επαναφέρετε τα πακέτα NuGet και τρέξτε το — χωρίς πρόσθετη ρύθμιση εκτός από ένα ενεργό τοπικό LLM.

```csharp
using Aspose.Words.AI;
using Aspose.Words;
using System;
using System.IO;
using System.Threading.Tasks;

class Program
{
    static async Task Main()
    {
        // -------------------------------------------------
        // Step 1: Connect to the locally hosted LLM endpoint
        // -------------------------------------------------
        var localLlm = new LocalLargeLanguageModel("http://localhost:11434/api/generate");

        // -------------------------------------------------
        // Step 2: Load the source Word document
        // -------------------------------------------------
        string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        Document sourceDocument = new Document(inputPath);

        // -------------------------------------------------
        // Step 3: Retrieve the text of the current paragraph
        // -------------------------------------------------
        DocumentBuilder docBuilder = new DocumentBuilder(sourceDocument);
        string originalParagraph = docBuilder.CurrentParagraph?.GetText() ?? string.Empty;

        if (string.IsNullOrWhiteSpace(originalParagraph))
        {
            Console.WriteLine("No paragraph found at the current cursor position.");
            return;
        }

        // -------------------------------------------------
        // Step 4: Ask the LLM to rewrite the paragraph in a formal tone
        // -------------------------------------------------
        string prompt = $"Rewrite the following sentence in a more formal tone:\n{originalParagraph}";
        string rewrittenParagraph = await localLlm.PromptAsync(prompt);

        // -------------------------------------------------
        // Step 5: Insert the rewritten text back into the document
        // -------------------------------------------------
        docBuilder.Writeln(rewrittenParagraph);

        // -------------------------------------------------
        // Step 6: Save the updated document
        // -------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
        sourceDocument.Save(outputPath);

        Console.WriteLine("Original paragraph:");
        Console.WriteLine(originalParagraph);
        Console.WriteLine("\nRewritten paragraph:");
        Console.WriteLine(rewrittenParagraph);
        Console.WriteLine($"\nDocument saved to {outputPath}");
    }
}
```

### Τι να Περιμένετε Όταν το Εκτελέσετε

1. Η κονσόλα εκτυπώνει τις αρχικές και τις επανεγγραμμένες παραγράφους.  
2. `output.docx` εμφανίζεται δίπλα στο `input.docx`.  
3. Ανοίγοντας το αρχείο δείχνει τη νέα επίσημη παράγραφο που έχει εισαχθεί μετά την αρχική (ή αντικατασταθεί, αν χρησιμοποιήσατε τον εναλλακτικό κώδικα).

---

## Διαχείριση Συνηθισμένων Edge Cases

| Situation | Solution |
|-----------|----------|
| **Empty or whitespace‑only paragraph** | Ελέγξτε `string.IsNullOrWhiteSpace` πριν το prompt (δείτε το Βήμα 3). |
| **LLM returns an error or empty string** | Τυλίξτε το `PromptAsync` σε `try/catch` και επιστρέψτε το αρχικό κείμενο σε περίπτωση σφάλματος. |
| **Multiple paragraphs need rewriting** | Επανάληψη μέσω `sourceDocument.GetChildNodes(NodeType.Paragraph, true)` και εφαρμογή της ίδιας λογικής prompt. |
| **Large documents cause latency** | Ομαδοποιήστε παραγράφους και στείλτε τις σε ένα ενιαίο αίτημα (prompt έως 4 KB ανά κλήση). |
| **Non‑ASCII characters get garbled** | Βεβαιωθείτε ότι το endpoint του LLM χρησιμοποιεί UTF-8 (τα περισσότερα μοντέλα το κάνουν). |

---

## Επόμενα Βήματα & Σχετικά Θέματα

- **Prompt large language model** με πιο πλούσιες οδηγίες (π.χ., οδηγούς στυλ, όρια μήκους).  
- Χρησιμοποιήστε **call local llm** σε web API για να εκθέσετε την αυτοματοποίηση εγγράφων ως υπηρεσία.  
- Εξερευνήστε το **load word document** σε παράλληλες ροές για σενάρια υψηλής απόδοσης.  
- Συνδυάστε αυτή την προσέγγιση με **rewrite text automatically** για μαζική δημιουργία email ή τυποποίηση αναφορών.  

Αν θέλετε να εμβαθύνετε, δείτε την τεκμηρίωση του Aspose για **document merging** και την αναφορά API του Ollama για προσαρμοσμένες παραμέτρους δειγματοληψίας.

---

## Συμπέρασμα

Μόλις σας δείξαμε πώς να **connect to local llm** από C#, **prompt large language model**, **load word document**, **call local llm**, και **rewrite text automatically** — όλα σε μια ενιαία, εκτελέσιμη εφαρμογή console. Το πρότυπο κλιμακώνεται: αλλάξτε το prompt, επαναλάβετε τις παραγράφους, ή εκθέστε τη λογική μέσω ενός endpoint ASP.NET. Το βασικό συμπέρασμα είναι ότι τα τοπικά μοντέλα AI μπορούν να ενσωματωθούν στενά με κλασικές βιβλιοθήκες επεξεργασίας εγγράφων, παρέχοντας ισχυρή αυτοματοποίηση χωρίς να αφήνετε το αξιόπιστο on‑prem περιβάλλον σας.

Έχετε ερωτήσεις σχετικά με το threading,

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}