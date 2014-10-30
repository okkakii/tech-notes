# MacOSX 開発環境セットアップ

## はじめに

みんなの環境どーやって整備するか。
用意しておいて欲しいもの＋α(趣味)メモです。


## いろいろインストール

- Dropbox
- Atom Editor
- GitHub クライアント
- chrome
- firefox
- sublime

## App Store からインストール

- 1password
- evernote
- wunderlist
- twitter
- transmit
- skitch
- witch
- alred


# homebrew をインストール


MacOSXのパッケージ管理のひとつ、homebrewをインストールします。
```
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
で導入してください。

brew 経由でいくつかインストールしておく。
```
brew install pkgconfig
brew install imagemagick
brew install git
brew install wget
```


## シェルの変更。

zshをデフォルトのシェルに切り替えます。
```
chsh -s /bin/zsh
```
で切り替えてください。パスワードを聞かれたら入力してください。

.zshrcを用意する。
```
wget https://raw.githubusercontent.com/rakd/etc/master/zshrc -O ~/.zshrc
```


## ruby用IDEインストール

まずは、
- [Aptana RadRails](http://www.aptana.com/products/radrails)
使ってみましょう。

- RubyMine

みんなで買うと高いので、Aptana RadRailsで不便の場合にrubymine検討しましょう。



## anyenv/rbenv/ruby/rails

rbenv経由でrubyを動かします。

- 参考： http://qiita.com/luckypool/items/f1e756e9d3e9786ad9ea
- 参考： http://qiita.com/budougumi0617/items/45658123196c3dde80ee

まずは、anyenvをインストールします。

```
cd
git clone https://github.com/riywo/anyenv ~/.anyenv
```
また、
```
vim .zshrc
```
で下記を追加してください
```
if [ -d $HOME/.anyenv ] ; then
    export PATH="$HOME/.anyenv/bin:$PATH"
    eval "$(anyenv init -)"
    for D in `ls $HOME/.anyenv/envs`
    do
        export PATH="$HOME/.anyenv/envs/$D/shims:$PATH"
    done

fi
```
anyenv経由でrbenv/ndenvをインストールしておきます。
```
exec $SHELL -l
anyenv install rbenv
anyenv install ndenv
exec $SHELL -l
```


## rubyのインストール

rbenv 経由でrubyをインストールします。
```
rbenv install -l
```
をすることで、インストールできるrubyのバージョンをチェックできます。

2014/10/29時点では、2.1.4がインストールできるっぽいので、
```
rbenv install 2.1.4
```
でインストールします。


また、 2.1.4を利用するために
```
rbenv global 2.1.4
```
としてください。
```
which ruby
```
や
```
ruby -v
```
の挙動を確認してください。


## gem/railsの導入
```
gem install bundler
sudo gem update --system
sudo gem install rails --no-ri --no-rdoc -V
rbenv rehash
```
でインストールします。
```
rails -v
```
や
```
which rails
```
の挙動を確認してください。

## github公式クライアントのダウンロード

https://github.com/ からダウンロードしてきてください。


## mongodb

### mongodb のインストール

http://www.mongodb.org/ からMacOSX用のものをダウンロードしてきてください。

展開して出てきたbinファイル以下を /usr/local/bin/ 以下にコピーしてください。

### mongodbの起動

mongodbのデータを格納するディレクトリをつくります。
```
sudo mkdir /db
sudo mkdir /db/data/
```


起動します。
```
sudo mongod --dbpath=/db/data
```
