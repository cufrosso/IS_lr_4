# Разработка приложения реального времени
## Текст задания
### Цель работы
Разработать и реализовать игру пинг-понг. Хранение и отработка модели происходит на сервере. Общение сервера и клиентов происходит по *websoket*. Для отрисовки вида используется *canvas*. Игра завершается при достижении нужного счёта одним из игроков.
## Ход работы
- Пользовательский интерфейс
- Пользовательские сценарии работы
- API сервера и хореографию
- Структура базы данных
- Алгоритмы
1) [Пользовательский интерфейс](https://www.figma.com/file/OmdQOaygiM84p9MuDEr4Aa/IS_lr_4?node-id=0%3A1&t=1VZWs9ntujbsojhk-1)

2) Пользовательские сценарии работы

Пользователь попадает на страницу *index.php*.

3. API сервера и хореография

![Добавление]()

![Удаление]()

4. Структура БД

5. Алгоритмы

*Add post*

![add]()

*Delete post*

![delete]()

*Reaction*

![Reaction]()

6. HTTP запросы/ответы

*Запрос*

GET /lr_4_/serv.js HTTP/1.1 <br>
Host: localhost <br>
Accept: */* <br>
sec-ch-ua: "Not_A Brand";v="99", "Google Chrome";v="109", "Chromium";v="109" <br>
sec-ch-ua-mobile: ?0 <br>
sec-ch-ua-platform: "Windows" <br>
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/109.0.0.0 Safari/537.36 <br>

*Ответ*

HTTP/1.1 200 OK <br>
Accept-Ranges: bytes <br>
Content-Length: 7738 <br>
Content-Type: application/javascript <br>
Date: Wed, 11 Jan 2023 22:42:55 GMT <br>
ETag: "1e3a-5f1f159537471" <br>
Last-Modified: Tue, 10 Jan 2023 23:36:11 GMT <br>
Server: Apache <br>
X-Content-Type-Options: nosniff <br>

7. Значимые фрагменты кода

*Функция отрисовки игры*
```js
function draw() {
    game.draw(); // игровое поле
    // разделительная полоса
    for (var i = 10; i < game.height; i += 45) {
        context.fillStyle = "#ccc";
        context.fillRect(game.width / 2 - 10, i, 20, 30);
    }
    // рисуем на поле счёт
    context.font = 'bold 128px courier';
    context.textAlign = 'center';
    context.textBaseline = 'top';
    context.fillStyle = '#ccc';
    context.fillText(ai.scores, 100, 0);
    context.fillText(player.scores, game.width - 100, 0);
    ai.draw(); // левая ракетка
    player.draw(); // ракетка игрока
    ball.draw(); // шарик
    if (!start) {
        // вывод статстики
        context.fillStyle = "#ccc";
        context.globalAlpha = 0.7;
        context.fillRect(0, 0, game.width, game.height);
        context.font = 'bold 16px courier';
        context.textBaseline = 'top';
        context.fillStyle = '#000';
        context.fillText("Total: " + game.total + " Win: " + game.win + " Lose: " + game.lose, game.width / 2, 0);
        context.font = 'bold 60px courier';
        context.textBaseline = 'top';
        context.fillStyle = '#000';
        context.font = 'bold 16px courier';
        context.textBaseline = 'top';
        context.fillStyle = '#000';
        context.fillText("click on me", game.width / 2, game.height / 2 + 25);
        context.textBaseline = 'bottom';

    }
}
```

