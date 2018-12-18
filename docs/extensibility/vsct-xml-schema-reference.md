---
title: VSCT XML Şeması Başvurusu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 51be3e86f1f19cc3701dd456b3085d3e8993b7a8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915561"
---
# <a name="vsct-xml-schema-reference"></a>VSCT XML Şeması Başvurusu
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
  
 [CommandTable öğesi](../extensibility/commandtable-element.md)  
  
 [Extern öğesi](../extensibility/extern-element.md)  
  
 [Öğe Ekle](../extensibility/include-element.md)  
  
 [Define öğesi](../extensibility/define-element.md)  
  
 [Commands öğesi](../extensibility/commands-element.md)  
  
 [CommandPlacements öğesi](../extensibility/commandplacements-element.md)  
  
 [VisibilityConstraints öğesi](../extensibility/visibilityconstraints-element.md)  
  
 [KeyBindings öğesi](../extensibility/keybindings-element.md)  
  
 [UsedCommands öğesi](../extensibility/usedcommands-element.md)  
  
 [Üst öğe](../extensibility/parent-element.md)  
  
 [Icon öğesi](../extensibility/icon-element.md)  
  
 [Strings öğesi](../extensibility/strings-element.md)  
  
 [Command Flag öğesi](../extensibility/command-flag-element.md)  
  
 [Symbols öğesi](../extensibility/symbols-element.md)  
  
 [Koşullu öznitelikleri](../extensibility/vsct-xml-schema-conditional-attributes.md)  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [VSPackage kullanıcı arabirimi öğelerini nasıl eklenir](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Vspackage'larda komut yönlendirme](../extensibility/internals/command-routing-in-vspackages.md)