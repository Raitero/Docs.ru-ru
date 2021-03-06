---
uid: single-page-application/overview/templates/breezeangular-template
title: Просто/угловая шаблона | Документы Microsoft
author: madskristensen
description: Шаблон одностраничного приложения просто/угловая
ms.author: aspnetcontent
manager: wpickett
ms.date: 03/08/2013
ms.topic: article
ms.assetid: db31e909-563a-4516-aadd-62aa210ac7e4
ms.technology: ''
ms.prod: .net-framework
msc.legacyurl: /single-page-application/overview/templates/breezeangular-template
msc.type: authoredcontent
ms.openlocfilehash: faf28a510a83b7fa07585904344176601c2e1f34
ms.sourcegitcommit: 6784510cfb589308c3875ccb5113eb31031766b4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/08/2018
ms.locfileid: "26506693"
---
<a name="breezeangular-template"></a>Просто/угловая шаблона
====================
по [Мэдс Kristensen](https://github.com/madskristensen)

> Шаблон MVC просто/угловая было написано с Ворд колокольчика
> 
> [Загрузка просто и углового шаблона MVC](https://go.microsoft.com/fwlink/?LinkId=286437)


[AngularJS](http://angularjs.org) — библиотеке с открытым исходным кодом из Google для создания приложений на одной странице (SPAs). Он обеспечивает привязку данных, внедрения зависимостей и управления на экране. Объединять его с [BreezeJS](http://www.breezejs.com/?utm_source=ms-spa), главные этапы значительные клиентского приложения HTML/JavaScript имеют другой библиотеке открытым исходным кодом для моделирования данных и управления данными.

Просто/угловая SPA шаблона является разновидностью на [шаблона с использованием KnockoutJS SPA](../introduction/knockoutjs-template.md) включены в ASP.NET и веб-средства 2012.2 обновление. Если у вас есть Visual Studio, вы получите пример SPA запущен и работает в менее 60 секунд.

![](http://www.breezejs.com/sites/all/images/spa-template/NgRunningTodoPage.png)

Внешне приложение очень похож на шаблон использованием KnockoutJS SPA. Но это совершенно другой за кулисами. Шаблон использованием KnockoutJS использует маскирования для привязки данных и необработанные AJAX для доступа к данным. Шаблон просто/угловая использует угловая для привязки данных и просто для доступа к данным. Эти библиотеки включить дополнительные возможности, включая навигацию по страницам и журнала.

Вот о странице приложения.

![](http://www.breezejs.com/sites/all/images/spa-template/NgRunningAboutPage.png)

На этой странице отображаются журнал событий во время текущего сеанса пользователя, включая:

- Разбиение на страницы. Обратите внимание, создание контроллера Todo с #2 и #7.
- Удаленные запросы (3) и локальный кэш запросов (7).
- Сохранение новой (#5, #6) и изменения сущностей (4).
- Изменения, проверки на стороне клиента (9), поэтому пользователь может исправить ошибки перед фиксацией изменений, к базе данных.

Больше для просмотра в данном шаблоне, включая:

- Динамическая загрузка шаблонов представлений HTML.
- Привязка пользовательских данных до момента «директивы».
- Внедрение модульности и зависимостей.
- Фильтры запросов, сортировка, разбиение по страницам, проекции и включения связанных сущностей.
- Совместное использование данных на нескольких экранах.
- Сохранение нескольких изменений в одной транзакции.
- Правила проверки распространяются автоматически с сервера на клиент JavaScript.

Итак, начнем.

## <a name="create-a-breezeangular-template-project"></a>Создание проекта шаблона просто и углового

Загрузите и установите шаблон, нажав кнопку «Загрузить» выше. Шаблон упаковывается в виде файла расширения Visual Studio (VSIX). Может потребоваться перезапустить Visual Studio.

В **шаблоны** выберите **установленные шаблоны** и разверните **Visual C#** узла. В разделе **Visual C#** выберите **Web**. В списке шаблонов проектов выберите **веб-приложение ASP.NET MVC 4**. Имя проекта и нажмите кнопку **ОК**.

В **новый проект** мастера выберите **углового SPA просто**.

![](http://www.breezejs.com/sites/all/images/spa-template/SelectBreezeNgSpaTemplate.png)

Нажмите Ctrl + F5, чтобы построить и запустить приложение без отладки, или нажмите клавишу F5 для запуска без отладки.

![](http://www.breezejs.com/sites/all/images/spa-template/ZephyrLogin.png)

При первом запуске приложения оно отображает экран входа. Щелкните ссылку «Регистрация» и glides новую страницу в представлении, где можно ввести имя пользователя и пароль. (Страницы входа и регистрации создаются с помощью ASP.NET MVC.) Для отправки формы регистрации сервера приводит к возникновению ошибки TodoList с двумя элементами для вашей учетной записи. Затем он возвращает их вам желтый заметки.

![](http://www.breezejs.com/sites/all/images/spa-template/TodoList.png)

Теперь вы находитесь в Земли SPA. Все, что вы просматриваете и возникают во время обработки Todos к просмотру и управляется на клиенте с помощью Knockout и просто. Исследовать приложения, имени пользователя... но с глаз разработчика. Используйте инструменты разработчика в браузере для записи сетевого трафика. (В Internet Explorer: нажмите клавишу F12, выберите **сети** и нажмите кнопку **начать захват**.) Теперь выполните следующее:

- Добавьте новый элемент Todo.
- Щелкните метку и изменить заголовок элемента Todo
- Установите флажок, чтобы пометить элемент done. Обратите внимание, что текстовое поле отключено, поэтому заголовок больше не является редактируемой.
- Нажмите кнопку «x» справа от метки. Элемент исчезнет и удаляется из базы данных.
- Выберите другой элемент и очистить его название. Вы получите ошибку проверки, что заголовок является обязательным. После небольшой паузы восстанавливается предыдущих заголовка.
- Введите в нелепо длинный заголовок. Вы сможете получить ошибки проверки другой заголовок слишком велика.
- Нажмите кнопку «Добавить Todo List». Новый список появляется слева от приведенного выше списка.
- Воспроизведение с заголовком TodoList, активируя его требуется и проверки длины.
- Щелкните текстовое поле заголовка, чтобы очистить сообщение об ошибке.
- Нажмите кнопку «x» в кружке в правом верхнем углу для удаления TodoList и его todos.
- Щелкните ссылку «About» в правом верхнем углу, чтобы просмотреть журнал выполнения этих действий.

Логика проверки реализуется выполнено клиентского по просто. Атрибуты проверки на классах модели сервера распространяются на клиент и выполняется автоматически, прежде чем клиент подключается к серверу.

Проверьте сетевой трафик. Обратите внимание, что было не обращений к серверу при просто обнаружена ошибка. Каждое допустимое изменение привел к запросу POST на «/ api/Todo/SaveChanges». Просто объединяет изменения и отправляет их вместе в одном запросе контроллера веб-API `SaveChanges` метод. Это отличается от KockoutJS SPA шаблона, который делает PUT, POST и удалять запросы для каждого элемента по отдельности.

Кроме того Обратите внимание, что отсутствует сетевой трафик при переключении между TodoList, а также о страницах. Это, так как в локальном кэше просто была ограничена запроса.

## <a name="peek-inside"></a>Показать внутри

У этого приложения стороны клиента и стороне сервера. Стек клиентского состоит из небольшой HTML и сочетание модулей JavaScript приложения (в папке «приложение») плюс сторонних библиотек JavaScript (в папке «Сценарии»).

![](http://www.breezejs.com/sites/all/images/spa-template/NgClientArchitecture2.png)

Архитектура пользовательского интерфейса в презентации код контроллеры разделяет мини-приложений HTML представления. Угловое системы привязки данных координирует представлений и контроллеров, что каждый может выполнять свою работу без глубоких знаний другой.

Контроллер запрашивает контекст данных для получения и сохранения модели сущностей. Контекст данных делегируют большую часть работы, чтобы просто, которая создает самоотслеживающейся модели объектов из результатов запроса JSON.

Серверные стек состоит из некоторых разработчика кода и три библиотеки .NET принцип: веб-API, Entity Framework и Breeze.NET:

![](http://www.breezejs.com/sites/all/images/spa-template/ServerArchitecture.png)

Базовая архитектура совпадает с шаблоном KockoutJS SPA. Однако реализация является гораздо проще: DTO были удалены, и большинство данных Entity Framework о делегированных Breeze.NET.

## <a name="next-steps"></a>Следующие шаги

Рекомендуется изучить код, по [широко обсуждений](http://www.breezejs.com/ng-spa-template?utm_source=ms-spa) клиента и стеки серверов, просто веб-сайта.

Можно попробовать работа с просто клиентского запроса; Добавление некоторых фильтров и сортировки. Можно добавить дополнительные свойства модели и дополнительные сущности в лучше понять, для разработки SPA начала до конца. Если вы уверены, проектирования, можно разделять работу функций Todo и замените их собственными.

Удачного программирования!
