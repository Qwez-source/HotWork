### Шанс вопроса: 14%

ROC (Receiver Operating Characteristic) кривая и AUC (Area Under the Curve) являются важными метриками для оценки производительности бинарных классификаторов. 

ROC-кривая строится с использованием различных пороговых значений, где по оси X откладывается доля ложноположительных результатов (False Positive Rate), а по оси Y — доля истинноположительных результатов (True Positive Rate). Это позволяет визуально оценить баланс между ошибками первого и второго рода.

AUC представляет собой площадь под ROC-кривой. Значение AUC интерпретируется следующим образом:
- AUC = 1: Модель идеально различает классы, без ошибок (идеальный случай).
- AUC между 0.5 и 1: Модель демонстрирует хорошую способность различать классы.
- AUC = 0.5: Модель не лучше случайного угадывания.
- AUC ниже 0.5: Модель хуже случайного угадывания в оценке классов.

Пример расчета AUC на языке Python с использованием библиотеки scikit-learn:

```python
from sklearn.metrics import roc_auc_score, roc_curve
import matplotlib.pyplot as plt
from sklearn.linear_model import LogisticRegression
from sklearn.datasets import make_classification
import numpy as np

# Создание синтетического датасета для классификации
X, y = make_classification(n_samples=100, n_features=20, random_state=42)

# Обучение логистической регрессии
model = LogisticRegression()
model.fit(X, y)

# Предсказание вероятностей для каждого класса
y_pred_prob = model.predict_proba(X)[:, 1]

# Расчет ROC-кривой и AUC
fpr, tpr, thresholds = roc_curve(y, y_pred_prob)
auc_score = roc_auc_score(y, y_pred_prob)

# Визуализация ROC-кривой и расчета AUC
plt.plot(fpr, tpr, label=f'AUC = {auc_score:.2f}')
plt.xlabel('False Positive Rate')
plt.ylabel('True Positive Rate')
plt.title('ROC Curve')
plt.legend()
plt.show()
```

Этот код создает синтетический датасет, обучает логистическую регрессию и вычисляет ROC-кривую и AUC для оценки производительности модели.