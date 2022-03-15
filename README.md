# RxSwift使用してみた

### 非同期イベントの枠組みを提供してくれるライブラリ

### 目的
* RxSwiftを使用している企業があったのでどんなものか気になったから
* 実際に使用したらどのようなメリットがあるのか知りたいから

### 使用技術
Swift

### 機能の説明
>* UI イベント受け取り
>* Web API レスポンス受け取り
>* データの変化の監視

### 使用するために必要な条件
* Xcode 12.x
* Swift 5.x

### Installation
1. PodFileに下記の記述を追加する
```html
# Uncomment the next line to define a global platform for your project
# platform :ios, '9.0'

target 'RxSwiftSample' do
  # Comment the next line if you don't want to use dynamic frameworks
  use_frameworks!

  # Pods for RxSwiftSample

  pod 'RxSwift'
  pod 'RxCocoa'

end
```

2. pod installを行う
```html
pod install
```

### 例
> 例)URLSession
```html
session.rx.response(request)
    .catchError {
        // エラー時の処理
    .subscribe {
        // レスポンス受け取り時の処理
    }
    .disposed(by: disposeBag)
```

RxSwiftで書くと上記のようになります。

> 例)Notification
```html
NotificationCenter.default.rx.notification(..)
    .subscribe { [unowned self] _ in
        // 通知受け取り時の処理
    }
    .disposed(by: disposeBag)
```

NotificationCenterからの通知を受け取る処理をRxSwiftで書いたら上記のようになります。

##### SwinjectのREADMEは下記
`https://github.com/ReactiveX/RxSwift`

### 今後の課題
まだまだ、RxSwiftについての理解が浅いので今後は実践で使用してみて、慣れていこうかと思っております。
最初に勉強する際には、書籍などを活用するのをオススメします
