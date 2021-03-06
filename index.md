## Deeplearning

### 4.1　データから学習する

- 重みパラメータを自動で組んでくれるのが、ニューラルネットワークのすごいところだよ！自動でやってくれるその裏側について、アルゴリズムを勉強ていくよ！

### 4.1.1　データ駆動

- 機械学習はデータが命。
- 手書き文字の例から、数字を認識する場合の例　-> 画像の特徴量からパターンを抽出する
- 画像データ -> ベクトル変換　-> 識別器　->　学習　で規則性を自動で見つける、これが、機械学習でできるよ。


### 4.1.2　訓練データとテストデータ

- 機械学習モデルの汎化能力を試すフロー
- 2つのデータ群を用意する。
- 1.訓練データ  -> 最適なモデルのパラメータを探す用のデータ
- 2.テストデータ -> 訓練して作ったモデルを試すようのデータ
- 訓練データで、ざっくり認識なりのモデルを作り、それがどれくらい使えるかを試す、を繰り返して、調整していくよ。
- この訓練データと、テストデータは別に用意する必要があって、正確に汎化能力をはかるのに必要だよ


### 4.2 損失関数

- まず現在の指標を決める
- その基準に対して、パラメータの探索を行うよ！
- ニューラルネットワークの学習指標は、「損失関数」という名前だよ

### 4.2.1　2乗和誤差

- 2乗和誤差を用いる関数に、「二乗和誤差」があるよ
![式](https://raw.githubusercontent.com/johntips/python_deeplearning/master/0421.png)

- 手書き数字認識の例、数値化

> y = [0.1, 0.05, 0.6, 0.0, 0.005 ,0.1, 0.0, 0.1, 0.0 ,0.0,0.0]
> t = [0, 0, 1, 0, 0, 0, 0, 0, 0, 0]

- yk ->  ニュラルネットワークの出力 -> ニューラルネットワークでは、ソフトマックス関数
- tk -> (teacher)は教師データ
- k  -> 次元数
- t  -> tの教師データは、生後を決めるので、２進数で、one-hot表現というよ！（T/Fとかで）
- ソフトマックス関数の説明は飛ばすよ

- 次のpythonコードは、2の手書き文字正解に対して、出力が2で最も高い場合。
- pythonコードはこちら


```python
import numpy as np
// [2]を正解とする
t = [0, 0, 1, 0, 0, 0, 0, 0, 0, 0]
// 1.[2]の確率が高い順番はから、0.6...0.1...と続くよ！
y = [0.1,0.005,0.6,0.0,0.005,0.0,0.1,0.0,0.0,0.0]
result = mean_squared_error(np.array(y), np.array(t))
print result
//> 0.0975000000031
// 2. 2.[7]の確率が高い場合
y = [0.1, 0.05,0.1,0.0,0.05,0.1,0.0,0.6,0.5,0.0]
result = mean_squared_error(np.array(y), np.array(t))
print result
//> 0.7225000000003
```

#### この出力結果では、一つ目のほうが、損失関数が小さい = 教師データとのごzさが小さいということがわかる。

---------

## 2章　パーセプトロン
### 2.1　パーセプトロンとは
### 2.2　単純な論理回路
### 2.2.1　ANDゲート
### 2.2.2　NANDゲートとORゲート
### 2.3　パーセプトロンの実装
### 2.3.1　簡単な実装
### 2.3.2　重みとバイアスの導入
### 2.3.3　重みとバイアスによる実装
### 2.4　パーセプトロンの限界
### 2.4.1　XORゲート
### 2.4.2　線形と非線形
### 2.5　多層パーセプトロン
### 2.5.1　既存ゲートの組み合わせ
### 2.5.2　XORゲートの実装
### 2.6　NANDからコンピュータへ
### 2.7　まとめ

3章　ニューラルネットワーク
### 3.1　パーセプトロンからニューラルネットワークへ
### 3.1.1　ニューラルネットワークの例
### 3.1.2　パーセプトロンの復習
### 3.1.3　活性化関数の登場
### 3.2　活性化関数
### 3.2.1　シグモイド関数
### 3.2.2　ステップ関数の実装
### 3.2.3　ステップ関数のグラフ
### 3.2.4　シグモイド関数の実装
### 3.2.5　シグモイド関数とステップ関数の比較
### 3.2.6　非線形関数
### 3.2.7　ReLU関数
### 3.3　多次元配列の計算
### 3.3.1　多次元配列
### 3.3.2　行列の内積
### 3.3.3　ニューラルネットワークの内積
### 3.4　3層ニューラルネットワークの実装
### 3.4.1　記号の確認
### 3.4.2　各層における信号伝達の実装
### 3.4.3　実装のまとめ
### 3.5　出力層の設計
### 3.5.1　恒等関数とソフトマックス関数
### 3.5.2　ソフトマックス関数の実装上の注意
### 3.5.3　ソフトマックス関数の特徴
### 3.5.4　出力層のニューロンの数
### 3.6　手書き数字認識
### 3.6.1　MNISTデータセット
### 3.6.2　ニューラルネットワークの推論処理
### 3.6.3　バッチ処理
### 3.7　まとめ

4章　ニューラルネットワークの学習
### 4.1　データから学習する
### 4.1.1　データ駆動
### 4.1.2　訓練データとテストデータ
### 4.2　損失関数
### 4.2.1　2乗和誤差
### 4.2.2　交差エントロピー誤差
### 4.2.3　ミニバッチ学習
### 4.2.4　［バッチ対応版］交差エントロピー誤差の実装
### 4.2.5　なぜ損失関数を設定するのか？
### 4.3　数値微分
### 4.3.1　微分
### 4.3.2　数値微分の例
### 4.3.3　偏微分
### 4.4　勾配
### 4.4.1　勾配法
### 4.4.2　ニューラルネットワークに対する勾配
### 4.5　学習アルゴリズムの実装
### 4.5.1　2層ニューラルネットワークのクラス
### 4.5.2　ミニバッチ学習の実装
### 4.5.3　テストデータで評価
### 4.6　まとめ

## 5章　誤差逆伝播法
### 5.1　計算グラフ
### 5.1.1　計算グラフで解く
### 5.1.2　局所的な計算
### 5.1.3　なぜ計算グラフで解くのか？
### 5.2　連鎖率
### 5.2.1　計算グラフの逆伝播
### 5.2.2　連鎖率とは
### 5.2.3　連鎖率と計算グラフ
### 5.3　逆伝播
### 5.3.1　加算ノードの逆伝播
### 5.3.2　乗算ノードの逆伝播
### 5.3.3　リンゴの例
### 5.4　単純なレイヤの実装
### 5.4.1　乗算レイヤの実装
### 5.4.2　加算レイヤの実装
### 5.5　活性化関数レイヤの実装
### 5.5.1　ReLUレイヤ
### 5.5.2　Sigmoidレイヤ
### 5.6　A.ne／Softmaxレイヤの実装
### 5.6.1　A.neレイヤ
### 5.6.2　バッチ版A.neレイヤ
### 5.6.3　Softmax-with-Lossレイヤ
### 5.7　誤差逆伝播法の実装
### 5.7.1　ニューラルネットワークの学習の全体図
### 5.7.2　誤差逆伝播法に対応したニューラルネットワークの実装
### 5.7.3　誤差逆伝播法の勾配確認
### 5.7.4　誤差逆伝播法を使った学習
### 5.8　まとめ

## 6章　学習に関するテクニック
### 6.1　パラメータの更新
### 6.1.1　冒険家の話
### 6.1.2　SGD
### 6.1.3　SGDの欠点
### 6.1.4　Momentum
### 6.1.5　AdaGrad
### 6.1.6　Adam
### 6.1.7　どの更新手法を用いるか？
### 6.1.8　MNISTデータセットによる更新手法の比較
### 6.2　重みの初期値
### 6.2.1　重みの初期値を0にする？
### 6.2.2　隠れ層のアクティベーション分布
### 6.2.3　ReLUの場合の重みの初期値
### 6.2.4　MNISTデータセットによる重み初期値の比較
### 6.3　Batch Normalization
### 6.3.1　Batch Normalizationのアルゴリズム
### 6.3.2　Batch Normalizationの評価
### 6.4　正則化
### 6.4.1　過学習
### 6.4.2　Weight decay
### 6.4.3　Dropout
### 6.5　ハイパーパラメータの検証
### 6.5.1　検証データ
### 6.5.2　ハイパーパラメータの最適化
### 6.5.3　ハイパーパラメータ最適化の実装
### 6.6　まとめ

## 7章　畳み込みニューラルネットワーク
### 7.1　全体の構造
### 7.2　畳み込み層
### 7.2.1　全結合層の問題点
### 7.2.2　畳み込み演算
### 7.2.3　パディング
### 7.2.4　ストライド
### 7.2.5　3次元データの畳み込み演算
### 7.2.6　ブロックで考える
### 7.2.7　バッチ処理
### 7.3　プーリング層
### 7.3.1　プーリング層の特徴
### 7.4　Convolution／Poolingレイヤの実装
### 7.4.1　4次元配列
### 7.4.2　im2colによる展開
### 7.4.3　Convolutionレイヤの実装
### 7.4.4　Poolingレイヤの実装
### 7.5　CNNの実装
### 7.6　CNNの可視化
### 7.6.1　1層目の重みの可視化
### 7.6.2　階層構造による情報抽出
### 7.7　代表的なCNN
### 7.7.1　LeNet
### 7.7.2　AlexNet
### 7.8　まとめ

## 8章　ディープラーニング
### 8.1　ネットワークをより深く
### 8.1.1　よりディープなネットワークへ
### 8.1.2　さらに認識精度を高めるには
### 8.1.3　層を深くすることのモチベーション
### 8.2　ディープラーニングの小歴史
### 8.2.1　ImageNet
### 8.2.2　VGG
### 8.2.3　GoogLeNet
### 8.2.4　ResNet
### 8.3　ディープラーニングの高速化
### 8.3.1　取り組むべき問題
### 8.3.2　GPUによる高速化
### 8.3.3　分散学習
### 8.3.4　演算精度のビット削減
### 8.4　ディープラーニングの実用例
### 8.4.1　物体検出
### 8.4.2　セグメンテーション
### 8.4.3　画像キャプション生成
### 8.5　ディープラーニングの未来
### 8.5.1　画像スタイル変換
### 8.5.2　画像生成
### 8.5.3　自動運転
### 8.5.4　Deep Q-Network（強化学習）
### 8.6　まとめ



You can use the [editor on GitHub](https://github.com/johntips/python_deeplearning/edit/master/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/johntips/python_deeplearning/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
