---
title: Приступая к работе с API защиты данных в ASP.NET Core
author: rick-anderson
description: Сведения об использовании интерфейсов API защиты данных ASP.NET Core для защиты и снятие защиты данных в приложении.
manager: wpickett
ms.author: riande
ms.date: 10/14/2016
ms.prod: asp.net-core
ms.technology: aspnet
ms.topic: article
uid: security/data-protection/using-data-protection
ms.openlocfilehash: 3a69abd2b58e02f87ccaf2317b0a8a2a7e9d7b4a
ms.sourcegitcommit: 48beecfe749ddac52bc79aa3eb246a2dcdaa1862
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2018
---
# <a name="get-started-with-the-data-protection-apis-in-aspnet-core"></a>Приступая к работе с API защиты данных в ASP.NET Core

<a name="security-data-protection-getting-started"></a>

На простой защиту данных состоит из следующих шагов:

1. Создание данных предохранитель из поставщик защиты данных.

2. Вызовите `Protect` метод с данными, которую необходимо защитить.

3. Вызовите `Unprotect` метод с данными требуется вернулась в виде обычного текста.

Большинство платформ и модели приложения, такие как ASP.NET или SignalR, уже настройки системы защиты данных и добавьте его в контейнер службы, который доступен через внедрения зависимостей. Следующий пример демонстрирует настройку контейнер службы для внедрения зависимостей и регистрации стека защиты данных, получения поставщик защиты данных через DI, создания предохранителя и защиту и снятие защиты данных

[!code-csharp[](../../security/data-protection/using-data-protection/samples/protectunprotect.cs?highlight=26,34,35,36,37,38,39,40)]

При создании предохранителя необходимо указать один или несколько [строки цели](xref:security/data-protection/consumer-apis/purpose-strings). Строка цели обеспечивает изоляцию между потребителей. Например предохранителя, созданные с целью строку «зеленый» не смогут снять защиту данных, предоставленных предохранитель с целью «фиолетовый».

>[!TIP]
> Экземпляры `IDataProtectionProvider` и `IDataProtector` потокобезопасны для нескольких клиентов. Он предназначен, когда компонент получает ссылку на `IDataProtector` через вызов `CreateProtector`, он будет использовать эту ссылку для нескольких вызовов `Protect` и `Unprotect`.
>
>Вызов `Unprotect` CryptographicException вызывает исключение, если защищенный полезных данных не может быть проверена или расшифровать. Некоторые компоненты нужна возможность пропускать ошибки во время снятия защиты операций; компонент, который считывает файлы cookie проверки подлинности может обработать эту ошибку и обрабатывать запрос, как если бы объекты cookie не на всех, а не ошибкой запроса сразу. В частности, компонентами, которые хотите такого поведения следует перехватывать CryptographicException вместо подавление всех исключений.
