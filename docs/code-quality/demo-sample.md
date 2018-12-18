---
title: Örnek C++ projesi için kod çözümleme
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: sample
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: aafbaaf682852adaea8f20a1373ea1ae4b025fad
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704869"
---
# <a name="sample-c-project-for-code-analysis"></a>Örnek C++ projesi için kod çözümleme

Bu aşağıdaki yordamlar örneğe oluşturulacağını gösterir [izlenecek yol: C/C++ analiz kod kusurları için](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md). Yordamları oluşturun:

- CppDemo adlı bir Visual Studio çözümü.

- CodeDefects adlı bir statik kitaplık projesi oluşturun.

- Ek açıklamalar adlı bir statik kitaplık projesi oluşturun.

Yordamlar, kod ayrıca üst bilgi sağlar. ve *.cpp* statik kitaplıklar için dosyaları.

## <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>CppDemo çözüm ve CodeDefects proje oluşturma

1. Tıklatın **dosya** menüsündeki **yeni**ve ardından **yeni proje**.

2. İçinde **proje türleri** ağaç listesi, Visual C++ VS varsayılan dilde değilse genişletin **diğer diller**.

3. Genişletme **Visual C++** ve ardından **genel**.

4. İçinde **şablonları**, tıklatın **boş proje**.

5. İçinde **adı** metin kutusunda, **CodeDefects**.

6. Seçin **çözüm için dizin oluştur** onay kutusu.

7. İçinde **çözüm adı** metin kutusunda, **CppDemo**.

## <a name="configure-the-codedefects-project-as-a-static-library"></a>Statik kitaplık olarak CodeDefects projeyi yapılandırın

1. Çözüm Gezgini'nde sağ **CodeDefects** ve ardından **özellikleri**.

2. Genişletme **yapılandırma özellikleri** ve ardından **genel**.

3. İçinde **genel** listesinde, metni seçin sütunda yanına **hedef uzantısı**ve ardından **.lib**.

4. İçinde **Proje Varsayılanları**, sütun tıklayın **yapılandırma türü**ve ardından **statik Lib (.lib)**.

## <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>CodeDefects projesine üst bilgisinin ve kaynak dosyası ekleme

1. Çözüm Gezgini'nde genişletin **CodeDefects**, sağ **üstbilgi dosyaları**, tıklatın **Ekle**ve ardından **yeni öğe**.

2. İçinde **Yeni Öğe Ekle** iletişim kutusu, tıklatın **kod**ve ardından **üstbilgi dosyası (.h)**.

3. İçinde **adı** kutusuna **Bug.h** ve ardından **Ekle**.

4. Aşağıdaki kodu kopyalayın ve yapıştırın *Bug.h* dosyasını Visual Studio düzenleyicisinde.

    ```cpp
    #include <windows.h>

    //
    //These 3 functions are consumed by the sample
    //  but are not defined. This project cannot be linked!
    //

    bool CheckDomain( LPCSTR );
    HRESULT ReadUserAccount();

    //
    //These constants define the common sizes of the
    //  user account information throughout the program
    //

    const int USER_ACCOUNT_LEN = 256;
    const int ACCOUNT_DOMAIN_LEN = 128;
    ```

5. Çözüm Gezgini'nde sağ **kaynak dosyaları**, işaret **yeni**ve ardından **yeni öğe**.

6. İçinde **Yeni Öğe Ekle** iletişim kutusu, tıklatın **C++ dosyasına (.cpp)**

7. İçinde **adı** kutusuna **Bug.cpp** ve ardından **Ekle**.

8. Aşağıdaki kodu kopyalayın ve yapıştırın *Bug.cpp* dosyasını Visual Studio düzenleyicisinde.

    ```cpp
    #include <stdlib.h>
    #include "Bug.h"

    // the user account
    TCHAR g_userAccount[USER_ACCOUNT_LEN] = "";
    int len = 0;

    bool ProcessDomain()
    {
        TCHAR* domain = new TCHAR[ACCOUNT_DOMAIN_LEN];
        // ReadUserAccount gets a 'domain\user' input from
        //the user into the global 'g_userAccount'
        if (ReadUserAccount() )
        {

            // Copies part of the string prior to the '\'
            // character onto the 'domain' buffer
            for( len = 0 ; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != '\0') ; len++  )
            {
                if ( g_userAccount[len] == '\\' )
                {
                    // Stops copying on the domain and user separator ('\')
                    break;
                }
                domain[len] = g_userAccount[len];
            }
            if((len= ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))
            {
                // '\' was not found. Invalid domain\user string.
                delete [] domain;
                return false;
            }
            else
            {
                domain[len]='\0';
            }
            // Process domain string
            bool result = CheckDomain( domain );

            delete[] domain;
            return result;
        }
        return false;
    }

    int path_dependent(int n)
    {
        int i;
        int j;
        if (n == 0)
            i = 1;
        else
            j = 1;
        return i+j;
    }
    ```

9. Tıklatın **dosya** menüsüne ve ardından **Tümünü Kaydet**.

## <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>Ek açıklamalar proje ekleyin ve bir statik kitaplık yapılandırın

1. Çözüm Gezgini'nde tıklatın **CppDemo**, işaret **Ekle**ve ardından **yeni proje**.

2. İçinde **Yeni Proje Ekle** iletişim kutusunda, Visual C++'ı genişletin, **genel**ve ardından **boş proje**.

3. İçinde **adı** metin kutusunda, **ek açıklamaları**ve ardından **Ekle**.

4. Çözüm Gezgini'nde sağ **ek açıklamaları** ve ardından **özellikleri**.

5. Genişletme **yapılandırma özellikleri** ve ardından **genel**.

6. İçinde **genel** listesinde, metni seçin sütunda yanına **hedef uzantısı**ve ardından **.lib**.

7. İçinde **Proje Varsayılanları**, sütun tıklayın **yapılandırma türü**ve ardından **statik Lib (.lib)**.

## <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>Kaynak dosya ve üstbilgi dosyası ek açıklamaları projeye ekleyin

1. Çözüm Gezgini'nde genişletin **ek açıklamaları**, sağ **üstbilgi dosyaları**, tıklatın **Ekle**ve ardından **yeni öğe**.

2. İçinde **Yeni Öğe Ekle** iletişim kutusu, tıklatın **üstbilgi dosyası (.h)**.

3. İçinde **adı** kutusuna **annotations.h** ve ardından **Ekle**.

4. Aşağıdaki kodu kopyalayın ve yapıştırın *annotations.h* dosyasını Visual Studio düzenleyicisinde.

    ```cpp
    #include <CodeAnalysis/SourceAnnotations.h>

    struct LinkedList
    {
        struct LinkedList* next;
        int data;
    };

    typedef struct LinkedList LinkedList;

    [returnvalue:SA_Post( Null=SA_Maybe )] LinkedList* AllocateNode();

    ```

5. Çözüm Gezgini'nde sağ **kaynak dosyaları**, işaret **yeni**ve ardından **yeni öğe**.

6. İçinde **Yeni Öğe Ekle** iletişim kutusu, tıklatın **kod** ve ardından **C++ dosyasına (.cpp)**

7. İçinde **adı** kutusuna **annotations.cpp** ve ardından **Ekle**.

8. Aşağıdaki kodu kopyalayın ve yapıştırın *annotations.cpp* dosyasını Visual Studio düzenleyicisinde.

    ```cpp
    #include <CodeAnalysis/SourceAnnotations.h>
    #include <windows.h>
    #include <stdlib.h>
    #include "annotations.h"

    LinkedList* AddTail( LinkedList *node, int value )
    {
        LinkedList *newNode = NULL;

        // finds the last node
        while ( node->next != NULL )
        {
            node = node->next;
        }

        // appends the new node
        newNode = AllocateNode();
        newNode->data = value;
        newNode->next = 0;
        node->next = newNode;

        return newNode;
    }

    ```

9. Tıklatın **dosya** menüsüne ve ardından **Tümünü Kaydet**.
