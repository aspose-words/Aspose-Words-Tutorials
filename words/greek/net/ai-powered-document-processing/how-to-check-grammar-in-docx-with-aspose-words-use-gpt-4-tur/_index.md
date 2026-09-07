---
category: general
date: 2026-01-14
description: Μάθετε πώς να ελέγχετε τη γραμματική σε ένα αρχείο DOCX χρησιμοποιώντας
  το Aspose.Words και το μοντέλο gpt-4 turbo. Αυτός ο οδηγός δείχνει επίσης πώς να
  φορτώνετε το docx και να καταγράφετε τα γραμματικά σφάλματα.
draft: false
keywords:
- how to check grammar
- how to load docx
- load word document
- use gpt-4 turbo
- list grammar errors
language: el
og_description: Οδηγός βήμα‑βήμα για το πώς να ελέγξετε τη γραμματική σε αρχείο DOCX
  χρησιμοποιώντας το Aspose.Words και το μοντέλο AI gpt‑4 turbo. Περιλαμβάνει κώδικα,
  συμβουλές και το αναμενόμενο αποτέλεσμα.
og_title: Πώς να ελέγξετε τη γραμματική σε DOCX – Aspose.Words & gpt-4 turbo
tags:
- Aspose.Words
- C#
- AI grammar checking
title: Πώς να ελέγξετε τη γραμματική σε DOCX με το Aspose.Words – χρησιμοποιήστε το
  gpt‑4 turbo
url: /el/net/ai-powered-document-processing/how-to-check-grammar-in-docx-with-aspose-words-use-gpt-4-tur/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Ελέγξετε τη Γραμματική σε DOCX με το Aspose.Words – χρήση gpt-4 turbo

Έχετε αναρωτηθεί ποτέ **πώς να ελέγξετε τη γραμματική** σε ένα έγγραφο Word χωρίς να ανοίξετε το Microsoft Word; Δεν είστε μόνοι. Πολλοί προγραμματιστές χρειάζονται να επικυρώνουν κείμενο προγραμματιστικά, ειδικά όταν δημιουργούν pipelines περιεχομένου, back‑ends CMS ή αυτοματοποιημένα εργαλεία διόρθωσης. Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα μια πλήρη, έτοιμη‑για‑εκτέλεση λύση που φορτώνει ένα *.docx* αρχείο, στέλνει το περιεχόμενό του στο μοντέλο **gpt‑4 turbo** και εκτυπώνει κάθε γραμματικό ζήτημα που εντοπίζει.

Θα καλύψουμε επίσης **how to load docx**, τις λεπτομέρειες του βήματος **load word document**, και πώς να **list grammar errors** σε μια σαφή, καταναλώσιμη μορφή. Στο τέλος, θα έχετε ένα μόνο αρχείο C# που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο .NET και να αρχίσετε να εντοπίζετε λάθη αμέσως.

> **Συμβουλή:** Αν ήδη χρησιμοποιείτε το Aspose.Words αλλού (π.χ., για μετατροπή σε PDF), αυτή η προσέγγιση προσθέτει σχεδόν καθόλου επιπλέον φόρτο.

![Διάγραμμα που δείχνει τη ροή φόρτωσης ενός DOCX, αποστολής του στο gpt‑4 turbo, και λήψης γραμματικών ζητημάτων. Κείμενο alt: how to check grammar diagram](/images/grammar-check-flow.png)

## Τι Θα Χρειαστείτε

- **.NET 6+** (ο κώδικας μεταγλωττίζεται με .NET Framework 4.6 επίσης, αλλά το .NET 6 είναι το τρέχον LTS)
- **Aspose.Words for .NET** – έκδοση 23.9 ή νεότερη (μπορείτε να το κατεβάσετε από το NuGet)
- **Aspose.Words.AI** πακέτο – περιέχει το enum `AiModelType` και το βοηθητικό `GrammarChecker`
- Ένα έγκυρο **Aspose Cloud API key** (ή τοπικό αρχείο άδειας) – απαιτείται για κλήσεις AI
- Ένα δείγμα **input.docx** τοποθετημένο σε φάκελο που ελέγχετε (θα το ονομάσουμε `YOUR_DIRECTORY`)

Δεν απαιτούνται εξωτερικοί πελάτες REST ή χειροκίνητος χειρισμός HTTP—το Aspose κάνει τη βαριά δουλειά.

## Πώς να Ελέγξετε τη Γραμματική σε Αρχείο DOCX

Παρακάτω βρίσκεται το **πλήρες, εκτελέσιμο πρόγραμμα**. Μπορείτε ελεύθερα να το αντιγράψετε‑και‑επικολλήσετε σε ένα έργο κονσόλας και να πατήσετε **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.AI;

namespace GrammarCheckDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -------------------------------------------------
            // Step 1: Load the Word document you want to analyze.
            // -------------------------------------------------
            // The path can be absolute or relative; here we assume a folder called
            // YOUR_DIRECTORY sits next to the executable.
            string docPath = @"YOUR_DIRECTORY/input.docx";

            // The Document constructor reads the file into memory.
            // If the file doesn't exist, an exception is thrown – we catch it later.
            Document document;
            try
            {
                document = new Document(docPath);
                Console.WriteLine($"✅ Loaded document: {docPath}");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"❌ Failed to load document. {ex.Message}");
                return;
            }

            // -------------------------------------------------
            // Step 2: Choose the AI model that will perform the grammar check.
            // -------------------------------------------------
            // Aspose.Words.AI currently supports several models.
            // For best accuracy and speed, we pick gpt‑4 turbo.
            AiModelType grammarModel = AiModelType.Gpt4Turbo;

            // -------------------------------------------------
            // Step 3: Run the grammar checker and collect any issues.
            // -------------------------------------------------
            // GrammarChecker.CheckGrammar returns a collection of Issue objects.
            // Each Issue contains Severity, Message, and Location (page/paragraph).
            var grammarIssues = GrammarChecker.CheckGrammar(document, grammarModel);

            // -------------------------------------------------
            // Step 4: Output each issue with its severity, message, and location.
            // -------------------------------------------------
            if (grammarIssues.Count == 0)
            {
                Console.WriteLine("🎉 No grammar issues found! Your document looks good.");
            }
            else
            {
                Console.WriteLine($"🔎 Found {grammarIssues.Count} grammar issue(s):");
                foreach (var issue in grammarIssues)
                {
                    // Example output: "Warning: Use of passive voice at Paragraph 3, Run 5"
                    Console.WriteLine($"{issue.Severity}: {issue.Message} at {issue.Location}");
                }
            }

            // Keep the console window open when debugging.
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### Εξήγηση Κάθε Τμήματος

| Τμήμα | Γιατί Είναι Σημαντικό | Τι Θα Μπορούσατε Να Αλλάξετε |
|--------|----------------|-----------------------|
| **Φόρτωση του εγγράφου** | Αυτό είναι το βήμα **how to load docx**. Το Aspose αναλύει το αρχείο σε ένα αντικείμενο `Document`, παρέχοντάς σας πρόσβαση σε παραγράφους, runs, πίνακες κ.λπ. | Αν λαμβάνετε ένα stream (π.χ., από μεταφόρτωση web), χρησιμοποιήστε `new Document(stream)` αντί για διαδρομή αρχείου. |
| **Select AI model** | Η σταθερά `AiModelType.Gpt4Turbo` λέει στο Aspose να προωθήσει το κείμενο στο endpoint του GPT‑4 Turbo της OpenAI. Ισορροπεί το κόστος και την ταχύτητα. | Για πιο αυστηρή συμμόρφωση μπορείτε να μεταβείτε σε `AiModelType.Gpt4` (πιο αργό, πιο ακριβό) ή σε οποιοδήποτε μελλοντικό μοντέλο που υποστηρίζει το Aspose. |
| **Run the grammar checker** | `GrammarChecker.CheckGrammar` διαχειρίζεται την τοκενοποίηση, στέλνει το κείμενο στο AI και αναλύει την απάντηση JSON σε αντικείμενα `Issue` με ισχυρούς τύπους. | Μπορείτε να προσαρμόσετε την υπερφόρτωση `CheckGrammar` για να περάσετε ένα προσαρμοσμένο `GrammarCheckOptions` (π.χ., να αγνοήσετε ορισμένες κατηγορίες κανόνων). |
| **Print results** | Αυτό το τμήμα **lists grammar errors** σε μορφή κατανοητή από άνθρωπο. Μπορείτε επίσης να τα γράψετε σε αρχείο καταγραφής ή σε βάση δεδομένων. | Αν χρειάζεστε έξοδο κατανοητή από μηχανή, σειριοποιήστε το `grammarIssues` σε JSON με `JsonSerializer.Serialize`. |

## Πώς να Φορτώσετε DOCX Αποτελεσματικά (Δευτερεύουσα Λέξη‑Κλειδί: **how to load docx**)

Όταν εργάζεστε με μεγάλα αρχεία (10 MB+), η φόρτωση ολόκληρου του εγγράφου στη μνήμη μπορεί να είναι σπατάλη. Το Aspose προσφέρει μια κλάση **LoadOptions** που σας επιτρέπει να:

- **Read only the main text** (παράλειψη εικόνων, ενσωματωμένων αντικειμένων)
- **Detect the file format** αυτόματα, κάτι που είναι χρήσιμο αν δέχεστε τόσο `.docx` όσο και `.doc` μεταφορτώσεις.

```csharp
using Aspose.Words.Loading;

// Example: load only the text, ignore images.
LoadOptions options = new LoadOptions
{
    LoadFormat = LoadFormat.Docx,
    // Prevent loading of non‑text elements for speed.
    LoadImages = false,
    LoadHeadersFooters = false
};

Document lightweightDoc = new Document(docPath, options);
Console.WriteLine($"Loaded docx with {lightweightDoc.GetChildNodes(NodeType.Paragraph, true).Count} paragraphs.");
```

**Πότε να το χρησιμοποιήσετε;**  
Αν δημιουργείτε ένα API υψηλής απόδοσης που ελέγχει δεκάδες έγγραφα ανά δευτερόλεπτο, η ενεργοποίηση του `LoadImages = false` μπορεί να μειώσει τη χρήση CPU και μνήμης έως και 30 %.

## Χρήση gpt‑4 Turbo με το Aspose.Words.AI (Δευτερεύουσα Λέξη‑Κλειδί: **use gpt-4 turbo**)

Το Aspose αφαιρεί την κλήση REST της OpenAI πίσω από ένα απλό enum, αλλά στην πραγματικότητα:

1. Αποκτά απλό κείμενο από το `Document`.
2. Στέλνει ένα prompt όπως “Identify grammatical errors in the following text” στο endpoint **gpt‑4 turbo**.
3. Λαμβάνει μια λίστα JSON με ζητήματα και τα αντιστοιχίζει στις αρχικές θέσεις του Word.

Αν χρειάζεστε μεγαλύτερο έλεγχο του prompt (π.χ., επιβολή Βρετανικής Αγγλικής), μπορείτε να παρέχετε ένα προσαρμοσμένο `AiPrompt`:

```csharp
var customPrompt = new AiPrompt
{
    SystemMessage = "You are a professional proofreader using British English conventions.",
    UserMessage = "Find all grammatical errors in the supplied text."
};

var grammarIssues = GrammarChecker.CheckGrammar(document, grammarModel, customPrompt);
```

**Σκέψεις κόστους:**  
`gpt‑4 turbo` χρεώνεται ανά token. Ένα έγγραφο 5 σελίδων συνήθως καταναλώνει < 2 K tokens, μεταφράζοντας σε μερικά λεπτά ανά έλεγχο. Πάντα παρακολουθείτε τη χρήση σας στην κονσόλα Aspose Cloud.

## Καταγραφή Γραμματικών Σφαλμάτων με Φιλικό Τρόπο (Δευτερεύουσα Λέξη‑Κλειδί: **list grammar errors**)

Η ακατέργαστη συμβολοσειρά `Issue.Location` φαίνεται ως `"Paragraph 4, Run 2"`. Για χρήση σε UI μπορείτε

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}