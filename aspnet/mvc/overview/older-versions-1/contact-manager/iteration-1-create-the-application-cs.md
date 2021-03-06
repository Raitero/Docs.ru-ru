---
uid: mvc/overview/older-versions-1/contact-manager/iteration-1-create-the-application-cs
title: 'Итерации #1 – Создание приложения (C#) | Документы Microsoft'
author: microsoft
description: 'В первой итерации мы создадим диспетчера контактов простейшим способом невозможно. Добавлена поддержка для основных операций базы данных: создание, чтение, обновление и D....'
ms.author: aspnetcontent
manager: wpickett
ms.date: 02/20/2009
ms.topic: article
ms.assetid: db0f160b-901c-46d3-865e-7ab6cd4ed68d
ms.technology: dotnet-mvc
ms.prod: .net-framework
msc.legacyurl: /mvc/overview/older-versions-1/contact-manager/iteration-1-create-the-application-cs
msc.type: authoredcontent
ms.openlocfilehash: 30f626511164363fea2195a05e73aeee5764933b
ms.sourcegitcommit: f8852267f463b62d7f975e56bea9aa3f68fbbdeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
<a name="iteration-1--create-the-application-c"></a>Итерации #1 – Создание приложения (C#)
====================
по [Microsoft](https://github.com/microsoft)

[Загрузить исходный код](iteration-1-create-the-application-cs/_static/contactmanager_1_cs1.zip)

> В первой итерации мы создадим диспетчера контактов простейшим способом невозможно. Добавлена поддержка для основных операций базы данных: создание, чтение, обновление и удаление (CRUD).


## <a name="building-a-contact-management-aspnet-mvc-application-vb"></a>Создание приложения ASP.NET MVC управления контактами (Visual Basic)

В этой серии учебники мы создаем всего приложения управления контактами от начала и завершения. Приложение диспетчера контактов позволяет хранить контактные данные - имена, номера телефонов и адресов электронной почты — список людей.

Мы постройте приложение в нескольких итерациях. С каждой итерацией постепенно мы улучшить приложение. Это несколько итераций предназначена для того, чтобы позволяют понять причину для каждого изменения.

- Итерации #1 - создать приложение. В первой итерации мы создадим диспетчера контактов простейшим способом невозможно. Добавлена поддержка для основных операций базы данных: создание, чтение, обновление и удаление (CRUD).

- Итерации #2 — сделать приложение поиска работы с низким приоритетом. В этой итерации нам улучшить внешний вид приложения, изменив значение по умолчанию главной страницы представления ASP.NET MVC и каскадные таблицы стилей.

- Итерации #3 - Добавление проверки формы. В третьем проходе добавим проверки базовой формы. Мы запретить отправки формы, не завершая обязательные поля. Мы также для проверки адреса электронной почты и номера телефонов.

- Итерации #4 - сделать приложение слабо. В этой третьей итерации мы воспользоваться преимуществами нескольких шаблонов разработки программного обеспечения, чтобы упростить обслуживание и изменить приложение диспетчера контактов. Например мы выполнили рефакторинг наше приложение, чтобы использовать шаблон репозитория и шаблон внедрения зависимостей.

- Итерации #5 - Создание модульных тестов. В пятой итерации сделан нашего приложения проще в обслуживании и изменить, добавив модульных тестов. Мы макета наших классов модели данных и создания модульных тестов для наших контроллеров и логику проверки.

- Итерация 6 # — с помощью управляемой тестами разработки. В итерации этого шестой мы добавим новые функциональные возможности наше приложение, сначала написание модульных тестов и писать код для модульных тестов. В этой итерации добавим групп контактов.

- Итерации #7. Добавление функциональности Ajax. В седьмой итерации мы повысить скорость реагирования и производительности приложения, добавляя поддержку Ajax.

## <a name="this-iteration"></a>Этой итерации

В этой первой итерации мы создание простого приложения. Целью является быстрым и простым способом выполнять сборку диспетчера контактов. В последующих итерациях нам улучшить конструкцию приложения.

Приложение диспетчера контактов является простого приложения на основе базы данных. Приложение можно использовать для создания новых контактов, редактировать существующие контакты и удалять контакты.

В этой итерации мы выполните следующие действия:

1. Приложение ASP.NET MVC
2. Создать базу данных для хранения нашей контактов
3. Создайте класс модели для наших базы данных с платформой Entity Framework Microsoft
4. Создание действия контроллера и представление, которое позволяет нам получить список всех контактов в базе данных
5. Создание действия контроллера и представление, которое позволяет создать новый контакт в базе данных
6. Создание действия контроллера и представления, нужны для изменения существующей базы данных
7. Создание действия контроллера и представление, которое позволяет удалить существующего контакта в базе данных

## <a name="software-prerequisites"></a>Необходимое программное обеспечение

В приложениях ASP.NET MVC необходимо иметь Visual Studio 2008 или Visual Web Developer 2008 установлены на компьютере (Visual Web Developer — это бесплатная версия Visual Studio, которая содержит не все дополнительные функции Visual Studio). Можно загрузить либо пробной версии Visual Studio 2008 или Visual Web Developer следующий адрес:

[https://www.asp.net/downloads/essential/](https://www.asp.net/downloads/essential)

> [!NOTE] 
> 
> Для приложений ASP.NET MVC в Visual Web Developer необходимо иметь Visual Web Developer установленного пакета обновления 1. Без пакета обновления 1 нельзя создавать проекты веб-приложений.


Платформа ASP.NET MVC. Платформа ASP.NET MVC можно загрузить по следующему адресу:

[https://www.asp.net/mvc](../../../index.md)

В этом учебнике мы используем Microsoft Entity Framework для доступа к базе данных. Платформа Entity Framework входит в состав .NET Framework 3.5 с пакетом обновления 1. Этот пакет обновления можно загрузить из следующей папки:

[https://www.microsoft.com/downloads/details.aspx?familyid=ab99342f-5d1a-413d-8319-81da479ab0d7&amp;displaylang=en](https://www.microsoft.com/downloads/details.aspx?familyid=ab99342f-5d1a-413d-8319-81da479ab0d7&amp;displaylang=en)

В качестве альтернативы для выполнения каждого из этих загружаемых компонентов по одному можно воспользоваться преимуществами установщика веб-платформы (Web PI). Установщик веб-Платформы можно загрузить по следующему адресу:

[https://www.asp.net/downloads/essential/](https://www.asp.net/downloads/essential)

## <a name="aspnet-mvc-project"></a>Проект ASP.NET MVC

Проект веб-приложения ASP.NET MVC. Запустите Visual Studio и выберите пункт меню в **файл, создать проект**. **Новый проект** откроется диалоговое окно (см. рис. 1). Выберите **Web** тип проекта и **веб-приложение ASP.NET MVC** шаблона. Имя нового проекта *ContactManager* и нажмите кнопку "ОК".


Убедитесь, что .NET Framework 3.5, выбранный из раскрывающегося списка в верхней правой части **новый проект** диалогового окна. В противном случае шаблон веб-приложения ASP.NET MVC, выиграл t отображаться.


[![Диалоговое окно нового проекта](iteration-1-create-the-application-cs/_static/image1.jpg)](iteration-1-create-the-application-cs/_static/image1.png)

**На рисунке 01**: диалоговое окно нового проекта ([Просмотр полноразмерное изображение](iteration-1-create-the-application-cs/_static/image2.png))


Приложение ASP.NET MVC **Создание проекта модульных тестов** откроется диалоговое окно. Это диалоговое окно позволяет указать, что для создания и добавления в решение проект модульного теста, при создании приложения ASP.NET MVC. Несмотря на то, что мы выиграл t быть построения модульных тестов в этой итерации, следует выбрать вариант **Да, создать проект модульного теста** так, как мы планируем добавить модульные тесты в более поздней итерации. Добавление тестового проекта при создании нового проекта ASP.NET MVC — гораздо проще, чем при добавлении тестовый проект, созданный проект ASP.NET MVC.

> [!NOTE] 
> 
> Поскольку Visual Web Developer не поддерживает проекты тестов, вы не получите диалогового окна создания проекта модульного теста при использовании Visual Web Developer.


[![Диалоговое окно нового проекта](iteration-1-create-the-application-cs/_static/image2.jpg)](iteration-1-create-the-application-cs/_static/image3.png)

**На рисунке 02**: диалоговое окно Создание проекта модульных тестов ([Просмотр полноразмерное изображение](iteration-1-create-the-application-cs/_static/image4.png))


Приложение ASP.NET MVC, появится в окне обозревателя решений Visual Studio (см. рис. 3). Если пункт не отображается в окне обозревателя решений, это окно можно открыть, выбрав параметр меню **вид, обозреватель решений**. Обратите внимание, что решение содержит два проекта: проект ASP.NET MVC и тестовый проект. Проект ASP.NET MVC имеет имя ContactManager и тестовый проект называется ContactManager.Tests.


[![Диалоговое окно нового проекта](iteration-1-create-the-application-cs/_static/image3.jpg)](iteration-1-create-the-application-cs/_static/image5.png)

**На рисунке 03**: в окне обозревателя решений ([Просмотр полноразмерное изображение](iteration-1-create-the-application-cs/_static/image6.png))


## <a name="deleting-the-project-sample-files"></a>Удаление файлов образца проекта

Шаблон проекта ASP.NET MVC включает файлы образцов для контроллеров и представлений. Перед созданием нового приложения ASP.NET MVC, следует удалить эти файлы. Можно удалить файлы и папки в окне обозревателя решений, правой кнопкой мыши файл или папку и выбрав пункт меню **удалить**.

Необходимо удалить следующие файлы из проекта ASP.NET MVC:

- \Controllers\HomeController.cs

- \Views\Home\About.aspx

- \Views\Home\Index.aspx

Кроме того, необходимо удалить следующий файл из тестового проекта:

\Controllers\HomeControllerTest.cs

## <a name="creating-the-database"></a>Создание базы данных

Приложение диспетчера контактов является управляемой базы данных веб-приложения. Мы используем базу данных для хранения сведений о контактах.

Платформа ASP.NET MVC с любой современной базы данных, включая базы данных Microsoft SQL Server, Oracle, MySQL и IBM DB2. В этом учебнике мы используем базы данных Microsoft SQL Server. При установке Visual Studio предоставляется возможность установки Microsoft SQL Server Express которого — это бесплатная версия базы данных Microsoft SQL Server.

Создать новую базу данных, щелкнув правой кнопкой мыши приложение\_папки данных в окне обозревателя решений и выбрав пункт меню **добавить, новый элемент**. В **Добавление нового элемента** диалогового окна выберите **данные** категории и **базы данных SQL Server** шаблона (см. рис. 4). Имя новой базы данных ContactManagerDB.mdf и нажмите кнопку "ОК".


[![Диалоговое окно нового проекта](iteration-1-create-the-application-cs/_static/image4.jpg)](iteration-1-create-the-application-cs/_static/image7.png)

**На рисунке 04**: Создание новой базы данных Microsoft SQL Server Express ([Просмотр полноразмерное изображение](iteration-1-create-the-application-cs/_static/image8.png))


После создания новой базы данных, базы данных отображается в приложении\_папки данных в окне обозревателя решений. Дважды щелкните файл ContactManager.mdf, чтобы открыть окно обозревателя серверов и подключения к базе данных.

> [!NOTE] 
> 
> Окно обозревателя серверов, называется окно обозревателя базы данных в случае Microsoft Visual Web Developer.


Окно обозревателя серверов можно использовать для создания новых объектов базы данных, таких как таблицы базы данных, представления, триггеры и хранимые процедуры. Щелкните правой кнопкой мыши папку «таблицы» и выберите пункт меню в **добавить новую таблицу**. Конструктор таблиц базы данных отображается (см. рис. 5).


[![Диалоговое окно нового проекта](iteration-1-create-the-application-cs/_static/image5.jpg)](iteration-1-create-the-application-cs/_static/image9.png)

**На рисунке 05**: конструктора таблиц базы данных ([Просмотр полноразмерное изображение](iteration-1-create-the-application-cs/_static/image10.png))


Необходимо создать таблицу, которая содержит следующие столбцы:

<a id="0.1_table01"></a>


| **Имя столбца** | **Тип данных** | **Разрешить значения NULL** |
| --- | --- | --- |
| Идентификатор | int | False |
| FirstName | nvarchar(50) | False |
| LastName | nvarchar(50) | False |
| Номер телефона | nvarchar(50) | False |
| Адрес эл. почты | nvarchar(255) | False |


Первый столбец, столбец идентификатора является специальной. Необходимо пометить как столбец идентификаторов и первичный ключевой столбец со столбцом идентификаторов. Можно указать, что столбец является столбцом идентификаторов, развернув свойств столбца (найдите в нижней части рис. 6) и прокрутка вниз до свойства Спецификация идентификации. Задать **(идентификатор)** значение **Да**.

Пометить столбец как столбец первичного ключа, выберите столбец и нажмите кнопку со значком ключа. После некоторый столбец помечен как столбец первичного ключа, появится значок ключа рядом со столбцом (см. рис. 6).

После создания таблицы, нажмите кнопки «Сохранить» (кнопка со значком гибкого) для сохранения новой таблицы. Присвойте имя новой таблицы *контактов*.

После завершения создания базы данных таблицы Contacts следует добавить некоторые записи в таблицу. Щелкните правой кнопкой мыши в таблице Contacts в окне обозревателя решений и выбрать пункт меню **Показать таблицу данных**. Введите один или несколько контактов в появившейся сетке.

## <a name="creating-the-data-model"></a>Создание модели данных

Приложение ASP.NET MVC состоит из моделей, представлений и контроллеров. Мы начнем с создания модели класс, представляющий таблице Contacts, созданную в предыдущем разделе.

В этом учебнике мы используем Microsoft Entity Framework для автоматического создания модели из базы данных.

> [!NOTE] 
> 
> Платформа ASP.NET MVC не привязан к Microsoft Entity Framework каким-либо образом. ASP.NET MVC можно использовать с технологиями доступа к альтернативной базы данных, включая NHibernate, LINQ to SQL или ADO.NET.


Выполните следующие действия для создания классов модели данных.

1. Щелкните правой кнопкой мыши папку модели в окне обозревателя решений и выберите **добавить, новый элемент**. **Добавление нового элемента** откроется диалоговое окно (см. рис. 6).
2. Выберите **данные** категории и **ADO.NET Entity Data Model** шаблона. Имя модели данных *ContactManagerModel.edmx* и нажмите кнопку **добавить** кнопки. Появится мастер модели EDM, в (см. рис. 7).
3. В **Выбор содержимого модели** шаг, выберите **создать из базы данных** (см. рис. 7).
4. В **Выбор подключения к данным** шаг, выберите базу данных ContactManagerDB.mdf и введите имя *ContactManagerDBEntities* для настройки подключения сущности (см. рис. 8).
5. В **Выбор объектов базы данных** шаг, установленном флажке таблицы (см. рис. 9). Модель данных будет содержать все таблицы, содержащиеся в базе данных (не существует только один, в таблице Contacts). Введите пространство имен *моделей*. Нажмите кнопку "Готово", чтобы завершить работу мастера.


[![Диалоговое окно нового проекта](iteration-1-create-the-application-cs/_static/image6.jpg)](iteration-1-create-the-application-cs/_static/image11.png)

**На рисунке 06**: диалоговое окно добавления нового элемента ([Просмотр полноразмерное изображение](iteration-1-create-the-application-cs/_static/image12.png))


[![Диалоговое окно нового проекта](iteration-1-create-the-application-cs/_static/image7.jpg)](iteration-1-create-the-application-cs/_static/image13.png)

**На рисунке 07**: Выбор содержимого модели ([Просмотр полноразмерное изображение](iteration-1-create-the-application-cs/_static/image14.png))


[![Диалоговое окно нового проекта](iteration-1-create-the-application-cs/_static/image8.jpg)](iteration-1-create-the-application-cs/_static/image15.png)

**На рисунке 08**: Выбор подключения к данным ([Просмотр полноразмерное изображение](iteration-1-create-the-application-cs/_static/image16.png))


[![Диалоговое окно нового проекта](iteration-1-create-the-application-cs/_static/image9.jpg)](iteration-1-create-the-application-cs/_static/image17.png)

**На рисунке 09**: Выбор объектов базы данных ([Просмотр полноразмерное изображение](iteration-1-create-the-application-cs/_static/image18.png))


После завершения мастера моделей EDM, откроется конструктор модели EDM. Конструктор отображает класс, который соответствует для каждой таблицы моделируемого. Вы увидите один класс с именем контактов.

Мастер модели EDM создает имена классов на основе имен таблицы базы данных. Почти всегда необходимо изменить имя класса, созданные с помощью мастера. Щелкните правой кнопкой мыши класс контактов в конструкторе и выберите пункт меню в **переименование**. Измените имя класса из контактов (во множественном числе) контакт (единственное). После изменения имени класса, класс должен выглядеть как на рис. 10.


[![Диалоговое окно нового проекта](iteration-1-create-the-application-cs/_static/image10.jpg)](iteration-1-create-the-application-cs/_static/image19.png)

**Рис. 10**: класс контакт ([Просмотр полноразмерное изображение](iteration-1-create-the-application-cs/_static/image20.png))


На этом этапе мы создали нашей модели базы данных. Контакт класс можно использовать для представления к конкретной записи контактов в базе данных.

## <a name="creating-the-home-controller"></a>Создание контроллера Home

Следующим шагом является создание нашей контроллера Home. Контроллер Home является по умолчанию вызывается в приложении ASP.NET MVC.

Создайте класс контроллера Home, щелкнув правой кнопкой мыши папку Controllers в окне обозревателя решений и выбрав пункт меню **Add, контроллер** (см. рис. 11). Обратите внимание, флажок **добавить методы действий для сценариев создания, обновления и сведения о**. Убедитесь, что этот флажок установлен перед нажатием кнопки **добавить** кнопки.


[![Диалоговое окно нового проекта](iteration-1-create-the-application-cs/_static/image11.jpg)](iteration-1-create-the-application-cs/_static/image21.png)

**Рис. 11**: Добавление контроллера Home ([Просмотр полноразмерное изображение](iteration-1-create-the-application-cs/_static/image22.png))


При создании контроллера Home, вы получаете класс в список 1.

**Листинг 1 - Controllers\HomeController.cs**

[!code-csharp[Main](iteration-1-create-the-application-cs/samples/sample1.cs)]

## <a name="listing-the-contacts"></a>Список контактов

Чтобы отобразить записи в таблице базы данных контактов, нам нужно создания Index() действие и просмотра индекса.

Контроллер Home уже содержит Index() действие. Нам нужно изменить этот метод, чтобы он выглядел листинг 2.

**Перечисление Controllers\HomeController.cs. 2.**

[!code-csharp[Main](iteration-1-create-the-application-cs/samples/sample2.cs)]

Обратите внимание, что класс контроллера Home в списке 2 содержит закрытое поле с именем \_сущностей. \_Поле сущности представляет сущностей из модели данных. Мы используем \_поле сущности для взаимодействия с базой данных.

Метод Index() возвращает представление, которое представляет все контакты из таблицы базы данных контактов. Выражение \_сущностей. ContactSet.ToList() возвращает список контактов в виде универсального списка.

Теперь, мы хранять создан индекс контроллера, далее, необходимо создать индекс представления. Перед созданием индекса представления, скомпилируйте приложение, выбрав параметр меню **построить, построить решение**. Всегда следует скомпилировать проект перед добавлением в порядке для списка классов модели для отображения в представлении **добавить представление** диалогового окна.

Создание индекса представления, щелкнув правой кнопкой мыши метод Index() и выбрав пункт меню **добавить представление** (см. рис. 12). При выборе этого варианта меню **добавить представление** диалогового окна (см. рис. 13).


[![Диалоговое окно нового проекта](iteration-1-create-the-application-cs/_static/image12.jpg)](iteration-1-create-the-application-cs/_static/image23.png)

**Рис. 12**: Добавление индекса представления ([Просмотр полноразмерное изображение](iteration-1-create-the-application-cs/_static/image24.png))


В **добавить представление** диалогового окна, установите флажок "с меткой" **создать строго типизированное представление**. Выберите класс представления данных ContactManager.Models.Contact и просмотр содержимого списка. Выбор этих параметров создает представление, отображающее список записей, обратитесь в службу.


[![Диалоговое окно нового проекта](iteration-1-create-the-application-cs/_static/image13.jpg)](iteration-1-create-the-application-cs/_static/image25.png)

**Рис. 13**: диалоговое окно добавления представления ([Просмотр полноразмерное изображение](iteration-1-create-the-application-cs/_static/image26.png))


При нажатии кнопки **добавить** создается кнопка, просмотр индекса в списке 3. Обратите внимание &lt;% @ Page %&gt; директивы, который отображается в верхней части файла. Индекс наследовало от ViewPage&lt;IEnumerable&lt;ContactManager.Models.Contact&gt; &gt; класса. Другими словами класс модели в представлении представляет список сущностей, обратитесь в службу.

Текст в представлении индекса содержит цикл, который выполняет итерацию всех контактов, представленный классом модели. Значение каждого свойства класса контакта отображается в HTML-таблицу.

**Листинг 3 - Views\Home\Index.aspx (без изменений)**

[!code-aspx[Main](iteration-1-create-the-application-cs/samples/sample3.aspx)]

Необходимо внести одно изменение в представлении индекса. Так как мы не создается представление сведений, мы можем удалить ссылку сведения. Найдите и удалите следующий код в представлении индекса:

{Идентификатор = элемент. % Идентификатор})&gt;

После изменения индекса представления можно запустить приложение диспетчера контактов. Выберите пункт меню Отладка, начать отладку или просто нажмите клавишу F5. При первом запуске запустите приложение, вы получаете диалогового окна на рис. 14. Выберите параметр **измените файл Web.config для включения отладки** и нажмите кнопку "ОК".


[![Диалоговое окно нового проекта](iteration-1-create-the-application-cs/_static/image14.jpg)](iteration-1-create-the-application-cs/_static/image27.png)

**Рис. 14**: включение отладки ([Просмотр полноразмерное изображение](iteration-1-create-the-application-cs/_static/image28.png))


По умолчанию возвращается представление Index. В этом представлении перечислены все данные из таблицы Contacts базы данных (см. рис. 15).


[![Диалоговое окно нового проекта](iteration-1-create-the-application-cs/_static/image15.jpg)](iteration-1-create-the-application-cs/_static/image29.png)

**Рис. 15**: индекс представления ([Просмотр полноразмерное изображение](iteration-1-create-the-application-cs/_static/image30.png))


Обратите внимание, что просмотр индекса содержит ссылку с меткой создать в нижней части представления. В следующем разделе вы узнаете, как создание новых контактов.

## <a name="creating-new-contacts"></a>Создание новых контактов

Чтобы разрешить пользователям создавать новые контакты, нам нужно добавить два действия Create() контроллера Home. Нам нужно создать одно действие Create(), который возвращает HTML-форму для создания нового контакта. Необходимо создать второе действие Create(), выполняющий вставки нового элемента реальной базы данных.

Новых Create() методы, которые необходимо добавить в контроллер Home содержатся в листинге 4.

**Листинг 4 - Controllers\HomeController.cs (с создавать методы)**

[!code-csharp[Main](iteration-1-create-the-application-cs/samples/sample4.cs)]

Первый метод Create() может вызываться с помощью HTTP GET, пока второй метод Create() может быть вызван только HTTP POST. Другими словами второй метод Create() может вызываться только при учете формы HTML. Первый метод Create() просто возвращает представление, содержащее форма HTML для создания нового контакта. Второй метод Create() — гораздо более интересным: Добавляет новый контакт в базу данных.

Обратите внимание, что второй метод Create() была изменена, чтобы принять экземпляр класса контакта. Форма значений, переданных из формы HTML, привязываются к этому классу контакт платформой ASP.NET MVC автоматически. Каждого поля формы из формы HTML создать назначается свойство параметра контакта.

Обратите внимание, что параметр контакт снабжен атрибута [Bind]. Атрибут [привязки] используется для исключения свойство идентификатора контакта из привязки. Так как свойство Id представляет свойство Identity, мы не хотите t, необходимо задать свойство идентификатора.

В теле метода Create() Entity Framework используется для вставки нового контакта в базе данных. Новый контакт добавляется в существующий набор контакты и вызове метода SaveChanges() принудительно отправить эти изменения обратно в основной базе данных.

Можно создавать HTML-формы для создания новых контактов, щелкнув правой кнопкой мыши один из двух методов Create() и выбрав пункт меню **добавить представление** (см. рис. 16).


[![Диалоговое окно нового проекта](iteration-1-create-the-application-cs/_static/image16.jpg)](iteration-1-create-the-application-cs/_static/image31.png)

**На рисунке 16**: Добавление представления создания ([Просмотр полноразмерное изображение](iteration-1-create-the-application-cs/_static/image32.png))


В **добавить представление** диалогового окна выберите **ContactManager.Models.Contact** класса и **создать** параметр для представления содержимого (см. Рисунок 17). При нажатии кнопки **добавить** кнопку Create view, создается автоматически.


[![Диалоговое окно нового проекта](iteration-1-create-the-application-cs/_static/image17.jpg)](iteration-1-create-the-application-cs/_static/image33.png)

**Рисунок 17**: страница разрезать ([Просмотр полноразмерное изображение](iteration-1-create-the-application-cs/_static/image34.png))


Создать представление содержит поля формы для каждого из свойств класса контакта. Код для представления создания включается в листинге 5.

**Список 5 - Views\Home\Create.aspx**

[!code-aspx[Main](iteration-1-create-the-application-cs/samples/sample5.aspx)]

После изменения методов Create() и Добавление представления создания, можно запустить приложение диспетчера контактов и создание новых контактов. Нажмите кнопку **создать новый** ссылку, которая появляется в представлении индекса в представлении "Создать". Вы увидите представление на рисунке 18.


[![Диалоговое окно нового проекта](iteration-1-create-the-application-cs/_static/image18.jpg)](iteration-1-create-the-application-cs/_static/image35.png)

**На рисунке 18**: Create View ([Просмотр полноразмерное изображение](iteration-1-create-the-application-cs/_static/image36.png))


## <a name="editing-contacts"></a>Изменения контактов

Добавление функциональности для редактирования запись контакта очень сходно с добавлением функциональные возможности для создания новой записи контактов. Во-первых необходимо добавить два новых метода изменения в класс контроллера Home. Эти новые методы Edit() содержатся в 6 со списком.

**Перечисление 6 - Controllers\HomeController.cs (с помощью методов редактирования)**

[!code-csharp[Main](iteration-1-create-the-application-cs/samples/sample6.cs)]

Первый метод Edit() вызывается операция HTTP GET. Этот метод, который представляет идентификатор контакте редактируемого передается параметр Id. Платформа Entity Framework используется для извлечения контактов, который соответствует идентификатору. Представление, содержащее форму HTML для редактирования запись возвращается.

Второй метод Edit() выполняет фактического обновления к базе данных. Этот метод принимает экземпляр класса контакта как параметр. Платформа ASP.NET MVC привязывает поля формы в форме редактирования к этому классу автоматически. Обратите внимание, что вы не хотите t включает атрибут [привязки] при редактировании контакт (требуется значение свойства Id).

Entity Framework позволяет сохранить измененный контакта в базе данных. Исходного контакта необходимо сначала извлечь из базы данных. Затем метод Entity Framework ApplyPropertyChanges() вызывается для записи изменений для контакта. Наконец метод Entity Framework SaveChanges() вызывается для сохранения изменений в основную базу данных.

Вы можете создать представление, содержащее форме редактирования, щелкните правой кнопкой мыши метод Edit() и выбрав пункт меню Добавить представление. В диалоговом окне Добавить представление, выберите **ContactManager.Models.Contact** класса и **изменить** просмотра содержимого (см. на рисунке 19).


[![Диалоговое окно нового проекта](iteration-1-create-the-application-cs/_static/image19.jpg)](iteration-1-create-the-application-cs/_static/image37.png)

**На рисунке 19**: Добавление представления изменения ([Просмотр полноразмерное изображение](iteration-1-create-the-application-cs/_static/image38.png))


При нажатии кнопки Добавить новое представление изменения будет создан автоматически. HTML-формы, которое создается, содержит поля, которые соответствуют каждому из свойств класса контакт (см. Листинг 7).

**Листинг 7 - Views\Home\Edit.aspx**

[!code-aspx[Main](iteration-1-create-the-application-cs/samples/sample7.aspx)]

## <a name="deleting-contacts"></a>Удаление контактов

Если вы хотите удалять контакты, необходимо добавить два действия Delete() класс контроллера Home. Первое действие Delete() отображает форму подтверждения удаления. Второе действие Delete() выполняет фактическое удаление.

> [!NOTE] 
> 
> Более поздней версии в итерации #7, мы изменить диспетчера контактов таким образом, чтобы он поддерживает один шаг, удалить Ajax.


В список 8 содержатся два новых метода Delete().

**Перечисление 8 - Controllers\HomeController.cs (методы удаления)**

[!code-csharp[Main](iteration-1-create-the-application-cs/samples/sample8.cs)]

Первый метод Delete() возвращает форму подтверждения удаления записи контакта из базы данных (см. Figure20). Второй метод Delete() выполняет операции фактического удаления в базе данных. После получения исходного контакта из базы данных Entity Framework DeleteObject() и SaveChanges() методы вызываются выполнение удаления базы данных.


[![Диалоговое окно нового проекта](iteration-1-create-the-application-cs/_static/image20.jpg)](iteration-1-create-the-application-cs/_static/image39.png)

**Рис. 20**: представление подтверждение удаления ([Просмотр полноразмерное изображение](iteration-1-create-the-application-cs/_static/image40.png))


Нам нужно изменить представление Index таким образом, чтобы он содержит ссылки на удаление записей о контактах (см. рисунок 21). Необходимо добавить следующий код в одной ячейке таблицы, который содержит ссылку "Изменить":

Html.ActionLink ({id = элемент. % Идентификатор})&gt;


[![Диалоговое окно нового проекта](iteration-1-create-the-application-cs/_static/image21.jpg)](iteration-1-create-the-application-cs/_static/image41.png)

**Рисунок 21**: индекс представления с ссылку "Изменить" ([Просмотр полноразмерное изображение](iteration-1-create-the-application-cs/_static/image42.png))


Теперь нам нужны для создания представления подтверждения удаления. Щелкните правой кнопкой мыши метод в класс контроллера Home Delete() и выбрать пункт меню Добавить представление. Открывается диалоговое окно добавления представления, в (см. Рисунок 22).

В отличие от в случае представления списка, создание и редактирование диалоговое окно добавления представления не содержит параметр, чтобы создать представление удаления. Вместо этого выберите **ContactManager.Models.Contact** класс данных и **пустой** просмотра содержимого. При выборе пустое представление, что параметр содержимого потребуется создать представление сами.


[![Диалоговое окно нового проекта](iteration-1-create-the-application-cs/_static/image22.jpg)](iteration-1-create-the-application-cs/_static/image43.png)

**На рисунке 22**: Добавление представления удаления подтверждения ([Просмотр полноразмерное изображение](iteration-1-create-the-application-cs/_static/image44.png))


Содержимое представления удаления содержится в Листинг 9. Это представление содержит формы, подтверждает ли определенного контакта должен быть удален (см. рисунок 21).

**Листинг 9 - Views\Home\Delete.aspx.**

[!code-aspx[Main](iteration-1-create-the-application-cs/samples/sample9.aspx)]

## <a name="changing-the-name-of-the-default-controller"></a>Изменение имени контроллера по умолчанию

Он может использоваться имя класса контроллера для работы с контактами с именами класс HomeController. T не старее контроллера называться ContactController?

Эта проблема является довольно легко исправить. Во-первых необходимо выполнить рефакторинг имени контроллера Home. Откройте класс HomeController в редакторе кода Visual Studio, щелкните правой кнопкой мыши имя класса и выберите пункт меню в **рефакторинга и переименования**. При выборе этого параметра меню открывает диалоговое окно переименования.


[![Диалоговое окно нового проекта](iteration-1-create-the-application-cs/_static/image23.jpg)](iteration-1-create-the-application-cs/_static/image45.png)

**На рисунке 23**: рефакторинг имя контроллера ([Просмотр полноразмерное изображение](iteration-1-create-the-application-cs/_static/image46.png))


[![Диалоговое окно нового проекта](iteration-1-create-the-application-cs/_static/image24.jpg)](iteration-1-create-the-application-cs/_static/image47.png)

**Рис. 24**: с помощью диалогового окна Переименование ([Просмотр полноразмерное изображение](iteration-1-create-the-application-cs/_static/image48.png))


При переименовании классе контроллера, имя папки в папке Views будет обновление Visual Studio. Visual Studio будет переименовать папку \Views\Home \Views\Contact папку.

После внесения этого изменения приложение больше не будет контроллера Home. При запуске приложения, появится страница «ошибка» в рис. 25.


[![Диалоговое окно нового проекта](iteration-1-create-the-application-cs/_static/image25.jpg)](iteration-1-create-the-application-cs/_static/image49.png)

**Рис. 25**: без контроллера по умолчанию ([Просмотр полноразмерное изображение](iteration-1-create-the-application-cs/_static/image50.png))


Необходимо обновить маршрут по умолчанию в файле Global.asax для использования контроллера контакт вместо контроллера Home. Откройте файл Global.asax и изменение контроллера по умолчанию, используемые маршрут по умолчанию (см. список 10).

**Перечисление 10 - Global.asax.cs**

[!code-csharp[Main](iteration-1-create-the-application-cs/samples/sample10.cs)]

После внесения этих изменений будет работать диспетчера контактов. Теперь он использовать класс контроллера контакт как контроллера по умолчанию.

## <a name="summary"></a>Сводка

В этой первой итерации мы создано простое приложение диспетчера контактов в наиболее быстрым способом. Мы воспользовался Visual Studio автоматически создать исходный код для наших контроллеры и представления. Мы также воспользовался Entity Framework для автоматического создания наших классов модели базы данных.

В настоящее время мы можно перечислить, создать, изменить и удалить контакты с приложением диспетчера контактов. Другими словами мы выполнить все операции баз данных basic, необходимые для базы данных веб-приложения.

К сожалению наше приложение имеет некоторые проблемы. Первый и я каких-либо опасений это признать, приложение диспетчера контактов не является наиболее полезным приложения. Ему некоторые решения. В следующей итерации мы рассмотрим, как мы можем изменить по умолчанию представления главной страницы и таблицы каскадных стилей для улучшения внешнего вида приложения.

Во-вторых не были реализованы проверку формы. Например нет ничего для предотвращения отправки формы контактов создать без ввода значений для полей формы. Кроме того можно ввести недопустимые телефонных номеров и адресах электронной почты. Мы начнем решение этой задачи проверку формы в итерации #3.

Наконец и что самое главное текущей итерации приложение диспетчера контактов нельзя легко или изменить сохраняется. Например логики доступа к базе данных является помещенного справа в действия контроллера. Это означает, что не удается изменить наш код доступа к данным без изменения наших контроллеров. В последующих итерациях мы исследуем принципы разработки программного обеспечения, которые мы можно реализовать, чтобы сделать более устойчивым к изменить диспетчера контактов.

> [!div class="step-by-step"]
> [Вперед](iteration-2-make-the-application-look-nice-cs.md)
