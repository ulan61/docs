## Описание

Добро пожаловать в документацию программного интерфейса для взаимодействия с  
Rahmet Pay.

Интерфейс адреса для **тестовых** интеграций [https://gateway.chocodev.kz](https://gateway.chocodev.kz)  
Интерфейс адреса для **боевой** интеграции [https://gateway.choco.kz](https://gateway.choco.kz)  

Rahmet Pay поддерживает функции:  
&nbsp;&nbsp;&nbsp;&nbsp;- [авторизации](auth.md);  
&nbsp;&nbsp;&nbsp;&nbsp;- [создания заказа](order.md);  
&nbsp;&nbsp;&nbsp;&nbsp;- [проверки статуса заказа](status.md);  
&nbsp;&nbsp;&nbsp;&nbsp;- [возврата денег](refund.md).  

Оплата производится пользователем через клиентское приложение Rahmetapp.  

## Приложение 

*Для проведения тестовых оплат, мы выдаём приложение с предварительно созданным аккаунтом с деньгами на счету.*  

[Ссылка на скачивание приложения](https://www.dropbox.com/s/oqxi9is3kjjp74q/app-develop-debug.apk?dl=0)  
 
Данные для входа в приложение (выбрать вход через email)  
Email: rahmetpay.test@rahmetapp.kz  
Пароль: zqww26ww

## Архитектура 
API использует REST архитектуру. Параметры передаются методом **POST** в теле запроса в формате "key: value".  

В заголовке каждого запроса указывать `Content-Type: application/x-www-form-urlencoded`  

## Ответ

Ответ система выдает в JSON формате, который включает себя следующие параметры:
```
{
    "error_code": 101,
    "status": "error",
    "message": "Неверное имя пользователя или пароль",
    "data": null
}
```
`error_code` - код ошибки  
`status` - результат выполнения запроса (success или error)  
`message` - описание результата выполнения запроса  
`data` - данные, которые вернет система