---
title: Клиент .NET ASP.NET Core SignalR
author: rachelappel
description: Сведения о клиенте .NET ASP.NET Core SignalR
manager: wpickett
monikerRange: '>= aspnetcore-2.1'
ms.author: rachelap
ms.custom: mvc
ms.date: 05/18/2018
ms.prod: aspnet-core
ms.technology: aspnet
ms.topic: article
uid: signalr/dotnet-client
ms.openlocfilehash: 412d2362575789f1fb4792940df6d3dd24dbdd5a
ms.sourcegitcommit: 300a1127957dcdbce1b6ad79a7b9dc676f571510
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
---
# <a name="aspnet-core-signalr-net-client"></a><span data-ttu-id="6dcfa-103">Клиент .NET ASP.NET Core SignalR</span><span class="sxs-lookup"><span data-stu-id="6dcfa-103">ASP.NET Core SignalR .NET Client</span></span>

<span data-ttu-id="6dcfa-104">Автор: [Рэйчел Аппель](http://twitter.com/rachelappel) (Rachel Appel)</span><span class="sxs-lookup"><span data-stu-id="6dcfa-104">By [Rachel Appel](http://twitter.com/rachelappel)</span></span>

<span data-ttu-id="6dcfa-105">Клиент ASP.NET Core SignalR .NET можно использовать для приложений Xamarin, WPF, Windows Forms, веб-консоль и .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6dcfa-105">The ASP.NET Core SignalR .NET client can be used by Xamarin, WPF, Windows Forms, Console, and .NET Core apps.</span></span> <span data-ttu-id="6dcfa-106">Как [клиента JavaScript](xref:signalr/javascript-client), клиент .NET позволяет получать и отправлять и получать сообщения с концентратором в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="6dcfa-106">Like the [JavaScript client](xref:signalr/javascript-client), the .NET client enables you to receive and send and receive messages to a hub in real time.</span></span>

<span data-ttu-id="6dcfa-107">[Просмотреть или скачать образец кода](https://github.com/aspnet/Docs/tree/live/aspnetcore/signalr/dotnet-client/sample) ([как скачивать](xref:tutorials/index#how-to-download-a-sample))</span><span class="sxs-lookup"><span data-stu-id="6dcfa-107">[View or download sample code](https://github.com/aspnet/Docs/tree/live/aspnetcore/signalr/dotnet-client/sample) ([how to download](xref:tutorials/index#how-to-download-a-sample))</span></span>

<span data-ttu-id="6dcfa-108">В образце кода в этой статье является приложением WPF, использующее клиент ASP.NET Core SignalR .NET.</span><span class="sxs-lookup"><span data-stu-id="6dcfa-108">The code sample in this article is a WPF app that uses the ASP.NET Core SignalR .NET client.</span></span>

## <a name="setup-client"></a><span data-ttu-id="6dcfa-109">Программа установки клиента</span><span class="sxs-lookup"><span data-stu-id="6dcfa-109">Setup client</span></span>

<span data-ttu-id="6dcfa-110">`Microsoft.AspNetCore.SignalR.Client` Пакет требуется для клиентов .NET для подключения к концентраторов SignalR.</span><span class="sxs-lookup"><span data-stu-id="6dcfa-110">The `Microsoft.AspNetCore.SignalR.Client` package is needed for .NET clients to connect to SignalR hubs.</span></span> <span data-ttu-id="6dcfa-111">Чтобы установить клиентскую библиотеку, выполните следующую команду **консоль диспетчера пакетов** окна:</span><span class="sxs-lookup"><span data-stu-id="6dcfa-111">To install the client library, run the following command in the **Package Manager Console** window:</span></span>

```powershell
Install-Package Microsoft.AspNetCore.SignalR.Client
```

## <a name="connect-to-a-hub"></a><span data-ttu-id="6dcfa-112">Подключения к концентратору</span><span class="sxs-lookup"><span data-stu-id="6dcfa-112">Connect to a hub</span></span>

<span data-ttu-id="6dcfa-113">Чтобы установить подключение, создайте `HubConnectionBuilder` и вызвать `Build`.</span><span class="sxs-lookup"><span data-stu-id="6dcfa-113">To establish a connection, create a `HubConnectionBuilder` and call `Build`.</span></span> <span data-ttu-id="6dcfa-114">URL-адрес концентратора, протокола, тип транспорта, уровень ведения журнала, заголовки и другие параметры можно настроить при создании соединения.</span><span class="sxs-lookup"><span data-stu-id="6dcfa-114">The hub URL, protocol, transport type, log level, headers, and other options can be configured while building a connection.</span></span> <span data-ttu-id="6dcfa-115">Настройте необходимые параметры вставляя `HubConnectionBuilder` методы в `Build`.</span><span class="sxs-lookup"><span data-stu-id="6dcfa-115">Configure any required options by inserting any of the `HubConnectionBuilder` methods into `Build`.</span></span> <span data-ttu-id="6dcfa-116">Запустить подключение с `StartAsync`.</span><span class="sxs-lookup"><span data-stu-id="6dcfa-116">Start the connection with `StartAsync`.</span></span>

[!code-csharp[Build hub connection](dotnet-client/sample/signalrchatclient/MainWindow.xaml.cs?highlight=15-17,33)]

## <a name="call-hub-methods-from-client"></a><span data-ttu-id="6dcfa-117">Вызов методов концентратора из клиента</span><span class="sxs-lookup"><span data-stu-id="6dcfa-117">Call hub methods from client</span></span>

<span data-ttu-id="6dcfa-118">`InvokeAsync` вызывает методы концентратора.</span><span class="sxs-lookup"><span data-stu-id="6dcfa-118">`InvokeAsync` calls methods on the hub.</span></span> <span data-ttu-id="6dcfa-119">Передайте имя метода концентратора и все аргументы, заданные в методе концентратора для `InvokeAsync`.</span><span class="sxs-lookup"><span data-stu-id="6dcfa-119">Pass the hub method name and any arguments defined in the hub method to `InvokeAsync`.</span></span> <span data-ttu-id="6dcfa-120">SignalR выполняется в асинхронном режиме, поэтому следует использовать `async` и `await` при выполнении вызовов.</span><span class="sxs-lookup"><span data-stu-id="6dcfa-120">SignalR is asynchronous, so use `async` and `await` when making the calls.</span></span>

[!code-csharp[InvokeAsync method](dotnet-client/sample/signalrchatclient/MainWindow.xaml.cs?range=48-49)]

## <a name="call-client-methods-from-hub"></a><span data-ttu-id="6dcfa-121">Вызовите методы клиента от концентратора</span><span class="sxs-lookup"><span data-stu-id="6dcfa-121">Call client methods from hub</span></span>

<span data-ttu-id="6dcfa-122">Определите методы концентратора вызовы с использованием `connection.On` после сборки, но до начала соединения.</span><span class="sxs-lookup"><span data-stu-id="6dcfa-122">Define methods the hub calls using `connection.On` after building, but before starting the connection.</span></span>

[!code-csharp[Define client methods](dotnet-client/sample/signalrchatclient/MainWindow.xaml.cs?range=22-29)]

<span data-ttu-id="6dcfa-123">Приведенный выше код в `connection.On` выполняется, когда серверный код вызывает ее с помощью `SendAsync` метод.</span><span class="sxs-lookup"><span data-stu-id="6dcfa-123">The preceding code in `connection.On` runs when server-side code calls it using the `SendAsync` method.</span></span>

[!code-csharp[Call client method](dotnet-client/sample/signalrchat/hubs/chathub.cs?range=8-11)]

## <a name="error-handling-and-logging"></a><span data-ttu-id="6dcfa-124">Обработка ошибок и ведение журнала</span><span class="sxs-lookup"><span data-stu-id="6dcfa-124">Error handling and logging</span></span>

<span data-ttu-id="6dcfa-125">Обработку ошибок с помощью оператора try-catch.</span><span class="sxs-lookup"><span data-stu-id="6dcfa-125">Handle errors with a try-catch statement.</span></span> <span data-ttu-id="6dcfa-126">Проверить `Exception` объектом, чтобы определить правильное действие, предпринимаемое после возникновения ошибки.</span><span class="sxs-lookup"><span data-stu-id="6dcfa-126">Inspect the `Exception` object to determine the proper action to take after an error occurs.</span></span>

[!code-csharp[Logging](dotnet-client/sample/signalrchatclient/MainWindow.xaml.cs?range=46-54)]

## <a name="additional-resources"></a><span data-ttu-id="6dcfa-127">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="6dcfa-127">Additional resources</span></span>

* [<span data-ttu-id="6dcfa-128">Центры</span><span class="sxs-lookup"><span data-stu-id="6dcfa-128">Hubs</span></span>](xref:signalr/hubs)
* [<span data-ttu-id="6dcfa-129">Клиент JavaScript</span><span class="sxs-lookup"><span data-stu-id="6dcfa-129">JavaScript client</span></span>](xref:signalr/javascript-client)
* [<span data-ttu-id="6dcfa-130">Публикация в Azure</span><span class="sxs-lookup"><span data-stu-id="6dcfa-130">Publish to Azure</span></span>](xref:signalr/publish-to-azure-web-app)