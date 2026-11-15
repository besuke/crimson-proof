# Crimson Proof『Leanから見た金融数学』

金融モデルを「手元で計算する」「サーバーで動かす」「仮定から何が導けるかを証明する」の三つの入口から学ぶ三部作のうち、**金融モデルの仮定を Lean で定義し、どの仮定のもとで何が成り立つかを証明する**本です（旧名 LagrangeAcademy）。

> この価格は、どの市場の仮定のもとで、無裁定条件を満たすのか。

取引可能な資産、ニューメレール、確率測度を定め、どの市場の仮定のもとで価格が無裁定となるかを Lean で確かめます。現在の公開原稿は、第I部「Leanの論理・型理論・形式的証明」と第II部「無裁定を中心とした金融数学」からなります。第III部では、同じ理論に基づく数値実装と検証を扱う予定です。数式とRコードで計算を再現したい読者には Coral Book を、ブラウザからサーバー上のモデルを操作したい読者には Carmine Studio を案内します。

## 三部作

| | Coral Book『金融工学の応用基礎』 | Carmine Studio『エンタープライズ金融モデル』 | Crimson Proof『Leanから見た金融数学』 |
|---|---|---|---|
| 学び方 | **手元で計算する**：理論を読み、手元の R で計算を再現する Quarto の本 | **サーバーで動かす**：React で条件を操作し、R サーバー上の RiemannFinMath でモデルを評価する Web アプリ | **証明する**：金融モデルの仮定を Lean で定義し、どの仮定のもとで何が成り立つかを証明する本 |
| リポジトリ | <https://github.com/besuke/coral-book> | <https://github.com/besuke/carmine-studio> | <https://github.com/besuke/crimson-proof> |
| 始め方 | `quarto render`（または RStudio で各章を実行） | R API（`npm run api`、127.0.0.1:8787）と画面（`npm run dev`）を起動し、<http://127.0.0.1:8081/> を開く | `lean/` で `lake build`、本は `quarto render` |

## 同じテーマを三つの入口で

| テーマ | Coral Book（手元で計算する） | Carmine Studio（サーバーで動かす） | Crimson Proof（証明する） |
|---|---|---|---|
| 割引と無裁定 | 第II部 第1章 確定キャッシュフロー、第3章 OISスワップとマルチカーブ評価で、割引係数と複製を手で計算する | 「イールドカーブと円OIS」（`#/yield-curve-ois`）で OIS の気配を動かしてスワップの時価を確かめる。「OISアセットスワップ」（`#/asw`） | 第10章 有限市場における無裁定と価格の一意性、第11章 ニューメレール、第12章 資産価格の基本定理で、無裁定に必要な市場の仮定を定義して定理を証明する |
| 金利カーブ | 第II部 第2章 金利カーブ | 「金利カーブ」（`#/yield-curves`）、「国債先物・CTD」（`#/jgb-futures`） | 第11章 ニューメレール（割引による価格の正規化） |
| オプション | 第II部 第4章 ブラックモデル | 「ブラックモデル」（`#/black-model`） | — |
| 信用リスク | 第II部 第5章 信用リスクとCDS | 「信用リスクとCDS」（`#/credit-cds`） | — |
| 金利モデルと早期償還 | 第II部 第6〜8章 | `#/irs-calibration`、`#/rate-models`、`#/early-redemption` | — |
| PRDC | 第II部 第9章 | 「PRDC」（`#/prdc`）、「11. 自動微分」の PRDC の節 | PRDC のクーポンの分解（`lean/LagrangeAcademy/PrdcCoupon.lean`） |
| 並列・分散・自動微分 | — | 「 9. 並列計算」（`#/enterprise/parallel-computing`）、「10. 分散計算」（`#/enterprise/distributed-jobs`）、「11. 自動微分」（`#/enterprise/automatic-differentiation`） | — |
| 計算の保証 | 各章の計算例 | 照合の記録（`reconciliation/`） | 第1章 計算と証明、第7章 実数と数値計算 |

Lean のライブラリーの名前（`lean/LagrangeAcademy/`）は、検査済みのコードを変えないために旧名のままです。

## この教材の考え方

Coral Book（旧 LagrangeFinance）を受け継ぐ金融計算の教材。金融計算の結果について、何が・どこまで・誰によって保証されているかを、次の 4 段に分けて扱う。

- Lean による証明
- 独立した実装との照合
- 統計的検証
- 人の判断

本書の中心の問いは、どの市場の仮定のもとで価格が無裁定となるかである。AI と形式的証明の関係は、その問いを考える導入として扱う。

構想は `docs/concept.md`（2026-11-07 初版、設計案）。
