---
uid: web-forms/overview/ajax-control-toolkit/animation/executing-animations-using-client-side-code-vb
title: "Выполнение анимации с помощью кода на стороне клиента (Visual Basic) | Документы Microsoft"
author: wenz
description: "Элемент управления анимации в наборе элементов управления ASP.NET AJAX не только элемент управления, но всю платформу, позволяющую Добавление анимации в элемент управления. Выполнение анимации..."
ms.author: aspnetcontent
manager: wpickett
ms.date: 06/02/2008
ms.topic: article
ms.assetid: f7073f50-d765-456d-9957-926ce60f35f6
ms.technology: dotnet-webforms
ms.prod: .net-framework
msc.legacyurl: /web-forms/overview/ajax-control-toolkit/animation/executing-animations-using-client-side-code-vb
msc.type: authoredcontent
ms.openlocfilehash: c97ce87addd566ed1ba63ccdb81206c6449f49a2
ms.sourcegitcommit: 9a9483aceb34591c97451997036a9120c3fe2baf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/10/2017
---
<a name="executing-animations-using-client-side-code-vb"></a><span data-ttu-id="66027-104">Выполнение анимации с помощью кода на стороне клиента (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="66027-104">Executing Animations Using Client-Side Code (VB)</span></span>
====================
<span data-ttu-id="66027-105">по [Кристиан Wenz](https://github.com/wenz)</span><span class="sxs-lookup"><span data-stu-id="66027-105">by [Christian Wenz](https://github.com/wenz)</span></span>

<span data-ttu-id="66027-106">[Загрузить код](http://download.microsoft.com/download/f/9/a/f9a26acd-8df4-4484-8a18-199e4598f411/Animation10.vb.zip) или [скачать PDF](http://download.microsoft.com/download/6/7/1/6718d452-ff89-4d3f-a90e-c74ec2d636a3/animation10VB.pdf)</span><span class="sxs-lookup"><span data-stu-id="66027-106">[Download Code](http://download.microsoft.com/download/f/9/a/f9a26acd-8df4-4484-8a18-199e4598f411/Animation10.vb.zip) or [Download PDF](http://download.microsoft.com/download/6/7/1/6718d452-ff89-4d3f-a90e-c74ec2d636a3/animation10VB.pdf)</span></span>

> <span data-ttu-id="66027-107">Элемент управления анимации в наборе элементов управления ASP.NET AJAX не только элемент управления, но всю платформу, позволяющую Добавление анимации в элемент управления.</span><span class="sxs-lookup"><span data-stu-id="66027-107">The Animation control in the ASP.NET AJAX Control Toolkit is not just a control but a whole framework to add animations to a control.</span></span> <span data-ttu-id="66027-108">Выполнения анимации может также запускаться с помощью настраиваемый код JavaScript на стороне клиента.</span><span class="sxs-lookup"><span data-stu-id="66027-108">The animation execution may also be triggered using custom client-side JavaScript code.</span></span>


## <a name="overview"></a><span data-ttu-id="66027-109">Обзор</span><span class="sxs-lookup"><span data-stu-id="66027-109">Overview</span></span>

<span data-ttu-id="66027-110">Элемент управления анимации в наборе элементов управления ASP.NET AJAX не только элемент управления, но всю платформу, позволяющую Добавление анимации в элемент управления.</span><span class="sxs-lookup"><span data-stu-id="66027-110">The Animation control in the ASP.NET AJAX Control Toolkit is not just a control but a whole framework to add animations to a control.</span></span> <span data-ttu-id="66027-111">Выполнения анимации может также запускаться с помощью настраиваемый код JavaScript на стороне клиента.</span><span class="sxs-lookup"><span data-stu-id="66027-111">The animation execution may also be triggered using custom client-side JavaScript code.</span></span>

## <a name="steps"></a><span data-ttu-id="66027-112">Шаги</span><span class="sxs-lookup"><span data-stu-id="66027-112">Steps</span></span>

<span data-ttu-id="66027-113">Во-первых, включают `ScriptManager` страницы; затем библиотека ASP.NET AJAX загружена, что позволяет использовать набор элементов управления:</span><span class="sxs-lookup"><span data-stu-id="66027-113">First of all, include the `ScriptManager` in the page; then, the ASP.NET AJAX library is loaded, making it possible to use the Control Toolkit:</span></span>

[!code-aspx[Main](executing-animations-using-client-side-code-vb/samples/sample1.aspx)]

<span data-ttu-id="66027-114">Анимация применяется панель текста, который выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="66027-114">The animation will be applied to a panel of text which looks like this:</span></span>

[!code-aspx[Main](executing-animations-using-client-side-code-vb/samples/sample2.aspx)]

<span data-ttu-id="66027-115">В связанный класс CSS для панели определяются цвет фона для работы с низким приоритетом, а также задать фиксированную ширину панели:</span><span class="sxs-lookup"><span data-stu-id="66027-115">In the associated CSS class for the panel, define a nice background color and also set a fixed width for the panel:</span></span>

[!code-css[Main](executing-animations-using-client-side-code-vb/samples/sample3.css)]

<span data-ttu-id="66027-116">Затем добавьте `AnimationExtender` страницу, предоставляя `ID`, `TargetControlID` атрибута и обязательным `runat="server"`:</span><span class="sxs-lookup"><span data-stu-id="66027-116">Then, add the `AnimationExtender` to the page, providing an `ID`, the `TargetControlID` attribute and the obligatory `runat="server"`:</span></span>

[!code-aspx[Main](executing-animations-using-client-side-code-vb/samples/sample4.aspx)]

<span data-ttu-id="66027-117">В пределах `<Animations>` узла, используйте `<OnClick>` однократного запуска анимации пользователь нажимает кнопку на панели.</span><span class="sxs-lookup"><span data-stu-id="66027-117">Within the `<Animations>` node, use `<OnClick>` to run the animations once the user clicks on the panel.</span></span> <span data-ttu-id="66027-118">Добавьте две анимации для выполнения parallelly:</span><span class="sxs-lookup"><span data-stu-id="66027-118">Add two animations to be executed parallelly:</span></span>

[!code-xml[Main](executing-animations-using-client-side-code-vb/samples/sample5.xml)]

<span data-ttu-id="66027-119">Для примера анимации (и другие анимации, созданные с помощью набора средств управления) выполняется с помощью кода JavaScript, когда страница выполняется.</span><span class="sxs-lookup"><span data-stu-id="66027-119">For the sake of demonstration, this animation (and any other animation created using the Control Toolkit) is executed using JavaScript code, once the page runs.</span></span> <span data-ttu-id="66027-120">Во-первых, мы необходим доступ к `AnimationExtender` элемента управления.</span><span class="sxs-lookup"><span data-stu-id="66027-120">First of all we need access to the `AnimationExtender` control.</span></span> <span data-ttu-id="66027-121">Библиотека ASP.NET AJAX предоставляет `$find()` функции для выполнения этой задачи:</span><span class="sxs-lookup"><span data-stu-id="66027-121">The ASP.NET AJAX library provides the `$find()` function for this task:</span></span>

[!code-csharp[Main](executing-animations-using-client-side-code-vb/samples/sample6.cs)]

<span data-ttu-id="66027-122">`AnimationExtender` Элемент управления предоставляет широкие возможности API, включая методы с именами, идентичными обработчикам событий, используемых в XML-разметку: `OnClick()`, `OnLoad()`, и т. д.</span><span class="sxs-lookup"><span data-stu-id="66027-122">The `AnimationExtender` control exposes a rich API, including methods with names identical to the event handlers used in the XML markup: `OnClick()`, `OnLoad()`, and so on.</span></span> <span data-ttu-id="66027-123">Например, вызов `OnClick()` метод выполняется анимация в течение `<OnClick>` элемент `AnimationExtender` управления:</span><span class="sxs-lookup"><span data-stu-id="66027-123">For instance, a call of the `OnClick()` method executes the animation within the `<OnClick>` element of the `AnimationExtender` control:</span></span>

[!code-javascript[Main](executing-animations-using-client-side-code-vb/samples/sample7.js)]

<span data-ttu-id="66027-124">Ниже приведен полный код JavaScript клиентского имитацией нажмите на панели после полной загрузки страницы Обратите внимание, что `pageLoad()` вызываемая ASP.NET AJAX один раз страницы используется имя функции и все включены были библиотек JavaScript загрузить.</span><span class="sxs-lookup"><span data-stu-id="66027-124">Here is the complete client-side JavaScript code that emulates the click on the panel once the page has been fully loaded note that the `pageLoad()` function name is used which is called by ASP.NET AJAX once the page and all included JavaScript libraries have been loaded.</span></span>

[!code-html[Main](executing-animations-using-client-side-code-vb/samples/sample8.html)]


<span data-ttu-id="66027-125">[![Анимация выполняется немедленно, без щелчка кнопкой мыши](executing-animations-using-client-side-code-vb/_static/image2.png)](executing-animations-using-client-side-code-vb/_static/image1.png)</span><span class="sxs-lookup"><span data-stu-id="66027-125">[![The animation runs immediately, without a mouse click](executing-animations-using-client-side-code-vb/_static/image2.png)](executing-animations-using-client-side-code-vb/_static/image1.png)</span></span>

<span data-ttu-id="66027-126">Анимация выполняется немедленно, без щелчок мыши ([Просмотр полноразмерное изображение](executing-animations-using-client-side-code-vb/_static/image3.png))</span><span class="sxs-lookup"><span data-stu-id="66027-126">The animation runs immediately, without a mouse click ([Click to view full-size image](executing-animations-using-client-side-code-vb/_static/image3.png))</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="66027-127">[Назад](modifying-animations-from-the-server-side-vb.md)
[Вперед](changing-an-animation-using-client-side-code-vb.md)</span><span class="sxs-lookup"><span data-stu-id="66027-127">[Previous](modifying-animations-from-the-server-side-vb.md)
[Next](changing-an-animation-using-client-side-code-vb.md)</span></span>