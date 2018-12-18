---
title: SccGetProjPath işlevi | Microsoft Docs
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
- SccGetProjPath
helpviewer_keywords:
- SccGetProjPath function
ms.assetid: 1079847e-d45f-4cb8-9d92-1e01ce5d08f6
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 978316cd9c953217a3e59a7ecd1b047cab12734b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51752587"
---
# <a name="sccgetprojpath-function"></a>SccGetProjPath İşlevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu işlev, yalnızca kaynak denetimi eklentisi anlamlı bir dize olan bir proje yolu kullanıcıya sorar. Kullanıcı olduğunda çağrılır:  
  
-   Yeni proje oluşturma  
  
-   Mevcut bir projeyi sürüm denetimine ekleme  
  
-   Var olan sürüm denetimi projesinde bulunmaya çalışılıyor  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp#  
SCCRTN SccGetProjPath (  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPSTR  lpProjName,  
   LPSTR  lpLocalPath,  
   LPSTR  lpAuxProjPath,  
   BOOL   bAllowChangePath,  
   LPBOOL pbNew  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 pvContext  
 [in] Kaynak Denetimi Eklentisi bağlam yapısı.  
  
 hWnd  
 [in] Kaynak Denetimi Eklentisi sağladığı herhangi bir iletişim kutusu için bir üst öğe olarak kullanabileceğiniz IDE penceresi için bir tanıtıcı.  
  
 lpUser  
 [out içinde] Kullanıcı adı (NULL Sonlandırıcı dahil olmak üzere, SCC_USER_SIZE aşmayı değil)  
  
 lpProjName  
 [out içinde] IDE projeye, proje çalışma alanı veya derleme görevleri dosyası (SCC_PRJPATH_SIZE, NULL sonlandırıcıyı da dahil olmak üzere aşmayı değil) adı.  
  
 lpLocalPath  
 [out içinde] Projenin çalışma yolu. Varsa `bAllowChangePath` olduğu `TRUE`, kaynak denetimi eklentisi şu dizeyi (Sonlandırıcı null dahil olmak üzere, _MAX_PATH aşmayı değil) değiştirebilirsiniz.  
  
 lpAuxProjPath  
 [out içinde] Döndürülen proje yolu (SCC_PRJPATH_SIZE, NULL sonlandırıcıyı da dahil olmak üzere aşmayı değil) için bir arabellek.  
  
 bAllowChangePath  
 [in] Bu ise `TRUE`, kaynak denetimi eklentisi iste ve değiştirme `lpLocalPath` dize.  
  
 pbNew  
 [out içinde] Yeni bir proje oluşturulup oluşturulmayacağını gelen bir değer belirtir. Döndürülen değer, bir proje oluşturma başarılı olduğunu gösterir:  
  
|gelen|Yorumu|  
|--------------|--------------------|  
|TRUE|Kullanıcı yeni bir proje oluşturabilirsiniz.|  
|FALSE|Kullanıcı yeni bir proje oluşturabilirsiniz.|  
  
|Giden|Yorumu|  
|--------------|--------------------|  
|TRUE|Yeni bir proje oluşturuldu.|  
|FALSE|Mevcut bir projeyi seçildi.|  
  
## <a name="return-value"></a>Dönüş Değeri  
 Kaynak Denetimi Eklentisi uygulanması bu işlev, aşağıdaki değerlerden birini döndürmesi beklenir:  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|SCC_OK|Proje başarıyla oluşturuldu veya alınır.|  
|SCC_I_OPERATIONCANCELED|İşlem iptal edildi.|  
|SCC_E_ACCESSFAILURE|Kaynak denetim sistemi, ağ veya çakışma sorunları nedeniyle muhtemelen erişilirken sorun oluştu.|  
|SCC_E_CONNECTIONFAILURE|Kaynak Denetim sistemine bağlanmaya çalışılırken bir hata oluştu.|  
|SCC_E_NONSPECIFICERROR|Belirtilmeyen bir hata oluştu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu işlevin amacı parametreleri almak için ıde'dir `lpProjName` ve `lpAuxProjPath`. Kaynak Denetimi Eklentisi bu bilgiyi kullanıcıya sorar. sonra bu iki dizeyi IDE'ye geçirir. IDE Çözüm dosyasındaki bu dizeler devam ediyorsa ve bunları geçirmeden [SccOpenProject](../extensibility/sccopenproject-function.md) her kullanıcıya bu proje açılır. Bu dizeler, eklentinin bir projeyle ilişkili bilgileri izlemek etkinleştirin.  
  
 İşlev ilk kez çağrıldığında, `lpAuxProjPath` boş bir dizeye ayarlayın. `lProjName` boş olabilir veya kaynak denetimi eklentisi kullanın veya yoksay IDE proje adı içeriyor olabilir. İşlev başarıyla geri döndüğünde, eklenti, karşılık gelen iki dizeyi döndürür. IDE bu dizeler hakkında hiçbir varsayım yapmaz, bunları kullanmaz ve bunları değiştirmek kullanıcı izin vermez. Kullanıcı ayarlarını değiştirmek isterse, IDE çağıracak `SccGetProjPath` iletmeden aynı değerleri önceki bir zamana yeniden almış. Bu, bu iki dizeler üzerinde eklenti tam denetim verir.  
  
 İçin `lpUser`, IDE bir kullanıcı adı olarak oldfashionedgoat ya da yalnızca boş bir dizeye bir işaretçi iletebilir. Bir kullanıcı adı varsa, kaynak denetimi eklentisi, varsayılan olarak kullanmanız gerekir. Ancak, adsız aktarılırsa veya verilen ada sahip bir oturum açma başarısız olursa, eklentinin bir oturum açma adı yeniden geçişi için kullanıcı isteyecektir `lpUser` aldığında geçerli bir oturum açma. Bu dize eklenti değişebilir olduğundan, IDE her zaman bir arabellek boyutunu tahsis (`SCC_USER_LEN`+ 1).  
  
> [!NOTE]
>  IDE yaptığı ilk eylemi ya da bir çağrı olabilir `SccOpenProject` işlevi veya `SccGetProjPath` işlevi. Bu nedenle, her ikisi de aynı sahip `lpUser` parametresini ya da zaman kullanıcının oturumunu açmak için eklenti kaynak denetimi sağlar. İşlev dönüş bir hata gösteriyor olsa bile, eklentinin bir geçerli oturum açma adı Bu dizeyle doldurmanız gerekir.  
  
 `lpLocalPath` Burada kullanıcının proje tutar dizindir. Boş bir dize olabilir. (Durumunda, kaynak denetim sisteminden proje yüklemeyi deneyen bir kullanıcı gibi) şu anda tanımlanmış hiçbir dizin varsa ve `bAllowChangePath` olduğu `TRUE`, kaynak denetimi eklentisi giriş kullanıcıdan veya yerleştirmek için başka bir yöntem kullanın, kendi dizeye `lpLocalPath`. Varsa `bAllowChangePath` olduğu `FALSE`, kullanıcı belirtilen dizinde zaten çalıştığından eklentinin dize değiştirmemesi gerekir.  
  
 Kullanıcının kaynak denetimi altında koymak üzere yeni bir proje oluşturur, kaynak denetimi eklentisi gerçekten, kaynak denetim sistemi zaman oluşturmayabilir `SccGetProjPath` çağrılır. Bunun yerine, sıfır dışında bir değer dizesiyle boyunca geri geçirir `pbNew`, kaynak denetim sistemi proje oluşturulacak belirten.  
  
 Örneğin, bir kullanıcı, **yeni proje** Sihirbazı'nda Visual Studio, kendi proje kaynak denetimine ekler, Visual Studio bu işlevi çağırır ve eklentinin yeni bir proje için kaynak denetim sistemi oluşturmak uygun olup olmadığını belirler Visual Studio projesini içerir. Kullanıcı tıklarsa **iptal** Sihirbazı tamamlamadan önce projeyi hiçbir zaman oluşturulur. Kullanıcı tıklarsa **Tamam**, Visual Studio çağırır `SccOpenProject`, içinde geçen `SCC_OPT_CREATEIFNEW`, ve o anda kaynak denetimli Proje oluşturulur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetimi Eklentisi API işlevleri](../extensibility/source-control-plug-in-api-functions.md)   
 [SccOpenProject](../extensibility/sccopenproject-function.md)

