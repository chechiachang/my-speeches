# Me

# 這是一邊導讀

1. 如果不是 Kubernetes 的開發者，其實完全不需要一行一行把他看完
2. 就算在接 go-client，我們也是用到時才看，一邊使用一邊看

如果只有 25 分鐘要看 kube-apiserver 源碼，推薦的閱讀方法
1. 基礎常用的東西: access, authentication
2. 好用的東西：go-client
3. 整個架構
4. api 進來後源碼流程

如果你是個 golang 開發工程師
他用了什麼 package, pattern, 架構設計

對於不熟 kubernetes 的朋友，完全可以當作一組寫的蠻漂亮的 apiserver 欣賞

# Outline

1. Let's use kube-apiserver
2. Let's read api code

# Why Read Source Code

遇到 bug 時來 debug
-欣賞 kubernetes 的架構-

# How to Read Source Code

我自己沒有把整份 api server 的源碼看完

把源碼 git clone 下來，然後像讀小說一樣一行一行，把源碼變成很好的睡前讀物，這也是

一邊使用，一邊查詢源碼中有用到的部分

# Kube-apiserver The Easy Way

# First API call

What is kubectl

# Flow

Creates a proxy server or application-level gateway between localhost and the Kubernetes API Server.
