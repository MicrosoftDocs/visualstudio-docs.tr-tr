---
title: Günlükçüleri derleme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing loggers
- MSBuild, logging
- logging [MSBuild]
ms.assetid: fa34810d-185a-4d22-92bd-9852915e5f1d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2e1faf28c05dec58117e5d34e21e7c8020ad3a4d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894293"
---
# <a name="build-loggers"></a>Günlükçüleri derleme
Günlükçüleri derleme çıkışını özelleştirebilir ve belirli bir yapı olaylarına yanıt olarak iletileri, hata veya uyarı görüntülemek bir yol sağlar. Her bir Günlükçü uygulayan bir .NET sınıfı uygulanır <xref:Microsoft.Build.Framework.ILogger> tanımlanan arabirimi *Microsoft.Build.Framework.dll* derleme.  
  
 Günlükçü uygularken kullanabileceğiniz iki yaklaşım vardır:  
  
- Uygulama <xref:Microsoft.Build.Framework.ILogger> doğrudan arabirim.  
  
- Sınıfınıza Yardımcısı sınıfından türetilen <xref:Microsoft.Build.Utilities.Logger>, tanımlanan *Microsoft.Build.Utilities.dll* derleme. <xref:Microsoft.Build.Utilities.Logger> uygulayan <xref:Microsoft.Build.Framework.ILogger> ve bazı varsayılan uygulamalarını sağlar <xref:Microsoft.Build.Framework.ILogger> üyeleri.  
  
  Bu konuda, türetilen bir basit bir Günlükçü yazılacağı nasıl açıklayacak <xref:Microsoft.Build.Utilities.Logger>, ve derleme olaylarını konsolunda belirli yanıt iletileri görüntüler.  
  
## <a name="register-for-events"></a>Olayları için kaydolun  
 Günlükçü amacı, yapı altyapısı tarafından raporlanan yapı ilerlemesini bilgi toplamak ve daha sonra bu bilgileri faydalı bir şekilde rapor sağlamaktır. Tüm günlükçüleri kılmalı <xref:Microsoft.Build.Utilities.Logger.Initialize%2A> Günlükçü olayları için kaydettiği olan yöntem. Bu örnekte Günlükçü için kayıtları <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>, ve <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> olayları.  
  
 [!code-csharp[msbuild_SimpleConsoleLogger#2](../msbuild/codesnippet/CSharp/build-loggers_1.cs)]  
  
## <a name="respond-to-events"></a>Olaylara yanıt vermesi  
 Günlükçü belirli olayları kaydedildiğinden, ortaya çıkan bu olayları işlemek gerekir. İçin <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>, ve <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> olayları Günlükçü yalnızca yazar kısa ifade ve olayla proje dosyasının adı. Günlükçü gelen tüm iletileri konsol penceresine yazılır.  
  
 [!code-csharp[msbuild_SimpleConsoleLogger#3](../msbuild/codesnippet/CSharp/build-loggers_2.cs)]  
  
## <a name="respond-to-logger-verbosity-values"></a>Günlükçü ayrıntı değerlerine yanıt  
 Bazı durumlarda yalnızca bilgileri, bir olay günlüğe isteyebilirsiniz MSBuild.exe **-ayrıntı** anahtarını belirli bir değer içeriyor. Bu örnekte, <xref:Microsoft.Build.Framework.IEventSource.TargetStarted> olay işleyicisi, bir ileti yalnızca günlükleri <xref:Microsoft.Build.Utilities.Logger.Verbosity%2A> tarafından ayarlanan özellik **-ayrıntı** değiştirmek, eşittir <xref:Microsoft.Build.Framework.LoggerVerbosity> `Detailed`.  
  
 [!code-csharp[msbuild_SimpleConsoleLogger#4](../msbuild/codesnippet/CSharp/build-loggers_3.cs)]  
  
## <a name="specify-a-logger"></a>Bir Günlükçü belirtin  
 Günlükçü bütünleştirilmiş kod içine derlenmiş olan bir kez söylemeniz gerekir [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] bu Günlükçü yapılar sırasında kullanılacak. Bu yapılır kullanarak **-Günlükçü** anahtarı ile *MSBuild.exe*. Kullanılabilir anahtarları hakkında daha fazla bilgi için *MSBuild.exe*, bkz: [komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md).  
  
 Aşağıdaki komut satırını projeyi derler *MyProject.csproj* Günlükçü sınıfı içinde uygulanan kullanır *SimpleLogger.dll*. **- Nologo** anahtar başlığını ve telif hakkı iletisini gizler ve **- noconsolelogger** anahtarı varsayılan devre dışı bırakır [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] konsol Günlükçü.  
  
```cmd  
MSBuild -nologo -noconsolelogger -logger:SimpleLogger.dll  
```  
  
 Aşağıdaki komut satırını, aynı Günlükçü ancak ile projeyi oluşturur bir `Verbosity` düzeyini `Detailed`.  
  
```cmd  
MSBuild -nologo -noconsolelogger -logger:SimpleLogger.dll -verbosity:Detailed  
```  

## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, Günlükçü için tam kod içerir.  
  
### <a name="code"></a>Kod  
 [!code-csharp[msbuild_SimpleConsoleLogger#1](../msbuild/codesnippet/CSharp/build-loggers_4.cs)]  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek, konsol penceresinde görüntüleme yerine bir dosya günlüğüne yazan bir Günlükçü uygulamak gösterilmektedir.  
  
### <a name="code"></a>Kod  
 [!code-csharp[msbuild_BasicLogger#1](../msbuild/codesnippet/CSharp/build-loggers_5.cs)]  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Derleme günlükleri alın](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [MSBuild kavramları](../msbuild/msbuild-concepts.md)