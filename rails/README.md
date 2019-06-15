# Ruby on Rails

### 指定したキーがないときにエラーを出さないようにする

```ruby
params.fetch(:user, {}).permit(:name, :email, :password)
```

user パラメータがなかったときは ActionController::ParameterMissing のエラーが起きるようになっています。
上記の設定をしてあると user パラメータの代わりに{}がデフォルト値として評価されるようになります。

## Model

### Validations

[https://qiita.com/shunhikita/items/772b81a1cc066e67930e](https://qiita.com/shunhikita/items/772b81a1cc066e67930e)

### has_secure_password

[https://qiita.com/shumpeism/items/4d8946ade2dbdccab31c](https://qiita.com/shumpeism/items/4d8946ade2dbdccab31c)

## Gems

### seed_fu

Managament Seed Files

[https://rubygems.org/gems/seed-fu](https://rubygems.org/gems/seed-fu)

[https://bagelee.com/programming/make-data-with-seed-fu/](https://bagelee.com/programming/make-data-with-seed-fu/)

### HIRB

Rails Console Helper

Command: Hirb.enable

[https://rubygems.org/gems/hirb](https://rubygems.org/gems/hirb)
