.. _classification-label:

Classification
==============

Models
------

+---------------------------------------------------------------------+------+
| Model                                                               | Lang |
+=====================================================================+======+
| `cointegrated/rubert-tiny-toxicity <https                           | EN   |
| ://huggingface.co/cointegrated/rubert-tiny-toxicity>`__             |      |
+---------------------------------------------------------------------+------+
| `cointegrated/rubert-tiny2-cedr-emotion-detection <https://hugging  | RU   |
| face.co/cointegrated/rubert-tiny2-cedr-emotion-detection>`__        |      |
+---------------------------------------------------------------------+------+
| `papluca/xlm-roberta-base-language-detection <https://hugging       | RU   |
| face.co/papluca/xlm-roberta-base-language-detection>`__             |      |
+---------------------------------------------------------------------+------+
| `fabriceyhc/bert-base-uncased-ag_news <https://hugging              | EN   |
| face.co/fabriceyhc/bert-base-uncased-ag_news>`__                    |      |
+---------------------------------------------------------------------+------+
| `XSY/albert-base-v2-imdb-calssification <https://hugging            | EN   |
| face.co/XSY/albert-base-v2-imdb-calssification>`__                  |      |
+---------------------------------------------------------------------+------+
| `IlyaGusev/rubertconv_toxic_clf <https://hugging                    | EN   |
| face.co/IlyaGusev/rubertconv_toxic_clf>`__                          |      |
+---------------------------------------------------------------------+------+
| `aiknowyou/it-emotion-analyzer <https://hugging                     | RU   |
| face.co/aiknowyou/it-emotion-analyzer>`__                           |      |
+---------------------------------------------------------------------+------+
| `blanchefort/rubert-base-cased-sentiment-rusentiment <https://hugg  | RU   |
| ingface.co/blanchefort/rubert-base-cased-sentiment-rusentiment>`__  |      |
+---------------------------------------------------------------------+------+
| `tatiana-merz/turkic-cyrillic-classifier <https://hugging           | RU   |
| face.co/tatiana-merz/turkic-cyrillic-classifier>`__                 |      |
+---------------------------------------------------------------------+------+
| `s-nlp/russian_toxicity_classifier <https://hugging                 | RU   |
| face.co/s-nlp/russian_toxicity_classifier>`__                       |      |
+---------------------------------------------------------------------+------+

Datasets
--------

1. `OxAISH-AL-LLM/wiki_toxic <https://huggingface.co/datasets/OxAISH-AL-LLM/wiki_toxic/viewer/default/validation>`__

   1. **Lang**: EN
   2. **Rows**: 31915
   3. **Preprocess**:

      1. Drop column ``id``.
      2. Rename column ``label`` to ``target``.
      3. Rename column ``comment_text`` to ``source``.
      4. Reset indexes.

2. `seara/ru_go_emotions <https://huggingface.co/datasets/seara/ru_go_emotions>`__

   1. **Lang**: RU
   2. **Rows**: 5430
   3. **Preprocess**:

      1. Select ``simplified`` subset.
      2. Drop columns ``id`` and ``text``.
      3. Convert column ``labels`` to tuple.
      4. Remove from ``labels`` values ``0``, ``4``, ``5``, ``6``, ``7``, ``8``,
         ``10``, ``12``, ``15``, ``18``, ``21``, ``22``, ``23``.
      5. Rename column ``labels`` to ``target``.
      6. Rename column ``ru_text`` to ``source``.
      7. Group emotions and change numbers to words:

         1. Labels ``1``, ``13``, ``17``, ``20`` change to label ``1``.
         2. Labels ``9``, ``16``, ``24``, ``25`` change to label ``2``.
         3. Labels ``14``, ``19`` change to label ``3``.
         4. Labels ``2``, ``3`` change to label ``4``.
         5. Labels ``27`` change to label ``7``.
         6. Labels ``26`` change to label ``6``.
         7. Other labels to label ``8``.

      8. Delete duplicates in ``target``.
      9. Clean column ``source``.
      10. Reset indexes.

3. `papluca/language-identification <https://huggingface.co/datasets/papluca/language-identification>`__

   1. **Lang**: EN
   2. **Rows**: 10000
   3. **Preprocess**:

      1. Rename column ``labels`` to ``target``.
      2. Rename column ``text`` to ``source``.
      3. Map language abbreviation to label classes.
      4. Reset indexes.

4. `ag_news <https://huggingface.co/datasets/ag_news>`__

   1. **Lang**: EN
   2. **Rows**: 7600
   3. **Preprocess**:

      1. Rename column ``label`` to ``target``.
      2. Rename column ``text`` to ``source``.
      3. Reset indexes.

5. `imdb <https://huggingface.co/datasets/imdb>`__

   1. **Lang**: EN
   2. **Rows**: 25000
   3. **Preprocess**:

      1. Select ``test`` split.
      2. Rename column ``labels`` to ``target``.
      3. Rename column ``text`` to ``source``.
      4. Reset indexes.

6. `dair-ai/emotion <https://huggingface.co/datasets/dair-ai/emotion>`__

   1. **Lang**: EN
   2. **Rows**: 2000
   3. **Preprocess**:

      1. Select ``split`` subset.
      2. Select ``validation`` split.
      3. Rename column ``label`` to ``target``.
      4. Rename column ``text`` to ``source``.
      5. Reset indexes.

7. `blinoff/kinopoisk <https://huggingface.co/datasets/blinoff/kinopoisk>`__

   1. **Lang**: RU
   2. **Rows**: 36591
   3. **Preprocess**:

      1. Select ``validation`` split.
      2. Leave only ``content`` and ``grade3`` columns.
      3. Rename column ``grade3`` to ``target``.
      4. Rename column ``content`` to ``source``.
      5. Delete empty rows in dataset.
      6. Map ``target`` with class labels.
      7. Reset indexes.

8. `blinoff/healthcare_facilities_reviews <https://huggingface.co/datasets/blinoff/healthcare_facilities_reviews>`__

   1. **Lang**: RU
   2. **Rows**: 70597
   3. **Preprocess**:

      1. Select ``validation`` split.
      2. Leave only ``content`` and ``sentiment`` columns.
      3. Rename column ``sentiment`` to ``target``.
      4. Rename column ``content`` to ``source``.
      5. Map ``target`` with class labels.

.. note:: In combination with a multiclass model ``blanchefort/rubert-base-cased-sentiment-rusentiment``
          it is necessary to bring the ``neutral`` class to the ``negative`` class at the prediction stage.

9. `tatiana-merz/cyrillic_turkic_langs <https://huggingface.co/datasets/tatiana-merz/cyrillic_turkic_langs>`__

   1. **Lang**: RU
   2. **Rows**: 9000
   3. **Preprocess**:

      1. Select ``validation`` split.
      2. Rename column ``label`` to ``target``.
      3. Rename column ``text`` to ``source``.
      4. Map ``target`` with class labels.

10. `s-nlp/ru_paradetox_toxicity <https://huggingface.co/datasets/s-nlp/ru_paradetox_toxicity>`__

   1. **Lang**: RU
   2. **Rows**: 6350
   3. **Preprocess**:

      1. Rename column ``toxic`` to ``target``.
      2. Rename column ``neutral`` to ``source``.
      3. Delete duplicates in dataset.
      4. Map ``target`` with class labels.
      5. Reset indexes.

11. `d0rj/rudetoxifier_data <https://huggingface.co/datasets/d0rj/rudetoxifier_data>`__

   1. **Lang**: RU
   2. **Rows**: 163187
   3. **Preprocess**:

      1. Select ``train`` split.
      2. Rename column ``toxic`` to ``target``.
      3. Rename column ``text`` to ``source``.

12. `s-nlp/ru_non_detoxified <https://huggingface.co/datasets/s-nlp/ru_non_detoxified>`__

   1. **Lang**: RU
   2. **Rows**: 20900
   3. **Preprocess**:

      1. Rename column ``reasons`` to ``target``.
      2. Rename column ``toxic_comment`` to ``source``.
      3. Rename ``{"toxic_content":true}`` label to ``1``
         and ``{"not_toxic":true}`` label to ``0``.
      4. Remove irrelevant rows in dataset.
      5. Delete duplicates in dataset.
      6. Reset indexes.

13. `Arsive/toxicity_classification_jigsaw <https://huggingface.co/datasets/Arsive/toxicity_classification_jigsaw>`__

   1. **Lang**: EN
   2. **Rows**: 6490
   3. **Preprocess**:

      1. Select ``validation`` split.
      2. Drop column ``id``, ``severe_toxic``, ``obscene``,
         ``threat``, ``insult``, ``identity_hate``.
      3. Rename column ``toxic`` to ``target``.
      4. Rename column ``comment_text`` to ``source``.
      5. Reset indexes.

14. `s-nlp/en_paradetox_toxicity <https://huggingface.co/datasets/s-nlp/en_paradetox_toxicity>`__

   1. **Lang**: EN
   2. **Rows**: 26507
   3. **Preprocess**:

      1. Select ``train`` split.
      2. Rename column ``toxic`` to ``target``.
      3. Rename column ``comment`` to ``source``.
      4. Reset indexes.


Supervised Fine-Tuning (SFT) Parameters
---------------------------------------

.. note:: Set the parameter ``target_modules=["query", "key", "value", "dense"]`` for the
          `XSY/albert-base-v2-imdb-calssification <https://hugging
          face.co/XSY/albert-base-v2-imdb-calssification>`__ model as SFT parameter.

Metrics
-------

-  F1-score
