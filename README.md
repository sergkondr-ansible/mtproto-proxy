mtproto-proxy
=========

The role runs official docker container of the mtproto-proxy and send necessary parameters to you.

You can set secret key for proxy(`mtproto_secret_key`) manually, or it will be generated automatically.

Role Variables
--------------
```
    mtproto_proxy_port: 8000
    mtproto_secret_key: ''

    mtproto_send_parameters: yes
    mtproto_telegram_token: ''
    mtproto_telegram_chat_id: 0000000
```

To get chat id, do the following:
1. Add your bot to group or send message to it
2. Go to this page(or curl to it): https://api.telegram.org/bot{{ mtproto_telegram_token }}/getUpdates
3. Find the object named 'chat' and take it's parameter 'id'

Example Playbook
----------------

```
    - hosts: servers
      roles:
         - { role: mtproto-proxy, mtproto_telegram_token: '000000000:0123456qwerty', mtproto_telegram_chat_id: 0000000 }
```

License
-------

WTFPL

Author Information
------------------

[Sergey Kondrashov](https://github.com/sergkondr)
