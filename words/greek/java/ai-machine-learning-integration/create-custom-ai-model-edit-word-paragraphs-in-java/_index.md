---
category: general
date: 2026-03-25
description: Δημιουργήστε προσαρμοσμένο μοντέλο AI για την επεξεργασία εγγράφων Word
  – μάθετε πώς να κάνετε το κείμενο πιο επίσημο, να αντικαταστήσετε το κείμενο παραγράφου
  και να ξαναγράψετε μια παράγραφο Word χρησιμοποιώντας το Aspose.Words AI.
draft: false
keywords:
- create custom ai model
- make text more formal
- replace paragraph text
- edit paragraph with ai
- rewrite word paragraph
language: el
og_description: Δημιουργήστε προσαρμοσμένο μοντέλο AI για την επεξεργασία εγγράφων
  Word. Μάθετε πώς να κάνετε το κείμενο πιο επίσημο, να αντικαταστήσετε το κείμενο
  παραγράφου και να ξαναγράψετε μια παράγραφο Word χρησιμοποιώντας το Aspose.Words
  AI.
og_title: Δημιουργία Προσαρμοσμένου Μοντέλου AI – Επεξεργασία Παραγράφων Word σε Java
tags:
- Aspose.Words
- Java
- AI integration
title: Δημιουργία Προσαρμοσμένου Μοντέλου AI – Επεξεργασία Παραγράφων Word σε Java
url: /el/java/ai-machine-learning-integration/create-custom-ai-model-edit-word-paragraphs-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία Προσαρμοσμένου Μοντέλου AI – Επεξεργασία Παραγράφων Word σε Java

Έχετε ποτέ χρειαστεί να **create custom AI model** που μπορεί να βελτιώσει μια παράγραφο μέσα σε ένα αρχείο Word; Ίσως έχετε μια σειρά συμβάσεων που ακούγονται λίγο πολύ ανεπίσημες, και θα θέλατε να κάνετε το κείμενο πιο επίσημο με μια μόνο γραμμή κώδικα. Τα καλά νέα είναι ότι μπορείτε να το κάνετε ακριβώς αυτό—χωρίς εξωτερικές υπηρεσίες, χωρίς βαριά SDKs, μόνο το Aspose.Words for Java και ένα OpenAI‑compatible endpoint.

Σε αυτό το tutorial θα περάσουμε από κάθε βήμα που απαιτείται για να **create custom AI model**, να το συνδέσουμε με έναν τοπικό διακομιστή LLM, και στη συνέχεια να το χρησιμοποιήσουμε για *replace paragraph text* με μια πιο επίσημη εκδοχή. Στο τέλος θα έχετε ένα εκτελέσιμο πρόγραμμα Java που **edit paragraph with AI**, ξαναγράφει μια παράγραφο Word, και αποθηκεύει το αποτέλεσμα ξανά στο δίσκο. Χωρίς περιττά, μόνο μια πρακτική λύση που μπορείτε να αντιγράψετε‑επικολλήσετε στο δικό σας έργο.

> **Τι θα χρειαστείτε**  
> • Java 17 ή νεότερη (ο κώδικας μεταγλωττίζεται με παλαιότερες εκδόσεις, αλλά η 17 είναι η ιδανική)  
> • Aspose.Words for Java 23.9 (ή η πιο πρόσφατη έκδοση)  
> • Ένας ενεργός OpenAI‑compatible LLM server (π.χ., Ollama, LocalAI) που ακούει στο `http://localhost:8000/v1`  
> • Ένα αρχείο Word εισόδου (`input.docx`) τοποθετημένο σε φάκελο που ελέγχετε  

Αν αναρωτιέστε *why bother building a custom model* αντί να καλέσετε απευθείας το OpenAI, η απάντηση είναι η ευελιξία: ελέγχετε το endpoint, μπορείτε να αλλάζετε μοντέλα χωρίς αλλαγές κώδικα, και κρατάτε τυχόν API keys εκτός του αποθετηρίου του κώδικά σας. Ας βουτήξουμε.

---

## Δημιουργία Προσαρμοσμένου Μοντέλου AI – Ρύθμιση και Διαμόρφωση

Πρώτα πρέπει να πούμε στο Aspose.Words πού βρίσκεται το LLM μας. Η κλάση `AiModelEndpoint` περιέχει το URL και το προαιρετικό API key. Επειδή χρησιμοποιούμε τοπικό διακομιστή, το κλειδί μπορεί να είναι κενή συμβολοσειρά, αλλά η παράμετρος είναι υποχρεωτική.

```java
import com.aspose.words.ai.*;

public class LlmDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Define the LLM endpoint (OpenAI‑compatible)
        AiModelEndpoint llmEndpoint = new AiModelEndpoint(
                "http://localhost:8000/v1",   // URL of your LLM server
                "my-api-key");                // API key if required
```

> **Pro tip:** Αν ποτέ μεταβείτε σε μοντέλο φιλοξενούμενο (π.χ., Azure OpenAI), απλώς αλλάξτε το URL και το κλειδί—δεν χρειάζονται άλλες αλλαγές κώδικα.

---

## Φόρτωση του Εγγράφου Word

Τώρα φέρνουμε το αρχείο προέλευσης στη μνήμη. Η `Document` μπορεί να διαβάσει `.docx`, `.doc`, `.rtf`, και πολλές άλλες μορφές, αλλά για αυτό το παράδειγμα παραμένουμε στο `.docx`.

```java
        // Step 2: Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

Βεβαιωθείτε ότι το `YOUR_DIRECTORY` δείχνει σε έναν πραγματικό φάκελο· διαφορετικά θα αντιμετωπίσετε `FileNotFoundException`. Σε μια πραγματική εφαρμογή μπορεί να περάσετε τη διαδρομή ως όρισμα γραμμής εντολών ή να την διαβάσετε από αρχείο ρυθμίσεων.

---

## Αρχικοποίηση του Προσαρμοσμένου Μοντέλου AI

Δημιουργούμε ένα `AiModel` τύπου `CUSTOM` και του δίνουμε το endpoint που ορίσαμε νωρίτερα. Αυτό λέει στο Aspose.Words να δρομολογεί όλες τις κλήσεις AI μέσω του δικού μας διακομιστή.

```java
        // Step 3: Create a custom AI model that uses the endpoint
        AiModel llmModel = new AiModel(AiModelType.CUSTOM, llmEndpoint);
```

Πίσω από τις σκηνές, το Aspose.Words δημιουργεί έναν μικρό πελάτη HTTP που επικοινωνεί με το LLM χρησιμοποιώντας το τυπικό σχήμα chat/completion του OpenAI. Γι' αυτό το endpoint πρέπει να είναι *OpenAI‑compatible*.

---

## Ανάκτηση και Επανεγγραφή της Πρώτης Παραγράφου

Εδώ είναι που πραγματικά **make text more formal**. Πιάνουμε την πρώτη παράγραφο, στέλνουμε το ακατέργαστο κείμενό της στο μοντέλο με ένα prompt, και λαμβάνουμε την επεξεργασμένη έκδοση.

```java
        // Step 4: Retrieve the first paragraph and ask the model to rewrite it
        Paragraph firstParagraph = document.getFirstSection()
                                            .getBody()
                                            .getParagraphs()
                                            .get(0);
        String rewrittenText = llmModel.editText(
                firstParagraph.getText(),
                "Make it more formal");
```

Το δεύτερο όρισμα (`"Make it more formal"`) είναι η οδηγία που δίνουμε στο μοντέλο. Μπορείτε να το αντικαταστήσετε με οποιαδήποτε εντολή—**replace paragraph text**, **summarize**, **translate**, κ.λπ. Η μέθοδος επιστρέφει μια απλή συμβολοσειρά, την οποία θα εισάγουμε αργότερα ξανά στο έγγραφο.

> **Why this works:** Η `editText` στέλνει ένα JSON payload όπως `{ \"model\": \"...\", \"messages\": [{ \"role\":\"user\", \"content\":\"<text>\\nMake it more formal\"}] }`. Το LLM βλέπει την αρχική παράγραφο και την οδηγία, και απαντά με το αναθεωρημένο κείμενο.

---

## Αντικατάσταση του Αρχικού Περιεχομένου Παραγράφου

Τώρα **replace paragraph text** μέσα στο μοντέλο αντικειμένων του Word. Καθαρίζουμε τυχόν υπάρχουσες `Run` (τα χαμηλού επιπέδου κομμάτια κειμένου) και εισάγουμε ένα νέο `Run` που περιέχει τη συμβολοσειρά που δημιουργήθηκε από το AI.

```java
        // Step 5: Replace the original paragraph content with the rewritten text
        firstParagraph.removeAllChildren();
        firstParagraph.appendChild(new Run(document, rewrittenText));
```

Προσέξτε να μην καλέσετε `firstParagraph.setText()`—αυτή η μέθοδος θα αφαιρέσει όλη τη μορφοποίηση. Η χρήση του `Run` διατηρεί το στυλ της παραγράφου (επικεφαλίδα, κουκίδα, κ.λπ.) ενώ αντικαθιστά τους πραγματικούς χαρακτήρες.

---

## Αποθήκευση του Επεξεργασμένου Εγγράφου

Τέλος, γράφουμε το τροποποιημένο έγγραφο ξανά στο δίσκο. Μπορείτε να αντικαταστήσετε το αρχικό αρχείο ή, όπως κάνουμε εδώ, να δημιουργήσετε ένα νέο αντίγραφο.

```java
        // Step 6: Save the edited document
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

Όταν ανοίξετε το `output.docx` θα πρέπει να δείτε ότι η πρώτη παράγραφος ακούγεται πλέον σημαντικά πιο επίσημη. Αν το LLM δεν ακολούθησε την οδηγία τέλεια, μπορείτε να προσαρμόσετε το prompt ή να δοκιμάσετε διαφορετική έκδοση μοντέλου.

---

## Πλήρες Παράδειγμα Εργασίας

Παρακάτω είναι το πλήρες πρόγραμμα—αντιγράψτε το στο `LlmDemo.java`, προσαρμόστε τις διαδρομές, και τρέξτε το με `javac` + `java`.

```java
import com.aspose.words.*;
import com.aspose.words.ai.*;

public class LlmDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Define the LLM endpoint (OpenAI‑compatible)
        AiModelEndpoint llmEndpoint = new AiModelEndpoint(
                "http://localhost:8000/v1",   // URL of your LLM server
                "my-api-key");                // API key if required

        // Step 2: Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // Step 3: Create a custom AI model that uses the endpoint
        AiModel llmModel = new AiModel(AiModelType.CUSTOM, llmEndpoint);

        // Step 4: Retrieve the first paragraph and ask the model to rewrite it
        Paragraph firstParagraph = document.getFirstSection()
                                            .getBody()
                                            .getParagraphs()
                                            .get(0);
        String rewrittenText = llmModel.editText(
                firstParagraph.getText(),
                "Make it more formal");

        // Step 5: Replace the original paragraph content with the rewritten text
        firstParagraph.removeAllChildren();
        firstParagraph.appendChild(new Run(document, rewrittenText));

        // Step 6: Save the edited document
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**Expected output:** Ανοίξτε το `output.docx` και θα δείτε την αρχική παράγραφο μετασχηματισμένη. Για παράδειγμα, μια ανεπίσημη πρόταση όπως “We’ll get the thing done soon.” μπορεί να γίνει “We shall complete the task promptly.” Η ακριβής διατύπωση εξαρτάται από το μοντέλο που χρησιμοποιείτε.

---

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

### Τι γίνεται αν το έγγραφό μου έχει πολλαπλές ενότητες;

Ο παραπάνω κώδικας αγγίζει μόνο την *πρώτη* παράγραφο της *πρώτης* ενότητας. Για **edit paragraph with AI** σε όλο το αρχείο, κάντε βρόχο μέσω `document.getSections()` και στη συνέχεια κάθε `section.getBody().getParagraphs()`. Θυμηθείτε να παραλείψετε τις κενές παραγράφους, διαφορετικά το LLM θα λάβει κενή συμβολοσειρά και δεν θα επιστρέψει τίποτα.

### Πώς να διαχειριστώ μεγάλες παραγράφους που υπερβαίνουν τα όρια token;

Τα περισσότερα LLM περιορίζουν την είσοδο σε περίπου 4 000 tokens. Αν μια παράγραφος είναι ασυνήθιστα μεγάλη, χωρίστε την σε μικρότερα κομμάτια πριν καλέσετε την `editText`. Μπορείτε να επαναχρησιμοποιήσετε την ίδια παρουσία `AiModel`; απλώς προσέξτε τα όρια ταχύτητας στον τοπικό σας διακομιστή.

### Μπορώ να χρησιμοποιήσω διαφορετική εντολή, όπως “summarize” ή “translate to French”;

Απολύτως. Το δεύτερο όρισμα της `editText` είναι ελεύθερης μορφής. Για μια σύνοψη μπορείτε να περάσετε `"Summarize in one sentence"`. Για μετάφραση, `"Translate to French, keep the tone formal"` λειτουργεί εξίσου καλά. Αυτή η ευελιξία σας επιτρέπει να **replace paragraph text** για πολλές περιπτώσεις χωρίς αλλαγή κώδικα.

### Διατηρεί το μοντέλο το στυλ της παραγράφου (γραμματοσειρές, χρώματα);

Επειδή αντικαθιστούμε μόνο το `Run` μέσα στο ίδιο αντικείμενο `Paragraph`, τα υπάρχοντα στυλ (επίπεδο επικεφαλίδας, λίστα με κουκίδες, εσοχή) παραμένουν αμετάβλητα. Αν χρειαστεί να αλλάξετε το ίδιο το στυλ, μπορείτε να χειριστείτε το `Paragraph.getParagraphFormat()` μετά την αντικατάσταση.

### Τι γίνεται αν ο διακομιστής LLM απαιτεί HTTPS με αυτο‑υπογεγραμμένο πιστοποιητικό;

`AiModelEndpoint` δέχεται URL με `https://`. Αν το πιστοποιητικό δεν είναι αξιόπιστο, θα πρέπει να ρυθμίσετε το SSL context της Java ώστε να το εμπιστεύεται, ή να τρέξετε τον διακομιστή με έγκυρο πιστοποιητικό. Αυτή η ρύθμιση είναι εκτός του πεδίου του tutorial αλλά τεκμηριώνεται καλά στους οδηγούς Java SSL.

---

## Συμβουλές για Ενσωμάτωση Έτοιμη για Παραγωγή

| Tip | Why it matters |
|-----|----------------|
| **Cache the endpoint** | Η επανδημιουργία του `AiModelEndpoint` σε κάθε αίτηση προσθέτει επιπλέον φόρτο. |
| **Batch edits** | Αν έχετε πολλές παραγράφους, στείλτε τις σε ένα μόνο αίτημα (π.χ., JSON array) για να μειώσετε την καθυστέρηση. |
| **Validate LLM output** | Πάντα ελέγξτε τη επιστρεφόμενη συμβολοσειρά για null ή κενές τιμές πριν την εισαγάγετε. |
| **Log prompts and responses** | Χρήσιμο για εντοπισμό σφαλμάτων και για συμμόρφωση όταν ξαναγράφετε νομικό κείμενο. |
| **Graceful fallback** | Αν το LLM είναι εκτός λειτουργίας, επανέλθετε στην αρχική παράγραφο ή σε μια απλή επανασυγγραφή με ευρετική μέθοδο. |

---

## Συμπέρασμα

Σας δείξαμε πώς να **create custom AI model** με το Aspose.Words, να το συνδέσετε με ένα OpenAI‑compatible endpoint, και στη συνέχεια να **edit paragraph with AI** για να **make text more formal**. Ακολουθώντας τα έξι βήματα—ορισμός του endpoint, φόρτωση του εγγράφου, αρχικοποίηση του μοντέλου,

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}