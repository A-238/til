■ Laravel ログイン機能

- laravel/uiを使用して生成したログイン機能
- バリデーションをカスタムしたい場合は**AuthenticatesUsers.php**の「`validateLogin`」メソッドを**LoginController**でオーバーライドする
    
    ```php
    protected function validateLogin(Request $request)
    {
        $request->validate([
            $this->username() => 'required|string',
            'password' => 'required|string|max:8',
        ]);
    }
    ```
    
- ログイン認証失敗時のエラーメッセージをemail入力欄の横に出力したくない場合は**AuthenticatesUsers.phpの**「`sendFailedLoginResponse`」メソッドを**LoginController**でオーバーライドする
    
    ```php
    protected function sendFailedLoginResponse(Request $request)
    {
        throw ValidationException::withMessages([
            'login_failed' => [trans('auth.failed')],
        ]);
    }
    ```
    
- その後、**login.blade.php**にて下記のコードを変更する
    
    ```php
    @error('email')
              <div class="em" style="color: red;">{{ $message }}</div>
    @enderror
    
    ↓↓
    
    @error('login_failed')
              <div class="em" style="color: red;">{{ $message }}</div>
    @enderror
    ```