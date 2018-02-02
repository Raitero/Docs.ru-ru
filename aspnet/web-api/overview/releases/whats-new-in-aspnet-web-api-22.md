---
uid: web-api/overview/releases/whats-new-in-aspnet-web-api-22
title: "Новые возможности в ASP.NET Web API 2.2 | Документы Microsoft"
author: microsoft
description: 
ms.author: aspnetcontent
manager: wpickett
ms.date: 12/25/2014
ms.topic: article
ms.assetid: 99c59ae4-167e-4f66-a6cd-d3f1098c4e4a
ms.technology: dotnet-webapi
ms.prod: .net-framework
msc.legacyurl: /web-api/overview/releases/whats-new-in-aspnet-web-api-22
msc.type: authoredcontent
ms.openlocfilehash: 400329dd852ca3c527387ee45e3e902b725e771b
ms.sourcegitcommit: 9a9483aceb34591c97451997036a9120c3fe2baf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/10/2017
---
<a name="whats-new-in-aspnet-web-api-22"></a><span data-ttu-id="92252-102">Новые возможности в ASP.NET Web API 2.2</span><span class="sxs-lookup"><span data-stu-id="92252-102">What's New in ASP.NET Web API 2.2</span></span>
====================
<span data-ttu-id="92252-103">по [Microsoft](https://github.com/microsoft)</span><span class="sxs-lookup"><span data-stu-id="92252-103">by [Microsoft](https://github.com/microsoft)</span></span>

<span data-ttu-id="92252-104">В этом разделе описаны новые для ASP.NET Web API 2.2.</span><span class="sxs-lookup"><span data-stu-id="92252-104">This topic describes what's new for ASP.NET Web API 2.2.</span></span>

- [<span data-ttu-id="92252-105">Скачать</span><span class="sxs-lookup"><span data-stu-id="92252-105">Download</span></span>](#download)
- [<span data-ttu-id="92252-106">Документация</span><span class="sxs-lookup"><span data-stu-id="92252-106">Documentation</span></span>](#documentation)
- [<span data-ttu-id="92252-107">Новые возможности в ASP.NET Web API 2.2</span><span class="sxs-lookup"><span data-stu-id="92252-107">New Features in ASP.NET Web API 2.2</span></span>](#newf)

    - [<span data-ttu-id="92252-108">OData v4</span><span class="sxs-lookup"><span data-stu-id="92252-108">OData v4</span></span>](#OData)
    - [<span data-ttu-id="92252-109">Атрибут улучшения маршрутизации</span><span class="sxs-lookup"><span data-stu-id="92252-109">Attribute Routing Improvements</span></span>](#ARI)
    - [<span data-ttu-id="92252-110">Поддержка веб-API клиента Windows Phone 8.1</span><span class="sxs-lookup"><span data-stu-id="92252-110">Web API Client support for Windows Phone 8.1</span></span>](#phone)
- [<span data-ttu-id="92252-111">Известные проблемы и критические изменения</span><span class="sxs-lookup"><span data-stu-id="92252-111">Known Issues and Breaking Changes</span></span>](#known-issues)
- [<span data-ttu-id="92252-112">Исправления ошибок</span><span class="sxs-lookup"><span data-stu-id="92252-112">Bug Fixes</span></span>](#bug-fixes)
- [<span data-ttu-id="92252-113">5.2.1 Microsoft.AspNet.OData</span><span class="sxs-lookup"><span data-stu-id="92252-113">Microsoft.AspNet.OData 5.2.1</span></span>](#odata521)
- [<span data-ttu-id="92252-114">Microsoft.AspNet.WebAPI 5.2.2</span><span class="sxs-lookup"><span data-stu-id="92252-114">Microsoft.AspNet.WebAPI 5.2.2</span></span>](#522RC)
- [<span data-ttu-id="92252-115">Microsoft.AspNet.WebAPI 5.2.3 бета-версии</span><span class="sxs-lookup"><span data-stu-id="92252-115">Microsoft.AspNet.WebAPI 5.2.3 Beta</span></span>](#523)

<a id="download"></a>
## <a name="download"></a><span data-ttu-id="92252-116">Скачать</span><span class="sxs-lookup"><span data-stu-id="92252-116">Download</span></span>

<span data-ttu-id="92252-117">Компоненты среды выполнения выпущены в виде пакетов NuGet при галереи NuGet.</span><span class="sxs-lookup"><span data-stu-id="92252-117">The runtime features are released as NuGet packages on the NuGet gallery.</span></span> <span data-ttu-id="92252-118">Выполните все пакеты среды выполнения [семантического управления версиями](http://semver.org/) спецификации.</span><span class="sxs-lookup"><span data-stu-id="92252-118">All the runtime packages follow the [Semantic Versioning](http://semver.org/) specification.</span></span> <span data-ttu-id="92252-119">Последнюю версию пакета ASP.NET Web API 2.2 имеет следующую версию: «5.2.0».</span><span class="sxs-lookup"><span data-stu-id="92252-119">The latest ASP.NET Web API 2.2 package has the following version: "5.2.0".</span></span> <span data-ttu-id="92252-120">Можно установить или обновить эти пакеты через [NuGet](http://www.nuget.org/packages/Microsoft.AspNet.WebApi/).</span><span class="sxs-lookup"><span data-stu-id="92252-120">You can install or update these packages through [NuGet](http://www.nuget.org/packages/Microsoft.AspNet.WebApi/).</span></span> <span data-ttu-id="92252-121">Этот выпуск также включает соответствующие локализованные пакеты в NuGet.</span><span class="sxs-lookup"><span data-stu-id="92252-121">The release also includes corresponding localized packages on NuGet.</span></span>

<span data-ttu-id="92252-122">Можно установить или обновить выпущенных пакетов NuGet, используя консоль диспетчера пакетов NuGet:</span><span class="sxs-lookup"><span data-stu-id="92252-122">You can install or update to the released NuGet packages by using the NuGet Package Manager Console:</span></span>

[!code-console[Main](whats-new-in-aspnet-web-api-22/samples/sample1.cmd)]

<a id="documentation"></a>
## <a name="documentation"></a><span data-ttu-id="92252-123">Документация</span><span class="sxs-lookup"><span data-stu-id="92252-123">Documentation</span></span>

<span data-ttu-id="92252-124">Учебники и другие сведения о ASP.NET Web API 2.2 доступны из веб-сайт ASP.NET ([https://www.asp.net/web-api](../../index.md)).</span><span class="sxs-lookup"><span data-stu-id="92252-124">Tutorials and other information about ASP.NET Web API 2.2 are available from the ASP.NET web site ([https://www.asp.net/web-api](../../index.md)).</span></span>

<a id="newf"></a>
## <a name="new-features-in-aspnet-web-api-22"></a><span data-ttu-id="92252-125">Новые возможности в ASP.NET Web API 2.2</span><span class="sxs-lookup"><span data-stu-id="92252-125">New Features in ASP.NET Web API 2.2</span></span>

<a id="OData"></a>
### <a name="odata-v4"></a><span data-ttu-id="92252-126">OData v4</span><span class="sxs-lookup"><span data-stu-id="92252-126">OData v4</span></span>

<span data-ttu-id="92252-127">Этот выпуск добавляет поддержку для протокола OData версии 4.</span><span class="sxs-lookup"><span data-stu-id="92252-127">This release adds support for the OData v4 protocol.</span></span> <span data-ttu-id="92252-128">Дополнительные сведения см. в разделе [документации v4 OData веб-API.](../odata-support-in-aspnet-web-api/odata-v4/create-an-odata-v4-endpoint.md)</span><span class="sxs-lookup"><span data-stu-id="92252-128">For more information, see the [Web API OData v4 documentation.](../odata-support-in-aspnet-web-api/odata-v4/create-an-odata-v4-endpoint.md)</span></span>

<span data-ttu-id="92252-129">Ниже приведены некоторые основные возможности и изменения для OData v4.</span><span class="sxs-lookup"><span data-stu-id="92252-129">Here are some of the key features and changes for OData v4:</span></span>

- [<span data-ttu-id="92252-130">Поддержка Совмещение имен свойств в модели OData</span><span class="sxs-lookup"><span data-stu-id="92252-130">Support for aliasing properties in OData model</span></span>](http://aspnet.codeplex.com/SourceControl/latest#Samples/WebApi/OData/v4/ODataModelAliasingSample/)
- [<span data-ttu-id="92252-131">Поддержка ComplexTypeAttribute, AssociationAttribute, TimesTampAttribute и ConcurrencyCheckAttribute в ODataConventionModelBuilder</span><span class="sxs-lookup"><span data-stu-id="92252-131">Support for ComplexTypeAttribute, AssociationAttribute, TimesTampAttribute and ConcurrencyCheckAttribute in ODataConventionModelBuilder</span></span>](http://aspnet.codeplex.com/SourceControl/latest#Samples/WebApi/OData/v4/ODataEtagSample/)
- [<span data-ttu-id="92252-132">Предоставляют возможность указать понятное название для действий</span><span class="sxs-lookup"><span data-stu-id="92252-132">Provide ability to supply friendly Title for actions</span></span>](http://aspnet.codeplex.com/SourceControl/latest#Samples/WebApi/OData/v4/ODataActionsSample/)
- <span data-ttu-id="92252-133">Интеграция с ODL UriParser</span><span class="sxs-lookup"><span data-stu-id="92252-133">Integrate with ODL UriParser</span></span>
- <span data-ttu-id="92252-134">Поддержка [перечисления](http://aspnet.codeplex.com/SourceControl/latest#Samples/WebApi/OData/v4/ODataEnumTypeSample/ODataEnumTypeSample/), [вложения](http://aspnet.codeplex.com/SourceControl/latest#Samples/WebApi/OData/v4/ODataContainmentSample/) и [одноэлементный](http://aspnet.codeplex.com/SourceControl/latest#Samples/WebApi/OData/v4/ODataSingletonSample/)</span><span class="sxs-lookup"><span data-stu-id="92252-134">Support for [enum](http://aspnet.codeplex.com/SourceControl/latest#Samples/WebApi/OData/v4/ODataEnumTypeSample/ODataEnumTypeSample/), [containment](http://aspnet.codeplex.com/SourceControl/latest#Samples/WebApi/OData/v4/ODataContainmentSample/) and [singleton](http://aspnet.codeplex.com/SourceControl/latest#Samples/WebApi/OData/v4/ODataSingletonSample/)</span></span>
- <span data-ttu-id="92252-135">Поддержка приведения типов-примитивов</span><span class="sxs-lookup"><span data-stu-id="92252-135">Support cast for primitive types</span></span>
- [<span data-ttu-id="92252-136">Добавлена поддержка OData-функция</span><span class="sxs-lookup"><span data-stu-id="92252-136">Added OData function support</span></span>](http://aspnet.codeplex.com/SourceControl/latest#Samples/WebApi/OData/v4/ODataFunctionSample/)
- [<span data-ttu-id="92252-137">Поддержка псевдонимы параметра вызовы функций</span><span class="sxs-lookup"><span data-stu-id="92252-137">Support parameter aliases for function calls</span></span>](http://aspnet.codeplex.com/SourceControl/latest#Samples/WebApi/OData/v4/ODataFunctionSample/)
- [<span data-ttu-id="92252-138">Поддерживает camel варианта именования в модели</span><span class="sxs-lookup"><span data-stu-id="92252-138">Support camel case naming convention in model</span></span>](http://aspnet.codeplex.com/SourceControl/latest#Samples/WebApi/OData/v4/ODataCamelCaseSample/)
- <span data-ttu-id="92252-139">Поддержка cast() в $filter</span><span class="sxs-lookup"><span data-stu-id="92252-139">Support for cast() in $filter</span></span>
- <span data-ttu-id="92252-140">Поддержка открытых сложный тип</span><span class="sxs-lookup"><span data-stu-id="92252-140">Support for open complex type</span></span>
- <span data-ttu-id="92252-141">Удален EntitySetController и AsyncEntitySetController</span><span class="sxs-lookup"><span data-stu-id="92252-141">Removed EntitySetController and AsyncEntitySetController</span></span>
- [<span data-ttu-id="92252-142">Измененные $link для $ref</span><span class="sxs-lookup"><span data-stu-id="92252-142">Changed $link to $ref</span></span>](http://aspnet.codeplex.com/SourceControl/latest#Samples/WebApi/OData/v4/ODataServiceSample/)
- [<span data-ttu-id="92252-143">Добавлена поддержка маршрутизации атрибута</span><span class="sxs-lookup"><span data-stu-id="92252-143">Added Attribute routing support</span></span>](https://aspnet.codeplex.com/SourceControl/latest#Samples/WebApi/OData/v4/ODataAttributeRoutingSample/)
- <span data-ttu-id="92252-144">Использует основные OData библиотеки 6.4.0</span><span class="sxs-lookup"><span data-stu-id="92252-144">Uses OData Core Libraries 6.4.0</span></span>

<a id="ARI"></a>
### <a name="attribute-routing-improvements"></a><span data-ttu-id="92252-145">Атрибут улучшения маршрутизации</span><span class="sxs-lookup"><span data-stu-id="92252-145">Attribute Routing Improvements</span></span>

<span data-ttu-id="92252-146">Атрибут маршрутизации теперь предоставляет точку расширения, вызывается IDirectRouteProvider, что позволяет полностью контролировать способа обнаружения и настройки маршрутов с атрибутами.</span><span class="sxs-lookup"><span data-stu-id="92252-146">Attribute Routing now provides an extensibility point called IDirectRouteProvider, which allows full control over how attribute routes are discovered and configured.</span></span> <span data-ttu-id="92252-147">IDirectRouteProvider отвечает за предоставление списка контроллеров вместе с информацией о связанного маршрута для указания точно конфигурации маршрутизации, которые является полезными для тех действий, и действия.</span><span class="sxs-lookup"><span data-stu-id="92252-147">An IDirectRouteProvider is responsible for providing a list of actions and controllers along with associated route information to specify exactly what routing configuration is desired for those actions.</span></span> <span data-ttu-id="92252-148">Реализация IDirectRouteProvider может быть указан при вызове MapAttributes/MapHttpAttributeRoutes.</span><span class="sxs-lookup"><span data-stu-id="92252-148">An IDirectRouteProvider implementation may be specified when calling MapAttributes/MapHttpAttributeRoutes.</span></span>

<span data-ttu-id="92252-149">Настройка IDirectRouteProvider будет простым, расширяя реализацию по умолчанию DefaultDirectRouteProvider.</span><span class="sxs-lookup"><span data-stu-id="92252-149">Customizing IDirectRouteProvider will be easiest by extending our default implementation, DefaultDirectRouteProvider.</span></span> <span data-ttu-id="92252-150">Этот класс предоставляет отдельный overridable виртуальные методы для изменения логики для обнаружения атрибутов, создание записи маршрута и обнаружение префикс маршрута и префикс области.</span><span class="sxs-lookup"><span data-stu-id="92252-150">This class provides separate overridable virtual methods to change the logic for discovering attributes, creating route entries, and discovering route prefix and area prefix.</span></span>

<span data-ttu-id="92252-151">Ниже приведены некоторые примеры на что можно сделать с помощью этой новой точке расширения.</span><span class="sxs-lookup"><span data-stu-id="92252-151">Following are some examples on what you could do with this new extensibility point:</span></span>

1. <span data-ttu-id="92252-152">Поддержка наследования атрибутов маршрута</span><span class="sxs-lookup"><span data-stu-id="92252-152">Support inheritance of Route attributes</span></span>

    <span data-ttu-id="92252-153">Пример.</span><span class="sxs-lookup"><span data-stu-id="92252-153">Example:</span></span>

    <span data-ttu-id="92252-154">Здесь запрос like «/ 10/api/значений» успешно вернет «Успех: 10»</span><span class="sxs-lookup"><span data-stu-id="92252-154">Here a request like "/api/values/10" would successfully return "Success:10"</span></span>

    [!code-csharp[Main](whats-new-in-aspnet-web-api-22/samples/sample2.cs)]
2. <span data-ttu-id="92252-155">Укажите имя маршрута по умолчанию для маршрутов с атрибутами, выполнив некоторые соглашение, как вам удобно.</span><span class="sxs-lookup"><span data-stu-id="92252-155">Provide a default route name for your attribute routes by following some convention you like.</span></span> <span data-ttu-id="92252-156">По умолчанию атрибут маршрутизации не создает автоматически имена маршрутов с атрибутами.</span><span class="sxs-lookup"><span data-stu-id="92252-156">By default, attribute routing doesn't automatically create names for attribute routes.</span></span>
3. <span data-ttu-id="92252-157">Измените шаблон маршрута маршруты атрибутов в одном централизованном месте, прежде чем они заключаются в таблице маршрутов.</span><span class="sxs-lookup"><span data-stu-id="92252-157">Modify attribute routes' route template at one central place before they end up in the route table.</span></span>

<a id="phone"></a>
### <a name="web-api-client-support-for-windows-phone-81"></a><span data-ttu-id="92252-158">Поддержка веб-API клиента Windows Phone 8.1</span><span class="sxs-lookup"><span data-stu-id="92252-158">Web API Client Support for Windows Phone 8.1</span></span>

<span data-ttu-id="92252-159">Теперь можно использовать пакет NuGet клиента Web API для реализации логики клиента веб-API при разработке для Windows Phone 8.1 или из внутри универсального приложения.</span><span class="sxs-lookup"><span data-stu-id="92252-159">You can now use the Web API Client NuGet package to implement your Web API client logic when targeting Windows Phone 8.1 or from within a Universal App.</span></span>

<a id="known-issues"></a>
## <a name="known-issues-and-breaking-changes"></a><span data-ttu-id="92252-160">Известные проблемы и критические изменения</span><span class="sxs-lookup"><span data-stu-id="92252-160">Known Issues and Breaking Changes</span></span>

<span data-ttu-id="92252-161">В этом разделе описываются известные проблемы и критические изменения в ASP.NET Web API 2.2.</span><span class="sxs-lookup"><span data-stu-id="92252-161">This section describes known issues and breaking changes in the ASP.NET Web API 2.2.</span></span>

### <a name="odata-v4"></a><span data-ttu-id="92252-162">OData v4</span><span class="sxs-lookup"><span data-stu-id="92252-162">OData v4</span></span>

#### <a name="model-builder"></a><span data-ttu-id="92252-163">Построитель модели</span><span class="sxs-lookup"><span data-stu-id="92252-163">Model builder</span></span>

<span data-ttu-id="92252-164">Проблема: Перегруженные функции не может быть представлено как FunctionImport</span><span class="sxs-lookup"><span data-stu-id="92252-164">Issue: Overloaded Functions could not be exposed as FunctionImport</span></span>

<span data-ttu-id="92252-165">При наличии 2 перегруженные функции, которые также FunctionImport, как показано ниже, затем запрос приведет к ~/GetAllConventionCustomers(CustomerName={customerName}) System.InvalidOperationException.</span><span class="sxs-lookup"><span data-stu-id="92252-165">If there are 2 overloaded functions and they are also FunctionImport as shown below then requesting ~/GetAllConventionCustomers(CustomerName={customerName}) results in System.InvalidOperationException.</span></span>

[!code-xml[Main](whats-new-in-aspnet-web-api-22/samples/sample3.xml)]

<span data-ttu-id="92252-166">Обходной путь: Решение для этой проблемы является добавление перегрузок функций как FunctionImports.</span><span class="sxs-lookup"><span data-stu-id="92252-166">Workaround: The workaround for this issue is to add both the function overloads as FunctionImports.</span></span>

#### <a name="odata-routing"></a><span data-ttu-id="92252-167">Маршрутизация OData</span><span class="sxs-lookup"><span data-stu-id="92252-167">OData Routing</span></span>

<span data-ttu-id="92252-168">Строковые литералы, которые включают URL-адрес закодированные косая черта (% 2F) и backslash(%5C) вызывают ошибку 404, при их использовании в пути к ресурсам OData.</span><span class="sxs-lookup"><span data-stu-id="92252-168">String literals that include the URL encoded slash (%2F), and backslash(%5C) cause a 404 error when they are used in the OData resource paths.</span></span>

<span data-ttu-id="92252-169">Строковые литералы могут использоваться в пути к ресурсам OData как параметры функций или ключевых значений наборов сущностей.</span><span class="sxs-lookup"><span data-stu-id="92252-169">For example, string literals can be used in the OData resource paths as parameters of functions or key values of entity sets.</span></span>

<span data-ttu-id="92252-170">/Employees/Total.GetCount(Name='Name%2F')</span><span class="sxs-lookup"><span data-stu-id="92252-170">/Employees/Total.GetCount(Name='Name%2F')</span></span>

<span data-ttu-id="92252-171">/Employees('Name%5C')</span><span class="sxs-lookup"><span data-stu-id="92252-171">/Employees('Name%5C')</span></span>

<span data-ttu-id="92252-172">Когда службы получают такие запросы узлов будет отменить escape-символ те escape-последовательность перед их передачей в среду выполнения веб-API.</span><span class="sxs-lookup"><span data-stu-id="92252-172">When services receive such requests the hosts will un-escape those escape sequences before passing them to the Web API runtime.</span></span> <span data-ttu-id="92252-173">Это обеспечивает защиту от атак на систему следующим образом:</span><span class="sxs-lookup"><span data-stu-id="92252-173">This protects against attacks like the following:</span></span>  
  
 <span data-ttu-id="92252-174">http://www.contoso.com/..%2f..%2f/Windows/System32/cmd.exe?/c+dir+c:</span><span class="sxs-lookup"><span data-stu-id="92252-174">http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:</span></span>

<span data-ttu-id="92252-175">В этом случае в стек OData веб-API, чтобы сообщение об ошибке 404 (не найдено).</span><span class="sxs-lookup"><span data-stu-id="92252-175">This causes the Web API OData stack to return a 404 error (Not Found).</span></span> <span data-ttu-id="92252-176">Чтобы предотвратить эту ошибку, ваш клиент должен использовать двойные escape-последовательности для косой черты (% 252F) и обратную косую черту (% 255C).</span><span class="sxs-lookup"><span data-stu-id="92252-176">To prevent this error, your client should use the double escape sequences for slash (%252F) and backslash (%255C).</span></span> <span data-ttu-id="92252-177">Этого не происходит для строк запросов, например /Employees? $filter = имя eq «% 2F имя»</span><span class="sxs-lookup"><span data-stu-id="92252-177">This does not happen for query strings such as /Employees?$filter=Name eq 'Name%2F'</span></span>

<span data-ttu-id="92252-178">**Обратите внимание, без escape-символы косой черты (/) и символы обратной косой черты ("") не допустимы в строковые литералы в пути ресурса OData. Символы косой черты появится только в качестве разделителей пути и символы обратной косой черты не должен появляться в пути к ресурсу OData вообще. (Оба могут использоваться в некоторые части строки запроса OData).**</span><span class="sxs-lookup"><span data-stu-id="92252-178">**Note un-escaped slashes ('/') and backslashes ('') are not legal in OData resource path string literals. Slashes should appear only as path separators and backslashes should not appear in the OData resource path at all. (Both are usable in some portions of an OData query string.)**</span></span>

<span data-ttu-id="92252-179">Обходной путь: Можно переопределить метод Parse DefaultODataPathHandler для escape-знаком косой черты и обратной косой черты в строковых литералах перед началом фактически их обработки.</span><span class="sxs-lookup"><span data-stu-id="92252-179">Workaround: You could override the Parse method of DefaultODataPathHandler to escape the slash and backslash in string literals before actually parsing them.</span></span> <span data-ttu-id="92252-180">Пример такого подхода, здесь можно найти.</span><span class="sxs-lookup"><span data-stu-id="92252-180">You can find a sample of this approach here.</span></span>

### <a name="odata-v3"></a><span data-ttu-id="92252-181">OData v3</span><span class="sxs-lookup"><span data-stu-id="92252-181">OData v3</span></span>

#### <a name="queryable"></a><span data-ttu-id="92252-182">[Запрашиваемым]</span><span class="sxs-lookup"><span data-stu-id="92252-182">[Queryable]</span></span>

<span data-ttu-id="92252-183">Атрибут [Queryable] является устаревшим.</span><span class="sxs-lookup"><span data-stu-id="92252-183">The [Queryable] attribute is deprecated.</span></span> <span data-ttu-id="92252-184">Новые OData v3 приложения должны использовать **System.Web.Http.OData.EnableQueryAttribute**.</span><span class="sxs-lookup"><span data-stu-id="92252-184">New OData v3 applications should use **System.Web.Http.OData.EnableQueryAttribute**.</span></span>

<span data-ttu-id="92252-185">**ODataHttpConfigurationExtensions.EnableQuerySupport** теперь добавляет метод расширения **EnableQueryAttribute** глобальную коллекцию фильтров.</span><span class="sxs-lookup"><span data-stu-id="92252-185">The **ODataHttpConfigurationExtensions.EnableQuerySupport** extension method now adds an **EnableQueryAttribute** to the global filter collection.</span></span> <span data-ttu-id="92252-186">Если все контроллеры имеют **[Queryable]** атрибут вызова `config.EnableQuerySupport()` приведет к **[Queryable]** атрибут к сбою</span><span class="sxs-lookup"><span data-stu-id="92252-186">If any controllers have the **[Queryable]** attribute, calling `config.EnableQuerySupport()` will cause the **[Queryable]** attribute to fail</span></span>

<span data-ttu-id="92252-187">Для устранения этой проблемы рекомендуется для замены всех экземпляров **QueryableAttribute** с **System.Web.Http.OData.EnableQueryAttribute**.</span><span class="sxs-lookup"><span data-stu-id="92252-187">The recommended way to resolve this issue is to replace all instances of **QueryableAttribute** with **System.Web.Http.OData.EnableQueryAttribute**.</span></span>

<span data-ttu-id="92252-188">Второе решение — использовать следующий код в настройку веб-API:</span><span class="sxs-lookup"><span data-stu-id="92252-188">An alternative workaround is to use the following code in your Web API configuration:</span></span>

[!code-csharp[Main](whats-new-in-aspnet-web-api-22/samples/sample4.cs)]

### <a name="attribute-routing"></a><span data-ttu-id="92252-189">Атрибут маршрутизации</span><span class="sxs-lookup"><span data-stu-id="92252-189">Attribute Routing</span></span>

<span data-ttu-id="92252-190">Проблема: Привязка модели сложного типа, который является помеченной атрибутом FromUri ведет себя по-разному при использовании атрибута маршрутизации.</span><span class="sxs-lookup"><span data-stu-id="92252-190">Issue: Model binding of complex type which is decorated with FromUri attribute behaves differently when using Attribute Routing.</span></span>

<span data-ttu-id="92252-191">Используйте следующую ссылку отслеживает проблемы, а также сведения о временном решении.</span><span class="sxs-lookup"><span data-stu-id="92252-191">Following link is tracking the issue and also has details about a workaround.</span></span>  
[<span data-ttu-id="92252-192">http://aspnetwebstack.CodePlex.com/WorkItem/1944</span><span class="sxs-lookup"><span data-stu-id="92252-192">http://aspnetwebstack.codeplex.com/workitem/1944</span></span>](http://aspnetwebstack.codeplex.com/workitem/1944)

<span data-ttu-id="92252-193">Проблема: API MVC или веб-формирования шаблонов в проект с 5.2.0 результаты пакеты в 5.1.2 пакеты для те, которые уже не существуют в проекте</span><span class="sxs-lookup"><span data-stu-id="92252-193">Issue: Scaffolding MVC/Web API into a project with 5.2.0 packages results in 5.1.2 packages for ones that don't already exist in the project</span></span>

<span data-ttu-id="92252-194">Обновление пакетов NuGet для ASP.NET MVC 5.2 не обновляет средства Visual Studio, такие как формирование шаблонов ASP.NET или шаблон проекта веб-приложения ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="92252-194">Updating NuGet packages for ASP.NET MVC 5.2 does not update the Visual Studio tools such as ASP.NET scaffolding or the ASP.NET Web Application project template.</span></span> <span data-ttu-id="92252-195">Они используют предыдущую версию пакета среды выполнения ASP.NET (например 5.1.2 в обновлении 2).</span><span class="sxs-lookup"><span data-stu-id="92252-195">They use the previous version of the ASP.NET runtime packages (e.g. 5.1.2 in Update 2).</span></span> <span data-ttu-id="92252-196">В результате формирование шаблонов ASP.NET установит предыдущую версию (например 5.1.2 в обновлении 2) необходимые пакеты, если они отсутствуют доступные в проектах.</span><span class="sxs-lookup"><span data-stu-id="92252-196">As a result, the ASP.NET scaffolding will install the previous version (e.g. 5.1.2 in Update 2) of the required packages, if they are not already available in your projects.</span></span> <span data-ttu-id="92252-197">Формирование шаблонов ASP.NET в Visual Studio 2013 RTM или обновлением 1 не перезаписывает последние пакеты в проекте.</span><span class="sxs-lookup"><span data-stu-id="92252-197">However, the ASP.NET scaffolding in Visual Studio 2013 RTM or Update 1 does not overwrite the latest packages in your projects.</span></span> <span data-ttu-id="92252-198">Если вы используете формирование шаблонов ASP.NET после обновления пакеты проектов Web API 2.2 или ASP.NET MVC 5.2, убедитесь, что версии веб-API и ASP.NET MVC согласованы.</span><span class="sxs-lookup"><span data-stu-id="92252-198">If you use ASP.NET scaffolding after updating the packages of your projects to Web API 2.2 or ASP.NET MVC 5.2, make sure the versions of Web API and ASP.NET MVC are consistent.</span></span>

<a id="bug-fixes"></a>
## <a name="bug-fixes-and-minor-feature-updates"></a><span data-ttu-id="92252-199">Исправления и обновления вспомогательных компонентов</span><span class="sxs-lookup"><span data-stu-id="92252-199">Bug Fixes and Minor Feature Updates</span></span>

<span data-ttu-id="92252-200">Этот выпуск включает несколько исправлений ошибок, а также дополнительный компонент обновления.</span><span class="sxs-lookup"><span data-stu-id="92252-200">This release also includes several bug fixes and minor feature updates.</span></span> <span data-ttu-id="92252-201">Можно найти полный список здесь:</span><span class="sxs-lookup"><span data-stu-id="92252-201">You can find the complete list here:</span></span>

- [<span data-ttu-id="92252-202">5.2 пакета</span><span class="sxs-lookup"><span data-stu-id="92252-202">5.2 package</span></span>](https://aspnetwebstack.codeplex.com/workitem/list/advanced?keyword=&status=All&type=All&priority=All&release=v5.2%20RC|v5.2%20RTM&assignedTo=All&component=Web%20API|Web%20API%20OData&sortField=AssignedTo&sortDirection=Ascending&page=0&reasonClosed=Fixed)

<a id="odata521"></a>
## <a name="microsoftaspnetodata-521"></a><span data-ttu-id="92252-203">5.2.1 Microsoft.AspNet.OData</span><span class="sxs-lookup"><span data-stu-id="92252-203">Microsoft.AspNet.OData 5.2.1</span></span>

<span data-ttu-id="92252-204">Пакета Microsoft.AspNet.OData 5.2.1 содержит обновления зависимостей NuGet, но без исправления ошибок.</span><span class="sxs-lookup"><span data-stu-id="92252-204">The Microsoft.AspNet.OData 5.2.1 package contains NuGet dependency updates but no bug fixes.</span></span> <span data-ttu-id="92252-205">Это обновление больше не strict зависимостей на Microsoft.OData.Core 6.4.0, но один можно обновить до любой версии между 6.4.0 и 7.0.0.</span><span class="sxs-lookup"><span data-stu-id="92252-205">With this update, there is no longer a strict dependency on Microsoft.OData.Core 6.4.0, but one can upgrade to any version between 6.4.0 and 7.0.0.</span></span>

<a id="522RC"></a>
## <a name="microsoftaspnetwebapi-522"></a><span data-ttu-id="92252-206">Microsoft.AspNet.WebAPI 5.2.2</span><span class="sxs-lookup"><span data-stu-id="92252-206">Microsoft.AspNet.WebAPI 5.2.2</span></span>

<span data-ttu-id="92252-207">В этом выпуске были внесены изменения для зависимости `Json.Net 6.0.4`.</span><span class="sxs-lookup"><span data-stu-id="92252-207">In this release we have made a dependency change for `Json.Net 6.0.4`.</span></span> <span data-ttu-id="92252-208">Дополнительные сведения о новых возможностях этого выпуска `Json.NET`, в разделе [Json.NET 6.0 Release 4 - слияния JSON, внедрение зависимостей](http://james.newtonking.com/archive/2014/08/04/json-net-6-0-release-4-json-merge-dependency-injection).</span><span class="sxs-lookup"><span data-stu-id="92252-208">For more information on what is new in this release of `Json.NET`, see [Json.NET 6.0 Release 4 - JSON Merge, Dependency Injection](http://james.newtonking.com/archive/2014/08/04/json-net-6-0-release-4-json-merge-dependency-injection).</span></span> <span data-ttu-id="92252-209">Этот выпуск не имеет других новых возможностей или исправления ошибок в веб-API.</span><span class="sxs-lookup"><span data-stu-id="92252-209">This release doesn't have any other new features or bug fixes in Web API.</span></span> <span data-ttu-id="92252-210">Впоследствии мы обновили все зависимые пакеты мы собственные зависят от этой новой версии веб-API.</span><span class="sxs-lookup"><span data-stu-id="92252-210">We have subsequently updated all other dependent packages we own to depend on this new version of Web API.</span></span>

<a id="523"></a>
## <a name="microsoftaspnetwebapi-523-beta"></a><span data-ttu-id="92252-211">Microsoft.AspNet.WebAPI 5.2.3 бета-версии</span><span class="sxs-lookup"><span data-stu-id="92252-211">Microsoft.AspNet.WebAPI 5.2.3 Beta</span></span>

<span data-ttu-id="92252-212">Можно прочитать о выпуске [здесь](https://blogs.msdn.com/b/webdev/archive/2014/12/17/asp-net-mvc-5-2-3-web-pages-5-2-3-and-web-api-5-2-3-beta-releases.aspx).</span><span class="sxs-lookup"><span data-stu-id="92252-212">You can read about the release [here](https://blogs.msdn.com/b/webdev/archive/2014/12/17/asp-net-mvc-5-2-3-web-pages-5-2-3-and-web-api-5-2-3-beta-releases.aspx).</span></span> <span data-ttu-id="92252-213">Этот выпуск содержит только исправления ошибок.</span><span class="sxs-lookup"><span data-stu-id="92252-213">This release contains only bug fixes.</span></span> <span data-ttu-id="92252-214">Можно использовать [этот запрос](https://aspnetwebstack.codeplex.com/workitem/list/advanced?keyword=&amp;status=Closed&amp;type=All&amp;priority=All&amp;release=v5.2.3%20Beta&amp;assignedTo=All&amp;component=Web%20API&amp;sortField=LastUpdatedDate&amp;sortDirection=Descending&amp;page=0&amp;reasonClosed=Fixed) Чтобы просмотреть список проблем, исправленных в этом выпуске.</span><span class="sxs-lookup"><span data-stu-id="92252-214">You can use [this query](https://aspnetwebstack.codeplex.com/workitem/list/advanced?keyword=&amp;status=Closed&amp;type=All&amp;priority=All&amp;release=v5.2.3%20Beta&amp;assignedTo=All&amp;component=Web%20API&amp;sortField=LastUpdatedDate&amp;sortDirection=Descending&amp;page=0&amp;reasonClosed=Fixed) to see the list of issues fixed in this release.</span></span>