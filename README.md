# scene_separation
## 概要
このプログラムは動画内の各シーンを分離する際に、利用できるプログラムになっています。
なおシステム概要として、まず動画の各フレームをVGG16を使って特徴量に変換します。\
そして現在のフレームの特徴量と過去のフレームの特長量の類似度を測定し、閾値判定で現在のフレームが過去のフレームのシーンの延長なのかを決定します。
また各シーンのキーフレームを取得後、細かく分割してしまっているシーンに関しては再度、特長量照合を行い、できるだけ大きな塊に分割するようにしています。
これにより、分離しすぎてしまうミスは減りますが、類似部分が多いシーン間の結合をしてしまうことがあります。\
また、変化が激しいシーン(輝度が瞬間的に変化するようなシーンなど)ではシーンの分割ミスが起きやすくなっています。
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

## 備考

今後、このプログラムの改良として、このプログラムで作成した大量のシーンデータを使って、より激しいシーンにも対応出来るニューラルシーン分離機を作成する予定です。

