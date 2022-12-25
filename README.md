# Ubuntuの初期設定手順 2023年版

- Ubuntu22.10をインストールしたのでその際の作業メモ

## 手順

- 事前準備
  - Windowsの回復ドライブの作成
  - Ubuntuのインストールメディアの作成
- Ubuntuインストールと初期設定
  - Ubuntuのインストール
  - apt packageのインストール
  - CapsLockキーをCtrlキーにする
  - IMEの日本語設定
  - Google Chromeのインストール
  - SSHキーの設定
  - GPGキーの設定
  - Dockerのインストール

### Ubuntuインストールと初期設定

#### apt packageのインストール

```
sudo apt update && sudo apt dist-upgrade && sudo apt autoremove
```

```
sudo apt install \
  build-essential \
  git \
  gnupg \
  vim \
  xsel \
  dconf-editor \
  curl \
  tree \
  net-tools \
  nmap \
  python-is-python3 \
  python3-pip \
  unzip \

```

#### CapsLockキーをCtrlキーにする

```
gsettings set org.gnome.desktop.input-sources xkb-options "['ctrl:nocaps']"
```

#### IMEの日本語設定（ibus-mozc）

```sh
$(check-language-support -l ja)
```

- Settings > Keyboard > Input Sources の設定を変更する
  - Input Sources に `Japanese (Mozc)` を追加する
  - Input Sources に `Japanese` を追加する
    - この設定を変更しないとIMEがJIS配列キーボードに対応しない

<img src="https://user-images.githubusercontent.com/15353515/209467014-1889fafa-ddeb-4646-bd1a-e2bd6bca9140.png" width="600px" />

- Japanese (Mozc)の設定を変更する
  - General > Keymap > Keymap style を変更する
    - 以下画像の8項目を設定する

<img src="https://user-images.githubusercontent.com/15353515/209467152-694bb8b5-e942-4176-b646-d59ea342847b.png" width="600px" />


#### IMEの日本語設定（fcitx-mozc）

- 以下のコマンドで `fcitx-mozc` をインストールする

```
sudo apt install fcitx-mozc && $(check-language-support -l ja)
im-config -n fcitx 
reboot
```

- fcitxの設定を変更する
  - Configure > Input Method を設定する
    - Keyboard - Japanese の追加
    - Mozc の追加
  - Configure > Global Config > Hotkey を設定する
    - Activate Input Method を設定
    - Inactivate Input Method を設定

<img src="https://user-images.githubusercontent.com/15353515/209463108-38beb08f-7202-4854-87bc-c383a44d339f.png" width="600px" />
<img src="https://user-images.githubusercontent.com/15353515/209463170-61ee2fba-87f1-414e-b946-d0a8fb23ec5f.png" width="600px" />


Settings > Keyboard > Input Sources の設定を手動で変更する
  - Input Sources に `Japanese` を追加して既存の設定を置き換える 
  - この設定を変更しないとターミナルがJIS配列キーボードに対応しない

<img src="https://user-images.githubusercontent.com/15353515/209462931-40a52df6-8345-4d9b-8bfa-a4267f5ccfce.png" width="600px" />

#### SSHキーの設定

```
ssh-keygen
cat .ssh/id_rsa.pub | xsel -ib
```

#### GPGキーの設定

```
sudo apt install gnupg
gpg --allow-secret-key-import --import PASS_TO_MASTER_KEY
gpg --edit-key KEY_ID
# trust
# set ~/.gitconfig
```

#### Dockerのインストール

- https://docs.docker.com/engine/install/ubuntu/

