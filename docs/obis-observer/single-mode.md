# Single multi observer mode

## Single meter mode

The OBIS observer works only with one meter with empty address.
The readout request will be `/?!\r\n`.
Such meter always exists and have the predefined meter id `0`.
User can't remove this meter or assign the meter address.
In single meter mode no action will be performed for all meters with id other then `0`.

## Multi meter mode

The OBIS observer works with meters with address.
The readout request will be `/?<meter address>!\r\n`.
User can add, remove or change the address for such meters.
In multi meter mode no action will be performed for meter with `0` id.
