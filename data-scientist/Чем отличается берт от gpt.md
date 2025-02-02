### Шанс вопроса: 14%

Bert и GPT (Generative Pre-trained Transformer) — это два различных подхода к обработке естественного языка, разработанные компанией Google для обучения моделей глубокого обучения. Вот основные отличия между ними:

1. **Архитектура**:
   - **BERT (Bidirectional Encoder Representations from Transformers)** использует архитектуру трансформаторов, которая обрабатывает текст в обе стороны, что позволяет учитывать контекст предшествующих и последующих слов. Это делает BERT особенно эффективным для задач, требующих понимания целостного контекста (например, токенизация, классификация текстов, извлечение информации).
   - **GPT (Generative Pre-trained Transformer)**, с другой стороны, является однонаправленной моделью, которая обрабатывает текст в одном направлении. Однако последние версии GPT могут быть модифицированы для использования как би- или многонаправленные модели, что делает их более гибкими в применении к различным задачам.

2. **Область применения**:
   - **BERT** предназначен в основном для задач обработки естественного языка и извлечения информации, таких как токенизация текста, классификация текстов, вопросно-ответные системы, аннотирование ссылок и т.д.
   - **GPT** в первую очередь ориентирован на генерацию текста, включая создание ответов на вопросы, завершение предложений и порождение новых текстов, что делает его полезным для автоматической генерации контента.

3. **Тренировочные данные**:
   - **BERT** обычно обучается на огромном корпусе немаркированных текстов (например, книг, википедии) с использованием метода маскированного языкового моделирования.
   - **GPT**, с другой стороны, может быть обучен на меньших корпусах или даже на задачах конкретных текстов (например, новостные статьи), что делает его более специализированным подходом.

4. **Примеры кода**:
   - Пример использования BERT для токенизации и классификации:
     ```python
     from transformers import BertTokenizer, BertForSequenceClassification
     tokenizer = BertTokenizer.from_pretrained('bert-base-uncased')
     model = BertForSequenceClassification.from_pretrained('bert-base-uncased')
     
     # Пример токенизации и классификации текста
     text = "This is a sample sentence for BERT tokenization and classification."
     tokens = tokenizer(text, return_tensors='pt', truncation=True)
     outputs = model(**tokens)
     ```
   - Пример использования GPT для генерации ответа:
     ```python
     from transformers import GPT2LMHeadModel, GPT2Tokenizer
     
     tokenizer = GPT2Tokenizer.from_pretrained('gpt2')
     model = GPT2LMHeadModel.from_pretrained('gpt2')
     
     # Пример генерации ответа на вопрос
     input_text = "What is the capital of France?"
     inputs = tokenizer(input_text, return_tensors='pt')
     outputs = model.generate(**inputs)
     print(tokenizer.decode(outputs[0], skip_special_tokens=True))
     ```

В целом, BERT и GPT представляют собой мощные инструменты для обработки естественного языка, каждый из которых имеет свои особенности и области применения. Выбор между ними зависит от конкретной задачи и доступных данных.