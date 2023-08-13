# G検定
## 1章 人工知能とは

## 2章 人工知能をめぐる同行

## 3章 人工知能分野の問題
### 3-1
- ローブナーコンテスト、ローブナー賞
  - 人工知能として最も人間に近いと判定された会話ボットに対して毎年授与される賞。競技の形式は標準的なチューリングテスト。
## 4章 機械学習の具体的手法
### 4-1
- アンサンブル学習
  - バギング：
    - 全体から一部のデータを用いて複数のモデルを用いて学習する方法。並列処理可能。
  - ブースティング：
    - 一部のデータを繰り返し抽出し、複数のモデルに学習させる。並列処理不可能、以前に使用したデータを再利用する。逐次的に弱学習器を構築


#### 代表的な手法・強化学習
- 理論

- バンディットアルゴリズム

- マルコフ決定過程モデル

- 価値関数

- 方策勾配

  - REINFORCE
    - 方策勾配法ベースの手法
  - Actor-Critic
    - 価値関数ベースおよび方策勾配ベースの考え方を組み合わせたもの
  - A3C (Asynchronous Advantage Actor-Critic)
    - Actor-Criticの応用。
### 4-2 モデルの評価
- ホールドアウト法、ホールドアウト検証
  - 学習データとテストデータに分割して評価する。
- 交差検証、クロスバリデーション
  - k-分割交差検証
    - データをk子に分割してそのうちの1つをテストデータ、残りを学習データに

## 5章 ディープラーニングの概要
### 5-5 学習率の最適化
- 勾配降下法
  - 確率的勾配降下法
    https://ja.wikipedia.org/wiki/%E7%A2%BA%E7%8E%87%E7%9A%84%E5%8B%BE%E9%85%8D%E9%99%8D%E4%B8%8B%E6%B3%95
    - 
- 鞍点
  - モーメンタム
  - Adagrad, Adadelta, RMSprop, Adam, AdaBound, AMSBound
  
## 6章 ディープラーニングの手法
### 6-1 CNN
- ネオコグニトロン
- LeNet

- AlexNet、2012 ILSVRC

- VGG
- GoogLeNet
  - Inceptionモジュール

- ResNet
  - skip connection

- MoblieNet
  - パラメータ数を削減
  - Depthwise Separable Convolutionを用いる
    - Depthwise convolution、Pointwise Convolution

- Neural Architecture Search / NAS
- NASNet
- MnasNet

- EfficientNet
  - 2019年5月にGoogle Brainから発表されたモデルで、従来よりかなり少ないパラメータ数で高い精度を叩きだす
  - 転移学習にも有用なモデル

- 転移学習
  - 既存のモデルに、新たに何層かを自分でつけたし、その層だけを学習して高性能なネットワークを得ること
- ファインチューニング
  - 付け足した層だけでなく、ネットワーク全体を学習する方法
- 学習済みCNNモデルの利用方法まとめ / https://sinyblog.com/deaplearning/pre_train_model/

### 6-2 深層生成
- 変分オートエンコーダ, VAE
  - 入力データを統計分布に変換する。平均と分散で表現
- 敵対的生成ネットワーク, GAN
  - ジェネレータとディスクりみねーた
    - 画像生成して出力、画像が本物か偽物か予測
  - Pix2Pix / もとの画像データと変換した画像のペアが、本物か偽物化を予測
  - CycleGAN / 画像のペアが必要ない

### 6-3 画像認識分野
- 2012, AlexNet, ILSVRC
- 2014 Inceptionモジュール、GoogLeNet
  - 同年にVGG
- 2015, Skip connection ResNet
  - Wide ResNet / カーネル数を増やす
  - DenseNet / Skip connectionを工夫
- 2017, Attention機構、Squeeze-and-Excitation Networks (SENet)

#### 物体検出タスク
- 2段階
  - R-CNN
    - Fast R-CNN / 
    - Faster R-CNN / Region Proposal Network <-Selective Search
  - FPN
- 1段階
  - YOLO (You Only Look Once)
  - SSD

#### セグメンテーションタスク
- 画像の画素ごとに識別を行うタスク
  - Semantic Segmentation /セマンティックセグメンテーション ・ 領域分割 / 画像全体を対象とする
  - Instance Segmentation  / インスタンスセグメンテーション / 物体検出した領域を対象とする
  - Panoptic Segmentation / パノプティックセグメンテーション / 個々の物体をそれぞれ分離しつつ、道路や建物などはひとまとめにする

- FCN / Fully Convolutional Network / 
  - CNNをセマンティックセグメンテーションに利用したもの
    全結合層を用いず、畳み込み層だけで構成するモデル
- SegNet
  - 小さくなった特徴マップを徐々に拡大する構造を採用した手法
    - エンコーダ：特徴マップを徐々に小さくしていく部分
    - デコーダ：徐々に大きくしていく部分
- U-Net
  - 特徴マップを拡大して畳み込み処理をする際、エンコーダ側の特徴マップを同じサイズになるように切り出して利用する
- PSPNet
  - Pyramid Poling Moduleという複数の解像度で特徴をとらえるモジュールをついkあ

- DeepLab
   Dilated convolution / Atrous convolutionを採用。
- DeepLab V3+
  - PSPNetのような複数解像度の特徴をとらえる機構(ASPP: Astrous Spatial Pyramid Pooling)を持つ

#### 姿勢推定タスク
- 人の頭や足、手などの関節位置を推定するタスク
- 信頼度マップによるアプローチが有効

- Convolutional Pose Machines : CNNを多段に組み合わせて徐々に各骨格の信頼度マップを高精度化していく

- Open Pose
  - 複数の人の骨格を同時に推定できるようにした手法
    - Parts Affinity Fieldsという骨格関係の位置関係を考慮した処理を導入している
#### マルチタスク学習
- 複数のタスクを1つのモデルで対応すること
  - Faster R-CNNやYOLOなども物体クラスの識別と、物体領域の位置検出を同時に行っている
- Mask R-CNN
  - 物体検出だけでなく、セグメンテーションも同時に行う。
  
### 6-4 音声処理と自然言語処理
#### データの扱い方
#### RNN / リカレントニューラルネットワーク
- LSTM

- Bidirectional RNN (BiRNN)

- Sequence-to-Sequence / seq2seq / Google, 2014
  - 系列(sequence)を別の系列へ変換するモデル。系列は具体的には自然言語や音声。
  - 入力が時系列なら、出力も時系列で予測したい。
  - 2つのRNNを組み合わせる
    - https://blog.octopt.com/sequence-to-sequence/
    - Encoder, Decoderと2つのパートに分かれる。

- Attention

#### Transformer
#### Pre-trained models
- GPT (Penerative Pre-Trained)
- BERT (Bidirectional Encoder Representations from Transformers) / Google

- ALBERT
- DistilBERT

- GPT-2  / 15億ものパラメータ / 2019/2、OpenAI
  - フェイクニュースへの懸念から完全版は公開せず。
- Megatron-LM / 83億のパラメータ / 2019/9、NVIDIA
- Turing-NLG / 170億のパラメータ / 2020/2、Microsoft
- GPT-3 / 1750億のパラメータ / 2020/5

- Vision Transformer (ViT) / CNNを使わない事前学習モデル、トランスフォーマー
#### その他
- WaveNet / DeepMind
  - 機械学習により自然な音声を生成する技術。

### 6-5 深層強化学習
- DQN (Deep Q-Network) / DeeepMind
  - Atari2600で人間並み、または人間以上のスコアで攻略可能
### 6-6 モデルの解釈性の問題とその対応
#### 解釈性問題
#### Grad-CAM
- Grad-CAM
  - 可視化を目的とした手法。
    画像認識系のタスクを対象として、画像のどこを見ているか、を可視化する。

- Guided Grad-CAM
  - 画像が低解像度にならないよう、入力値の勾配情報も用いる。
### その他
- モデル圧縮 https://laboro.ai/activity/column/engineer/%E3%83%87%E3%82%A3%E3%83%BC%E3%83%97%E3%83%A9%E3%83%BC%E3%83%8B%E3%83%B3%E3%82%B0%E3%82%92%E8%BB%BD%E9%87%8F%E5%8C%96%E3%81%99%E3%82%8B%E3%83%A2%E3%83%87%E3%83%AB%E5%9C%A7%E7%B8%AE/
  - Pruning / プルーニング・枝刈り
    - ノード間の重みが小さい箇所の接続を削除、または影響の小さいノードを削除することでパラメータ数を削減
  - Quantize / クオンタイズ・量子化
    - 重みなどのパラメータをより小さいビットで表現することで、モデルを軽量化
  - Distillation / ディスティレーション・蒸留
    - 大きいモデルやアンサンブルモデルを教師モデルとして、その知識を小さいモデル・生徒モデルの学習に利用する方法。
      大きいモデルに匹敵する精度を持つ小さいモデルを作ることが期待される。
    
## 7章 ディープラーニングの社会実装に向けて
### 7-2 AIプロジェクト
- AIプロジェクトで、納品と権利移転などはどうするか
  https://storialaw.jp/blog/2894
### 7-3 データを集める
- オープンデータセット
  - コンピュータビジョン分野
    - ImageNet : 自然画像。1400万枚を超える画像を、2魔手以上のラベルで示したもの。ILSVRCで用いられている。
    - MNIST : 0-9の手書き数字の文字セット。
    - PascalVOC, MS COCO
  - 自然言語処理
    - WordNet, SQuAD, DBPedia
  - 音声分野
    - LibriSpeech

- センサを利用

- 著作権法30条の4 / 平成30年著作権法改正
  https://www.soei.com/blog/2020/06/20/%E5%B9%B3%E6%88%90-30-%E5%B9%B4%E8%91%97%E4%BD%9C%E6%A8%A9%E6%B3%95%E6%94%B9%E6%AD%A3%EF%BC%8830-%E6%9D%A1%E3%81%AE4%EF%BC%89/
  - 日本では、情報解析の用に供する場合に著作物を利用することが、営利・非営利問わず適法とされる。
    著作者に無断で複製や翻案をしても適法。
    もっとも、著作権者の利益を不当に害する場合はその限りでない。

### 7-4 データを加工・分析・学習させる
- FAT (Fairness, Accontability, and Transparency: 公平性、説明責任、透明性)
- ACM FAT: 米国コンピューター学会におけるFAT
    
### 7-5 実装・運用・評価
- 知的財産として
  - 営業秘密、秘密管理。
  - 限定提供データ

- 悪用
  - IBM、警察による選別で使われるなどした顔認識ソフトの提供中止、撤退
  - Amazon、AIによる顔認識技術を１年停止

- ディープフェイク
  
### 

## その他用語など
- ナイキスト周波数
  - サンプリング周波数の半分の周波数のこと。一般的なwav形式の44100Hzならば22050Hz。
    正しく検出できる最大の周波数。
    検出したい周波数があるならば、その倍のサンプリング間隔が必要（標本化定理、サンプリング定理）

- メル尺度 / mel scale
  - 音程の知覚的尺度。メル尺度の差が同じであれば、人間が感じる音高の差が同じになることを意図している。

- ハイパーパラメータ
  - 機械学習アルゴリズムの挙動をせてチスルパラメータ。少し乱暴な言い方をすると機械学習のアルゴリズムの「設定」
    https://www.codexa.net/hyperparameter-tuning-python/

- 共分散
  - 2つの変数の関係を表す値で、「平均値からの偏差の席の平均」で求められる。

- シリアスゲーム
  - コンピュータゲームではあるが、純粋な娯楽のためではなく、社会課題の解決を目的として作られているもの。
    教育や医療用となど。
  - ゲーム内でのゴール（クリア）よりも、ゲーム外でのゴール（能力の習得）の方が最終目的の場合も多い。

- ポアソン回帰
  - 発生率が低いアウトカムの分析に向いている

- ロジスティック回帰
- トービット回帰

- コサイン類似度
  - https://manabitimes.jp/math/1378
  - 2本のベクトルがどれくらい同じ向きを向いているかを指す指標。-1以上1以下。

- リーケージ Leakage
  - 本来得られるはずのないデータをモデルの学習に使用してしまうこと。
  - https://note.com/kenichiro/n/n2ff08344160a
