---
title: Построение гибких служб готов для облака. Принять временные сбои в облаке
description: Модернизировать существующие приложения .NET с контейнерами Windows и облако Azure | Построение гибких служб готов для облака. Принять временные сбои в облаке
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: 1df21d0f647b96c315686921276be3526f66bbc8
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud"></a>Построение гибких служб готов для облака: принятию временные сбои в облаке

Устойчивость — это возможность восстановления после сбоев и продолжение работы. Устойчивость не о как избежать ошибок, но принимает тот факт, что происходит сбой и затем реакции на них в, позволяющих избежать простою или потере данных. Цель устойчивости — вернуть приложение в полностью функционирующее состояние после сбоя.

Приложение будет готово для облака, если по крайней мере, он реализует модель на основе программного обеспечения устойчивости, а не модель на основе оборудования. Облачные приложения должен учесть частичные сбои, которые наверняка возникнет. Разработка или частично оптимизации приложения для обеспечения устойчивости с ожидаемой частичные сбои. Его необходимо предусмотреть справляться с частичные сбои, как сбои в работе временного сетевого и узлы или виртуальные машины, аварийное завершение работы в облаке. Даже контейнеры перемещается на другой узел в кластере orchestrator может привести к временные короткий неполадки в приложении.

## <a name="handling-partial-failure"></a>Обработка частичного сбоя

В приложении облачной нет штат постоянно риск частичных сбоев. Для экземпляра экземпляр одного веб-сайта или контейнер может произойти сбой, или он может быть недоступен или не отвечает в течение некоторого времени. Или одной виртуальной Машины или сервере может завершиться со сбоем.

Поскольку клиенты и службы являются отдельными процессами, службы могут не иметь возможность своевременно ответить на запрос клиента. Служба может быть перегружена и медленно реагировать на запросы, или она может быть недоступна в течение некоторого времени из-за сетевых проблем.

Например рассмотрим монолитные приложения .NET, который обращается к базе данных в базе данных SQL Azure. Если база данных Azure SQL или любой другой службы сторонних разработчиков не отвечает в течение кратких времени (базы данных Azure SQL может быть перемещена на другой узел или сервер, а не отвечать в течение нескольких секунд), когда пользователь пытается выполнить какие-либо действия, приложение может завершиться со сбоем и Показать w исключение одновременно.

Похожее может произойти в приложении, которое использует службы HTTP. В сети или самой службы могут оказаться недоступными в облаке short, временного сбоя.

Надежное приложение, как показано на рисунке 4 – 9 должны реализовывать такие методы, как «повторных попыток с экспоненциально растущим» для предоставления приложению возможность обработки временных сбоев в ресурсах. «Размыкатели» также следует использовать в приложениях. Размыкатель цепи прекращает попытки доступа к ресурсу, если это длительный сбой приложения. Используя Размыкатель цепи, приложение позволяет избежать подстегивающих мысль отказ в обслуживании на самого себя.

![Частичные сбои, обрабатываемых повторных попыток с экспоненциально растущим](./media/image9.png)

> **На рисунке 4 – 9.** Частичные сбои, обрабатываемых повторных попыток с экспоненциально растущим

Эти методы можно использовать в HTTP-ресурсов и ресурсов баз данных. В на рисунке 4 – 9, приложение основано на 3-уровневой архитектуре, поэтому необходимо, чтобы эти методы на уровне службы (HTTP) и на уровне данных (TCP). Монолитные приложения, использующего только одно приложение для уровня в дополнение к базе данных (без дополнительных служб или микрослужбами) обработка временных ошибок подключения на уровне базы данных будет достаточно. В этом случае требуется только конкретной конфигурации подключения к базе данных.

При реализации гибкой связи, доступ к базе данных, в зависимости от версии .NET с помощью, может быть простым (например, [Entity Framework 6 или более поздней версии](https://msdn.microsoft.com/library/dn456835(v=vs.113).aspx), это лишь Настройка подключение базы данных). Или, может потребоваться использовать дополнительные библиотеки, такие как [временных Fault Handling Application Block](https://msdn.microsoft.com/library/hh680934(v=pandp.50).aspx) (для более ранних версиях .NET), или даже реализуют собственные библиотеки.

При реализации попыток HTTP и выключатели, для .NET рекомендуется использовать [Polly](https://github.com/App-vNext/Polly) библиотеки, который нацелен на .NET Framework 4.0, .NET Framework 4.5 и .NET Standard 1.1, которая включает поддержку .NET Core.

Чтобы узнать, как для реализации стратегии для обработки частичные сбои в облаке, см. следующие ссылки.

### <a name="additional-resources"></a>Дополнительные ресурсы

-   **Реализация гибкой связи для обработки частичный сбой**

    [https://docs.microsoft.com/dotnet/standard/microservices-architecture/implement-resilient-applications/partial-failure-strategies](../../microservices-architecture/implement-resilient-applications/partial-failure-strategies.md)

-   **Entity Framework подключения устойчивости и логика повторных попыток (версия 6 и более поздние версии)**

    [https://msdn.microsoft.com/library/dn456835(v=vs.113).aspx](https://msdn.microsoft.com/library/dn456835(v=vs.113).aspx)

-   **Блок приложения обработки временных сбоев**

-   [https://msdn.microsoft.com/library/hh680934(v=pandp.50).aspx](https://msdn.microsoft.com/library/hh680934(v=pandp.50).aspx)

-   **Библиотека Polly для гибкой взаимодействие по протоколу HTTP**

    https://github.com/App-vNext/Polly

>[!div class="step-by-step"]
[Назад](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Вперед](modernize-your-apps-with-monitoring-and-telemetry.md)