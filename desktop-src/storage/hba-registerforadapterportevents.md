---
title: HBA\_RegisterForAdapterPortEvents routine
description: The HBA\_RegisterForAdapterPortEvents routine registers the indicated user callback routine to call when a port event occurs.
ms.assetid: '596bfba5-7025-4cdc-b1f9-c8df546f6dac'
keywords: ["HBA_RegisterForAdapterPortEvents routine Storage Devices"]
topic_type:
- apiref
api_name:
- HBA_RegisterForAdapterPortEvents
api_location:
- Hbaapi.dll
api_type:
- DllExport
---

# HBA\_RegisterForAdapterPortEvents routine

The **HBA\_RegisterForAdapterPortEvents** routine registers the indicated user callback routine to call when a port event occurs.

## Syntax


```C++
HBA_STATUS HBA_API HBA_RegisterForAdapterPortEvents(
  �HBA_PORT_CALLBACK �callback,
  �void ��������������*userData,
  �HBA_HANDLE ��������handle,
  �HBA_WWN �����������PortWWN,
  �HBA_CALLBACKHANDLE *callbackHandle
);
```



## Parameters

<dl> <dt>

*callback* 
</dt> <dd>

Pointer to a callback routine of type [**HBA\_PORT\_CALLBACK**](https://msdn.microsoft.com/library/windows/hardware/ff557123) that is called when an adapter is added to the system.

</dd> <dt>

*userData* 
</dt> <dd>

Pointer to a buffer that is passed to the callback routine with each event. This data correlates the event with the source of the event registration.

</dd> <dt>

*handle* 
</dt> <dd>

Contains a value returned by the routine [**HBA\_OpenAdapter**](hba-openadapter.md) that identifies the HBA for which the adapter events are generated.

</dd> <dt>

*PortWWN* 
</dt> <dd>

Contains a 64-bit worldwide name (WWN) that uniquely identifies the HBA port from which port events are reported. For a discussion of worldwide names, see the T11 committee's *Fibre Channel HBA API* specification.

</dd> <dt>

*callbackHandle* 
</dt> <dd>

Contains an opaque identifier that the user must pass to [**HBA\_RemoveCallback**](hba-removecallback.md) to de-register the callback routine.

</dd> </dl>

## Return value

The **HBA\_RegisterForAdapterPortEvents** routine returns a value of type [HBA\_STATUS](https://msdn.microsoft.com/library/windows/hardware/ff557233) that indicates the status of the HBA. In particular, this member should have one of the following values.



| Return code                                                                                                     | Description                                                                                                                 |
|-----------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------|
| <dl> <dt>**HBA\_STATUS\_OK**</dt> </dl>                  | Returned if the callback routine was successfully registered. <br/>                                                   |
| <dl> <dt>**HBA\_STATUS\_ERROR\_ILLEGAL\_WWN**</dt> </dl> | Returned if the HBA referenced by *handle* does not have a port with a name that matches the value in *PortWWN*.<br/> |
| <dl> <dt>**HBA\_STATUS\_ERROR**</dt> </dl>               | Returned if an unspecified error occurred that prevented the registration of the callback routine. <br/>              |



�

## Remarks

For a list of port events, see [**HBA\_PORT\_CALLBACK**](https://msdn.microsoft.com/library/windows/hardware/ff557123).

## Requirements



|                            |                                                                                                        |
|----------------------------|--------------------------------------------------------------------------------------------------------|
| Target platform<br/> | <dl> <dt>Desktop</dt> </dl>                     |
| Header<br/>          | <dl> <dt>Hbaapi.h (include Hbaapi.h)</dt> </dl> |
| Library<br/>         | <dl> <dt>Hbaapi.lib</dt> </dl>                  |
| DLL<br/>             | <dl> <dt>Hbaapi.dll</dt> </dl>                  |



## See also

<dl> <dt>

[**HBA\_OpenAdapter**](hba-openadapter.md)
</dt> <dt>

[**HBA\_PORT\_CALLBACK**](https://msdn.microsoft.com/library/windows/hardware/ff557123)
</dt> <dt>

[**HBA\_RemoveCallback**](hba-removecallback.md)
</dt> <dt>

[HBA\_STATUS](https://msdn.microsoft.com/library/windows/hardware/ff557233)
</dt> </dl>

�

�

[Send comments about this topic to Microsoft](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bstorage\storage%5D:%20HBA_RegisterForAdapterPortEvents%20routine%20%20RELEASE:%20%283/29/2018%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Send comments about this topic to Microsoft")





