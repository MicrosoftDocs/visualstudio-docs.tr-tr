---
title: Komut kullanılabilirliği | Microsoft Docs
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 98250763f504bc7d142f15e559334f296a2e026b
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39511140"
---
# <a name="command-availability"></a>Komut kullanılabilirliği

Visual Studio bağlamı, hangi komutları kullanılabilir olduğunu belirler. İçerik, geçerli proje, geçerli Düzenleyici, yüklenen VSPackage'ları ve diğer yönleri tümleşik geliştirme ortamı (IDE) bağlı olarak değiştirebilirsiniz.

## <a name="command-contexts"></a>Komut bağlamları

Aşağıdaki komut bağlamları en yaygın şunlardır:

- IDE: IDE tarafından sağlanan komutları her zaman kullanılabilir.

- VSPackage: VSPackages komutlar için görünür veya gizli olduğunda tanımlayabilirsiniz.

- Proje: Yalnızca şu anda seçili proje için proje komut belirir.

- Düzenleyen: Yalnızca bir düzenleyici aynı anda etkin olabilir. Aktif Düzenleyici komutları kullanılabilir. Bir düzenleyici bir dil hizmeti ile yakın bir tümleştirmede çalışır. Dil hizmeti ilişkili Düzenleyicisi bağlamında komutlarının işlemesi gerekir.

- Dosya türü: dosyanın birden fazla tür yükleyebilir ve bir düzenleyici. Kullanılabilir komutlar, dosya türüne bağlı olarak değiştirebilirsiniz.

- Etkin pencereyi: son etkin belge penceresini tuş bağlamaları için kullanıcı arabirimi (UI) bağlamını ayarlar. Ancak, iç web tarayıcısını benzer bir anahtar bağlaması tablo içeren bir araç penceresi UI bağlamı ayarlayabilirsiniz. HTML düzenleyicisi gibi birden çok sekmeli belge pencereleri için farklı komut bağlam GUID her sekmesi vardır. Araç penceresi kaydedildikten sonra her zaman kullanılabilir **görünümü** menüsü.

- UI bağlamı: UI bağlamları değerleri tarafından tanımlanan <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> sınıfından, örneğin, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> çözüm yerleşik olduğunda veya <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> hata ayıklayıcısı etkinken. Aynı anda birden fazla UI bağlamı etkin olabilir.

## <a name="define-custom-context-guids"></a>Özel bağlam GUID'leri tanımlayın

GUID zaten tanımlı değil bir uygun komut bağlamı ise, VSPackage birinde tanımlayabilir ve etkin veya etkin değil olarak komutlarınızı görünürlüğünü denetleme için gerekli olması için program:

1.  Bağlam GUID'leri çağırarak kayıt <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> yöntemi.

2.  Bir bağlam GUID durumunu çağırarak alma <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> yöntemi.

3.  Çağırarak bağlam GUID'leri açıp kapatma <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> yöntemi.
   
> [!CAUTION]
> Diğer VSPackage'ları bunlara bağımlı çünkü, VSPackage'ı tüm mevcut bir bağlamı GUID'leri etkilemez emin olun.

## <a name="see-also"></a>Ayrıca bkz.

- [Seçim bağlamı nesneleri](../../extensibility/internals/selection-context-objects.md)
- [VSPackage kullanıcı arabirimi öğelerini nasıl eklenir](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)