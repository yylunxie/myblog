---
title: "機器學習常見問題：監督式學習和非監督式學習的差異？"
date: "2025-02-02T17:04:15+08:00"
tags:
  [
    "AI",
    "Machine Learning",
    "Supervised Learning",
    "Unsupervised Learning",
    "Semi-supervised Learning",
  ]
slug: aws_aif_qanda
draft: true
cover:
  image: "<image path/url>" # image path/url
  alt: "<alt text>" # alt text
  caption: "<text>" # display caption under cover
  relative: false # when using page bundles set this to true
  hidden: true # only hide on current single page
---

在 AI 世界有太多太多名詞，對於小白來說特別容易感到沒有方向。不論是經典的機器學習或是深度學習，當提到訓練方法時，大致上可以分成三種：

1. **監督式學習 Supervised Learning**
2. **非監督式學習 Unsupervised Learning**
3. **半監督式學習 Semi-supervised Learning**

你可能會好奇：「為什麼叫監督式學習？難道我要在旁邊盯著模型學習嗎？」其實，「監督」的意思是指提供標註資料，而「非監督」則是讓模型自行尋找模式，今天這篇文章就會幫你釐清以上的問題。

# 監督式學習 Supervised Learning

> 監督式學習的目標是希望透過大量的 **標註資料（Labeled Data）** 訓練模型，使模型能夠從輸入預測對應的輸出。

舉例來說，現在你想要透過機器學習模型辨是貓或是狗，因此你收集了大量貓和狗的照片作為訓練資料，另外你還對照片加上註解，說明這張照片是貓還是狗，因此你的訓練資料即為「標註資料」。只要有足夠的標註資料，經過訓練的模型就能正確的回答你這張照片是貓或是狗。因此在此例中，輸入即為照片，而輸出即為是貓還是狗的回答。

# 非監督式學習 Unsupervised Learning

> 非監督式學習使用 **未標記的資料** 來進行訓練，目標是讓模型自行發現數據中的模式與結構，例如將相似的資料點分成不同群組。

同樣以動物來舉例，現在你有許多動物的照片如圖一，並且你想知道具體可以分成幾種分類，因此你將所有照片丟給機器學習模型進行學習。最後，模型告訴你可以分成貓、狗和魚三類，這就是一個非監督式學習經典的分群應用。

# 半監督式學習 Semi-supervised Learning

> 半監督式學習介於監督與非監督學習之間，它使用少量的標註資料與大量未標註的資料來訓練模型。

# 總結

| 類型         | 標註資料              | 應用範圍                       |
| ------------ | --------------------- | ------------------------------ |
| 監督式學習   | 需要大量標註資料      | 影像分類、語音辨識、數值預測   |
| 非監督式學習 | 不需要標註資料        | 分群、降維、異常偵測           |
| 半監督式學習 | 少量標註 + 大量未標註 | 自然語言處理、大型影像數據分析 |

# 參考資料

- [機器學習任務：監督學習/半監督學習/無監督學習](https://u9534056.medium.com/%E6%A9%9F%E5%99%A8%E5%AD%B8%E7%BF%92%E4%BB%BB%E5%8B%99-%E7%9B%A3%E7%9D%A3%E5%AD%B8%E7%BF%92-%E5%8D%8A%E7%9B%A3%E7%9D%A3%E5%AD%B8%E7%BF%92-%E7%84%A1%E7%9B%A3%E7%9D%A3%E5%AD%B8%E7%BF%92-9b75972f91d6)

- [監督式學習與非監督式學習之間有何差異？](https://aws.amazon.com/tw/compare/the-difference-between-machine-learning-supervised-and-unsupervised/)
