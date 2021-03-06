---
uid: web-pages/overview/getting-started/introducing-aspnet-web-pages-2/intro-to-web-pages-programming
title: Введение в ASP.NET Web Pages — основы программирования | Документы Microsoft
author: tfitzmac
description: 'Этот учебник дает Общие сведения о том, как программы в веб-страниц ASP.NET с синтаксисом Razor. Вы узнаете: базовый синтаксис «Razor», используйте для pr...'
ms.author: aspnetcontent
manager: wpickett
ms.date: 06/17/2015
ms.topic: article
ms.assetid: 7526ed45-a97d-4e8a-8301-01324ef0eff9
ms.technology: dotnet-webpages
ms.prod: .net-framework
msc.legacyurl: /web-pages/overview/getting-started/introducing-aspnet-web-pages-2/intro-to-web-pages-programming
msc.type: authoredcontent
ms.openlocfilehash: 60115dd06a27bf856427953de29e993194afb991
ms.sourcegitcommit: 477d38e33530a305405eaf19faa29c6d805273aa
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2018
---
<a name="introducing-aspnet-web-pages---programming-basics"></a>Общие сведения о веб-страницах ASP.NET — основы программирования
====================
по [Tom FitzMacken](https://github.com/tfitzmac)

> Этот учебник дает Общие сведения о том, как программы в веб-страниц ASP.NET с синтаксисом Razor.
> 
> Что вы узнаете следующее.
> 
> - Базовый синтаксис «Razor», можно использовать для программирования веб-страницах ASP.NET.
> - Некоторые основные C#, который является языком программирования, который будет использоваться.
> - Некоторые основные понятия программирования для веб-страниц.
> - Как установить пакеты (компоненты, содержащие предварительно подготовленный код) для использования с веб-узла.
> - Как использовать *вспомогательные методы* выполнять типовые задачи программирования.
>   
> 
> Обсуждаются функции и технологии:
> 
> - NuGet и диспетчер пакетов.
> - `Gravatar` Вспомогательные.


Этот учебник предназначен в первую очередь это операция, в которых представлен синтаксис программирования, который будет использоваться для веб-страниц ASP.NET. Вы узнаете о *синтаксисом Razor* и языков программирования, код, написанный на языке C#. Вы ознакомились этот синтаксис в предыдущем учебнике; в этом учебнике вы узнаете, как синтаксис дополнительные.

Обещаем, этот учебник включает программирования вы увидите в одном учебника и что он является единственным учебник, в котором находится большинство *только* о программировании. В оставшихся учебниках в этом наборе фактически создается страницам, не интересных вещей.

Вы также узнаете о *вспомогательные методы*. Вспомогательный объект — это компонент, упакованные вверх фрагмент кода —, можно добавить на страницу. Вспомогательное приложение выполняет работу, в противном случае может быть утомительным или сложных делать вручную.

## <a name="creating-a-page-to-play-with-razor"></a>Создание страницы для воспроизведения в Razor

В этом разделе мы выполним немного Razor, можно получить представление о основной синтаксис.

Запустите WebMatrix, если она еще не запущена. Веб-сайт, созданный в предыдущем учебнике будет использоваться ([Приступая к работе с веб-страниц](https://go.microsoft.com/fwlink/?LinkId=251578)). Чтобы снова открыть его, нажмите кнопку **личных узлов** и выберите **WebPageMovies**:

![WebMatrix начального экрана показаны параметры открыть сайт и выделяются личных сайтов](intro-to-web-pages-programming/_static/image1.png)

Выберите **файлы** рабочей области.

На ленте щелкните **New** для создания страницы. Выберите **CSHTML** и назовите страницу *TestRazor.cshtml*.

Нажмите кнопку **ОК**.

Скопируйте следующий код в файле полной замены, которые уже существует.

> [!NOTE]
> При копировании кода или разметки из примеров в страницу, отступов и выравнивания может не быть такой же, как учебника. Отступов и выравнивания не влияют на способ выполнения кода, однако.


[!code-cshtml[Main](intro-to-web-pages-programming/samples/sample1.cshtml)]

## <a name="examining-the-example-page"></a>Пример страницы проверки

Большая часть вы видите — обычный HTML-код. Тем не менее в верхней находится этот блок кода:

[!code-cshtml[Main](intro-to-web-pages-programming/samples/sample2.cshtml)]

Обратите внимание на следующие момента о блоке кода:

- Символ @ сообщает ASP.NET, ниже приведен код Razor, не HTML. ASP.NET обрабатывает все, что после @ символа как код, пока не будет запущен в HTML-ФАЙЛ еще раз. (В этом случае с &lt;! DOCTYPE&gt; элемента.
- Фигурные скобки ({и}) заключайте блок кода Razor, если код содержит более одной строки. Фигурные скобки сообщить ASP.NET, где код для этого блока начинается и заканчивается.
- / / Символы обозначения комментариев — то есть, часть кода, который не будет выполняться.
- Каждая инструкция имеет конечную точку с запятой (;). (Не в комментарии, однако.)
- Можно хранить значения в *переменных*, который создается (*объявить*) с помощью ключевого слова var. При создании переменной можно присвоить ему имя, которое может включать буквы, цифры и символ подчеркивания (\_). Имена переменных не может начинаться с цифры и не может использовать имя программного ключевого слова (например, var).
- Символьные строки (например, «ASP.NET» и «Веб-страниц») заключите в кавычки. (Они должны быть двойные кавычки). Числа не заключаются в кавычки.
- Пробелы за пределами кавычек не имеет значения. Разрывы строк практически не имеет значения; исключением является строкой в кавычках не может разбить по строкам. Не имеет значения отступов и выравнивания.

Это не очевидно из этого примера является весь код с учетом регистра. Это означает, что TheSum переменной другой переменной, чем переменные, которые может называться theSum или thesum. Аналогично var является ключевым словом, но Var не.

### <a name="objects-and-properties-and-methods"></a>Объекты и свойства и методы

То есть выражение DateTime.Now. Проще говоря, даты и времени — *объекта*. Объект является вещь, можно программировать — страницы, текстовое поле, файл, изображения, веб-запроса, сообщение электронной почты, запись клиента, и т. д. Объекты имеют один или несколько *свойства* , описывающие их характеристики. Объект-поле имеет свойство Text (среди прочих), объект запроса имеет свойство URL-адреса (и других), сообщение электронной почты имеет свойства From и свойство To, и т. д. Объекты также имеют *методы* , которые они могут выполнять «команды». Вы будете работать с объектами во многом.

Как видно из примера DateTime находится объект, который позволяет программе даты и времени. Он содержит свойство с именем теперь, возвращает текущую дату и время.

### <a name="using-code-to-render-markup-in-the-page"></a>Использование кода для визуализации разметки на странице

В основной области страницы Обратите внимание на следующее:

[!code-html[Main](intro-to-web-pages-programming/samples/sample3.html)]

Еще раз символ @ сообщает ASP.NET, ниже приведен код, не HTML. В разметке можно добавить следуют выражения кода, и платформа ASP.NET отображать значения этого выражения вправо на данный момент. В примере @a будут отображаться все, что значение переменной с именем, @product отображает указаны в переменной названного продукта и т. д.

Можно не только к переменным, хотя. В некоторых случаях, символ @ перед выражением:

- @(\*b) отображает совокупность на переменные и b. ( \* Оператор означает умножение.)
- @(технология + "" + продукта) отрисовывает значений в переменных технологии и продуктов после их объединения и добавления пробела между ними. Оператор (+) для объединения строк является таким же, как оператор сложения чисел. ASP.NET обычно можно определить, можно ли работе с числами или строками, то вправо, с помощью оператора +.
- @Request.Url Отображает свойства URL-адрес объекта запроса. Объект запроса содержит сведения о текущем запросе из браузера, а само собой свойство URL-адрес содержит URL-адрес текущего запроса.

Пример также демонстрирует, вы можете работать по-разному. Можно выполнять вычисления в блок кода в верхней, помещает результат в переменной и затем отображать переменной в разметке. Или можно выполнять вычисления выражения справа в разметке. Используется подход зависит от выполняемых задач и, в некоторой степени на собственных предпочтений.

### <a name="seeing-the-code-in-action"></a>Просмотр кода в действии

Щелкните правой кнопкой мыши имя файла и нажмите кнопку **запуск в браузере**. Вы увидите страницу в браузере с всех значений и выражений, которые разрешены на странице.

![Страница «TestRazor», выполняются в браузере](intro-to-web-pages-programming/_static/image2.png)

Посмотрите на источник в браузере.

!['Test Razor» исходный код страницы в браузере](intro-to-web-pages-programming/_static/image3.png)

Как и следует ожидать от работы в предыдущем учебнике ни один кода Razor, на странице. Все, что вы видите — это фактическое значения. При запуске страницы реальных запроса на веб-сервер, который встроен в WebMatrix. При получении запроса ASP.NET разрешает значений и выражений и отображает их значения на странице. После этого он отправляет страницу браузера.

> [!TIP] 
> 
> **Razor и C#**
> 
> До сих мы указали, что работа с синтаксисом Razor. Это верно, но не является описание функциональности. Фактическое язык программирования, вы используете называется *C#*. C# был создан корпорацией Майкрософт более десяти лет назад и стал одним из первичного языков программирования для создания приложений Windows. Все правила, которые вы уже видели об имени переменной и создания инструкций и т. д, фактически все правила в языке C#.
> 
> В частности к небольшому числу соглашения о том, как внедрить этот код в страницу ссылается Razor. Например, соглашение о том, с помощью, чтобы пометить код на странице и @ {} для внедрения блока кода является аспектом Razor страницы. Вспомогательные функции, также считаются частью Razor. В других местах, чем просто веб-страницах ASP.NET используется синтаксис Razor. (Например, он используется в представления ASP.NET MVC также.)
> 
> Мы упомянем, так как искать сведения о программирования веб-страниц ASP.NET, можно найти множество ссылок на Razor. Тем не менее много эти ссылки не применимы к выполняется это сведения и поэтому могут вызвать путаницу. И в действительности многие вопросы по программированию действительно должны быть о работе с C# или работе с ASP.NET. Поэтому если вы специально для получения сведений о Razor, может оказаться не необходимые ответы.


## <a name="adding-some-conditional-logic"></a>Добавление условную логику

Одна из замечательных функций об использовании кода на странице — что можно изменить, что происходит на основе различных условий. В этой части учебника мы выполним несколько способов изменения данных, отображающихся на странице.

Пример будет простой и несколько надуманный, чтобы мы позволяет сосредоточиться на условной логики. Страница, которую вы создадите для этого:

- Отображение другого текста на странице, в зависимости от того, является ли он при первом отображении страницы или ли кнопка была нажата кнопка для передачи на странице. Используется первая проверка условия.
- Отображать сообщение только в том случае, если определенное значение передается в строке запроса URL-адреса (http://...?show=true). Используется вторая проверка условия.

В WebMatrix, создайте страницу и назовите его *TestRazorPart2.cshtml*. (На ленте щелкните **New**, выберите **CSHTML**, назовите файл и нажмите кнопку **ОК**.)

Замените содержимое этой страницы с помощью следующего:

[!code-cshtml[Main](intro-to-web-pages-programming/samples/sample4.cshtml)]

Блок кода в верхней инициализирует переменную с именем сообщение с какой-либо текст. В основной области страницы, содержимое переменной сообщение отображается внутри &lt;p&gt; элемента. Разметка также содержит &lt;ввода&gt; создаваемый элемент **отправить** кнопки.

Запустите страницу, чтобы просмотреть их работу. Сейчас это по сути статической страницы, даже при нажатии кнопки **отправить** кнопки.

Вернитесь в WebMatrix. Добавьте следующий выделенный код в пределах блока кода, *после* строки, которая инициализирует сообщение:

[!code-cshtml[Main](intro-to-web-pages-programming/samples/sample5.cshtml?highlight=4-6)]

### <a name="the-if---block"></a>Если блок {}

Только что добавленный был if условие. В коде Если условие имеет структуру следующим образом:

[!code-csharp[Main](intro-to-web-pages-programming/samples/sample6.cs)]

Проверяемое условие, указан в скобках. Он должен иметь значение или выражение, возвращающее значение true или false. Если условие равно true, ASP.NET выполняет инструкцию или инструкции, которые находятся внутри фигурных скобок. (Они *затем* частью *if-then* логику.) Если условие равно false, пропускается блока кода.

Вот несколько примеров условий можно проверить в операторе if инструкции:

[!code-csharp[Main](intro-to-web-pages-programming/samples/sample7.cs)]

Можно проверить переменные, значения или выражения с помощью <em>логический оператор</em> или <em>оператор сравнения</em>: равно (==), больше (&gt;), меньше (&lt;), больше или равно (&gt;=) и меньше или равно (&lt;=). ! = Не равно означает оператор — например, если (! = 0) означает <em>Если</em> <em>a</em><em>не равно 0</em>.

> [!NOTE]
> Убедитесь, что вы Обратите внимание, что оператора сравнения равно (==) не так же, как =. = Только для присвоения значений используется оператор (var = 2). Если эти операторы смешать, либо приведет к ошибке или получите непредвиденных результатов.


Чтобы убедиться, что-нибудь имеет значение true, является полный синтаксис if(IsDone == true). Однако можно также использовать if(IsDone) ярлык. Если нет оператора сравнения, ASP.NET предполагает тестировании для значения верно.

! оператор сам по себе означает логическое не. Например, условие if (! IsPost) означает *Если IsPost не выполняется*.

Можно сочетать условия с помощью логического и (&amp; &amp; оператор) или логического или (|| оператор). Например, последнего if условий в предыдущем означает примеры *Если FileProcessingIsDone не присвоено значение true, и displayMessage имеет значение false*.

### <a name="the-else-block"></a>Блок else

Заключительную о блоках: Если блок может следовать блок else. Полезно блок else необходимо выполнить другой код, если условие имеет значение false. Ниже приведен простой пример.

[!code-csharp[Main](intro-to-web-pages-programming/samples/sample8.cs)]

Вы увидите некоторые примеры на следующих занятиях рассматривается в этой серии, в которых удобно использовать блок else.

### <a name="testing-whether-the-request-is-a-submit-post"></a>Проверка, является ли запрос отправки (post)

Больше, но вернемся к в примере, который имеет условие if(IsPost) {...}. IsPost является фактически свойством текущей страницы. В первом запросе страницы IsPost возвращает значение false. Тем не менее при нажатии кнопки, или отправить страницу в противном случае — то есть блога — IsPost возвращает значение true. Таким образом IsPost позволяет определить, является ли вы имеете дело с отправки формы. (С точки зрения HTTP-команды, если запрос выполняется операция GET, IsPost возвращает значение false. Если запрос на операцию POST, IsPost возвращает значение true.) В этом руководстве вы будете работать с формами ввода, где этот тест будет особенно полезно.

Запустите страницу. Поскольку это первый раз запрошены странице вы видите «Является в первый раз, запрашиваемая страница». Строка имеет значение, которое инициализировать переменную сообщения. If(IsPost) тест выполняется, но, возвращает значение false, если в данный момент, блокируют код внутри оператора if не запускается.

Нажмите кнопку **отправить** кнопки. Страница запрашивается еще раз. Как до, сообщение переменной задается «Это в первый раз...». Но на этот раз if(IsPost) тест возвращает значение true, поэтому блок кода внутри оператора if. В коде изменяется значение переменной сообщение в другое значение, которое будет отображаться в разметке.

Теперь добавьте if условие в разметке. Ниже &lt;p&gt; элемент, содержащий **отправить** , добавьте следующую разметку:

[!code-cshtml[Main](intro-to-web-pages-programming/samples/sample9.cshtml)]

Вы добавляете код в разметке, их необходимо начинать с @. То есть выражение if теста, аналогичном расположению, добавленный ранее в блоке кода. В фигурных скобках, однако вы добавляете обычный HTML-код — по крайней мере, это обычный пока достигнет @DateTime.Now. Это другой небольшого фрагмента кода Razor, и опять же необходимо добавить перед ним.

Суть в том, что можно добавить, если условия, как в код блока в начале и в разметке. Если вы используете if условие в теле страницы внутри блока строк может быть разметки или кода. В этом случае и как имеет значение true, в любое время можно сочетать разметку и код, необходимо использовать, чтобы сделать снимите флажок, чтобы ASP.NET его.

Запустите страницу и щелкните **отправить**. Это время не появляется только разные сообщения при отправке («после отправки...»), но вы видите новое сообщение, которое указывает дату и время.

![Страница «тестирование Razor 2", выполняются в браузере с меткой времени, показывающий после отправки](intro-to-web-pages-programming/_static/image4.png)

### <a name="testing-the-value-of-a-query-string"></a>Проверка значения строки запроса

Один дополнительные тест. На этот раз вам предстоит добавить if блок, который проверяет значение с именем показывают, что может быть передано в строке запроса. (Следующим образом: `http://localhost:43097/TestRazorPart2.cshtml?show=true`) вы измените страницу, чтобы сообщение вы отображение («Это в первый раз...», т. д.) отображается только в том случае, если отображается значение true.

В нижней (но внутри) блок кода в верхней части страницы, добавьте следующее:

[!code-csharp[Main](intro-to-web-pages-programming/samples/sample10.cs)]

Теперь посмотрите блок полный код имеет следующий вид. (Помните, что при копировании код на страницу, отступы может выглядеть иначе. Однако, не влияет на способ выполнения кода.)

[!code-cshtml[Main](intro-to-web-pages-programming/samples/sample11.cshtml)]

Новый код в блоке инициализирует переменную с именем showMessage значение false. Затем он выполняет if теста для поиска значения в строке запроса. При первом запросе страницы, он имеет URL-адрес, похожее на следующее:

`http://localhost:43097/TestRazorPart2.cshtml`

Код определяет, содержит ли URL-адрес переменной с именем отображать в строке запроса, как эта версия URL-адрес:

`http://localhost:43097/TestRazorPart2.cshtml`? Показать = true

Сам тест анализирует свойства QueryString объекта запроса. Если строка запроса содержит элемент с именем Показать, и если этот элемент имеет значение true, если блок выполняется и присваивает переменной showMessage значение true.

Нет нюанс, как показано. Как говорит: имя строки запроса — это строка. Тем не менее можно только для проверки true и false, если вы тестируете значение логическое значение (ИСТИНА или ЛОЖЬ). Перед тестированием значение переменной отображения в строке запроса, необходимо преобразовать его в значение типа Boolean. Это метод AsBool не — она принимает строку в качестве входных данных и преобразует его в значение типа Boolean. Очевидно если строка является «true», метод AsBool преобразует это значение true. Если значение строки используется другой AsBool возвращает значение false.

> [!TIP] 
> 
> **Типы данных и методов As()**
> 
> Мы только вышесказанное, при создании переменной, используйте ключевое слово var. Это не весь материал, хотя. Чтобы управлять значениями — для добавления числа, или объединения строк, или сравнить даты и проверки на true или false — C# должен работать с внутреннего представления соответствующие значения. C# можно *обычно* выяснить это представление, которое должно быть (то есть, что *тип* данные) зависимости от выполняемых задач со значениями. Сейчас или позже однако его сделать это невозможно. В противном случае необходимо оказать помощь, явно указав как C# должно представлять данные. Метод AsBool делает это, он сообщает C#, строковое значение «true» или «false» должны рассматриваться как значение типа Boolean. Существуют аналогичные методы для представления строки в виде других типов, а также как AsInt (обрабатывать как целое число), AsDateTime (различать даты и времени), AsFloat (обрабатывать как число с плавающей запятой) и т. д. Если при использовании их в качестве методов (), C# не может представлять строковое значение, по запросу, вы увидите ошибку.


В разметке страницы, удалите или закомментируйте этот элемент (здесь он показан закомментированным):

[!code-html[Main](intro-to-web-pages-programming/samples/sample12.html)]

Справа, где удален или закомментирован текст, добавьте следующий код:

[!code-cshtml[Main](intro-to-web-pages-programming/samples/sample13.cshtml)]

Если тест указано, если значение равно true, переменная showMessage отрисовки &lt;p&gt; элемент со значением переменной сообщения.

### <a name="summary-of-your-conditional-logic"></a>Сводка условной логики

В случае, если вы не знаете полностью просто сделанное, здесь приведен краткий обзор.

- Сообщение переменной присваивается значение по умолчанию строка («это в первый раз...»).
- Если запрос страницы является результатом отправки (post), значение сообщения меняется на «теперь отправки...»
- Переменной showMessage присваивается значение false.
- Если строка запроса содержит? Показать = true, значение переменной showMessage задано значение true.
- В разметке, если значение равно true, showMessage &lt;p&gt; элемент подготавливается к просмотру, показывающий значение сообщения. (Если showMessage имеет значение false, ничего не отображается на этом этапе в разметке.)
- В разметке, если запрос post &lt;p&gt; элемент подготавливается к просмотру, отображаются дата и время.

Запустите страницу. Отсутствуют сообщения, так как showMessage имеет значение false, поэтому в разметке if(showMessage) тест возвращает значение false.

Нажмите кнопку **Отправить**. Вы видите, что дата и время, но по-прежнему не сообщение об ошибке.

В браузере, перейдите в поле URL-адрес и добавьте следующее в конец URL-адрес:? Показать = true, и нажмите клавишу ВВОД.

![«Тестирование Razor 2"страницу в браузере, отображающий строку запроса](intro-to-web-pages-programming/_static/image5.png)

Снова откроется страница. (Поскольку вы изменили URL-адрес, это нового запроса, а не отправки). Нажмите кнопку **отправить** еще раз. Появляется сообщение опять же, как дата и время.

![Страница «тестирование Razor 2"после отправки при строка запроса](intro-to-web-pages-programming/_static/image6.png)

В URL-адрес, измените? Показать = true в? Показать = false, а затем нажмите клавишу ВВОД. Отправьте страницу еще раз. Данная страница является к как была начата работа — не сообщение об ошибке.

Как отмечалось ранее, логика этого примера находится несколько надуманный. Однако, если планируется поставляются в много страниц, и может занять один или несколько форм, вы уже видели здесь.

## <a name="installing-a-helper-displaying-a-gravatar-image"></a>Установка вспомогательного класса (отображение изображений глобально распознаваемые)

Некоторые задачи, которые пользователи часто необходимо сделать на веб-страницах требуют большого объема кода или дополнительных знаний. Примеры: отображение диаграммы для данных; Размещение Facebook «Как» на странице; При отправке сообщения из веб-сайта; Обрезание или изменение размеров изображений; для веб-узла с помощью PayPal. Чтобы облегчить выполните этих видов веб-страниц ASP.NET позволяет использовать *вспомогательные методы*. Вспомогательные методы являются компонентами установки для сайта и позволяют выполнять типовые задачи с помощью всего нескольких строк кода Razor.

Веб-страницы ASP.NET имеет несколько вспомогательных методов, встроенных в. Тем не менее многие вспомогательные методы доступны в пакетах (надстройки), которые предоставляются с помощью диспетчера пакетов NuGet. NuGet позволяет выбрать пакет установки, а затем он берет на себя все сведения об установке.

В этой части учебника вы установите вспомогательный класс, который дает возможность отображать изображения глобально распознаваемые («глобально распознаваемым аватара»). Мы рассмотрим две вещи. Он, как найти и установить модуль поддержки. Вы также узнаете, как модуль поддержки позволяет легко выполнить действие, в противном случае потребуется сделать с помощью большого объема кода, необходимо написать самостоятельно.

Вы можете зарегистрировать свои собственные глобально распознаваемые на веб-сайте глобально распознаваемые в [ http://www.gravatar.com/ ](http://www.gravatar.com/), но не важно создать глобально распознаваемые учетную запись для выполнения этой части учебника.

В WebMatrix, щелкните **NuGet** кнопки.

![Диалоговое окно галереи NuGet в WebMatrix](intro-to-web-pages-programming/_static/image7.png)

При этом будет запущен диспетчер пакетов NuGet и отображаются доступные пакеты. (Не все пакеты, вспомогательные объекты; некоторые добавить функциональные возможности для WebMatrix сам, некоторые дополнительные шаблоны и т. д.) Может появиться сообщение об ошибке о несовместимости версий. Можно игнорировать это сообщение об ошибке, щелкнув **ОК** и продолжении работы с учебником.

![Диалоговое окно галереи NuGet в WebMatrix](intro-to-web-pages-programming/_static/image8.png)

В поле поиска введите «вспомогательных методов asp.net». NuGet отображаются пакеты, соответствующие условиям поиска.

![Галереи NuGet в WebMatrix, показывающая пакетов](intro-to-web-pages-programming/_static/image9.png)

Библиотека вспомогательных методов ASP.NET Web содержит код для упрощения многие часто встречающиеся задачи, включая использование глобально распознаваемые изображений. Выберите **библиотека вспомогательных методов ASP.NET Web** пакета, а затем нажмите кнопку **установить** запустить программу установки. Выберите **Да** при появлении запроса, если вы хотите установить пакет и примите условия, чтобы завершить установку.

Вот и все. NuGet загружает и устанавливает все компоненты, включая дополнительные компоненты, которые могут быть необходимы (*зависимости*).

Если по некоторым причинам необходимо удалить вспомогательный класс, процесс очень похож. Нажмите кнопку **NuGet** , выберите элемент **установленные** вкладку и выберите пакет, который требуется удалить.

## <a name="using-a-helper-in-a-page"></a>Использование вспомогательного метода на странице

Теперь воспользуйтесь помощник, который был только что установлен. Процесс добавления вспомогательного класса для страницы похоже на большинстве вспомогательных методов.

В WebMatrix, создайте страницу и назовите его *GravatarTest.cshml*. (Вы создаете специальный страницы для тестирования модуля поддержки, но можно использовать вспомогательные методы для любой страницы веб-узла.)

Внутри &lt;текст&gt; элемента, добавьте &lt;div&gt; элемента. Внутри &lt;div&gt; элемент, введите следующее:

@Gravatar.

Символ @ является тот же символ, вы уже использовали для пометки кода Razor. **Глобально распознаваемые** вспомогательный объект, которым вы работаете.

Сразу после ввода точки (.), WebMatrix отображает список *методы* (функций), вспомогательные глобально распознаваемые делает доступными:

![Глобально распознаваемые поддержки IntelliSense раскрывающегося списка](intro-to-web-pages-programming/_static/image10.png)

Эта функция называется *IntelliSense*. Это помогает при кодировании, предоставляя соответствующие контексту варианты. IntelliSense работает с HTML, CSS, код ASP.NET, JavaScript и других языков, поддерживаемых в WebMatrix. Это еще одна функция, для упрощения разработки веб-страниц в WebMatrix.

Нажать G на клавиатуре, а также см. в том, что IntelliSense находит метод GetHtml. Нажмите клавишу Tab. IntelliSense вставляет выбранный метод (GetHtml). Введите открывающую скобку и обратите внимание, что закрывающая круглая скобка добавляется автоматически. Введите адрес электронной почты в кавычки, между двумя скобками. При наличии учетной записи глобально распознаваемые изображение профиля будут возвращены. Если у вас учетной записи глобально распознаваемые, возвращается изображение по умолчанию. Когда закончите, строка выглядит следующим образом:

[!code-css[Main](intro-to-web-pages-programming/samples/sample14.css)]

Теперь можно просмотрите страницу в браузере. Изображения или изображения по умолчанию отображается, в зависимости от наличия у учетной записи глобально распознаваемые.

![Глобально распознаваемые](intro-to-web-pages-programming/_static/image11.png) ![изображение по умолчанию](intro-to-web-pages-programming/_static/image12.png)

Чтобы получить представление о том, что делает вспомогательное приложение для вас, просмотреть источник страницы в браузере. Вместе с HTML, заданные на странице см, который содержит идентификатор элемента изображения. Это вспомогательный объект отображаются на странице в том месте, где имеется код @Gravatar.GetHtml. Вспомогательный объект занял сведения предоставляются и созданный код, который обращается напрямую к глобально распознаваемые для получения нужного образа для указанной учетной записи.

Метод GetHtml также позволяет настраивать образ, указав другие параметры. В следующем коде показано, как запросить изображения имеет ширину и высоту 40 пикселей и применяет заданные по умолчанию образ с именем **wavatar** Если указанная учетная запись не существует.

[!code-javascript[Main](intro-to-web-pages-programming/samples/sample15.js)]

Этот код выводит нечто похожее на следующий результат (изображение по умолчанию случайным образом будет другим).

![](intro-to-web-pages-programming/_static/image13.png)

## <a name="coming-up-next"></a>В ближайшее время

Чтобы сохранить это учебник короткое, нам пришлось сосредоточиться на только с основными сведениями. Конечно, является *много* дополнительные Razor и C#. Вы узнаете, как вы см. этими руководствами. Если вы заинтересованы в дополнительной информацией о элементами программирования C# и Razor прямо сейчас, можно прочитать более глубокое введение здесь: [введение в ASP.NET веб-программирование с использованием синтаксиса Razor](https://go.microsoft.com/fwlink/?LinkID=202890).

Следующее руководство содержит описание работы с базой данных. В этом учебнике вы начнете создание примера приложения, который позволяет вывести избранные фильмов.

## <a name="complete-listing-for-testrazor-page"></a>Полный пример для TestRazor страницы

[!code-cshtml[Main](intro-to-web-pages-programming/samples/sample16.cshtml)]

## <a name="complete-listing-for-testrazorpart2-page"></a>Полный пример для TestRazorPart2 страницы

[!code-cshtml[Main](intro-to-web-pages-programming/samples/sample17.cshtml)]

## <a name="complete-listing-for-gravatartest-page"></a>Полный пример для GravatarTest страницы

[!code-cshtml[Main](intro-to-web-pages-programming/samples/sample18.cshtml)]

## <a name="additional-resources"></a>Дополнительные ресурсы

- [Введение в программирование веб-ASP.NET с использованием синтаксиса Razor](https://go.microsoft.com/fwlink/?LinkID=202890)
- [Вспомогательный модуль Twitter](../../ui-layouts-and-themes/twitter-helper.md)

> [!div class="step-by-step"]
> [Назад](getting-started.md)
> [Вперед](displaying-data.md)
