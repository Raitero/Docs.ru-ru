---
uid: mvc/overview/older-versions-1/controllers-and-routing/creating-a-controller-vb
title: Создание контроллера (VB) | Документы Microsoft
author: StephenWalther
description: В этом учебнике Стивен Вальтер показано, как добавить контроллер в приложении ASP.NET MVC.
ms.author: aspnetcontent
manager: wpickett
ms.date: 03/02/2009
ms.topic: article
ms.assetid: 204b7e86-f560-4611-8adb-785b33e777b9
ms.technology: dotnet-mvc
ms.prod: .net-framework
msc.legacyurl: /mvc/overview/older-versions-1/controllers-and-routing/creating-a-controller-vb
msc.type: authoredcontent
ms.openlocfilehash: e9a2bbcb09672f5247429064908cd4d2ef67f518
ms.sourcegitcommit: f8852267f463b62d7f975e56bea9aa3f68fbbdeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
<a name="creating-a-controller-vb"></a>Создание контроллера (Visual Basic)
====================
по [Стивен Вальтер](https://github.com/StephenWalther)

> В этом учебнике Стивен Вальтер показано, как добавить контроллер в приложении ASP.NET MVC.


Целью данного учебника является объясняется, как можно создать новый ASP.NET MVC контроллеры. Вы узнаете, как для создания контроллеров, как с помощью пункта меню добавления контроллера Visual Studio, так и вручную создав файл класса.

### <a name="using-the-add-controller-menu-option"></a>С помощью контроллера добавить команду меню

Самый простой способ создать новый контроллер — щелкните правой кнопкой мыши папку Controllers в окне обозревателя решений Visual Studio и выберите **Add, контроллер** меню (см. рис. 1). При выборе этого варианта меню **добавить контроллер** диалогового окна (см. рис. 2).


[![Диалоговое окно нового проекта](creating-a-controller-vb/_static/image1.jpg)](creating-a-controller-vb/_static/image1.png)

**На рисунке 01**: Добавление нового контроллера ([Просмотр полноразмерное изображение](creating-a-controller-vb/_static/image2.png))


[![Диалоговое окно нового проекта](creating-a-controller-vb/_static/image2.jpg)](creating-a-controller-vb/_static/image3.png)

**На рисунке 02**: диалоговое окно добавления контроллера ([Просмотр полноразмерное изображение](creating-a-controller-vb/_static/image4.png))


Обратите внимание, что первая часть имени контроллера, выделяется в **добавить контроллер** диалогового окна. Имя каждого контроллера должно заканчиваться суффиксом *контроллера*. Например, можно создать контроллер с именем *ProductController* , но не контроллер с именем *продукта*.


При создании контроллера, который отсутствует *контроллера* суффикс, то его нельзя вызвать контроллера. Не используйте этот — я занято бесчисленные часы своей жизни после установления этой ошибке.


**Листинг 1 - Controllers\ProductController.vb**

[!code-vb[Main](creating-a-controller-vb/samples/sample1.vb)]

Рекомендуется всегда создавать контроллеров в папке Controllers находится. В противном случае будет нарушения соглашения о ASP.NET MVC и другим разработчикам будет сложнее основные сведения о приложении.

### <a name="scaffolding-action-methods"></a>Методы действия формирования шаблонов

При создании контроллера, у вас есть возможность автоматически создавать методы действий для создания, обновления и получения сведений (см. рис. 3). Если этот параметр выбран, создается класс контроллера в списке 2.


[![Автоматическое создание методов действий](creating-a-controller-vb/_static/image3.jpg)](creating-a-controller-vb/_static/image5.png)

**На рисунке 03**: автоматическое создание методов действий ([Просмотр полноразмерное изображение](creating-a-controller-vb/_static/image6.png))


**Листинг 2 - Controllers\CustomerController.vb**

[!code-vb[Main](creating-a-controller-vb/samples/sample2.vb)]

Эти созданные методы являются методы-заглушки. Необходимо добавить фактической логики для создания, обновления и подробными сведениями для клиента самостоятельно. Но методы-заглушки дает с низким приоритетом отправной точки.

### <a name="creating-a-controller-class"></a>Создание класса контроллера

Контроллер ASP.NET MVC — это класс. При желании можно игнорировать удобный контроллера формирование шаблонов Visual Studio и создать класс контроллера вручную. Выполните следующие действия.

1. Щелкните правой кнопкой мыши папку Controllers и выбрать пункт меню **добавить, новый элемент** и выберите **класса** шаблона (см. рис. 4).
2. Имя для нового класса PersonController.vb и нажмите кнопку **добавить** кнопки.
3. Измените полученный файл так, чтобы класс наследует от базового класса System.Web.Mvc.Controller (см. список 3).


[![Создание нового класса](creating-a-controller-vb/_static/image4.jpg)](creating-a-controller-vb/_static/image7.png)

**На рисунке 04**: Создание нового класса ([Просмотр полноразмерное изображение](creating-a-controller-vb/_static/image8.png))


**Листинг 3 - Controllers\PersonController.vb**

[!code-vb[Main](creating-a-controller-vb/samples/sample3.vb)]

Контроллер в списке 3 предоставляет одно действие с именем Index(), которое возвращает строку «Hello World!». Можно вызвать это действие контроллера путем запуска приложения и запроса URL-адреса следующим образом:

`http://localhost:40071/Person`

> [!NOTE]
> 
> ASP.NET Development Server использует случайный номер порта (например, 40071). При вводе URL-адрес для вызова контроллер, необходимо будет указать номер порта вправо. Можно определить номер порта, наведите указатель мыши на значок для ASP.NET Development Server в области уведомлений Windows (правой нижней части экрана).
> 
> [!div class="step-by-step"]
> [Назад](adding-dynamic-content-to-a-cached-page-vb.md)
> [Вперед](creating-an-action-vb.md)
