---
title: IActiveScript::AddNamedItem | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.AddNamedItem
apilocation:
- scrobj.dll
helpviewer_keywords:
- AddNamedItem method, IActiveScript interface
ms.assetid: a7c6317d-948f-4bb3-b169-1bbe5b7c7cc5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: db65361e4bde14e803d9085a4530a505ccaf9fcb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24792137"
---
# <a name="iactivescriptaddnameditem"></a>IActiveScript::AddNamedItem
Komut dosyası altyapısı ad alanı için bir kök düzeyinde öğesinin adını ekler. Kök düzeyinde bir nesne özellikleri ve yöntemleri, bir olay kaynağı veya üçünü öğesidir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT AddNamedItem(  
    LPCOLESTR pstrName,  // address of item name  
    DWORD dwFlags          // item flags  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pstrName`  
 [in] Komut dosyasını görüntülendiği şekilde öğesinin adını içeren bir arabellek adresi. Adın benzersiz ve kalıcı olması gerekir.  
  
 `dwFlags`  
 [in] Bir öğesiyle ilişkili bayraklar. Bu değerleri bir bileşimi olabilir:  
  
|Değer|Açıklama|  
|-----------|-------------|  
|SCRIPTITEM_CODEONLY|Adlandırılmış öğe yalnızca kod bir nesneyi temsil eder ve ana bilgisayar yok olduğunu gösterir `IUnknown` bu yalnızca kod nesne ile ilişkili olmalıdır. Konak, yalnızca bu nesne için bir adı vardır. Nesne odaklı dillerde C++ gibi bu bayrak bir sınıf oluşturursunuz. Bu bayrak tüm diller desteklemez.|  
|SCRIPTITEM_GLOBALMEMBERS|Öğe koleksiyonunu genel özellikleri ve yöntemleri komut dosyası ile ilişkili olduğunu gösterir. Normalde, bir komut dosyası motoru nesne adını yoksay (dışında bir tanımlama bilgisi olarak kullanma amacıyla [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) yöntemi veya açık kapsamı çözmek için) ve üyelerine genel olarak kullanıma sunma değişkenleri ve yöntemleri. Bu kitaplık (çalışma zamanı işlevleri vb.) için betik kullanılabilir genişletmek için ana sağlar. Adı ile mücadele etmek için komut dosyası altyapısı sol (örneğin, iki SCRIPTITEM_GLOBALMEMBERS öğeleri yöntemlerine aynı ada sahip olduğunda) bir hata nedeniyle bu durum döndürülmemesi gereken olsa da, çakışıyor.|  
|SCRIPTITEM_ISPERSISTENT|Komut dosyası altyapısı kaydettiyseniz öğesi kaydedilmesi gerektiğini gösterir. Benzer şekilde, bu bayrağı ayarlama gösterir Başlatıldı durumuna geçiş öğenin adı ve türü bilgileri (komut dosyası altyapısı gerekir ancak sürüm gerçek nesne arabirimlerde tüm işaretçiler) korurlar.|  
|SCRIPTITEM_ISSOURCE|Öğesi komut dosyası havuzu olayları kaynakları gösterir. Bağımlı nesneler (kendileri nesneleri özellikler nesnesinin) de olayları komut dosyası için kaynak olarak alabilir. Bu özyinelemeli değildir, ancak genel olarak için kullanışlı bir mekanizma Örneğin, bir kapsayıcı ve tüm üye denetimleri oluşturmayı sağlar.|  
|SCRIPTITEM_ISVISIBLE|Öğenin adını ad alanı özellikleri, yöntemleri ve olayları öğenin izin veren komut dosyasının kullanılabilir olduğunu gösterir. Kurala göre öğenin alt öğeleri öğenin özelliklerini içerir; Bu nedenle, tüm alt nesne özellikleri ve yöntemleri (ve bunların alt öğeleri, yinelemeli olarak) erişilebilir olacaktır.|  
|SCRIPTITEM_NOCODE|Öğe yalnızca komut dosyanızın ad alanı için eklenmekte olan bir ad ve kod ilişkili olacağı bir öğe değerlendirilmeyen gösterir. Örneğin, bu bayrağı ayarlanmış olmadan VBScript adlandırılmış öğesi için ayrı bir modül oluşturur ve C++ adlandırılmış öğesi için ayrı sarmalayıcı sınıfı oluşturabilirsiniz.|  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|Dönüş Değeri|Açıklama|  
|------------------|-------------|  
|`S_OK`|Başarılı.|  
|`E_INVALIDARG`|Bağımsız değişken geçersiz.|  
|`E_POINTER`|Geçersiz bir işaretçi belirtildi.|  
|`E_UNEXPECTED`|Çağrı beklendiği (örneğin, komut dosyası altyapısı henüz yüklenen başlatılmadı veya).|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IActiveScript](../../winscript/reference/iactivescript.md)