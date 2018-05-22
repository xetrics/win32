---
Description: 'The InitAllocator method creates a memory allocator.'
ms.assetid: 'a1fa0ffb-ed43-446d-811e-6c3594743592'
title: 'CBaseOutputPin.InitAllocator method'
---

# CBaseOutputPin.InitAllocator method

The `InitAllocator` method creates a memory allocator.

## Syntax


```C++
virtual HRESULT InitAllocator(
  �IMemAllocator **ppAlloc
);
```



## Parameters

<dl> <dt>

*ppAlloc* 
</dt> <dd>

Address of a variable that receives a pointer to the allocator's [**IMemAllocator**](imemallocator.md) interface.

</dd> </dl>

## Return value

Returns S\_OK if successful, or an error code from the **CoCreateInstance** function.

## Remarks

If the input pin does not provide a memory allocator, the [**CBaseOutputPin::DecideAllocator**](cbaseoutputpin-decideallocator.md) method calls this method to create an allocator.

## Requirements



|                    |                                                                                                                                                                                            |
|--------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Header<br/>  | <dl> <dt>Amfilter.h (include Streams.h)</dt> </dl>                                                                                  |
| Library<br/> | <dl> <dt>Strmbase.lib (retail builds); </dt> <dt>Strmbasd.lib (debug builds)</dt> </dl> |



## See also

<dl> <dt>

[**CBaseOutputPin Class**](cbaseoutputpin.md)
</dt> </dl>

�

�



