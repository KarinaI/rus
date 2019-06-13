### 1. Executables
- index.js - главный файл для запуска ноды
- savePrivateKey.js - файл для записи приватного ключа в файл (аналог keystore)

### 2. Node launch
- **win**
- **mac**
- **from sources**

*Node launch for Linux:*
```
sudo apt update
sudo apt -y install npm
sudo npm i -g n
sudo n 10.15.2
git clone https://github.com/SilentNotaryEcosystem/Cil-core.git
cd Cil-core
git checkout tags/latest
npm i
```
- **docker**
### 3. Ключи для запуска ноды

По умолчанию константы заданы в файле prod.conf.js (для production сети) и devel.conf.js (для development сети). 

Их можно переопределить с помощью ключей:

|Ключ|Описание|
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

### 4. Запуск ноды тестовой сети

Необходимо установить переменную окружения NODE_ENV в значение Devel.
Вывод отладочной информации установка переменной DEBUG. 

В компонентах которые поддерживают отладку в начале файла есть тэг, который используется для debug.

Так запускается нода тестовой сети с отладкой под linux:
```
NODE_ENV=Devel 
DEBUG=peer:*,node:* 
node index.js
```

### 5. Тестирование

* run tests ```npm test``` <br> 
if you want tonns of debug info
* run ```npm run-script testDebugNix``` for *nix
* run ```npm run-script testDebugWin``` for Windows
