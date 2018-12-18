---
title: Combos öğesi | Microsoft Docs
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
- Combos element (VSCT XML schema)
- VSCT XML schema elements, Combos
ms.assetid: 392e3063-f0a0-4130-9583-23bd2aa3fa36
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0ab350133813f32b87570ea17df50060f93bc300
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51788945"
---
# <a name="combo-element"></a>Combo Öğesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir açılan kutunun içinde görünen komutlar tanımlar. Birleşik giriş kutuları dört tür vardır: aşağı açılan, DynamicCombo IndexCombo ve MRUCombo.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
<combo guid="guidMyCommandSet" id="MyCommand" defaultWidth="20" idCommandList="MyCommandListID" priority="0x102" type="DropDownCombo">  
  <Parent>... </Parent  
  <CommandFlag>... </CommandFlag>  
  <Strings>... </Strings>  
</combo>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|GUID|Gerekli. GUID/ID komut tanımlayıcısı GUİD'si.|  
|kimlik|Gerekli. Kimliği bir GUID/ID komut tanımlayıcısı.|  
|defaultWidth|Gerekli. Birleşik giriş kutusu için bir piksel genişliği belirten bir tamsayı.|  
|idCommandList|Gerekli. Birleşik giriş kutusunda görüntülenecek öğelerin listesini almak için etkin bir komutu kuyruğa hedef gönderilen bir kimliği. Kimlik denetimi ile aynı GUID kapsamda olur.|  
|önceliği|İsteğe bağlı. Bir sayısal değer yönelik önceliği belirtir.|  
|türü|İsteğe bağlı. Düğmenin türü belirten bir numaralandırılmış değeri.<br /><br /> Belirtilmemişse, düğme kullanır.<br /><br /> Aşağı açılan<br /> VSPackage'ı bu birleşik giriş kutusunun içeriğini doldurma için sorumludur. Kullanıcının herhangi bir şey bu açılan metin kutusuna yazamazsınız.<br /><br /> DynamicCombo<br /> VSPackage'ı bu birleşik giriş kutusunun içeriğini doldurmak için sorumludur. Kullanıcı bu birleşik düzenleyebilir ve ayrıca öğeleri seçin.<br /><br /> IndexCombo<br /> BT'nin dışında DynamicCombo aynı metin yerine öğenin dizinini oluşturur.<br /><br /> MRUCombo<br /> VSPackage'ı adına tümleşik geliştirme ortamı (IDE) tarafından doldurulur.  Kullanıcı bu birleşik giriş kutusunda düzenleyebilirsiniz. Son 16 girişleri birleşik giriş kutusu başına en fazla IDE hatırlar.<br /><br /> Kullanıcı bir birleşik giriş kutusunda seçerse ya da yeni bir şeyler girer, IDE uygun VSPackage size bildirir.|  
|Koşul|İsteğe bağlı. Bkz: [koşullu öznitelikler](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|Üst|İsteğe bağlı. Düğmenin üst öğe.|  
|CommandFlag|Gerekli. Bkz: [Command Flag öğesi](../extensibility/command-flag-element.md). Bir düğme için geçerli CommandFlag değerler aşağıdaki gibidir.<br /><br /> -CaseSensitive<br /><br /> -CommandWellOnly<br /><br /> -DefaultDisabled<br /><br /> -DefaultInvisible<br /><br /> -DynamicVisibility<br /><br /> -Süzme<br /><br /> -IconAndText<br /><br /> -NoAutoComplete<br /><br /> -NoButtonCustomize<br /><br /> -NoCustomize<br /><br /> -NoKeyCustomize<br /><br /> -StretchHorizontally|  
|Dizeler|Gerekli. Bkz: [dizeleri öğesi](../extensibility/strings-element.md). Alt ButtonText öğesi tanımlanmalıdır.|  
|Ek Açıklama|İsteğe bağlı bir açıklama.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[Commands Öğesi](../extensibility/commands-element.md)|VSPackage araç çubuğundaki komutları koleksiyonunu temsil eder.|  
  
## <a name="example"></a>Örnek  
  
```  
<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"  
  defaultWidth="100" idCommandList="cmdidGetInsertOptionsList">  
  <CommandFlag>DynamicVisibility</CommandFlag>  
  <Strings>  
    <ButtonText>Select Insert Options</ButtonText>  
  </Strings>  
</Combo>  
  
<Combo guid="guidWidgetPackage" id="cmdidInsertOptions"  
  priority="0x0500" type="DropDownCombo" defaultWidth="100"  
  idCommandList="cmdidGetInsertOptionsList">  
  <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit">  
  <CommandFlag>DynamicVisibility</CommandFlag>  
  <Strings>  
    <ButtonText>Select Insert Options</ButtonText>  
  </Strings>  
</Combo>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

