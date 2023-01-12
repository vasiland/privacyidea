# privacyidea

Авторизация  получаем токен
curl -k -X POST -F 'username=user' -F 'password=pass' https://site.local/auth

Проверяяем 
curl -k -X GET https://site.local/auth/rights -H "accept: application/json" -H "authorization: Токен_от_авторизации"

Готовим HEX 
echo Секрет_который_получен | base32 -d | hex


curl -k -X POST -F 'otpkey=hex(полученный ранее)' -F 'user=пользователь' -F 'raelm=ИМЯ' -F 'type=totp' https://site.local/token/init  -H "authorization: Токен_от_авторизации"
