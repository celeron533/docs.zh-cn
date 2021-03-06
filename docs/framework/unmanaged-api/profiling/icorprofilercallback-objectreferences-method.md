---
title: ICorProfilerCallback::ObjectReferences 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectReferences
helpviewer_keywords:
- ObjectReferences method [.NET Framework profiling]
- ICorProfilerCallback::ObjectReferences method [.NET Framework profiling]
ms.assetid: dd5e9b64-b4a3-4ba6-9be6-ddb540f4ffcf
topic_type:
- apiref
ms.openlocfilehash: 6e6cc44c2f9028c0e26c4f933242cad93e3a98c3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866086"
---
# <a name="icorprofilercallbackobjectreferences-method"></a>ICorProfilerCallback::ObjectReferences 方法
通知探查器有关指定的对象正在引用的内存中的对象。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
## <a name="parameters"></a>参数  
 `objectId`  
 中引用对象的对象的 ID。  
  
 `classId`  
 中指定对象是其实例的类的 ID。  
  
 `cObjectRefs`  
 中指定的对象引用的对象数（即，`objectRefIds` 数组中元素的数目）。  
  
 `objectRefIds`  
 中`objectId`引用的对象的 Id 数组。  
  
## <a name="remarks"></a>备注  
 完成垃圾回收后，将为堆中剩余的每个对象调用 `ObjectReferences` 方法。 如果探查器从此回调返回错误，则分析服务将停止调用此回调，直到下一次垃圾回收。  
  
 `ObjectReferences` 回调可与[ICorProfilerCallback：： RootReferences](icorprofilercallback-rootreferences-method.md)回调结合使用，以便为运行时创建完整的对象引用关系图。 公共语言运行时（CLR）确保每个对象引用只能由 `ObjectReferences` 方法报告一次。  
  
 `ObjectReferences` 返回的对象 Id 在回调过程中无效，因为垃圾回收可能是在移动对象的中间。 因此，探查器不能尝试在 `ObjectReferences` 调用过程中检查对象。 调用[ICorProfilerCallback2：： GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)时，垃圾回收已完成，可安全完成检查。  
  
 Null `ClassId` 指示 `objectId` 具有正在卸载的类型。  
  
## <a name="requirements"></a>需求  
 **平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **头文件：** CorProf.idl、CorProf.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另请参阅

- [ICorProfilerCallback 接口](icorprofilercallback-interface.md)
