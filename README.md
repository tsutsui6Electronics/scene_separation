# scene_separation
## 概要


シーン分離は既存の音声や動画、アニメーションなどを個人が編集・合成し、再構成したMADムービーの作成や、行動認識や行動キャプションタスクにおけるデータセット構築の際に役立つ処理になります。

このプログラムは動画内の各シーンをルールベース手法によって分離するプログラムになっています。

システムとしては、まず動画の各フレーム情報を畳み込みニューラルネットワークで構成されるVGG16で特徴量に変換します。\
そして現在のフレームの特徴量と1つ前のフレームの特長量の類似度を測定し、閾値判定で現在のフレームが1つ前のフレームのシーンの延長なのかを判別し、キーフレーム情報を取得します。

このプログラムの工夫としては、各シーンのキーフレームを取得後、細かく分割してしまっているシーンに関しては再度、特長量照合を行い、できるだけ大きな塊に分割するようにしています。
この後処理によって、分離しすぎてしまうミスを減らしています。

しかし、現状、変化が激しいシーン(輝度が瞬間的に変化するようなシーンなど)ではシーンの分割ミスが起きやすくなっており、改善する必要があります。
## 動作確認環境
windows10\
Python3.8.8
```
主なライブラリ
torchvision==0.10.0
opencv-python==4.6.0.66
scipy==1.6.2
```
## 使い方
``` python scene_separation.py "動画ファイル.mp4"```

## サンプル
この動画はBlenderを用いて作成したもので権利は作者にあります。
この動画の分離結果は`output/`にあります。

https://user-images.githubusercontent.com/55880071/178159094-64ba36de-eb38-4ce2-8e8c-1695786f9dd6.mp4

## 備考


今後、このプログラムの改良として、より激しいシーンにも対応出来るニューラルシーン分離機を作成する予定です。


