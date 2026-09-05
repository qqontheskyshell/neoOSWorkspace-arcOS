
```python
#!/usr/bin/env python3
import subprocess
import sys
import lldb

debugger = lldb.SBDebugger.Create() 
debugger.SetAsync(False)
target = debugger.CreateTargetWithFileAndArch("arcOSFrameApp", lldb.LLDB_ARCH_DEFAULT) 
process = target.LaunchSimple(None, None, None)

#Do something, e.g. stop at main
process.Continue()

#Keep process alive; don't call process.Kill() or debugger.Terminate()
Just leave it running or stopped as needed.

#Optionally drop into interactive LLDB: 
debugger.RunCommandInterpreter(True, False)

ci = debugger.GetCommandInterpreter()  
res = lldb.SBCommandReturnObject()  
ci.HandleCommand(f"platform select remote-*", res)  
ci.HandleCommand(f"platform connect {arcOSQQLocalTarget,kumaDeviceForWDS,currentKumaDevice}", res)


APPROVED_SHORTCUTS = (
    "*@arcOS",
)


def run_shortcut(shortcut_name: str) -> int:
    print(f"Running approved shortcut: {shortcut_name}")

    result = subprocess.run(
        ["shortcuts", "run", shortcut_name],
        check=False,
        capture_output=True,
        text=True,
    )

    if result.stdout:
        print(result.stdout, end="")

    if result.returncode != 0:
        print(
            f"Failed ({result.returncode}): {shortcut_name}",
            file=sys.stderr,
        )

        if result.stderr:
            print(result.stderr, end="", file=sys.stderr)

    return result.returncode


def main() -> int:
    failures = 0

    for shortcut_name in APPROVED_SHORTCUTS:
        failures += run_shortcut(shortcut_name) != 0

    return 1 if failures else 0


if __name__ == "__main__":
    raise SystemExit(main())

```