# タイヤ保管・入出庫管理（デモ）

車のディーラー店舗と物流事業者が共通で使う、タイヤ保管・入出庫の業務Webのデモです。
店舗の入庫・出庫依頼 → 倉庫への作業指示（倉庫・棚番）→ 作業指示書の印刷 → 完了 → 保管タイヤ台帳 → 月ごとの請求明細（CSV・Excel出力）までを1つの画面で扱います。

- **権限は3つ**：店舗（自店の分だけ）／倉庫（全店舗の作業指示と実績入力）／管理者（全部）
- **他店・他社のデータは見えない**：見せ分けは画面ではなくデータベース（PostgreSQL の行ごとの権限＝RLS）が行うため、依頼のURLを直接開いても他店の分は「ありません」になります
- **技術**：Next.js（TypeScript）＋ PostgreSQL（Supabase へそのまま移せる設計）
- 自動試験20本と、実サーバで3権限を使って1件を最後まで通す確認26項目に合格しています
- データはすべて架空です（法人名に「デモ」と付けています）

## 画面

**ログイン（デモ用アカウント）**

![ログイン](evidence/01_login.png)

**店舗A：自店の依頼だけが見える**

![店舗Aの依頼一覧](evidence/02_shopA_requests.png)

**店舗Aの入庫依頼の入力**

![入庫依頼の入力](evidence/03_shopA_new_request.png)

**店舗B（別の法人）：店舗Aの依頼は0件**

![店舗Bの依頼一覧](evidence/05_shopB_requests_only_own.png)

**店舗Bが店舗Aの依頼のURLを直接開いても表示されない**

![直接URLは404](evidence/06_shopB_direct_url_404.png)

**倉庫：全店舗の依頼**

![倉庫の依頼一覧](evidence/07_warehouse_requests_all_shops.png)

**倉庫：作業指示（倉庫・棚番を決める）**

![作業指示](evidence/08_warehouse_instruct_form.png)

**作業指示書（印刷用）**

![作業指示書](evidence/09_work_order_print.png)

**倉庫：完了の入力と履歴**

![完了](evidence/10_warehouse_completed.png)

**保管タイヤ台帳（検索・状態・棚番）**

![保管タイヤ台帳](evidence/12_admin_tire_ledger.png)

**請求明細（保管料＋入庫・出庫の作業料／CSV・Excel出力）**

![請求明細](evidence/14_admin_billing.png)

**店舗A：自店の請求だけ（ダークモードの端末でも白い画面）**

![店舗Aの請求明細](evidence/15_shopA_billing_dark_device.png)

**スマホ幅での依頼入力**

![スマホ](evidence/16_mobile_new_request.png)
