# Ubuntuの初期設定手順 2023年版

- Ubuntu22.10をインストールしたのでその際の作業メモ

## 手順

- 事前準備
  - Windowsの回復ドライブの作成
  - Ubuntuのインストールメディアの作成
- Ubuntuインストールと初期設定
  - Ubuntuのインストール
  - apt packageのインストール
  - CapsLockキーとCtrlキーの入れ替え
  - IMEの日本語設定
  - Google Chromeのインストール

### Ubuntuインストールと初期設定

#### apt packageのインストール

```
sudo apt update && sudo apt dist-upgrade && sudo apt autoremove
sudo apt install build-essential git vim xsel dconf-editor curl tree net-tools nmap python-is-python3 python3-pip unzip
```

#### CapsLockキーとCtrlキーの入れ替え

```
gsettings set org.gnome.desktop.input-sources xkb-options "['ctrl:nocaps']"
```

#### IMEの日本語設定

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
    
![image](https://user-images.githubusercontent.com/15353515/209463108-38beb08f-7202-4854-87bc-c383a44d339f.png)
![image](https://user-images.githubusercontent.com/15353515/209463170-61ee2fba-87f1-414e-b946-d0a8fb23ec5f.png)


Settings > Keyboard > Input Sources の設定を手動で変更する
  - Input Sources に `Japanese` を追加して既存の設定を置き換える 
  - この設定を変更しないとターミナルがJIS配列キーボードに対応しない

![image](https://user-images.githubusercontent.com/15353515/209462931-40a52df6-8345-4d9b-8bfa-a4267f5ccfce.png)


