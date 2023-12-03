# deploy-test

## Инициализация директории

```bash
npx @vkontakte/create-vk-mini-app deploy-test
cd deploy-test
```

## Локальный запуск

### Подготовка

__Примечание:__ перед следующими шагами требуется создать мини-приложение на [https://vk.com/apps?act=manage](https://vk.com/apps?act=manage)

```bash
npm install @vkontakte/vk-tunnel --include=dev
```

Далее добавляем в `package.json` скрипт `tunnel`:

```json
"scripts": {
  ...
  "tunnel": "vk-tunnel --insecure=1 --http-protocol=https --ws-protocol=wss --host=0.0.0.0 --port=10888"
}
```

### Запуск

Чтобы запустить приложения потребуется два окна терминала.

В первом окне:

```bash
npm start
```

Во втором окне:

```bash
npm run tunnel
```

Подтверждаем запуск и вставляем полученные ссылки в настройки приложения.

## Деплой на VK Cloud

```bash
npm install @vkontakte/vk-miniapps-deploy --include=dev
```

Далее указываем app_id из настроек приложения в `vk-hosting-config.json`:

```json
{
  "static_path": "build",
  "app_id": <APP_ID>,
  "endpoints": {
    "mobile": "index.html",
    "mvk": "index.html",
    "web": "index.html"
  }
}
```

Далее:

```bash
npm run deploy
```

Подтвержаем действия и вставляем полученные ссылки в настройки приложения.