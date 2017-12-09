---
title: "Контейнеры docker, изображения и реестров"
description: "Жизненный цикл приложений контейнерного Docker с помощью платформы Майкрософт и средств"
keywords: "Docker, микрослужбы, ASP.NET, контейнер"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: b115b25d8ae335aafbe41bac0d694170be7e3c49
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="0123e-104">Контейнеры docker, изображения и реестров</span><span class="sxs-lookup"><span data-stu-id="0123e-104">Docker containers, images, and registries</span></span>

<span data-ttu-id="0123e-105">При использовании Docker, вы создаете приложения или службы и пакета его и его зависимости в образ контейнера.</span><span class="sxs-lookup"><span data-stu-id="0123e-105">When using Docker, you create an app or service and package it and its dependencies into a container image.</span></span> <span data-ttu-id="0123e-106">Образ — это статическое представление приложения или службы и его конфигурации и зависимостей.</span><span class="sxs-lookup"><span data-stu-id="0123e-106">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="0123e-107">Для выполнения приложения или службы, чтобы создать контейнер, в котором будут выполняться на узле Docker создается образ приложения.</span><span class="sxs-lookup"><span data-stu-id="0123e-107">To run the app or service, the app's image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="0123e-108">Контейнеров, изначально проверены в среде разработки или ПК.</span><span class="sxs-lookup"><span data-stu-id="0123e-108">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="0123e-109">Хранятся в реестре, который выступает в качестве библиотеки образов изображения.</span><span class="sxs-lookup"><span data-stu-id="0123e-109">You store images in a registry, which acts as a library of images.</span></span> <span data-ttu-id="0123e-110">При развертывании в рабочей среде orchestrators необходимо реестра.</span><span class="sxs-lookup"><span data-stu-id="0123e-110">You need a registry when deploying to production orchestrators.</span></span> <span data-ttu-id="0123e-111">Docker обслуживает открытого реестра через [Docker Hub](https://hub.docker.com/); другие поставщики предлагают реестров для различных коллекций изображений.</span><span class="sxs-lookup"><span data-stu-id="0123e-111">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images.</span></span> <span data-ttu-id="0123e-112">Кроме того, предприятия могут иметь частного реестра локальными для своих собственных образов Docker.</span><span class="sxs-lookup"><span data-stu-id="0123e-112">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="0123e-113">На рис. 1-4 показано, как изображения и реестров в Docker связаны с другими компонентами.</span><span class="sxs-lookup"><span data-stu-id="0123e-113">Figure 1-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="0123e-114">Он также содержит несколько предложений реестра от поставщиков.</span><span class="sxs-lookup"><span data-stu-id="0123e-114">It also shows the multiple registry offerings from vendors.</span></span>

![](./media/image4.png)

<span data-ttu-id="0123e-115">Рисунок 1-4: классификация Docker термины и основные понятия</span><span class="sxs-lookup"><span data-stu-id="0123e-115">Figure 1-4: Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="0123e-116">Поместив изображения в реестре, можно хранить разряды статические и неизменяемый приложения, включая все их зависимости на уровне framework.</span><span class="sxs-lookup"><span data-stu-id="0123e-116">By putting images in a registry, you can store static and immutable application bits, including all of their dependencies, at a framework level.</span></span> <span data-ttu-id="0123e-117">Вы затем можно версии и развертывания образов в нескольких средах и таким образом предоставляют единицу развертывания.</span><span class="sxs-lookup"><span data-stu-id="0123e-117">You then can version and deploy images in multiple environments and thus provide a consistent deployment unit.</span></span>

<span data-ttu-id="0123e-118">Реестры частный образ размещается локально или в облаке, рекомендуется использовать в следующих ситуациях:</span><span class="sxs-lookup"><span data-stu-id="0123e-118">Private image registries, either hosted on-premises or in the cloud, are recommended for the following situations:</span></span>

-   <span data-ttu-id="0123e-119">Изображения не должен быть общим открыто из-за конфиденциальность.</span><span class="sxs-lookup"><span data-stu-id="0123e-119">Your images must not be shared publicly due to confidentiality.</span></span>

-   <span data-ttu-id="0123e-120">Требуется минимальная сетевая задержка между образов и среды выбранного развертывания.</span><span class="sxs-lookup"><span data-stu-id="0123e-120">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="0123e-121">Например если вашей рабочей среде Azure, может потребоваться хранения рисунков в реестре контейнера Azure, чтобы сетевая задержка будет минимальной.</span><span class="sxs-lookup"><span data-stu-id="0123e-121">For example, if your production environment is Azure, you probably want to store your images in Azure Container Registry so that network latency will be minimal.</span></span> <span data-ttu-id="0123e-122">Аналогичным образом Если в локальной рабочей среды может потребоваться иметь локальные доверенный реестр Docker в той же локальной сети.</span><span class="sxs-lookup"><span data-stu-id="0123e-122">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="0123e-123">[Предыдущие] docker (terminology.md) [Далее] (Docker приложения-жизненного цикла/index.md)</span><span class="sxs-lookup"><span data-stu-id="0123e-123">[Previous] (docker-terminology.md) [Next] (Docker-application-lifecycle/index.md)</span></span>