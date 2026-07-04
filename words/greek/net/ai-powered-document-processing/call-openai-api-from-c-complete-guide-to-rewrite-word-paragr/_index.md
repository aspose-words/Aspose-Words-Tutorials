---
category: general
date: 2026-05-23
description: Κλήση του OpenAI API σε C# για την αναδιατύπωση πρότασης σε επίσημο στυλ.
  Μάθετε πώς να φορτώνετε έγγραφο Word, να καλείτε το τοπικό LLM και να αναδιατυπώνετε
  την παράγραφο επίσημα με το Aspose.Words.
draft: false
keywords:
- call openai api
- call local llm
- rewrite sentence formal
- rewrite paragraph formal
- load word document
language: el
og_description: Καλέστε το API της OpenAI σε C# για να ξαναγράψετε μια πρόταση σε
  επίσημο ύφος. Πλήρης βήμα‑βήμα οδηγός με κώδικα, εξηγήσεις και συμβουλές.
og_title: Κλήση του OpenAI API από C# – Αναδιατύπωση παραγράφων Word
schemas:
- author: Aspose
  dateModified: '2026-05-23'
  description: Call OpenAI API in C# to rewrite sentence formal style. Learn how to
    load word document, call local LLM, and rewrite paragraph formal with Aspose.Words.
  headline: Call OpenAI API from C# – Complete Guide to Rewrite Word Paragraphs
  type: TechArticle
- description: Call OpenAI API in C# to rewrite sentence formal style. Learn how to
    load word document, call local LLM, and rewrite paragraph formal with Aspose.Words.
  name: Call OpenAI API from C# – Complete Guide to Rewrite Word Paragraphs
  steps:
  - name: Why This Works
    text: '- **LocalLargeLanguageModel** abstracts the HTTP details, letting you **call
      local llm** exactly the same way you would a cloud OpenAI endpoint. - The prompt
      we send (`Rewrite the following sentence in formal tone:`) is concise, which
      helps the model focus on a **rewrite sentence formal** transforma'
  - name: Expected Output Example
    text: '| Original (informal) | Rewritten (formal) | |---------------------|--------------------|
      | *Hey team, can we get the results ASAP?* | *Dear team, could you please provide
      the results at your earliest convenience?* |'
  - name: Empty Paragraphs
    text: 'Sometimes a Word file contains empty paragraphs that throw off the LLM.
      Guard against this:'
  - name: Large Documents
    text: 'Processing a 100‑page report paragraph‑by‑paragraph can be slow. Batch
      the calls:'
  type: HowTo
tags:
- Aspose.Words
- C#
- LLM
- OpenAI
- Word Automation
title: Κλήση του OpenAI API από C# – Πλήρης οδηγός για την επανεγγραφή παραγράφων
  Word
url: /el/net/ai-powered-document-processing/call-openai-api-from-c-complete-guide-to-rewrite-word-paragr/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Κλήση του OpenAI API από C# – Πλήρης Οδηγός για την Αναγραφή Παραγράφων Word

Έχετε αναρωτηθεί ποτέ πώς να **call OpenAI API** από μια εφαρμογή .NET και να βελτιώσετε άμεσα ένα κομμάτι κειμένου; Ίσως έχετε ένα αρχείο Word που χρειάζεται πιο επίσημο τόνο για μια αναφορά πελάτη, και δεν θέλετε να το πληκτρολογήσετε ξανά. Σε αυτό το tutorial θα περάσουμε ακριβώς από αυτό: φόρτωση ενός εγγράφου Word, αποστολή μιας παραγράφου σε ένα τοπικά φιλοξενούμενο LLM που μιμείται το OpenAI‑compatible API, και λήψη μιας έκδοσης **rewrite paragraph formal**. Στο τέλος θα έχετε μια εκτελέσιμη εφαρμογή C# console που κάνει όλη τη δουλειά σε λίγες γραμμές.

Θα καλύψουμε όλα όσα χρειάζεστε: τα απαιτούμενα πακέτα NuGet, πώς να **load word document** με το Aspose.Words, τις ιδιαιτερότητες του **call local llm**, και γιατί η προτροπή «Rewrite the following sentence in formal tone» παράγει αξιόπιστα ένα αποτέλεσμα **rewrite sentence formal**. Χωρίς εξωτερικά έγγραφα, μόνο ένας αυτόνομος οδηγός που μπορείτε να αντιγράψετε‑επικολλήσετε και να εκτελέσετε.

## Τι Θα Επιτύχετε

- Φορτώστε ένα αρχείο *.docx* χρησιμοποιώντας το Aspose.Words.  
- Δημιουργήστε έναν πελάτη που μπορεί να **call OpenAI API**‑compatible endpoints, ακόμη και αν τρέχουν τοπικά.  
- Στείλτε μια παράγραφο στο LLM και λάβετε μια απάντηση **rewrite paragraph formal**.  
- Αντικαταστήστε το αρχικό κείμενο στο αρχείο Word και αποθηκεύστε το ενημερωμένο έγγραφο.  

Οι προαπαιτήσεις είναι ελάχιστες: .NET 6+ SDK, Visual Studio ή VS Code, και μια εγκατάσταση τοπικού LLM που εκθέτει ένα OpenAI‑compatible HTTP endpoint (π.χ., Ollama, LM Studio). Αν έχετε ήδη κλειδί cloud, μπορείτε να αλλάξετε το endpoint και το API key – ο κώδικας παραμένει ίδιος.

---

## Βήμα 1: Ρύθμιση του Έργου και Εγκατάσταση Πακέτων

Για αρχή, δημιουργήστε ένα νέο έργο console:

```bash
dotnet new console -n WordLlmRewrite
cd WordLlmRewrite
```

Τώρα προσθέστε τα δύο πακέτα NuGet που θα χρειαστούμε:

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

> **Pro tip:** Το Aspose.Words.AI περιλαμβάνει μια ελαφριά wrapper που γνωρίζει πώς να **call OpenAI API**‑style υπηρεσίες, ώστε να μην χρειάζεται να δημιουργήσετε χειροκίνητα HTTP αιτήματα.

## Βήμα 2: Γράψτε τον Κώδικα που **Call OpenAI API** (ή ένα Local LLM)

Ανοίξτε το `Program.cs` και αντικαταστήστε το περιεχόμενό του με το παρακάτω. Κάθε γραμμή εξηγείται παρακάτω, ώστε να μην χαθείτε.

```csharp
using Aspose.Words;
using Aspose.Words.AI;
using System;

// ------------------------------------------------------------
// 1️⃣ Create a client for the local LLM that follows the
//    OpenAI‑compatible API. This is the heart of the
//    “call openai api” step.
// ------------------------------------------------------------
var localLlm = new LocalLargeLanguageModel(
    endpoint: "http://localhost:8000/v1", // change if your server runs elsewhere
    apiKey: "dummy",                      // dummy because the local server usually skips auth
    model: "my-llm");                     // name of the model you want to use

// ------------------------------------------------------------
// 2️⃣ Load the source Word document.
// ------------------------------------------------------------
Document doc = new Document("YOUR_DIRECTORY/source.docx");

// ------------------------------------------------------------
// 3️⃣ Grab the first paragraph that we want to rewrite.
// ------------------------------------------------------------
Paragraph paragraph = doc.FirstSection.Body.FirstParagraph;

// ------------------------------------------------------------
// 4️⃣ Ask the LLM to rewrite the paragraph in a formal tone.
//    This is where we “rewrite paragraph formal”.
// ------------------------------------------------------------
string revisedText = localLlm.GenerateText(
    $"Rewrite the following sentence in formal tone:\n{paragraph.GetText()}");

// ------------------------------------------------------------
// 5️⃣ Replace the original paragraph text with the revised version.
// ------------------------------------------------------------
paragraph.Runs.Clear();                     // remove old runs
paragraph.AppendChild(new Run(doc, revisedText));

// ------------------------------------------------------------
// 6️⃣ Save the updated document.
// ------------------------------------------------------------
doc.Save("YOUR_DIRECTORY/rewritten.docx");

// ------------------------------------------------------------
// 7️⃣ Confirmation output.
// ------------------------------------------------------------
Console.WriteLine("✅ Document rewritten and saved as rewritten.docx");
```

### Γιατί Αυτό Λειτουργεί

- **LocalLargeLanguageModel** αφαιρεί τις λεπτομέρειες του HTTP, επιτρέποντάς σας να **call local llm** ακριβώς με τον ίδιο τρόπο όπως θα κάνατε σε ένα cloud OpenAI endpoint.  
- Η προτροπή που στέλνουμε (`Rewrite the following sentence in formal tone:`) είναι σύντομη, κάτι που βοηθά το μοντέλο να εστιάσει σε μια μετατροπή **rewrite sentence formal** αντί να προσθέτει άσχετο περιεχόμενο.  
- Καθαρίζοντας το `paragraph.Runs` και προσθέτοντας ένα νέο `Run`, εξασφαλίζουμε ότι το αρχείο Word περιέχει μόνο το νέο, επίσημο κείμενο.

## Βήμα 3: Εκτέλεση της Εφαρμογής

Βεβαιωθείτε ότι ο τοπικός διακομιστής LLM είναι ενεργός και ακούει στο `http://localhost:8000/v1`. Στη συνέχεια εκτελέστε:

```bash
dotnet run
```

Αν όλα είναι σωστά συνδεδεμένα, θα δείτε:

```
✅ Document rewritten and saved as rewritten.docx
```

Ανοίξτε το `rewritten.docx` – η πρώτη παράγραφος θα πρέπει τώρα να εμφανίζεται σε μια γυαλισμένη, επίσημη μορφή.

### Παράδειγμα Αναμενόμενης Εξόδου

| Αρχικό (ανεπίσημο) | Αναδιατυπωμένο (επίσημο) |
|---------------------|--------------------------|
| *Hey team, can we get the results ASAP?* | *Dear team, could you please provide the results at your earliest convenience?* |

Η μετατροπή δείχνει μια καθαρή μετατροπή **rewrite sentence formal**, ιδανική για επιχειρηματική επικοινωνία.

## Βήμα 4: Προσαρμογή της Προτροπής για Διαφορετικούς Τόνους

Αν χρειάζεστε μια πιο χαλαρή αναδιατύπωση, απλώς αλλάξτε την προτροπή:

```csharp
string revisedText = localLlm.GenerateText(
    $"Rewrite the following sentence in a casual tone:\n{paragraph.GetText()}");
```

Ανάλογα, μπορείτε να ζητήσετε από το μοντέλο να **rewrite paragraph formal** για μεγαλύτερα τμήματα, ή ακόμη και να συνοψίσει ολόκληρο το έγγραφο. Το ίδιο μοτίβο **call openai api** ισχύει – αλλάξτε την προτροπή, κρατήστε τον κώδικα πελάτη αμετάβλητο.

## Βήμα 5: Διαχείριση Ακραίων Περιστατικών

### Κενές Παράγραφοι

Μερικές φορές ένα αρχείο Word περιέχει κενές παραγράφους που μπέρδεψαν το LLM. Προστατέψτε εναντίον αυτού:

```csharp
if (string.IsNullOrWhiteSpace(paragraph.GetText()))
{
    Console.WriteLine("Skipped empty paragraph.");
}
else
{
    // generate and replace as before
}
```

### Μεγάλα Έγγραφα

Η επεξεργασία μιας αναφοράς 100‑σελίδων παράγραφο‑με‑παράγραφο μπορεί να είναι αργή. Ομαδοποιήστε τις κλήσεις:

```csharp
foreach (Paragraph p in doc.GetChildNodes(NodeType.Paragraph, true))
{
    // same rewrite logic for each paragraph
}
```

Να είστε ενήμεροι για τα όρια ταχύτητας στον τοπικό σας διακομιστή· ίσως χρειαστεί να προσθέσετε ένα μικρό `Thread.Sleep(200)` μεταξύ των κλήσεων.

## Βήμα 6: Ανάπτυξη στην Παραγωγή

1. Αντικαταστήστε το ψεύτικο API key με ένα πραγματικό αν μεταβείτε σε Azure OpenAI ή OpenAI SaaS.  
2. Αποθηκεύστε το endpoint και το κλειδί σε μεταβλητές περιβάλλοντος (`OPENAI_ENDPOINT`, `OPENAI_KEY`) και διαβάστε τα μέσω `Environment.GetEnvironmentVariable`.  
3. Προσθέστε logging (π.χ., Serilog) γύρω από το μπλοκ **call openai api** για να παρακολουθείτε τα payloads των αιτήσεων/απαντήσεων.

## Βήμα 7: Bonus – Προσθήκη Απλού UI

Αν προτιμάτε ένα γρήγορο front‑end Windows Forms:

```csharp
// inside a button click handler
var filePath = openFileDialog1.FileName;
Document doc = new Document(filePath);
// reuse the same rewriting logic...
```

---

## Συμπέρασμα

Μόλις δημιουργήσαμε ένα μικρό αλλά ισχυρό εργαλείο C# που **call openai api** (ή οποιοδήποτε συμβατό τοπικό LLM) για να **rewrite paragraph formal** μέσα σε ένα αρχείο Word. Με το **load word document**, στέλνοντας μια σύντομη προτροπή, και αντικαθιστώντας το κείμενο της παραγράφου, παίρνετε ένα γυαλισμένο έγγραφο σε δευτερόλεπτα.

Από εδώ μπορείτε:

- Επεκτείνετε το εργαλείο για να διαχειρίζεται πίνακες και εικόνες.  
- Ενσωματώστε το με SharePoint για αυτοματοποιημένη βελτίωση εγγράφων.  
- Πειραματιστείτε με άλλους τόνους—**rewrite sentence formal**, **rewrite sentence casual**, ή ακόμη **rewrite sentence persuasive**.

Δοκιμάστε το, προσαρμόστε τις προτροπές, και αφήστε το LLM να κάνει το σκληρό έργο για εσάς. Καλή προγραμματιστική!

## Σχετικά Μαθήματα

- [Create and Style a Word Document in Aspose.Words for .NET](/words/english/net/document-styling/apply-paragraph-style/)
- [Apply Paragraph Style In Word Document](/words/english/net/document-formatting/apply-paragraph-style/)
- [Move To Paragraph In Word Document](/words/english/net/add-content-using-documentbuilder/move-to-paragraph/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}