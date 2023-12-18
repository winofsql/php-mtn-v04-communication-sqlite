# php-mtn-v04-communication-sqlite

- ## 会話コントロールによるコントロールプロテクト

✅ 第一会話\
![image](https://github.com/winofsql/php-mtn-v04-communication-sqlite/assets/1501327/8b96a9fd-dd76-4902-a9c4-45d60e32b01f)

✅ 第二会話\
![image](https://github.com/winofsql/php-mtn-v04-communication-sqlite/assets/1501327/0f2d5f8f-584e-4c27-8539-deb3bbe1310a)

- ✅ setting.css ( コントロール用 css 追加 )
    ```css
    /* 小さなテキスト入力サイズ */
    .w100 {
        width:100px;
    }
    
    /* 入力の行間隔 */
    .entry {
        margin-bottom: 20px;
    }
    
    .form-control {
        border: 1px solid #000000;
    }
    ``` 

- ✅ setting.php
    ```php
    // グローバル変数
    $gno = 0; // 会話番号
    $disabled_type = "disabled";
    $disabled_type_text = "readonly style='background-color:lightgray'";
    
    $readonly_1 = "";
    $readonly_2 = $disabled_type_text;
    $disabled_1 = "";
    $disabled_2 = $disabled_type;
    ```
    - disabled
        - ボタン用
    - readonly
        - 入力フィールド用
