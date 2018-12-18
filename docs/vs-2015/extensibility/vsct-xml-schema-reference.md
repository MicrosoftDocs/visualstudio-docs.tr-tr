---
title: VSCT XML Şeması Başvurusu | Microsoft Docs
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
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bff3fb766c11987b84ba88b5c86ab3c8d24dbc94
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51755873"
---
# <a name="vsct-xml-schema-reference"></a>VSCT XML Şeması Başvurusu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Komut tablosu derleyici şema öğelerinin bir tablo ile izin verilen alt öğeler ve öznitelikler için her sağlar.  
  
 Bir XML tabanlı komut tablosu (.vsct) yapılandırma dosyası tümleşik geliştirme ortamı (IDE) bir VSPackage sağlayan komut öğeleri tanımlar. Menü öğeleri, menüler, araç çubukları ve birleşik giriş kutuları bu öğeleri içerir.  
  
> [!NOTE]
>  VSCT derleyici bir önişlemci .vsct dosyası üzerinde çalıştırabilirsiniz. Bu genellikle olduğundan C++ önişlemcisi tanımlayabileceğiniz içerir ve makroları, C++ dosyalarında kullanılan aynı söz dizimine sahip. Bu örnekler .vsct sağlanan dosya **yeni proje** sihirbaz VSPackage projesi oluşturur.  
  
## <a name="optional-elements"></a>İsteğe bağlı öğeler  
 Bazı VSCT öğeler isteğe bağlıdır. Varsa bir `Parent` bağımsız değişkeni belirtilmezse, Group_Undefined:0 kapsanan. Varsa bir `Icon` bağımsız değişkeni belirtilmezse, guidOfficeIcon:msotcidNoIcon kapsanan. Bir kısayol tuşu tanımlandığında, genellikle kullanılmaz, öykünme isteğe bağlıdır.  
  
 Bit eşlem öğeleri katıştırılmış derleme zamanında bit eşlem şeridinde konumunu belirterek `href` bağımsız değişken. Bit eşlem Şerit birleştirme sırasında kopyalanan yerine DLL kaynaklarından ayıklanan. Olduğunda bir `href` bağımsız değişkeni sağlanmışsa `usedList` bağımsız değişken isteğe bağlı olur ve tüm yuvalarda bit eşlem Şerit kullanılan olarak kabul edilir.  
  
 Simgesel adlar kullanarak tüm GUID ve ID değerleri tanımlanması gerekir. Bu adlar üstbilgi dosyalarında veya VSCT tanımlanabilir \<sembolleri > bölümler. Simgesel adlar aracılığıyla dahil yerel olmalıdır \<Ekle > öğelerini, veya başvurulan \<Extern > öğeleri. Bir simgesel ad içinde belirtilen bir üstbilgi dosyasından içeri aktarılan bir \<Extern > basit desenini izliyorsa öğesi #define SEMBOL değeri. Bu sembol önceden tanımlanmış olduğu sürece değeri başka bir sembol olabilir. GUID tanımları OLE ya da C++ biçimi izlemelidir. Kimliği değerleri aşağıdaki satırlarda gösterilen ondalık basamak veya 0 x tarafından öncelenen onaltılık basamak olabilir:  
  
- {6D484634-E53D-4a2c-ADCB-55145C9362C8}  
  
- {0x6d484634, 0xe53d 0x4a2c, {0xad, 0xcb, 0x55, 0x14, 0x5c, 0x93, 0x62, 0xc8}}  
  
  XML açıklamaları kullanılabilir, ancak bunları atmak gidiş dönüş grafik kullanıcı arabirimi (GUI) araçları. İçeriğini \<ek açıklama > öğeleri biçim bağımsız olarak korunmasını garanti edilir.  
  
## <a name="schema-hierarchy"></a>Şema hiyerarşisi  
 .Vsct dosyası şu temel öğelere sahiptir.  
  
 [CommandTable Öğesi](../extensibility/commandtable-element.md)  
  
 [Extern Öğesi](../extensibility/extern-element.md)  
  
 [Include Öğesi](../extensibility/include-element.md)  
  
 [Define Öğesi](../extensibility/define-element.md)  
  
 [Commands Öğesi](../extensibility/commands-element.md)  
  
 [CommandPlacements Öğesi](../extensibility/commandplacements-element.md)  
  
 [VisibilityConstraints Öğesi](../extensibility/visibilityconstraints-element.md)  
  
 [KeyBindings Öğesi](../extensibility/keybindings-element.md)  
  
 [UsedCommands Öğesi](../extensibility/usedcommands-element.md)  
  
 [Parent Öğesi](../extensibility/parent-element.md)  
  
 [Icon Öğesi](../extensibility/icon-element.md)  
  
 [Strings Öğesi](../extensibility/strings-element.md)  
  
 [Command Flag Öğesi](../extensibility/command-flag-element.md)  
  
 [Symbols Öğesi](../extensibility/symbols-element.md)  
  
 [Koşullu Öznitelikler](../extensibility/vsct-xml-schema-conditional-attributes.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPackage kullanıcı arabirimi öğelerini nasıl eklenir](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [VSPackage’larda Komut Yönlendirme](../extensibility/internals/command-routing-in-vspackages.md)

