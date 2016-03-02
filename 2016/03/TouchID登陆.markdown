# TouchID登陆
首先需要引入一个库`#import <LocalAuthentication/LAContext.h>`，官方的一个用于TouchID安全验证登陆的`Framework`，

```Objective-C
- (BOOL)canEvaluatePolicy
{
    LAContext *context = [[LAContext alloc] init];
    NSError *error;
    BOOL success;
    return [context canEvaluatePolicy:LAPolicyDeviceOwnerAuthentication error:&error];
}
```
