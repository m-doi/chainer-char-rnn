## Setup

1. pyenvのインストール
1. python2.7.9のインストール
```
pyenv install 2.7.9
python local 2.7.9
```

1. Mecabのインストール
```
brew install mecab
brew install mecab-ipadic
```
1. 必要に応じて辞書を拡張（https://qiita.com/ysk_1031/items/7f0cfb7e9e4c4b9129c9）
1. cudaのインストール（https://developer.nvidia.com/cuda-downloads?target_os=MacOSX&target_arch=x86_64&target_version=1012&target_type=dmglocal）
1. 依存ライブラリのインストール

```
pip install -r requirements.txt
```

## Train
1. 学習データを以下に配置する
```
data/dazai/input.txt
```

1. 学習させる
```
python train.py --data_dir data/dazai ¥
--checkpoint_dir cv/dazai --rnn_size 1024 ¥
--gpu -1 --enable_checkpoint False ¥
data/dazai/input.txt
```

### output

* data/dazai/vocab.bin
* cv/dazai/charrnn_final.chainermodel
* cv/dazai/loss.txt

## Predict
```
python sample.py \
--vocabulary data/dazai/vocab.bin \
--model cv/dazai/charrnn_final.chainermodel \
--primetext '宮島さん' --gpu -1
```
