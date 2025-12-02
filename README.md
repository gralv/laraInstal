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

## Консоль openServer для VSCode
- создать файл d:\OS646\home\vue7.lara\www\.vscode\settings.json - изменить на свой путь к проекту
- добавить
```
{
    "terminal.integrated.defaultProfile.windows": "OpenServer",

    "terminal.integrated.profiles.windows": {
        "OpenServer": {
            "path": "C:\\Windows\\System32\\cmd.exe",
            "args": [
                "/k",
                "D:\\OS646\\bin\\osp.bat reset init noprint & D:\\OS646\\bin\\osp.bat project vue7.lara"
            ],
            "cwd": "D:\\OS646\\home\\vue7.lara\\www"
        }
    }
}
```
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
### example app.js
```
import './bootstrap';
import '../css/app.css';
import {createApp, defineAsyncComponent} from 'vue/dist/vue.esm-bundler.js';


const RootComponent1 = createApp({
    data() {
        return {
            message: 'Hello root Component 1',
        };
    },
    components: {
        ExampleComponent: defineAsyncComponent(() =>
            import('/resources/js/components/ExampleComponent.vue')
        )
    },
},);
RootComponent1.mount('#root-component-1');
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
## Install bootstrap
```
npm install bootstrap
npm install sass
```
- создать файл **resources/sсss/app.scss** с содержимым https://github.com/twbs/bootstrap-npm-starter/blob/main/scss/starter.scss
- там же файл иконок **_icon-list.scss** https://github.com/twbs/bootstrap-npm-starter/blob/main/scss/_icon-list.scss
- в файл **resources/js/bootstrap.js** добавить
```
import "../scss/app.scss"
import * as bootstrap from 'bootstrap'
```
- возможно в файл vite.config.js добавить
```
resolve: {
        alias: {
            // '@': '/resources/js',
            // 'vue': '../node_modules/vue/dist/vue.esm-bundler.js',
               '~bootstrap': path.resolve(__dirname, 'node_modules/bootstrap'),
        },
    },
```
- частично информация бралась https://creagia.com/blog/using-laravel-vite-with-bootstrap-and-sass
- Полный гайд по SCSS/SASS https://medium.com/nuances-of-programming/полный-гайд-по-scss-sass-b09ae0c87afe

# Установка VUE для laravel 12
- Для первого пункта — установки Vue 3 и плагина Vite для Vue — вам нужно выполнить следующую команду в терминале, находясь в директории проекта:
```
npm install vue@next @vitejs/plugin-vue
```
# VSCode установка агентов AI
https://www.youtube.com/watch?v=4mZLmNPwfYI
авторизации в поролях по имени VSCode Agent AI

# VSCode подключение gemini
- после авторизации при ошибке
```
Failed to login. Message: This account requires setting the GOOGLE_CLOUD_PROJECT or GOOGLE_CLOUD_PROJECT_ID env    │
│   var. See https://goo.gle/gemini-cli-auth-docs#workspace-gca
```
- смотрим https://www.youtube.com/watch?v=Mf_p4mnyceg
- переходим по https://goo.gle/gemini-cli-auth-docs#workspace-gca
- создать проект в https://console.cloud.google.com/apis/dashboard?pli=1&project=bold-meridian-160318
- установка прав для проекта
- в консоли export GOOGLE_CLOUD_PROJECT="YOUR_PROJECT_ID" или
- создать в проекте папку .gemini и файл .env с записью
```
GOOGLE_CLOUD_PROJECT="myproject1-479712"
```

