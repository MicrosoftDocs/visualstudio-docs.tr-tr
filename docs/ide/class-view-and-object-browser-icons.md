---
title: Sınıf Görünümü ve Nesne Tarayıcısı Simgeleri
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- icons, in Object Browser
- signal icons
- Class View tool, symbols
- graphic symbols
- IntelliSense, icons
- icons, IntelliSense
- symbols, Object Browser icons
- Object Browser, icons in Class View
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6ff94e67291bff8dc00d3fa63976f283da485f6a
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34745795"
---
# <a name="class-view-and-object-browser-icons"></a>Sınıf Görünümü ve Nesne Tarayıcısı simgeleri

**Sınıf Görünümü** ve **Nesne Tarayıcısı** kodu varlıkları, örneğin temsil eden simgeleri, ad alanları, sınıflar, işlevleri ve değişkenler görüntüler. Aşağıdaki tabloda gösterilmiştir ve simgeleri açıklar.

|Simge|Açıklama|Simge|Açıklama|
|----------|-----------------|----------|-----------------|
|![Namespace simgesi](../ide/media/vxnamespace_icon.gif)|Ad Alanı|![Bildirim simgesi](../ide/media/vxmethod_icon.gif)|Yöntem veya işlevi|
|![Sınıf simgesi](../ide/media/vxclass_icon.gif)|örneği|![İşleç simgesi](../ide/media/vxoperator_icon.gif)|İşleç|
|![Lolipop arabirimi sembolü](../ide/media/vxinterface_icon.gif)|Arabirim|![Özellik simgesi](../ide/media/vxproperty_icon.gif)|Özellik|
|![Yapı simgesi](../ide/media/vxstruct_icon.gif)|Yapı|![Alan simgesi](../ide/media/vxfield_icon.gif)|Alan veya değişken|
|![Birleşim simgesi](../ide/media/vxunion_icon.gif)|UNION|![Olay simgesi](../ide/media/vxevent_icon.gif)|Olay|
|![Numaralandırma simgesi](../ide/media/vxenum_icon.gif)|Enum|![Sabit simgesi](../ide/media/vxconstant_icon.gif)|Sabit|
|![Tür tanımı simgesi](../ide/media/vxtypedef_icon.gif)|TypeDef|![Öğe numaralandırma sembolü](../ide/media/vxenumitem_icon.gif)|Enum öğesi|
|![Visual Studio modülü simgesi](../ide/media/vxmodule_icon.gif)|Modül|![Harita öğesi simgesi](../ide/media/vxmapitem_icon.gif)|Harita öğesi|
|![Uzantı yöntemi simgesi](../ide/media/extensionmethod.gif)|Genişletme yöntemi|![Bildirim simgesi](../ide/media/vxmethod_icon.gif)|Dış bildirimi|
|![Temsilci sembolü](../ide/media/vxdelegate_icon.gif)|Temsilci|![Sınıf Görünümü ve nesne tarayıcısı için hata simgesi](../ide/media/erroricon.gif)|Hata|
|![Özel durum simgesi](../ide/media/vxexception_icon.gif)|Özel Durum|![Şablon simgesi](../ide/media/vxtemplate_icon.gif)|Şablon|
|![Eşleme Sembolü](../ide/media/vxmap_icon.gif)|eşleme|![Hata ünlem işareti sembolü](../ide/media/vxerror_icon.gif)|Bilinmiyor|
|![Tür iletme simgesi](../ide/media/ob_type_forward.gif)|Tür iletme|||

## <a name="signal-icons"></a>Sinyal simgeleri

Aşağıdaki sinyal simgeleri tüm önceki simgeleri uygulamak ve kendi erişilebilirlik gösterir.

|Simge|Açıklama|
|----------|-----------------|
|\<Sinyal simge yok >|Ortak. Erişilebilen herhangi bir yerden bu bileşeni ve başvurduğu herhangi bir bileşeni.|
|![Sembol sinyal korumalı](../ide/media/vxsignal_icon_key.gif)|Korumalı. Kapsayan sınıfı veya türü veya bunları içeren sınıf ya da türü türetilen erişilebilir.|
|![Sinyal özel simge](../ide/media/vxsignal_icon_lock.gif)|Özel. Yalnızca içeren sınıf ya da türü erişilebilir.|
|![Sembol korumalı sinyali](../ide/media/vxsignal_icon_envelope.gif)|Korumalı.|
|![Sinyal arkadaş&#47;iç simgesi](../ide/media/vxsignal_icon_diamond.gif)|Arkadaş/iç hata. Yalnızca proje erişilebilir.|
|![Sinyal simgesi oku](../ide/media/vxsignal_icon_arrow.gif)|Kısayol. Nesne için bir kısayol.|

> [!NOTE]
> Projenizi bir kaynak denetimi veritabanında varsa, ek sinyal simgeleri kaynak denetimi durumu göstermek için görüntülenen, gibi iade veya olabilir kullanıma alınmış.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod yapısını görüntüleme](../ide/viewing-the-structure-of-code.md)