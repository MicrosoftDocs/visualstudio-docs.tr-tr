---
title: Microsoft.VisualStudio.TestTools.CppUnitTestFramework API Reference
ms.date: 11/04/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: reference
ms.author: mblome
manager: douge
ms.workload:
- multiple
author: mikeblome
ms.openlocfilehash: b2225ec5db308b290e932cb9d29d1c50e32d4608
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49820271"
---
# <a name="microsoftvisualstudiotesttoolscppunittestframework-api-reference"></a>Microsoft.VisualStudio.TestTools.CppUnitTestFramework API Başvurusu

Bu konu genel üyeleri listeler `Microsoft::VisualStudio::CppUnitTestFramework` ad alanı. Microsoft yerel birim testi Framework'ü temel C++ birim testleri yazmak için bu API'leri kullanın. Var olan bir [kullanım örneği](#example) konunun sonunda.

 Üstbilgi dosyalarında bulunan _[x 86] VisualStudio2012 InstallFolder_**\VC\UnitTest\include** klasör.

 LIB dosyaları bulunan _[x 86] VisualStudio2012 InstallFolder_**\VC\UnitTest\lib** klasör.

Üst bilgi ve LIB yolları yerel Test projesinde otomatik olarak yapılandırılır.

##  <a name="In_this_topic"></a> Bu konudaki
 [CppUnitTest.h](#cppUnitTest_h)

- [Test sınıflar ve yöntemler oluşturma](#create_test_classes_and_methods)

- [Başlatma ve temizleme](#Initialize_and_cleanup)

  -   [Test yöntemleri](#test_methods)

  -   [Test sınıfları](#test_classes)

  -   [Test modülleri](#test_modules)

- [Test öznitelikleri oluşturma](#create_test_attributes)

  - [Test yöntemi öznitelikleri](#test_method_attributes)

  - [Test sınıfı öznitelikler](#test_class_attributes)

  - [Test modül öznitelikleri](#test_module_attributes)

  - [Önceden tanımlı öznitelikleri](#pre_defined_attributes)

    [CppUnitTestAssert.h](#cppUnitTestAssert_h)

  - [Genel onaylar](#general_asserts)

    -   [Eşit](#general_are_equal)

    -   [Eşit değildir](#general_are_not_equal)

    -   [Aynı](#general_are_same)

    -   [Aynı değil](#general_are_not_same)

    -   [Null](#general_is_null)

    -   [Null değil](#general_is_not_null)

    -   [Geçerlidir](#general_is_True)

    -   [Yanlış](#general_is_false)

    -   [Başarısız](#general_Fail)

  - [Windows çalışma zamanı onaylar](#winrt_asserts)

    -   [Eşit](#winrt_are_equal)

    -   [Aynı](#winrt_are_same)

    -   [Eşit değildir](#winrt_are_not_equal)

    -   [Aynı değil](#winrt_are_not_same)

    -   [Null](#winrt_is_null)

    -   [Null değil](#winrt_is_not_null)

  - [Özel durum onaylar](#exception_asserts)

    - [Özel durum beklediğiniz](#expect_exception)

      [CppUnitTestLogger.h](#cppunittestlogger_h)

    - [Günlükçü](#logger)

    - [İleti Yaz](#write_message)

  - [Kullanım örneği](#example)

##  <a name="cppUnitTest_h"></a> CppUnitTest.h

###  <a name="create_test_classes_and_methods"></a> Test sınıflar ve yöntemler oluşturma

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

###  <a name="Initialize_and_cleanup"></a> Başlatma ve temizleme

####  <a name="test_methods"></a> Test yöntemleri

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

####  <a name="test_classes"></a> Test sınıfları

```cpp
TEST_CLASS_INITIALIZE(methodName)
{
    // test class initialization  code
}
```

 Tanımlar *methodName* her test sınıfı oluşturulmadan önce çalıştırılan bir yöntem olarak. `TEST_CLASS_INITIALIZE` yalnızca bir kez bir test sınıfında tanımlanabilir ve test sınıfı kapsamında tanımlanmış olması gerekir.

```cpp
TEST_CLASS_CLEANUP(methodName)
{
    // test class cleanup  code
}
```

 Tanımlar *methodName* her test sınıfı oluşturulduktan sonra çalıştırılan bir yöntem olarak. `TEST_CLASS_CLEANUP` yalnızca bir kez bir test sınıfında tanımlanabilir ve test sınıfı kapsamında tanımlanmış olması gerekir.

####  <a name="test_modules"></a> Test modülleri

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

###  <a name="create_test_attributes"></a> Test öznitelikleri oluşturma

####  <a name="test_method_attributes"></a> Test yöntemi öznitelikleri

```cpp
BEGIN_TEST_METHOD_ATTRIBUTE(testMethodName)
    TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_METHOD_ATTRIBUTE()
```

 Bir veya daha fazla tanımlanan öznitelik ekler `TEST_METHOD_ATTRIBUTE` makroları test yöntemi *testClassName*.

 A `TEST_METHOD_ATTRIBUTE` makrosunu tanımlayan bir öznitelik adı ile *attributeName* ve değer *attributeValue*.

####  <a name="test_class_attributes"></a> Test sınıfı öznitelikler

```cpp
BEGIN_TEST_CLASS_ATTRIBUTE(testClassName)
    TEST_CLASS_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_CLASS_ATTRIBUTE()
```

 Bir veya daha fazla tanımlanan öznitelik ekler `TEST_CLASS_ATTRIBUTE` makroları test sınıfına *testClassName*.

 A `TEST_CLASS_ATTRIBUTE` makrosunu tanımlayan bir öznitelik adı ile *attributeName* ve değer *attributeValue*.

####  <a name="test_module_attributes"></a> Test modül öznitelikleri

```cpp
BEGIN_TEST_MODULE_ATTRIBUTE(testModuleName)
    TEST_MODULE_ATTRIBUTE(attributeName, attributeValue)
    ...
END_TEST_MODULE_ATTRIBUTE()
```

 Bir veya daha fazla tanımlanan öznitelik ekler `TEST_MODULE_ATTRIBUTE` makroları test modülüne *testModuleName*.

 A `TEST_MODULE_ATTRIBUTE` makrosunu tanımlayan bir öznitelik adı ile *attributeName* ve değer *attributeValue*.

####  <a name="pre_defined_attributes"></a> Önceden tanımlı öznitelikleri
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

##  <a name="cppUnitTestAssert_h"></a> CppUnitTestAssert.h

###  <a name="general_asserts"></a> Genel onaylar

####  <a name="general_are_equal"></a> Eşit
 İki nesnenin eşit olup olmadığını doğrulayın

```cpp
template<typename T>
static void Assert::AreEqual(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 İki çiftten eşit olduğunu doğrulayın

```cpp
static void Assert::AreEqual(
    double expected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 İki floattan eşit olduğunu doğrulayın

```cpp
static void Assert::AreEqual(
    float expected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 İki char * dizelerin eşit olduğunu doğrulayın

```cpp
static void Assert::AreEqual(
    const char* expected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 İki w_char * dizelerin eşit olduğunu doğrulayın

```cpp
static void Assert::AreEqual(
    const wchar_t* expected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

####  <a name="general_are_not_equal"></a> Eşit değildir
 İki çiftten eşit olmadığını doğrulayın

```cpp
static void Assert::AreNotEqual(
    double notExpected,
    double actual,
    double tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 İki floattan eşit olmadığını doğrulayın

```cpp
static void Assert::AreNotEqual(
    float notExpected,
    float actual,
    float tolerance,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 İki char * dizeler eşit olmadığını doğrulayın

```cpp
static void Assert::AreNotEqual(
    const char* notExpected,
    const char* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 İki w_char * dizeler eşit olmadığını doğrulayın

```cpp
static void Assert::AreNotEqual(
    const wchar_t* notExpected,
    const wchar_t* actual,
    bool ignoreCase = false,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

 İki başvuru operatörüne göre eşit olmadığını doğrulayın ==.

```cpp
template<typename T>
static void Assert::AreNotEqual(
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

####  <a name="general_are_same"></a> Aynı
 İki başvurunun aynı nesne örneği (kimlik) başvurduğunu doğrulayın.

```cpp
template<typename T>
static void Assert::AreSame(
    const T& expected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

####  <a name="general_are_not_same"></a> Aynı değil
 Aynı nesne örneği (kimlik) başvurmamasını iki başvuru doğrulayın.

```cpp
template<typename T>
static void Assert::AreNotSame (
    const T& notExpected,
    const T& actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

####  <a name="general_is_null"></a> Null
 Bir işaretçi NULL olduğundan emin olun.

```cpp
template<typename T>
static void Assert::IsNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

####  <a name="general_is_not_null"></a> Null değil
 Bir işaretçi NULL olmadığından emin olun

```cpp
template<typename T>
static void Assert::IsNotNull(
    const T* actual,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

####  <a name="general_is_True"></a> Geçerlidir
 Bir koşul doğru olduğundan emin olun

```cpp
static void Assert::IsTrue(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

####  <a name="general_is_false"></a> Yanlış
 Bir koşul false olduğundan emin olun

```cpp
static void Assert::IsFalse(
    bool condition,
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

####  <a name="general_Fail"></a> Başarısız
 Test çalışması sonucu başarısız olarak zorla

```cpp
static void Assert::Fail(
    const wchar_t* message = NULL,
    const __LineInfo* pLineInfo = NULL)
```

###  <a name="winrt_asserts"></a> Windows çalışma zamanı onaylar

####  <a name="winrt_are_equal"></a> Eşit
 İki Windows çalışma zamanı işaretçileri eşit olduğunu doğrular.

```cpp
template<typename T>
static void Assert::AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

 Bu iki doğrular Platform::String ^ dizeler eşit.

```cpp
template<typename T>
static void Assert::AreEqual(
    T^ expected,
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

####  <a name="winrt_are_same"></a> Aynı
 İki Windows Runtime başvuru aynı nesneye referans gösterdiğini doğrular.

```cpp
template<typename T>
static void Assert::AreSame(
    T% expected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

####  <a name="winrt_are_not_equal"></a> Eşit değildir
 İki Windows çalışma zamanı işaretçileri eşit olmadığını doğrular.

```cpp
template<typename T>
static void Assert::AreNotEqual(
    T^ notExpected,
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

 Bu iki doğrular Platform::String ^ dizeler eşit değildir.

```cpp
static void Assert::AreNotEqual(
    Platform::String^ notExpected,
    Platform::String^ actual,
    bool ignoreCase = false,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

####  <a name="winrt_are_not_same"></a> Aynı değil
 İki Windows Runtime başvuru aynı nesneye başvurma doğrular.

```cpp
template<typename T>
static void Assert::AreNotSame(
    T% notExpected,
    T% actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

####  <a name="winrt_is_null"></a> Null
 Bir Windows çalışma zamanı işaretçi bir nullptr olduğunu doğrular.

```cpp
template<typename T>
static void Assert::IsNull(
    T^ actual,
    Platform::String^ message = nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

####  <a name="winrt_is_not_null"></a> Null değil
 Bir Windows çalışma zamanı işaretçi bir nullptr olmadığını doğrular.

```cpp
template<typename T>
static void Assert::IsNotNull(
    T^ actual,
    Platform::String^ message= nullptr,
    const __LineInfo* pLineInfo= nullptr)
```

###  <a name="exception_asserts"></a> Özel durum onaylar

####  <a name="expect_exception"></a> Özel durum beklediğiniz
 Bir işlev özel durum harekete doğrulayın:

```cpp
template<typename _EXPECTEDEXCEPTION, typename _FUNCTOR>
static void Assert::ExpectException(
    _FUNCTOR functor,
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo= NULL)
```

 Bir işlev özel durum harekete doğrulayın:

```cpp
template<typename _EXPECTEDEXCEPTION, typename _RETURNTYPE>
    static void Assert::ExpectException(
    _RETURNTYPE (*func)(),
    const wchar_t* message= NULL,
    const __LineInfo* pLineInfo = NULL)
```

##  <a name="cppunittestlogger_h"></a> CppUnitTestLogger.h

###  <a name="logger"></a> Günlükçü
 Günlükçü sınıfı yazmak için statik yöntemler içeren **çıkış penceresine**.

###  <a name="write_message"></a> İleti Yaz
Bir dizeye yaz **çıkış penceresi**

```cpp
static void Logger::WriteMessage(const wchar_t* message)
```

```cpp
static void Logger::WriteMessage(const char* message)
```

## <a name="example"></a> Örnek
 Bu kod, VSCppUnit kullanım örneğidir. Bu örnekler öznitelik meta verileri, armatürleri, onaylamalar ve özel günlük kaydı ile birim testleri içerir.

```cpp
// USAGE EXAMPLE

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

## <a name="see-also"></a>Ayrıca bkz.

- [Birim testi kod](../test/unit-test-your-code.md)
- [C/C++ için birim testleri yazma](writing-unit-tests-for-c-cpp.md)

