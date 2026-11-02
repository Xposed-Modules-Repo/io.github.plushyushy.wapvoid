# WapVoid

LSPosed module that neutralizes CVE-2026-58882 at runtime — a WAP Push SMS DoS that crashes `com.android.phone` into an infinite restart loop on unpatched devices.

## What it does

- Intercepts `dispatchWapPdu` and `decodeWapPdu` inside `com.android.phone`
- Voids the `NegativeArraySizeException` before it kills the telephony process
- Scrubs the malformed PDU from `content://sms/raw` to prevent reboot loops
- Logs every blocked attempt with timestamp, sender, and exception type

## Who needs this

Android 12 and 13 never received the October 2026 patch (EOL). Most mid-range devices and older Samsung/Pixel builds on pre-October 2026 security patches are permanently exposed without a module like this.

## Requirements

- Android 12–17
- Root (Magisk / KernelSU) with Zygisk enabled
- LSPosed

## Source

[github.com/plushyushy/wapvoid](https://github.com/plushyushy/wapvoid)
