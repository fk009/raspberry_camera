# ラズベリーパイで監視カメラ


![camera](https://user-images.githubusercontent.com/103634835/164973752-6fb1abd7-8e85-4cdb-8ca7-96a9f2c53b93.jpg)
![hontai](https://user-images.githubusercontent.com/103634835/164973754-718e5637-1113-40c9-9683-665bd606311a.jpg)


## カメラの方には『 motion 』ソフトウェアを利用しました。

## 撮影された動画は、同じくラズベリーパイで作成した自宅のNASへと送信されます。
　使用ソフトは『 Openmediavault 5 』です。

## １つの動画ファイルの撮影時間は、基本的に数秒ほどとなっています。

　理由としては主に、
① 動体検知している間だけなので、検知したあとで動画内で変化があまりなかった場合、余分に撮影してしまい、保存容量を使ってしまうため。
② 撮影時間が長いと、撮影している最中に不審者がカメラを停止してしまった場合、NASへ動画が送信される前にデータが消えてしまうため。
となっています。

## PCから動画の結合処理
　任意のタイミングで、PCから動画結合処理のプログラムを走らせることにより、複数のカメラのそれぞれの日付ごとに、結合動画を作成し、保存します。

## 結合された動画は、2倍速で保存されます。
　これは動画の確認を簡単にするためです。動画自体のコマは消えるわけではないので、もし気になる部分があれば低速再生することで、より詳しく確認することができます。


# それぞれのpythonファイル説明

## came_join_v2 - Github用.py
NASに保存されている動画ファイルを、1日ごとの動画ファイルとして、結合して出力します。
ライブラリ『opencv』を使用しています。

## rapyPGM_you.py
動体検知の際、検出する範囲を指定するための、マスクファイルを作成します。
なぜ格子状にするのかというと、検出範囲を網目にし、絞ることで、処理の負担を減らすことができるためです。
