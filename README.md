# PDA_vectorization_text

**Описание кейса:** Датасет IMDB — набор данных по классификации эмоциональной окраски отзывов.   
Тренировочная и тестовая части IMDB достаточно большие — каждая состоит из 25 000 примеров.   
Для доступа к нему мы используем библиотеку datasets — она содержит в себе много интересных текстовых датасетов.

**Задача:** предсказать по тексту отзыва к фильму, положительный ли он. Сравнить различные модели машинного обучения по метрике ***accuracy***

**Метрика:** accuracy 
Accuracy рассчитывает долю правильных классификаций, и определяется как соотношение всех истинных результатов и суммы всех комбинаций матрицы ошибок.

**Этапы:**
1. Baseline: LogisticRegression() + векторизатор TF-IDF
2. LinearSVM + векторизатор TF-IDF
3. LogisticRegression() + N-грамма в векторизаторе TF-IDF
4. LinearSVM + N-грамма в векторизаторе TF-IDF

**Результаты:**
1. Baseline: LogisticRegression() + векторизатор TF-IDF
```
Время выполнения: 3.68 s
Значение метрики accuracy: 0.88316
```
2. LinearSVM + векторизатор TF-IDF
```
Время выполнения:  21min 24s
Значение метрики accuracy: 0.88256
```
3. LogisticRegression() + N-грамма в векторизаторе TF-IDF
```
Время выполнения: 4.23 s
Значение метрики accuracy: 0.89436
```
4. LinearSVM + N-грамма в векторизаторе TF-IDF
```
Время выполнения: 40min 24s
Значение метрики accuracy: 0.89872
```
**Выводы:** Наилучшее качество классификации негативных и положительных отзывов показала модель линейной регресии LinearSVM с использованием n-gram в токенизаторе TF-IDF с показателем метрики accuracy = 0.89872 т.е. примерно в ~90% случаев модель правильно угадала окраску отзыва.  
Выигрыш по сравнению с Baseline составил ~1,5%.
Однако, если проанализировать затраты времени на работу модели, то становится очевидно, что такой прогресс явился следствием почти 660 кратного увеличения временных затрат.   
Учитывая, что качество предсказания достаточно высокое, а речь не идет об предсказании болезней или вещей, представляющих угрозу безопасности человека, то использование данной модели представляется нецелесообразным.  
Так же как и 2 вариант(LinearSVM + векторизатор TF-IDF) с меньшим, чем у Baseline качеством и значительным увеличением времени выполнения.  
3 вариант реализации(LogisticRegression() + N-грамма в векторизаторе TF-IDF) хоть и дает выигрыш в качестве предсказания на 1.1%, однако времени затрачивает 6.7% больше.   
Следовательно вариант реализации модели Baseline(LogisticRegression()) представляется наиболее оптимальным.
