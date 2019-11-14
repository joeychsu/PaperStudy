# Machine Learning for Recommender systems — Part 1 (algorithms, evaluation and cold start)
[reference, Medium 2018.](https://medium.com/recombee-blog/machine-learning-for-recommender-systems-part-1-algorithms-evaluation-and-cold-start-6f696683d0ed)
本篇主要翻譯該文章，做個筆記

## 作者簡介
* 作者 Pavel Kordík 的公司 [Recombee](https://www.recombee.com/) 提供一個自動推薦的引擎，他可以依照各種商業需求(Media, E-Commerce, Job boards, Travel, Real Estate, Education)做調整。

## Algorithms
* 在推薦系統中大致可分為兩種分法：content based and collaborative filtering methods，應用上是兩者都會用到
  1. Content based 的方法是計算 item attributes 的相似度
  2. collaborative methods 是計算 互動(interactions) 的相似度
* 下面大多討論的是 collaborative methods，因為這樣的方法較有機會讓使用者挖掘到與自己過去感興趣的項目較不同的新發現。
