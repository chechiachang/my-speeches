# Me

# Outline

原先要講的題目太大，我根本講不完，再來就是太硬，這邊做了點調整

- Before read source code
棄坑推薦：沒事別來讀 Save your time!
- Let's read Source Code the hard way
- Let's read Source Code the esay way

# Why read kube-apiserver

雖然這個 session 系列叫帶大家讀源碼
但一開始，我要先勸在做的各位契坑
沒事幹嘛要讀源碼

1. 你是kubernetes 的源碼貢獻者
2. 有使用 go-client 整合 kubernetes 開發
3. 正在設計大型雲服務架構，ex. 自建分散式 api server

個人不建議的理由
1. 欣賞 kubernetes 的架構，因為他太複雜（架構圖）
2. 把人家的寫法學起來，之後遇到時可以用
  kube-apiserver 是非常複雜的系統，想解決的問題，平常是很難遇到的，除非你是大型分散式系統的架構師

如果不是 Kubernetes 的開發者，其實完全不需要一行一行把他看完
就算在接 go-client，我們也是用到時才看，一邊使用一邊看
我個人是遇到才看，用到才讀的

# Question

讀過 kubernetes source code 舉個手
用過 kubernetes ，知道大體架構的請舉個手
會寫 golang

# Before read kube-apiserver

- Understand kube-apiserver architecture 
[Official Tutorial: Access API](https://kubernetes.io/docs/tasks/administer-cluster/access-cluster-api)
[What happens when k8s](https://github.com/jamiehannaford/what-happens-when-k8s)
[Deep Dive API server](https://blog.openshift.com/kubernetes-deep-dive-api-server-part-1/)

- Design concepts

- A running kubernetes. Try this
[Katacoda](https://www.katacoda.com/courses/kubernetes/playground)

手邊應準備 Kube-apiserver The Easy Way

# 讀之前要先知道的幾件事情

1. 還沒讀源碼，先要認識 kube-apiserver
看源碼之前，先知道這源碼
源碼跟書本或是文章不一樣

書本是在給你一個想法
源碼是在解決一個實際的問題

你讀一段 function code 然後把 function 名稱遮起來
可以理解我想表達的意思嗎？
是的，你認真地讀完源碼後，你會知道這段源碼在做什麼
不覺得先看 function name 比較省時間？

如果我把 kube-apiserver package name 遮起來，你看完終究會發現他是 apiserver...eventually

1. Kubernetes 的基本架構，服務元件功能

其實我也不敢說我對，只能說常用的功能大概有遇到過

2. kube-apiserver 的設計理念 -> 為何要這樣做
實作是來解決特定問題的。先知道實作想解決的問題，才來看實作

這行 code 在幹嘛 -> 為了什麼目的這樣寫 -> 解決了什麼問題

# kube-apiserver architecture

# 從開始的地方開始

1. 從 api-server 啟動開始讀，程式啟動，啟動參數
找一個 running kube-apiserver ，檢查他的啟動參數

2. 選一個有興趣的 api，從 api request 進來後trace ，一直到 response 出去

# Still with me?

# Filter interesting PRs

api group label:sig/api-machinery label:approved

https://github.com/kubernetes/kubernetes/issues?utf8=%E2%9C%93&q=api+group+label%3Asig%2Fapi-machinery+label%3Aapproved

# 從 PR 開始讀

label:approved label:sig/api-machinery

源碼未必有足夠的文件，但PR往往都會講述清楚這個 PR 的目的
1. 篩選 label: 
  - Approved / Merged 
  - sig:api-machinery 
2. 找看得懂的標題開始下手，conversation 少的通常比較入門
3. 先看 Files changed ，再開 View 整個檔案
4. 用 PR 的內容說明，彌補源碼中 comment 不足的地方
5. (Optional) 看懂了後，幫忙加個 comment ，自己發個 PR

# Let's learn Pod GC Controller

# End

http://slack.k8s.io/
