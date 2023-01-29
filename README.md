# SD1111_colab
AUTOMATIC1111/Stable Diffusion WebUI（SD/WebUI）をGoogle Colaboratoryで使うためのipynb

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/imamurayusuke/SD1111_colab/blob/main/SD1111_colab.ipynb)

## 特徴

- Googleドライブの容量をなるべく消費しない一方、設定や生成した画像はGoogleドライブに保存される
  - SD/WebUIはランタイム上にインストール
  - 学習モデル（ckptやsafetensors）もランタイム上にダウンロード
    - 読み込まれる学習モデルは公式（[v2-1_768-ema-pruned.safetensors](https://huggingface.co/stabilityai/stable-diffusion-2-1)）とでりだモデル（[derrida_final.ckpt](https://huggingface.co/naclbit/trinart_derrida_characters_v2_stable_diffusion)）、vae含む
  - Googleドライブに保存されるもの
    - 生成した画像（outputsフォルダ、logフォルダ）
    - 各種の設定（config.json、ui-config.json、styles.csv）
    - インストールした拡張機能（extensionsフォルダ。日本語化の拡張機能に限り初回起動時に自動でダウンロードされます）
- ただ起動するだけで使える（テキストボックスへの入力やチェックボックスのオン／オフなどの操作は不要）
  - その結果、学習モデルを追加したいときなどはノートブックを自分のGoogleドライブにコピーしてソースコードを編集する必要がある
- 起動に約7分～10分かかる
  - 毎回SD/WebUIをインストールし学習モデルをダウンロードしているため
- 初回起動のあと／Settingsタブの「Apply settings」を初めてクリックしたあと／Stylesを初めて登録したあと、の3回に限り、SD/WebUIを停止したあとに設定バックアップのためのコードセルを実行する必要がある
  - 各回とも一度実行すればSD/WebUIはGoogleドライブ側の各種設定ファイルを読み出し書き出す（シンボリックリンクを利用）
