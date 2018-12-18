---
title: Sembol sağlayıcısı arabirimleri | Microsoft Docs
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
- interfaces, symbol handler
- symbol handler, interfaces
- symbol handler, evaluating variables
ms.assetid: 4201f10e-c9f7-4b38-bb45-40fe0082d5bf
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a37e27f6d7d1a9435f9519d3cecf359eb65fe204
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51790779"
---
# <a name="symbol-provider-interfaces"></a>Sembol Sağlayıcısı Arabirimleri
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Sembol işleme arabirimleri için verilmiştir [!INCLUDE[vsipsdk](../../../includes/vsipsdk-md.md)].  
  
## <a name="discussion"></a>Tartışma  
 Bu arabirimler, kesme modu sırasında çağrı yığınını değişkenleri değerlendirmek için kullanılır. Bunlar yalnızca ortak dil çalışma zamanı sembol sağlayıcıları için (SP) uygulanır.  
  
|Arabirim|Uygulayan|Açıklama|  
|---------------|--------------------|-----------------|  
|[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)|SP|Bir öğenin adresi temsil eder.|  
|[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)|SP|İşlem kimliğine erişim sağlayan, bir öğenin adresi temsil eder|  
|[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)|SP|Bir dizi simge ya da dizi türü temsil eder.|  
|[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)|SP|Bir sınıf sembol veya sınıf türü temsil eder.|  
|[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)|SP|Yönetilen kod için özel yöntemler ile bir COM + simgesi sağlayıcısını temsil eder.|  
|[IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)|SP|Yönetilen kod için özel yöntemler ile bir COM + simgesi sağlayıcısını temsil eder ve genişleten **IDebugComPlusSymbolProvider**.|  
|[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)|SP|Sembolü veya diğer semboller veya türler için bir kapsayıcı türü temsil eder.|  
|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)|SP|Bir simgeye bağlı özel bir özniteliği temsil eder.|  
|[IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)|SP|Bir sorgu için bir yöntem veya türü özel öznitelikleri temsil eder.|  
|[IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)|SP|Özel özniteliklere erişim üzerinde bir sembol sağlar.|  
|[IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)|SP|Çalışma zamanında belirlenebilir herhangi bir türü için temel arabirim.|  
|[IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)|SP|Dinamik bir alan için temsil eden bir [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) nesne.|  
|[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)|SP|Bir numaralandırma türü temsil eder.|  
|[IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)|SP|Yönetilen kod genel türleri desteklemek için kullanılabilir alan türlerini genişletir.|  
|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)|SP|Tüm alanlar için temel sınıf; sembolü veya tür açıklamasını temsil eder.|  
|[IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)|SP|Yönetilen kod genel bir tür için bir alan tanımını temsil eder.|  
|[IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)|SP|Yönetilen kod genel bir tür için bir alan örneğini temsil eder.|  
|[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)|SP|Yönetilen kod genel bir tür için bir parametreyi temsil eder.|  
|[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)|SP|Bir yöntemi temsil eder.|  
|[IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)|SP|Hata ayıklama isteğe bağlı bir değiştirici temsil eder.|  
|[IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)|SP|Bir işaretçiyi temsil eder.|  
|[IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)|SP|Bir basit tür sabit listesi değeri temsil eden bir [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) arabirimi.|  
|[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)|SP|Get veya ayarlanmış bir yönetilen kod sınıfının bir özelliği temsil eder.|  
|[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)|SP|Sembollere ve türlere sağlayan bir sembol sağlayıcısını temsil eder.|  
|[IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)|SP|Doğrudan erişimli bir sembol sağlayıcısı meta verileri ve çekirdek sembol arabirimleri temsil eder.|  
|[IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)|SP|Türünü temsil eden bir alan oluşturma özelliği temsil eder.|  
|[IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)|SP|Genişletir **IDebugTypeFieldBuilder** dizi türleri oluşturabilmek için.|  
|[IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)|SP|Bir koleksiyonunu temsil eder [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) nesneleri.|  
|[IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)|SP|Bir koleksiyonunu temsil eder [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) nesneleri.|  
|[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)|SP|Bir koleksiyonunu temsil eder [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) nesneleri.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [API Başvurusu](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)

