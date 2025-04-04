.. _lectures-content-llm-label-2023:

Краткий конспект лекций
=======================

Лекция 1. Установочная встреча.
-------------------------------

Знакомство с преподавателем. Общая структура курса.
Формирование итоговой оценки. Основные идеи, закладываемые в курс.
Место курса в образовательной программе. Структура лабораторной работы.
``LLM``. Типовые задачи ``NLP``, решаемые с помощью нейросетевых моделей.

Лекция 2. Датасеты в экосистеме HuggingFace.
--------------------------------------------

Экосистема HuggingFace. Поиск подходящего датасета.
Ключевые характеристики датасета: имя, вложенные датасеты,
названия сплитов и их количество, количество колонок, их структура и
необходимость при замере метрики. Установка необходимых библиотек.
Скачивание датасета с помощью ``load_dataset``. Получение необходимого сплита.
Перевод в формат ``DataFrame``. Основные задачи при обработке табличных значений.
Перегрузка протоколов в пользовательских классах
для поддержки поведения стандартных типов: итерируемость и взятие длины.

Лекция 3. Инференс языковых моделей.
------------------------------------

Структура языковой модели. Препроцессинг датасета. Токенизация входа. Инференс модели
через вызов как функции. Постпроцессинг результатов модели. Классификация: взятие
индекса логита с максимальным значением.

Лекция 4. Оценка качества работы языковых моделей.
--------------------------------------------------

Инференс генерационной модели. Паралелельная обработка нескольких семплов.
Упаковка семплов в батч с помощью ``DataLoader``. Автоматические метрики качества.
Библиотека ``evaluate``.
