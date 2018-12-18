---
title: Günlükçüleri derleme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, writing loggers
- MSBuild, logging
- logging [MSBuild]
ms.assetid: fa34810d-185a-4d22-92bd-9852915e5f1d
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dbf27388013b71945879537dffff1e53a7314e7b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49853254"
---
# <a name="build-loggers"></a>Günlükçüleri Derleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Günlükçüleri derleme çıkışını özelleştirebilir ve belirli bir yapı olaylarına yanıt olarak iletileri, hata veya uyarı görüntülemek bir yol sağlar. Her bir Günlükçü uygulayan bir .NET sınıfı uygulanır <xref:Microsoft.Build.Framework.ILogger> Microsoft.Build.Framework.dll derlemede tanımlanan arabirimi.  
  
 Günlükçü uygularken kullanabileceğiniz iki yaklaşım vardır:  
  
- Uygulama <xref:Microsoft.Build.Framework.ILogger> doğrudan arabirim.  
  
- Sınıfınıza Yardımcısı sınıfından türetilen <xref:Microsoft.Build.Utilities.Logger>, Microsoft.Build.Utilities.dll derlemesinde tanımlanmıştır. <xref:Microsoft.Build.Utilities.Logger> uygulayan <xref:Microsoft.Build.Framework.ILogger> ve bazı varsayılan uygulamalarını sağlar <xref:Microsoft.Build.Framework.ILogger> üyeleri.  
  
  Bu konuda, türetilen bir basit bir Günlükçü yazılacağı nasıl açıklayacak <xref:Microsoft.Build.Utilities.Logger>, ve derleme olaylarını konsolunda belirli yanıt iletileri görüntüler.  
  
## <a name="registering-for-events"></a>Olayları'nın kaydedilmesi  
 Günlükçü amacı, yapı altyapısı tarafından raporlanan yapı ilerlemesini bilgi toplamak ve daha sonra bu bilgileri faydalı bir şekilde rapor sağlamaktır. Tüm günlükçüleri kılmalı <xref:Microsoft.Build.Utilities.Logger.Initialize%2A> Günlükçü olayları için kaydettiği olan yöntem. Bu örnekte Günlükçü için kayıtları <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>, ve <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> olayları.  
  
 [!code-csharp[msbuild_SimpleConsoleLogger#2](../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs#2)]  
  
## <a name="responding-to-events"></a>Olaylarına yanıt verme  
 Günlükçü belirli olayları kaydedildiğinden, ortaya çıkan bu olayları işlemek gerekir. İçin <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>, ve <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> olayları Günlükçü yalnızca yazar kısa ifade ve olayla proje dosyasının adı. Günlükçü gelen tüm iletileri konsol penceresine yazılır.  
  
 [!code-csharp[msbuild_SimpleConsoleLogger#3](../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs#3)]  
  
## <a name="responding-to-logger-verbosity-values"></a>Günlükçü ayrıntı değerlerine yanıt  
 Bazı durumlarda yalnızca bilgileri, bir olay günlüğe isteyebilirsiniz MSBuild.exe **/verbosity** anahtarını belirli bir değer içeriyor. Bu örnekte, <xref:Microsoft.Build.Framework.IEventSource.TargetStarted> olay işleyicisi, bir ileti yalnızca günlükleri <xref:Microsoft.Build.Utilities.Logger.Verbosity%2A> tarafından ayarlanan özellik **/verbosity** değiştirmek, eşittir <xref:Microsoft.Build.Framework.LoggerVerbosity> `Detailed`.  
  
 [!code-csharp[msbuild_SimpleConsoleLogger#4](../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs#4)]  
  
## <a name="specifying-a-logger"></a>Günlükçü belirtme  
 Günlükçü bütünleştirilmiş kod içine derlenmiş olan bir kez söylemeniz gerekir [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] bu Günlükçü yapılar sırasında kullanılacak. Bu yapılır kullanarak **/logger** MSBuild.exe ile geçiş yapın. MSBuild.exe kullanılabilir anahtarları hakkında daha fazla bilgi için bkz. [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md).  
  
 Aşağıdaki komut satırını projeyi derler `MyProject.csproj` Günlükçü sınıfı içinde uygulanan kullanır `SimpleLogger.dll`. **/Nologo** anahtar başlığını ve telif hakkı iletisini gizler ve **/noconsolelogger** anahtarı varsayılan devre dışı bırakır [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] konsol Günlükçü.  
  
```  
MSBuild /nologo /noconsolelogger /logger:SimpleLogger.dll  
```  
  
 Aşağıdaki komut satırını, aynı Günlükçü ancak ile projeyi oluşturur bir `Verbosity` düzeyini `Detailed`.  
  
```  
MSBuild /nologo /noconsolelogger /logger:SimpleLogger.dll /verbosity:Detailed  
```  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, Günlükçü için tam kod içerir.  
  
### <a name="code"></a>Kod  
 [!code-csharp[msbuild_SimpleConsoleLogger#1](../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleConsoleLogger/CS/msbuild_SimpleConsoleLogger.cs#1)]  
  
### <a name="comments"></a>Açıklamalar  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, konsol penceresinde görüntüleme yerine bir dosya günlüğüne yazan bir Günlükçü uygulamak gösterilmektedir.  
  
### <a name="code"></a>Kod  
 [!code-csharp[msbuild_BasicLogger#1](../snippets/csharp/VS_Snippets_Misc/msbuild_BasicLogger/CS/msbuild_BasicLogger.cs#1)]  
  
### <a name="comments"></a>Açıklamalar  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Derleme günlükleri alma](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [MSBuild Kavramları](../msbuild/msbuild-concepts.md)



