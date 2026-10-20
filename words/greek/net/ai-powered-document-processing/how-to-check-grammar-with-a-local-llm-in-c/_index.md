---
category: general
date: 2026-03-19
description: Μάθετε πώς να ελέγχετε τη γραμματική στο Word χρησιμοποιώντας ένα τοπικό
  LLM, να καταχωρίσετε το μοντέλο και να αποθηκεύσετε τα διορθωμένα έγγραφα—όλα σε
  ένα ενιαίο σεμινάριο C#.
draft: false
keywords:
- how to check grammar
- set up local llm
- check grammar in word
- how to register llm
- how to save corrected
language: el
og_description: Πώς να ελέγξετε τη γραμματική στο Word χρησιμοποιώντας ένα τοπικό
  LLM, να καταχωρίσετε το μοντέλο και να αποθηκεύσετε τα διορθωμένα έγγραφα—οδηγός
  βήμα‑προς‑βήμα.
og_title: Πώς να ελέγξετε τη γραμματική με ένα τοπικό LLM σε C#
tags:
- Aspose.Words
- AI
- C#
title: Πώς να ελέγξετε τη γραμματική με ένα τοπικό LLM σε C#
url: /el/net/ai-powered-document-processing/how-to-check-grammar-with-a-local-llm-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να ελέγξετε τη γραμματική με ένα τοπικό LLM σε C#

Αναρωτηθήκατε ποτέ **πώς να ελέγξετε τη γραμματική** σε ένα έγγραφο Word χωρίς να στέλνετε το κείμενό σας στο cloud; Δεν είστε μόνοι. Πολλοί προγραμματιστές θέλουν την ιδιωτικότητα ενός αυτο‑φιλοξενούμενου μοντέλου ενώ εξακολουθούν να λαμβάνουν προτάσεις με τεχνητή νοημοσύνη. Σε αυτόν τον οδηγό θα περάσουμε από την καταχώριση ενός προσαρμοσμένου LLM, τη διαμόρφωση του Aspose.Words για χρήση του, και τελικά **πώς να αποθηκεύσετε τα διορθωμένα** αρχεία—όλα σε απλό C#.

Θα καλύψουμε επίσης τις λεπτομέρειες **setup local llm**, θα σας δείξουμε **πώς να καταχωρίσετε llm** endpoints, και θα επιδείξουμε τα ακριβή βήματα για **check grammar in word** έγγραφα. Στο τέλος θα έχετε ένα εκτελέσιμο δείγμα που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο .NET.

## Προαπαιτήσεις

Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε:

- .NET 6+ SDK (ο κώδικας λειτουργεί σε .NET Core και .NET Framework)
- Visual Studio 2022 ή VS Code με επεκτάσεις C#
- Aspose.Words for .NET (v24.12 ή νεότερο) – μπορείτε να το κατεβάσετε από το NuGet
- Ένα τοπικά τρέχον LLM που υποστηρίζει το συμβατό με OpenAI API (π.χ., Ollama στη θύρα 11434)

> **Pro tip:** Αν χρησιμοποιείτε Ollama, η εντολή `ollama serve` θα δημιουργήσει αυτόματα το endpoint `http://localhost:11434/api/generate`.

## Βήμα 1 – Πώς να καταχωρίσετε llm: Προσθήκη του προσαρμοσμένου μοντέλου στο Aspose.Words

Το πρώτο που χρειάζεται είναι να ενημερώσουμε το Aspose.Words για το **local llm** μας. Αυτό γίνεται μία φορά κατά την εκκίνηση της εφαρμογής.

```csharp
using Aspose.Words;
using Aspose.Words.AI;

// Register a custom LLM endpoint – no API key required for local servers
AiEngine.RegisterModel(
    modelName: "local-llm",                         // identifier we’ll reference later
    endpoint: new Uri("http://localhost:11434/api/generate"),
    apiKey: null,                                   // local server doesn’t need a key
    provider: AiProvider.Custom);
```

**Γιατί είναι σημαντικό:** Καταχωρίζοντας το μοντέλο δίνετε στο Aspose.Words ένα ονομαστικό αναγνωριστικό (`"local-llm"`). Αργότερα, όταν καλέσουμε το `CheckGrammar`, η βιβλιοθήκη ξέρει ακριβώς ποιο endpoint να προσεγγίσει. Η παράλειψη αυτού του βήματος αναγκάζει τη βιβλιοθήκη να επιστρέψει στην ενσωματωμένη cloud υπηρεσία, κάτι που αναιρεί το σκοπό ενός ιδιωτικού LLM.

## Βήμα 2 – Φόρτωση του εγγράφου Word που θέλετε να αναλύσετε

Τώρα φέρνουμε το αρχείο στη μνήμη. Μπορείτε να δείξετε σε οποιοδήποτε αρχείο `.docx`, `.doc`, ή ακόμη και `.rtf`.

```csharp
// Replace YOUR_DIRECTORY with the actual folder path on your machine
Document sourceDocument = new Document("YOUR_DIRECTORY/input.docx");

// Quick sanity check – print the number of paragraphs we just loaded
Console.WriteLine($"Loaded document with {sourceDocument.GetChildNodes(NodeType.Paragraph, true).Count} paragraphs.");
```

**Τι συμβαίνει:** Το `Document` είναι το βασικό αντικείμενο μοντέλου του Aspose.Words. Αναλύει το αρχείο και δημιουργεί ένα δέντρο κόμβων (παράγραφοι, πίνακες, εικόνες κ.λπ.). Αυτό επιτρέπει στη μηχανή AI να στοχεύει συγκεκριμένα εύρη κειμένου για ανάλυση γραμματικής.

## Βήμα 3 – Διαμόρφωση επιλογών ελέγχου γραμματικής (set up local llm)

Εδώ συνδέουμε το προηγουμένως καταχωρισμένο μοντέλο με τη λειτουργία ελέγχου γραμματικής.

```csharp
AiGrammarCheckOptions grammarOptions = new AiGrammarCheckOptions
{
    Model = "local-llm",               // references the name we used in RegisterModel
    // Optional: you can tweak temperature, maxTokens, etc. if your LLM supports them
    // Temperature = 0.7,
    // MaxTokens = 512
};
```

**Γιατί εκθέτουμε αυτές τις επιλογές:** Διαφορετικά LLM έχουν διαφορετική συμπεριφορά. Με το `Model`, το Aspose.Words σας επιτρέπει να εναλλάσσετε μεταξύ τοπικού μοντέλου και cloud‑βασισμένου χωρίς να αλλάξετε άλλο κώδικα. Αυτή η ευελιξία είναι ουσιώδης όταν **set up local llm** περιβάλλοντα για συμμόρφωση ή offline σενάρια.

## Βήμα 4 – Εκτέλεση του AI‑οδηγούμενου ελέγχου γραμματικής (check grammar in word)

Με όλα συνδεδεμένα, ο πραγματικός έλεγχος γραμματικής είναι μια μόνο γραμμή.

```csharp
// This mutates sourceDocument in place, inserting suggestions and corrections
sourceDocument.CheckGrammar(grammarOptions);
Console.WriteLine("Grammar check completed.");
```

**Πίσω από τη σκηνή:** Το Aspose.Words εξάγει κάθε πρόταση, τη στέλνει στο endpoint του LLM, λαμβάνει ένα JSON payload με προτεινόμενες διορθώσεις, και στη συνέχεια εφαρμόζει αυτές τις διορθώσεις πίσω στο δέντρο του εγγράφου. Η διαδικασία εκτελείται συγχρονισμένα εδώ για απλότητα· μπορείτε επίσης να καλέσετε την ασύγχρονη υπερφόρτωση `CheckGrammarAsync` αν προτιμάτε μη‑αποκλειστικό I/O.

## Βήμα 5 – Πώς να αποθηκεύσετε τα διορθωμένα έγγραφα

Αφού το AI ολοκληρώσει τη δουλειά του, θα θέλετε να αποθηκεύσετε τις αλλαγές.

```csharp
// Save the corrected file – you can change the format to PDF, HTML, etc.
sourceDocument.Save("YOUR_DIRECTORY/checked.docx");
Console.WriteLine("Corrected document saved as checked.docx");
```

**Τι να περιμένετε:** Ανοίξτε το `checked.docx` στο Word και θα δείτε τα προβλήματα γραμματικής επισημασμένα (ή αυτόματα διορθωμένα, ανάλογα με το `AiGrammarCheckOptions`). Αν ενεργοποιήσατε την παρακολούθηση, θα δείτε επίσης σημάδια αναθεώρησης.

## Πλήρες Παράδειγμα Λειτουργίας

Συνδυάζοντας τα παραπάνω, εδώ είναι μια έτοιμη για εκτέλεση console εφαρμογή:

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.AI;

class Program
{
    static void Main()
    {
        // 1️⃣ Register the local LLM
        AiEngine.RegisterModel(
            modelName: "local-llm",
            endpoint: new Uri("http://localhost:11434/api/generate"),
            apiKey: null,
            provider: AiProvider.Custom);

        // 2️⃣ Load the source document
        string inputPath = "YOUR_DIRECTORY/input.docx";
        Document sourceDocument = new Document(inputPath);
        Console.WriteLine($"Loaded: {inputPath}");

        // 3️⃣ Set up grammar‑check options (using the local model)
        AiGrammarCheckOptions grammarOptions = new AiGrammarCheckOptions
        {
            Model = "local-llm"
        };

        // 4️⃣ Perform the AI‑driven grammar check
        sourceDocument.CheckGrammar(grammarOptions);
        Console.WriteLine("Grammar analysis finished.");

        // 5️⃣ Save the corrected document
        string outputPath = "YOUR_DIRECTORY/checked.docx";
        sourceDocument.Save(outputPath);
        Console.WriteLine($"Corrected file saved to: {outputPath}");
    }
}
```

**Αναμενόμενη έξοδος στην κονσόλα:**

```
Loaded: YOUR_DIRECTORY/input.docx
Grammar analysis finished.
Corrected file saved to: YOUR_DIRECTORY/checked.docx
```

Ανοίξτε το `checked.docx` και θα πρέπει να δείτε τις βελτιώσεις γραμματικής να έχουν εφαρμοστεί αυτόματα.

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

| Ερώτηση | Απάντηση |
|----------|--------|
| *Τι γίνεται αν το LLM μου απαιτεί API key;* | Περάστε το κλειδί στο `apiKey` στο `RegisterModel`. Ο ίδιος κώδικας λειτουργεί τόσο για υπηρεσίες με κλειδί όσο και χωρίς. |
| *Μπορώ να χρησιμοποιήσω διαφορετική μορφή αρχείου;* | Απόλυτα. Το `Document.Save` δέχεται `.pdf`, `.html`, `.txt`, κ.λπ. Απλώς αλλάξτε την επέκταση. |
| *Τι γίνεται αν το LLM επιστρέψει σφάλμα;* | Τυλίξτε το `CheckGrammar` σε try/catch· ελέγξτε το `AiException` για λεπτομέρειες. Συχνά είναι timeout—σκεφτείτε να αυξήσετε το `grammarOptions.Timeout`. |
| *Η λειτουργία είναι thread‑safe;* | Το βήμα καταχώρισης είναι παγκόσμιο και πρέπει να εκτελείται μία φορά κατά την εκκίνηση. Οι επόμενες κλήσεις `CheckGrammar` είναι ασφαλείς για παράλληλη εκτέλεση εφόσον κάθε μία χρησιμοποιεί το δικό της `Document` instance. |

## Επόμενα Βήματα

Τώρα που ξέρετε **πώς να ελέγξετε τη γραμματική** χρησιμοποιώντας ένα **local llm**, μπορείτε να εξερευνήσετε:

- **Batch processing**: Επανάληψη σε φάκελο εγγράφων και εκτέλεση της ίδιας αλυσίδας.
- **Custom prompts**: Προσαρμόστε το payload του αιτήματος ορίζοντας `grammarOptions.PromptTemplate` για ελέγχους ειδικού στυλ.
- **Ενσωμάτωση με ASP.NET Core**: Εκθέστε ένα API endpoint που δέχεται ανεβασμένα `.docx` αρχεία, τρέχει τον έλεγχο γραμματικής, και επιστρέφει το διορθωμένο αρχείο.

Αυτές οι επεκτάσεις σας επιτρέπουν να χτίσετε μια πλήρως εξοπλισμένη πλατφόρμα “grammar‑as‑a‑service” χωρίς ποτέ να αφήσετε τα δεδομένα σας εκτός των εγκαταστάσεών σας.

---

*Καλό coding! Αν συναντήσετε προβλήματα, αφήστε ένα σχόλιο παρακάτω—είμαι στη διάθεσή σας για να βοηθήσω με τη ρύθμιση.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}