### Размещение
Для создания заказа отправить POST запрос на адрес  
`https://gateway.chocodev.kz/orders/v1/preorder/create`  
Headers:  
`Content-Type: x-application/x-www-form-urlencoded`  
со следующими данными:

Ключ | Описание | Пример
--- | --- | ---
merchant_order_id | ID заказа в вашей системе **required** | 100500
amount | Сумма заказа для оплаты через Rahmet **required** | 2500
token | Токен для определения филиала **required** | hash, выдается нами
backlink | DeepLink приложения, на которое мы отправим пользователя (чаще всего, ThankYouPage) | https://project.kz/backend/setStatus?id=100500&paid=true
postlink | Ссылка для оповещения вашего бэка после оплаты (GET) | https://project.kz/backend/order/100500/setPaid
image_size | Размер картинки, если требуется вернуть QR в формате PNG/base_64 | 300
timeout | Срок действия заказа (в секундах) | 3600

### Ответ
```
{
    "error_code": 0,
    "status": "success",
    "message": "Предзаказ создан",
    "data": {
        "preorder_id":      111,
        "url":              "https://rahmetapp.kz/?id=HASH",
        "qr_image_base_64": "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAASwAAAEsCAIAAAD2HxkiAAAACXBIWXMAAA7EAAAOxAGVKw4bAAAFLElEQVR4nO3dS2okMRBAwbHx/Y9s5gLDWBihl6qKWDdd30dtEunjz4t9f3//+JvPz89Rx1r5nxW7jnXyf57qvVcOQ4gQYiKEmAghJkKIiRBiIoSYCCEmQoiJEGIihNjXyo92zSuedHIWcdf9uXHG8uS78dT3cNYThRcSIcRECDERQkyEEBMhxEQIMRFCTIQQEyHERAixpdnRFTfOau461lPX3jy55uouN76Hs546vJAIISZCiIkQYiKEmAghJkKIiRBiIoSYCCEmQohtmx19sxv3o19x47zrjdxBiIkQYiKEmAghJkKIiRBiIoSYCCEmQoiJEGIihJjZ0R9Mm/lcOdbJmc8b95GfxpcQYiKEmAghJkKIiRBiIoSYCCEmQoiJEGIihJgIIbZtdvTNM4Qn50tXTDufk268Ll9CiIkQYiKEmAghJkKIiRBiIoSYCCEmQoiJEGIihNjS7Kh9yf/v5J71T/2fFU99D595VXAREUJMhBATIcRECDERQkyEEBMhxEQIMRFCTIQQ+7pxncanunG90F3nM+26TvIlhJgIISZCiIkQYiKEmAghJkKIiRBiIoSYCCEmQoh9nDzYtPUnd62refJYJ2csT65NetK093DW3YEXEiHERAgxEUJMhBATIcRECDERQkyEEBMhxEQIsaV1R7fNyB2cjZy2b/tJJ89n2j28ckb32JGAfxIhxEQIMRFCTIQQEyHERAgxEUJMhBATIcRECLGj647uMm2ec9o6ljfOau5y47X7EkJMhBATIcRECDERQkyEEBMhxEQIMRFCTIQQEyHEltYdnWbaupEnnVyX9aSnns/SfOmWIwG/JkKIiRBiIoSYCCEmQoiJEGIihJgIISZCiIkQYh/TZvZO7oF+45qZu0y7rqfOA1t3FC4gQoiJEGIihJgIISZCiIkQYiKEmAghJkKIiRBiXys/mjbPuWLafOmb97XfZdp86a77M+suwwuJEGIihJgIISZCiIkQYiKEmAghJkKIiRBiIoTYx64/unEWccW0WcRp57PLjde1652/rwp4GBFCTIQQEyHERAgxEUJMhBATIcRECDERQkyEENu2Z701PM+Ydp9vfF4rjj7TY0cC/kmEEBMhxEQIMRFCTIQQEyHERAgxEUJMhBATIcS2rTu6YtqM5S7TZiOfugbsLuPmpXecDPB7IoSYCCEmQoiJEGIihJgIISZCiIkQYiKEmAghtm3d0aeaNoN648zntJnhaedz3xOFhxEhxEQIMRFCTIQQEyHERAgxEUJMhBATIcRECLGvG2cRd1mZIXzq/u+77Hp/brz2Xd5bIAwhQoiJEGIihJgIISZCiIkQYiKEmAghJkKIiRBiXys/unFm7+RM4y7T5lRPuvEdW2HPeriACCEmQoiJEGIihJgIISZCiIkQYiKEmAghJkKIfaz8aNos4o1reE47nxXT5kt32XWft80nb/kX4NdECDERQkyEEBMhxEQIMRFCTIQQEyHERAgxEUJsad1Rzji5puiu+clp53Nyvdld1+5LCDERQkyEEBMhxEQIMRFCTIQQEyHERAgxEUJMhBAzO/qDXTOE2+YML5yN3OWp1+5LCDERQkyEEBMhxEQIMRFCTIQQEyHERAgxEUJMhBDbNjs6bb/1k6bNl06b+Vxx8nxOrrm6YtaTgBcSIcRECDERQkyEEBMhxEQIMRFCTIQQEyHERAixpdnRaXOGN5p2D0/O+t64r/3JY816M+CFRAgxEUJMhBATIcRECDERQkyEEBMhxEQIMRFC7C9/2YhD8YM5vwAAAABJRU5ErkJggg==""
    }
}
```
_url - ставить эту ссылку для оплаты или сформировать с нее QR_
