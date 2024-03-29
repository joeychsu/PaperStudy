# L2-ARCTIC: A Non-Native English Speech Corpus
[paper link, Interspeech 2018](https://www.isca-speech.org/archive/Interspeech_2018/abstracts/1110.html)

## Abstract
* 這個 corpus 主要是設計來進行 voice conversion, accent conversion and mispronunciation detection 等研究
* 其中 10 位語者有的 first languages (L1s) 分別是 Hindi(印度), Korean, Mandarin, Spanish and Arabic，每種語言男女各一
* 每個語者參考 [CMU ARCTIC prompts](http://www.festvox.org/cmu_arctic/) 錄製一個小時的語料(read speech)
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
* 跟 mispronunciation detection 較相關的 corpora：

  |corpora|description|
  |---|---|
  |[CU-CHLOE](http://www1.se.cuhk.edu.hk/~hccl/publications/pub/2014_PID3298385_LK.pdf)|只有 Chinese learners of English 的語音以及 error tags，且未公開|
  |[COLSEC](https://en.wikipedia.org/wiki/Shanghai_Foreign_Language_Education_Press)|只有 Chinese learners of English 的語音以及 error tags|
  |[ISLE](http://www.lrec-conf.org/proceedings/lrec2000/pdf/313.pdf)|僅供學術使用，且著重在 German and Italian learners of English，有發音錯誤標記|
  |[SingaKids-Mandarin](https://www.semanticscholar.org/paper/SingaKids-Mandarin%3A-Speech-Corpus-of-Singaporean-Chen-Tong/8491d159467ef495049a9792592124537787ed0a)|內容豐富，但著重在新加坡孩童學習普通話的 error pattern|
  
## Corpus curation procedure
* 為何要挑選這些 L1s (Hindi1, Korean, Mandarin, Spanish and Arabic)? 因為這些不同母語的英文學習者的口音差異大，可以提供不同的挑戰。
* 不同母語者的 error pattern 不盡相同，但寫得好複雜偶不是唸語文系的偶看不下去
* 語者都是來自 Iowa State University 的學生，年齡分佈在 22~43，平均 29 歲。每個學生皆有托福網路測驗的成績量化英語程度(參考[Table 1](https://github.com/joeychsu/PaperStudy/blob/master/table/L2-ARCTIC%EF%BC%9AA%20Non-Native%20English%20Speech%20Corpus%EF%BC%9Btable1.png))。

  <img src="./table/L2-ARCTIC：A Non-Native English Speech Corpus；table1.png" width="400"/>

* 該語料使用 CMU ARCTIC prompts 1,132 句，選擇這份 prompt 有兩個原因：
  1. 他是音素平衡(phonetically-balanced)的，phonemes, diphones and triphones 的 coverage 為 100%, 79.6% and 13.7%
  2. ARCTIC corpus 被證實在 語音合成 以及 voice conversion 等任務都表現得不錯 (猜測是 phone coverage 很好的意思)
* 該語料是在安靜的房間使用 Samson C03U microphone + Earamble studio microphone pop filter(麥克風防風罩) 等設備錄製。麥克風距離語者 20cm 避免噴麥(air puffing)。若是語句有嚴重不順暢或偏離 prompt 則會要求重錄。

  <img src="./extra/Samson C03U microphone.png" width="300"/>
  <img src="./extra/Earamble studio microphone pop filter.jpg" width="300"/>
  
* 使用 Montreal forced-aligner 來產生 phone boundaries，並以 PRAAT’s TextGrid 格式來儲存 (參考[Figure 1](https://github.com/joeychsu/PaperStudy/blob/master/figure/L2-ARCTIC%EF%BC%9AA%20Non-Native%20English%20Speech%20Corpus%EF%BC%9Bfigure1.png))

<img src="./figure/L2-ARCTIC：A Non-Native English Speech Corpus；figure1.png" width="500"/>

* 每個語者皆標記 100 句 common set，另外 50 句的錯誤為 L1-dependent，使用 [ARPAbet phoneme](https://en.wikipedia.org/wiki/ARPABET) 來標注以及 phonetic transcriptions 以及 error tags
* 為確保高品質的標注，標註者為 3 位 語言與科技相關的 PhD 學生

## Corpus statistics
* 整個 dataset 有 11,026 句，11.2 小時，平均每個語者 67 分鐘，每句平均 3.7 秒。約有 97,000 word segments，平均每句 9 個 words，總共約有 349,000 phone segments。
* 專家標記的結果有 1,499 句，其中含有 5,199 substitutions, 1,048 deletions and 497 additions (phone-level)，[Figure 3](https://github.com/joeychsu/PaperStudy/blob/master/figure/L2-ARCTIC%EF%BC%9AA%20Non-Native%20English%20Speech%20Corpus%EF%BC%9Bfigure3.png) 顯示個母語者較常發生的 error pattern。

  <img src="./figure/L2-ARCTIC：A Non-Native English Speech Corpus；figure3.png" width="800"/>

## Mispronunciation detection evaluation
* 使用傳統的 [GOP](https://github.com/guanlongzhao/kaldi-gop) 來建立 Mispronunciation detection benchmark
* Acoustic Model 使用 [Kaldi's Librispeech training script](https://github.com/kaldi-asr/kaldi/tree/master/egs/librispeech) 訓練，AM 架構為 GMM(tri6b)，使用 Librispeech (native English speech) 作為訓練語料。該 AM 基於 3-gram LM 在 clean test set WER 約 8%。
 * 實驗 based on GOP score 且 phone-independent thresholding 來畫出 Recall-Precision Curve ([Figure 4](https://github.com/joeychsu/PaperStudy/blob/master/figure/L2-ARCTIC%EF%BC%9AA%20Non-Native%20English%20Speech%20Corpus%EF%BC%9Bfigure4.png))

  <img src="./figure/L2-ARCTIC：A Non-Native English Speech Corpus；figure4.png" width="500"/>

* 初步的實驗著重在 substitution errors，GOP 目前無法處理 additions / deletions error
* 1,499 個有標記的語句，其中 206 句用來偵測 threshold(phone-independent) 的 range，剩下的 1,293 句作為 test data。測試資料有 41,353 個 phone segments，其中 4,415(10.7%) 個有發生 substitution errors。
* log GOP threshold 設置在 0 ~ -16 之間，step size 為 0.1 來畫出 Curve ([Figure 4](https://github.com/joeychsu/PaperStudy/blob/master/figure/L2-ARCTIC%EF%BC%9AA%20Non-Native%20English%20Speech%20Corpus%EF%BC%9Bfigure4.png))。當 threshold = -4.2，Precision 與 Recall 相同 (0.29)
