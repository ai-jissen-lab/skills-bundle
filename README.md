# AI運用の番人 スキル3本セット（配布版）

note連載「AI運用の実践メモ」で紹介した自作スキル3本を、1つの配布パッケージにまとめたものです。
いずれも、実際にAIアシスタントを自律運用している現場の手順を、そのままスキル（SKILL.md）として切り出したものです。数字はすべて実測です。

> すぐ使う：Claudeのチャットで「https://github.com/ai-jissen-lab/skills-bundle のスキルを使えるようにして」と送るだけ。

## 収録スキル

| スキル | 何を防ぐ／何をするか | こんなときに |
|---|---|---|
| **memory-metabolism**（メモリ代謝） | AIのメモリが育ちすぎて答えが矛盾するのを防ぐ。常駐メモリの棚卸し、シーン別分割、訂正台帳、整理前後の再質問検証までを手順化 | 長く使ったAIが古い決定や訂正済みの事実を引きずり始めたら |
| **draft-or-done**（完了と言わせない） | 「カートに入れた＝買った」「下書き保存＝送信した」のような中間状態と完了の取り違えを防ぐ。状態の階段・証拠カタログ・報告の3点セット | 買い物・送信・予約・投稿・公開をAIに任せているなら |
| **ningen-slides**（人間スライド） | AIが作るスライドの「AIっぽさ」を消す。図と太い線と言い切る文の制作ルール＋仕上げのNG点検リスト（3分類）で、人が作ったような資料にする | 営業資料・提案資料をAIに作らせるなら |

個別リポジトリもあります（中身は同じです）：
- https://github.com/ai-jissen-lab/memory-metabolism
- https://github.com/ai-jissen-lab/draft-or-done
- https://github.com/ai-jissen-lab/ningen-slides （natural-slides強化版）

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
extras/
  ningen-slides-samples/  スライドのサンプル画像3枚（zip配布版のみに収録。GitHub上では個別リポジトリ ningen-slides の samples/ を参照）
CATALOG.md  記事との対応表
LICENSE     MIT
```

## ライセンスとクレジット
- MIT License（`LICENSE`）
- ningen-slides は natural-slides（yoshitakagiii、MIT）を土台に、仕上げのNG点検を加えた強化版です。点検項目の一部は KAWAI（@kawai_design）の図解を参考に再構成しました。
- memory-metabolism の「常駐に足す前の問い」「訂正台帳」の考え方は、テツメモ（@tetumemo）のメモリ代謝の発想に着想を得ています。

バージョン：v1.0（2026-11-20）
