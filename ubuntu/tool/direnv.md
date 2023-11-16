# Ubuntuでのインストール方法
 - `$ sudo apt-get update`
 - `$ sudo apt-get install -y direnv`
 - `$ vi ~/.bashrc`
   - bashrcファイルの最後に次の行を追加
     - `eval "$(direnv hook bash)"`
 - `$ source ~/.bashrc`