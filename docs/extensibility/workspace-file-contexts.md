---
title: Visual Studio çalışma dosyası bağlamlarda | Microsoft Docs
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 7aaa0e65-f492-49ea-a845-35bd14910ca7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: cdb013bb10c72041b03fce43e115806ecb3faeac
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31146357"
---
# <a name="workspace-file-contexts"></a>Çalışma alanında dosya bağlamları

Tüm Öngörüler [Klasör Aç](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) çalışma alanları "uygulayan dosya bağlam sağlayıcıları tarafından" üretilen <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> arabirimi. Bu uzantılar klasörlerde desenler için görünebilir veya dosyaları MSBuild dosyalarını ve derleme görevleri dosyaları, okuma, bir dosya bağlam tanımlamak ihtiyaç duydukları Öngörüler birikmesini için Paket bağımlılıklarını, vb. algılama. Tek başına bir dosya bağlam herhangi bir işlem gerçekleştirmez, ancak bunun yerine başka bir uzantı, üzerinde çalışabilmek için veri sağlar.

Her <xref:Microsoft.VisualStudio.Workspace.FileContext> sahip bir `Guid` veri türünü tanımlayan onu taşıyan ilişkili. Bu çalışma alanı kullanır `Guid` daha sonra üzerinden verileri kullanan uzantılı eşleştirme amacıyla <xref:Microsoft.VisualStudio.Workspace.FileContext.Context> özelliği. Bir dosya bağlam sağlayıcısına hangi dosya bağlam tanımlayan meta verilerini dışa `Guid`s Bu verileri oluşturabilir.

Bir kez tanımlandıktan sonra bir dosya bağlam dosyaları veya klasörleri çalışma alanındaki herhangi bir sayıda ilişkili olabilir. Belirli bir dosya veya klasör, dosya bağlamları herhangi bir sayı ile ilişkili olabilir. Bir çok-çok ilişkisi var.

En yaygın senaryolar dosya bağlamları için yapı, hata ayıklama ve dil hizmetlere ilişkilidir. Daha fazla bilgi için bu senaryolarla ilgili diğer konulara bakın.

## <a name="file-context-lifecycle"></a>Dosya içeriği yaşam döngüsü

Ömürleri bir `FileContext` belirleyici şunlardır. Herhangi bir zamanda bir bileşen bağlam türleri bazı kümesi için zaman uyumsuz olarak isteyebilir. Bazı alt istek bağlamı türleri kümesi desteği sağlayıcıları Sorgulanacak. `IWorkspace` Tüketici sağlayıcıları üzerinden arasındaki orta adam örneği görür <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> yöntemi. Tüketiciler bir içerik isteği ve diğerlerinin bir içerik isteği ve uzun süreli bir başvuru korumak içeriğine tabanlı kısa süreli bazı eylemler gerçekleştirme. 

Değişiklikler, bir dosya bağlam eskir neden dosyalara gerçekleşebilir. Sağlayıcı üzerinde bir olay tetikleyin `FileContext` tüketicilere güncelleştirme. Örneğin, bir derleme bağlamı için bazı dosyası sağlanır, ancak herhangi bir disk üzerinde değişiklik bu bağlamda geçersiz kılar, ardından olay özgün üretici çağırabilirsiniz. Yine, başvuran herhangi bir tüketiciye `FileContext` sonra yeni bir sorgulayabilirsiniz `FileContext`.

>[!NOTE]
>Hiçbir gönderme modeli tüketiciye yoktur. Tüketiciler olmaz bildirim bir sağlayıcının yeni `FileContext` kendi istekten sonra.

## <a name="expensive-file-context-computations"></a>Pahalı dosya bağlam hesaplamalar

Özellikle bir sağlayıcı dosyaları arasındaki ilişkiyi çözümlemek gerektiğinde disk okuma dosyası içeriği pahalı olabilir. Örneğin, bir sağlayıcı için bazı kaynak dosyanın dosya bağlam sorgulanan, ancak bir proje dosyasından meta veri dosyası içeriği bağlı. Proje dosyası ayrıştırılırken veya MSBuild ile değerlendirme maliyetlidir. Bunun yerine, uzantı verebilirsiniz bir `IFileScanner` oluşturmak için `FileDataValue` çalışma dizin oluşturma sırasında veri. Artık dosya bağlamları için sorulduğunda `IFileContextProvider` bu dizinli verileri hızla sorgulayabilir. Dizin oluşturma hakkında daha fazla bilgi için bkz: [çalışma dizinini](workspace-indexing.md) konu.

>[!WARNING]
>Diğer yolları dikkatli olun, `FileContext` işlem pahalı olabilir. Bazı kullanıcı Arabirimi etkileşimleri zaman uyumlu ve üzerinde yüksek hacimli kullanan `FileContext` istekleri. Örnekler bir düzenleyici sekmesini açmak ve açma bir **Çözüm Gezgini** bağlam menüsü. Bu eylemler istekleri yazın birçok yapı bağlam olun.

## <a name="file-context-related-apis"></a>Dosya içeriği ilgili API'ler

- <xref:Microsoft.VisualStudio.Workspace.FileContext> veri ve meta verileri tutar.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> ve <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider`1> dosyası içeriği oluşturabilir.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextProviderAttribute> bir dosya bağlam sağlayıcısına dışa aktarır.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> Tüketiciler için dosya içerikleri almak için kullanılır.
- <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes> Klasör Aç tüketir yapı içerik türlerini tanımlar.

## <a name="file-context-actions"></a>Dosya içeriği Eylemler

Sırada bir `FileContext` kendisi hakkında bazı dosyalar yalnızca verileri olan bir <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> express ve bu verilerde işlem yapmak için bir yoldur. `IFileContextAction` içinde kullanım esnektir. İki, en yaygın örnekleri oluşturma hata ayıklama ve.

## <a name="reporting-progress"></a>Raporlama ilerleme durumu

<xref:Microsoft.VisualStudio.Workspace.IFileContextActionBase.ExecuteAsync%2A> Yöntemi geçirilir `IProgress<IFileContextActionProgressUpdate>`, ancak bağımsız değişken, türü olarak kullanılmamalıdır. `IFileContextActionProgressUpdate` boş bir arabirim ve çağırma `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` throw `NotImplementedException`. Bunun yerine, `IFileContextAction` senaryo için gerektiği gibi başka bir tür bağımsız değişkeni dönüştürmeniz gerekir.

Visual Studio tarafından sağlanan türleri hakkında daha fazla bilgi için ilgili senaryonun belgelerine bakın.

## <a name="file-context-action-related-apis"></a>Dosya bağlam eylemi ilgili API'ler

- <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> Bazı davranışını göre yürüten bir `FileContext`.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextActionProvider> örneklerini oluşturur `IFileContextAction`.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextActionProviderAttribute> türü aktarır `IWorkspaceProviderFactory<IFileContextActionProvider>`.

## <a name="file-watching"></a>Dosya izleme

Bir çalışma alanı için dosya değişiklik bildirimlerini dinler ve sağlar <xref:Microsoft.VisualStudio.Workspace.IFileWatcherService> aracılığıyla <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A>. "ExcludedItems" ayarı eşleşen dosyaları dosya bildirim olayları oluşturmaz. Olaylar arasındaki bir eşik bildirimi basitleştirme ve yinelenen azaltma için kullanılır. Bir dosya değişikliği tepki gerektiğinde, bu hizmete abone olmalıdır.

>[!TIP]
>Çalışma alanı 's [dizin oluşturma hizmeti](workspace-indexing.md) varsayılan dosya olayları kaydeder. Dosya eklemeleri ve değişiklikleri neden olacak ilgili `IFileScanner`bu dosya için yeni veriler için çağrılacak s olayları. Dosya silme işlemlerinin dizinli verileri kaldırır. Abone olmanız gerekmez, `IFileScanner` dosya İzleyici hizmeti.

## <a name="next-steps"></a>Sonraki adımlar

* [Dizin oluşturma](workspace-indexing.md) -çalışma dizinini toplar ve çalışma alanı hakkında bilgi devam ettirir.
* [Çalışma alanları](workspaces.md) -çalışma kavramları ve ayarlarını depolama gözden geçirin.
