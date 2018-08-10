# Me

# Why Read Source Code

遇到 bug 時來 debug
-欣賞 kubernetes 的架構-

# 這是一邊導讀

這行 code 在幹嘛 -> 為了什麼目的這樣寫 -> 解決了什麼問題

# 什麼條件下建議認真讀

1. 你是kubernetes 的源碼貢獻者
2. 有使用 go-client 整合 kubernetes 開發
3. 正在設計大型雲服務架構，ex. 自建分散式 api server -> kube-apiserver 有很多很特別的
4. 你很喜歡看複雜的程式碼

我個人是遇到才看，用到才讀的

1. 如果不是 Kubernetes 的開發者，其實完全不需要一行一行把他看完
2. 就算在接 go-client，我們也是用到時才看，一邊使用一邊看

# 讀之前要先知道的幾件事情

1. Kubernetes 的基本架構，服務元件功能

其實我也不敢說我對，只能說常用的功能大概有遇到過

2. kube-apiserver 的設計理念 -> 為何要這樣做
實作是來解決特定問題的。先知道實作想解決的問題，才來看實作

3. 跑一個 kube-apiserver

# 好上手的開頭與閱讀方向

1. 從第一行開始讀 -> X

推薦的閱讀方法
1. 基礎常用的東西: access, authentication
2. 從 api-server 啟動開始讀，程式啟動，啟動參數
3. 從 api request 進來後trace ，一直到 response 出去

# Outline

1. Let's use kube-apiserver
2. Let's read api code
  - Basic
  - Design

# How to Read Source Code

我自己沒有把整份 api server 的源碼看完

把源碼 git clone 下來，然後像讀小說一樣一行一行，把源碼變成很好的睡前讀物，這也是

一邊使用，一邊查詢源碼中有用到的部分

# Kube-apiserver The Easy Way

# First API call

What is kubectl

# Flow

Creates a proxy server or application-level gateway between localhost and the Kubernetes API Server.
