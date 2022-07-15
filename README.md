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
## Install Vue 3 and Vite config
```
npm install //установит текушие пакеты из package
npm install vue@next vue-loader@next
npm i @vitejs/plugin-vue@2.3.3
composer require innocenzi/laravel-vite:0.2.*
npm i -D vite vite-plugin-laravel
```
### Изменить vite.config.js
```
import { defineConfig } from 'vite'
import vue from '@vitejs/plugin-vue'
import laravel from 'vite-plugin-laravel'

export default defineConfig({
	plugins: [
		vue(),
		laravel()
	]
})
```
### add config/vite.php
```
php artisan vendor:publish --tag=vite-config
```

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
