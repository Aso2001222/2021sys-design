```uml
@startuml
[*] --> トップページ
会員情報 -down-> 会員登録済みトップページ : トップページをクリック/商品検索
会員登録済みトップページ -down-> 商品詳細 : 商品をクリック
ログイン -> 会員登録済みトップページ : トップページをクリック/商品検索
ログイン : entry/id,passwordを入力
ログイン : do/ログイン認証
トップページ -down-> 買い物終了 : ログアウトをクリック
トップページ -> トップページ : 商品検索
トップページ -left-> 商品詳細 : 商品をクリック
ログイン -down-> 会員情報 : 会員登録をクリック
トップページ -down-> ログイン : ログインをクリック
トップページ -down-> カート内 : カートの中をクリック
トップページ : do/商品一覧を表示
商品詳細 -down-> カート内 : カートに入れるをクリック
商品詳細 -> 会員登録済みカート内 : カートに入れるをクリック
商品詳細 --> トップページ : 前の画面に戻るをクリック
商品詳細 : do/商品説明を表示
カート内 -up-> トップページ : トップページをクリック/商品検索
カート内 -down-> 買い物終了 : ログアウトをクリック
会員登録済みカート内 -down-> 買い物終了 : ログアウトをクリック
カート内 -> 商品詳細 : 詳細へをクリック


state カート内{
[*] --> カート
カート -down-> 購入 : 購入をクリック
カート -> カート : サイズを変更/数量を変更/商品を削除
購入 --> カート : カートをクリック
state 購入{
[*] --> 購入商品
購入商品 -> 購入商品の情報 : 購入をクリック
購入商品の情報 -> 購入商品の内容確認 : 内容確認をクリック
購入商品の内容確認 -down-> 注文 : 購入確定をクリック
state 注文{
[*] --> お届け先入力
お届け先入力 -> お届け先入力入力内容確認 : 入力内容確認をクリック
お届け先入力内容確認 -> お届け先入力 : 修正をクリック
お届け先入力内容確認 -> 購入完了 : 注文確定をクリック
}
}
}
state 会員登録済みカート内{
[*] --> 会員カート
会員カート -> 会員注文 : 注文をクリック
会員カート -> 会員カート : 数量を変更/商品を削除
会員注文 --> 会員カート : カートをクリック
state 会員注文{
[*] --> 会員購入
会員購入 -> 購入商品情報 : 注文をクリック
購入商品情報 -> 購入商品内容確認 : 内容確認をクリック
購入商品内容確認 -> 会員購入完了 : 注文確定をクリック
}
}
@enduml
```
