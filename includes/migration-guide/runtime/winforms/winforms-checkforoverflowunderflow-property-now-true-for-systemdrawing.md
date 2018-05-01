### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a><span data-ttu-id="90449-101">Свойство CheckForOverflowUnderflow WinForm теперь имеет значение true для System.Drawing</span><span class="sxs-lookup"><span data-stu-id="90449-101">WinForm's CheckForOverflowUnderflow property is now true for System.Drawing</span></span>

|   |   |
|---|---|
|<span data-ttu-id="90449-102">Подробные сведения</span><span class="sxs-lookup"><span data-stu-id="90449-102">Details</span></span>|<span data-ttu-id="90449-103">Свойство CheckForOverflowUnderflow для сборки System.Drawing.dll имеет значение true.</span><span class="sxs-lookup"><span data-stu-id="90449-103">The CheckForOverflowUnderflow property for the System.Drawing.dll assembly is set to true.</span></span>|
|<span data-ttu-id="90449-104">Предложение</span><span class="sxs-lookup"><span data-stu-id="90449-104">Suggestion</span></span>|<span data-ttu-id="90449-105">Раньше при переполнениях результат усекался без уведомления.</span><span class="sxs-lookup"><span data-stu-id="90449-105">Previously when overflows occurred, the result would be silently truncated.</span></span> <span data-ttu-id="90449-106">Теперь создается исключение <xref:System.OverflowException?displayProperty=name>,</span><span class="sxs-lookup"><span data-stu-id="90449-106">Now an <xref:System.OverflowException?displayProperty=name> exception is thrown.</span></span>|
|<span data-ttu-id="90449-107">Область</span><span class="sxs-lookup"><span data-stu-id="90449-107">Scope</span></span>|<span data-ttu-id="90449-108">Пограничный случай</span><span class="sxs-lookup"><span data-stu-id="90449-108">Edge</span></span>|
|<span data-ttu-id="90449-109">Версия</span><span class="sxs-lookup"><span data-stu-id="90449-109">Version</span></span>|<span data-ttu-id="90449-110">4.5</span><span class="sxs-lookup"><span data-stu-id="90449-110">4.5</span></span>|
|<span data-ttu-id="90449-111">Тип</span><span class="sxs-lookup"><span data-stu-id="90449-111">Type</span></span>|<span data-ttu-id="90449-112">Среда выполнения</span><span class="sxs-lookup"><span data-stu-id="90449-112">Runtime</span></span>|
