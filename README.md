# dance-kinect

## 概要
姿勢推定を使ったパフォーマンス案。  
kinectを使って、DJがパフォーマンスしている際の観客の踊りを検出&パラメーター化し、音楽を生成or選曲する。  
踊ってない人には指向性スピーカーを使って、踊れるグルーブをその人だけに届ける。

## ライブラリのインストール
ターミナルで以下のコマンドを実行。
```python
pip install -r requirements.txt
```

## OSC Reference
* IP & PORT (IP:PORT)  
State Controller ```127.0.0.1:9999```  
Moving Light ```127.0.0.1:8888```  
Kinect ```127.0.0.1:7777```  
Music Generation ```127.0.0.1:6666```  
UI ```127.0.0.1:5555```  



## test
```python
python test_state.py
```