<h1 align="center">
  <br>
    <img src="https://github.com/OlegKunitsyn/gnucobol-debug/blob/master/icon.png?raw=true" alt="logo" width="200">
  <br>
  VS Code Debugger for GnuCOBOL
  <br>
  <br>
</h1>

<h4 align="center">Debug COBOL code from VS Code.</h4>

A VS Code extension to debug or execute GnuCOBOL code. [Install from VS Code Marketplace](https://marketplace.visualstudio.com/items?itemName=OlegKunitsyn.gnucobol-debug).

### Features
* Setting breakpoints
* Continue, Stop, Restart, Step Over, Step Into, Step Out
* Variables pane
* No mainframe required

![Screenshot](screenshot.png)

### Requirements
* GnuCOBOL `cobc` 2.2+ installed.
* GNU Debugger `gdb` 6.0+ installed.
* A COBOL-syntax extension i.e. `ibm.zopeneditor`, `broadcommfd.cobol-language-support`, `rechinformatica.rech-editor-cobol` or `bitlang.cobol` installed. Otherwise, the breakpoints will be unavailable.

### Usage
When your `launch.json` config is set up, you can debug or execute your COBOL program. If you debug a Compilation Group (main- and sub- programs), you need to list sub-programs inside `group` property. Here's an example:
```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "COBOL debugger",
            "type": "gdb",
            "request": "launch",
            "target": "${file}",
            "targetargs": [],
            "cwd": "${workspaceRoot}",
            "gdbpath": "gdb",
            "cobcpath": "cobc",
            "cobcargs": ["-free", "-x"],
            "group": ["subsample.cbl", "subsubsample.cbl"]
        }
    ]
}
```

Pick `COBOL debugger` from the dropdown on the Debug pane in VS Code. Press the Play button or `F5` to debug or `Ctrl+F5` to execute.

The debugger uses C sourcecode generated by the compiler upon each debugging session. If the sourcemap isn't accurate or you see any other issues, please make a bug-report.

### Roadmap
- Mac
- Windows

Your contribution is always welcome!

### Troubleshooting
Add `verbose` property to your `launch.json` and start debugiing session. In `DEBUG CONSOLE` you will see complete communication log between `gdb` and VS Code. Here's an example:
```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "COBOL debugger",
            "type": "gdb",
            "request": "launch",
            "target": "${file}",
            "targetargs": [],
            "cwd": "${workspaceRoot}",
            "gdbpath": "gdb",
            "cobcpath": "cobc",
            "cobcargs": ["-free", "-x"],
            "group": [],
            "verbose": true
        }
    ]
}
```

