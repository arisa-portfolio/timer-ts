# 共通シーケンス図

## 1. アプリを起動する

```mermaid
sequenceDiagram
    actor User as ユーザー
    participant UI as 画面
    participant Timer as タイマー
    participant Alarm as アラーム

    User->>+UI: アプリを起動する

    UI->>+Timer: 初期化を依頼
    Timer-->>-UI: 初期化完了

    UI->>+Alarm: 初期化を依頼
    Alarm-->>-UI: 初期化完了

    UI->>-User: 初期画面を表示
```

## 2. 通知が競合する

> タイマー通知が鳴っている最中に、アラーム通知が発生した場合

```mermaid
sequenceDiagram
    participant Timer as タイマー
    participant Alarm as アラーム
    participant Notification as 通知管理
    participant UI as 画面
    actor User as ユーザー

    Timer->>+Notification: タイマー通知を依頼
    Notification->>+UI: タイマー通知を開始
    UI->>User: タイマー通知を表示

    Alarm->>Notification: アラーム通知を依頼
    Notification->>Notification: 通知が鳴動中か確認
    Notification->>Notification: アラーム通知を待機

    User->>UI: タイマー通知を停止
    UI->>Notification: 通知終了を通知

    Notification->>UI: 待機中のアラーム通知を開始
    UI->>-User: アラーム通知を表示
    Notification-->>-UI: 通知処理完了
```

## 3. 複数のアラーム通知が発生する

> アラームAが鳴っている間に、アラームB・Cの通知時刻になった場合

```mermaid
sequenceDiagram
    actor User as ユーザー
    participant Alarm as アラーム
    participant Notification as 通知管理
    participant UI as 画面

    Alarm->>+Notification: アラームAの通知を依頼
    Notification->>+UI: アラームAの通知を開始
    UI->>User: アラームAのポップアップを表示

    Alarm->>Notification: アラームBの通知を依頼
    Notification->>Notification: 通知が鳴動中か確認
    Notification->>Notification: アラームBを待機

    Alarm->>Notification: アラームCの通知を依頼
    Notification->>Notification: アラームCを待機

    User->>UI: アラームAを停止
    UI->>Notification: 通知終了を通知

    Notification->>UI: アラームBの通知を開始
    UI->>User: アラームBのポップアップを表示

    User->>UI: アラームBを停止
    UI->>Notification: 通知終了を通知

    Notification->>UI: アラームCの通知を開始
    UI->>-User: アラームCのポップアップを表示

    Notification-->>-UI: 通知処理完了
```

## 4. 通知が待機している状態

> 現在の通知が鳴っている間に後続の通知が発生したら、現在の通知が終わるまで待機する。<br>
> 現在の通知が終了したら、待機中の通知を表示する。

```mermaid
sequenceDiagram
    participant Timer as タイマー
    participant Alarm as アラーム
    participant Notification as 通知管理
    participant UI as 画面
    actor User as ユーザー

    Timer->>+Notification: タイマー通知を依頼
    Notification->>+UI: タイマー通知を開始
    UI->>User: タイマー通知を表示

    Alarm->>Notification: アラームAの通知を依頼
    Notification->>Notification: アラームAを待機

    Alarm->>Notification: アラームBの通知を依頼
    Notification->>Notification: アラームBを待機

    Note over Notification: 待機中の通知あり
```