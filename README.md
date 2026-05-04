# student-id-converter
CSVの対応表を使って、PDF内の学籍番号を氏名表示に変換するブラウザ完結型ツールです。  
GitHub Pages にそのまま配置して利用できます。

## 概要

このアプリは、CSV に登録された「学籍番号,名前」の対応表をもとに、PDF 内の学籍番号を検出し、画面上で氏名を重ねて表示します。  
さらに、変換結果を反映した PDF をダウンロードできます。

- ブラウザだけで動作
- ローカル処理のみで完結
- GitHub Pages で公開

## 主な機能

- CSV ファイルの読み込み
  - フォーマット: `学籍番号,名前`(1人1行)
  - 例: `21001,田中 太郎`
  - Excel等で作成可能

- PDF ファイルの読み込み
  - PDF のみ対応
  - テキストレイヤー付き PDF を対象

- 学籍番号の桁数設定
  - 数字部分の桁数を変更可能
  - CSV と PDF の照合条件を調整可能

- 変換結果の可視化
  - PDF 上の学籍番号位置に氏名を重ね表示
  - 学籍番号の頭のMは無視して処理

- 結果 PDF のダウンロード
  - 表示結果を反映した PDF を保存可能

## 使い方
1. [ツールページ](https://tmed-it.github.io/student-id-converter/) を開きます

2. 名簿のCSV ファイルを選択します  
   形式は `学籍番号,名前`(1人1行) です

3. PDF ファイルを選択します

4. 変換を実行します

5. 画面上で結果を確認し、必要なら PDF をダウンロードします

## 公開先

GitHub Pages で公開  
下記のURLにアクセスして使用してください  
URL: https://tmed-it.github.io/student-id-converter/

### (開発者向け) GitHub Pages での公開手順
1. GitHub の `Settings` → `Pages` を開く
2. `Deploy from a branch` を選択
3. `main` ブランチ / `/ (root)` を指定
4. 保存後、数分待って公開 URL にアクセス

## 動作要件

- JavaScript 有効
- インターネット接続環境
  - 外部 CDN からライブラリを読み込みます

## 使用ライブラリ

- [pdf-lib](https://pdf-lib.js.org/)  ver.1.17.1 CDN  
  - 変換後 PDF の生成に使用
- [@pdf-lib/fontkit](https://www.npmjs.com/package/@pdf-lib/fontkit)  ver.1.1.1 CDN  
  - 日本語フォントの埋め込みに使用
- [pdf.js](https://cdnjs.com/libraries/pdf.js)  ver.5.4.149　./vendor/pdfjs  
  - PDF の読み込み、テキストレイヤー解析、Canvas 描画に使用

### フォント

- [Noto Sans CJK JP Regular](https://github.com/notofonts/noto-cjk) ver.2.004 ./vendor/font  
  - 出力 PDF に日本語を描画するため、実行時に OTF フォントを取得


#### (開発者向け)
ライブラリやフォントのアップデートに合わせてhtml中のCDNリンク・integrityまたは、html中のリンクとvendorフォルダ内のライブラリを更新する必要があります  
integrityはファイルの整合性を確認するハッシュ値で、unpkg.comの場合はURL末尾に?metaを追加することで取得できます  
(例:https://unpkg.com/pdf-lib@1.17.1/dist/?meta)  
pdf.jsとフォントはSRIを実装できないため、DLしvendorフォルダ内に配置しています

Last CDN Update 2026/5/4



## 注意事項

- テキストレイヤーのない PDF では正しく処理できません。事前にOCRを行うことで変換できる可能性があります
- PDF 内の文字配置やフォントによっては検出精度に差が出る場合があります
- 個人情報が含まれる名簿や PDF の取り扱いには十分注意してください
- 保存時に約16MBのフォントファイルをダウンロードします。通信量の制限が厳しい方はWiFiに繋いでご利用ください
- 一部ライブラリは、CDN 読み込みを用いています。リンク先の改竄にご注意ください
- 自己責任でご使用ください

## ライセンス
MIT
