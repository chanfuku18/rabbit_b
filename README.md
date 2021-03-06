# ラビットチャレンジ 機械学習  
  
## 線形回帰モデル  

要点  
・1次式（=直線）で表現されるモデル。  
・慣例として予測値にはハットをつける。  
・パラメータは最小二乗法で決定。  
（但し、外れ値には弱く、他の手法もある。）  
・線形回帰の場合には、最尤法でのパラメータ推定と一致する。  
  
実装演習（rabbit_b_1.ipynb）  
（結果）  
・部屋数4、犯罪率0.3の物件の予測は、4.24。  
（考察）  
・回帰係数は、犯罪率に対して-0.26491325、部屋数に対して8.39106825。  
・部屋数の方が係数が大きい。  
・犯罪に対しては負の相関がある。  

## 非線形回帰モデル  
  
要点  
・ほとんどの実データは線形モデルでは捉えられない。  
・基底関数を用いてモデルを構築。  
・多項式基底、ガウス基底、スプライン基底。  
・モデルの表現力が上がる事でオーバーフィッティングが生じる。  
・対策：①データを増やす ②パラメータの数を調整 ③正則化。  
・クロスバリデーション法やホールドアウト法で汎化性能をチェック。  

実装演習（skl_nonlinear regression.ipynb）  
・非線形のモデルを用いる事で、線形では表現できないモデルを学習できる。  
・正則化パラメーターを調整する事で、オーバーフィッティングが起きる事を確認した。  
・表現力のあるモデルで、適切にハイパーパラメータを調整する事が重要。  
  
## ロジスティック回帰モデル  
  
要点  
・分類問題を解く為のモデル。  
・線形結合をシグモイド関数に通す。  
・シグモイド関数の微分はシグモイド関数自身で表せる。  
・確率が0.5以上だと正、o.5未満だと負と定義して最尤推定。  
・ベルヌーイ分布を仮定して最尤推定としてパラメータを推定。  
・パラメータは解析的に求められないので、勾配降下法を求める。  
・評価はRecall、Precision、F値等で行う。  
  
実装演習（rabbit_b_3.ipynb）  
（結果）  
・30歳、男性の生存確率は、0.19335257。  
（考察）  
・女性や子供を助ける為に男性の生存率が低かったと考えられる。  
  
## 主成分分析  
  
要点  
・多変量データをより少数のデータで表す。  
・制約付き最小化問題→ラグランジュ未定計数法。  
・元データの分散共分散行列の固有値と固有ベクトルが解となる。  
・分散共分散行列は正定値行列なので固有値は必ず0以上で、固有ベクトルは直行する。  
  
実装演習（rabbit_b_4.ipynb）  
（結果）  
・次元圧縮無しの精度 96.0% 次元圧縮後の精度 93.2%  
（考察）  
・次元圧縮すると次元数は約1/16になるにもかかわらず、精度はそれほど落ちない。  
・第二主成分まででほとんどが説明できている。  
  
## アルゴリズム  
  
要点  
k近傍法  
・最近傍のデータをk個とってきてその多数決で分類する手法。  
・kを大きくすると決定協会は滑らかになる。  
k-means  
・クラスタ重心からの距離で分類するアルゴリズム。  
・中心の初期値を変えると結果が変わりうる。  
・kの値を変えると結果が変わる。  
  
実装演習（np_knn.ipynb / np_kmeans.ipynb）  
k近傍法  
・kの値が小さい時に、ノイズとなる点の影響を受ける事を確認した。  
k-means  
・クラスタ数を変えて実験した。  
・初期値を変えても今回の問題では、さほど影響がなかった。  
・問題が容易であった為と考えられる。  
  
## サポートベクターマシーン  
  
要点  
・線形判別関数と最も近いデータ点との距離＝マージン。  
・マージンが最大となる線形判別関数を求める。  
・ソフトマージン→誤差に対してペナルティを課す。  
・カーネルトリック→カーネル関数により高次元空間で表現する事で  
非線形な分離が可能になる。  
  
実装演習（np_svm.ipynb）  
・ハイバーパラメータCを調節して変化を見た。  
・Cが大きい場合はご認識のペナルティが大きい為、決定境界を複雑にしようとする。  
・但し、線形の場合は、マージンを小さくしようとするだけになる。  
  
