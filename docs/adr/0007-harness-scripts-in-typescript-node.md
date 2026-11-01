# Harness scripts are TypeScript on Node, not shell or C#

Hooks run on every tool call and must behave identically on the owner's Windows machine, Linux CI and Ubuntu cloud sessions. Bash and PowerShell drift across those, and `dotnet run file.cs` has a slow cold start. Node is already required by Angular, so every hook, verification and metrics script is TypeScript run with `tsx`; C# is reserved for the app backend.
