---
title: USB Device
has_children: true
nav_order: 2
has_toc: false
---


# USB Device
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Electrical

USB consists of 
Before we go into detail, we need to look at how the host recognises and installs a device when you plug it in. We need to do this in general terms without getting bogged down with the detail.

When you plug a USB device in, the host becomes aware (because of the pullup resistor on one data line), that a device has been plugged in.
	  	

The host now signals a USB Reset to the device, in order that it should start in a known state at the end of the reset. In this state the device responds to the default address 0. Until the device has been reset the host prevents data from being sent downstream from the port. It will only reset one device at a time, so there is no danger of two devices responding to address 0.

The host will now send a request to endpoint 0 of device address 0 to find out its maximum packet size. It can discover this by using the Get Descriptor (Device) command. This request is one which the device must respond to even on address 0.

Typically (i.e. with Windows) the host will now reset the device again. It then sends a Set Address request, with a unique address to the device at address 0. After the request is completed, the device assumes the new address. (And at this point the host is now free to reset other recently plugged-in devices.)

Typically the host will now begin to quiz the device for as many details as it feels it needs. Some requests involved here are:

    Get Device Descriptor
    Get Configuration Descriptor
    Get String Descriptor

At the moment the device is in an addressed but unconfigured state, and is only allowed to respond to standard requests.

Once the host feels it has a clear enough picture of what the device is, it will load a suitable device driver.

The device driver will then select a configuration for the device, by sending a Set Configuration request to the device.

The device is now in the configured state, and can start working as the device it was designed to be. From now on it may respond to device specific requests, in addition to the standard requests which it must continue to support.
	  	 

We can now see that there is a set of requests which a device must respond to, and need to look at the detailed means by which the requests are conveyed.

We saw in the last chapter that data is transfered in 4 different types of transfer:

    Control Transfers
    Interrupt Transfers
    Bulk Transfers
    Isochronous Transfers

The only transfer type available before the device has been configured is the Control Transfer. The only endpoint available at this time is the bidirectional Endpoint 0.
Before we go into detail, we need to look at how the host recognises and installs a device when you plug it in. We need to do this in general terms without getting bogged down with the detail.

When you plug a USB device in, the host becomes aware (because of the pullup resistor on one data line), that a device has been plugged in.
	  	

The host now signals a USB Reset to the device, in order that it should start in a known state at the end of the reset. In this state the device responds to the default address 0. Until the device has been reset the host prevents data from being sent downstream from the port. It will only reset one device at a time, so there is no danger of two devices responding to address 0.

The host will now send a request to endpoint 0 of device address 0 to find out its maximum packet size. It can discover this by using the Get Descriptor (Device) command. This request is one which the device must respond to even on address 0.

Typically (i.e. with Windows) the host will now reset the device again. It then sends a Set Address request, with a unique address to the device at address 0. After the request is completed, the device assumes the new address. (And at this point the host is now free to reset other recently plugged-in devices.)

Typically the host will now begin to quiz the device for as many details as it feels it needs. Some requests involved here are:

    Get Device Descriptor
    Get Configuration Descriptor
    Get String Descriptor

At the moment the device is in an addressed but unconfigured state, and is only allowed to respond to standard requests.

Once the host feels it has a clear enough picture of what the device is, it will load a suitable device driver.

The device driver will then select a configuration for the device, by sending a Set Configuration request to the device.

The device is now in the configured state, and can start working as the device it was designed to be. From now on it may respond to device specific requests, in addition to the standard requests which it must continue to support.
	  	 

We can now see that there is a set of requests which a device must respond to, and need to look at the detailed means by which the requests are conveyed.

We saw in the last chapter that data is transfered in 4 different types of transfer:

    Control Transfers
    Interrupt Transfers
    Bulk Transfers
    Isochronous Transfers

The only transfer type available before the device has been configured is the Control Transfer. The only endpoint available at this time is the bidirectional Endpoint 0.

---

## Transactions

Before we go into detail, we need to look at how the host recognises and installs a device when you plug it in. We need to do this in general terms without getting bogged down with the detail.

When you plug a USB device in, the host becomes aware (because of the pullup resistor on one data line), that a device has been plugged in.
	  	

The host now signals a USB Reset to the device, in order that it should start in a known state at the end of the reset. In this state the device responds to the default address 0. Until the device has been reset the host prevents data from being sent downstream from the port. It will only reset one device at a time, so there is no danger of two devices responding to address 0.

The host will now send a request to endpoint 0 of device address 0 to find out its maximum packet size. It can discover this by using the Get Descriptor (Device) command. This request is one which the device must respond to even on address 0.

Typically (i.e. with Windows) the host will now reset the device again. It then sends a Set Address request, with a unique address to the device at address 0. After the request is completed, the device assumes the new address. (And at this point the host is now free to reset other recently plugged-in devices.)

Typically the host will now begin to quiz the device for as many details as it feels it needs. Some requests involved here are:

    Get Device Descriptor
    Get Configuration Descriptor
    Get String Descriptor

At the moment the device is in an addressed but unconfigured state, and is only allowed to respond to standard requests.

Once the host feels it has a clear enough picture of what the device is, it will load a suitable device driver.

The device driver will then select a configuration for the device, by sending a Set Configuration request to the device.

The device is now in the configured state, and can start working as the device it was designed to be. From now on it may respond to device specific requests, in addition to the standard requests which it must continue to support.
	  	 

We can now see that there is a set of requests which a device must respond to, and need to look at the detailed means by which the requests are conveyed.

We saw in the last chapter that data is transfered in 4 different types of transfer:

    Control Transfers
    Interrupt Transfers
    Bulk Transfers
    Isochronous Transfers

The only transfer type available before the device has been configured is the Control Transfer. The only endpoint available at this time is the bidirectional Endpoint 0.

