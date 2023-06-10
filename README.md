# dance-kinect

## 概要
姿勢推定を使ったパフォーマンス案。kinectを使って、DJがパフォーマンスしている際の観客の踊りを検出&パラメーター化し、音楽を生成 or 選曲する。  
踊ってない人には指向性スピーカーを使って、踊れるグルーブをその人だけに届ける。  
![system](https://github.com/dai0618/dance-kinect/assets/90552127/51a07516-e3c3-499e-b98e-41bd767782c4)

## 必要なライブラリのインストール
ターミナルで以下のコマンドを実行。
```python
pip install -r requirements.txt
```  
テスターのみを用いる時は以下のコマンドを実行。
```python
pip install python-osc
```

## OSC Reference
### IP & PORT (IP:PORT)  
* State Controller ```127.0.0.1:9999```  
* Moving Light ```127.0.0.1:8888```  
* Kinect ```127.0.0.1:7777```  
* Music Select ```127.0.0.1:6666```  
* UI ```127.0.0.1:5555``` 
### OSCの対応表
| Address             | From             | To               | Content | Discription              | 
| :-----------------: | :--------------: | :--------------: | :-----: | :----------------------: | 
| /move               | Kinect           | Moving Light     | 0 or 1  | 0が停止、1が再生         | 
| /finish_analyze     | Kinect           | State_Controller | bang    | 動いてない人の検知終了   | 
| /start_music_select | State_Controller | Music Select     | bang    | 音楽生成を選択の開始     | 
| /finish_select      | Music Select     | State_Controller | path    | 音楽のファイルパスを送信 | 
| /player             | State_Controller | UI               | path    | 音楽のファイルパスを送信 | 
| /restart            | UI               | State_Controller | bang    | 検知再開                 | 
| /start_analyze      | State_Controller | Kinect           | bang    | 検知再開                 | 


## test
テスターの実行。
```python
python test_state.py
```