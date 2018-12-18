---
title: VSPackage yapısı (kaynak denetimi VSPackage) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d36e31db9c47325e62fe759cd5030c5f24fb73be
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37057629"
---
# <a name="vspackage-structure-source-control-vspackage"></a>VSPackage Yapısı (Kaynak Denetimi VSPackage’ı)

Kaynak denetimi paket SDK bilgilendirilmesine kaynak denetimi işlevlerinin Visual Studio ortamıyla tümleştirmek bir kaynak denetimi uygulayan bir VSPackage oluşturma yönergeleri olanak sağlar. Bir VSPackage genellikle isteğe bağlı olarak, kayıt defteri girdileri paket tarafından tanıtılan Hizmetleri göre Visual Studio tümleşik geliştirme ortamı (IDE) tarafından yüklenen bir COM bileşenidir. Her VSPackage uygulamalıdır <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>. Tipik bir VSPackage Visual Studio IDE tarafından sunulan hizmetlerin tükettiği ve bazı hizmetler kendi proffers.

Bir VSPackage menü öğelerinden bildirir ve varsayılan öğesi durumu .vsct dosyası aracılığıyla oluşturur. VSPackage yüklenene kadar Visual Studio IDE bu durumda menü öğelerini görüntüler. Sonuç olarak, VSPackage'nın uyarlamasını <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> yöntemi etkinleştirmek veya menü öğelerini devre dışı bırakmak için çağrılır.

## <a name="source-control-package-characteristics"></a>Kaynak denetimi paket özellikleri

Kaynak denetimi VSPackage Visual Studio'ya son derece tümleşiktir. VSPackage semantiğini şunları içerir:

-   Bir VSPackage olması uygulanacak arabirim ( `IVsPackage` arabirimi)

-   UI komutu uygulaması (.vsct dosya ve uyarlamasını <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimi)

-   Visual Studio ile VSPackage kaydı.

Kaynak denetimi VSPackage bu bir Visual Studio varlıklar ile iletişim kurması gerekir:

-   Projeler

-   Düzenleyiciler

-   Çözümler

-   Windows

-   Çalışan belge tablosu

### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Tüketilebilir visual Studio ortamında Hizmetleri

<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>

SVsRegisterScciProvider hizmeti

<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>

### <a name="vsip-interfaces-implemented-and-called"></a>Uygulanan ve adlı VSIP arabirimleri

Kaynak denetimi bir VSPackage paketidir ve bu nedenle doğrudan Visual Studio ile kaydedilen diğer VSPackages ile etkileşebilirsiniz. Kaynak denetimi işlevlerinin tüm tekliflerden sağlamak için bir kaynak denetimi VSPackage projeleri veya kabuk tarafından sağlanan arabirimleri uğraşmanız.

Visual Studio her projede uygulamalıdır <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> Visual Studio IDE içinde bir proje olarak kabul edilecek. Ancak, bu arabirim değil özelleştirilmiş yeterli kaynak denetimi için. Kaynak altında olması beklenen projeleri uygulama Denetim <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>. Bu arabirim kaynak denetimi VSPackage karakterlerin ve bağlama bilgileri (sunucu konumu ve disk konumun altındaki bir projenin arasında bağlantı kurmak için gerekli bilgileri sağlamak için ve içeriği için bir proje sorgulamak için kullanılır Kaynak Denetimi).

VSPackage uygulayan kaynak denetimi <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, sırayla sağlayan kendileri için kaynak denetimi kaydetmek ve bunların durumunu karakterlerin almak projeleri.

Kaynak denetimi VSPackage dikkate almanız gereken arabirimleri tam bir listesi için bkz: [ilgili hizmet ve arabirimi](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Tasarım öğeleri](../../extensibility/internals/source-control-vspackage-design-elements.md)
- [İlgili hizmet ve arabirimi](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)