---
title: Request
parent: USB Device
has_children: false
nav_order: 1
has_toc: false
---

# Request

---

A USB request is sent from the host to the device in the first stage of a control transfer.

### Request format


| Name    | Size | Description                                                      |
|:---------:|:------:|------------------------------------------------------------------|
| type    | 1    |This field contain overall information about the request. If the control transfor include a data stage, the direction will hold the direction of the data. The recipient will indicate who the request applies to. The type will determine who should handle the request.|
| request | 1    |Depending on the **type** member, this number is given to either the device, the class or the vendor, and holds the request code. |
| value   | 2    |The value is used to pass parameters to the request. If the request is GET_DESCRIPTOR or SET_DESCRIPTOR, this field represent the descriptor index and the descriptor type. Basically it tells what descriptor to set or get. In other requests it can have a different meaning. For example, the unique device address is sent through this field.|
| index   | 2    |The index is used to pass parameters to the request. The index can be used to represent the language ID, the endpoint index or the interface index. In some requests, this field is ignored.|
| length  | 2    |This specifies the length of the data in the second stage of the control transfor. If the second stage is not present, this field is **zero**.|

### Request structure field

```
struct {
    u8 type;
    u8 request;
    union {
        u16 value;
        struct {
            u8 descriptor_index;
            u8 descriptor_type;
        }
    }
    u16 index;
    u16 length;
}
```

### Type field

```
enum {
    USB_REQUEST_TYPE_HOST_TO_DEVICE   = 0 << 7,
    USB_REQUEST_TYPE_DEVICE_TO_HOST   = 1 << 7,
  
    USB_REQUEST_TYPE_STANDARD         = 0 << 5,
    USB_REQUEST_TYPE_CLASS            = 1 << 5,
    USB_REQUEST_TYPE_VENDOR           = 2 << 5,
  
    USB_REQUEST_TYPE_DEVICE           = 0 << 0,
    USB_REQUEST_TYPE_INTERFACE        = 1 << 0,
    USB_REQUEST_TYPE_ENDPOINT         = 2 << 0,
    USB_REQUEST_TYPE_OTHER            = 3 << 0,
}
```

### Request field

```
enum {
    USB_REQUEST_CODE_GET_STATUS          = 0,
    USB_REQUEST_CODE_SET_FEATURE         = 1,
    USB_REQUEST_CODE_CLEAR_FEATURE       = 3,
    USB_REQUEST_CODE_SET_ADDRESS         = 5,
    USB_REQUEST_CODE_GET_DESCRIPTOR      = 6,
    USB_REQUEST_CODE_SET_DESCRIPTOR      = 7,
    USB_REQUEST_CODE_GET_CONFIGURATION   = 8,
    USB_REQUEST_CODE_SET_CONFIGURATION   = 9,
    USB_REQUEST_CODE_GET_INTERFACE       = 10,
    USB_REQUEST_CODE_SET_INTERFACE       = 11,
    USB_REQUEST_CODE_SYNC_FRAME          = 12,
}
```

### Descriptor type

```
enum {
    USB_DESCRIPTOR_TYPE_DEVICE        = 1,
    USB_DESCRIPTOR_TYPE_CONFIGURATION = 2,
    USB_DESCRIPTOR_TYPE_STRING        = 3,
    USB_DESCRIPTOR_TYPE_INTERFACE     = 4,
    USB_DESCRIPTOR_TYPE_ENDPOINT      = 5,
}
```

### Language ID

```
enum {
    USB_DESCRIPTOR_TYPE_DEVICE        = 1,
}
```
