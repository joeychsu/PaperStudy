# L2-ARCTIC: A Non-Native English Speech Corpus
[paper link, Interspeech 2018](https://www.isca-speech.org/archive/Interspeech_2018/abstracts/1110.html)

## Abstract
* 這個 corpus 主要是設計來進行 voice conversion, accent conversion and mispronunciation detection 等研究
* 其中 10 位語者有的 first languages (L1s) 分別是 Hindi(印度), Korean, Mandarin, Spanish and Arabic，每種語言男女各一
* 每個語者參考 CMU ARCTIC prompts 錄製一個小時的語料(read speech)
* 每個語者有 150 句手動標記出三種類型的錯誤發音(substitutions, deletions and additions)

## Introduction
* 要建立 mispronunciation detection benchmark，發音錯誤的標記需要細緻到 phone-level。然而現有的 non-native English corpora：[Speech Accent Archive](http://accent.gmu.edu/) and [IDEA](https://www.dialectsarchive.com/) 並沒有達到此標準。
* 該 corpus 最終目的要達到 20 位語者(v4已經達到24位語者)，以下簡述語料的內容：

  ||description|
  |---|---|
  |Speech recordings:|每個語者超過 1 小時且音素平衡(phonetically-balanced)的短句|
  |Word level transcriptions:|用字正確的文本以及 forced-aligned word boundaries for each sentence|
  |Phoneme level transcriptions:|forced-aligned phoneme transcription for each sentence|
  |Manual annotations:| 每個語者挑約 150 句進行標記。其中 100 句每個語者相同(?)。另外 50 句因應不同 L1 來標記。標記內容包含正確的 word 以及 pheon boundaries, phone substitution, deletion, and addition errors|
