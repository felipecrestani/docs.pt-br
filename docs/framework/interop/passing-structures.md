---
title: Passando estruturas
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- platform invoke, calling unmanaged functions
ms.assetid: 9b92ac73-32b7-4e1b-862e-6d8d950cf169
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3764916263f6f88615d61badaf2c32807bcc09b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="passing-structures"></a>Passando estruturas
Muitas funções não gerenciadas esperam que você passe, como um parâmetro para a função, membros de estruturas (tipos definidos pelo usuário no Visual Basic) ou membros de classes que são definidas em código gerenciado. Ao passar estruturas ou classes para código não gerenciado usando invocação de plataforma, você deve fornecer informações adicionais para preservar o layout original e o alinhamento. Este tópico apresenta o atributo <xref:System.Runtime.InteropServices.StructLayoutAttribute>, que você usa para definir tipos formatados. Para classes e estruturas gerenciadas, você pode selecionar vários comportamentos de layout previsível fornecidos pela enumeração **LayoutKind**.  
  
 Há uma diferença importante entre tipos de estrutura e classe que e central para os conceitos apresentados neste tópico. Estruturas são tipos de valor e classes são tipos de referência – classes sempre fornecem pelo menos um nível de indireção de memória (um ponteiro para um valor). Essa diferença é importante porque funções não gerenciadas geralmente exigem indireção, conforme mostrado pelas assinaturas na primeira coluna da tabela a seguir. A estrutura gerenciada e as declarações de classe nas colunas restantes mostram o grau em que você pode ajustar o nível de indireção na sua declaração. Declarações são fornecidas para o Visual Basic e Visual C#.  
  
|Assinatura não gerenciada|Declaração gerenciada: <br />sem indireção<br />`Structure MyType`<br />`struct MyType;`|Declaração gerenciada: <br />um nível de indireção<br />`Class MyType`<br />`class MyType;`|  
|-------------------------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|  
|`DoWork(MyType x);`<br /><br /> Demanda zero níveis de indireção.|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> Adiciona zero níveis de indireção.|Não é possível porque já existe um nível de indireção.|  
|`DoWork(MyType* x);`<br /><br /> Demanda um nível de indireção.|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> Adiciona um nível de indireção.|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> Adiciona zero níveis de indireção.|  
|`DoWork(MyType** x);`<br /><br /> Demanda dois níveis de indireção.|Não é possível porque **ByRef** **ByRef** ou `ref` `ref` não pode ser usado.|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> Adiciona um nível de indireção.|  
  
 A tabela descreve as diretrizes a seguir para declarações de invocação de plataforma:  
  
-   Use uma estrutura passada por valor quando a função não gerenciada não demanda nenhuma indireção.  
  
-   Use uma estrutura passada por referência ou uma classe passada por valor quando a função não gerenciada demanda um nível de indireção.  
  
-   Use uma classe passada por referência quando a função não gerenciada demanda dois níveis de indireção.  
  
## <a name="declaring-and-passing-structures"></a>Declarando e passando estruturas  
 O exemplo a seguir mostra como definir as estruturas `Point` e `Rect` em código gerenciado e passar tipos como parâmetro para a função **PtInRect** no arquivo User32.dll. **PtInRect** tem a seguinte assinatura não gerenciada:  
  
```  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 Observe que você deve passar a estrutura Rect por referência, pois a função espera um ponteiro para um tipo RECT.  
  
```vb  
Imports System.Runtime.InteropServices  
  
<StructLayout(LayoutKind.Sequential)> Public Structure Point  
    Public x As Integer  
    Public y As Integer  
End Structure  
  
Public Structure <StructLayout(LayoutKind.Explicit)> Rect  
    <FieldOffset(0)> Public left As Integer  
    <FieldOffset(4)> Public top As Integer  
    <FieldOffset(8)> Public right As Integer  
    <FieldOffset(12)> Public bottom As Integer  
End Structure  
  
Class Win32API      
    Declare Auto Function PtInRect Lib "user32.dll" _  
    (ByRef r As Rect, p As Point) As Boolean  
End Class  
```  
  
```csharp  
using System.Runtime.InteropServices;  
  
[StructLayout(LayoutKind.Sequential)]  
public struct Point {  
    public int x;  
    public int y;  
}     
  
[StructLayout(LayoutKind.Explicit)]  
public struct Rect {  
    [FieldOffset(0)] public int left;  
    [FieldOffset(4)] public int top;  
    [FieldOffset(8)] public int right;  
    [FieldOffset(12)] public int bottom;  
}     
  
class Win32API {  
    [DllImport("User32.dll")]  
    public static extern bool PtInRect(ref Rect r, Point p);  
}  
```  
  
## <a name="declaring-and-passing-classes"></a>Declarando e passando classes  
 Você pode passar membros de uma classe para uma função de DLL não gerenciada, desde que a classe tenha um layout de membro fixo. O exemplo a seguir demonstra como passar membros da classe `MySystemTime`, que são definidos em ordem sequencial, para o **GetSystemTime** no arquivo User32.dll. **GetSystemTime** tem a seguinte assinatura não gerenciada:  
  
```  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 Diferentemente dos tipos de valor, classes sempre têm pelo menos um nível de indireção.  
  
```vb  
Imports System  
Imports System.Runtime.InteropServices  
Imports Microsoft.VisualBasic  
  
<StructLayout(LayoutKind.Sequential)> Public Class MySystemTime  
    Public wYear As Short  
    Public wMonth As Short  
    Public wDayOfWeek As Short   
    Public wDay As Short  
    Public wHour As Short  
    Public wMinute As Short  
    Public wSecond As Short  
    Public wMiliseconds As Short  
End Class  
  
Public Class Win32  
    Declare Auto Sub GetSystemTime Lib "Kernel32.dll"(sysTime _  
        As MySystemTime)  
    Declare Auto Function MessageBox Lib "User32.dll"(hWnd As IntPtr, _  
        txt As String, caption As String, Typ As Integer) As Integer  
End Class  
  
Public Class TestPlatformInvoke      
    Public Shared Sub Main()  
        Dim sysTime As New MySystemTime()  
        Win32.GetSystemTime(sysTime)  
  
        Dim dt As String  
        dt = "System time is:" & ControlChars.CrLf & _  
              "Year: " & sysTime.wYear & _  
              ControlChars.CrLf & "Month: " & sysTime.wMonth & _  
              ControlChars.CrLf & "DayOfWeek: " & sysTime.wDayOfWeek & _  
              ControlChars.CrLf & "Day: " & sysTime.wDay  
        Win32.MessageBox(IntPtr.Zero, dt, "Platform Invoke Sample", 0)        
    End Sub  
End Class  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public class MySystemTime {  
    public ushort wYear;   
    public ushort wMonth;  
    public ushort wDayOfWeek;   
    public ushort wDay;   
    public ushort wHour;   
    public ushort wMinute;   
    public ushort wSecond;   
    public ushort wMilliseconds;   
}  
class Win32API {  
    [DllImport("Kernel32.dll")]  
    public static extern void GetSystemTime(MySystemTime st);  
  
    [DllImport("user32.dll", CharSet=CharSet.Auto)]  
     public static extern int MessageBox(IntPtr hWnd,  
         string text, string caption, int options);  
}  
  
public class TestPlatformInvoke  
{  
    public static void Main()  
    {  
        MySystemTime sysTime = new MySystemTime();  
        Win32API.GetSystemTime(sysTime);  
  
        string dt;  
        dt = "System time is: \n" +  
              "Year: " + sysTime.wYear + "\n" +  
              "Month: " + sysTime.wMonth + "\n" +  
              "DayOfWeek: " + sysTime.wDayOfWeek + "\n" +  
              "Day: " + sysTime.wDay;  
        Win32API.MessageBox(IntPtr.Zero, dt, "Platform Invoke Sample", 0);  
    }  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Chamando uma função de DLL](../../../docs/framework/interop/calling-a-dll-function.md)  
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>  
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>  
 <xref:System.Runtime.InteropServices.FieldOffsetAttribute>
