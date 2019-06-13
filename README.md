### Процесс установки (Linux, macOS, Windows):
#### 1. Склонировать проект
```
git clone https://github.com/SilentNotaryEcosystem/Cil-core.git
cd Cil-core
git checkout tags/latest
```
#### 2. Установить [Node.js (10.15.2) и npm](https://nodejs.org/dist/v10.15.2/node-v10.15.2.pkg)
#### 3. Установить зависимости и запустить ноду
```
npm install
node index.js //запуск ноды
node savePrivateKey.js` //запись приватного ключа в файл (аналог keystore)
```

### Процесс установки (Docker):
#### 1. ...

### Параметры для запуска ноды
Параметры по умолчанию заданы в файле [prod.conf.js](https://github.com/SilentNotaryEcosystem/Cil-core/blob/devel/config/prod.conf.js) (для production сети) и [devel.conf.js](https://github.com/SilentNotaryEcosystem/Cil-core/blob/devel/config/devel.conf.js) (для development сети). 

|Параметр|Описание|
|---|---|
|listenAddr|Заданный адрес|
|port|Заданный порт|
|seedAddr|Адрес seed'а для загрузки ноды|
|rpcUser|Имя пользователя для вызова функций из ноды|
|rpcPass|Пароль для вызова функций из ноды|
|rpcPort|Порт для вызова функций из ноды|
|rpcAddress|Адрес для вызова функций из ноды|
|genesisHash|Хэш генезис блока для настройки тестового окружения|
|conciliumDefContract|Контракт генезис блока для настройки тестового окружения|
|privateKey|Файл с приватным ключом для запуска ноды свидетеля|
|dbPath|директория для хранения файлов с базами данных|есть в конфиге
|seed|запускаемая нода будет являться seed'ом (будет хранить и раздавать адреса тех, кто к ней подключен (peers))|
|strictAddresses|Опция для закрытия соединений с двойными IP адресами|
|txIndex|Опция получения индекса транзакции по хешу|
|watchAddress|Применяется для локальных кошельков. Добавляем адрес кошелька в ноду для отслеживания входящих и исходящих транзакций на этот адрес|
|reIndexWallet|Опция для работы с старыми кошельками. Используется для получения всех транзакций в базе по заданному адресу кошелька.|
|walletSupport|Булевая функция. поддерживает ли нода кошельки|
|listWallets|Служебная функция. Показать какие адреса, которые добавлены в ноду|

### Запуск ноды development сети
Необходимо установить переменную окружения NODE_ENV в значение Devel.
Для вывода отладочной информации необходимо установить переменную DEBUG. 
В компонентах которые поддерживают отладку в начале файла есть тэг, который используется для debug.

Пример (Linux):
```
NODE_ENV=Devel DEBUG=peer:*,node:* node index.js
```

### Тестирование
#### Запуск тестов
```npm test```
#### Запуск тестов c выводом отладочной информации
* run ```npm run-script testDebugNix``` for *nix
* run ```npm run-script testDebugWin``` for Windows
