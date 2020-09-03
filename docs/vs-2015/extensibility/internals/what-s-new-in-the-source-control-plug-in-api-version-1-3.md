---
title: Kaynak denetimi eklentisi API sürümü 1,3 ' deki yenilikler |&#39;Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4d5333a5b44e9c990843e66da357578e4a90d210
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200925"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>Kaynak denetimi eklentisi API sürüm 1,3 ' deki yenilikler&#39;
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kaynak denetimi eklentisi API sürümü 1,3, daha gelişmiş denetim sağlamak için aşağıdaki yeni işlevleri sunmaktadır.  
  
## <a name="changes"></a>Değişiklikler  
 Aşağıdaki işlevler, kaynak denetimi eklentisi API sürümü 1,3 ' de yenidir:  
  
|İşlev|Genel Bakış|  
|--------------|--------------|  
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|Ek özellik bitlerinin raporlanmasını sağlar|  
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|Sürüm denetimi veritabanında yeni sürümlere sahip dosyaların yerel diskten incelemesini sağlar|  
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|Belirtilen dosyalar için ad değişikliklerinin (yeniden adlandırmalar, eklemeler ve silmeler) durumunun incelemesini sağlar|  
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|Sürüm denetimi veritabanındaki dizinlerin ve dosyaların incelemesini sağlar|  
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|Sürüm denetim veritabanından geçerli projeye belirtilen dosya listesini ekler|  
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|Belirtilen dosyaların sessiz bir "Al" işlemini gerçekleştirir (Kullanıcı arabirimi gösterilmez)|  
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|Kullanıcıya özgü seçeneklere erişime izin verir|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başlarken](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)   
 [Kaynak Denetimi Eklentisi API Sürümü 1.2’deki Yenilikler](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
