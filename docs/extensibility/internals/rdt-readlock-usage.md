---
title: RDT_ReadLock kullanım | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7fda2fbb4a4b03dff9d677d9c7581a4138d9fcf7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131687"
---
# <a name="rdtreadlock-usage"></a>RDT_ReadLock kullanımı

<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> Visual Studio IDE içinde şu anda açık olan tüm belgelerin listesini olduğu çalıştıran Belge tablosu (RDT), bir belge kilitleme için mantığı sağlayan bayrak değeridir. Bu bayrak, belge açıldığında ve bir belgeyi görünür kullanıcı arabiriminde görünmez bellekte tutulan olup belirler.

Genellikle, kullanacağınız <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> zaman aşağıdakilerden biri doğruysa:

- Bir belgeyi görünmez açmak istediğinizde ve salt okunur ancak değil henüz hangi kurulan <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> sahip.

- Kullanıcı Arabiriminde görüntülenir ve kapatmak çalıştı önce görünmez açılmış bir belgeyi kaydetmek için sizden kullanıcıya istediğinizde.

## <a name="how-to-manage-visible-and-invisible-documents"></a>Görünür ve görünmez belgeleri yönetme

Bir kullanıcı kullanıcı Arabiriminde bir belge açıldığında bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> belge sahibi oluşturulması gerekir ve bir <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> bayrağı ayarlanmış olması gerekir. Öyle değilse <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> sahibi kurulabileceği sonra kullanıcı tıklattığında belge kaydedilmeyecek **Tümünü Kaydet** veya IDE kapatır. Bu belge görünmez burada bellekte değiştirilir ve kullanıcı kapanışında belge kaydetmenizi veya varsa kaydedilmiş açık olup olmadığını anlamına gelir **Tümünü Kaydet** seçilir, ardından bir `RDT_ReadLock` kullanılamaz. Bunun yerine, kullanmanız gereken bir `RDT_EditLock` ve kaydetme bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> zaman bir <xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER> bayrağı.

## <a name="rdteditlock-and-document-modification"></a>RDT_EditLock ve Belge değişikliği

Belge görünmez açılmasını sunacak bahsedilen önceki bayrağı gösterir, `RDT_EditLock` zaman belge açıldığında kullanıcı tarafından görünür **DocumentWindow**. Bu durumda, kullanıcı ile sunulan bir **kaydetmek** ne zaman sor görünür **DocumentWindow** kapalı. `Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel` kullanan uygulamaları <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> hizmet başlangıçta iş yalnızca bir `RDT_ReadLock` (yani, belge görünmez bilgilerini açıldığında) alınır. Belge değiştirilmesi gerekir, daha sonra ardından kilidi için zayıf yükseltilir **RDT_EditLock**. Kullanıcı daha sonra belgeyi görünür durumda açarsa **DocumentWindow**, `CodeModel`'s zayıf `RDT_EditLock` yayımlanır.

Kullanıcı ardından kapatırsa **DocumentWindow** ve seçer **Hayır** açık belgeyi kaydetmek isteyip istemediğiniz sorulduğunda sonra `CodeModel` uygulama belgedeki tüm bilgilerin siler ve açana Daha fazla bilgi ve belge için gerekli görünmez sonraki zaman diskten belgesi. Bu davranış subtlety burada kullanıcının açılır bir örneğidir **DocumentWindow** görünmez açık belgenin değiştirdiği, kapatılır ve ardından seçer **Hayır** belgeyi kaydetmek isteyip istemediğiniz sorulduğunda. Belge varsa, bu durumda, bir `RDT_ReadLock`, ardından belgeyi değil gerçekte kapatılacak ve belgeyi kaydetmesini önlemek kullanıcının seçtiği olsa bile değiştirilen belgeyi görünmez bellekte açık kalır.

Belgenin görünmez açılırken bir zayıf kullanıyorsa `RDT_EditLock`, sonra da kullanıcının belgeyi görünür şekilde açar ve diğer kilitler tutulmaz kendi kilit verir. Kullanıcının kapattığı zaman **DocumentWindow** ve seçer **Hayır** belgeyi kaydetmek isteyip istemediğiniz sorulduğunda sonra belgenin bellekten kapatılması gerekir. Başka bir deyişle, görünmez istemci bu oluşumu izlemek RDT olaylarını dinleyecek gerekir. Belge gereklidir başlattığınızda belgeyi yeniden gerekir.