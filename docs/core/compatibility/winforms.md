---
title: Breaking Changes bei Windows Forms
description: Hier werden die Breaking Changes in Windows Forms für .NET Core und .NET 5 aufgelistet.
ms.date: 09/08/2020
ms.openlocfilehash: 3e7d077d07203d9c231ae4a7805e593c5432c135
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2020
ms.locfileid: "90678998"
---
# <a name="breaking-changes-in-windows-forms"></a><span data-ttu-id="8e550-103">Breaking Changes bei Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8e550-103">Breaking changes in Windows Forms</span></span>

<span data-ttu-id="8e550-104">Windows Forms-Unterstützung wurde zu .NET Core in Version 3.0 hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="8e550-104">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="8e550-105">In diesem Artikel werden Breaking Changes für Windows Forms anhand der .NET-Version aufgeführt, in der sie eingeführt wurden.</span><span class="sxs-lookup"><span data-stu-id="8e550-105">This article lists breaking changes for Windows Forms by the .NET version in which they were introduced.</span></span> <span data-ttu-id="8e550-106">Wenn Sie ein Upgrade einer Windows Forms-App von .NET Framework oder einer früheren Version von .NET Core (3.0 oder höher) durchführen, bietet Ihnen dieser Artikel Unterstützung.</span><span class="sxs-lookup"><span data-stu-id="8e550-106">If you're upgrading a Windows Forms app from .NET Framework or from a previous version of .NET Core (3.0 or later), this article applies to you.</span></span>

<span data-ttu-id="8e550-107">Auf dieser Seite sind die folgenden Breaking Changes dokumentiert:</span><span class="sxs-lookup"><span data-stu-id="8e550-107">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="8e550-108">Unterbrechende Änderung</span><span class="sxs-lookup"><span data-stu-id="8e550-108">Breaking change</span></span> | <span data-ttu-id="8e550-109">Eingeführt in Version</span><span class="sxs-lookup"><span data-stu-id="8e550-109">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="8e550-110">Das OutputType-Atttribut für WPF- und WinForms-Apps wurde auf WinExe festgelegt</span><span class="sxs-lookup"><span data-stu-id="8e550-110">OutputType set to WinExe for WPF and WinForms apps</span></span>](#outputtype-set-to-winexe-for-wpf-and-winforms-apps) | <span data-ttu-id="8e550-111">5.0</span><span class="sxs-lookup"><span data-stu-id="8e550-111">5.0</span></span> |
| [<span data-ttu-id="8e550-112">Mit DataGridView verbundene APIs lösen jetzt InvalidOperationException aus</span><span class="sxs-lookup"><span data-stu-id="8e550-112">DataGridView-related APIs now throw InvalidOperationException</span></span>](#datagridview-related-apis-now-throw-invalidoperationexception) | <span data-ttu-id="8e550-113">5.0</span><span class="sxs-lookup"><span data-stu-id="8e550-113">5.0</span></span> |
| [<span data-ttu-id="8e550-114">WinForms- und WPF-Apps verwenden Microsoft.NET.Sdk</span><span class="sxs-lookup"><span data-stu-id="8e550-114">WinForms and WPF apps use Microsoft.NET.Sdk</span></span>](#winforms-and-wpf-apps-use-microsoftnetsdk) | <span data-ttu-id="8e550-115">5.0</span><span class="sxs-lookup"><span data-stu-id="8e550-115">5.0</span></span> |
| [<span data-ttu-id="8e550-116">Statusleisten-Steuerelement wurde entfernt</span><span class="sxs-lookup"><span data-stu-id="8e550-116">Removed status bar controls</span></span>](#removed-status-bar-controls) | <span data-ttu-id="8e550-117">5.0</span><span class="sxs-lookup"><span data-stu-id="8e550-117">5.0</span></span> |
| [<span data-ttu-id="8e550-118">WinForms-Methoden lösen jetzt ArgumentException aus</span><span class="sxs-lookup"><span data-stu-id="8e550-118">WinForms methods now throw ArgumentException</span></span>](#winforms-methods-now-throw-argumentexception) | <span data-ttu-id="8e550-119">5.0</span><span class="sxs-lookup"><span data-stu-id="8e550-119">5.0</span></span> |
| [<span data-ttu-id="8e550-120">WinForms-Methoden lösen jetzt ArgumentNullException aus</span><span class="sxs-lookup"><span data-stu-id="8e550-120">WinForms methods now throw ArgumentNullException</span></span>](#winforms-methods-now-throw-argumentnullexception) | <span data-ttu-id="8e550-121">5.0</span><span class="sxs-lookup"><span data-stu-id="8e550-121">5.0</span></span> |
| [<span data-ttu-id="8e550-122">WinForms-Eigenschaften lösen nun ArgumentOutOfRangeException aus</span><span class="sxs-lookup"><span data-stu-id="8e550-122">WinForms properties now throw ArgumentOutOfRangeException</span></span>](#winforms-properties-now-throw-argumentoutofrangeexception) | <span data-ttu-id="8e550-123">5.0</span><span class="sxs-lookup"><span data-stu-id="8e550-123">5.0</span></span> |
| [<span data-ttu-id="8e550-124">Entfernte Steuerelemente</span><span class="sxs-lookup"><span data-stu-id="8e550-124">Removed controls</span></span>](#removed-controls) | <span data-ttu-id="8e550-125">3.1</span><span class="sxs-lookup"><span data-stu-id="8e550-125">3.1</span></span> |
| [<span data-ttu-id="8e550-126">CellFormatting-Ereignis wird nicht ausgelöst, wenn QuickInfo angezeigt wird</span><span class="sxs-lookup"><span data-stu-id="8e550-126">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown) | <span data-ttu-id="8e550-127">3.1</span><span class="sxs-lookup"><span data-stu-id="8e550-127">3.1</span></span> |
| [<span data-ttu-id="8e550-128">Control.DefaultFont wurde in Segoe UI 9 pt geändert</span><span class="sxs-lookup"><span data-stu-id="8e550-128">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt) | <span data-ttu-id="8e550-129">3.0</span><span class="sxs-lookup"><span data-stu-id="8e550-129">3.0</span></span> |
| [<span data-ttu-id="8e550-130">Modernisierung von FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="8e550-130">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog) | <span data-ttu-id="8e550-131">3.0</span><span class="sxs-lookup"><span data-stu-id="8e550-131">3.0</span></span> |
| [<span data-ttu-id="8e550-132">SerializableAttribute aus einigen Windows Forms-Typen entfernt</span><span class="sxs-lookup"><span data-stu-id="8e550-132">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types) | <span data-ttu-id="8e550-133">3.0</span><span class="sxs-lookup"><span data-stu-id="8e550-133">3.0</span></span> |
| [<span data-ttu-id="8e550-134">Kompatibilitätsoption AllowUpdateChildControlIndexForTabControls wird nicht unterstützt</span><span class="sxs-lookup"><span data-stu-id="8e550-134">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported) | <span data-ttu-id="8e550-135">3.0</span><span class="sxs-lookup"><span data-stu-id="8e550-135">3.0</span></span> |
| [<span data-ttu-id="8e550-136">Kompatibilitätsoption DomainUpDown.UseLegacyScrolling wird nicht unterstützt</span><span class="sxs-lookup"><span data-stu-id="8e550-136">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported) | <span data-ttu-id="8e550-137">3.0</span><span class="sxs-lookup"><span data-stu-id="8e550-137">3.0</span></span> |
| [<span data-ttu-id="8e550-138">Kompatibilitätsoption DoNotLoadLatestRichEditControl wird nicht unterstützt</span><span class="sxs-lookup"><span data-stu-id="8e550-138">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported) | <span data-ttu-id="8e550-139">3.0</span><span class="sxs-lookup"><span data-stu-id="8e550-139">3.0</span></span> |
| [<span data-ttu-id="8e550-140">Kompatibilitätsoption DoNotSupportSelectAllShortcutInMultilineTextBox wird nicht unterstützt</span><span class="sxs-lookup"><span data-stu-id="8e550-140">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported) | <span data-ttu-id="8e550-141">3.0</span><span class="sxs-lookup"><span data-stu-id="8e550-141">3.0</span></span> |
| [<span data-ttu-id="8e550-142">Kompatibilitätsoption DontSupportReentrantFilterMessage wird nicht unterstützt</span><span class="sxs-lookup"><span data-stu-id="8e550-142">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported) | <span data-ttu-id="8e550-143">3.0</span><span class="sxs-lookup"><span data-stu-id="8e550-143">3.0</span></span> |
| [<span data-ttu-id="8e550-144">Kompatibilitätsoption EnableVisualStyleValidation wird nicht unterstützt</span><span class="sxs-lookup"><span data-stu-id="8e550-144">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported) | <span data-ttu-id="8e550-145">3.0</span><span class="sxs-lookup"><span data-stu-id="8e550-145">3.0</span></span> |
| [<span data-ttu-id="8e550-146">Kompatibilitätsoption UseLegacyContextMenuStripSourceControlValue wird nicht unterstützt</span><span class="sxs-lookup"><span data-stu-id="8e550-146">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported) | <span data-ttu-id="8e550-147">3.0</span><span class="sxs-lookup"><span data-stu-id="8e550-147">3.0</span></span> |
| [<span data-ttu-id="8e550-148">Kompatibilitätsoption UseLegacyImages wird nicht unterstützt</span><span class="sxs-lookup"><span data-stu-id="8e550-148">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported) | <span data-ttu-id="8e550-149">3.0</span><span class="sxs-lookup"><span data-stu-id="8e550-149">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="8e550-150">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="8e550-150">.NET 5.0</span></span>

[!INCLUDE [automatically-infer-winexe-output-type](../../../includes/core-changes/windowsforms/5.0/automatically-infer-winexe-output-type.md)]

***

[!INCLUDE [null-owner-causes-invalidoperationexception](../../../includes/core-changes/windowsforms/5.0/null-owner-causes-invalidoperationexception.md)]

***

[!INCLUDE [sdk-and-target-framework-change](../../../includes/core-changes/windowsforms/5.0/sdk-and-target-framework-change.md)]

***

[!INCLUDE [winforms-deprecated-controls](../../../includes/core-changes/windowsforms/5.0/winforms-deprecated-controls.md)]

***

[!INCLUDE [invalid-args-cause-argumentexception](../../../includes/core-changes/windowsforms/5.0/invalid-args-cause-argumentexception.md)]

***

[!INCLUDE [null-args-cause-argumentnullexception](../../../includes/core-changes/windowsforms/5.0/null-args-cause-argumentnullexception.md)]

***

[!INCLUDE [invalid-args-cause-argumentoutofrangeexception](../../../includes/core-changes/windowsforms/5.0/invalid-args-cause-argumentoutofrangeexception.md)]

***

## <a name="net-core-31"></a><span data-ttu-id="8e550-151">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="8e550-151">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="8e550-152">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="8e550-152">.NET Core 3.0</span></span>

[!INCLUDE[Control.DefaultFont changed to Segoe UI 9pt](~/includes/core-changes/windowsforms/3.0/control-defaultfont-changed.md)]

***

[!INCLUDE[Modernization of the FolderBrowserDialog](~/includes/core-changes/windowsforms/3.0/modernized-folderbrowserdialog.md)]

***

[!INCLUDE[SerializableAttribute removed from some Windows Forms types](~/includes/core-changes/windowsforms/3.0/remove-serializationattribute.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-allowupdatechildcontrolindexfortabcontrols.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyscrolling.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotloadlatestricheditcontrol.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotsupportselectallshortcutinmultilinetextbox.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DontSupportReentrantFilterMessage compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-dontsupportreentrantfiltermessage.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.EnableVisualStyleValidation compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-enablevisualstylevalidation.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacycontextmenustripsourcecontrolvalue.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyImages compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyimages.md)]

***

## <a name="see-also"></a><span data-ttu-id="8e550-153">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="8e550-153">See also</span></span>

- [<span data-ttu-id="8e550-154">Portieren einer Windows Forms-App zu .NET Core</span><span class="sxs-lookup"><span data-stu-id="8e550-154">Port a Windows Forms app to .NET Core</span></span>](../porting/winforms.md)
