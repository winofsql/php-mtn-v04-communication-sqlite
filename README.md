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
    - 社員コードの幅を定義
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

- ✅ syain.php
    - ヘッダー(第一会話) から ボディ(第二会話)への遷移
        ```php
        // $gno が 1 でエラーが無い場合( ここではエラーチェクをしていない )
        // プロテクトコントロール
        $readonly_1 = $disabled_type_text;
        $readonly_2 = "";
        $disabled_1 = $disabled_type;
        $disabled_2 = "";
       
        // 次の画面の会話番号( 確認がクリックされた )
        $gno = 2;
        ```

    - ヘッダー(第ニ会話) から ボディ(第一会話)への遷移
        ```php
        // $gno が 2 でエラーが無い場合( ここではエラーチェクをしていない )
        // プロテクトコントロール
        $readonly_1 = "";
        $readonly_2 = $disabled_type_text;
        $disabled_1 = "";
        $disabled_2 = $disabled_type;
        
        // 次の画面の会話番号( 更新がクリックされた )
        $gno = 1;
        ```

- ✅ syain-view.php ( 画面 )
    - $readonly_1, $disabled_1, $readonly_2, $disabled_2 をそれぞれの会話対象コントロールに埋め込む
        ```html
        <div>
            <div class="entry left">社員コード</div>
            <div class="entry right">
                <input class="form-control w100"
                    required
                    <?= $readonly_1 ?>
                    maxlength="4"
                    pattern="[0-9]+"
                    placeholder="9999"
                    type="text"
                    name="scode"
                    id="scode"
                    value="<?= $_POST["scode"] ?>">
            </div>
            <input <?= $disabled_1 ?> type="submit" name="btn" id="btn" class="btn btn-primary ms-4" value="確認">
        </div>
        
        <div>
            <div class="entry left">氏名
            </div>
            <div class="entry right">
                <input class="form-control"
                    <?= $readonly_2 ?>
                    type="text"
                    name="sname"
                    id="sname"
                    value="<?= $_POST["sname"] ?>">
            </div>
        </div>
        <div>
            <div class="entry left">フリガナ
            </div>
            <div class="entry right">
                <input class="form-control"
                    <?= $readonly_2 ?>
                    type="text"
                    name="fname"
                    id="fname"
                    value="<?= $_POST["fname"] ?>">
            </div>
        </div>
        
        <div class="mt-4">
            <input <?= $disabled_2 ?> type="submit" name="btn" id="btn" class="btn btn-primary" value="更新">
            <span class="ms-5"><?= $_POST["message"] ?></span>
        </div>
        ```
