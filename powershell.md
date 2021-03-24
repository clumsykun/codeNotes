# Powershell Tutorial

PowerShell is a task *automation* and *configuration* management framework from Microsoft, consisting of a command-line shell and the associated scripting language.
Initially a Windows component only, known as Windows PowerShell, it was made open-source and cross-platform on 18 August 2016 with the introduction of PowerShell Core.
The former is built on the `.NET Framework`, the latter on `.NET Core`.

## Find Environment Variables by PowerShell

You can use `Get-ChildItem` to enumerate all user environment variables on your system.

You can also access environment variables using the built-in variable called `$env` followed by a colon and the name of the environment variable.
For example, if you want to access environment variables PATH, you can simply enter the command in Powershell:

```bash
$env:PATH
```

