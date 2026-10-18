# Граф ключевых слов публикаций arXiv: LLM hallucination

Вся работа находится в ноутбуке `lab.ipynb`.

## Структура

```
arxiv_graph_lab/
├── lab.ipynb          ноутбук с лабораторной (пункты 1–9)
├── requirements.txt   зависимости
├── .venv/             готовое виртуальное окружение
└── data/              создаётся при запуске: arxiv_papers.csv (скачанные статьи)
```

## Запуск в PyCharm

1. File → Open → выбрать папку `arxiv_graph_lab`.
2. Интерпретатор: Settings → Project → Python Interpreter → Add Interpreter →
   Add Local Interpreter → Select existing → `.venv\Scripts\python.exe`
   (обычно PyCharm подхватывает `.venv` сам).
3. Открыть `lab.ipynb` и выполнить все ячейки (Run All).

Если окружения `.venv` нет или оно сломалось:

```
py -m venv .venv
.venv\Scripts\python -m pip install -r requirements.txt
```

Если в вашей версии PyCharm ноутбуки не открываются, запустите Jupyter из терминала PyCharm:

```
.venv\Scripts\jupyter notebook lab.ipynb
```

## Доступ к arXiv

Первая ячейка с данными скачивает 400 статей через arXiv API (≈15 секунд) и сохраняет их в
`data/arxiv_papers.csv`. Если `export.arxiv.org` заблокирован провайдером, нужен VPN или
рабочий профиль Zapret. После первого скачивания интернет больше не нужен.
NLTK при первом запуске докачивает словари `stopwords` и `wordnet`.

## Результаты

Интерпретация кластеров, центральностей и выводы написаны в ноутбуке по данным из
`data/arxiv_papers.csv`. Если скачать данные заново, состав статей может измениться,
и числа в тексте нужно будет сверить с новым выводом.
