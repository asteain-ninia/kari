# RESX Merger Tool

## 概要
RESX Merger Toolは、2つの言語（日本語と英語）のリソースファイル（.resx）を効率的に結合するPythonスクリプトです。このツールは、翻訳キーを対応させ、日本語と英語の翻訳を統合した新しいresxファイルを生成します。

このツールは、asteainの指示の下、AnthropicのAI言語モデルであるClaude 3.5 Sonnetによって作成されました。特に、SpaceEngineersというゲームの翻訳ファイルをカスタマイズする目的で開発されました。

## 機能
- 日本語と英語のresxファイルを解析
- 対応するキーの翻訳を結合
- 完全に一致する翻訳は結合せず、日本語版を保持
- 結合された翻訳を新しいresxファイルに出力
- マッチングできなかった項目を別のログファイルに出力
- 結果のプレビュー表示

## 必要条件
- Python 3.6以上

## 使い方
1. スクリプトをダウンロードし、Pythonがインストールされている環境で実行します。
2. コマンドラインで以下のコマンドを実行します：
   ```
   python resx_merger.py
   ```
3. プロンプトに従って、以下の情報を入力します：
   - 日本語のresxファイルパス
   - 英語のresxファイルパス
   - 出力ファイルのパス
   - ログファイルのパス
4. スクリプトが実行され、結果が表示されます。

## 出力
1. 結合されたresxファイル：指定した出力パスに生成されます。
2. ログファイル：マッチングできなかった項目の詳細がJSON形式で出力されます。
3. コンソール出力：
   - 結合結果のプレビュー（最初の5件）
   - 未マッチの項目数（日本語ファイルのみ、英語ファイルのみ）

## 動作の詳細
1. 入力ファイルの解析：
   - 各resxファイルを解析し、キーと値のディクショナリを作成します。

2. 翻訳の結合：
   - 両言語のディクショナリを比較し、以下のルールに従って結合します：
     - キーが両方の言語に存在し、値が異なる場合：「日本語 英語」の形式で結合
     - キーが両方の言語に存在し、値が同じ場合：日本語の値のみを保持
     - キーが一方の言語にのみ存在する場合：未マッチとしてログに記録

3. 結果の出力：
   - 結合された翻訳を新しいresxファイルに出力します。
   - 未マッチの項目をJSONファイルとして出力します。

4. 結果のプレビュー：
   - 結合結果の最初の5件をコンソールに表示します。

## 注意事項
- 入力するファイルパスは、絶対パスまたはスクリプトからの相対パスで指定してください。
- 大量のデータを処理する場合、実行に時間がかかる可能性があります。
- 未マッチの項目は手動で確認し、必要に応じて追加の処理を行ってください。
- このツールは特にSpaceEngineersの翻訳ファイルを処理することを想定していますが、同様の構造を持つ他のresxファイルにも使用できる可能性があります。
