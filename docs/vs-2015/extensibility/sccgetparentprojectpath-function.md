---
title: SccGetParentProjectPath işlevi | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccGetParentProjectPath
helpviewer_keywords:
- SccGetParentProjectPath function
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0e75c3e39f2d4f56d40ca546291b2f86bd185f88
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51744416"
---
# <a name="sccgetparentprojectpath-function"></a>SccGetParentProjectPath İşlevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu işlev, belirtilen bir projenin ana proje yolu belirler. Kullanıcı bir Visual Studio projesi kaynak denetimine eklerken, bu işlev çağrılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp#  
SCCRTN SccGetParentProjectPath(  
   LPVOID pContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPCSTR lpProjPath,  
   LPSTR  lpAuxProjPath,  
   LPSTR  lpParentProjPath  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 pContext  
 [in] Kaynak Denetimi Eklentisi bağlam işaretçisi.  
  
 hWnd  
 [in] Kaynak Denetimi Eklentisi sağladığı herhangi bir iletişim kutusu için bir üst öğe olarak kullanabileceğiniz IDE penceresi için bir tanıtıcı.  
  
 lpUser  
 [out içinde] Kullanıcı adı (en fazla SCC_USER_SIZE, NULL sonlandırıcıyı da dahil olmak üzere).  
  
 lpProjPath  
 [in] Proje yolu (en fazla SCC_PRJPATH_SIZE, NULL sonlandırıcıyı da dahil olmak üzere) tanımlayan dize.  
  
 lpAuxProjPath  
 [out içinde] Proje (en fazla SCC_PRJPATH_SIZE, NULL sonlandırıcıyı da dahil olmak üzere) tanımlayan yardımcı dize.  
  
 lpParentProjPath  
 [out içinde] Ana proje yolu (en fazla SCC_PRJPATH_SIZE, NULL sonlandırıcıyı da dahil olmak üzere) tanımlayan çıkış dizesi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Kaynak Denetimi Eklentisi uygulanması bu işlev, aşağıdaki değerlerden birini döndürmesi beklenir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|SCC_OK|Ana proje yolu başarıyla alındı.|  
|SCC_E_INITIALIZEFAILED|Proje başlatılamadı.|  
|SCC_E_INVALIDUSER|Kullanıcının kaynak denetimi eklentisi için oturum açılamadı.|  
|SCC_E_UNKNOWNPROJECT|Proje Kaynak Denetimi Eklentisi bilinmiyor.|  
|SCC_E_INVALIDFILEPATH|Dosya geçersiz veya kullanılamaz durumda yolu.|  
|SCC_E_NOTAUTHORIZED|Kullanıcı bu işlemi gerçekleştirmek için izin verilmiyor.|  
|SCC_E_ACCESSFAILURE|Kaynak denetim sistemi, ağ veya çakışma sorunları nedeniyle muhtemelen erişilirken sorun oluştu. Bir yeniden deneme önerilir.|  
|SCC_E_PROJSYNTAXERR|Geçersiz proje söz dizimi.|  
|SCC_E_CONNECTIONFAILURE|Store bağlantısı sorunu.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Belirli olmayan hata oluştu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu işlev başarı veya hata kodunu döndürür ve başarılı olursa, değişken doldurur `lpParentProjPath` belirtilen projeyi tam proje yoluyla.  
  
 Bu işlev, ana proje yolu mevcut bir projeyi döndürür. Kök proje için işlev, geçirilen proje yolu döndürür (diğer bir deyişle, aynı kök proje yolu). Proje yolu yalnızca kaynak denetimi eklentisi anlamlı bir dize olduğunu unutmayın.  
  
 IDE değişiklikleri kabul etmek için hazırlanmış `lpUser` ve `lpAuxProjPath` de parametreleri. IDE bu dizeler kalıcı hale getirmek ve bunlara geçirmek [SccOpenProject](../extensibility/sccopenproject-function.md) kullanıcı açtığında bu proje gelecekte. Bu dizeler, bu nedenle, kaynak denetimi eklentisi projesi ile ilişkilendirmek için gereken izleme bilgileri için bir yol sağlar.  
  
 Bu işlev benzer [SccGetProjPath](../extensibility/sccgetprojpath-function.md), bir proje seçmek için kullanıcı sormaz hariç aynıdırlar. Ayrıca, hiçbir zaman yalnızca var olan bir projeyle çalışır ancak yeni bir proje oluşturur.  
  
 Zaman `SccGetParentProjectPath` çağrıldığında `lpProjPath` ve `lpAuxProjPath` boş olmaz ve geçerli bir projeye karşılık gelir. Bu dizeler genellikle önceki bir çağrı IDE'den tarafından alınan `SccGetProjPath` işlevi.  
  
 `lpUser` Bağımsız değişken ise kullanıcı adı. IDE, daha önce gelen almış aynı kullanıcı adı geçer `SccGetProjPath` işlevi ve kaynak denetimi eklentisi kullanması gereken adı varsayılan olarak. Kullanıcı eklenti ile açık bir bağlantı zaten varsa, ardından eklentiyi işlevi sessiz bir şekilde çalıştığından emin olmak için herhangi bir istemi ortadan kaldırmak denemelisiniz. Oturum açma başarısız olursa, ancak, eklenti için bir oturum açma ve kullanıcı, geçerli bir oturum adı yeniden geçişi aldığında isteyecektir `lpUser`. Bu dize eklenti değişebilir olduğundan, IDE her zaman bir arabellek boyutunu tahsis (`SCC_USER_LEN`+ 1). Dize değiştirilirse, yeni bir dize (eski dize olarak en az geçerli olarak) bir geçerli oturum açma adı olmalıdır.  
  
## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>SccCreateSubProject ve SccGetParentProjectPath teknik notlar  
 Kaynak denetim sistemi konumları seçmek için bir kullanıcıdan sayısını en aza indirmek için Visual Studio'da çözümler ve projeler kaynak denetimine eklemeye basitleştirilmiştir. Yeni İşlevler, her ikisi de kaynak denetimi eklentisi destekliyorsa, bu değişikliklerin Visual Studio tarafından etkinleştirilen [SccCreateSubProject](../extensibility/scccreatesubproject-function.md) ve `SccGetParentProjectPath` işlevi. Ancak, bu değişiklikleri devre dışı bırakın ve önceki Visual Studio (kaynak denetimi eklentisi API sürüm 1.1) davranışa dönmek için aşağıdaki kayıt defteri girdisini kullanılabilir:  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = dword: 00000001  
  
 Bu kayıt defteri girdisi yok veya için DWORD: 00000000 olarak ayarlayın, Visual Studio yeni işlevlerin kullanımına dener `SccCreateSubProject`ve`SccGetParentProjectPath`.  
  
 Kayıt defteri girdisi için DWORD: 00000001 ayarlarsanız, Visual Studio bu yeni işlevleri çalışmaz ve kaynak denetimine ekleme işlemleri Visual Studio'nun önceki sürümlerinde olduğu gibi çalışır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetimi Eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)

