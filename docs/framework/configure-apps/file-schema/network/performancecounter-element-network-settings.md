---
title: <performanceCounters>-Element (Netzwerkeinstellungen)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounters element
ms.assetid: 3afa1586-e1b8-473d-8985-c3fc90cf561b
ms.openlocfilehash: 584bdafbbd60303401cbc6ad96b8654fe11c7077
ms.sourcegitcommit: a8a205034eeffc7c3e1bdd6f506a75b0f7099ebf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/06/2020
ms.locfileid: "91756259"
---
# <a name="performancecounters-element-network-settings"></a><span data-ttu-id="ab01d-102">\<performanceCounters>-Element (Netzwerkeinstellungen)</span><span class="sxs-lookup"><span data-stu-id="ab01d-102">\<performanceCounters> Element (Network Settings)</span></span>

<span data-ttu-id="ab01d-103">Aktiviert oder deaktiviert Netzwerk Leistungsindikatoren.</span><span class="sxs-lookup"><span data-stu-id="ab01d-103">Enables or disables networking performance counters.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<performanceCounters>**

## <a name="syntax"></a><span data-ttu-id="ab01d-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="ab01d-104">Syntax</span></span>  
  
```xml  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ab01d-105">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="ab01d-105">Attributes and Elements</span></span>  

 <span data-ttu-id="ab01d-106">In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.</span><span class="sxs-lookup"><span data-stu-id="ab01d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ab01d-107">Attribute</span><span class="sxs-lookup"><span data-stu-id="ab01d-107">Attributes</span></span>  
  
|<span data-ttu-id="ab01d-108">attribute</span><span class="sxs-lookup"><span data-stu-id="ab01d-108">Attribute</span></span>|<span data-ttu-id="ab01d-109">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ab01d-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="ab01d-110">Gibt an, ob die Netzwerk Leistungsindikatoren aktiviert sind.</span><span class="sxs-lookup"><span data-stu-id="ab01d-110">Specifies whether the networking performance counters are enabled.</span></span> <span data-ttu-id="ab01d-111">Standardwert: `false`.</span><span class="sxs-lookup"><span data-stu-id="ab01d-111">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ab01d-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="ab01d-112">Child Elements</span></span>  

 <span data-ttu-id="ab01d-113">Keine</span><span class="sxs-lookup"><span data-stu-id="ab01d-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ab01d-114">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="ab01d-114">Parent Elements</span></span>  
  
|<span data-ttu-id="ab01d-115">Element</span><span class="sxs-lookup"><span data-stu-id="ab01d-115">Element</span></span>|<span data-ttu-id="ab01d-116">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ab01d-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ab01d-117">settings</span><span class="sxs-lookup"><span data-stu-id="ab01d-117">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="ab01d-118">Konfiguriert grundlegende Netzwerkoptionen für den <xref:System.Net>-Namespace.</span><span class="sxs-lookup"><span data-stu-id="ab01d-118">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab01d-119">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="ab01d-119">Remarks</span></span>  

 <span data-ttu-id="ab01d-120">Dieses Element kann in der Anwendungskonfigurationsdatei oder in der Computerkonfigurationsdatei ("Machine.config") verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="ab01d-120">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="ab01d-121">Netzwerkleistungsindikatoren müssen in der zu verwendenden Konfigurationsdatei aktiviert sein.</span><span class="sxs-lookup"><span data-stu-id="ab01d-121">Networking performance counters need to be enabled in the configuration file to be used.</span></span> <span data-ttu-id="ab01d-122">Alle Netzwerkleistungsindikatoren werden mit einer einzelnen Einstellung in der Konfigurationsdatei aktiviert bzw. deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="ab01d-122">All networking performance counters are enabled or disabled with a single setting in the configuration file.</span></span> <span data-ttu-id="ab01d-123">Einzelne Netzwerkleistungsindikatoren können nicht aktiviert oder deaktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="ab01d-123">Individual networking performance counters cannot be enabled or disabled.</span></span> <span data-ttu-id="ab01d-124">Weitere Informationen zu den spezifischen Netzwerk Leistungsindikatoren finden Sie unter [Netzwerk Leistungsindikatoren](../../../debug-trace-profile/performance-counters.md#networking-performance-counters).</span><span class="sxs-lookup"><span data-stu-id="ab01d-124">For more information on the specific networking performance counters, see [Networking performance counters](../../../debug-trace-profile/performance-counters.md#networking-performance-counters).</span></span>  
  
 <span data-ttu-id="ab01d-125">Der Standardwert ist, dass Netzwerk Leistungsindikatoren deaktiviert werden.</span><span class="sxs-lookup"><span data-stu-id="ab01d-125">The default value is that networking performance counters are disabled.</span></span>  
  
 <span data-ttu-id="ab01d-126">Die- <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> Eigenschaft kann verwendet werden, um den aktuellen Wert des **aktivierten** Attributs aus den anwendbaren Konfigurationsdateien zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="ab01d-126">The <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> property can be used to get the current value of the **enabled** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab01d-127">Beispiel</span><span class="sxs-lookup"><span data-stu-id="ab01d-127">Example</span></span>  

 <span data-ttu-id="ab01d-128">Im folgenden Beispiel wird gezeigt, wie die verknüpften <xref:System.Net> Namespaces und zum Aktivieren von Netzwerk Leistungsindikatoren konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="ab01d-128">The following example shows how to configure the <xref:System.Net> and related namespaces to enable networking performance counters.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <performanceCounters  
        enabled="true"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ab01d-129">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="ab01d-129">See also</span></span>

- <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="ab01d-130">Network Settings Schema (Schema für Netzwerkeinstellungen)</span><span class="sxs-lookup"><span data-stu-id="ab01d-130">Network Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ab01d-131">Netzwerk Leistungsindikatoren</span><span class="sxs-lookup"><span data-stu-id="ab01d-131">Networking Performance Counters</span></span>](../../../debug-trace-profile/performance-counters.md#networking-performance-counters)
