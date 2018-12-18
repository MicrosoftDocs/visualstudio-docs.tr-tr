---
title: GUID'leri ve kimlikleri Visual Studio komutları | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 35e2c354293679d9cb6044b0c5f21b77aadb7f52
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220166"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>GUID'leri ve kimlikleri, Visual Studio komutları
Visual Studio tümleşik geliştirme ortamında (IDE) dahil komutların GUID ve ID değerleri Visual Studio SDK'ın bir parçası olarak yüklenen .vsct dosyaları tanımlanır. Daha fazla bilgi için [IDE tanımlı komutlar, menüler ve gruplar](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
 Tanımlanan IDE nesneler ile çalışma hakkında daha fazla bilgi için *.vsct* dosyaları görmek [genişletmek menüler ve komutlar](../../extensibility/extending-menus-and-commands.md).  
  
## <a name="find-a-command-definition"></a>Bir komut tanımı bulunamadı  
 Visual Studio 1000'den fazla komutları tanımladığından, tüm burada listeleyin zordur. Bunun yerine, bir komut tanımı bulmak için aşağıdaki adımları izleyin.  
  
### <a name="to-locate-a-command-definition"></a>Bir komut tanımı bulunamadı  
  
1. Aşağıdaki dosyaları Visual Studio'da açın *< Visual Studio SDK yükleme yolunu\>\VisualStudioIntegration\Common\Inc\\*  klasör: *SharedCmdDef.vsct*, *ShellCmdDef.vsct*, *VsDbgCmdUsed.vsct*, *Venusmenu.vsct*.  
  
    Çoğu Visual Studio komutları tanımlanan *SharedCmdDef.vsct* ve *ShellCmdDef.vsct*. *VsDbgCmdUsed.vsct* hata ayıklayıcıya, ilgili komutları tanımlar ve *Venusmenu.vsct* Web geliştirmeye özgü komutlar tanımlar.  
  
2. Komut bir menü öğesi ise, menü öğesinin tam metin unutmayın. Araç çubuğu üzerindeki bir düğme komutsa üzerine geldiğinizde görüntülenen araç ipucu metni unutmayın.  
  
3. Tuşuna **Ctrl**+**F** açmak için **Bul** iletişim kutusu.  
  
4. İçinde **Aranan** 2. adımda not ettiğiniz metin yazın.  
  
5. Doğrulayın **tüm açık belgeleri** görüntülenen **konum** kutusu.  
  
6. Tıklayın **Sonrakini Bul** içinde metin seçilene kadar düğmesini `<Strings>` bölümünü bir [Button öğesi](../../extensibility/button-element.md).  
  
    `<Button>` Komutu görünen öğedir komut tanımı.  
  
   Komut tanımı bulduğunuzda, komutu bir kopyasını başka bir menü veya araç çubuğunda oluşturarak koyabilirsiniz bir [CommandPlacement öğesi](../../extensibility/commandplacement-element.md) aynı olan `guid` ve `id` değerleri komutu. Daha fazla bilgi için [yeniden kullanılabilir düğme grupları oluşturma](../../extensibility/creating-reusable-groups-of-buttons.md).  
  
### <a name="special-cases"></a>Özel durumlar  
 Aşağıdaki durumlarda, araç ipucu metnini ve menü metni tam olarak komut tanımında nedir eşleşmiyor olabilir.  
  
-   Gibi bir altı çizili karakter içeren bir menü öğelerini **yazdırma** komutunu **dosya** Burada, menü *P* çizilir.  
  
     Ve işareti tarafından öncelenen karakterleri (&) karakter menü öğesi adları, görüntülenen altı çizili olarak. Ancak, *.vsct* dosyaları, özel karakterler belirtmek için (&) karakteri kullanır ve görüntülenecek ve işareti olarak yazılmalıdır olduğunu gerektiren XML'de yazılır  *&amp;amp;*. Bu nedenle bir *.vsct* dosyası **yazdırma** komut görünür olarak  *&amp;amp; Yazdırma*.  
  
-   Dinamik metin sahip komutları **Kaydet** \<geçerli dosya\>ve dinamik olarak üretilen öğeler gibi menü öğeleri üzerinde **son kullanılan dosyalar** listesi.  
  
     Dinamik metin araması için güvenilir bir yolu yoktur. Bunun yerine, danışmanlık tarafından istenen komut barındıran Grup bulma [GUID'leri ve kimlikleri, Visual Studio menü](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) veya [GUID'leri ve kimlikleri, Visual Studio araç çubukları](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)ve arama bu grubun kimliği. Komut tanımı grup olarak yoksa, [üst öğe](../../extensibility/parent-element.md), arama *SharedCmdPlace.vsct* ve *ShellCmdPlace.vsct* (veya  *VsDbgCmdPlace.vsct* hata ayıklayıcı komutları için) için bir `<CommandPlacement>` ayarlar komutu üst öğesi. *SharedCmdPlace.vsct*, *ShellCmdPlace.vsct*, ve *VsDbgCmdPlace.vsct* bulunan *\<Visual Studio SDK yükleme yolunu\>\ VisualStudioIntegration\Common\Inc\\* klasör.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [MenuCommands vs. OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)   
 [Visual Studio komut tablosu (.vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [VSCT XML Şeması Başvurusu](../../extensibility/vsct-xml-schema-reference.md)
