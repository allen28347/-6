# build_server
編譯伺服器，透過Ansible Playbook操作，讓服務器可以自己Git抓程式碼下來，自己做程式碼分析、自動化測試、自動編譯、自動上版

## 資料夾結構
resources 用來存放軟體相關設定檔用

tasks 用來存放分類存放要安裝、設定的Ansible Playbook排程

.env.swp Ansible Playbook主機參數檔

install.yml 用來安裝所需之套件

config.yml 用來設定相關之設定

## Ansible Playbook 操作流程
1. 將./env/env.swp檔名改成.env
2. 設定.env中，對應的主機名與IP，可一次設定多台
3. 運行以下指令安裝所需之套件
```
ansible-playbook -i .env install.yml --ask-become-pass
```
4. 輸入登入用密碼
5. 等全部的所需套件都安裝完成，並且沒有跳Fail
6. 運行以下指令設定服務器
```
ansible-playbook -i .env config.yml --ask-become-pass
```
7. 輸入登入用密碼
8. 等全部的所需套件都安裝完成，並且沒有跳Fail