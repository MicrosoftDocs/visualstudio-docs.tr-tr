---
title: Sembol sağlayıcısı arabirimleri | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- interfaces, symbol handler
- symbol handler, interfaces
- symbol handler, evaluating variables
ms.assetid: 4201f10e-c9f7-4b38-bb45-40fe0082d5bf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 798334058a89199e1e40e023e0b7f46d13c36997
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131307"
---
# <a name="symbol-provider-interfaces"></a>Sembol sağlayıcısı arabirimleri
Sembol işleme arabirimler için şunlardır [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)].  
  
## <a name="discussion"></a>Tartışma  
 Bu arabirimleri sırasında kesme modu çağrı yığını değişkenlerde değerlendirmek için kullanılır. Bunlar yalnızca ortak dil çalışma zamanı simgesi sağlayıcılar için (SP) uygulanır.  
  
|Arabirim|Tarafından uygulanan|Açıklama|  
|---------------|--------------------|-----------------|  
|[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)|SP|Bir öğenin adresini temsil eder.|  
|[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)|SP|İşlem kimliğine erişim sağlayan bir öğe adresini temsil eder|  
|[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)|SP|Bir dizi simge veya dizi türü temsil eder.|  
|[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)|SP|Bir sınıf simge veya sınıf türü temsil eder.|  
|[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)|SP|Yönetilen kod için özel yöntemleriyle bir COM + simgesi sağlayıcısını temsil eder.|  
|[IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)|SP|Yönetilen kod için özel yöntemleriyle bir COM + simgesi sağlayıcısını temsil eder ve genişleten **IDebugComPlusSymbolProvider**.|  
|[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)|SP|Bir simge veya başka bir simge veya türleri için bir kapsayıcı türü temsil eder.|  
|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)|SP|Bir simge eklenebilecek özel bir özniteliği temsil eder.|  
|[IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)|SP|Bir sorgu için bir yöntem veya türü özel öznitelikleri temsil eder.|  
|[IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)|SP|Özel öznitelikler erişim simgesinin üzerine sağlar.|  
|[IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)|SP|Çalışma zamanında belirlenebilir herhangi bir türü için temel arabirim.|  
|[IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)|SP|Dinamik bir alan için temsil eden bir [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) nesnesi.|  
|[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)|SP|Bir numaralandırma türü temsil eder.|  
|[IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)|SP|Yönetilen kod genel türler desteklemek için kullanılabilir alan türlerini genişletir.|  
|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)|SP|Tüm alanlar için temel sınıf; bir simge veya türü açıklamasını temsil eder.|  
|[IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)|SP|Yönetilen kod genel bir tür için bir alan tanımını temsil eder.|  
|[IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)|SP|Yönetilen kod genel bir tür için bir alan örneğini temsil eder.|  
|[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)|SP|Yönetilen kod genel bir tür için bir parametreyi temsil eder.|  
|[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)|SP|Bir yöntemi temsil eder.|  
|[IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)|SP|Hata ayıklama isteğe bağlı değiştiricisi temsil eder.|  
|[IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)|SP|Bir işaretçi temsil eder.|  
|[IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)|SP|Bir basit tür numaralandırma değeri temsil eden bir [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) arabirimi.|  
|[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)|SP|Özellik get olabilir veya ayarlayın bir yönetilen kod sınıfı temsil eder.|  
|[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)|SP|Simgeler ve türleri sağlayan bir simge sağlayıcısını temsil eder.|  
|[IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)|SP|Doğrudan erişimi olan bir simge sağlayıcısı meta verileri ve çekirdek simge arabirimlerine temsil eder.|  
|[IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)|SP|Bir türü temsil eden bir alan oluşturma olanağı temsil eder.|  
|[IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)|SP|Genişletir **IDebugTypeFieldBuilder** dizi türleri oluşturmak için.|  
|[IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)|SP|Bir koleksiyonunu temsil eder [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) nesneleri.|  
|[IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)|SP|Bir koleksiyonunu temsil eder [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) nesneleri.|  
|[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)|SP|Bir koleksiyonunu temsil eder [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) nesneleri.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [API Başvurusu](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)