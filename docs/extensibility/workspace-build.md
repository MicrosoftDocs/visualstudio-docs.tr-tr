---
title: Visual Studio çalışma alanı oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 813f7a5e-f298-4469-9f4c-a5bddf5a6e14
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: f7415c99c68436519f9bab721fe88a48f750fa1c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49857654"
---
# <a name="workspace-build"></a>Çalışma alanı oluşturma

Derleme desteği [Klasör Aç](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) senaryoları sağlamak için bir uzatıcı gerektirir [dizine](workspace-indexing.md) ve [dosya bağlamını](workspace-file-contexts.md) verilerini [çalışma](workspaces.md), olarak çalıştırılacak iyi derleme eylemi.

Uzantınızı ihtiyacınız, bir ana hat aşağıdadır.

## <a name="build-file-context"></a>Dosya içerik oluşturun

- Sağlayıcı üreteci
  - `ExportFileContextProviderAttribute` özniteliğini `supportedContextTypeGuids` tüm geçerli `string` arasındaki sabitleri `BuildContextTypes`
  - Uygulayan `IWorkspaceProviderFactory<IFileContextProvider>`
  - Dosya içeriği sağlayıcısı
    - Döndürür bir `FileContext` her biri için işlemi ve desteklenen yapılandırma derleme
      - `contextType` Kaynak <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes>
      - `context` uygulayan <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> ile `Configuration` özelliği olarak derleme yapılandırmasını (örneğin `"Debug|x86"`, `"ret"`, veya `null` uygulanabilir değilse). Alternatif olarak, bir örneğini kullanması <xref:Microsoft.VisualStudio.Workspace.Build.BuildConfigurationContext>. Yapılandırma değeri **gerekir** dizinli dosya veri değeri yapılandırmasından eşleşmesi.

## <a name="indexed-build-file-data-value"></a>Dizinli derleme dosya veri değeri

- Sağlayıcı üreteci
  - `ExportFileScannerAttribute` özniteliğini `IReadOnlyCollection<FileDataValue>` desteklenen bir tür olarak
  - Uygulayan `IWorkspaceProviderFactory<IFileScanner>`
- Üzerinde dosya tarayıcı `ScanContentAsync<T>`
  - Veri döndüren zaman `FileScannerTypeConstants.FileDataValuesType` bağımsız değişken türü
  - Her yapılandırma ile oluşturulmuş bir dosya veri değerini döndürür:
    - `type` olarak `BuildConfigurationContext.ContextTypeGuid`
    - `context` Yapı yapılandırmanızı olarak (örneğin `"Debug|x86"`, `"ret"`, veya `null` uygulanabilir değilse). Bu değer **gerekir** dosya bağlamını yapılandırmasından eşleşmesi.

## <a name="build-file-context-action"></a>Derleme dosya bağlamı eylemi

- Sağlayıcı üreteci
  - `ExportFileContextActionProvider` özniteliğini `supportedContextTypeGuids` tüm geçerli `string` arasındaki sabitleri `BuildContextTypes`
  - Uygulayan `IWorkspaceProviderFactory<IFileContextActionProvider>`
- Eylem sağlayıcısında `IFileContextActionProvider.GetActionsAsync`
  - Döndürür bir `IFileContextAction` eşleşen verilen `FileContext.ContextType` değeri
- Dosya bağlamı eylemi
  - Implements `IFileContextAction` ve <xref:Microsoft.VisualStudio.Workspace.Extensions.VS.IVsCommandItem>
  - `CommandGroup` özellik döndürür `16537f6e-cb14-44da-b087-d1387ce3bf57`
  - `CommandId` olan `0x1000` yapı için `0x1010` yeniden oluşturma için veya `0x1020` temizlemek için

>[!NOTE]
>Bu yana `FileDataValue` sıralanması gerekiyor, bazı çalışma ve hangi dosya tarama için tam yapı işlevselliğinde noktası açma arasındaki süre miktarını olacaktır. Gecikme, daha önce önbelleğe alınmış dizin olduğundan ilk bir klasör açılırken görülür.

## <a name="reporting-messages-from-a-build"></a>Bir yapıdan raporlama iletileri

Derleme bilgi, uyarı ve hata iletileri kullanıcılara iki yoldan biriyle ortaya çıkabilir. Basit bir yolla kullanmaktır <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> ve sağlayan bir <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage>, şu şekilde:

```csharp
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Build;

private static void OutputBuildMessage(IWorkspace workspace)
{
    IBuildMessageService buildMessageService = workspace.GetBuildMessageService();

    if (buildMessageService != null)
    {
      // Example error build message. See the documentation for BuildMessage for more information.
      var message = new BuildMessage()
      {
          Type = BuildMessage.TaskType.Error,
          Code = "MY1001",
          TaskText = "This is a sample error",
          ProjectFile = "buildfile.bld",
          File = "sourcefile.src"
          LogMessage = $"This is sample text that will only go to the Build output window pane.\n"

          // And any other properties to set
      };

      buildMessageService.ReportBuildMessages(new BuildMessage[] { message });
    }
}
```

`BuildMessage.Type` ve `BuildMessage.LogMessage` bilgileri kullanıcıya Burada sunulan davranışını denetler. Tüm `BuildMessage.TaskType` dışındaki değeri `None` oluşturacak bir **hata listesi** sağlanan Ayrıntılar girişi. `LogMessage` her zaman içinde çıkarır **derleme** bölmesinde **çıkış** araç penceresi.

Alternatif olarak, uzantıları doğrudan etkileşim kurabilir **hata listesi** veya **derleme** bölmesi. Visual Studio 2017 sürüm 15.7'dan önceki sürümlerde bir hata var. burada `pszProjectUniqueName` bağımsız değişkeni <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane2.OutputTaskItemStringEx2*> göz ardı edilir.

>[!WARNING]
>Arayanlar `IFileContextAction.ExecuteAsync` rastgele temel uygulamaları sağlayabilir `IProgress<IFileContextActionProgressUpdate>` bağımsız değişken. Hiçbir zaman çağırma `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` doğrudan. Şu anda bu bağımsız değişken kullanmak için hiçbir genel yönergeleri vardır, ancak bu yönergelerdir değiştirilebilir.

## <a name="build-related-apis"></a>Derleme ilgili API'ler

- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildConfigurationContext> Yapı yapılandırma ayrıntıları sağlar.
- <xref:Microsoft.VisualStudio.Workspace.Build.IBuildMessageService> gösterir <xref:Microsoft.VisualStudio.Workspace.Build.BuildMessage>kullanıcılara s.

## <a name="tasksvsjson-and-launchvsjson"></a>Tasks.vs.JSON ve launch.vs.json

Bir launch.vs.json ya da tasks.vs.json dosyası yazma hakkında daha fazla bilgi için bkz: [yapı özelleştirme ve hata ayıklama görevleri](../ide/customize-build-and-debug-tasks-in-visual-studio.md).

## <a name="next-steps"></a>Sonraki adımlar

* [Dil sunucusu Protokolü](language-server-protocol.md) -dil sunucuları Visual Studio'ya tümleştirmeyi öğrenin.