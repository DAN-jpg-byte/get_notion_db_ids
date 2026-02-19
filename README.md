# get_notion_db_ids

Notion APIを活用した自作データーベースID取得用プログラムです。


## フォルダ構成
- `NotionのデータベースIDを調べる.py` : DB内の各プロパティ（列）の固有IDを特定するためのツール。
- `.env` : APIトークンやデータベースIDなどの機密情報を管理（Git等には含めない）。

## 習得した技術・工夫点
1. **ライブラリに頼らないAPI操作**
   - 環境による依存関係のトラブル（AttributeError等）を避けるため、Python標準の `urllib` を使用してNotion APIと直接通信する実装を採用しました。
2. **プロパティIDによる指定**
   - Notion側で列名（例：「山田列」→「近藤列」）を変更してもプログラムが壊れないよう、名前ではなく固有ID（`title`, `I%5BJp` 等）を使用して操作する仕組みを導入しました。

## 例）データベースのプロパティID一覧
*現在の「インタースティシャル・ジャーナリングDB」の構成*

| 列名 | ID | 型 |
| :--- | :--- | :--- |
| **完了したこと** | `title` | title |
| **日時** | `I%5BJp` | date |
| **気持ち** | `cNJ%5C` | rich_text |
| **次にやりたいこと** | `udPY` | rich_text |
| **後でやりたいこと、メモなど** | `c%3BQ%7C` | rich_text |

## 使用方法
1. `.env` ファイルに `NOTION_API_TOKEN` と `DATABASE_ID` を設定します。
2. `NotionのデータベースIDを調べる.py` を実行して、最新のDB構造を確認します。

---
*Created with the help of Gemini - Feb 2026*