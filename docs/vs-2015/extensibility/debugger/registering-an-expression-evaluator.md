---
title: İfade değerlendiricisi kaydetme | Microsoft Docs
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
- debugging [Debugging SDK], expression evaluation
- expression evaluators, registering
ms.assetid: 236be234-e05f-4ad8-9200-24ce51768ecf
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 29aaef797ad18fd63e4f587901dbf3b29dbb73b0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51808350"
---
# <a name="registering-an-expression-evaluator"></a>İfade Değerlendiricisi Kaydetme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015'te, bu şekilde ifade değerlendiricisi uygulama kullanım dışı bırakılmıştır. CLR ifade değerlendiricisi uygulama hakkında daha fazla bilgi için lütfen bkz [CLR ifade Değerlendiricilerini](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendiricisi örnek](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 İfade değerlendirici (EE) kendisi Windows COM ortam ve Visual Studio ile bir sınıf üreteci olarak kaydetmeniz gerekir. Böylece, hata ayıklama altyapısı (DE) adres alanı veya varlık EE başlatır, bağlı olarak Visual Studio adres alanı eklenmesi bir EE DLL olarak uygulanır.  
  
## <a name="managed-code-expression-evaluator"></a>Yönetilen kod ifade değerlendiricisi  
 EE kendisini genellikle VSIP programı için bir çağrı tarafından başlatılan COM ortamıyla kaydeden bir DLL olan bir sınıf kitaplığı, olarak gerçekleştirilen bir yönetilen kod **regpkg.exe**. COM ortamı için kayıt defteri anahtarlarını yazma gerçek işlemi otomatik olarak gerçekleştirilir.  
  
 Ana sınıfının bir yöntem ile işaretlenmiş <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>, DLL com ile kaydedildiğinde çağrılacak yöntem olduğunu belirten Genellikle olarak adlandırılan bu kayıt yöntemi `RegisterClass`, DLL ile Visual Studio'yu kayıt ettirme görevi gerçekleştirir. Karşılık gelen `UnregisterClass` (ile işaretlenen <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>), etkilerini geri alır `RegisterClass` DLL zaman kaldırılır.  
  
 Aynı kayıt defteri girdilerini, yönetilmeyen kodda yazılmış bir EE olduğu gibi yapılır; tek fark olduğunu yardımcı bir işlev gibi `SetEEMetric` iş sizin için gerçekleştirmesini istemeniz. Bu kaydolmayı/kaydı kaldırmayı işlemin bir örnek şöyle görünür:  
  
### <a name="example"></a>Örnek  
 Bu işlev, nasıl bir yönetilen kod EE kaydeder ve kendisi ile Visual Studio kaydını gösterir.  
  
```csharp  
namespace EEMC  
{  
    [GuidAttribute("462D4A3D-B257-4AEE-97CD-5918C7531757")]  
    public class EEMCClass : IDebugExpressionEvaluator  
    {  
        #region Register and unregister.  
        private static Guid guidMycLang = new Guid("462D4A3E-B257-4AEE-97CD-5918C7531757");  
        private static string languageName = "MyC";  
        private static string eeName = "MyC Expression Evaluator";  
  
        private static Guid guidMicrosoftVendor = new Guid("994B45C4-E6E9-11D2-903F-00C04FA302A1");  
        private static Guid guidCOMPlusOnlyEng = new Guid("449EC4CC-30D2-4032-9256-EE18EB41B62B");  
        private static Guid guidCOMPlusNativeEng = new Guid("92EF0900-2251-11D2-B72E-0000F87572EF");  
  
        /// <summary>  
        /// Register the expression evaluator.  
        /// Set "project properties/configuration properties/build/register for COM interop" to true.  
        /// </summary>  
         [ComRegisterFunctionAttribute]  
        public static void RegisterClass(Type t)  
        {  
            // Get Visual Studio version (set by regpkg.exe)  
            string hive = Environment.GetEnvironmentVariable("EnvSdk_RegKey");  
            string s = @"SOFTWARE\Microsoft\VisualStudio\"  
                        + hive  
                        + @"\AD7Metrics\ExpressionEvaluator";  
  
            RegistryKey rk = Registry.LocalMachine.CreateSubKey(s);  
            if (rk == null)  return;  
  
            rk = rk.CreateSubKey(guidMycLang.ToString("B"));  
            rk = rk.CreateSubKey(guidMicrosoftVendor.ToString("B"));  
            rk.SetValue("CLSID", t.GUID.ToString("B"));  
            rk.SetValue("Language", languageName);  
            rk.SetValue("Name", eeName);  
  
            rk = rk.CreateSubKey("Engine");  
            rk.SetValue("0", guidCOMPlusOnlyEng.ToString("B"));  
            rk.SetValue("1", guidCOMPlusNativeEng.ToString("B"));  
        }  
        /// <summary>  
        /// Unregister the expression evaluator.  
        /// </summary>  
         [ComUnregisterFunctionAttribute]  
        public static void UnregisterClass(Type t)  
        {  
            // Get Visual Studio version (set by regpkg.exe)  
            string hive = Environment.GetEnvironmentVariable("EnvSdk_RegKey");  
            string s = @"SOFTWARE\Microsoft\VisualStudio\"  
                        + hive  
                        + @"\AD7Metrics\ExpressionEvaluator\"  
                        + guidMycLang.ToString("B");  
            RegistryKey key = Registry.LocalMachine.OpenSubKey(s);  
            if (key != null)  
            {  
                key.Close();  
                Registry.LocalMachine.DeleteSubKeyTree(s);  
            }  
        }  
    }  
}  
```  
  
## <a name="unmanaged-code-expression-evaluator"></a>Yönetilmeyen kod ifade değerlendiricisi  
 EE DLL uygulayan `DllRegisterServer` COM ortam yanı sıra Visual Studio kendisini kaydetmek için işlevi.  
  
> [!NOTE]
>  VSIP yükleme EnVSDK\MyCPkgs\MyCEE altında bulunan dosya dllentry.cpp MyCEE kodundan örnek kayıt defteri bulunabilir.  
  
### <a name="dll-server-process"></a>DLL sunucu işlemi  
 EE DLL sunucu kaydı sırasında:  
  
1.  Kendi sınıf üreteci kaydettirir `CLSID` normal COM kurallarına göre.  
  
2.  Yardımcı işlevini çağıran `SetEEMetric` aşağıdaki tabloda gösterilen EE ölçümleri Visual Studio ile kaydetmek için. İşlev `SetEEMetric` ve aşağıda belirtilen ölçümleri dbgmetric.lib Kitaplığı'nın bir parçasıdır. Bkz: [hata ayıklama için SDK Yardımcıları](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) Ayrıntılar için.  
  
    |Ölçüm|Açıklama|  
    |------------|-----------------|  
    |`metricCLSID`|`CLSID` EE sınıf fabrikası|  
    |`metricName`|Annotatable dize olarak EE adı|  
    |`metricLanguage`|EE dil adını değerlendirmek için tasarlanmıştır|  
    |`metricEngine`|`GUID`Bu EE çalışma hata ayıklama altyapısı (DE) s|  
  
    > [!NOTE]
    >  `metricLanguage``GUID` Tanımlayan adı, ancak dil olan `guidLang` bağımsız değişkeni `SetEEMetric` , dil seçer. Derleyici hata ayıklama bilgileri dosyası oluşturduğunda, uygun yazmalısınız `guidLang` DE kullanmak için hangi EE bilebilmesi. DE genellikle bu dil için Sembol sağlayıcısı ister `GUID`, hata ayıklama bilgileri dosyasında depolanır.  
  
3.  Visual Studio ile anahtarları hkey_local_machıne\software\microsoft\visualstudio altında oluşturarak kaydettirir\\*X.Y*burada *X.Y* kaydetmek için Visual Studio sürümüdür.  
  
### <a name="example"></a>Örnek  
 Bu işlev, nasıl bir yönetilmeyen kod (C++) EE kaydeder ve kendisi ile Visual Studio kaydını gösterir.  
  
```cpp#  
/*---------------------------------------------------------  
  Registration  
-----------------------------------------------------------*/  
#ifndef LREGKEY_VISUALSTUDIOROOT  
    #define LREGKEY_VISUALSTUDIOROOT L"Software\\Microsoft\\VisualStudio\\8.0"  
#endif  
  
static HRESULT RegisterMetric( bool registerIt )  
{  
    // check where we should register  
    const ULONG cchBuffer = _MAX_PATH;  
    WCHAR wszRegistrationRoot[cchBuffer];  
    DWORD cchFreeBuffer = cchBuffer - 1;  
    wcscpy(wszRegistrationRoot, LREGKEY_VISUALSTUDIOROOT_NOVERSION);  
    wcscat(wszRegistrationRoot, L"\\");  
  
    // this is Environment SDK specific  
    // we check for  EnvSdk_RegKey environment variable to  
    // determine where to register  
    DWORD cchDefRegRoot = lstrlenW(LREGKEY_VISUALSTUDIOROOT_NOVERSION) + 1;  
    cchFreeBuffer = cchFreeBuffer - cchDefRegRoot;  
    DWORD cchEnvVarRead = GetEnvironmentVariableW(  
        /* LPCTSTR */ L"EnvSdk_RegKey", // environment variable name  
        /* LPTSTR  */ &wszRegistrationRoot[cchDefRegRoot],// buffer for variable value  
        /* DWORD   */ cchFreeBuffer);// size of buffer  
    if (cchEnvVarRead >= cchFreeBuffer)  
        return E_UNEXPECTED;  
    // If the environment variable does not exist then we must use   
    // LREGKEY_VISUALSTUDIOROOT which has the version number.  
    if (0 == cchEnvVarRead)  
        wcscpy(wszRegistrationRoot, LREGKEY_VISUALSTUDIOROOT);  
  
    if (registerIt)  
    {  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricCLSID,  
                    CLSID_MycEE,  
                    wszRegistrationRoot );  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricName,  
                    GetString(IDS_INFO_MYCDESCRIPTION),  
                    wszRegistrationRoot );  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricLanguage, L"MyC",  
                    wszRegistrationRoot);  
  
        GUID engineGuids[2];  
        engineGuids[0] = guidCOMPlusOnlyEng;  
        engineGuids[1] = guidCOMPlusNativeEng;  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricEngine,  
                    engineGuids,  
                    2,  
                    wszRegistrationRoot);  
    }  
    else  
    {  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricCLSID,  
                        wszRegistrationRoot);  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricName,  
                        wszRegistrationRoot );  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricLanguage,  
                        wszRegistrationRoot );  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricEngine,  
                        wszRegistrationRoot );  
    }  
  
    return S_OK;  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bir CLR ifade değerlendiricisi yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Hata Ayıklama için SDK Yardımcıları](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)

