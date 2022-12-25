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

```
sudo apt install fcitx-mozc && $(check-language-support -l ja)
im-config -n fcitx 
reboot
```
