## Проверка

В силу того, что все мы _стоим на плечах гигантов_, Rahmet Pay может не работать, когда не работает какой-то из наших провайдеров.  

Перед тем, как показывать пользователям способ оплаты через Rahmet Pay и создавать заказы, необходимо сделать проверку на доступность сервиса.

## Запрос

Для проверки доступности необходимо выполнить вызов метода  
`https://gateway.chocodev.kz/orders/v1/preorder/availability`  
(в заголовке не забываем [Content-Type](/#_3) и [токен](/auth))  

## Ответ

В ответ сервер возвращает JSON с указанными [здесь](/#_4) составляющими.  

Возможные варианта ответа: 
```
{
    "error_code": 0,
    "status": "success",
    "message": "Доступность оплаты",
    "data": {
        "available": true
    }
}
```
```
{
    "error_code": 0,
    "status": "success",
    "message": "Доступность оплаты",
    "data": {
        "available": false
    }
}
```