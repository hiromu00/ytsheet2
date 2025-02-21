####################################
##               ゆとシートⅡ     ##
##          by ゆとらいず工房     ##
##    https://yutorize.2-d.jp     ##
####################################

### 設置の手順 #######################################################################################
 1. config.cgi.defaultのファイル名をconfig.cgiに変更する（.defaultを消す）

 2. config.cgiを開いて、管理用パスなどを設定する

 3. ゆとシートのファイルをすべてサーバーにアップする

 4. index.cgiのパーミッション（属性）を<705>または<755>に変更する
   （サーバーによっては<700>などの可能性もアリ）

 5. ブラウザからシートのTOPページ(http://○○○/ytsheet2/sw2.5/（または/dx3rd/や/blp/）)へアクセスして
    問題なく表示されれば設置完了

### ファイル構成 #####################################################################################
  <>内は一般的なパーミッション設定です。基本的に、「index.cgi」以外は設定（変更）する必要はありません。
  ※index.cgiはシステムごとに1つあります

 /ytsheet2 <705> ディレクトリ（フォルダ）名は変更可
  |
  |- /_core <705> 本体部分格納ディレクトリ
  |  |
  |  |- /data <705> 共通登録データ（ユーザー情報）格納ディレクトリ
  |  |
  |  |- /lib  <705> 処理ファイル格納ディレクトリ
  |  |  |
  |  |  |- /sw2 <705> SW2.5用処理ファイル格納ディレクトリ
  |  |  |  |- config-default.pl <604> デフォルト設定格納ファイル
  |  |  |  |- data-*****.pl     <604> 種族・特技データ等格納ファイル
  |  |  |  |- *****.pl          <604> その他処理ライブラリ
  |  |  |
  |  |  |- /dx3 <705> DX3rd用処理ファイル格納ディレクトリ
  |  |     |- config-default.pl <604> デフォルト設定格納ファイル
  |  |     |- data-*****.pl     <604> シンドローム等データ等格納ファイル
  |  |     |- *****.pl          <604> その他処理ライブラリ
  |  |  |
  |  |  |- /blp <705> BLP用処理ファイル格納ディレクトリ
  |  |     |- config-default.pl <604> デフォルト設定格納ファイル
  |  |     |- data-*****.pl     <604> シンドローム等データ等格納ファイル
  |  |     |- *****.pl          <604> その他処理ライブラリ
  |  |
  |  |- /skin <705> HTMLテンプレート格納ディレクトリ
  |
  |- /sw2.5 <705> SW2.5シートの入り口・データ格納ディレクトリ（名前変更可）
  |  |- /data              <705> 登録データ格納ディレクトリ
  |  |- index.cgi          <705> 入り口になるCGIファイル。パーミッション（属性）設定必須
  |  |- config.cgi.default <604> 設定ファイル。ファイル名を「必ず」 config.cgi に変更してください
  |
  |- /sw2.0 <705> SW2.0シートの入り口・データ格納ディレクトリ（名前変更可）
  |  |- /data              <705> 登録データ格納ディレクトリ
  |  |- index.cgi          <705> 入り口になるCGIファイル。パーミッション（属性）設定必須
  |  |- config.cgi.default <604> 設定ファイル。ファイル名を「必ず」 config.cgi に変更してください
  |
  |- /dx3rd <705> DX3rdシートの入り口・データ格納ディレクトリ（名前変更可）
  |  |- /data              <705> 登録データ格納ディレクトリ
  |  |- index.cgi          <705> 入り口になるCGIファイル。パーミッション（属性）設定必須
  |  |- config.cgi.default <604> 設定ファイル。ファイル名を「必ず」 config.cgi に変更してください
  |
  |- /blp <705> BLPシートの入り口・データ格納ディレクトリ（名前変更可）
     |- /data              <705> 登録データ格納ディレクトリ
     |- index.cgi          <705> 入り口になるCGIファイル。パーミッション（属性）設定必須
     |- config.cgi.default <604> 設定ファイル。ファイル名を「必ず」 config.cgi に変更してください

### 運用解説 #########################################################################################
# 複数設置したい場合
 /ytsheet2
  |- /_core
  |- /sw2.5  ←このディレクトリをコピー＆名前変更して……
  |- /sw2.0
  |- /dx3rd
  |- /blp
                ↓  ↓  ↓
 /ytsheet2
  |- /_core
  |- /swA    ←swA～swCでそれぞれ別の設定で運用できる
  |- /swB    ←┘
  |- /swC    ←┘
  |- /sw2.0
  |- /dx3rd
  |- /blp

# 特定システムだけでいい時
 /ytsheet2
  |- /_core
  |- /sw2.5 
  |- /sw2.0
  |- /dx3rd  ←DX3rdだけでいい場合は……
  |- /blp
                ↓  ↓  ↓
 /ytsheet2
  |- /_core  ←_coreと、
  |- /dx3rd  ←dx3rdディレクトリ以外は削除してよい

### 更新履歴 #########################################################################################
# ver.1.14.0 - 2021-08-14 --------------------------------------------------
- SW2.5: アウトロープロファイルブック対応
- SW2.0: 蛮族名誉点と盟竜点
- ココフォリアのクリップボードAPI対応
- 「保存」ボタンを「出力」ボタンへ変更
- 他、不具合修正多数

# ver.1.13.0 - 2021-06-18 --------------------------------------------------
- DX3rd: クロウリングケイオス対応
- DX3rd: エフェクト欄にドラッグ＆ドロップで削除できるエリア追加
- SW2.0: 超越帯の対応強化
- 名前・二つ名・コードネーム欄の仕様変更（ルビ用の欄を追加）
- 他、不具合修正多数
- レイアウト等微調整

# ver.1.12.0 - 2021-03-10 --------------------------------------------------
- ソードワールド2.0に対応
- 人鬼血盟RPGブラッドパスに対応
- 閲覧制限機能を強化（段階的な閲覧制限を追加）
- チャットパレットの調整
- レイアウト調整（特にモバイル閲覧時）
- SW2.x: 言語欄の機能強化（セージ・バード技能による習得をカウントする仕様に）
- 他、不具合修正多数

# ver.1.11.0 - 2020-12-23 --------------------------------------------------
- キャラクターシートの保存機能追加
- 過去ログ（バックアップ）からの復元編集機能追加
- チャットパレットのデフォルト出力内容変更
- SW2.5: 防具欄の仕様変更
- SW2.5: 一般技能にソート機能追加
- SW2.5: 魔物データ・アイテムデータのコンバート機能追加（ゆとシートⅡ間のみ）
- DX3rd: 能力値内訳、エフェクト経験点修正を表示するよう修正
- 他、不具合修正多数
- レイアウト等微調整


# ver.1.10.2 - 2020-11-08 --------------------------------------------------
- SW2.5: 言語欄のに入力候補追加
- SW2.5: 装備の必筋が上限を超える場合に表示変更
- 他、不具合修正多数

# ver.1.10.1 - 2020-10-28 --------------------------------------------------
- DX3rd: コンボ欄のソート不具合修正

# ver.1.10.0 - 2020-10-22 --------------------------------------------------
- SW2.5: モンストラスロア対応
- DX3rd: コンボ欄の技能補正自動挿入追加
- PL名検索追加

# ver.1.09.0 - 2020-06-17 --------------------------------------------------
- テキスト整形ルールに折り畳み追加
- 画像トリミング項目の改良
- SW2.5: 魔力欄の改良
- DX3rd: 一部表示・計算不具合
- DX3rd: チャットパレット出力をゆとチャ向けとBCDice向けの二種に分割
- DX3rd: コンバート時の不具合修正・変換調整
- チャットパレット出力を改良
- 他、軽微な修正
- レイアウト等微調整

# ver.1.08.2 - 2020-05-03 --------------------------------------------------
- DX3rd: エフェクト説明の開閉機能追加
- DX3rd: 保管所からのコンバート不具合数点修正
- DX3rd: エフェクトの攻撃力と基準値が入れ替わる不具合修正
- 他、軽微な修正
- レイアウト等微調整

# ver.1.08.1 - 2020-04-09 --------------------------------------------------
- 全般: 経験点欄の表示を変更
- DX3rd: ゆとシートⅠ⇒Ⅱにおけるコンバート不具合数点修正

# ver.1.08.0 - 2020-04-07 --------------------------------------------------
- ダブルクロスThe 3rd Editionに対応、名前を「ゆとシートⅡ」に変更（for SW2.5を削除）
- ディレクトリ構造を変更
- レイアウト等調整
- 一部項目にドラッグ＆ドロップによるソート機能追加
- コンバート機能追加
- キャラクターシートにOGP設定追加

# ver.1.07.0 - 2020-03-21 --------------------------------------------------
- キャラクターシートのカラーカスタム機能追加
- フェローに第二行動欄追加
- 適用フォントの修正・変更
- チャットパレットの編集結果をプリセットに上書きするか追加するか選択できる項目追加
- チャットパレットのプリセットで変数を使わないものを選択できる項目を追加
- OAuth認証機能追加（by @Shunshun94）
- Template.pm内蔵
- ソースコードの整理

# ver.1.06.0 - 2019-10-19 --------------------------------------------------
- 割り振り作成のポイント算出に2.5式(ET)を追加
- 装飾品欄の追加枠が再編集時に表示されていない不具合修正
- 登録数が多い場合、リストの処理が遅かったのを改善
- 賦術などにも専用化補正のチェックを追加
- 武器欄に「ガン（物理）」のカテゴリ追加（バヨネット等向け）
- ナイトモードの処理を変更
- ナイトモードの状態でページを移動した際のチラつきを低減

# ver.1.05.0 - 2019-05-23 --------------------------------------------------
- マテリアルカード欄追加
- パッケージ・魔物知識・先制に修正値欄追加
- キャラクター画像の表示形式を編集画面でも反映
- チャットパレット用の変数を自動出力
- 幅広用のレイアウト追加
- 武器欄の入れ替え機能追加
- チャットパレットの編集欄を追加

# ver.1.04.0 - 2019-02-24 --------------------------------------------------
- 2.0要素対応（各冒険者技能、一般技能欄、秘伝欄追加）
- 検索機能強化（名前・種族・経験点・技能・信仰）
- 戦闘特技の自動置き換えをオフに
- 置き換え条件を満たした特技を強調表示
- 習得条件を満たさない特技を強調表示
- 一部ファイル名変更
- ノーブルエルフとマナフレアが作成できない不具合修正
- 細かなバグ修正

# ver.1.03.0 - 2019-01-21 --------------------------------------------------
- アイテム登録機能追加
- 武器アイコン追加
- 閲覧禁止機能追加
- 不名誉欄追加
- ルールブックⅢ対応
- 細かなバグ修正 ／ レイアウト調整

# ver.1.02.0 - 2018-10-18 --------------------------------------------------
- ルールブックⅡ対応
- ＰＣ能力値作成機能追加
- 割り振り作成機能追加
- キャラクターリストのソート（名前／PL／Lv／経験点／更新日時）追加
- 細かなバグ修正 ／ レイアウト調整

# ver.1.01.0 - 2018-09-13 --------------------------------------------------
- 魔物データ管理機能追加
- キャラクターデータ格納ディレクトリを data から data/chara へ変更
- 細かなバグ修正 ／ レイアウト調整

# ver.1.00.0 - 2018-09-03 --------------------------------------------------
- リリース


### SPECIAL THANKS ###################################################################################
# json出力 および OAuth認証ログイン制作
# ＆ コンバート機能参考
- しゅんしゅんひよこ (@Shunshun94) さん
