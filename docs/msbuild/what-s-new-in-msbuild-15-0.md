---
title: Hangi&#39;s MSBuild 15'deki yenilikler | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.technology: msbuild
ms.topic: conceptual
ms.assetid: 9976b6fd-d052-4017-b848-35b5bf4b2f66
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2333f45cca5510a4ba3bb0f54abf45a569454cf8
ms.sourcegitcommit: 25fc9605ba673afb51a24ce587cf4304b06aa577
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2018
ms.locfileid: "47028969"
---
# <a name="whats-new-in-msbuild-15"></a>MSBuild 15'te Yenilikler

MSBuild olarak kullanıma sunuldu parçası [.NET Core SDK'sı](https://www.microsoft.com/net/download/core) ve Windows, macOS ve Linux üzerinde .NET Core projeleri oluşturabilirsiniz.

## <a name="changed-path"></a>Değiştirilen yolu

 MSBuild, şimdi Visual Studio'nun her sürümü altında bir klasöre yüklenir. Örneğin, *C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\MSBuild*. MSBuild bulmak için aşağıdaki PowerShell modülünü de kullanabilirsiniz: [vssetup.powershell](https://github.com/Microsoft/vssetup.powershell).

 MSBuild artık genel derleme önbelleğinde yüklü değil. MSBuild'ı programlı olarak başvurmak için NuGet paketlerini kullanın.

## <a name="changed-properties"></a>Özellikleri değiştirilmiş

 Aşağıdaki MSBuild özellikleri nedeniyle yeni sürüm numarası güncelleştirildi.

- `MSBuildToolsVersion` Bu araçlar için 15.0 sürümüdür. Derleme 15.1.0.0 sürümüdür.

- `MSBuildToolsPath` artık sabit bir konum vardır. Varsayılan olarak bulunur *MSBuild\15.0\Bin* klasörüyle ilgili Visual Studio yükleme konumunu, ancak Visual Studio yükleme konumu yükleme sırasında değiştirilebilir.

- `ToolsVersion` değerleri, kayıt defterinde artık ayarlanır.

- `SDK35ToolsPath` Ve `SDK40ToolsPath` noktası özelliklerini (örneğin, 10.0A 4.X araçları için) Visual Studio'nun bu sürümü ile paketlenmiştir .NET Framework SDK'sına.

## <a name="updates"></a>Güncelleştirmeler
- [Proje öğesi](../msbuild/project-element-msbuild.md) yeni bir `SDK` özniteliği. Ayrıca `Xmlns` özniteliği, artık isteğe bağlıdır. Hakkında daha fazla bilgi için `SDK` özniteliği için bkz: [nasıl yapılır: kullanım MSBuild proje SDK'ları](../msbuild/how-to-use-project-sdk.md), [paketler, meta paketler ve çerçeveler](/dotnet/core/packages) ve [csproj eklemeler biçimlendirmek için .NET Çekirdek](/dotnet/core/tools/csproj).
- [Öğe unsuru](../msbuild/item-element-msbuild.md) dış hedefleri olan yeni bir `Update` özniteliği. Ayrıca, kısıtlama `Remove` özniteliği ortadan kaldırılmıştır.
- *Directory.Build.props* özelleştirmeleri bir dizin altında projelerine sağlayan kullanıcı tanımlı bir dosya. Bu dosya gelen otomatik olarak içeri aktarılır *Microsoft.Common.props* sürece özelliği `ImportDirectoryBuildTargets` ayarlanır **false**. *Directory.Build.targets* tarafından alınan *Microsoft.Common.targets*.
- Herhangi bir meta veri öznitelikleri geçerli listesi ile çakışmadığından bir ad ile isteğe bağlı olarak bir özniteliği olarak ifade edilebilir. Daha fazla bilgi için [öğe](../msbuild/item-element-msbuild.md).

## <a name="new-property-functions"></a>Yeni özellik işlevleri

- `EnsureTrailingSlash` zaten yoksa eğik bir yolu ekler.
- `NormalizePath` yol öğesi bir araya getirir ve çıkış dizesi geçerli işletim sistemi için doğru dizin ayırıcı karakterleri sahip olmasını sağlar.
- `NormalizeDirectory` yol öğesi bir araya getirir, sonunda bir eğik çizgi sağlar ve çıkış dizesi geçerli işletim sistemi için doğru dizin ayırıcı karakterleri sahip olmasını sağlar.
- `GetPathOfFileAbove` Bu tek hemen önceki dosya yolunu döndürür. Arama için işlevsel olarak eşdeğerdir `<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />`

## <a name="see-also"></a>Ayrıca bkz.
[MSBuild](../msbuild/msbuild.md)
