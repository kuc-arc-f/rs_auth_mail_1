# rs_auth_mail_1

 Version: 0.9.1

 Author  : 

 date    : 2026/11/19
 
 update  :

***

Rust Axum , Mail Authrize SQLite Example

* SQLite DB
* node22
* Linux

***
* .env

```
DATABASE_URL=sqlite://app.db
BIND_ADDR=127.0.0.1:3000
# OTP ハッシュ用の秘密文字列 (ランダムな長い値にする)
OTP_PEPPER=change-me-to-a-long-random-string
# HTTPS 運用時は true
COOKIE_SECURE=false
# SMTP (未設定なら OTP はサーバーログに出力 = 開発モード)
SMTP_HOST=smtp.gmail.com
SMTP_USER=your-name
SMTP_PASS=your-pass
SMTP_FROM=App <no-reply@example.com>
```

***
* start
```
cargo build
cargo run
```

***
* test-code
```
# register
curl -X POST localhost:3000/auth/register -H 'content-type: application/json' -d '{"email":"a@example.com","password":"password123"}'

# verify-email code
curl -X POST localhost:3000/auth/verify-email -H 'content-type: application/json' -d '{"email":"a@example.com","code":"123456"}'

# login
curl -c jar -X POST localhost:3000/auth/login -H 'content-type: application/json' -d '{"email":"a@example.com","password":"password123"}'

# show-me
curl -b jar localhost:3000/me

# logout
curl -b jar -X POST localhost:3000/auth/logout
```
***
### version
* V_0_9_1: new

***
### blog

