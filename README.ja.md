# ウェブサイト移行テンプレート

[English](README.md) | [简体中文](README.zh-CN.md) | [日本語](README.ja.md) | [繁體中文](README.zh-HK.md)

ウェブサイトのリニューアルに使える、URL の移行計画、プロジェクト要件、公開時の確認用テンプレートです。サンプルのパスは架空のものです。使用時は、承認済みのプロジェクトデータに置き換えてください。

[ウェブサイトのリニューアル手順](https://zequnweb.com/jp/blog/homepage-renewal-checklist/)。

## テンプレート一覧

| ファイル | 用途 |
| --- | --- |
| [url-inventory.ja.csv](url-inventory.ja.csv) | ページの維持、移行、統合、廃止を決め、担当者と確認結果を記録する |
| [redirect-map.tsv](redirect-map.tsv) | チェッカーで使用できる、直接リダイレクト 3 件のサンプル |
| [project-brief.ja.csv](project-brief.ja.csv) | 対象ユーザー、範囲、言語、資料、システム連携、検収条件を整理する |
| [seo-deliverables.ja.csv](seo-deliverables.ja.csv) | SEO の各作業について、確認できる成果物と担当者を明確にする |
| [launch-checklist.ja.csv](launch-checklist.ja.csv) | コンテンツ、リダイレクト、インデックス登録、フォーム、端末対応、公開の責任者を確認する |

このページでリンクしている CSV テンプレートは、すべて日本語です。

## 使用手順

1. リポジトリのコードメニューから ZIP をダウンロードするか、このリポジトリをクローンします。
2. CSV ファイルを表計算ソフトで開きます。有用な旧 URL を残し、関連する転送先を選び、各判断の担当者を指定します。
3. 実際にリダイレクトする行だけを対象に、旧 URL と転送先の 2 列を出力します。列の区切りはタブとし、見出し行を削除して、1 行に 1 件の対応関係を残します。
4. [ローカル版リダイレクトチェッカー](https://github.com/awesomellm/redirect-map-checker/blob/main/README.ja.md)で対応表を確認します。
5. サーバーにルールを設定した後、実際の HTTP 応答、転送先の内容、内部リンク、インデックス登録の設定を検証します。
6. フォームの送信結果、公開の承認、元の状態に戻す際の責任者、公開後の問題をチェックリストに記録します。

**複数列の CSV 一覧は、チェッカーの入力には使えません。** 維持または廃止するページの判断をチェッカーに貼り付けないでください。同梱の `redirect-map.tsv` は、見出しのない 2 列形式になっています。

## 対応範囲と制限

これらは計画用のテンプレートであり、サーバー設定やクローラーではありません。本番環境のリダイレクトを検証したり、検索順位の安定を保証したりするものではありません。廃止するすべての URL をトップページへ転送せず、関連する代替ページを選んでください。代替がない場合は、適切な「ページが見つからない」応答を使用します。

## 参考資料

- [Google：URL の変更を伴うサイトの移転](https://developers.google.com/search/docs/crawling-indexing/site-move-with-url-changes?hl=ja)
- [ZequnWeb：リニューアルチェックリスト](https://zequnweb.com/jp/blog/homepage-renewal-checklist/)

## 改善への参加

不足している判断項目、検収項目、サンプルを具体的に提案してください。公開の問題報告には架空のデータを使用してください。

## メンテナンスとライセンス

B2B ウェブサイトのデザインと開発を行う独立した制作スタジオ、[ZequnWeb](https://zequnweb.com/jp/) が作成しました。テンプレートと文書は MIT ライセンス（`LICENSE`）で公開しています。
