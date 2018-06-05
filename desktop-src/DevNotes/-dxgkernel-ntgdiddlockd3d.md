---
Description: Used to lock a specified area of buffer memory and to provide a valid pointer to a block of memory associated with the buffer.
ms.assetid: 6f2ecefa-376c-4f6c-a031-666dd992f96a
title: NtGdiDdLockD3D function
ms.technology: desktop
ms.prod: windows
ms.author: windowssdkdev
ms.topic: article
ms.date: 05/31/2018
---

# NtGdiDdLockD3D function

\[This function is subject to change with each operating system revision. Instead, use the Microsoft DirectDraw and Microsoft Direct3DAPIs; these APIs insulate applications from such operating system changes, and hide many other difficulties involved in interacting directly with display drivers.\]

Used to lock a specified area of buffer memory and to provide a valid pointer to a block of memory associated with the buffer.

## Syntax


```C++
DWORD APIENTRY NtGdiDdLockD3D(
  _In_    HANDLE       hSurface,
  _Inout_ PDD_LOCKDATA puLockData
);
```



## Parameters

<dl> <dt>

*hSurface* \[in\]
</dt> <dd>

Pointer to a [**DD\_SURFACE\_LOCAL**](https://www.bing.com/search?q=**DD\_SURFACE\_LOCAL**) structure that describes the surface associated with the memory region to be locked down.

</dd> <dt>

*puLockData* \[in, out\]
</dt> <dd>

Pointer to a [**DD\_LOCKDATA**](https://www.bing.com/search?q=**DD\_LOCKDATA**) structure that contains the information required to perform the lock down.

</dd> </dl>

## Return value

**NtGdiDdLockD3D** returns one of the following callback codes.



| Return code                                                                                              | Description                                                                                                                                                                                                                                                                                                                                                                |
|----------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <dl> <dt>**DDHAL\_DRIVER\_HANDLED**</dt> </dl>    | The driver has performed the operation and returned a valid return code for that operation. If this code is DD\_OK, DirectDraw or Direct3D proceeds with the function. Otherwise, DirectDraw or Direct3D returns the error code provided by the driver and aborts the function.<br/>                                                                                 |
| <dl> <dt>**DDHAL\_DRIVER\_NOTHANDLED**</dt> </dl> | The driver has no comment on the requested operation. If the driver is required to have implemented a particular callback, DirectDraw or Direct3D reports an error condition. Otherwise, DirectDraw or Direct3D handles the operation as if the driver callback had not been defined by executing the DirectDraw or Direct3D device-independent implementation.<br/> |



 

## Requirements



|                                     |                                                                                    |
|-------------------------------------|------------------------------------------------------------------------------------|
| Minimum supported client<br/> | Windows 2000 Professional \[desktop apps only\]<br/>                         |
| Minimum supported server<br/> | Windows 2000 Server \[desktop apps only\]<br/>                               |
| Header<br/>                   | <dl> <dt>Ntgdi.h</dt> </dl> |



## See also

<dl> <dt>

[Graphics Low Level Client Support](-dxgkernel-low-level-client-support.md)
</dt> </dl>

 

 



