---
title: Активация ПО промежуточного слоя на основе фабрики в ASP.NET Core
author: guardrex
description: В этой статье приводятся сведения о том, как использовать строго типизированное ПО промежуточного слоя с реализацией активации на основе фабрики в ASP.NET Core.
ms.author: riande
manager: wpickett
ms.custom: mvc
ms.date: 01/29/2018
ms.topic: article
ms.technology: aspnet
ms.prod: asp.net-core
uid: fundamentals/middleware/extensibility
ms.openlocfilehash: 8cec5b3b498f5a23463d8c3cd5901e14f22f6eab
ms.sourcegitcommit: 43bd79667bbdc8a07bd39fb4cd6f7ad3e70212fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34729120"
---
# <a name="factory-based-middleware-activation-in-aspnet-core"></a>Активация ПО промежуточного слоя на основе фабрики в ASP.NET Core

Автор [Люк Латэм](https://github.com/guardrex) (Luke Latham)

[IMiddlewareFactory](/dotnet/api/microsoft.aspnetcore.http.imiddlewarefactory)/[IMiddleware](/dotnet/api/microsoft.aspnetcore.http.imiddleware) — это точка расширяемости для активации [ПО промежуточного слоя](xref:fundamentals/middleware/index).

Методы расширения `UseMiddleware` проверяют, реализует ли зарегистрированный тип ПО промежуточного слоя `IMiddleware`. Если да, то экземпляр `IMiddlewareFactory`, зарегистрированный в контейнере, используется для разрешения реализации `IMiddleware` вместо стандартной логики активации ПО промежуточного слоя. ПО промежуточного слоя регистрируется как ограниченная или временная служба в контейнере служб приложения.

Преимущества:

* Активация по запросу (внедрение ограниченных служб)
* Строгая типизация ПО промежуточного слоя

`IMiddleware` активируется по запросу, благодаря чему ограниченные службы могут внедряться в конструктор ПО промежуточного слоя.

[Просмотреть или скачать образец кода](https://github.com/aspnet/Docs/tree/master/aspnetcore/fundamentals/middleware/extensibility/sample) ([как скачивать](xref:tutorials/index#how-to-download-a-sample))

В примере приложения показана активация ПО промежуточного слоя следующими способами:

* Стандартный. Дополнительные сведения о стандартной активации ПО промежуточного слоя см. [здесь](xref:fundamentals/middleware/index).
* Реализация [IMiddleware](/dotnet/api/microsoft.aspnetcore.http.imiddleware). По умолчанию ПО промежуточного слоя активируется [классом MiddlewareFactory](/dotnet/api/microsoft.aspnetcore.http.middlewarefactory).

Реализации ПО промежуточного слоя функционируют идентичным образом и записывают значение, предоставленное в параметре строки запроса (`key`). ПО промежуточного слоя использует внедренный контекст базы данных (ограниченная служба) для записи значения строки запроса в базу данных, выполняющуюся в памяти.

## <a name="imiddleware"></a>IMiddleware

[IMiddleware](/dotnet/api/microsoft.aspnetcore.http.imiddleware) определяет ПО промежуточного слоя для конвейера запросов приложения. Метод [InvokeAsync(HttpContext, RequestDelegate)](/dotnet/api/microsoft.aspnetcore.http.imiddleware.invokeasync#Microsoft_AspNetCore_Http_IMiddleware_InvokeAsync_Microsoft_AspNetCore_Http_HttpContext_Microsoft_AspNetCore_Http_RequestDelegate_) обрабатывает запрос и возвращает объект `Task`, который представляет выполнение ПО промежуточного слоя.

Стандартная активация ПО промежуточного слоя:

[!code-csharp[](extensibility/sample/Middleware/ConventionalMiddleware.cs?name=snippet1)]

Активация ПО промежуточного слоя с помощью `MiddlewareFactory`:

[!code-csharp[](extensibility/sample/Middleware/IMiddlewareMiddleware.cs?name=snippet1)]

Расширения, создаваемые для ПО промежуточного слоя:

[!code-csharp[](extensibility/sample/Middleware/MiddlewareExtensions.cs?name=snippet1)]

Невозможна передача объектов в ПО промежуточного слоя, активируемое на основе фабрики с помощью `UseMiddleware`:

```csharp
public static IApplicationBuilder UseIMiddlewareMiddleware(
    this IApplicationBuilder builder, bool option)
{
    // Passing 'option' as an argument throws a NotSupportedException at runtime.
    return builder.UseMiddleware<IMiddlewareMiddleware>(option);
}
```

Активируемое на основе фабрики ПО промежуточного слоя добавляется во встроенный контейнер в файле *Startup.cs*:

[!code-csharp[](extensibility/sample/Startup.cs?name=snippet1&highlight=12)]

Оба ПО промежуточного слоя регистрируются в конвейере обработки запросов в `Configure`:

[!code-csharp[](extensibility/sample/Startup.cs?name=snippet2&highlight=13-14)]

## <a name="imiddlewarefactory"></a>IMiddlewareFactory

[IMiddlewareFactory](/dotnet/api/microsoft.aspnetcore.http.imiddlewarefactory) предоставляет методы для создания ПО промежуточного слоя. Реализация ПО промежуточного слоя на основе фабрики регистрируется в контейнере в виде ограниченной службы.

Реализация `IMiddlewareFactory` по умолчанию, [MiddlewareFactory](/dotnet/api/microsoft.aspnetcore.http.middlewarefactory), находится в пакете [Microsoft.AspNetCore.Http](https://www.nuget.org/packages/Microsoft.AspNetCore.Http/) ([ссылки на источник](https://github.com/aspnet/HttpAbstractions/blob/release/2.0/src/Microsoft.AspNetCore.Http/MiddlewareFactory.cs)).

## <a name="additional-resources"></a>Дополнительные ресурсы

* [ПО промежуточного слоя](xref:fundamentals/middleware/index)
* [Активация ПО промежуточного слоя со сторонним контейнером](xref:fundamentals/middleware/extensibility-third-party-container)
