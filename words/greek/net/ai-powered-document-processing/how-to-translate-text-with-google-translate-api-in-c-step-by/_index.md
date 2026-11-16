---
category: general
date: 2026-11-15
description: Μάθετε πώς να μεταφράζετε κείμενο με το Google σε C#. Αυτό το σεμινάριο
  παρουσιάζει ένα παράδειγμα του Google Translate, διαχείριση πολλαπλών γλωσσών και
  βέλτιστες πρακτικές.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to translate text
- translate text with google
- google translate example
- google translate tutorial
- translate multiple languages
language: el
lastmod: 2026-11-15
og_description: Πώς να μεταφράσετε κείμενο με το Google σε C# χρησιμοποιώντας ένα
  πλήρες παράδειγμα Google Translate. Ακολουθήστε αυτό το σεμινάριο για να μεταφράζετε
  πολλαπλές γλώσσες με ασφάλεια.
og_image_alt: Console output showing translated text from English to French using
  Google Translate API
og_title: Πώς να μεταφράσετε κείμενο με το Google Translate API σε C# – γρήγορος οδηγός
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to translate text with Google in C#. This tutorial shows
    a Google Translate example, handling multiple languages and best practices.
  headline: How to translate text with Google Translate API in C# – step‑by‑step guide
  type: TechArticle
- description: Learn how to translate text with Google in C#. This tutorial shows
    a Google Translate example, handling multiple languages and best practices.
  name: How to translate text with Google Translate API in C# – step‑by‑step guide
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 SDK or later (the code compiles with .NET Core and .NET Framework).
      * A Google Cloud account with the **Cloud Translation API** enabled. * Basic
      familiarity with C# and console applications.'
  - name: Handling language detection
    text: 'If you need to know the source language, the response object contains `DetectedSourceLanguage`:'
  - name: Translating large documents
    text: The API supports up to 30 KB per request. For larger texts, split the content
      into chunks, translate each chunk, and then concatenate the results. Keep sentence
      boundaries intact to avoid awkward phrasing.
  - name: Rate‑limiting and quotas
    text: Google enforces per‑minute request limits. Implement a retry policy with
      exponential back‑off to respect quota limits and avoid `429 Too Many Requests`
      errors.
  type: HowTo
- questions:
  - answer: Yes. Use the `Format` parameter (`"text"` or `"html"`) when calling `TranslateText`.
      The SDK exposes this via the `TranslateText` overload that accepts a `TranslateTextRequest`.
    question: Can I translate a whole HTML page?
  - answer: The API returns an error. Validate language codes against the list returned
      by `client.ListSupportedLanguages()` before making a request.
    question: What if a language isn’t supported?
  - answer: 'Google bills per character translated. Estimate costs using the pricing
      page and consider caching frequent translations. --- ## Conclusion You now know
      **how to translate text** in C# using the official Google Translate API. The
      tutorial covered a **Google translate example**, demonstrated **transla'
    question: Does the API charge per character?
  type: FAQPage
tags:
- Google Cloud
- C#
- Translation API
title: Πώς να μεταφράσετε κείμενο με το Google Translate API σε C# – οδηγός βήμα‑προς‑βήμα
url: /el/net/ai-powered-document-processing/how-to-translate-text-with-google-translate-api-in-c-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να μεταφράσετε κείμενο με το Google Translate API σε C# – βήμα‑βήμα οδηγός

Αν χρειάζεστε **how to translate text** σε μια εφαρμογή .NET, το Google Cloud Translation API προσφέρει μια αξιόπιστη, ανεξάρτητη από τη γλώσσα λύση. Σε αυτό το tutorial θα δείτε ένα **Google Translate example** που μεταφράζει μια απλή συμβολοσειρά, επεκτείνεται σε **translate multiple languages**, και ακολουθεί τις βέλτιστες πρακτικές για κλειδιά API και διαχείριση σφαλμάτων.

Θα αποκτήσετε ένα έτοιμο προς εκτέλεση πρόγραμμα κονσόλας C#, μια σαφή κατανόηση του **translate text with Google**, και την αυτοπεποίθηση να προσαρμόσετε τον κώδικα για μεγαλύτερα έργα.

## Τι καλύπτει αυτό το tutorial

* Δημιουργία ενός έργου Google Cloud και λήψη κλειδιού API.  
* Εγκατάσταση του πακέτου NuGet `Google.Cloud.Translation.V2`.  
* Γραφή καθαρού, επαναχρησιμοποιήσιμου κώδικα που **how to translate text** χρησιμοποιώντας το επίσημο SDK.  
* Επέκταση της λύσης ώστε να **translate multiple languages** σε μία κλήση.  
* Κοινά προβλήματα και συμβουλές για υλοποιήσεις παραγωγικής ποιότητας.

### Προαπαιτούμενα

* .NET 6.0 SDK ή νεότερο (ο κώδικας μεταγλωττίζεται με .NET Core και .NET Framework).  
* Λογαριασμός Google Cloud με ενεργοποιημένο το **Cloud Translation API**.  
* Βασική εξοικείωση με C# και εφαρμογές κονσόλας.  

---

## Βήμα 1: Εγκατάσταση της βιβλιοθήκης πελάτη Google Cloud Translation

Η επίσημη βιβλιοθήκη πελάτη αφαιρεί τις κλήσεις HTTP και διαχειρίζεται τον έλεγχο ταυτότητας για εσάς.

```bash
dotnet add package Google.Cloud.Translation.V2
```

Η εκτέλεση της εντολής προσθέτει το πακέτο `Google.Cloud.Translation.V2` στο έργο σας, παρέχοντάς σας πρόσβαση στην κλάση `TranslationClient` που χρησιμοποιείται σε όλο τον οδηγό.

> **Γιατί αυτό το βήμα είναι σημαντικό** – Η χρήση του SDK αποφεύγει την χειροκίνητη κατασκευή αιτημάτων, μειώνει τα σφάλματα και εξασφαλίζει ότι είστε ευθυγραμμισμένοι με την πιο πρόσφατη έκδοση του API της Google.

## Βήμα 2: Δημιουργία ενός επαναχρησιμοποιήσιμου βοηθού μετάφρασης

Η ενσωμάτωση της λογικής μετάφρασης σε μια static κλάση κάνει τον κώδικα επαναχρησιμοποιήσιμο και απομονώνει τη διαχείριση του κλειδιού API.

```csharp
using Google.Cloud.Translation.V2;
using System;

namespace GoogleTranslateDemo
{
    /// <summary>
    /// Provides simple methods to translate text using the Google Cloud Translation API.
    /// </summary>
    public static class Translator
    {
        /// <summary>
        /// Translates a single string into the specified target language.
        /// </summary>
        /// <param name="sourceText">The text you want to translate.</param>
        /// <param name="targetLanguage">ISO‑639‑1 language code (e.g., "fr" for French).</param>
        /// <param name="apiKey">Your Google Cloud API key.</param>
        /// <returns>The translated text.</returns>
        public static string Translate(string sourceText, string targetLanguage, string apiKey)
        {
            // Initialise the client with the provided API key.
            var client = TranslationClient.CreateFromApiKey(apiKey);

            // Perform the translation. The API automatically detects the source language.
            var response = client.TranslateText(sourceText, targetLanguage);
            return response.TranslatedText;
        }

        /// <summary>
        /// Translates a collection of texts into several languages at once.
        /// </summary>
        /// <param name="sourceTexts">Array of strings to translate.</param>
        /// <param name="targetLanguages">Array of ISO‑639‑1 codes (e.g., "es", "de").</param>
        /// <param name="apiKey">Your Google Cloud API key.</param>
        /// <returns>A dictionary keyed by language code containing the translated results.</returns>
        public static Dictionary<string, string[]> TranslateMultiple(string[] sourceTexts,
                                                                    string[] targetLanguages,
                                                                    string apiKey)
        {
            var client = TranslationClient.CreateFromApiKey(apiKey);
            var result = new Dictionary<string, string[]>();

            foreach (var lang in targetLanguages)
            {
                var translations = client.TranslateTexts(sourceTexts, lang);
                result[lang] = translations.Select(t => t.TranslatedText).ToArray();
            }

            return result;
        }
    }
}
```

> **Γιατί επιστρέφουμε ένα dictionary** – Όταν χρειάζεται να **translate multiple languages**, η οργάνωση των αποτελεσμάτων κατά κωδικό γλώσσας κάνει την επεξεργασία των επόμενων βημάτων απλή.

## Βήμα 3: Δημιουργία της εφαρμογής κονσόλας που χρησιμοποιεί τον βοηθό

Παρακάτω υπάρχει ένα πλήρες `Program.cs` που δείχνει τόσο τη μετάφραση ενός μόνο κειμένου όσο και τη μαζική μετάφραση.

```csharp
using System;
using GoogleTranslateDemo; // Namespace from the helper class

class Program
{
    static void Main()
    {
        // ---- Single translation (Google Translate example) ----
        string sourceText = "Hello, world!";
        string targetLanguage = "fr"; // French
        string apiKey = "YOUR_GOOGLE_API_KEY"; // Replace with your actual key

        try
        {
            string translated = Translator.Translate(sourceText, targetLanguage, apiKey);
            Console.WriteLine($"[Single] English → French: {translated}");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"Translation failed: {ex.Message}");
        }

        // ---- Translate multiple languages (translate multiple languages) ----
        string[] texts = { "Good morning", "How are you?" };
        string[] languages = { "es", "de", "ja" }; // Spanish, German, Japanese

        try
        {
            var batchResult = Translator.TranslateMultiple(texts, languages, apiKey);
            foreach (var kvp in batchResult)
            {
                Console.WriteLine($"\n[Batch] Language: {kvp.Key}");
                for (int i = 0; i < texts.Length; i++)
                {
                    Console.WriteLine($"  {texts[i]} → {kvp.Value[i]}");
                }
            }
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"Batch translation failed: {ex.Message}");
        }
    }
}
```

**Αναμενόμενη έξοδος κονσόλας**

```
[Single] English → French: Bonjour le monde!

[Batch] Language: es
  Good morning → Buenos días
  How are you? → ¿Cómo estás?

[Batch] Language: de
  Good morning → Guten Morgen
  How are you? → Wie geht es Ihnen?

[Batch] Language: ja
  Good morning → おはようございます
  How are you? → お元気ですか？
```

> **Γιατί τα μπλοκ try/catch;** – Σφάλματα δικτύου, όρια ποσοστώσεων ή ένα μη έγκυρο κλειδί API προκαλούν εξαιρέσεις. Η διαχείρισή τους με χάρη βελτιώνει την εμπειρία του χρήστη και διατηρεί τη σταθερότητα της εφαρμογής.

## Βήμα 4: Ασφάλιση του κλειδιού API σας

Η ενσωμάτωση του κλειδιού API στον κώδικα, όπως φαίνεται παραπάνω, είναι αποδεκτή για μια γρήγορη επίδειξη αλλά όχι για παραγωγή. Ακολουθήστε αυτές τις πρακτικές:

* Αποθηκεύστε το κλειδί σε μια μεταβλητή περιβάλλοντος (`GOOGLE_API_KEY`) και διαβάστε το κατά την εκτέλεση:
  ```csharp
  string apiKey = Environment.GetEnvironmentVariable("GOOGLE_API_KEY");
  ```
* Χρησιμοποιήστε **Google Application Default Credentials** αντί για κλειδί API όταν εκτελείτε στο Google Cloud (App Engine, Cloud Run, κ.λπ.).
* Περιορίστε το κλειδί στο Translation API στην κονσόλα Google Cloud και περιορίστε τη χρήση σε συγκεκριμένες διευθύνσεις IP ή referrers.

## Βήμα 5: Επέκταση της λύσης για πραγματικές περιπτώσεις

### Διαχείριση ανίχνευσης γλώσσας

Αν χρειάζεστε να γνωρίζετε τη γλώσσα προέλευσης, το αντικείμενο απόκρισης περιέχει `DetectedSourceLanguage`:

```csharp
var response = client.TranslateText(sourceText, targetLanguage);
Console.WriteLine($"Detected source: {response.DetectedSourceLanguage}");
```

### Μετάφραση μεγάλων εγγράφων

Το API υποστηρίζει έως 30 KB ανά αίτηση. Για μεγαλύτερα κείμενα, χωρίστε το περιεχόμενο σε τμήματα, μεταφράστε κάθε τμήμα και στη συνέχεια ενώστε τα αποτελέσματα. Διατηρήστε τα όρια προτάσεων αμετάβλητα για να αποφύγετε αμήχανες φράσεις.

### Ρύθμιση ρυθμού (rate‑limiting) και ποσοστώσεις

Η Google επιβάλλει όρια αιτήσεων ανά λεπτό. Εφαρμόστε πολιτική επανάληψης με εκθετική αύξηση (exponential back‑off) για να σεβαστείτε τα όρια ποσοστώσεων και να αποφύγετε σφάλματα `429 Too Many Requests`.

```csharp
// Example using Polly (install Polly via NuGet)
var policy = Policy
    .Handle<Google.Api.Gax.Rpc.ResourceExhaustedException>()
    .WaitAndRetryAsync(3, attempt => TimeSpan.FromSeconds(Math.Pow(2, attempt)));

await policy.ExecuteAsync(() => client.TranslateTextAsync(...));
```

---

## Συχνές ερωτήσεις και ειδικές περιπτώσεις

**Q: Μπορώ να μεταφράσω ολόκληρη μια σελίδα HTML;**  
A: Ναι. Χρησιμοποιήστε την παράμετρο `Format` (`"text"` ή `"html"`) όταν καλείτε το `TranslateText`. Το SDK εκθέτει αυτό μέσω του υπερφορτωμένου `TranslateText` που δέχεται ένα `TranslateTextRequest`.

**Q: Τι γίνεται αν μια γλώσσα δεν υποστηρίζεται;**  
A: Το API επιστρέφει σφάλμα. Επικυρώστε τους κωδικούς γλώσσας έναντι της λίστας που επιστρέφει το `client.ListSupportedLanguages()` πριν κάνετε αίτηση.

**Q: Χρεώνει το API ανά χαρακτήρα;**  
A: Η Google χρεώνει ανά χαρακτήρα που μεταφράζεται. Εκτιμήστε το κόστος χρησιμοποιώντας τη σελίδα τιμολόγησης και σκεφτείτε την αποθήκευση (caching) συχνών μεταφράσεων.

---

## Συμπέρασμα

Τώρα γνωρίζετε **how to translate text** σε C# χρησιμοποιώντας το επίσημο Google Translate API. Το tutorial κάλυψε ένα **Google translate example**, επέδειξε **translate multiple languages**, και τόνισε πρακτικές έτοιμες για παραγωγή όπως η ασφάλεια κλειδιού API και η διαχείριση σφαλμάτων. Με την επαναχρησιμοποίηση του βοηθού `Translator`, μπορείτε να ενσωματώσετε τη μετάφραση σε οποιαδήποτε υπηρεσία .NET, εφαρμογή επιφάνειας εργασίας ή μικροϋπηρεσία.

**Επόμενα βήματα**

- Εξερευνήστε το **Google Translate tutorial** για προχωρημένα χαρακτηριστικά όπως γλωσσάρια (glossaries) και προσαρμοσμένα μοντέλα.  
- Συνδυάστε αυτόν τον κώδικα με ASP.NET Core για να δημιουργήσετε ένα πολυγλωσσικό web API.  
- Πειραματιστείτε με μαζική μετάφραση αρχείων CSV για αυτοματοποίηση των αγωγών τοπικοποίησης.

Καλή προγραμματιστική, και απολαύστε τη δημιουργία παγκοσμίως προσβάσιμων εφαρμογών!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετα χαρακτηριστικά του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [μεταφράστε docx στα γαλλικά με Aspose.Words και Google API](/words/english/net/ai-powered-document-processing/translate-docx-to-french-with-aspose-words-and-google-api/)
- [Πώς να αποθηκεύσετε μεταφρασμένο έγγραφο Word σε C# με Google AI](/words/english/net/ai-powered-document-processing/how-to-save-translated-word-document-in-c-with-google-ai/)
- [Μεταφράστε συμβολοσειρά στα Ισπανικά σε C# με Aspose.Words AI](/words/english/net/ai-powered-document-processing/translate-string-to-spanish-in-c-with-aspose-words-ai/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}