---
title: GUID'leri ve kimlikleri komutları | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1e263678cca7e85993fefd01866352cafc83a74c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53047654"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>Visual Studio Komutlarının GUID’leri ve Kimlikleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio tümleşik geliştirme ortamında (IDE) dahil komutların GUID ve ID değerleri Visual Studio SDK'ın bir parçası olarak yüklenen .vsct dosyaları tanımlanır. Daha fazla bilgi için [IDE-Defined komutlar, menüler ve gruplar](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

 .Vsct dosyaları içinde tanımlanan IDE nesneleri ile çalışma hakkında daha fazla bilgi için bkz. [genişletme menüler ve komutlar](../../extensibility/extending-menus-and-commands.md).

## <a name="finding-a-command-definition"></a>Bir komut tanımı bulma
 Visual Studio bir binden fazla komutları tanımladığından, tüm burada listeleyin zordur. Bunun yerine, bir komut tanımı bulmak için aşağıdaki adımları izleyin.

#### <a name="to-locate-a-command-definition"></a>Bir komut tanımı bulunamadı

1. Aşağıdaki dosyaları Visual Studio'da açın *Visual Studio SDK yükleme yolunu*\VisualStudioIntegration\Common\Inc\ klasör: SharedCmdDef.vsct, ShellCmdDef.vsct, VsDbgCmdUsed.vsct, Venusmenu.vsct.

    Çoğu Visual Studio komutları SharedCmdDef.vsct ve ShellCmdDef.vsct tanımlanır. Hata ayıklayıcıyı ilgilidir komutları VsDbgCmdUsed.vsct tanımlar ve Web geliştirme özgü komutlar Venusmenu.vsct tanımlar.

2. Komut bir menü öğesi ise, menü öğesinin tam metin unutmayın. Araç çubuğu üzerindeki bir düğme komutsa üzerine geldiğinizde görüntülenen araç ipucu metni unutmayın.

3. Açmak için CTRL + F tuşlarına basın **Bul** iletişim kutusu.

4. İçinde **Aranan** 2. adımda not ettiğiniz metin yazın.

5. Doğrulayın **tüm açık belgeleri** görüntülenen **konum** kutusu.

6. Tıklayın **Sonrakini Bul** içinde metin seçilene kadar düğmesini `<Strings>` bölümünü bir [Button öğesi](../../extensibility/button-element.md).

    `<Button>` Komutu görünen öğedir komut tanımı.

   Komut tanımı bulduğunuzda, komutu bir kopyasını başka bir menü veya araç çubuğunda oluşturarak koyabilirsiniz bir [CommandPlacement öğesi](../../extensibility/commandplacement-element.md) aynı olan `guid` ve `id` değerleri komutu. Daha fazla bilgi için [, yeniden kullanılabilir grupları düğmeler oluşturma](../../extensibility/creating-reusable-groups-of-buttons.md).

### <a name="special-cases"></a>Özel durumlar
 Aşağıdaki durumlarda, araç ipucu metnini ve menü metni tam olarak komut tanımında nedir eşleşmiyor olabilir.

-   Gibi bir altı çizili karakter içeren bir menü öğelerini **yazdırma** komutunu **dosya** menüsünde, P çizilir.

     Menü öğesi adları '&' karakteri tarafından öncelenen karakter görüntülenmezse altı çizili olarak. .Vsct dosyaları, özel karakterler belirtmek için '&' karakteri kullanır ve görüntülenecek olan bir ampersan yazılmalıdır olduğunu gerektiren XML ancak yazılır olarak&amp;'. Bu nedenle, bir .vsct dosyası içinde **yazdırma** komutu olarak görünür '&amp;yazdırma '.

-   Dinamik metin sahip komutları **Kaydet** *geçerli dosya*ve dinamik olarak üretilen öğeler gibi menü öğeleri üzerinde **son kullanılan dosyalar** listesi.

     Dinamik metin araması için güvenilir bir yolu yoktur. Bunun yerine, danışmanlık tarafından istenen komut barındıran Grup bulma [GUID'leri ve kimlikleri, Visual Studio menülerinin](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) veya [GUID'leri ve kimlikleri, Visual Studio araç çubuklarının](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)ve arama bu grubun kimliği. Komut tanımı grup olarak yoksa, [üst öğe](../../extensibility/parent-element.md), SharedCmdPlace.vsct ve ShellCmdPlace.vsct (veya hata ayıklayıcı komutları için VsDbgCmdPlace.vsct) arama bir `<CommandPlacement>` ayarlar üst öğesi komutu. SharedCmdPlace.vsct, ShellCmdPlace.vsct, andVsDbgCmdPlace.vsct bulunduğunuz *Visual Studio SDK yükleme yolunu*\VisualStudioIntegration\Common\Inc\ klasör.

## <a name="see-also"></a>Ayrıca Bkz.
 [MenuCommands Vs. OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md) [Visual Studio komut tablosu (. Vsct) dosyaları](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) [VSCT XML Şeması Başvurusu](../../extensibility/vsct-xml-schema-reference.md)
