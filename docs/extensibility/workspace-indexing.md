---
title: Çalışma alanı Visual Studio'da dizinleme | Microsoft Docs
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 3163e98c-1c79-48a7-813f-7923be894ba1
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 5004db0d895d1fdc697c18606c346c24cd484527
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49939156"
---
# <a name="workspace-indexing"></a>Çalışma dizini oluşturma

Bir çözümde proje sistemleri için derleme işlevselliği sağlamaktan sorumluysa, hata ayıklama, **GoTo** sembol arama ve daha fazlası. Proje sistemleri, ilişki ve bir proje içindeki dosyaların özelliklerini anlamak için bu işi yapabilmek için. Bir [Klasör Aç](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) çalışma zengin IDE özelliklerini de sağlamak için aynı olan bilgileri gerekir. Toplama ve bu verileri kalıcı olarak depolanması çalışma dizinini adlı bir işlemdir. Bu dizini oluşturulmuş bir veri kümesi zaman uyumsuz API'ler aracılığıyla sorgulanabilir. Genişleticiler için de geçerlidir dizin oluşturma işleminde sağlayarak <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScanner>belirli türden dosyalar yapılacağını bildiğiniz s.

## <a name="types-of-indexed-data"></a>Dizini oluşturulmuş veri türleri

Dizine alınmış verilerin üç türü vardır. Not Dosya tarayıcılarından beklenen türde dizinden seri durumdan çıkarılmış türü farklıdır.

|Veri|Dosya tarayıcı türü|Dizin sorgu sonuç türü|İlgili türleri|
|--|--|--|--|
|Referanslar|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfo>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileReferenceInfoType>|
|Simgeleri|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinition>|<xref:Microsoft.VisualStudio.Workspace.Indexing.SymbolDefinitionSearchResult>|<xref:Microsoft.VisualStudio.Workspace.Indexing.ISymbolService> yerine kullanılması gereken `IIndexWorkspaceService` sorgular için|
|Veri değerleri|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataValue>|<xref:Microsoft.VisualStudio.Workspace.Indexing.FileDataResult`1>||

## <a name="querying-for-indexed-data"></a>Dizini oluşturulmuş veri sorgulama

Kalıcı veri erişmek için kullanılabilecek iki zaman uyumsuz türler var. İlk aracılığıyladır <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceData>. Bir tek dosyanın temel erişim sağlayan `FileReferenceResult` ve `FileDataResult` veri ve sonuçlarını önbelleğe alır. İkinci <xref:Microsoft.VisualStudio.Workspace.Indexing.IIndexWorkspaceService> , önbelleğe alma kullanmıyor, ancak daha fazla sorgulama özellikleri sunar.

```csharp
using Microsoft.VisualStudio.Workspace;
using Microsoft.VisualStudio.Workspace.Indexing;

private static IIndexWorkspaceData GetCachedIndexedData(IWorkspace workspace)
{
    // Gets access to indexed data wrapped in a cache.
    return workspace?.GetIndexWorkspaceDataService()?.CreateIndexWorkspaceData();
}

private static IIndexWorkspaceService GetDirectIndexedData(IWorkspace workspace)
{
    // Gets direct access to indexed data.
    // Can also be casted to IIndexWorkspaceService2.
    return workspace?.GetIndexWorkspaceService();
}
```

## <a name="participating-in-indexing"></a>Dizin oluşturma işleminde katılma

Çalışma dizini oluşturma kabaca aşağıdaki sırayla aşağıdaki gibidir:

1. Bulma ve Kalıcılık dosya sistemi varlık çalışma alanı (yalnızca ilk açılış tarama).
1. Dosya en yüksek önceliğe sahip eşleşen sağlayıcısı taramak için sorulan `FileReferenceInfo`s.
1. Dosya en yüksek önceliğe sahip eşleşen sağlayıcısı taramak için sorulan `SymbolDefinition`s.
1. Dosya tüm sağlayıcılar için sorulan `FileDataValue`s.

Uzantıları, bir tarayıcı uygulayarak verebilirsiniz `IWorkspaceProviderFactory<IFileScanner>` ve türü ile dışarı aktarma <xref:Microsoft.VisualStudio.Workspace.Indexing.ExportFileScannerAttribute>. `SupportedTypes` Öznitelik bağımsız değişkeni, bir veya daha fazla değerlerinden olmalıdır <xref:Microsoft.VisualStudio.Workspace.Indexing.FileScannerTypeConstants>. Örnek tarayıcı için bkz: VS SDK [örnek](https://github.com/Microsoft/VSSDK-Extensibility-Samples/blob/master/Open_Folder_Extensibility/C%23/SymbolScannerSample/TxtFileSymbolScanner.cs).

> [!WARNING]
> Destekleyen bir dosya tarayıcı verme `FileScannerTypeConstants.FileScannerContentType` türü. Bu, Microsoft iç, yalnızca amacıyla kullanılır.

Gelişmiş durumlarda, bir uzantı dinamik olarak rastgele bir dosya türleri kümesi destekleyebilir. MEF dışarı aktarma yerine `IWorkspaceProviderFactory<IFileScanner>`, uzantı verebilirsiniz `IWorkspaceProviderFactory<IFileScannerProvider>`. Dizin oluşturma işlemi başladığında, bu Fabrika türü örneği, alınan, ve sahip kendi <xref:Microsoft.VisualStudio.Workspace.Indexing.IFileScannerProvider.GetSymbolScannersAsync%2A> yöntemi çağrılır. `IFileScanner` örnekleri destekleyen herhangi bir değer `FileScannerTpeConstants` testleriyle kullanılır, yalnızca simgeler.

## <a name="next-steps"></a>Sonraki adımlar

* [Çalışma alanları ve dil Hizmetleri](workspace-language-services.md) -bir klasör Aç çalışma alanınıza dil hizmetlerini tümleştirmeyi öğrenin.
* [Çalışma alanı derleme](workspace-build.md) -Klasör Aç destekler MSBuild ve derleme görevleri dosyalarını gibi sistemleri oluşturun.