---
title: SccCreateSubProject işlevi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccCreateSubProject
helpviewer_keywords:
- SccCreateSubProject function
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3aef071d0c124878adf58d8346ad0b50f741300b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49931356"
---
# <a name="scccreatesubproject-function"></a>SccCreateSubProject işlevi
Bu işlev tarafından belirtilen var olan bir üst projesi altında verilen ada sahip bir alt proje oluşturur. `lpParentProjPath` bağımsız değişken.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
SCCRTN SccCreateSubProject(  
   LPVOID pContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPCSTR lpParentProjPath,  
   LPCSTR lpSubProjName,  
   LPSTR  lpAuxProjPath,  
   LPSTR  lpSubProjPath  
);  
```  
  
### <a name="parameters"></a>Parametreler  
 pContext  
 [in] Kaynak Denetimi Eklentisi bağlam işaretçisi.  
  
 hWnd  
 [in] Kaynak Denetimi Eklentisi sağladığı herhangi bir iletişim kutusu için bir üst öğe olarak kullanabileceğiniz IDE penceresi için bir tanıtıcı.  
  
 lpUser  
 [out içinde] Kullanıcı adı (en fazla SCC_USER_SIZE, NULL sonlandırıcıyı da dahil olmak üzere).  
  
 lpParentProjPath  
 [in] (En fazla SCC_PRJPATH_SIZE, NULL sonlandırıcıyı da dahil olmak üzere) üst projesinin yolunu tanımlayan bir dize.  
  
 lpSubProjName  
 [in] Önerilen alt proje adı (en fazla SCC_PRJPATH_SIZE, NULL sonlandırıcıyı da dahil olmak üzere).  
  
 lpAuxProjPath  
 [out içinde] Proje (en fazla SCC_PRJPATH_SIZE, NULL sonlandırıcıyı da dahil olmak üzere) tanımlayan yardımcı dize.  
  
 lpSubProjPath  
 [out içinde] Çıkış dizesi (kadar SCC_PRJPATH_SIZE, NULL sonlandırıcıyı da dahil olmak üzere) alt yolu tanımlama.  
  
## <a name="return-value"></a>Dönüş değeri  
 Kaynak Denetimi Eklentisi uygulanması bu işlev, aşağıdaki değerlerden birini döndürmesi beklenir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|SCC_OK|Alt başarıyla oluşturuldu.|  
|SCC_E_INITIALIZEFAILED|Ana proje başlatılamadı.|  
|SCC_E_INVALIDUSER|Kullanıcı için kaynak denetim sistemi oturum açılamadı.|  
|SCC_E_COULDNOTCREATEPROJECT|Alt proje oluşturulamıyor.|  
|SCC_E_PROJSYNTAXERR|Geçersiz proje söz dizimi.|  
|SCC_E_UNKNOWNPROJECT|Ana proje kaynak denetimi eklentisi bilinmiyor.|  
|SCC_E_INVALIDFILEPATH|Dosya geçersiz veya kullanılamaz durumda yolu.|  
|SCC_E_NOTAUTHORIZED|Kullanıcı bu işlemi gerçekleştirmek için izin verilmiyor.|  
|SCC_E_ACCESSFAILURE|Kaynak denetim sistemi, ağ veya çakışma sorunları nedeniyle muhtemelen erişilirken sorun oluştu. Bir yeniden deneme önerilir.|  
|SCC_E_CONNECTIONFAILURE|Kaynak Denetimi Eklentisi bağlantı sorunu oluştu.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Belirli olmayan hata oluştu.|  
  
## <a name="remarks"></a>Açıklamalar  
 İşlev ekleyerek örneğin benzersiz bir tane oluşturmak için varsayılan adı değiştirebilirsiniz, bu ada sahip bir alt proje zaten varsa, "_\<number >" ona. Çağıranın değişiklikleri kabul etmek hazırlıklı olmalıdır `lpUser`, `lpSubProjPath`, ve `lpAuxProjPath`. `lpSubProjPath` Ve`lpAuxProjPath` çağrıda ardından bağımsız değişkenlerin [SccOpenProject](../extensibility/sccopenproject-function.md). Bunlar iade sırasında çağıran tarafından değiştirilmemelidir. Bu dizeler için kaynak denetimi eklentisi, bir proje ile ilişkilendirmek için gereken bilgileri izlemek için bir yol sağlar. Eklenti görüntülemek için uygun olmayabilecek bir biçimlendirilmiş dize kullanabileceğinizden arayan IDE üzerinde iade, bu iki parametre görüntülenmez. İşlev başarılı veya başarısız bir kod döndürür ve başarılı olursa, değişken doldurur `lpSubProjPath` tam proje yoluyla yeni bir proje.  
  
 Bu işlev benzer [SccGetProjPath](../extensibility/sccgetprojpath-function.md)dışında sessizce birini seçmek için kullanıcıdan yerine bir proje oluşturur. Zaman `SccCreateSubProject` işlevi çağrıldığında `lpParentProjName` ve `lpAuxProjPath` boş olmaz ve geçerli bir projeye karşılık gelir. Bu dizeler genellikle önceki bir çağrı IDE'den tarafından alınan `SccGetProjPath` işlevi veya [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).  
  
 `lpUser` Bağımsız değişken ise kullanıcı adı. IDE, daha önce gelen almış aynı kullanıcı adı geçer `SccGetProjPath`, ve varsayılan olarak kaynak denetimi Eklentisi adı kullanmanız gerekir. Kullanıcı eklenti ile açık bir bağlantı zaten varsa, ardından eklentiyi işlevi sessiz bir şekilde çalıştığından emin olmak için herhangi bir istemi ortadan kaldırmak denemelisiniz. Oturum açma başarısız olursa, ancak, eklenti için bir oturum açma ve kullanıcı, geçerli bir oturum adı yeniden geçişi aldığında isteyecektir `lpUser`. Bu dize eklenti değişebilir olduğundan, IDE her zaman bir arabellek ayırın (SCC_USER_LEN + 1 ya da null sonlandırıcıyı ortasının içeren SCC_USER_SIZE) boyutu. Dize değiştirilirse, yeni bir dize (eski dize olarak en az geçerli olarak) bir geçerli oturum açma adı olmalıdır.  
  
## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>SccCreateSubProject ve SccGetParentProjectPath teknik notlar  
 Kaynak denetim sistemi konumları seçmek için bir kullanıcıdan sayısını en aza indirmek için Visual Studio'da çözümler ve projeler kaynak denetimine eklemeye basitleştirilmiştir. Yeni İşlevler, her ikisi de kaynak denetimi eklentisi destekliyorsa, bu değişikliklerin Visual Studio tarafından etkinleştirilen `SccCreateSubProject` ve `SccGetParentProjectPath`. Ancak, bu değişiklikleri devre dışı bırakın ve önceki Visual Studio (kaynak denetimi eklentisi API sürüm 1.1) davranışa dönmek için aşağıdaki kayıt defteri girdisini kullanılabilir:  
  
 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] "DoNotCreateSolutionRootFolderInSourceControl" = dword: 00000001**  
  
 Bu kayıt defteri girdisi yok veya için DWORD: 00000000 olarak ayarlayın, Visual Studio yeni işlevlerin kullanımına dener `SccCreateSubProject` ve `SccGetParentProjectPath`.  
  
 Kayıt defteri girdisi için DWORD: 00000001 ayarlarsanız, Visual Studio bu yeni işlevleri çalışmaz ve kaynak denetimine ekleme işlemleri Visual Studio'nun önceki sürümlerinde olduğu gibi çalışır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Kaynak Denetimi Eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)