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
