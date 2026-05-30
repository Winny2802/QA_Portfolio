## Ошибка авторизации после смены пароля

### Summary 
При попытке входа в профиль с новым паролем (после процедуры смены пароля) выходит ошибка 401 

### Steps:
1. На странице авторизации вкладка "Primary Account" воспользоваться функцией "forgot password"
2. В появившемся поле ввести Email address, после чего нажать "reset password"
3. Перейти в свою почту, изменить пароль
4. После успешной смены пароля попытаться авторизоваться с новым паролем

### Actual Result 
При вводе новых данных сайт выдает окно с ошибкой "Login Failed", в Console: POST https://api.donetick.com/api/v1/auth/login 401 (Unauthorized)

### Expected Result
Происходит успешная авторизация

### Screenshots

![Header](https://github.com/Winny2802/QA_Portfolio/blob/main/assets/fp%20bug.png)



