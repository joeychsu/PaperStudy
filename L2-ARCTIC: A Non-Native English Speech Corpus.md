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

## The need for a new L2 English corpus
* 現有的 non-native English corpora 涵蓋 native languages and speakers 的範圍很廣，但是每個語者只有 short paragraph ([Speech Accent Archive](http://accent.gmu.edu/)) 或是 short free speech task ([IDEA](https://www.dialectsarchive.com/))。而且錄音有非常吵雜的環境噪音，這非常不適合用於 voice/accent conversion 等任務。
* 另外 [Wildcat](http://faculty.wcas.northwestern.edu/ann-bradlow/publications/2010/2010_VanEngenetal.pdf), [LDC2007S08](https://catalog.ldc.upenn.edu/) and [NUFAESD](http://www.tessabent.com/interlanguage.pdf) datasets 在每個 non-native speaker 的錄音數量都很有限，且 [LDC2007S08](https://catalog.ldc.upenn.edu/) 還要收費。
* 跟 mispronunciation detection 叫相關的 corpora：

  |corpora|description|
  |---|---|
  |[CU-CHLOE](http://www1.se.cuhk.edu.hk/~hccl/publications/pub/2014_PID3298385_LK.pdf)|只有 Chinese learners of English 的語音以及 error tags，且未公開|
  |[COLSEC](https://en.wikipedia.org/wiki/Shanghai_Foreign_Language_Education_Press)|只有 Chinese learners of English 的語音以及 error tags|
  |[ISLE](http://www.lrec-conf.org/proceedings/lrec2000/pdf/313.pdf)|僅供學術使用，且著重在 German and Italian learners of English，有發音錯誤標記|
  |[SingaKids-Mandarin](https://www.semanticscholar.org/paper/SingaKids-Mandarin%3A-Speech-Corpus-of-Singaporean-Chen-Tong/8491d159467ef495049a9792592124537787ed0a)|內容豐富，但著重在新加坡孩童學習普通話的 error pattern|
  
## Corpus curation procedure
* 為何要挑選這些 L1s (Hindi1, Korean, Mandarin, Spanish and Arabic)? 因為這些不同母語的英文學習者的口音差異大，可以提供不同的挑戰。

