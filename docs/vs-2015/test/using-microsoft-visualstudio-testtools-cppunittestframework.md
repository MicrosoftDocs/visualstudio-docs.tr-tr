---
title: Microsoft.VisualStudio.TestTools.CppUnitTestFramework kullanma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d1ac9188-d79f-407e-9f3a-80dbefa66317
caps.latest.revision: 10
ms.author: gewarren
manager: douge
ms.openlocfilehash: 68f083bf6aa99177f6b9e697be8affa5d29804a8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49889613"
---
# <a name="using-microsoftvisualstudiotesttoolscppunittestframework"></a>Microsoft.VisualStudio.TestTools.CppUnitTestFramework Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu genel üyeleri listeler `Microsoft::VisualStudio::CppUnitTestFramework` ad alanı.  
  
 Üstbilgi dosyalarında bulunan _[x 86] VisualStudio2012 InstallFolder_**\VC\UnitTest\include** klasör.  
  
 LIB dosyaları bulunan _[x 86] VisualStudio2012 InstallFolder_**\VC\UnitTest\lib** klasör.  
  
##  <a name="BKMK_In_this_topic"></a> Bu konudaki  
 [CppUnitTest.h](#BKMK_CppUnitTest_h)  
  
- [Test sınıflar ve yöntemler oluşturma](#BKMK_Create_test_classes_and_methods)  
  
- [Başlatma ve temizleme](#BKMK_Initialize_and_cleanup)  
  
  -   [Test yöntemleri](#BKMK_Test_methods)  
  
  -   [Test sınıfları](#BKMK_Test_classes)  
  
  -   [Test modülleri](#BKMK_Test_modules)  
  
- [Test öznitelikleri oluşturma](#BKMK_Create_test_attributes)  
  
  - [Test yöntemi öznitelikleri](#BKMK_Test_method_attributes)  
  
  - [Test sınıfı öznitelikler](#BKMK_Test_class_attributes)  
  
  - [Test modül öznitelikleri](#BKMK_Test_module_attributes)  
  
  - [Önceden tanımlı öznitelikleri](#BKMK_Pre_defined_attributes)  
  
    [CppUnitTestAssert.h](#BKMK_CppUnitTestAssert_h)  
  
  - [Genel onaylar](#BKMK_General_Asserts)  
  
    -   [Eşit](#BKMK_General_Are_Equal)  
  
    -   [Eşit değildir](#BKMK_General_Are_Not_Equal)  
  
    -   [Aynı](#BKMK_General_Are_Same)  
  
    -   [Aynı değil](#BKMK_General_Are_Not_Same)  
  
    -   [Null](#BKMK_General_Is_Null)  
  
    -   [Null değil](#BKMK_General_Is_Not_Null)  
  
    -   [Geçerlidir](#BKMK_General_Is_True)  
  
    -   [Yanlış](#BKMK_General_Is_False)  
  
    -   [Başarısız](#BKMK_General_Fail)  
  
  - [Windows çalışma zamanı onaylar](#BKMK_WinRT_Asserts)  
  
    -   [Eşit](#BKMK_WinRT_Are_Equal)  
  
    -   [Aynı](#BKMK_WinRT_Are_Same)  
  
    -   [Eşit değildir](#BKMK_WinRT_Are_Not_Equal)  
  
    -   [Aynı değil](#BKMK_WinRT_Are_Not_Same)  
  
    -   [Null](#BKMK_WinRT_Is_Null)  
  
    -   [Null değil](#BKMK_WinRT_Is_Not_Null)  
  
  - [Özel durum onaylar](#BKMK_Exception_Asserts)  
  
    - [Özel durum beklediğiniz](#BKMK_Expect_Exception)  
  
      [CppUnitTestLogger.h](#BKMK_CppUnitTestLogger_h)  
  
    - [Günlükçü](#BKMK_Logger)  
  
    - [İleti Yaz](#BKMK_Write_Message)  
  
##  <a name="BKMK_CppUnitTest_h"></a> CppUnitTest.h  
  
###  <a name="BKMK_Create_test_classes_and_methods"></a> Test sınıflar ve yöntemler oluşturma  
  
```cpp  
TEST_CLASS(className)  
```  
  
 Test yöntemleri içeren her bir sınıf için gereklidir. Tanımlar *className* olarak bir test sınıfı. `TEST_CLASS` namescape kapsamda bildirilmelidir.  
  
```cpp  
TEST_METHOD(methodName)   
{  
    // test method body  
}  
  
```  
  
 Tanımlar *methodName* bir test yöntemi olarak. `TEST_METHOD` yöntemin sınıf kapsamı içinde bildirilmesi gerekir.  
  
###  <a name="BKMK_Initialize_and_cleanup"></a> Başlatma ve temizleme  
  
####  <a name="BKMK_Test_methods"></a> Test yöntemleri  
  
```cpp  
TEST_METHOD_INITIALIZE(methodName)   
{  
    // method initialization code  
}  
  
```  
  
 Tanımlar *methodName* her test yönteminin çalıştırılmadan önce çalışan bir yöntem olarak. `TEST_METHOD_INITIALIZE` yalnızca bir kez bir test sınıfında tanımlanabilir ve test sınıfta tanımlanmalıdır.  
  
```cpp  
TEST_METHOD_CLEANUP(methodName)   
{  
    // test method cleanup  code  
}  
  
```  
  
 Tanımlar *methodName* her test yönteminin çalıştırdıktan sonra çalıştırılan bir yöntem olarak. `TEST_METHOD_CLEANUP` yalnızca bir kez bir test sınıfında tanımlanabilir ve test sınıfı kapsamında tanımlanmış olması gerekir.  
  
####  <a name="BKMK_Test_classes"></a> Test sınıfları  
  
```cpp  
TEST_CLASS_INITIALIZE(methodName)   
{  
    // test class initialization  code  
}  
  
```  
  
 Tanımlar *methodName* her test sınıfı oluşturulduktan sonra çalıştırılan bir yöntem olarak. `TEST_CLASS_INITIALIZE` yalnızca bir kez bir test sınıfında tanımlanabilir ve test sınıfı kapsamında tanımlanmış olması gerekir.  
  
```cpp  
TEST_CLASS_CLEANUP(methodName)   
{  
    // test class cleanup  code  
}  
  
```  
  
 Tanımlar *methodName* her test sınıfı oluşturulduktan sonra çalıştırılan bir yöntem olarak. `TEST_CLASS_CLEANUP` yalnızca bir kez bir test sınıfında tanımlanabilir ve test sınıfı kapsamında tanımlanmış olması gerekir.  
  
####  <a name="BKMK_Test_modules"></a> Test modülleri  
  
```cpp  
TEST_MODULE_INITIALIZE(methodName)  
{  
    // module initialization code  
}  
```  
  
 Yöntemi tanımlar *methodName* bir modül yüklendiğinde çalışır. `TEST_MODULE_INITIALIZE` yalnızca bir kez bir test modülde tanımlanabilir ve ad uzayı kapsamında bildirilmesi gerekir.  
  
```cpp  
TEST_MODULE_CLEANUP(methodName)  
```  
  
 Yöntemi tanımlar *methodName* bir modül kaldırıldığında çalışır. `TEST_MODULE_CLEANUP` yalnızca bir kez bir test modülde tanımlanabilir ve ad uzayı kapsamında bildirilmesi gerekir.  
  
###  <a name="BKMK_Create_test_attributes"></a> Test öznitelikleri oluşturma  
  
####  <a name="BKMK_Test_method_attributes"></a> Test yöntemi öznitelikleri  
  
```cpp  
BEGIN_TEST_METHOD_ATTRIBUTE(testMethodName)   
    TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)  
    ...  
END_TEST_METHOD_ATTRIBUTE()  
```  
  
 Bir veya daha fazla tanımlanan öznitelik ekler `TEST_METHOD_ATTRIBUTE` makroları test yöntemi *testClassName*.  
  
 A `TEST_METHOD_ATTRIBUTE` makrosunu tanımlayan bir öznitelik adı ile *attributeName* ve değer *attributeValue*.  
  
####  <a name="BKMK_Test_class_attributes"></a> Test sınıfı öznitelikler  
  
```cpp  
BEGIN_TEST_CLASS_ATTRIBUTE(testClassName)   
    TEST_CLASS_ATTRIBUTE(attributeName, attributeValue)  
    ...  
END_TEST_CLASS_ATTRIBUTE()  
```  
  
 Bir veya daha fazla tanımlanan öznitelik ekler `TEST_CLASS_ATTRIBUTE` makroları test sınıfına *testClassName*.  
  
 A `TEST_CLASS_ATTRIBUTE` makrosunu tanımlayan bir öznitelik adı ile *attributeName* ve değer *attributeValue*.  
  
####  <a name="BKMK_Test_module_attributes"></a> Test modül öznitelikleri  
  
```cpp  
BEGIN_TEST_MODULE_ATTRIBUTE(testModuleName)   
    TEST_MODULE_ATTRIBUTE(attributeName, attributeValue)  
    ...  
END_TEST_MODULE_ATTRIBUTE()  
```  
  
 Bir veya daha fazla tanımlanan öznitelik ekler `TEST_MODULE_ATTRIBUTE` makroları test modülüne *testModuleName*.  
  
 A `TEST_MODULE_ATTRIBUTE` makrosunu tanımlayan bir öznitelik adı ile *attributeName* ve değer *attributeValue*.  
  
####  <a name="BKMK_Pre_defined_attributes"></a> Önceden tanımlı öznitelikleri  
 Bu önceden tanımlı öznitelik makroları makroları yerine kullanılabileceği `TEST_METHOD_ATTRIBUTE`, `TEST_CLASS_ATTRIBUTE`, veya `TEST_MODULE_ATTRIBUTE` yukarıda açıklanan.  
  
```cpp  
TEST_OWNER(ownerAlias)  
```  
  
 Bu ada sahip bir öznitelik tanımlar `Owner` ve öznitelik değeri *ownerAlias*.  
  
```cpp  
TEST_DESCRIPTION(description)  
```  
  
 Bu ada sahip bir öznitelik tanımlar `Description` ve öznitelik değeri *açıklama*.  
  
```cpp  
TEST_PRIORITY(priority)  
```  
  
 Bu ada sahip bir öznitelik tanımlar `Priority` ve öznitelik değeri *öncelik*.  
  
```cpp  
TEST_WORKITEM(workitem)  
```  
  
 Bu ada sahip bir öznitelik tanımlar `WorkItem` ve öznitelik değeri *WorkItem*.  
  
```cpp  
TEST_IGNORE()  
```  
  
 Bu ada sahip bir öznitelik tanımlar `Ignore` ve öznitelik değeri `true`.  
  
##  <a name="BKMK_CppUnitTestAssert_h"></a> CppUnitTestAssert.h  
  
###  <a name="BKMK_General_Asserts"></a> Genel onaylar  
  
####  <a name="BKMK_General_Are_Equal"></a> Eşit  
 İki nesnenin eşit olup olmadığını doğrulayın  
  
```cpp  
template<typename T>   
static void AreEqual(  
    const T& expected,   
    const T& actual,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 İki çiftten eşit olduğunu doğrulayın  
  
```cpp  
static void AreEqual(  
    double expected,   
    double actual,   
    double tolerance,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 İki floattan eşit olduğunu doğrulayın  
  
```cpp  
static void AreEqual(  
    float expected,   
    float actual,   
    float tolerance,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 İki char * dizelerin eşit olduğunu doğrulayın  
  
```cpp  
static void AreEqual(  
    const char* expected,   
    const char* actual,   
    bool ignoreCase = false,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 İki w_char * dizelerin eşit olduğunu doğrulayın  
  
```cpp  
static void AreEqual(  
    const wchar_t* expected,   
    const wchar_t* actual,   
    bool ignoreCase = false,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Are_Not_Equal"></a> Eşit değildir  
 İki çiftten eşit olmadığını doğrulayın  
  
```cpp  
static void AreNotEqual(  
    double notExpected,   
    double actual,   
    double tolerance,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 İki floattan eşit olmadığını doğrulayın  
  
```cpp  
static void AreNotEqual(  
    float notExpected,   
    float actual,   
    float tolerance,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 İki char * dizeler eşit olmadığını doğrulayın  
  
```cpp  
static void AreNotEqual(  
    const char* notExpected,   
    const char* actual,   
    bool ignoreCase = false,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 İki w_char * dizeler eşit olmadığını doğrulayın  
  
```cpp  
static void AreNotEqual(  
    const wchar_t* notExpected,   
    const wchar_t* actual,   
    bool ignoreCase = false,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
 İki başvuru operatörüne göre eşit olmadığını doğrulayın ==.  
  
```cpp  
template<typename T>   
static void AreNotEqual(  
    const T& notExpected,   
    const T& actual,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Are_Same"></a> Aynı  
 İki başvurunun aynı nesne örneği (kimlik) başvurduğunu doğrulayın.  
  
```cpp  
template<typename T>   
static void AreSame(  
    const T& expected,   
    const T& actual,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Are_Not_Same"></a> Aynı değil  
 Aynı nesne örneği (kimlik) başvurmamasını iki başvuru doğrulayın.  
  
```cpp  
template<typename T>   
static void AreNotSame (  
    const T& notExpected,   
    const T& actual,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Is_Null"></a> Null  
 Bir işaretçi NULL olduğundan emin olun.  
  
```cpp  
template<typename T>   
static void IsNull(  
    const T* actual,  
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Is_Not_Null"></a> Null değil  
 Bir işaretçi NULL olmadığından emin olun  
  
```cpp  
template<typename T>   
static void IsNotNull(  
    const T* actual,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Is_True"></a> Geçerlidir  
 Bir koşul doğru olduğundan emin olun  
  
```cpp  
static void IsTrue(  
    bool condition,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Is_False"></a> Yanlış  
 Bir koşul false olduğundan emin olun  
  
```cpp  
static void IsFalse(  
    bool condition,   
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
####  <a name="BKMK_General_Fail"></a> Başarısız  
 Test çalışması sonucu başarısız olarak zorla  
  
```cpp  
static void Fail(  
    const wchar_t* message = NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
###  <a name="BKMK_WinRT_Asserts"></a> Windows çalışma zamanı onaylar  
  
####  <a name="BKMK_WinRT_Are_Equal"></a> Eşit  
 İki Windows çalışma zamanı işaretçileri eşit olduğunu doğrular.  
  
```  
template<typename T>   
static void AreEqual(  
    T^ expected,   
    T^ actual,   
    Platform::String^ message = nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
 Bu iki doğrular Platform::String ^ dizeler eşit.  
  
```  
template<typename T>   
static void AreEqual(  
    T^ expected,   
    T^ actual,   
    Platform::String^ message= nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
####  <a name="BKMK_WinRT_Are_Same"></a> Aynı  
 İki Windows Runtime başvuru aynı nesneye referans gösterdiğini doğrular.  
  
```  
template<typename T>   
static void AreSame(  
    T% expected,   
    T% actual,   
    Platform::String^ message= nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
####  <a name="BKMK_WinRT_Are_Not_Equal"></a> Eşit değildir  
 İki Windows çalışma zamanı işaretçileri eşit olmadığını doğrular.  
  
```  
template<typename T>   
static void AreNotEqual(  
    T^ notExpected,   
    T^ actual,   
    Platform::String^ message = nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
 Bu iki doğrular Platform::String ^ dizeler eşit değildir.  
  
```  
static void AreNotEqual(  
    Platform::String^ notExpected,   
    Platform::String^ actual,   
    bool ignoreCase = false,   
    Platform::String^ message= nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
####  <a name="BKMK_WinRT_Are_Not_Same"></a> Aynı değil  
 İki Windows Runtime başvuru aynı nesneye başvurma doğrular.  
  
```  
template<typename T>   
static void AreNotSame(  
    T% notExpected,   
    T% actual,   
    Platform::String^ message= nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
####  <a name="BKMK_WinRT_Is_Null"></a> Null  
 Bir Windows çalışma zamanı işaretçi bir nullptr olduğunu doğrular.  
  
```  
template<typename T>   
static void IsNull(  
    T^ actual,  
    Platform::String^ message = nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
####  <a name="BKMK_WinRT_Is_Not_Null"></a> Null değil  
 Bir Windows çalışma zamanı işaretçi bir nullptr olmadığını doğrular.  
  
```  
template<typename T>   
static void IsNotNull(  
    T^ actual,   
    Platform::String^ message= nullptr,   
    const __LineInfo* pLineInfo= nullptr)  
```  
  
###  <a name="BKMK_Exception_Asserts"></a> Özel durum onaylar  
  
####  <a name="BKMK_Expect_Exception"></a> Özel durum beklediğiniz  
 Bir işlev özel durum harekete doğrulayın:  
  
```  
template<typename _EXPECTEDEXCEPTION, typename _FUNCTOR>   
static void ExpectException(  
    _FUNCTOR functor,   
    const wchar_t* message= NULL,   
    const __LineInfo* pLineInfo= NULL)  
```  
  
 Bir işlev özel durum harekete doğrulayın:  
  
```  
template<typename _EXPECTEDEXCEPTION, typename _RETURNTYPE>   
    static void ExpectException(  
    _RETURNTYPE (*func)(),   
    const wchar_t* message= NULL,   
    const __LineInfo* pLineInfo = NULL)  
```  
  
##  <a name="BKMK_CppUnitTestLogger_h"></a> CppUnitTestLogger.h  
  
###  <a name="BKMK_Logger"></a> Günlükçü  
 Günlükçü sınıf yazmak için statik yöntemler içerir.  
  
```  
class Logger  
```  
  
###  <a name="BKMK_Write_Message"></a> İleti Yaz  
  
```  
static void   
Logger::WriteMessage(const wchar_t* message)  
```  
  
```  
static void   
Logger::WriteMessage(const char* message)  
```  
  
## <a name="example"></a>Örnek  
 Bu kod örneği yer almaktadır.  
  
```  
////////////////////////////////////////////////////////////  
/* USAGE EXAMPLE  
// The following is an example of VSCppUnit usage.  
// It includes examples of attribute metadata, fixtures,  
// unit tests with assertions, and custom logging.  
  
#include <CppUnitTest.h>  
  
using namespace Microsoft::VisualStudio::CppUnitTestFramework;  
  
BEGIN_TEST_MODULE_ATTRIBUTE()  
    TEST_MODULE_ATTRIBUTE(L"Date", L"2010/6/12")  
END_TEST_MODULE_ATTRIBUTE()  
  
TEST_MODULE_INITIALIZE(ModuleInitialize)  
{  
    Logger::WriteMessage("In Module Initialize");  
}  
  
TEST_MODULE_CLEANUP(ModuleCleanup)  
{  
    Logger::WriteMessage("In Module Cleanup");  
}  
  
TEST_CLASS(Class1)  
{  
  
public:  
  
    Class1()  
    {  
        Logger::WriteMessage("In Class1");  
    }  
  
    ~Class1()  
    {  
        Logger::WriteMessage("In ~Class1");  
    }  
  
    TEST_CLASS_INITIALIZE(ClassInitialize)  
    {  
        Logger::WriteMessage("In Class Initialize");  
    }  
  
    TEST_CLASS_CLEANUP(ClassCleanup)  
    {  
        Logger::WriteMessage("In Class Cleanup");  
    }  
  
    BEGIN_TEST_METHOD_ATTRIBUTE(Method1)  
        TEST_OWNER(L"OwnerName")  
        TEST_PRIORITY(1)  
    END_TEST_METHOD_ATTRIBUTE()  
  
    TEST_METHOD(Method1)  
    {     
        Logger::WriteMessage("In Method1");  
        Assert::AreEqual(0, 0);  
    }  
  
    TEST_METHOD(Method2)  
    {  
        Assert::Fail(L"Fail");  
    }  
};  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kodunuza birim testi](../test/unit-test-your-code.md)   
 [Yerel kod Test Gezgini ile birim testi](http://msdn.microsoft.com/en-us/8a09d6d8-3613-49d8-9ffe-11375ac4736c)   
 [Mevcut C++ uygulamalarına birim testleri ekleme](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)



