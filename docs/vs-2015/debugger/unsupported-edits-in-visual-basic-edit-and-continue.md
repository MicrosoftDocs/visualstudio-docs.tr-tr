---
title: Visual Basic'de desteklenmeyen düzenlemeler Düzenle ve devam et | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
helpviewer_keywords:
- Edit and Continue [Visual Basic], unsupported method and property body edits
ms.assetid: 9b8fdc41-a193-49ad-ad72-dfcadd46f4b3
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bc6e7a5d1d72464849bff20be066ea70e8264623
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51787906"
---
# <a name="unsupported-edits-in-visual-basic-edit-and-continue"></a>Visual Basic Düzenle ve Devam Et'de Desteklenmeyen Düzenlemeler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Düzenle ve kesme modunda programın yürütülmesini durdurur, kod için değişiklik ve yeni eklenen değişikliklerle program sürdürebilir les devam edin. Genel bir sınıf yapısını etkileyen bildirim temelli kod düzenleme genel olarak yasaklanmış olmasına karşın bir yöntem, özellik gövdesi veya özel bir sınıf bildirimlerinde yapabileceğiniz birçok düzenlemelere izin.  
  
 Desteklenmeyen bir değişiklik yapmanız gerekirse, hata ayıklamayı durdurmak, değişiklikleri yapın ve yeni bir hata ayıklama oturumu başlatın.  
  
###  <a name="BKMK_MethodandPropertyBodyEdits"></a> Yöntem ve özellik gövdesi düzenlemeleri  
 **Desteklenmeyen statik yerel değişkenler değişiklikleri**: ekleme veya bir yerel değişken güncelleştirmek veya statik bir yerel değişken, bir derleme hatasına neden olacaksa kaldırılıyor.  
  
 **Desteklenmeyen genel türlere değişiklikleri**: genel yöntem kendisini veya genel yöntemin gövdesi değişiklikleri desteklenmez. Genel bir tür veya varolan genel yöntemlere yapılan çağrılar örneğinin eklenen, değiştirilen veya silinebilir.  
  
 **Desteklenmeyen diğer değişiklikler**  
  
-   Çağrı yığınındaki bir yöntemi çağırma deyiminin değiştiriliyor.  
  
-   Ekleme bir `Try...Catch` bloğu içinde yönerge işaretçisi sona erdiğinde `Catch` blok veya `Finally` blok.  
  
-   Kaldırma bir `Try...Catch` yönerge işaretçisi olduğunda blok bir `Catch`blok veya `Finally` blok.  
  
-   Ekleme bir `Using` dosyadaki geçerli yönerge işaretçisini etrafında blok.  
  
-   Ekleme bir `SynchLock` dosyadaki geçerli yönerge işaretçisini etrafında blok.  
  
###  <a name="BKMK_AttributeEdits"></a> Özniteliği düzenleme  
 Düzenle ve devam et, değiştirme öznitelikleri desteklemiyor. Özellikle, Düzenle ve devam et aşağıdaki değişiklikleri desteklemez:  
  
-   Tanımlama, düzenleme veya silme öznitelik sınıfı.  
  
-   Bir öznitelik ekleme.  
  
-   Düzenleme veya varolan bir özniteliği kaldırılıyor.  
  
###  <a name="BKMK_ClassDeclarationEdits"></a> Sınıf bildirimi düzenleme  
 Değişikliklerin çoğu sınıf bildirimleri için Düzenle ve devam et kesme modunda tarafından izin verilmiyor. Özellikle, Düzenle ve devam et aşağıdaki değişiklikleri desteklemez:  
  
-   Yeniden adlandırma, silme veya mevcut bir sınıfın devralmayı değiştirme.  
  
-   Yeni bir arabirimi uygulayan veya bir arabirim uygulaması kaldırılıyor.  
  
-   Bir sınıf üzerindeki değiştiriciler değiştiriliyor.  
  
-   Ekleme, değiştirme veya kaldırma `ComClass` durumu.  
  
-   Herhangi bir genel sınıf bildirimine düzenleme.  
  
###  <a name="BKMK_ClassMemberDeclarationEdits"></a> Sınıf üyesi bildirim düzenlemeler  
 Üye bildirimleri değişiklikler, çoğu Düzen yasaktır ve çalışmaları devam edin. Örneğin, imza değiştirilemiyor veya, bir derleme hatasına neden olacaksa bir üye ve erişim düzeyine tamamen üyeler kaldırılamıyor. Özellikle, Düzenle ve devam et aşağıdaki değişiklikleri desteklemez:  
  
-   Bir genel bildirmek varolan bir üye değişkeni veya üye değişkeni kapsayan bir blok içinde aynı ada sahip gölgeleme.  
  
-   Statik bir yerel değişken bir bloğu içinde yeni bir örneğini bildirerek gölgeleme.  
  
-   Olay işleyicileri kaldırılıyor. Olay işleyici ekleme izin verilir.  
  
-   Yeni aşırı yüklerken özellik veya yöntem, özellik veya yöntem olmadığı sürece ekleme `Private` ve etkin bir deyim adı örneği vardır.  
  
-   Ekleme veya kaldırma `WithEvents` bir üye değişkeni yan tümcesi.  
  
-   Üye siliniyor.  
  
-   Arabirimi uygulama durdurmak için bir özellik veya yöntem bildiriminde değiştiriliyor.  
  
-   Genel türler kullanan herhangi bir yöntemi düzenleme.  
  
-   Özel olmayan özellik veya yöntem imzası veya dönüş türünü değiştirme.  
  
-   Geçersiz kılma ya da bir temel sınıf üye gölgeleme.  
  
-   İle işaretlenen herhangi bir sınıfın yeni alan ekleme `SequentialLayout` veya `ExplicitLayout`.  
  
-   Değiştirme `MustInherit` veya `NotOverridable` bir yöntemin durumunu.  
  
-   Bir özellik veya yöntemin erişim değiştiricileri değiştiriliyor.  
  
-   Türe veya bir alanı salt okunur durumunu değiştirme.  
  
-   Ortak alan değiştiriliyor.  
  
###  <a name="BKMK_CompilerOptionEdits"></a> Derleyici seçeneği düzenlemeleri  
 Düzenle ve devam et kesme modunda kullanırken, değiştirme, ekleyemez veya aşağıdaki derleyici seçeneklerinin kaldırın:  
  
-   **Katı tanımlama seçeneği**  
  
-   **Seçeneği açık**  
  
-   **Karşılaştırma seçeneği**  
  
###  <a name="BKMK_ConstantsEdits"></a> Sabitler düzenlemeler  
 Düzenle ve devam et modundayken sabitleri değişiklikler çok sınırlıdır. Özellikle, Düzenle ve devam et aşağıdaki değişiklikleri desteklemez:  
  
-   Ekleme veya sabit bir değişken güncelleştiriliyor.  
  
-   Türe veya bir sabit değerini değiştirme.  
  
-   Bir sabit kaldırılıyor.  
  
###  <a name="BKMK_DelegateandEventDeclarationEdits"></a> Temsilci ve olay bildirimi düzenleme  
 Temsilciler ve olaylar için bazı değişiklikler Düzenle ve devam et ile kesme modunda izin verilmez. Özellikle, Düzenle ve devam et aşağıdaki değişiklikleri desteklemez:  
  
-   Değiştirme veya temsilci tanımı siliniyor.  
  
-   Bir olay siliniyor.  
  
###  <a name="BKMK_EnumerationEdits"></a> Sabit listesi düzenlemeler  
 Sabit listeleri için değişiklikleri (`Enums`) Düzenle ve devam et ile kesme modunda izin verilmez. Özellikle, Düzenle ve devam et aşağıdaki değişiklikleri desteklemez:  
  
-   Altındaki değiştirme türü bir `Enum`.  
  
-   Ekleyerek, değiştirerek veya kaldırarak bir `Enum` üyesi.  
  
-   Erişim değiştiricisi değiştirerek bir `Enum`.  
  
###  <a name="BKMK_ExternalDeclarationsEdits"></a> Dış bildirimler düzenlemeler  
 Genel olarak, Düzenle ve devam et sırasında dış yöntemleri bildirimlerini değiştiremezsiniz. Özellikle, Düzenle ve devam et aşağıdaki değişiklikleri desteklemez:  
  
-   Ekleme veya bir dış bildirimi kaldırılıyor.  
  
-   İmza değiştirmeyi veya bir dış bildiriminin öznitelikleri hazırlama.  
  
###  <a name="BKMK_ImportsEdits"></a> İçeri aktarmaları düzenleme  
 Düzenle ve devam et izin vermiyor ekleyerek, değiştirerek veya kaldırarak `Imports` kesme modundayken deyimleri.  
  
###  <a name="BKMK_InterfaceDefinitionEdits"></a> Arabirim tanımı düzenleme  
 Sık sık değişiklik arabirimleri uygulayan üyeleri için izin verilir ancak gerçek bir arabirim tanımları değişiklikleri genel olarak Düzenle ve devam et tarafından izin verilmez. Özellikle, Düzenle ve devam et aşağıdaki değişiklikleri desteklemez:  
  
-   Ekleme, değiştirme veya arabirim üyeleri kaldırılıyor.  
  
-   Varolan arabirimi siliniyor.  
  
-   Bir arabirimin erişim değiştiricisi değiştiriliyor.  
  
-   Arabirimi Devralma Hiyerarşisi değiştiriliyor.  
  
###  <a name="BKMK_ModuleDeclarationEdits"></a> Modül bildirimi düzenleme  
 Modül bildirimlerinde yapılan değişikliklerin çoğu Düzenle ve devam et kesme modunda tarafından izin verilmiyor. Özellikle, Düzenle ve devam et aşağıdaki değişiklikleri desteklemez:  
  
-   Yeni modül oluşturuluyor.  
  
-   Yeniden adlandırma veya mevcut bir modül siliniyor.  
  
-   Bir modüle ait erişim değiştiricisinin değiştiriliyor.  
  
###  <a name="BKMK_ModuleMemberDeclarationEdits"></a> Modül üye bildirimi düzenleme  
 Düzenle ve devam et kullanarak, özellikleri, yöntemleri ve kesme modundayken alanları gibi modülü üyeleri değişiklikleri çeşitli yapabilirsiniz. Ancak, bazı değişiklikler desteklenmez. En önemlisi, Düzenle ve devam et, ekleme, silme veya türü veya herhangi bir üye imzası değiştirmeyi desteklemez.  
  
 Özellikle, Düzenle ve devam et aşağıdaki değişiklikleri desteklemez:  
  
-   Etkin bir deyim adı örneği olmadığı sürece, yeni bir üye ekleniyor.  
  
-   Bir özellik veya yöntem kaldırılıyor.  
  
-   Bir özellik veya yöntem imzasının değiştirilmesi.  
  
-   Ekleme, yeniden adlandırma, taşıma veya bir alan siliniyor.  
  
-   Genel türler kullanan herhangi bir yöntemi düzenleme.  
  
-   Bir özellik veya yöntemin erişim değiştiricileri değiştirme, örneğin, değiştirme `Public` için `Private`.  
  
-   Silme veya varolan bir alanın türünü değiştirme.  
  
###  <a name="BKMK_NestedTypeDeclarationEdits"></a> İç içe geçmiş tür bildirimi düzenleme  
 Düzenle ve devam et desteklemiyor iç içe türü başka bir ad alanı veya tür taşıma.  
  
###  <a name="BKMK_StructureDeclarationEdits"></a> Yapı bildirimi düzenleme  
 Yapı bildirimleri yapılan değişikliklerin çoğu Düzenle ve devam ederken'tarafından izin verilmeyen **sonu** modu. Özellikle, Düzenle ve devam et aşağıdaki değişiklikleri desteklemez:  
  
-   Yeniden adlandırma veya varolan bir yapısını siliniyor.  
  
-   Yeni bir arabirimi uygulayan veya bir arabirim uygulaması kaldırılıyor.  
  
-   Bir yapı için erişim değiştiricisini değiştiriliyor.  
  
###  <a name="BKMK_StructureMemberDeclarationEdits"></a> Yapı üyesi bildirimi düzenleme  
 Düzenle ve devam et kullanarak yapı üyeleri (özellikleri, yöntemleri ve alanları) sırasında kesme modunda değişiklikleri çeşitli yapabilirsiniz. Bazı değişiklikler ancak desteklenmez, özellikle bildirimi etkileyen değişiklikler yapı üyelerini. Özellikle, Düzenle ve devam et aşağıdaki değişiklikleri desteklemez:  
  
-   Bir özellik veya yöntem kaldırılıyor.  
  
-   Ekleme veya bir alan kaldırma.  
  
-   Bir özellik veya yöntem imzasının değiştirilmesi.  
  
-   Genel türler kullanan herhangi bir yöntemi düzenleme.  
  
-   Bir özellik veya yöntem bildiriminde bir arabirimi uygulayan olup olmadığını değiştiriliyor.  
  
-   Bir özellik veya yöntemin erişim değiştiricileri değiştirme (örneğin, değiştirme `Public` için **özel**).  
  
-   Bir alanı kaldırılıyor.  
  
-   Bir alanın türünü değiştirme.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Düzen ile kesme modunda düzenlemeleri uygulayın ve devam et](../debugger/how-to-apply-edits-in-break-mode-with-edit-and-continue.md)   
 [Düzenle ve Devam Et (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)



