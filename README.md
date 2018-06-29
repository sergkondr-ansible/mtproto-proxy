mtproto-proxy
=========
[![Build Status](https://travis-ci.com/sergkondr-ansible/mtproto-proxy.svg?branch=master)](https://travis-ci.com/sergkondr-ansible/mtproto-proxy)

The role runs official docker container of the mtproto-proxy and send necessary parameters to you.

You can set secret key for proxy(`mtproto_secret_key`) manually, or it will be generated automatically.

Requirements
------------
The role requires Docker 17.03 or higher installed.

Role Variables
--------------
```
    mtproto_proxy_port: 8000
    mtproto_secret_key: ''

    mtproto_send_parameters: no
    mtproto_telegram_token: ''
    mtproto_telegram_chat_id: 0000000
```

To create your own telegram-bot, see: https://core.telegram.org/bots

To get chat id, do the following:
1. Add your bot to group or send message to it
2. Go to this page(or curl to it): https://api.telegram.org/bot{{ mtproto_telegram_token }}/getUpdates
3. Find the object named 'chat' and take it's parameter 'id'

Example Playbook
----------------

Install mtproto-proxy, generate secret-key and send it to specified chat via bot:
```
    - hosts: mtproto-proxy
      roles:
         - { role: mtproto-proxy, 
             mtproto_send_parameters: yes, 
             mtproto_telegram_token: '000000000:0123456qwerty', 
             mtproto_telegram_chat_id: 1234567 
           }
```
Install mtproto-proxy with specified secret-key:
```
    - hosts: mtproto-proxy
      roles:
         - { role: mtproto-proxy, mtproto_secret_key: 'qazwsxedcrfv00' }
```

License
-------

WTFPL

Author Information
------------------

[Sergey Kondrashov](https://github.com/sergkondr)
