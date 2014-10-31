


```
gem "sorcery"
```

bundle install

rails generate sorcery:install

rails generate sorcery:install remember_me reset_password


rails g controller me index
MeControllerに
```
  before_filter :require_login
```
をくわえる。
