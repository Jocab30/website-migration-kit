# サイト移行の実践例

[English](MIGRATION.md) | [简体中文](MIGRATION.zh-CN.md) | [日本語](MIGRATION.ja.md) | [繁體中文](MIGRATION.zh-HK.md)

この例では `/old-contact.html` を `/contact/` に移し、`/company-profile.html` を `/about/` に統合し、`/expired-campaign/` を廃止します。パスは架空のものです。公開後の応答と移行先の内容を確認して初めて検収が完了します。

## 1. ルールを書く前にページの扱いを決める

[URL 一覧](url-inventory.ja.csv) に旧 URL、処理、最終移行先、理由、担当者、実測結果を記録します。移す必要がない有用なページは既存 URL を維持します。移動したページは関連する代替ページへ転送します。代替がない廃止ページには、ホームへの一律転送ではなく適切な 404 または 410 応答を用います。

用途のあるキャンペーンパラメータは保持し、不要なものは明示した方針で処理します。パス、大文字小文字、クエリ、末尾スラッシュは別々に確認してください。チェックツールでは異なる URL として扱います。

## 2. 転送する行だけを出力する

```text
/old-contact.html	/contact/
/company-profile.html	/about/
```

区切りはタブです。見出し、他の列、維持するページ、404/410 の判断を混ぜません。[redirect-map.tsv](redirect-map.tsv) はそのまま検査できる例です。

[ローカルチェックツール](https://github.com/awesomellm/redirect-map-checker/blob/main/README.ja.md) を複製し、ツールのディレクトリで出力ファイルのパスを指定します。

```sh
node check.mjs ../website-migration-kit/redirect-map.tsv https://example.com
```

循環、移行先の競合、中間転送を修正し、外部の移行先は手動で確認します。URL の関係が正しくても、サーバーにルールが反映された証明にはなりません。

## 3. 実際の配信環境に設定する

[設定手順](https://github.com/awesomellm/redirect-map-checker/blob/main/DEPLOYMENT.ja.md) から Cloudflare、Nginx、Apache を選びます。承認した一覧と同じ正確なパスと最終 URL を使い、個別ルールを広い条件の前に置きます。検証環境で試し、旧設定を保存し、切り戻し担当を決めます。

内部リンク、正規 URL、ナビゲーション、言語切り替え、サイトマップは最終ページへ直接向けます。旧リンクの救済と、新サイト内のリンク更新を両方行います。

## 4. 公開後に GET 応答を調べる

```sh
curl -sS -D - -o /dev/null 'https://example.com/old-contact.html?utm_source=test'
curl -sS -L --max-redirs 5 -D - -o /dev/null 'https://example.com/old-contact.html?utm_source=test'
```

最初のコマンドは初回のステータスと `Location`、次は転送の連続を表示します。管理するドメインに置き換え、恒久転送、クエリ処理、最終 200 応答、内容の関連性を確認します。廃止 URL は別に検査します。スマートフォンで移行先を操作し、管理する受信先へ合意したテスト問い合わせを送って確認します。

## 5. 検収と公開後の観察を記録する

[公開チェック表](launch-checklist.ja.csv)、[問い合わせ検収表](inquiry-acceptance.ja.csv)、[観察計画](tracking-plan.ja.csv) に URL、時刻、結果、証拠、担当者を記録します。公開直後に重要な旧 URL、ナビゲーション、受信システムを確認します。その後は日・週単位で実際の 404、サイトマップ処理、対象ページのインデックスを観察します。完全な報告期間を比較し、短期変動だけで成功や失敗を判断しません。

## 6. 操作できる形で引き継ぐ

[引き継ぎ表](handover-checklist.ja.csv)、承認済み一覧、実際の設定、検査結果、切り戻し手順を渡します。事業者がドメイン、配信、内容、問い合わせ受信の管理者を把握できる状態にします。この資料は計画と検証の手順であり、設定の配信や検索順位の保証は行いません。

[Google のサイト移行資料](https://developers.google.com/search/docs/crawling-indexing/site-move-with-url-changes?hl=ja) · [ZequnWeb 日本語サイト](https://zequnweb.com/jp/)
