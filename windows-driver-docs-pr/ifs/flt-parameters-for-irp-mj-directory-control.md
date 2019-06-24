---
title: FLT_PARAMETERS IRP_MJ_DIRECTORY_CONTROL 联合
description: 联合组件时使用 FLT MajorFunction 字段\_IO\_参数\_操作的块结构是 IRP\_MJ\_DIRECTORY\_控件。
ms.assetid: 3dadd64b-7e93-4c75-808d-2f26edb3ebd7
keywords:
- FLT_PARAMETERS IRP_MJ_DIRECTORY_CONTROL 联合可安装文件系统驱动程序
- FLT_PARAMETERS 联合可安装文件系统驱动程序
- PFLT_PARAMETERS 联合指针可安装文件系统驱动程序
topic_type:
- apiref
api_name:
- FLT_PARAMETERS
api_location:
- fltkernel.h
api_type:
- HeaderDef
ms.date: 11/28/2017
ms.localizationpriority: medium
ms.openlocfilehash: 68a729a2977356e243b4fe3ab6ddbb4455b8edde
ms.sourcegitcommit: 0cc5051945559a242d941a6f2799d161d8eba2a7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63365019"
---
# <a name="fltparameters-for-irpmjdirectorycontrol-union"></a>FLT\_IRP 的参数\_MJ\_DIRECTORY\_控件联合


联合组件时使用**MajorFunction**字段[ **FLT\_IO\_参数\_阻止**](https://msdn.microsoft.com/library/windows/hardware/ff544638)结构操作已[ **IRP\_MJ\_目录\_控制**](irp-mj-directory-control.md)。

<a name="syntax"></a>语法
------

```ManagedCPlusPlus
typedef union _FLT_PARAMETERS {
  ...   ;
  union {
    struct {
      ULONG                   Length;
      PUNICODE_STRING         FileName;
      FILE_INFORMATION_CLASS  FileInformationClass;
      ULONG POINTER_ALIGNMENT FileIndex;
      PVOID                   DirectoryBuffer;
      PMDL                    MdlAddress;
    } QueryDirectory;
    struct {
      ULONG                   Length;
      ULONG POINTER_ALIGNMENT CompletionFilter;
      ULONG                   Spare1;
      ULONG POINTER_ALIGNMENT Spare2;
      PVOID                   DirectoryBuffer;
      PMDL                    MdlAddress;
    } NotifyDirectory;
  } DirectoryControl;
  ...   ;
} FLT_PARAMETERS, *PFLT_PARAMETERS;
```

<a name="members"></a>成员
-------

**DirectoryControl**  
结构，它包含以下成员。

**QueryDirectory**  
联合组件用于 IRP\_MN\_查询\_目录操作。

**长度**  
缓冲区的长度，以字节为单位，该**QueryDirectory.DirectoryBuffer**成员指向。

**FileName**  
指向[ **UNICODE\_字符串**](https://msdn.microsoft.com/library/windows/hardware/ff564879)结构，其中包含指定的目录中的文件的名称。

**FileInformationClass**  
指定其中一个如下所述的值。

| ReplTest1                          | 含义                                                                                                                   |
|--------------------------------|---------------------------------------------------------------------------------------------------------------------------|
| FileBothDirectoryInformation   | 返回[**文件\_两者\_DIR\_信息**](https://msdn.microsoft.com/library/windows/hardware/ff540235)为每个文件的结构。                      |
| FileDirectoryInformation       | 返回[**文件\_DIRECTORY\_信息**](https://msdn.microsoft.com/library/windows/hardware/ff540248)为每个文件的结构。                     |
| FileFullDirectoryInformation   | 返回[**文件\_完整\_DIR\_信息**](https://msdn.microsoft.com/library/windows/hardware/ff540289)为每个文件的结构。                      |
| FileIdBothDirectoryInformation | 返回[**文件\_ID\_同时\_DIR\_信息**](https://msdn.microsoft.com/library/windows/hardware/ff540303)为每个文件的结构。               |
| FileIdFullDirectoryInformation | 返回[**文件\_ID\_完整\_DIR\_信息**](https://msdn.microsoft.com/library/windows/hardware/ff540310)为每个文件的结构。               |
| FileNamesInformation           | 返回[**文件\_名称\_信息**](https://msdn.microsoft.com/library/windows/hardware/ff540329)为每个文件的结构。                             |
| FileObjectIdInformation        | 返回[**文件\_OBJECTID\_信息**](https://msdn.microsoft.com/library/windows/hardware/ff540335)为每个文件的结构。                       |
| FileReparsePointInformation    | 返回单个[**文件\_重新分析\_点\_信息**](https://msdn.microsoft.com/library/windows/hardware/ff540354)目录结构。 |

 

**FileIndex**  
目录扫描的开始处的文件的索引。 已忽略的如果 SL\_索引\_未设置指定标志。 不能在任何 Win32 函数或内核模式下支持例程中指定此参数。 当前它只能由仅在 32 位基于 NT 的操作系统存在的 NT 虚拟 DOS 机 (NTVDM) 使用。 请注意，文件索引的文件系统，如 NTFS，在其中的父目录中的文件的位置不固定的可以在任何时维护排序顺序更改未定义。

**DirectoryBuffer**  
指向接收内容的目录的请求的有关的调用方提供输出缓冲区的指针。

**MdlAddress**  
描述缓冲区的内存描述符列表 (MDL) 的地址， **QueryDirectory.DirectoryBuffer**成员指向。 此成员是可选的可以是**NULL**。

**NotifyDirectory**  
联合组件用于 IRP\_MN\_通知\_更改\_目录操作。

**长度**  
缓冲区的长度，以字节为单位，该**NotifyDirectory.DirectoryBuffer**成员指向。

**CompletionFilter**  
指定到文件或目录应导致 Irp，若要完成的通知列表中的更改类型的标志的位掩码。 介绍了以下可能的标志值。

| Flag                                | 含义                                                                        |
|-------------------------------------|--------------------------------------------------------------------------------|
| 文件\_通知\_更改\_文件\_名称    | 已添加、 删除，或在此目录中重命名文件。                  |
| 文件\_通知\_更改\_DIR\_名称     | 已创建、 删除或重命名了一个子目录。                          |
| 文件\_通知\_更改\_名称          | 此目录的名称已更改。                                             |
| 文件\_通知\_更改\_属性    | 该文件，例如上次访问时间的属性的值已更改。 |
| 文件\_通知\_更改\_大小          | 此文件的大小已更改。                                                  |
| 文件\_通知\_更改\_最后一个\_编写   | 此文件的上次修改时间已更改。                                |
| 文件\_通知\_更改\_最后一个\_访问  | 此文件的上次访问时间已更改。                                      |
| 文件\_通知\_更改\_创建      | 此文件的创建时间已更改。                                         |
| 文件\_通知\_更改\_EA            | 此文件的扩展的属性已被修改。                            |
| 文件\_通知\_更改\_安全      | 此文件的安全信息已更改。                                  |
| 文件\_通知\_更改\_流\_名称  | 已添加、 删除，或在此目录中重命名文件流。           |
| 文件\_通知\_更改\_流\_大小  | 此文件流的大小已更改。                                           |
| 文件\_通知\_更改\_流\_编写 | 此文件流数据已更改。                                           |

 

**Spare1**  
当前未使用。

**Spare2**  
当前未使用。

**DirectoryBuffer**  
指向接收内容的目录的请求的有关的调用方提供输出缓冲区的指针。

**MdlAddress**  
描述缓冲区 MDL 地址的**NotifyDirectory.DirectoryBuffer**成员指向。 此成员是可选的可以是**NULL**。

<a name="remarks"></a>备注
-------

[ **FLT\_参数**](https://msdn.microsoft.com/library/windows/hardware/ff544673)结构 IRP\_MJ\_DIRECTORY\_控制操作包含基于 IRP 的参数表示的回调数据的控件的目录信息操作 ([**FLT\_回调\_数据**](https://msdn.microsoft.com/library/windows/hardware/ff544620)) 结构。 包含在 FLT\_IO\_参数\_块结构。

IRP\_MJ\_DIRECTORY\_控件是一个基于 IRP 的操作。

<a name="requirements"></a>要求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>Header</p></td>
<td align="left">Fltkernel.h （包括 Fltkernel.h）</td>
</tr>
</tbody>
</table>

## <a name="see-also"></a>请参阅


[**文件\_两者\_DIR\_信息**](https://msdn.microsoft.com/library/windows/hardware/ff540235)

[**文件\_DIRECTORY\_信息**](https://msdn.microsoft.com/library/windows/hardware/ff540248)

[**文件\_完整\_DIR\_信息**](https://msdn.microsoft.com/library/windows/hardware/ff540289)

[**文件\_ID\_同时\_DIR\_信息**](https://msdn.microsoft.com/library/windows/hardware/ff540303)

[**文件\_ID\_完整\_DIR\_信息**](https://msdn.microsoft.com/library/windows/hardware/ff540310)

[**文件\_名称\_信息**](https://msdn.microsoft.com/library/windows/hardware/ff540329)

[**文件\_OBJECTID\_信息**](https://msdn.microsoft.com/library/windows/hardware/ff540335)

[**FILE\_REPARSE\_POINT\_INFORMATION**](https://msdn.microsoft.com/library/windows/hardware/ff540354)

[**FLT\_CALLBACK\_DATA**](https://msdn.microsoft.com/library/windows/hardware/ff544620)

[**FLT\_IO\_PARAMETER\_BLOCK**](https://msdn.microsoft.com/library/windows/hardware/ff544638)

[**FLT\_IS\_FASTIO\_OPERATION**](https://msdn.microsoft.com/library/windows/hardware/ff544645)

[**FLT\_IS\_FS\_FILTER\_OPERATION**](https://msdn.microsoft.com/library/windows/hardware/ff544648)

[**FLT\_IS\_IRP\_操作**](https://msdn.microsoft.com/library/windows/hardware/ff544654)

[**FLT\_PARAMETERS**](https://msdn.microsoft.com/library/windows/hardware/ff544673)

[**FltNotifyFilterChangeDirectory**](https://msdn.microsoft.com/library/windows/hardware/ff543377)

[**FsRtlNotifyFilterChangeDirectory**](https://msdn.microsoft.com/library/windows/hardware/ff547010)

[**FsRtlNotifyFilterReportChange**](https://msdn.microsoft.com/library/windows/hardware/ff547018)

[**FsRtlNotifyFullChangeDirectory**](https://msdn.microsoft.com/library/windows/hardware/ff547026)

[**FsRtlNotifyFullReportChange**](https://msdn.microsoft.com/library/windows/hardware/ff547041)

[**IRP\_MJ\_DIRECTORY\_控件**](irp-mj-directory-control.md)

[**ZwQueryDirectoryFile**](https://msdn.microsoft.com/library/windows/hardware/ff567047)

 

 





