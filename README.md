# biometric

This repository holds projects using biometrics. The first project is simply called biometric, 
and is based on Apple's LocalAuthentication framework. This command line program will prompt the
user to authenticate on macOS using Touch ID. If the user fails Touch ID authentication, the 
reason for the failure will be displayed.

The code requires biometric authentication using policy ```LAPolicyDeviceOwnerAuthenticationWithBiometrics```, which means that attempts to input the password will
fail:

```objective-c
[myContext evaluatePolicy:LAPolicyDeviceOwnerAuthenticationWithBiometrics
                      localizedReason:myLocalizedReasonString
                                reply:^(BOOL success, NSError *error) {
                                    result = success ? kTouchIDResultAllowed : kTouchIDResultFailed;
                                    authError = error;
                                    CFRunLoopWakeUp(CFRunLoopGetCurrent());
                                }];
```

When running biometric from the terminal, the following Touch ID prompt is displayed:
![Touch ID Prompt](img/screenshot.00.png?raw=true "Touch ID Prompt")

Here are examples of the kinds of output biometric will produce based on different authentication states.
![biometric return statuses](img/screenshot.01.png?raw=true "biometric return statuses")
