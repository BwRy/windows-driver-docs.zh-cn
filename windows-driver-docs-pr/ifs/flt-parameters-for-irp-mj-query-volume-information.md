---
title: IRP_MJ_QUERY_VOLUME_INFORMATION 联合的 FLT_PARAMETERS
description: 在 FLT 的 MajorFunction 字段\_IO\_参数\_操作的块结构时使用的联合组件是 IRP\_MJ\_查询\_卷\_信息。
ms.assetid: fc790885-a378-40dc-829d-94e75a7c6f13
keywords:
- IRP_MJ_QUERY_VOLUME_INFORMATION 联合可安装文件系统驱动程序的 FLT_PARAMETERS
- FLT_PARAMETERS 联合可安装文件系统驱动程序
- PFLT_PARAMETERS 联合指针可安装的文件系统驱动程序
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
ms.openlocfilehash: ffd2de1034314d996d899a9ad78c83effe1a7757
ms.sourcegitcommit: 4b7a6ac7c68e6ad6f27da5d1dc4deabd5d34b748
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72841356"
---
# <a name="flt_parameters-for-irp_mj_query_volume_information-union"></a>用于 IRP\_MJ\_查询\_卷\_信息联合的 FLT\_参数


在 FLT 的**MajorFunction**字段[ **\_IO\_参数\_** ](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/ns-fltkernel-_flt_io_parameter_block)操作的块结构时使用的联合组件是[**IRP\_MJ\_查询\_卷\_信息**](irp-mj-query-volume-information.md)。

<a name="syntax"></a>语法
------

```ManagedCPlusPlus
typedef union _FLT_PARAMETERS {
  ...    ;
  struct {
    ULONG                                  Length;
    FS_INFORMATION_CLASS POINTER_ALIGNMENT FsInformationClass;
  } QueryVolumeInformation;
  PVOID  VolumeBuffer;
  ...    ;
} FLT_PARAMETERS, *PFLT_PARAMETERS;
```

<a name="members"></a>成员
-------

**QueryVolumeInformation**  
包含以下成员的结构。

**长度**  
**VolumeBuffer**缓冲区的长度（以字节为单位）。

**FsInformationClass**  
文件系统返回的卷信息的类型。 下列情况之一：

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">值</th>
<th align="left">含义</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><a href="" id="filefsattributeinformation"></a>
<strong>FileFsAttributeInformation</strong></td>
<td align="left"><p>返回<a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/ns-ntddk-_file_fs_volume_information" data-raw-source="[&lt;strong&gt;FILE_FS_VOLUME_INFORMATION&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/ns-ntddk-_file_fs_volume_information)"><strong>FILE_FS_VOLUME_INFORMATION</strong></a> ，其中包含卷的相关信息，例如卷标、序列号和创建时间。</p></td>
</tr>
<tr class="even">
<td align="left"><a href="" id="filefscontrolinformation"></a>
<strong>FileFsControlInformation</strong></td>
<td align="left"><p>返回一个<a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/ns-ntifs-_file_fs_control_information" data-raw-source="[&lt;strong&gt;FILE_FS_CONTROL_INFORMATION&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/ns-ntifs-_file_fs_control_information)"><strong>FILE_FS_CONTROL_INFORMATION</strong></a>结构，该结构包含有关卷的文件系统控制信息。</p></td>
</tr>
<tr class="odd">
<td align="left"><a href="" id="filefsdeviceinformation"></a>
<strong>FileFsDeviceInformation</strong></td>
<td align="left"><p>返回<a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/ns-wdm-_file_fs_device_information" data-raw-source="[&lt;strong&gt;FILE_FS_DEVICE_INFORMATION&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/ns-wdm-_file_fs_device_information)"><strong>FILE_FS_DEVICE_INFORMATION</strong></a>结构，该结构包含卷的设备信息。</p></td>
</tr>
<tr class="even">
<td align="left"><a href="" id="filefsdriverpathinformation"></a>
<strong>FileFsDriverPathInformation</strong></td>
<td align="left"><p>返回一个<a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/ns-ntifs-_file_fs_driver_path_information" data-raw-source="[&lt;strong&gt;FILE_FS_DRIVER_PATH_INFORMATION&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/ns-ntifs-_file_fs_driver_path_information)"><strong>FILE_FS_DRIVER_PATH_INFORMATION</strong></a>结构，该结构包含有关指定的驱动程序是否位于该卷的 i/o 路径中的信息。 在将 IRP 发送到文件系统卷设备堆栈之前，IRP_MJ_QUERY_VOLUME_INFORMATION 请求的发起方必须将驱动程序的名称存储到 FILE_FS_DRIVER_PATH_INFORMATION 结构中。</p></td>
</tr>
<tr class="odd">
<td align="left"><a href="" id="filefsfullsizeinformation"></a>
<strong>FileFsFullSizeInformation</strong></td>
<td align="left"><p>返回<a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/ns-ntddk-_file_fs_full_size_information" data-raw-source="[&lt;strong&gt;FILE_FS_FULL_SIZE_INFORMATION&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/ns-ntddk-_file_fs_full_size_information)"><strong>FILE_FS_FULL_SIZE_INFORMATION</strong></a>结构，该结构包含有关卷上可用空间总量的信息。</p></td>
</tr>
<tr class="even">
<td align="left"><a href="" id="filefsobjectidinformation"></a>
<strong>FileFsObjectIdInformation</strong></td>
<td align="left"><p>返回<a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/ns-ntddk-_file_fs_objectid_information" data-raw-source="[&lt;strong&gt;FILE_FS_OBJECTID_INFORMATION&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/ns-ntddk-_file_fs_objectid_information)"><strong>FILE_FS_OBJECTID_INFORMATION</strong></a>结构，该结构包含卷的特定于文件的对象 ID 信息。 请注意，这与操作系统分配的（全局唯一标识符 [GUID]）唯一卷名称不同。</p></td>
</tr>
<tr class="odd">
<td align="left"><a href="" id="filefssizeinformation"></a>
<strong>FileFsSizeInformation</strong></td>
<td align="left"><p>返回一个<a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/ns-ntddk-_file_fs_size_information" data-raw-source="[&lt;strong&gt;FILE_FS_SIZE_INFORMATION&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/ns-ntddk-_file_fs_size_information)"><strong>FILE_FS_SIZE_INFORMATION</strong></a>结构，该结构包含有关卷上的空间量的信息，该信息可供与发出 IRP_MJ_QUERY_VOLUME_INFORMATION 请求的线程关联的用户使用。</p></td>
</tr>
<tr class="even">
<td align="left"><a href="" id="filefsvolumeinformation"></a>
<strong>FileFsVolumeInformation</strong></td>
<td align="left"><p>返回<a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/ns-ntddk-_file_fs_volume_information" data-raw-source="[&lt;strong&gt;FILE_FS_VOLUME_INFORMATION&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/ns-ntddk-_file_fs_volume_information)"><strong>FILE_FS_VOLUME_INFORMATION</strong></a> ，其中包含卷的相关信息，例如卷标、序列号和创建时间。</p></td>
</tr>
<tr class="odd">
<td align="left"><a href="" id="filefssectorsizeinformation"></a>
<strong>FileFsSectorSizeInformation</strong></td>
<td align="left"><p>返回<a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/ns-ntifs-_file_fs_driver_path_information" data-raw-source="[&lt;strong&gt;FILE_FS_SECTOR_SIZE_INFORMATION&lt;/strong&gt;](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/ns-ntifs-_file_fs_driver_path_information)"><strong>FILE_FS_SECTOR_SIZE_INFORMATION</strong></a>结构，该结构包含有关卷的物理扇区大小和逻辑扇区大小的信息。</p></td>
</tr>
</tbody>
</table>

 

**VolumeBuffer**  
一个指针，指向要在其中返回卷信息的输出缓冲区。

<a name="remarks"></a>备注
-------

IRP\_MJ\_查询的[**FLT\_参数**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/ns-fltkernel-_flt_parameters)结构\_卷\_信息操作包含由回调数据（[**FLT\_回调\_数据**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/ns-fltkernel-_flt_callback_data)）结构表示的基于 IRP 的查询-信息操作的参数。 它包含在 FLT\_IO\_参数\_块结构。

IRP\_MJ\_查询\_卷\_信息是基于 IRP 的操作。

<a name="requirements"></a>要求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"><p>标头</p></td>
<td align="left">Fltkernel （包括 Fltkernel）</td>
</tr>
</tbody>
</table>

## <a name="see-also"></a>另请参阅


[**文件\_FS\_属性\_信息**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/ns-ntifs-_file_fs_attribute_information)

[**文件\_FS\_控制\_信息**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/ns-ntifs-_file_fs_control_information)

[**文件\_FS\_设备\_信息**](https://docs.microsoft.com/windows-hardware/drivers/ddi/wdm/ns-wdm-_file_fs_device_information)

[**文件\_FS\_驱动程序\_路径\_信息**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntifs/ns-ntifs-_file_fs_driver_path_information)

[**文件\_FS\_完整\_大小\_信息**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/ns-ntddk-_file_fs_full_size_information)

[**文件\_FS\_OBJECTID\_信息**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/ns-ntddk-_file_fs_objectid_information)

**文件\_fs\_扇区\_大小\_信息**
[**文件\_FS\_大小\_信息**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/ns-ntddk-_file_fs_size_information)

[**文件\_FS\_卷\_信息**](https://docs.microsoft.com/windows-hardware/drivers/ddi/ntddk/ns-ntddk-_file_fs_volume_information)

[**FLT\_回调\_数据**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/ns-fltkernel-_flt_callback_data)

[**FLT\_IO\_参数\_块**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/ns-fltkernel-_flt_io_parameter_block)

[**FLT\_\_FASTIO\_操作**](https://docs.microsoft.com/windows-hardware/drivers/ddi/index)

[**FLT\_\_FS\_筛选器\_操作**](https://docs.microsoft.com/previous-versions/ff544648(v=vs.85))

[**FLT\_\_IRP\_操作**](https://docs.microsoft.com/previous-versions/ff544654(v=vs.85))

[**FLT\_参数**](https://docs.microsoft.com/windows-hardware/drivers/ddi/fltkernel/ns-fltkernel-_flt_parameters)

[**IRP\_MJ\_查询\_信息**](irp-mj-query-information.md)

[**ZwQueryVolumeInformationFile**](https://msdn.microsoft.com/library/windows/hardware/ff567070)

 

 






