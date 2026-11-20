# AI運用の番人 スキル10本集（配布版）

note連載「AI運用の実践メモ」で紹介した自作スキル10本を、1つの配布パッケージにまとめたものです。
いずれも、実際にAIアシスタントを自律運用している現場の手順を、そのままスキル（SKILL.md）として切り出したものです。数字はすべて実測です。

> すぐ使う：Claudeのチャットで「https://github.com/ai-jissen-lab/skills-bundle のスキルを使えるようにして」と送るだけ。

> noteでスキしてくださった方へ：記事ごとの特典は [記事別特典の受け取りページ（GIFTS.md）](GIFTS.md) から受け取れます。

## 収録スキル

| スキル | 何を防ぐ／何をするか | こんなときに |
|---|---|---|
| **memory-metabolism**（メモリ代謝） | AIのメモリが育ちすぎて答えが矛盾するのを防ぐ。常駐メモリの棚卸し、シーン別分割、訂正台帳、整理前後の再質問検証までを手順化 | 長く使ったAIが古い決定や訂正済みの事実を引きずり始めたら |
| **draft-or-done**（完了と言わせない） | 「カートに入れた＝買った」「下書き保存＝送信した」のような中間状態と完了の取り違えを防ぐ。状態の階段・証拠カタログ・報告の3点セット | 買い物・送信・予約・投稿・公開をAIに任せているなら |
| **ningen-slides**（人間スライド） | AIが作るスライドの「AIっぽさ」を消す。図と太い線と言い切る文の制作ルール＋仕上げのNG点検リスト（3分類）で、人が作ったような資料にする | 営業資料・提案資料をAIに作らせるなら |
| **delegation-rules**（委任の型） | 任せる前に、完了の証拠・承認ゲート・報告の形（working／waiting／done）を決めて委任文で渡す。委任文・受け取りチェックのテンプレート付き | AIに仕事を任せ始めたが、報告の取り違えや確認の多さで困っているなら |
| **skill-gate**（外部スキル検査ゲート） | 外部スキルを取り込む前にSkillSpectorでスキャン（必ず`--no-llm`）し、判定ごとの扱いに従い、プロンプト部分のみを移植する検査手順 | 外部スキルやプラグインを入れる前に、必ず通す関門として |
| **api-first-ledger**（API優先と台帳） | 作業前にAPI台帳を引いて、ブラウザ操作よりAPIを優先する進め方。台帳に取り込むのは完全無料で継続性が高いものだけ（除外条件5つ） | APIの使い分けや無料枠の管理が場当たりになっているなら |
| **email-thread-ops**（メール・スレッド読み） | 下書き前にスレッド全体を原文で読み、求めていることと未決事項を分け、数字と条件の整合を確認してから、固定した文面の型で書く | AIのメール下書きが「なんとなく噛み合わない」とき |
| **correction-ledger**（訂正台帳） | 一度直した間違いが戻らないよう、訂正を「旧（誤）／現行（正）／検証質問の形」で台帳化し、整理の前後で再質問して検証する。memory-metabolismと併用 | 同じ訂正を何度も繰り返しているなら |
| **full-brief**（フルブリーフ） | 文脈を持たない別のAIや外注先へ渡す指示文を、6要素（実態・背景と目的・仕様・基準と嫌うもの・禁止事項・自己チェック）で設計する | 外部への指示文が短すぎて、平均的な成果物しか返ってこないなら |
| **cron-design**（定期ジョブ設計） | 定期実行が静かに増えるのを防ぐ設計の型。「変化なし」を報告するためだけの監視は作らない、相乗りを先に確認、新規は日次以下から、停止したものは勝手に戻さない | 定期ジョブが増えて消費と通知が膨らんできたなら |

個別リポジトリもあります（memory-metabolism、draft-or-done、ningen-slides の3本。中身は同じです）：
- https://github.com/ai-jissen-lab/memory-metabolism
- https://github.com/ai-jissen-lab/draft-or-done
- https://github.com/ai-jissen-lab/ningen-slides （natural-slides強化版）

残りの7本（delegation-rules、skill-gate、api-first-ledger、email-thread-ops、correction-ledger、full-brief、cron-design）は、このバンドルに収録しています。

## 使い方

### Claudeのチャット（claude.ai・デスクトップアプリ）
設定の「機能」で「クラウドでコードを実行」と「外部ネットワークへの通信を許可」をオンにしてから、新しいチャットで次のように送ります。

```
https://github.com/ai-jissen-lab/skills-bundle のスキルを使えるようにして
```

うまくいかないときは、使いたいスキルのフォルダ（`skills/<スキル名>`）を丸ごとzipにして、「設定」の「Skills」からアップロードしてください。zipはこのリポジトリの Releases にもスキル別に置いてあります。

### Claude Code
```bash
git clone https://github.com/ai-jissen-lab/skills-bundle.git
cp -r skills-bundle/skills/* ~/.claude/skills/
```

各スキルのテンプレートや設定見本（`templates/`、`*.example.md`、`ng-checklist.md`）は SKILL.md から参照されるので、スキルフォルダごと置いてください。

## 解説記事（note）
仕組みの解説と実測は、note連載で無料公開しています。有料の実践編（実際の設定・プロンプト全文・チェックリスト）もこちらです。
- note： https://note.com/ai_jissen_lablab （AI運用の番人）
- X： https://x.com/ai_jissen_labla

記事とスキルの対応表は `CATALOG.md` にあります。

## フォルダ構成
```
skills/
  memory-metabolism/  SKILL.md, config.example.md, templates/
  draft-or-done/      SKILL.md, proofs.example.md, templates/
  ningen-slides/      SKILL.md, brand.example.md, ng-checklist.md
  delegation-rules/   SKILL.md, templates/
  skill-gate/         SKILL.md, templates/
  api-first-ledger/   SKILL.md, templates/
  email-thread-ops/   SKILL.md, templates/
  correction-ledger/  SKILL.md, templates/
  full-brief/         SKILL.md, templates/
  cron-design/        SKILL.md, templates/
extras/
  ningen-slides-samples/  スライドのサンプル画像3枚（zip配布版のみに収録。GitHub上では個別リポジトリ ningen-slides の samples/ を参照）
CATALOG.md  記事との対応表
LICENSE     MIT
```

## ライセンスとクレジット
- MIT License（`LICENSE`）
- ningen-slides は natural-slides（yoshitakagiii、MIT）を土台に、仕上げのNG点検を加えた強化版です。点検項目の一部は KAWAI（@kawai_design）の図解を参考に再構成しました。
- memory-metabolism の「常駐に足す前の問い」「訂正台帳」の考え方は、テツメモ（@tetumemo）のメモリ代謝の発想に着想を得ています。

バージョン：v2.0（2026-11-20、スキル10本集）
