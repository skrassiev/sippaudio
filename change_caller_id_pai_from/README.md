# Changing caller ID via __PAI:__ or __From:__ headers

_PAI stands for `P-Asserted-Identity:` header._

The set of `SIPp` scenarios in this folder allow to test if a device is compliant with updating caller ID with __PAI:__ header or __From:__ header.
For example, Poly supports both, while Yealink supports __From:__, and ALE CE 80xx support none.


## Common flow

All scenarios below work similarly:
1. A call is placed by `SIPp` to the device;
1. A __PAI:__ or __From:__ with a new __CallerID__ are sent in `UPDATE` on early dialog (after 5 seconds of receiving __180 OK__ and before the call is answered on the device);
1. Alternatively, a __PAI:__ or __From:__ with a new __CallerID__ are sent in `UPDATE` on established dialog.
1. Established call is terminated by `SIPp` in 5 seconds or can be hung up manually.


## Scenarios details
* Sending __PAI:__ in initial `INVITE`;
* Sending __PAI:__ in `UPDATE` on early dialog;
* Sending __From:__ in `UPDATE` on early dialog;
* Sending __PAI:__ in `UPDATE` on established dialog;
* Sending __From:__ in `UPDATE` on established dialog.

## Preconditions to run the scenarios

1. Make sure your device is registered with RC;
1. Make sure device is not using TLS (preferably TCP);
1. Learn the device _IP_, SIP _Port_, and phone number.

## Invocation

All scenarios are invoked similarly, just the scenario file name changes:
```bash
# sipp -sf <scenario-file-name>  <device-IP>:<device-SIP-port> -t t1 -m 1 -d 5000 -s <phone-number>
# Here, `-t t1` uses TCP and a single `-m 1` call is made and duration of the call is `5000` msec.
# For example:

sipp -sf uac_update_pai_early_dialog.xml 192.168.130.15:5062 -t t1 -m 1 -d 5000 -s 13345210653
```

## Results

Every successful test will present the changed __CallerID__ display name, corresponding to scenario:
* `foobar_PAI_early`
* etc



