Exercise 1:

```python
def normalize_text_to_tokens(text):
    text = unicode_to_ascii(text)
    spacy_nlp = spacy.load('en')
    doc = spacy_nlp(text)
    lemmatized_tokens = [token.lemma_ if '-' not in token.lemma_ else token.text for token in doc]
    return lemmatized_tokens
```

Exercise 2:

```python
import json

train_data = []

with open('data/doccano_annots.json', 'r') as fptr:
    for line in fptr:
        annot = json.loads(line.rstrip())
        tuple_data = ()
        for _ in annot:
            label = annot['labels']
            new_label = []
            for lab in label:
                new_label.append(tuple(lab))
        tuple_data = (annot['text'], {'entities': new_label})
        train_data.append(tuple_data)
print(train_data)
```