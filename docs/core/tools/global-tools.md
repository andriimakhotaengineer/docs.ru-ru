---
title: Глобальные средства .NET Core
description: Обзор глобальных средств .NET Core и доступных для них команд .NET Core CLI.
author: KathleenDollard
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 077ffd53f1ba2988c80a637aaa109a66139736b0
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34697096"
---
# <a name="net-core-global-tools-overview"></a><span data-ttu-id="3055d-103">Обзор глобальных средств .NET Core</span><span class="sxs-lookup"><span data-stu-id="3055d-103">.NET Core Global Tools overview</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

<span data-ttu-id="3055d-104">Глобальное средство .NET Core — это специальный пакет NuGet, который содержит консольное приложение.</span><span class="sxs-lookup"><span data-stu-id="3055d-104">A .NET Core Global Tool is a special NuGet package that contains a console application.</span></span> <span data-ttu-id="3055d-105">Глобальное средство можно установить на компьютере в расположении по умолчанию, которое включено в переменную среды PATH, или в другом расположении.</span><span class="sxs-lookup"><span data-stu-id="3055d-105">A Global Tool can be installed on your machine on a default location that is included in the PATH environment variable or on a custom location.</span></span>

<span data-ttu-id="3055d-106">Процесс работы с глобальным средством .NET Core включает следующие этапы:</span><span class="sxs-lookup"><span data-stu-id="3055d-106">If you want to use a .NET Core Global Tool:</span></span>

* <span data-ttu-id="3055d-107">поиск информации о средстве (обычно на веб-сайте или странице GitHub);</span><span class="sxs-lookup"><span data-stu-id="3055d-107">Find information about the tool (usually a website or GitHub page).</span></span>
* <span data-ttu-id="3055d-108">проверку автора и статистики в корневой папке веб-канала (обычно NuGet.org);</span><span class="sxs-lookup"><span data-stu-id="3055d-108">Check the author and statistics in the home for the feed (usually NuGet.org).</span></span>
* <span data-ttu-id="3055d-109">установку средства;</span><span class="sxs-lookup"><span data-stu-id="3055d-109">Install the tool.</span></span>
* <span data-ttu-id="3055d-110">вызов средства;</span><span class="sxs-lookup"><span data-stu-id="3055d-110">Call the tool.</span></span>
* <span data-ttu-id="3055d-111">обновление средства;</span><span class="sxs-lookup"><span data-stu-id="3055d-111">Update the tool.</span></span>
* <span data-ttu-id="3055d-112">удаление средства.</span><span class="sxs-lookup"><span data-stu-id="3055d-112">Uninstall the tool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3055d-113">Глобальные средства .NET Core устанавливаются по выбранному вами пути и выполняются в режиме полного доверия.</span><span class="sxs-lookup"><span data-stu-id="3055d-113">.NET Core Global Tools appear on your path and run in full trust.</span></span> <span data-ttu-id="3055d-114">Не устанавливайте глобальные средства .NET Core, если вы не доверяете автору.</span><span class="sxs-lookup"><span data-stu-id="3055d-114">Do not install .NET Core Global Tools unless you trust the author.</span></span>

## <a name="find-a-net-core-global-tool"></a><span data-ttu-id="3055d-115">Как найти глобальное средство .NET Core</span><span class="sxs-lookup"><span data-stu-id="3055d-115">Find a .NET Core Global Tool</span></span>

<span data-ttu-id="3055d-116">В интерфейсе командной строки (CLI) .NET Core пока нет функции поиска глобальных средств.</span><span class="sxs-lookup"><span data-stu-id="3055d-116">Currently, there isn't a Global Tool search feature in the .NET Core Command-line Interface (CLI).</span></span>

<span data-ttu-id="3055d-117">Глобальные средства .NET Core можно найти в [NuGet](https://www.nuget.org).</span><span class="sxs-lookup"><span data-stu-id="3055d-117">You can find .NET Core Global Tools on [NuGet](https://www.nuget.org).</span></span> <span data-ttu-id="3055d-118">При этом NuGet пока не позволяет выполнять поиск конкретных глобальных средств .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3055d-118">However, NuGet doesn't yet allow you to search specifically for .NET Core Global Tools.</span></span>

<span data-ttu-id="3055d-119">Вы можете найти рекомендации средств в записях блога или в репозитории GitHub [natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools).</span><span class="sxs-lookup"><span data-stu-id="3055d-119">You may also find tool recommendations in blog posts or in the [natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) GitHub repository.</span></span>

<span data-ttu-id="3055d-120">Кроме того, в репозитории GitHub [aspnet/DotNetTools](https://github.com/aspnet/DotNetTools/) вам доступен исходный код для глобальных средств, созданных командой разработчиков для ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="3055d-120">You can also see the source code for the Global Tools created by the ASP.NET team at the [aspnet/DotNetTools](https://github.com/aspnet/DotNetTools/) GitHub repository.</span></span>

## <a name="check-the-author-and-statistics"></a><span data-ttu-id="3055d-121">Проверка автора и статистики</span><span class="sxs-lookup"><span data-stu-id="3055d-121">Check the author and statistics</span></span>

<span data-ttu-id="3055d-122">Поскольку глобальные средства .NET Core выполняются в режиме полного доверия и обычно устанавливаются по заданному вами пути, они имеют большие привилегии.</span><span class="sxs-lookup"><span data-stu-id="3055d-122">Since .NET Core Global Tools run in full trust and are generally installed on your path, they can be very powerful.</span></span> <span data-ttu-id="3055d-123">Не скачивайте средства авторов, которым вы не доверяете.</span><span class="sxs-lookup"><span data-stu-id="3055d-123">Don't download tools from people you don't trust.</span></span>

<span data-ttu-id="3055d-124">Если средство размещается в NuGet, вы можете проверить автора и статистику, выполнив поиск средства.</span><span class="sxs-lookup"><span data-stu-id="3055d-124">If the tool is hosted on NuGet, you can check the author and statistics by searching for the tool.</span></span>

## <a name="install-a-global-tool"></a><span data-ttu-id="3055d-125">Установка глобального средства</span><span class="sxs-lookup"><span data-stu-id="3055d-125">Install a Global Tool</span></span>

<span data-ttu-id="3055d-126">Чтобы установить глобальное средство, используйте команду .NET Core CLI [dotnet tool install](dotnet-tool-install.md).</span><span class="sxs-lookup"><span data-stu-id="3055d-126">To install a Global Tool, you use the [dotnet tool install](dotnet-tool-install.md) .NET Core CLI command.</span></span> <span data-ttu-id="3055d-127">В примере ниже показано, как установить глобальное средство в расположении по умолчанию:</span><span class="sxs-lookup"><span data-stu-id="3055d-127">The following example shows how to install a Global Tool in the default location:</span></span>

```console
dotnet tool install -g dotnetsay
```

<span data-ttu-id="3055d-128">Если не удается установить средство, отображаются сообщения об ошибках.</span><span class="sxs-lookup"><span data-stu-id="3055d-128">If the tool can't be installed, error messages are displayed.</span></span> <span data-ttu-id="3055d-129">Убедитесь, что установлены флажки для нужных веб-каналов.</span><span class="sxs-lookup"><span data-stu-id="3055d-129">Check that the feeds you expected are being checked.</span></span>

<span data-ttu-id="3055d-130">Если вам необходимо установить предварительную или конкретную версию средства, можно указать номер версии, используя следующий формат:</span><span class="sxs-lookup"><span data-stu-id="3055d-130">If you're trying to install a pre-release version or a specific version of the tool, you can specify the version number using the following format:</span></span>

```console
dotnet tool install -g <package-name> --version <version-number>
```

<span data-ttu-id="3055d-131">Если установка выполнена успешно, отображается сообщение с командой, используемой для вызова средства, и установленной версией, аналогичное приведенному ниже:</span><span class="sxs-lookup"><span data-stu-id="3055d-131">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.0.0') was successfully installed.
```

<span data-ttu-id="3055d-132">Глобальные средства можно установить в каталоге по умолчанию или в выбранном вами расположении.</span><span class="sxs-lookup"><span data-stu-id="3055d-132">Global Tools can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="3055d-133">Каталоги по умолчанию:</span><span class="sxs-lookup"><span data-stu-id="3055d-133">The default directories are:</span></span>

| <span data-ttu-id="3055d-134">Операционная система</span><span class="sxs-lookup"><span data-stu-id="3055d-134">OS</span></span>          | <span data-ttu-id="3055d-135">Путь</span><span class="sxs-lookup"><span data-stu-id="3055d-135">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="3055d-136">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="3055d-136">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="3055d-137">Windows</span><span class="sxs-lookup"><span data-stu-id="3055d-137">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="3055d-138">Эти расположения добавляются в путь пользователя при первом запуске пакета SDK, поэтому установленные в них глобальные средства можно вызывать напрямую.</span><span class="sxs-lookup"><span data-stu-id="3055d-138">These locations are added to the user's path when the SDK is first run, so Global Tools installed there can be called directly.</span></span>

<span data-ttu-id="3055d-139">Обратите внимание, что глобальные средства входят в область конкретного пользователя, а не глобальную область компьютера.</span><span class="sxs-lookup"><span data-stu-id="3055d-139">Note that the Global Tools are user-specific, not machine global.</span></span> <span data-ttu-id="3055d-140">Таким образом, нельзя установить глобальное средство, которое будет доступно для всех пользователей компьютера.</span><span class="sxs-lookup"><span data-stu-id="3055d-140">Being user-specific means you cannot install a Global Tool that is available to all users of the machine.</span></span> <span data-ttu-id="3055d-141">Средство доступно только для тех профилей пользователей, в которых оно установлено.</span><span class="sxs-lookup"><span data-stu-id="3055d-141">The tool is only available for each user profile where the tool was installed.</span></span>

<span data-ttu-id="3055d-142">Глобальные средства также можно установить в конкретном каталоге.</span><span class="sxs-lookup"><span data-stu-id="3055d-142">Global Tools can also be installed in a specific directory.</span></span> <span data-ttu-id="3055d-143">При установке в конкретном каталоге необходимо убедиться, что команда доступна, включив этот каталог в путь, вызвав команду с указанным каталогом или вызвав средство из указанного каталога.</span><span class="sxs-lookup"><span data-stu-id="3055d-143">When installed in a specific directory, the user must ensure the command is available, by including that directory in the path, by calling the command with the directory specified, or calling the tool from within the specified directory.</span></span>
<span data-ttu-id="3055d-144">В этом случае .NET Core CLI не добавляет это расположение автоматически в переменную среды PATH.</span><span class="sxs-lookup"><span data-stu-id="3055d-144">In this case, the .NET Core CLI doesn't add this location automatically to the PATH environment variable.</span></span>

## <a name="use-the-tool"></a><span data-ttu-id="3055d-145">Работа со средством</span><span class="sxs-lookup"><span data-stu-id="3055d-145">Use the tool</span></span>

<span data-ttu-id="3055d-146">После установки средства его можно вызывать с помощью команды.</span><span class="sxs-lookup"><span data-stu-id="3055d-146">Once the tool is installed, you can call it by using its command.</span></span> <span data-ttu-id="3055d-147">Обратите внимание, что команда может отличаться от имени пакета.</span><span class="sxs-lookup"><span data-stu-id="3055d-147">Note that the command may not be the same as the package name.</span></span>

<span data-ttu-id="3055d-148">Если команда — `dotnetsay`, она вызывается с помощью:</span><span class="sxs-lookup"><span data-stu-id="3055d-148">If the command is `dotnetsay`, you call it with:</span></span>

```console
dotnetsay
```

<span data-ttu-id="3055d-149">Если автор средства предусмотрел его отображение в контексте запроса `dotnet`, оно может вызываться как `dotnet <command>`, например:</span><span class="sxs-lookup"><span data-stu-id="3055d-149">If the tool author wanted the tool to appear in the context of the `dotnet` prompt, they may have written it in a way that you call it as `dotnet <command>`, such as:</span></span>

```console
dotnet doc
```

<span data-ttu-id="3055d-150">Чтобы узнать, какие средства входят в установленный пакет глобального средства, можно перечислить установленные пакеты с помощью команды [dotnet tool list](dotnet-tool-list.md).</span><span class="sxs-lookup"><span data-stu-id="3055d-150">You can find which tools are included in an installed Global Tool package by listing the installed packages using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

<span data-ttu-id="3055d-151">Вы также можете найти инструкции по использованию на веб-сайте средства или выполнив одну из следующих команд:</span><span class="sxs-lookup"><span data-stu-id="3055d-151">You can also look for usage instructions at the tool's website or by typing one of the following commands:</span></span>

```console
<command> --help
dotnet <command> --help
```

### <a name="what-could-go-wrong"></a><span data-ttu-id="3055d-152">Какие проблемы могут возникнуть</span><span class="sxs-lookup"><span data-stu-id="3055d-152">What could go wrong</span></span>

<span data-ttu-id="3055d-153">Глобальные средства — это [приложения, зависящие от платформы](../deploying/index.md#framework-dependent-deployments-fdd), то есть от среды выполнения .NET Core, установленной на компьютере.</span><span class="sxs-lookup"><span data-stu-id="3055d-153">Global Tools are [framework-dependent applications](../deploying/index.md#framework-dependent-deployments-fdd), which means they rely on a .NET Core runtime installed on your machine.</span></span> <span data-ttu-id="3055d-154">Если ожидаемая среда выполнения не найдена, они следуют обычным правилам наката среды выполнения .NET Core:</span><span class="sxs-lookup"><span data-stu-id="3055d-154">If the expected runtime is not found, they follow normal .NET Core runtime roll-forward rules such as:</span></span>

* <span data-ttu-id="3055d-155">Накат выполняется к последнему номеру выпуска исправления указанной основной и дополнительной версии.</span><span class="sxs-lookup"><span data-stu-id="3055d-155">An application rolls forward to the highest patch release of the specified major and minor version.</span></span>
* <span data-ttu-id="3055d-156">Если соответствующая среда выполнения с соответствующим номером основной и дополнительный версии отсутствует, используется следующий последний дополнительный номер версии.</span><span class="sxs-lookup"><span data-stu-id="3055d-156">If there is no matching runtime with a matching major and minor version number, the next higher minor version is used.</span></span>
* <span data-ttu-id="3055d-157">Накат не выполняется между предварительными версиями среды выполнения или между предварительной версией и версией выпуска.</span><span class="sxs-lookup"><span data-stu-id="3055d-157">Roll forward doesn't occur between preview versions of the runtime or between preview versions and release versions.</span></span> <span data-ttu-id="3055d-158">Таким образом, глобальные средства, созданные с помощью предварительных версий, должны быть перестроены и повторно опубликованы автором, а затем переустановлены.</span><span class="sxs-lookup"><span data-stu-id="3055d-158">Thus, Global Tools created using preview versions must be rebuilt and republished by the author and reinstalled.</span></span>
* <span data-ttu-id="3055d-159">Дополнительные проблемы могут возникать с глобальными средствами, созданными в .NET Core 2.1 предварительной версии 1.</span><span class="sxs-lookup"><span data-stu-id="3055d-159">Additional issues can occur with Global Tools created in .NET Core 2.1 Preview 1.</span></span> <span data-ttu-id="3055d-160">Дополнительные сведения см. в статье, посвященной [известным проблемам .NET Core 2.1 предварительной версии 2](https://github.com/dotnet/core/blob/master/release-notes/2.1/Preview/2.1.0-preview2-known-issues.md).</span><span class="sxs-lookup"><span data-stu-id="3055d-160">For more information, see [.NET Core 2.1 Preview 2 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/2.1/Preview/2.1.0-preview2-known-issues.md).</span></span>

<span data-ttu-id="3055d-161">Если приложению не удается найти подходящую среду выполнения, оно не запускается и сообщает об ошибке.</span><span class="sxs-lookup"><span data-stu-id="3055d-161">If an application cannot find an appropriate runtime, it fails to run and reports an error.</span></span>

<span data-ttu-id="3055d-162">Может возникать еще одна проблема, которая связана с тем, что глобальное средство, которое было создано в более ранней предварительной версии, может не поддерживать текущие установленные среды выполнения .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3055d-162">Another issue that might happen is that a Global Tool that was created during an earlier preview may not run with your currently installed .NET Core runtimes.</span></span> <span data-ttu-id="3055d-163">Просмотреть, какие среды выполнения установлены на компьютере, можно с помощью следующей команды:</span><span class="sxs-lookup"><span data-stu-id="3055d-163">You can see which runtimes are installed on your machine using the following command:</span></span>

```console
dotnet --list-runtimes
```

<span data-ttu-id="3055d-164">Обратитесь к автору глобального средства и попросите его перекомпилировать и повторно опубликовать пакет средства в NuGet с обновленным номером версии.</span><span class="sxs-lookup"><span data-stu-id="3055d-164">Contact the author of the Global Tool and see if they can recompile and republish their tool package to NuGet with an updated version number.</span></span> <span data-ttu-id="3055d-165">После обновления пакета в NuGet вы сможете обновить установленную копию.</span><span class="sxs-lookup"><span data-stu-id="3055d-165">Once they have updated the package on NuGet, you can update your copy.</span></span>

<span data-ttu-id="3055d-166">Интерфейс .NET Core CLI пытается добавить расположения по умолчанию в переменную среды PATH при первом использовании.</span><span class="sxs-lookup"><span data-stu-id="3055d-166">The .NET Core CLI tries to add the default locations to the PATH environment variable on its first usage.</span></span> <span data-ttu-id="3055d-167">Однако есть ситуации, когда расположение не удается добавить в переменную PATH автоматически, например:</span><span class="sxs-lookup"><span data-stu-id="3055d-167">However, there are a couple of scenarios where the location might not be added to PATH automatically, such as:</span></span>

* <span data-ttu-id="3055d-168">вы задали переменную среды `DOTNET_SKIP_FIRST_TIME_EXPERIENCE`;</span><span class="sxs-lookup"><span data-stu-id="3055d-168">If you've set the `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` environment variable.</span></span>
* <span data-ttu-id="3055d-169">в macOS пакет SDK для .NET Core установлен с помощью *TAR.GZ*-, а не *PKG*-файлов;</span><span class="sxs-lookup"><span data-stu-id="3055d-169">On macOS, if you've installed the .NET Core SDK using *.tar.gz* files and not *.pkg*.</span></span>
* <span data-ttu-id="3055d-170">в Linux необходимо изменить файл среды оболочки для настройки переменной PATH.</span><span class="sxs-lookup"><span data-stu-id="3055d-170">On Linux, you need to edit the shell environment file to configure the PATH.</span></span>

## <a name="other-cli-commands"></a><span data-ttu-id="3055d-171">Другие команды интерфейса командной строки</span><span class="sxs-lookup"><span data-stu-id="3055d-171">Other CLI commands</span></span>

<span data-ttu-id="3055d-172">Пакет SDK для .NET Core содержит другие команды, которые поддерживают глобальные средства .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3055d-172">The .NET Core SDK contains other commands that support .NET Core Global Tools.</span></span> <span data-ttu-id="3055d-173">Все команды `dotnet tool` можно использовать с одним из следующих параметров:</span><span class="sxs-lookup"><span data-stu-id="3055d-173">Use any of the `dotnet tool` commands with one of the following options:</span></span>

* <span data-ttu-id="3055d-174">`--global` или `-g` указывает, что команда применяется к глобальному средству уровня пользователя;</span><span class="sxs-lookup"><span data-stu-id="3055d-174">`--global` or `-g` specifies that the command is applicable to user-wide Global Tools.</span></span>
* <span data-ttu-id="3055d-175">`--tool-path` задает пользовательское расположение для глобальных средств.</span><span class="sxs-lookup"><span data-stu-id="3055d-175">`--tool-path` specifies a custom location for Global Tools.</span></span>

<span data-ttu-id="3055d-176">Чтобы узнать, какие команды доступны для глобальных средств, выполните следующую команду:</span><span class="sxs-lookup"><span data-stu-id="3055d-176">To find out which commands are available for Global Tools:</span></span>

```console
dotnet tool --help
```

<span data-ttu-id="3055d-177">Обновление глобального средства подразумевает его удаление и установку последней стабильной версии.</span><span class="sxs-lookup"><span data-stu-id="3055d-177">Updating a Global Tool involves uninstalling and reinstalling it with the latest stable version.</span></span> <span data-ttu-id="3055d-178">Чтобы обновить глобальное средство, используйте команду [dotnet tool update](dotnet-tool-update.md):</span><span class="sxs-lookup"><span data-stu-id="3055d-178">To update a Global Tool, use the [dotnet tool update](dotnet-tool-update.md) command:</span></span>

```console
dotnet tool update -g <packagename>
```

<span data-ttu-id="3055d-179">Удалите глобальное средство с помощью команды [dotnet tool uninstall](dotnet-tool-uninstall.md):</span><span class="sxs-lookup"><span data-stu-id="3055d-179">Remove a Global Tool using the [dotnet tool uninstall](dotnet-tool-uninstall.md):</span></span>

```console
dotnet tool uninstall -g <packagename>
```

<span data-ttu-id="3055d-180">Чтобы отобразить все глобальные средства, установленные на компьютере (вместе со сведениями о версиях и командах), используйте команду [dotnet tool list](dotnet-tool-list.md):</span><span class="sxs-lookup"><span data-stu-id="3055d-180">To display all of the Global Tools currently installed on the machine, along with their version and commands, use the [dotnet tool list](dotnet-tool-list.md) command:</span></span>

```console
dotnet tool list -g
```