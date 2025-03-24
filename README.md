
# Мотивация
У моего знакомого(далее заказчик) есть небольшая проектная компания. Он хочет в будущем вывести её на IPO. Для подготовки к сложной задаче, заказчик попросил меня создать крипто-токен, аналог акций его компании. Я как раз вникал в тему криптовалют и принял его "вызов".

# Крипто-токен
Мой заказчик хотел, чтобы его токен брал комиссию при продаже. Это стимулирует держать акцию дольше и уберегает долгосрочных держателей от спекулянтов, которые хотят заработать на быстрых скачках цены вверх и вниз. При этом необходимо оставить возможность её менять от 0 до 10%.<br><br>
Для токена я выбрал сеть TON и язык TACT, потому что на тот момент знал их лучше всего. Главная проблема на этом этапе была реализовать плавующую комиссию. Я это решил так: при отправке токенов на продажу, транзакция проходит через контракт-прослойку, в котором сохранена текущая комиссия. Таким образом изменяя комиссию в контракте-прослойке, можно менять ее при продажах.<br><br>
[Пример продажи с комиссией.](https://tonviewer.com/transaction/e605cce0988d0fde74b4a9f9f8c084d94688af93daac1c8c8e4cf9709c5382ba)<br>
В данном примере видно, что с кошелька "[B](https://tonviewer.com/EQAVJ-ULEh5jzeSkFs3gw0xXkCers2wacGau840AW_WuPfQf)" отправляется транзакция на контракт "[C](https://tonviewer.com/EQAKwGt6wEK6zvoBRVp0UDygtcCZe_nrI_VAG9ktBeqhsF3b)", а потом обратно на "B". В контракте "С" и записана комиссия на продажу.<br><br>
Я рад, что смог выполнить нетривиальную задачу со столь небольшим удорожанием транзакции (на 0.03$).<br><br>
Ссылки:
+ [адрес токена](https://tonviewer.com/EQB4bnS7oHHVfHUAS7Qb-Xjqc-ALA_Pz-_K3PqBCb5fW6XIP)
+ [код токена](https://tonviewer.com/EQB4bnS7oHHVfHUAS7Qb-Xjqc-ALA_Pz-_K3PqBCb5fW6XIP?section=code)
  <br>
# NFT
# Сайт
Заказчик считает, что для плавого погружения пользователей в мир криптовалют необходимо им рассказать о базовых вещах: 'Как создать крипто-кошелек?', 'Как купить крипто-токен?', 'Как его продать?'.<br>
Необходим свой miniapp в Telegram. Заказчик также попросил добавить:<br>
+ немного информации о Telegram каналах
+ отображение монет на балансе кошелька
+ больше способов покупки (покупка через кошеле авторов и переводом на карту, а также, в будущем через СБП)
<br>
Я использовал базовый комплект web-разработчика: HTML, CSS, Javascript. Сложностей не возникало. Самая интересная часть - это работа с бибилиотекой TonConnect, которая позволяет подключать криптокошельки к сайту и упрощающет отправку транзакций в блокчейн.<br>
Самый удбный способ посмотреть на сайт - это <a href="https://t.me/BIPapp_bot/app">miniapp</a> в Telegram, но можно и через <a href="https://app.biptoken.xyz?tg_mode=true">браузер</a>.<br><br>
Информацию о разработчике можно узнать здесь: https://biptoken.xyz/authors.json , среди прочего есть ссылка на этот Github.

# API 
Для корректной работы сайта необходим API сервис.<br>
Я выбрал язык Python и библиотеку FastAPI, так-как сервис пока не планируется высоконагруженым, максимум - 1-2 RPS, а так-же важна скорость разработки. FastAPI подошел лучше всего.<br>
Через API сайт получает цену токенов и отдает информацию о Telegram User.<br><br>
В моем случае, он также используется для определения картинки для NFT, по количеству токенов "запакованных" в ней.<br>
Каждая NFT содержит ссылку на свою meta информацию. Пример: https://nft.biptoken.xyz/CreateItemMetadata?value=4242 ,при создании NFT в поле value передается количество токенов, которое она "содержит".<br>
В поле "image" возращается нужная ссылка на изображение.<br>

# Итог
#### Я написал комиссионный крипто-токен, создал NFT коллекцию и сайт для него. <br>Заказчик остался доволен, а я получил необходимый опыт.
