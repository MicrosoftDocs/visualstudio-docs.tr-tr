---
title: Yardım İçerik Yöneticisi geçersiz kılmaları
ms.date: 11/01/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 95fe6396-276b-4ee5-b03d-faacec42765f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 30953bb5cd41722ff99e37a0820a67aba77f3eef
ms.sourcegitcommit: 75e02ed88a1ace6e8265fd4e3a82a1bc78f3adca
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53378133"
---
# <a name="help-content-manager-overrides"></a>Yardım İçerik Yöneticisi geçersiz kılmaları

Yardım Görüntüleyici ve Yardım güvenlikle ilgili özellikler Visual Studio IDE içindeki varsayılan davranışını değiştirebilirsiniz. Bazı seçenekler oluşturarak belirtilen bir [.pkgdef](https://blogs.msdn.microsoft.com/visualstudio/2009/12/18/whats-a-pkgdef-and-why/) çeşitli kayıt defteri anahtarı değerlerini ayarlamak için dosya. Diğer kayıt defterinde doğrudan ayarlanır.

## <a name="how-to-control-help-viewer-behavior-by-using-a-pkgdef-file"></a>.Pkgdef dosyası kullanarak Yardım Görüntüleyici davranışını denetleme

1. Oluşturma bir *.pkgdef* ilk satırı dosyasıyla `[$RootKey$\Help]`.

2. Kayıt defteri anahtarı değerlerini açıklanan örneğin ayrı satırlarda aşağıdaki tabloda bir bölümünü veya tamamını ekleme `"UseOnlineHelp"=dword:00000001`.

3. Dosyayı kopyalamak *% ProgramFiles (x86) %\Microsoft Visual Studio\2017\\< edition\>\Common7\IDE\CommonExtensions*.

4. Çalıştırma `devenv /updateconfiguration` bir geliştirici komut isteminde.

### <a name="registry-key-values"></a>Kayıt defteri anahtarı değerlerini

|Kayıt defteri anahtarı değeri|Tür|Veri|Açıklama|
|------------------|----|----|-----------|
|NewContentAndUpdateService|dize|\<Hizmet uç noktası için http URL'si\>|Benzersiz bir hizmet uç noktası tanımlama|
|UseOnlineHelp|dword|`0` Yerel Yardım belirtmek için `1` çevrimiçi Yardım belirtmek için|Çevrimiçi veya çevrimdışı Yardım varsayılan tanımlayın|
|OnlineBaseUrl|dize|\<Hizmet uç noktası için http URL'si\>|Benzersiz bir F1 uç noktası tanımlama|
|OnlineHelpPreferenceDisabled|dword|`0` etkinleştirmek için veya `1` çevrimiçi Yardım tercihini seçeneği devre dışı bırakmak için|Çevrimiçi Yardım tercihini seçeneği devre dışı bırak|
|DisableManageContent|dword|`0` etkinleştirmek için veya `1` devre dışı bırakmak için **içeriği Yönet** Yardım Görüntüleyicisi sekmesinde|Devre dışı **içeriği Yönet** sekmesi|
|DisableFirstRunHelpSelection|dword|`0` etkinleştirmek için veya `1` Visual Studio başlayan ilk kez yapılandırılan Yardım özellikleri devre dışı bırakmak için|Visual Studio'nun ilk başlatılması içerik yüklenmesini devre dışı bırak|

### <a name="example-pkgdef-file-contents"></a>Örnek .pkgdef dosyası içeriği

```pkgdef
[$RootKey$\Help]
"NewContentAndUpdateService"="https://some.service.endpoint"
"UseOnlineHelp"=dword:00000001
"OnlineBaseUrl"="https://some.service.endpoint"
"OnlineHelpPreferenceDisabled"=dword:00000000
"DisableManageContent"=dword:00000000
"DisableFirstRunHelpSelection"=dword:00000001
```

## <a name="use-registry-editor-to-change-help-viewer-behavior"></a>Yardım Görüntüleyici davranışını değiştirmek için Kayıt Defteri Düzenleyicisi'ni kullanın

Aşağıdaki iki davranışları, Kayıt Defteri Düzenleyicisi'nde kayıt defteri anahtarı değerlerini ayarlayarak denetlenebilir.

|Görev|Kayıt Defteri Anahtarı|Değer|Veri|
|----------|-----|------|----|
|BITS iş önceliği geçersiz kıl|(Bulunan bir 64-bit machine)\Microsoft\Help\v2.3 HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node|BITSPriority|**ön plan**, **yüksek**, **normal**, veya **düşük**|
|Yerel içerik deposuna ağ paylaşımına işaret|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\ v2.3\Catalogs\VisualStudio15|LocationPath|"*ContentStoreNetworkShare*"|

## <a name="see-also"></a>Ayrıca bkz.

- [Yardım Görüntüleyicisi Yönetici Kılavuzu](../help-viewer/administrator-guide.md)
- [Komut satırı bağımsız değişkenleri için Yardım içeriği Yöneticisi](../help-viewer/command-line-arguments.md)
- [Microsoft Yardım Görüntüleyicisi](../help-viewer/overview.md)