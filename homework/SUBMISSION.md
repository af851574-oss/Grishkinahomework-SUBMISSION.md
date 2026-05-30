# Домашнее задание RAG

## Ссылка на репозиторий с заданием
- **Repo URL:** `https://github.com/af851574-oss/Grishkina_lab_korpdata`

## Автор
- **ФИО / ник:** Анна Гришкина / Grishkinahomework

## Комментарий

### Реализация
- Полный RAG pipeline: ingestion → chunking → TF-IDF → retrieval → demo-answer → Streamlit UI.
- Данные: 10 синтетических жалоб на финансовые продукты.
- Индекс: TF-IDF (max_features=5000), 10 чанков, 87 признаков.
- Поиск: косинусная близость, top_k=5, порог отказа 0.1.
- Отказ по ключевым словам: `безработица`, `инфляция`, `ВВП`, `погода`, `борщ`.

### Демо-вопросы и ответы
| Вопрос | Ожидание | Результат |
|--------|----------|-----------|
| ипотека Citibank | Ответ из чанка (doc_id=0) | ✅ score 0.31 |
| Wells Fargo закрытие счёта | Ответ из чанка (doc_id=1) | ✅ score >0 |
| безработица | Отказ | ✅ |
| как приготовить борщ | Отказ | ✅ |

### Тесты
- 3 теста: `test_chunking_basic`, `test_retriever_loads`, `test_search_returns_list` – все проходят.

### Запуск
```bash
python scripts/build_index.py
streamlit run app/main.py
