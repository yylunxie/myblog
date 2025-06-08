---
title: "Few-Shot Learning"
date: "2025-02-28T16:38:10+08:00"
tags: ["Machine Learning"]
slug:
# cover:
# image: "<image path/url>" # image path/url
# alt: "<alt text>" # alt text
# caption: "<text>" # display caption under cover
# relative: false # when using page bundles set this to true
# hidden: true # only hide on current single page
draft: true
---

## 前言

如果你要讓一個人可以分辨圖片裡的動物是不是貓，通常你只需要提供幾張貓的照片，大概率就能夠學習好貓的特徵，並且能夠正確辨識出是否為貓。但是如果要讓傳統機器學習模型學會辨識貓，那可需要上百張，甚至上千張貓的圖片才能有令人滿意的結果。

現在，如果想要讓傳統機器學習模型也和人類一樣，只需要少量樣本就能學習，機器該如何做到這點呢？

## Few-shot Leaerning

> Few-shot learning is a machine learning framework in which an AI model learns to make accurate predictions by training on a very small number of labeled examples.

「Few-shot learning 是一種機器學習方法，AI 模型僅需少量標註數據即可訓練並進行準確預測。」
