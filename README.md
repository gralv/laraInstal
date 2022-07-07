# laraInstal
## Composer openServer phpstorm
- доступ к команде composer из терминала phpstorm
- положить phpstorm как закладку в панель openserver "Мои закладки". Настройки -> Закладки "путь к phpstorm64.exe"
## Laravel install в текущую папку без создания подпапки
```
composer create-project laravel/laravel . 
```
- работает если папка пуста 
- не работает если предварительно открыть папку в phpstorm тот добавляет свою папку проекта
## Запуск laravel на openserver->nginx
- скопировать файл \userdata\config\Nginx_1.21_vhost.conf -> projectLaravel\public\Nginx_1.21_vhost.conf
- раскоментировать строку rewrite ^/(.*)$ /index.php?/$1 last;
- возможно добавить попку домена в Настройки -> Домены
## Install git openserver
- в папку modules\git\ скопировать portable версию с оф. сайта
## Добавить git и php в cmd
- дополнительные параметры -> переменные среды -> системные переменные -> path
- - добавить
- - modules\php\PHP_8.0
- - modules\git\bin\
