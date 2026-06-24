---
category: general
date: 2026-06-24
description: Τοπικό σεμινάριο LLM που δείχνει πώς να καλέσετε ένα τοπικό LLM, να φορτώσετε
  ένα έγγραφο Word και να εκτελέσετε έλεγχο γραμματικής χρησιμοποιώντας AI έλεγχο
  γραμματικής σε C#.
draft: false
keywords:
- local llm tutorial
- run grammar check
- ai grammar check
- call local llm
- load word document
language: el
og_description: Το τοπικό σεμινάριο LLM εξηγεί βήμα‑προς‑βήμα πώς να καλέσετε ένα
  τοπικό LLM, να φορτώσετε ένα έγγραφο Word και να εκτελέσετε έναν AI έλεγχο γραμματικής
  σε C#.
og_title: Τοπικός Οδηγός LLM – Κλήση Τοπικού LLM και Εκτέλεση Ελέγχου Γραμματικής
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: Local LLM tutorial that shows you how to call a local LLM, load a Word
    document and run grammar check using AI grammar check in C#.
  headline: Local LLM Tutorial – How to Call a Local LLM and Run Grammar Check
  type: TechArticle
- description: Local LLM tutorial that shows you how to call a local LLM, load a Word
    document and run grammar check using AI grammar check in C#.
  name: Local LLM Tutorial – How to Call a Local LLM and Run Grammar Check
  steps:
  - name: How to Run
    text: 1. Open a terminal in the project folder. 2. Run `dotnet run`. 3. Watch
      the console print the corrected text.
  - name: Can I use a different LLM brand?
    text: Absolutely. As long as the server respects the OpenAI v1 API schema, just
      change `Endpoint` and pick the corresponding `AiModelType` enum value (e.g.,
      `AiModelType.Llama2`). The rest of the code stays identical.
  - name: What if my document is huge (10 MB+)?
    text: Large payloads can exceed the default request size of many servers. Split
      the document into sections and call `CheckGrammar` per section, then concatenate
      the results. This also reduces the chance of a timeout.
  - name: How do I write the corrected output back to a `.docx` file?
    text: 'The `Document` class usually provides a `Save(string path, string content)`
      method. After you get `result.CorrectedText`, call:'
  - name: Is the dummy API key a security risk?
    text: No. The key is ignored by self‑hosted endpoints, but some SDKs enforce a
      non‑null string. Using a placeholder like `"dummy"` satisfies the SDK without
      exposing any secrets.
  type: HowTo
tags:
- LLM
- C#
- GrammarCheck
- AI
title: Τοπικό Σεμινάριο LLM – Πώς να Κλήσετε ένα Τοπικό LLM και να Εκτελέσετε Έλεγχο
  Γραμματικής
url: /el/net/ai-powered-document-processing/local-llm-tutorial-how-to-call-a-local-llm-and-run-grammar-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Τοπικό LLM Tutorial – Κλήση Τοπικού LLM και Εκτέλεση Ελέγχου Γραμματικής

Έχετε αναρωτηθεί ποτέ πώς να **εκτελέσετε έλεγχο γραμματικής** σε ένα αρχείο Word χωρίς να στέλνετε τίποτα στο cloud; Σε αυτό το **τοπικό llm tutorial** θα συνδέσουμε ένα αυτο‑φιλοξενούμενο μεγάλο μοντέλο γλώσσας, θα φορτώσουμε ένα αρχείο `.docx` και θα αφήσουμε το AI να τακτοποιήσει το κείμενο. Χωρίς κλειδιά API, χωρίς εξωτερική κίνηση—μόνο ο δικός σας υπολογιστής να κάνει τη σκληρή δουλειά.

Θα περάσουμε από κάθε γραμμή κώδικα, θα εξηγήσουμε γιατί κάθε μέρος είναι σημαντικό, και θα σας δείξουμε πώς να αντιμετωπίζετε τα συνηθισμένα προβλήματα (όπως ελλιπή αρχεία ή μη προσβάσιμο σημείο λήψης). Στο τέλος θα έχετε μια έτοιμη προς εκτέλεση εφαρμογή κονσόλας C# που εκτελεί έναν **ai grammar check** χρησιμοποιώντας ένα τοπικά φιλοξενούμενο μοντέλο.

> **Τι θα πάρετε:** ένα πλήρες, εκτελέσιμο πρόγραμμα, μια σαφή εξήγηση κάθε βήματος, και συμβουλές για κλιμάκωση της λύσης σε μεγαλύτερα έγγραφα ή διαφορετικούς παρόχους LLM.

![διάγραμμα τοπικού tutorial LLM](https://example.com/local-llm-tutorial-diagram.png "Διάγραμμα που απεικονίζει τη ροή του τοπικού tutorial LLM")

## Προαπαιτούμενα

- .NET 6.0 SDK ή νεότερο (μπορείτε να το κατεβάσετε από τον ιστότοπο της Microsoft)
- Ένα τοπικά εκτελούμενο διακομιστή LLM που εκθέτει ένα συμβατό με OpenAI endpoint (π.χ., Ollama, LM Studio, ή ένα προσαρμοσμένο FastAPI wrapper)
- Το πακέτο NuGet `AiGrammar` (ή οποιαδήποτε βιβλιοθήκη παρέχει τις κλάσεις `LocalLargeLanguageModel`, `Document`, και `AiModelType`)
- Ένα δείγμα εγγράφου Word (`input.docx`) τοποθετημένο σε φάκελο που θα αναφέρετε αργότερα

Αυτό είναι όλο—δεν απαιτούνται επιπλέον διαπιστευτήρια cloud.

## Βήμα 1: Τοπικό LLM Tutorial – Ρύθμιση του Endpoint

Το πρώτο πράγμα που χρειάζεστε είναι ένα αντικείμενο **call local llm** που ξέρει πού να στέλνει τα αιτήματά του. Σκεφτείτε το ως τον αριθμό τηλεφώνου που καλείτε πριν μπορέσετε να μιλήσετε.

```csharp
using System;
using AiGrammar;   // Hypothetical library containing the LLM helpers

// Step 1: Configure a local large language model (LLM) endpoint
var llm = new LocalLargeLanguageModel
{
    Endpoint = "http://localhost:8000/v1",
    ApiKey = "dummy"   // Not required for self‑hosted models, but the property is mandatory
};
```

**Γιατί είναι σημαντικό:**  
Τα περισσότερα LLM SDKs αναμένουν ένα HTTP endpoint που ακολουθεί το συμβόλαιο του OpenAI API. Καθορίζοντας το `Endpoint` στο `http://localhost:8000/v1` λέμε στη βιβλιοθήκη να **call local llm** αντί να απευθύνεται στους διακομιστές της OpenAI. Το ψεύτικο κλειδί API είναι μόνο ένας placeholder—ορισμένοι πελάτες απορρίπτουν μια τιμή null, οπότε του δίνουμε κάτι αβλαβές.

> **Συμβουλή:** Αν τρέχετε το LLM πίσω από έναν reverse proxy, ορίστε το `Endpoint` στη διεύθυνση URL του proxy και αφήστε το proxy να διαχειριστεί την τερματισμό TLS. Αυτό κρατά την εφαρμογή κονσόλας σας απλή και ασφαλή.

## Βήμα 2: Φόρτωση Εγγράφου Word για Έλεγχο Γραμματικής

Τώρα που το μοντέλο είναι προσβάσιμο, πρέπει να **load word document** το περιεχόμενο στη μνήμη. Η κλάση `Document` αφαιρεί την ανάλυση του `.docx` για εμάς.

```csharp
// Step 2: Load the document you want to check
var docPath = @"C:\Projects\GrammarDemo\YOUR_DIRECTORY\input.docx";
if (!System.IO.File.Exists(docPath))
{
    Console.Error.WriteLine($"Error: The file '{docPath}' does not exist.");
    return;
}

var doc = new Document(docPath);
```

**Γιατί είναι σημαντικό:**  
Η άμεση παροχή ενός δυαδικού αρχείου `.docx` σε ένα LLM θα το συγχέει. Ο βοηθός `Document` εξάγει το ακατέργαστο κείμενο διατηρώντας τις διακοπές παραγράφων, κάτι που δίνει στο **ai grammar check** μια καθαρή είσοδο για επεξεργασία. Ο έλεγχος ύπαρξης αποτρέπει ένα ανεπιθύμητο `FileNotFoundException` που διαφορετικά θα κατέρρευε την εφαρμογή.

## Βήμα 3: Εκτέλεση Ελέγχου Γραμματικής Χρησιμοποιώντας το LLM

Αυτή είναι η καρδιά του tutorial: ζητάμε από το τοπικό μοντέλο να διορθώσει το κείμενο. Η μέθοδος `CheckGrammar` κρύβει τη σύνδεση HTTP και επιστρέφει ένα αντικείμενο αποτελέσματος.

```csharp
// Step 3: Run the grammar‑check operation using the LLM
var result = doc.CheckGrammar(
    llm,
    AiModelType.Gpt4   // You can swap this for any model supported by AiModelType
);
```

**Γιατί είναι σημαντικό:**  
Το `AiModelType.Gpt4` είναι μόνο μια ετικέτα που λέει στην απομακρυσμένη υπηρεσία ποιο πρότυπο prompt να χρησιμοποιήσει. Αν έχετε ένα μικρότερο μοντέλο (π.χ., `Llama2`), αντικαταστήστε το αντίστοιχα. Η βιβλιοθήκη σειριοποιεί το κείμενο του εγγράφου, το στέλνει στο `http://localhost:8000/v1/completions`, και αναλύει την διορθωμένη έξοδο.

> **Ακραία περίπτωση:** Αν το LLM υπερβεί το χρονικό όριο, το `CheckGrammar` ρίχνει ένα `TimeoutException`. Τυλίξτε την κλήση σε ένα μπλοκ `try/catch` αν αναμένετε μεγάλα έγγραφα ή έναν πολυάσχολο διακομιστή.

## Βήμα 4: Εξαγωγή του Διορθωμένου Κειμένου

Τέλος, εμφανίζουμε την καθαρισμένη έκδοση. Σε μια πραγματική εφαρμογή μπορεί να την γράψετε πίσω σε ένα νέο αρχείο `.docx`, αλλά για αυτό το tutorial μια εκτύπωση στην κονσόλα αρκεί.

```csharp
// Step 4: Output the corrected text
Console.WriteLine("=== Corrected Text ===");
Console.WriteLine(result.CorrectedText);
```

**Αναμενόμενη έξοδος** (υποθέτοντας ότι το αρχικό αρχείο περιείχε μερικά σκόπιμα λάθη):

```
=== Corrected Text ===
The quick brown fox jumps over the lazy dog. 
She doesn't like apples, but she loves oranges.
```

Αν το LLM δεν βρει κανένα σφάλμα, η έξοδος θα είναι ταυτόσημη με την είσοδο, κάτι που παραμένει χρήσιμο σήμα.

## Πλήρες Παράδειγμα Λειτουργίας

Συνδυάζοντας όλα, εδώ είναι το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε‑επικολλήσετε σε ένα νέο έργο κονσόλας:

```csharp
using System;
using AiGrammar;   // Replace with the actual namespace of your grammar library

namespace LocalLlmGrammarDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Configure the local LLM endpoint
            var llm = new LocalLargeLanguageModel
            {
                Endpoint = "http://localhost:8000/v1",
                ApiKey = "dummy"
            };

            // Path to the Word document you want to check
            var docPath = @"C:\Projects\GrammarDemo\YOUR_DIRECTORY\input.docx";

            // Verify the file exists before proceeding
            if (!System.IO.File.Exists(docPath))
            {
                Console.Error.WriteLine($"Error: The file '{docPath}' does not exist.");
                return;
            }

            // Load the document (this also extracts plain text)
            var doc = new Document(docPath);

            // Perform the AI grammar check using the local LLM
            GrammarCheckResult result;
            try
            {
                result = doc.CheckGrammar(llm, AiModelType.Gpt4);
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Grammar check failed: {ex.Message}");
                return;
            }

            // Show the corrected text
            Console.WriteLine("=== Corrected Text ===");
            Console.WriteLine(result.CorrectedText);
        }
    }
}
```

### Πώς να Εκτελέσετε

1. Ανοίξτε ένα τερματικό στον φάκελο του έργου.  
2. Εκτελέστε `dotnet run`.  
3. Παρακολουθήστε την κονσόλα να εκτυπώνει το διορθωμένο κείμενο.

Αυτό είναι ολόκληρο το **local llm tutorial** σε λιγότερο από 100 γραμμές κώδικα.

## Συχνές Ερωτήσεις (FAQ)

### Μπορώ να χρησιμοποιήσω διαφορετική μάρκα LLM;

Απόλυτα. Εφόσον ο διακομιστής σέβεται το σχήμα του OpenAI v1 API, απλώς αλλάξτε το `Endpoint` και επιλέξτε την αντίστοιχη τιμή του enum `AiModelType` (π.χ., `AiModelType.Llama2`). Το υπόλοιπο του κώδικα παραμένει αμετάβλητο.

### Τι γίνεται αν το έγγραφό μου είναι τεράστιο (10 MB+);

Μεγάλα payloads μπορούν να υπερβούν το προεπιλεγμένο μέγεθος αιτήματος πολλών διακομιστών. Χωρίστε το έγγραφο σε ενότητες και καλέστε το `CheckGrammar` ανά ενότητα, έπειτα συνδέστε τα αποτελέσματα. Αυτό επίσης μειώνει την πιθανότητα timeout.

### Πώς να γράψω το διορθωμένο αποτέλεσμα πίσω σε αρχείο `.docx`;

Η κλάση `Document` συνήθως παρέχει μια μέθοδο `Save(string path, string content)`. Αφού λάβετε το `result.CorrectedText`, καλέστε:

```csharp
doc.Save(@"C:\Projects\GrammarDemo\output_corrected.docx", result.CorrectedText);
```

Ελέγξτε την τεκμηρίωση της βιβλιοθήκης για την ακριβή υπογραφή.

### Είναι το ψεύτικο κλειδί API κίνδυνος ασφαλείας;

Όχι. Το κλειδί αγνοείται από τα αυτο‑φιλοξενούμενα endpoints, αλλά ορισμένα SDKs απαιτούν μια μη‑null συμβολοσειρά. Η χρήση ενός placeholder όπως `"dummy"` ικανοποιεί το SDK χωρίς να εκθέτει μυστικά.

## Επόμενα Βήματα και Σχετικά Θέματα

- **Fine‑tune your local LLM** για γραμματική ειδική σε τομέα (π.χ., νομική ή ιατρική γραφή).  
- **Run a batch job** που επεξεργάζεται ολόκληρο φάκελο αρχείων Word—ιδανικό για pipelines δημοσίευσης.  
- Εξερευνήστε **streaming responses** αν θέλετε προτάσεις σε πραγματικό χρόνο ενώ ο χρήστης πληκτρολογεί.  
- Συνδυάστε αυτό με **spell‑checking libraries** για διπλό επίπεδο ελέγχου ποιότητας.

Κάθε μία από αυτές τις ιδέες βασίζεται στις βασικές έννοιες που καλύπτονται σε αυτό το **local llm tutorial**, έτσι θα βρείτε τα ίδια μοτίβα—**call local llm**, **load word document**, **run grammar check**, και **handle results**—να επαναλαμβάνονται σε όλο το κείμενο.

---

*Καλό προγραμματισμό! Αν αντιμετωπίσετε πρόβλημα, αφήστε ένα σχόλιο παρακάτω και θα το επιλύσουμε μαζί.*

## Τι Θα Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά σχετικές θεματικές που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να κυριαρχήσετε σε πρόσθετα χαρακτηριστικά API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Φόρτωση με Κωδικοποίηση σε Έγγραφο Word](/words/english/net/programming-with-loadoptions/load-with-encoding/)
- [Φόρτωση Κρυπτογραφημένου σε Έγγραφο Word](/words/english/net/programming-with-loadoptions/load-encrypted-document/)
- [Ανάκτηση Κατεστραμμένου DOCX – Άνοιγμα & Φόρτωση Εγγράφου Word](/words/english/python-net/document-operations/recover-corrupted-docx-open-load-word-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}