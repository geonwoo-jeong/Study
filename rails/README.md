# Ruby on Rails

### 指定したキーがないときにエラーを出さないようにする
```ruby
params.fetch(:user, {}).permit(:name, :email, :password)
```

userパラメータがなかったときはActionController::ParameterMissingのエラーが起きるようになっています。
上記の設定をしてあるとuserパラメータの代わりに{}がデフォルト値として評価されるようになります。
