
使用Keras來寫Encoder-Decoder Model
基本步驟如下

1. 獲取資料: 拿到的資料如以下形式: English sentence	中文句子。
2. 分詞
3. 建立單字查詢表（這個步驟等同於為每個單字標一個index）
4. 將每個字轉成用index表示，所以input會變成一個二維的矩陣，看起來像: [[1, 2, 3, 0, ...], [1, 77, 14, 3, 0, ...], ...]
5. 建立Encoder跟Decoder的模型，這邊注意的是維度的關係

Encoder由一層Embedding加上LSTM構成，輸出最後一個狀態[hidden_state, cell_state]當作Decoder的initial state
Decoder也由一層Embedding加上LSTM構成，每個字的output是下個字，所以我們一開始只要輸入起始字串符就像推倒骨牌般能輸出整個字串

6. 建立好模型後，就能把input跟target丟進去訓練

(opt. 1). 我們可以使用預訓練的Word Embedding來優化，一般來說容量都大概1G~2G甚至以上，所以主記憶需要夠大
我們這裡用了: 
英文(from stanford): https://nlp.stanford.edu/projects/glove/
中文(from facebookresearch): https://github.com/facebookresearch/fastText/blob/master/pretrained-vectors.md

(opt. 2). (未完成)Encoder-Decoder模型除了使用LSTM以外，我也想實驗看看GRU, Bi-LSTM, CNN不同元件做出來的效果會如何

 
