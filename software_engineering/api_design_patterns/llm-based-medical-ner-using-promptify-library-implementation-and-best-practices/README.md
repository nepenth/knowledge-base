**Source:** [https://twitter.com/i/web/status/1934273537113526435](https://twitter.com/i/web/status/1934273537113526435)
**Original Post Date:** 2025-06-17 15:43:46

# LLM-Based Medical NER Using Promptify Library: Implementation and Best Practices

## Introduction
This article explores the implementation of domain-specific Named Entity Recognition (NER) for medical text using the `promptify` library. We'll examine how to leverage Large Language Models via OpenAI's API to extract structured information from complex medical sentences, focusing on accuracy in specialized domains where traditional NLP approaches may fall short.

## Library Setup and Dependencies

The `promptify` library provides a streamlined approach to implementing NER tasks through LLM integration. Ensure you have the necessary dependencies installed via pip:

API authentication is crucial for secure interaction with OpenAI's models, requiring proper environment configuration.

```bash
pip install promptify
pip install openai
```

## Code Implementation and Execution

The implementation begins with importing necessary components from the `promptify` library. This allows for easy integration of OpenAI's capabilities with NER functionality.

Model initialization requires an API key, which should be managed securely to prevent unauthorized access.

```python
from promptify import OpenAI
from promptify import Prompter

sentence = 'The patient is a 93-year-old female with...' # Medical text
model = OpenAI(api_key)
nlp_prompter = Prompter(model=model)
```

## NER Task Execution and Output Analysis

The NER task is executed using a Jinja template, specifying the medical domain for specialized entity recognition.

Output structure consists of entity-type pairs, providing structured information suitable for downstream processing.

```python
result = nlp_prompter.fit('ner.jinja',
             domain='medical',
             text_input=sentence)
```

- Entities are categorized into types like 'Age', 'Medical Condition', and 'Symptom'
- Domain context (Medicine, Geriatrics) provides additional classification layers

## Best Practices and Optimization

Implement rate limiting to manage API costs effectively.

Cache results for frequently processed medical texts to improve performance.

> **Note/Tip:** Always validate entity extraction accuracy against domain experts

> **Note/Tip:** Consider implementing fallback mechanisms for cases where LLM confidence is low

## Key Takeaways

- LLM-based NER provides superior accuracy in specialized domains compared to traditional models.
- Proper template design and domain specification are crucial for accurate entity extraction.
- Implement robust error handling and rate limiting for production use.

## Conclusion
The `promptify` library offers a powerful approach to medical text analysis through LLM integration. By understanding the implementation details, output structure, and best practices, developers can effectively leverage this technology for specialized NLP applications.

## External References

- [Promptify Library Documentation](https://promptify.readthedocs.io/)
- [OpenAI API Reference](https://platform.openai.com/docs/api-reference)


## Media

**Image Description:** The image shows a Python code snippet that demonstrates the use of a Natural Language Processing (NLP) library, specifically for Named Entity Recognition (NER), in a medical domain. The code is written in a syntax-highlighted text editor, with different colors used to distinguish keywords, strings, and other elements. Below is a detailed breakdown of the image:

### **Main Subject**
The main subject of the image is a Python script that uses the `promptify` library to perform Named Entity Recognition (NER) on a medical sentence. The script interacts with the OpenAI API to process the text and extract relevant entities.

### **Technical Details**

#### **1. Imports**
- The script begins with imports from the `promptify` library:
  ```python
  from promptify import import OpenAI
  from promptify import import Prompter
  ```
  - `OpenAI`: This is likely a class or function from the `promptify` library that interfaces with the OpenAI API.
  - `Prompter`: This is another class or function from the same library, used to create and manage prompts for NLP tasks.

#### **2. Sentence Definition**
- A long medical sentence is defined as a string variable named `sentence`:
  ```python
  sentence = 'The patient is a 93-year-old female with a medical history of chronic right hip pain, osteoporosis, hypertension, depression, and chronic atrial fibrillation admitted for evaluation and management of severe nausea and vomiting and urinary tract infection.'
  ```
  - The sentence contains various medical terms, symptoms, and conditions, making it suitable for NER tasks in the medical domain.

#### **3. Model Initialization**
- An instance of the `OpenAI` class is created, requiring an `api_key`:
  ```python
  model = OpenAI(api_key)
  ```
  - `api_key`: This is a placeholder for the actual API key needed to authenticate with the OpenAI API.

#### **4. Prompter Initialization**
- A `Prompter` object is created, initialized with the `model`:
  ```python
  nlp_prompter = Prompter(model=model)
  ```
  - This object will be used to perform NLP tasks, such as NER.

#### **5. NER Task Execution**
- The `fit` method of the `Prompter` object is called to perform NER:
  ```python
  result = nlp_prompter.fit('ner.jinja',
                            domain='medical',
                            text_input=sentence)
  ```
  - **Parameters:**
    - `'ner.jinja'`: This specifies the template or model to use for NER. The `.jinja` extension suggests it might be a Jinja2 template.
    - `'medical'`: The domain is set to `'medical'`, indicating that the NER task is focused on medical entities.
    - `sentence`: The input text to be processed.

#### **6. Output**
- The output of the NER task is displayed as a list of dictionaries:
  ```python
  [{'E': '93-year-old', 'T': 'Age'},
   {'E': 'chronic right hip pain', 'T': 'Medical Condition'},
   {'E': 'osteoporosis', 'T': 'Medical Condition'},
   {'E': 'hypertension', 'T': 'Medical Condition'},
   {'E': 'depression', 'T': 'Medical Condition'},
   {'E': 'chronic atrial fibrillation', 'T': 'Medical Condition'},
   {'E': 'severe nausea and vomiting', 'T': 'Symptom'},
   {'E': 'urinary tract infection', 'T': 'Medical Condition'},
   {'Branch': 'Medicine', 'Internal Medicine Group': 'Geriatrics'}]
  ```
  - **Structure of Output:**
    - Each dictionary in the list represents an entity (`E`) and its corresponding type (`T`).
    - For example:
      - `'E': '93-year-old'` and `'T': 'Age'` indicates that "93-year-old" is recognized as an age entity.
      - `'E': 'chronic right hip pain'` and `'T': 'Medical Condition'` indicates that "chronic right hip pain" is recognized as a medical condition.
    - The last dictionary provides additional context, indicating the branch of medicine (`Medicine`) and the specific group (`Geriatrics`).

### **Color Coding**
- The syntax highlighting in the image uses the following colors:
  - **Green**: Keywords and function names (e.g., `from`, `import`, `OpenAI`, `Prompter`).
  - **Orange/Yellow**: Strings (e.g., the sentence and output entities).
  - **White**: Variables and other code elements.
  - **Lighter Text**: Comments or less prominent elements.

### **Summary**
The image demonstrates a Python script using the `promptify` library to perform Named Entity Recognition (NER) on a medical sentence. The script interacts with the OpenAI API to extract medical entities such as age, symptoms, and conditions. The output is a structured list of entities and their types, along with additional medical context. The use of syntax highlighting enhances readability and emphasizes the structure of the code.
![The image shows a Python code snippet that demonstrates the use of a Natural Language Processing NLP...](./media/image_1.jpg)