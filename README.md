# SD1111_colab
AUTOMATIC1111/Stable Diffusion WebUI（SD/WebUI）をGoogle Colaboratoryで使うためのipynb

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/imamurayusuke/SD1111_colab/blob/main/SD1111_colab.ipynb) ←これをクリックしてどうぞ

## 特徴

### Googleドライブの容量をなるべく消費しない一方、設定や生成した画像はGoogleドライブに保存される
- SD/WebUIはランタイム上にインストール
- 学習モデル（ckptやsafetensors）もランタイム上にダウンロード
  - 読み込まれる学習モデルは公式（[v2-1_768-ema-pruned.safetensors](https://huggingface.co/stabilityai/stable-diffusion-2-1)）とでりだモデル（[derrida_final.ckpt](https://huggingface.co/naclbit/trinart_derrida_characters_v2_stable_diffusion)）、vae含む

#### Googleドライブに保存されるもの（保存先は「Colab Notebooks」－「Stable Diffusion」フォルダ）
- 生成した画像（outputsフォルダ、logフォルダ）
- 各種の設定（config.json、ui-config.json、styles.csv）
  - これらはSD/WebUIが読み込む際にGoogleドライブ上にバックアップを作る（config_bak.json、ui-config_bak.json、styles_bak.csv）
- インストールした拡張機能（extensionsフォルダ。日本語化の拡張機能に限り初回起動時に自動でダウンロードされる）

### ただ起動するだけで使える（テキストボックスへの入力やチェックボックスのオン／オフなどの操作は不要）

- その結果、学習モデルを追加したいときなどはノートブックを自分のGoogleドライブにコピーしてソースコードを編集する必要がある

### 起動に約7分～10分かかる
  - 毎回SD/WebUIをインストールし学習モデルをダウンロードしているため

## 解決したい問題

特定の条件で、SD/WebUIを停止したあとに設定バックアップのためのコードセルを実行する必要がある。

1. 初回起動のあと（ui-config.jsonが生成される）
1. Settingsタブの「Apply settings」を初めてクリックしたあと（config.jsonが生成される）
1. Stylesを初めて登録したあと（styles.csvが生成される）

各回とも一度実行すれば、SD/WebUIは次回以降の起動時にGoogleドライブ側にある各種設定ファイルを読み出し書き出す（シンボリックリンクを利用）。

SD/WebUIがgit pullの時点でこれらのファイルをとりあえず生成してくれれば、それをGoogleドライブにコピーしてそこへシンボリックリンクを張ってからSD/WebUIをインストールできる。しかしこれらが生成されるのは早くても初回の起動後である
