---
title: Миграция с веб-API ASP.NET на ASP.NET Core
author: ardalis
description: Дополнительные сведения о миграции реализация веб-API из веб-API ASP.NET ASP.NET Core MVC.
manager: wpickett
ms.author: riande
ms.date: 05/10/2018
ms.prod: asp.net-core
ms.technology: aspnet
ms.topic: article
uid: migration/webapi
ms.openlocfilehash: 8d842877e49e317323d453e71ebb3302245f388d
ms.sourcegitcommit: 3d071fabaf90e32906df97b08a8d00e602db25c0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="migrate-from-aspnet-web-api-to-aspnet-core"></a>Миграция с веб-API ASP.NET на ASP.NET Core

Авторы: [Стив Смит](https://ardalis.com/) (Steve Smith) и [Скотт Эдди](https://scottaddie.com) (Scott Addie)

Веб-API — это службы HTTP, которые широкого диапазона клиентов, включая браузеры и мобильные устройства. Основные ASP.NET MVC включает поддержку для создания веб-API, обеспечивая единый, согласованный способ создания веб-приложений. В этой статье мы демонстрируются шаги, необходимые для миграции реализация веб-API из веб-API ASP.NET ASP.NET Core MVC.

[Просмотреть или скачать образец кода](https://github.com/aspnet/Docs/tree/master/aspnetcore/migration/webapi/sample) ([как скачивать](xref:tutorials/index#how-to-download-a-sample))

## <a name="review-aspnet-web-api-project"></a>Просмотр ASP.NET Web API проекта

В этой статье используется пример проекта *ProductsApp*, созданный в статье [Приступая к работе с ASP.NET Web API 2](/aspnet/web-api/overview/getting-started-with-aspnet-web-api/tutorial-your-first-web-api) начальной точкой. В этом проекте простого проекта веб-API ASP.NET настраивается следующим образом.

В *Global.asax.cs*, выполняется вызов `WebApiConfig.Register`:

[!code-csharp[](../migration/webapi/sample/ProductsApp/Global.asax.cs?highlight=14)]

`WebApiConfig` определен в *App_Start*, и имеет только один статический `Register` метод:

[!code-csharp[](../migration/webapi/sample/ProductsApp/App_Start/WebApiConfig.cs?highlight=15,16,17,18,19,20)]


Этот класс настраивает [маршрутизацией атрибутов](https://docs.microsoft.com/aspnet/web-api/overview/web-api-routing-and-actions/attribute-routing-in-web-api-2), несмотря на то, что он фактически не используется в проекте. Он также настраивает таблицу маршрутизации, которая используется веб-API ASP.NET. В этом случае веб-API ASP.NET будет ожидать, что URL-адреса в соответствии с форматом */api/ {controller} / {id}*, с *{id}* дополнительными.

*ProductsApp* проект содержит только один простой контроллер, который наследует от `ApiController` и предоставляет два метода:

[!code-csharp[](../migration/webapi/sample/ProductsApp/Controllers/ProductsController.cs?highlight=19,24)]

Наконец, модель *продукта*, используемый в *ProductsApp*, — это простой класс:

[!code-csharp[](webapi/sample/ProductsApp/Models/Product.cs)]

Теперь, когда у нас есть простой проект, из которого следует начать, мы показано, как перенести этот проект веб-API ASP.NET Core MVC.

## <a name="create-the-destination-project"></a>Создайте проект назначения

С помощью Visual Studio, создайте новый, пустой решение и назовите его *WebAPIMigration*. Добавить существующий *ProductsApp* проекта к нему, затем добавьте в решение новый ASP.NET Core проект веб-приложения. Имя для нового проекта *ProductsCore*.

![Откройте диалоговое окно нового проекта для веб-шаблонов](webapi/_static/add-web-project.png)

Затем выберите шаблон проекта веб-API. Мы перенесем *ProductsApp* содержимое в новый проект.

![Диалоговое окно создания веб-приложения с помощью шаблона проекта веб-API, выбранного в списке шаблонов ASP.NET Core](webapi/_static/aspnet-5-webapi.png)

Удалить `Project_Readme.html` файла из нового проекта. Решение теперь должна выглядеть следующим образом:

![Откройте решение приложения в обозревателе решений файлы и папки проектов ProductsApp и ProductsCore](webapi/_static/webapimigration-solution.png)

## <a name="migrate-configuration"></a>Перенос конфигурации

Больше не используется ASP.NET Core *Global.asax*, *web.config*, или *App_Start* папки. Вместо этого все задачи запуска выполняются в *файла Startup.cs* в корневой папке проекта (в разделе [запуска приложения](../fundamentals/startup.md)). В ASP.NET MVC ядра маршрутизации на основе атрибута теперь включается по умолчанию при `UseMvc()` вызове; и это рекомендуемый подход для настройки веб-API маршрутов (и как начальный проект веб-API обрабатывает маршрутизации).

[!code-csharp[](../migration/webapi/sample/ProductsCore/Startup.cs?highlight=31)]

Предположим, что вы хотите использовать в проекте, в дальнейшем маршрутизацией атрибутов, необходим без дополнительной настройки. Просто применить атрибуты, необходимыми для контроллеров и действий, как показано в образце `ValuesController` класс, который включен в начальный проект веб-API:

[!code-csharp[](../migration/webapi/sample/ProductsCore/Controllers/ValuesController.cs?highlight=9,13,20,27,33,39)]

Обратите внимание на наличие *[контроллер]* в строке 8. Атрибут маршрутизации на основе теперь поддерживает определенные токены, такие как *[контроллер]* и *[действие]*. Эти токены заменяются во время выполнения имя контроллер или действие, соответственно, к которому был применен атрибут. Это служит для уменьшения количества magic строк в проекте и гарантирует, что маршруты будут синхронизироваться с их соответствующие контроллеры и действия при применении Автоматическое переименование рефакторинга.

Чтобы перенести контроллер API продуктов, нам необходимо скопировать *ProductsController* в новый проект. Затем просто включите атрибут маршрута на контроллере:

```csharp
[Route("api/[controller]")]
```

Необходимо также добавить `[HttpGet]` атрибут два метода, поскольку они оба должны быть вызваны посредством HTTP Get. Включить предположения параметра «идентификатор» в атрибуте `GetProduct()`:

```csharp
// /api/products
[HttpGet]
...

// /api/products/1
[HttpGet("{id}")]
```

На этом этапе маршрутизации настроена правильно; Тем не менее мы не еще тестирования. Дополнительные изменения должны быть выполнены до *ProductsController* будет компилироваться.

## <a name="migrate-models-and-controllers"></a>Миграция моделей и контроллеры

Последний шаг в процессе миграции для этого простого проекта веб-API необходимо для копирования через контроллера и всех моделей, они используют. В этом случае просто скопировать *Controllers/ProductsController.cs* исходного проекта в новый. Затем скопируйте всю папку моделей исходного проекта в новый. Настройка пространства имен в соответствии с новым именем проекта (*ProductsCore*).  На этом этапе можно построить приложение, и вы увидите число ошибок компиляции. Они должны обычно делятся на следующие категории:

* *ApiController* не существует

* *System.Web.Http* пространство имен не существует.

* *IHttpActionResult* не существует

К счастью это все очень легко исправить.

* Изменение *ApiController* для *контроллера* (может потребоваться добавить *с помощью Microsoft.AspNetCore.Mvc*)

* Удалить все с помощью инструкции, ссылающиеся на *System.Web.Http*

* Изменение любого метода возврат *IHttpActionResult* для возврата *IActionResult*

После завершения эти изменения были сделаны и неиспользуемые с помощью инструкций удаляется, перенесенная *ProductsController* класса выглядит следующим образом:

[!code-csharp[](../migration/webapi/sample/ProductsCore/Controllers/ProductsController.cs?highlight=1,2,6,8,9,27)]

Теперь можно запустить перенесенного проекта и перейдите к */api/продуктов*; и следует просмотреть весь список продуктов, 3. Перейдите к */api/products/1* и вы увидите первого продукта.

## <a name="microsoftaspnetcoremvcwebapicompatshim"></a>Microsoft.AspNetCore.Mvc.WebApiCompatShim

— Это эффективное средство, если миграция веб-API ASP.NET проектов для ASP.NET Core [Microsoft.AspNetCore.Mvc.WebApiCompatShim](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.WebApiCompatShim) библиотеки. Оболочки совместимости расширяет ASP.NET Core, чтобы разрешить несколько разных соглашений веб-API 2 для использования. Образца перенесена ранее в этом документе является достаточно простым и оболочку совместимости был необходим. Для крупных проектов с помощью оболочки совместимости можно использовать для временного мост API разрыв между ASP.NET Core и ASP.NET Web API 2.

Оболочки совместимости веб-API предназначен для использования в качестве временной меры для упрощения переноса больших проектов веб-API для ASP.NET Core. Со временем проектов должен быть обновлен для использования шаблонов ASP.NET Core, не полагаясь на оболочку совместимости. 

Совместимость возможности, включенные в Microsoft.AspNetCore.Mvc.WebApiCompatShim:

* Добавляет `ApiController` тип, так что контроллеров базовые типы не должны быть обновлены.
* Включение API веб-привязки модели. Основные ASP.NET MVC модель привязки работает так же MVC 5 по умолчанию. Изменения оболочки совместимости модели больше похож на соглашения привязки модели веб-API 2 привязки. Например сложные типы автоматически привязываются в тексте запроса.
* Расширяет привязки модели, благодаря чему действия контроллера может использовать параметры типа `HttpRequestMessage`.
* Добавляет модули форматирования сообщений разрешение действий для возврата результатов типа `HttpResponseMessage`.
* Добавляет ответа дополнительные методы, которые воспользовались для обслуживания ответы веб-API 2 действия:
    * Генераторы HttpResponseMessage:
        * `CreateResponse<T>`
        * `CreateErrorResponse`
    * Методы действий результат:
        * `BadResuestErrorMessageResult`
        * `ExceptionResult`
        * `InternalServerErrorResult`
        * `InvalidModelStateResult`
        * `NegotiatedContentResult`
        * `ResponseMessageResult`
* Добавляет экземпляр `IContentNegotiator` контейнер DI приложения и делает содержимое из типов, связанных с согласования [Microsoft.AspNet.WebApi.Client](https://www.nuget.org/packages/Microsoft.AspNet.WebApi.Client/) доступны. Сюда входят типы, такие как `DefaultContentNegotiator`, `MediaTypeFormatter`и т. д.

Чтобы использовать оболочку совместимости, необходимо:

* Справочник по [Microsoft.AspNetCore.Mvc.WebApiCompatShim](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.WebApiCompatShim) пакет NuGet.
* Зарегистрируйте служб оболочку совместимости с контейнером DI приложения путем вызова `services.AddWebApiConventions()` в приложении `Startup.ConfigureServices` метод.
* Определение конкретных Web API маршрутов с помощью `MapWebApiRoute` на `IRouteBuilder` в приложении `IApplicationBuilder.UseMvc` вызова.

## <a name="summary"></a>Сводка

Миграция простого проекта веб-API ASP.NET ASP.NET Core MVC является довольно просто благодаря использованию встроенную поддержку веб-API в ASP.NET Core MVC. Основных элементах, которые потребуется миграция каждый проект веб-API ASP.NET: маршруты, контроллеры и моделей, а также обновления для типов, используемых контроллеров и действий.
