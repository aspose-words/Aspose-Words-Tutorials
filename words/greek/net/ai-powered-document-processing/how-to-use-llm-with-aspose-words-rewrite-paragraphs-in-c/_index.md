---
category: general
date: 2026-05-04
description: Πώς να χρησιμοποιήσετε το LLM για την επεξεργασία εγγράφων με το Aspose
  – μάθετε πώς να αντικαθιστάτε κείμενο παραγράφων, να συνδέεστε με το τοπικό LLM
  και να ξαναγράφετε κείμενο χρησιμοποιώντας AI.
draft: false
keywords:
- how to use llm
- replace paragraph text
- connect to local llm
- rewrite text using ai
- edit document aspose
language: el
og_description: Πώς να χρησιμοποιήσετε LLM για την επεξεργασία εγγράφων με το Aspose.
  Αυτός ο οδηγός δείχνει πώς να συνδεθείτε σε ένα τοπικό LLM, να αντικαταστήσετε το
  κείμενο παραγράφου και να ξαναγράψετε το κείμενο χρησιμοποιώντας AI.
og_title: Πώς να χρησιμοποιήσετε το LLM με το Aspose.Words – Επαναγραφή παραγράφων
  σε C#
tags:
- Aspose.Words
- C#
- AI
- LLM
title: Πώς να χρησιμοποιήσετε το LLM με το Aspose.Words – Επαναγράψτε παραγράφους
  σε C#
url: /el/net/ai-powered-document-processing/how-to-use-llm-with-aspose-words-rewrite-paragraphs-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Χρησιμοποιήσετε LLM με το Aspose.Words – Επανάληψη Παραγράφων σε C#

Έχετε αναρωτηθεί ποτέ **πώς να χρησιμοποιήσετε LLM** για να βελτιώσετε ένα έγγραφο Word χωρίς να το ανοίξετε χειροκίνητα; Δεν είστε ο μόνος. Πολλοί προγραμματιστές συναντούν πρόβλημα όταν χρειάζεται να *αντικαταστήσουν το κείμενο μιας παραγράφου* προγραμματιστικά αλλά δεν έχουν μια καθαρή ροή εργασίας βασισμένη σε AI.

Σε αυτό το tutorial θα συνδέσουμε ένα τοπικό μεγάλο μοντέλο γλώσσας, θα του δώσουμε ένα απόσπασμα από ένα αρχείο `.docx`, θα του ζητήσουμε να **επαναγράψει το κείμενο χρησιμοποιώντας AI**, και τελικά θα αποθηκεύσουμε το ενημερωμένο έγγραφο—όλα με το Aspose.Words. Στο τέλος θα έχετε μια έτοιμη προς εκτέλεση εφαρμογή C# console που δείχνει ολόκληρη τη διαδικασία.

> **Τι θα λάβετε:** ένα πλήρες, εκτελέσιμο παράδειγμα, εξηγήσεις για κάθε βήμα, συμβουλές για ειδικές περιπτώσεις, και ιδέες για επέκταση της λύσης.

## Τι Θα Χρειαστείτε

- **.NET 6+** (ή .NET Framework 4.7.2 – ο κώδικας λειτουργεί και στα δύο)
- **Aspose.Words for .NET** (πακέτο NuGet `Aspose.Words`)
- Ένας **τοπικός διακομιστής LLM** που εκθέτει ένα απλό HTTP `/generate` endpoint (π.χ., Ollama, LMStudio, ή μια προσαρμοσμένη υπηρεσία Flask)
- Βασική εξοικείωση με C# και κώδικα HTTP client  

Δεν απαιτούνται πρόσθετα SDKs· όλα τα υπόλοιπα βρίσκονται στον κώδικα που θα γράψουμε μαζί.

## Βήμα 1: Πώς να Χρησιμοποιήσετε LLM για να Αντικαταστήσετε το Κείμενο Παραγράφου

Το πρώτο που πρέπει να κάνουμε είναι να εντοπίσουμε την παράγραφο που θέλουμε να τροποποιήσουμε. Το Aspose.Words το κάνει εύκολο, εκθέτοντας ένα πλούσιο αντικειμενοστραφές μοντέλο.

```csharp
using Aspose.Words;
using Aspose.Words.AI;   // Imaginary namespace for illustration – replace with actual if needed
using System.Net.Http;
using System.Text;
using System.Text.Json;

// Load the source document
Document document = new Document("YOUR_DIRECTORY/input.docx");

// Grab the third paragraph (zero‑based index)
Paragraph targetParagraph = document.FirstSection.Body.Paragraphs[2];

// Show the original text in the console – handy for debugging
Console.WriteLine("Original paragraph:");
Console.WriteLine(targetParagraph.GetText());
```

**Γιατί είναι σημαντικό:**  
Η επιλογή του σωστού κόμβου αποτρέπει την τυχαία αντικατάσταση τίτλων ή πινάκων. Χρησιμοποιώντας την προσέγγιση **replace paragraph text** διατηρούμε τη δομή του εγγράφου αμετάβλητη, ενώ επεξεργαζόμαστε μόνο το περιεχόμενο που μας ενδιαφέρει.

> **Pro tip:** Εάν το έγγραφό σας περιέχει ενότητες μεταβλητού μήκους, χρησιμοποιήστε `document.GetChildNodes(NodeType.Paragraph, true)` και LINQ για να εντοπίσετε μια παράγραφο με βάση το κείμενό της ή το στυλ.

## Βήμα 2: Σύνδεση με Τοπικό Endpoint LLM

Τώρα που έχουμε το κείμενο, πρέπει να το στείλουμε στο LLM. Το παράδειγμα χρησιμοποιεί μια απλή κλάση περιτύλιξης `LocalLargeLanguageModel` που κρύβει τις λεπτομέρειες του HTTP. Μπορείτε να την αντικαταστήσετε με κλήσεις `HttpClient` αν προτιμάτε.

```csharp
/// <summary>
/// Minimal wrapper around a local LLM HTTP API.
/// Assumes the API accepts a JSON payload { "prompt": "..."} and returns { "response": "..." }.
/// </summary>
public class LocalLargeLanguageModel
{
    private readonly HttpClient _client;
    private readonly string _endpoint;

    public LocalLargeLanguageModel(string endpoint)
    {
        _endpoint = endpoint.TrimEnd('/');
        _client = new HttpClient();
    }

    public string GenerateText(string prompt)
    {
        var payload = new { prompt };
        var content = new StringContent(JsonSerializer.Serialize(payload), Encoding.UTF8, "application/json");

        // Synchronous call for brevity – in production use async/await
        var response = _client.PostAsync($"{_endpoint}/generate", content).Result;
        response.EnsureSuccessStatusCode();

        var json = response.Content.ReadAsStringAsync().Result;
        var result = JsonSerializer.Deserialize<Dictionary<string, string>>(json);
        return result?["response"] ?? string.Empty;
    }
}

// Step 2: Instantiate the LLM client pointing at localhost
var localLlm = new LocalLargeLanguageModel("http://localhost:5000");
```

**Γιατί συνδέουμε με αυτόν τον τρόπο:**  
Μια ρύθμιση **connect to local llm** εξαλείφει την καθυστέρηση, διατηρεί τα δεδομένα εντός της υποδομής και αποφεύγει τα κόστη API. Η κλάση περιτύλιξης κάνει επίσης τον επόμενο κώδικα πιο καθαρό, επιτρέποντάς μας να εστιάσουμε στη λογική **rewrite text using ai**.

## Βήμα 3: Επανάληψη Κειμένου Χρησιμοποιώντας AI με το Aspose.Words

Με το κείμενο της παραγράφου στα χέρια και το LLM έτοιμο, δημιουργούμε ένα prompt που λέει στο μοντέλο ακριβώς τι θέλουμε — επανάληψη σε επίσημο τόνο. Μπορείτε να προσαρμόσετε το prompt για άλλες μορφές (φιλικό, τεχνικό κ.λπ.).

```csharp
// Build the prompt – notice the newline for readability
string prompt = $"Rewrite the following in a formal tone:\n{targetParagraph.GetText()}";

// Ask the LLM to generate the revised version
string revisedText = localLlm.GenerateText(prompt);

// Show the AI‑generated text
Console.WriteLine("\nRevised paragraph:");
Console.WriteLine(revisedText);
```

**Γιατί λειτουργεί:**  
Τα LLM λειτουργούν με prompts· η παροχή σαφών οδηγιών (“Rewrite … in a formal tone”) αποδίδει συνεπή αποτελέσματα. Το βήμα **rewrite text using ai** είναι η καρδιά του tutorial – δείχνει πώς το AI μπορεί να ενσωματωθεί άμεσα σε ροές εργασίας εγγράφων.

## Βήμα 4: Επεξεργασία του Εγγράφου και Αποθήκευση Αλλαγών

Τώρα αντικαθιστούμε τα αρχικά runs με το νέο περιεχόμενο. Το Aspose.Words αποθηκεύει το κείμενο σε αντικείμενα `Run`, οπότε η εκκαθάριση τους πρώτα αποτρέπει υπολειπόμενα σφάλματα μορφοποίησης.

```csharp
// Clear existing runs (pieces of text) from the paragraph
targetParagraph.Runs.Clear();

// Append a new Run containing the revised text
targetParagraph.AppendChild(new Run(document, revisedText));

// Save the updated document
document.Save("YOUR_DIRECTORY/output.docx");

// Confirmation
Console.WriteLine("\nDocument saved as output.docx");
```

**Σημείωση για ειδικές περιπτώσεις:**  
Εάν η αρχική παράγραφος περιείχε μικτή μορφοποίηση (έντονα, πλάγια), ίσως θέλετε να διατηρήσετε τα στυλ. Σε αυτήν την περίπτωση, δημιουργήστε ένα νέο `Run`, αντιγράψτε τις αρχικές ρυθμίσεις `Font`, και στη συνέχεια ορίστε το `Text` του σε `revisedText`.

## Πλήρες Παράδειγμα Λειτουργίας

Παρακάτω βρίσκεται ολόκληρο το πρόγραμμα που μπορείτε να αντιγράψετε‑επικολλήσετε σε ένα console project. Θυμηθείτε να εγκαταστήσετε πρώτα το πακέτο NuGet Aspose.Words (`dotnet add package Aspose.Words`).

```csharp
// ---------------------------------------------------------------
// Complete C# console app: how to use llm to edit a Word doc
// ---------------------------------------------------------------
using Aspose.Words;
using Aspose.Words.AI;   // Replace with real namespace if needed
using System;
using System.Collections.Generic;
using System.Net.Http;
using System.Text;
using System.Text.Json;

namespace LlmAsposeDemo
{
    public class LocalLargeLanguageModel
    {
        private readonly HttpClient _client;
        private readonly string _endpoint;

        public LocalLargeLanguageModel(string endpoint)
        {
            _endpoint = endpoint.TrimEnd('/');
            _client = new HttpClient();
        }

        public string GenerateText(string prompt)
        {
            var payload = new { prompt };
            var content = new StringContent(JsonSerializer.Serialize(payload), Encoding.UTF8, "application/json");

            var response = _client.PostAsync($"{_endpoint}/generate", content).Result;
            response.EnsureSuccessStatusCode();

            var json = response.Content.ReadAsStringAsync().Result;
            var result = JsonSerializer.Deserialize<Dictionary<string, string>>(json);
            return result?["response"] ?? string.Empty;
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the document
            Document document = new Document("YOUR_DIRECTORY/input.docx");

            // 2️⃣ Pick the third paragraph (index 2)
            Paragraph targetParagraph = document.FirstSection.Body.Paragraphs[2];
            Console.WriteLine("Original paragraph:");
            Console.WriteLine(targetParagraph.GetText());

            // 3️⃣ Connect to the local LLM
            var localLlm = new LocalLargeLanguageModel("http://localhost:5000");

            // 4️⃣ Ask the model to rewrite it formally
            string prompt = $"Rewrite the following in a formal tone:\n{targetParagraph.GetText()}";
            string revisedText = localLlm.GenerateText(prompt);
            Console.WriteLine("\nRevised paragraph:");
            Console.WriteLine(revisedText);

            // 5️⃣ Replace the paragraph contents
            targetParagraph.Runs.Clear();
            targetParagraph.AppendChild(new Run(document, revisedText));

            // 6️⃣ Save the file
            document.Save("YOUR_DIRECTORY/output.docx");
            Console.WriteLine("\nDocument saved as output.docx");
        }
    }
}
```

### Αναμενόμενο Αποτέλεσμα

```
Original paragraph:
the quick brown fox jumps over the lazy dog.

Revised paragraph:
The quick brown fox leaps over the lazy dog in a formal manner.

Document saved as output.docx
```

Ανοίξτε το `output.docx` – θα δείτε ότι η τρίτη παράγραφος τώρα εμφανίζει την επεξεργασμένη έκδοση.

## Συχνές Ερωτήσεις & Προβλήματα

| Ερώτηση | Απάντηση |
|----------|--------|
| **Τι γίνεται αν το LLM μου επιστρέφει JSON με επιπλέον πεδία;** | Προσαρμόστε το `GenerateText` ώστε να αποσυμπιέζει τη σωστή ιδιότητα ή να αναλύει την απάντηση χειροκίνητα. |
| **Μπορώ να επεξεργαστώ πολλές παραγράφους ταυτόχρονα;** | Ναι – επαναλάβετε πάνω στο `document.FirstSection.Body.Paragraphs` και εφαρμόστε την ίδια λογική prompt, ίσως προσθέτοντας έναν δείκτη παραγράφου στο prompt για συμφραζόμενα. |
| **Ο διακομιστής LLM μου χρησιμοποιεί έλεγχο ταυτότητας;** | Προσθέστε ένα header στο `HttpClient` πριν το POST: `_client.DefaultRequestHeaders.Add("Authorization", "Bearer YOUR_TOKEN");`. |
| **Η μορφοποίηση χάνεται μετά την αντικατάσταση.** | Διατηρήστε τις αρχικές ρυθμίσεις `Run.Font`: δημιουργήστε ένα νέο `Run`, αντιγράψτε το `originalRun.Font.Clone()`, και στη συνέχεια ορίστε το `Text`. |
| **Το LLM μερικές φορές επιστρέφει κενές συμβολοσειρές.** | Υλοποιήστε fallback – αν `revisedText.Trim().Length == 0`, διατηρήστε το αρχικό κείμενο ή δοκιμάστε ξανά με πιο απλό prompt. |

## Επέκταση της Λύσης

Τώρα που έχετε κατακτήσει **how to use llm** για μια μόνο παράγραφο, σκεφτείτε τα επόμενα βήματα:

- **Batch processing:** Επανάληψη σε κάθε παράγραφο και επαναγραφή σε επιλεγμένο στυλ (π.χ., “κάντε όλο το κείμενο συνοπτικό”).  
- **Style‑aware rewriting:** Περάστε το όνομα του αρχικού στυλ παραγράφου στο prompt ώστε το LLM να σέβεται τίτλους vs κείμενο σώματος.  
- **Integration with a CI pipeline:** Αυτοματοποιήστε την επεξεργασία εγγράφων ως μέρος της διαδικασίας δημιουργίας τεκμηρίωσης.  
- **Alternative prompts:** Δοκιμάστε “summarize this paragraph” ή “translate this paragraph to Spanish” για να εξερευνήσετε τη πλήρη δύναμη του **rewrite text using ai**.

## Συμπέρασμα

Διασχίσαμε όλη τη ροή του **how to use llm** με το Aspose.Words: φόρτωση εγγράφου, **connect to local llm**, εξαγωγή παραγράφου, **rewrite text using ai**, **replace paragraph text**, και τελικά αποθήκευση του αποτελέσματος. Ο κώδικας είναι αυτόνομος, λειτουργεί αμέσως, και παρουσιάζει έναν πρακτικό τρόπο ενσωμάτωσης AI σε παραδοσιακή αυτοματοποίηση εγγράφων.

Δοκιμάστε το, προσαρμόστε τα prompts, και αφήστε

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}